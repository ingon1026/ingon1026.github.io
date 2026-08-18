---
layout: page
title: 사용자 그림 기반 인터랙티브 캐릭터
description: 손그림을 인식·리깅하고 사용자의 몸동작·표정·음성을 실시간으로 입히는 캐릭터 기술.
category: industry
importance: 3
lang: ko
img: assets/img/projects/drawing-character.gif
permalink: /projects/drawing-character/
---

## 개요

사용자가 직접 그린 그림을 Vision AI로 인식해 움직이는 캐릭터로 변환하고, 사용자의 몸동작과 얼굴 표정, 텍스트·음성까지 그림에 적용하는 인터랙티브 캐릭터 기술입니다. ① 몸동작 → 손그림 애니메이션, ② 얼굴 표정 실시간 전이, ③ 말하는 캐릭터의 세 방향으로 확장했습니다. (K3I 재직 중 수행)

## ① 몸동작 기반 Animated Drawing

웹캠 영상에서 MediaPipe Pose로 **33개 신체 관절**을 추출해 BVH Motion으로 변환하고, AnimatedDrawings가 자동 인식한 손그림 캐릭터 골격에 리타게팅합니다. 사용자 촬영 모션·Rokoko·Mixamo·기본 모션을 하나의 BVH 라이브러리로 통합해 같은 모션을 서로 다른 손그림에 적용할 수 있습니다.

![그림 인식·리깅 흐름](/assets/img/projects/figs/drawing-bvh-flow.png)

_손그림에서 캐릭터 영역과 관절을 자동 인식하고, BVH 모션을 결합해 애니메이션을 생성하는 흐름._

![모션이 결합된 손그림](/assets/img/projects/figs/drawing-animated-result.gif)

_BVH 모션이 결합되어 실제로 움직이는 손그림 캐릭터._

![모션 리타게팅](/assets/img/projects/figs/drawing-motion-retarget.gif)

_사용자의 실제 동작이 여러 손그림 캐릭터에 동시에 리타게팅되는 모습._

## ② 얼굴 표정 실시간 전이 — DrawFace Live

웹캠 표정을 3D 헤드·2D 벡터·손그림 캐릭터에 실시간 전이합니다. **전부 브라우저 안에서 동작해 서버가 없고, 얼굴 영상이 기기 밖으로 나가지 않습니다.** MediaPipe FaceLandmarker의 478 랜드마크와 **ARKit 52채널 blendshape**를 공통 언어로 써서 3D·2D 렌더러가 같은 채널을 소비합니다.

기술 선택은 실측으로 갈랐습니다 — 손그림에 신경망 워핑(LivePortrait 계열)을 돌리면 화풍이 뭉개지는 것을 확인하고 **손그림은 ARAP 기하 변형**(원본 획을 보존), **표준 비율 일러스트는 LivePortrait TensorRT**(27–37 ms/frame, 약 30 FPS)로 경로를 분리했습니다.

![표정 미러링](/assets/img/projects/figs/drawing-face-mirror.jpg)

_웹캠 표정 트래킹이 ARKit 52채널로 변환되어 3D 헤드에 실시간 반영되는 모습._

## ③ Talking Drawing Avatar

그림 한 장과 텍스트를 넣으면 그림이 말합니다. 로컬 LLM(EXAONE 3.5)이 문장별 감정을 판정해 음성 톤(edge-TTS)과 표정에 동시에 싣고, JoyVASA + LivePortrait로 입이 실제로 벌어지는 발화 영상을 생성합니다. 전 과정 로컬 실행.

| 최적화 단계                          | 재생 시작 시간 (4.7초 발화 기준) |
| ------------------------------------ | -------------------------------- |
| 초기                                 | 4.8 s                            |
| TensorRT (병목 warping+spade만 교체) | 3.3 s                            |
| 프래그먼트 스트리밍                  | 2.3 s                            |
| 감정 판정 병렬화                     | **2.1 s**                        |

`MediaPipe` · `ARKit 52ch` · `AnimatedDrawings` · `BVH` · `ARAP` · `WebGL` · `LivePortrait` · `TensorRT` · `JoyVASA` · `EXAONE 3.5` · `edge-TTS` · `FastAPI`

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
