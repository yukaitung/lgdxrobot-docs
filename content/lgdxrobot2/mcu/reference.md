---
title: Reference
weight: 6
---

This page introduces all types of data that can be received from the MCU, as well as the commands that can be sent to the MCU.

## Common Structs

The following are details of the structs used in communication. Check here if the data type starts with `MCU`.

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

This consists of the basic data such as transforms, motor speeds, and sensor data.

`McuData` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| type | char | Must be `MCU_DATA_TYPE` |
| transform | McuDof | Transform of the robot |
| motors_target_velocity | float[4] | Target velocity of the motors |
| motors_desired_velocity | float[4] | Desired velocity of the motors (for speed control) |
| motors_actual_velocity | float[4] | Actual velocity of the motors |
| motors_ccr | int[4] | Output of the PID controller and final PWM value |
| battery1 | McuPower | Power of battery 1 |
| battery2 | McuPower | Power of battery 2 |
| software_emergency_stop_enabled | bool | Whether the software emergency stop is enabled |
| hardware_emergency_stop_enabled | bool | Whether the hardware stop button is pressed |
| battery_low_emergency_stop_enabled | bool | Whether the battery level is too low for motor power |
{.table}

### Serial Number

The serial number of the MCU. Convert the bits to hexadecimal and concatenate them to obtain the full serial number.

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

PID settings for each motor.

`McuPid` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| type | char | Must be `MCU_PID_TYPE` |
| level_velocity | float[3] | Velocity for each PID level |
| p | float[3][4] | Proportional gain constant for motor PID control |
| i | float[3][4] | Integral gain constant for motor PID control |
| d | float[3][4] | Derivative gain constant for motor PID control |
| motors_maximum_speed | float[4] | Maximum speed of the motors |
{.table}

## PC to MCU (Write to MCU)

Please ensure the `command` variable is set correctly to prevent unexpected behaviour.
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

Set the speed of a single motor.

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
| level | float[3] | Velocity for each PID level |
{.table}

### Get PID

Get the PID settings of the motor. The MCU will return it via serial read.

`McuGetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_GET_PID_COMMAND_TYPE` |
{.table}

### Set PID

Set the PID settings for a single motor and a single level.

`McuSetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| command | char | Must be `MCU_SET_PID_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| level | uint8_t | Level number (0 to 2) |
| p | float | Proportional gain constant |
| i | float | Integral gain constant |
| d | float | Derivative gain constant |
{.table}

### Save PID

Save the PID settings and level velocities. These persist after reset but may be overwritten by a full chip erase.

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

Get the serial number of the MCU. The MCU will return it via serial read.

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
