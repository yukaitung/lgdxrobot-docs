---
title: MCU Communication
weight: 5
---

The communication is managed by STM32 Virtual Com Port, it is compatible to Serial Port programming. When initialising connection to MCU, keep all setting (Baud Rate, Data Bits, etc.) to default. To reduce overhead in communication, this project relys on raw data to communicate with MCU, below is an example to send command from PC. 

``` C++
int p = 1;
char ba[9];
// Command
ba[0] = 'V';
// Parameter 1
ba[1] = (p & 4278190080) >> 24;
ba[2] = (p & 16711680) >> 16;
ba[3] = (p & 65280) >> 8;
ba[4] = p & 255;
// Parameter 2
...
mySerial.write(ba, 9); // If you are using Qt
```

This project assumes char is 1 byte; int and float are 4 bytes.

## PC to MCU

| Description              | Command (char) | Parameter 1             | Parameter 2          | Parameter 3          | Parameter 4        |
|--------------------------|----------------|-------------------------|----------------------|----------------------|--------------------|
| Software E-Stop          | E              | Enable (int) (N2)       |                      |                      |                    |
| External IMU Data (N3)   | I              | Accel X-axis (float)    | Accel X-axis (float) | Accel X-axis (float) | Gyro Z-axis        |
| Motor Inverse Kinematics | M              | X Velocity (float)      | Y Velocity (float)   | w Velocity (float)   |                    |
| Motor PID                | P              | Motor Number (int) (N1) | P Constant (float)   | I Constant (float)   | D Constant (float) |
| Serial Number (N4)       | S              |                         |                      |                      |                    |
| Reset Transform          | T              |                         |                      |                      |                    |
| Single Motor Velocity    | V              | Motor Number (int) (N1) | Velocity (float)     |                      |                    |
{.table}

Note1: Motor number starting from 0

Note2: 0 = Disable, 1 = Enable

Note3: Using ROS convention

Note4: Start with pattern 0xAB

## MCU to PC

A message broadcast from MCU about every 10ms, below is the sequence of the message.

Version 1:

| Description              | Member                                          | Size (bytes) |
|--------------------------|-------------------------------------------------|--------------|
| 0xAA Pattern             | OxAA (char)                                     | 1            |
| Version                  | version (unsigned short)                        | 1            |
| Frame Total Size         | Size (char)                                     | 1            |
| Refresh Time ms          | Refresh Time ms (unsigned short)                | 2            |
| Transform                | x, y, w (3 float)                               | 12           |
| Forward Kinematic        | x velocity, y velocity, w velocity (3 float)    | 12           |
| Target Wheels Velocity   | wheel1, wheel2, wheel3, wheel4 (4 float)        | 16           |
| Measured Wheels Velocity | wheel1, wheel2, wheel3, wheel4 (4 float)        | 16           |
| P Constant               | wheel1, wheel2, wheel3, wheel4 (4 float)        | 16           |
| I Constant               | wheel1, wheel2, wheel3, wheel4 (4 float)        | 16           |
| D Constant               | wheel1, wheel2, wheel3, wheel4 (4 float)        | 16           |
| Battery Voltage          | Battery 1, Battery 2 (N1) (unsigned short)      | 4            |
| E-Stop Enabled           | MSB Software bit (N2), Hardware bit (N3) (char) | 1            |
|                          | Total                                           | 114          |
{.table}

Note1: he chassis has 2 power source, Battery 1 is moter, Battery 2 is for computer

Note2: 0 = Disable, 1 = Enable

Note3: Software E-Stop can triggers this because of circuit design
