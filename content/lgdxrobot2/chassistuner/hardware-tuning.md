---
title: PID Tuning
weight: 4
---

The PID Tuning tab allows you to fine-tune the PID constants for each motor to achieve the desired performance. The controller board supports three levels of PID control, which helps maintain system stability at different velocities.

Switch to the PID Tuning tab, and the PID parameters will be displayed. If they are not visible, press **Refresh**.

## Motor Maximum Speed

The maximum speed defines the upper limit used by the PID controller when calculating output. To measure the maximum speed:

Please ensure the robot is lifted when sending commands. Otherwise, it may move and cause damage.
{.alert .alert-danger}

1. Switch back to the Robot Data tab and set the motor velocity to a high value, such as 100.
2. Note the maximum speed for each motor.
3. Switch back to the PID Tuning tab and enter the maximum speed for each motor.
4. Press **Send**.

## Level Velocity

Level velocity defines the maximum velocity for each PID configuration. Level 1 is expected to be the lowest, and Level 3 the highest. To define the level velocity:

1. Enter the desired velocity for each level.
2. Press **Send**.

## PID Test

The PID Test allows you to fine-tune the PID constants for each motor using a chart. You should adjust PID values for each motor and each level to achieve the desired performance. For example, to tune PID for Motor 1 at Level 1:

Please ensure the robot is lifted when sending commands. Otherwise, it may move and cause damage.
{.alert .alert-danger}

1. Select Motor 1 from the drop-down menu and Level 1 from the level menu.
2. Set the PID constants and press **Update**.
3. Press **Send** to start the test and observe the chart.
4. Press **Stop** to halt the test.

There are various methods for tuning PID. When adjusting the PID constants, try increasing P by 1, I by 10, and D by 0.1.
{.alert .alert-info}

The two additional checkboxes allow you to define a custom velocity for testing, enabling further performance evaluation.

The reverse direction option changes the motor to rotate in the opposite direction.

## Save PID

Scroll to the bottom and press **Save**. The PID constants will persist after reset but may be overwritten by a full chip erase.
