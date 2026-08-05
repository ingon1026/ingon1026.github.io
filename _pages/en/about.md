---
layout: about
title: About
permalink: /en/
subtitle: Vision AI Researcher · Robot Vision · ROS2 · Embodied AI
lang: en

selected_papers: false
social: false

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
      I am a Vision AI Researcher at <a href="https://www.k3i.co.kr/web/index.do" target="_blank" rel="noopener noreferrer">K3I</a> (Vision AI Lab),
      where I research and develop vision models used in the company's XR and Physical AI products.
    </p>
    <p class="yd-bio">
      I received my M.S. in IT Convergence Engineering from Kumoh National Institute of Technology
      (<a href="https://wens.kumoh.ac.kr/home" target="_blank" rel="noopener noreferrer">WENS Lab</a>, 2026), advised by Prof.
      <a href="https://scholar.google.com/citations?user=c8JDiHYAAAAJ" target="_blank" rel="noopener noreferrer">Soo Young Shin</a>. My master's
      research centered on LLM-based navigation, visual recognition, and edge AI. I earned my B.S. in Electrical Engineering from Korea National
      University of Transportation (2024).
    </p>
    <p class="yd-bio">
      My research interests lie in Vision AI — particularly robot vision, SLAM, navigation, and autonomous driving — with a focus on making
      perception models work reliably inside real systems.
    </p>
    <div class="yd-links">
      <a href="mailto:ingon4359@gmail.com"><i class="fa-solid fa-envelope"></i> Email</a>
      <a href="https://scholar.google.com/citations?user=76h0N_QAAAAJ" target="_blank" rel="noopener noreferrer"><i class="ai ai-google-scholar"></i> Scholar</a>
      <a href="https://github.com/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-github"></i> GitHub</a>
      <a href="https://www.linkedin.com/in/ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-brands fa-linkedin"></i> LinkedIn</a>
      <a href="https://huggingface.co/ingon1" target="_blank" rel="noopener noreferrer">🤗 Demo</a>
      <a href="https://velog.io/@ingon1026" target="_blank" rel="noopener noreferrer"><i class="fa-solid fa-pen-nib"></i> Blog</a>
      <a href="/assets/pdf/KimInGon_CV.pdf" target="_blank" rel="noopener noreferrer"><i class="fa-solid fa-file-pdf"></i> CV</a>
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
  </div>
</div>

## Research

<div class="yd-umbrella">
  <h3 class="yd-umbrella-title">Vision AI</h3>
  <div class="yd-axes">
    <div class="yd-axis">
      <h4><i class="fa-solid fa-robot"></i> Robot Vision &amp; Navigation</h4>
      <p>ROS2 · Nav2 · SLAM · Autonomous driving</p>
    </div>
    <div class="yd-vla">VLA</div>
    <div class="yd-axis">
      <h4><i class="fa-solid fa-comments"></i> VLM &amp; LLM Routing</h4>
      <p>VLM · LLM · Natural-language robot control</p>
    </div>
  </div>
  <p class="yd-axes-note">Where the two axes meet — Vision-Language-Action (VLA)</p>
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
    align-items: center;
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

  /* recent news card (inside the hero text column) */
  .yd-news {
    background: var(--global-card-bg-color, #fff);
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    padding: 1rem 1.25rem;
    margin: 1.2rem 0 0;
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

  /* Vision AI umbrella + VLA venn diagram */
  .yd-umbrella {
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    padding: 1.2rem 1.4rem 1.6rem;
    margin: 1rem 0 1.5rem;
  }

  .yd-umbrella-title {
    font-size: 1.05rem;
    font-weight: 700;
    color: var(--global-theme-color, #0056b3);
    margin: 0 0 1rem;
  }

  .yd-axes {
    display: flex;
    align-items: stretch;
  }

  .yd-axis {
    flex: 1;
    border: 1px solid var(--global-divider-color, #e0e0e0);
    border-radius: 0.75rem;
    padding: 1.1rem 2rem;
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .yd-axis h4 {
    font-size: 0.98rem;
    font-weight: 600;
    margin: 0 0 0.35rem;
  }

  .yd-axis h4 i {
    color: var(--global-theme-color, #0056b3);
    margin-right: 0.35rem;
  }

  .yd-axis p {
    font-size: 0.85rem;
    color: var(--global-text-color-light, #828282);
    margin: 0;
  }

  .yd-vla {
    align-self: center;
    flex-shrink: 0;
    width: 3.4rem;
    height: 3.4rem;
    border-radius: 50%;
    margin: 0 -1.7rem;
    z-index: 2;
    display: flex;
    align-items: center;
    justify-content: center;
    background: var(--global-theme-color, #0056b3);
    color: #fff;
    font-size: 0.88rem;
    font-weight: 700;
    letter-spacing: 0.02em;
    box-shadow: 0 0 0 4px var(--global-bg-color, #fff);
  }

  .yd-axes-note {
    text-align: center;
    font-size: 0.85rem;
    color: var(--global-text-color-light, #828282);
    margin: 0.9rem 0 0;
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

    .yd-axes {
      flex-direction: column;
    }

    .yd-vla {
      margin: -1.7rem 0;
    }
  }
</style>
