---
title: "Source: OB-to-FID Email Journey Analysis"
source: raw/Groww-Email-System/OB_TO_FID_ANALYSIS.md
date_ingested: 2026-04-06
tags: [email, onboarding, activation, journey]
---

# Source: OB-to-FID Email Journey Analysis

## Summary

Complete reference for the onboarding email + push notification journey, analyzed from `OB to FID_Feb_v3.pdf`. Maps 12 email types (4 educational + 8 onboarding across Day 0–7) with per-email block sequences, push specs, and ~50 app screenshots needed.

## Key Facts

- **Two programs**: Educational Series (4 commodity emails, standalone) + Onboarding Journey (8 emails, Day 0–7)
- **9 onboarding recipes built** (Session 6): welcome, stocks, SIP, stocks_tools, mf_explore, stocks_features, mf_features, fno, brand_story
- **3 new blocks built**: `app_screenshot_pair` (text + screenshot side-by-side), `product_category_grid` (2-col product cards), `social_showcase` (social channel cards)
- **Total blocks now**: 18 (up from 15)
- **Total recipes now**: 13 (up from 4)
- **All 13 recipes validated**: 0 issues, 12-17KB each
- **~50 placeholder images** need replacing with real app screenshots
- **Push notification specs**: Title + Body + CTA for all 9 days documented
- **Open rate data**: Edu-3 highest (25.4%), Edu-4 lowest (15.3%)

## Design Patterns Documented

1. Personalization: "Hello \<Name\>," on all onboarding emails
2. Alternating screenshot layout (left-text/right-text)
3. Step-by-step flows for Day 1 (buy stock), Day 2 (SIP), Day 6 (F&O)
4. CTA colors: Green = explore/invest, Blue = features/trading
5. App screenshots ARE the content in onboarding (minimal text)

## Relationships

- supports: [[groww-email-system]] — major expansion of the recipe catalog
- supports: [[activation-funnel]] — these emails are the comms layer for KYC→FID activation
- related: [[invest-activation-pod]] — this journey is their primary email tool
- related: [[fid]] — the entire journey aims to drive FID
