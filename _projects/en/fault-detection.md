---
layout: page
title: Deep-Learning Camera Fault Detection
description: Detecting and removing camera noise and environmental artifacts during drone operation.
category: research
importance: 6
lang: en
img: assets/img/projects/fault-detection.png
permalink: /en/projects/fault-detection/
---

[한국어](/projects/fault-detection/)

## Problem

Cameras on a flying drone are exposed to noise and environmental artifacts that degrade downstream perception. This project detected such faults during operation and cleaned the affected frames.

## Contribution

- Detected camera noise with OpenCV-based analysis.
- Fed flagged frames to a deep-learning model that removes the noise.
- Started from open-source detection models, then moved to a zero-shot detection approach to fit memory constraints.

`ROS2` · `OpenCV` · `PyTorch` · `Python`
