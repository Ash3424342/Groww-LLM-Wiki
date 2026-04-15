# Groww — Data Architecture

> Technical knowledge: DB schemas, table structures, BigQuery datasets, Kafka topics, data pipelines, data flows.
> Pre-populated from internal PDF docs (2026-03-27). Add to this as you dump schemas and configs.

---

## Data Warehouse: BigQuery (BQ)

**Role:** Primary data warehouse for Groww's Growth/UE team.

**Known datasets / tables:**

| Table / Topic | Domain | Contents | Used for |
|--------------|--------|----------|---------|
| `fo_feed` | F&O | Real-time F&O market feed | NARAD Kafka ingestion source |
| `indices_v3` | F&O | Index data (Nifty, BankNifty, etc.) | NARAD Kafka ingestion source |
| `derived_contract_master` | F&O | Derived attributes per contract | NARAD master_tables computation |
| `screener_underlying_details` | F&O | Underlying instrument details for screener | NARAD Kafka ingestion source |
| *(user segments)* | Growth | Audience segments (BQ → Audience Manager → WebEngage daily) | Campaign targeting |

> **Dump more tables here.** When you paste a schema, Claude will extract: table name, key columns, what the table tracks, and which pipeline or tool uses it.

---

## NARAD — Internal CRM Data Pipeline

NARAD is Groww's in-house CRM and real-time campaign trigger system. Below is its technical architecture.

### Ingestion Layer (Kafka)

```
External data sources
  ↓
Kafka topics: fo_feed, indices_v3, derived_contract_master, screener_underlying_details
  ↓
Spark stateful structured streaming
  (joins multiple sources at different refresh intervals)
  (handles event-triggered state + time-based refreshes every minute)
  ↓
master_tables schema (stored, queryable)
```

### master_tables Schema

The central data store for NARAD. All F&O derived attributes live here.

| Table group | Contents |
|------------|---------|
| **Contract master** | Per-contract data (strike, expiry, OI, PCR, price) |
| **Index master** | Index-level data (Nifty spot, PCR, ATM straddle price) |
| **ATM master** | At-The-Money feature tables for options campaigns |
| **Historical attributes** | 30min, 60min, 120min, 1D batch snapshots for each metric |

### Derived Attributes (live in master_tables)

Business team can define new derived attributes in <1 day without DP team involvement. Self-serve model.

| Attribute | Formula / Definition | Campaign it powers |
|-----------|--------------------|--------------------|
| `curr_oi < oi_30min_before * 0.90` | OI dropped >10% in 30 min | OI drop alert |
| **PCR** | Put OI / Call OI | PCR alert campaign |
| **ATM straddle price** | ATM call price + ATM put price | Straddle movement alert |
| **Long buildup** | OI↑ AND price↑ | Buildup alert |
| **Short buildup** | OI↑ AND price↓ | Buildup alert |
| **Covering** | OI↓ AND price↑ | Covering alert |
| **Unwinding** | OI↓ AND price↓ | Unwinding alert |
| **Strike rank** | Distance of contract from ATM in strike steps | OI Buildup targeting filter |

**Next planned:** Greeks (delta, gamma, theta, vega); CNC & MF pipelines on same architecture.

### NARAD Self-Serve Campaign Flow

```
Business team defines eligibility rule (e.g., PCR > 1.2 AND PCR changed > 10%)
  ↓
Rule compiled into derived attribute in master_tables
  ↓
Campaign manager reads eligibility from master_tables
  ↓
Eligible users → WebEngage → Push / WA
  ↓
Result: 20+ F&O campaigns automated; <1 day to add new campaign type
```

---

## User Segmentation Pipeline

```
BigQuery (BQ)
  ↓ daily batch
Audience Manager (AM) — segment computation + user assignment
  ↓
WebEngage — campaign delivery engine
  ↓
FCM (push) / Netcore (email) / WA API
```

**Refresh cadence:** Daily for most segments. Fortnightly for retention propensity model.
**Lag:** C-MAB content affinity currently 2-day lag (EMS upgrade will reduce to 1 day).

---

## Segment Registry (Audience Manager IDs)

### Naming Conventions

**PA segment format:** `PA_{affinity_tier}_{product}_P{rank}_{product2}_P{rank2}_{version}`

| Token | Meaning | Known values |
|-------|---------|-------------|
| `PA` | Product Affinity model | — |
| `HA` | High Affinity tier | — |
| `MA` | Mid Affinity tier | — |
| `lia` | ❓ Low/Inactive Affinity? (lowercase, no version suffix — confirm) | — |
| `CNC_P1` | CNC ranked #1 by model for this user | P1 = top predicted product |
| `MF_P2` | MF ranked #2 | P2 = second predicted product |
| `FnO_P2` | FnO ranked #2 | — |
| `V2` | Version 2 of segment definition | Present on HA/MA segments, absent on `lia` segments |

**NTU cross-product affinity segment format:** `NTU_{P1product}_{P2product}_{LD/HD}`

