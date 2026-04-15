# Groww — Analytics & Metrics

> OKRs, metric baselines, KPI trees, funnel numbers, cohort sizes, dashboard links.
> Pre-populated from internal PDF docs (2026-03-27). Add current-state numbers as you share them.

---

## Acquisition Channel Taxonomy

3 channels of user acquisition (from notes):

| Channel | Type | Examples |
|---------|------|---------|
| **Organic** | Non-paid, non-referral | Search, word of mouth, app store discovery, brand awareness |
| **Performance** | Paid / paid media | Google UAC, Facebook/Meta ads, YouTube ads, remarketing |
| **Referral** | User-driven | Refer-a-friend programs, invite flows |

> Confirm: which team owns each channel? How is attribution split across these 3?

---

## Affinity Tier Classification

Affinity models (Product Affinity, Instrument Affinity, F&O content affinity) output a grouped score, then categorized into:

| Tier | Description | Campaign strategy |
|------|-------------|-----------------|
| **High affinity** | Strong behavioral signal — likely to act | Personalized, specific content; S&R + OI insights for F&O |
| **Mid affinity** | Moderate signal — some intent | Simplified alerts; moderate personalization |
| **Low affinity** | Weak signal — exploratory | Broad, educational content; instrument affinity alerts |

This High/Mid/Low bucketing is a cross-model pattern — applies to Product Affinity, Instrument Affinity, and F&O content targeting. A "crossed model" combines signals across dimensions to produce the final affinity group.

---

## Metric Hierarchy (KPI Tree)

```
North Star: MAI (Monthly Active Investors)
├── Activation: FID rate (KYC-done → FID)
│   ├── D7 NTU rate
│   ├── Onboarding completion % (per step)
│   └── CAC (cost per NTU/FID)
├── Retention: TTU-MAU% retention
│   ├── M1 / M3 / M6 / M12 retention of NTU cohort
│   ├── Resurrection rate (lapsed TTU returning)
│   └── App-Keep TTU MAU%
├── Cross-sell: Active PPU
│   ├── CNTU rate (NTU → CNTU)
│   └── Cross-sell FID per product
└── Engagement: DAU/MAU (App Affinity)
    ├── Feed/NC DAU, WAU, weekly retention
    ├── Push CTR (by campaign type)
    └── Email open rate, click rate
```

---

## Metric Definitions

| Metric | Formula | Pod | Notes |
|--------|---------|-----|-------|
| **FID** | First transaction event ever | Activation | Primary activation conversion |
| **NTU** | First transaction in current period | Activation | Activation endpoint |
| **TTU** | Total Transacting Users — activity_threshold AND transaction_threshold both met | RID | Core "active user" definition |
| **RID** | Repeat transaction (2nd+) | RID | Habit signal |
| **CNTU** | First transaction in product #2 | Cross-sell | Cross-sell NTU |
| **DTU** | Users transacting on a given day | RID, Trading | Per-product tracking |
| **MTU** | Users transacting at least once in month | All | Used in Active PPU formula |
| **ATU** | Users with AUM > 0 in a product | RID | "Active" definition for invest products |
| **Active PPU** | COUNT(distinct active products per ATU) / COUNT(ATUs) | Cross-sell | Recommended cross-sell metric |
| **PPU (old)** | Products transacted ever / TTU | Cross-sell | Deprecated — market-driven, unstable |
| **GCG uplift** | (TG metric - CG metric) / CG metric | Measurement | Incremental lift from campaigns |
| **App Affinity** | DAU / MAU | Engagement | How frequently active users visit |
| **D0 / D1 tags** | Milestone completion tags, NOT raw day numbers. Format: `D{N}_{milestone}_from_{origin}`. D0 and D1 both refer to the initial account creation day — "D0_onboarding" and "D1_onboarding" mean the same thing: user completed that milestone on the day they signed up. | Activation | Comprehensive cohort labels used in data pipelines. Examples: `D1_onboarding_from_signup`, `D1_NTU_from_signup`. More tag names to be added as data is shared. |
| **D7** | % of a signup cohort who reach a milestone by Day 7 — a time-bounded activation signal | Activation | Separate from D0/D1 tags; this is a time threshold metric |
| **Onboarding %** | Users completing step N / users reaching step N | Activation | Per KYC step |

