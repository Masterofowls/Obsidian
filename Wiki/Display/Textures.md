---
aliases: [textures, texture-mapping, 3d-texture]
tags: [display, textures, 3d, mapping]
cssclass: wiki
---
# What are Textures

## Overview
Textures are **2D images** that are wrapped onto 3D surfaces to add detail without increasing geometry.

## How It Works
1. 3D model has **UV coordinates** (mapping from 3D surface to 2D image)
2. GPU samples the texture at each pixel using UV coordinates
3. Texture color is combined with lighting to produce the final pixel color

## Types of Textures
| Type | Purpose |
|------|---------|
| Diffuse/Albedo | Base color of the surface |
| Normal map | Simulates surface bumps |
| Specular | Shininess/reflectivity |
| Roughness | How rough/smooth the surface is |
| Ambient Occlusion | Soft shadows in crevices |

## Texture Filtering
- **Nearest**: Sharp, pixelated (retro look)
- **Bilinear/Trilinear**: Smooth interpolation
- **Anisotropic**: Better quality at grazing angles

## Related
- [[Wiki\Display\Rendering|Rendering]]
- [[Wiki\Display\Shaders|Shaders]]
