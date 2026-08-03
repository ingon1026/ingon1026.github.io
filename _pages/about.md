---
layout: about
title: About
permalink: /
subtitle: Vision AI Researcher at K3I · Robot Vision · ROS2 · Embodied AI
profile:
  align: left
  image: prof_pic.jpg
  image_circular: true
  more_info:

selected_papers: true
social: true

announcements:
  enabled: true
  scrollable: false
  limit: 5

latest_posts:
  enabled: false
  scrollable: false
  limit: 3
---

<div class="hero-links">
  <a href="mailto:ingon4359@gmail.com"><i class="fa-solid fa-envelope"></i> Email</a>
  <a href="https://scholar.google.com/citations?user=76h0N_QAAAAJ" target="_blank" rel="noopener noreferrer"><i class="ai ai-google-scholar"></i> Scholar</a>
  <a href="https://github.com/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-github"></i> GitHub</a>
  <a href="https://www.linkedin.com/in/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-linkedin"></i> LinkedIn</a>
  <a href="https://velog.io/@ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-solid fa-pen-nib"></i> Blog</a>
  <a href="/cv/"><i class="fa-solid fa-file"></i> CV</a>
</div>

I am a **Vision AI Researcher at K3I** (Vision AI Lab), building vision systems that connect research ideas to working robots and edge devices. My work spans perception, ROS2 navigation, vision-language systems, and deployment-aware AI—from sensing and model design to system integration and evaluation.

I received my M.S. in IT Convergence Engineering from [Kumoh National Institute of Technology](https://wens.kumoh.ac.kr/home) (WENS Lab, 2026), where I developed an event-driven LLM router for ROS2 navigation that combines visual detections, LiDAR, and localization signals to select driving policies in crowded environments. I earned my B.S. in Electrical Engineering from Korea National University of Transportation (2024).

## Research interests

- **Robot Vision & Navigation:** ROS2, Nav2, SLAM, LiDAR-camera integration, autonomous navigation
- **Vision AI:** object detection, segmentation, Vision Transformers, temporal visual reasoning
- **Embodied & Language AI:** vision-language models, LLM routing, natural-language robot control
- **Edge Deployment:** Jetson Orin NX, Docker, CUDA, real-time perception pipelines

## Selected work

- [Hybrid LLM Navigation System](/projects/hybrid-llm-navigation/) — context-aware policy selection for ROS2 navigation, evaluated against Nav2 in simulated crowded environments.
- [MobileViT Motorcycle Violation Detection](/projects/mobilevit-traffic-violation/) — temporal traffic-event detection deployed on Jetson Orin NX with ROS2.
- [ROS2 UGV Platform Integration](/projects/ros2-ugv/) — sensors, CAN communication, SLAM, and navigation for an unmanned ground vehicle.

<style>
  /* yaodu-style hero, scoped to this page only */
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

  .hero-links {
    display: flex;
    flex-wrap: wrap;
    gap: 0.55rem;
    margin: 0.25rem 0 1.4rem;
  }

  .hero-links a {
    display: inline-flex;
    align-items: center;
    gap: 0.45rem;
    padding: 0.38rem 0.95rem;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.5rem;
    font-size: 0.92rem;
    font-weight: 500;
    color: var(--global-text-color, #333);
    text-decoration: none !important;
    transition:
      color 0.15s ease,
      border-color 0.15s ease,
      background-color 0.15s ease;
  }

  .hero-links a:hover {
    color: var(--global-theme-color, #2698ba);
    border-color: var(--global-theme-color, #2698ba);
    background-color: rgba(0, 0, 0, 0.02);
  }

  .profile img {
    box-shadow:
      0 0 0 4px var(--global-divider-color, rgba(0, 0, 0, 0.06)),
      0 10px 20px rgba(0, 0, 0, 0.12);
  }

  .news table td {
    font-size: 0.95rem;
  }
</style>