---

## Known Baselines (from docs — verify currency)

| Metric | Value | As of | Source |
|--------|-------|-------|--------|
| TTU-MAU% Retention | **~73%** | Jan 2024 | Retention Deepdive |
| App-Keep TTU MAU% | **~87%** (ATH) | Jan 2024 | Retention Deepdive |
| NTU → CNTU within 3M | **~70%** | — | NTU→CNTU doc |
| NTU → CNTU within 24M | **~80%** | — | NTU→CNTU doc |
| TTU users becoming inactive/month | **3.2M** | — | Revive doc |
| Signup → Esign in 7D | **26%** | — | WA Onboarding doc |
| Account opening cost | **Rs.44/user** | — | WA Onboarding doc |
| Daily Digest MAU | **8M** (declining) | Mar-25 | Email Optimization doc |
| Monthly comms volume | **~3 Billion** | Feb-24 | Long-term strategy doc |
| % promotional PNs that are generic | **~52%** | — | ML personalization doc |
| Feed/NC WAU | **243K** | Doc date | Feed Content doc |
| Feed/NC DAU | **104K** | Doc date | Feed Content doc |
| Feed weekly retention | **33%** | Doc date | Feed Content doc |

> **Add current state here.** Paste your latest OKR doc, WBR numbers, or cohort size dump and Claude will extract the metrics and populate/update this section.

---

## Dashboard: Overall User Activity Dashboard

> Superset dashboard. Tracks the **full registered user base** — not product-TTU-filtered. Use T-2 for accurate data. Three tabs: Daily / Weekly / Monthly User Activity.

**Two-dashboard distinction:**
- **Overall** (this section) — denominator = `total_base` (~117M registered users). All users, regardless of TTU status.
- **Product TTU** (next section) — denominator = product's TTU count. Activity and transactions by users who have met the TTU threshold for that product.

### Column Definitions

**Daily view:**

| Column | Meaning | Watch out for |
|--------|---------|--------------|
| `total_base` | Total registered users — denominator for MAU%, DAU% etc. | ~117M as of Mar 2026; changes slowly |
| `DAU` | Daily Active Users (opened app) | — |
| `DAU%` | DAU / total_base | Very low (~7-8%) — most registered users don't open app daily |
| `Sessions/DAU` | Average sessions per daily active user | Engagement intensity; was 80-100 in 2022, now ~50-60 — declining trend |
| `Email Accepted%` | % of users whose email was accepted by ESP (Netcore) | Higher than Reached% — ESP can accept but still fail to deliver |
| `Email Reached%` | % of users actually reached by email (delivered/opened) | Always ≤ Email Accepted% |
| `Push_Del/User` | Average push notifications delivered per user per day | Volume-per-user proxy; affected by frequency cap |

**Weekly view:**

| Column | Meaning | Watch out for |
|--------|---------|--------------|
| `WAU` | Weekly Active Users | — |
| `WAU%` | WAU / total_base | ~13-15% of base is weekly active |
| `Push Reached%` | % of users who received at least one push notification in the week | Only ~16-17% — push opt-in is very low; 1 in 6 TTU users reachable via push per week |
| `Sessions/WAU` | Average sessions per weekly active user | — |
| `WTU/WAU` | % of weekly active users who transacted | Transaction conversion rate of engaged base |

**Monthly view:**

| Column | Meaning | Watch out for |
|--------|---------|--------------|
| `MAU` | Monthly Active Users | — |
| `MAU%` | MAU / total_base | ~20% of base (~23-25M) is monthly active |
| `Sessions/MAU` | Average sessions per monthly active user | Declining long-term (~80-100 → ~50-60) — engagement intensity per user falling even as MAU grows |
| `MTU/MAU` | % of monthly active users who transacted | — |

### Key Structural Patterns

