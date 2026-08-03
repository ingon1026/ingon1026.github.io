---
layout: about
title: About
permalink: /
subtitle: Vision AI Researcher · Robot Vision · ROS2 · Embodied AI

selected_papers: true
social: true

announcements:
  enabled: false
  scrollable: false
  limit: 5

latest_posts:
  enabled: false
  scrollable: false
  limit: 3
---

<div class="yd-hero">
  <img class="yd-avatar" src="/assets/img/prof_pic.jpg" alt="Kim In Gon — Vision AI Researcher" />
  <div class="yd-hero-text">
    <h1 class="yd-name">Kim In Gon</h1>
    <p class="yd-role">Vision AI Researcher</p>
    <p class="yd-loc"><i class="fa-solid fa-location-dot"></i> Republic of Korea</p>
    <p class="yd-bio">
      I am a Vision AI Researcher at K3I (Vision AI Lab), where I research and develop vision models for AI transformation (AX) applications, working
      across data, model design, evaluation, and deployment.
    </p>
    <p class="yd-bio">
      I received my M.S. in IT Convergence Engineering from
      <a href="https://wens.kumoh.ac.kr/home" target="_blank" rel="noopener noreferrer">Kumoh National Institute of Technology</a> (WENS Lab, 2026),
      advised by Prof.
      <a href="https://scholar.google.com/citations?user=c8JDiHYAAAAJ" target="_blank" rel="noopener noreferrer">Soo Young Shin</a>. My thesis brought
      semantic context into ROS2 navigation through an event-driven LLM router that combines visual detections, LiDAR, and localization signals to
      select driving policies in crowded environments. I earned my B.S. in Electrical Engineering from Korea National University of Transportation
      (2024).
    </p>
    <p class="yd-bio">
      My research interests center on robot vision and embodied AI—visual SLAM, 3D Gaussian Splatting, and autonomous navigation—where perception
      models have to work reliably inside a real system.
    </p>
    <div class="yd-links">
      <a href="mailto:ingon4359@gmail.com"><i class="fa-solid fa-envelope"></i> Email</a>
      <a href="https://scholar.google.com/citations?user=76h0N_QAAAAJ" target="_blank" rel="noopener noreferrer"><i class="ai ai-google-scholar"></i> Scholar</a>
      <a href="https://github.com/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-github"></i> GitHub</a>
      <a href="https://www.linkedin.com/in/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-linkedin"></i> LinkedIn</a>
      <a href="https://huggingface.co/ingon1" target="_blank" rel="noopener noreferrer">🤗 Demo</a>
      <a href="https://velog.io/@ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-solid fa-pen-nib"></i> Blog</a>
      <a href="/cv/"><i class="fa-solid fa-file"></i> CV</a>
    </div>
  </div>
</div>

<div class="yd-news">
  <h3>Recent News</h3>
  <ul>
    <li><span>Jun 2026</span> "Hybrid LLM Navigation System for Edge-Cloud Reasoning" was published in JKICS (vol. 51, no. 6).</li>
    <li><span>Mar 2026</span> Joined K3I as a Vision AI Researcher (Vision AI Lab).</li>
    <li><span>Feb 2026</span> Completed my M.S. in IT Convergence Engineering at Kumoh National Institute of Technology (WENS Lab).</li>
    <li><span>Dec 2025</span> "A MobileViT-Based Detection System for Motorcycle Traffic Violations" was published in JKICS (vol. 50, no. 12).</li>
    <li><span>May 2024</span> Won 3rd place (Surveillance and Reconnaissance, civilian division) at the 2nd ROK Second Operations Command Dronebot Combat Competition.</li>
  </ul>
</div>

## Research

<div class="yd-grid">
  <div class="yd-card">
    <h4><i class="fa-solid fa-robot"></i> Robot Vision &amp; Navigation</h4>
    <p>ROS2, Nav2, SLAM, LiDAR-camera integration, autonomous navigation</p>
  </div>
  <div class="yd-card">
    <h4><i class="fa-solid fa-eye"></i> Vision AI</h4>
    <p>Object detection, segmentation, Vision Transformers, temporal visual reasoning</p>
  </div>
  <div class="yd-card">
    <h4><i class="fa-solid fa-comments"></i> Embodied &amp; Language AI</h4>
    <p>Vision-language models, LLM routing, natural-language robot control</p>
  </div>
  <div class="yd-card">
    <h4><i class="fa-solid fa-microchip"></i> Edge Deployment</h4>
    <p>Jetson Orin NX, Docker, CUDA, real-time perception pipelines</p>
  </div>
</div>

## Selected work

<div class="yd-projects">
  <a class="yd-project" href="/projects/hybrid-llm-navigation/">
    <img src="/assets/img/projects/hybrid-llm-navigation.png" alt="Hybrid LLM Navigation System" />
    <div class="yd-project-body">
      <h4>Hybrid LLM Navigation System</h4>
      <p>Context-aware policy selection for ROS2 navigation in crowded environments.</p>
      <div class="yd-badges"><span>ROS2</span><span>Nav2</span><span>LLM</span></div>
    </div>
  </a>
  <a class="yd-project" href="/projects/mobilevit-traffic-violation/">
    <img src="/assets/img/projects/mobilevit-traffic-violation.jpg" alt="MobileViT Motorcycle Traffic-Violation Detection" />
    <div class="yd-project-body">
      <h4>MobileViT Violation Detection</h4>
      <p>Temporal traffic-event detection deployed on Jetson Orin NX.</p>
      <div class="yd-badges"><span>MobileViT</span><span>YOLO</span><span>Jetson</span></div>
    </div>
  </a>
  <a class="yd-project" href="/projects/ros2-ugv/">
    <img src="/assets/img/projects/ros2-ugv.jpg" alt="ROS2 UGV Platform Integration" />
    <div class="yd-project-body">
      <h4>ROS2 UGV Platform</h4>
      <p>Sensors, CAN communication, SLAM, and navigation for a UGV.</p>
      <div class="yd-badges"><span>ROS2</span><span>SLAM</span><span>LiDAR</span></div>
    </div>
  </a>
