# Groww Context Store

This file is the living memory of your Groww growth and marketing context.
The skill reads it at the start of every session and updates it as you share new information.
When something is missing, the skill will ask and then fill it in here.

---

## 🏢 Company Overview

**Groww** is India's largest retail investment platform (registered with SEBI as a Stock Broker, AMFI-registered Mutual Fund Distributor, and IRDA-registered Insurance Distributor).

- **Headquarters**: Bengaluru, Karnataka
- **User base**: ~10 crore+ registered users (as of 2024)
- **Products**: Mutual Funds, Stocks & F&O, IPO, US Stocks, Gold, Fixed Deposits, Digital Gold, Insurance
- **Key differentiator**: Simplified UX for first-time investors, strong brand trust among millennials and Gen Z

---

## 📦 Active Products & Features

> Update this as you share product-specific context

| Product | Status | Key User Actions | Notes |
|---------|--------|-----------------|-------|
| Mutual Funds | Active | SIP start, lump sum, ELSS | Core revenue driver |
| Stocks / F&O | Active | Buy/sell equity, derivatives | Brokerage revenue |
| IPO | Active | Apply via UPI | Seasonal, high-intent |
| US Stocks | Active | Fractional investing | LRS limit: $250K/year |
| Digital Gold | Active | Buy/sell 24K gold | Festive demand spike |
| Fixed Deposits | Active | FD booking via partners | Trust play for conservative users |
| Insurance | Active | Term / health / motor | Cross-sell from investment users |

---

## 📊 Key Metrics & Baselines

| Metric | Full Form | Baseline | Notes |
|--------|-----------|---------|-------|
| **FID** | First Investment Done | Unknown | Primary activation goal |
| **RID** | Repeat Investment Done | Unknown | Retention / habit metric |
| **NTU** | New Transacting User | Unknown | New users transacting in period |
| **D7** | Day 7 activation/onboarding % | Unknown | Key milestone in activation funnel |
| **MBR** | Monthly Business Review | — | Reporting cadence metric, not a number itself |
| **TTU** | TBD (activity + transaction cut) | Unknown | Defines active vs lapsed — confirm definition with Nikhil |
| **CrossSell FID** | Cross-sell First Investment Done | Unknown | FID in product #2 for existing investor |
| **Onboarding %** | Step completion rate | Unknown | 7-8 step KYC funnel completion |
| **Convert rate** | Per-step funnel conversion | Unknown | % moving from step N to N+1 |
| **Dropoff rate** | Per-step funnel dropoff | Unknown | % leaving at step N |
| DAU | Daily Active Users | Unknown | — |
| MAU | Monthly Active Users | Unknown | — |
| MAI | Monthly Active Investors | Unknown | Subset of MAU who transacted |
| SIP Book | Active SIPs | Unknown | — |
| Push CTR | Push notification CTR | Unknown | — |
| Email Open Rate | — | Unknown | — |

---

## 🎯 Current OKRs / Focus Areas

> Updated as you share quarterly priorities

Ashish is in a learning / onboarding phase (as of 2026-03-26). Engineering major background — strong on technical concepts, building knowledge of marketing and growth terminology. Current task: understand how the Growth vertical functions — pods, people, metrics, workflows.

When explaining concepts, use engineering analogies (state machines, pipelines, APIs, SQL queries, event-driven systems). Avoid assuming familiarity with marketing jargon — define terms before using them.

---

## 🧪 Active Experiments & Campaigns

> Track what's live or recently run