These are onboarded **Non-TTU** segments (users who haven't reached TTU status — may have transacted but haven't crossed the combined activity + transaction threshold). Built on cross-product affinity signals.

> ⚠️ **Naming collision:** `NTU` in segment names = **Non-TTU** (targeting context). `NTU` as a standalone metric = **New Transacting User** (activation context). Two different meanings — same letters.

| Token | Meaning |
|-------|---------|
| `NTU` | **Non-TTU** — onboarded user who hasn't yet reached TTU status |
| `P1product` | Product with higher affinity score (primary affinity) |
| `P2product` | Product with secondary affinity signal |
| `LD` | Low Difference — user has similar affinity for both products; messaging can go either way |
| `HD` | High Difference — strong preference for P1 over P2; lead with P1 content |

**Known Non-TTU cross-product segments (9 unique IDs — each appears in 2 of 3 product affinity groups = 18 targeting use cases):**

| Segment | Read as |
|---------|---------|
| `NTU_MF_Stock_LD` | MF-affinity user with Stock secondary, similar scores |
| `NTU_MF_Stock_HD` | MF-affinity user with Stock secondary, strong MF preference |
| `NTU_FnO_Stock_LD` | FnO-affinity, Stock secondary, similar scores |
| `NTU_FnO_Stock_HD` | FnO-affinity, Stock secondary, strong FnO preference |
| `NTU_Stock_MF_HD` | Stock-affinity, MF secondary, strong Stock preference |
| `NTU_Stock_FnO_HD` | Stock-affinity, FnO secondary, strong Stock preference |
| `NTU_MF_FnO_LD` | MF-affinity, FnO secondary, similar scores |
| `NTU_MF_FnO_HD` | MF-affinity, FnO secondary, strong MF preference |
| `NTU_FnO_MF_HD` | FnO-affinity, MF secondary, strong FnO preference |

> The 18 segments cover all 3-product combinations (Stock/MF/FnO) × 2 directions × LD/HD. Used to personalize onboarded non-TTU push campaigns with product-specific content.

### IPO Segments

| Segment ID | Meaning |
|-----------|---------|
| `onb_ever_applied_ipo_not_allot` | Completed onboarding, ever applied to an IPO, but was not allotted |
| `IPO_applied_in_last_12M` | Applied to an IPO in the last 12 months |
| `IPO_ever_applied` | Ever applied to any IPO |

### Holdings

| Segment ID | Meaning |
|-----------|---------|
| `stock_holding_gt_0` | Has current stock holdings (AUM > 0 in stocks) |

### Clicker Segments

| Segment ID | Meaning |
|-----------|---------|
| `clicker_last_30days` | Clicked a push notification in the last 30 days |
| `pn_clicker_90_days` | Clicked a push notification in the last 90 days |

### Gold/Silver

| Segment ID | Meaning |
|-----------|---------|
| `only_gold_silver_ntu` | NTU whose only product is Gold or Silver (not invested in stocks/MF/etc.) |
| `Signup_Not_Onboarded_app_active_last_1M` | Signed up, did not complete KYC onboarding, but still active in app within last 1 month |

### Activity / TTU Lifecycle

| Segment ID | Meaning |
|-----------|---------|
| `TTU_LM_Active_CM_Inactive` | TTU who were active last month but inactive current month |
| `TTU_L7D_Inactive` | TTU inactive for last 7 days |
| `TTU_L14D_Inactive` | TTU inactive for last 14 days |
| `TTU_L30D_Inactive` | TTU inactive for last 30 days |
| `TTU_CM_Inactive` | TTU inactive in current month |
| `Ressurection_email_base` | Base for resurrection email campaigns (lapsed TTU reachable by email) |
| `TTU_ddpi_success` | TTU who have successfully completed DDPI (❓ confirm — likely Demat Debit and Pledge Instruction, used for pledging stocks) |
| `MTU_14_30D_ar` | MTU active in the 14–30 day window (at-risk cohort) |
| `MTU_7_14D_ar` | MTU active in the 7–14 day window (at-risk cohort) |
| `MTU_3_7D` | MTU active in the 3–7 day window |
| `MTU_L7D_ar` | MTU active in last 7 days (at-risk) |

> `ar` suffix = "at risk" — recency-based risk signal. Shorter recency window = higher churn risk.

### PA (Product Affinity) Segments

| Segment ID | Affinity Tier | P1 Product | P2 Product | Notes |
|-----------|--------------|-----------|-----------|-------|
| `PA_HA_CNC_P1_V2` | High | CNC | — | Single-product HA targeting |
| `PA_HA_CNC_P1_MF_P2_V2` | High | CNC | MF | CNC primary, MF secondary |
| `PA_HA_CNC_P1_FnO_P2_V2` | High | CNC | FnO | CNC primary, FnO secondary |
| `PA_HA_MF_P1_CNC_P2_V2` | High | MF | CNC | MF primary, CNC secondary |
| `PA_MA_CNC_P1_V2` | Mid | CNC | — | Single-product MA targeting |
| `PA_MA_CNC_P1_MF_P2_V2` | Mid | CNC | MF | — |
| `PA_MA_MF_P1_CNC_P2_V2` | Mid | MF | CNC | — |
| `pa_lia_cnc_p1` | ❓ `lia` tier | CNC | — | No V2 suffix — older version or different tier? |
| `pa_lia_mf_p1` | ❓ `lia` tier | MF | — | ❓ Needs more context — what is this segment used for? |
| `pa_lia_cnc_p1_mf_p2` | ❓ `lia` tier | CNC | MF | — |
| `pa_lia_mf_p1_cnc_p2` | ❓ `lia` tier | MF | CNC | — |

