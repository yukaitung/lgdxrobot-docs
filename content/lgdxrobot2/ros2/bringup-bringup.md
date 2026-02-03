---
title: Bringup - Bringup
weight: 102
---

The `bringup` launch file is used to start the robot with all required hardware, the joy node, and display it in the RViz2 GUI.

![Image of the bringup](../img/bringup/bringup.png)

## Examples

```bash
ros2 launch lgdxrobot2_bringup bringup.launch.py \
  use_rviz:=True
```

Using other LiDAR models (default is C1)

```bash
ros2 launch lgdxrobot2_bringup bringup.launch.py \
  lidar_model:='a1' \
  use_rviz:=True
```

Launch with joystick control only

```bash
ros2 launch lgdxrobot2_bringup bringup.launch.py \
  use_lidar:=False \
  use_rviz:=True
```

## Parameters

| Parameter        | Type   | Description                              |
| ---------------- | ------ | ---------------------------------------- |
| serial_port_name | string | Absolute path to the serial port device. |
| use_joy          | bool   | Whether to enable the joy.               |
| use_lidar        | bool   | Whether to enable the LiDAR.             |
| lidar_model      | string | RPLIDAR model name.                      |
| use_rviz         | bool   | Visualize in RViz.                       |
{.table}

## Mapping For Xbox Controller

| Button | Function                                  |
|------------------------|------------------------------------------|
| A                      | Disable software emergency stop          |
| B                      | Enable software emergency stop           |
| D-pad                  | Move the robot                            |
| LSB                    | Move the robot                            |
| LB                     | Reduce robot speed                        |
| RB                     | Increase robot speed                      |
| LT                     | Rotate the robot counter-clockwise        |
| RT                     | Rotate the robot clockwise                |
{.table}