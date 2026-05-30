---
layout: page
title: DA-TextSpotter
description: Domain-agnostic scene text spotting in multi-domain noisy scenes
img: assets/img/da_textspotter.jpg
importance: 11
category: work
---

**DA-TextSpotter** tackles **domain-agnostic scene text spotting** — training a single model on multi-domain source data so it generalizes directly to unseen target domains, rather than specializing for one scenario. Published at **ICRA 2024**.

### Problem

State-of-the-art methods pretrain and fine-tune on natural-scene datasets and fail to exploit feature interaction across complex domains (e.g. underwater and document scenes).

### Approach

- An efficient **super-resolution based end-to-end transformer** with a Swin backbone and dual text-localization / recognition decoders
- Introduces the **Under-Water Text (UWT)** validation benchmark for noisy underwater scenes
- Matches or exceeds existing spotters on regular and arbitrary-shaped benchmarks in both accuracy and efficiency

### Publication

Das, A., Biswas, S., Pal, U., Lladós, J. _Diving into the Depths of Spotting Text in Multi-Domain Noisy Scenes._ ICRA 2024. (arXiv:2310.00558)
