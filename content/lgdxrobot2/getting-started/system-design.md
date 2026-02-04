---
title: System Design
weight: 4
---

The LGDXRobot2 has a two-layer control system. The first layer is a microcontroller unit (MCU) responsible for real-time motor control, PID regulation, and sensor data acquisition. The second layer is an onboard computer running high-level applications such as ROS 2 and Nav2. Communication between these two controllers is handled via STM32 VCP (Virtual COM Port).

To ensure system stability, the power supply is isolated between the motors and the logic circuits. The robot uses a single master switch to power the onboard computer. The motor power is controlled via a relay and the MCU. This ensures the robot is completely powered down once the computer is turned off.

![System Design](../img/system/system.png)

## Controller Board (MCU)

![Controller Board](../img/system/controller-board.png)

The controller board has a modular design, making it easy to replace individual components. It is built around the BlackPill (STM32F411CEU6) microcontroller. It has two TB6612FNG motor driver modules to control the four motors and an ICM-20948 IMU for sensor fusion in navigation.

Safety is a key priority, so the board supports an emergency stop. This cuts power to the motors and notifies the controller that the robot is in an emergency state. Also, the board monitors the voltage for both power sources using voltage divider circuit. If the voltage drops below a set threshold, it automatically cuts power to the motors.

The controller also handles PID regulation using encoder feedback. The PID system uses three distinct configuations to maintain stability across different velocities. The response time for the control loop is approximately 10 ms.

### Extra Technical Information

Motor control is achieved via PWM. The system clock runs at 96 MHz, and the PWM frequency is set to 10 kHz. The auto-reload register (ARR) is therefore 9599, calculated using the formula: Fpwm = (Fclk / ((ARR + 1) * (PSC + 1))).

For the wheels and encoders, 1 revolution of a wheel corresponds to 3960 counts in the STM32 counter.
The gear ratio is 1:90, and the encoder PPR is 11 × 4 counts per edge (up/down), giving 11 × 4 × 90 = 3960 counts per wheel revolution. Each count corresponds to approximately 0.0015867 rad.

## Onboard Computer

The computer can be any device capable of running ROS 2 or Docker, supporting at both AMD64 and ARM64 architectures. LGDXRobot2 includes mounting holes for the Nvidia Jetson Nano, Raspberry Pi, and NUC (slim version only).

Besides, the computer connects to a LiDAR sensor and an optional camera.