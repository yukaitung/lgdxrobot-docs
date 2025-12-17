---
title: Installation - APT
weight: 2
---

LGDXRobot2 ROS 2 can be installed using APT. The packages are available for both AMD64 and ARM64 architectures. However, only ROS 2 Jazzy (Ubuntu 24.04) is supported.

## Permission Configuration

The host machine must be configured to allow access to the USB devices used by the robot. The corresponding udev rules are stored in the [udev](http://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/udev?ref_type=heads) folder. Copy the rules to `/etc/udev/rules.d` and reload them using the commands below:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Installation

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. The packages are hosted in a repository managed by LGDXRobotics, so add this repository before installation.

```bash
cd /etc/apt/keyrings
sudo wget -q https://lgdxrobot.bristolgram.uk/keys/lgdxrobotics.asc
sudo echo "deb [signed-by=/etc/apt/keyrings/lgdxrobotics.asc] https://ros.bristolgram.uk/ noble main" | sudo tee /etc/apt/sources.list.d/lgdxrobotics.list
sudo apt update
```

3. Install the packages. This will also install the required dependencies, including the Nav2 stack.

```bash
apt install ros-${ROS_DISTRO}-sllidar-ros2 ros-${ROS_DISTRO}-lgdxrobot2*
```

Do not install rplidar_ros, as it appears to be out of date.
{.alert .alert-info}