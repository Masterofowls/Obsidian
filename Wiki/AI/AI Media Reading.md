---
aliases: [ai-media-reading, ai-reading-media, ai-processing-images]
tags: [ai, media, image-processing, machine-learning]
cssclass: wiki
---
# How AI Reads Media Files

## Images
1. Image is divided into **patches** (e.g., 16×16 pixels)
2. Each patch is flattened and converted to a vector
3. Vision Transformer processes all patches in parallel
4. Outputs a description or classification

## Audio
1. Audio is converted to a **spectrogram** (visual representation)
2. CNN or Transformer processes the spectrogram
3. Outputs text (transcription) or classification

## Video
1. Frames are sampled at regular intervals
2. Each frame is processed like an image
3. Temporal relationships are modeled across frames
4. Outputs: captions, object tracking, scene description

## Related
- [[Wiki\AI\LLM|LLM]]
