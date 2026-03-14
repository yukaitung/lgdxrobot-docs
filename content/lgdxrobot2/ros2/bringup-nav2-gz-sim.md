---
title: Bringup - Nav2 Gazebo Simulation
weight: 153
---

The `gz_nav` launch file is used to start the Nav2 stack by initialising the Gazebo simulation and displaying it in RViz2.

LGDXRobot2 for Gazebo simulation is under development and it is not support LGDXRobot Cloud
{.alert .alert-warning}

![Screenshot](../img/bringup/sim-gz.png)

## Examples

SLAM on Nav2

```bash
ros2 launch lgdxrobot2_bringup gz_nav.launch.py \
  slam:=True \
  profile:='slam-gz' \
  use_rviz:=True
```

Localisation on Nav2

```bash
ros2 launch lgdxrobot2_bringup gz_nav.launch.py \
  profile:='loc-gz' \
  use_rviz:=True
```

SLAM on other Webots map

```bash
ros2 launch lgdxrobot2_bringup gz_nav.launch.py \
  slam:=True \
  profile:='slam-gz' \
  world:='deport.sdf' \
  map:='deport.yaml' \
  use_rviz:=True
```

Localisation on other Webots map

```bash
ros2 launch lgdxrobot2_bringup gz_nav.launch.py \
  profile:='loc-gz' \
  world:='deport.sdf' \
  map:='deport.yaml' \
  use_rviz:=True
```

## Parameters
| Parameter        | Type   | Description                                           |
| ---------------- | ------ | ----------------------------------------------------- |
| profiles_path    | string | bsolute path to the profiles directory, or leave empty to use the default. |
| profile          | string | Parameters profile.                                   |
| namespace        | string | Namespace for the robot.                              |
| world             | string   | World file in `lgdxrobot2sim_gz` package.|
| slam             | bool   | Whether to run a SLAM.                                |
| use_localization | bool   | Whether to enable localization or not.                |
| map              | string | Map yaml file in `lgdxrobot2sim_gz` package.       |
| autostart        | bool   | Automatically start up the Nav2 stack.                |
| use_composition  | bool   | Whether to use composed bringup.                      |
| use_respawn      | bool   | Whether to respawn if a node crashes.                 |
| use_rviz         | bool   | Launch RViz2.                                         |
| rviz_config      | string | Absolute path for the RViz config file.               |
| use_cloud           | bool   | Whether to enable cloud connectivity.         |
| cloud_address       | string | Address of the LGDXRobot Cloud service.        |
| cloud_root_cert     | string | Path to the server’s root certificate file.   |
| cloud_client_key    | string | Path to the client’s private key file.        |
| cloud_client_cert   | string | Path to the client’s certificate file.        |
{.table}