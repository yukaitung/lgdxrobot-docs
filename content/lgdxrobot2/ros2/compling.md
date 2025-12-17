---
title: Compling
weight: 4
---

This tutorial assumes that Ubuntu 24.04 LTS has already been installed.

## Prerequisites

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html) ensure that the development tools are installed.

2. Install Packages for LiDAR:
```bash
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
git clone https://github.com/Slamtec/sllidar_ros2.git
cd ..
colcon build --symlink-install
cd src/rpldiar_ros/
source scripts/create_udev_rules.sh
```

Do not install rplidar_ros, as it appears to be out of date.
{.alert .alert-info}

## Build

Clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2
rosdep update
rosdep install --from-paths lgdxrobot2-ros2 --ignore-src -y
cd ..
colcon build --symlink-install
```

## Configuration

First, add the user to the `dialout` group to allow access to the controller board.

```bash
sudo usermod -a -G dialout $USER
```

Then, source the setup files for the ROS 2 workspaces.

```bash
source ~/lgdx_ws/install/setup.bash
source ~/ros2_ws/install/setup.bash
```
