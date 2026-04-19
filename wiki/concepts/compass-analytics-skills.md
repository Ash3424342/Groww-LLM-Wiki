---
title: Compass Analytics Skills
date_updated: 2026-04-19
tags: [concept, compass, analytics-skills, data-platform]
---

# Compass Analytics Skills

16 domain-specific knowledge packages that tell the AI which tables, columns, filters, and query patterns to use. Skills are loaded automatically when Compass detects the domain.

## What Each Skill Contains

- **Tables Overview** — tables with row counts, freshness, grain, partition columns
- **Key Columns Reference** — column types, descriptions, sample values
- **Common Filter Values** — exact enumerations (status codes, product types, etc.)
- **10+ Example Queries** — production-ready SQL templates
- **Query Strategy Table** — "If user asks X, use table Y with approach Z"
- **Table Relationships** — join keys and cross-table navigation
- **Data Quality Notes** — stale tables, naming inconsistencies, PII warnings
- **Critical Guardrails** — partition requirements, row count warnings, timeout prevention

## All 16 Skills

| # | Skill | Domain | Key Tables | Scale |
|---|-------|--------|-----------|-------|
| 1 | **Stocks & Trading** | Equities | `core_stocks_order`, `fact_transaction_stocks` | 2.5B, 7.1B rows |
| 2 | **F&O Analytics** | Derivatives | `fno_order_master`, `fno_pnl_master` | 3.8B, 1.9B |
| 3 | **Mutual Funds** | MF | `fact_mutual_fund_order_details_enriched`, `view_mf_user_aum_latest` | Millions |
| 4 | **User Master & Growth** | Growth | `growth_user_master_ultimate`, `user_product_txn_master_fact` | 117M, 8.3B |
| 5 | **User Events** | Instrumentation | DataHub `userEvent` entities + `ems_raw` | 57B+ events |
| 6 | **Onboarding** | Activation | `onb_usercheckpoints_master`, `fact_onboarding_invest` | 117M, 45M |
| 7 | **UPI Payments** | Payments | `groww_upi_onb_user_fact`, `groww_upi_mandate_fact_table` | 66.9M, 27.2M |
| 8 | **MTF & Pledge** | Margin | `aay_mtf_fid_agg`, `fact_pledge_transaction` | 243, 50M |
| 9 | **Commodities** | MCX | `commodity_day_view_seg`, `commodity_order_master` | 684K, 71.6M |
| 10 | **915 Trading** | 915 App | `userday_details_915`, `usersession_915` | 1.9M |
| 11 | **Help & Support** | Support | `hns_helpdesktickets_master_trino`, `hns_chatbot_fact_table_v3` | 12M, 135K |
| 12 | **Engagement** | Comms | `engagement_pn_narad_master`, `engagement_user_session_daily` | 250M/day, 8M |
| 13 | **Context Push** | Notifications | Context-aware push tables | Varies |
| 14 | **User Financial Health** | Wellness | Financial health tables | Varies |
| 15 | **Datahub Navigation** | Meta | DataHub entities | N/A |
| 16 | **MF Analytics Extended** | MF | Extended MF tables | Varies |

## Skill #12: Engagement & Communications (Most Relevant to Growth)

**Trigger**: DAU, sessions, push notifications, email, SMS, WhatsApp, DND, app install, campaign performance

*Fully cataloged 2026-04-18/19 via live Compass session. See `Deliverables/cmp-1-engagement-skill-spec.md` for complete schemas, SQL examples, and guardrails.*

### Tables (all in `platform_iceberg.core_bgv`)

