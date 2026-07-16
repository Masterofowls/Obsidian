---
aliases: [frame-generation, frame-gen, interpolation]
tags: [hardware, gpu, rendering, frame-generation]
cssclass: wiki
---
# How Frame Generation Works

## Overview
Frame generation uses AI to **interpolate or predict** additional frames between real rendered frames, making animations appear smoother.

## Technologies
- **DLSS 3 Frame Generation** (NVIDIA)
- **FSR 3 Frame Generation** (AMD)
- **XeSS Frame Generation** (Intel)

## How It Works
1. GPU renders frames normally (e.g., 60 FPS)
2. AI analyzes motion vectors and previous/next frames
3. AI generates **intermediate frames** between real frames
4. Final output: 120 FPS (doubled from 60)

## Limitations
- Adds input latency (frame is generated, not rendered in response to input)
- Artifacts in fast motion or complex scenes
- Best for single-player, cinematic games

## Related
- [[Wiki\Hardware\GPU|GPU]]
- [[Wiki\Display\Rendering|Rendering]]
- [[Wiki\Display\Shaders|Shaders]]
