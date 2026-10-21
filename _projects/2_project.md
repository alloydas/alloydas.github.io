---
layout: page
title: Lighting-Robust Instance Segmentation
description: WACV 2027 · Lighting-robust SAM via Lighting Convolutional Attention and pairwise training
img: assets/img/lca.jpg
importance: 2
category: work
chart:
  echarts: true
---

**Lighting-aware Unified Model for Instance Segmentation** makes the Segment Anything Model (SAM) robust to real-world illumination — night scenes, dim interiors, harsh shadows, overexposure and mixed artificial/natural light — without fine-tuning its heavy backbone. We call the framework **PLAP-LCA**: a **P**airwise **L**ighting **A**ugmentation **P**ipeline plus a **L**ighting **C**onvolutional **A**ttention adapter.

**Authors:** Qisai Liu\*, **Alloy Das**\*, Zhanhong Jiang, Joshua R. Waite, Aditya Balu, Adarsh Krishnamurthy, Soumik Sarkar
<br><small>Iowa State University · \*Equal contribution</small>

**Accepted at WACV 2027** · [arXiv:2605.20436](https://arxiv.org/abs/2605.20436) · [PDF](https://arxiv.org/pdf/2605.20436) · [LinkedIn post](https://www.linkedin.com/posts/alloy-das-a512a916b_wacv2027-computervision-instancesegmentation-share-7516522194076872704-uib_/)

{% include figure.liquid loading="eager" path="assets/img/lca_pipeline.jpg" class="img-fluid rounded z-depth-1" caption="PLAP-LCA. Clean and lighting-variant images share SAM's frozen ViT-B encoder with LCA modules injected into the last two blocks. Only the LCA weights, per-block scalar gates and the mask decoder are trained, with segmentation and consistency losses." %}

### Problem

SAM generalizes impressively zero-shot, but it was trained mostly on well-lit, high-quality images and degrades under adverse illumination. That matters wherever lighting variation is the norm: autonomous driving at night, robotic manipulation, medical imaging, and agricultural monitoring across the day–night cycle. Most segmentation work treats lighting as a side issue handled by generic augmentation or domain adaptation. We tackle it at three levels at once: **data**, **architecture** and **training**.

### Contributions

1. **LCA module** — a lightweight adapter that gives a frozen foundation model illumination-robust structural features.
2. **Pairwise training** — a curriculum of clean/variant image pairs with a feature-consistency loss that explicitly closes the gap between ideal and adverse lighting.
3. **Empirical study + new dataset** — a lighting-vulnerability study on COCO, VOC and Cityscapes, plus a new **Unity-based synthetic dataset** with physically rendered illumination.

### Data: two ways to make lighting pairs

Lighting changes never move object geometry, so masks, boxes and labels stay valid across every lighting variant. Each clean image and its variant share one ground truth, which gives a direct training signal for invariance.

- **PLAP (image-space augmentation)** works on any existing dataset. It composes physically motivated operations — exposure (in linear light), directional shadow, warm/cool colour temperature, vignetting, contrast, gamma, brightness, film grain and atmospheric haze — with **conflict-aware sampling** (e.g. never warm _and_ cool, never haze _and_ contrast) and a **three-level severity protocol**: one subtle change at Severity 1, up to two at Severity 2, up to three extreme operations at Severity 3.
- **Unity-Lighting (physically rendered)** captures what 2D edits can't: real 3D light transport, sunlight reflections and mixed illuminants. A lighting rig manipulates sun angle, colour temperature, indoor intensity, fill lights and directional light inside indoor apartment scenes. Every viewpoint is re-rendered under **Clean, Mild, Moderate and Severe** lighting with pixel-perfect instance masks (481 classes; 1,418 train / 251 val images).

{% include figure.liquid loading="lazy" path="assets/img/lca_unity.jpg" class="img-fluid rounded z-depth-1" caption="Unity synthetic data pipeline: a physical lighting rig (top), a capture loop that moves 16 cameras and records instance masks via the Unity Perception API (middle), and every viewpoint re-rendered from bright daylight to night with harsh artificial light (bottom)." %}

### Method: the LCA module

Illumination corrupts features in three ways — **globally** (brightness or colour shifts bias whole channels), **locally** (shadows and specular highlights hit specific regions) and **structurally** (lost edge contrast hides object boundaries). LCA answers each with a parallel attention gate:

- **Channel gate** — average- and max-pooled channel statistics through a shared MLP recalibrate the channels that swing with lighting.
- **Spatial gate** — a 7×7 convolution over channel-mean and channel-max maps finds shadow and highlight regions (just 98 parameters).
- **Contrast gate** — a learned 1×1 projection to an intensity map, a **fixed Laplacian** edge detector, per-sample normalization and a 3×3 refinement pick out lighting edges.

The gates are **multiplied**, so a feature survives only when its channel matters, its location is relevant and a lighting edge is present. A depthwise-separable projection maps the result back into the residual stream.

{% include figure.liquid loading="lazy" path="assets/img/lca_module.jpg" class="img-fluid rounded z-depth-1" caption="The LCA module: channel, spatial and Laplacian-contrast gates run in parallel, are fused by element-wise multiplication, projected by a depthwise-separable convolution, and added through a learned scalar gate." %}

**Safe integration into SAM.** All 12 ViT-B blocks stay frozen, and LCA is attached to the last two. The pointwise projection is **zero-initialized**, so training starts as an _exact_ copy of pretrained SAM, and LCA "fades in" as it learns. Each block also has its own learnable gate, so blocks that see more lighting-sensitive features can take more adaptation.

### Training: dual-stream consistency

Each sample is a (clean, variant) pair of the same scene. Both pass through the encoder and are decoded with the **same prompts** (a random foreground point and a box), so any difference in the predicted masks comes only from lighting. The loss combines:

- **Supervised loss** — BCE + Dice on both streams, weighted equally.
- **Consistency loss** — an L1 penalty between the clean and variant mask predictions (weight 0.1). It needs no extra labels, only the image pairs.

### Results

mIoU under clean (C) and lighting-variant (V) conditions on four benchmarks:

| Model            | Cityscapes C / V  | VOC C / V         | COCO C / V        | Unity C / V       |
| ---------------- | ----------------- | ----------------- | ----------------- | ----------------- |
| SAM-0 (baseline) | 0.562 / 0.560     | 0.614 / 0.608     | 0.658 / 0.652     | 0.610 / 0.606     |
| Decoder FT       | 0.770 / 0.767     | 0.725 / 0.713     | 0.806 / 0.804     | 0.823 / 0.808     |
| YOLOv11s         | 0.245 / 0.238     | 0.542 / 0.518     | 0.364 / 0.346     | 0.052 / 0.038     |
| LCA (ours)       | 0.759 / 0.756     | 0.690 / 0.682     | 0.792 / 0.788     | 0.801 / 0.797     |
| LCA+Dec (ours)   | **0.787 / 0.784** | **0.735 / 0.728** | **0.814 / 0.811** | **0.833 / 0.837** |

LCA+Dec is best on every benchmark, and LCA keeps the clean-vs-variant gap very small, which is the signature of lighting robustness.

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

On lighting-variant Cityscapes, LCA raises mean instance IoU over the SAM baseline from **0.235 to 0.380 (+61.7%)** and wins on **195 of 290 instances (67.2%)**. The biggest gains are in the hardest cases, where lighting disrupts the encoder most.

{% include figure.liquid loading="lazy" path="assets/img/lca_iou.jpg" class="img-fluid rounded z-depth-1" caption="Instance-level IoU on lighting-variant Cityscapes. Left: LCA shifts the IoU distribution to the right (mean 0.380 vs 0.235). Right: points above the diagonal are instances where LCA beats the SAM baseline." %}

### Qualitative Segmentation

{% include figure.liquid loading="lazy" path="assets/img/lca_compare.jpg" class="img-fluid rounded z-depth-1" caption="Low-contrast scene: the SAM baseline floods the hillside with false positives (IoU 0.007) while LCA isolates the target instance (IoU 0.585)." %}

GradCAM shows _why_: under degraded lighting the baseline spreads attention across low-contrast background, while LCA's contrast gate pulls it back onto high-contrast object boundaries. The same behaviour appears on clean images, which suggests the Laplacian branch learns a structural prior rather than just patching artifacts.

{% include figure.liquid loading="lazy" path="assets/img/lca_gradcam.jpg" class="img-fluid rounded z-depth-1" caption="GradCAM on a lighting-variant image: decoder-only fine-tuning (left) diffuses into the background; LCA (middle) concentrates on the target; the difference map (right) shows where LCA refocuses attention." %}

### Ablations (VOC)

- **Architecture:** the parallel-gate design with a depthwise-separable projection (V3, 2.49M params) reaches **0.6905 / 0.6848** mIoU (clean / variant), clearly beating sequential CBAM-style gating (V1) and softmax gate fusion (V2), both around 0.659. The spatially aware residual projection is the key design choice.
- **Resolution:** the clean–variant gap stays about 0.005 from 128×128 to 1024×1024, so the robustness doesn't depend on resolution.
- **Consistency weight:** results vary by less than 0.15% mIoU between λ = 0 and λ = 10. LCA alone already gives substantial invariance; λ = 0.1 is the best balance.

### Limitations

Extreme cases such as complete darkness with point lights are untested. Training needs paired clean/variant images, and synthetic augmentation may not fully cover natural lighting. LCA adds some compute that may matter on edge devices, and video and panoptic segmentation remain future work.

Work done at [SCSLab, Iowa State University](https://sites.google.com/view/scslab-isu/home).
