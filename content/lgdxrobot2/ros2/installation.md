---
title: Installation
weight: 2
---

LGDXRobot2 ROS 2 can be installed using package manager. The packages are available for both AMD64 and ARM64 architectures. However, only ROS 2 Jazzy (Ubuntu 24.04) is supported.

## Permission Configuration

To allow access to hardware devices without root permissions, the `lgdxrobot2-udev` package needs to be installed. This installation is included in the steps below.

## Installation

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. The packages are hosted in a self-hosted repository, install this package to add the repository and the public key.

```bash
wget -q http://packages.bristolgram.uk/lgdxrobotics-apt-source.deb
sudo dpkg -i lgdxrobotics-apt-source.deb
sudo apt update
```

3. Install the packages. This will also install the required dependencies, including the Nav2 stack.

```bash
sudo apt install lgdxrobot2-udev \
  ros-${ROS_DISTRO}-sllidar-ros2 \
  ros-${ROS_DISTRO}-lgdxrobot2-*
```

4. Optionally, install the simulation package for Webots.

```bash
sudo apt install ros-${ROS_DISTRO}-lgdxrobot2sim-webots
```

Do not install rplidar_ros, as it appears to be out of date.
{.alert .alert-info}