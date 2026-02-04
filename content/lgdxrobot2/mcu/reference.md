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

### McuAxisRaw

| Variable Name | Type | Description |
|---------------|------|-------------|
| x | float | X-axis |
| y | float | Y-axis |
| z | float | Z-axis |
{.table}

### McuImuData

| Variable Name | Type | Description |
|---------------|------|-------------|
| accelerometer | McuAxisRaw | Accelerometer data |
| accelerometer_covariance | McuAxisRaw | Accelerometer covariance matrix major |
| gyroscope | McuAxisRaw | Gyroscope data |
| gyroscope_covariance | McuAxisRaw | Gyroscope covariance matrix major |
| magnetometer | McuAxisRaw | Magnetometer data |
| magnetometer_covariance | McuAxisRaw | Magnetometer covariance matrix major |
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
| response_time | uint32_t | Time (in microseconds) since the last PID loop |
| transform | McuDof | Transform of the robot |
| forward_kinematic | McuDof | Forward Kinematic of the robot |
| motors_target_velocity | float[4] | Target velocity of the motors |
| motors_desired_velocity | float[4] | Desired velocity of the motors (for speed control) |
| motors_actual_velocity | float[4] | Actual velocity of the motors |
| motors_ccr | int[4] | Output of the PID controller and final PWM value |
| battery1 | McuPower | Power of battery 1 |
| battery2 | McuPower | Power of battery 2 |
| imu | McuImuData | IMU data |
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
| pid_speed | float[3] | Speed for each PID level |
| p | float[3][4] | Proportional gain constant for motor PID control |
| i | float[3][4] | Integral gain constant for motor PID control |
| d | float[3][4] | Derivative gain constant for motor PID control |
| motors_maximum_speed | float[4] | Maximum speed of the motors |
{.table}

### Magnetometer Calibration Data

| Variable Name | Type | Description |
|---------------|------|-------------|
| type | char | Must be `MCU_MAGNETOMETER_CALIBRATION_DATA_TYPE` |
| hard_iron_max | float[3] | Hard iron maximum |
| hard_iron_min | float[3] | Hard iron minimum |
| soft_iron_matrix | float[9] | Soft iron matrix |
{.table}

## PC to MCU (Write to MCU)

Please ensure the `command` variable is set correctly to prevent unexpected behaviour.
{.alert .alert-info}

### Software Emergency Stop

Set the software emergency stop.

`McuSoftwareEmergencyStopCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SOFTWARE_EMERGENCY_STOP_COMMAND_TYPE` |
| enabled | bool | Whether to enable the software emergency stop |
{.table}

### Inverse Kinematics

Control the movement of the robot.

`McuInverseKinematicsCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_INVERSE_KINEMATICS_COMMAND_TYPE` |
| velocity | McuDof | Target velocity of the robot |
{.table}

### Motor Speed

Set the speed of a single motor.

`McuMotorCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_MOTOR_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| velocity | float | Target velocity of the motor |
{.table}

### Set PID Speed

Set the speed of the PID controller.

`McuSetPidSpeedCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SET_PID_SPEED_COMMAND_TYPE` |
| pid_speed | float[3] | Speed for each PID level |
{.table}

### Get PID

Get the PID settings of the motor. The MCU will return it via serial read.

`McuGetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_GET_PID_COMMAND_TYPE` |
{.table}

### Set PID

Set the PID settings for a single motor and a single level.

`McuSetPidCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SET_PID_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| level | uint8_t | Level number (0 to 2) |
| p | float | Proportional gain constant |
| i | float | Integral gain constant |
| d | float | Derivative gain constant |
{.table}

### Set Motor Maximum Speed

Set the maximum speed of all motors.

`McuSetMotorMaximumSpeedCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SET_MOTOR_MAXIMUM_SPEED_COMMAND_TYPE` |
| motor | uint8_t | Motor number (0 to 3) |
| speed | float[4] | Maximum speed of the motor |
{.table}

### Get Magnetometer Calibration Data

Get the magnetometer calibration data. The MCU will return it via serial read.

`McuGetMagCalibrationDataCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_GET_MAG_CALIBRATION_DATA_COMMAND_TYPE` |
{.table}

### Set Magnetometer Calibration Data

Set the magnetometer calibration data.

`McuSetMagCalibrationDataCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SET_MAG_CALIBRATION_DATA_COMMAND_TYPE` |
| hard_iron_max | float[3] | Hard iron maximum |
| hard_iron_min | float[3] | Hard iron minimum |
| soft_iron_matrix | float[9] | Soft iron matrix |
{.table}

### Get Serial Number

Get the serial number of the MCU. The MCU will return it via serial read.

`McuGetSerialNumberCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_GET_SERIAL_NUMBER_COMMAND_TYPE` |
{.table}

### Reset Transform

Reset the transform of the robot.

`McuResetTransformCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_RESET_TRANSFORM_COMMAND_TYPE` |
{.table}

### Save Configuration

This persist configuration after reset but may be overwritten by a full chip erase.

`McuSaveConfigurationCommand` is defined as follows:

| Variable Name | Type | Description |
|---------------|------|-------------|
| header 1 | uint8_t | Must be `MCU_HEADER1` |
| header 2 | uint8_t | Must be `MCU_HEADER2` |
| command | char | Must be `MCU_SAVE_CONFIGURATION_COMMAND_TYPE` |
{.table}
