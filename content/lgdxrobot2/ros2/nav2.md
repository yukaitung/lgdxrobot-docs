---
title: NAV2 Integration
weight: 5
---

The NAV2 integration launch files are located in the `lgdxrobot2_bringup` package. These files support various simulation and real-world navigation setups, including SLAM, localisation, and exploration.

## Examples

Run SLAM in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py slam:=True
```

Run SLAM with Auto Exploration in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py slam:=True use_explore_lite:=True
```

Run Localisation in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py profile:='sim-loc'
```

Run NAV2 with Actual Hardware

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup nav_rtabmap.launch.py
```