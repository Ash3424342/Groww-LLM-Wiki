---
title: Campaign Affinity Model
date_updated: 2026-04-06
tags: [concept, ml-model]
---
# Campaign Affinity
Selects the best campaign template/format for each user per time slot.
## Versions
| Version | Algorithm | Result |
|---------|-----------|--------|
| V0 | Classical ML | 10-15% CTR lift; F&O 1.5% → 2.4% |
| V1 | Thompson Sampling | **+20% CTR uplift** (early reads) |
## Features
- **Template Fatigue Penalty**: reduces score for templates seen too often
- **Eligibility Filtering**: filters ineligible campaigns before bandit selects
## Related
- [[c-mab]] — complementary (C-MAB selects content, Campaign Affinity selects format)
- [[daily-push-slots]] — operates within the slot structure
