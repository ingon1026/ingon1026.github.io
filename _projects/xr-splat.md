---
layout: page
title: Gaussian Splatting 기반 XR 공간 재구성·위치추정
description: 공간을 한 번 촬영하면 둘러볼 수 있는 3D 공간과 실내 위치추정을 함께 만드는 두 가지 파이프라인.
category: industry
importance: 2
lang: ko
img: assets/img/projects/figs/xrsplat-mvs-cloud.jpg
permalink: /projects/xr-splat/
---

## 개요

공간을 카메라로 한 번 촬영하면, **브라우저에서 둘러볼 수 있는 실사 3D 공간**을 만드는 프로젝트입니다. 촬영 장비에 따라 두 가지 방법을 만들었습니다 — ① 360° 카메라로 걸으며 찍는 방법, ② 깊이 카메라 + SLAM으로 위치추정까지 같이 얻는 방법. (K3I 재직 중 수행)

## ① 360° 카메라로 공간 만들기

Insta360을 들고 공간을 **약 70초 걷기만 하면** 됩니다. OpenSfM이 영상의 각 장면이 어디서 찍혔는지(카메라 위치) 계산하고, 그 위치들로 촘촘한 3D 점 구름을 만든 뒤, 이 점들을 시작점으로 Gaussian Splatting을 학습시켜 3D 공간을 완성합니다.

핵심 개선은 **시작점을 촘촘하게** 만든 것입니다. 원래는 듬성듬성한 점에서 시작하는데, MVS라는 방식으로 수백만 개의 촘촘한 점을 만들어 시작하게 바꿨더니 화질이 **+2.3 dB** 좋아지고 허공에 뜨는 잡티(floater)가 대부분 사라졌습니다.

![MVS Dense Point Cloud와 카메라 궤적](/assets/img/projects/figs/xrsplat-mvs-cloud.jpg)

_촬영 영상에서 복원한 촘촘한 3D 점 구름과 걸어간 경로 — 이 점들이 3D 공간의 시작점이 됩니다._

![360° Gaussian Splatting 렌더](/assets/img/projects/figs/xrsplat-360-render.gif)

_완성된 로비 공간을 자유 시점으로 둘러보는 모습 — 실제로 걸어간 적 없는 각도에서도 렌더링됩니다._

- 자체 촬영 2개 공간 모두 전체 프레임 위치 계산 성공(142/142, 149/149), 화질 19.70 / 19.99 dB

## ② 깊이 카메라 + SLAM으로 위치추정까지

RGB-D(깊이) 카메라 녹화 하나에서 **두 가지를 동시에** 만듭니다 — 실사 3D 공간, 그리고 그 공간 안에서 "지금 내가 어디 있는지" 아는 위치추정 기능. XR 기기가 그 공간에 다시 들어왔을 때 내 위치와 공간 화면을 바로 얻는 것이 목표입니다.

방법은 역할 분담입니다. **ORB-SLAM3**가 카메라가 어디를 지나갔는지 계산하고(위치 담당), **gsplat**이 그 위치 정보를 그대로 받아 실사 3D 공간을 만듭니다(그래픽 담당). 둘이 같은 위치 정보에서 출발하니 두 지도가 **자동으로 겹쳐져** 따로 맞추는 과정이 없습니다. 위치와 그래픽을 한 모델로 동시에 푸는 기존 방식들을 직접 돌려보니 둘 다 어중간해서, 각자 잘하는 것을 맡기는 쪽으로 설계했습니다.

![Gaussian 맵 내 위치추정](/assets/img/projects/figs/xrsplat-localize-render.jpg)

_완성된 3D 공간 안에 카메라가 지나간 경로가 표시된 모습 — 공간과 위치가 같은 좌표를 씁니다._

| 무엇을 확인했나                   | 결과                                                   |
| --------------------------------- | ------------------------------------------------------ |
| 위치 정확도 (TUM 공개 데이터)     | 오차 **1.89 cm** (표준 도구 COLMAP의 2.04 cm보다 정확) |
| 자체 촬영 공간 화질               | **27.96 dB**                                           |
| 처음 보는 위치에서 자기 위치 찾기 | **100% 성공**                                          |
| 위치추정 속도                     | **초당 62.8회** (CPU만으로)                            |
| 렌더링 속도                       | **초당 123프레임** (일반 GPU 1장)                      |

![28.8m 전체 맵 전역 위치추정](/assets/img/projects/figs/xrsplat-full-map.png)

_28.8m를 걸은 전체 공간 어디서든 위치 찾기 성공(40/40) — 한 지점이 아니라 경로 전체에서 동작합니다._

`3D Gaussian Splatting` · `gsplat` · `ORB-SLAM3` · `OpenSfM` · `RealSense D455` · `Insta360` · `PyTorch` · `CUDA` · `WebGL`

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
