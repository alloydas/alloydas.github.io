---
layout: page
title: FastTextSpotter
description: High-Efficiency Transformer for Multilingual Scene Text Spotting
img: assets/img/fasttextspotter.jpg
importance: 3
category: work
chart:
  echarts: true
---

**FastTextSpotter** is an end-to-end transformer-based scene text spotting model designed for high efficiency and multilingual robustness. Published at **ICPR 2024**.

### Key Contributions

- Swin Transformer backbone with a novel faster self-attention unit (SAC2)
- Unified detection + recognition head trained end-to-end
- Pre-training leveraging multilingual synthetic datasets for cross-lingual transfer
- Strong speed-accuracy trade-off on Total-Text, CTW1500, ICDAR-15, and VinText benchmarks

### Results

Detection F-measure and end-to-end H-mean (full lexicon) versus state-of-the-art spotters:

| Method              | TT Det-F  | TT E2E-Full | CTW Det-F | CTW E2E-Full |
| ------------------- | --------- | ----------- | --------- | ------------ |
| ABCNet v2           | 87.0      | 78.1        | 84.7      | 77.2         |
| SwinTextSpotter     | 88.0      | 84.1        | 88.0      | 77.0         |
| TESTR               | 86.9      | 83.3        | 86.3      | 79.9         |
| **FastTextSpotter** | **87.95** | **86.0**    | **88.19** | **82.91**    |

```echarts
{
  "tooltip": { "trigger": "axis", "formatter": "{b}: {c}" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": {
    "type": "category",
    "data": ["TT Det", "TT E2E", "CTW Det", "CTW E2E", "IC15 Det", "VinText"],
    "axisLabel": { "interval": 0 }
  },
  "yAxis": { "type": "value", "name": "H-mean (%)", "max": 100 },
  "series": [
    {
      "name": "FastTextSpotter",
      "type": "bar",
      "data": [87.95, 86.0, 88.19, 82.91, 90.13, 72.95],
      "itemStyle": { "color": "#4f8ef7", "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Publication

Das, A., Biswas, S., Pal, U., Lladós, J., Bhattacharya, S. _FastTextSpotter: A High-Efficiency Transformer for Multilingual Scene Text Spotting._ ICPR 2024. (arXiv:2408.14998)

Work done at [CVPRU, Indian Statistical Institute Kolkata](https://cvpru.isical.ac.in/).
