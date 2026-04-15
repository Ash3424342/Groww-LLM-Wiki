---
title: CNC Personalization Ladder
date_updated: 2026-04-05
tags: [concept, strategy, cnc, alerts]
---

# CNC Personalization Ladder

Progression of CNC (Stocks) alert types from generic to highly personalized, ranked by CTR performance.

Intent definition: Holdings OR Watchlist OR PP-visits >4 in L7D. Attribution: 12-min post PN.

```
Generic "Stocks in Spotlight" (3% CTR)      ← baseline
  ↓
Automated Stock News (4-7% CTR)
  ↓
Price Alerts ±5% (3.5-8% CTR)
  ↓
52W High/Low (11-13% CTR)                   ← 4X generic
  ↓
50/150 DMA breakout (9-17% CTR)
  ↓
200 DMA breakout (14-19% CTR)               ← BEST
  ↓ Next
C-MAB auto-selection per user
```

## Key Stats

| Alert | CTR | Session Conversion ⚠️ |
|-------|-----|--------------------|
| 200 DMA breakout | **14-19%** | **40-51%** |
| 52W High/Low | 11-13% | 33-37% |
| 50 DMA | 11-17% | 32-45% |

⚠️ **"Session Conversion" definition unconfirmed.** Likely: % of PN clickers who open an app session within 12-min attribution window (per CNC alert targeting docs). Could also mean: % of sessions resulting in a transaction. (Source: Master Reference v2, CNC Personalized Alert Benchmarks section)

200 DMA = 200-day moving average. Crossing it = major technical signal.

## People

[[ritvik]] (analytics), [[amit]] (instrument affinity ML)

## Related

- [[push-notifications]] — delivery channel
- [[instrument-affinity]] — ML model powering stock selection
- [[narad]] — campaign automation
