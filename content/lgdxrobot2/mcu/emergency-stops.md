---
title: Emergency Stops
weight: 2
---

Even though LGDXRobot2 is not an industrial robot, it has several emergency stops to protect both people and the robot. The controller board has two LEDs that indicate the status of the emergency stops. If no emergency stop is active, the green LED is on. Otherwise, the red LED is lit and the robot will stop.

## Software Emergency Stop

The software emergency stop is a software feature that prevents the robot from moving. It can be enabled in the firmware by sending a command to the MCU.

## Hardware Emergency Stop

The hardware emergency stop is a physical emergency-stop button that cuts power to the motors to stop the robot. In the firmware, it is detected by monitoring the current measured by the INA226 sensor. If the current exceeds the threshold, the hardware emergency stop is considered to have been triggered.

## Battery-Low Emergency Stop

To prevent the battery from being drained, the controller board has two INA226 sensors. The firmware checks only the voltage of the battery connected to the motors. If the voltage falls below the threshold, the battery-low emergency stop is considered to have been triggered. The battery for the PC should be monitored by the PC itself.
