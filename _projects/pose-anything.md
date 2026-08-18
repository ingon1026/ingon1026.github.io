---
layout: page
title: 제로샷 객체 인식·3D Pose 추정 시스템
description: 텍스트 프롬프트만으로 임의 물체를 인식하고 RGB-D로 3D 자세를 추정하는 로봇 인지 파이프라인.
category: industry
importance: 1
lang: ko
img: assets/img/projects/pose-anything.jpg
permalink: /projects/pose-anything/
---

## 문제

컨베이어 위 물체를 로봇이 집으려면 3D 자세(위치·크기·방향)가 필요한데, 기존 방식은 물체가 바뀔 때마다 데이터 수집→라벨링→재학습(일 단위)이거나 CAD 모델을 요구합니다. 이 프로젝트는 **텍스트 프롬프트("thermos", "book")만 바꾸면 임의 물체를 즉시 검출·추적**하고, RGB-D 기하로 3D 자세와 신뢰도까지 산출해 ROS2로 발행합니다 — 학습 없음, CAD 없음. (K3I 재직 중 수행)

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_실시간 데모 — 텍스트 프롬프트로 지정한 물체들을 검출·추적하며 3D OBB와 자세를 발행합니다._

## 시스템

**SAM3 제로샷 인식** — Meta SAM 3(open-vocabulary detection+segmentation)로 텍스트 프롬프트 기반 분할. 새 물체를 추가할 때 재학습 파이프라인 자체를 만들지 않았습니다. bf16 추론으로 fp32 대비 3.7배 가속, 프롬프트별 텍스트 임베딩 캐시.

**하이브리드 추적** — SAM3 상시 추론은 ~3 FPS가 상한이라, 5프레임마다 한 번만 돌리고 사이 프레임은 Lucas-Kanade 광학흐름(마스크 내 ~300점, 이동량 중앙값)으로 마스크를 이동시킵니다. 3D 자세는 매 프레임 실제 depth로 재계산 — 결과 **9~13 FPS**. 가림(occlusion) 상황에서도 동일 객체 ID를 유지합니다.

**기하 기반 3D 자세** — 마스크+aligned depth를 역투영해 점군을 만들고 Open3D PCA OBB로 위치·크기·방향을 추정합니다(정지 물체 크기 실물 대비 ±1cm). PCA 축의 순열·부호 임의성은 축 매칭 → 2° 데드밴드 → slerp 3단으로 안정화해 **프레임당 0.94°, 축 뒤집힘 0회**.

**확률 융합 필터** — 임계값 게이트를 쌓는 대신 축별 칼만 필터 + χ² 게이트(위치/크기 분리)로 관측 신뢰를 판정합니다. 거부가 이어지면 예측 불확실성이 커져 게이트가 스스로 열리므로 **교착이 원리적으로 불가능**하고, 물체별 관측 잡음(실측 40배 차이)은 트랙별로 적응합니다.

![ROS2 파이프라인](/assets/img/projects/figs/pose-pipeline.png)

_ROS2 노드·토픽 구성 — 카메라 입력과 프롬프트를 받아 /perception/detections·markers·debug_image를 발행하고 RViz·로봇 노드가 소비합니다._

![발행 시점의 3D 자세](/assets/img/projects/figs/pose-detections.gif)

_로봇이 실제 받는 것 — 가림 중에는 자세 발행을 보류하고("pose withheld") 재등장 시 같은 ID로 재개합니다. 신뢰하지 못하는 좌표는 로봇에 보내지 않는다는 발행 철학입니다._

![Isaac Sim 연동](/assets/img/projects/figs/pose-isaac.jpg)

_Isaac Sim 컨베이어 디지털 트윈 연동 — XR 기술융합팀에서 구축한 환경을 ROS2 Bridge로 연결해 가상 카메라에서 동일 파이프라인을 검증합니다._

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
