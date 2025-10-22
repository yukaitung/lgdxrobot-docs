---
title: LGDXRobot2  
description: A flexible DIY Mecanum wheel chassis designed to inspire your enthusiasm on robotics.
homepage: https://lgdxrobot.bristolgram.uk/lgdxrobot2/  
weight: 4
---

LGDXRobot2 is a DIY Mecanum wheel chassis designed for building ROS2 robots using low-cost hardware. It offers complete freedom to customise hardware specifications and aims to inspire your enthusiasm on robotics. It also integrates seamlessly with the [LGDXRobot Cloud](https://lgdxrobot.bristolgram.uk/cloud/).

This documentation covers the process of building the LGDXRobot2 from scratch. The first three sections describe the physical robot, including the chassis, controller board, and chassis tuning.

* [Chassis](chassis)
* [Control Board](mcu)  
* [ChassisTuner](chassistuner)  

The final section covers software integration with ROS 2, including using the robot with NAV2 and the joystick (JOY), as well as simulation configurations in Webots.

* [ROS 2](ros2)

## Links

### Repositories

* Hardware designs for both the chassis and controller board: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-design) [GitHub](https://github.com/yukaitung/lgdxrobot2-design)
* Firmware for the controller board: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-mcu) [GitHub](https://github.com/yukaitung/lgdxrobot2-mcu)
* ChassisTuner: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-chassistuner) [GitHub](https://github.com/yukaitung/lgdxrobot2-chassistuner)
* ROS2 packages: [GitLab](https://gitlab.com/yukaitung/lgdxrobot2-ros2) [GitHub](https://github.com/yukaitung/lgdxrobot2-ros2)

### Docker Images

* [LGDXRobot2](https://hub.docker.com/r/yukaitung/lgdxrobot2)
* [LGDXRobot2 Desktop](https://hub.docker.com/r/yukaitung/lgdxrobot2.desktop)
* [LGDXRobot2 Support Image](https://hub.docker.com/r/yukaitung/lgdxrobot2.support)
* [LGDXRobot2 Desktop Support Image](https://hub.docker.com/r/yukaitung/lgdxrobot2.supportdesktop)
* [LGDXRobot2 Webots](https://hub.docker.com/r/yukaitung/lgdxrobot2.webots)