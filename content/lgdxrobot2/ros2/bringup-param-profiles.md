---
title: Bringup - Parameter Profiles
weight: 153
---

When running the NAV2 bringup, a **profile** is required in the parameters. It is used to switch between the parameter sets for the nodes used by the NAV2 bringup and it is simply a Python function that locates the relevant parameter files. To check the available profiles, navigate to the [lgdxrobot2_bringup/param](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/lgdxrobot2_bringup/param?ref_type=heads) folder.

## Nav2 Controller Plugins

Nav2 offers different controller plugins for line following, each using a distinct algorithm. LGDXRobot2 ROS 2 allows switching between the available plugins through profiles.

* `DWB Controller`  – This is the default plugin, so specifying a profile is not required.
* `Model Predictive Path Integral Controller (MPPI)` – Use `loc-mppi` as the profile name.
* `Graceful Controller` – Use `loc-gc` as the profile name.
* `Regulated Pure Pursuit Controller` – Use `loc-rpp` as the profile name.

## Creating a Profile

1. Copy the `param` and `rviz` folders from the [lgdxrobot2_bringup](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/lgdxrobot2_bringup?ref_type=heads) package to any folder.
2. In the `param` folder, copy any existing folder and rename it using a custom profile name. It is recommended that the name starts with `slam-` or `loc-`.
3. Edit the parameters in the copied folder. Parameters may be copied from the root of `param`, but `ekf.yaml` and `nav2.yaml` are required.
4. (Optional) In the `rviz` folder, copy any RViz configuration file and rename it to match the custom profile name.  
5. Recompile the package.  
6. Start the Nav2 bringup with the custom profile using `profiles_path:=<path to custom profiles folder> profile:=<profile_name>`.