---
title: Compass Analytics Skills
date_updated: 2026-04-06
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

### Tables

| Table | Rows/Day | Channel |
|-------|----------|---------|
| `engagement_pn_narad_master` | **170-250M** | Push (NARAD) |
| `engagement_email_backend_master` | 3-6M | Email (Backend) |
| `engagement_sms_backend_master` | 500-650K | SMS |
| `engagement_whatsapp_backend_master` | 100-140K | WhatsApp |
| `engagement_user_session_daily` | 8M | DAU (aggregated) |
| `engagement_dau_indepth` | 8M | App engagement metrics |
| `engagement_session_indepth` | **65M (57B total)** | Per-session detail |
| `engagement_app_fact` | Weekly | App install/reachability |
| `engagement_dnd_fact` | 70K | DND state changes |

### PN Delivery Funnel (typical day)

```
Total: ~3M → Sent: ~2M (66%) → Received: ~440K (22%) → Shown: ~438K → Clicked: ~19K (4.3% CTR)
```

### PN Status Distribution

| Status | % |
|--------|---|
| SENT | 72% |
| OPTED_OUT | 9% |
| VENDOR_FAILURE | 9% |
| FREQUENCY_CAPPED | 8.6% |
| EXPIRED | 1.7% |

### Key Guardrails

- `engagement_session_indepth` has **57 BILLION rows** — SINGLE DAY queries only
- PN NARAD `os` column: mixed casing (`android` vs `ANDROID`) — always use `LOWER(os)`
- DND `s7` column is VARCHAR (`'true'`/`'false'`), not boolean
- Prefer `engagement_user_session_daily` for DAU over `engagement_session_indepth`

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

## Related

- [[compass-mcp]] — the platform these skills run on
- [[narad]] — Engagement skill queries NARAD tables
- [[activation-funnel]] — Onboarding skill covers the same funnel from the data side
- [[segment-registry]] — User Master skill has the source data for segments
- [[push-notifications]] — Engagement skill has PN delivery funnel data
