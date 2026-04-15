# Groww — Campaign Library

> Active campaigns, SOPs, templates, frequency rules, targeting rules, what's live vs tested.
> Pre-populated from internal PDF docs (2026-03-27). Add campaign configs, briefs, and SOPs as you dump them.

---

## Campaign Taxonomy

```
Communications
├── BAU Comms          — planned, regular, broad (e.g., weekly market update push)
├── Adhoc Comms        — reactive, event-driven (e.g., IPO open, market event)
├── Mid-Market Action  — real-time triggers during market hours (intraday)
├── Personalized Comms — ML-driven, user-specific (right product + right time per user)
├── Journeys           — automated lifecycle sequences triggered by user behavior
└── GTM Communications — go-to-market for product/feature launches
```

---

## Daily Push Notification Slot Structure

Onboarded user campaigns run in 4 structured daily time slots:

| Slot | Time | Content type | Products |
|------|------|-------------|---------|
| **Slot 1** | ~9:45 AM | Opening Bell — market open context, overnight developments | Stocks, MF |
| **Slot 2** | ~11:00–12:30 PM | Market Action / Stock properties — intraday signals | Stocks, F&O |
| **Slot 3** | ~1:30 PM | Stock Collections — curated lists (trending, large cap, sectoral, 52W high/low) | Stocks |
| **Slot 4** | ~3:45 PM | MF Collections — fund categories (high return, SIP, popular funds, gold funds) | MF |

> Weekends: no Slot 2/3 (market closed). MF content runs on weekends (SIPs). Each slot has 5+ content variations for A/B testing and personalization.

**CMAB slots (within onboarded base):**
- **CMAB-1**: First personalized slot — Opening Bell variants (global, pre-open, BAU, sector, movement title, news, top mover, etc.)
- **CMAB-2**: Second personalized slot — Stock property variants (MA, Sector, Trending, Volume, Large cap, RSI)
- **BAU**: Non-CMAB standard campaigns (same content for all eligible users in slot)
- **CG**: Control Group campaigns — mirror of BAU but tracked separately as holdout

---

## Onboarding Journey Touchpoints

Channel mix per drop-off stage (from journey config):

| Journey stage | Duration | Channels | # Touchpoints |
|--------------|---------|---------|--------------|
| Install → Signup | 3 days | Push | 3 PN |
| Welcome on Signup | 1 day | Email | 1 Email |
| Mobile Verification drop-off | 4 days | Push + Email | 5 PN + 2 Email |
| PAN drop-off | 6 days | Push | (TBC) |
| Bank Verification drop-off | 6 days | Push + WA + SMS + RCS + Email | 7 PN + 2 WA + 4 SMS + 2 RCS + 3 Email |
| Digilocker drop-off | — | Push + WA + Email | (TBC) |
| Selfie drop-off | — | Push | (TBC) |
| Signature drop-off | — | Push | (TBC) |
| Esign drop-off | — | Push + WA | (TBC) |
| FID drop-off | — | Push + WA + Email | (TBC) |

> Bank drop-off uses the most channels (5 channels) — highest-stakes drop point. Earlier steps (mobile verification) use fewer channels. Channel escalation pattern: Push → Email → WA/SMS/RCS as urgency increases.

---

## Live Campaigns (as of docs)

### Onboarding Journeys (Activation Pod)

| Campaign | Channel | Trigger | Status | Result |
|---------|---------|---------|--------|--------|
| KYC drop-off WA journey | WhatsApp | User drops at any KYC step | **Live** | ~200 incremental Esign/day; ₹145/conversion |
| WA at Esign step | WA | User reaches Esign step | **Live** | +30% conversion uplift |
| 7-day post-install push sequence | Push | App install | Live | Standard activation |

### RID / Retention (RID Pod)

| Campaign | Channel | Trigger | Cadence | Status |
|---------|---------|---------|---------|--------|
| Portfolio Update (Revive) | WhatsApp | TTU inactive >30D, AUM>100 | Tue (MF) + Wed (CNC) weekly | **Live (Apr rollout)** |
| PA Calendar comms | Push | Daily, per affinity model output | Daily | **Live** |
| C-MAB push selection | Push | Per user per eligible slot | Real-time | **Live** (5 models for TTU) |
| Campaign Affinity V1 | Push | Per user per slot | Real-time | **Live** (Thompson Sampling) |
| GrowwFlix email | Email | Weekly | Weekly | **Scaled** (7M users) |
| Daily Digest | Email | Daily | Daily 7:30-8pm | **Live** (8M users, declining) |
| Weekly Digest (optimized) | Email | Weekly | Weekly | **Live** (11M targeted, 2.1M opens) |

