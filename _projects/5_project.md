---
layout: page
title: Tricho-Vision
description: Computer vision for trichotaxonomy and wildlife conservation
img: assets/img/tricho.jpg
importance: 5
category: work
chart:
  echarts: true
---

**Tricho-Vision** applies computer vision to trichotaxonomy — the classification of mammalian hair microstructures — to enhance wildlife conservation of priority species. Published in **Ecological Informatics (2025)**.

### Motivation

Manual identification of species via hair (cuticle and medulla) analysis is time-consuming and requires expert knowledge. Automated vision pipelines can scale species identification from microscopy images, aiding biodiversity monitoring and wildlife-crime forensics.

### Contributions

- Curated the first benchmark dataset of **76 conservation-priority species**, including critically endangered taxa
- Classifies hair across four taxonomic levels — **Order, Family, Genus, Species**
- Benchmarks CNNs, ViTs, and Swin Transformers; Swin Transformers perform best across all levels
- Image cropping further improves accuracy by diversifying the training set

### Dataset

Per-model accuracy is reported in the journal article; the public benchmark is summarized below:

| Property               | Value                                |
| ---------------------- | ------------------------------------ |
| Species in dataset     | 76 (incl. endangered)                |
| Taxonomic levels       | 4 (Order / Family / Genus / Species) |
| Architecture families  | 3 (CNN / ViT / Swin)                 |
| Best architecture      | Swin Transformer                     |
| Hair features analyzed | Cuticle patterns + medulla           |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["Species", "Taxonomic levels", "Architecture families"] },
  "yAxis": { "type": "log", "name": "count (log scale)" },
  "series": [
    {
      "type": "bar",
      "data": [76, 4, 3],
      "barMaxWidth": 60,
      "itemStyle": { "color": "#5cc88a", "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Publication

Das, A., Banerjee, P., Biswas, S. et al. _Tricho-Vision: The use of computer vision in trichotaxonomy for enhancing wildlife conservation of priority species._ Ecological Informatics, 2025.

Work done at [Habitat Lens Private Limited](https://habitatlens.in/).
