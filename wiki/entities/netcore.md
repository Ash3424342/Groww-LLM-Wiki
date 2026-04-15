---
title: Netcore
date_updated: 2026-04-06
tags: [entity, system, email]
---
# Netcore
Email Service Provider (ESP) for Groww. Delivers Digest, GrowwFlix, and all campaign emails.
## Key Stats
- Throughput: **10M/hr** (upgraded from 2.2M/hr, Nov 2022)
- Delivery rate: 99%
- Subdomains: `digest.groww.in` (primary), `dailydigest.groww.in` (backup)
- Domain warmup: 30-day ramp (100 → 10M), must maintain >20% open rate
## Pipeline
```
WebEngage → Netcore (ESP) → User inbox
```
## Related
- [[email-channel]] — the channel Netcore delivers
- [[groww-email-system]] — generates the HTML that Netcore sends
