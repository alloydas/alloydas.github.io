---
layout: page
title: FASTER
description: Font-Agnostic Scene Text Editing and Rendering Framework
img: assets/img/faster.jpg
importance: 4
category: work
chart:
  echarts: true
---

**FASTER** (Font-Agnostic Scene Text Editing and Rendering Framework) addresses scene text editing — replacing text in natural images while preserving the original font style, background texture, and visual coherence. Published at **WACV 2025**.

### Problem

Existing text editing methods require font labels or rely on style transfer that degrades quality at diverse fonts and backgrounds. FASTER removes this requirement via a font-agnostic rendering pipeline.

### Approach

- **Style extractor**: encodes the glyph style of source text independent of content
- **Text renderer**: renders new target text using the extracted style embedding
- **Background inpainting**: fills occluded regions naturally without visible seams
- **End-to-end training**: jointly optimized on paired synthetic and real-world data

### Results

Quantitative comparison against state-of-the-art scene-text-editing methods (↑ higher better, FID ↓ lower better):

| Metric    | SRNet | MOSTEL | DiffSTE | FASTER    |
| --------- | ----- | ------ | ------- | --------- |
| PSNR ↑    | 18.66 | 20.75  | 13.40   | **20.84** |
| SSIM ↑    | 0.614 | 0.707  | 0.389   | **0.790** |
| FID ↓     | 48.16 | 37.55  | 65.06   | **11.79** |
| OCR Acc ↑ | 14.79 | 20.10  | 11.90   | **30.30** |

FASTER cuts FID (perceptual distance, lower is better) to less than a third of the next-best method:

```echarts
{
  "tooltip": { "trigger": "axis", "formatter": "{b}: {c} FID" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["SRNet", "SwapText", "MOSTEL", "DiffSTE", "FASTER"] },
  "yAxis": { "type": "value", "name": "FID (lower better)" },
  "series": [
    {
      "type": "bar",
      "data": [
        { "value": 48.16, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 35.62, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 37.55, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 65.06, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 11.79, "itemStyle": { "color": "#4f8ef7" } }
      ],
      "barMaxWidth": 50,
      "itemStyle": { "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Qualitative Results

{% include figure.liquid loading="eager" path="assets/img/faster_results.jpg" class="img-fluid rounded z-depth-1" caption="Scene-text-editing results — target text rendered into natural images while preserving font style and background texture." %}

### Publication

Das, A. et al. _FASTER: A Font-Agnostic Scene Text Editing and Rendering Framework._ WACV 2025. (arXiv:2308.02905)

Work done at [CVPRU, Indian Statistical Institute Kolkata](https://cvpru.isical.ac.in/).
