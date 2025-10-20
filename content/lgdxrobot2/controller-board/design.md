---
title: Design
weight: 2
---

**LGDXRobot2 MCU** follows a modular design, allowing individual components to be replaced when necessary. For basic safety precautions, it includes an emergency stop button.

The control board features the **BlackPill (STM32F411CEU6)** microcontroller, which provides a sufficient number of GPIO pins at a reasonable cost. It is equipped with **two TB6612FNG** motor driver modules to control the four motors, and **two INA226** modules are included to monitor the battery voltage. 