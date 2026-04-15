---
title: Activation Funnel
date_updated: 2026-04-05
tags: [concept, funnel, activation]
---

# Activation Funnel

The path from app install to [[fid]] (First Investment Done). 7-8 steps with measurable convert/dropoff rates at each.

## Steps (with exact drop rates)

```
Signup
    ↓ [20% drop]
OTP verified
    ↓ [40% drop]  ← BIGGEST drop
PAN verified
    ↓ [35% drop]  ← 2nd biggest
Bank Verified (BV)
    ↓ [20% drop]
Digilocker done
    ↓ [22% drop]
Esign ✅ — KYC complete
    ↓
[Product Browse → PP Visits → Watchlist]
    ↓
FID ✅ → user becomes NTU
```

## Key Metrics Per Step

- **Convert rate**: % moving to next step
- **Dropoff rate**: % leaving at this step
- **D7**: % of cohort reaching a milestone by Day 7
- **PP visits**: Product Page visits ≥2-5 = high intent signal

## Benchmarks

| Metric | Value |
|--------|-------|
| Signup → Esign (7D) | **26%** |
| Biggest drop | OTP→PAN (**40%**) |
| Second biggest | PAN→BV (**35%**) |
| Account opening cost | **Rs.44/user** |
| WA at Esign step | +30% uplift, ₹145/conversion |
| WA onboarding | ~200 incremental Esigns/day |

## Post-Esign: Inactive Cohorts

| Cohort | Push Reachability | Notes |
|--------|-------------------|-------|
| L30D Active (last activity within 30 days) | High | ~10% of monthly NTU |
| L150D+ Active (last activity 31-150 days ago, NOT in L30D) | **~1.5%** | Largest base; ~30% MAU from Google retargeting ⚠️ (which month? See [[open-verification-checklist]] #15) |

~50% of non-investors are Push-unreachable → [[whatsapp-channel]] is critical.

## Pod Ownership

Owned by [[invest-activation-pod]]. Campaigns designed to reduce dropoff at each step.

## Related

- [[fid]] — the endpoint of this funnel
- [[ntu]] — what a user becomes after FID
- [[personalization-engine]] — ML models optimize which nudge to send at each step
