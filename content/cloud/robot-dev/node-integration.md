---
title: Node Integration
weight: 3
---

To integrate any ROS 2 robot with LGDXRobot Cloud, the robot must map the following topics and services. In addition, Nav2 must be installed on the robot.

## Mandatory Topics

LGDXRobot Cloud requires the following information provided by the robot. Change the robot node to map the following topics.

### Published From the Robot

| Topic Name | Type | Description |
| --- | --- | --- |
| /cloud/robot_data | [lgdxrobot_cloud_msgs/RobotData](https://gitlab.com/lgdxrobotics/lgdxrobot-cloud-adapter/-/blob/main/lgdxrobot_cloud_msgs/msg/RobotData.msg) | Robot data sent to the cloud |
{.table}

`RobotData` includes the following fields:

| Field Name | Type | Description |
| --- | --- | --- |
| hardware_emergency_stop_enabled | bool | Indicates whether the robot is in a hardware emergency stop state. |
| batteries_voltage | float32[2] | Battery voltages: [0] for the first battery, [1] for the second battery. |
{.table}

### Subscribed From the Cloud Adapter

| Topic Name | Type | Description |
| --- | --- | --- |
| /cloud/software_emergency_stop | std_msgs/Bool | Enables or disables the software emergency stop to halt robot movement. |
{.table}

## Transform

The LGDXRobot Cloud Adapter requires the transform from the `map` frame to the robot’s `base_link` frame. This transform is usually provided by the Nav2 stack.

## Optional Service

LGDXRobot Cloud can optionally validate the serial number of the robot’s controller board. When `need_mcu_sn` is set to `true`, send the serial number to allow the LGDXRobot Cloud Adapter to initialise the connection.

| Service Name     | Type                                                                                                             | Description                                               |
|------------------|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| /cloud/mcu_sn    | [lgdxrobot_cloud_msgs/McuSn](https://gitlab.com/lgdxrobotics/lgdxrobot-cloud-adapter/-/blob/main/lgdxrobot_cloud_msgs/srv/McuSn.srv) | Validates the serial number of the controller board.     |
{.table}

The `lgdxrobot_cloud_msgs/McuSn` service contains only one field:

| Field Name | Type   | Description                               |
|------------|--------|-------------------------------------------|
| mcu_sn     | string | Serial number of the controller board.   |
{.table}