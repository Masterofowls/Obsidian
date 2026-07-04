---
aliases: [gif, animated-gif, gif-format]
tags: [software, gif, image, animation]
cssclass: wiki
---
# How GIF Works

## Overview
GIF (Graphics Interchange Format) is an image format that supports **animation** and **transparency**.

## How It Works
- Uses **LZW compression** (lossless, dictionary-based)
- Limited to **256 colors** per frame (8-bit palette)
- Animation: stores multiple frames with delay timing
- Transparency: 1-bit (fully transparent or fully opaque)

## GIF Animation
1. First frame is displayed
2. After specified delay (e.g., 100ms), next frame is shown
3. Loop count determines how many times to repeat
4. Frame disposal: how previous frame is handled (clear, restore, leave)

## Limitations
- Only 256 colors → banding on photos
- No alpha transparency (only binary)
- Larger file sizes than modern video formats for same content
- No audio

## Modern Alternatives
- **WebP**: Better compression, more colors, alpha transparency
- **MP4/WebM**: Better for video-like animations

## Related
- [[Wiki\Physics\File Formats|File Formats]]
