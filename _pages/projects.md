---
layout: page
title: Projects
permalink: /projects/
description: Robot Vision, ROS2, 엣지 AI 분야의 연구·엔지니어링 프로젝트.
lang: ko
nav: true
nav_order: 2
---

[English](/en/projects/)

<div class="prj-list">
  <div class="prj-item">
    <a class="prj-thumb" href="/projects/hybrid-llm-navigation/">
      <img src="/assets/img/projects/hybrid-llm-navigation.png" alt="Hybrid LLM Navigation System" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/hybrid-llm-navigation/">Hybrid LLM Navigation System</a></h3>
      <p class="prj-desc">혼잡 환경에서 상황을 인지해 주행 정책을 선택하는 ROS2 내비게이션 — Nav2 대비 목표 도달 성공률 82% vs 43%.</p>
      <p class="prj-links">
        <a href="/publications/">Paper · JKICS 2026</a>
        <a href="/patents/">Patent</a>
        <a href="/projects/hybrid-llm-navigation/">Details →</a>
      </p>
      <p class="prj-tags">ROS2 · Nav2 · LLM · Gazebo</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/mobilevit-traffic-violation/">
      <img src="/assets/img/projects/mobilevit-traffic-violation.jpg" alt="MobileViT 이륜차 교통 위반 탐지" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/mobilevit-traffic-violation/">MobileViT 이륜차 교통 위반 탐지</a></h3>
      <p class="prj-desc">YOLO와 MobileViT로 시계열 교통 이벤트를 인식하고 Jetson Orin NX에 실시간 배포한 위반 탐지 시스템.</p>
      <p class="prj-links">
        <a href="/publications/">Paper · JKICS 2025</a>
        <a href="/projects/mobilevit-traffic-violation/">Details →</a>
      </p>
      <p class="prj-tags">MobileViT · YOLO · ROS2 · Jetson Orin NX</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/ros2-ugv/">
      <img src="/assets/img/projects/ros2-ugv.jpg" alt="ROS2 UGV 플랫폼 통합" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/ros2-ugv/">ROS2 UGV 플랫폼 통합</a></h3>
      <p class="prj-desc">무인지상차량의 센서·CAN 통신·SLAM·내비게이션을 통합한 자율주행 플랫폼 구축.</p>
      <p class="prj-links">
        <a href="/projects/ros2-ugv/">Details →</a>
      </p>
      <p class="prj-tags">ROS2 · SLAM · LiDAR · CAN</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/strawberry-quality/">
      <img src="/assets/img/projects/strawberry-quality.png" alt="LLM 기반 딸기 품질 자동 판별" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/strawberry-quality/">LLM 기반 딸기 품질 자동 판별</a></h3>
      <p class="prj-desc">세그멘테이션·정량 영상 분석을 RAG와 LLM에 연결해 자연어 품질 리포트를 생성하는 스마트팜 시스템.</p>
      <p class="prj-links">
        <a href="/publications/">Paper · JCCI 2025</a>
        <a href="/projects/strawberry-quality/">Details →</a>
      </p>
      <p class="prj-tags">YOLOv11-seg · OpenCV · RAG · LLM</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/fewshot-writer-id/">
      <img src="/assets/img/projects/fewshot-writer-id.png" alt="소량 샘플 필적 작성자 식별" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/fewshot-writer-id/">소량 샘플 필적 작성자 식별 (Vision Transformer)</a></h3>
      <p class="prj-desc">소량의 필적 샘플로 작성자를 식별하는 ViT 기반 프로토타입 메타러닝 — 특허 출원으로 연계.</p>
      <p class="prj-links">
        <a href="/publications/">Paper · KICS 2025</a>
        <a href="/patents/">Patent</a>
        <a href="/projects/fewshot-writer-id/">Details →</a>
      </p>
      <p class="prj-tags">Vision Transformer · Meta-learning · PyTorch</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/fault-detection/">
      <img src="/assets/img/projects/fault-detection.png" alt="딥러닝 기반 카메라 Fault Detection" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/fault-detection/">딥러닝 기반 카메라 Fault Detection</a></h3>
      <p class="prj-desc">드론 운용 중 카메라 노이즈·환경 이상을 탐지하고 프레임을 정제하는 딥러닝 파이프라인.</p>
      <p class="prj-links">
        <a href="/projects/fault-detection/">Details →</a>
      </p>
      <p class="prj-tags">OpenCV · PyTorch · Zero-shot</p>
    </div>
  </div>
</div>

<style>
  .prj-item {
    display: flex;
    gap: 1.1rem;
    background: var(--global-card-bg-color, #fff);
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.6rem;
    padding: 0.9rem;
    margin-bottom: 1rem;
  }

  .prj-thumb {
    flex-shrink: 0;
  }

  .prj-thumb img {
    width: 11rem;
    height: 8rem;
    object-fit: cover;
    border-radius: 0.45rem;
    display: block;
  }

  .prj-body h3 {
    font-size: 1.02rem;
    font-weight: 600;
    margin: 0 0 0.3rem;
  }

  .prj-body h3 a {
    color: var(--global-text-color, #333);
    text-decoration: none;
  }

  .prj-body h3 a:hover {
    color: var(--global-theme-color, #0056b3);
  }

  .prj-desc {
    font-size: 0.88rem;
    margin: 0 0 0.5rem;
  }

  .prj-links {
    margin: 0;
  }

  .prj-links a {
    display: inline-block;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.4rem;
    padding: 0.12rem 0.55rem;
    font-size: 0.78rem;
    font-weight: 500;
    color: var(--global-text-color, #333);
    text-decoration: none !important;
    margin: 0 0.3rem 0.3rem 0;
    transition:
      color 0.15s ease,
      border-color 0.15s ease;
  }

  .prj-links a:hover {
    color: var(--global-theme-color, #0056b3);
    border-color: var(--global-theme-color, #0056b3);
  }

  .prj-tags {
    font-size: 0.8rem;
    color: var(--global-text-color-light, #828282);
    margin: 0.15rem 0 0;
  }

  @media (max-width: 768px) {
    .prj-item {
      flex-direction: column;
    }

    .prj-thumb img {
      width: 100%;
      height: 10rem;
    }
  }
</style>
