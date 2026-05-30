---
layout: page
title: Doc2Graph-X
description: A multilingual graph-based framework for form understanding
img: assets/img/doc2graphx.jpg
importance: 9
category: work
chart:
  echarts: true
---

**Doc2Graph-X** is a multilingual extension of Doc2Graph that enables language-agnostic structured document understanding for forms.

### Problem

The original Doc2Graph relied on monolingual text processing, limiting generalization across languages.

### Approach

- Combines **XLM-RoBERTa** (word-level) and **S-BERT** (sentence-level) embeddings for language-agnostic entity detection
- A multimodal GNN fuses textual, visual, and geometric features
- A node classifier performs **Semantic Entity Recognition (SER)** and an edge classifier handles **Relation Extraction (RE)**

### Results

Multilingual SER F1 (fine-tune on 8 languages) — Doc2Graph-X matches or beats much larger LayoutXLM with **~55× fewer parameters**:

| Model (SER)     | #Params | FUNSD     | IT        | Avg.  |
| --------------- | ------- | --------- | --------- | ----- |
| XLM-RoBERTa     | 125M    | 66.70     | 66.87     | 70.47 |
| InfoXLM         | 362M    | 68.52     | 67.51     | 72.07 |
| LayoutXLM       | 345M    | 79.40     | 80.82     | 80.56 |
| **Doc2Graph-X** | 6.2M    | **80.07** | **81.38** | 77.39 |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["XLM-RoBERTa", "InfoXLM", "LayoutXLM", "Doc2Graph-X"] },
  "yAxis": { "type": "value", "name": "SER F1 on FUNSD", "max": 100 },
  "series": [
    {
      "type": "bar",
      "data": [
        { "value": 66.7, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 68.52, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 79.4, "itemStyle": { "color": "#b9c4d0" } },
        { "value": 80.07, "itemStyle": { "color": "#4f8ef7" } }
      ],
      "barMaxWidth": 55,
      "itemStyle": { "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Multilingual Results

{% include figure.liquid loading="eager" path="assets/img/doc2graphx_results.jpg" class="img-fluid rounded z-depth-1" caption="Multilingual SER comparison (Input / Doc2Graph / Doc2Graph-X / Ground Truth) across Chinese, English, and French forms." %}

### Publication

Mazumder, S., Biswas, S., Das, A., Lladós, J. _Doc2Graph-X: A Multilingual Graph-Based Framework for Form Understanding._ GbR 2025.
