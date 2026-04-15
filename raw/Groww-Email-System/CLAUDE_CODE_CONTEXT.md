# Claude Code Context — Groww Email System

> **Paste this at the start of a new Claude Code session to resume work.**
> **Last updated**: 2026-04-08 (Session 8)

---

## Project summary

I'm building a block-based email generation system for Groww (fintech, India). Two sub-projects:

1. **groww-creative-mcp** (`/Users/ashishch/Downloads/To Build/groww-creative-mcp/`) — MCP server that assembles emails from JSON recipes using reusable Jinja2 blocks. Registered in `~/.mcp.json`.

2. **chart-image-agent** (`/Users/ashishch/Downloads/To Build/chart-image-agent/`) — Python CLI that generates email-ready PNG chart images (price cards, listings, comparisons, etc.) at 3x retina via Playwright headless screenshots.

## Architecture

Three layers:
- **Tokens** (`tokens/groww.py`, `tokens/nine15.py`) — design system values (colors, fonts, spacing)
- **Blocks** (`blocks/*.html`) — 22 reusable Jinja2 email sections (header, hero, article, factor card, CTA, transaction summary, status badge, footer, etc.)
- **Recipes** (`recipes/*.json`) — JSON configs that list blocks in order with data. No new templates needed per email type.

The assembler engine (`assembler/engine.py`) takes a recipe → loads brand tokens → renders each block → stitches into base HTML skeleton → strips whitespace → validates (102KB, SEBI, unsubscribe, alt text).

## Workflow enforcement

CLAUDE.md contains a strict 6-step email generation workflow and a "Things you must NEVER do" blocklist. All sessions must follow the workflow: generate charts → write recipe → write copy → assemble → visual verify → update project log.

## What's built (all complete)

- All tokens: Groww light (default) + 915 light (default) + 915 dark (opt-in via `meta.theme: "dark"`)
- Assembler engine with token_overrides + theme support
- Validator (102KB, alt text, nesting, SEBI, unsubscribe)
- 22 blocks (all working, audited, QA-verified)
- 24 recipes:
  - 8 educational (commodity, natgas, natgas_mini, basics, pretrading, first_trade, commentary, april_expiry)
  - 1 feature_launch
  - 9 onboarding (welcome Day 0 → brand Day 7)
  - 1 infosec (digital_arrests)
  - 3 new 915 recipes (market alert, daily wrap digest, event invite) — dark theme
  - 2 transactional (order confirmation, SIP execution) — with new blocks
- All 24 recipes QA-audited — 0 validation issues, 10-20KB each
- MCP tools: groww_assemble_email, groww_generate_email, groww_list_blocks, groww_generate_chart_image, groww_validate_email_html, groww_analyze_email, groww_get_design_system
- Chart-image-agent: 5 templates with light + dark theme support
- Automated test suite: `tests/test_all_recipes.py` — all 24 recipes pass
- Skills updated: `/groww-email` and `/915-email` rewritten for block-based MCP workflow

## What needs to be done next

1. **Build alert email recipes**: price alert, margin call, 52W H/L
2. **Add 915 bg_image support**: base template needs background-image for 915 dark theme (currently solid color)
3. **Build remaining recipes**: 915 educational, resurrection types, portfolio summary digest
4. **Replace placeholder images** in onboarding recipes with real Groww app screenshots
5. **Create Figma "Groww Email Assets" file** (I12)

## Key design tokens (from production email 8)

```
Font: Inter Tight, weights 400-800
Text primary: #353839
Text body: #555555
Text muted: #777777
CTA green: #00b386
CTA blue: #5367ff
Factor card bg: #E6FCF5
Social proof bg: #f4fdf9
Divider: #f0f0f0
Card radius: 12-16px
CTA radius: 10px
```

## Recent fixes applied (Session 8)

- **transaction_summary nesting depth**: Flattened from inner-table-per-row (depth 5) to direct `<td>` pairs (depth 4)
- **Skills rewritten**: Both `/groww-email` and `/915-email` now reference block-based MCP workflow instead of old Node.js scripts

## Email constraints

- Max 102KB HTML (Gmail clips beyond this)
- Table-based layout only, inline styles, max 4 nesting levels
- VML fallback for Outlook CTA buttons
- SEBI disclaimer required
- Unsubscribe link required (CAN-SPAM)
- All images need alt text
- Retina images at 3x with width="420" on img tags

## Project log location

Obsidian vault: `/Users/ashishch/Desktop/Groww/Groww-Email-System/`
- `PROJECT_STATE.md` — current status
- `CHANGELOG.md` — all changes logged
- `OPEN_ISSUES.md` — known bugs and TODOs

**After completing any task, update PROJECT_STATE.md and CHANGELOG.md in the Obsidian vault.**
