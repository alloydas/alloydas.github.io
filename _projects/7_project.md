---
layout: page
title: NoTeS-Bank
description: Benchmarking Neural Transcription and Search for scientific notes
img: assets/img/notesbank.jpg
importance: 8
category: work
chart:
  echarts: true
---

**NoTeS-Bank** is an evaluation benchmark for **Neural Transcription and Search** in note-based question answering over complex, handwritten academic notes — mathematical equations, diagrams, and scientific notation that break OCR-based document AI.

### Problem

Existing Document VQA benchmarks focus on printed or structured handwritten text, limiting generalization to real-world note-taking with unstructured, multimodal content.

### Benchmark

- **Evidence-Based VQA** — retrieve localized answers with bounding-box evidence
- **Open-Domain VQA** — classify the domain, then retrieve relevant documents and answers
- Demands vision–language fusion, retrieval, and multimodal reasoning rather than OCR alone
- Evaluated with ANLS\*, IoU, NDCG@5, MRR, and Recall@K across state-of-the-art VLMs

### Results

Evidence-Based VQA — even the strongest VLMs trail far behind the human baseline, exposing a large reasoning gap (ANLS\* = answer accuracy):

| Model              | ANLS\*    | Local Acc | Global Acc |
| ------------------ | --------- | --------- | ---------- |
| Qwen-2.5-VL (open) | 28.21     | 11.83     | 4.86       |
| Gemini 2.5 Pro     | 24.49     | 0.20      | —          |
| GPT-4.5            | 21.65     | 13.40     | 7.19       |
| GPT-4o             | 17.88     | 12.00     | 9.00       |
| **Human baseline** | **61.11** | **83.0**  | **79.0**   |

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "3%", "right": "4%", "bottom": "3%", "containLabel": true },
  "xAxis": { "type": "category", "data": ["Qwen2.5-VL", "Gemini2.5Pro", "GPT-4.5", "GPT-4o", "Human"] },
  "yAxis": { "type": "value", "name": "ANLS* (answer accuracy)" },
  "series": [
    {
      "type": "bar",
      "data": [
        { "value": 28.21, "itemStyle": { "color": "#4f8ef7" } },
        { "value": 24.49, "itemStyle": { "color": "#4f8ef7" } },
        { "value": 21.65, "itemStyle": { "color": "#4f8ef7" } },
        { "value": 17.88, "itemStyle": { "color": "#4f8ef7" } },
        { "value": 61.11, "itemStyle": { "color": "#5cc88a" } }
      ],
      "barMaxWidth": 50,
      "itemStyle": { "borderRadius": [4, 4, 0, 0] },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

### Qualitative Comparison

{% include figure.liquid loading="eager" path="assets/img/notesbank_results.jpg" class="img-fluid rounded z-depth-1" caption="Qualitative comparison of Vision-Language Models, OCR+LLMs, and human responses on a handwritten scientific note." %}

### Publication

Pal, A., Biswas, S., Das, A. et al. _NoTeS-Bank: Benchmarking Neural Transcription and Search for Scientific Notes Understanding._ 2025. (arXiv:2504.09249)

Work done at [Habitat Lens Private Limited](https://habitatlens.in/).
