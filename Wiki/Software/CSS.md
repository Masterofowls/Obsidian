---
aliases: [css, cascading-style-sheets, how-css-works]
tags: [software, css, styling, web]
cssclass: wiki
---
# How CSS Works

## Overview
CSS (Cascading Style Sheets) controls the **visual presentation** of HTML elements.

## How It Works

### Specificity (which rule wins)
1. Inline styles (highest)
2. ID selectors (`#id`)
3. Class selectors (`.class`)
4. Element selectors (`div`, `p`) (lowest)

### Cascade
- Rules are applied in order
- Later rules override earlier ones
- `!important` overrides everything (avoid using)

### Inheritance
- Some properties (color, font) are inherited by child elements
- Others (margin, padding) are not

## Box Model
Every element is a box:
```
Margin → Border → Padding → Content
```

## Selectors
```css
/* Element */
p { color: blue; }

/* Class */
.highlight { background: yellow; }

/* ID */
#header { font-size: 24px; }

/* Descendant */
div p { margin: 10px; }
```

## Related
- [[Wiki\Software\Browser|Browser]]
