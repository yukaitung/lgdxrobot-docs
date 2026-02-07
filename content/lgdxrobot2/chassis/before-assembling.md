---
title: Before Assembling
weight: 5
---

## Controller Board

1. **Header Strips:** Solder the header strips to the controller board (excluding the relay module).
2. **LED:** Solder the red LED to **D1**
3. **Resistors:** Solder a **220 Ω** resistor to **R1**, **68 kΩ** resistors to **R2–R4**, and **10 kΩ** resistors to **R5–R7**.
4. **Capacitors:** Solder **0.1 µF** capacitors to **C1–C3**.
5. **Connectors:** Solder the **PH2.0** connectors and the **XT30** connector to the board.
6. **Relay Module:** If the relay module does not use the header strip, solder wires directly to the board and connect them to the module. The pinout is: **Left (Signal)**, **Middle (GND)** and **Right (5V)**.
7. **Optional Jumper:** Optionally, solder a wire to connect the **GND** pins of **+J2** and **+J3** (note: both pin numbers are Ground).

![Image of controller board with soldered components](../img/soldering/board1.png)

8. **Module Installation:** 
    * **TB6612FNG:** Ensure the capacitor faces the **bottom** side (both **GND** pins should face the **up** side).
    * **BlackPill:** The USB connector must face the **top** side.
    * **ICM-20948:** Ensure the chip is facing the **right-hand** side.
    * **Relay Module**

Warning: Ensure the TB6612FNG modules are installed correctly, as incorrect installation may cause them to explode.  
{.alert .alert-danger}

![Image of controller board with all modules installed](../img/soldering/board2.png)

## Power Supply

No matter the type of power supply or configuration, it is recommended to connect the battery in an easy-to-remember orientation and label the polarity clearly.
{.alert .alert-danger}

Connect the 18650 batteries in series. If a battery protection board is being used, connect it according to the manufacturer’s instructions. Then attach the battery protection board to the battery holder using hot glue.

![Image of the power supply with batteries connected](../img/soldering/power.png)