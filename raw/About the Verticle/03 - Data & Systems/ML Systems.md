# Groww — ML Systems

> ML model specs, features, training data, inference pipelines, model performance.
> Pre-populated from internal PDF docs (2026-03-27). Add model documentation, feature store schemas, and training configs as you dump them.

---

## Model Inventory

| Model | Purpose | Owner | Status | Version |
|-------|---------|-------|--------|---------|
| **Product Affinity (PA)** | Next-day top 2 product prediction per user | Preksha Vyas (OB/NTU); Himanshu (TTU) | Live | V1+ |
| **Instrument Affinity** | Top stock/fund the user is most likely to act on | Amit Kumar | Live (Top 10); Top 11-50 paused | V1 |
| **Time Activity Model** | Optimal send time per user | — | Live | — |
| **Retention Propensity** | P(user transacts next month) | — | Live | — |
| **Cross-sell Affinity** | Next best product for single-product TTU | — | Live | V0 (PPU=1 scope) |
| **C-MAB (Contextual MAB)** | Best push notification campaign per user per slot | Anshul / Saurabh (eng) | Live (5 TTU models) | V1 |
| **Campaign Affinity** | Best campaign format/template per user per slot | — | Live | V1 (Thompson Sampling) |
| **Widget Ranker Engine** | Best widget order for on-app Stocks Explore | Anshul / Saurabh (eng) | In progress | V0 |
| **Rf Score (Stories)** | D1 retention prediction for each Story | — | Live | Random Forest |

---

## Model Details

---

### 1. Product Affinity (PA) Model

**What it does:** Given a user's app activity, predict the top 2 products they are most likely to transact in the next day.

**Training data:** App activity events (BigQuery)

**Output:** Top 2 product recommendations per user per day

**Accuracy:**
| Product | Accuracy |
|---------|---------|
| F&O | Best (~73%+) |
| MF | **55%** — weakest link; drags overall |
| Overall | **73%** |

**Inference pipeline:**
```
BQ app activity events (daily batch)
  ↓
Model inference
  ↓
Audience Manager (segment: user → top 2 products)
  ↓
WebEngage (PA Calendar — schedules which product to promote per user)
  ↓
Push Notification
```

**Refresh:** Daily

**Applied to:**
- TTU: drives RID campaign targeting (vs RFM baseline → CTR +6%, DTU +1.3%, Sessions +7%)
- D7+ Onboarded non-TTU: CTR↑, Sessions↑ — NO FID conversion uplift yet

**Open issues:**
- MF accuracy 55% — needs improvement
- Pay not yet in scope (to be added)
- FID conversion uplift not proven for OB/NTU segment — further iteration needed

---

### 2. Instrument Affinity Model

**What it does:** Predict the top stock/fund/instrument the user is most likely to act on.

**Training data:** App activity events (BQ) — browsing, watchlist, PP visits

**Owner:** Amit Kumar

**Results:**
| Scope | CTR | DAU uplift | Status |
|-------|-----|-----------|--------|
| Top 10 instruments | Moderate | +3% DAU | Live — automating into in-house CM |
| Top 11-50 instruments | **+23% CTR** | NO DAU impact | Paused (CTR without action = not useful) |

**Learning:** More instruments doesn't help. Quality signal matters more than quantity. CTR without downstream action = zero business value.

---

### 3. C-MAB (Contextual Multi-Armed Bandit)

**Algorithm:** Thompson Sampling

**What it does:** At each eligible slot (push send opportunity), selects the best campaign out of the active pool for each specific user.

**Reward function (V1):** `0.5 × CTR + 0.5 × Transaction rate`
*(V0 was CTR-only — V1 added Tx weight to optimize for business outcomes, not just clicks)*

**Exploration rate:** 10% (explore vs exploit balance)

**Architecture:**
```
Campaign pool (active eligible campaigns per user)
  ↓
C-MAB selects one campaign (Thompson Sampling draws from posterior)
  ↓
Push sent to user
  ↓
Reward observed: click? (50%) + transaction? (50%)
  ↓
Posterior updated → model learns
  ↓
Next eligible slot → cycle repeats
```

**Deployment:**
- 5 C-MAB models live for TTU segments
- 3 Non-TTU C-MABs in progress
- On-app expansion: Widget Ranker Engine (same algorithm, different surface)

**Performance:**
| Version | CTR uplift | DTU uplift |
|---------|-----------|-----------|
| V0 | +34% (post warmup) | — |
| V1 | **+40%** | **+3%** |

**Data lag issue:** Content affinity signal currently 2-day lag (WebEngage pipeline). EMS replacement will reduce to 1 day.

**Industry reference users:** Zomato, Duolingo, LinkedIn, Facebook, Doordash

---

### 4. Campaign Affinity Model

**What it does:** Select the best campaign template/format for each user per time slot.

**V0:** Classical ML — 10-15% CTR lift; F&O CTR 1.5% → 2.4%

**V1:** Thompson Sampling bandit — **20% CTR uplift** (early reads)

**Additional features:**
- **Template Fatigue Penalty:** Reduces score for templates the user has seen many times recently
- **Eligibility Filtering:** Filters out campaigns user isn't eligible for before the bandit selects

**Integration:** NARAD auto-triggers from Audience Manager segments

---

### 5. Retention Propensity Model

**What it does:** Predict probability of each TTU user transacting in the next month. Outputs a decile score 1-10.

**Refresh:** Fortnightly

