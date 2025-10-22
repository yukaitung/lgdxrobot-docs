---
title: Before Assembling
weight: 5
---

## Controller Board

Solder the header strip to the controller board (except for the relay module), then solder the green LED to D1 and the red LED to D2. Next, solder a 220 Ω resistor to R1 and a 4.7 kΩ resistor to both R2 and R3. Solder the PH2.0 connector to the board, ensuring the key is facing the letters, and then solder the XT30 connector to the board.

Install the modules onto the board. When installing the TB6612FNG modules, ensure the capacitor is facing the right side (both GND pins should face the left side), and the USB connector for the BackPill is facing the left side.

Ensure the TB6612FNG modules are installed correctly, as incorrect installation may cause them to explode.
{.alert .alert-danger}

If your relay module does not use the header strip, solder wires and connect them to the relay module. The top pin is 5V, the middle pin is GND, and the bottom pin is the signal pin.

## Power Supply

Solder the 18650 battery case to connect the batteries in series. Connecting additional batteries in series or parallel is acceptable. If you are using an 18650 battery protection board, solder the wires to the battery case as shown in the diagram.
