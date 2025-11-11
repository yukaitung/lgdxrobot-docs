---
title: Bringup - NAV2
weight: 7
---

The `nav` launch file is used to start the robot with all required hardware, the **NAV2** stack, and display it in the **RViz2** GUI.

## Examples

SLAM on NAV2

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py slam:=True profile:='slam'
```

Localisation on NAV2

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py map:<Absolute path to the map yaml file>
```

SLAM on NAV2 with JOY

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py slam:=True profile:='slam' use_joy:=True
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