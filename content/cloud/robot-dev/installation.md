---
title: Installation
weight: 1
---

LGDXRobot2 Cloud Adapter can be installed using package manager. The packages are available for both AMD64 and ARM64 architectures. However, only ROS 2 Jazzy (Ubuntu 24.04) is supported.

## Installation

1. Install [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. Install [Nav2](https://docs.nav2.org/getting_started/index.html)
3. The packages are hosted in a self-hosted repository, install this package to add the repository and the public key.

```bash
wget -q http://packages.bristolgram.uk/lgdxrobotics-apt-source.deb
sudo dpkg -i lgdxrobotics-apt-source.deb
sudo apt update
```

4. Install LGDXRobot Cloud Adapter.

```bash
sudo apt install ros-${ROS_DISTRO}-lgdxrobot-cloud-*
```

