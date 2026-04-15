# Groww Growth Vertical — Overview

---

## What the Vertical Does

Drives user **activation** and **retention** across all Groww products through targeted communications, personalization, and lifecycle management.

Two primary goals:
- **0→1 (Activation):** KYC-done users → First Investment Done (FID)
- **1→N (Repeat):** Keep investors transacting across products (RID)

---

## Pod Structure

| Pod | Sub-pod | Core Focus | Products |
|-----|---------|-----------|---------|
| **Invest** | Activation | 0→1: KYC → First Investment (FID) | MF, Stocks, Gold, FDs, IPO, US Stocks |
| **Invest** | RID | Repeat transactions after FID | CNC, ETF, Bonds, IPO, MF |
| **Invest** | Personalization | ML-driven hyper-personalized comms | All invest products |
| **Trading** | — | FID + RID for trading products | FnO, Commodities, MTF, MIS |
| **Other Businesses** | — | Growth for wealth & AMC products | Wealth (Fisdom), Groww AMC |

---

## People

| Name | Pod | Role | Owns |
|------|-----|------|------|
| **Aastha** | Trading | Strategy | Trading pod |
| **Nikhil** | Invest | Strategy | Activation strategy, WhatsApp channel, RID strategy |
| **Shweta** | Invest | Strategy + Execution | Invest & Instigate strategy, Comms Orchestration (RID) |
| **Himanshu** | Invest | Strategy + ML | RID strategy, ML personalization models |
| **Amit** | Invest | Strategy | MF strategy, Invest pod ownership |
| **Aishwarya** | Invest | Execution | Campaigns, RCS, SMS, In-app Stories |
| **Yash** | Trading | Strategy + Channel | Trading strategy, 9:15 comms, WhatsApp |
| **Samir** | Trading | Execution | Trading pod campaigns |

---

## Key Metrics

| Metric | Meaning | Pod |
|--------|---------|-----|
| **FID** | First Investment Done — user's first transaction | Activation, Trading |
| **RID** | Repeat Investment Done — habit signal | RID, Trading |
| **NTU** | New Transacting User — activation endpoint | Activation |
| **CrossSell FID** | FID in a second product by an existing investor | RID, Trading |
| **D7** | Onboarding % at Day 7 post-registration | Activation |
| **Onboarding %** | Step-by-step funnel completion rate | Activation |
| **Convert rate** | % of users moving from one funnel step to the next | All |
| **Dropoff rate** | % of users leaving at a given funnel step | All |
| **TTU** | Activity + transaction cut — defines active vs lapsed | RID |
| **WBR / MBR** | Weekly / Monthly Business Review | Reporting |

---

## Activation Funnel (0 → FID)

7-8 steps from registration to First Investment Done.

```
Sign-up / App install
    ↓
KYC initiation
    ↓
KYC steps (PAN / Aadhaar / Bank)
    ↓
KYC completion
    ↓
Account activation
    ↓
First product browse / watchlist
    ↓
Investment initiation
    ↓
   FID  →  user becomes NTU
```

At each step: measure Convert rate and Dropoff rate → design targeted comms to move users forward.

---

## Personalization Engine

**Signal source:** App activity (what users browse, hold, and watchlist)

| Layer | How it works |
|-------|-------------|
| Generic | Broad segment — same message to a defined cohort |
| Personalized | User-level signals: holdings, watchlist, ML model outputs |

**ML models (2-3 models):**

| Model | Output |
|-------|--------|
| Product affinity | Top 2 products the user is likely to transact in next day |
| Instrument affinity | Top stock/fund/instrument for the user |
| Time activity | Optimal send time per user |
| **Combined** | Right product + right instrument + right time = personalized daily nudge |

---

## Channels

| Channel | Type | Owner |
|---------|------|-------|
| Push Notifications | Off-app | All pods |
| WhatsApp | Off-app | Nikhil (channel manager), Yash (trading) |
| Email | Off-app | — |
| RCS | Off-app | Aishwarya |
| SMS | Off-app | Aishwarya |
| In-app Stories | On-app | Aishwarya |

---

## Communication Types

From reactive to automated — a progression:

```
BAU Comms          Regular planned campaigns (daily / weekly)
Adhoc Comms        Reactive to market events or news
Mid-Market Action  Real-time triggers during market hours
      ↓
Personalized Comms ML-driven, per-user (refreshed daily)
      ↓
Journeys           Automated lifecycle sequences (behavior-triggered)
```

---

## How a Campaign Gets Sent

```
1. Define Cohort      →  Who are we targeting? (e.g., KYC done, no FID, active D3–D7)
2. Create Content     →  Write copy, apply personalization variables
3. Audience Manager   →  Segment Query → pull matching users
4. Send               →  Via NARAD / WebEngage, with timing + frequency caps
5. Measure            →  CTR, conversion (FID/RID), dropoff → report in Comms 360 / WBR
```

---

## Tools

| Tool | What it's for |
|------|--------------|
| NARAD | Groww's internal CRM — campaign management |
| WebEngage | External CRM — push, email, in-app orchestration |
| Audience Manager | Build and query user segments |
| Superset | Dashboards and data visualization |
| User Engagement Dashboard | Top-level UE metrics |
| Comms 360 | Cross-channel campaign performance |
