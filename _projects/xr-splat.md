---
layout: page
title: Gaussian Splatting 기반 XR 공간 재구성·위치추정
description: 360° 영상과 RGB-D SLAM 두 접근으로 공간 자산 생성과 실내 위치추정을 구현.
category: industry
importance: 2
lang: ko
img: assets/img/projects/figs/xrsplat-mvs-cloud.jpg
permalink: /projects/xr-splat/
---

## 개요

Gaussian Splatting을 XR 공간 재구성에 적용하면서 **입력과 목적이 다른 두 접근**을 구현·검증했습니다 — ① Insta360 360° 영상 기반 공간 재구성, ② RGB-D SLAM과 Gaussian Splatting을 결합한 공간 재구성·위치추정. (K3I 재직 중 수행)

## ① 360° 영상 기반 재구성 — 360GS

Insta360으로 공간을 약 70초 걸으며 촬영한 영상만으로, 브라우저에서 둘러볼 수 있는 3D Gaussian 공간 자산을 만듭니다. OpenSfM으로 구면 카메라 Pose를 추정하고, **MVS Dense Point Cloud로 Gaussian을 초기화**하도록 기존 360° GS 구현을 확장했습니다(포크 기여).

![MVS Dense Point Cloud와 카메라 궤적](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_OpenSfM·MVS로 복원한 Dense Point Cloud와 촬영 궤적 — 이 밀집 포인트가 Gaussian 초기값이 됩니다._

![360° Gaussian Splatting 렌더](/assets/img/projects/figs/xrsplat-360-render.jpg)

_자체 촬영 로비 공간의 360° Gaussian Splatting 렌더 결과._

- Dense 초기화로 희소 뷰 테스트에서 held-out **PSNR +2.3 dB**, floater 대부분 제거
- 자체 촬영 2개 공간: SfM 등록 **142/142, 149/149**, Test PSNR **19.70 / 19.99 dB**
- 셀피스틱 촬영자 마스킹, novel-view 렌더 통합 등 도구 기여

## ② RGB-D SLAM × Gaussian Splatting — xr-splat

RGB-D 녹화 하나에서 **같은 좌표계를 공유하는 두 산출물** — 실사형 3D Gaussian 자산과 그 공간의 실내 위치추정기 — 를 만듭니다. XR 기기가 공간에 재진입할 때 정렬 단계 없이 "내 위치"와 "공간 렌더"를 동시에 얻는 것이 목표입니다.

핵심 결정은 **SLAM과 Gaussian Splatting의 분리(decoupled)**입니다. 포즈 추정과 맵 최적화를 동시에 수행하는 coupled 방식(SplaTAM·Photo-SLAM 등)을 재현 실험한 결과 품질·정확도·속도가 모두 미달해, 위치추정은 ORB-SLAM3, 실사화는 SLAM 포즈를 고정 입력으로 받는 gsplat(MCMC)으로 역할을 갈랐습니다. 두 맵이 동일한 SLAM 포즈에서 나오므로 별도 정합 없이 좌표계가 구조적으로 공유됩니다.

![Gaussian 맵 내 위치추정](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_Gaussian 맵 안에 표시된 카메라 궤적 — 렌더와 위치추정이 같은 좌표계에서 동작합니다._

| 검증 항목                          | 결과                                                  |
| ---------------------------------- | ----------------------------------------------------- |
| TUM fr1/desk ATE (ORB-SLAM3 포즈)  | **1.89 cm** (COLMAP baseline 2.04 cm)                 |
| 자체 RGB-D 자산 품질               | **27.96 dB PSNR** (MCMC 전략, 동일 예산 대비 +4.1 dB) |
| 전역 Relocalization                | **100%** (초기 추정 없이)                             |
| Feature-PnP 위치추정 속도          | **62.8 FPS**                                          |
| 렌더 속도 (2M Gaussians, 1280×720) | **123 FPS**                                           |

![28.8m 전체 맵 전역 위치추정](/assets/img/projects/figs/xrsplat-full-map.png)

_28.8 m 보행 전체 맵(키프레임 242개)에서 미학습 프레임 40/40 전역 위치추정 성공 — 특정 지점이 아니라 경로 전체에서 동작합니다._

자체 데이터에는 mocap 정답이 없어 절대 정확도는 TUM 공개 데이터에서만 주장합니다. 실험에서 품질 상한이 Gaussian 개수가 아니라 **캡처 커버리지·센서 품질**임을 정량 확인했습니다(동일 코드가 클린 합성 데이터에서 45.35 dB — 격차 +17 dB가 데이터에서만 발생).

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
