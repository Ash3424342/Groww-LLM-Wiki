---
title: ML Models Overview
date_updated: 2026-04-05
tags: [concept, ml, overview]
---

# ML Models Overview

9 models in production or development across the Growth vertical.

| Model | Purpose | Accuracy/Result | Refresh | Status |
|-------|---------|----------------|---------|--------|
| [[product-affinity]] | Next-day top 2 products | 73% overall (MF 55%) | Daily | Live |
| Instrument Affinity | Top stock/fund per user | Top 10: DAU +3% | Daily | Live (Top 10); Top 50 paused |
| Time Activity | Optimal send time | Part of personalization engine | Daily | Live |
| [[retention-propensity]] | P(transact next month) | 10 deciles | Fortnightly | Live |
| [[cross-sell-affinity]] | Next best product | +3.2% CS FID; Pay +23% | 14D window | Live (V0) |
| [[c-mab]] | Best PN per user per slot | +40% CTR, +3% DTU | Continuous | Live (5 TTU) |
| [[campaign-affinity]] | Best campaign format | +20% CTR | Continuous | Live (V1) |
| Widget Ranker | On-app widget order | In progress (prev A/Bs failed) | Daily + RT inference | In progress |
| [[rf-score]] | Story D1 retention | R²=0.254 | Per story | Live |

## Key Learnings

- **CTR ≠ value**: Instrument Affinity Top 50 had +23% CTR but zero DAU impact → paused
- **Transactions matter**: C-MAB V1 added 50% Tx weight to reward function → +3% DTU
- **Widget mix > widget count**: Fewer widgets didn't help NTU; personalizing the mix is the answer
- **Aampe rejected**: Rs.21-32L/month too expensive vs building in-house

## Pipeline Patterns

| Pattern | Models | How |
|---------|--------|-----|
| Daily batch | PA, Instrument, Cross-sell | BQ → Model → AM → WebEngage |
| Continuous bandit | C-MAB, Campaign Affinity | Online learning via WebEngage events |
| Real-time inference | Widget Ranker | BFF per page load |
| Per-content scoring | Rf Score | Scored post-publish |

## Related

- [[personalization-engine]] — ML models are the engine
- [[source-ml-systems]] — detailed specs
