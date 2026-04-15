---
title: Wiki Index
date_updated: 2026-04-06
---

# Index

Master catalog of all wiki pages. Updated on every ingest.

---

## Overview
- [[overview]] — High-level synthesis of the entire knowledge base
- [[project-map]] — Wiki ↔ Code reference (what's built, where files live, what's not built yet)
- [[open-verification-checklist]] — 16 unconfirmed items marked with ⚠️ across wiki pages

## Source Summaries
- [[source-overview]] — Overview & org structure of Growth vertical
- [[source-master-reference]] — Exhaustive source of truth: metrics, tools, people, benchmarks
- [[source-pod-playbooks]] — All 8 pod strategies, experiments, results
- [[source-concepts-notes]] — Deep-dive explanations for engineering audience
- [[source-data-architecture]] — NARAD, BigQuery, segments, pipelines
- [[source-ml-systems]] — 9 ML models with specs and accuracy
- [[source-analytics-metrics]] — KPI tree, dashboards, cohort definitions
- [[source-campaign-library]] — Live campaigns, SOPs, frequency rules
- [[source-vocabulary]] — A-Z glossary with confirmation status
- [[source-email-system]] — Email system docs (architecture, blocks, recipes, project state)
- [[source-ob-to-fid-analysis]] — OB-to-FID onboarding email journey (12 emails, Day 0–7, push specs)
- [[source-compass-mcp]] — Compass MCP docs (3 PDFs: product overview, 16 analytics skills, setup guide)
- [[source-handwritten-notes]] — Handwritten task notes (2 images: full task + Content Engine architecture)

## Entities

### People
- [[aastha]] — Trading pod strategy lead
- [[nikhil]] — Invest strategy: Activation, WhatsApp, RID
- [[shweta]] — Invest strategy + execution, comms orchestration
- [[himanshu]] — RID strategy + ML personalization
- [[amit]] — MF strategy, Invest pod ownership
- [[aishwarya]] — Execution: campaigns, RCS, SMS, Stories
- [[yash]] — Trading strategy, 9:15 comms, WhatsApp
- [[samir]] — Trading pod campaign execution
- [[preksha]] — PA model for OB/NTU activation
- [[ritvik]] — MF TTU personalization, Feed strategy

### Pods
- [[invest-activation-pod]] — 0→1: KYC → FID
- [[invest-rid-pod]] — Repeat transactions, retention
- [[invest-personalization-pod]] — ML-driven personalization
- [[trading-pod]] — F&O, MTF, MIS, Commodities
- [[other-businesses-pod]] — Wealth (Fisdom), Groww AMC
- [[pay-pod]] — UPI/BBPS, Pay FPD, resurrection economics

### Products
- [[mutual-funds]] — MF product (SIP, lumpsum)
- [[stocks-cnc]] — Cash & Carry equity
- [[fno]] — Futures & Options
- [[commodities]] — Commodity trading
- [[mtf]] — Margin Trade Funding
- [[mis]] — Margin Intraday Square-off
- [[ipo]] — Initial Public Offerings
- [[pay-upi]] — UPI payments & BBPS
- [[gold]] — Gold & SGB investments
- [[fixed-deposits]] — FD product

### Systems
- [[narad]] — In-house CRM + campaign trigger system
- [[webengage]] — External CRM platform
- [[cosmos]] — WhatsApp journey system
- [[bigquery]] — Data warehouse
- [[audience-manager]] — Segment builder
- [[compass-mcp]] — Unified data platform (DataHub + Superset + Trino via MCP)
- [[superset]] — BI dashboards
- [[ems]] — Event Management System
- [[netcore]] — Email delivery platform
- [[fcm]] — Firebase Cloud Messaging (push delivery)

### Channels
- [[push-notifications]] — Push via WebEngage → FCM
- [[whatsapp-channel]] — WhatsApp via COSMOS
- [[email-channel]] — Email via Netcore
- [[rcs-sms]] — RCS and SMS
- [[in-app-stories]] — On-app story cards
- [[feed-nc]] — Notification Center / Feed

## Concepts

### Metrics
- [[fid]] — First Investment Done
- [[rid]] — Repeat Investment Done
- [[ntu]] — New Transacting User
- [[ttu]] — Total Transacting Users
- [[cntu]] — Cross-sell NTU
- [[active-ppu]] — Active Products Per User
- [[gcg]] — Global Control Group (experiment baseline)
- [[kpi-tree]] — Full metric hierarchy (MAI as North Star)

### Strategies
- [[activation-funnel]] — Signup → KYC → FID pipeline (with drop rates)
- [[cross-sell]] — Moving users from 1 product to 2+ (discovery ≠ problem)
- [[personalization-engine]] — ML-driven per-user comms
- [[retention-strategy]] — Preventing TTU churn, resurrection by cohort
- [[cnc-personalization-ladder]] — CNC alert progression (3% → 19% CTR)
- [[daily-push-slots]] — 4-slot daily PN structure with CMAB
- [[segment-registry]] — PA/NTU/TTU segment IDs and naming conventions
- [[sebi-regulations]] — Regulatory constraints (F&O cross-sell, IPO language)
- [[compass-analytics-skills]] — 16 Compass skills (tables, columns, guardrails per domain)

### ML Models
- [[ml-models-overview]] — All 9 models summary
- [[product-affinity]] — Next-day top 2 products (73% accuracy)
- [[c-mab]] — Contextual Multi-Armed Bandit (+40% CTR)
- [[campaign-affinity]] — Best campaign per user (+20% CTR)
- [[cross-sell-affinity]] — Cross-sell prediction (+3.2% FID)
- [[retention-propensity]] — Churn risk deciles
- [[widget-ranker]] — On-app widget ranking
- [[instrument-affinity]] — Top stocks per user (+3% DAU)
- [[rf-score]] — Story card retention predictor (R²=0.254)
- [[sip]] — Systematic Investment Plan (primary MF transaction type)

### Other
- [[groww-email-system]] — Block-based email generation system

## Analyses
*(filed from queries — grows over time)*

## Comparisons
*(filed from comparisons — grows over time)*
