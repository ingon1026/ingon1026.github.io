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

## 접근

- YOLOv11-seg로 딸기를 개체 단위로 세그멘테이션했습니다.
- OpenCV로 숙도, 크기, 병해 가능성 지표를 정량화했습니다.
- 검색 증강 생성(RAG) 파이프라인으로 측정값을 품질·병해 가이드 문서와 연결했습니다.
- LLM으로 수확 적기와 권장 조치에 대한 자연어 평가를 생성했습니다.

고정된 이진 분류기를 넘어, 품질 기준이 달라져도 적응할 수 있는 문서 기반 해석을 제공하는 것이 목표였습니다.

`YOLOv11-seg` · `OpenCV` · `RAG` · `LLM` · `PyTorch` · `Python`

**발표:** 제35회 통신정보 합동학술대회(JCCI). 저자 순서, 연도, 페이지, 공개 논문 링크는 확인 후 게시 예정(**TODO**).
