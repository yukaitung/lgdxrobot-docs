---
title: Customisation
weight: 5
---

The firmware for the controller board is aware of the chassis dimensions, so the LGDXRobot2 design is created with flexibility in mind. This page provides details of components that can be changed.

## Chassis

The firmware uses the parameters from the `Inc/configuration.h` file to calculate inverse kinematics and PID. These values can be modified to adapt the chassis to different configurations.

### Dimensions

* If the size change affects the distance between the centre of the chassis and the centre of the wheels, the `CHASSIS_LX` and `CHASSIS_LY` parameters in the controller board firmware must be updated.
* NAV2 parameters, including `footprint` and `robot_radius`, must be updated to ensure the navigation system recognises the new chassis dimensions.

### Wheel Radius

* The wheel radius can be adjusted. For the default design, the maximum allowed size is 80 mm.
* In the controller board firmware, the `WHEEL_RADIUS` parameter must be updated.
* No NAV2 parameters need to be updated.

### Motors

* The recommended gear ratio is at least 1:90.
* In the controller board firmware, the `MOTOR_GEAR_RATIO` parameter must be updated. If the encoder counts per revolution differ, the `ENCODER_PPR` parameter must also be updated.

## Computer / Sensors

* The computer can be any device capable of running ROS 2 or Docker that fits within the space of the PC plate.
* The LiDAR can be any model supported by the [sllidar_ros2](https://github.com/Slamtec/sllidar_ros2) package.
* The recommended camera is the Intel RealSense D435 or D435i (if IMU functionality is required). Technically, any USB camera with compatible mounting holes can be used, provided it is not required for navigation.
