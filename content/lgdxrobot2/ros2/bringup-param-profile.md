---
title: Bringup - Parameter Profile
weight: 10
---

When running the NAV2 bringup, a **profile** is required in the parameters. It is used to switch between the parameter sets for the nodes used by the NAV2 bringup and it is simply a Python function that locates the relevant parameter files. To check the available profiles, navigate to the `lgdxrobot2_bringup/param` folder.

## Creating a Profile

To create a profile, modify the source code of the `lgdxrobot2_bringup` package:

1. In the `lgdxrobot2_bringup/param` folder, copy any existing folder and rename it to a custom profile name.  
2. Edit the parameters in the copied folder. Parameters may be copied from the root of `lgdxrobot2_bringup/param`, but `eky.yaml` and `nav2.yaml` are required.
3. In the `lgdxrobot2_bringup/rviz` folder, copy any RViz configuration file and rename it to match the custom profile name.  
4. Recompile the package.  
5. Start the NAV2 bringup with the custom profile using `profile:=<your_profile_name>`.
