---
title: Audience Manager
date_updated: 2026-04-05
tags: [entity, system]
---

# Audience Manager

Segment builder and user assignment engine.

## Pipeline

```
BigQuery (daily batch)
  ↓
Audience Manager — segment computation + user assignment
  ↓
WebEngage — campaign delivery
```

## Refresh

- Most segments: **daily**
- Retention Propensity: **fortnightly**
- C-MAB: **continuous** (but 2D lag until EMS goes live)

## Open Questions

- ❓ Is this the same as [[narad]]'s CDP, or a separate tool?

## Related

- [[bigquery]] — upstream data source
- [[webengage]] — downstream delivery
- [[segment-registry]] — the segments it manages
