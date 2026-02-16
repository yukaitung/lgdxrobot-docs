---
title: Agent Node
weight: 101
---

`lgdxrobot2_agent_node` is a ROS 2 node that drives the robot using ROS 2 topics and services. 

## Parameters


| Parameter           | Type   | Description                                                       |
|---------------------|--------|-------------------------------------------------------------------|
| serial_port_name | string | Serial port name for the LGDXRobot2 or default to /dev/lgdxrobot2. |
| reset_transform | bool | Reset robot transform on start up. |
| publish_tf | bool | Publishing tf information from the robot. |
| base_link_name | string | Custom `base_link` name. |
| use_joy | bool | Control robot using `joy` node. |
{.table}

## Topics
### Published Topics

| Topic Name        | Message Type                       | Description                       |
|-------------------|------------------------------------|-----------------------------------|
| `/joint_states`   | `sensor_msgs/JointState`           | Robot wheel movement.             |
| `/agent/odom`     | `nav_msgs/Odometry`                | Odometry for the robot.           |
| `/agent/imu`      | `sensor_msgs/Imu`                  | IMU data.                         |
| `/agent/mag`      | `sensor_msgs/MagneticField`        | Magnetometer data.                |
| `/agent/system`   | `lgdxrobot2_msgs/System`            | Hardware system information.      |
{.table}

### Subscribed Topics

MCU only:

| Topic Name     | Type                | Description                     |
|----------------|---------------------|---------------------------------|
| /cmd_vel       | geometry_msgs/Twist |                                 |
| /joy           | sensor_msgs/Joy     |                                 |
{.table}
