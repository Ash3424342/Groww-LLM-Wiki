---
title: TTU — Total Transacting Users
date_updated: 2026-04-05
tags: [concept, metric, retention]
---

# TTU — Total Transacting Users

Users who have crossed both **activity AND transaction thresholds**. Core active-investor definition. Basis for RID campaigns.

⚠️ **Exact thresholds unconfirmed** — e.g., "≥N transactions AND ≥M app opens in last X days." See [[open-verification-checklist]] #1.

## Benchmarks

| Metric | Value | Date |
|--------|-------|------|
| TTU-MAU% retention | ~73% | Jan 2024 (source: Master Reference v2, 2026-03-26) |
| App-Keep TTU MAU% | ~87% (ATH achieved Jan 2024) | Jan 2024 (source: Master Reference v2) |
| Monthly churn | 3.2M TTU become inactive | 2024 (source: Revive doc via Master Reference) |
| M3/M6/M12 retention | Uptrend | Jan 2024 (source: Master Reference v2) |
| App Affinity (DAU/MAU) | ⚠️ No value given — see [[open-verification-checklist]] #8 | — |
| High-active TTU ML uplift | None — self-direct (already high-engagement; ML nudges don't add incremental lift because these users already transact without comms) | — |
| Mid/Low-active TTU CTR uplift | ~6% from ML affinity | — |
| ML affinity DTU uplift | +1.3% | — |
| WA resurrection cost | Rs.75/user | — |

## Retention Propensity Deciles

| Decile | Segment | Profile |
|--------|---------|---------|
| 1,2,3 | **High Risk** | PPI=1, AUM<500, peak AUM was high → exited, PN reach >90% |
| 8,9,10 | **High Potential** | Active in last 2M, some AUM, low PN reach → use WA/RCS/Email |

## Open Question
- ❓ Exact activity/transaction day cutoffs for TTU thresholds

## Related
- [[rid]] — what keeps users as TTU
- [[retention-strategy]] — preventing TTU churn
- [[ntu]] — naming collision (NTU in segments = Non-TTU)
