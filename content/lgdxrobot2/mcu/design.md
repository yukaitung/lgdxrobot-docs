---
title: Design
weight: 2
---

**LGDXRobot2 MCU** follows a modular design, allowing individual components to be replaced when necessary. For basic safety precautions, it includes an emergency stop button.

## Control Board

![LGDXRobot2 Control Board](../img/control-board.jpg)
[Download the PDF](/files/board.pdf)

The control board features the **BlackPill (STM32F411CEU6)** microcontroller, which provides a sufficient number of GPIO pins at a reasonable cost. It is equipped with **two TB6612FNG** motor driver modules to control the four motors, and **two INA219** modules are included to monitor the battery voltage. Please note that current sensing is not implemented.

**LGDXRobot2** is designed to operate using **two 12V batteries**: one dedicated to powering the motors and the other for the onboard computer. This separation provides a simple and effective way to prevent damage caused by voltage fluctuations. Users are welcome to integrate a battery protection board or choose a higher-capacity battery according to their requirements.

## Hardware (Mechanical)

**LGDXRobot2** is compatible with Mecanum wheel chassis of various sizes. Users may select any chassis and wheel dimensions they prefer; however, they must modify the source code — specifically a set of constants — to reflect the chosen configuration.

The recommended motor for this platform is the **GM37-520 12V with a 1:90 gear ratio**. It is advisable to use motors with at least a 1:90 ratio to ensure that the robot has sufficient torque for reliable operation.

## Hardware (Computing)

Any computer that supports **Ubuntu 24.04** can be used with **LGDXRobot2**. However, only **x86-based PCs**, such as **Intel NUC** devices, have been tested. An **Intel RealSense** camera can be used for sensing purposes.

## Assembly

The assembly process is straightforward. All components should be connected as specified in the provided schematic. There is no need to fabricate a printed circuit board (**PCB**), making the construction accessible and convenient.
