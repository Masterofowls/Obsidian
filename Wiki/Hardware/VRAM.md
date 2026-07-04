---
aliases: [vram, video-memory, gpu-memory]
tags: [hardware, vram, gpu, memory]
cssclass: wiki
---
# How VRAM Works

## Overview
VRAM (Video RAM) is dedicated memory on a GPU that stores textures, framebuffers, and other graphics data.

## How It Works
- Similar to system RAM but optimized for the GPU's parallel access patterns
- Uses **wide memory buses** (256-bit, 384-bit, 512-bit) for massive bandwidth
- GDDR6X, GDDR7, and HBM3 are current types

## What VRAM Stores
- **Frame Buffer** — the image being displayed
- **Textures** — images wrapped onto 3D surfaces
- **Z-buffer** — depth information for 3D rendering
- **Shader data** — programs running on the GPU

## Why VRAM Matters
- Not enough VRAM → textures must stream from system RAM → stuttering
- 8GB is minimum for 1080p gaming
- 12-16GB for 1440p/4K
- 24GB+ for professional/AI work

## Related
- [[Wiki\Hardware\GPU|GPU]]
- [[Wiki\Hardware\RAM|RAM]]
