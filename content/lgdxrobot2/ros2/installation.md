---
title: Installation
weight: 2
---

LGDXRobot2 ROS 2 can be installed using package manager. The packages are available for both AMD64 and ARM64 architectures. However, only ROS 2 Jazzy (Ubuntu 24.04) is supported.

## Permission Configuration

The host machine must be configured to allow access to the USB devices used by the robot. The corresponding udev rules are stored in the [udev](http://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/udev?ref_type=heads) folder. Copy the rules to `/etc/udev/rules.d` and reload them using the commands below:

```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Installation

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)

The LGDXRobot2 ROS 2 is not configured to depend on RViz, it can be installed separately if required.
{.alert .alert-info}

2. The packages are hosted in a self-hosted repository, so add this repository before installation.

```bash
cd /etc/apt/keyrings
sudo wget -q https://lgdxrobot.bristolgram.uk/keys/lgdxrobotics.asc
sudo echo "deb [signed-by=/etc/apt/keyrings/lgdxrobotics.asc] https://ros.bristolgram.uk/ noble main" | sudo tee /etc/apt/sources.list.d/lgdxrobotics.list
sudo apt update
```

3. Install the packages. This will also install the required dependencies, including the Nav2 stack.

```bash
ros-${ROS_DISTRO}-sllidar-ros2 ros-${ROS_DISTRO}-lgdxrobot2* ros-${ROS_DISTRO}-explore-lite ros-${ROS_DISTRO}-multirobot-map-merge
```

Do not install rplidar_ros, as it appears to be out of date.
{.alert .alert-info}

## Installation (.deb Packages)

If adding the repository is not possible, the packages can be installed using the .deb packages.

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. Download the `SLAMTEC LIDAR ROS 2`, `M-EXPLORE ROS 2`, `LGDXRobot2 ROS 2` packages from the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/releases) page.
3. Install the packages and dependencies.

```bash
cd <path to .deb files>
sudo apt install ./*.deb
sudo dpkg -i ./*.deb
```

## Customisation

If certain functionality is not required, it can be omitted when installing the packages.

* `lgdxrobot2_navigation`, `explore_lite`, `multirobot_map_merge` \
  Can be omitted if the Nav2 is not required. In the `lgdxrobot2_bringup` package, launch files that include `nav` should not be used.

* `lgdxrobot2_webots` \
  Can be omitted if the Webots simulation is not required. In the `lgdxrobot2_bringup` package, launch files that include `simulation` should not be used.