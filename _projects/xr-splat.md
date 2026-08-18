---
layout: page
title: Gaussian Splatting 기반 XR 공간 재구성·위치추정
description: 360° 영상과 RGB-D SLAM 두 방식으로 XR 공간 재구성과 실내 위치추정을 구현·검증.
category: industry
importance: 2
lang: ko
img: assets/img/projects/figs/xrsplat-mvs-cloud.jpg
permalink: /projects/xr-splat/
---

## 개요

- **기간:** 2026.05 – 2026.07 · (주)케이쓰리아이
- Gaussian Splatting 기반 XR 공간 재구성을 **360° 영상**과 **RGB-D SLAM** 두 방식으로 구현·검증
- 공간 촬영 한 번으로 실사형 3D 공간 자산과 실내 위치추정을 생성

![360° Gaussian Splatting 렌더](/assets/img/projects/figs/xrsplat-360-render.gif)

_자체 촬영 로비 공간 — 360° Gaussian Splatting 자유 시점 렌더_

## ① 360° 영상 기반 재구성

- Insta360 촬영 영상 → OpenSfM 카메라 Pose 추정 → MVS Dense Point Cloud 생성 → Gaussian 초기화
- Sparse 대신 **MVS Dense 초기화**를 적용해 held-out PSNR **+2.3 dB**, floater 대부분 제거
- 자체 촬영 2개 공간: SfM 등록 **142/142 · 149/149**, Test PSNR **19.70 / 19.99 dB**

![MVS Dense Point Cloud와 카메라 궤적](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_OpenSfM·MVS Dense Point Cloud와 카메라 궤적_

## ② RGB-D SLAM × Gaussian Splatting

- **ORB-SLAM3**(Pose·Loop Closure·Relocalization)와 **gsplat**(렌더)을 분리 구성, SLAM Pose를 고정 입력으로 공유
- 두 맵이 동일 SLAM Pose에서 생성되어 **별도 정합 없이 동일 좌표계** 공유
- RGB-D 녹화 하나에서 3D 공간 자산 + 실내 위치추정을 동시 생성

![Gaussian 맵 내 위치추정](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_Gaussian 맵 내 카메라 Pose·Localization_

| 검증 항목                       | 결과                                  |
| ------------------------------- | ------------------------------------- |
| 위치 정확도 (TUM fr1/desk, ATE) | **1.89 cm** (COLMAP baseline 2.04 cm) |
| 자체 RGB-D 자산 품질            | **27.96 dB PSNR**                     |
| 전역 Relocalization             | **100%**                              |
| Feature-PnP 위치추정            | **62.8 FPS** (CPU)                    |
| 렌더링                          | **123 FPS** (2M Gaussians, 1280×720)  |

![28.8m 전체 맵 전역 위치추정](/assets/img/projects/figs/xrsplat-full-map.png)

_28.8m 전체 맵 전역 위치추정 40/40_

`3D Gaussian Splatting` · `gsplat` · `ORB-SLAM3` · `OpenSfM` · `MVS` · `RealSense D455` · `Insta360` · `PyTorch` · `CUDA` · `WebGL`

**Code:** [github.com/ingon1026/xr-splat](https://github.com/ingon1026/xr-splat) · [github.com/ingon1026/360-gaussian-splatting](https://github.com/ingon1026/360-gaussian-splatting) (포크 기여) · **Demo:** [HF xr-splat-demo](https://huggingface.co/spaces/ingon1/xr-splat-demo) · [HF 360gs-walkthroughs](https://huggingface.co/spaces/ingon1/360gs-walkthroughs)

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
