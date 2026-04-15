# Design Tokens

> Source of truth for all visual values. Extracted from production emails.

---

## Groww (light theme)

### Colors

| Token | Hex | Usage |
|-------|-----|-------|
| `text_primary` | `#353839` | Headings, prices, ticker names |
| `text_body` | `#555555` | Body paragraphs, descriptions |
| `text_muted` | `#777777` | Labels, captions, meta text, period labels |
| `text_disclaimer` | `#999999` | Footer disclaimer, fine print |
| `positive` | `#00b386` | Gains, green CTA, brand accent |
| `positive_dark` | `#00D09C` | Brighter green (used in headlines: "What moved <span style='color:#00D09C'>Crude Oil</span>") |
| `negative` | `#eb5b3c` | Losses, red alerts |
| `cta_blue` | `#5367ff` | Feature launch CTAs, secondary actions |
| `cta_blue_alt` | `#4f74ee` | IPO email CTAs |
| `bg_page` | `#ffffff` | Email body background |
| `bg_card` | `#ffffff` | Card surfaces |
| `bg_factor` | `#E6FCF5` | Factor/insight card tint (light mint) |
| `bg_social_proof` | `#f4fdf9` | "India's No.1" banner background |
| `bg_insight` | `#eaf3f0` | Alternate insight card tint (from email 7) |
| `separator` | `#f0f0f0` | Between-section dividers |
| `border_footer` | `#eeeeee` | Footer top border |
| `footer_link` | `#777777` | Footer links color |

### Typography

| Role | Size | Weight | Line-height | Letter-spacing | Color token |
|------|------|--------|-------------|----------------|-------------|
| Hero headline | 21-30px | 700-800 | 1.3 | -0.3px | text_primary |
| Section title | 16-18px | 700 | 1.3 | 0 | text_primary |
| Card title | 14px | 700 | 1.4 | 0 | text_primary |
| Body | 14px (11pt) | 400 | 1.6-1.7 | 0.28px | text_body |
| Caption | 12px | 400 | 1.5 | 0.28px | text_muted |
| Social proof title | 14px | 800 | 1.3 | 3.5px | text_primary |
| CTA text | 14-15px | 700 | 1.0 | 1px | #ffffff |
| Footer body | 12px | 400 | 1.5 | 0 | text_muted |
| Disclaimer | 10px | 400 | 1.5 | 0.28px | text_disclaimer |
| Font family | `'Inter Tight', Arial, sans-serif` | | | | |
| Font import | `https://fonts.googleapis.com/css2?family=Inter+Tight:wght@400;500;600;700;800&display=swap` | | | | |

### Spacing

| Token | Value | Usage |
|-------|-------|-------|
| Email width | 600px | Max container width |
| Section padding | 0 40px | Left/right padding on content sections |
| Card padding | 20-24px | Inside card containers |
| Card border-radius | 12-16px | Card corners |
| CTA border-radius | 10px | Button corners |
| CTA padding | 14px 34px | Button internal padding |
| Factor card radius | 12px | Factor/insight cards |
| Section gap | 24-28px | Between major sections |

---

## 915 (dark theme)

### Colors

| Token | Hex | Usage |
|-------|-----|-------|
| `text_primary` | `#ffffff` | All primary text |
| `text_secondary` | `#cccccc` | Body text |
| `text_muted` | `#888888` | Labels, captions |
| `positive` | `#00d69a` | Brighter green for dark bg |
| `negative` | `#ff6b4a` | Brighter red for dark bg |
| `bg_page` | `#000000` | Email background |
| `bg_card` | `#1a1a1a` | Card surfaces |
| `border_card` | `#333333` | Card borders |
| `separator` | `#222222` | Between items |

---

## Chart-Image-Agent Tokens

Separate from email tokens. Used for PNG generation.

### Light

| Token | Hex |
|-------|-----|
| `card_bg` | `#ffffff` |
| `outer_bg` | `#f0f0f0` |
| `text_primary` | `#1a1a2a` |
| `text_secondary` | `#8b8b8b` |
| `chart_line` | `#1a1a1a` |
| `positive` | `#00b386` |
| `negative` | `#eb5b3c` |
| `pill_active_bg` | `#f4f4f4` |

### Dark

| Token | Hex |
|-------|-----|
| `card_bg` | `#1a1a1a` |
| `outer_bg` | `#000000` |
| `text_primary` | `#ffffff` |
| `text_secondary` | `#999999` |
| `chart_line` | `#ffffff` |
| `pill_active_bg` | `#2a2a2a` |
