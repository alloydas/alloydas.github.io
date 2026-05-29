---
layout: page
title: EmbodiedMAE
description: Multi-modal Masked Autoencoder for 3D Plant Phenotyping
img: assets/img/12.jpg
importance: 1
category: work
related_publications: false
---

**EmbodiedMAE** is a multi-modal masked autoencoder designed for 3D reconstruction and phenotyping of Sorghum plants. The model jointly encodes RGB images, depth maps, and point clouds to learn rich 3D-aware representations without requiring complete supervision.

### Motivation

Plant phenotyping — measuring structural traits like plant height, leaf angle, and biomass — is critical for precision agriculture and crop breeding. Traditional methods are manual and slow. EmbodiedMAE aims to automate this via scalable self-supervised learning from readily available sensor data.

### Approach

- **Multi-modal encoder**: separate ViT-based encoders for RGB, depth, and point cloud modalities
- **Cross-modal masked reconstruction**: randomly mask tokens across modalities; reconstruct them using visible tokens from all modalities
- **3D-aware loss**: combines pixel-level, depth-level, and point-wise Chamfer distance losses
- **Target crop**: Sorghum phenotyping using the ISU field robot dataset

### Status

Active development. Part of PhD research at [SCSLab, Iowa State University](https://sites.google.com/view/scslab-isu/home).
