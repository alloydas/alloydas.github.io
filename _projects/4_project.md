---
layout: page
title: FASTER
description: Font-Agnostic Scene Text Editing and Rendering Framework
img:
importance: 4
category: work
---

**FASTER** (Font-Agnostic Scene Text Editing and Rendering Framework) addresses scene text editing — replacing text in natural images while preserving the original font style, background texture, and visual coherence. Published at **WACV 2025**.

### Problem

Existing text editing methods require font labels or rely on style transfer that degrades quality at diverse fonts and backgrounds. FASTER removes this requirement via a font-agnostic rendering pipeline.

### Approach

- **Style extractor**: encodes the glyph style of source text independent of content
- **Text renderer**: renders new target text using the extracted style embedding
- **Background inpainting**: fills occluded regions naturally without visible seams
- **End-to-end training**: jointly optimized on paired synthetic and real-world data

### Publication

Das, A. et al. *FASTER: A Font-Agnostic Scene Text Editing and Rendering Framework.* WACV 2025.
