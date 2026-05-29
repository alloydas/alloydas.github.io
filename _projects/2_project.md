---
layout: page
title: Lighting-Robust Instance Segmentation
description: SAM extended with a Lighting Convolutional Attention module
img: assets/img/3.jpg
importance: 2
category: work
---

**Lighting-aware Unified Model for Instance Segmentation** extends the Segment Anything Model (SAM) with a novel **Lighting Convolutional Attention (LCA)** module that makes segmentation robust to challenging real-world illumination conditions — harsh shadows, specular highlights, and uneven lighting common in agricultural and industrial settings.

### Problem

SAM achieves strong zero-shot segmentation on standard benchmarks, but degrades significantly under difficult lighting. Agricultural robotics and field deployments face highly variable natural illumination that breaks standard instance segmentation pipelines.

### Solution: LCA Module

The LCA module is inserted into the SAM image encoder. It:

1. Estimates a per-channel lighting map from the input feature map
2. Applies a convolutional attention mechanism to suppress lighting artifacts
3. Produces lighting-normalized features that feed into SAM's prompt encoder and mask decoder

### Publications

- Preprint (2026): *Lighting-aware Unified Model for Instance Segmentation* — Liu, Das et al.

### Status

Preprint available. Experiments run on custom agricultural datasets and standard COCO benchmarks.
