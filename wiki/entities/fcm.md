---
title: FCM (Firebase Cloud Messaging)
date_updated: 2026-04-06
tags: [entity, system, infrastructure]
---

# FCM (Firebase Cloud Messaging)

Google's push notification delivery infrastructure. Final hop in the push pipeline.

## Pipeline

```
WebEngage (250K/min) → FCM → User device
```

## Key Finding

After WebEngage scaled to 250K/min, **FCM became the bottleneck** — FCM→user latency increased 120% even after WE scaled. The constraint is downstream, not upstream.

## Related

- [[webengage]] — upstream campaign orchestration
- [[push-notifications]] — the channel FCM delivers
