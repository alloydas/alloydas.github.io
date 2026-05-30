---
layout: page
title: NoTeS-Bank
description: Benchmarking Neural Transcription and Search for scientific notes
img: assets/img/notesbank.jpg
importance: 7
category: work
---

**NoTeS-Bank** is an evaluation benchmark for **Neural Transcription and Search** in note-based question answering over complex, handwritten academic notes — mathematical equations, diagrams, and scientific notation that break OCR-based document AI.

### Problem

Existing Document VQA benchmarks focus on printed or structured handwritten text, limiting generalization to real-world note-taking with unstructured, multimodal content.

### Benchmark

- **Evidence-Based VQA** — retrieve localized answers with bounding-box evidence
- **Open-Domain VQA** — classify the domain, then retrieve relevant documents and answers
- Demands vision–language fusion, retrieval, and multimodal reasoning rather than OCR alone
- Evaluated with NDCG@5, MRR, Recall@K, IoU, and ANLS across state-of-the-art VLMs and retrieval frameworks

### Publication

Pal, A., Biswas, S., Das, A. et al. _NoTeS-Bank: Benchmarking Neural Transcription and Search for Scientific Notes Understanding._ 2025. (arXiv:2504.09249)
