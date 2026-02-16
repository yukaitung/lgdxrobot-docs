---
title: Bringup - Nav2 Webots Simulation
weight: 152
---

The `webots_nav` launch file is used to start the Nav2 stack by initialising the Webots simulation and displaying it in RViz2.

![Screenshot](../img/bringup/sim-img.png)

## Examples

### Robot Only

SLAM on Nav2

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  slam:=True \
  profile:='slam-sim' \
  use_rviz:=True
```

Localisation on Nav2

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  profile:='loc-sim' \
  use_rviz:=True
```

SLAM on other Webots map

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  slam:=True \
  profile:='slam-sim' \
  world:='apartment.wbt' \
  map:='apartment.yaml' \
  use_rviz:=True
```

Localisation on other Webots map

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  profile:='loc-sim' \
  world:='apartment.wbt' \
  map:='apartment.yaml' \
  use_rviz:=True
```

## Parameters

| Parameter        | Type   | Description                                           |
| ---------------- | ------ | ----------------------------------------------------- |
| profiles_path    | string | bsolute path to the profiles directory, or leave empty to use the default. |
| profile          | string | Parameters profile.                                   |
| namespace        | string | Namespace for the robot.                              |
| slam             | bool   | Whether to run a SLAM.                                |
| use_localization | bool   | Whether to enable localization or not.                |
| map              | string | Absolute path to the map YAML file.                   |
| autostart        | bool   | Automatically start up the Nav2 stack.                |
| use_composition  | bool   | Whether to use composed bringup.                      |
| use_respawn      | bool   | Whether to respawn if a node crashes.                 |
| use_rviz         | bool   | Launch RViz2.                                         |
| rviz_config      | string | Absolute path for the RViz config file.               |
| use_lidar        | bool   | Whether to enable the LiDAR.                          |
| lidar_model      | string | RPLIDAR model name.                                   |
| use_camera       | bool   | Whether to enable the camera.                         |
| use_joy          | bool   | Whether to enable the joy.                            |
| use_cloud           | bool   | Whether to enable cloud connectivity.         |
| cloud_address       | string | Address of the LGDXRobot Cloud service.        |
| cloud_root_cert     | string | Path to the server’s root certificate file.   |
| cloud_client_key    | string | Path to the client’s private key file.        |
| cloud_client_cert   | string | Path to the client’s certificate file.        |
{.table}