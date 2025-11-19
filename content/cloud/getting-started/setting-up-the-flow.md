---
title: Setting Up The Flow
weight: 4
---

A **flow** is a sequence of steps for completing tasks. Each flow can be customised to suit specific operational requirements.

## Step 1: Navigate to The Flows Creation Page

Expand the **Automation**, select **Flows** and press **Create Flow** in the top-right corner.

## Step 2: Create a Flow

In the **Flow Detail** section, you can specify the flow name and details. Search for **Moving** under **Progress Name**, then press **Create**.

![](../img/flow1.png)

**Progress Name** defines each step in the flow. You can customise the robot's behaviour in ROS 2 for each step (excluding `PreMoving` and `Moving`).  
- `Moving` is required and handles robot navigation.  
- `PreMoving` instructs the robot to move to the first waypoint and allows for preparatory actions, such as loading.

**Proceed Condition** determines how the robot advances to the next step. The component responsible for this obtains a token to progress the flow. For example, if you select **API**, the robot waits for an external API call to continue — in this case, a **Trigger** is needed.

**Trigger** is the external API call that initiates the specified **Progress** step. It is triggered at the beginning of the step.