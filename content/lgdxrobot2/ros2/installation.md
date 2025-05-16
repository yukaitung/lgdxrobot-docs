---
title: Installation
weight: 2
---

This project is designed for ROS2 Jazzy. Any computer running Ubuntu 24.04 is recommended; however, only x86 PCs (such as Intel NUC) have been tested.

## Prerequisites

1. [Install ROS2](https://docs.ros.org/en/jazzy/Installation.html)
2. [Install NAV2](https://docs.nav2.org/getting_started/index.html)
3. [Install Webots](https://cyberbotics.com/doc/guide/installation-procedure)
4. Install the following packages:

```bash
sudo apt install libprotobuf-dev libgrpc++-dev protobuf-compiler-grpc ros-jazzy-rtabmap-ros ros-jazzy-imu-transformer ros-jazzy-webots-ros
```

## Build

After installing all dependencies, clone the [project](https://gitlab.com/yukaitung/lgdxrobot2-ros2) and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
colcon build
```