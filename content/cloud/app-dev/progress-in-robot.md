---
title: Progress in Robot
weight: 2
---

This tutorial describes how to use the Next Token in a ROS robot. This applies to both physical and simulated robots.

## Prerequisites

1. Create a new flow with two progress steps: **Loading** and **Moving**.

![Screenshot of creating a new flow](../img/progress-in-robot/flow-create.png)

2. Connect a robot to LGDXRobot Cloud.

## Completing the Progress

1. Create a new task using the flow just created. The waypoints can be any waypoints in the realm.

![Screenshot of creating a new task](../img/progress-in-robot/task-create.png)

2. The robot will not move because the current progress is **Loading**.
3. Connect to the robot or web interface.
4. In the terminal, run the following command to obtain the task ID and Next Token:


```bash
ros2 topic echo /cloud/auto_task
```

![Screenshot of obtaining the task ID and Next Token](../img/progress-in-robot/next-echo.png)

5. In another terminal, run the following command to complete the progress:

```bash
ros2 service call /auto_task_next lgdxrobot_cloud_msgs/srv/AutoTaskNext "{task_id: <task ID>, next_token: '<Next Token>'}"
```

![Screenshot of completing the progress](../img/progress-in-robot/next-service.png)

6. The robot will move to the next waypoint.

## Aborting the Task

1. Create a new task using the flow just created. The waypoints can be any waypoints in the realm.
2. The robot will not move because the current progress is **Loading**.
3. Connect to the robot or web interface.
4. In the terminal, run the following command to obtain the task ID and Next Token:

```bash
ros2 topic echo /cloud/auto_task
```

![Screenshot of obtaining the task ID and Next Token](../img/progress-in-robot/abort-echo.png)

5. In another terminal, run the following command to abort the task:

```bash
ros2 service call /auto_task_abort lgdxrobot_cloud_msgs/srv/AutoTaskAbort "{task_id: <task ID>, next_token: '<Next Token>'}"
```

![Screenshot of aborting the task](../img/progress-in-robot/abort-service.png)

6. The task will be aborted, and an email notification will be sent.
