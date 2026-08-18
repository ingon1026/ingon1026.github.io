---
layout: page
title: Projects
permalink: /projects/
lang: ko
nav: true
nav_order: 2
---

<h2 class="prj-section">Industry</h2>

<div class="prj-list">
  <div class="prj-item">
    <a class="prj-thumb" href="/projects/pose-anything/">
      <img src="/assets/img/projects/pose-anything.jpg" alt="제로샷 객체 인식·3D Pose 추정 시스템" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/pose-anything/">제로샷 객체 인식·3D Pose 추정 시스템</a></h3>
      <p class="prj-desc">텍스트 프롬프트만으로 임의 물체를 인식·추적하고 RGB-D로 3D 자세·신뢰도를 ROS2로 발행 — 재학습 없음, CAD 없음, 9~13 FPS.</p>
      <p class="prj-links">
        <a href="https://github.com/ingon1026/pose-anything">Code</a>
        <a href="https://hub.docker.com/r/ingon1026/pose-anything">Docker</a>
        <a href="/projects/pose-anything/">Details →</a>
      </p>
      <p class="prj-tags">SAM3 · ROS2 Jazzy · Open3D · RealSense · Isaac Sim</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/xr-splat/">
      <img src="/assets/img/projects/xr-splat.jpg" alt="Gaussian Splatting 기반 XR 공간 재구성·위치추정" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/xr-splat/">Gaussian Splatting 기반 XR 공간 재구성·위치추정</a></h3>
      <p class="prj-desc">360° 영상과 RGB-D SLAM 두 접근으로 공간 자산과 실내 위치추정을 한 좌표계에서 — 렌더 123 FPS, 전역 위치추정 100%·62.8 FPS.</p>
      <p class="prj-links">
        <a href="https://github.com/ingon1026/xr-splat">Code</a>
        <a href="https://huggingface.co/spaces/ingon1/xr-splat-demo">Demo</a>
        <a href="/projects/xr-splat/">Details →</a>
      </p>
      <p class="prj-tags">3DGS · ORB-SLAM3 · OpenSfM · Insta360 · WebGL</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/projects/drawing-character/">
      <img src="/assets/img/projects/drawing-character.png" alt="사용자 그림 기반 인터랙티브 캐릭터" />
    </a>
    <div class="prj-body">
      <h3><a href="/projects/drawing-character/">사용자 그림 기반 인터랙티브 캐릭터</a></h3>
      <p class="prj-desc">손그림을 자동 인식·리깅하고 사용자의 몸동작·표정·음성을 실시간으로 입히는 캐릭터 기술 — 발화 영상 생성 4.8→2.1초.</p>
      <p class="prj-links">
        <a href="https://github.com/ingon1026/drawface-live">Code</a>
        <a href="https://ingon1-drawface-live.static.hf.space">Demo</a>
        <a href="/projects/drawing-character/">Details →</a>
      </p>
      <p class="prj-tags">MediaPipe · ARKit 52ch · LivePortrait · TensorRT · WebGL</p>
    </div>
  </div>
</div>

<h2 class="prj-section">Research</h2>

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
  .prj-section {
    color: var(--global-theme-color, #0056b3);
    font-size: 1.15rem;
    font-weight: 600;
    border-bottom: 1px solid var(--global-divider-color, #e0e0e0);
    padding-bottom: 0.4rem;
    margin: 1.8rem 0 1rem;
  }

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
