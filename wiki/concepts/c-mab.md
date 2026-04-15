---
title: C-MAB — Contextual Multi-Armed Bandit
date_updated: 2026-04-05
tags: [concept, ml-model]
---

# C-MAB — Contextual Multi-Armed Bandit

Thompson Sampling algorithm selecting best push notification per user per slot.

## Versions

| Version | Reward Function | Result |
|---------|----------------|--------|
| V0 | CTR only | **+34% CTR** (after warmup) |
| V1 | 50% CTR + 50% Transaction rate | **+40% CTR + 3% DTU** |

10% exploration rate. 5 models deployed for TTU; 3 Non-TTU in progress.

⚠️ **"5 TTU models" — breakdown unconfirmed.** Per-product? Per time slot? Per campaign pool? See [[open-verification-checklist]] #5.

## Expanding To

- On-app [[widget-ranker]] (C-MAB for widget ranking in Stocks Explore)
- More slots and channels

## Industry Users

Zomato, Duolingo, LinkedIn, Facebook, DoorDash

## Related

- [[personalization-engine]] — C-MAB is core to personalized push
- [[push-notifications]] — the channel it optimizes
- [[campaign-affinity]] — complementary model (campaign selection vs content selection)
- [[ems]] — will reduce C-MAB content affinity lag from 2D → 1D
