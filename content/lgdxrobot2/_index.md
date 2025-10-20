---
title: LGDXRobot2  
description: A flexible DIY Mecanum wheel chassis designed to inspire your enthusiasm on robotics.
homepage: https://lgdxrobot.bristolgram.uk/lgdxrobot2/  
weight: 1
---

LGDXRobot2 is a DIY Mecanum wheel chassis designed for building ROS2 robots using low-cost hardware. It offers complete freedom to customise hardware specifications and aims to inspire your enthusiasm on robotics. It also integrates seamlessly with the [LGDXRobot Cloud](https://lgdxrobot.bristolgram.uk/cloud/).

This tutorial covers how to assemble the robot, configure the firmware, and integrate with ROS 2. To start build the physical robot, following tutorials below:

* [Chassis](chassis)
* [Control Board](mcu)  
* [ChassisTuner](chassistuner)  

The software section covers integration with ROS 2. It includes examples for using the robot with NAV2 and joystick (JOY), as well as simulation configurations in Webots:

* [ROS 2](ros2)

## Links

### Repositories

* Hardware designs for both the chassis and control: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-design) [GitHub](https://github.com/yukaitung/lgdxrobot2-design)
* Firmware for the control board: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-mcu) [GitHub](https://github.com/yukaitung/lgdxrobot2-mcu)
* ChassisTuner: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-chassistuner) [GitHub](https://github.com/yukaitung/lgdxrobot2-chassistuner)
* ROS2 Packages: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-ros2) [GitHub](https://github.com/yukaitung/lgdxrobot2-ros2)

### Docker Images

* [LGDXRobot2](https://hub.docker.com/r/yukaitung/lgdxrobot2)
* [LGDXRobot2 Support Image](https://hub.docker.com/r/yukaitung/lgdxrobot2.support)