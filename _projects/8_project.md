---
layout: page
title: Doc2GraphFormer
description: Bridging graph learning with transformer attention for document understanding
img: assets/img/doc2graphformer.jpg
importance: 8
category: work
---

**Doc2GraphFormer** is a hybrid graph-transformer framework for document understanding that integrates the structured reasoning of Graph Neural Networks with the global context modeling of transformers.

### Problem

GraphSAGE-based message passing struggles with long-range dependencies and global context, while token-based transformers lack an explicit structured representation of document elements.

### Approach

- Converts documents into graph representations and applies multi-head self-attention for structured parsing
- Jointly optimizes three tasks: **Entity Recognition**, **Subgraph Clustering**, and **Entity Linking**
- Dynamically refines entity relationships, capturing both local and global dependencies

### Publication

Mazumder, S., Biswas, S., Pal, A., Das, A., Pal, U., Lladós, J. _Doc2GraphFormer: Bridging Structured Graph Learning with Transformer Attention for Efficient Document Understanding._ ICDAR 2025.