### Reactivation (Cross-pod)

| Campaign | Channel | Target | Cadence | Status |
|---------|---------|--------|---------|--------|
| WA reactivation (Non-OB) | WhatsApp | Inactive non-investors | 1-2x/month | **Scaled** (300K users) |
| WA reactivation (OB users) | WhatsApp | Inactive onboarded users | 1-2x/month | **Live** |
| Remarketing | Google/FB | L150D+ inactive non-investors | Continuous | **Live** |

### F&O Automated Campaigns (NARAD — Trading Pod)

20+ campaigns running via NARAD pipeline. All market-triggered.

| Campaign | Trigger condition | Channel |
|---------|-----------------|---------|
| PCR alert (30min) | PCR crosses threshold in 30 min | Push |
| PCR alert (day) | PCR crosses threshold for the day | Push |
| OI surge alert | OI increases >X% in window | Push |
| OI drop alert | OI drops >X% in window | Push |
| ATM straddle (30min / 1hr / day) | ATM straddle price moves | Push |
| Long buildup | OI↑ AND price↑ for contract | Push |
| Short buildup | OI↑ AND price↓ for contract | Push |
| Covering | OI↓ AND price↑ | Push |
| Unwinding | OI↓ AND price↓ | Push |
| OI Buildup contracts alert | Contracts with significant OI buildup | Push |
| Put/Call OI Change | Unusual put or call OI shift | Push |

### CNC Personalized Alerts (CNC Sub-pod)

| Campaign | CTR | Status |
|---------|-----|--------|
| 200 DMA breakout | 14-19% | **Live / scaling** |
| 50 DMA breakout | 11-17% | **Live** |
| 52W High/Low | 11-13% | **Live** (450K daily reach) |
| Price Alert (±5%) | 3.5-8% | **Live** |
| Automated Stock News | 4-7% | **Live** |

### Onboarded Non-TTU — Daily Push Calendar (BAU)

Content strategy for onboarded users who haven't yet transacted. Two strategy axes:

**By affinity difference (LD vs HD):**
- **LD segments** (Low Difference): user has similar interest in both products — content can go either way; mix P1 and P2 content
- **HD segments** (High Difference): user strongly prefers P1 — lead with P1 content, use P2 as cross-sell

**By product affinity (P1):**

| Affinity | Weekday content pattern | Cross-sell opportunity |
|---------|------------------------|----------------------|
| **Stock affinity** | Opening bell → Market action / trending stocks → Large cap / sectoral → Gainers/losers | P2: MF collections (Slot 4) or F&O (pre-market, OI) |
| **F&O affinity** | Pre-market daily → OI alerts → Expiry alerts → Most traded | P2: Stock collections or MF |
| **MF affinity** | Opening bell → Popular funds / trending MFs / Market update → SIP / collections | P2: Stock content (trending, large cap) |
| **No affinity (OB)** | Opening bell → Single stocks / market action → Sectoral / 52W high-low → Value props | Both stocks + MF |

**Signup segment (not yet onboarded, app-active):**
- Slot 1 (9:45 AM): Opening bell — stock educational
- Slot 2 (12:30 PM): Market action
- Slot 3 (11 AM): Stock properties with "Complete onboarding" CTA
- Slot 4 (3:45 PM): MF collection with "Complete onboarding" CTA

### IPO & SGB (RID Pod)

| Campaign | Channel | Targeting | CTR | Status |
|---------|---------|----------|-----|--------|
| IPO comms | Push + Email | PA Calendar; intent segments (applied L3M, PP visits >3, Apply clicked) | 4% (TTU) | **SOP live** |
| SGB comms | Push | TTU base | 3-4.5% | **SOP live** |

---

## Frequency Rules & Caps

