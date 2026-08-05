---
layout: about
title: About
permalink: /
subtitle: Vision AI Researcher · Robot Vision · ROS2 · Embodied AI
lang: ko

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
  <img class="yd-avatar" src="/assets/img/prof_pic.jpg" alt="김인곤 — Vision AI 연구원" />
  <div class="yd-hero-text">
    <h1 class="yd-name">김인곤</h1>
    <p class="yd-role">Vision AI 연구원</p>
    <p class="yd-loc"><i class="fa-solid fa-location-dot"></i> 대한민국</p>
    <p class="yd-bio">
      <a href="https://www.k3i.co.kr/web/index.do" target="_blank" rel="noopener noreferrer">K3I</a> Vision AI Lab에서 Vision AI 연구원으로 재직하며,
      회사의 XR·Physical AI 제품에 쓰이는 비전 모델을 연구·개발하고 있습니다.
    </p>
    <p class="yd-bio">
      금오공과대학교 IT융복합공학 석사 학위(<a href="https://wens.kumoh.ac.kr/home" target="_blank" rel="noopener noreferrer">WENS 연구실</a>,
      2026)를 <a href="https://scholar.google.com/citations?user=c8JDiHYAAAAJ" target="_blank" rel="noopener noreferrer">신수용</a> 교수님 지도로
      취득했습니다. 석사 연구는 LLM 기반 내비게이션 · 비전 인식 · 엣지 AI를 중심으로 진행했습니다. 한국교통대학교 전기공학 학사(2024)를
      졸업했습니다.
    </p>
    <p class="yd-bio">
      연구 관심사는 Vision AI, 그중에서도 로봇 비전·SLAM·내비게이션·자율주행이며, 인지 모델이 실제 시스템 안에서 안정적으로 동작하도록 만드는 데
      집중합니다.
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
      <h3>최근 소식</h3>
      <ul>
        <li><span>2026.06</span> "Hybrid LLM Navigation System for Edge-Cloud Reasoning" 논문이 JKICS(51권 6호)에 게재되었습니다.</li>
        <li><span>2026.03</span> K3I Vision AI Lab에 Vision AI 연구원으로 입사했습니다.</li>
        <li><span>2026.02</span> 금오공과대학교 IT융복합공학 석사과정을 졸업했습니다(WENS 연구실).</li>
        <li><span>2025.12</span> "A MobileViT-Based Detection System for Motorcycle Traffic Violations" 논문이 JKICS(50권 12호)에 게재되었습니다.</li>
        <li><span>2024.05</span> 제2회 대한민국 제2작전사령관배 드론봇 전투경연대회에서 감시정찰 민간부 3위를 수상했습니다.</li>
      </ul>
    </div>
  </div>
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

  }
</style>