</div>

<style>
  /* ---- yaodu-style home, scoped to this page ---- */
  body {
    font-family:
      -apple-system,
      BlinkMacSystemFont,
      "Segoe UI",
      Roboto,
      "Noto Sans",
      "Noto Sans KR",
      sans-serif;
  }

  /* hide the theme's default header; the custom hero replaces it */
  .post-header {
    display: none;
  }

  /* hero */
  .yd-hero {
    display: flex;
    align-items: flex-start;
    gap: 2.4rem;
    margin: 1.2rem 0 1.8rem;
  }

  .yd-avatar {
    width: 12rem;
    height: 12rem;
    border-radius: 9999px;
    object-fit: cover;
    flex-shrink: 0;
    box-shadow:
      0 0 0 4px rgba(0, 86, 179, 0.12),
      0 10px 24px rgba(0, 0, 0, 0.14);
  }

  .yd-name {
    font-size: 2.3rem;
    font-weight: 700;
    margin: 0 0 0.2rem;
    line-height: 1.15;
  }

  .yd-role {
    font-size: 1.15rem;
    color: var(--global-text-color-light, #828282);
    margin: 0 0 0.15rem;
  }

  .yd-loc {
    font-size: 0.9rem;
    color: var(--global-text-color-light, #828282);
    margin: 0 0 0.9rem;
  }

  .yd-loc i {
    margin-right: 0.25rem;
  }

  .yd-bio {
    font-size: 0.95rem;
    line-height: 1.65;
    margin: 0 0 0.7rem;
  }

  /* link buttons */
  .yd-links {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-top: 0.4rem;
  }

  .yd-links a {
    display: inline-flex;
    align-items: center;
    gap: 0.42rem;
    padding: 0.36rem 0.85rem;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.5rem;
    font-size: 0.9rem;
    font-weight: 500;
    color: var(--global-text-color, #333);
    text-decoration: none !important;
    transition:
      color 0.15s ease,
      border-color 0.15s ease;
  }

  .yd-links a:hover {
    color: var(--global-theme-color, #0056b3);
    border-color: var(--global-theme-color, #0056b3);
  }

  /* recent news card */
  .yd-news {
    background: var(--global-card-bg-color, #fff);
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    padding: 1rem 1.25rem;
    margin: 0 0 2rem;
  }

  .yd-news h3 {
    font-size: 0.95rem;
    font-weight: 600;
    margin: 0 0 0.6rem;
  }

  .yd-news ul {
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .yd-news li {
    display: flex;
    gap: 1rem;
    font-size: 0.92rem;
    padding: 0.22rem 0;
  }

  .yd-news li span {
    color: var(--global-text-color-light, #828282);
    font-weight: 500;
    white-space: nowrap;
    min-width: 5.2rem;
  }

  /* research interest cards */
  .yd-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 0.9rem;
    margin: 1rem 0 1.5rem;
  }

  .yd-card {
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    padding: 0.95rem 1.1rem;
  }

  .yd-card h4 {
    font-size: 1rem;
    font-weight: 600;
    margin: 0 0 0.35rem;
  }

  .yd-card h4 i {
    color: var(--global-theme-color, #0056b3);
    margin-right: 0.4rem;
  }

  .yd-card p {
    font-size: 0.9rem;
    color: var(--global-text-color-light, #828282);
    margin: 0;
  }

  /* project cards */
  .yd-projects {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 0.9rem;
    margin: 1rem 0 1.5rem;
  }

  .yd-project {
    display: block;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    overflow: hidden;
    color: var(--global-text-color, #333);
    text-decoration: none !important;
    transition:
      transform 0.15s ease,
      box-shadow 0.15s ease;
  }

  .yd-project:hover {
    transform: translateY(-3px);
    box-shadow: 0 10px 24px rgba(0, 0, 0, 0.12);
    color: var(--global-text-color, #333);
  }

  .yd-project img {
    width: 100%;
    height: 8.5rem;
    object-fit: cover;
    display: block;
    background: var(--global-card-bg-color, #fff);
  }

  .yd-project-body {
    padding: 0.8rem 0.95rem 0.95rem;
  }

  .yd-project h4 {
    font-size: 0.98rem;
    font-weight: 600;
    margin: 0 0 0.3rem;
  }

  .yd-project p {
    font-size: 0.85rem;
    color: var(--global-text-color-light, #828282);
    margin: 0 0 0.55rem;
  }

  .yd-badges {
    display: flex;
    flex-wrap: wrap;
    gap: 0.35rem;
  }

  .yd-badges span {
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 9999px;
    padding: 0.1rem 0.6rem;
    font-size: 0.72rem;
    font-weight: 600;
  }

  /* responsive */
  @media (max-width: 768px) {
    .yd-hero {
      flex-direction: column;
      align-items: center;
    }

    .yd-hero-text {
      text-align: center;
    }

    .yd-hero-text .yd-bio {
      text-align: left;
    }

    .yd-links {
      justify-content: center;
    }

    .yd-grid,
    .yd-projects {
      grid-template-columns: 1fr;
    }
  }
</style>
