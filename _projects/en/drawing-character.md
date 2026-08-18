---
layout: page
title: Drawing-Based Interactive Character
description: Recognizing and rigging hand drawings, then driving them with body motion, facial expressions, and speech in real time.
category: industry
importance: 3
lang: en
img: assets/img/projects/drawing-character.gif
permalink: /en/projects/drawing-character/
---

## Overview

Interactive character technology that turns a user's own drawing into a moving character with Vision AI, then applies the user's body motion, facial expressions, and even text/voice to the drawing. The work grew in three directions: ① body motion → hand-drawing animation, ② real-time facial expression transfer, ③ a talking character. (Carried out while at K3I.)

## ① Body-motion Animated Drawing

MediaPipe Pose extracts **33 body landmarks** per webcam frame, converted into BVH motion and retargeted onto the character skeleton that AnimatedDrawings auto-detects in the hand drawing. User-recorded, Rokoko, Mixamo, and stock motions are unified into a single BVH motion library, so the same motion drives different drawings.

![Drawing recognition and rigging flow](/assets/img/projects/figs/drawing-bvh-flow.png)

_The flow from a hand drawing — automatic character detection and joint extraction — to animation combined with BVH motion._

![Animated drawing result](/assets/img/projects/figs/drawing-animated-result.gif)

_The hand-drawn character actually moving once BVH motion is applied._

![Motion retargeting](/assets/img/projects/figs/drawing-motion-retarget.gif)

_A user's actual movement retargeted onto multiple hand-drawn characters at once._

## ② Real-time expression transfer — DrawFace Live

Webcam expressions transfer in real time onto a 3D head, 2D vector characters, and hand drawings. **Everything runs in the browser — no server, and face video never leaves the device.** MediaPipe FaceLandmarker's 478 landmarks and **ARKit 52-channel blendshapes** are the common language consumed by both the 3D and 2D renderers.

Technology choices were settled by measurement: neural warping (LivePortrait family) smears the art style on hand drawings, so **hand drawings use deterministic ARAP deformation** (preserving original strokes) while **standard-proportion illustrations use LivePortrait TensorRT** (27–37 ms/frame, ~30 FPS).

![Expression mirroring](/assets/img/projects/figs/drawing-face-mirror.jpg)

_Webcam face tracking converted into ARKit 52 channels and mirrored onto the 3D head in real time._

## ③ Talking Drawing Avatar

Drop in one drawing and some text, and the drawing speaks. A local LLM (EXAONE 3.5) judges per-sentence emotion, which lands simultaneously in the voice tone (edge-TTS) and the facial expression, while JoyVASA + LivePortrait generate speech video where the mouth actually opens. Fully local.

| Optimization step                                      | Playback start (4.7 s utterance) |
| ------------------------------------------------------ | -------------------------------- |
| Initial                                                | 4.8 s                            |
| TensorRT (replacing only the warping+spade bottleneck) | 3.3 s                            |
| Fragment streaming                                     | 2.3 s                            |
| Parallelized emotion judging                           | **2.1 s**                        |

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
