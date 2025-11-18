---
title: LGDXRobot2  
description: A flexible DIY Mecanum wheel chassis designed to inspire your enthusiasm on robotics.
homepage: https://lgdxrobot.bristolgram.uk/lgdxrobot2/  
weight: 1
---

LGDXRobot2 is a DIY Mecanum wheel chassis designed for building ROS2 robots using low-cost hardware. It offers complete freedom to customise hardware specifications and aims to inspire your enthusiasm on robotics. It also integrates seamlessly with the [LGDXRobot Cloud](https://lgdxrobot.bristolgram.uk/cloud/).

LGDXRobot2 is not designed for beginners and requires some knowledge of robotics.
{.alert .alert-info}

This documentation covers the process of building the LGDXRobot2 from scratch. The first three sections describe the physical robot, including the chassis, controller board, and chassis tuning.

* [Chassis](chassis)
* [Control Board](mcu)  
* [ChassisTuner](chassistuner)  

The final section covers software integration with ROS2, including using the robot with NAV2 and the joystick (JOY), as well as simulation in Webots.

* [ROS2](ros2)

## Links

### Repositories

| Project | Description | GitLab | GitHub |
|--------|-------------|--------|--------|
| LGDXRobot2 Design | Design files for the chassis and controller board | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-design) | [GitHub](https://github.com/yukaitung/lgdxrobot2-design) |
| LGDXRobot2 MCU | Firmware for the controller board | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu) | [GitHub](https://github.com/yukaitung/lgdxrobot2-mcu) |
| LGDXRobot2 ChassisTuner | Software for tuning the chassis | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner) | [GitHub](https://github.com/yukaitung/lgdxrobot2-chassistuner) |
| LGDXRobot2 ROS2 | ROS2 packages for LGDXRobot2 | [GitLab](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2) | [GitHub](https://github.com/yukaitung/lgdxrobot2-ros2) |
{.table}

### Docker Images

| Project | Description | Docker Hub |
|---------|-------------|------------|
| LGDXRobot2 Core | ROS image for command-line use | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-core) |
| LGDXRobot2 Desktop | ROS image with GUI and ChassisTuner included | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-desktop) |
| LGDXRobot2 Support Image | Base image for ROS builds | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-support-core) |
| LGDXRobot2 Desktop Support Image | Base image for GUI-enabled ROS builds | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-support-desktop) |
| LGDXRobot2 ChassusTuner Build Image | Toolchain image for building the ChassisTuner | [Docker](https://hub.docker.com/r/yukaitung/lgdxrobot2-chassistuner-build) |
{.table}