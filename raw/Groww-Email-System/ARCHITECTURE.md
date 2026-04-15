# Architecture

> Three-layer system: Tokens → Blocks → Recipes

---

## Layer 1: Design tokens

Python modules in `tokens/` that encode every visual value. Two brand variants:
- `groww.py` — light theme (white bg, dark text, green/blue CTAs)
- `nine15.py` — dark theme (black bg, white text, bright green CTA)
- `shared.py` — spacing, email constraints, icon SVGs

Tokens are the single source of truth. Blocks never hardcode colors — they reference `{{ t.colors.text_primary }}`.

## Layer 2: Section blocks

15 Jinja2 partials in `blocks/`. Each receives a tokens dict (`t`) and a data dict (`d`).

```
_base_email.html      — HTML skeleton (DOCTYPE, fonts, preheader, outer table)
header_logo.html      — Logo bar
hero_text.html        — Headline + subtitle
hero_image.html       — Full-width image
article_section.html  — Heading + paragraphs
factor_card.html      — Tinted card (mint bg, centered text)
cta_button.html       — Green or blue button (VML for Outlook)
social_proof_banner   — "INDIA'S NO.1" bar
divider.html          — 1px line or spacer
footer_standard.html  — Social icons + SEBI + unsubscribe
card_wrapper.html     — Card container wrapping other blocks
chart_image.html      — Hosted PNG chart
step_instruction.html — Numbered step + screenshot
contract_row.html     — Commodity listing rows
filter_pills.html     — Horizontal filter tabs
listing_header.html   — Page title with back arrow
```

## Layer 3: Email recipes

JSON configs in `recipes/` that list blocks in order with data:

```json
{
  "meta": {
    "brand": "groww",
    "theme": "light",
    "subject": "What moved Crude Oil?",
    "preheader": "MCX Crude Oil surged 49%",
    "token_overrides": {}
  },
  "blocks": [
    {"block": "header_logo", "data": {"brand": "groww"}},
    {"block": "hero_text", "data": {"headline": "...", "subtitle": "..."}},
    {"block": "chart_image", "data": {"image_url": "...", "alt_text": "..."}},
    {"block": "factor_card", "data": {"title": "...", "body": "..."}},
    {"block": "cta_button", "data": {"text": "Track on Groww", "url": "..."}},
    {"block": "footer_standard", "data": {"brand": "groww"}}
  ]
}
```

## Assembly flow

```
Recipe JSON
    │
    ▼
Assembler Engine (assembler/engine.py)
    │
    ├── 1. Load recipe
    ├── 2. Resolve brand → load tokens (groww.py or nine15.py)
    ├── 3. Merge token_overrides on top of defaults
    ├── 4. For each block:
    │       ├── Load block Jinja2 template
    │       └── Render with tokens + block data
    ├── 5. Stitch all rendered blocks into _base_email.html
    ├── 6. Strip excess whitespace
    └── 7. Validate (102KB, SEBI, unsubscribe, alt text)
    │
    ▼
Final email HTML (ready for CleverTap/NARAD)
```

## MCP tools

| Tool | Purpose |
|------|---------|
| `groww_assemble_email(recipe_json)` | Recipe → complete HTML |
| `groww_list_blocks()` | List available blocks with params |
| `groww_generate_chart_image(template, config)` | Generate chart PNG |
| `groww_get_design_system(brand)` | Return token values |
| `groww_validate_email_html(html)` | Run validation checks |
