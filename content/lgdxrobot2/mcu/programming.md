---
title: Programming (Qt C++)
weight: 5
---

Communication with the MCU is managed via the STM32 Virtual COM Port, which is compatible with standard serial port programming. When initialising the connection to the MCU, ensure all settings (baud rate, data bits, etc.) remain at their default values. To reduce communication overhead, this project relies on raw data transfer. To program the MCU, include `lgdxrobot2.h` in the source code. This tutorial uses Qt as an example, as the functions are self-explanatory.

Big-endian devices may cause issues.
{.alert .alert-info}

### Reading Data

The data received from the MCU starts with the hex sequence `0xAA55` and ends with `0xA55A`. These markers can be used to split the data. Assume the program has received a complete first data packet.


```bash
[0xAA] [0x55] [Data for frame 1] [0xA5] [0x5A] [0xAA] [0x55] [Partial data for frame 2] ...
```

We can split the data in Qt as follows:

```cpp
// Find the start of the data
int start = buffer.indexOf("\xAA\x55");

// Find the end of the data
int end = buffer.indexOf("\xA5\x5A", start + 2);

// Extract the data
QByteArray data = buffer.mid(start, end - start);
```

There are several types of data, which can be identified using `data[2]`. The possible cases are defined in `lgdxrobot2.h.` After identifying the type, create the corresponding struct and copy the data into it. The struct will then contain all the required information and is ready to use.

```cpp
switch (data[2])
{
  case MCU_DATA_TYPE:
    McuData mcuData;
    memcpy(&mcuData, data.data(), sizeof(McuData));
    // Your function to process the data
    break;
  case MCU_SERIAL_NUMBER_TYPE:
    McuSerialNumber mcuSerialNumber;
    memcpy(&mcuSerialNumber, data.data(), sizeof(McuSerialNumber));
    // Your function to process the data
    break;
  case MCU_PID_TYPE:
    McuPid mcuPid;
    memcpy(&mcuPid, data.data(), sizeof(McuPid));
    // Your function to process the data
    break;
  default:
    break;
}
```

### Sending Data

The logic for sending data is similar to reading data. First, identify the command to be sent, then create the corresponding command struct and assign the required values. For example, to send an inverse kinematics command to control the movement of the chassis:

```cpp
// Create the McuInverseKinematicsCommand struct
McuInverseKinematicsCommand command;

// Set the header and command type corresponding to the inverse kinematics command
command.header1 = MCU_HEADER1;
command.header2 = MCU_HEADER2;
command.command = MCU_INVERSE_KINEMATICS_COMMAND_TYPE;

// Set the target velocities
command.velocity.x = 1.0f;
command.velocity.y = 0.0f;
command.velocity.rotation = 0.0f;

// Send the command over the serial port
QByteArray ba(reinterpret_cast<const char*>(&command), sizeof(McuInverseKinematicsCommand));
serial.write(ba);
```
