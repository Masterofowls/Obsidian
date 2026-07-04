---
aliases: [gpu, graphics-card, how-gpu-works]
tags: [hardware, gpu, graphics, parallel]
cssclass: wiki
---
# How GPU Works

## Overview
A GPU (Graphics Processing Unit) is designed for **massive parallel computation** — thousands of small cores working simultaneously.

## GPU vs CPU
| Feature | CPU | GPU |
|---------|-----|-----|
| Cores | 4-64 | Thousands |
| Design | Few powerful cores | Many simple cores |
| Best at | Sequential tasks | Parallel tasks |
| Example | Running OS, logic | Rendering pixels, ML |

## How a GPU Renders

### Rasterization Pipeline
1. **Application Stage** — CPU sends draw calls and geometry data to GPU
2. **Vertex Processing** — GPU processes each vertex (3D point) — transforms, lighting
3. **Primitive Assembly** — Vertices are connected into triangles
4. **Rasterization** — Triangles are converted into pixels (fragments)
5. **Fragment Processing** — Each pixel is colored, textured, shaded
6. **Framebuffer** — Final image is written to memory → sent to display

### Shaders
- Small programs that run on the GPU for each vertex or pixel
- **Vertex Shader** — positions 3D points on a 2D screen
- **Fragment Shader** — determines the color of each pixel

## GPU Compute
- GPUs are now used for **non-graphics** workloads: AI/ML, crypto mining, scientific simulation
- **CUDA** (NVIDIA) and **ROCm** (AMD) allow general-purpose GPU programming

## Related
- [[Wiki\Hardware\VRAM|VRAM]]
- [[Wiki\Display\Rendering|Rendering]]
- [[Wiki\Display\Shaders|Shaders]]
