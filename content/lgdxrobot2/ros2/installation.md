---
title: Installation
weight: 2
---

LGDXRobot2 ROS 2 can be installed using package manager. The packages are available for both AMD64 and ARM64 architectures. However, only ROS 2 Jazzy (Ubuntu 24.04) is supported.

## Installation

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. The packages are hosted in a self-hosted repository, install this package to add the repository and the public key.

```bash
wget -q https://ros.bristolgram.uk/lgdxrobot2-apt-source.deb
sudo dpkg -i lgdxrobot2-apt-source.deb
sudo apt update
```

3. Install the packages. This will also install the required dependencies, including the Nav2 stack.

```bash
sudo apt install lgdxrobot2-udev \
  ros-${ROS_DISTRO}-sllidar-ros2 \
  ros-${ROS_DISTRO}-lgdxrobot2* \
  ros-${ROS_DISTRO}-explore-lite \
  ros-${ROS_DISTRO}-multirobot-map-merge
```

Do not install rplidar_ros, as it appears to be out of date.
{.alert .alert-info}

## Installation (.deb Packages)

If adding the repository is not possible, the packages can be installed using the .deb packages.

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. Download following packages from the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/releases) page.

* `SLAMTEC LIDAR ROS 2`
* `M-EXPLORE ROS 2`
* `LGDXRobot2 ROS 2`
* `LGDXRobot2 UDEV (Universal)`

3. Install the packages and dependencies.

```bash
sudo apt install ./*.deb
```

## Customisation

If certain functionality is not required, it can be omitted when installing the packages.

* `lgdxrobot2_navigation`, `explore_lite`, `multirobot_map_merge` \
  Can be omitted if the Nav2 is not required. In the `lgdxrobot2_bringup` package, launch files that include `nav` should not be used.

* `lgdxrobot2_webots` \
  Can be omitted if the Webots simulation is not required. In the `lgdxrobot2_bringup` package, launch files that include `simulation` should not be used.