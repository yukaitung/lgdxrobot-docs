---
title: Design
weight: 2
---

LGDXRobot2 MCU relies on modular design, making the components are replacinable. Also, it has an emergency stop button for basic safety measure.

## Control Board

The control Board features BlackPill (STM32F411CEU6) for MCU, which has enough GPIO in a reasonable price. 2 TB6612FNG modules for controllnig motors and 2 INA219 modules for measuring voltage of batteries (Does not measuing current).

For power source, LGDXRobot2 is designed for using two 12V batteries, one for motors and one for computer. It is a simple solution to prevent damange from voltage fluctuation. You are free to add a protection board for batteries or using powerful battery.

## Hardware (Mechanic)

LGDXRobot2 is designed for any size of mecanum wheel chassis, so you can select any size of chassis and mecanum wheels, you will need to modifiy the source code (It is a constants) to fit the configuration.

The motors using in LGDXRobot2 are GM37-520 12V with 1:90 gear ratio, it is recommend to select motor with at least 1:90 to ensure enough torque for the robot.

## Hardware (Logic)

Any computer supports Ubuntu 24.04 can be used, however only x86 PC (Intel NUC) is being tested. Intel realsense can used for sensor.

## Assembly

The assembly is simple by connected everything spefifed in schematic, there is no PCB board needed to print.