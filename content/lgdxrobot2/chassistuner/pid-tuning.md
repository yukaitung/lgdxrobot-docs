---
title: PID Tuning
weight: 5
---

The **PID Tuning** tab allows fine-tuning of the PID constants for each motor to achieve the desired performance. The controller board supports three levels of PID control, which helps maintain system stability at different velocities.

Switch to the **PID Tuning** tab to view the PID parameters. If they are not visible, press **Refresh**.

## Motors Maximum Speed

The maximum speed defines the upper limit used by the PID controller when calculating output. To obtain the maximum speed, press the **Auto Config** button to automatically measure the maximum speed for each motor. The maximum speed can also be set manually before pressing **Send**.

Please ensure the robot is lifted when sending commands; otherwise, it may move and cause damage.  
{.alert .alert-danger}

![Screenshot of the Motors Maximum Speed](../img/motors_max_speed.png)

## PID Configuration

This section stores the PID constants for each motor and level. The controller supports three levels, allowing different PID configurations for different speeds. Level 1 is expected to be the lowest, and Level 3 the highest. 

![Screenshot of the PID Configuration](../img/pid_config.png)

To define the PID speed:

1. Enter the desired speed for each level.  
2. Press **Send**.

## PID Test

The **PID Test** allows fine-tuning of the PID constants for each motor using a chart. Adjust the PID values for each motor and each level to achieve the desired performance. 

![Screenshot of the PID Test](../img/pid_test.png)

For example, to tune the PID for Motor 1 at Level 3:

Please ensure the robot is lifted when sending commands; otherwise, it may move and cause damage.  
{.alert .alert-danger}

1. Select Motor 1 from the drop-down menu and Level 3 from the level menu.  
2. Set the PID constants and press **Update**.  
3. Press **Send** to start the test and observe the chart.  
4. Press **Stop** to halt the test.

There are various methods for tuning PID. When adjusting the PID constants, try increasing P by 1, I by 10, and D by 0.1.  
{.alert .alert-info}

The **Custom Velocity** checkbox may be selected to define a custom velocity for testing.
