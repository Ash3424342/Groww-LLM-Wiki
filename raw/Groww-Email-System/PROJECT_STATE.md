# Project State

> **Last updated**: 2026-04-08
> **Current phase**: Phase 6 (915 + Transactional) — in progress
> **Next action**: Build alert email type (price alert, margin call), add bg_image support for 915 dark theme

---

## Build progress

### Phase 1: Tokens + Engine Foundation — COMPLETE

| File | Status | Notes |
|------|--------|-------|
| `tokens/__init__.py` | Done | |
| `tokens/groww.py` | Done | Locked from production email 8. Primary: #353839, body: #555555, muted: #777777 |
| `tokens/nine15.py` | Done | Dark theme. Primary: #ffffff, bg: #1a1a1a |
| `tokens/shared.py` | Done | Spacing, email constraints, icon SVGs |
| `assembler/__init__.py` | Done | |
| `assembler/engine.py` | Done | Supports token_overrides per recipe. Blank-line stripping added. |
| `assembler/validator.py` | Done | 102KB, alt text, nesting, unsubscribe, SEBI checks |

### Phase 2: Core Blocks — COMPLETE

| Block | File | Status | Notes |
|-------|------|--------|-------|
| Base skeleton | `_base_email.html` | Done | DOCTYPE, fonts, dark mode meta, preheader, outer/inner tables |
| Header logo | `header_logo.html` | Done | Two variants: banner image vs inline logo |
| Hero text | `hero_text.html` | Done | Headline + subtitle + optional overline. Whitespace trimmed. |
| Hero image | `hero_image.html` | Done | Full-width with optional border-radius |
| Article section | `article_section.html` | Done | Heading + paragraphs + optional bullets. Whitespace trimmed. |
| Factor card | `factor_card.html` | Done | Tinted bg (#E6FCF5), centered text, 12px radius, no icons |
| CTA button | `cta_button.html` | Done | Green (#00b386) or blue (#5367ff). VML Outlook fallback. |
| Social proof | `social_proof_banner.html` | Done | "INDIA'S NO.1" bar. Apostrophe entity fixed. |
| Divider | `divider.html` | Done | 1px line or spacer |
| Footer | `footer_standard.html` | Done | Social icons + SEBI + unsubscribe + registered office |
| Card wrapper | `card_wrapper.html` | Done | Wraps blocks in card container with shadow |

### Phase 3: Data Blocks — COMPLETE

| Block | File | Status | Notes |
|-------|------|--------|-------|
| Chart image | `chart_image.html` | Done | Hosted PNG with border-radius |
| Step instruction | `step_instruction.html` | Done | Numbered steps with screenshots, VML badge fallback |
| Contract row | `contract_row.html` | Done | Commodity rows with icon + price + change + link circle |
| Filter pills | `filter_pills.html` | Done | Horizontal pill row with active/inactive states |
| Listing header | `listing_header.html` | Done | Back arrow + title + action link |

### Phase 4: Recipes + MCP Integration — COMPLETE

| Recipe | Status | Notes |
|--------|--------|-------|
| `groww_educational_commodity.json` | Done | Matches production email 8 structure |
| `groww_educational_natgas.json` | Done | Natural Gas educational, same structure as commodity. Real MCX data. |
| `groww_educational_commentary.json` | Done | "Sailing through volatile markets" style |
| `groww_feature_launch.json` | Done | MTF SL/TGT style with step instructions |
| `groww_onboarding_welcome.json` | Done | Day 0: Welcome + product grid + home screen |
| `groww_onboarding_stocks.json` | Done | Day 1: First stock tutorial with app screenshots + steps |
| `groww_onboarding_sip.json` | Done | Day 2: First SIP tutorial with app screenshots + steps |
| `groww_onboarding_stocks_tools.json` | Done | Day 3: Stock tools — screener, trends, watchlist |
| `groww_onboarding_mf_explore.json` | Done | Day 4: MF explore — sort, collections, compare, import |
| `groww_onboarding_stocks_features.json` | Done | Day 5a: Stock features — MTF, IPO, ETFs, intraday |
| `groww_onboarding_mf_features.json` | Done | Day 5b: MF features — trending, popular, performance |
| `groww_onboarding_fno.json` | Done | Day 6: F&O trading with 3-step instructions + charts |
| `groww_onboarding_brand.json` | Done | Day 7: Brand story + social showcase |
| MCP tools updated in `server.py` | Done | `groww_assemble_email(recipe_json)` + `groww_list_blocks()` |

### Phase 5: Migration + Cleanup — COMPLETE

| Task | Status | Notes |
|------|--------|-------|
| Verify recipe output matches production email 8 | **DONE** | Light images generated, email rebuilt with light chart + listing PNGs |
| Delete old monolithic templates | **DONE** | `templates/email/` deleted in Session 2b. `templates/charts/` kept (used by chart-image-agent) |
| Update skills to reference block system | **DONE** | Both `/groww-email` and `/915-email` rewritten for block-based MCP workflow |
| Wire server.py to new assembler | **DONE** | Old tools deleted, `groww_assemble_email(recipe_json)` wired to assembler |
| Figma MCP workflow documented | **DONE** | CLAUDE.md updated with two-tier image generation, Figma skill file created |
| Create Figma "Groww Email Assets" file | Not started | I12: Needs manual or automated setup. Requires Groww design team icons. |
| Automated test suite | **DONE** | `tests/test_all_recipes.py` — verifies all recipes assemble with 0 issues |

### Phase 6: 915 + Transactional + New Email Types — IN PROGRESS

| Task | Status | Notes |
|------|--------|-------|
| 915 market alert recipe | **DONE** | `915_alert_market.json` — dark theme, Nifty ATH alert |
| 915 daily wrap digest recipe | **DONE** | `915_digest_daily_wrap.json` — dark theme, equity + F&O + commodities |
| 915 event invite recipe | **DONE** | `915_promotional_event_invite.json` — dark theme, Inside 915 webinar |
| `transaction_summary` block | **DONE** | 2-column key-value table with heading + highlight row, flat nesting |
| `status_badge` block | **DONE** | Success/pending/failed badge with icon + color |
| Order confirmation recipe | **DONE** | `groww_transactional_order_confirmation.json` — stock buy confirmation |
| SIP execution recipe | **DONE** | `groww_transactional_sip_execution.json` — monthly SIP processing |
| Alert email recipes | Not started | Price alert, margin call, 52W H/L |
| 915 bg_image support | Not started | Base template needs background-image for 915 dark theme |

---

## Chart-Image-Agent Status

| Feature | Status | Notes |
|---------|--------|-------|
| Light theme (5 templates) | Done | price_card, listing_card, comparison, portfolio, metric |
| Dark theme | Done | `COLORS_DARK`, `ICONS_DARK` added. Pass `"theme": "dark"` in config. |
| Zero-change grey color | Done | Was green, now #8b8b8b for zero values |
| Filter pill overflow fix | Done | Reduced padding from 18px to 12px |
| Pill border tokenized | Done | Was hardcoded #ddd, now uses `{{ c.border_pill }}` |
| Listing card green glow border | Done | Matches reference: green-tinted border + shadow, Mini card wider |
| Listing card compact spacing | Done | Tighter padding, smaller fonts, matches reference screenshot |
| Sync Playwright renderer | Done | Switched from async_api + asyncio.run() to sync_api. Fixes MCP tool invocation. |

---

## Immediate next steps

1. **Build alert email recipes**: price alert, margin call, 52W H/L
2. **Add bg_image support for 915 dark theme**: base template needs background-image rendering
3. **Build remaining recipes**: 915 educational, resurrection types
4. **Replace placeholder images** in onboarding recipes with real Groww app screenshots
5. **Create Figma "Groww Email Assets" file** (I12)

---

## Session budget tracking

| Date | Session | Model | Tokens used | Budget hit | Notes |
|------|---------|-------|-------------|------------|-------|
| 2026-04-02 | Session 1 | Opus 4.6 (1M) | ~685K/1M | $50.31 | Built phases 1-4, 3 audit rounds, 18+ bugs fixed |
| 2026-04-03 | Session 2 | Opus 4.6 (1M) | ~700K/1M | — | Dark theme for charts, 915 light default fix, listing card quality, light images in email |
| 2026-04-08 | Session 8 | Opus 4.6 (1M) | — | — | 915 recipes (3), transactional blocks (2) + recipes (2), test suite, skills rewrite |
