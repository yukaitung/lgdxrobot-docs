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
| base_link_name | string | Custom `base_link` name. |
| publish_tf | bool | Publishing tf information from the robot. |
| reset_transform | bool | Reset robot transform on start up. |
| serial_port_name | string | Serial port name for the LGDXRobot2 or default to /dev/lgdxrobot2. |
| use_cloud | bool | Enable LGDXRobot Cloud integration. |
| use_joy | bool | Control robot using `joy` node. |
{.table}

## Published Topics

| Topic Name        | Message Type                       | Description                       |
|-------------------|------------------------------------|-----------------------------------|
| /agent/imu      | sensor_msgs/Imu                  | IMU data.                         |
| /agent/mag      | sensor_msgs/MagneticField       | Magnetometer data.                |
| /agent/odom     | nav_msgs/Odometry                | Odometry for the robot.           |
| /agent/system  | [lgdxrobot2_msgs/System](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_msgs/msg/System.msg)           | Hardware system information.      |
| /joint_states   | sensor_msgs/JointState           | Robot wheel movement.             |
| /cloud/robot_data | [lgdxrobot2_cloud_msgs/RobotData](https://gitlab.com/lgdxrobotics/lgdxrobot-cloud-adapter/-/blob/main/lgdxrobot_cloud_msgs/msg/RobotData.msg?ref_type=heads)           | Robot data from LGDXRobot Cloud.  |
{.table}

## Subscribed Topics

| Topic Name     | Type                | Description                     |
|----------------|---------------------|---------------------------------|
| /cmd_vel       | geometry_msgs/Twist |                                 |
| /joy           | sensor_msgs/Joy     |                                 |
| /cloud/software_emergency_stop | std_msgs/msg/Bool | Software emergency stop from LGDXRobot Cloud. |
{.table}
