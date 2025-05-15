---
title: MCU / Cloud Integration
weight: 4
---

`lgdxrobot2_daemon` is the core application for integrating MCU to the cloud and ROS2.

## Parameters

### LGDXRobot2 Cloud

`cloud_enable` (bool)

Enable LGDXRobot2 Cloud.

`cloud_address` (string)

Address of LGDXRobot2 Cloud.

`cloud_root_cert` (string)

Path to server root certificate, required in LGDXRobot2 Cloud.

`cloud_client_key` (string)

Path to client key, required in LGDXRobot2 Cloud.

`cloud_client_cert` (string)

Path to client certificate, required in LGDXRobot2 Cloud.

### Serial Port

`serial_port_enable` (bool)

Default serial port name or (Linux only) perform automated search if the this is unspecified.

`serial_port_name` (string)

Serial port name.

`serial_port_reset_transform` (bool)

Reset robot transform on start up.

`serial_port_control_mode` (string)

Robot control mode, using `joy` for joystick or `cmd_vel` for ROS nav stack.

`serial_port_publish_odom` (bool)

Publishing odometry information from the robot.

`serial_port_publish_tf` (bool)

Publishing tf information from the robot.

`serial_port_base_link_name` (string)

Custom `base_link` name.

`serial_port_use_external_imu`

Using external IMU for odometry calcuation.

## Examples

Connecting LGDXRobot2 to joy

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_mcu joy.launch.py
```