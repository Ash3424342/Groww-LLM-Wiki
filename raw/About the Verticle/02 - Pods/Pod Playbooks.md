# Groww Growth Vertical — Pod Playbooks

> **Pod-centric reference.** Everything you need to understand or work on a specific pod — its people, metrics, experiments, channel strategies, ML models, and open questions — all in one place per pod.
>
> For detailed metric definitions and exhaustive benchmarks: see `Growth Vertical - Master Reference.md`
> For concept explanations (the "why"): see `Growth Vertical - Concepts & Notes.md`
>
> Last updated: 2026-03-27

---

## Table of Contents

1. [Invest Pod — Activation](#1-invest-pod--activation)
2. [Invest Pod — RID & Retention](#2-invest-pod--rid--retention)
3. [Invest Pod — CNC (Stocks Trading)](#3-invest-pod--cnc-stocks-trading)
4. [Invest Pod — Personalization](#4-invest-pod--personalization)
5. [Trading Pod (F&O, MTF, MIS, Commodities)](#5-trading-pod-fo-mtf-mis-commodities)
6. [Pay Pod](#6-pay-pod)
7. [Feed & Content Pod (NC / Stories)](#7-feed--content-pod-nc--stories)
8. [Cross-sell (Cross-Pod Initiative)](#8-cross-sell-cross-pod-initiative)
9. [Shared Infrastructure](#9-shared-infrastructure)

---

## 1. Invest Pod — Activation

**Goal:** Get KYC-done users to make their first investment (FID). The 0→1 journey.

**Funnel:** Sign-up → OTP → PAN → Bank Verification → Digilocker → Esign → Product Browse → PP Visits → FID

### People

| Person | Role |
|--------|------|
| **Nikhil** | Overall activation strategy, experiment design |
| **Shweta** | "Invest & Instigate" — campaign strategy to nudge users toward first investment |
| **Aishwarya** | Communication execution — builds/sends campaigns; owns RCS, SMS, Stories channels |

### Key Metrics

| Metric | Definition | Target |
|--------|-----------|--------|
| **FID** | First Investment Done — user's first transaction anywhere on Groww | Primary goal |
| **NTU** | New Transacting User — user who transacted for first time in a period | Activation endpoint |
| **D7** | % of registered users who become NTU by Day 7 | Early activation signal |
| **Onboarding %** | Step-by-step completion rate through 7-8 step KYC funnel | Watch per step |
| **PP Visits** | Product Page visits — proxy for investment intent for non-TTU users | Signal for high-intent sub-segment |
| **CAC** | Cost per Acquisition (per NTU/FID) | Minimize vs channel |

### Funnel Drop Rates (KYC)

```
Signup
  ↓ 20% drop → OTP verified
  ↓ 40% drop → PAN verified  ← BIGGEST drop
  ↓ 35% drop → Bank Verified ← 2nd biggest
  ↓ 20% drop → Digilocker done
  ↓ 22% drop → Esign ✅ (KYC complete)
```
**Only 26% of users complete Signup → Esign within 7 days.**
Account opening baseline cost: **Rs.44/user**

### Onboarding Journey Touchpoints (per drop-off stage)

| Journey | Duration | Channels | # Touchpoints |
|---------|---------|---------|--------------|
| Install → Signup | 3 days | Push | 3 PN |
| Welcome on Signup | 1 day | Email | 1 Email |
| Mobile Verification drop-off | 4 days | Push + Email | 5 PN + 2 Email |
| PAN drop-off | 6 days | Push | TBC |
| Bank Verification drop-off | 6 days | Push + WA + SMS + RCS + Email | 7 PN + 2 WA + 4 SMS + 2 RCS + 3 Email |
| Digilocker drop-off | — | Push + WA + Email | TBC |
| Selfie / Signature drop-off | — | Push | TBC |
| Esign drop-off | — | Push + WA | TBC |
| FID drop-off | — | Push + WA + Email | TBC |

> Channel escalation: earlier steps use Push + Email only. Bank drop-off = 5 channels (most touchpoints — highest-stakes step). COSMOS manages the journey automation.

### Channel Strategies

| Cohort | Channel | Approach | Result |
|--------|---------|----------|--------|
| All KYC-in-progress users | WhatsApp | Journey triggered at each drop-off step (OTP_PAN through SIGN_ESIGN) | ~200 incremental Esign/day; **₹145/conversion**; live 100% via COSMOS |
| Active within 30D | Push / Email / WA | Standard activation sequence | High reachability |
| Inactive 150D+ (non-OB) | WhatsApp | FID-focused reactivation | CAC = **1/5th** of remarketing CAC |
| Inactive 150D+ (OB users) | WhatsApp | FID-focused reactivation | CAC = **1/10th** of remarketing CAC |
| Inactive 150D+ (broad) | Remarketing (Google/FB) | Retargeting ads | ~30% of L150D+ MAU comes from ads; old CAC 6,000+ |
| Push-unreachable base | WhatsApp | Primary channel — ~50% of non-investors have push off | Only reachable channel |
| High-intent (PP visits ≥2-5) | All channels | Concentrated activation push | Higher conversion than broad blast |

### Key Experiments

| Experiment | Hypothesis | Result | Status |
|-----------|-----------|--------|--------|
| WA at Esign step | WA adds to push+email+SMS → more KYC completions | **+30% conversion uplift** in TG vs CG | Live permanently |
| WA at IFSC→BV step | WA helps at this early funnel step too | Only 4% uplift — adds Rs.20 CAC | NOT live (reverted) |
| WA for Inactive Non-OB users | WA brings dormant non-investors back to FID | FID CAC = 1/5th of remarketing | Scaled to 300K users |
| Instrument Affinity — Top 10 stocks NTU | Show NTU the stock they're most likely to buy | DAU +3%; minimal NTU uplift | Automating into in-house CM |
| Instrument Affinity — Top 11-50 stocks NTU | More stocks = more relevance? | CTR +23%, NO DAU impact | Paused |
| PA Model for OB/NTU (D7+ users) | Product affinity ML improves FID conversion | CTR↑, Sessions↑, NO FID uplift | Running — further iteration needed |
| Scale-up Non-TTU (D30+ inactive) | WA + Remarketing revives inactive non-investors | D90-180 OB remarketing: **+5.43% FID**; Activity uplift: **+15.82%** | Ongoing |

### ML Models Used

| Model | What it does | Owner | Status |
|-------|-------------|-------|--------|
| **Product Affinity (PA)** | Predicts top 2 products for user to invest in next | Preksha Vyas | Live; 73% overall accuracy (MF 55% — weakest) |
| **Instrument Affinity** | Predicts top stock/fund the user is most likely to act on | Amit Kumar | Top 10 live; expanding |
| **Time Activity Model** | When the user is most active — optimal send time | — | Part of personalization engine |

### Open Questions

- Improve PA model accuracy for MF (currently 55% — dragging overall accuracy)
- Pay yet to be added to PA model scope
- Next: C-MAB widget personalization for Stocks Explore (previous v0/v1 showed NTU flat — widget mix wasn't the problem)

---

## 2. Invest Pod — RID & Retention

**Goal:** Keep TTU users transacting repeatedly. Prevent churn. Resurrect lapsed users.

**Products covered:** MF, CNC (Stocks), ETF, Bonds, IPO — see CNC section for CNC-specific detail.

### People

| Person | Role |
|--------|------|
| **Nikhil** | RID strategy — all products |
| **Himanshu Khandelwal** | RID strategy + ML models; email infra ownership |
| **Amit** | MF-specific RID strategy (possibly full Invest pod ownership) |
| **Shweta** | Communication orchestration for RID pod |
| **Ritvik Pandey** | MF TTU personalization, Feed personalization strategy |

### Key Metrics

| Metric | Value / Definition |
|--------|-------------------|
| **TTU** | Total Transacting Users — crossed both activity + transaction threshold. Core active-investor definition |
| **TTU-MAU% Retention** | % of TTU in month M who transact in M+1 — **~73%** (Jan 2024) |
| **App-Keep TTU MAU%** | MAU% among TTU who kept app installed — **~87%** (ATH Jan 2024) |
| **M3 / M6 / M12 Retention** | % of NTU cohort still active at 3/6/12 months — on uptrend |
| **Resurrection rate** | DoD rate of lapsed users returning — gap seen beyond Day 5 |
| **DTU** | Daily Transacting User — tracked per product |
| **3.2M** | TTU users who become inactive per month (scale of the resurrection problem) |

### Channel Strategies

| Cohort | Channel | Approach | Key Metric |
|--------|---------|----------|-----------|
| High-active TTU | Push (personalized) | PA Calendar / C-MAB | CTR; no incremental uplift needed |
| Mid/Low-active TTU | Push + ML targeting | PA model targeting (not generic blast) | CTR +6%, DTU +1.3%, Sessions +7% |
| High Potential Inactive (decile 8-10) | WhatsApp | Portfolio Update (WA PU) — personalized market alerts | Rs.75/resurrection; targets AUM>100 |
| High Risk MAU TTU (decile 1-3) | Email + Push | Lower uplift than WA; email has high reachability | Lower resurrection vs WA |
| Push-unreachable inactive TTU | WhatsApp / RCS | Primary channel when PN reachability is near 0 | Brings app opens (not always transactions) |
| All TTU inactive >30D with AUM>100 | WA Portfolio Update | Tue (MF) + Wed (CNC) weekly cron | Rolled out Apr+May/Jun 2024 |

### Key Experiments

| Experiment | TG Definition | Result | Status |
|-----------|--------------|--------|--------|
| **PU Testing (Aug-23)** | Inactive TTU >60D, AUM≥100 | WA: **+23% resurrection**; Email: +2% | WA 1x/month + Email 2x/month going forward |
| **Asia Cup WA (17 Sep)** | Inactive TTU >180D, push-unreachable | TG1 (Pay content) WAU% 1.96%; TG2 (Invest content) WAU% 2.09%. Resurrection CAC: Invest **Rs.181** vs Pay **Rs.287** | Key learning: Invest content wins for resurrection |
| **Product Affinity ML vs RFM (BAU)** | Mid/Low-active TTU | PN CTR +6%, DTU +1.3%, Sessions +7% | Live |
| **WA Portfolio Update (Revive)** | Inactive TTU >30D, AUM>100 | Tested Jan → scaled Apr | Live (weekly cron) |
| **GrowwFlix Email** | 7M users | TTU MAU +100K (1.7%); Non-TTU +26K (0.71%); YT subscribers grew | Scaled |
| **MF Purchase Abandonment** | 4.2L users with buy intent ≥2 clicks L30D | +7,800 lumpsum orders (+5% of new orders); SIP +~2% | Scaled |

### Retention Propensity Model

ML model scoring each TTU user's probability of transacting next month. Splits base into 10 deciles:

| Decile group | Segment | Key traits | Best channel |
|-------------|---------|-----------|-------------|
| 1, 2, 3 (Jan MAU) | **High Risk of churn** | Almost PPI=1; AUM<500; PN reachability >90% | Push (reachable) |
| 8, 9, 10 (Jan Inactive) | **High Potential for resurrection** | Active last 2 months; some AUM; low PN reachability | WA / RCS / Email |

### IPO & SGB Strategy (SOP)

- **IPO targeting**: Intent segments — applied L3M, PP visit >3 L7D, Apply clicked; CTR **4%** for TTU base
- **SGB (Sovereign Gold Bond)**: CTR **3-4.5%** for TTU base; IPO Corner in-app property
- Regulatory: "Pre-apply" NOT allowed in communications (SEBI)

---

## 3. Invest Pod — CNC (Stocks Trading)

> CNC = "Cash and Carry" — the Stocks product for regular equity buy/hold (not intraday/F&O)

**Goal:** Keep CNC TTU users active and discovering relevant stocks. Personalized alert strategy is the core lever.

### People

| Person | Role |
|--------|------|
| **Hritwik Sahay** | CNC personalization analytics — 52W alerts, DMA experiments |
| **Amit Kumar** | Instrument affinity ML model; co-author with Hritwik on CNC alerts |

### CNC Alert CTR Hierarchy (Best to Worst)

All campaigns define intent as: Holdings OR Watchlist OR PP-visits >4 in L7D. Session attribution: 12-min post PN.

| Alert Type | PN CTR | Session Conversion | Notes |
|-----------|--------|--------------------|-------|
| Generic Stocks in Spotlight (BAU) | ~3% | — | Baseline |
| Automated Stock News | 4-7% | 10-35% | Existing personalised |
| Price Alert (±5%) | 3.5-8% | 17-40% | Existing personalised |
| 52W High/Low | **11-13%** | 33-37% | 450K daily reach; expand to Nifty 500 |
| 50 DMA breakout | **11-17%** | 32-45% | SMA-based |
| 150 DMA breakout | **9-14%** | 27-47% | — |
| **200 DMA breakout** | **14-19%** | **40-51%** | **Best performing**; Nifty 100/200 |

**DMA = Daily Moving Average.** 200 DMA = 200-day moving average; crossing it = major technical signal.

### App Source Splits (where CNC NTU comes from)

| Source | Contribution |
|--------|-------------|
| Stocks Explore section | **48% of Groww NTU**, 33% of Cross-sell CNC FID |
| Within Explore: Most Bought/Traded | 76% of Explore NTU |

### CNC Feature Discovery Experiment (Low/Mid Active Users)

Target: CNC TTU who are low/mid active (haven't used alerts/advanced features).
Goal: Increase feature adoption → more engagement → more sessions.
Status: Experiment run; specific results pending deeper write-up.

### Personalization Ladder

```
Generic "Stocks in Spotlight" (3% CTR)
  ↓
Automated Stock News (4-7% CTR)
  ↓
Price Alerts ±5% (3.5-8% CTR)
  ↓
52W High/Low alerts (11-13% CTR)  ← 4X generic
  ↓
50/150 DMA breakout (11-17% CTR)
  ↓
200 DMA breakout (14-19% CTR)    ← Current best
  ↓ Next step
C-MAB to auto-select best alert per user
```

---

## 4. Invest Pod — Personalization

**Goal:** Replace generic campaign blasts with hyper-personalized 1:1 communications at scale. Use ML to send the right product, right instrument, right campaign format, at the right time — for every user.

### People

| Person | Role |
|--------|------|
| **Himanshu Khandelwal** | ML models strategy + F&O TTU instrument affinity |
| **Preksha Vyas** | Product Affinity model for OB/NTU activation |
| **Ritvik Pandey** | MF TTU personalization; MF purchase abandonment |
| **Anshul / Saurabh** | Engineering — on-app MAB Widget Ranker Engine (BFF/tech) |

### ML Models in Production

| Model | What it does | Accuracy / Result | Refresh |
|-------|-------------|------------------|---------|
| **Product Affinity (PA)** | Predicts next-day top 2 products per user | 73% overall; MF 55% weakest; F&O best | Daily |
| **Instrument Affinity** | Predicts top stock/fund user will act on | Top 10 stocks: DAU +3%; Top 50: CTR +23% but NO DAU → paused | Daily |
| **Time Activity Model** | Optimal send time per user | Part of personalization engine | Daily |
| **Retention Propensity** | Probability of transacting next month | Powers high-risk vs high-potential segmentation | Fortnightly |
| **Cross-sell Affinity** | Next best product for single-product TTU users | +3.2% Cross-sell FID vs CG; Pay biggest winner (+23%) | 14D window |
| **C-MAB (Thompson Sampling)** | Selects best PN out of active campaigns per user per slot | V1: 40% CTR uplift + 3% DTU | Continuous |
| **Campaign Affinity** | Selects best campaign format/template per user | V1 (Thompson Sampling): 20% CTR uplift | Continuous |
| **Widget Ranker Engine** | On-app widget ranking for Stocks Explore | V0: 4 widget slots; in progress | Daily |

### C-MAB Architecture

**V1 Reward function: 50% CTR + 50% Transaction rate** (not CTR-only).
Exploration rate: **10%** (explore vs exploit balance).
Industry users: Zomato, Duolingo, LinkedIn, Facebook, Doordash.

```
User opens app / eligible for PN
  ↓
C-MAB selects best campaign from pool
  ↓ Thompson Sampling — prior updated by past rewards
User receives PN
  ↓
Reward signal: did they click? (50%) + did they transact? (50%)
  ↓ Back to model → posterior updated
Next eligible slot → C-MAB selects again
```

5 C-MABs live for TTU; 3 Non-TTU C-MABs in progress.
2D data lag (EMS replacing WebEngage pipeline to reduce to 1D).

### Pipeline Architecture

```
BigQuery (BQ)
  ↓ daily batch
Audience Manager (AM) — user segment assignments
  ↓
WebEngage — campaign orchestration + push delivery
  ↓ via FCM
User Device (Push Notification)
```

### ML Personalization Benchmarks

| Model / Experiment | Result |
|-------------------|--------|
| PA Model vs RFM baseline | PN CTR +6%, DTU +1.3%, Sessions +7% |
| Cross-sell Affinity | +3.2% Cross-sell FID |
| C-MAB V0 | 34% CTR uplift (after warmup) |
| C-MAB V1 | 40% CTR + 3% DTU uplift |
| Campaign Affinity V0 | 10-15% CTR |
| Campaign Affinity V1 | 20% CTR (early reads) |
| F&O TTU Index personalization | PN CTR +6-10%; DAU/Session minimal |
| MF Purchase Abandonment (4.2L) | +7,800 lumpsum orders; SIP +~2% |
| Generic PN click retention decay | 28% week 1 → **5% by week 40** |

### Aampe Evaluation (rejected)

External AI-agentic PN tool evaluated Sep-24.
Architecture: BQ Table → Aampe Engine → WebEngage → User PN.
Swiggy learnings from Aampe: 1 PN/day > 2 PNs; Thompson Sampling >> UCB.
**Rejected:** Cost (POC Rs.21L/month for 20M MAU; post-POC Rs.32L/month) + integration complexity.

---

## 5. Trading Pod (F&O, MTF, MIS, Commodities)

**Goal:** Drive FID and RID for trading-specific products. Keep traders active across sessions.

**Products:** F&O (Futures & Options), MTF (Margin Trade Funding), MIS (Intraday/Margin Intraday Square-off), Commodities.

### People

| Person | Role |
|--------|------|
| **Aastha** | Trading pod strategy (possible vertical lead — positioned above all pods in docs) |
| **Yash** | Trading strategy, 9:15 AM comms, WhatsApp (trading) |
| **Samir** | Communication execution for trading pod |
| **Himanshu Khandelwal** | F&O TTU instrument level affinity (ML); F&O content performance analysis |

### Key Triggers & Timing

- **9:15 AM** = Market open time. Core daily trigger for intraday/F&O users.
- Pre-market, market open, mid-session, end-of-day = 4 distinct comms windows.
- **Morning goal**: Drive DAU (Traders Corner + SGX/Gift Nifty; S&R; Pre-market; Opening Bell)
- **Afternoon goal**: Drive sessions (Index Updates; S&R Alerts; High OI; Top Traded Options; Expiry Alert; RSI/DMA)
- **Personalization**: Open Position Alerts; Index Tx Affinity movement alerts

### F&O Content Performance — By Cohort

| F&O Cohort | What Works | What Doesn't | Best Properties |
|------------|-----------|-------------|----------------|
| High Intent | S&R + OI insights; sentiment-rich | Generic; international | Traders Corner S&R; OI insights; S&R alerts; RSI/DMA |
| Mid Intent | Simplified market alerts | Generic; international | S&R alerts; OI insights |
| Low Intent | Personalized instrument affinity; crisp alerts | Generic; OI insights | Index Tx Affinity movement; S&R alerts |
| Churned | In-depth analysis; pre/during; international works | Short alerts during market | Traders Corner SGX; S&R alerts |
| Beginners | Crisp detailed alerts pre/during; high intent focus | Generic; international | Options with High OI; S&R Alert |

**Finding:** "Properties providing more insights on market trend or market sentiment perform better for High/Mid intent vs generic updates."

**Way forward:** Automate S&R alerts in in-house Campaign Manager; bring Traders Corner on-app; test VIX + DMA for High/Mid intent; F&O educational flow post D7 onboarding.

### NARAD F&O Data Signals (Live Triggers)

These derived attributes power 20+ automated F&O campaigns:

| Signal | Definition |
|--------|-----------|
| **PCR (Put-Call Ratio)** | PCR >1 = bearish; PCR <1 = bullish. Tracked as point-in-time + % change from day start |
| **ATM straddle** | At-The-Money options straddle price = market volatility expectation signal |
| **OI (Open Interest)** | Total open contracts; surge/drop = significant market activity |
| **Strike rank** | Distance from spot price to ATM; filters near-ATM contracts |
| **Long buildup** | OI↑ + Price↑ → bulls adding fresh positions |
| **Short buildup** | OI↑ + Price↓ → bears adding fresh positions |
| **Covering** | OI↓ + Price↑ → short sellers closing |
| **Unwinding** | OI↓ + Price↓ → long holders exiting |

Pipeline: Kafka + Spark stateful streaming → master_tables schema → <1 day for new derived attributes.

### F&O Regulatory Constraints (Responsibility Charter)

| Date | Event |
|------|-------|
| Dec-23 | Responsibility Charter discussions (SEBI-aligned responsible broker policy) |
| Jan-24 | **F&O cross-sell paused** — stopped cross-selling F&O to non-F&O TTU base |
| Mar-24 | **F&O cross-sell restarted** — ONLY for F&O onboarded users + F&O affinity users |
| Post Mar-24 | F&O NTU share declining M/M but not proportionally (organic conversions continue) |

### MTF (Margin Trade Funding) GTM

3-part strategy:
1. Drop-off journey for users who discovered MTF but didn't activate
2. Nudged discovery for focused cohort (F&O users most likely)
3. [Part 3 = visual in PDF — not fully extractable]

### F&O Personalization Experiment

- Target: F&O TTU users; personalize by which index (Nifty/BankNifty/etc.) user trades most
- Result: PN CTR +6-10%; User CTR +6-9%; DAU/Session minimal (comms → app opens, not always trades)
- Mid/low intent users benefit most; high-intent self-direct

### App Source Splits (F&O)

| Source | Contribution |
|--------|-------------|
| Explore | Very low |
| Positions + Index Cards | Primary drivers of F&O sessions |

---

## 6. Pay Pod

**Goal:** First Pay transaction (Pay FPD) and Pay user retention. Cross-sell between Pay and Invest.

### Key Metrics

| Metric | Value |
|--------|-------|
| Pay discovery rate (June→July trend) | 33% → ~50% (improving) |
| TTU resurrection: Invest content CAC | **Rs.181** (cheaper than Pay content Rs.287) |
| Non-TTU resurrection CAC (Pay content) | **Rs.65** (vs Invest content Rs.270) |
| Pay FPD CAC (Pay content) | **Rs.5,284** |
| Pay FPD CAC (Invest content) | Rs.21,021 (much worse for Pay FPD specifically) |
| Pay discovery (resurrected users) | Only **1/3** visit Pay (default landing = Invest page) |
| UPI CAC vs Bill rewards CAC | UPI = **half** of Bill rewards |
| PreLoad vs Regular Cashback | PreLoad wins: higher WAU conversion + Pay Onboarding + Pay FPD |

### Resurrection Campaign Results (Rakhi + UPI Rewards + Bill+Invest)

| Insight | Finding |
|---------|---------|
| TTU resurrection | Invest content > Pay content (resurrect the user first, then cross-sell Pay) |
| Non-TTU resurrection | Pay content wins: CAC Rs.65 vs Invest Rs.270 |
| BBPS FPD vs UPI FPD | BBPS FPD much more expensive |
| Default landing fix needed | Enable Pay landing for Pay reward campaigns (currently defaults to Invest page) |

### Retention Strategy Framework

| Cohort | Problem | Strategy |
|--------|---------|----------|
| BBPS Non-Bill (Fastag, MR) | No auto bill reminders generated | Category-based approach; split by amount |
| BBPS Bill Category | Users pay more near bill generation date than due date | Experiment around bill generation date (not due date) |
| UPI users | Generic comms | **MCC Code**-based targeting by merchant type |
| Unused Cashback holders | Cashback unused >3 months | Awareness → bill payment with unused balance |
| All users (activity) | Not using Groww UPI as primary | Nudge to link mobile number → incoming payments in Groww |
| Pay Only users | Never explored Invest | Cross-sell nudge to start investing |

---

## 7. Feed & Content Pod (NC / Stories)

> Feed = Notification Center (NC) — same product, two names. Pull product inside the app.

**Goal:** Make the in-app content feed a habit-forming engagement surface for TTU users.

**Owner:** Ritvik Pandey (Feed personalization strategy with NARAD)

### Feed / NC Metrics

| Metric | Value |
|--------|-------|
| Feed avg WAU | **243K** |
| Feed avg DAU | **104K** |
| Feed weekly visit retention | **33%** |
| % NC visitors who are TTU | **93%** (non-TTU almost absent) |
| F&O MAU visiting NC | **28%** (highest product engagement) |
| CNC MAU visiting NC | **14%** |
| MF MAU visiting NC | **7%** (MF = very static content) |
| Feed content mix | Macro/Market 45%, Opportunities 25%, Personalized 18%, Personal Finance 12% |

**Problem:** Personalized content = only 18% of impressions despite being highest-quality. Feed is "running at half potential."

### Content Strategy by User Type

| User Type | Content that works | Content to avoid |
|-----------|-------------------|-----------------|
| F&O TTU | Market data, OI analysis, position-specific updates | Generic market overviews |
| CNC TTU | Stock-specific price/technical alerts | Generic market sentiment |
| MF TTU | Portfolio performance, fund news | General market noise |
| Non-TTU | Basic investor education | Advanced product content |

### NARAD Personalization Phases (Feed)

| Phase | Properties |
|-------|-----------|
| **Phase 1** | Portfolio Analysis, Alert Properties, Benchmarking, Interested Stocks Newsletter, Brokerage Outlook |
| **Phase 2** | Fundamentals Data, Portfolio Health Report |

**NARAD CDP limitation:** Text-only personalization. No personalized images at scale. Constrains how rich Feed content can be per user.

### Stories — Rf Score Model

**Rf (Random Forest) score** predicts D1 retention of each Story (R²=0.254; beats linear regression R²=0.174).

| Feature | Weight | What it signals |
|---------|--------|-----------------|
| Skip Rate | **0.24** | Most punishing signal — users voting with swipes |
| Normalized Completion | 0.23 | Adjusted for slide count (expected = 0.9297 - 0.0344 × slides) |
| Unified Action Rate | 0.18 | MAX(Deeplink Click%, Share%) |
| Weighted Time | 0.16 | P50×0.1 + P75×0.2 + P90×0.3 + P95×0.4 (weights for engaged users) |
| Screenshot Rate | 0.13 | Save-worthy signal |
| Slide Count | 0.06 | Fewer = better |

**Tiers:** A ≥ 0.325 | B 0.262–0.324 | C < 0.262
**Optimal story length:** 3-6 slides (7-10 → completion rate drops).
**248 stories scored.** Median score 0.288, mean 0.299.

---

## 8. Cross-sell (Cross-Pod Initiative)

**Goal:** Get single-product TTU users to their first transaction in a second product (CNTU).

### Key Finding: Discovery ≠ Problem

| Metric | Value |
|--------|-------|
| Ever discovered products/user (TTU MAU) | 2.4 / 3 (excl. Loans/Pay) |
| Monthly discovered products/user | 2 / 3 |
| Bottom Nav products ever discovery | ~100% (MF, Stocks universal) |
| F&O discovery rate | Considerably lower (not Bottom Nav) |
| Comms can improve discovery by | ~10% (small marginal opportunity) |

**The real problem is conversion, not discovery.** Most TTU have explored products they haven't transacted in. Strategy: ML to identify and convert high-intent undecided users.

### Key Metrics

| Metric | Definition | Benchmark |
|--------|-----------|-----------|
| **CNTU** | Cross-sell NTU — first transaction in 2nd product | NTU → CNTU within 3M: **~70%**; within 24M: **~80%** |
| **Active PPU** | Active transacting user products / active user | Current metric — stable + actionable |
| **PPU (old)** | Products transacted ever / TTU | Deprecated — market-driven fluctuation |
| **CrossSell FID** | FID in second product | +3.2% via Cross-sell Affinity ML |

### Next Best Product Experiment Results

**Setup:** ML Cross-sell Affinity model; all L30D Active TTU; +1 PN/day frequency (cross-sell on top of PA calendar). TG = 3.1M; CG = 3.1M. 8-21 Dec.

| Metric | Result |
|--------|--------|
| Cross-sell conversion | **+4%** (significant) |
| Cross-sell product DAU | **+3%** |
| Overall DAU / Sessions | Flat (users redirected, not net new) |
| DND (push opt-out) | +2% (insignificant) |
| PN CTR | **-10%** (expected — more targeted = lower raw CTR) |
| User CTR | **+8%** (right users clicking) |

**Product-wise uplift:**

| Product | Uplift | Notes |
|---------|--------|-------|
| **Pay** | **+23%** | Biggest winner |
| F&O | +2% | Model accuracy weakest for F&O |
| Stocks | +1.5% | — |
| MF | +1% | — |

**By PPI:**
- PPI=1 users: marginal CS uplift + **huge DND spike** ⚠️ — not safe to target aggressively
- PPI>1 users: sharp CS uplift + no DND ✅

**By NTU recency:** Best cross-sell uplift: 12M+ NTU or very recent NTU (< 1M). Trough: 2-3M NTU.

**Next steps:** Improve F&O model; roll out on PPI>1 + high-engagement only; optimize cool-off period.

---

## 9. Shared Infrastructure

Infrastructure and tools used across all pods.

### GCG (Global Control Group)

Permanent holdout from promotional comms (only transactional messages). Baseline for measuring incremental lift.

| Lifecycle stage | GCG size | Notes |
|----------------|---------|-------|
| New users (Activation pod) | 2-5% | Smaller CG to maximize learning |
| Active users (RID pod) | 5-10% | Larger CG for cleaner measurement |
| Churn-risk users (Retention/resurrection) | 5-8% | — |
| Overall blended average | **~5%** | This is the figure cited in most campaign docs |

30-day holdout window. Incremental uplift = TG metric vs GCG metric.

### Attribution Model

| Method | When to use | Platform |
|--------|------------|---------|
| MTA (Multi-Touch Attribution) | Long-window conversions: NTU, CNTU, Reactivation, Cross-sell | Adobe Omniture |
| Time-decay | Recommended for Groww by attribution doc | Adobe Omniture |
| Last-click | Simpler measurement; short conversion windows | WebEngage native |
| First-click | Brand awareness campaigns | — |

### NARAD — In-house CRM

Real-time event streaming pipeline. Self-serve model for business team (no DP team for new attributes).

```
Kafka (event streaming: fo_feed, indices_v3, derived_contract_master, screener_underlying_details)
  ↓
Spark stateful structured streaming (joins multiple sources)
  ↓
master_tables schema (Contract master, Index master, ATM master)
  ↓
Campaign eligibility engine → WebEngage → User
```
**20+ F&O campaigns automated.** Next: replicate for CNC + MF.

### Channel Infrastructure

| Channel | Platform | Key Stats |
|---------|---------|-----------|
| Push Notifications | WebEngage → FCM | 250K/min throughput (upgraded); FCM bottleneck |
| Email | WebEngage → Netcore | 10M/hr (upgraded from 2.2M/hr); 18-20% open rate |
| WhatsApp | COSMOS journey system | BIC: 73p/msg; UIC: 33p/msg |
| In-app Stories | Custom | Scored via Rf model |
| RCS | External | Aishwarya — rich SMS alternative |
| Remarketing | Google/FB ads | ~30% of L150D+ MAU |

### Data Pipeline

```
BigQuery (warehouse)
  ↓ daily
Audience Manager (segmentation)
  ↓
WebEngage (campaign orchestration)
  ↓
FCM / Netcore / WA API (delivery)
  ↓
EMS (Event Management System — replacing WE data pipeline for C-MAB data lag reduction)
```

### Measurement Cadences

| Cadence | Doc | Frequency |
|---------|-----|-----------|
| WBR | UE Weekly Business Review | Weekly |
| MBR | Monthly Business Review | Monthly |
| Campaign reports | Comms 360 dashboard | Real-time + weekly |
| Experiment reads | GCG-based incremental uplift | Post-experiment (typically 2-4 weeks) |

---

*Cross-reference with `Growth Vertical - Master Reference.md` for exhaustive metric tables, benchmark numbers, and tool details.*