| Table | Total rows | Rows/day | Channel | Partition | Last snapshot |
|-------|-----------|----------|---------|-----------|---------------|
| `engagement_pn_narad_master` | 92.7B | 170-250M | Push (NARAD) | `event_date` | 2026-04-17 daily |
| `engagement_email_backend_master` | 5.5B | 3-14M | Email (Blazr/EMS) | `event_date` | 2026-04-17 daily |
| `engagement_sms_backend_master` | 722M | 500-650K | SMS (INFOBIP) | `event_date` | 2026-04-17 daily |
| `engagement_whatsapp_backend_master` | 47.7M | 100-140K | WhatsApp (GUPSHUP) | `event_date` | 2026-04-17 daily |
| `engagement_user_session_daily` | 9.1B | 8M | DAU aggregated | `session_date` | 2026-04-17 daily |
| `engagement_dau_indepth` | 8.5B | 8M | App engagement | `session_date` | 2026-04-17 daily |
| `engagement_session_indepth` | **58.1B** | **60M** | Per-session detail | `session_date` | 2026-04-17 daily |
| `engagement_app_fact` | 16.2B | Weekly | App install/reachability | `week` (Sundays) | 2026-04-13 |
| `engagement_dnd_fact` | 92.5M | ~70K | DND state changes | **NONE** (COR table) | 2026-04-17 |
| `engagement_email_narad_master` | — | — | Email (Narad/campaign) | `event_date` | — |

