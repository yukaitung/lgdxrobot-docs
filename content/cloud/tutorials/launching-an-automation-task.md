---
title: Launching an Automation Task
weight: 5
---

Finally, the system is ready to start the first automation task. In another terminal window, launch NAV2 Localisation in Simulation

```bash
cd lgdx_ws
. install/setup.bash
ros2 launch lgdxrobot2_bringup sim_nav.launch.py profile:='sim-loc'
```

## Create A Task

Navigate to **Automation -> Tasks** and press **Create Task**.  

Select your newly created flow. Then, select waypoint **A** and press **Add Waypoint**. Next, select waypoint **B**. Press **Create**.

![](../img/task1.png)

- **Priority** indicates the importance of the task; a higher value means higher priority.
- **Assign Robot** allows you to specify which robot will run the task.
- **Create as Template Task** enables you to save the task as a template for quicker creation in the future.
- You can specify custom X, Y, or Rotation values to override the predefined waypoint coordinates.

## View The Task

You will be redirected to the task list page, which may appear empty initially. Select **Running** at the top right to filter active tasks.

![](../img/task2.png)

Navigate to **Map** to see the real-time progress of the task.

![](../img/task3.png)
