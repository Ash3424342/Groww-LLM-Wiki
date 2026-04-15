---
title: Cross-sell Affinity Model
date_updated: 2026-04-06
tags: [concept, ml-model, cross-sell]
---
# Cross-sell Affinity
Predicts next best product for single-product TTU users.
## Specs
- Products covered: F&O, MF, CNC, MIS (Pay & Credit to be added)
- Prediction window: 14 days (30D recommended based on experiment)

  ⚠️ **Why 14D if 30D recommended?** Rationale not documented. See [[open-verification-checklist]] #9.
- Coverage: 70-90% of users; 80-90% of daily DTUs
## Results
| Product | Cross-sell FID uplift |
|---------|---------------------|
| **Pay** | **+23%** |
| F&O | +2% |
| Stocks | +1.5% |
| MF | +1% |
| **Overall** | **+3.2%** |
## ⚠️ PPI=1 Risk
PPI=1 users show DND spike — only safe to target PPI>1, high-engagement cohorts.
## Related
- [[cross-sell]] — the strategy this model powers
- [[cntu]] — the metric it optimizes
