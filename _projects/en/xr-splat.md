---
layout: page
title: Gaussian Splatting XR Space Reconstruction & Localization
description: Two approaches — 360° video and RGB-D SLAM — to photorealistic space assets and indoor localization.
category: industry
importance: 2
lang: en
img: assets/img/projects/xr-splat.jpg
permalink: /en/projects/xr-splat/
---

## Overview

Applied Gaussian Splatting to XR space reconstruction through **two approaches with different inputs and goals** — ① 360° video-based reconstruction from an Insta360 camera, and ② RGB-D SLAM combined with Gaussian Splatting for reconstruction plus localization. (Carried out while at K3I.)

## ① 360° video reconstruction — 360GS

A ~70-second walk with an Insta360 becomes a browser-walkable 3D Gaussian asset. OpenSfM estimates spherical camera poses, and the existing 360° GS implementation was extended to **initialize Gaussians from the MVS dense point cloud** (fork contribution).

![MVS dense point cloud and camera trajectory](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_Dense point cloud and capture trajectory recovered with OpenSfM/MVS — these dense points seed the Gaussians._

![360° Gaussian Splatting render](/assets/img/projects/figs/xrsplat-360-render.jpg)

_360° Gaussian Splatting render of a self-captured lobby space._

- Dense initialization: held-out **PSNR +2.3 dB** in sparse-view tests, most floaters removed
- Two self-captured scenes: SfM registration **142/142 and 149/149**, test PSNR **19.70 / 19.99 dB**
- Tooling contributions: photographer masking for selfie-stick captures, unified novel-view rendering

## ② RGB-D SLAM × Gaussian Splatting — xr-splat

From a single RGB-D recording, produce **two artifacts sharing one coordinate frame** — a photorealistic 3D Gaussian asset and an indoor localizer for that space. An XR device re-entering the space gets "where am I" and "what does it look like" at once, with no alignment step.

The key decision is **decoupling SLAM from Gaussian Splatting**. Reproducing coupled Gaussian-SLAM systems (SplaTAM, Photo-SLAM, etc.) traded away rendering quality, tracking accuracy, and speed all at once — so localization goes to ORB-SLAM3, and photorealism goes to gsplat (MCMC) trained on **frozen SLAM poses**. Both maps derive from the same poses, so the coordinate frame is shared by construction.

![Localization inside the Gaussian map](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_Camera trajectory shown inside the Gaussian map — rendering and localization operate in the same coordinate frame._

| Validation                            | Result                                                                 |
| ------------------------------------- | ---------------------------------------------------------------------- |
| TUM fr1/desk ATE (ORB-SLAM3 poses)    | **1.89 cm** (COLMAP baseline 2.04 cm)                                  |
| Own RGB-D asset quality               | **27.96 dB PSNR** (MCMC strategy, +4.1 dB over default at same budget) |
| Global relocalization                 | **100%** (no pose hint)                                                |
| Feature-PnP localization speed        | **62.8 FPS** (CPU only)                                                |
| Render speed (2M Gaussians, 1280×720) | **123 FPS**                                                            |

![Global localization across the full 28.8 m map](/assets/img/projects/figs/xrsplat-full-map.png)

_40/40 global localizations across the full 28.8 m walk (242 keyframes) — it works along the whole path, not just at one spot._

Absolute accuracy is only claimed on public TUM data (own captures have no mocap ground truth). Experiments also quantified that the quality ceiling is **capture coverage and sensor quality**, not Gaussian count — the same code reaches 45.35 dB on clean synthetic data, a +17 dB gap from data alone.

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
