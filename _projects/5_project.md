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

| Property               | Value                                |
| ---------------------- | ------------------------------------ |
| Species in dataset     | 76 (incl. endangered)                |
| Taxonomic levels       | 4 (Order / Family / Genus / Species) |
| Architecture families  | 3 (CNN / ViT / Swin)                 |
| Best architecture      | Swin Transformer                     |
| Hair features analyzed | Cuticle patterns + medulla           |

### Results

Accuracy (%) across taxonomic levels — Swin Transformers lead, with Swin-V2-Base best at the fine-grained Species and Genus levels:

| Method           | Species   | Genus     | Family    | Order     | Inf. (ms) |
| ---------------- | --------- | --------- | --------- | --------- | --------- |
| ViT-Base         | 70.60     | 74.90     | 87.48     | 95.84     | 4.02      |
| EfficientNet-b3  | 69.49     | 73.71     | 86.73     | 95.11     | 12.17     |
| DeiT-Base        | 70.03     | 74.96     | 87.45     | 95.24     | 12.29     |
| BEiT-Base        | 70.07     | 74.92     | 87.72     | **95.98** | 15.70     |
| Swin-Base        | 71.60     | 75.07     | **88.41** | **95.98** | **3.56**  |
| **Swin-V2-Base** | **72.63** | **76.27** | 88.25     | 95.90     | 14.64     |
| ResNet-50        | 66.90     | 72.88     | 86.35     | 94.99     | 15.96     |
| MobileNetV2      | 40.38     | 68.66     | 80.90     | 92.92     | 17.51     |

Accuracy drops steadily from coarse (Order) to fine-grained (Species) labels, and the best Swin model stays consistently ahead of the CNN baseline at every level:

```echarts
{
  "tooltip": { "trigger": "axis" },
  "legend": { "data": ["Swin-V2-Base (best)", "ResNet-50 (CNN baseline)"], "top": "2%" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["Order", "Family", "Genus", "Species"] },
  "yAxis": { "type": "value", "name": "accuracy (%)", "min": 60, "max": 100 },
  "series": [
    {
      "name": "Swin-V2-Base (best)",
      "type": "bar",
      "data": [95.9, 88.25, 76.27, 72.63],
      "itemStyle": { "color": "#4f8ef7", "borderRadius": [4, 4, 0, 0] }
    },
    {
      "name": "ResNet-50 (CNN baseline)",
      "type": "bar",
      "data": [94.99, 86.35, 72.88, 66.9],
      "itemStyle": { "color": "#b9c4d0", "borderRadius": [4, 4, 0, 0] }
    }
  ]
}
```

### Activation Maps

{% include figure.liquid loading="eager" path="assets/img/tricho_actmap.jpg" class="img-fluid rounded z-depth-1" caption="Grad-CAM activation maps from the best model across four orders (Carnivora, Primates, Rodentia, Pholidota): (a) input hair microscopy, (b–d) progressive layer activations highlighting the attended hair-shaft and scale regions." %}

### Publication

Das, A., Banerjee, P., Biswas, S. et al. _Tricho-Vision: The use of computer vision in trichotaxonomy for enhancing wildlife conservation of priority species._ Ecological Informatics, 2025.

Work done at [Habitat Lens Private Limited](https://habitatlens.in/).
