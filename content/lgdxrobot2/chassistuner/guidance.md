---
title: Guidance
weight: 2
---

There is no binary available for download. ChassisTuner must be built on your computer.

## Installation

Qt is required to run the tool. Install the latest version of Qt, including the Serial Port and Qt Charts modules. Then, open the project using Qt Creator and press **Run**.

## Hardware Testing

Connect the MCU to your computer, select the correct serial device name, and press **Connect**. You can press **Refresh** to update the list.

![](../img/gui1.png)

The robot status should display **Connected**, and you should see all data received from the robot.

![](../img/gui2.png)

To test the inverse kinematics of the robot, enter the velocity for any axis and press **Send**. Please start with a low value such as 0.1 to avoid unexpected movement. The interface shows the current velocity of each motor. Press **Stop** to halt the robot.

![](../img/gui3.png)

To test the emergency stop function, press **Enable** in section 4. The red LED should turn on, and the robot should stop moving. Press **Disable** to deactivate the emergency stop; the green LED should then turn on.

![](../img/gui4.png)

## PID Tuning

The lower half of the interface contains charts and controls for PID tuning. Each motor has a chart for performance verification and fields for adjusting the PID values.

![](../img/gui5.png)

Begin tuning by setting the P constant to 1 for Motor 1, then press **Send PID**. Set the target velocity and press **Test** to begin. The chart will display the motor's velocity in real time. Press **Stop** to halt the motor and pause the chart updates.

![](../img/gui6.png)

There are multiple methods for tuning PID. If you forget the initial PID settings, press **Reset PID** to restore the defaults. Once you are satisfied with the PID constants, reflash the MCU firmware with the updated values.

![](../img/gui7.png)
