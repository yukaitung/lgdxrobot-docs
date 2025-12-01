---
title: Agent Node
weight: 6
---

`lgdxrobot2_agent_node` is a ROS 2 node that drives the robot using ROS 2 topics and services. It also functions as a client for the LGDXRobot Cloud.

## Parameters

### LGDXRobot2 Cloud Parameters

| Parameter           | Type   | Description                                                       |
|---------------------|--------|-------------------------------------------------------------------|
| cloud_enable        | bool   | Enables connection to the LGDXRobot2 Cloud.                       |
| cloud_address       | string | Address and port number of the LGDXRobot2 Cloud service.          |
| cloud_root_cert     | string | Path to the server's root certificate (required by the cloud).    |
| cloud_client_key    | string | Path to the client’s key file (required by the cloud).            |
| cloud_client_cert   | string | Path to the client’s certificate file (required by the cloud).    |
| cloud_slam_enable   | bool   | Enable LGDXRobot Cloud SLAM Mode.                                 |
{.table}

### Serial Port Parameters

| Parameter              | Type   | Description                                                                                   |
|------------------------|--------|-----------------------------------------------------------------------------------------------|
| mcu_enable             | bool   | Enables the serial connection. If unspecified (Linux only), an automatic search is performed. |
| mcu_port_name         | string | The name of the serial port device.                                                           |
| mcu_reset_transform    | bool   | Resets the robot’s transform on initialisation.                                               |
| mcu_control_mode       | string | Control mode, e.g., `joy` for joystick or `cmd_vel` for ROS navigation stack or `both` for both inputs.                |
| mcu_publish_odom       | bool   | Enables publishing of odometry information.                                                   |
| mcu_publish_tf         | bool   | Enables publishing of `tf` transformation frames.                                             |
| mcu_publish_joint_state | bool   | Enables publishing of JointState messages.
| mcu_base_link_name     | string | Custom name for the `base_link` frame.                                                        |
{.table}


### Simulation

| Parameter    | Type | Description                                                                 |
|--------------|------|-----------------------------------------------------------------------------|
| sim_enable   | bool | Enables simulation for LGDXRobot2 hardware. The MCU must be disabled for this feature. |
{.table}

## Topics
### Published Topics

| Topic Name         | Type                                                                                                  | Description                                             |
|--------------------|-------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| /joint_states        |  sensor_msgs/JointState                                                                                     | Robot wheels movement (MCU required). |
| /agent/odom        | nav_msgs/Odometry                                                                                     | Odometry for the robot (MCU required). |
| /agent/auto_task   | [lgdxrobot2_agent/AutoTask](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_agent/msg/AutoTask.msg)   | Current task of the robot (Cloud required).             |
| /agent/robot_data  | [lgdxrobot2_agent/RobotData](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_agent/msg/RobotData.msg) | Current robot data from sensors.                        |
{.table}

### Subscribed Topics

MCU only:

| Topic Name     | Type                | Description                     |
|----------------|---------------------|---------------------------------|
| /cmd_vel       | geometry_msgs/Twist |                                 |
| /joy           | sensor_msgs/Joy     |                                 |
{.table}

### Services

Cloud only:

| Service Name     | Type                                                                                                   | Description                                               |
|------------------|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| auto_task_next   | [lgdxrobot2_agent/AutoTaskNext](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_agent/srv/AutoTaskNext.srv)   | Commands the robot to proceed to the next step in the task. |
| auto_task_abort  | [lgdxrobot2_agent/AutoTaskAbort](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/blob/main/lgdxrobot2_agent/srv/AutoTaskAbort.srv) | Aborts the current task.                                   |
{.table}
