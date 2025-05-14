---
title: Guidance
weight: 2
---

ChassisTuner requires compile on the computer.

## Installation

Qt is required for the tool. Install latest Qt with Serial Port and Qt Chart. Then, using Qt Creator to open the project and press "Run".

## Usage

Connect the MCU to the computer, select the correct serial device name and press connect. You can select Refresh to update the list.

The robot status should showing Connected and you can see all data from robot.

To test the inverse kinematics of the robot, enter the velocity for any axis and press "Send", please start with 0.1 to prevent overrun. Press "Stop" to stop the robot.

To test the emergency stop, press "Enable" in section 4, the red LED should turns on and the robot should not move. Press "Disable" to disable the emergency stop, the green LED should be turns on.

The lower half of the interface are charts for PID turning, every motor has the chart for performance verficaiton and the setting of PID.

Start the PID turning by setting P constant as 1 for Motor 1, then select "Send PID". Then, setup the target velocity and press "Test" to start. The chart shows the velocity of the moter immediately. Press "Stop" to stop the motor and stop updating the chart. 

There are different way to tune PID, if you forgot the initalise PID setting, press "Reset PID" to reset the PID. After getting satisfying PID constants, you can reflash the firmware for MCU with latest PID setting.