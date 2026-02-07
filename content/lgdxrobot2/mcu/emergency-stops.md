---
title: Emergency Stops
weight: 2
---

Even though LGDXRobot2 is not an industrial robot, it has several emergency stops to protect both people and the robot. The controller board has a red LED that indicates the emergency stop status. When the robot enters an emergency state, the red LED turnes on and power to the motors is cut off.

## Software Emergency Stop

The software emergency stop is a software feature that prevents the robot from moving. It can be enabled in the firmware by sending a command to the MCU.

## Hardware Emergency Stop

he hardware emergency stop is a physical button that directly disconnects power to the motors. The firmware monitors this state via a voltage divider circuit, to detect when the E-stop has been triggered.

## Battery-Low Emergency Stop

To prevent the battery from being drained, the controller board has two voltage divider circuits. The firmware monitors the voltage of both power sources, but it only cuts power to the motors if the voltage drops below a threshold. The battery for the PC should be monitored by the PC itself.
