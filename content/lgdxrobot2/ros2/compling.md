---
title: Compling
weight: 3
---

This tutorial assumes that you have already installed Ubuntu 24.04 LTS.

## Prerequisites

1. [Install ROS2](https://docs.ros.org/en/jazzy/Installation.html)
2. [Install NAV2](https://docs.nav2.org/getting_started/index.html)

```bash
sudo apt install ros-jazzy-navigation2 ros-jazzy-nav2-bringup ros-jazzy-nav2-route
```

3. Install the dependencies:

```bash
sudo apt install ros-jazzy-joy libprotobuf-dev libgrpc++-dev protobuf-compiler-grpc 
```

4. Install Packages for LiDAR:
```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
git clone https://github.com/Slamtec/sllidar_ros2.git
cd ..
colcon build --symlink-install
cd src/rpldiar_ros/
source scripts/create_udev_rules.sh
```

5. Install Packages for Realsense (Optional):

```bash
sudo apt install ros-jazzy-imu-filter-madgwick ros-jazzy-librealsense2* ros-jazzy-realsense2-*
```

6. [Install Webots](https://cyberbotics.com/doc/guide/installation-procedure) (Optional)
7. [Install Webots ROS2 Interface](https://github.com/cyberbotics/webots_ros2/wiki/Getting-Started) (Optional)
```bash
mkdir -p ~/webots_ws/src
cd ~/webots_ws/src
git clone --recurse-submodules https://github.com/cyberbotics/webots_ros2.git
rosdep update
rosdep install --from-paths src --ignore-src --rosdistro jazzy -y
cd ..
colcon build --symlink-install
```

## Build

After installing all dependencies, clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
source "~/webots_ws/install/setup.bash
colcon build --symlink-install
```

If you are not using Webots:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/yukaitung/lgdxrobot2-ros2
cd ..
colcon build --symlink-install --packages-ignore lgdxrobot2_webots
```

## Configuration

```bash
sudo usermod -a -G dialout $USER # Add user to dialout group
source ~/lgdx_ws/install/setup.bash
source ~/ros2_ws/install/setup.bash
source ~/webots_ws/install/setup.bash # Optional without Webots
```