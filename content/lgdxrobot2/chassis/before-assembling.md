---
title: Before Assembling
weight: 5
---

## Controller Board

Solder the header strip to the controller board (except for the relay module), then solder the green LED to D1 and the red LED to D2. Next, solder a 220 Ω resistor to R1 and a 4.7 kΩ resistor to both R2 and R3. Solder the PH2.0 connector to the board, and then solder the XT30 connector to the board.

If your relay module does not use the header strip, solder wires directly and connect them to the relay module. The top pin is **5V**, the middle pin is **GND**, and the bottom pin is the **signal** pin.

![Image of controller board with soldered components](../img/soldering/board1.png)

Install the modules onto the board. When installing the **TB6612FNG** modules, ensure the capacitor faces the right-hand side (both **GND** pins should face the left-hand side), and the USB connector for the **BackPill** faces the left-hand side.

Ensure the TB6612FNG modules are installed correctly, as incorrect installation may cause them to explode.  
{.alert .alert-danger}

![Image of controller board with all modules installed](../img/soldering/board2.png)

## Power Supply

Solder the 18650 battery holders to connect the batteries in series. If a battery protection board is being used, connect it according to the manufacturer’s instructions.
