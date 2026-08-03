---
layout: page
title: Few-Shot Writer Identification with Vision Transformers
description: Prototype-based meta-learning for identifying writers from limited handwriting samples.
category: research
importance: 5
img: assets/img/projects/fewshot-writer-id.png
permalink: /projects/fewshot-writer-id/
---

## Approach

Writer identification usually assumes abundant handwriting data per person. This personal side project targeted the few-shot setting instead: identifying a writer from only a small number of handwriting samples.

- Extracted global handwriting features with a Vision Transformer backbone.
- Built per-writer style prototypes with a Prototypical Network so that new writers can be recognized from limited samples.
- Updated prototypes from user feedback on wrong predictions, incrementally improving accuracy with little data.
- Built the data and training pipeline in PyTorch.

`Vision Transformer` · `meta-learning` · `PyTorch` · `Python`

**Presentation:** 김인곤, 신수용, "소량의 필적 샘플을 활용한 Vision Transformer 기반 메타러닝 작성자 식별 기법," 한국통신학회 학술대회논문집, pp. 582–583, 2025.

**Patent:** Related patent work is described on the [Patents](/patents/) page; identifiers await confirmation.
