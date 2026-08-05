---
layout: page
title: Hybrid LLM Navigation System
description: Natural-language ROS2 navigation with edge-cloud LLM routing for context reasoning.
category: featured
importance: 1
lang: en
img: assets/img/projects/hybrid-llm-navigation.png
permalink: /en/projects/hybrid-llm-navigation/
---

[한국어](/projects/hybrid-llm-navigation/)

## Problem

Standard Nav2 treats humans and boxes as identical geometric obstacles, so it refuses traversable passages and suffers unnecessary stops and deadlocks as scenes get crowded. This master's research adds semantic reasoning to natural-language navigation through a **hybrid decision architecture combining an Edge LLM and a Cloud LLM** (WENS Lab, advised by Prof. [Soo Young Shin](https://scholar.google.com/citations?user=c8JDiHYAAAAJ)).

## System

**Natural-language command interpretation** — everyday commands such as "Go to zone D" or "Move to the back door" are processed in four steps: expression normalization → key-term extraction → semantic similarity against predefined Resource–Zone definitions → goal-coordinate selection. Ambiguous candidates trigger clarification ("Which door would you like to move to?"), and a 0–1 matching score decides execution, confirmation, or rejection.

**Vision–LLM fusion** — a YOLOv11n detector recognizes person, shelf, box, and door. From 11 minutes of real camera footage plus 3 minutes of Gazebo frames, 3,702 original images were augmented to 14,808 training samples (7:2:1 split, 100 epochs), reaching **96% mAP@0.5** on the test set. Detections are summarized into short texts such as "1 person at 1.2 m ahead" for the router.

**Hybrid LLM router** — LiDAR- and vision-based safety states (HPSS: minimum human distance, free-space ratio) generate events on escalation (Safe → Caution), and the router computes an environment score **τ = wₛS + w꜀C − wₗL** (safety margin S, scene complexity C, cost/latency L). Following an **edge-first policy**, a lightweight Gemma-3 (QAT, via Ollama) handles most scenes, and the Cloud model (GPT-3.5-turbo) is invoked only when the score crosses a threshold in scenes that require semantic judgment. The selected model outputs two policy parameters, `speed_gain` and `min_person_dist`, applied through Nav2.

Platform: TurtleBot3 Burger (LDS LiDAR + USB webcam), ROS2 + Gazebo warehouse environment.

## Results

With crowd levels N=1–8 (three goals × three runs = 9 trials per level), Conventional Nav2, Local-only (Edge), and Hybrid were compared. **Nav2 collapses from N=3** (3/9 at N=4, 1/9 at N=5), while Hybrid stays high:

| N   | Local succ. | Hybrid succ. | Local T<sub>goal</sub> | Hybrid T<sub>goal</sub> | Cloud calls/9 |
| --- | ----------- | ------------ | ---------------------- | ----------------------- | ------------- |
| 2   | 9/9         | 9/9          | 21.5 s                 | 20.4 s                  | 2             |
| 4   | 7/9         | 9/9          | 28.7 s                 | 25.0 s                  | 4             |
| 6   | 5/9         | 8/9          | 42.1 s                 | 34.5 s                  | 6             |
| 8   | 2/9         | 6/9          | 59.7 s                 | 47.2 s                  | 8             |

Hybrid also maintained larger minimum human distances (0.69–0.75 m) across all crowd levels while keeping Cloud invocations to a handful per task — combining edge responsiveness with cloud-level reasoning without continuous cloud inference.

`ROS2` · `Nav2` · `YOLOv11` · `LiDAR` · `Ollama` · `Gemma 3` · `GPT-3.5` · `Gazebo`

**Publication:** Kim, In Gon and Shin, Soo Young, "Hybrid LLM Navigation System for Edge-Cloud Reasoning," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 51, no. 6, pp. 1175–1186, 2026.

**Patent:** Mobile Robot Navigation System and Method Using Hybrid LLM Routing Based on Natural-Language Commands and Environment Scores (application no. 10-2025-0212453) — see [Patents](/en/patents/).
