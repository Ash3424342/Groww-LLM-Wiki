# Groww — Vocabulary

> Running glossary of all terms, acronyms, tag names, and naming conventions.
> ✅ = confirmed | ⚠️ = uncertain / partial | ❓ = unknown — needs confirmation

---

## A

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **Active PPU** | Active Products Per User | COUNT(distinct active products per ATU) / COUNT(ATUs). Current cross-sell metric — more stable than old PPU. | ✅ |
| **ATU** | Active Transacting User | User with AUM > 0 in a product | ✅ |
| **AUM** | Assets Under Management | Total value of a user's investments on Groww | ✅ |

---

## B

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **BAU** | Business As Usual | Planned, regular, broad campaigns (e.g., weekly market update push) | ✅ |
| **BBPS** | Bharat Bill Payment System | Bill payments product on Groww (electricity, gas, etc.) | ✅ |
| **BFF** | Backend for Frontend | Tech pattern for real-time ML inference per page load (needed for on-app widget ranking) | ✅ |
| **BIC** | Business Initiated Conversation | WhatsApp message initiated by Groww. Price: 73p/message | ✅ |
| **BQ** | BigQuery | Groww's data warehouse (Google Cloud) | ✅ |

---

## C

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **CAC** | Customer Acquisition Cost | Cost per acquired user/conversion (per NTU, FID, etc.) | ✅ |
| **C-MAB** | Contextual Multi-Armed Bandit | Thompson Sampling ML algorithm selecting best push per user per slot. V1 reward = 50% CTR + 50% Tx. | ✅ |
| **CNC** | Cash and Carry | Regular equity buy/hold stocks product (not intraday) | ✅ |
| **CNTU** | Cross-sell NTU | First transaction in a second product by an existing investor | ✅ |
| **COSMOS** | — | Journey/automation system where WhatsApp flows are built and run | ⚠️ Relationship to NARAD/WebEngage unclear |
| **CTR** | Click-Through Rate | Clicks / messages delivered | ✅ |

---

## D

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **D0 / D1 tags** | Day-0 / Day-1 milestone tags | Compound labels for events on the user's signup/account creation day. D0 and D1 are interchangeable — both mean "on the day the account was made." Format: `D{N}_{milestone}_from_{origin}` | ✅ |
| **D7** | Day 7 | % of a signup cohort who reach a milestone by Day 7. Time-bounded activation signal — distinct from the D0/D1 tag system. | ✅ |
| **DAU** | Daily Active Users | Users who open the app on a given day | ✅ |
| **DDPI** | Demat Debit and Pledge Instruction | Authorization mechanism for pledging stocks held in demat account. `TTU_ddpi_success` = users who've completed this. | ⚠️ Confirm exact use case |
| **DMA** | Daily Moving Average | 200 DMA = 200-day moving average of a stock's price. Crossing it = major technical signal. NOT "Direct Market Access." | ✅ |
| **DND** | Do Not Disturb | Push opt-out / unsubscribe from notifications | ✅ |
| **DTU** | Daily Transacting User | Users who transact on a given day, tracked per product | ✅ |

---

## E

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **EMS** | Event Management System | Real-time events pipeline replacing WebEngage data pipeline for C-MAB (reduces affinity lag from 2D → 1D) | ✅ |
| **Esign** | Electronic Signature | Final step in KYC onboarding — signs the account opening form digitally | ✅ |

---

## F

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **F&O** | Futures & Options | Derivatives trading product | ✅ |
| **FCM** | Firebase Cloud Messaging | Google's push notification delivery infrastructure | ✅ |
| **FID** | First Investment Done | User's first transaction on any Groww product. Primary activation milestone. | ✅ |
| **FPD** | First Pay Done | First Pay transaction by a user | ✅ |

---

## G

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **GCG** | Global Control Group | Permanent holdout from promotional comms. Size varies by lifecycle stage: 2-5% (new users), 5-10% (active), 5-8% (churn-risk). 30-day window. | ✅ |
| **GTM** | Go To Market | Product/feature launch communication strategy | ✅ |
| **GrowwFlix** | — | Groww's YouTube-linked email property — financial education videos (MF, Stocks, Trading). 7M users, 30% open rate. | ✅ |

---

## H

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **HD** | High Difference | In NTU cross-product affinity segments: user has a strong affinity preference for P1 over P2. Lead with P1 content. e.g. `NTU_MF_Stock_HD` = user strongly prefers MF, Stock is secondary. | ✅ |

---

## I

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **IPO** | Initial Public Offering | New stock listings; seasonal high-intent event | ✅ |

---

## J

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **JAS** | Jul-Aug-Sep | Quarter abbreviation | ✅ |
| **JFM** | Jan-Feb-Mar | Quarter abbreviation | ✅ |

---

## K

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **KYC** | Know Your Customer | Regulatory identity verification: PAN, Aadhaar, bank account, selfie, signature. 7-8 step funnel. | ✅ |

---

## L

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **L30D** | Last 30 Days | Active within last 30 days — cohort definition | ✅ |
| **LD** | Low Difference | In NTU cross-product affinity segments: user has similar affinity scores for P1 and P2. Messaging can lean either way. e.g. `NTU_MF_Stock_LD` = user has comparable interest in MF and Stocks. | ✅ |
| **L150D+** | Last 150 Days+ | Active within last 150 days (not last 30) — large inactive base | ✅ |
| **LO** | ❓ | Mentioned as "major metric for overall business." Could be L0 (north-star metric), "Logged On," or something else. | ❓ Confirm |
| **LTCG** | Long Term Capital Gains | Tax on gains from assets held >1 year; 10% rate; first Rs.1L/year tax-free | ✅ |

---

