---
layout: page
title: DA-TextSpotter
description: Domain-agnostic scene text spotting in multi-domain noisy scenes
img: assets/img/da_textspotter.jpg
importance: 11
category: work
chart:
  echarts: true
---

**DA-TextSpotter** tackles **domain-agnostic scene text spotting** — training a single model on multi-domain source data so it generalizes directly to unseen target domains, rather than specializing for one scenario. Published at **ICRA 2024**.

### Problem

State-of-the-art methods pretrain and fine-tune on natural-scene datasets and fail to exploit feature interaction across complex domains (e.g. underwater and document scenes).

### Approach

- An efficient **super-resolution based end-to-end transformer** with a Swin backbone and dual text-localization / recognition decoders
- Introduces the **Under-Water Text (UWT)** validation benchmark for noisy underwater scenes
- Matches or exceeds existing spotters on regular and arbitrary-shaped benchmarks in both accuracy and efficiency

### Results

On the new Under-Water Text (UWT) benchmark, DA-TextSpotter more than doubles end-to-end accuracy over prior spotters:

| Method             | P         | R         | F         | E2E (None) |
| ------------------ | --------- | --------- | --------- | ---------- |
| TESTR              | 92.24     | 33.86     | 49.54     | 29.63      |
| SwinTextSpotter    | 83.21     | 34.49     | 48.77     | 29.08      |
| **DA-TextSpotter** | **95.65** | **48.73** | **64.57** | **64.15**  |

```echarts
{
  "tooltip": { "trigger": "axis", "formatter": "{b}: {c}" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["TESTR", "SwinTextSpotter", "DA-TextSpotter"] },
  "yAxis": { "type": "value", "name": "UWT end-to-end (None) %" },
  "series": [
    {
      "type": "bar",
      "data": [
        { "value": 29.63, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 29.08, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 64.15, "itemStyle": { "color": "#4f8ef7" } }
      ],
      "barMaxWidth": 60,
      "itemStyle": { "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Qualitative Results

{% include figure.liquid loading="eager" path="assets/img/icra_montage.jpg" class="img-fluid rounded z-depth-1" caption="Qualitative text spotting across natural-scene and noisy underwater (UWT) images." %}

### Publication

Das, A., Biswas, S., Pal, U., Lladós, J. _Diving into the Depths of Spotting Text in Multi-Domain Noisy Scenes._ ICRA 2024. (arXiv:2310.00558)

Work done at [CVPRU, Indian Statistical Institute Kolkata](https://cvpru.isical.ac.in/).