> **`engagement_email_narad_master`** — recommended addition (#10). Campaign-level email tracking with `campaign_name`, `open_time`, `click_time`, `unsubscribe_time`. Mirrors PN narad for email.

### PN Delivery Funnel (live 2026-04-17)

```
Total attempts: ~249M → SENT: 181M (72.9%) → VENDOR_FAILURE: 32.5M (13.1%)
OPTED_OUT: 23.6M (9.5%) → FREQUENCY_CAPPED: 11.6M (4.7%) → EXPIRED: 94K
DND: 27K | INTERNAL_SERVICE_FAILURE: 1.4K
```

### PN Status Enum (7 values — wiki previously had 5)

| Status | % (2026-04-17) |
|--------|----------------|
| SENT | 72.9% |
| VENDOR_FAILURE | 13.1% |
| OPTED_OUT | 9.5% |
| FREQUENCY_CAPPED | 4.7% |
| EXPIRED | 0.04% |
| DND | 0.01% |
| INTERNAL_SERVICE_FAILURE | <0.01% |

### Email Delivery Funnel (live 2026-04-17)

```
Total: 5.4M records → Delivered: 5.2M (95.2%) → Opened: 622K (12.0% open rate)
→ Clicked: 10.6K (1.7% click-to-open rate)
```

> Note: `event_name` in email_backend_master = **email template identifier** (e.g., `contract_note`, `git_mf_sip_order_processed`), NOT a delivery event. Delivery funnel = `deliver_flag`, `open_flag`, `click_flag` (integer 0/1).

### Vendor mapping (confirmed)
- Email: **AWS_SES** | Source: **Blazr**
- SMS: **INFOBIP**
- WhatsApp: **GUPSHUP**

### App reachability (week 2026-04-13)
- Android push-reachable: **26.6M** (80% of installed)
- iOS push-reachable: **3.6M** (70% of installed)
- Total push-reachable: **~30.2M**

### Cross-skill join keys

| Engagement table | Join to user_master on |
|---|---|
| email, sms, session_daily, app_fact | `e.user_account_id = u.user_account_id` |
| **pn_narad, whatsapp** | **`pn.useraccountid = u.user_account_id`** (no underscore!) |
| dau_indepth, session_indepth, dnd_fact | `e.cuid = u.cuid` (UUID format) |

TTU segmentation: `growth_user_master.fid_ts_growth IS NOT NULL` → TTU user

### Critical Guardrails (17 confirmed 2026-04-19)

| # | Rule |
|---|------|
| G1 | Trino date syntax: `current_date - interval '1' day` (NOT `current_date - 1`) |
| G2 | No `RIGHT()` in Trino — use `SUBSTR(str, LENGTH(str) - n + 1)` |
| G3 | PN narad `os`: 6 raw values (android/ANDROID/Android/ios/IOS/iOS) — **always `LOWER(os)`** |
| G4 | PN narad `status`: 7 values — includes DND and INTERNAL_SERVICE_FAILURE (not just 5) |
| G5 | DND `s7`: VARCHAR `'true'`/`'false'` + 4 null rows — use `COALESCE(s7,'false')='true'` |
| G6 | `engagement_session_indepth`: **60M rows/day** — single-day filter MANDATORY |
| G7 | `session_duration` in session_indepth: frequently NULL — filter `IS NOT NULL` |
| G8 | `comm_session` in session_indepth: NOT always null — CEP campaign attribution field |
| G9 | email `event_name` = template name, NOT delivery status |
| G10 | `txn_dau=1` with `session_count=0` is valid (API transactors) |
| G11 | `app_fact` MAX(week) scan times out — always hardcode `week = DATE '2026-04-13'` |
| G12 | SMS `priority`: mixed casing (`MEDIUM` vs `medium`) — use `LOWER(priority)` |
| G13 | `app_fact os_name`: 4 values — Android, iOS, iPadOS, `iPhone OS` (legacy, 0 reachable) |
| G14 | `os_name` casing: PN narad = mixed (use LOWER); session/DAU/app tables = Title Case |
| G15 | `cuid` (UUID format) is the join key for dau_indepth/session_indepth/dnd_fact |
| G16 | iOS PN `click_time` = always null — iOS click tracking not captured in this column |
| G17 | `engagement_dnd_fact`: no partition (COR table) — `date` is a regular column |

## Skill #4: User Master & Growth

**Trigger**: User profiles, signup funnels, FID tracking, AUM, segmentation, referrals, uninstalls, cohort analysis, demographics

### Key Dimensions

| Dimension | Column | Values |
|-----------|--------|--------|
| User Status | — | SignUp (72M), Onboarded & Transacted (27M), Onboarded & Non-Transacted (17M) |
| Source | — | `performance` (63M), `organic++` (47M), `referral` (7.6M) |
| Platform | — | `android` (98M), `ios` (7M), `msite` (3.7M), `desktop` (3.3M) |
| Age Group | — | 18-22, 23-27, 28-35, 36-40, 40+ |
| AUM Band | — | Zero AUM, <1k, 1k-10k, 10k-50k, 50k-1L, 1L-5L, 5L-10L, 10L-50L, >=50L |
| FID Product | — | `cnc`, `sip`, `lumpsum`, `mis`, `fno`, `gold`, `mtf`, `commodity`, ... |

### Key Guardrails

- `user_product_txn_master_fact` is **8.3B rows** — MUST filter on `order_date`
- Product type naming: **inconsistent** (FID: `cnc`, `sip`; txn_master: `Stocks`, `Mf`)
- Universal join key: `user_account_id` (format `ACC<digits>`)
- Prefer `growth_user_master_ultimate` over `growth_user_master` for analytics

## Skill #6: Onboarding

### The Onboarding Funnel (from data tables)

```
Signup → Email Verified → Mobile Verified → PAN Entered → Bank Verified
→ Signature → E-sign → KYC Verified → Stock Onboarding (success)
                            ↓
                   F&O Activation → Commodity Activation
```

Each step = a timestamp column in `onb_usercheckpoints_master`. NULL = step not reached.

### Guardrails

- `esign_details` contains PII (PAN, Aadhaar, bank numbers) — never SELECT *
- `daily_onb_conversions` is EMPTY, pipeline broken — use `daily_onboarding_and_fid`
- `fact_onboarding_fno` has 154 columns — select only needed funnel steps

## Build Status (as of 2026-04-19)

| Task | Skill | Priority | Status |
|------|-------|----------|--------|
| CMP-1 | Engagement & Comms (#12) | Tier 1 — feeds Content Engine | **✅ done** — schemas, enums, 45 SQL examples, cross-skill joins all confirmed |
| CMP-2 | Context Push (#13) | High — ground-up build | todo |
| CMP-3 | User Financial Health (#14) | High — ground-up build | todo |
| CMP-4 | MF Analytics Extended (#16) | High — extends existing MF skill | todo |

## Related

- [[compass-mcp]] — the platform these skills run on
- [[saurabh-dubey]] — built Compass MCP; Analytics Skills Deep Dive doc (18 pages) is the source of truth
- [[narad]] — Engagement skill queries NARAD tables
- [[groww-campaign-engine]] — Content Engine uses Compass to inform campaign strategy
- [[activation-funnel]] — Onboarding skill covers the same funnel from the data side
- [[segment-registry]] — User Master skill has the source data for segments
- [[push-notifications]] — Engagement skill has PN delivery funnel data