- **Push opt-in is very low** — Push Reached% ~16-17% weekly means only 1 in 6 TTU receives push per week. Push volume ≠ push reach.
- **Email Accepted% > Email Reached%** always — ESP accepts a higher % than actually reaches inbox. Accepted is the ESP's acceptance signal; Reached is the effective delivery signal.
- **Sessions/DAU declining** — was 80-100 sessions/user/day in 2022, now ~50-60. User engagement intensity per session is falling even as absolute DAU grows.
- **total_base is the right denominator for MAU%** — not TTU count. ~20% of all registered users are monthly active.
- **DAU% is low (~7-8%)** — the large denominator (total_base) makes even healthy engagement look small.

---

## Dashboard: Product Daily/Weekly/Monthly Active Investors UE Dashboard

> Superset dashboard. **Use T-2 for accurate data** (2-day pipeline lag). Products covered: Stocks, CNC, MF, MIS, FnO, Options, Futures, MTF, Pay, UPI, BBPS, Credit.

### Column Definitions

**Daily view:**

| Column | Meaning | Denominator | Watch out for |
|--------|---------|-------------|--------------|
| `Overall Product TTU Users` | Rolling TTU count for that product — investment-state, not activity-based | — | Changes slowly; not a daily activity metric |
| `Product TTU App DAU` | Of product TTU, how many opened the app today | Product TTU | — |
| `App DAU Users % TTU` | App DAU / Product TTU | Product TTU | Drops to ~1-2% on weekends; ~18-25% on weekdays |
| `Product DAU` | Users active on that product's section today — includes non-TTU | All users | Different denominator than App DAU |
| `Product DAU % App DAU` | Product DAU / App DAU (TTU only) | App DAU (TTU-only) | **Can exceed 100%** — Product DAU includes non-TTU visitors; App DAU denominator is TTU-only |
| `Product DTU` | Daily Transacting Users for that product | — | 0 on weekends for all market products (market closed) |
| `Product Orders` | Total orders/transactions placed | — | — |
| `Product DTU % DAU` | DTU / Product DAU | Product DAU | Conversion rate: visited section → transacted |
| `Product Order/DTU` | Orders per transacting user | DTU | Trading intensity proxy |

**Weekly view:**

| Column | Meaning |
|--------|---------|
| `App WAU (by Product TTU)` | Weekly active users among that product's TTU |
| `App WAU (% Product TTU)` | WAU / TTU — weekly engagement rate of TTU base |
| `Product WAU` | All users active on product section in the week (TTU + non-TTU) |
| `Product WAU (% App WAU)` | Product WAU / App WAU (TTU-only) — can exceed 100% same reason as daily |
| `Product WTU` | Weekly Transacting Users |
| `WTU / WAU` | % of weekly section visitors who transacted |
| `Order / WTU` | Orders per transacting user per week — trading intensity |
| `Overall Sessions` | Total app sessions by that product's TTU in the week |

**Monthly view:**

| Column | Meaning |
|--------|---------|
| `App MAU (% Product TTU)` | Monthly app engagement rate for that product's TTU — core retention signal |
| `Product MAU` | Users who visited that product's section in the month |
| `Product MTU` | Monthly Transacting Users |
| `MTU / MAU` | % of monthly active who transacted — conversion rate |
| `Orders / MTU` | Monthly trading intensity per transacting user |
| `Sessions / Month` | Total sessions by product TTU — engagement volume proxy |

### Key Structural Patterns (from reading the dashboard)

- **Options ≈ FnO** in all metrics — Options is a subset of FnO; TTU counts and engagement rates are near-identical
- **MF has weekend DTU** — SIPs execute on weekends (automated, date-driven). All market products show DTU=0 on weekends
- **Product DAU % App DAU can exceed 100%** — not a data error; caused by denominator mismatch (Product DAU = all users; App DAU = TTU only)
- **Trading products** (FnO, MIS, Futures) show high Orders/MTU; invest products (MF, CNC) show low Orders/MTU but large absolute volumes
- **MF TTU are product-sticky** — high % who open the app also visit the MF section; FnO TTU less so (open app but may not always go to F&O section)
- **TTU sizes are stable and change slowly** — don't read daily fluctuations as meaningful; monthly trend is the right unit

---

## OKRs

> Populate this section when you share the OKR doc or quarterly goals.

