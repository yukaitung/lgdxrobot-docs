---
title: Design
weight: 2
---

The controller board follows a modular design, allowing individual components to be replaced when necessary. For basic safety, it includes an emergency stop button.

The board features the **BlackPill (STM32F411CEU6)** microcontroller, which provides a sufficient number of GPIO pins at a reasonable cost. It is equipped with **two TB6612FNG** motor driver modules to control the four motors, and **two INA226** modules are included to monitor battery voltage and current. The relay module controls the power supply to the motors.

The board has a built-in three-level PID controller for the motors, which reads values from the encoders. The response time is approximately 20 ms.
