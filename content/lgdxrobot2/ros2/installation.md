---
title: Installation
weight: 2
---

## Docker Installation

Docker images support both AMD64 and ARM64 architectures and it is suitable for simulation.

```bash
docker run -it --name lgdxrobot2 yukaitung/lgdxrobot2:latest
```

## Tradtional Installation

It is recommanded to use Ubuntu 24.04 LTS on an AMD64 computer.

### Prerequisites

1. [Install ROS2](https://docs.ros.org/en/jazzy/Installation.html)
2. [Install NAV2](https://docs.nav2.org/getting_started/index.html)

```bash
sudo apt install ros-jazzy-navigation2
sudo apt install ros-jazzy-nav2-bringup
```

3. [Install Webots](https://cyberbotics.com/doc/guide/installation-procedure)
4. [Install Webots ROS2 Interface](https://github.com/cyberbotics/webots_ros2/wiki/Getting-Started)
5. Install the following packages:

```bash
sudo apt install libprotobuf-dev libgrpc++-dev protobuf-compiler-grpc 
sudo apt install ros-jazzy-rtabmap-ros ros-jazzy-imu-transformer # Optional for physical robot
```

### Build

After installing all dependencies, clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
colcon build
```
