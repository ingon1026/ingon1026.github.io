---
layout: page
title: 제로샷 객체 인식·3D Pose 추정 시스템
description: 텍스트 프롬프트만으로 임의 물체를 인식하고 RGB-D로 3D 위치·크기·방향을 추정하는 Robot Perception 파이프라인.
category: industry
importance: 1
lang: ko
img: assets/img/projects/pose-anything.jpg
permalink: /projects/pose-anything/
---

## 개요

- **기간:** 2026.08 – 현재 (K3I)
- 컨베이어 환경에서 **텍스트 프롬프트만으로 임의 물체를 인식**하고, RGB-D 정보로 3D 위치·크기·방향을 추정하는 Robot Perception 파이프라인
- 물체별 추가 학습 데이터·CAD 모델 없이 새로운 대상 물체에 대응

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_실시간 데모_

## 주요 개발 내용

- **SAM3 기반 텍스트 프롬프트 객체 분할** — "thermos", "book"처럼 텍스트로 대상 지정, 재학습 없음
- **하이브리드 추적** — SAM3는 5프레임마다 1회, 사이 프레임은 광학흐름으로 추적 → **9~13 FPS**
- **RGB-D 3D Pose 추정** — Depth를 Point Cloud로 변환 후 Open3D OBB로 위치·크기·방향 산출, 정지 물체 크기 **실물 ±1cm**, 회전 안정화로 축 뒤집힘 0회
- **가림(Occlusion) 대응** — 칼만 필터 기반 신뢰 판정으로 가림 중 pose 발행 보류, 재등장 시 동일 ID 유지
- **ROS2 파이프라인** — 결과를 ROS2 Topic으로 발행, RViz 시각화, Isaac Sim 컨베이어 환경 연동 검증

![ROS2 파이프라인](/assets/img/projects/figs/pose-pipeline.png)

_ROS2 노드·토픽 구성_

![발행 시점의 3D 자세](/assets/img/projects/figs/pose-detections.gif)

_/perception/detections 발행 화면 — 가림 시 발행 보류_

![Isaac Sim 연동](/assets/img/projects/figs/pose-isaac.jpg)

_Isaac Sim 컨베이어 연동_

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
