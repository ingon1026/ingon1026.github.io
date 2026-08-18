---
layout: page
title: 사용자 그림 기반 인터랙티브 캐릭터
description: 손그림을 자동 인식·리깅하고 사용자의 몸동작·표정·음성을 적용하는 인터랙티브 캐릭터 기술.
category: industry
importance: 3
lang: ko
img: assets/img/projects/figs/drawing-bvh-flow.gif
permalink: /projects/drawing-character/
---

## 개요

- **기간:** 2026.03 – 2026.07 (K3I)
- 사용자가 그린 캐릭터를 자동 인식·리깅하고, 모션·표정·음성을 적용해 움직이는 캐릭터로 변환
- 몸동작 애니메이션 → 표정 실시간 전이 → 말하는 캐릭터로 확장

## ① 몸동작 기반 Animated Drawing

- **MediaPipe Pose**로 웹캠에서 33개 신체 관절 추출 → **BVH Motion** 변환
- **AnimatedDrawings**로 손그림의 캐릭터 영역·관절 자동 인식 → 모션 리타게팅
- 웹캠 촬영·Rokoko·Mixamo 모션을 BVH 라이브러리로 통합 — 같은 모션을 여러 그림에 적용

![그림 인식·리깅 흐름](/assets/img/projects/figs/drawing-bvh-flow.gif)

_객체 추출 → 관절 추출 → BVH 모션 결합_

![모션 리타게팅](/assets/img/projects/figs/drawing-motion-retarget.gif)

_다중 캐릭터 동시 리타게팅_

## ② 실시간 표정 전이 — DrawFace Live

- **MediaPipe FaceLandmarker** 478 랜드마크 → **ARKit 52채널 blendshape** 추출
- 손그림은 **ARAP 기하 변형**(원본 획 보존), 표준 비율 일러스트는 **LivePortrait TensorRT 27~37ms (~30 FPS)**
- 전부 브라우저 실행 — 서버 없음, 얼굴 영상 미전송

![표정 미러링](/assets/img/projects/figs/drawing-face-mirror.jpg)

_ARKit 52채널 기반 3D 표정 미러링_

## ③ Talking Drawing Avatar

- 로컬 LLM(**EXAONE 3.5**)이 문장별 감정 판정 → **edge-TTS** 음성 톤과 표정에 동시 반영
- **JoyVASA + LivePortrait**로 발화 영상 생성 (입·이·구강 픽셀 생성), 전 과정 로컬 실행
- TensorRT 가속 + 프래그먼트 스트리밍 + 감정 판정 병렬화 → 재생 시작 **4.8초 → 2.1초**

`MediaPipe` · `AnimatedDrawings` · `BVH` · `ARAP` · `ARKit 52ch` · `WebGL` · `LivePortrait` · `TensorRT` · `JoyVASA` · `EXAONE 3.5` · `edge-TTS` · `FastAPI`

**Code:** [github.com/ingon1026/drawface-live](https://github.com/ingon1026/drawface-live) · [github.com/ingon1026/talking-drawing-avatar](https://github.com/ingon1026/talking-drawing-avatar) · **Demo:** [HF DrawFace Live](https://ingon1-drawface-live.static.hf.space)

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
