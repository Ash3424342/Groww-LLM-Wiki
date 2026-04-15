---
title: Wiki Overview
date_updated: 2026-04-06
tags: [meta, overview]
---

# Groww Growth Vertical — Wiki Overview

## What This Knowledge Base Covers

This wiki compiles knowledge about **Groww's User Engagement (Growth) vertical** — the team responsible for driving user activation and retention across India's largest retail investment platform (~10 crore registered users).

## Two Core Missions

1. **0→1 (Activation)**: Move KYC-complete users to their First Investment Done ([[fid]])
2. **1→N (Retention)**: Keep investors transacting repeatedly ([[rid]]) and cross-selling into new products ([[cross-sell]])

## Organizational Structure

**5 Pods** execute against these goals:
- [[invest-activation-pod]] — KYC → FID across MF, Stocks, Gold, FDs, IPO
- [[invest-rid-pod]] — Repeat transactions, retention, reactivation
- [[invest-personalization-pod]] — ML-driven hyper-personalized communications
- [[trading-pod]] — FID + RID for F&O, Commodities, MTF, MIS
- [[other-businesses-pod]] — Wealth (Fisdom), Groww AMC

## Scale & Key Numbers

| Metric | Value | Date |
|--------|-------|------|
| Registered users | ~10 crore | 2024 (source: Master Reference v2, 2026-03-26) |
| TTU-MAU% retention | ~73% | Jan 2024 (source: Master Reference v2) |
| App-Keep TTU MAU% | ~87% (ATH achieved Jan 2024) | Jan 2024 (source: Master Reference v2) |
| Monthly inactive churn | 3.2M TTU | 2024 (source: Revive doc via Master Reference) |
| NTU → CNTU (3M) | 70% | 2024 (source: NTU→CNTU doc via Master Reference) |
| NTU → CNTU (24M) | 80% | 2024 (source: NTU→CNTU doc via Master Reference) |
| Monthly comms volume | ~3 Billion messages | Feb 2024 (source: Long-term strategy doc) |
| Account opening cost | Rs.44/user ⚠️ (scope undefined — blended? organic? See [[open-verification-checklist]] #7) | 2024 |
| Signup → Esign (7D) | 26% conversion | 2024 (source: WA Onboarding doc) |

## Communication Channels

| Channel | Key Stat | Tools |
|---------|----------|-------|
| [[push-notifications]] | 3% generic CTR, 12% personalized (4X) | WebEngage → FCM |
| [[whatsapp-channel]] | 73p BIC, 33p UIC; FID CAC 1/5th–1/10th of remarketing | COSMOS |
| [[email-channel]] | 18-20% open rate, 10M/hr throughput | Netcore |
| [[rcs-sms]] | Rich SMS alternative | — |
| [[in-app-stories]] | Rf score model for retention | — |
| [[feed-nc]] | WAU 243K, 33% weekly retention | — |

## ML / Personalization Stack

9 models power personalization — see [[ml-models-overview]]:
- [[product-affinity]] (73% accuracy), [[c-mab]] (+40% CTR), [[campaign-affinity]] (+20% CTR)
- [[cross-sell-affinity]] (+3.2% cross-sell FID), [[retention-propensity]], [[widget-ranker]]
- [[instrument-affinity]] (+3% DAU), [[rf-score]] (R²=0.254)

## Data Infrastructure

- [[narad]] — In-house CRM (Kafka + Spark → campaign triggers)
- [[bigquery]] — Data warehouse (feeds Audience Manager segment pipeline)
- [[audience-manager]] — Segment builder
- [[webengage]] — External CRM
- [[cosmos]] — WhatsApp journey system (⚠️ relationship to NARAD unclear)
- [[superset]] — BI dashboards
- [[ems]] — Real-time events pipeline
- [[compass-mcp]] — Unified data interface (DataHub + Superset + Trino via MCP). ⚠️ Note: Compass queries via **Trino on platform_iceberg**, not BigQuery directly. BQ feeds segments; Trino feeds analytics.

## Also In This KB

- [[groww-email-system]] — Block-based HTML email generation system (tokens → blocks → recipes)

## Open Questions

- ❓ What is **LO** metric? (L0 north-star? Logged On?)
- ❓ How does **COSMOS** relate to NARAD/WebEngage?
- ❓ **TTU thresholds** — exact activity/transaction day cutoffs?
- ❓ **Feed Phase 1** timeline?
