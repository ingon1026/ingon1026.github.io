---
layout: page
title: MobileViT 이륜차 교통 위반 탐지
description: 임베디드 ROS2 플랫폼에서 실시간으로 동작하는 시계열 교통 위반 인식.
category: featured
importance: 2
lang: ko
img: assets/img/projects/mobilevit-traffic-violation.jpg
permalink: /projects/mobilevit-traffic-violation/
---

[English](/en/projects/mobilevit-traffic-violation/)

## 문제

단일 프레임 검출기는 신호 변화나 횡단보도 점유처럼 **시간적 맥락에 의존하는 위반**을 놓치고, 순간적인 검출 실패가 오탐으로 이어집니다. 이 시스템은 도로교통법 기준으로 **신호위반 · 중앙선 침범 · 횡단보도 위반** 세 가지를 정의하고 실시간 탐지합니다.

## 시스템

![시스템 개요](/assets/img/projects/figs/mobilevit-system.png)

_시스템 개요 — 이륜차 블랙박스 영상이 Jetson 보드에서 YOLO 검출 + MobileViT 시계열 분석을 거쳐 위반 판정·기록으로 이어집니다._

- YOLO로 차량, 신호등, 정지선, 횡단보도 등 도로 요소와 이륜차를 검출합니다.
- 검출 객체의 ROI 시퀀스를 구성해 MobileViT로 프레임 간 위치·상태 변화를 시계열 분석합니다 — 예: 적색 신호에서 정지선 통과 여부, 횡단보도 영역의 지속 점유 여부.
- 위반 확률이 신뢰도 임계값을 넘으면 즉시 기록하고, 결과를 JSON·CSV로 저장해 후처리에 활용합니다.
- ROS2 Humble 기반으로 Jetson Orin NX(+ RealSense D435i, Ubuntu 22.04 · JetPack 6)에서 실시간 동작합니다.

## 검증

![실주행 영상 검출 예시](/assets/img/projects/figs/mobilevit-detection.jpg)

_실제 주행 영상에서의 검출 예시 — 신호등·횡단보도 검출과 함께 위반 유형별 카운트가 실시간으로 기록됩니다._

실제 블랙박스 주행 영상 **75분**(도심 30분 + 교외 45분, 주간·야간 포함)으로 평가해 다양한 조건에서 **정확도 90% 이상**을 확인했습니다. MobileViT의 시계열 분석이 순간 미검출을 보완하고, 일시적 이벤트를 걸러 오탐을 줄였습니다.

구미 강소특구육성사업의 이륜차 블랙박스 기반 안전 운행 평가 시스템의 일부로 수행했습니다.

`MobileViT` · `YOLO` · `ROS2 Humble` · `Jetson Orin NX` · `RealSense D435i` · `PyTorch`

**논문:** Kim, In Gon and Shin, Soo Young, "A MobileViT-Based Detection System for Motorcycle Traffic Violations," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 50, no. 12, pp. 1822–1829, 2025.
