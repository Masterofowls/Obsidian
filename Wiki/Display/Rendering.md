---
aliases: [rendering, how-rendering-works, computer-graphics]
tags: [display, rendering, graphics, visual]
cssclass: wiki
---
# What is Rendering & How Computer Graphics Work

## Overview
Rendering is the process of **converting 3D data into a 2D image** that can be displayed on screen.

## The Rendering Pipeline

### 1. Application Stage
- Game/app decides what to render
- Sends geometry, textures, and lighting data to GPU

### 2. Vertex Processing
- Each 3D point (vertex) is transformed
- **Model transform**: object → world space
- **View transform**: world → camera space
- **Projection**: 3D → 2D screen coordinates

### 3. Primitive Assembly
- Vertices are connected into triangles
- Triangles are the basic building blocks of 3D graphics

### 4. Rasterization
- Triangles are converted into **fragments** (potential pixels)
- Determines which pixels are covered by each triangle

### 5. Fragment Processing (Shading)
- For each fragment: calculate final color
- Apply **textures**, **lighting**, **shadows**
- Runs **shader programs**

### 6. Output
- Final image is written to the **framebuffer**
- Display reads the framebuffer and shows the image

## Related
- [[Wiki\Hardware\GPU|GPU]]
- [[Wiki\Display\Shaders|Shaders]]
- [[Wiki\Display\Textures|Textures]]
