---
title: Installation
weight: 2
---

This project is designed for ROS2 Jazzy, any computer running Ubuntu 24.04 is recommended. However, only x86 PC (Intel NUC) is being tested.

## Prerequisites

1. Install ROS2
2. Install NAV2
3. Install Webots
4. Install following packages

```bash
sudo apt install libprotobuf-dev libgrpc++-dev protobuf-compiler-grpc ros-jazzy-rtabmap-ros ros-jazzy-imu-transformer
```

## Build

After installing all dependencies, clone the project and run:

```bash
mkdir -p ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
colcon build
```