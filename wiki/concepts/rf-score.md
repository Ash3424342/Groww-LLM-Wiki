---
title: Rf Score — Stories Retention Model
date_updated: 2026-04-05
tags: [concept, ml-model, stories]
---

# Rf Score

Random Forest model predicting **D1 retention** of each in-app Story card.

## Model Stats
- **R² = 0.254** (beats linear regression R²=0.174)
- 248 stories scored
- Score distribution: median 0.288, mean 0.299

⚠️ **R² interpretation unconfirmed** — explains 25.4% of variance. Is this good for Groww's use case? When measured? Still valid? See [[open-verification-checklist]] #14.

## Feature Weights

| Feature | Weight | Signal |
|---------|--------|--------|
| **Skip Rate** | 0.24 | Users voting with swipes (most punishing) |
| Normalized Completion | 0.23 | Actual / expected completion (adjusted for slides) |
| Unified Action Rate | 0.18 | MAX(Deeplink Click%, Share%) |
| Weighted Time | 0.16 | 0.1×P50 + 0.2×P75 + 0.3×P90 + 0.4×P95 |
| Screenshot Rate | 0.13 | Save-worthy signal |
| Slide Count | 0.06 | Fewer = better |

Expected completion formula: `0.9297 - 0.0344 × slide_count`

## Scoring Tiers

| Tier | Score | Quality |
|------|-------|---------|
| A | ≥ 0.325 | High-performing |
| B | 0.262 – 0.324 | Mid |
| C | < 0.262 | Low |

**Optimal story length**: 3-6 slides (7-10 → completion drops)

## Related

- [[in-app-stories]], [[feed-nc]] — the surfaces this model scores
- [[aishwarya]] — Stories channel owner
