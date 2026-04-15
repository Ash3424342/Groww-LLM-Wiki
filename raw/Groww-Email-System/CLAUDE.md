# CLAUDE.md — Groww Email System

## Project overview

This is a block-based email generation system for Groww (fintech, India). Two sub-projects:
1. `groww-creative-mcp` — MCP server that assembles emails from JSON recipes
2. `chart-image-agent` — Python CLI for generating chart PNG images

Full project documentation lives in the Obsidian vault at:
**`/Users/ashishch/Desktop/Groww/Groww-Email-System/`**

## CRITICAL: Update the project log after EVERY task

After completing any task (fix, feature, investigation), you MUST update these files:

### 1. `PROJECT_STATE.md` — Update the build progress table
- Change status of completed items
- Add new items if scope changed
- Update "Immediate next steps" section
- Update the session budget tracking table

### 2. `CHANGELOG.md` — Append to the changelog
Format:
```
## YYYY-MM-DD — Session N (model name)

### Added
- What was built

### Fixed  
- What was fixed

### Changed
- What was modified

### Pending
- What didn't get finished
```

### 3. `OPEN_ISSUES.md` — Update issue statuses
- Close resolved issues (change status to Closed, add resolution date)
- Add new issues discovered during the session
- Reprioritize if needed

### 4. `CLAUDE_CODE_CONTEXT.md` — Update the resume context
- Update "What's built" section if new things were built
- Update "What needs to be done next" section
- Update "Recent fixes applied" section
- This file gets pasted into new sessions, so it must be current

## Project structure

```
groww-creative-mcp/
├── server.py                    # MCP server entry point
├── assembler/
│   ├── engine.py                # Recipe → rendered HTML
│   └── validator.py             # 102KB, SEBI, alt text checks
├── tokens/
│   ├── groww.py                 # Groww light theme tokens
│   ├── nine15.py                # 915 dark theme tokens
│   └── shared.py                # Shared spacing, constraints
├── blocks/                      # 15 Jinja2 email section blocks
│   ├── _base_email.html
│   ├── header_logo.html
│   ├── hero_text.html
│   ├── hero_image.html
│   ├── article_section.html
│   ├── factor_card.html
│   ├── cta_button.html
│   ├── social_proof_banner.html
│   ├── divider.html
│   ├── footer_standard.html
│   ├── card_wrapper.html
│   ├── chart_image.html
│   ├── step_instruction.html
│   ├── contract_row.html
│   ├── filter_pills.html
│   └── listing_header.html
├── recipes/                     # JSON email configs
├── formatters.py                # Indian number formatting, ₹ symbol
└── output/                      # Generated test emails

chart-image-agent/
├── chart_agent/
│   ├── config.py                # COLORS_LIGHT, COLORS_DARK, ICONS
│   ├── generator.py             # Config → HTML → PNG pipeline
│   ├── renderer.py              # Playwright screenshot engine
│   ├── formatters.py            # Price formatting, SVG path builder
│   └── templates/               # 5 chart HTML templates
└── output/
```

## Key constraints

- Email HTML must be table-based, inline styles only, max 3 nesting levels
- Max 102KB total (Gmail clips beyond this)
- VML fallback for Outlook CTA buttons
- SEBI disclaimer required on all financial emails
- Unsubscribe link required (CAN-SPAM)
- All images need alt text
- Chart PNGs: 3x retina, 420px logical width
- Font: Inter Tight for emails, Inter for charts
- Indian number formatting: ₹1,23,456.00 (lakhs/crores system)

## How to test

```bash
# Generate email from recipe
cd groww-creative-mcp
python3 -c "
from assembler.engine import assemble_email
import json
recipe = json.load(open('recipes/groww_educational_commodity.json'))
html = assemble_email(recipe)
open('output/test.html', 'w').write(html)
"
open output/test.html

# Generate chart image
cd chart-image-agent
python3 -m chart_agent generate examples/price_card.json -o output/chart.png

# Validate email
python3 -c "
from assembler.validator import validate_html
html = open('output/test.html').read()
issues = validate_html(html)
print(issues if issues else 'All checks passed')
"
```

## Design token source of truth

Production email: "What moved Crude Oil this March?" (email 8 in screenshots catalog)
- Text primary: #353839
- Text body: #555555
- Text muted: #777777
- CTA green: #00b386
- CTA blue: #5367ff
- Factor card bg: #E6FCF5
- Social proof bg: #f4fdf9
