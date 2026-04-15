---
title: Open Verification Checklist
date_updated: 2026-04-09
tags: [meta, checklist, verification]
---

# Open Verification Checklist

Items the LLM cannot verify from existing docs. Fill these in and the wiki will be updated automatically.

---

## How to use

Fill in the **Answer** column. When you confirm an item, tell the LLM `/wiki-kb update` and it will propagate the answer to all affected pages and remove the ⚠️ marker.

---

| # | Question | Current wiki value | Affected pages | Answer |
|---|----------|-------------------|----------------|--------|
| 1 | **TTU thresholds** — exact activity + transaction day/count cutoffs (e.g., "≥3 transactions AND ≥5 app opens in last 30 days") | "activity AND transaction thresholds" (no numbers) | ttu.md, overview.md | _fill in_ |
| 2 | **PA model refresh time** — what hour IST does the daily batch run? | "Daily refresh" (no time) | product-affinity.md, ml-models-overview.md | _fill in_ |
| 3 | **Instrument Affinity refresh time** — same question | "Daily refresh" (no time) | instrument-affinity.md | _fill in_ |
| 4 | **Retention Propensity refresh cadence** — which specific dates? 1st+15th? Every 2 weeks from X? | "Fortnightly" (no anchor) | retention-propensity.md, audience-manager.md | _fill in_ |
| 5 | **C-MAB "5 TTU models"** — what are the 5? Per-product line? Per time slot? Per campaign pool? | "5 models deployed for TTU" (no breakdown) | c-mab.md, ml-models-overview.md | _fill in_ |
| 6 | **"Top 10 instruments"** — ranked by what metric? Trading volume? User affinity score? DAU contribution? | "Top 10" (ranking criteria unspecified) | instrument-affinity.md | _fill in_ |
| 7 | **Rs.44/user account opening cost** — what does this include? Blended all-channel CAC? Organic only? Excludes WA/remarketing? | "Rs.44/user" (scope undefined) | overview.md, activation-funnel.md | _fill in_ |
| 8 | **App Affinity (DAU/MAU)** — current value for Groww? Industry benchmark? | "Higher = better" (no value given) | ttu.md | _fill in_ |
| 9 | **Cross-sell 14D vs 30D window** — why is 14D deployed if 30D was recommended? What was the experiment delta? | "14 days (30D recommended)" (no rationale) | cross-sell-affinity.md | _fill in_ |
| 10 | **`lia` segment tier** — what does it stand for? Low Intent Active? Low/Inactive Affinity? Deprecated? | "❓ Unknown" | segment-registry.md | _fill in_ |
| 11 | **LO metric** — L0 (north-star)? Logged On? Something else? | "❓ major metric for overall business" | overview.md | _fill in_ |
| 12 | **COSMOS** — how does it relate to NARAD and WebEngage? Same system? Layer on top? Separate? | "❓ Relationship unclear" | cosmos.md, overview.md | _fill in_ |
| 13 | **WebEngage throughput upgrade** — when was 75K→250K/min upgrade done? | "upgraded from 75K/min" (no date) | webengage.md | _fill in_ |
| 14 | **Rf Score R²=0.254** — is this considered good at Groww? When was this measured? Still valid? | "R²=0.254 (beats linear R²=0.174)" (no interpretation) | rf-score.md | _fill in_ |
| 15 | **30% of L150D+ MAU from Google retargeting** — which month was this measured? Still accurate? | "~30% MAU from Google retargeting" (no date) | activation-funnel.md | _fill in_ |
| 16 | **user_account_id dedup** — can a user have multiple ACC IDs? How are they unified for MAI counting? | "Universal join key: user_account_id (ACC<digits>)" (dedup unknown) | compass-analytics-skills.md | _fill in_ |
