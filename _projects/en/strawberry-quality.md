---
layout: page
title: LLM-Assisted Strawberry Quality Assessment
description: Segmentation, quantitative image analysis, retrieval, and natural-language reporting for smart farms.
category: research
importance: 4
lang: en
img: assets/img/projects/strawberry-quality.png
permalink: /en/projects/strawberry-quality/
---

## Problem

Conventional quality assessment stops at simple image classification or binary decisions, offering no **detailed interpretation** such as harvest criteria or disease-guidance references. Fixed classifiers also adapt poorly when criteria change across cultivars and environments.

## Approach

![System architecture](/assets/img/projects/figs/strawberry-system.png)

_Pipeline — YOLOv11-seg segmentation → OpenCV quantitative analysis → RAG document retrieval → LLM interpretation and report generation._

- Segmented individual strawberries with YOLOv11-seg to isolate analysis targets.
- Quantified **ripeness (color), size, and potential disease indicators** with OpenCV.
- Converted measurements into natural-language prompts and retrieved quality and disease-guidance documents through a RAG pipeline.
- An LLM interprets the retrieved references to generate a natural-language report on **harvest readiness and recommended actions**.

The goal was document-grounded interpretation that adapts by swapping reference documents — instead of retraining a fixed binary classifier.

`YOLOv11-seg` · `OpenCV` · `RAG` · `LLM` · `PyTorch` · `Python`

**Presentation:** In Gon Kim and Soo Young Shin, "An LLM-Based Automated Strawberry Quality Assessment System for Smart Farming Environments," 35th Joint Conference on Communications and Information (JCCI 2025), 2025.

<style>
  .post img {
    display: block;
    max-width: min(100%, 42rem);
    height: auto;
    margin: 0.6rem auto 0.2rem;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.5rem;
  }

  .post p > em:only-child {
    display: block;
    text-align: center;
    font-size: 0.85rem;
    color: var(--global-text-color-light, #828282);
    margin-top: 0.1rem;
  }
</style>
