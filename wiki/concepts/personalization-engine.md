---
title: Personalization Engine
date_updated: 2026-04-05
tags: [concept, ml, personalization]
---

# Personalization Engine

ML-driven system that moves comms from generic cohort-level to user-level targeting.

## Two Layers

| Layer | How it works |
|-------|-------------|
| **Generic** | Broad segment — same message to a defined cohort |
| **Personalized** | User-level signals: holdings, watchlist, ML model outputs |

## Core ML Models

Three models combine into a single personalized nudge:

| Model | Output |
|-------|--------|
| [[product-affinity]] | Top 2 products user will transact in next day |
| [[instrument-affinity]] | Top stock/fund/instrument for the user |
| Time activity | Optimal send time per user |

**Combined** = right product + right instrument + right time → personalized daily nudge

## Comms Maturity Progression

```
BAU Comms          → Regular planned campaigns
Adhoc Comms        → Reactive to market events
Mid-Market Action  → Real-time triggers during market hours
Personalized Comms → ML-driven, per-user (refreshed daily)
Journeys           → Automated lifecycle sequences (behavior-triggered)
```

## Pod Ownership

Owned by [[invest-personalization-pod]] (Himanshu, Preksha).

## Related

- [[c-mab]] — selects best push per user per slot
- [[campaign-affinity]] — picks best campaign per user
- [[activation-funnel]] — personalization applied at each funnel step
