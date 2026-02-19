---
title: Compiling
weight: 2
---

This tutorial assumes that Ubuntu 24.04 LTS has already been installed.

## Prerequisites

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. Install [Nav2](https://docs.nav2.org/getting_started/index.html)

## Build

Clone the project and run the following commands:

```bash
mkdir -p ~/lgdx_ws/src
cd ~/lgdx_ws/src
git clone --recurse-submodules https://gitlab.com/lgdxrobotics/lgdxrobot-cloud-adapter.git
cd ..

# Install dependencies
rosdep install --from-paths /src --ignore-src -y

# Ensure that lgdxrobot_cloud_msgs is installed
colcon build --packages-select lgdxrobot_cloud_msgs  --symlink-install
source install/setup.bash

colcon build --symlink-install
```
