---
title: Instrument Affinity Model
date_updated: 2026-04-06
tags: [concept, ml-model]
---
# Instrument Affinity
Predicts top stock/fund/instrument user will act on. Daily refresh.

⚠️ **Refresh time unconfirmed** — what hour IST? See [[open-verification-checklist]] #3.

## Results
| Scope | CTR | DAU | Status |
|-------|-----|-----|--------|
| Top 10 instruments ⚠️ (ranked by what metric? See [[open-verification-checklist]] #6) | Moderate | **+3% DAU** | Live — automating into CM |
| Top 11-50 | **+23% CTR** | NO DAU impact | **Paused** |
## Key Learning
"CTR without downstream action = zero business value." More instruments doesn't help — quality signal matters.
## Related
- [[product-affinity]] — PA predicts product, Instrument drills to specific instrument
- [[personalization-engine]] — second of three models in the combined nudge
- [[cnc-personalization-ladder]] — instrument affinity feeds CNC alerts
