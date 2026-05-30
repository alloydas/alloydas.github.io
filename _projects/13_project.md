---
layout: page
title: AFM Contact Mode Simulator
description: Browser-based simulator of AFM tip-geometry artifacts via Minkowski-sum morphology
img: assets/img/afm_simulator.jpg
importance: 13
category: work
chart:
  echarts: true
---

**AFM Contact Mode Simulator** is a browser-based educational tool that models how the finite geometry of an Atomic Force Microscope (AFM) tip distorts measured surface topography. The distortion is formulated exactly as a **Minkowski sum** (morphological dilation / erosion) of the sample surface with the negated tip profile.

### What it does

- Interactive **2D cross-section** and **3D Three.js raster-scan** views of tip–surface convolution
- Implements **nine tip geometries** — sharp/blunt cone, sphere, hyperboloid, flat punch, concave sphere, asymmetric cone, double tip, and cone+sphere apex — each with correct kernel math
- Invert / transform toggles for contrastive teaching of dilation vs. erosion
- Built for EE 5490X (Advanced Microscopy) at Iowa State; deployed as static HTML on Vercel

### Computational complexity

| Mode         | Operations per recompute | Typical time |
| ------------ | ------------------------ | ------------ |
| 2D simulator | ~396,270                 | < 5 ms       |
| 3D simulator | ~4,000,000               | ~20 ms       |

```echarts
{
  "tooltip": { "trigger": "axis", "formatter": "{b}: {c} ms" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["2D simulator", "3D simulator"] },
  "yAxis": { "type": "value", "name": "recompute time (ms)" },
  "series": [
    {
      "type": "bar",
      "data": [5, 20],
      "barMaxWidth": 60,
      "itemStyle": { "color": "#5cc88a", "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top", "formatter": "{c} ms" }
    }
  ]
}
```

> Note: despite the working name ("AFM-AI"), this is a deterministic physics / morphology simulator — there is no learned or ML component.
