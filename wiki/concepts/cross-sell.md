---
title: Cross-sell Strategy
date_updated: 2026-04-05
tags: [concept, strategy, cross-sell]
---

# Cross-sell Strategy

Moving single-product investors to 2+ products.

## Key Insight

**Discovery is NOT the problem.** TTU users have already explored 2.4/3 products. The bottleneck is conversion.

## Benchmarks

| Metric | Value |
|--------|-------|
| NTU → CNTU (3M) | ~70% |
| NTU → CNTU (24M) | ~80% |
| Ever discovered products/user (TTU) | 2.4/3 |
| Bottom Nav discovery | ~100% |
| Comms marginal improvement scope | ~10% |

## ML Experiment Results

Cross-sell Affinity model on L30D Active TTU (3.1M TG, 2 weeks):

| Metric | Result |
|--------|--------|
| Cross-sell conversion | **+4%** |
| Cross-sell product DAU | +3% |
| Overall DAU/Sessions | Same (redirected, not net-new) |
| PN CTR | -10% (expected) |
| User CTR | +8% |

**Product-wise uplift**: Pay +23% (best), F&O +2%, Stocks +1.5%, MF +1%

## ⚠️ PPI=1 Risk

PPI=1 users show **marginal uplift + huge DND spike**. Safe to target only PPI>1 / high-engagement cohorts.

## NTU Recency Pattern

Cross-sell uplift by NTU age: 12M+ > 1M > 3-12M > 2-3M > 1-2M. Very old + very recent NTUs cross-sell best; 2-3M is the trough.

## Related

- [[cntu]] — the metric
- [[cross-sell-affinity]] — the ML model
- [[sebi-regulations]] — F&O cross-sell restrictions
