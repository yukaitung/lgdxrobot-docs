---
title: Programming (C++)
weight: 5
---

Communication with the MCU is managed via the STM32 Virtual COM Port, which is compatible with standard serial port programming. When initialising the connection to the MCU, ensure all settings (baud rate, data bits, etc.) are left at their default values. To reduce communication overhead, this project relies on raw data transfer. To programming, the lgdxrobot2.h must be included in the source code. This tutorial uses Qt as example as the functions are self-explanatory.

### Reading Data

The data received from the MCU starting with hex `0xAA55` and ending with hex `0xA55A`, we can use it to split the data. Assume the program have the complete first data packet.

```bash
[0xAA] [0x55] [Data for frame 1] [0xA5] [0x5A] [0xAA] [0x55] [Partial data for frame 2] ...
```

We can split it in Qt as follows:

```cpp
// Find the start of the data
int start = buffer.indexOf("\xAA\x55");

// Find the end of the data
int end = buffer.indexOf("\xA5\x5A", start + 2);

// Extract the data
QByteArray data = buffer.mid(start, end - start);
```

There are few types of data, we need to identify them at data[2]. The cases is defined in the lgdxrobot2.h. After identifying the type, we can create a struct, then copy the data to the struct. The structs contains the data we need and it is ready to use.

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

The logic for sending data is similar to reading data. We need to identify the command we send, then create a struct using the command struct. For example, we are sending the inverse kinematics command, to control the movement of the chassis.

```cpp
// Create McuInverseKinematicsCommand struct
McuInverseKinematicsCommand command;

// Set the command type
command.command = MCU_INVERSE_KINEMATICS_COMMAND_TYPE;

// Set the target velocity
command.velocity.x = 1.0f;
command.velocity.y = 0.0f;
command.velocity.rotation = 0.0f;

// Send the command
QByteArray ba(reinterpret_cast<const char*>(&command), sizeof(McuInverseKinematicsCommand));
serial.write(ba);
```