| Name | Type | Status | Results / Notes |
|------|------|--------|----------------|
| WA for Esign drop-off (onboarding journey) | Channel addition to journey | ✅ Live (100%) | 30% conversion uplift TG vs CG; ~200 incremental Esigns/day; ₹145 cost/incremental conversion |
| WA for IFSC→BV drop-off | Channel addition | ❌ Reverted | 4% uplift — not worth the Rs.20 added to Rs.44 account opening cost |
| WA for inactive non-investor reactivation | Channel vs Remarketing | ✅ Scaled (300K users) | WA FID CAC = 1/5th of remarketing (Non-OB), 1/10th (OB users) |
| Product affinity personalization (Post-OB) | ML personalization | ✅ Live; V2 in progress | CTR increase target: 5-10% |
| Instrument affinity (ISIN/Fund level) | ML personalization | 🔄 Being automated into NARAD | Currently manually scheduled |
| FB Remarketing + WA for D3-D15 post-OB | Reach expansion | 🔄 Testing ongoing | — |
| WA/RCS for PN-unreachable users | Channel reach | 🔄 Testing ongoing | — |
| Retention Propensity experiment (WA + Push for High Risk + High Potential TTU) | Differentiated comms | 🔄 Push live; WA closed | High Potential users show much higher uplift; WA brings app opens but not transactions; WA incremental cost Rs.75/PU |
| Product Level Affinity experiment (ML vs BAU targeting for DTU) | ML personalization | ✅ Live (implemented in BAU) | PN CTR +6%, DTU +1.3%, Sessions +7% vs BAU; no uplift for high-active TTU; uplift for mid/low-active |
| Next Best Product experiment for TTU (Cross-sell ML model) | Cross-sell ML | 🔄 Iteration 2 planned | Mixed: CTR/DAU down but cross-sell product DAU up in some cohorts; 14D window too short → 30D needed |
| Revive — WA Portfolio Updates for inactive TTU | Resurrection | ✅ Live (weekly cron) | Sent to inactive>30D, AUM>Rs.100; Tue (MF), Wed (CNC); results in screenshots |
| C-MAB V0 (Stocks mid-market push) | ML push optimization | ✅ Live | 34% CTR uplift after warmup; 1 campaign → 6 campaigns; Thompson Sampling |
| C-MAB V1 (richer contextual features) | ML push optimization | ✅ Live | **40% CTR uplift + 3% DTU uplift**; 5 models for TTU; 3 Non-TTU in progress |
| Campaign Affinity V1 (Thompson Sampling, 9:30am slot) | ML campaign selection | 🔄 Testing ongoing | 20% CTR uplift (early reads); Template Fatigue Penalty + Eligibility Filtering |
| Widget Ranker Engine on Stocks Explore (C-MAB) | On-app ML personalization | 🔄 In development | Goal: improve NTU conversion; V0 = 4 widget slots ranked daily |
| PA for OB/NTU (D7+ onboarded, non-TTU) | ML personalization | ✅ Validated; scale-up planned | CTR ↑, Sessions ↑; NO FID uplift; F&O best, MF negative (55% PA accuracy) |
| Instrument Affinity Top 10 stocks (NTU) | ML personalization | 🔄 Manual; automating into CM | Top 10: 3% DAU; Top 11-50: paused (CTR up but no DAU) |
| MF Purchase Abandonment (buy intent ≥2 L30D) | Behavioral personalization | 🔄 Automating (4.2L scale-up) | CTR ↑, MF DAU ↑, PP Visits ↑; +7,800 lumpsum orders at scale (+5% new orders) |
| F&O TTU Index personalization (instrument affinity) | ML personalization | ✅ Validated | PN CTR +6-10%, User CTR +6-9%; DAU/Session: minimal |
| Aampe POC evaluation | External tool eval | ❌ Rejected | Too expensive (10.2L for 5M for 8M MAU); integration complexity; Sep-24 evaluation |
| Email Throughput Ramp-up (WebEngage + Netcore) | Channel infra | ✅ Done (Mar-23) | WebEngage 2hrs at 10M/hr; Netcore 2.2M/hr → 10M/hr; open rate +2-2.5% |
| Weekly Digest segmentation optimization | Email optimization | ✅ Done | 24M → 11M targets; same 2.1M opens; saved Rs.7-8L/month |
| GrowwFlix YT Email experiment | New email property | ✅ Live (7M intent users) | TTU: +100K MAU (1.7%); Non-TTU: +26K (0.71%); YT Trading channel +27% subscribers; open rate 30% |
| Push Throughput Upgrade (WebEngage) | Channel infra | ✅ Done (Apr-23) | 75K/min → 250K/min; WE→FCM latency -50%; net DAU +0.5-0.6% |
| Push Banners experiment | PN creative | ❌ Stopped | No major CTR uplift for TTU/F&O; marginal for non-TTU; F&O banners stopped |

---

## 🏁 Experiment Backlog

> Prioritized ideas you've discussed or are considering

*Nothing captured yet.*

---

## 🕵️ Competitor Intelligence Log

> Running notes on competitor moves (Zerodha, Angel One, Paytm Money, Kuvera, INDmoney, Upstox, etc.)

