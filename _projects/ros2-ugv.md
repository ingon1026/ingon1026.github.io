---
layout: page
title: ROS2 UGV 플랫폼 통합
description: 무인지상차량의 센서·통신·SLAM·내비게이션 통합.
category: featured
importance: 3
lang: ko
img: assets/img/projects/ros2-ugv.jpg
permalink: /projects/ros2-ugv/
---

[English](/en/projects/ros2-ugv/)

## 범위

연구실의 **multi-UXV(무인이동체) 팀 프로젝트**에서 UGV(무인 지상 차량) 파트를 담당해, 플랫폼 셋업부터 자율주행 파이프라인 구축까지 수행했습니다. UGV는 드론 군집과 연계되는 이동식 충전 스테이션 역할도 겸하는 구성입니다.

![multi-UXV 시스템 개요](/assets/img/projects/figs/ugv-multi-uxv.png)

_multi-UXV 시스템 개요 — 드론 군집(3D LiDAR·RGB-D)과 지상의 UGV 이동식 충전 스테이션이 연계되는 구조. 이 중 UGV 플랫폼 구축을 담당했습니다._

## 기여

- ROS2 환경에서 UGV 플랫폼 초기 셋업과 주행 환경 구성을 수행했습니다.
- CAN 통신, 로봇 SDK, Ouster LiDAR, Intel RealSense D435i 카메라, IMU 센싱을 통합했습니다.
- Docker 컨테이너 기반으로 센서 드라이버·주행 환경을 구성해 재현 가능한 셋업을 만들었습니다.
- SLAM과 내비게이션 워크플로를 구성하고, 팀원이 따라할 수 있는 셋업·통합 가이드를 문서화했습니다.

![SLAM 매핑 화면](/assets/img/projects/figs/ugv-slam-rviz.png)

_RViz에서 확인한 LiDAR 포인트클라우드 기반 SLAM 매핑 — 맵·포인트클라우드·오도메트리를 실시간 시각화합니다._

`ROS2` · `ROS1` · `SLAM` · `Ouster LiDAR` · `RealSense D435i` · `CAN` · `Docker` · `Python` · `C++`

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
