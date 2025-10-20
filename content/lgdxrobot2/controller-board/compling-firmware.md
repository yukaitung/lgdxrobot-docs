---
title: Compling Firmware
weight: 4
---

The LGDXRobot2 MCU includes only the minimal source code, so it is necessary to generate the complete project before proceeding. You may then use any supported IDE to build and flash the firmware.

## Prerequisites

The following software is required to build and flash the firmware:

* [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)  
* A supported IDE, such as:  
  * [STM32 VS Code extension](https://www.st.com/content/st_com/en/campaigns/stm32-vs-code-extension-z11.html)  
  * [MDK-Community Edition](https://www.keil.arm.com/mdk-community/) (not for commercial use)  

## Build

Clone the [project repository](https://gitlab.com/yukaitung/lgdxrobot2-mcu), then open it with STM32CubeMX and generate the project accordingly. Next, launch your IDE and open the file `Inc/motor.h`. Modify the source code as needed to match your robot's specifications.

| Variable Name   | Example Value                           | Description                                                           |
|-----------------|---------------------------------------|-----------------------------------------------------------------------|
| CHASSIS_LX      | 0.237                                 | Size of the chassis in metres (m), X axis representing left to right |
| CHASSIS_LY      | 0.287                                 | Size of the chassis in metres (m), Y axis facing forward             |
| WHEEL_RADIUS    | 0.0375                                | Radius of the wheels in metres (m)                                    |
| MOTOR_GEAR_RATIO| 90                                    | Gear ratio of the motor                                               |
| MOTOR_MAX_SPEED | {10.948, 11.424, 11.1066, 10.6306}   | Maximum speed of each motor (wheel velocity in ChassisTuner)         |
| ENCODER_PPR     | 3960                                  | Encoder pulses per revolution; multiply by 4 (e.g., 11 × 90 × 4)      |
| PID_KP          | {6, 5, 6, 6}                         | Proportional constant for motor PID                                   |
| PID_KI          | {11, 11, 13, 13}                     | Integral constant for motor PID                                       |
| PID_KD          | {0.0, 0.0, 0.0, 0.0}                 | Derivative constant for motor PID                                     |
{.table}

*Note: The arrays start from motor 1.*

Once the modifications are complete, you can build and flash the firmware onto the device.