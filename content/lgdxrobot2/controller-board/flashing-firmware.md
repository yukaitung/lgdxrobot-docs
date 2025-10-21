---
title: Flashing Firmware
weight: 3
---

The firmware can be found in the [lgdxrobot2-mcu](https://gitlab.com/yukaitung/lgdxrobot2-mcu) repository. Download the elf file for the latest release.

## Prerequisites

* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)
* ST-LINK V2

## Flashing

1. Plugin the BlackPill to the ST-LINK V2, then plug the ST-LINK V2 to the computer.
2. Press BOOT0 button on the BlackPill then reset to enter the bootloader mode.
3. Launch STM32CubeProgrammer
4. Press Connect button on the right side of the window
5. Select the Erasing & Programming option of the left side of the window (Arrow to a device icon)
6. Press Browse at the middle of the window and locate the firmware file (.elf)
7. Press Start Programming
8. Wait for the firmware to be flashed
9. Close STM32CubeProgrammer and reset the BlackPill
10. You should hear the click sound from the relay module

## Next Steps

If you are not interested in modifying the firmware, you can skip to the ChassisTuner section.
