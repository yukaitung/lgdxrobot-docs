---
title: Robot Testing
weight: 4
---

The Robnot Testing section covers reading data from the robot and sending commands to it.

## Connecting to the Robot

![Screenshot of the Robot Data tab](../img/robot_data.png)

1. Connect the controller board to the computer using a USB cable, as communication is performed over USB (STM32 Virtual COM Port).
2. In the top-right corner, select the correct serial device name.
3. If the device is not listed, press **Refresh** on the left.
4. Press **Connect** on the right.
5. The connection status should display **Connected**.
6. Data should be visible as being received from the robot. Rotating the wheels will show corresponding changes in the data.

## Sending Commands (Hardware Testing Section)

![Screenshot of the Hardware Testing](../img/hardware_testing.png)

### Get Serial Number

Each microcontroller has a unique serial number. Press **Get** under Get Serial Number. The serial number will be displayed at the top.

### Reset Transform

Press the **Reset** button to reset the robot's transform. The transform values should return to zero.

### Inverse Kinematics

This command sets the robot’s vector motion. The velocity for each axis can be set individually before pressing **Send**. Press **Stop** to halt the robot. The robot should move in the desired direction.

Please ensure the robot is lifted when sending commands. Otherwise, the robot may move and cause damage.
{.alert .alert-danger}

### Motor Speed

This command sets the speed of an individual motor. Select the motor from the drop-down menu, set the desired velocity, and press **Send**. Press **Stop** to halt the motor. Only the selected motor should move.

Please ensure the robot is lifted when sending commands. Otherwise, the robot may move and cause damage.
{.alert .alert-danger}

### Set Software Emergency Stop

This command enables or disables the software emergency stop. Press **Enable** to activate it and **Disable** to deactivate it. When enabled, the status should change to **Enabled** and the red LED will illuminate.
