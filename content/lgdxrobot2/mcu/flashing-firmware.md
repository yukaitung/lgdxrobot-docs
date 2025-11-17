---
title: Flashing Firmware
weight: 3
---

Download the `.elf` file [here](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu/-/releases).

## Prerequisites

* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)
* ST-LINK V2

## Flashing

1. Plug the BlackPill into the ST-LINK V2, then connect the ST-LINK V2 to your computer.
2. Press the BOOT0 button on the BlackPill, then reset it to enter bootloader mode.
3. Launch STM32CubeProgrammer.
4. Click the **Connect** button on the right side of the window.
5. Select **Erasing & Programming** from the left side of the window (arrow pointing to a device icon).
6. Click **Browse** in the middle of the window and locate the firmware file (`.elf`).
7. Press **Start Programming**.
8. Wait for the firmware to be flashed.
9. Close STM32CubeProgrammer and reset the BlackPill.
10. You should hear a click sound from the relay module.

## Next Steps

If you are not planning to modify the firmware, you can skip to the ChassisTuner section.