> ❓ **`lia` tier is unconfirmed.** Hypothesis: "Low Intent Active" or "Low/Inactive Affinity." Lowercase naming and absence of `V2` suffix suggests these may be an older or separate tier. Confirm what `lia` means and how these segments are used differently from HA/MA.

---

## Email Infrastructure

```
WebEngage
  ↓ triggers send
Netcore (ESP) — throughput: 10M/hr (upgraded from 2.2M/hr in Nov-22)
  ↓
User inbox
```

**Subdomains:**
- `digest.groww.in` — primary Digest domain
- `dailydigest.groww.in` — backup domain

**Domain warmup:** 30-day process (100 → 10M emails); requires >20% open rate during warmup.

---

## Push Notification Infrastructure

```
WebEngage (throughput: 250K/min, upgraded from 75K/min)
  ↓
FCM (Firebase Cloud Messaging)
  ↓ (bottleneck discovered here — FCM→user latency increased 120% even after WE scaled)
User device
```

**Note:** Peak push time shifted earlier after throughput upgrade (9:30am, 1:00pm, 4:00pm).

---

## Event Management System (EMS)

**Status:** In progress — replacing WebEngage's data pipeline for C-MAB model inputs.
**Goal:** Reduce C-MAB content affinity data lag from 2 days → 1 day.

---

## ML Data Pipelines

| Model | Training data | Inference | Refresh |
|-------|--------------|---------|---------|
| Product Affinity (PA) | BQ app activity events | BQ → AM → WE | Daily |
| Instrument Affinity | BQ app activity events | BQ → AM → WE | Daily |
| Retention Propensity | BQ transaction history | Segment output → WE | Fortnightly |
| Cross-sell Affinity | BQ transaction + product interaction data | BQ → AM → WE | Daily (14D prediction window) |
| C-MAB (Thompson Sampling) | WE event stream (CTR + Tx reward) | Real-time in WE | Continuous |
| Campaign Affinity | WE event stream (CTR reward) | Real-time in WE | Continuous |
| Widget Ranker | BQ app activity + Explore events | BFF (real-time per page load) | Daily model; real-time inference |

---

## WhatsApp (WA) Infrastructure

**Platform:** COSMOS flow system — WA journeys are built and run here.
**Pricing:** BIC (Business Initiated Conversation): 73p/message. UIC (User Initiated Conversation): 33p/message.
**Volume:** ~3 Billion communications/month across all channels (Feb 2024).

---

## Milestone Tag Naming Convention

User milestone events in the data pipeline use a compound tag format:

```
D{N}_{milestone}_from_{origin}
```

| Component | Meaning | Examples |
|-----------|---------|---------|
| `D{N}` | Day index relative to a starting event. D0 and D1 both = the initial/signup day (interchangeable in naming) | D0, D1 |
| `{milestone}` | What was completed | `onboarding`, `dmat`, `NTU` |
| `from_{origin}` | Starting point of the journey | `from_signup` |

**Key rule:** D0 and D1 are not strictly different days — they are both used to tag events that happened on the user's account creation day. `D0_dmat` and `D0_onboarding` both mean the user completed that milestone on the same day they created their account.

**Known tags so far:**
| Tag | Meaning |
|-----|---------|
| `D0_onboarding` / `D1_onboarding` | User completed full onboarding on signup day |
| `D0_dmat` | User completed Demat account on signup day |
| `D1_onboarding_from_signup` | User completed onboarding within Day 1 of signup |
| `D1_NTU_from_signup` | User became NTU (New Transacting User) on Day 1 from signup |

> More tags to be added as data schemas are shared.

---

## Data Dictionary — Key Terms

| Term | Technical meaning | Business meaning |
|------|-----------------|----------------|
| **TTU** | User where activity_flag=1 AND transaction_flag=1 (thresholds TBD from user) | Total Transacting Users |
| **FID** | First ever transaction event timestamp | User's first investment |
| **NTU** | First transaction in current period | New transacting user this month |
| **CNTU** | First transaction in a non-primary product | Cross-sell conversion |
| **GCG** | Users in holdout cohort (no promotional comms sent) | Control group for measurement |
| **PP visits** | Product page view events ≥ threshold | Investment intent signal |
| **Active PPU** | COUNT(DISTINCT active product) / COUNT(active users) | Products per active user |

---

> **Add schemas here:** Paste any BigQuery table DDL, column list, ERD, or pipeline config and Claude will parse it, identify what each table/column tracks, and document it in this file.
