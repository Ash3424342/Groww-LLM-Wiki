---
title: Segment Registry
date_updated: 2026-04-05
tags: [concept, data, segments, targeting]
---

# Segment Registry

Actual Audience Manager segment IDs used for campaign targeting. Understanding these is critical for building or debugging campaigns.

## PA Segment Format

`PA_{tier}_{product}_P{rank}_{product2}_P{rank2}_{version}`

| Tier | Meaning |
|------|---------|
| `HA` | High Affinity |
| `MA` | Mid Affinity |
| `lia` | ❓ Unknown (Low Intent Active? Low/Inactive Affinity?) — lowercase, no V2 suffix |

Examples: `PA_HA_CNC_P1_MF_P2_V2`, `pa_lia_cnc_p1_mf_p2`

## NTU Cross-Product Segments

Format: `NTU_{P1product}_{P2product}_{LD/HD}`

⚠️ **NTU here = Non-TTU** (not New Transacting User)

| Token | Meaning |
|-------|---------|
| `LD` | Low Difference — similar affinity for both products |
| `HD` | High Difference — strong P1 preference, lead with P1 content |

9 unique segments covering Stock/MF/FnO combinations × LD/HD = 18 targeting use cases.

## TTU Lifecycle Segments

| Segment | Meaning |
|---------|---------|
| `TTU_L7D_Inactive` | Inactive 7 days |
| `TTU_L14D_Inactive` | Inactive 14 days |
| `TTU_L30D_Inactive` | Inactive 30 days |
| `TTU_CM_Inactive` | Inactive current month |
| `TTU_LM_Active_CM_Inactive` | Active last month, inactive now |
| `MTU_3_7D` | Active 3-7 day window |
| `MTU_7_14D_ar` | Active 7-14D (**at-risk**) |
| `MTU_14_30D_ar` | Active 14-30D (**at-risk**) |

`ar` suffix = "at risk" — shorter recency = higher churn risk.

## Other Segments

| Category | Examples |
|----------|---------|
| IPO | `IPO_ever_applied`, `IPO_applied_in_last_12M`, `onb_ever_applied_ipo_not_allot` |
| Holdings | `stock_holding_gt_0` |
| Clickers | `clicker_last_30days`, `pn_clicker_90_days` |
| Gold/Silver | `only_gold_silver_ntu` |
| Resurrection | `Ressurection_email_base` |

## Related

- [[audience-manager]] — where segments are built and managed
- [[product-affinity]] — PA model generates the PA segments
- [[ntu]] — naming collision: NTU in segments = Non-TTU
- [[narad]] — campaign eligibility reads from segments
