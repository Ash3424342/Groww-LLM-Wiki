---
title: Stocks / CNC (Cash & Carry)
date_updated: 2026-04-06
tags: [entity, product]
---
# Stocks / CNC
Regular equity buy/hold product (not intraday). CNC = Cash and Carry.
## Key Stats
- CNC Explore = 48% of Groww NTU, 33% of Cross-sell CNC FID
- Within Explore: Most Bought/Traded = 76% of Explore NTU
- 200 DMA breakout alert CTR: **14-19%** (best performing alert)
- Cross-sell uplift: +1.5%
## Pod Ownership
[[invest-rid-pod]], [[invest-activation-pod]]
## Key Tables (Compass)
- `core_stocks_order` (core_invest, 2.5B rows) — partition: `order_date`
- `fact_transaction_stocks` (core_invest, 7.1B rows) — partition: `order_date`
## Related
- [[cnc-personalization-ladder]] — alert CTR progression
- [[instrument-affinity]] — top stocks per user
