---
title: Bringup - Nav2 Webots Simulation
weight: 152
---

The `webots_nav` launch file is used to start the Nav2 stack by initialising the Webots simulation and displaying it in RViz2.

![Screenshot](../img/bringup/sim-img.png)

## Examples

SLAM on Nav2

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  slam:=True \
  profile:='slam-wb' \
  use_rviz:=True
```

Localisation on Nav2

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  profile:='loc-wb' \
  use_rviz:=True
```

SLAM on other Webots map

List of available maps can be found [here](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/lgdxrobot2sim_webots/worlds).

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  slam:=True \
  profile:='slam-wb' \
  world:='apartment.wbt' \
  map:='apartment.yaml' \
  use_rviz:=True
```

Localisation on other Webots map

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  profile:='loc-wb' \
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
| world             | string   | World file in `lgdxrobot2sim_webots` package.|
| slam             | bool   | Whether to run a SLAM.                                |
| use_localization | bool   | Whether to enable localization or not.                |
| map              | string | Map yaml file in `lgdxrobot2sim_webots` package.       |
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