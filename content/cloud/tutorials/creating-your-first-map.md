---
title: Creating Your First Map
weight: 2
---

The first thing we need is the map, it can be created using NAV2 stack in ROS2. The LGDXRobot2 ROS2 is required for this.

## Create Map

Launch 

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_map.launch.py 
```

## Setup Realm

1. Go to Navigation -> Realms and select "View" for "First Realm"
2. Convert the map from PGM to PNG, then upload the image
3. Update Resolution, Origin X, Origin Y, Origin Rotation
4. Restart LGDXRobotCloud.UI

## Setup Waypoints

