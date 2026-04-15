---
title: Daily Push Slot Structure
date_updated: 2026-04-05
tags: [concept, campaigns, push]
---

# Daily Push Slot Structure

4 structured daily time slots for onboarded user campaigns:

| Slot | Time | Content | Products |
|------|------|---------|---------|
| **1** | ~9:45 AM | Opening Bell — market open, overnight | Stocks, MF |
| **2** | ~11-12:30 PM | Market Action — intraday signals | Stocks, F&O |
| **3** | ~1:30 PM | Stock Collections — curated lists | Stocks |
| **4** | ~3:45 PM | MF Collections — fund categories | MF |

Weekends: no Slot 2/3 (market closed). MF runs on weekends (SIPs).

## CMAB Slots

| Slot | Type |
|------|------|
| CMAB-1 | Personalized Opening Bell variants |
| CMAB-2 | Personalized Stock property variants |
| BAU | Standard campaigns (same content for all) |
| CG | Control Group campaigns (holdout) |

Each slot has 5+ content variations for A/B testing.

## Non-TTU Content Calendar

| Affinity | Weekday Pattern |
|---------|----------------|
| Stock | Opening bell → Trending stocks → Large cap → Gainers/losers |
| F&O | Pre-market → OI alerts → Expiry → Most traded |
| MF | Opening bell → Popular funds → SIP/collections |
| No affinity (OB) | Opening bell → Single stocks → Sectoral → Value props |

LD segments: mix P1 and P2 content. HD segments: lead with P1, P2 as cross-sell.

## Related

- [[c-mab]] — selects best campaign per user per slot
- [[push-notifications]] — delivery channel
- [[segment-registry]] — targeting for each slot
