---
layout: page
title: Gaussian Splatting XR Space Reconstruction & Localization
description: Capture a space once and get a walkable photoreal 3D space — plus indoor localization — via two pipelines.
category: industry
importance: 2
lang: en
img: assets/img/projects/figs/xrsplat-mvs-cloud.jpg
permalink: /en/projects/xr-splat/
---

## Overview

Capture a space once with a camera and get a **photorealistic 3D space you can walk through in a browser**. Two pipelines were built depending on the camera — ① walking with a 360° camera, ② a depth camera + SLAM that also gives indoor localization. (Carried out while at K3I.)

## ① Building a space from a 360° camera

Just **walk the space for about 70 seconds** with an Insta360. OpenSfM works out where each video frame was taken (camera positions), a dense 3D point cloud is built from them, and Gaussian Splatting is trained from those points into a finished 3D space.

The key improvement was **starting from dense points**. Instead of the usual sparse points, millions of dense points from MVS seed the training — image quality improved by **+2.3 dB** and most floating artifacts disappeared.

![MVS dense point cloud and camera trajectory](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_The dense 3D point cloud recovered from the footage, with the walking path — these points seed the 3D space._

![360° Gaussian Splatting render](/assets/img/projects/figs/xrsplat-360-render.gif)

_Free-viewpoint fly-through of the finished lobby space — rendered even from angles never actually walked._

- Both self-captured scenes registered every frame (142/142, 149/149), quality 19.70 / 19.99 dB

## ② Depth camera + SLAM, with localization

From a single RGB-D (depth) recording, **two things are produced at once** — a photoreal 3D space, and the ability to know "where am I right now" inside it. The goal: when an XR device re-enters the space, it instantly gets both its position and the rendered view.

The method is a division of labor. **ORB-SLAM3** works out where the camera traveled (position), and **gsplat** takes those positions as-is to build the photoreal space (graphics). Because both start from the same positions, the two maps **overlap automatically** — no alignment step. Existing methods that solve position and graphics in one model were reproduced first and came out mediocre at both, which motivated the split.

![Localization inside the Gaussian map](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_The camera's path shown inside the finished 3D space — position and graphics share the same coordinates._

| What was verified                       | Result                                                                    |
| --------------------------------------- | ------------------------------------------------------------------------- |
| Position accuracy (public TUM data)     | **1.89 cm** error (more accurate than the standard tool COLMAP's 2.04 cm) |
| Image quality, own capture              | **27.96 dB**                                                              |
| Finding own position from unseen frames | **100% success**                                                          |
| Localization speed                      | **62.8 times per second** (CPU only)                                      |
| Rendering speed                         | **123 FPS** (one consumer GPU)                                            |

![Global localization across the full 28.8 m map](/assets/img/projects/figs/xrsplat-full-map.png)

_Position found from anywhere along the full 28.8 m walk (40/40) — it works along the whole path, not just one spot._

`3D Gaussian Splatting` · `gsplat` · `ORB-SLAM3` · `OpenSfM` · `RealSense D455` · `Insta360` · `PyTorch` · `CUDA` · `WebGL`

**Code:** [github.com/ingon1026/xr-splat](https://github.com/ingon1026/xr-splat) · [github.com/ingon1026/360-gaussian-splatting](https://github.com/ingon1026/360-gaussian-splatting) (fork contribution) · **Demo:** [HF xr-splat-demo](https://huggingface.co/spaces/ingon1/xr-splat-demo) · [HF 360gs-walkthroughs](https://huggingface.co/spaces/ingon1/360gs-walkthroughs)

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
