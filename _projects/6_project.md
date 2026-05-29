---
layout: page
title: Soft-set MSER Text System
description: Occluded scene text detection, recognition, and prediction
img: assets/img/softset_mser.jpg
importance: 6
category: work
---

**Soft set-based MSER end-to-end system** tackles occluded scene text by combining Maximally Stable Extremal Regions (MSER) with soft set theory for robust text detection, recognition, and missing character prediction. Published in **Knowledge-Based Systems (2024)**.

### Problem

Scene text in the wild is often partially occluded by objects, shadows, or degradation. Standard detection pipelines miss or mis-recognize such text. Predicting the missing characters requires higher-order reasoning beyond standard sequence models.

### Approach

- MSER-based candidate region generation with soft-set-theoretic filtering to reduce false positives
- Recognition module handling partial character sequences
- Soft-set-based prediction head for recovering occluded characters based on contextual soft membership
- Validated on IIIT5K, SVT, and a custom occluded text benchmark

### Publication

Das, A., Shivakumara, P., Banerjee, A., Antonacopoulos, A., Pal, U. _Soft set-based MSER end-to-end system for occluded scene text detection, recognition and prediction._ Knowledge-Based Systems, 2024.
