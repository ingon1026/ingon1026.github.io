---
layout: page
title: Drawing-Based Interactive Character
description: AI recognizes a hand drawing and turns it into a moving character driven by your body, face, and voice.
category: industry
importance: 3
lang: en
img: assets/img/projects/figs/drawing-bvh-flow.gif
permalink: /en/projects/drawing-character/
---

## Overview

Technology that recognizes a drawing on paper and turns it into a **moving character**. Your body motion, facial expressions, and even your voice are applied to the drawing — when you move, the drawing moves; type text, and the drawing speaks. (Carried out while at K3I.)

## ① A drawing that moves like you

- The **MediaPipe Pose model** finds 33 body joints in every webcam frame.
- Those joint movements are converted into the standard animation format (BVH).
- **Meta's AnimatedDrawings** automatically finds the character and its limbs in the hand drawing, and the converted motion is applied to it.
- Motions recorded from the webcam, plus stock motions from Rokoko and Mixamo, are collected in the same format — so **any motion can drive any drawing**.

![Drawing recognition and rigging flow](/assets/img/projects/figs/drawing-bvh-flow.gif)

_The character and its joints are found automatically in the drawing, and applying motion makes it actually move._

![Motion retargeting](/assets/img/projects/figs/drawing-motion-retarget.gif)

_When the user moves, multiple hand-drawn characters follow at the same time._

## ② A drawing that mirrors your face — DrawFace Live

Characters — a 3D head, 2D characters, and hand drawings — mirror your webcam expressions in real time. **Everything runs inside the browser: no server, and your face video never leaves your device.**

- The **MediaPipe face model** finds 478 points on the face and converts them into **52 expression values** — blink, mouth open, smile, and so on.
- Those values drive the 3D character's facial muscles and the drawing's deformation directly.
- Experiments showed neural networks smear the art style of hand drawings, so hand drawings use **geometric deformation (ARAP) that bends the original strokes as-is**. Normally proportioned illustrations instead use the **LivePortrait model (TensorRT-accelerated, ~30 fps)**.

![Expression mirroring](/assets/img/projects/figs/drawing-face-mirror.jpg)

_Webcam expressions transferred onto the 3D character in real time._

## ③ A drawing that talks — Talking Drawing Avatar

Drop in one drawing and some text, and **the drawing speaks with emotion.**

- A local LLM (**EXAONE 3.5**) judges the emotion of each sentence (joy, sadness, ...).
- That emotion lands in both the **voice tone (edge-TTS)** and the **facial expression** at the same time.
- **JoyVASA + LivePortrait** generate speech video where the mouth actually opens. Everything runs locally.
- Accelerating only the bottleneck with TensorRT and streaming video while it is generated cut the **time until speech starts from 4.8 s to 2.1 s**.

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
