---
title: Setting Up Your Flow
weight: 3
---

A flow is a sequence of steps for completing tasks. Each flow can be customised to fit specific operational requirements.

## Create a flow

Navigate ro "Automation" -> "Flows", then select "Create Flow"

In the Flow Detail, you can specific the flow name and detail. Search "Moving" for Progress Name and press Create

`Progress Name` is every step in the flow, you can define your operation for the process in ROS2 (exclude `PreMoving` and `Moving`). The `Moving` is the operation for the robot to navigating and it should be included in the flow. `PreMoving` tells the robot to move to first waypoint, it allows the robot perform other operation like loading.

`Proceed Condition` is the compoment that command the robot to continue to next step, the component will obtains a token to progress the flow. For the `API`, an external API call is required so a `Trigger` is required.

`Trigger` is an external API call which trigerred at the begining of `Progress`