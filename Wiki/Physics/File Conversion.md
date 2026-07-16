---
aliases: [file-conversion, format-conversion, transcoding]
tags: [software, conversion, transcoding, media]
cssclass: wiki
---
# How File Format Conversion Works

## Overview
File conversion transforms data from one format to another.

## How It Works
1. **Read** — Parser reads the source file
2. **Decode** — Data is decoded into a raw/intermediate format
3. **Transform** — Data is converted to the target format
4. **Encode** — Data is encoded in the target format
5. **Write** — Output is written to a new file

## Lossy vs Lossless

### Lossy (JPEG, MP3, H.264)
- Discards "less important" data
- Smaller files but quality degrades each conversion
- Cannot be reversed

### Lossless (PNG, FLAC, H.265)
- Preserves all data
- Larger files but no quality loss
- Perfectly reversible

## Related
- [[Wiki\Physics\File Formats|File Formats]]
