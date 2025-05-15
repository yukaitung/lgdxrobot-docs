---
title: NAV2 Integration
weight: 5
---

The launch files for NAV2 Integration are stored in `lgdxrobot2_bringup` package.

## Examples

Run SLAM in simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py slam:=True
```

Run SLAM with auto exploration in simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py slam:=True use_explore_lite:=True
```

Run localication in simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py profile:='sim-loc'
```

Run NAV2 with actural hardware

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup nav_rtabmap.launch.py
```