---
title: Mutual Funds (MF)
date_updated: 2026-04-06
tags: [entity, product]
---
# Mutual Funds (MF)
Mutual fund investment product — SIP (systematic) and lumpsum orders. Groww's largest product by user count.
## Key Stats
- PA model accuracy for MF: **55%** (weakest — drags overall 73%)
- MF Explore = 62-66% of MF NTU & Cross-sell FID
- MF MAU visiting Feed/NC: only 7% (lowest — "very static" content)
- MF has weekend DTU (SIPs execute on weekends, automated)
## Pod Ownership
[[invest-rid-pod]] (Amit — MF strategy), [[invest-activation-pod]]
## Key Tables (Compass)
- `fact_mutual_fund_order_details_enriched` (dwh_invest) — enriched orders + FID flags
- `fact_mutual_fund_sip_details` (dwh_invest) — SIP lifecycle
- `view_mf_user_aum_latest` (dwh_invest) — latest AUM snapshot
## Related
- [[product-affinity]] — MF accuracy needs improvement
- [[cross-sell]] — MF cross-sell uplift +1%
- [[sip]] — SIP is the primary MF transaction type
