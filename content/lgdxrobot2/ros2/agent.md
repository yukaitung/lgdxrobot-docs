---
title: Agent Node
weight: 101
---

`lgdxrobot2_agent_node` integrates LGDXRobot2 hardware into ROS 2. It provides several topics for the Nav2 stack.

## Connection

The `lgdxrobot2_udev` package defines the path of the controller board as `/dev/lgdxrobot2`. The agent node will automatically connect to it. If the connection fails or is lost, the node will attempt to reconnect automatically.

## Parameters

| Parameter           | Type   | Description                                                       |
|---------------------|--------|-------------------------------------------------------------------|
| serial_port_name | string | Serial port name for the LGDXRobot2 or default to /dev/lgdxrobot2. |
| reset_transform | bool | Reset robot transform on start up. |
| publish_tf | bool | Publishing tf information from the robot. |
| base_link_name | string | Custom `base_link` name. |
| use_joy | bool | Control robot using `joy` node. |
{.table}

## Published Topics

| Topic Name        | Message Type                       | Description                       |
|-------------------|------------------------------------|-----------------------------------|
| /joint_states   | sensor_msgs/JointState           | Robot wheel movement.             |
| /agent/odom     | nav_msgs/Odometry                | Odometry for the robot.           |
| /agent/imu      | sensor_msgs/Imu                  | IMU data.                         |
| /agent/mag      | sensor_msgs/MagneticField       | Magnetometer data.                |
| /agent/system  | [lgdxrobot2_msgs/System](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_msgs/msg/System.msg)           | Hardware system information.      |
{.table}

## Subscribed Topics

| Topic Name     | Type                | Description                     |
|----------------|---------------------|---------------------------------|
| /cmd_vel       | geometry_msgs/Twist |                                 |
| /joy           | sensor_msgs/Joy     |                                 |
{.table}