*Nothing captured yet. Ask me to research a competitor and I'll log key findings here.*

---

## 📣 Channel Context

| Channel | On/Off App | Tool | Owner | Notes |
|---------|-----------|------|-------|-------|
| Push Notifications | Off-app | NARAD / WebEngage | All pods | Primary volume channel |
| WhatsApp | Off-app | Unknown | Nikhil (channel manager), Yash (trading) | High engagement |
| Email | Off-app | WebEngage | TBD | — |
| RCS | Off-app | Unknown | Aishwarya | Rich SMS with images/CTAs |
| SMS | Off-app | Unknown | Aishwarya | Fallback / transactional |
| In-app Stories | On-app | Unknown | Aishwarya | Content-led browseable feed |

---

## 📅 Marketing Calendar & Seasonal Context

> Key dates already planned or important to track

| Period | Event | Products to Activate | Status |
|--------|-------|---------------------|--------|
| Jan–Mar | Tax Saving Season (80C / ELSS) | MF, ELSS | Annual |
| Mar 31 | Tax year end | All | Annual |
| Apr | New Financial Year | All | Annual |
| Apr–May | IPL Season | Brand / Stocks | Annual |
| Jul–Aug | Budget aftermath campaigns | MF, Stocks | Annual |
| Oct–Nov | Diwali / Dhanteras | Gold, Digital Gold, MF | Annual |
| Nov | Akshaya Tritiya (sometimes) | Gold | Annual |
| Jan | ELSS last push | MF | Annual |
| Ongoing | IPO season | IPO | Event-driven |

---

## 👥 Team & Stakeholder Context

### Growth Vertical — People Directory

| Name | Pod | Role | Owns |
|------|-----|------|------|
| **Nikhil** | Invest (Activation + RID) | Strategy | Activation strategy, WhatsApp channel, RID strategy (with Himanshu) |
| **Shweta** | Invest (Activation + RID) | Strategy + Execution | Invest & Instigate strategy, Comms Orchestration for RID |
| **Himanshu** | Invest (RID + Personalization) | Strategy + ML | RID strategy all products, ML personalization models |
| **Amit** | Invest (RID — MF) | Strategy | MF-specific RID |
| **Aishwarya** | Invest (Activation) | Execution | Campaign execution, RCS, SMS, In-app Stories |
| **Aastha** | Trading | Strategy | Trading pod strategy (with Yash) |
| **Yash** | Trading | Strategy + Channel | Trading strategy, 9:15 comms, WhatsApp (with Nikhil) |
| **Samir** | Trading | Execution | Trading pod comms execution |

### Sub-Pods

| Pod | Products | Strategy | Execution |
|-----|---------|----------|----------|
| Invest — Activation | All invest | Nikhil, Shweta | Aishwarya |
| Invest — RID | CNC, ETF, Bonds, IPO, MF | Nikhil, Himanshu (MF: Amit) | Shweta |
| Invest — Personalization | All invest | Himanshu, Nikhil | — |
| Trading | FnO, Commodities, MTF, MIS | Aastha, Yash | Samir |
| Other Businesses | Wealth, Fisdom, Groww AMC | TBD | TBD |

---

## ⚖️ Regulatory Notes (Groww-Specific)

> Specific SEBI/AMFI/RBI constraints that affect Groww's marketing

- SEBI-registered Stock Broker: can market equity products, must include risk disclaimers
- AMFI-registered MF Distributor: mutual fund ads must include "Mutual Fund investments are subject to market risks, read all scheme related documents carefully"
- All return-based messaging requires past performance disclaimer
- No guaranteed return language for market-linked products
- Insurance ads must comply with IRDA guidelines
- UPI-based IPO applications: must clearly communicate refund timelines
- Cannot cold-call: SEBI restrictions on unsolicited investment advice

*Add specific campaign-level compliance flags here as they come up.*

---

## 🔑 Internal Terminology & Shorthand

