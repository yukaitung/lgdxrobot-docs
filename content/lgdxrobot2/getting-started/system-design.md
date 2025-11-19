---
title: System Design
weight: 4
---

LGDXRobot2 features a two-layer control system. The first layer is controller board (MCU), responsible for real-time motor control and PID regulation. The second layer is a computer running ROS 2, which handles LiDAR and other sensor data. Communication between the microcontroller and the computer is achieved via USB using STM32VCP.

The system is powered by two separate sources, each consisting of four 18650 batteries managed by a BMS to isolate power for the motors and the logical components. For the motors, a 12 V DC-DC step-down converter is used. The computer is powered via either 12 V or 5 V, depending on the device.

![System Design](../img/system/system.png)

## Controller Board (MCU)

The controller board follows a modular design, allowing individual components to be replaced as needed. For basic safety, it includes an emergency stop button.

The board is built around the BlackPill (STM32F411CEU6) microcontroller, which provides a sufficient number of GPIO pins at a reasonable cost. It is equipped with two TB6612FNG motor driver modules for controlling the four motors, and two INA226 modules to monitor power sources voltage and current. A relay module manages the power supply to the motors.

The controller is also responsible for PID regulation of the motors, using encoder feedback. The PID system offers three levels, allowing distinct configurations for different velocities and stabilising the motors under variable speed conditions. The response time is approximately 20 ms.

Motor control is achieved via PWM. The system clock runs at 96 MHz, and the PWM frequency is set to 10 kHz. The auto-reload register (ARR) is therefore 9599, calculated using the formula: Fpwm = (Fclk / ((ARR + 1) * (PSC + 1))).

For the wheels and encoders, 1 revolution of a wheel corresponds to 3960 counts in the STM32 counter.
The gear ratio is 1:90, and the encoder PPR is 11 × 4 counts per edge (up/down), giving 11 × 4 × 90 = 3960 counts per wheel revolution. Each count corresponds to approximately 0.0015867 rad.

## Computer (PC)

The computer can be any device capable of running ROS 2 or Docker, supporting at both AMD64 and ARM64 architectures. LGDXRobot2 includes mounting holes for the Nvidia Jetson Nano, Raspberry Pi, and NUC (slim version only).

Testing has shown that the minimum requirement is the Nvidia Jetson Nano B01. However, NAV2 struggles to run SLAM on this device. Therefore, the Raspberry Pi 4B+ will be more suitable for LGDXRobot2.

For LiDAR, LGDXRobot2 provides mounting holes for the RPLIDAR C1 and RPLIDAR A1, though other models can also be used. For cameras, only the RealSense D435 and D435i (if IMU functionality is required) are recommended.
