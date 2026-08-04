---
layout: page
title: Hybrid LLM 내비게이션 시스템
description: 이벤트 기반 상황 추론과 주행 정책 선택을 결합한 ROS2 내비게이션.
category: featured
importance: 1
lang: ko
img: assets/img/projects/hybrid-llm-navigation.png
permalink: /projects/hybrid-llm-navigation/
---

[English](/en/projects/hybrid-llm-navigation/)

## 문제

거리 기반 장애물 회피만으로는 혼잡, 안전거리 감소, 모호한 자연어 명령 같은 상황적 판단을 다루기 어렵습니다. WENS 연구실에서 [신수용](https://scholar.google.com/citations?user=c8JDiHYAAAAJ) 교수님 지도로 수행한 이 석사 연구는 의미적 상황 정보로 기존 Nav2 파이프라인을 보강하는 방법을 탐구했습니다.

## 기여

- YOLO 검출, LiDAR 관측, AMCL 위치추정 신호를 결합하는 이벤트 기반 **LLM 라우터**를 설계했습니다.
- 안전거리, 의미 클래스, 위치 불확실성을 결합한 임계값 점수로 LLM 추론이 필요한 시점을 판단하도록 정의했습니다.
- `nav2_simple_commander`를 통해 자연어 명령을 ROS2 동작으로 연결하고, 모호한 명령은 재질문으로 명확히 하도록 했습니다.
- ROS2 Jazzy와 Gazebo Harmonic 환경에서 주행·회피·혼잡 시나리오를 통합했습니다.

## 평가

1~8명의 혼잡도 시뮬레이션에서 LLM 결합 시스템은 평균 목표 도달 성공률 **82%**를 기록해 Nav2 기본 파이프라인의 **43%**를 크게 앞섰습니다. 이는 학위 논문에 보고된 시뮬레이션 결과이며, 실환경 배포 지표로 해석해서는 안 됩니다.

혼잡도별 상세 지표(목표 도달 시간, 최소 안전거리, 불필요 정지 횟수):

| 혼잡도 | Nav2 T<sub>goal</sub> | Nav2 D<sub>min</sub> | Nav2 정지 | LLM T<sub>goal</sub> | LLM D<sub>min</sub> | LLM 정지 |
| ------ | --------------------- | -------------------- | --------- | -------------------- | ------------------- | -------- |
| 1–2명  | 111 s                 | 0.79 m               | 0.8회     | 121 s                | 0.89 m              | 0.5회    |
| 3명    | 116 s                 | 0.76 m               | 1.4회     | 127 s                | 0.86 m              | 1.0회    |
| 4명    | 121 s                 | 0.73 m               | 2.1회     | 133 s                | 0.84 m              | 1.4회    |
| 5명    | 126 s                 | 0.70 m               | 2.9회     | 139 s                | 0.82 m              | 1.9회    |
| 6명    | 130 s                 | 0.68 m               | 3.6회     | 145 s                | 0.80 m              | 2.4회    |
| 7–8명  | 140 s                 | 0.635 m              | 4.5회     | 155 s                | 0.77 m              | 3.0회    |

LLM 결합 시스템은 모든 혼잡도에서 더 큰 최소 안전거리를 유지하고 불필요한 정지를 줄였으며, 그 대가로 목표 도달 시간이 다소 길어졌습니다.

`ROS2` · `Nav2` · `YOLO` · `LiDAR` · `AMCL` · `LLM` · `Gazebo`

**논문:** Kim, In Gon and Shin, Soo Young, "Hybrid LLM Navigation System for Edge-Cloud Reasoning," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 51, no. 6, pp. 1175–1186, 2026.
