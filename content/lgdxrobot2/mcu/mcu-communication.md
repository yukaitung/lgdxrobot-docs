---
title: MCU Communication
weight: 5
---

Communication with the MCU is managed via the STM32 Virtual COM Port, which is compatible with standard serial port programming. When initialising the connection to the MCU, ensure all settings (baud rate, data bits, etc.) are left at their default values. To reduce communication overhead, this project relies on raw data transfer. Below is an example of sending a command `Single Motor Velocity` from the PC:

```c++
int p = 1;
char ba[9];
// Command
ba[0] = 'V';
// Parameter 1
ba[1] = (p & 0xFF000000) >> 24;
ba[2] = (p & 0x00FF0000) >> 16;
ba[3] = (p & 0x0000FF00) >> 8;
ba[4] = p & 0x000000FF;
// Parameter 2
...
mySerial.write(ba, 9); // If you are using Qt
```

This project assumes `char` is 1 byte; `int` and `float` are 4 bytes.

## PC to MCU

| Description              | Command (char) | Parameter 1             | Parameter 2          | Parameter 3          | Parameter 4        |
|--------------------------|----------------|-------------------------|----------------------|----------------------|--------------------|
| Software E-Stop          | E              | Enable (int) (Note 2)   |                      |                      |                    |
| External IMU Data (Note 3)| I             | Accel X-axis (float)    | Accel Y-axis (float) | Accel Z-axis (float) | Gyro Z-axis (float)|
| Motor Inverse Kinematics | M              | X Velocity (float)      | Y Velocity (float)   | ω Velocity (float)   |                    |
| Motor PID                | P              | Motor Number (int) (Note 1)| P Constant (float) | I Constant (float)   | D Constant (float) |
| Serial Number (Note 4)   | S              |                         |                      |                      |                    |
| Reset Transform          | T              |                         |                      |                      |                    |
| Single Motor Velocity    | V              | Motor Number (int) (Note 1)| Velocity (float)   |                      |                    |
{.table}

*Note 1:* Motor numbering starts from 0  
*Note 2:* 0 = Disable, 1 = Enable  
*Note 3:* Uses ROS conventions  
*Note 4:* Starts with pattern `0xAB`

## MCU to PC

The MCU broadcasts a message approximately every 10 ms. Below is the sequence of the message for Version 1:

| Description              | Member                                          | Size (bytes) |
|--------------------------|-------------------------------------------------|--------------|
| Start Pattern            | 0xAA (char)                                     | 1            |
| Version                  | version (unsigned short)                        | 1            |
| Frame Total Size         | size (char)                                     | 1            |
| Refresh Time (ms)        | refresh time (unsigned short)                   | 2            |
| Transform                | x, y, ω (3 floats)                              | 12           |
| Forward Kinematics       | x velocity, y velocity, ω velocity (3 floats)  | 12           |
| Target Wheel Velocities  | wheel1, wheel2, wheel3, wheel4 (4 floats)      | 16           |
| Measured Wheel Velocities| wheel1, wheel2, wheel3, wheel4 (4 floats)      | 16           |
| P Constants              | wheel1, wheel2, wheel3, wheel4 (4 floats)      | 16           |
| I Constants              | wheel1, wheel2, wheel3, wheel4 (4 floats)      | 16           |
| D Constants              | wheel1, wheel2, wheel3, wheel4 (4 floats)      | 16           |
| Battery Voltages         | Battery 1, Battery 2 (Note 1) (unsigned short) | 4            |
| E-Stop Status            | MSB Software bit (Note 2), Hardware bit (Note 3) (char) | 1          |
| **Total**                |                                                 | **114**      |
{.table}

*Note 1:* The chassis has two power sources; Battery 1 powers the motors, Battery 2 powers the computer  
*Note 2:* 0 = Disabled, 1 = Enabled  
*Note 3:* Software E-Stop can trigger this status due to the circuit design
