---
aliases: [shaders, shader-program, glsl]
tags: [display, shaders, gpu, rendering, programming]
cssclass: wiki
---
# How Shaders Work

## Overview
Shaders are **small programs** that run on the GPU to determine how each vertex or pixel looks.

## Types of Shaders

### Vertex Shader
- Runs once per vertex
- Transforms 3D position to 2D screen position
- Passes data (normals, UVs) to fragment shader

### Fragment Shader
- Runs once per pixel (fragment)
- Calculates the final color
- Applies textures, lighting, shadows, effects

### Compute Shader
- General-purpose GPU computation
- Used for: particles, post-processing, ML

## GLSL (OpenGL Shading Language)

```glsl
// Fragment shader example
#version 330
in vec2 TexCoord;
out vec4 FragColor;
uniform sampler2D ourTexture;

void main() {
    FragColor = texture(ourTexture, TexCoord);
}
```

## Related
- [[Wiki\Display\Rendering|Rendering]]
- [[Wiki\Hardware\GPU|GPU]]
- [[Wiki\Display\Textures|Textures]]
