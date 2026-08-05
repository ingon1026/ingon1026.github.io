---
layout: page
title: ROS2 UGV Platform Integration
description: Sensor, communication, SLAM, and navigation integration for an unmanned ground vehicle.
category: featured
importance: 3
lang: en
img: assets/img/projects/ros2-ugv.jpg
permalink: /en/projects/ros2-ugv/
---

## Scope

In the laboratory's **multi-UXV team project**, I owned the UGV (unmanned ground vehicle) part — from platform setup to the autonomous-driving pipeline. The UGV also serves as a mobile charging station linked to the UAV swarm.

![Multi-UXV system overview](/assets/img/projects/figs/ugv-multi-uxv.png)

_Multi-UXV system overview — a UAV swarm (3D LiDAR, RGB-D) works with the ground UGV mobile charging station. I was responsible for building the UGV platform._

## Contribution

- Set up the UGV platform and driving environment in ROS2.
- Integrated CAN communication, the robot SDK, an Ouster LiDAR, an Intel RealSense D435i camera, and IMU sensing.
- Containerized sensor drivers and the driving stack with Docker for a reproducible setup.
- Configured SLAM and navigation workflows, and documented setup and integration guides for the team.

![SLAM mapping in RViz](/assets/img/projects/figs/ugv-slam-rviz.png)

_LiDAR point-cloud SLAM mapping in RViz — map, point cloud, and odometry visualized in real time._

`ROS2` · `ROS1` · `SLAM` · `Ouster LiDAR` · `RealSense D435i` · `CAN` · `Docker` · `Python` · `C++`

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
