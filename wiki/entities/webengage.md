---
title: WebEngage
date_updated: 2026-04-06
tags: [entity, system, crm]
---
# WebEngage
External CRM platform — campaign orchestration for push, email, in-app.
## Role in Pipeline
```
Audience Manager → WebEngage → FCM (push) / Netcore (email) / WA API
```
## Key Stats
- Push throughput: **250K/min** (upgraded from 75K) ⚠️ upgrade date unconfirmed — see [[open-verification-checklist]] #13
- Latency improvement: 50% reduction (but FCM bottleneck found downstream)
## Related
- [[narad]] — complementary in-house CRM
- [[push-notifications]], [[email-channel]] — delivery channels it orchestrates
- [[compass-mcp]] — Compass uses Superset SQL against WebEngage data
