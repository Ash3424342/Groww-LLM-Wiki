# Chart-Image-Agent

> Python CLI that generates email-ready PNG chart images at 3x retina.
> Location: `/Users/ashishch/Downloads/To Build/chart-image-agent/`

---

## How it works

```
JSON config → Jinja2 HTML template → Playwright headless Chromium screenshot at 3x → PNG
```

## Templates (5)

| Template | Description | Output size |
|----------|-------------|-------------|
| `price_card` | Single ticker price card with SVG line chart, period pills, link icon | 420px logical / 1260px physical |
| `listing_card` | Commodity list with filter tabs, contract rows, barrel icons | 420px / 1260px |
| `comparison` | Horizontal bar chart (green/red for positive/negative sectors) | 420px / 1260px |
| `portfolio` | Donut chart with custom legend | 420px / 1260px |
| `metric` | Big KPI number + sparkline area chart | 420px / 1260px |

## Theme support

Pass `"theme": "dark"` in config JSON. Defaults to light.

- Light: white card, dark text, dark chart line
- Dark: #1a1a1a card, white text, white chart line, adjusted icon colors

## Usage

```bash
cd chart-image-agent

# Generate from JSON config
python3 -m chart_agent generate examples/price_card.json -o output/chart.png

# Dark theme
python3 -c "
from chart_agent.generator import ChartGenerator
g = ChartGenerator()
g.generate({'template': 'price_card', 'theme': 'dark', ...}, 'output/dark.png')
"
```

## Key implementation details

- **Chart lines**: Inline SVG `<path>`, NOT Chart.js canvas. SVG scales perfectly at 3x.
- **Screenshot**: Playwright with `device_scale_factor=3`, viewport 520x520, 1500ms wait for fonts
- **Selector**: Screenshots just the `.card` element (or `.page-wrapper` for listing), not full page
- **Fonts**: Inter from Google Fonts (loaded in HTML, waited for via networkidle)
- **Indian formatting**: Comma system for lakhs/crores. ₹ symbol (U+20B9).
- **Zero change**: Grey #8b8b8b (not green) when amount and pct are both 0

## Dependencies

```
playwright>=1.40.0
Jinja2>=3.1.0
Pillow>=10.0.0 (optional)
```

```bash
pip install playwright Jinja2
python -m playwright install chromium
```
