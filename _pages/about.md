---
layout: about
title: About
permalink: /
subtitle: >
  PhD Student · <a href="https://www.iastate.edu/">Iowa State University</a> ·
  Advised by <a href="https://www.me.iastate.edu/faculty/soumik-sarkar/">Prof. Soumik Sarkar</a>

profile:
  align: right
  image: prof_pic.jpg
  image_circular: false
  more_info: >
    <p>Ames, Iowa, USA</p>
    <p><a href="mailto:alloyuit@gmail.com">alloyuit@gmail.com</a></p>

news: true
selected_papers: true
social: true
chart:
  echarts: true
---

I am a PhD student in the [Department of Mechanical Engineering](https://www.me.iastate.edu/) at **Iowa State University**, working in the [SCSLab](https://sites.google.com/view/scslab-isu/home) under the supervision of [Prof. Soumik Sarkar](https://www.me.iastate.edu/faculty/soumik-sarkar/).

My research lies at the intersection of **computer vision**, **multi-modal representation learning**, and **agricultural AI**. I am currently working on:

- **EmbodiedMAE** — a multi-modal masked autoencoder for 3D plant reconstruction from RGB images, depth maps, and point clouds, targeting Sorghum phenotyping.
- **Lighting-robust instance segmentation** — extending SAM with a custom Lighting Convolutional Attention (LCA) module for robust segmentation under challenging illumination conditions.

Previously, I was a Research Assistant at the [Computer Vision and Pattern Recognition Unit (CVPRU)](https://cvpru.isical.ac.in/), [Indian Statistical Institute, Kolkata](https://www.isical.ac.in/), supervised by [Prof. Umapada Pal](https://www.isical.ac.in/~umapada/). My work there focused on **scene text spotting**, **recognition**, and **editing** — resulting in publications at WACV 2024, WACV 2025, ICRA 2024, and ICPR 2024.

I am a peer reviewer for [*The Visual Computer*](https://www.springer.com/journal/371) journal.

My scholarly record spans **24 works indexed on [ORCID](https://orcid.org/0000-0002-4502-4984)** (2022–2026) — including 11 conference papers and 6 journal articles — and is also catalogued on [Scopus](https://www.scopus.com/authid/detail.uri?authorId=57560089800). My research has appeared at venues such as **WACV**, **ICRA**, **ICPR**, and **ICDAR**, and in journals including *Knowledge-Based Systems*, *Multimedia Tools and Applications*, and *Ecological Informatics*.

---

## Research at a Glance

<div class="row mt-3">
  <div class="col-sm-6" markdown="1">

**Publication Timeline**

```echarts
{
  "tooltip": { "trigger": "axis" },
  "grid": { "left": "5%", "right": "5%", "bottom": "10%", "containLabel": true },
  "xAxis": {
    "type": "category",
    "data": ["2021", "2022", "2024", "2025", "2026"],
    "axisLabel": { "color": "#666" }
  },
  "yAxis": {
    "type": "value",
    "name": "Papers",
    "minInterval": 1,
    "axisLabel": { "color": "#666" }
  },
  "series": [
    {
      "name": "Publications",
      "type": "bar",
      "barMaxWidth": 40,
      "data": [1, 2, 5, 7, 1],
      "itemStyle": {
        "color": {
          "type": "linear",
          "x": 0, "y": 0, "x2": 0, "y2": 1,
          "colorStops": [
            { "offset": 0, "color": "#4f8ef7" },
            { "offset": 1, "color": "#7fcfe8" }
          ]
        },
        "borderRadius": [4, 4, 0, 0]
      },
      "label": { "show": true, "position": "top" }
    }
  ]
}
```

  </div>
  <div class="col-sm-6" markdown="1">

**Research Skills**

```echarts
{
  "tooltip": {},
  "radar": {
    "indicator": [
      { "name": "Computer Vision", "max": 10 },
      { "name": "Deep Learning", "max": 10 },
      { "name": "Multi-modal Learning", "max": 10 },
      { "name": "Scene Text Spotting", "max": 10 },
      { "name": "Agricultural AI", "max": 10 },
      { "name": "3D Reconstruction", "max": 10 }
    ],
    "radius": "65%"
  },
  "series": [
    {
      "type": "radar",
      "data": [
        {
          "value": [9, 9, 8, 9, 7, 6],
          "name": "Expertise",
          "areaStyle": { "opacity": 0.3 },
          "lineStyle": { "color": "#4f8ef7", "width": 2 },
          "itemStyle": { "color": "#4f8ef7" }
        }
      ]
    }
  ]
}
```

  </div>
</div>

<div class="row mt-2">
  <div class="col-sm-12" markdown="1">

**Publication Venues**

```echarts
{
  "tooltip": { "trigger": "item", "formatter": "{b}: {c} papers ({d}%)" },
  "legend": {
    "orient": "vertical",
    "right": "5%",
    "top": "center"
  },
  "series": [
    {
      "type": "pie",
      "radius": ["35%", "60%"],
      "center": ["38%", "50%"],
      "avoidLabelOverlap": true,
      "itemStyle": { "borderRadius": 6, "borderColor": "#fff", "borderWidth": 2 },
      "label": { "show": false },
      "emphasis": {
        "label": { "show": true, "fontSize": 13, "fontWeight": "bold" }
      },
      "data": [
        { "value": 4, "name": "WACV / ICRA / ICPR", "itemStyle": { "color": "#4f8ef7" } },
        { "value": 3, "name": "Journals (KBS / MTA / Eco. Inf.)", "itemStyle": { "color": "#7fcfe8" } },
        { "value": 4, "name": "ICDAR / LNCS", "itemStyle": { "color": "#5cc88a" } },
        { "value": 3, "name": "Preprints / Workshops", "itemStyle": { "color": "#f7a64f" } },
        { "value": 2, "name": "AIP / IJPRAI", "itemStyle": { "color": "#e87c7c" } }
      ]
    }
  ]
}
```

  </div>
</div>
