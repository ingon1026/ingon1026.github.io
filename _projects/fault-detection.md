---
layout: page
title: 딥러닝 기반 카메라 Fault Detection
description: 드론 주행 중 카메라 노이즈·환경 이상을 탐지하고 제거.
category: research
importance: 6
lang: ko
img: assets/img/projects/fault-detection.png
permalink: /projects/fault-detection/
---

## 문제

비행 중인 드론의 카메라는 노이즈와 외부 환경 요인에 노출되어 하위 인지 성능이 저하됩니다. 이 프로젝트는 운용 중 이런 이상을 탐지하고 해당 프레임을 정제했습니다.

## 기여

- OpenCV 기반 분석으로 카메라 노이즈를 탐지했습니다.
- 탐지된 프레임을 딥러닝 모델에 전달해 노이즈를 제거했습니다.
- 오픈소스 검출 모델에서 시작해, 메모리 제약에 맞추기 위해 zero-shot 검출 방식으로 전환했습니다.

`ROS2` · `OpenCV` · `PyTorch` · `Python`
