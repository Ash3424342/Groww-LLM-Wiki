---
title: SIP (Systematic Investment Plan)
date_updated: 2026-04-06
tags: [concept, product, mf]
---

# SIP (Systematic Investment Plan)

Regular automated mutual fund investment (monthly, weekly, etc.). Primary MF transaction type.

## Key Facts

- SIP creation, mandates, step-ups tracked in `fact_mutual_fund_sip_details` (Compass MF skill)
- MF has weekend DTU because SIPs execute on weekends (automated, date-driven)
- MF Purchase Abandonment experiment: SIP +~2% at 4.2L user scale
- Onboarding Day 2 email: "First SIP made simple" — [[groww-email-system]] recipe `groww_onboarding_sip.json`

## Related

- [[mutual-funds]] — the product SIPs belong to
- [[invest-activation-pod]] — SIP is a key FID path for MF
