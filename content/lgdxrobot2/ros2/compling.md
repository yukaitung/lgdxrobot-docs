---
title: Compling
weight: 3
---

LGDXRobot2 ROS2 has been tested on Ubuntu 24.04 LTS and requires ROS 2 Jazzy.

### Prerequisites

1. [Install ROS2](https://docs.ros.org/en/jazzy/Installation.html)
2. [Install NAV2](https://docs.nav2.org/getting_started/index.html)

```bash
sudo apt install ros-${ROS_DISTRO}-navigation2 ros-${ROS_DISTRO}-nav2-bringup
```

3. [Install Webots](https://cyberbotics.com/doc/guide/installation-procedure) (Optional)
4. [Install Webots ROS2 Interface](https://github.com/cyberbotics/webots_ros2/wiki/Getting-Started)
```bash
mkdir -p webots_ws/src
cd webots_ws/src
git clone --recurse-submodules https://github.com/cyberbotics/webots_ros2.git
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro ${ROS_DISTRO} -y
cd ..
colcon build --symlink-install
```
5. Install the following packages:

```bash
sudo apt install libprotobuf-dev libgrpc++-dev protobuf-compiler-grpc 
```

### Build

After installing all dependencies, clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
colcon build --symlink-install
```