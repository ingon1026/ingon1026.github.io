---
layout: page
title: LLM-Assisted Strawberry Quality Assessment
description: Segmentation, quantitative image analysis, retrieval, and natural-language reporting for smart farms.
category: research
importance: 4
permalink: /projects/strawberry-quality/
---

## Approach

- Segmented individual strawberries with YOLOv11-seg.
- Used OpenCV to quantify ripeness, size, and potential disease indicators.
- Connected measurements to quality and disease-guidance documents through a retrieval-augmented generation pipeline.
- Generated a natural-language assessment of harvest readiness and recommended actions with an LLM.

The goal was to move beyond a fixed binary classifier and provide document-grounded interpretations that can adapt to different quality criteria.

`YOLOv11-seg` · `OpenCV` · `RAG` · `LLM` · `PyTorch` · `Python`

**Presentation:** 35th Joint Conference on Communications and Information. Author order, year, pages, and public paper link remain **TODO** until confirmed.