| Quarter | Objective | Key Results | Owner | Status |
|---------|-----------|------------|-------|--------|
| JFM-26 | *(dump OKR doc)* | — | — | — |

---

## Funnel Metrics

### Activation Funnel — Drop Rates

| Step | Drop rate | Notes |
|------|-----------|-------|
| Signup → OTP | 20% | |
| OTP → PAN | **40%** | Biggest drop |
| PAN → Bank Verification | **35%** | 2nd biggest |
| BV → Digilocker | 20% | |
| Digilocker → Esign | 22% | |
| **Overall: Signup → Esign (7D)** | **26% completion** | |

> Actual cohort sizes per step — add when dumped.

### RID / Retention Funnel

| Stage | Metric | Value | Notes |
|-------|--------|-------|-------|
| FID → M1 active | M1 retention | *(dump)* | |
| M1 → M3 | M3 retention | On uptrend (Jan-24) | |
| M3 → M6 | M6 retention | On uptrend (Jan-24) | |
| M6 → M12 | M12 retention | On uptrend (Jan-24) | |
| Inactive TTU day 5+ | Resurrection rate gap | Lower than Dec-23 benchmark | Jan-24 data |

---

## Channel Performance Baselines

### Push Notifications

| Metric | Value | Notes |
|--------|-------|-------|
| Generic campaign CTR | ~3% | BAU baseline |
| Personalized (52W H/L) CTR | **12%** | 4X generic |
| C-MAB V1 CTR uplift | +40% | vs baseline |
| Non-TTU comms DAU uplift (D15) | +55-60% | vs GCG |
| Non-TTU comms NTU uplift (D15) | +75% | vs GCG |
| TTU personalized comms DAU uplift | +11% peak | vs GCG |
| WebEngage throughput | 250K/min | Post-upgrade |

### Email

| Metric | Value |
|--------|-------|
| Delivery rate | **99%** |
| Overall open rate | **18-20%** |
| GrowwFlix open rate | **30%** |
| Weekly Digest opens (post-optimization) | ~2.1M (from 11M targeted) |
| Throughput (Netcore) | 10M/hr |

### WhatsApp

| Use case | CAC / Result |
|---------|-------------|
| WA Esign onboarding | **₹145/incremental Esign** |
| WA reactivation (OB users) | FID CAC = **1/10th** of remarketing |
| WA reactivation (Non-OB users) | FID CAC = **1/5th** of remarketing |
| WA Portfolio Update (resurrection) | **Rs.75/resurrection** |
| BIC message price | **73p/message** |

---

## Dashboards

| Dashboard | What it shows | Tool |
|-----------|-------------|------|
| User Engagement Dashboard | Top-level UE metrics | Superset |
| Comms 360 | Cross-channel communication performance | Superset |
| UE WBR | Weekly business review metrics | Coda / Sheets |
| Campaign-level | CTR, delivery, conversion per campaign | WebEngage native |

> **Add dashboard links when shared.** Paste the URL or screenshot and Claude will document what each panel shows.

---

## Cohort Definitions (for targeting)

| Cohort name | Definition | Typical size | Notes |
|------------|-----------|-------------|-------|
| L30D Active | Opened app within last 30 days | — | High reachability |
| L150D+ Active | Active in last 150 days (not last 30) | Largest inactive base | Push reachability ~1.5% |
| Inactive TTU >60D, AUM>100 | Lapsed investors with skin in game | — | PU Testing target |
| Inactive TTU >180D, PN-unreachable | Deeply lapsed; push useless | — | Asia Cup WA target |
| High Risk (Propensity decile 1-3) | At-risk of churn (Jan MAU) | — | Almost all PPI=1, AUM<500 |
| High Potential (Propensity decile 8-10) | Inactive but recently active | — | Low PN reachability; use WA/RCS |
| PPI=1 | Single-product investors | — | ⚠️ Cross-sell DND risk is high |
| PPI>1, L30D Active | Multi-product active investors | 3.1M (Dec experiment) | Safe cross-sell target |
| D7+ Onboarded non-TTU | KYC-done, haven't invested | — | PA model target |

> **Add more cohorts when shared.** Paste cohort SQL definitions or Audience Manager configs.
