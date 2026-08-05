---
layout: page
title: Hybrid LLM 내비게이션 시스템
description: Edge-Cloud LLM 라우팅으로 상황을 판단하는 자연어 기반 ROS2 내비게이션.
category: featured
importance: 1
lang: ko
img: assets/img/projects/hybrid-llm-navigation.png
permalink: /projects/hybrid-llm-navigation/
---

## 문제

기존 Nav2는 사람과 박스를 똑같은 기하학적 장애물로 취급합니다. 지날 수 있는 통로도 막힌 것으로 판단해 혼잡한 환경에서 불필요한 정지와 데드락이 급증합니다. 이 연구는 **Edge LLM과 Cloud LLM을 결합한 하이브리드 판단 구조**로 자연어 명령 기반 내비게이션에 의미적 상황 판단을 더했습니다. (석사 학위 연구, WENS 연구실 · [신수용](https://scholar.google.com/citations?user=c8JDiHYAAAAJ) 교수 지도)

## 시스템

![Hybrid LLM 내비게이션 시스템 아키텍처](/assets/img/projects/figs/hybrid-architecture.png)

_전체 시스템 구조 — 자연어 명령·멀티모달 센서 입력이 Edge LLM(Gemma 3) 기반 의미 매칭을 거쳐, LLM 라우터가 τ 점수로 Edge/Cloud를 선택하고 주행 정책을 생성합니다._

**자연어 명령 해석** — "D 구역으로 가", "뒷문으로 이동" 같은 일상 표현을 표현 정규화 → 핵심어 추출 → 사전 정의된 Resource–Zone 정의와의 의미 유사도 계산 → 목표 좌표 변환의 4단계로 처리합니다. 후보가 모호하면 "어느 문으로 갈까요?"처럼 재질문하고, 매칭 점수(0–1)에 따라 실행·확인·거부를 결정합니다.

**비전-LLM 융합** — YOLOv11n으로 person·shelf·box·door를 검출합니다. 실제 카메라 영상 11분 + Gazebo 3분에서 수집한 원본 3,702장을 증강해 14,808장으로 학습(7:2:1 분할, 100 epochs)했고, 테스트셋 **mAP@0.5 96%**를 달성했습니다. 검출 결과는 "전방 1.2 m에 사람 1명" 같은 요약 텍스트로 변환되어 라우터에 전달됩니다.

**하이브리드 LLM 라우터** — LiDAR·비전 기반 안전 상태(HPSS: 최소 인간 거리, 여유 공간 비율)가 승급(Safe→Caution)될 때 이벤트가 발생하고, 라우터는 환경 점수 **τ = wₛS + w꜀C − wₗL** (안전 여유 S, 장면 복잡도 C, 비용/지연 L)를 계산합니다. **Edge 우선 정책**으로 경량 Gemma-3(QAT, Ollama)를 사용하고, 점수가 임계값을 넘는 의미 판단이 필요한 장면에서만 Cloud(GPT-3.5-turbo)를 호출합니다. 출력은 `speed_gain`, `min_person_dist` 두 정책 파라미터로, Nav2 실행 모듈에 적용됩니다.

![LLM 라우터 구조](/assets/img/projects/figs/hybrid-router.png)

_LLM 라우터 — 자연어 목표와 이벤트 입력으로 환경 점수 τ를 계산하고 Local/Cloud 모델을 선택합니다._

플랫폼: TurtleBot3 Burger(LDS LiDAR + USB 웹캠), ROS2 + Gazebo 창고 환경.

## 실험 결과

사람 수 N=1~8의 창고 시뮬레이션에서 목표 3곳 × 3회(레벨당 9회)로 Nav2 · Local-only(Edge) · Hybrid를 비교했습니다. **기존 Nav2는 N=3부터 급락**(N=4에서 3/9, N=5에서 1/9 성공)한 반면, Hybrid는 높은 성공률을 유지했습니다:

| N   | Local 성공 | Hybrid 성공 | Local T<sub>goal</sub> | Hybrid T<sub>goal</sub> | Cloud 호출/9회 |
| --- | ---------- | ----------- | ---------------------- | ----------------------- | -------------- |
| 2   | 9/9        | 9/9         | 21.5 s                 | 20.4 s                  | 2              |
| 4   | 7/9        | 9/9         | 28.7 s                 | 25.0 s                  | 4              |
| 6   | 5/9        | 8/9         | 42.1 s                 | 34.5 s                  | 6              |
| 8   | 2/9        | 6/9         | 59.7 s                 | 47.2 s                  | 8              |

![혼잡도별 성공률 비교](/assets/img/projects/figs/hybrid-success-rate.png)

_혼잡도(N)별 목표 도달 성공률 — Nav2는 급락하는 반면 Hybrid는 완만하게 유지됩니다._

Hybrid는 모든 혼잡도에서 더 큰 최소 인간 거리(0.69–0.75 m)를 유지하면서도 Cloud 호출을 태스크당 소수로 제한했습니다 — 상시 Cloud 추론 없이 Edge의 실시간성과 Cloud의 추론 능력을 결합한 결과입니다.

`ROS2` · `Nav2` · `YOLOv11` · `LiDAR` · `Ollama` · `Gemma 3` · `GPT-3.5` · `Gazebo`

**논문:** Kim, In Gon and Shin, Soo Young, "Hybrid LLM Navigation System for Edge-Cloud Reasoning," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 51, no. 6, pp. 1175–1186, 2026.

**특허:** 자연어 명령과 환경 점수 기반 하이브리드 대규모 언어모델 라우팅을 이용한 이동 로봇 내비게이션 시스템 및 방법 (출원번호 10-2025-0212453) — [특허](/patents/) 페이지 참고.

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
