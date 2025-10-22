---
title: Design
weight: 2
---

The controller board follows a modular design, allowing individual components to be replaced when necessary. For basic safety, it includes an emergency stop button.

The board features the **BlackPill (STM32F411CEU6)** microcontroller, which provides a sufficient number of GPIO pins at a reasonable cost. It is equipped with **two TB6612FNG** motor driver modules to control the four motors, and **two INA226** modules are included to monitor battery voltage and current. The relay module controls the power supply to the motors.

The board has a built-in three-level PID controller for the motors, which uses encoders for feedback. The three levels allow three distinct PID configurations for different velocities, stabilising the motors under variable speed changes. The response time is approximately 20 ms.

The motors are controlled via PWM. The system clock is 96 MHz, and the PWM frequency is 10 kHz. Therefore, the auto-reload register (ARR) is 9599, calculated using the formula: Fpwm = (Fclk / ((ARR + 1) * (PSC + 1))).

For the wheels and encoders, 1 revolution of a wheel corresponds to 3960 counts in the STM32 counter.  
The gear ratio is 1:90, and the encoder PPR is 11 × 4 counts per edge (up/down), giving 11 × 4 × 90 = 3960 counts per wheel revolution. Each count corresponds to approximately 0.0015867 rad.
