---
title: Widget Ranker Engine
date_updated: 2026-04-06
tags: [concept, ml-model, on-app]
---
# Widget Ranker
C-MAB-powered on-app widget ranking for Stocks Explore. Uses [[c-mab]] algorithm on a different surface (app, not push).
## Specs
- V0: 4 widget slots (reduced from 9), 13 widgets in pool
- Daily batch produces model weights; real-time serving layer uses latest weights per page load via BFF
## Previous A/B Tests (all failed)
| Variation | Result |
|-----------|--------|
| 1 widget, onboarded | NTU **-50%** + 40 escalations → stopped 4 days |
| 4 widgets, onboarded | NTU **-20%** → stopped |
| 5 widgets, new signups | NTU **flat** |
## Key Learning
Reducing widgets alone doesn't improve NTU. The **widget mix** matters — C-MAB to personalize the mix is the answer. 51% of users visit Explore BEFORE completing onboarding.
## Related
- [[c-mab]] — same algorithm, different surface
- [[stocks-cnc]] — the product section it personalizes
