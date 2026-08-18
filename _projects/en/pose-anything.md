---
layout: page
title: Zero-Shot Object Recognition & 3D Pose Estimation
description: A robot perception pipeline that detects arbitrary objects from text prompts and estimates 3D position, size, and orientation from RGB-D.
category: industry
importance: 1
lang: en
img: assets/img/projects/pose-anything.jpg
permalink: /en/projects/pose-anything/
---

## Overview

- **Period:** Aug 2026 – present (K3I)
- Robot perception pipeline that detects **arbitrary objects from a text prompt alone** in a conveyor environment and estimates 3D position, size, and orientation from RGB-D
- Handles new target objects without per-object training data or CAD models

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_Live demo_

## Key work

- **SAM3 text-prompt segmentation** — objects specified by text ("thermos", "book"), no retraining
- **Hybrid tracking** — SAM3 every 5th frame, optical flow in between → **9–13 FPS**
- **RGB-D 3D pose** — depth to point cloud, Open3D OBB for position/size/orientation; static objects within **±1 cm**, rotation stabilized with zero axis flips
- **Occlusion handling** — Kalman-filter trust check withholds pose during occlusion, same ID on reappearance
- **ROS2 pipeline** — results published as ROS2 topics, RViz visualization, validated against an Isaac Sim conveyor

![ROS2 pipeline](/assets/img/projects/figs/pose-pipeline.png)

_ROS2 node and topic layout_

![Published poses](/assets/img/projects/figs/pose-detections.gif)

_/perception/detections view — pose withheld during occlusion_

![Isaac Sim integration](/assets/img/projects/figs/pose-isaac.jpg)

_Isaac Sim conveyor integration_

`SAM3` · `ROS2 Jazzy` · `Open3D` · `RealSense D455` · `RGB-D` · `Kalman filter` · `RViz` · `Isaac Sim` · `Docker`

**Code:** [github.com/ingon1026/pose-anything](https://github.com/ingon1026/pose-anything) (MIT) · **Docker:** [hub.docker.com/r/ingon1026/pose-anything](https://hub.docker.com/r/ingon1026/pose-anything)

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
