---
title: Compile the Firmware
weight: 4
---

The firmware can be compiled using IDEs such as [MDK-Community Edition](https://www.keil.arm.com/mdk-community/) or [STM32CubeIDE for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension).

This guide explains how to compile the firmware using the command line, which is particularly useful for CI/CD pipelines. It has been tested on Ubuntu 24.04.

1. Install the dependencies.

```bash
sudo apt install --no-install-recommends cmake ninja-build gcc-arm-none-eabi libnewlib-arm-none-eabi
```

2. Clone the project repository.

```bash
git clone https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu.git
```

3. Navigate to the project directory in terminal.
4. Compile the firmware.

```bash
cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_TOOLCHAIN_FILE=./cmake/gcc-arm-none-eabi.cmake -S ./ -B ./build/Release -G Ninja
cmake --build ./build/Release
```

5. The firmware file `LGDXRobot2.elf` is located in the `build/Release` directory.
6. Flash the firmware using STM32CubeProgrammer.

## Configure

The firmware is designed to be adaptable to different configurations, but it must be customised for specific setup. Open the project in IDE and navigate to the `Inc/configuration.h` file. Change the following variables to match the configuration:

| Variable Name | Example Value | Description |
|----------------|----------------|----------------|
| CHASSIS_LX  | 0.082  | Distance from chassis centre to wheel centre in metres (m) along the X-axis (left to right). |
| CHASSIS_LY  | 0.104  | Distance from chassis centre to wheel centre in metres (m) along the Y-axis (forward direction). |
| WHEEL_RADIUS | 0.0375 | Radius of each wheel in metres (m). |
| ENCODER_PPR | 3960 | Encoder pulses per revolution, multiply by 4 (e.g. 11×90×4). |
| MOTOR_GEAR_RATIO | 90 | Gear ratio of the motor. |
| MOTOR_MAX_SPEED | {10.948,11.424,11.1066,10.6306} | Maximum speed of each motor. |
| PID_LEVEL_VELOCITY | {2.0f,5.0f,10.0f} | Velocity for each PID level (m/s). (From lower to higher.) |
| PID_KP | {{6,5,6,6},{...},{...}} | Proportional gain constant for motor PID control. (From lower level to higher and from motor 1 to motor 4.) |
| PID_KI | {{6,5,6,6},{...},{...}} | Integral gain constant for motor PID control. |
| PID_KD | {{6,5,6,6},{...},{...}} | Derivative gain constant for motor PID control. |
| MOTOR_SPEED_RAMP | 0.1f | Speed reduction when decelerating the motor (m/s). |
| POWER_MINIMUM_VOLTAGE | 12.0f | Minimum operating voltage for the motor power supply (V). |
{.table}

The configuration for PID can be adjusted in ChassisTuner
{.alert .alert-info}
