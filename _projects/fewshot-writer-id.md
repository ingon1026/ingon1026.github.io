---
layout: page
title: 소량 샘플 필적 작성자 식별 (Vision Transformer)
description: 소량의 필적 샘플로 작성자를 식별하는 프로토타입 기반 메타러닝.
category: research
importance: 5
lang: ko
img: assets/img/projects/fewshot-writer-id.png
permalink: /projects/fewshot-writer-id/
---

[English](/en/projects/fewshot-writer-id/)

## 접근

작성자 식별은 보통 사람마다 풍부한 필적 데이터를 전제합니다. 이 개인 사이드 프로젝트는 반대로 소량의 필적 샘플만으로 작성자를 식별하는 few-shot 설정을 다뤘습니다.

- Vision Transformer 백본으로 필적의 전역 특징을 추출했습니다.
- Prototypical Network로 작성자별 스타일 프로토타입을 구성해, 적은 샘플로도 새로운 작성자를 인식할 수 있도록 했습니다.
- 잘못된 예측에 대한 사용자 피드백으로 프로토타입을 갱신해, 적은 데이터로 정확도를 점진적으로 개선했습니다.
- 데이터·학습 파이프라인을 PyTorch로 구축했습니다.

`Vision Transformer` · `meta-learning` · `PyTorch` · `Python`

**발표:** 김인곤, 신수용, "소량의 필적 샘플을 활용한 Vision Transformer 기반 메타러닝 작성자 식별 기법," 한국통신학회 학술대회논문집, pp. 582–583, 2025.

**특허:** 이 방법에 대한 국내 특허 출원은 [특허](/patents/) 페이지에 정리되어 있습니다.
