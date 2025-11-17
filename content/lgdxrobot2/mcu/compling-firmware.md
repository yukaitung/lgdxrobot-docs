---
title: Compling Firmware
weight: 4
---

## Build

Assume that you are using Ubuntu 24.04.

1. Install the dependencies.

```bash
sudo apt install --no-install-recommends cmake ninja-build gcc-arm-none-eabi libnewlib-arm-none-eabi
```

2. Clone the project repository.

```bash
git clone https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu.git
```

3. Navigate to the project directory in terminal.
4. Build the firmware.

```bash
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=./cmake/gcc-arm-none-eabi.cmake -S ./ -B ./build/Release -G Ninja
cmake --build ./build/Release
```

5. Locate the firmware file (`.elf`) in the `build/Release` directory.
6. Flash the firmware using STM32CubeProgrammer.

## Configure

The firmware is designed to be adaptable to different configurations, but it must be customised for your specific setup. Open the project in your IDE and navigate to the `Inc/configuration.h` file. Change the following variables to match your configuration:

| Variable Name | Example Value | Description |
|----------------|----------------|----------------|
| CHASSIS_LX  | 0.082  | Distance from chassis centre to wheel centre in metres (m) along the X-axis (left to right). |
| CHASSIS_LY  | 0.104  | Distance from chassis centre to wheel centre in metres (m) along the Y-axis (forward direction). |
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
