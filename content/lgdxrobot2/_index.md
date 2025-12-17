---
title: LGDXRobot2  
description: A flexible DIY Mecanum wheel mobile robot designed to inspire your enthusiasm on robotics.
homepage: https://lgdxrobot.bristolgram.uk/lgdxrobot2/  
weight: 1
---

LGDXRobot2 is a DIY Mecanum wheel mobile robot designed for building ROS 2-based robots using low-cost hardware with decent performance. It offers the freedom to customise hardware specifications and aims to inspire your enthusiasm for robotics. It also integrates seamlessly with the [LGDXRobot Cloud](https://lgdxrobot.bristolgram.uk/cloud/).

LGDXRobot2 is not designed for beginners and requires some knowledge of robotics.
{.alert .alert-info}

To begin, this section provides an overview of the project:

* [Getting Started](getting-started)

The sections below outline the process of building LGDXRobot2 from scratch and testing its hardware:

* [Chassis](chassis)
* [Control Board (MCU)](mcu)  
* [ChassisTuner](chassistuner)  

The final section covers software integration with ROS 2, including teleoperation, navigation and simulation.

* [ROS 2](ros2)

## Links

[Project Website](https://lgdxrobot.bristolgram.uk/lgdxrobot2/)

### Repositories

| Project | Description | GitLab | GitHub |
|--------|-------------|--------|--------|
| LGDXRobot2 Design | Design files for the chassis and controller board | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-design) | [GitHub](https://github.com/yukaitung/lgdxrobot2-design) |
| LGDXRobot2 MCU | Firmware for the controller board | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu) | [GitHub](https://github.com/yukaitung/lgdxrobot2-mcu) |
| LGDXRobot2 ChassisTuner | Software for tuning the chassis | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner) | [GitHub](https://github.com/yukaitung/lgdxrobot2-chassistuner) |
| LGDXRobot2 ROS 2 | ROS 2 packages for LGDXRobot2 | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2) | [GitHub](https://github.com/yukaitung/lgdxrobot2-ros2) |
{.table}

### Docker Images

| Project | Description | Docker Hub |
|---------|-------------|------------|
| LGDXRobot2 Base | ROS image for command-line use | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-base) |
| LGDXRobot2 Desktop | ROS image with GUI and ChassisTuner included | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-desktop) |
| LGDXRobot2 ChassusTuner Build Image | Toolchain image for building the ChassisTuner | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-chassistuner-build) |
{.table}