---
layout: page
title: LLM 기반 딸기 품질 자동 판별
description: 스마트팜을 위한 세그멘테이션, 정량 영상 분석, 검색, 자연어 리포트.
category: research
importance: 4
lang: ko
img: assets/img/projects/strawberry-quality.png
permalink: /projects/strawberry-quality/
---

[English](/en/projects/strawberry-quality/)

## 문제

기존 품질 판별은 단순 이미지 분류나 이진 판단에 머물러, 수확 기준·병해 진단 지침 같은 **세부 해석**을 제공하지 못합니다. 품종·환경에 따라 기준이 달라질 수 있어 고정된 분류기로는 유연한 대응이 어렵다는 한계도 있습니다.

## 접근

![시스템 구성](/assets/img/projects/figs/strawberry-system.png)

_시스템 구성 — YOLOv11-seg 세그멘테이션 → OpenCV 정량 분석 → RAG 문서 검색 → LLM 해석·리포트 생성으로 이어지는 파이프라인._

- YOLOv11-seg로 딸기를 개체 단위로 분리해 분석 대상을 추출했습니다.
- OpenCV 영상처리로 **익음 정도(색상), 크기, 병해 의심 요소**를 정량화했습니다.
- 측정값을 자연어 프롬프트로 변환해 RAG(검색 증강 생성) 구조로 품질 기준·병해 지침 문서를 검색했습니다.
- LLM이 문서 기반 정보를 해석해 **수확 가능 여부와 권고사항**을 자연어 리포트로 생성합니다.

고정된 이진 분류기를 넘어, 품질 기준이 달라져도 문서만 바꾸면 적응할 수 있는 **문서 기반 해석**을 제공하는 것이 목표였습니다.

`YOLOv11-seg` · `OpenCV` · `RAG` · `LLM` · `PyTorch` · `Python`

**발표:** 김인곤, 신수용, "스마트팜 환경을 위한 LLM 기반 딸기 품질 자동 판별 시스템," 제35회 통신정보 합동학술대회 (JCCI 2025), 2025.

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
