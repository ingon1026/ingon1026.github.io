---
layout: page
title: Projects
permalink: /en/projects/
description: Selected research and engineering projects in Robot Vision, ROS2, and edge AI.
lang: en
nav: false
---

[한국어](/projects/)

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

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/fewshot-writer-id/">
      <img src="/assets/img/projects/fewshot-writer-id.png" alt="Few-Shot Writer Identification" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/fewshot-writer-id/">Few-Shot Writer Identification with Vision Transformers</a></h3>
      <p class="prj-desc">ViT-based prototypical meta-learning that identifies writers from a few handwriting samples — extended into a patent application.</p>
      <p class="prj-links">
        <a href="/en/publications/">Paper · KICS 2025</a>
        <a href="/en/patents/">Patent</a>
        <a href="/en/projects/fewshot-writer-id/">Details →</a>
      </p>
      <p class="prj-tags">Vision Transformer · Meta-learning · PyTorch</p>
    </div>
  </div>

  <div class="prj-item">
    <a class="prj-thumb" href="/en/projects/fault-detection/">
      <img src="/assets/img/projects/fault-detection.png" alt="Deep-Learning Camera Fault Detection" />
    </a>
    <div class="prj-body">
      <h3><a href="/en/projects/fault-detection/">Deep-Learning Camera Fault Detection</a></h3>
      <p class="prj-desc">Deep-learning pipeline that detects and cleans camera noise and environmental artifacts during drone operation.</p>
      <p class="prj-links">
        <a href="/en/projects/fault-detection/">Details →</a>
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