| Channel | Rule | Source |
|---------|------|--------|
| WhatsApp | ~3/month for reactivation (1/week max); industry: 1/week major brands, 2/week Swiggy | WA Strategy doc |
| WA for inactive TTU | 1x/month (PU); 1x/month Email additional | PU Testing SOP |
| Cross-sell PN | 5/week (Next Best Product experiment) | Cross-sell experiment |
| F&O NARAD campaigns | Real-time (market-triggered); no explicit daily cap found | NARAD doc |
| DND / Push opt-out | PPI=1 users: high DND risk on cross-sell. PPI>1, high-engagement: safe | Cross-sell experiment |

---

## Targeting Rules & Eligibility

### Intent Signals (by product)

| Signal | Definition | Used for |
|--------|-----------|---------|
| Holdings | User owns this instrument | Personalized alerts |
| Watchlist | User tracking but hasn't bought | High-intent push |
| PP visits ≥2 (L30D) | Product page visited twice | Activation targeting |
| PP visits >3 (L7D) | Recent high-frequency product visit | IPO intent signal |
| PP visits >4 (L7D) + Holdings/Watchlist | CNC TTU high-intent definition | CNC alert targeting |
| Apply clicked (IPO) | Clicked IPO apply at least once | IPO intent |
| Applied L3M (IPO) | Applied for IPO in last 3 months | IPO interest signal |
| Buy intent ≥2 clicks L30D | MF product page + add-to-cart type events | MF purchase abandonment |

### F&O Responsibility Charter Rules (SEBI-aligned)

| Rule | Effective | Detail |
|------|----------|--------|
| F&O cross-sell banned | Jan-24 | Cannot cross-sell F&O to non-F&O TTU base |
| F&O cross-sell restarted | Mar-24 | Only for: F&O onboarded users OR F&O affinity score users |
| MTF same framing | Ongoing | Responsible broker policy applies |
| Pre-apply language | Always | "Pre-apply" NOT allowed in IPO communications |

---

## Campaign Measurement SOPs

### Standard Experiment Setup

| Parameter | Groww standard |
|-----------|---------------|
| Control group | GCG (2-10% by lifecycle stage, 30-day holdout) |
| Statistical significance | 95% (standard) |
| Experiment duration | Min 2 weeks for most; 30D window for cross-sell / NTU-objective campaigns |
| Primary metrics | Metric specific to campaign goal (FID, DTU, resurrection rate, CTR) |
| Guardrail metrics | DND rate (push opt-out); overall DAU; unsubscribe rate |
| Attribution | MTA (Multi-Touch Attribution) for long-window conversions; Time-decay recommended |

### GCG Sizes by Lifecycle Stage

| Cohort | GCG size |
|--------|---------|
| New users (Activation) | 2-5% |
| Active TTU (RID) | 5-10% |
| Churn-risk users | 5-8% |

---

## Campaign SOPs

### WA Portfolio Update (Revive) — SOP

- **Target:** TTU inactive >30D AND AUM > Rs.100
- **Message:** Personalized portfolio update (current value, P&L, market context)
- **Cadence:** Tuesday (MF) + Wednesday (CNC), weekly
- **Channel:** WhatsApp only
- **Measurement:** Resurrection rate (app open + transaction within window) vs GCG
- **Cost:** Rs.75/resurrection (WA PU cost)
- **Status:** Scaled Apr 2024; May-Jun second rollout done

### IPO Communication SOP

- **Targeting tiers:**
  1. Applied L3M (strongest intent)
  2. PP visit >3 in L7D
  3. "Apply clicked" event
  4. TTU base (broad)
- **Content:** IPO Corner in-app property; CTR 4% for TTU
- **Restriction:** "Pre-apply" language NOT allowed per SEBI
- **Channel:** Push + Email

### WA Onboarding Drop-off — SOP

- **Trigger:** User drops at any KYC step (OTP_PAN through SIGN_ESIGN)
- **Journey:** COSMOS-based automated journey
- **Cadence:** Triggered per step; respects frequency caps
- **Result:** ~200 incremental Esign/day; ₹145/conversion
- **Key insight:** Higher-intent steps (closer to Esign) = better WA impact; PAN step exception (large drop = large impact even if early)

---

> **Add campaign briefs here.** Paste a campaign doc, brief, or config and Claude will extract: target audience, channel, objective, creative angle, measurement plan, and result (if available), then file it here.
