---
title: EMS (Event Management System)
date_updated: 2026-04-06
tags: [entity, system, data]
---
# EMS
Real-time events pipeline. Replacing [[webengage]]'s data pipeline for [[c-mab]] model inputs.
## Purpose
Reduce C-MAB content affinity data lag from **2 days → 1 day**.
## Status
In progress.
## Related
- [[c-mab]] — primary consumer (needs fresher data for better bandit decisions)
- [[narad]] — EMS feeds into NARAD's campaign triggers
