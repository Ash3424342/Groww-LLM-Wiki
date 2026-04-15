---
title: Groww Email System
date_updated: 2026-04-05
tags: [entity, system, email, project, figma]
---

# Groww Email System

Block-based email generation system for Groww and 915 brand campaigns. Built by Ashish Chhabra (Growth Engagement).

## Architecture: Tokens → Blocks → Recipes

```
Recipe JSON
    │
    ▼
Assembler Engine (assembler/engine.py)
    │
    ├── 1. Load recipe
    ├── 2. Resolve brand → load tokens (groww.py or nine15.py)
    ├── 3. Merge token_overrides
    ├── 4. For each block: load Jinja2 template → render with tokens + data
    ├── 5. Stitch into _base_email.html
    ├── 6. Strip whitespace
    └── 7. Validate (102KB, SEBI, unsubscribe, alt text)
    │
    ▼
Final email HTML
```

### Layer 1: Design Tokens

Python modules encoding every visual value. Two brand variants:
- `groww.py` — light theme (white bg, #353839 text, #00b386 green CTA)
- `nine15.py` — dark theme (#1a1a1a bg, white text, bright green CTA)
- `shared.py` — spacing, email constraints, icon SVGs

### Layer 2: Section Blocks (34 Jinja2 partials)

**Core (11)**: `_base_email`, `header_logo`, `hero_text`, `hero_image`, `article_section`, `factor_card`, `cta_button`, `social_proof_banner`, `divider`, `footer_standard`, `card_wrapper`

**Data (5)**: `chart_image`, `step_instruction`, `contract_row`, `filter_pills`, `listing_header`

**Onboarding (3)**: `app_screenshot_pair`, `product_category_grid`, `social_showcase`

**Transactional (2)**: `transaction_summary`, `status_badge`

**Newsletter (9)**: `bulletin_header`, `index_ticker`, `section_heading`, `concept_card`, `feedback_buttons`, `dot_divider`, `team_signoff`, `stock_table`, `callout`

**Promotional (4)**: `content_cards`, `featured_question`, `ipo_card`, `step_card`

See [[project-map]] for full block-by-block table.

### Layer 3: Email Recipes

JSON configs listing blocks in order with data. Example:
```json
{"meta": {"brand": "groww", "theme": "light", "subject": "..."}, 
 "blocks": [{"block": "header_logo", "data": {}}, ...]}
```

## Project Status

**Phase 6 (915 + Transactional)** — in progress as of 2026-04-08.
- Phases 1-5 complete (Tokens, Core Blocks, Data Blocks, Recipes + MCP, Migration)
- Next: Alert email recipes (price alert, margin call), 915 bg_image support

### Session 5 Updates (2026-04-05)

- **Figma MCP integration**: Two-tier image generation path added
  - **Primary**: chart-image-agent (SVG) → Figma MCP (`use_figma` components) → `get_screenshot` (2x PNG)
  - **Fallback**: chart-image-agent direct PNGs (only when Figma unavailable, must log in OPEN_ISSUES)
- **4 blocks refined**: step_instruction (VML badge fallback), contract_row (link circle), filter_pills (active/inactive states), listing_header
- **2 new recipes**: `groww_educational_commentary` (market commentary + 3 factor cards), `groww_feature_launch` (SL & TGT feature + 3 step instructions)
- **Renderer fix**: detects running async event loop, offloads Playwright to `threading.Thread`
- **New tokens**: `border_pill` and `border_pill_active` added to groww.py, nine15.py

### Session 6 Updates (2026-04-06)

- **OB-to-FID analysis**: Full onboarding email journey mapped from design PDF — 12 email types (4 educational + 8 onboarding Day 0–7)
- **3 new blocks**: `app_screenshot_pair` (text + screenshot side-by-side), `product_category_grid` (2-col product cards), `social_showcase` (social channel cards with CTAs)
- **9 onboarding recipes built**: welcome (D0), stocks (D1), SIP (D2), stocks_tools (D3), mf_explore (D4), stocks_features (D5a), mf_features (D5b), fno (D6), brand_story (D7)
- **Push notification specs**: Title + Body + CTA for all 9 days
- **All 13 recipes validated**: 0 issues, 12-17KB each
- **Nesting fixes**: product_category_grid and social_showcase reduced from 5 to 4 levels
- **Pending**: ~50 placeholder images need real app screenshots; 915 brand recipes still TBD

### Session 6b Updates (2026-04-06)

- **QA audit report**: Ruthless source verification against design PDFs — found 4 P0 issues (missing emojis in push titles, missing personalization tokens, missing recipe for Edu 1-3), 6 P1 issues
- **3 educational recipes built** (fixing P0): `groww_educational_basics` (Edu-1), `groww_educational_pretrading` (Edu-2), `groww_educational_first_trade` (Edu-3)

### Session 7 Updates (2026-04-07)

- **Natural Gas Mini educational email**: `groww_educational_natgas_mini.json` — lot size, price parity, expiry cycle, suitability. Chart images generated.
- **April 2026 expiry calendar email**: `groww_educational_april_expiry.json` — all MCX commodity expiry dates consolidated

### Session 8 Updates (2026-04-08)

- **3 new 915 brand recipes** (dark theme): `915_alert_market` (Nifty ATH market alert), `915_digest_daily_wrap` (daily trading wrap), `915_promotional_event_invite` (Inside 915 live masterclass)
- **11 new blocks**: transaction_summary, status_badge, bulletin_header, index_ticker, section_heading, concept_card, feedback_buttons, dot_divider, team_signoff, stock_table, callout
- **2 transactional recipes**: `groww_transactional_order_confirmation` (stock buy), `groww_transactional_sip_execution` (monthly SIP)
- **3 newsletter recipes** (from production): trading_bulletin (daily TA), daily_digest (gainers/losers/news), investment_weekly (most-traded by market cap)
- **Automated test suite**: `tests/test_all_recipes.py` — all 24 recipes pass
- **Skills rewritten**: `/groww-email` and `/915-email` updated for block-based MCP workflow
- **Phase 5 complete**, now Phase 6 (915 + Transactional)

### Current State (as of disk scan 2026-04-09)

- **34 blocks** — 11 core + 5 data + 3 onboarding + 2 transactional + 9 newsletter + 4 promotional
- **56 recipes** — 14 educational, 10 onboarding, 8 newsletter, 7 x 915, 6 promotional, 6 transactional, 2 alert, 1 feature, 1 infosec, 1 F&O journey
- **11 skills** — groww-email, 915-email, create-email (new), chart-image, + 7 utility/dev
- **New modules**: `analyzer/` (email classifier + detector + parser), `tools/` (chart_image, content_planner), `tests/`, `cli.py`
- **Pending**: Alert recipes (price alert, margin call, 52W H/L), 915 bg_image, resurrection recipes, ~50 app screenshots

See [[project-map]] for the full file-by-file inventory.

### Open Issue: I12

❓ **Figma file "Groww Email Assets" not yet created.** The Figma MCP workflow is documented but the actual Figma file with component templates (Price Card, Listing Card, Factor Card) doesn't exist yet. Needs Groww design team's commodity icons (barrel, gold, gas, silver).

## Two Sub-projects

| Component | Path | Purpose |
|-----------|------|---------|
| `groww-creative-mcp` | `/Users/ashishch/Downloads/To Build/groww-creative-mcp/` | MCP server with email assembly tools |
| `chart-image-agent` | `/Users/ashishch/Downloads/To Build/chart-image-agent/` | Python CLI for retina PNG chart cards |

## MCP Tools

| Tool | Purpose |
|------|---------|
| `groww_assemble_email(recipe_json)` | Recipe → complete HTML |
| `groww_generate_email()` | Higher-level email generation |
| `groww_list_blocks()` | List available blocks with params |
| `groww_generate_chart_image(template, config)` | Generate chart PNG |
| `groww_get_design_system(brand)` | Return token values |
| `groww_validate_email_html(html)` | Run validation checks |
| `groww_analyze_email()` | Analyze existing email HTML |

## Key Constraints

- Table-based HTML, inline styles only, max 3 nesting levels
- Max **102KB** total (Gmail clips beyond)
- VML fallback for Outlook CTA buttons
- SEBI disclaimer required
- Unsubscribe link required (CAN-SPAM)
- All images need alt text
- Charts: 3x retina, 420px logical width
- Font: Inter Tight (emails), Inter (charts)
- Indian number formatting: ₹1,23,456.00

## Design Token Source of Truth

Production email: "What moved Crude Oil this March?"

| Token | Value |
|-------|-------|
| Text primary | #353839 |
| Text body | #555555 |
| Text muted | #777777 |
| CTA green | #00b386 |
| CTA blue | #5367ff |
| Factor card bg | #E6FCF5 |
| Social proof bg | #f4fdf9 |

## Related

- [[email-channel]] — the Growth vertical's email channel this system serves
- [[netcore]] — ESP that delivers these emails
