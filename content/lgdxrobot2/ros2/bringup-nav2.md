---
title: Bringup - Nav2
weight: 151
---

The `nav` launch file is used to start the Nav2 stack by initialising the required hardware and displaying it in RViz2.

![Image of the Nav2](../img/bringup/nav-img.png)

## Examples

### Robot Only

SLAM on Nav2

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  slam:=True \
  profile:='slam' \
  use_rviz:=True
```

Localisation on Nav2

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  map:=<Absolute path to the map yaml file> \
  use_rviz:=True
```

SLAM on Nav2 with JOY

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  slam:=True \
  profile:='slam' \
  use_joy:=True \
  use_rviz:=True
```

### With LGDXRobot Cloud

Assuming that the `/config/keys` folder contains `root.crt`, `Robot1.key` and `Robot1.crt` files. The path of these files can be set using the `cloud_root_cert`, `cloud_client_key` and `cloud_client_cert` parameters.

SLAM

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  slam:=True \
  profile:='slam' \
  use_cloud:=True \
  cloud_address:=<Address of the LGDXRobot Cloud service with port> 
```

Localisation

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  map:=<Absolute path to the map yaml file> \
  use_cloud:=True \
  cloud_address:=<Address of the LGDXRobot Cloud service with port>
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
| use_explore_lite | bool   | Launch explore_lite to explore the map automatically. |
| use_rviz         | bool   | Launch RViz2.                                         |
| rviz_config      | string | Absolute path for the RViz config file.               |
| use_lidar        | bool   | Whether to enable the LiDAR.                          |
| lidar_model      | string | RPLIDAR model name.                                   |
| use_joy          | bool   | Whether to enable the joy.                            |
| use_cloud           | bool   | Whether to enable cloud connectivity.         |
| cloud_address       | string | Address of the LGDXRobot Cloud service.        |
| cloud_root_cert     | string | Path to the server’s root certificate file.   |
| cloud_client_key    | string | Path to the client’s private key file.        |
| cloud_client_cert   | string | Path to the client’s certificate file.        |
{.table}