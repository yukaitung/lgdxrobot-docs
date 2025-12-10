---
title: Bringup - NAV2 Simulation
weight: 9
---

The `simulation_nav` launch file is used to start the NAV2 stack by initialising the Webots simulation and displaying it in RViz2.

![Screenshot](../img/bringup/nav2-sim.png)

## Examples

SLAM on NAV2

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py slam:=True profile:='slam-sim'
```

Localisation on NAV2

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py profile:='loc-sim' 
```

SLAM on other map

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py slam:=True profile:='slam-sim' world:='apartment.wbt' map:='apartment.yaml'
```

Localisation on other map

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py profile:='loc-sim' world:='apartment.wbt' map:='apartment.yaml'
```

## Parameters

| Parameter        | Type   | Description                                           |
| ---------------- | ------ | ----------------------------------------------------- |
| profile          | string | Parameters profile.                                   |
| namespace        | string | Namespace for the robot.                              |
| slam             | bool   | Whether to run a SLAM.                                |
| use_localization | bool   | Whether to enable localization or not.                |
| map              | string | Absolute path to the map YAML file.                   |
| autostart        | bool   | Automatically start up the Nav2 stack.                |
| use_composition  | bool   | Whether to use composed bringup.                      |
| use_respawn      | bool   | Whether to respawn if a node crashes.                 |
| use_explore_lite | bool   | Launch explore_lite to explore the map automatically. |
| use_rviz         | bool   | Launch RViz2.                                         |
| rviz_config      | string | Absolute path for the RViz config file.               |
| use_lidar        | bool   | Whether to enable the LiDAR.                          |
| lidar_model      | string | RPLIDAR model name.                                   |
| use_camera       | bool   | Whether to enable the camera.                         |
| use_joy          | bool   | Whether to enable the joy.                            |
{.table}