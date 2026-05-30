---
layout: page
title: Soft-set MSER Text System
description: Occluded scene text detection, recognition, and prediction
img: assets/img/softset_mser.jpg
importance: 6
category: work
chart:
  echarts: true
---

**Soft set-based MSER end-to-end system** tackles occluded scene text by combining Maximally Stable Extremal Regions (MSER) with soft set theory for robust text detection, recognition, and missing character prediction. Published in **Knowledge-Based Systems (2024)**.

### Problem

Scene text in the wild is often partially occluded by objects, shadows, or degradation. Standard detection pipelines miss or mis-recognize such text. Predicting the missing characters requires higher-order reasoning beyond standard sequence models.

### Approach

- MSER-based candidate region generation with soft-set-theoretic filtering to reduce false positives
- A Graph Recurrent Neural Network groups candidate components into text lines
- A CRNN recognizes text and predicts missing characters under occlusion
- Validated on IIIT5K, SVT, and the newly released **Occluded Scene Text Dataset (OSTD)**

### Dataset (OSTD)

Detection/recognition F-measures are reported in the journal article; the released OSTD benchmark is summarized below:

| Split                     | Images |
| ------------------------- | ------ |
| Train                     | 220    |
| Validation                | 60     |
| Test                      | 29     |
| **Total**                 | 309    |
| Vocabulary (word classes) | 1494   |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["Train", "Validation", "Test"] },
  "yAxis": { "type": "value", "name": "OSTD images" },
  "series": [
    {
      "type": "bar",
      "data": [220, 60, 29],
      "barMaxWidth": 60,
      "itemStyle": { "color": "#4f8ef7", "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Qualitative Detection

{% include figure.liquid loading="eager" path="assets/img/softset_mser_results.jpg" class="img-fluid rounded z-depth-1" caption="Occluded scene-text detection results on the OSTD benchmark." %}

### Publication

Das, A., Shivakumara, P., Banerjee, A., Antonacopoulos, A., Pal, U. _Soft set-based MSER end-to-end system for occluded scene text detection, recognition and prediction._ Knowledge-Based Systems, 2024. ([code + OSTD](https://github.com/alloydas/Softset-MSER-Based-Occluded-Scene-Text-Spotting))
