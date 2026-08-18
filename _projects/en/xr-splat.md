---
layout: page
title: Gaussian Splatting XR Space Reconstruction & Localization
description: XR space reconstruction and indoor localization implemented and validated via 360° video and RGB-D SLAM.
category: industry
importance: 2
lang: en
img: assets/img/projects/figs/xrsplat-mvs-cloud.jpg
permalink: /en/projects/xr-splat/
---

## Overview

- **Period:** May 2026 – Jul 2026 (K3I)
- Gaussian Splatting-based XR space reconstruction implemented and validated in **two ways** — 360° video and RGB-D SLAM
- One capture produces a photoreal 3D space asset, plus indoor localization

![360° Gaussian Splatting render](/assets/img/projects/figs/xrsplat-360-render.gif)

_Self-captured lobby — 360° Gaussian Splatting free-viewpoint render_

## ① 360° video reconstruction

- Insta360 footage → OpenSfM camera poses → MVS dense point cloud → Gaussian initialization
- **MVS dense initialization** instead of sparse points: held-out PSNR **+2.3 dB**, most floaters removed
- Two self-captured scenes: SfM registration **142/142 · 149/149**, test PSNR **19.70 / 19.99 dB**

![MVS dense point cloud and camera trajectory](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_OpenSfM/MVS dense point cloud and camera trajectory_

## ② RGB-D SLAM × Gaussian Splatting

- **ORB-SLAM3** (pose, loop closure, relocalization) and **gsplat** (rendering) kept separate, sharing frozen SLAM poses
- Both maps derive from the same SLAM poses → **one coordinate frame, no alignment step**
- A single RGB-D recording yields the 3D asset and indoor localization together

![Localization inside the Gaussian map](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_Camera pose and localization inside the Gaussian map_

| Validation                        | Result                                |
| --------------------------------- | ------------------------------------- |
| Pose accuracy (TUM fr1/desk, ATE) | **1.89 cm** (COLMAP baseline 2.04 cm) |
| Own RGB-D asset quality           | **27.96 dB PSNR**                     |
| Global relocalization             | **100%**                              |
| Feature-PnP localization          | **62.8 FPS** (CPU)                    |
| Rendering                         | **123 FPS** (2M Gaussians, 1280×720)  |

![Global localization across the full 28.8 m map](/assets/img/projects/figs/xrsplat-full-map.png)

_Global localization 40/40 across the full 28.8 m map_

`3D Gaussian Splatting` · `gsplat` · `ORB-SLAM3` · `OpenSfM` · `MVS` · `RealSense D455` · `Insta360` · `PyTorch` · `CUDA` · `WebGL`

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
