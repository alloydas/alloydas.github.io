---
layout: page
title: Lighting-Robust Instance Segmentation
description: SAM extended with a Lighting Convolutional Attention module
img: assets/img/lca.jpg
importance: 2
category: work
chart:
  echarts: true
---

**Lighting-aware Unified Model for Instance Segmentation** extends the Segment Anything Model (SAM) with a novel **Lighting Convolutional Attention (LCA)** module that makes segmentation robust to challenging real-world illumination conditions — harsh shadows, specular highlights, and uneven lighting common in agricultural and industrial settings.

### Problem

SAM achieves strong zero-shot segmentation on standard benchmarks, but degrades significantly under difficult lighting. Agricultural robotics and field deployments face highly variable natural illumination that breaks standard instance segmentation pipelines.

### Solution: LCA Module

The LCA module is inserted into the SAM image encoder. It:

1. Estimates a per-channel lighting map from the input feature map
2. Applies a convolutional attention mechanism to suppress lighting artifacts
3. Produces lighting-normalized features that feed into SAM's prompt encoder and mask decoder

### Results

mIoU under lighting-variant (V) conditions — the lightweight LCA adapter recovers most of SAM's lost accuracy and, combined with decoder fine-tuning, beats all baselines:

| Model            | Cityscapes (V) | VOC (V) | COCO (V) |
| ---------------- | -------------- | ------- | -------- |
| SAM-0 (baseline) | 0.560          | 0.608   | 0.652    |
| YOLOv11s         | 0.238          | 0.518   | 0.346    |
| LCA (ours)       | 0.756          | 0.682   | 0.788    |
| LCA+Dec (ours)   | 0.784          | 0.728   | 0.811    |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "legend": { "data": ["SAM-0 baseline", "LCA+Dec (ours)"], "top": "2%" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["Cityscapes", "VOC", "COCO"] },
  "yAxis": { "type": "value", "name": "mIoU (lighting-variant)", "max": 1 },
  "series": [
    {
      "name": "SAM-0 baseline",
      "type": "bar",
      "data": [0.56, 0.608, 0.652],
      "itemStyle": { "color": "#e0a96d", "borderRadius": [4, 4, 0, 0] }
    },
    {
      "name": "LCA+Dec (ours)",
      "type": "bar",
      "data": [0.784, 0.728, 0.811],
      "itemStyle": { "color": "#4f8ef7", "borderRadius": [4, 4, 0, 0] }
    }
  ]
}
```

### Qualitative Segmentation

{% include figure.liquid loading="eager" path="assets/img/lca_compare.jpg" class="img-fluid rounded z-depth-1" caption="Low-contrast scene: the SAM baseline floods the hillside with false positives (IoU 0.007) while LCA isolates the target instance (IoU 0.585)." %}

### Publications

- Preprint (2026): _Lighting-aware Unified Model for Instance Segmentation_ — Liu, Das et al. (arXiv:2605.20436)

### Status

Preprint available. Experiments run on custom agricultural datasets and standard COCO benchmarks.

Work done at [SCSLab, Iowa State University](https://sites.google.com/view/scslab-isu/home).
