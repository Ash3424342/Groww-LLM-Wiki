---
title: F&O (Futures & Options)
date_updated: 2026-04-06
tags: [entity, product, trading]
---
# F&O (Futures & Options)
Derivatives trading product. Managed by [[trading-pod]].
## Key Stats
- 20+ NARAD automated campaigns (PCR, OI, ATM straddle, buildup)
- F&O NTU share declining post Responsibility Charter (Mar-24) but organic continues
- F&O Explore: very low contribution — Positions + Index Cards are primary drivers
- Cross-sell uplift: +2% (model accuracy weakest for F&O)
## Regulatory
F&O cross-sell restricted to F&O-onboarded or F&O-affinity users only ([[sebi-regulations]])
## Key Tables (Compass)
- `fno_order_master` (core_invest, 3.8B rows) — partition: `pt`
- `fno_pnl_master` (core_invest, 1.9B rows) — partition: `pt`
- `fno_livemonitoring` (~133 rows, real-time)
## Related
- [[narad]] — F&O signal definitions and automated campaigns
- [[trading-pod]] — owning pod
- [[c-mab]] — selects best F&O campaign per user
