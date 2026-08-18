---
layout: page
title: 사용자 그림 기반 인터랙티브 캐릭터
description: 손그림을 자동 인식해 움직이는 캐릭터로 만들고, 사용자의 몸동작·표정·음성을 실시간으로 입히는 기술.
category: industry
importance: 3
lang: ko
img: assets/img/projects/figs/drawing-bvh-flow.gif
permalink: /projects/drawing-character/
---

## 개요

사용자가 종이에 그린 그림을 AI가 인식해서 **움직이는 캐릭터**로 만들어주는 기술입니다. 여기에 사용자의 몸동작, 얼굴 표정, 목소리까지 그림에 입혀서 — 내가 움직이면 그림이 따라 움직이고, 텍스트를 넣으면 그림이 말을 합니다. (K3I 재직 중 수행)

## ① 내 몸동작대로 움직이는 그림

- **MediaPipe Pose 모델**이 웹캠 영상에서 사람의 관절 33개 위치를 매 프레임 찾아냅니다.
- 이 관절 움직임을 애니메이션 표준 형식(BVH)으로 변환합니다.
- **Meta의 AnimatedDrawings**가 손그림에서 캐릭터 영역과 팔다리 관절을 자동으로 찾아내고, 거기에 변환한 모션을 입힙니다.
- 웹캠으로 찍은 내 동작뿐 아니라 Rokoko·Mixamo의 기성 모션도 같은 형식으로 모아둬서, **어떤 모션이든 어떤 그림에든** 적용할 수 있습니다.

![그림 인식·리깅 흐름](/assets/img/projects/figs/drawing-bvh-flow.gif)

_손그림에서 캐릭터와 관절을 자동으로 찾고, 모션을 입히면 그림이 실제로 움직입니다._

![모션 리타게팅](/assets/img/projects/figs/drawing-motion-retarget.gif)

_사용자가 움직이면 여러 손그림 캐릭터가 동시에 따라 움직입니다._

## ② 내 표정을 따라하는 그림 — DrawFace Live

웹캠 속 내 표정을 3D 캐릭터·2D 캐릭터·손그림이 실시간으로 따라합니다. **전부 브라우저 안에서만 돌아서 서버가 없고, 얼굴 영상이 컴퓨터 밖으로 나가지 않습니다.**

- **MediaPipe 얼굴 모델**이 얼굴에서 478개 지점을 찾아 눈 깜빡임·입 벌림·미소 같은 **표정 수치 52개**로 바꿉니다.
- 이 수치를 3D 캐릭터의 얼굴 근육과 손그림 변형에 그대로 연결합니다.
- 손그림에 신경망을 쓰면 그림체가 뭉개진다는 걸 직접 실험으로 확인해서, 손그림은 **원본 획을 그대로 구부리는 기하 변형(ARAP)** 방식을 썼습니다. 반대로 비율이 정상적인 일러스트는 **LivePortrait 모델(TensorRT 가속, 약 30fps)**로 자연스럽게 움직입니다.

![표정 미러링](/assets/img/projects/figs/drawing-face-mirror.jpg)

_웹캠 표정이 실시간으로 3D 캐릭터에 옮겨지는 모습._

## ③ 말하는 그림 — Talking Drawing Avatar

그림 한 장과 텍스트를 넣으면 **그림이 감정을 담아 말합니다.**

- 로컬 LLM(**EXAONE 3.5**)이 문장마다 감정(기쁨·슬픔 등)을 판단합니다.
- 그 감정이 **목소리 톤(edge-TTS)**과 **얼굴 표정**에 동시에 실립니다.
- **JoyVASA + LivePortrait** 모델이 입이 실제로 벌어지는 발화 영상을 만듭니다. 전 과정이 로컬에서 실행됩니다.
- 병목 구간만 TensorRT로 가속하고, 영상을 만들면서 동시에 재생하는 스트리밍을 적용해 **말 시작까지 걸리는 시간을 4.8초에서 2.1초로** 줄였습니다.

`MediaPipe` · `AnimatedDrawings` · `BVH` · `ARAP` · `WebGL` · `LivePortrait` · `TensorRT` · `JoyVASA` · `EXAONE 3.5` · `edge-TTS` · `FastAPI`

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
