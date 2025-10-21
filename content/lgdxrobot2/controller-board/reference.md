---
title: Reference
weight: 6
---

This page introduces the all kinds of data that can be received from the MCU as well as the commands that can be sent to the MCU.

## Common Structs

Those are the detail for the structs that are used in the communication. Check here if the daty type is starting from MCU.

### McuDof

| Variable Name | Type | Description |
|---------------|------|-------------|
| x | float | X-axis position |
| y | float | Y-axis position |
| rotation | float | Rotation |
{.table}

### McuPower

| Variable Name | Type | Description |
|---------------|------|-------------|
| voltage | float | Voltage |
| current | float | Current |
{.table}

## MCU to PC (Read from MCU)

### Robot Data

Consist of the basic data likes transforms, motor speeds and sensors data.

`McuData` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| type | char | Must be `MCU_DATA_TYPE` |
| transform | McuDof | Transform of the robot |
| motors_target_velocity | float[4] | Target velocity of the motors |
| motors_desire_velocity | float[4] | Desired velocity of the motors (For speed down control) |
| motors_actual_velocity | float[4] | Actual velocity of the motors |
| motors_ccr | int[4] | The output of the PID controller and the final PWM value |
| battery1 | McuPower | Power of the battery 1 |
| battery2 | McuPower | Power of the battery 2 |
| software_emergency_stop_enabled | bool | Whether the emergency stop is enabled |
| hardware_emergency_stop_enabled | bool | Whether the hardware stop is pressed |
| bettery_low_emergency_stop_enabled | bool | Whether the battery is low for motors power |
{.table}

### Serial Number

The serial number of the MCU, convert the bit to hex and concatenate them.

```cpp
QString serialNumber = QString("%1%2%3")
		.arg(mcuSerialNumber.serial_number1, 8, 16, QLatin1Char('0'))
		.arg(mcuSerialNumber.serial_number2, 8, 16, QLatin1Char('0'))
		.arg(mcuSerialNumber.serial_number3, 8, 16, QLatin1Char('0'))
		.toUpper();
```

`McuSerialNumber` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|  
| type | char | Must be `MCU_SERIAL_NUMBER_TYPE` |
| serial_number1 | uint32_t | Serial number of the MCU (Part 1) |
| serial_number2 | uint32_t | Serial number of the MCU (Part 2) |
| serial_number3 | uint32_t | Serial number of the MCU (Part 3) |
{.table}

### PID

The PID setting for each motor.

`McuPid` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| type | char | Must be `MCU_PID_TYPE` |
| level_velocity | float[3] | Velocity for each PID level |
| p | float[3][4] | Proportional gain constant for motor PID control |
| i | float[3][4] | Integral gain constant for motor PID control |
| d | float[3][4] | Derivative gain constant for motor PID control |
| motors_maximum_speed | float[4] | Maximum speed of the motor |
{.table}

## PC to MCU (Write to MCU)

Please ensure the command variable is set correctly to prevent unexpected behaviour.
{.alert .alert-info}

### Software Emergency Stop

Set the software emergency stop.

`McuSoftwareEmergencyStopCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SOFTWARE_EMERGENCY_STOP_COMMAND_TYPE` |
| enabled | bool | Whether to enable the software emergency stop |
{.table}

### Inverse Kinematics

Control the movement of the robot.

`McuInverseKinematicsCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_INVERSE_KINEMATICS_COMMAND_TYPE` |
| velocity | McuDof | Target velocity of the robot |
{.table}

### Motor Speed

Set the speed of the one motor.

`McuMotorCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_MOTOR_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| velocity | float | Target velocity of the motor |
{.table}

### Set Level Velocity

Set the level velocity of the PID controller.

`McuSetLevelVelocityCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SET_LEVEL_VELOCITY_COMMAND_TYPE` |
| level | float[3] | The velocity for each PID level |
{.table}

### Get PID

Get the PID setting of the motor, the MCU will return it from serial read.

`McuGetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_GET_PID_COMMAND_TYPE` |
{.table}

### Set PID

Set the PID setting of one motor and one level.

`McuSetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SET_PID_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| level | uint8_t | Level number (0 to 2) |
| p | float | Proportional gain constant for motor PID control |
| i | float | Integral gain constant for motor PID control |
| d | float | Derivative gain constant for motor PID control |
{.table}

### Save PID

Save the PID setting and the level velocity. It will presist after reset, but could be overwritten by full chip erase.

`McuSavePidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SAVE_PID_COMMAND_TYPE` |
{.table}

### Set Motor Maximum Speed

Set the maximum speed of all motors.

`McuSetMotorMaximumSpeedCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SET_MOTOR_MAXIMUM_SPEED_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| speed | float[4] | Maximum speed of the motor |
{.table}

### Get Serial Number

Get the serial number of the MCU, the MCU will return it from serial read.

`McuGetSerialNumberCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_GET_SERIAL_NUMBER_COMMAND_TYPE` |
{.table}

### Reset Transform

Reset the transform of the robot.

`McuResetTransformCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_RESET_TRANSFORM_COMMAND_TYPE` |
{.table}
