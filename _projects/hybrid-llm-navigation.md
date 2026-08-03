---
layout: page
title: Hybrid LLM Navigation System
description: Event-driven context reasoning and policy selection for ROS2 navigation.
category: featured
importance: 1
img: assets/img/projects/hybrid-llm-navigation.png
permalink: /projects/hybrid-llm-navigation/
---

## Problem

Distance-based obstacle avoidance alone does not capture congestion, reduced safety margins, or ambiguous natural-language commands. This master's research, carried out at WENS Lab under Prof. [Soo Young Shin](https://scholar.google.com/citations?user=c8JDiHYAAAAJ), explored how semantic context can augment a conventional Nav2 pipeline.

## Contribution

- Designed an event-driven **LLM router** that combines YOLO detections, LiDAR observations, and AMCL localization signals.
- Defined a thresholded score using safety distance, semantic class, and localization uncertainty to decide when LLM reasoning is needed.
- Connected natural-language commands to ROS2 actions through `nav2_simple_commander`, including clarification for ambiguous commands.
- Integrated the system in ROS2 Jazzy and Gazebo Harmonic for navigation, avoidance, and congestion scenarios.

## Evaluation

In the documented simulation with crowd sizes from one to eight people, the LLM-assisted system achieved an average goal-arrival success rate of **82%**, compared with **43%** for the Nav2 baseline. These are simulation results reported in the thesis portfolio and should not be interpreted as field-deployment metrics.

Per-crowd-level metrics (goal-arrival time, minimum safe distance, unnecessary stops):

| Crowd level | Nav2 T<sub>goal</sub> | Nav2 D<sub>min</sub> | Nav2 stops | LLM T<sub>goal</sub> | LLM D<sub>min</sub> | LLM stops |
| ----------- | --------------------- | -------------------- | ---------- | -------------------- | ------------------- | --------- |
| 1–2 people  | 111 s                 | 0.79 m               | 0.8        | 121 s                | 0.89 m              | 0.5       |
| 3 people    | 116 s                 | 0.76 m               | 1.4        | 127 s                | 0.86 m              | 1.0       |
| 4 people    | 121 s                 | 0.73 m               | 2.1        | 133 s                | 0.84 m              | 1.4       |
| 5 people    | 126 s                 | 0.70 m               | 2.9        | 139 s                | 0.82 m              | 1.9       |
| 6 people    | 130 s                 | 0.68 m               | 3.6        | 145 s                | 0.80 m              | 2.4       |
| 7–8 people  | 140 s                 | 0.635 m              | 4.5        | 155 s                | 0.77 m              | 3.0       |

The LLM-assisted system maintained larger minimum safe distances and made fewer unnecessary stops across all crowd levels, at the cost of moderately longer goal-arrival times.

`ROS2` · `Nav2` · `YOLO` · `LiDAR` · `AMCL` · `LLM` · `Gazebo`

**Publication:** Kim, In Gon and Shin, Soo Young, "Hybrid LLM Navigation System for Edge-Cloud Reasoning," _The Journal of Korean Institute of Communications and Information Sciences_ (JKICS), vol. 51, no. 6, pp. 1175–1186, 2026.
