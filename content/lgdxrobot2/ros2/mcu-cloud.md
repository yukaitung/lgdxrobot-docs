---
title: MCU / Cloud Integration
weight: 4
---

`lgdxrobot2_daemon` is the core application responsible for integrating the LGDXRobot2 MCU with ROS2 and the cloud.

## Parameters

### LGDXRobot2 Cloud Parameters

| Parameter           | Type   | Description                                                       |
|---------------------|--------|-------------------------------------------------------------------|
| cloud_enable        | bool   | Enables connection to the LGDXRobot2 Cloud.                       |
| cloud_address       | string | Address of the LGDXRobot2 Cloud service.                          |
| cloud_root_cert     | string | Path to the server's root certificate (required by the cloud).    |
| cloud_client_key    | string | Path to the client’s key file (required by the cloud).            |
| cloud_client_cert   | string | Path to the client’s certificate file (required by the cloud).    |
{.table}

### Serial Port Parameters

| Parameter                    | Type   | Description                                                                                  |
|------------------------------|--------|----------------------------------------------------------------------------------------------|
| serial_port_enable           | bool   | Enables the serial connection. If unspecified (Linux only), an automatic search is performed. |
| serial_port_name             | string | The name of the serial port device.                                                          |
| serial_port_reset_transform  | bool   | Resets the robot’s transform on initialisation.                                              |
| serial_port_control_mode     | string | Control mode, e.g., `joy` for joystick or `cmd_vel` for ROS navigation stack.               |
| serial_port_publish_odom     | bool   | Enables publishing of odometry information.                                                  |
| serial_port_publish_tf       | bool   | Enables publishing of `tf` transformation frames.                                            |
| serial_port_base_link_name   | string | Custom name for the `base_link` frame.                                                       |
| serial_port_use_external_imu | bool   | Enables the use of an external IMU for odometry calculations.                                |
{.table}

## Examples

To connect LGDXRobot2 using a joystick:

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_mcu joy.launch.py
```