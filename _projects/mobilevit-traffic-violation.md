---
layout: page
title: MobileViT Motorcycle Traffic-Violation Detection
description: Temporal traffic-event recognition on an embedded ROS2 platform.
category: featured
importance: 2
permalink: /projects/mobilevit-traffic-violation/
---

## Problem

Single-frame detectors can miss traffic violations that depend on temporal context, such as signal changes or occupancy of a crosswalk. Momentary detection failures also produce avoidable false positives.

## Contribution

- Used YOLO to detect traffic lights, lane boundaries, crosswalks, and vehicles.
- Constructed temporal ROI sequences and analyzed state changes and motion patterns with MobileViT.
- Integrated the inference pipeline with ROS2 and deployed it on a Jetson Orin NX for real-time operation.

This work was part of a motorcycle dashcam-based safe-driving evaluation system under the Gumi Innopolis development program.

`MobileViT` · `YOLO` · `ROS2` · `Jetson Orin NX` · `PyTorch` · `Python`

**Publication:** Notion records this work as published in a December issue of JKICS. Complete volume, issue, pages, DOI, author order, and publication year remain **TODO** until confirmed.
