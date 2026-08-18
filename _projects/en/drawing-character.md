---
layout: page
title: Drawing-Based Interactive Character
description: Auto-recognizing and rigging hand drawings, then applying body motion, facial expressions, and speech.
category: industry
importance: 3
lang: en
img: assets/img/projects/figs/drawing-bvh-flow.gif
permalink: /en/projects/drawing-character/
---

## Overview

- **Period:** Mar 2026 – Jul 2026 (K3I)
- Auto-recognizes and rigs a user's drawing, then applies motion, expressions, and voice to make it a moving character
- Extended from body-motion animation → real-time expression transfer → a talking character

## ① Body-motion Animated Drawing

- **MediaPipe Pose** extracts 33 body joints from the webcam → converted to **BVH motion**
- **AnimatedDrawings** auto-detects the character and joints in the drawing → motion retargeting
- Webcam, Rokoko, and Mixamo motions unified in a BVH library — one motion drives many drawings

![Drawing recognition and rigging flow](/assets/img/projects/figs/drawing-bvh-flow.gif)

_Character detection → joint extraction → BVH motion_

![Motion retargeting](/assets/img/projects/figs/drawing-motion-retarget.gif)

_Simultaneous multi-character retargeting_

## ② Real-time expression transfer — DrawFace Live

- **MediaPipe FaceLandmarker** 478 landmarks → **ARKit 52-channel blendshapes**
- Hand drawings use **ARAP geometric deformation** (original strokes preserved); standard-proportion illustrations use **LivePortrait TensorRT, 27–37 ms (~30 FPS)**
- Runs entirely in the browser — no server, face video never leaves the device

![Expression mirroring](/assets/img/projects/figs/drawing-face-mirror.jpg)

_ARKit 52-channel 3D expression mirroring_

## ③ Talking Drawing Avatar

- Local LLM (**EXAONE 3.5**) judges per-sentence emotion → applied to **edge-TTS** voice tone and facial expression together
- **JoyVASA + LivePortrait** generate speech video (mouth interior pixels generated), fully local
- TensorRT acceleration + fragment streaming + parallel emotion judging → playback start **4.8 s → 2.1 s**

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
