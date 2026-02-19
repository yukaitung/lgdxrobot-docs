---
title: Compling
weight: 5
---

This tutorial assumes that Ubuntu 24.04 LTS has already been installed.

## Prerequisites

Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html) ensure that the development tools are installed.

## Build

Clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2.git
cd ..

# Remove Cloud Adapter
rm -rf ~/lgdx_ws/src/lgdxrobot2-ros2/third_party/cloud/lgdxrobot2_cloud_adapter
rm -rf ~/lgdx_ws/src/lgdxrobot2-ros2/third_party/cloud/third_party

# Install build dependencies
rosdep update
rosdep install --from-paths src --ignore-src -y

# Ensure that lgdxrobot2_msgs is in the system
colcon build --packages-select lgdxrobot2_msgs --symlink-install
colcon build --packages-select lgdxrobot_cloud_msgs --symlink-install
source install/setup.bash

colcon build --symlink-install
```

## Configuration

First, configure the permissions for the hardwares.

```bash
source  ~/lgdx_ws/src/lgdxrobot2-ros2/third_party/lidar/scripts/create_udev_rules.sh
sudo usermod -a -G dialout $USER
```

Then, source the setup files for the ROS 2 workspaces.

```bash
source ~/lgdx_ws/install/setup.bash
```
