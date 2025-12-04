---
title: Automation - Tasks
weight: 100
---
A *Task* is an automation job executed by a robot. It includes a list of waypoints that the robot must visit, as well as a flow that defines the steps to be performed when executing the task.

## Creating a Task

* Click the **Create Task** button at the top right.
* Enter the task settings.
* Click **Create**.

## Viewing a Task

* Tasks are not displayed by default.
* To display tasks, click the **Select Task Category...** dropdown at the top right.
* Select a task category:
  * **Templates**: Template tasks that can be reused.
  * **Waiting**: Tasks waiting to be executed.
  * **Completed**: Tasks that have finished successfully.
  * **Aborted**: Tasks that have been aborted.
  * **Running**: Tasks that are currently being executed.
* Click the **View** button on the right of the task.

## Editing a Task

* Only tasks in the **Templates** category can be edited.
* Click the **Select Task Category...** dropdown at the top right.
* Select **Templates**.
* Click the **View** button on the right of the task.
* Update the task settings.
* Click **Update**.

## Cloning a Task

* Cloning creates a new task with the same settings as the original.
* Click the **Select Task Category...** dropdown at the top right.
* Select any category.
* Click the **Clone** button on the right of the task.
* Update the task settings if needed.
* Click **Create**.

## Deleting a Template Task

* Only tasks in the **Templates** category can be deleted.
* Click the **Select Task Category...** dropdown at the top right.
* Select **Templates**.
* Click the **View** button on the right of the task.
* Click **Delete**.
* Press **Yes** to confirm.

## Aborting a Task

* Only tasks in the **Running** and **Waiting** categories can be aborted.
* Click the **Select Task Category...** dropdown at the top right.
* Select **Running** or **Waiting**.
* Click the **View** button on the right of the task.
* Click **Abort**.
* Press **Abort** to confirm.
* If the assigned robot is online, the system will send a message to the robot to abort the task. Otherwise, the task will be aborted immediately.

## Settings

* **Name**: The name of the task.
* **Priority**: The priority level of the task. Higher-priority tasks are executed first. If multiple tasks have the same priority, they are executed in the order they were created.
* **Flow**: The workflow for the task. Enter the flow name to search for it.
* **Assigned Robot**: The robot assigned to the task, or *Any Robot* if none is specified.
* **Create as Template Task**: If enabled, the task will be created as a template.
* **Waypoints**: The list of waypoints the robot must visit.
  * **Waypoint**: The waypoint to visit. Enter the waypoint name to search for it.
  * **X**: Overrides the waypoint’s X coordinate in metres.
  * **Y**: Overrides the waypoint’s Y coordinate in metres.
  * **Rotation**: Overrides the waypoint’s rotation in radians.
  * **Reorder**: Use the up and down arrows to change the order of waypoints.
  * **Remove**: Click the rubbish bin icon to remove the waypoint.
  * **Add Waypoint**: Click the **Add Waypoint** button to add a new waypoint.

Please note that position overrides may break Traffic Rules if the overridden coordinates are too far from the traffic paths. The system does not validate overridden values against Traffic Rules.
{.alert .alert-info}
