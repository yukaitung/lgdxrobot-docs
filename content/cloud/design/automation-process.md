---
title: Automation Process
weight: 2
---

With the ability to remotely control a ROS 2 robot, LGDXRobot Cloud also manages the robot’s automation process. This system is designed for Automated Guided Vehicles (AGVs) operating in transportation and logistics. Therefore, the automation process contains the following elements:

* **Task**: A Task is an automation job executed by a robot. It includes a list of waypoints that the robot must visit, as well as a flow that defines the steps to be performed when executing the task.
* **Flow**: A Flow is a sequence of steps that defines the automation workflow when the robot executes a task. A flow allows additional steps to be added, such as loading or unloading an object, or calling third-party APIs using Triggers.
* **Progress**: A Progress is a step in a flow that represents the action to be performed. The action should be defined by the developer and identified by its name or ID.
* **Trigger**: A Trigger is a third-party API call that is invoked at the beginning of a progress. The trigger can include data that will be passed in the call.

## Defining a Flow

A task essentially commands the robot to reach the waypoints, but with a flow, the entire system enables a useful application to be developed. For example, this is a minimal flow:

**Progress: Moving**

The robot moves according to the waypoints.

To develop a useful application, more progress steps can be added, such as:

**Progress: PreMoving → Loading → Moving → Unloading**

The robot moves to the first waypoint, loads the object, moves according to the waypoints, and finally unloads the object. A trigger can also be added in the *Unloading* progress, such as calling a third-party API to update the inventory status.

## How to Progress in a Flow

The system now understands how to execute a transportation task, but it becomes stuck in the first progress because it does not know when that progress has finished. Therefore, LGDXRobot Cloud issues a **Next Token** that can be used to inform the system when the progress is complete.

When the progress is finished, the component (either the robot or a third-party system) that owns the Next Token will notify LGDXRobot Cloud that it has completed the current progress by sending the Next Token. The Next Token is an MD5 string that prevents incorrect tasks from being modified or reused.

The flow and current progress are managed by LGDXRobot Cloud, so the component does not need to be aware of the overall flow. The only requirement is to perform the action for the current progress as instructed by LGDXRobot Cloud.

## Conclusion

This page describes how to design a custom workflow for a robot to execute an automation task. In the custom workflow, the robot or the third-party system must perform the action for the current progress and then inform LGDXRobot Cloud that the progress has finished by sending the Next Token. LGDXRobot Cloud manages the progress and updates the status of the task accordingly until all progress steps are completed or the task is aborted.
