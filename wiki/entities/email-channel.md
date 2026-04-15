---
title: Email Channel
date_updated: 2026-04-05
tags: [entity, channel]
---

# Email Channel

Cheapest off-app channel. Owned by [[himanshu]] (infra/strategy), [[yash]] (GrowwFlix).

Sent via [[webengage]] → [[netcore]] or AWS. Subdomains: digest.groww.in, dailydigest.groww.in.

## Benchmarks

| Metric | Value |
|--------|-------|
| Delivery rate | 99% |
| Open rate (overall) | 18-20% |
| Throughput (post-upgrade) | 10M/hr (from 2.2M/hr) |
| Open rate improvement from speed | +2-2.5% |
| Domain warmup | 30 days (100 → 10M emails), must maintain >20% open rate |
| File size limit | 102KB (Gmail clips beyond) |

## Email Properties

| Property | Scale | Engagement |
|----------|-------|-----------|
| **Daily Digest** | 15M users | MAU declining: 13M (Oct-24) → **8M** (Mar-25) |
| **Weekly Digest** | Optimized 24M → 11M targets | Same 2.1M opens; saved Rs.7-8L/month |
| **GrowwFlix** | 7M users | **30% open rate**; TTU +1.7% MAU, Non-TTU +0.71% |

## Key Insight

Email is high-reach but low-conversion for resurrection (+2% vs WA's +23%). Best used for engagement/education, not reactivation.

## Related

- [[whatsapp-channel]] — 10-12x better at resurrection
- [[netcore]] — ESP
- [[groww-email-system]] — block-based email generation
