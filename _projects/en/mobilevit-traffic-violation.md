---
layout: page
title: MobileViT Motorcycle Traffic-Violation Detection
description: Temporal traffic-event recognition on an embedded ROS2 platform.
category: featured
importance: 2
lang: en
img: assets/img/projects/mobilevit-traffic-violation.jpg
permalink: /en/projects/mobilevit-traffic-violation/
---

[한국어](/projects/mobilevit-traffic-violation/)

## Problem

Single-frame detectors can miss traffic violations that depend on temporal context, such as signal changes or occupancy of a crosswalk. Momentary detection failures also produce avoidable false positives.

## Contribution

- Used YOLO to detect traffic lights, lane boundaries, crosswalks, and vehicles.
- Constructed temporal ROI sequences and analyzed state changes and motion patterns with MobileViT.
- Integrated the inference pipeline with ROS2 and deployed it on a Jetson Orin NX for real-time operation.

This work was part of a motorcycle dashcam-based safe-driving evaluation system under the Gumi Innopolis development program.

`MobileViT` · `YOLO` · `ROS2` · `Jetson Orin NX` · `PyTorch` · `Python`

**Publication:** Kim, In Gon and Shin, Soo Young, "A MobileViT-Based Detection System for Motorcycle Traffic Violations," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 50, no. 12, pp. 1822–1829, 2025.
