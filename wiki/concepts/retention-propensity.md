---
title: Retention Propensity Model
date_updated: 2026-04-06
tags: [concept, ml-model, retention]
---
# Retention Propensity
Predicts P(user transacts next month) for each TTU. Outputs a decile score 1-10. Refresh: fortnightly.

⚠️ **"Fortnightly" — anchor dates unconfirmed.** 1st+15th? Every 2 weeks from when? See [[open-verification-checklist]] #4.
## Decile Interpretation
| Decile | Segment | Profile | Best Channel |
|--------|---------|---------|-------------|
| 1,2,3 | **High churn risk** | PPI≈1, AUM<500, PN reach >90% | Push |
| 4-7 | Mid | Mixed | Mixed |
| 8,9,10 | **High resurrection potential** | Active L2M, some AUM, low PN reach | WA / RCS / Email |
## Related
- [[ttu]] — the user base this model scores
- [[whatsapp-channel]] — primary channel for high-potential (decile 8-10)
