---
layout: page
title: Projects
permalink: /en/projects/
lang: en
nav: false
---

<h2 class="prj-section">Industry</h2>

<div class="prj-list">
  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/pose-anything/">
      <img src="/assets/img/projects/pose-anything.jpg" alt="Zero-Shot Object Recognition and 3D Pose Estimation" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/pose-anything/">Zero-Shot Object Recognition &amp; 3D Pose Estimation</a></h3>
      <p class="prj-desc">Detect and track arbitrary objects from a text prompt, publish RGB-D 3D pose with confidence over ROS2 — no retraining, no CAD, 9–13 FPS.</p>
      <p class="prj-links">
        <a href="https://github.com/ingon1026/pose-anything"><i class="fa-brands fa-github"></i> Source</a>
        <a href="https://hub.docker.com/r/ingon1026/pose-anything"><i class="fa-brands fa-docker"></i> Docker</a>
        <a href="/en/projects/pose-anything/">Details →</a>
      </p>
      <p class="prj-tags">SAM3 · ROS2 Jazzy · Open3D · RealSense · Isaac Sim</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/xr-splat/">
      <img src="/assets/img/projects/figs/xrsplat-mvs-cloud.jpg" alt="Gaussian Splatting XR Space Reconstruction and Localization" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/xr-splat/">Gaussian Splatting XR Space Reconstruction &amp; Localization</a></h3>
      <p class="prj-desc">Space assets and indoor localization in one coordinate frame, via 360° video and RGB-D SLAM — 123 FPS rendering, 100% global relocalization at 62.8 FPS.</p>
      <p class="prj-links">
        <a class="prj-btn" href="https://huggingface.co/spaces/ingon1/xr-splat-demo">🤗 Live demo</a>
        <a href="https://github.com/ingon1026/xr-splat"><i class="fa-brands fa-github"></i> Source</a>
        <a href="/en/projects/xr-splat/">Details →</a>
      </p>
      <p class="prj-tags">3DGS · ORB-SLAM3 · OpenSfM · Insta360 · WebGL</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/drawing-character/">
      <img src="/assets/img/projects/figs/drawing-bvh-flow.gif" alt="Drawing-Based Interactive Character" style="object-fit: contain; background: #fff" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/drawing-character/">Drawing-Based Interactive Character</a></h3>
      <p class="prj-desc">Auto-rig hand drawings and drive them with the user's body motion, facial expressions, and speech in real time — talking video generation 4.8→2.1 s.</p>
      <p class="prj-links">
        <a class="prj-btn" href="https://ingon1-drawface-live.static.hf.space">🤗 Live demo</a>
        <a href="https://github.com/ingon1026/drawface-live"><i class="fa-brands fa-github"></i> Source</a>
        <a href="/en/projects/drawing-character/">Details →</a>
      </p>
      <p class="prj-tags">MediaPipe · ARKit 52ch · LivePortrait · TensorRT · WebGL</p>
    </div>
  </div>
</div>

<h2 class="prj-section">Research</h2>

<div class="prj-list">
  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/hybrid-llm-navigation/">
      <img src="/assets/img/projects/hybrid-llm-navigation.png" alt="Hybrid LLM Navigation System" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/hybrid-llm-navigation/">Hybrid LLM Navigation System</a></h3>
      <p class="prj-desc">Context-aware ROS2 navigation that selects driving policies in crowded environments — 82% vs 43% goal-arrival success over the Nav2 baseline.</p>
      <p class="prj-links">
        <a href="/en/publications/">Paper · JKICS 2026</a>
        <a href="/en/patents/">Patent</a>
        <a href="/en/projects/hybrid-llm-navigation/">Details →</a>
      </p>
      <p class="prj-tags">ROS2 · Nav2 · LLM · Gazebo</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/mobilevit-traffic-violation/">
      <img src="/assets/img/projects/mobilevit-traffic-violation.jpg" alt="MobileViT Motorcycle Traffic-Violation Detection" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/mobilevit-traffic-violation/">MobileViT Motorcycle Traffic-Violation Detection</a></h3>
      <p class="prj-desc">Temporal traffic-event recognition with YOLO and MobileViT, deployed in real time on a Jetson Orin NX.</p>
      <p class="prj-links">
        <a href="/en/publications/">Paper · JKICS 2025</a>
        <a href="/en/projects/mobilevit-traffic-violation/">Details →</a>
      </p>
      <p class="prj-tags">MobileViT · YOLO · ROS2 · Jetson Orin NX</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/ros2-ugv/">
      <img src="/assets/img/projects/ros2-ugv.jpg" alt="ROS2 UGV Platform Integration" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/ros2-ugv/">ROS2 UGV Platform Integration</a></h3>
      <p class="prj-desc">Autonomous-driving platform integration for an unmanned ground vehicle: sensors, CAN communication, SLAM, and navigation.</p>
      <p class="prj-links">
        <a href="/en/projects/ros2-ugv/">Details →</a>
      </p>
      <p class="prj-tags">ROS2 · SLAM · LiDAR · CAN</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/strawberry-quality/">
      <img src="/assets/img/projects/strawberry-quality.png" alt="LLM-Assisted Strawberry Quality Assessment" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/strawberry-quality/">LLM-Assisted Strawberry Quality Assessment</a></h3>
      <p class="prj-desc">Smart-farm system linking segmentation and quantitative image analysis to RAG and LLM-generated quality reports.</p>
      <p class="prj-links">
        <a href="/en/publications/">Paper · JCCI 2025</a>
        <a href="/en/projects/strawberry-quality/">Details →</a>
      </p>
      <p class="prj-tags">YOLOv11-seg · OpenCV · RAG · LLM</p>
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

  .prj-links a.prj-btn {
    background: var(--global-theme-color, #0056b3);
    border: 1px solid var(--global-theme-color, #0056b3);
    color: #fff;
    font-weight: 600;
  }

  .prj-links a.prj-btn:hover {
    color: #fff;
    opacity: 0.85;
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
