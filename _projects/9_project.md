---
layout: page
title: Doc2Graph-X
description: A multilingual graph-based framework for form understanding
img: assets/img/doc2graphx.jpg
importance: 9
category: work
---

**Doc2Graph-X** is a multilingual extension of Doc2Graph that enables language-agnostic structured document understanding for forms.

### Problem

The original Doc2Graph relied on monolingual text processing, limiting generalization across languages.

### Approach

- Combines **XLM-RoBERTa** (word-level) and **S-BERT** (sentence-level) embeddings for language-agnostic entity detection
- A multimodal GNN fuses textual, visual, and geometric features
- A node classifier performs **Semantic Entity Recognition (SER)** and an edge classifier handles **Relation Extraction (RE)**

### Publication

Mazumder, S., Biswas, S., Das, A., Lladós, J. _Doc2Graph-X: A Multilingual Graph-Based Framework for Form Understanding._ GbR 2025.
