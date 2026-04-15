# Groww Growth Vertical — Master Reference

> **Living document.** Updated as context is shared. Source of truth for people, pods, metrics, tools, channels, and workflows.
> Last updated: 2026-03-26 (v2 — audit pass, 10 gaps filled)

---

## Table of Contents

1. [Vertical Overview](#1-vertical-overview)
2. [Pod Structure](#2-pod-structure)
   - 2a. [Invest Pod — Activation](#2a-invest-pod--activation-sub-pod)
   - 2b. [Invest Pod — RID (Repeat Investment)](#2b-invest-pod--rid-repeat-investment-sub-pod)
   - 2c. [Invest Pod — Personalization](#2c-invest-pod--personalization)
   - 2d. [Trading Pod](#2d-trading-pod)
   - 2e. [Other Businesses Pod](#2e-other-businesses-pod)
3. [People Directory](#3-people-directory)
4. [Key Metrics & Definitions](#4-key-metrics--definitions)
5. [User Funnel](#5-user-funnel)
6. [Channels & Communication Types](#6-channels--communication-types)
7. [Tools & Systems](#7-tools--systems)
8. [Audience / Cohort Workflow](#8-audience--cohort-workflow)
9. [Open Questions](#9-open-questions)

---

## 1. Vertical Overview

**Vertical name:** User Engagement (UE) / Growth

**What it does:** Drives user acquisition, activation, and retention across all Groww products through targeted communications, personalization, and lifecycle management.

**Two primary KPI clusters:**
- **Activation (0→1):** Getting registered/KYC-done users to make their first investment (FID)
- **Retention & Repeat (1→N):** Keeping users transacting across products (RID)

**Pod structure:**

| Pod                  | Sub-pod         | Core Focus                         | Products                              |
| -------------------- | --------------- | ---------------------------------- | ------------------------------------- |
| **Invest**           | Activation      | 0→1: KYC → First Investment (FID)  | MF, Stocks, Gold, FDs, IPO, US Stocks |
| **Invest**           | RID             | Repeat transactions after FID      | CNC, ETF, Bonds, IPO, MF              |
| **Invest**           | Personalization | ML-driven hyper-personalized comms | All invest products                   |
| **Trading**          | —               | FID + RID for trading products     | FnO, Commodities, MTF, MIS (Intraday) |
| **Other Businesses** | —               | Growth for wealth & AMC products   | Wealth (Fisdom), Groww AMC            |

**Key dashboards:**
- **User Engagement Dashboard** — top-level UE metrics
- **Comms 360** — cross-channel communication performance

**Key docs:**
- UE Projects (work tracker)
- **UE Weekly Business Review Docs (WBR)** — reviewed weekly
- Monthly Business Review (MBR) — monthly reporting cadence

---

## 2. Pod Structure

### 2a. Invest Pod — Activation Sub-Pod

**Goal:** Convert KYC-done users into first-time investors (FID). Covers the full 0→1 journey.

**Funnel:** 7-8 step KYC onboarding charter → First Investment Done

| Role | Person | Responsibility |
|------|--------|---------------|
| Strategy — Activation | Nikhil | Overall activation strategy, experiment design |
| Strategy — Invest & Instigate | Shweta | Campaign strategy to nudge users toward first investment |
| Execution | Aishwarya | Communication execution (building/sending campaigns) + channels: RCS, SMS, Stories |
| Overall Invest Pod Ownership | Amit | *See disambiguation below* |

> **Amit disambiguation:** "Amit - does the full then" appears in the notes after the Trading pod description. Two possible readings:
> - **Reading A:** Amit owns the **full Invest pod strategy** (across Activation + RID + MF), contrasted with Trading where strategy is split between Aastha + Yash
> - **Reading B:** Amit does QA/review for the full Invest pod output before execution
> → *Confirm with Amit or Nikhil.*

**Key metrics for this pod:**
- **FID** — First Investment Done (primary conversion goal)
- **NTU** — New Transacting User (activation tracking end-point)
- **D0/D1 tags** — Compound milestone labels, not raw day numbers. Format: `D{N}_{milestone}_from_{origin}`. D0 and D1 both refer to the signup/account creation day. E.g., `D1_onboarding_from_signup`, `D1_NTU_from_signup`. More tag names TBD as data is shared.
- **D7** — % of a signup cohort who reach a milestone by Day 7 (time-bounded activation signal — distinct from D0/D1 tag system)
- **MBR / WBR** — Monthly + Weekly Business Review reporting
- **Onboarding %** — Step-by-step completion rate through the 7-8 step funnel

> **"till NTU"** in the notes suggests the Activation pod tracks metrics **up to the point a user becomes an NTU** — i.e., NTU is the activation endpoint, not just a metric.

**Ask Nikhil:** for deeper context on activation strategy and D7 specifics.

---

### 2b. Invest Pod — RID (Repeat Investment Sub-Pod)

**Goal:** Keep existing investors transacting. Drive repeat investments across products.

**Products covered:** CNC, ETF, Bonds, IPO, Mutual Funds (MF)

| Role | Person | Responsibility |
|------|--------|---------------|
| Strategy | Nikhil & Himanshu | RID strategy across CNC, ETF, Bonds, IPO, MF |
| Strategy — MF | Amit | MF-specific repeat investment strategy (and possibly full Invest pod ownership) |
| Execution / Comms Orchestration | Shweta | Communication orchestration and execution for RID |

**How RID works:**
- **TTU** — activity cut + transaction cut used to define "lapsed" vs "active" cohorts
- Campaigns are **hyperpersonalized** based on day-to-day market trends and user behavior
- Communication is orchestrated across channels (push, email, WhatsApp, etc.)

**CrossSell FID logic:**
- User has done FID in one product → strategy to move them to their first investment in another product
- e.g., MF investor → nudge toward Stocks FID, or Stocks investor → ETF FID
- Different strategies designed for each segment and product combination
- Goal: increase the **total transaction base** of each product

---

### 2c. Invest Pod — Personalization

**Goal:** Replace generic blasts with hyper-personalized comms at scale.

**Primary signal source:** App activity ("App ac" = App activity — what users do in the app drives the personalization engine)

**Two layers:**

| Layer | Type | Description |
|-------|------|-------------|
| Generic | Broadcast | Same message to all or broad segments |
| Personalized | Individual | Based on user-specific signals (holdings, watchlist, ML outputs) |

**Personalization signals (Personalized layer):**
- **Holdings** — what the user already owns
- **Watchlist** — what they're tracking but haven't bought
- **ML model outputs** (see below)

**ML Models (2-3 models total):**

| Model | Signal Used | Output |
|-------|------------|--------|
| Product affinity model | App activity → predicts which 2 products user is most likely to transact in next day | 2 product recommendations per user |
| Instrument affinity model | App activity → which specific stock/fund/bond the user is most likely to act on | Top instrument recommendation |
| Time activity model | App usage patterns → when the user is most active | Optimal send time per user |
| **Combined output** | All three models → | Top stock/instrument + right time = personalized daily nudge |

**Owners:** Himanshu (ML models — ask for more context), Nikhil (strategy/application)

---

### 2d. Trading Pod

**Goal:** Drive FID and RID for trading-specific products. Keep traders active and engaged.

**Products:** FnO (Futures & Options), Commodities, MTF (Margin Trade Funding), MIS (Intraday / Margin Intraday Square-off)

| Role | Person | Responsibility |
|------|--------|---------------|
| Strategy | Aastha & Yash | Overall trading pod strategy |
| Market-open comms (9:15) | Yash | Pre-market and opening bell nudges |
| WhatsApp (Trading) | Yash & Nikhil | WhatsApp campaign execution for traders |
| Execution | Samir | Communication execution for trading pod |

**Key concepts:**
- **9:15 AM:** Market open time. Core daily trigger for intraday and F&O users.
- **"915 new app"** (from Excel): Likely refers to either a new product/feature called "915" (a pre-market or opening experience) OR simply the 9:15 AM timing trigger. *Clarify — it may be an internal product name.*
- **FID (Trading):** Getting a Groww user to make their first FnO / Commodity / MTF / MIS trade
- **RID (Trading):** Keeping traders active and returning across sessions
- **CrossSell FID:** Moving an invest user to their first trading product, or cross-selling between trading products
- Strategies differ by segment (experienced trader vs. first-time options buyer vs. intraday curious)

---

### 2e. Other Businesses Pod

**Goal:** Growth and engagement for non-core invest/trading products.

**Products covered:**
- **Wealth (W)** — high-ticket investment advisory (Fisdom partnership)
- **Fisdom** — wealth management platform (Groww-acquired)
- **Groww AMC** — Groww's own Asset Management Company (mutual fund schemes)

> *Context pending — to be filled in.*

---

## 3. People Directory

| Name | Pod | Role | Owns | Notes |
|------|-----|------|------|-------|
| **Aastha** | *Possibly vertical lead?* | Strategy (Trading) | Trading pod strategy (with Yash) | ⚠️ Listed at the very top of notes before any pod description — may be team/vertical lead, not just Trading pod. *Confirm seniority and scope.* |
| **Nikhil** | Invest (Activation + RID) | Strategy | Activation strategy, WhatsApp channel manager, RID strategy (with Himanshu) | |
| **Shweta** | Invest (Activation + RID) | Strategy + Execution | Invest & Instigate strategy, Communication Orchestration for RID | |
| **Himanshu Khandelwal** | Invest (Activation + RID + Personalization) | Strategy + ML | Activation & Invest scope (confirmed from notes); RID strategy all products; ML personalization models (F&O TTU instrument affinity); F&O TTU content performance analysis; Email infra | Full name confirmed in Batch 9 F&O doc. Notes say "Himanshu → Activation & Invest (which includes)" — broader scope than previously recorded |
| **Amit** | Invest | Strategy | MF-specific RID + possibly full Invest pod ownership | ⚠️ Role unclear — see disambiguation in §2a |
| **Aishwarya** | Invest (Activation) + Shared? | Execution | Campaign execution, RCS, SMS, In-app Stories | ⚠️ "Stories bhi" (Hindi: "Stories also") — suggests she handles these channels across pods, not just Activation |
| **Yash** | Trading | Strategy + Channel | Trading strategy, 9:15 comms, WhatsApp (with Nikhil) | |
| **Samir** | Trading | Execution | Trading pod comms execution | |
| **Preksha Vyas** | Invest (Personalization) | ML/Analytics | Product Affinity model for OB/NTU activation (segment personalization) | Confirmed author of Batch 4 PA doc |
| **Ritvik Pandey** | Invest (RID — MF) + Feed | Analytics | MF TTU personalization — purchase abandonment funnel; Feed Personalisation Strategy with NARAD | Confirmed author of Batch 4 MF TTU doc and Batch 6 Feed doc |
| **Anshul / Saurabh** | Tech/ML | Engineering | On-app MAB Widget Ranker Engine tech implementation | Mentioned in C-MAB Part 2 for BFF/tech flow |
| **Hritwik Sahay** | Invest (RID — CNC) | Analytics | CNC 52W alert personalization experiments | Co-author with Amit Kumar on CNC 52W alert doc |
| **Juie Shah** | Invest (Activation?) | Execution | Push notification engagement experiments (co-author: PN Banners experiment) | |
| **Shivam Chopra** | Analytics | Analytics | Data analytics for push campaigns | Mentioned in Push Throughput doc |

> *Designations, seniority, and reporting lines — to be confirmed and added.*

---

## 4. Key Metrics & Definitions

### User State Metrics

| Metric | Full Form | Definition | Pod |
|--------|-----------|-----------|-----|
| **FID** | First Investment Done | User's first transaction on any Groww product | Activation, Trading |
| **RID** | Repeat Investment Done | Second+ transaction — habit signal | RID, Trading |
| **NTU** | New Transacting User | User who transacted for the first time in a period; the **endpoint** of Activation | Activation |
| **TTU** | Total Transacting Users | All users who have crossed both activity AND transaction thresholds — the "active investor" definition. Used as the core engaged-user base for RID campaigns. | RID, All |
| **CNTU** | Cross-sell NTU | First transaction in a second/new product by an existing investor (Cross-sell NTU) | RID, CrossSell |
| **DTU** | Daily Transacting User | Users who transact on a given day — tracked per product (Stocks DTU, MF DTU, etc.) | RID, Trading |
| **MTU** | Monthly Transacting User | Users who transact at least once in a month — used in the Active PPU formula | All |
| **ATU** | Active Transacting User | User with AUM > 0 in a product — defines "active" for invest products | RID |
| **DAU** | Daily Active User | Users who open the app on a given day | All |
| **MAU** | Monthly Active User | Users who open the app at least once in a month | All |

### Cross-sell Metrics

| Metric | Definition | Notes |
|--------|-----------|-------|
| **PPU (old)** | Products Transacted Ever (TTU) / TTU | Deprecated — fluctuates with market conditions |
| **Active PPU (current)** | Active transacting user products per user / Active user | **Recommended metric.** Counts distinct products where user is actively transacting. More stable and actionable. |
| **CrossSell FID** | FID in a second product by an existing single-product investor | Tracked per product transition (e.g., MF → Stocks, CNC → MF) |

**Active PPU product scope** (as of Oct 2023): Stocks (Intraday/cash), F&O, MF, Credit/Loans, UPI payments, BBPS (bill payments), Insurance.

### Retention Metrics

| Metric | Definition | Benchmark (Jan 2024) |
|--------|-----------|---------------------|
| **TTU-MAU% Retention** | % of TTU in month M who also transact in month M+1 | ~73% (up from ~70%) |
| **App-Keep TTU MAU%** | MAU% among TTU who kept app installed | ~87% (ATH as of Jan 2024) |
| **M3 / M6 / M12 Retention** | % of NTU cohort still active at 3/6/12 months | On uptrend (Jan 2024) |
| **Resurrection rate** | DoD (Day on Day) rate at which lapsed users come back | Gap seen beyond Day 5 (Jan 2024 vs Dec 2023) |
| **App Affinity** | DAU/MAU ratio — measures depth of user engagement | Higher = user visits more frequently |

### Campaign Measurement Metrics

| Metric | Definition |
|--------|-----------|
| **GCG** | Global Control Group — permanent holdout from all promotional comms (only transactional messages). 30-day holdout window. Baseline for measuring incremental uplift. GCG size varies by lifecycle stage: **2-5% for new users** (Activation pod), **5-10% for active users** (RID pod), **5-8% for churn-risk users** (Retention/resurrection). The "5%" figure cited in campaign docs is the overall blended average, not a single fixed rate. |
| **Incremental uplift** | Lift in metric (DAU, DTU, NTU) for treatment group vs GCG |
| **MTA** | Multi-Touch Attribution — for conversion objectives with long windows (NTU, CNTU, Reactivation, Cross-sell) |
| **CTR** | Click-Through Rate — clicks on a message / messages delivered |

### Business Review Cadences

| Term | Meaning |
|------|---------|
| **WBR** | Weekly Business Review |
| **MBR** | Monthly Business Review |
| **JAS** | Jul-Aug-Sep quarter |
| **OND** | Oct-Nov-Dec quarter |
| **JFM** | Jan-Feb-Mar quarter |

### Notable Campaign Benchmarks (from docs)

| Campaign type | CTR / Uplift | vs Baseline |
|--------------|-------------|------------|
| Generic campaigns | ~3% CTR | baseline |
| 52W H/L personalised alerts | **12% CTR** | **4X generic** |
| Personalised comms (TTU) | Peak DAU uplift **+11%** | vs GCG |
| Non-TTU comms (day 15) | DAU **+55-60%**, NTU **+75%** uplift | vs GCG |

### Pay Pod — Resurrection Experiment Benchmarks (Batch 12)

Three Pay resurrection experiments ran in Aug-Sep (Rakhi, UPI Rewards, Bill+Invest):

| Insight | Value |
|---------|-------|
| **TTU resurrection** | Invest content > Pay content (better resurrection rate) |
| **Non-TTU resurrection CAC** | Pay: **Rs.65** vs Invest: **Rs.270** (Pay much cheaper for non-TTU) |
| **PreLoad vs Regular Cashback** | PreLoad wins: higher WAU conversion, Pay Onboarding conversion, Pay FPD |
| **UPI cashback vs Bill rewards CAC** | UPI CAC = **half of Bill rewards** CAC |
| **BBPS FPD CAC vs UPI FPD CAC** | BBPS FPD much more expensive than UPI FPD |
| **Pay Discovery rate (resurrected users)** | Only **1/3** of resurrected base visits Pay (default landing = Invest page) |
| **Fix needed** | Enable Pay default landing for Pay reward campaigns to improve Pay discovery |

### Pay Pod — Retention Strategy Framework (Batch 12)

| Cohort | Problem | Strategy |
|--------|---------|----------|
| BBPS Non-Bill (Fastag, MR) | No auto bill reminders generated | Category-based approach; split by amount |
| BBPS Bill Category users | Users pay more near bill generation date than due date | Experiment around bill generation date (not due date) |
| UPI users | Generic comms; low contextual relevance | **MCC Code**-based targeting by merchant type |
| Unused Cashback holders | Cashback unused >3 months | Awareness campaign → bill payment with unused balance |
| All users | Generic persona | Build cohorts by Profession, age, income, area |
| All users (activity retention) | Not using Groww UPI as primary | Nudge to link mobile number to Groww UPI → incoming payments land in Groww |
| **Pay Only users** | Never explored Invest | Cross-sell nudge to start investing |

### WhatsApp vs Email — Resurrection Benchmarks (Batch 11)

| Experiment | WA uplift | Email uplift | Notes |
|-----------|-----------|-------------|-------|
| **PU Testing (Aug-23)** — Inactive TTU >60D, AUM≥100 | **+23% resurrection** | **+2% resurrection** | Portfolio Update; WA wins decisively; WA 1x/month + Email 2x/month going forward |
| **Asia Cup WA (17 Sep)** — Inactive TTU >180D, PN-unreachable | Invest content > Pay content | — | Breakout Stocks (Invest content) outperformed Bill Rewards (Pay content). Exact results: TG1 (Pay content) WAU% 1.96%; TG2 (Invest content) WAU% 2.09%. Resurrection CAC: Invest content **Rs.181** vs Pay content **Rs.287**. Pay FPD CAC: Pay content Rs.5,284 vs Invest content Rs.21,021. Key insight: Invest content cheaper for resurrection; Pay content cheaper if Pay FPD is the goal. 1-day experiment. |

**Key insight:** WA dramatically outperforms Email for driving inactive user resurrection (~10-12x gap on uplift). Email interacts with inactive users (40% open rate) but doesn't convert them back to the app.

### Tax Calendar Engagement — FY-End Hook (Batch 11)

- **Tax loss harvesting**: selling holdings at a loss to offset capital gains tax liability
- **Target base**: Users with unrealized losses on stock holdings
- **STCG** (Short Term Capital Gains): 15% tax on gains from stocks/equity MF held < 1 year
- **LTCG** (Long Term Capital Gains): 10% tax on gains held > 1 year; first Rs 1L/year tax-free
- **Example**: User with Rs 1L STCG (owes Rs 15K) + Rs 60K unrealized loss → sell loss → net STCG = Rs 40K → tax = Rs 6K → **Rs 9K saved**
- **Channel plan**: Email + Push (awareness generic) → In-app Stories (personalized P&L data with actual loss amounts)
- **Timing**: FY-end cycle (Jan-Mar); Mar deadline creates urgency

### WhatsApp Channel Benchmarks (from docs)

| Use case | Result |
|---------|--------|
| WA + PN+Email+SMS at Esign step | **30%** conversion uplift in TG vs CG → Made live |
| WA + PN+Email+SMS at IFSC→BV step | 4% conversion uplift → NOT live (too small, adds Rs.20 to Rs.44 CAC) |
| WA Esign onboarding journey | ~200 incremental Esigns/day; **₹145** cost per incremental conversion |
| WA for inactive non-OB users (reactivation) | FID CAC = **1/5th** of remarketing CAC |
| WA for inactive OB users (reactivation) | FID CAC = **1/10th** of remarketing CAC |
| Push reachability — L150D+ inactive base | **~1.5%** (vs ~50% for active base) |
| Industry WA frequency | 1 WA/week (major brands), 2/week (Swiggy), 1 per 14D (most fintech) |

### Scale-up Non-TTU Reactivation — Cohort-Level Results (WA + Remarketing)

Experiment: D30+ inactive non-TTU users. TG split into Engagement (WA) + Remarketing (Invest+Pay). WA freq: 3/month. Duration: 1 month.

| Cohort | Channel | Metric | Uplift |
|--------|---------|--------|--------|
| **D90-180 Onboarded** | Remarketing | FID uplift | **+5.43%** |
| **D90-180 Onboarded** | Activity | Activity uplift | **+15.82%** |
| **D30-90 WA** | WA | Activity uplift | **+7.10%** |
| All inactive | WA | NTU uplift | Not statistically significant (experiment maturing) |

**Key insight:** Remarketing is more effective than WA for FID conversion in the onboarded D90-180 cohort. WA drives activity (app opens) but not necessarily transactions for this base.

### NTU → CNTU Conversion Benchmarks

| Milestone | Rate |
|----------|------|
| NTU → CNTU within 3 months | **~70%** |
| NTU → CNTU within 24 months | **~80%** |

### Email Channel Benchmarks

| Metric | Benchmark |
|--------|-----------|
| Email delivery rate | **99%** |
| Email open rate (overall) | **18-20%** |
| Daily Digest scale | 15M users (as of Nov-22 project) |
| Daily Digest MAU (peak) | 13M (Oct-24) |
| Daily Digest MAU (Mar-25) | **8M** (declining) |
| Weekly Digest target (after optimization) | 11M (from 24M); same 2.1M opens |
| Monthly email cost saving post optimization | Rs.7-8L/month |
| Email throughput (Netcore, post-upgrade) | 10M/hr (from 2.2M/hr) |
| Open rate improvement from timely delivery | **+2-2.5%** |
| GrowwFlix open rate | **30%** (at 7M users) |
| GrowwFlix TTU MAU uplift | **+100K (1.7%)** |
| GrowwFlix Non-TTU MAU uplift | **+26K (0.71%)** |
| Monthly unique Digest open rate (TTU) | ~60% |
| Monthly unique Digest open rate (Non-TTU) | ~55% |

### Push Channel Benchmarks

| Metric | Benchmark |
|--------|-----------|
| WebEngage push throughput (pre-upgrade) | 75K/min |
| WebEngage push throughput (post-upgrade) | **250K/min** |
| WebEngage → FCM latency improvement | **50% reduction** |
| Net push DAU attribution improvement | **+0.5-0.6% daily** |
| Push banners CTR uplift | No major uplift (industry claim of 60% did NOT hold) |
| Peak push time (after throughput upgrade) | 9:30am, 1:00pm, 4:00pm (shifted earlier) |

### F&O TTU Content Performance — What Works by Cohort (Batch 9)

F&O push properties are structured by time-of-day goal:
- **Morning** (drive DAU): Traders Corner + SGX/Gift Nifty; Traders Corner + S&R; Pre-market Open; F&O Opening Bell
- **Afternoon** (drive sessions): Index Updates; S&R Alerts; High OI Info; Top Traded Options; Expiry Alert; RSI/DMA updates
- **Personalization** (drive sessions): Open Position Alerts; Index Tx Affinity-based movement alerts

| F&O Cohort | What Works | What Doesn't | Best Properties |
|------------|-----------|-------------|----------------|
| **High Intent** | Detailed S&R + OI insights; sentiment-rich content | Generic updates; international market updates; instrument affinity volatile | Traders Corner S&R; OI insights; S&R alerts; RSI/DMA |
| **Mid Intent** | Simplified market alerts/updates | Generic; international | S&R alerts; OI insights |
| **Low Intent** | Personalized instrument affinity; crisp alerts | Generic; international; OI insights | Index Tx Affinity movement alerts; S&R alerts |
| **Churned** | In-depth analysis; pre/during market; international updates work | Short alerts during market | Traders Corner SGX; S&R alerts |
| **Beginners** | Crisp detailed alerts pre/during market; high intent | Generic alerts; international | Options with High OI; S&R Alert |

**Key finding:** "Properties providing more insights on market trend or market sentiment are performing better for High/Mid intent users as compared to generic market updates."

**Way forward:** Automate S&R alerts in in-house Campaign Manager; bring Traders Corner on-app; test VIX + DMA variations for High/Mid intent; F&O educational flow post D7 onboarding.

### Regulatory Context: Responsibility Charter & F&O Targeting

| Event | Date | Impact |
|-------|------|--------|
| **Responsibility Charter discussions** | Dec-23 | SEBI-aligned responsible broker policy; affects F&O marketing targeting |
| **F&O cross-sell paused** | Jan-24 | Stopped cross-selling F&O to non-F&O TTU base |
| **F&O cross-sell restarted** | Mar-24 | Restarted but ONLY for F&O onboarded users + F&O affinity users |
| **Activation funnel F&O targeting** | Mar-24 | Shifted to Product Affinity-based segmentation; only F&O affinity users get F&O promotional comms |
| **F&O NTU trend** | Post Mar-24 | F&O NTU share declining at M/M level, but not proportionally to targeting reduction (organic conversions continue) |

**MTF (Margin Trade Funding):** Same responsible broker framing applied. GTM strategy: 3 parts (Drop-off journey for discovered users; Nudged discovery for focused cohort; [Part 3 = image]).

### CNC Personalized Alert Benchmarks — CTR Hierarchy (Batch 8)

These are ranked from lowest to highest performing for CNC (Stocks) TTU users. Intent definition across all: Holdings OR Watchlist OR PP-visits > 4 in L7D. Session attribution window = 12 minutes post PN.

| Campaign type | PN CTR | Session Conversion | Notes |
|--------------|--------|--------------------|-------|
| Generic Stocks in Spotlight (BAU) | ~3% | — | Baseline / CG |
| Automated Stock News | 4-7% | 10-35% | Existing personalised |
| Price Alert (±5%) | 3.5-8% | 17-40% | Existing personalised |
| 52W High/Low | **11-13%** | **33-37%** | New (May-Jun experiment); 450K daily reach; expand to Nifty 500 |
| 50 DMA breakout | **11-17%** | **32-45%** | New (Sep experiment); SMA-based |
| 150 DMA breakout | **9-14%** | **27-47%** | New (Sep experiment) |
| **200 DMA breakout** | **14-19%** | **40-51%** | **Best performing** (Sep experiment); Nifty 100/200 |

DMA = Daily Moving Average. 200 DMA = the 200-day moving average of a stock's price. Crossing it up (positive breakout) or down (negative breakout) is a major technical signal.

### ML Personalization Benchmarks (from experiments)

| Model / Experiment | Result |
|-------------------|--------|
| **RID Product Affinity ML (vs RFM baseline)** | PN CTR +6%, DTU +1.3%, Sessions +7% |
| **Cross-sell Affinity ML** | +3.2% Cross-sell FID vs CG |
| **C-MAB V0 (Thompson Sampling, Stocks mid-market)** | **34% CTR uplift** (after model warmup) |
| **C-MAB V1 (richer contextual features)** | **40% CTR uplift + 3% DTU uplift** |
| **Campaign Affinity V0 (classical ML, 9:30am slot)** | 10-15% CTR lift; F&O 1.5% → 2.4% |
| **Campaign Affinity V1 (Thompson Sampling)** | **20% CTR uplift** (early reads) |
| **F&O TTU Index personalization** | PN CTR +6-10%; User CTR +6-9%; DAU/Session: minimal |
| **Instrument Affinity (Top 10 stocks, NTU)** | DAU +3% (0.45% absolute); NTU uplift minimal |
| **Instrument Affinity (Top 11-50 stocks, NTU)** | CTR +23%; NO DAU impact → paused |
| **PA Model for OB/NTU (D7+ onboarded users)** | CTR ↑, Sessions ↑; NO FID conversion uplift |
| **PA model accuracy** | 73% overall (MF only 55%) |
| **MF TTU Purchase Abandonment** | CTR ↑ all cohorts, MF DAU ↑ 3/4, MF PP Visits ↑ 4/4 |
| **MF Purchase Abandonment at scale (4.2L users)** | +7,800 lumpsum orders (+5% of new orders), SIP +~2% |
| **Generic PN click retention** | 28% Week 1 → **5% by Week 40** |
| **Stocks Explore v0 (1 widget, onboarded users)** | NTU **-50%** + 40 user escalations → paused after 4 days |
| **Stocks Explore v0 (4 widgets, onboarded users)** | NTU **-20%** → paused |
| **Stocks Explore v1 (5 widgets, new signups only)** | NTU conversion: **flat** (no uplift); no D3/D10 FID impact |
| **Stocks Explore key insight** | 51% of users visit Stocks Explore BEFORE completing onboarding; fewer widgets did NOT improve NTU → Next: C-MAB widget personalization |
| **% of promotional PNs that are generic** | **~52%** (vs personalised) |

### Cross-sell Discovery vs Conversion Status (Batch 10)

Key insight: **discovery is not the problem**. Most TTU users have already explored multiple products.

| Metric | Value | Notes |
|--------|-------|-------|
| Ever discovered Products/user (TTU MAU) | **2.4 / 3** (excl. Loans/Pay) | Not a significant gap |
| Monthly discovered Products/user | **2 / 3** | Monthly discovery is the active metric |
| Bottom Nav products ever discovery | **~100%** | MF, Stocks already discovered by almost all |
| F&O discovery rate | Considerably lower | F&O is not Bottom Nav |
| Pay discovery (June→July) | **33% → ~50%** | Pay improving |
| Scope for improvement via comms | **~10%** | Small marginal opportunity |

**The real problem is conversion, not discovery.** Most TTU users have seen/explored products they haven't yet transacted in. The ML cross-sell model focuses on converting these high-intent undecided users.

Open questions (from the doc itself):
- What cross-sell metric for OKR? Monthly discovery or ever transaction?
- What other levers beyond comms for cross-sell?

### Next Best Product Cross-sell Experiment Results (Batch 10)

**Setup:** ML model (Cross-sell Affinity) to identify next best product for each user. Changed from PPI=1 only → all L30D Active TTU. Added n+1 PN frequency (one additional cross-sell PN/day on top of PA calendar). TG = 3.1M, CG = 3.1M. 8-21 Dec (2 weeks). Cross-sell freq: 5 PN/week.

**Overall results:**

| Metric | Result |
|--------|--------|
| Cross-sell conversion | **+4%** (statistically significant) |
| Cross-sell product DAU | **+3%** |
| Overall DAU / Sessions | Same — users redirected, not net-new sessions |
| DND (push opt-out) | +2% (insignificant) |
| PN CTR | **-10%** (expected — more targeted = lower raw CTR) |
| User CTR | **+8%** (right users clicking) |

**Product-wise cross-sell uplift:**

| Product | Uplift | Model Accuracy Rank |
|---------|--------|-------------------|
| **Pay** | **+23%** | 3rd (Pay) |
| **F&O** | +2% | 4th (needs improvement) |
| **Stocks** | +1.5% | 1st (best) |
| **MF** | +1% | 2nd |

**By engagement level:** More engaged TTU → better CS uplift + lower DND. Less engaged → more DND risk.

**By PPI:**
- PPI=1 users: marginal CS uplift + **huge DND spike** ⚠️ — not safe to target aggressively
- PPI>1 users: sharp CS uplift + no DND increase ✅

**By NTU recency:** Cross-sell uplift: 12M+ > 1M > 3-12M > 2-3M > 1-2M. (Very old + very recent NTUs cross-sell best; 2-3M is the trough.)

**Next steps:** Improve F&O model accuracy; roll out on PPI>1 / high-engagement cohorts only; decision tree to identify negative-impact cohorts; optimize cool-off period.

### F&O Data Signals — NARAD Campaign Triggers

These are the derived attributes built into NARAD's master_tables schema for automated F&O campaign triggers. Each can be used as a campaign eligibility condition.

| Signal | Definition | Used in |
|--------|-----------|---------|
| **PCR (Put-Call Ratio)** | Ratio of Put OI to Call OI across a contract or index. PCR > 1 = more puts than calls = bearish sentiment; PCR < 1 = bullish. Tracked as point-in-time and as % change from day start. | PCR alert campaign |
| **ATM straddle** | At-The-Money options straddle — a strategy buying both ATM call and ATM put. ATM straddle price = key signal of market volatility expectation. Tracked across 30min, 1hr, and day change. | ATM straddle alert campaign |
| **OI (Open Interest)** | Total open contracts in a derivative. Surge/drop in OI = significant market activity signal. | OI alert campaign |
| **Strike rank** | How far a contract's strike price is from the live spot price (number of strikes away). Used to filter contracts to those near ATM. | OI Buildup campaign targeting |
| **Long buildup** | OI increasing + price increasing → bulls adding fresh positions | Buildup alert campaign |
| **Short buildup** | OI increasing + price decreasing → bears adding fresh positions | Buildup alert campaign |
| **Covering** | OI decreasing + price increasing → short sellers closing/covering positions | Buildup alert campaign |
| **Unwinding** | OI decreasing + price decreasing → long holders exiting positions | Buildup alert campaign |
| **Greeks** | Delta, gamma, theta, vega — options sensitivity metrics. Next planned data source to onboard into NARAD. | Planned (not yet live) |

**20+ F&O campaigns automated** (as of Batch 6 doc): PCR alert (30min/day), OI alert (surge/drop), ATM straddle movement (30min/1hr/day), Long/short buildup/covering/unwinding, OI Buildup contracts, Put/Call OI Change.

**Next**: Replicate same pipeline for CNC & MF (planned for Sep timeline).

### App Source Splits (where NTU and RID come from in-app)

| Product | Source | Contribution |
|---------|--------|-------------|
| **CNC / Stocks** | Explore section | 48% of Groww NTU, 33% of Cross-sell CNC FID |
| **CNC / Stocks** | Within Explore: Most Bought/Traded | 76% of Explore NTU |
| **MF** | Explore section | 62-66% of MF NTU & Cross-sell FID |
| **MF** | Within Explore: Popular funds + Collections | 46-55% |
| **MF** | Within Explore: Start a SIP Widget | 11-17% |
| **MF RID** | Explore | 40% |
| **MF RID** | Dashboard | 40% |
| **MF RID** | Search | 21% |
| **F&O** | Explore | Very low |
| **F&O** | Positions + Index Cards | Primary drivers |

### Feed / Notification Center Metrics (Batch 7 docs)

| Metric | Value | Notes |
|--------|-------|-------|
| Feed (NC) Avg WAU | **243K** | Over last 4 weeks from doc date |
| Feed (NC) Avg DAU | **104K** | Over last 4 weeks from doc date |
| Feed weekly visit retention | **33%** | Week-on-week return rate |
| % NC visitors who are TTU | **93%** | Non-TTU only 7% — very low non-investor engagement |
| F&O MAU visiting NC | **28%** of F&O MAU | Highest product engagement with Feed |
| CNC MAU visiting NC | **14%** of CNC MAU | Mid |
| MF MAU visiting NC | **7%** of MF MAU | Lowest — MF is "very static" content |
| Feed content mix (May) | Macro/Market 45%, Opportunities 25%, Personalized 18%, Personal Finance 12% | Personalized content only 18% of impressions despite being highest priority |

### Stories Scoring Model (Batch 7 docs)

**Rf score** = Random Forest model predicting D1 retention of each Story.

**Feature importance (most → least):**

| Feature | Weight | Definition |
|---------|--------|-----------|
| **Skip Rate** | 0.24 | % who skipped the story — most important signal |
| **Normalized Completion** | 0.23 | Actual completion / expected completion (adjusted for slide count); expected = 0.9297 - 0.0344 × slide_count |
| **Unified Action Rate** | 0.18 | MAX(Deeplink Click%, Share%) |
| **Weighted Time** | 0.16 | (0.1×P50) + (0.2×P75) + (0.3×P90) + (0.4×P95) — weights time spent by more engaged users |
| **Screenshot Rate** | 0.13 | % who took a screenshot |
| **Slide Count** | 0.06 | Number of slides — lowest importance; fewer = better |

**Scoring tiers:**
- **Tier A**: ≥ 0.325 — high-performing
- **Tier B**: 0.262 – 0.324 — mid-performing
- **Tier C**: < 0.262 — low-performing

**Model stats:** R²=0.254 (RF beats linear regression at R²=0.174). 248 stories scored. Score distribution: median 0.288, mean 0.299. Optimal story length: 3-6 slides (7-10 slides → completion rate drops).

### TTU Retention & Resurrection Benchmarks

| Metric | Benchmark |
|--------|-----------|
| TTU users becoming inactive per month | **3.2 Million** |
| High-active TTU: ML affinity uplift | None (they self-direct) |
| Mid/Low-active TTU: ML affinity CTR uplift | **~6%** |
| ML affinity DTU uplift | **+1.3%** |
| ML affinity comms-attributed session uplift | **~7%** |
| IPO comms CTR — inactive TTU base | 0.7% → 1.1% |
| IPO comms CTR — TTU base | **4%** |
| SGB comms CTR — TTU base | **3% → 4.5%** |
| WA for High Potential Inactive TTU | High uplift in resurrection |
| WA for High Risk MAU TTU | Lower uplift |
| WA incremental cost (PU) | **Rs.75/resurrection** |
| WA effectiveness for driving transactions | Low (brings back app opens, not transactions) |

### Retention Propensity Model — Decile Key

| Decile Group | Segment | Key Characteristics |
|------------|---------|-------------------|
| Decile 1,2,3 (Jan MAU) | **High Risk of churn** | Almost entirely PPI=1 (MF or Stocks only); AUM<500 (many AUM=0); Peak AUM was high → exited; PN reachability >90% |
| Decile 8,9,10 (Jan Inactive) | **High Potential for resurrection** | Active in last 2 months; some current AUM + decent peak AUM; PN reachability small → use WA/RCS/Email |

### Funnel / Activity Metrics

| Metric | Definition | Pod |
|--------|-----------|-----|
| **D7** | % of registered users who become NTU by Day 7 — early activation signal | Activation |
| **Onboarding %** | Step-by-step completion rate through KYC → FID funnel | Activation |
| **Convert rate** | % moving from funnel step N to N+1 | All |
| **Dropoff rate** | % leaving at a given funnel step | All |
| **PP visits** | Product Page visits — engagement proxy for non-TTU users | Activation |
| **PN-to-Session** | Push notification clicks that result in an app session | Campaign |
| **Campaign volume** | ~3 Billion communications/month across all channels (as of Feb 2024) | All |

---

## 5. User Funnel

### Activation Funnel (0 → FID)

The full KYC onboarding funnel from Sign-up to Esign (KYC completion). **Only 26% of users complete Signup → Esign within 7 days.** After Esign, users invest → FID.

#### Sign-up to Esign (KYC completion) — exact drop rates from experiment data

```
Signup
    ↓ [20% drop]  — Signup to OTP
OTP verified
    ↓ [40% drop]  — OTP to PAN  ← BIGGEST drop in the funnel
PAN verified
    ↓ [35% drop]  — PAN to Bank Verification (BV)  ← 2nd biggest
Bank Verified (BV done)
    ↓ [20% drop]  — BV to Digilocker (Aadhaar-based KYC)
Digilocker done
    ↓ [22% drop]  — Digilocker to Esign
Esign ✅ — KYC complete
    ↓
[Product Browse → PP Visits → Watchlist → First Investment]
    ↓
FID ✅ → user becomes NTU
```

**Major drop points in KYC:** PAN step (40%) and Bank Verification (35%). These are the highest-priority intervention points.

**Account opening cost baseline:** Rs.44/user (fully loaded cost for each KYC completion)

**Overall 7-day Signup → Esign completion rate: 26%**

**WhatsApp impact on onboarding funnel (experiment):**
- WA added to journeys across 6 steps: OTP_PAN, PAN_BV, BV_DOC, DOC_SELFIE, SELFIE_SIGN, SIGN_ESIGN
- Result: ~200 incremental Esign completions/day; Cost per incremental conversion: **₹145**
- Key insight: Better conversion uplift at steps closer to Esign (higher intent = higher WA impact); D7 uplift < D1 uplift (WA prepones onboarding, not just adds net new completions)
- PAN step exception: bigger drop = larger WA impact despite being early in funnel
- WA now live for 100% of users in onboarding journeys (implemented in COSMOS flow)

#### Post-Esign → FID (Post-Onboarding activation)

The user has completed KYC. Now they need to actually invest. Key strategy levers:
- Product affinity + Instrument affinity personalization (NARAD-automated push)
- PP (Product Page) visits as a behavior milestone — users who visit PP ≥2-5 times are higher intent
- Watchlist engagement, DAU, time spent on app = milestones tracked before FID

**Inactive base cohorts (non-investor users by recency):**

| Cohort | Definition | Push reachability | Notes |
|--------|-----------|-----------------|-------|
| **L30D+ Active** | Active within last 30 days | High | ~10% of monthly NTU |
| **L150D+ Active** | Active within last 150 days | **~1.5%** | Largest base; highest share of monthly NTU due to volume |

For L150D+ base: ~30% of their MAU is attributed to Google ads retargeting. Previous WhatsApp/remarketing CAC for this base: **6,000+** → focused targeting needed (PPvisit signal used to identify ready sub-segments).

**How engagement uses the funnel:**
- Identify where the largest user cohort is stuck (biggest dropoff step)
- Design targeted comms to push users from their current step to the next
- Each step has a different message angle (trust, education, urgency, FOMO, simplicity)
- Track Convert rate and Dropoff rate per step

### RID / Repeat Funnel

- User has done FID → are they returning?
- Activity cut: has the user logged in recently?
- Transaction cut: has the user transacted recently?
- TTU threshold defines the boundary between "active" and needing re-engagement

### Trading Funnel

- Similar logic but for trading products (FnO, MIS, etc.)
- 9:15 AM is a key trigger moment — pre-market, opening bell, mid-session, end-of-day are distinct comms opportunities

---

## 6. Channels & Communication Types

### Channels

| Channel | On/Off App | Owner | Notes |
|---------|-----------|-------|-------|
| **Push Notifications** | Off-app | All pods | Primary high-volume channel |
| **WhatsApp (WA)** | Off-app | Nikhil (channel manager), Yash (trading) | High engagement; regulated content. BIC price: 73p/message (up from 51p); UIC: 33p. Used for onboarding drop-off journeys, reactivation, and Push-unreachable users. ~50% of non-investor app-keep users are Push-unreachable. |
| **Email** | Off-app | Himanshu (infra/strategy), Yash (GrowwFlix) | Cheapest channel; 99% delivery, 18-20% open rate. Sent via WebEngage → Netcore (ESP) or AWS. Subdomains: digest.groww.in, dailydigest.groww.in. Declining engagement: Daily Digest MAU 13M (Oct-24) → 8M (Mar-25). |
| **RCS** | Off-app | Aishwarya | Rich Communication Services — enhanced SMS with images/buttons |
| **SMS** | Off-app | Aishwarya | Fallback / transactional |
| **In-app Stories** | On-app | Aishwarya | Content-led browseable feed inside the app |

### Communication Types — and How They Relate

These are not just a flat list — they represent a **progression from reactive to automated:**

```
BAU Comms          → Regular, planned, broad (e.g., weekly market update push)
    +
Adhoc Comms        → Reactive, event-driven (e.g., market crash alert, IPO open)
    +
Mid-Market Action  → Real-time triggers during market hours (intraday opportunities)
    ↓
Personalized Comms → User-specific, ML-driven (right product + right time per user)
    ↓
Journeys           → Automated lifecycle sequences triggered by user behavior
                     (e.g., 7-day drip for KYC-done-not-invested users)
```

| Type | Description | Cadence |
|------|-------------|---------|
| **BAU Comms** | Business As Usual — planned, regular campaigns | Daily / Weekly |
| **Adhoc Comms** | Reactive to market events or news | Event-triggered |
| **Mid-market Action** | Live triggers during market hours | Intraday |
| **Personalized Comms** | ML-driven, 1:1 personalization | Daily (model refresh) |
| **Journeys** | Automated lifecycle drip sequences | Behavior-triggered |
| **GTM Communications** | Go-to-market for product/feature launches | Per launch — *more context pending* |

---

## 7. Tools & Systems

| Tool | Category | Purpose |
|------|----------|---------|
| **NARAD** | CRM (internal) | Groww's internal CRM tool for campaign management. Architecture: real-time data streams ingested via Kafka + Spark stateful structured streaming → stored in master_tables schema → campaign triggers read from these tables. Self-serve model: business team can define derived attribute logic (e.g., `curr_oi < oi_30min_before * 0.90`) in <1 day without DP team involvement. Personalization engine: text-only via CDP (no personalized images at scale). Instrument affinity automation being built into it. |
| **Kafka** | Data pipeline | Event streaming platform used for ingesting real-time F&O data streams from Invest Pod (tables: fo_feed, indices_v3, derived_contract_master, screener_underlying_details). Foundation of NARAD's self-serve campaign pipeline. |
| **Spark stateful structured streaming** | Data pipeline | Stream processing framework joining multiple data sources at different refresh intervals; handles event-triggered state + time-based refreshes (every minute). Used for building F&O derived attributes in NARAD pipeline. |
| **master_tables schema** | Data store | Central data schema in NARAD where all structured F&O data streams are stored. Includes: Contract master, Index master, ATM master (feature tables). All base + historical attributes (30min, 60min, 120min, 1D batches) stored here. |
| **CDP (Customer Data Platform)** | Personalization | NARAD's data layer for personalization. Currently supports text personalization only — no personalized images at scale. Used for Feed personalization properties. |
| **WebEngage** | CRM (external) | Campaign orchestration platform (push, email, in-app); handles push throughput at scale |
| **COSMOS flow** | Journey system | Journey/automation system that WhatsApp comms are integrated into. WA onboarding journeys implemented in COSMOS. ⚠️ Confirm relationship to NARAD/WebEngage |
| **Audience Manager** | Segmentation | Build and manage user cohorts / segments for targeting |
| **Superset** | Analytics / BI | Dashboard and data visualization (Apache Superset) |
| **Table access** | Data | Raw data table access — specific warehouse TBD (BigQuery? internal?) |
| **User Engagement Dashboard** | Reporting | Top-level UE performance tracking |
| **Comms 360** | Reporting | Cross-channel communication performance dashboard |
| **UE Weekly Business Review Docs** | Reporting | Weekly performance review docs (WBR) |
| **Firebase** | Attribution | Mobile analytics platform; reinstall attribution (~60% reinstall accounted for in Firebase; actuals higher) |
| **FCM (Firebase Cloud Messaging)** | Push delivery | Google's push notification delivery infrastructure; pipeline: WebEngage → FCM → User device. Throughput bottleneck found at FCM (not WebEngage) even after WebEngage scaled to 250K/min |
| **Netcore** | Email ESP | Email Service Provider used by Groww for Digest delivery; throughput scaled from 2.2M/hr to 10M/hr (Mar-23). Subdomains: digest.groww.in (primary), dailydigest.groww.in (backup) |
| **GrowwFlix** | Email property | Groww's YouTube-linked email property with financial education videos (MF, Stocks, Trading); 7M users; 30% open rate; drives YouTube subscriber growth; MAU uplift: TTU +1.7%, Non-TTU +0.71% |
| **Daily Digest** | Email property | Daily market update email; 15M target users; sent at 7:30-8pm; throughput was bottleneck (fixed in Nov-22 project); MAU declining: 13M (Oct-24) → 8M (Mar-25) |
| **Weekly Digest** | Email property | Weekly market/portfolio summary; optimized from 24M → 11M targets (same 2.1M opens); saved Rs.7-8L/month; open rate drives key retention signal |
| **Domain reputation** | Email deliverability | Email domain's deliverability score; spam rate spike to 68% caused inboxing failure. Maintained by controlling send volume, open rates, and spam complaints |
| **Domain warmup** | Email infra | 30-day process of gradually ramping send volume (100 → 10M emails) to build domain reputation; requires maintaining >20% open rate during warmup |
| **Inboxing** | Email deliverability | Whether emails land in Primary inbox vs Promotions/Spam tabs; salesy subject lines → Promotions tab = lower open rate |
| **BigQuery (BQ)** | Data warehouse | Groww's data warehouse (confirmed via PA/instrument affinity pipeline); segments updated daily: BQ → Audience Manager → WebEngage |
| **Retention Propensity Model** | ML | Predicts each TTU user's probability of transacting next month; splits base into 10 deciles; powers differentiated comms strategy for high-risk vs high-potential users |
| **Cross-sell Affinity Model** | ML | Predicts next best product for single-product TTU users; currently covers F&O, MF, CNC, MIS; Pay & Credit to be added; built for Product/user=1 (V0); 14-day prediction window |
| **PA Calendar (Product Affinity Calendar)** | Scheduling | Daily/weekly schedule of which product to promote for each user segment based on affinity model output; the operational engine that translates ML predictions into PN campaigns |
| **C-MAB (Contextual Multi-Armed Bandit)** | ML | Thompson Sampling algorithm for selecting best push notification per user per slot. V0 reward: CTR only. **V1 reward function: 50% CTR + 50% Transaction rate** (not CTR-only); 10% exploration rate. V0: 34% CTR uplift after model warmup. V1: 40% CTR + 3% DTU uplift. 5 models deployed for TTU; 3 Non-TTU in progress; expanding to on-app widget ranking. Industry users: Zomato, Duolingo, LinkedIn, Facebook, Doordash. |
| **Widget Ranker Engine** | ML | C-MAB-powered on-app widget ranking for Stocks Explore; BFF capability; V0: 4 widget slots (down from 9); daily model refresh; goal: improve NTU conversion |
| **Campaign Affinity Model** | ML | Classical ML → Thompson Sampling bandit for selecting best campaign per user per time slot; V0: 10-15% CTR lift; V1: 20% CTR uplift (early); includes Template Fatigue Penalty + Eligibility Filtering |
| **EMS (Event Management System)** | Data pipeline | Real-time events pipeline; replacing WebEngage data pipeline for C-MAB (will reduce content affinity lag from 2 days to 1 day) |
| **In-house Campaign Manager (CM)** | CRM | New internal campaign manager being built (separate from NARAD and WebEngage?); instrument affinity automation and MF purchase abandonment scale-up depend on it |
| **BFF (Backend for Frontend)** | Architecture | Tech pattern enabling on-app MAB personalization (widget ranking requires real-time ML inference per page load) |
| **Aampe** | External tool (evaluated, not adopted) | AI-agentic system for PN content generation, segmentation, distribution; keyword tokenization + tonality tagging per user; evaluated Sep-24; rejected due to high cost (POC Rs.21L/month for 20M MAU; post-POC Rs.32L/month; Rs.10.2L for 5-month POC for 8M MAU in the initial proposal). Architecture: BQ Table → Aampe Engine → WebEngage → User PN. Swiggy learnings: 1 PN/day > 2 PNs; Thompson Sampling >> UCB. Rejected: cost + integration complexity. |
| **RFM segmentation** | Targeting (pre-ML) | Rule-based segmentation by Recency, Frequency, Monetary value — the CG baseline before ML affinity models; now replaced by ML for TTU comms |
| **Notification Center (NC)** | In-app product | The in-app Feed / content hub. NC = Feed (same thing). Users visit to browse content. WAU ~243K, DAU ~104K, Weekly retention 33%. TTU = 93% of visitors (F&O 28%, CNC 14%, MF 7%). Low-active TTU and Non-TTU show very little organic intent → solving via content + comms. |
| **CMOTS data** | External data | Data source showing which stocks are being bought/sold by Mutual Funds on a daily/weekly basis. Planned for Feed content to surface MF flow signals. |
| **KiteConnect** | Trading API | Zerodha's trading/market data API; used internally for fetching live F&O option chain data (OI, prices, bid-ask spreads). Data source: `invest_iceberg.live_data.stocks_data_live_nse_fo_feed` |
| **platform_pinot** | Data store | Real-time data store (`platform_pinot.default.fno_stocks_order`) used for live F&O order data; used in "Most Traded F&O Stocks" ranking. |
| **platform_iceberg** | Data store | Iceberg-based data store (`platform_iceberg.stocks_shared_invest.derivatives_contract_master_table`) for derivatives instrument metadata; also `invest_iceberg.live_data.stocks_data_live_nse_fo_feed`. |
| **Rf score (Stories)** | ML model | Random Forest content scoring model for in-app Stories. Target variable: D1 retention. R²=0.254. Formula: `0.24×SkipRate + 0.23×NormalizedCompletion + 0.18×ActionRate + 0.16×WeightedTime + 0.13×ScreenshotRate + 0.06×SlideCount`. Tiers: A ≥ 0.325, B 0.262-0.324, C < 0.262. |

---

## 8. Audience / Cohort Workflow

The standard process for sending any communication, based on the original notes:

```
1. Define Cohort
   → Who are we targeting?
   → Apply TTU logic: activity cut + transaction cut
   → Example: "KYC done, no FID, last active D3-D7"

2. Content Banao (Create Content)  ← "Content banana" in notes = Hindi "banao" (create/make)
   → Write copy, design creative (push body, email subject, WA message, etc.)
   → Apply personalization variables if applicable

3. Audience Manager
   → Pull user list matching cohort criteria using Segment Query
   → Validate reach and overlap with frequency caps

4. Send
   → Load into NARAD or WebEngage
   → Set timing, channel, frequency caps
   → QA → send

5. Measure
   → Track open rate, CTR, conversion (FID/RID), dropoff
   → Report in Comms 360 / UE Dashboard / WBR
```

> **Note on order:** Original notes list: `Cohort → to send comms → Content banana → Audience Manager → Segment Query` — content creation comes **before** audience finalization, not after.

---

## 9. Open Questions

Things to clarify as you learn more — update this section when answered:

- [ ] **Aastha's seniority** — Is she the vertical/team lead, or just Trading pod strategy? Her placement at the top of the notes suggests a senior role.
- [ ] **Amit's exact role** — Full Invest pod ownership, or MF-specific strategy only? "Does the full then" is ambiguous.
- [ ] **Aishwarya's scope** — Is she shared execution across all pods, or only Activation? "Stories bhi" suggests she does channels beyond Activation.
- [ ] **TTU** — Exact activity cut and transaction cut thresholds (days? actions?)
- [x] **"915 new app"** = **Groww 915** — a separate app product by Groww (not just the 9:15 AM timing trigger). Confirmed by user.
- [x] **Activation funnel steps** — Confirmed: Signup → OTP → PAN → BV → Digilocker → Esign → [Product Browse → FID]. Drop rates now known. (Batch 2)
- [ ] **1-2-3-4 step funnel** — How does this map to the 7-8 step KYC funnel? Higher-level abstraction?
- [x] **OB** = Onboarding (confirmed — used throughout Batch 2 docs for KYC onboarding completion / Esign completion)
- [ ] **GTM communications** — What does GTM comms look like at Groww? Who owns it? (empty in original notes)
- [ ] **COSMOS flow** — What is this exactly? Is it the same as NARAD journeys, WebEngage journeys, or a separate system? WhatsApp is integrated into it for onboarding.
- [x] **DMA Alert** = 200 Daily Moving Average alert (NOT Direct Market Access). When a stock price crosses above/below its 200-day moving average — a major technical analysis signal used for CNC personalized campaigns. (Confirmed in Batch 8 DMA doc)
- [x] **SGB** = Sovereign Gold Bond (confirmed — Batch 3, IPO & SGB SOP)
- [ ] **NTU → CNTU strategy** — Channel × Form factor × Content still being figured out (WIP as of doc date)
- [ ] **CNTU thresholds** — What counts as CNTU for each product? (e.g., MF: SIP with approved mandate; CNC: Buy transactions > X — X not specified)
- [ ] **Cold start problem** — How to personalize for brand new users with no behavioral history? Mentioned as open ideation item.
- [x] **Instrument Affinity for TTU** — Covered in Batch 4. Pending compliance approval.
- [ ] **In-house Campaign Manager (CM)** — New CRM being built internally; MF purchase abandonment automation and instrument affinity scale-up depend on it. Is this the same as NARAD V2 or a separate system?
- [ ] **EMS events** — Replacing WebEngage pipeline for C-MAB; will reduce content affinity lag from 2D to 1D. When going live?
- [ ] **BFF capability** — Backend for Frontend for widget ranking on Stocks Explore; tech dependency for on-app MAB.
- [ ] **Anshul / Saurabh** — Who are they exactly? Tech team or ML team? Pod affiliation?
- [ ] **PA model MF accuracy (55%)** — Why does the model perform poorly for MF? Feature engineering issue? MF users have different browse-to-invest patterns?
- [ ] **Digest** — What exactly is the Groww Digest? Email digest with market updates and portfolio summary sent weekly. CTA being added for email-active TTU. More detail in Batch 5 (Email docs).
- [ ] **GrowwFlix** — Groww's video/content initiative. Mentioned as potential resurrection hook. More detail in Batch 5 (Email docs).
- [ ] **Cross-sell window optimization** — Experiment showed 14D window too short for cross-sell to materialize; 30D window being explored.
- [ ] **IPO Corner** — Campaign property for multiple simultaneous smaller IPOs. 'Smaller IPO' definition still being formalized (market cap + user intent count).
- [ ] **D7 definition** — Day 7 retention, or Day 7 activation milestone?
- [ ] **MBR vs WBR** — Confirm MBR = Monthly Business Review; WBR = Weekly Business Review
- [ ] **NARAD vs WebEngage** — Which is primary? Are they used for different channels or different pods?
- [x] **Notification Center (NC) = Feed** — Confirmed. NC IS the in-app Feed/content hub. Same thing, two names.
- [ ] **CDP vs Audience Manager** — Is NARAD's CDP the same system as Audience Manager, or are these separate tools? Both seem to do user data/segmentation.
- [ ] **DP team** — Data Platform/Pipeline team (builds Kafka/Spark infra for NARAD). How large? Does each pod have a DP partner?
- [ ] **Feed personalization timeline** — When do the 5 Phase 1 properties (Portfolio Analysis, Alerts, Benchmarking, Newsletter, Brokerage Outlook) go live? Phase 2 (Fundamentals + Portfolio Health) depends on "Fundamental Attribute Creation" — when is that done?
- [ ] **Reporting lines** — Who does the Growth vertical report to?
- [ ] **Table access** — Which data warehouse? BigQuery? Internal system?
- [ ] **LO** — Mentioned in notes as "major metric for overall business". Abbreviation unclear — could be L0 (Level-0 / north-star metric), "Logged On", or something else. Confirm with team.
- [ ] **Himanshu's Activation scope** — Notes say "Himanshu → Activation & Invest (which includes)" — suggesting his scope is broader than just RID + Personalization. Confirm exact pods he covers.
- [ ] **CNC-MIS Intent** — Notes group CNC and MIS together as a combined intent segment. Confirm: is this a specific targeting cohort, or just a conceptual grouping?
- [ ] **D0/D1 tag system** — D0 and D1 are interchangeable labels for the signup day. More tag names coming as data is shared. Known so far: `D0_onboarding`, `D0_dmat`, `D1_onboarding_from_signup`, `D1_NTU_from_signup`.


---

*Feed in more context and this doc will grow. Ask to update any section.*
