---
title: Customisation
weight: 5
---

The firmware for the controller board is aware of the chassis dimensions, so the LGDXRobot2 design is created with flexibility in mind. This page provides details of components that can be changed.

## Chassis

* The chassis dimensions can be changed. The firmware stores these dimensions for calculating inverse kinematics, and they can be modified easily in the source code. Parameters for NAV2 must also be updated to ensure the navigation system recognises the new chassis dimensions.
* The wheel radius can be adjusted. For the default design, the maximum allowed size is 80 mm. Firmware modifications are straightforward, and no changes are required on the ROS side.

## PC / Sensors

* The PC can be any device capable of running ROS 2 or Docker that fits within the area of the PC plate.
* LiDAR can be any model supported by the [sllidar_ros2](https://github.com/Slamtec/sllidar_ros2) package.
* The recommended camera is the Intel RealSense D435 or D435i (if IMU functionality is required). Technically, any USB camera with compatible mounting holes can be used, provided it is not required for navigation.
