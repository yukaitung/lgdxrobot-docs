---
title: Creating Your First Map
weight: 2
---

The first thing we need is the map, which can be created using the NAV2 stack in ROS2. The LGDXRobot2 ROS2 package is required for this.

## Create Map

Launch the NAV2 stack in SLAM mode:

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py slam:=True
```

In RViz2, complete the exploration using **2D Goal Pose**, then press **Save Map** in the SlamToolboxPlugin on the right side of the window.

![](../img/map1.png)

You can find the map file and configuration file in the `lgdx_ws` folder.

![](../img/map2.png)

Below is an example of a map file and its configuration file:

![](../img/map3.png)

```
image: map.pgm
mode: trinary
resolution: 0.05
origin: [-0.543, -10.3, 0]
negate: 0
occupied_thresh: 0.65
free_thresh: 0.25
```

## Setup Realm

Login to the system using the account and password you specified. Navigate to **Navigation -> Realms** and select **View** for **First Realm**.

![](../img/map4.png)

Convert the map into a PNG file (or use the example image above), then upload the image. Update **Resolution**, **Origin X**, **Origin Y**, and **Origin Rotation** using the values from the configuration file. From the example above, the resolution is **0.05**, Origin X is **-0.543**, and Origin Y is **-10.3**. Press **Update** to save.

![](../img/map5.png)

It is recommend to restart `LGDXRobotCloud.UI` after updating the first realm.

## Setup Waypoints

We need to set up some waypoints for the robot to navigate through. Navigate to **Navigation -> Waypoints** and select **Create Waypoint**.

![](../img/map6.png)

First, create two waypoints using the data below. After entering the position for waypoint **A**, press **Create**, then press **Create Waypoint** again to create waypoint **B**.

| Name | X   | Y    | Rotation |
|------|-----|------|----------|
| A    | 0   | 0    | 0        |
| B    | 5.5 | -5.5 | 0        |
{.table}

![](../img/map7.png)

Both waypoints should now be created and visible on the interface.

![](../img/map8.png)
