---
title: Push Notifications
date_updated: 2026-04-05
tags: [entity, channel]
---

# Push Notifications

Primary high-volume off-app channel. Pipeline: [[webengage]] → [[fcm]] → User device.

## Benchmarks

All CTRs below are **per-message click rates** (clicks / messages delivered) for specific campaign types, NOT blended daily averages. Blended daily average CTR across all PN types is ~4.3% (source: Compass Engagement skill, typical day funnel: ~3M total → ~19K clicked).

| Metric | Value | Source |
|--------|-------|--------|
| Generic CTR | ~3% | Master Reference v2, 2026-03-26 |
| Personalized CTR (52W H/L alerts) | **12%** (4X generic) | CNC Personalized Alerts, Master Reference v2 |
| 52W H/L alert CTR | 11-13% | CNC experiment, Master Reference v2 |
| 200 DMA breakout CTR | **14-19%** (best single alert type) | CNC DMA experiment, Master Reference v2 |
| Throughput (post-upgrade) | 250K/min | Master Reference v2 |
| Latency improvement | 50% reduction | Master Reference v2 |
| Net DAU attribution | +0.5-0.6% daily | Master Reference v2 |
| Push banners uplift | No major uplift (industry 60% claim did NOT hold) | Master Reference v2 |
| Peak times | 9:30am, 1:00pm, 4:00pm IST | Master Reference v2 |
| L150D+ reachability | ~1.5% (L150D+ = users whose last activity was 31-150 days ago) | Master Reference v2 |
| Non-investor unreachable | ~50% | Master Reference v2 |
| Generic PNs as % of total | ~52% (room for personalization) | Master Reference v2 |
| PN click retention decay | 28% Week 1 → 5% by Week 40 | Master Reference v2 |

## Related

- [[webengage]], [[fcm]] — delivery infrastructure
- [[c-mab]] — selects best PN per user per slot
- [[personalization-engine]] — drives the 4X CTR uplift
