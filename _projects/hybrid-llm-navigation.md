---
layout: page
title: Hybrid LLM Navigation System
description: Event-driven context reasoning and policy selection for ROS2 navigation.
category: featured
importance: 1
permalink: /projects/hybrid-llm-navigation/
---

## Problem

Distance-based obstacle avoidance alone does not capture congestion, reduced safety margins, or ambiguous natural-language commands. This master's research explored how semantic context can augment a conventional Nav2 pipeline.

## Contribution

- Designed an event-driven **LLM router** that combines YOLO detections, LiDAR observations, and AMCL localization signals.
- Defined a thresholded score using safety distance, semantic class, and localization uncertainty to decide when LLM reasoning is needed.
- Connected natural-language commands to ROS2 actions through `nav2_simple_commander`, including clarification for ambiguous commands.
- Integrated the system in ROS2 Jazzy and Gazebo Harmonic for navigation, avoidance, and congestion scenarios.

## Evaluation

In the documented simulation with crowd sizes from one to eight people, the LLM-assisted system achieved an average goal-arrival success rate of **82%**, compared with **43%** for the Nav2 baseline. These are simulation results reported in the thesis portfolio and should not be interpreted as field-deployment metrics.

`ROS2` · `Nav2` · `YOLO` · `LiDAR` · `AMCL` · `LLM` · `Gazebo`

**TODO:** Add the final thesis title, advisor, repository, paper, and demonstration video after confirming public-release permission.
