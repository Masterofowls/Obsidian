---
aliases: [llm, large-language-model, how-llm-works, ai]
tags: [ai, llm, machine-learning, neural-network]
cssclass: wiki
---
# How LLMs Work

## Overview
LLMs (Large Language Models) are AI systems that **predict the next token** in a sequence, trained on massive text datasets.

## How It Works

### Training
1. Model reads billions of text examples
2. Learns statistical patterns: which words follow which
3. Adjusts billions of parameters (weights) to minimize prediction errors
4. Result: a neural network that can generate coherent text

### Inference (Generating Text)
1. User provides a **prompt**
2. Model converts tokens to vectors (embeddings)
3. **Transformer layers** process the vectors through self-attention
4. Model outputs probability distribution for next token
5. Token is selected (with temperature/randomness)
6. Process repeats until response is complete

## Why LLMs "Know Everything"
- Not storing exact facts, but **statistical patterns** from training data
- Can generalize and combine knowledge in new ways
- Limited by training data cutoff date

## How LLMs Work Offline
- Once trained, the model is just **weights in a file**
- No internet connection needed for inference
- Model runs entirely on local hardware (GPU/CPU)

## Why Small LLMs Contain Broad Information
- Compression during training captures general knowledge
- Smaller models sacrifice depth for size
- Can be fine-tuned for specific domains

## Related
- [[Wiki\AI\AI Text Reading|AI Text Reading]]
- [[Wiki\AI\AI Image Detection|AI Image Detection]]
