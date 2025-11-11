---
title: Compling Firmware
weight: 4
---

The LGDXRobot2 MCU includes only the minimal source code, so it is necessary to generate the complete project before proceeding. You can then use any supported IDE to build and flash the firmware.

## Prerequisites

The following software is required to build and flash the firmware:

* [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)  
* ST-LINK V2 programmer
* A supported IDE, such as:  
  * [STM32 VS Code extension](https://www.st.com/content/st_com/en/campaigns/stm32-vs-code-extension-z11.html)  
  * [MDK-Community Edition](https://www.keil.arm.com/mdk-community/) (not for commercial use)  

## Build

### Generate the Project

1. Clone the [project repository](https://gitlab.com/yukaitung/lgdxrobot2-mcu).  
2. Launch STM32CubeMX and open the `.ioc` file.  
3. (If not using the VS Code extension) Switch to the **Project Manager** tab and select the corresponding IDE.  
4. Press the **GENERATE CODE** button.

### Configure and Build

The firmware is designed to be adaptable to different configurations, but it must be customised for your specific setup. Open the project in your IDE and navigate to the `Inc/configuration.h` file. Change the following variables to match your configuration:

| Variable Name | Example Value | Description |
|----------------|----------------|----------------|
| CHASSIS_LX  | 0.237  | Distance from chassis centre to wheel centre in metres (m) along the X-axis (left to right). |
| CHASSIS_LY  | 0.287  | Distance from chassis centre to wheel centre in metres (m) along the Y-axis (forward direction). |
| WHEEL_RADIUS | 0.0375 | Radius of each wheel in metres (m). |
| ENCODER_PPR | 3960 | Encoder pulses per revolution; multiply by 4 (e.g. 11×90×4). |
| MOTOR_GEAR_RATIO | 90 | Gear ratio of the motor. |
| MOTOR_MAX_SPEED | {10.948,11.424,11.1066,10.6306} | Maximum speed of each motor (wheel velocity in *ChassisTuner*). |
| PID_LEVEL_VELOCITY | {2.0f,5.0f,10.0f} | Velocity for each PID level (m/s). |
| PID_KP | {{6,5,6,6},{...},{...}} | Proportional gain constant for motor PID control. |
| PID_KI | {{6,5,6,6},{...},{...}} | Integral gain constant for motor PID control. |
| PID_KD | {{6,5,6,6},{...},{...}} | Derivative gain constant for motor PID control. |
| MOTOR_SPEED_RAMP | 0.1f | Speed ramp rate when decelerating the motor (m/s). |
| ENABLE_POWER_MONITORING | N/A | Enables INA226 power monitoring; comment out if not used. |
| POWER_MAXIMUM_CURRENT | 15.0f | Maximum current limit of the power supply (A). A higher value indicates an open circuit. |
| POWER_MINIMUM_VOLTAGE | 12.0f | Minimum operating voltage for the motor power supply (V). A lower value indicates a depleted battery. |
{.table}

Motor numbering starts from 1, and PID levels also start from 1.
{.alert .alert-info}

Once the modifications are complete, you can build and flash the firmware onto the device.
