---
title: Retention Strategy
date_updated: 2026-04-06
tags: [concept, strategy, retention]
---

# Retention Strategy

Preventing TTU churn and resurrecting lapsed users. Owned by [[invest-rid-pod]].

## The Problem

**3.2 million TTU** become inactive every month. ~50% of non-investors are push-unreachable.

## Strategy by Cohort

| Cohort | Channel | Approach | Result |
|--------|---------|----------|--------|
| High-active TTU | Push (personalized) | PA Calendar / [[c-mab]] | Self-direct; no incremental uplift needed |
| Mid/Low-active TTU | Push + ML | [[product-affinity]] targeting | CTR +6%, DTU +1.3%, Sessions +7% |
| High Potential Inactive (decile 8-10) | [[whatsapp-channel]] | Portfolio Update (Rs.75/resurrection) | +23% resurrection |
| High Risk MAU (decile 1-3) | Email + Push | Lower uplift | Push reachable (>90%) |
| Push-unreachable | WA / [[rcs-sms]] | Only reachable channel | Brings app opens |

## Key Insight

WA dramatically outperforms Email for resurrection (~10-12x). Email gets opens but doesn't convert back to app.

## ML Models Used

- [[retention-propensity]] — segments users into 10 deciles (high-risk vs high-potential)
- [[product-affinity]] — drives personalized content for mid/low-active
- [[c-mab]] — selects best campaign per user per slot

## Related

- [[rid]] — the metric retention strategy drives
- [[ttu]] — the user base being retained
- [[invest-rid-pod]] — the pod that executes this
- [[whatsapp-channel]] — primary resurrection channel
