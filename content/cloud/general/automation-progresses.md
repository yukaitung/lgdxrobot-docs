---
title: Automation - Progresses
weight: 102
---

A *Progress* is a step in a flow that represents the action to be performed. The action should be defined by the developer and identified by its name or ID. For **PreMoving** and **Moving** progresses, the robot will automatically navigate the waypoints, and no action should be assigned.

Explanation of the progresses:

* **PreMoving**: The robot will move to the first waypoint and perform any preparatory actions, such as loading.
* **Moving**: The robot will move to the waypoints specified in the task.

Explanation of the progress types:

* **System Progress**: A progress defined by the system.
* **Reserved Progress**: A progress that is not suitable for use in a flow and will not appear in search results when creating a flow.

## Creating a Progress

* Click the **Create Progress** button at the top right.
* Enter the progress settings.
* Click **Create**.

## Updating a Progress

* Click the **View** button on the right of the progress.
* Update the progress settings.
* Click **Update**.

## Deleting a Progress

* Click the **View** button on the right of the progress.
* Click **Delete**.
* The system validates that the progress is not used by any flow.
* Press **Delete** to confirm.

## Settings

* **Name**: The name of the progress.