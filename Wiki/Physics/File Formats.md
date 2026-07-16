---
aliases: [file-format, file-type, format-conversion, bitrate, hdr, gif]
tags: [software, file-format, media, encoding]
cssclass: wiki
---
# What is File Format & How Conversion Works

## What is a File Format
A file format defines how data is **organized and encoded** in a file.

## Common Formats
| Type | Formats |
|------|---------|
| Text | .txt, .md, .json, .csv |
| Document | .pdf, .docx, .xlsx |
| Image | .jpg, .png, .gif, .webp |
| Video | .mp4, .mkv, .webm |
| Audio | .mp3, .wav, .flac |

## What is Bitrate
- Amount of data per second (kbps or Mbps)
- Higher bitrate = better quality = larger file
- Video: 1-50 Mbps typical
- Audio: 128-320 kbps typical

## What is HDR (High Dynamic Range)
- Captures wider range of brightness and color
- More detail in shadows and highlights
- Formats: HDR10, Dolby Vision, HLG

## How GIF Works
- Uses **LZW compression** (lossless)
- Limited to **256 colors** per frame
- Supports animation by storing multiple frames
- No audio support

## File Format Conversion
- **Transcoding**: Decoding from one format → encoding to another
- Example: MP4 → WebM = decode H.264 → encode VP9
- Lossy formats (JPEG, MP3) lose quality on each conversion
- Lossless formats (PNG, FLAC) preserve quality

## Related
- [[Wiki\Display\Rendering|Rendering]]
