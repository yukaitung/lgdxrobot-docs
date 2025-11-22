---
title: Bringup - Parameter Profile
weight: 10
---

When running the NAV2 bringup, a **profile** is required in the parameters. It is used to switch between the parameter sets for the nodes used by the NAV2 bringup and it is simply a Python function that locates the relevant parameter files. To check the available profiles, navigate to the [lgdxrobot2_bringup/param](https://gitlab.com/lgdxrobotics/lgdxrobot2-ros2/-/tree/main/lgdxrobot2_bringup/param?ref_type=heads) folder.

## Profile Explanation

* A profile name starting with `slam` indicates that the profile is intended for SLAM, while `loc` indicates that it is intended for localisation.
* If the profile name includes `-sim`, it is intended for simulation.
* If the profile name includes `-pi4`, it is intended for the Raspberry Pi 4B+, and `-jetson-nano` indicates that it is intended for the Nvidia Jetson Nano.
* If the profile name ends with `-no-cam`, it is intended for robots without a Realsense IMU.
* If the profile name does not include a device name, the profile is intended for a NUC.

## Creating a Profile

To create a profile, modify the source code of the `lgdxrobot2_bringup` package:

1. In the `lgdxrobot2_bringup/param` folder, copy any existing folder and rename it using a custom profile name. It is recommended that the name starts with `slam-` or `loc-`.
2. Edit the parameters in the copied folder. Parameters may be copied from the root of `lgdxrobot2_bringup/param`, but `ekf.yaml` and `nav2.yaml` are required.
3. (Optional) In the `lgdxrobot2_bringup/rviz` folder, copy any RViz configuration file and rename it to match the custom profile name.  
4. Recompile the package.  
5. Start the NAV2 bringup with the custom profile using `profile:=<your_profile_name>`.