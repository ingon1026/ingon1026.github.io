---
layout: page
title: Zero-Shot Object Recognition & 3D Pose Estimation
description: A robot perception pipeline that recognizes and tracks any object from a typed name — no retraining — and computes its 3D pose.
category: industry
importance: 1
lang: en
img: assets/img/projects/pose-anything.jpg
permalink: /en/projects/pose-anything/
---

## Problem

For a robot to pick objects off a conveyor, it needs each object's 3D position, size, and orientation. The usual way is to collect photos, label them, and retrain a model every time the object changes (days of work), or to have a CAD model. This project removes that step — **type the object's name, like "thermos" or "book", and it is recognized immediately**. (Carried out while at K3I.)

<video autoplay loop muted playsinline style="display: block; max-width: min(100%, 42rem); margin: 0.6rem auto 0.2rem; border: 1px solid var(--global-divider-color, #e0e0e0); border-radius: 0.5rem">
  <source src="/assets/video/pose-anything-demo.mp4" type="video/mp4" />
</video>

_Live demo — objects named by text are found and tracked while their 3D boxes (position, size, orientation) are computed._

## How it works

- **Recognition uses Meta's SAM3 model.** It finds and cuts out the object named in the text prompt. A new object only needs a new prompt — no training.
- **Speed comes from optical flow.** SAM3 is heavy — run every frame it caps at ~3 FPS. So SAM3 runs only every 5th frame, and lightweight optical flow carries the object in between, reaching **9–13 FPS**.
- **3D pose comes from depth-camera geometry.** RealSense depth pixels are turned into 3D points and a bounding box (position, size, orientation) is fitted — within **±1 cm** of real size for static objects, with the box orientation stabilized so it never flips between frames.
- **Untrusted values are never sent.** A Kalman filter checks each observation; if an object is occluded or the reading looks wrong, pose publishing pauses and resumes under the same ID when the object reappears. The robot never receives a coordinate the system doesn't trust.
- **Connected to robots via ROS2.** Results are published as ROS2 topics for RViz and robot control nodes, and the same pipeline was validated in an Isaac Sim virtual conveyor.

![ROS2 pipeline](/assets/img/projects/figs/pose-pipeline.png)

_Camera frames and text prompts go in; recognition results come out as ROS2 topics._

![Published poses](/assets/img/projects/figs/pose-detections.gif)

_What the robot actually receives — publishing pauses during occlusion and resumes under the same ID._

![Isaac Sim integration](/assets/img/projects/figs/pose-isaac.jpg)

_The same recognition running against a virtual camera in the Isaac Sim conveyor environment built by the XR technology convergence team._

`SAM3` · `ROS2 Jazzy` · `Open3D` · `RealSense D455` · `RGB-D` · `Kalman filter` · `RViz` · `Isaac Sim` · `Docker`

**Code:** [github.com/ingon1026/pose-anything](https://github.com/ingon1026/pose-anything) (MIT) · **Docker:** [hub.docker.com/r/ingon1026/pose-anything](https://hub.docker.com/r/ingon1026/pose-anything)

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
