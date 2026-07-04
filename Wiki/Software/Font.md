---
aliases: [font, how-font-works, typography, text-rendering]
tags: [software, font, typography, text]
cssclass: wiki
---
# How Text Fonts Work

## Overview
A font defines the **visual appearance** of text characters.

## Font Formats
| Format | Description |
|--------|-------------|
| TTF (TrueType) | Outlines with quadratic curves |
| OTF (OpenType) | Advanced features, ligatures |
| WOFF/WOFF2 | Web fonts, compressed |

## How Fonts Render Text
1. Character code (Unicode) is looked up in the font's **glyph table**
2. **Outline data** defines the shape of each character
3. **Rasterizer** converts outlines to pixels at the correct size
4. **Hinting** adjusts outlines for pixel-perfect rendering at small sizes

## Vector vs Bitmap
- **Vector fonts** (TTF, OTF): scale to any size, always sharp
- **Bitmap fonts**: fixed sizes, look pixelated when scaled

## Font Rendering Technologies
- **FreeType** (Linux, Android)
- **DirectWrite** (Windows)
- **Core Text** (macOS)

## Related
- [[Wiki\Display\Rendering|Rendering]]