## M

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **MAI** | Monthly Active Investors | Subset of MAU who actually transacted in the month | ✅ |
| **MAU** | Monthly Active Users | Users who open the app at least once in a month | ✅ |
| **MBR** | Monthly Business Review | Monthly performance review cadence | ✅ |
| **MCC Code** | Merchant Category Code | Standardized code identifying merchant type for UPI transactions — used for contextual Pay targeting | ✅ |
| **MF** | Mutual Fund | Mutual funds product | ✅ |
| **MIS** | Margin Intraday Square-off | Intraday trading product — positions must be squared off by end of day | ✅ |
| **MTA** | Multi-Touch Attribution | Attribution model for long-window conversions (NTU, CNTU, reactivation, cross-sell) | ✅ |
| **MTF** | Margin Trade Funding | Leveraged equity trading product | ✅ |
| **MTU** | Monthly Transacting User | Users who transact at least once in a month (used in Active PPU formula) | ✅ |

---

## N

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **NARAD** | — | Groww's in-house CRM + real-time campaign trigger system. Kafka + Spark → master_tables → campaign eligibility engine. | ✅ |
| **NC** | Notification Center | Same as Feed — the in-app content hub (pull product). WAU 243K, DAU 104K, 33% weekly retention. | ✅ |
| **NTU** | New Transacting User | User who transacted for the first time in a given period. Endpoint of the Activation funnel. ⚠️ **Naming collision:** In segment names like `NTU_MF_Stock_LD`, NTU = **Non-TTU** (users who haven't reached TTU status). Two meanings — context determines which. | ✅ |

---

## O

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **OB** | Onboarding | KYC onboarding completion (Esign done) | ✅ |
| **OI** | Open Interest | Total open contracts in a derivative — surge/drop = market activity signal | ✅ |
| **OND** | Oct-Nov-Dec | Quarter abbreviation | ✅ |

---

## P

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **PA** | Product Affinity | ML model predicting next-day top 2 products per user. 73% overall accuracy. | ✅ |
| **PA Calendar** | Product Affinity Calendar | Daily schedule translating PA model output into which product to promote per user | ✅ |
| **PCR** | Put-Call Ratio | Put OI / Call OI. PCR >1 = bearish; <1 = bullish. Used as F&O campaign trigger. | ✅ |
| **PN** | Push Notification | Push notification sent to user's device | ✅ |
| **PP visits** | Product Page visits | User visiting a product's page — intent signal. PP visits ≥2-5 = high intent. | ✅ |
| **PPI** | Products Per Investor | Number of distinct products a user has transacted in (ever). PPI=1 = single-product investor. | ✅ |
| **PPU** | Products Per User | Old cross-sell metric — products transacted ever / TTU. Deprecated; replaced by Active PPU. | ✅ |
| **PU** | Portfolio Update | WA message type showing user their portfolio current value and P&L. Cost: Rs.75/resurrection. | ✅ |

---

## R

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **RCS** | Rich Communication Services | Enhanced SMS with images/buttons — upgrade over plain SMS | ✅ |
| **RID** | Repeat Investment Done | Second+ transaction — habit/retention signal | ✅ |
| **Rf score** | Random Forest score | ML model predicting D1 retention of a Story card. Features: Skip Rate (0.24), Completion (0.23), Action Rate (0.18), Weighted Time (0.16), Screenshot (0.13), Slide Count (0.06). | ✅ |

---

## S

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **S&R** | Support & Resistance | Technical analysis levels — price points where stocks historically reverse. Used in F&O content. | ✅ |
| **SGB** | Sovereign Gold Bond | Government-issued gold investment bonds | ✅ |
| **SIP** | Systematic Investment Plan | Regular automated MF investment (monthly, weekly, etc.) | ✅ |
| **STCG** | Short Term Capital Gains | Tax on gains from assets held <1 year; 15% rate | ✅ |

---

## T

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **TTU** | Total Transacting Users | Users who have crossed both activity AND transaction thresholds. Core active-investor definition. Basis for RID campaigns. | ✅ |

---

## U

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **UE** | User Engagement | The Growth vertical's official name | ✅ |
| **UIC** | User Initiated Conversation | WhatsApp message initiated by the user. Price: 33p/message | ✅ |
| **UPI** | Unified Payments Interface | Real-time payment system (Pay product) | ✅ |

---

## W

| Term | Full Form | Meaning | Status |
|------|-----------|---------|--------|
| **WA** | WhatsApp | WhatsApp channel | ✅ |
| **WAU** | Weekly Active Users | Users who open the app at least once in a week | ✅ |
| **WBR** | Weekly Business Review | Weekly performance review cadence | ✅ |
| **WebEngage** | — | External CRM platform — campaign orchestration, push, email, in-app | ✅ |

---

## Tag Naming Convention

Format: **`D{N}_{milestone}_from_{origin}`**

| Tag | Meaning |
|-----|---------|
| `D0_onboarding` / `D1_onboarding` | User completed full onboarding on signup day (D0 and D1 = same day — interchangeable) |
| `D0_dmat` | User completed Demat account setup on signup day |
| `D1_onboarding_from_signup` | Completed onboarding within Day 1 of signup |
| `D1_NTU_from_signup` | Became NTU (New Transacting User) from signup on Day 1 |

> More tags added here as data schemas are shared.

---

## ❓ Unknown / Confirm

| Term | Where seen | Best guess | Action |
|------|-----------|-----------|--------|
| **LO** | Handwritten notes — "major metric for overall business" | L0 = north-star metric? "Logged On"? | Confirm with team |
| **COSMOS** | WA journey system | Journey automation layer — relation to NARAD/WE unclear | Confirm architecture |
| **CNC-MIS Intent** | Handwritten notes — combined targeting segment | CNC + MIS users grouped together for intent | Confirm exact cohort definition |
