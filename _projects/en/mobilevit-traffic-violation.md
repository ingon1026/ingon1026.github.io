---
layout: page
title: MobileViT Motorcycle Traffic-Violation Detection
description: Real-time temporal traffic-violation recognition on an embedded ROS2 platform.
category: featured
importance: 2
lang: en
img: assets/img/projects/mobilevit-traffic-violation.jpg
permalink: /en/projects/mobilevit-traffic-violation/
---

[한국어](/projects/mobilevit-traffic-violation/)

## Problem

Single-frame detectors miss violations that depend on **temporal context** — signal changes, sustained crosswalk occupancy — and momentary detection failures turn into false positives. This system defines and detects three violation types under the Road Traffic Act: **signal violation, centerline crossing, and crosswalk violation**, in real time.

## System

![System overview](/assets/img/projects/figs/mobilevit-system.png)

_System overview — motorcycle dashcam footage flows through YOLO detection and MobileViT temporal analysis on the Jetson board, ending in violation scoring and logging._

- YOLO detects road elements (vehicles, traffic lights, stop lines, crosswalks) and motorcycles.
- ROI sequences of detected objects feed a MobileViT time-series analysis of position and state changes across frames — e.g., whether the stop line is crossed on red, or a crosswalk stays occupied over time.
- When the violation probability exceeds a confidence threshold, the event is logged immediately in JSON and CSV for downstream use.
- Runs in real time on a Jetson Orin NX (RealSense D435i, Ubuntu 22.04 + JetPack 6) with ROS2 Humble.

## Validation

![Detection example on real footage](/assets/img/projects/figs/mobilevit-detection.jpg)

_Detection on real driving footage — traffic lights and crosswalks are detected while per-type violation counts are logged in real time._

Evaluated on **75 minutes of real dashcam footage** (30 min urban + 45 min rural, day and night), achieving **over 90% accuracy** across conditions. MobileViT's temporal analysis compensated for missed detections and filtered transient events to reduce false positives.

This work was part of a motorcycle dashcam-based safe-driving evaluation system under the Gumi Innopolis development program.

`MobileViT` · `YOLO` · `ROS2 Humble` · `Jetson Orin NX` · `RealSense D435i` · `PyTorch`

**Publication:** Kim, In Gon and Shin, Soo Young, "A MobileViT-Based Detection System for Motorcycle Traffic Violations," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 50, no. 12, pp. 1822–1829, 2025.