**Decile interpretation:**
| Decile | Segment | Profile | Best channel |
|--------|---------|---------|-------------|
| 1, 2, 3 (Jan MAU) | High churn risk | PPI≈1; AUM<500; PN reachable >90% | Push (reachable) |
| 4-7 | Mid | Mixed | Mixed |
| 8, 9, 10 (Jan Inactive) | High resurrection potential | Active L2M; some AUM; PN unreachable | WA / RCS / Email |

**Use in campaigns:** Differentiates strategy for High Risk vs High Potential cohorts (different message angles, channels, frequency).

---

### 6. Cross-sell Affinity Model

**What it does:** For single-product TTU users (PPI=1), predict the best next product to cross-sell.

**Products covered:** F&O, MF, CNC, MIS. *Pay & Credit: to be added.*

**Prediction window:** 14 days (too short — 30D recommended based on experiment)

**Coverage:** 70-90% of users; high-confidence predictions cover 80-90% of daily DTUs

**Performance:**
| Product | Cross-sell FID uplift |
|---------|---------------------|
| **Pay** | **+23%** (biggest winner) |
| F&O | +2% (model weakest here) |
| Stocks | +1.5% |
| MF | +1% |
| **Overall** | +3.2% Cross-sell FID vs CG |

**Guardrails:**
- PPI=1 users: DND spike risk — target carefully
- PPI>1, high-engagement: safe to target aggressively
- Cross-sell uplift by NTU recency: 12M+ NTU > 1M NTU > 2-3M NTU (trough)

---

### 7. Widget Ranker Engine

**What it does:** Rank the order of widgets shown on the Stocks Explore screen per user. Uses C-MAB algorithm applied to on-app surfaces (not push).

**Technical requirement:** BFF (Backend for Frontend) — needs real-time ML inference per page load.

**V0 setup:**
- 4 widget slots (reduced from 9)
- 13 widgets in pool
- Daily model refresh; real-time inference

**Stocks Explore context:**
- 51% of users visit Explore BEFORE completing onboarding
- CNC Explore = 48% of Groww NTU; 33% of Cross-sell CNC FID
- MF Explore = 62-66% of MF NTU
- Within Explore: Most Bought/Traded = 76% of Explore NTU

**Previous A/B tests:**
| Variation | Result |
|-----------|--------|
| 1 widget, onboarded users | NTU **-50%** + 40 escalations → stopped after 4 days |
| 4 widgets, onboarded users | NTU **-20%** → stopped |
| 5 widgets, new signups only | NTU flat (no uplift) |

**Key learning:** Reducing widgets alone doesn't improve NTU. The widget MIX is what matters — C-MAB to personalize the mix is the right next step.

---

### 8. Stories Rf Score Model

**What it does:** Predict D1 retention of a Story card (will users come back tomorrow after seeing this?). Used for Stories content ranking.

**Algorithm:** Random Forest
**R²:** 0.254 (RF beats linear regression at R²=0.174)
**Training set:** 248 stories scored

**Feature importance:**

| Feature | Weight | Formula |
|---------|--------|---------|
| Skip Rate | 0.24 | % who swiped past |
| Normalized Completion | 0.23 | Actual / Expected; Expected = 0.9297 - (0.0344 × slide_count) |
| Unified Action Rate | 0.18 | MAX(Deeplink Click%, Share%) |
| Weighted Time Spent | 0.16 | (P50×0.1) + (P75×0.2) + (P90×0.3) + (P95×0.4) |
| Screenshot Rate | 0.13 | % who took screenshot |
| Slide Count | 0.06 | Fewer slides = better |

**Score tiers:**
| Tier | Range | Interpretation |
|------|-------|---------------|
| A | ≥ 0.325 | High-performing |
| B | 0.262 – 0.324 | Mid-performing |
| C | < 0.262 | Low-performing |

**Distribution:** Median 0.288, Mean 0.299. Optimal story length: 3-6 slides.

---

## ML Pipeline Architecture (Shared)

```
Training data source: BigQuery
  ↓
Model training (offline, scheduled)
  ↓
Inference: BQ → Audience Manager → WebEngage (daily batch for most models)
         OR: Real-time inference via BFF (Widget Ranker — on page load)
         OR: Continuous online learning (C-MAB, Campaign Affinity — Thompson Sampling)
  ↓
Campaign execution: WebEngage → FCM (push) / Netcore (email) / WA API
  ↓
Reward observation: click events, transaction events (from EMS)
  ↓ (for bandits only)
Posterior update → next inference cycle
```

---

## Aampe — External Tool Evaluation (Rejected)

**What it is:** AI-agentic PN personalization platform. Keyword tokenization + tonality tagging per user.

**Architecture:** BQ Table → Aampe Engine → WebEngage → User PN

**Evaluation:** Sep-24

**Cost:**
| Scenario | Cost |
|---------|------|
| POC (8M MAU, 5 months) | Rs.10.2L total |
| POC (20M MAU/month) | **Rs.21L/month** |
| Post-POC (ongoing) | **Rs.32L/month** |

**Swiggy learnings from Aampe:**
- 1 PN/day > 2 PNs (frequency discipline matters)
- Thompson Sampling >> UCB (bandit algorithm matters)

**Decision:** Rejected — cost too high + integration complexity too high.

---

> **Add model documentation here.** Paste model spec docs, feature lists, training configs, or evaluation reports and Claude will extract: model purpose, features, performance metrics, pipeline, and open issues.
