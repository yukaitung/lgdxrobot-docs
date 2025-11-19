---
title: Bringup - Parameter Profile
weight: 10
---

You may be aware that when running the NAV2 bringup, a `profile` is required in the parameters. The `profile` is designed to switch the parameter sets for the nodes used by the NAV2 bringup. To check the available profiles, navigate to the `lgdxrobot2_bringup/param` folder.

## Creating a Profile

A `profile` is simply a Python function that locates the parameter files. To create a profile, you can modify the source code of the `lgdxrobot2_bringup` package:

1. In the `lgdxrobot2_bringup/param` folder, copy any existing folder and rename it to your profile name.  
2. Edit the parameters in the copied folder. You may copy the parameters from the root of `lgdxrobot2_bringup/param`, but `eky.yaml` and `nav2.yaml` are required.  
3. In the `lgdxrobot2_bringup/rviz` folder, copy any RViz configuration file and rename it to match your profile name.  
4. Recompile the package.  
5. Start the NAV2 bringup with your profile using `profile:=<your_profile_name>`.
