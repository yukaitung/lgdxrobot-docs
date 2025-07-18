---
title: Bringup
weight: 5
---

The `lgdxrobot2_bringup` package includes launch files that demonstrate how to bring up the robot with NAV2 and the LGDXRobot Cloud.

## Examples

Run SLAM in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py slam:=True profile:='sim-slam'
```

Run SLAM with Auto Exploration in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py slam:=True use_explore_lite:=True profile:='sim-slam'
```

Run Localisation in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py
```
