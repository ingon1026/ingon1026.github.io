---
layout: page
title: 제로샷 객체 인식·3D Pose 추정 시스템
description: 텍스트로 물체 이름만 입력하면 재학습 없이 인식·추적하고 3D 자세까지 계산하는 로봇 인지 파이프라인.
category: industry
importance: 1
lang: ko
img: assets/img/projects/pose-anything.jpg
permalink: /projects/pose-anything/
---

## 문제

로봇이 컨베이어 위 물체를 집으려면 물체의 3D 위치·크기·방향을 알아야 합니다. 기존에는 물체가 바뀔 때마다 사진을 모으고 라벨링해서 모델을 다시 학습시키거나(며칠 단위), 물체의 CAD 도면이 필요했습니다. 이 프로젝트는 그 과정을 없앴습니다 — **"thermos", "book"처럼 물체 이름을 글자로 입력하면 바로 인식**합니다. (K3I 재직 중 수행)

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_실시간 데모 — 글자로 지정한 물체를 찾아 추적하면서 3D 상자(위치·크기·방향)를 계산합니다._

## 어떻게 만들었나

- **인식은 Meta의 SAM3 모델로.** 텍스트로 지정한 물체를 화면에서 찾아 오려냅니다. 새 물체가 와도 프롬프트만 바꾸면 되고, 학습은 필요 없습니다.
- **속도는 광학흐름으로.** SAM3는 무거워서 매 프레임 돌리면 초당 3장이 한계입니다. 그래서 5프레임에 한 번만 SAM3를 돌리고, 그 사이에는 가벼운 광학흐름으로 물체를 따라가게 해 **초당 9~13프레임**을 냈습니다.
- **3D 자세는 깊이 카메라 계산으로.** RealSense 깊이 데이터를 3D 점으로 바꿔, 물체를 감싸는 상자(OBB)의 위치·크기·방향을 구합니다. 정지 물체 기준 실제 크기와 **±1cm** 오차이고, 상자 방향이 프레임마다 튀지 않게 안정화해 축 뒤집힘 0회를 만들었습니다.
- **믿을 수 없는 값은 안 보냅니다.** 칼만 필터가 관측을 검사해서, 물체가 가려지는 등 값이 이상하면 좌표 발행을 잠시 멈추고 다시 나타나면 같은 ID로 이어서 추적합니다. 로봇에게 틀린 좌표를 주지 않는 것이 원칙입니다.
- **로봇과는 ROS2로 연결.** 결과를 ROS2 토픽으로 내보내 RViz와 로봇 제어 노드가 바로 쓸 수 있고, Isaac Sim 가상 컨베이어에서도 같은 파이프라인을 검증했습니다.

![ROS2 파이프라인](/assets/img/projects/figs/pose-pipeline.png)

_카메라 영상과 텍스트 프롬프트가 들어가서, 인식 결과가 ROS2 토픽으로 나오는 구조._

![발행 시점의 3D 자세](/assets/img/projects/figs/pose-detections.gif)

_로봇이 실제로 받는 화면 — 물체가 가려지면 좌표 발행을 멈췄다가, 다시 보이면 같은 ID로 이어집니다._

![Isaac Sim 연동](/assets/img/projects/figs/pose-isaac.jpg)

_Isaac Sim 가상 컨베이어 연동 — XR 기술융합팀이 만든 시뮬레이션 환경에서도 같은 인식이 동작합니다._

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
