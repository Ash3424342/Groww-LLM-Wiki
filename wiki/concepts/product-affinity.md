---
title: Product Affinity Model
date_updated: 2026-04-05
tags: [concept, ml-model]
---

# Product Affinity (PA) Model

Predicts top 2 products a user will transact in next day. Daily refresh.

⚠️ **Refresh time unconfirmed** — what hour IST does the daily batch run? See [[open-verification-checklist]] #2.

## Accuracy

| Scope | Accuracy |
|-------|----------|
| Overall | **73%** |
| MF only | **55%** (❓ why so low?) |

## Experiment Results

| Experiment | Result |
|-----------|--------|
| RID PA vs RFM baseline | PN CTR +6%, DTU +1.3%, Sessions +7% |
| PA for OB/NTU (D7+ onboarded) | CTR ↑, Sessions ↑, but **NO FID conversion uplift** |

## PA Calendar

Daily schedule translating PA output → which product to promote per user. The operational engine connecting ML to campaigns.

## Segment Naming

Format: `PA_HA_CNC_P1_MF_P2_V2`
- HA/MA/LA = High/Mid/Low Affinity
- P1 = primary product, P2 = secondary
- V2 = model version

## Owners

[[himanshu]] (model), [[preksha]] (OB/NTU variant)

## Related

- [[personalization-engine]] — PA is the first of three models
- [[instrument-affinity]] — drills down from product to specific instrument
- [[c-mab]] — uses PA outputs as context
