---
layout: page
title: Zero-Shot Object Recognition & 3D Pose Estimation
description: A robot perception pipeline that detects arbitrary objects from text prompts and estimates 3D pose from RGB-D.
category: industry
importance: 1
lang: en
img: assets/img/projects/pose-anything.jpg
permalink: /en/projects/pose-anything/
---

## Problem

For a robot to pick objects off a conveyor it needs 3D pose (position, size, orientation) — but conventional approaches require per-object data collection, labeling, and retraining (days of work) or a CAD model. This project detects and tracks **arbitrary objects by simply changing a text prompt** ("thermos", "book"), derives 3D pose and confidence from RGB-D geometry, and publishes everything over ROS2 — no training, no CAD. (Carried out while at K3I.)

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_Live demo — objects specified by text prompt are detected and tracked while 3D OBBs and poses are published._

## System

**SAM3 zero-shot recognition** — Meta SAM 3 (open-vocabulary detection + segmentation) segments objects from text prompts. No retraining pipeline was built at all for new objects. bf16 inference gives 3.7× speedup over fp32; text embeddings are cached per prompt.

**Hybrid tracking** — continuous SAM3 inference caps at ~3 FPS, so it runs only every 5th frame and Lucas-Kanade optical flow (median displacement of ~300 in-mask points) carries the mask in between. 3D pose is recomputed every frame from that frame's actual depth — resulting in **9–13 FPS**. Object identity survives temporary occlusion.

**Geometry-based 3D pose** — mask + aligned depth are back-projected into a point cloud, and an Open3D PCA oriented bounding box gives position, size, and orientation (static object sizes within ±1 cm of ground truth). PCA axis permutation/sign ambiguity is stabilized in three stages — axis matching → 2° deadband → slerp — yielding **0.94°/frame with zero axis flips**.

**Probabilistic fusion filter** — instead of stacking threshold gates, per-axis Kalman filters with separate χ² gates (position/size) judge observation trust. When rejections persist, prediction uncertainty grows and the gate reopens by itself — **deadlock is impossible by construction** — and per-object observation noise (measured to vary 40×) adapts per track.

![ROS2 pipeline](/assets/img/projects/figs/pose-pipeline.png)

_ROS2 node/topic layout — camera input and prompts flow into perception, which publishes /perception/detections, markers, and debug_image for RViz and robot consumer nodes._

![Published poses](/assets/img/projects/figs/pose-detections.gif)

_What the robot actually receives — during occlusion, pose publication is withheld and resumes under the same ID on reappearance. Coordinates that cannot be trusted are never sent to the robot._

![Isaac Sim integration](/assets/img/projects/figs/pose-isaac.jpg)

_Isaac Sim conveyor digital twin — the environment built by the XR technology convergence team is connected over the ROS2 Bridge so the same pipeline is validated against a virtual camera._

`ROS2 Jazzy` · `SAM3` · `Open3D` · `RealSense D455` · `RGB-D` · `Kalman fusion` · `RViz` · `Isaac Sim` · `Docker`

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