| Term | Meaning |
|------|---------|
| **FID** | First Investment Done — user's first transaction on any Groww product |
| **RID** | Repeat Investment Done — second+ transaction, habit signal |
| **NTU** | New Transacting User — user who transacted for first time in a period |
| **CrossSell FID** | First investment in a second product by an existing investor |
| **D7** | Day 7 metric — activation/onboarding % at day 7 of registration |
| **TTU** | Activity cut + transaction cut — defines active vs lapsed (confirm threshold) |
| **MBR** | Monthly Business Review — reporting event, not a standalone metric |
| **MAI** | Monthly Active Investors (users who transacted in a month) |
| **KYC done** | Users who completed KYC but haven't invested yet — key activation cohort |
| **9:15** | Market open time — Yash owns comms strategy around this daily trigger |
| **BAU comms** | Business As Usual — regular planned campaigns, vs adhoc event-driven |
| **Journeys** | Automated drip/lifecycle communication sequences |
| **NARAD** | Groww's internal CRM tool for campaign management |
| **Comms 360** | Cross-channel communication performance dashboard |
| **Audience Manager** | Tool to build user cohorts/segments for targeting |
| **Superset** | BI/dashboarding tool (Apache Superset) |
| **SIP starts** | Number of new SIPs initiated in a period |
| **SIP persistence** | % of SIPs still active after N months |
| **Invest & Instigate** | Shweta's strategy stream — nudging users from browse to invest |
| **GTM comms** | Go-to-market communications for new product/feature launches |
| **DTU** | Daily Transacting User — users who transact on a given day (tracked per product) |
| **MTU** | Monthly Transacting User — users who transact at least once in a month |
| **ATU** | Active Transacting User — user with AUM > 0 in a product |
| **CNTU** | Cross-sell NTU — first transaction in a second/new product by an existing investor |
| **PPU** | Products Per User — active transacting products per user / active users (the recommended "Active PPU" version) |
| **GCG** | Global Control Group — 5% of users held out from all promo comms; 30-day holdout baseline for measuring incremental uplift |
| **Incremental uplift** | Lift in metric (DAU, NTU, DTU) for treatment group vs GCG |
| **MTA** | Multi-Touch Attribution — attribution model for long-window conversions (NTU, CNTU, Reactivation, Cross-sell) |
| **App Affinity** | DAU/MAU ratio — measures depth of daily engagement within monthly active users |
| **CLTV** | Customer Lifetime Value — strategic priority metric for which users to invest engagement effort in |
| **Business Layer** | Strategic framework: 1 RID message + 1 CrossSell message per user per month (CLTV × Capacity model) |
| **Campaign Affinity / MAB** | ML-driven campaign selection using Multi-Armed Bandits — routes each user to the most relevant campaign. ~50% of TTU have ≥1 campaign affinity score |
| **Resurrection** | Lapsed users who returned to the app and transacted again |
| **Push DND** | Push Do Not Disturb — users who have opted out of push notifications |
| **BBPS** | Bharat Bill Payment System — bill payment feature; one of the products counted in Active PPU |
| **AA** | Account Aggregator — regulatory framework enabling financial data sharing across institutions |
| **ATH** | All Time High — used in market context (e.g., Nifty at ATH) |
| **WBR** | Weekly Business Review — weekly reporting cadence (distinct from monthly MBR) |
| **JAS** | Jul-Aug-Sep quarter |
| **OND** | Oct-Nov-Dec quarter |
| **JFM** | Jan-Feb-Mar quarter |
| **TTU-MAU%** | Retention metric: % of TTU in month M who also transact in month M+1. Benchmark ~73% (Jan 2024) |
| **App-Keep TTU MAU%** | MAU% among TTU who kept app installed. Benchmark ~87% (ATH, Jan 2024) |
| **OB** | Onboarding — the KYC completion process (Signup → OTP → PAN → BV → Digilocker → Esign) |
| **BV** | Bank Verification — one of the KYC steps; 35% drop-off at this step |
| **PP visits** | Product Page visits — behavior milestone tracked pre-FID; PPvisit≥2 or ≥5 used as intent signal for targeting |
| **L30D / L150D** | Last 30 days / Last 150 days — activity recency labels for user cohorts (e.g., "L150D+ Active base" = users last active 150+ days ago) |
| **Non-OB / OB (in experiments)** | Not onboarded / Onboarded (KYC completed) — key split in reactivation experiment targeting |
| **FID CAC** | Cost of Acquiring a user to their First Investment Done — benchmark: WA = 1/5th to 1/10th of remarketing |
| **COSMOS flow** | Journey/automation system at Groww. WhatsApp onboarding journeys implemented in COSMOS. Relationship to NARAD/WebEngage TBD. |
| **BIC** | Business Initiated Conversation (WhatsApp) — marketing/promotional messages. Price: 73p/message (up from 51p) |
| **UIC** | User Initiated Conversation (WhatsApp) — reply/conversational messages. Price: 33p |
| **ISIN** | Instrument identifier for specific stock/bond — used in instrument affinity model |
| **Cold start problem** | Challenge of personalizing for brand-new users who have no behavioral history on the app |
| **Account opening cost** | Rs.44/user — fully loaded cost for each KYC completion |
| **PPI / PPU** | Products Per Investor (same as PPU) — number of distinct products user has invested in |
| **DTU** | Daily Transacting User — a user who transacts on a given day; key metric the ML Product Affinity model optimizes for |
| **PA calendar** | Product Affinity calendar — daily schedule of which product to promote for each user segment, derived from ML model output |
| **SGB** | Sovereign Gold Bond — GOI-issued gold bonds; sold in periodic series; 3-4.5% CTR on TTU base |
| **Retention Propensity Model** | ML model predicting each TTU user's probability of transacting next month; splits base into deciles; High Risk = decile 1,2,3; High Potential Inactive = decile 8,9,10 |
| **BQ** | BigQuery — Groww's data warehouse; daily pipeline: BQ → Audience Manager → WebEngage |
| **FC (Frequency Cap)** | Maximum number of messages per user per period; currently managed at segment level |
| **Digest** | Weekly email digest with market updates and portfolio summary; high email open/read rates even among inactive TTU |
| **GrowwFlix** | Groww's video/content initiative; used as engagement and resurrection hook |
| **IPO Corner** | Campaign property for multiple smaller IPOs simultaneously |
| **PA (Product Affinity)** | ML model outputting per-user product preference probabilities for next-day transactions; P1 = highest affinity product, P2 = second |
| **High Risk (Decile 1,2,3)** | TTU users most likely to churn in coming month per retention propensity model; mostly PPI=1, low AUM |
| **High Potential (Decile 8,9,10)** | Inactive TTU users most likely to resurrect; active in last 2 months, some AUM |
| **Revive** | Campaign property: WA-based portfolio update sent to inactive>30D TTU users with AUM>Rs.100 every week (Tue=MF, Wed=CNC) |
| **C-MAB** | Contextual Multi-Armed Bandit — ML algorithm (Thompson Sampling) for selecting best PN per user per slot; V1 result: 40% CTR uplift + 3% DTU uplift |
| **Thompson Sampling** | Probabilistic MAB algorithm; outperforms UCB for push selection; balances explore/exploit using Bayesian probability |
| **Template Fatigue Penalty** | Reduces C-MAB score for recently sent campaign templates to avoid repetition and boost content variety |
| **Eligibility Filtering** | C-MAB filter: only shows user a campaign if they have relevant holdings/watchlist (e.g., holdings PN only if user has holdings) |
| **Widget Ranker Engine** | C-MAB-powered on-app widget ranking system for Stocks Explore; 4 widget slots ranked daily; goal: improve NTU conversion |
| **BFF (Backend for Frontend)** | Tech pattern enabling on-app MAB personalization via real-time ML inference |
| **EMS** | Event Management System — real-time events pipeline replacing WebEngage for C-MAB; will reduce content affinity lag 2D → 1D |
| **RFM** | Recency, Frequency, Monetary — rule-based user segmentation (pre-ML baseline); now replaced by ML affinity models for TTU comms |
| **Aampe** | External AI-agentic tool for PN content/segmentation/distribution; evaluated Sep-24; rejected (too expensive: 10.2L for 5M POC for 8M MAU) |
| **OI** | Open Interest — total outstanding F&O contracts; used in campaign content ("Top options by High OI") |
| **S&R** | Support and Resistance — technical analysis concepts used in F&O content personalization |
| **Expiry day** | F&O contract expiry date (weekly for Nifty, monthly for others); high-intent moment for F&O traders |
| **Carryforward users** | F&O users with overnight positions (didn't close for the day) — a distinct user segment |
| **Golden crossover** | Positive moving average crossover (bullish signal) — used as campaign trigger |
| **Death crossover** | Negative moving average crossover (bearish signal) — used as campaign trigger |
| **Price breakout** | Stock breaking through a key resistance/support level — daily campaign trigger |
| **Block/Bulk deal** | Large institutional trades (>5L shares or >5Cr value) — weekly campaign trigger |
| **Purchase abandonment** | Users who showed buy intent (clicked StartSIP/One-Time ≥2 times in L30D) but didn't complete the purchase |
| **StartSIP / One-Time** | MF CTAs: StartSIP = initiate an SIP; One-Time = make a lumpsum investment |
| **In-house CM** | New internal Campaign Manager being built (beyond NARAD/WebEngage) — required for instrument affinity and MF purchase abandonment scale-up |
| **ESP** | Email Service Provider — external vendor that sends emails on Groww's behalf (e.g., Netcore, AWS) |
| **Netcore** | Email ESP used by Groww; scaled to 10M/hr; subdomain: digest.groww.in |
| **FCM** | Firebase Cloud Messaging — Google's push delivery infrastructure; pipeline: WebEngage → FCM → User device |
| **GrowwFlix** | Groww's YouTube-linked educational email property; 3 versions (MF, Stocks, Trading); 7M users; 30% open rate; drives YouTube subscriber growth |
| **Daily Digest** | Daily market update email to 15M users; sent 7:30-8pm; MAU declining (13M Oct-24 → 8M Mar-25) |
| **Weekly Digest** | Weekly market/portfolio summary email; optimized to 11M targets (from 24M); same 2.1M opens; saved Rs.7-8L/month |
| **Domain reputation** | Email deliverability score; maintained by controlling send volume, open rates, spam complaints |
| **Domain warmup** | 30-day ramp from 100 → 10M emails to build new subdomain reputation; needs >20% open rate |
| **Inboxing** | Whether email lands in Primary vs Promotions/Spam; salesy subject lines → Promotions = lower open rate |
| **Spam rate** | % emails marked as spam; spike to 68% caused a Digest open rate crash (23-Apr inboxing incident) |

*Add terms as you encounter them.*

---

## 📂 Reference Files on Desktop

| File | Purpose |
|------|---------|
| `Growth Vertical - Master Reference.md` | Full annotated source of truth — pods, people, metrics, open questions |
| `Growth Vertical - Overview.md` | Clean presentable summary — for meetings |
| `Growth Vertical - Concepts & Notes.md` | Educational deep-dive — growth concepts explained for an engineering background |
| `groww-context.md` | This file — skill's context store |

---

## 📝 Session Notes

> Key decisions or context from recent conversations

### 2026-03-26 — Batch 1 PDF Processing (6 Strategy & Foundations docs)

**Key findings from Batch 1:**
- Campaign volume: **~3 Billion communications/month** across all channels (Feb 2024 data)
- Business Layer: Each user gets max **1 RID nudge + 1 CrossSell nudge/month** from the strategic layer (CLTV × Capacity model)
- GCG holdout: **5% permanent holdout, 30-day window** for measuring incremental uplift
- Campaign Affinity (MAB): ~50% of TTU have ≥1 campaign affinity score
- Non-TTU campaign benchmark: +55-60% DAU uplift, +75% NTU uplift at Day 15 vs GCG
- Personalized TTU comms: Peak DAU +11% vs GCG
- 52W H/L personalized alerts CTR: **12%** (vs ~3% generic = 4X)
- TTU-MAU% retention benchmark: ~73% (up from ~70%, Jan 2024)
- App-Keep TTU MAU%: ~87% (ATH, Jan 2024)
- The 3-part engagement strategy: Part 1 = off-app comms (live), Part 2 = on-app personalization (in progress), Part 3 = combined (future)
- NARAD is Groww's in-house CRM; WebEngage handles push notification throughput at scale
- Low/Mid active users have higher incremental lift than high-active users from comms
- High-LTV users: focus on retention (session quality), not just engagement volume

### 2026-03-26 — Batch 2 PDF Processing (7 Activation Funnel docs)

**Key findings:**
- Activation funnel exact steps confirmed: Signup → OTP → PAN → BV → Digilocker → Esign → [Product Browse] → FID
- **Only 26% complete Signup → Esign within 7 days**; biggest drop: OTP→PAN (40%), PAN→BV (35%)
- WhatsApp at the Esign step: 30% conversion uplift → live at 100%; ~200 incremental Esigns/day; ₹145/conversion
- WA FID CAC = 1/5th of remarketing (Non-OB users), 1/10th (OB users) — dramatic cost advantage
- ~50% of non-investor app-keep users are NOT reachable via push
- Push reachability for L150D+ inactive base: ~1.5%
- NTU → CNTU: ~70% within 3 months, ~80% within 24 months
- Account opening cost baseline: Rs.44/user
- COSMOS flow = WhatsApp journey system (confirm relationship to NARAD/WebEngage)
- "Cold start problem" = open problem: how to personalize for new users with no behavioral history
- PP visits (≥2, ≥5) used as intent signal to identify ready-to-target inactive users
- Instrument affinity available at ISIN/Fund level but manually scheduled → being automated into NARAD

### 2026-03-26 — Batch 4 PDF Processing (11 Personalization & ML docs)

**Key findings:**
- C-MAB (Thompson Sampling): V0 = 34% CTR uplift; V1 = **40% CTR + 3% DTU** (even when only optimizing CTR)
- Generic PN click retention: 28% Week 1 → **5% by Week 40** — rapid decay driving MAB need
- 52% of promotional PNs are still generic (not personalized)
- ML RID: +6% CTR, +1.3% DTU vs RFM baseline; ML Cross-sell: +3.2% Cross-sell FID
- PA model accuracy: 73% overall; MF only 55% (explains negative MF results in PA experiment)
- CNC Explore = 48% of Groww NTU; MF Explore = 62-66% of MF NTU
- MF Purchase Abandonment: buy intent ≥2 clicks → +7,800 lumpsum orders at scale (+5%)
- F&O TTU Index personalization: 6-10% PN CTR uplift; DAU/session impact minimal
- Aampe (external AI push tool) evaluated Sep-24 → rejected (too expensive)
- New people: Preksha Vyas (PA personalization), Ritvik Pandey (MF TTU), Anshul+Saurabh (tech/ML)
- Widget Ranker Engine = MAB-powered on-app ranking for Stocks Explore (BFF dependency)
- In-house Campaign Manager (CM) being built — required for instrument affinity and MF automation scale-up

### 2026-03-26 — Batch 5 PDF Processing (6 Channel Strategy docs)

**Key findings:**
- Email: 99% delivery, 18-20% open rate; cheapest channel; large form factor
- Digest readership declining sharply: Daily Digest MAU 13M (Oct-24) → 8M (Mar-25)
- Weekly Digest optimized: 24M → 11M target users → same 2.1M opens; saved Rs.7-8L/month
- GrowwFlix = YouTube-linked email property; TTU +1.7% MAU, Non-TTU +0.71% MAU; YT Trading channel +27% subscribers
- Email pipeline: WebEngage → Netcore (ESP) → User; throughput scaled to 10M/hr (from 2.2M)
- Push throughput: WebEngage 75K/min → 250K/min; FCM latency improved 50%; net DAU +0.5-0.6%
- Push banners: No major CTR uplift (didn't replicate industry's 60% claim)
- New people: Juie Shah (PN), Shivam Chopra (analytics)
- Email strategy: shifting from Digest-heavy to objective-based (Activation, Reactivation, RID, Brand Recall)

### 2026-03-26 — Batch 3 PDF Processing (7 TTU & Retention docs)

**Key findings:**
- **3.2 Million TTU become inactive every month** — retention is a massive scale problem
- Retention Propensity Model splits TTU into deciles: High Risk (1,2,3) and High Potential Inactive (8,9,10)
- High active TTU: NO uplift from ML affinity comms (they self-direct their transactions)
- Mid/Low active TTU: ML affinity drives +6% CTR, +1.3% DTU, +7% session attribution
- WA brings inactive users back to app but NOT effective for driving transactions
- WA resurrection cost for Power Users: Rs.75/user
- Cross-sell ML experiment: mixed results; 14D window too short; 30D needed
- Revive: WA portfolio update to inactive>30D TTU with AUM>Rs.100 (weekly: Tue=MF, Wed=CNC)
- SGB = Sovereign Gold Bond (confirmed); SGB CTR on TTU: 3-4.5%; IPO CTR: 4%
- PA Calendar = Product Affinity calendar — the daily scheduling system for ML-targeted comms
- Digest = weekly email digest; email reachability is consistently HIGH even for inactive TTU
- BigQuery confirmed as data warehouse; pipeline: BQ → Audience Manager → WebEngage (daily)
- Instrument Affinity for TTU pending compliance approval
