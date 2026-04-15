---
title: NARAD
date_updated: 2026-04-05
tags: [entity, system, crm]
---

# NARAD

Groww's in-house CRM + real-time campaign trigger system.

## Architecture

```
Real-time data streams (Kafka)
    ↓
Spark stateful structured streaming (joins multiple sources)
    ↓
master_tables schema (contract master, index master, ATM master)
    ↓
Campaign eligibility engine (derived attributes)
    ↓
Campaign triggers → User notifications
```

## Key Capabilities

- **Self-serve**: Business team defines derived attribute logic (e.g., `curr_oi < oi_30min_before * 0.90`) in <1 day without DP team
- **Personalization**: Text-only via CDP (no personalized images at scale)
- **F&O automation**: 20+ campaigns automated (PCR, OI, ATM straddle, buildup alerts)

## F&O Signal Definitions

| Signal | Definition |
|--------|-----------|
| PCR | Put/Call OI ratio. >1 = bearish, <1 = bullish |
| ATM straddle | At-The-Money straddle price = volatility expectation |
| OI | Open Interest surge/drop = activity signal |
| Long buildup | OI↑ + Price↑ = bulls adding |
| Short buildup | OI↑ + Price↓ = bears adding |
| Covering | OI↓ + Price↑ = shorts closing |
| Unwinding | OI↓ + Price↓ = longs exiting |
| Greeks | Delta, gamma, theta, vega — planned, not yet live |

## Data Sources

- `invest_iceberg.live_data.stocks_data_live_nse_fo_feed` (via KiteConnect)
- `platform_pinot.default.fno_stocks_order` (live F&O orders)
- `platform_iceberg.stocks_shared_invest.derivatives_contract_master_table`

## Open Questions

- ❓ Relationship to [[cosmos]] unclear
- ❓ Is In-house Campaign Manager (CM) the same as NARAD V2?
- ❓ CDP vs [[audience-manager]] — same or separate?

## Related

- [[webengage]] — external CRM (complementary)
- [[bigquery]] — data warehouse feeding segments
- [[ems]] — replacing WebEngage pipeline for [[c-mab]]
