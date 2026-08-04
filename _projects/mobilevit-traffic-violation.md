---
layout: page
title: MobileViT 이륜차 교통 위반 탐지
description: 임베디드 ROS2 플랫폼에서 동작하는 시계열 교통 이벤트 인식.
category: featured
importance: 2
lang: ko
img: assets/img/projects/mobilevit-traffic-violation.jpg
permalink: /projects/mobilevit-traffic-violation/
---

[English](/en/projects/mobilevit-traffic-violation/)

## 문제

단일 프레임 검출기는 신호 변화나 횡단보도 점유처럼 시간적 맥락에 의존하는 교통 위반을 놓칠 수 있습니다. 순간적인 검출 실패는 피할 수 있는 오탐도 만들어냅니다.

## 기여

- YOLO로 신호등, 차선, 횡단보도, 차량을 검출했습니다.
- 시계열 ROI 시퀀스를 구성하고 MobileViT로 상태 변화와 움직임 패턴을 분석했습니다.
- 추론 파이프라인을 ROS2와 통합하고 Jetson Orin NX에 배포해 실시간으로 동작시켰습니다.

이 작업은 구미 강소특구육성사업의 이륜차 블랙박스 영상 기반 안전 운행 평가 시스템의 일부로 수행했습니다.

`MobileViT` · `YOLO` · `ROS2` · `Jetson Orin NX` · `PyTorch` · `Python`

**논문:** Kim, In Gon and Shin, Soo Young, "A MobileViT-Based Detection System for Motorcycle Traffic Violations," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 50, no. 12, pp. 1822–1829, 2025.
