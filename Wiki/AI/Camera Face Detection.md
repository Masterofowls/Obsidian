---
aliases: [face-detection, camera-detection, facial-recognition]
tags: [ai, face-detection, camera, recognition]
cssclass: wiki
---
# How Camera Face Detection Works

## Overview
Face detection identifies **human faces** in images/video using computer vision and AI.

## How It Works

### Classical Approach (Haar Cascades)
1. Scan image with a sliding window
2. Compare window to trained face templates
3. Use **AdaBoost** to quickly reject non-face regions
4. Output: bounding box around face

### Modern Approach (Deep Learning)
1. **MTCNN**: Multi-task CNN detects faces + landmarks
2. **RetinaFace**: Single-stage detector, very fast
3. **YOLO-Face**: Real-time detection

### Facial Recognition (identification)
1. Detect face → crop and align
2. Extract **face embedding** (512-dimensional vector)
3. Compare embedding to database of known faces
4. Cosine similarity or distance metric for matching

## Applications
- Phone unlock (Face ID)
- Photo organization
- Security surveillance
- Social media filters

## Related
- [[Wiki\AI\AI Image Detection|AI Image Detection]]
