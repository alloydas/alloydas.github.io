---
layout: page
title: Doc2GraphFormer
description: Bridging graph learning with transformer attention for document understanding
img: assets/img/doc2graphformer.jpg
importance: 8
category: work
chart:
  echarts: true
---

**Doc2GraphFormer** is a hybrid graph-transformer framework for document understanding that integrates the structured reasoning of Graph Neural Networks with the global context modeling of transformers.

### Problem

GraphSAGE-based message passing struggles with long-range dependencies and global context, while token-based transformers lack an explicit structured representation of document elements.

### Approach

- Converts documents into graph representations and applies multi-head self-attention for structured parsing
- Jointly optimizes three tasks: **Entity Recognition**, **Subgraph Clustering**, and **Entity Linking**
- Dynamically refines entity relationships, capturing both local and global dependencies

### Results

Semantic Entity Recognition (SER) and Relation Extraction (RE) F1 on FUNSD — Doc2GraphFormer leads while using a fraction of the parameters:

| Method                 | SER F1    | RE F1     | #Params (M) |
| ---------------------- | --------- | --------- | ----------- |
| BROS                   | 0.812     | 0.670     | 138         |
| LayoutLM               | 0.790     | 0.428     | 343         |
| Doc2Graph              | 0.823     | 0.534     | 6.2         |
| **Doc2GraphFormer+GL** | **0.862** | **0.555** | **3.62**    |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["BROS", "LayoutLM", "Doc2Graph", "Doc2GraphFormer+GL"] },
  "yAxis": { "type": "value", "name": "SER F1", "max": 1 },
  "series": [
    {
      "type": "bar",
      "data": [
        { "value": 0.812, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 0.79, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 0.823, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 0.862, "itemStyle": { "color": "#4f8ef7" } }
      ],
      "barMaxWidth": 55,
      "itemStyle": { "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Qualitative Results

{% include figure.liquid loading="eager" path="assets/img/doc2graphformer_results.jpg" class="img-fluid rounded z-depth-1" caption="Semantic Entity Recognition — predicted entity boxes on form documents (green = correct, red = incorrect)." %}

### Publication

Mazumder, S., Biswas, S., Pal, A., Das, A., Pal, U., Lladós, J. _Doc2GraphFormer: Bridging Structured Graph Learning with Transformer Attention for Efficient Document Understanding._ ICDAR 2025.

Work done at [Habitat Lens Private Limited](https://habitatlens.in/).
