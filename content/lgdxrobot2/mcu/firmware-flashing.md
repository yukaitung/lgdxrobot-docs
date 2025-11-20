---
title: Firmware Flashing
weight: 3
---

The firmware can be found in the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu/-/releases) page for the MCU project.

## Prerequisites

* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)
* ST-LINK V2

## Flashing

1. Download the latest firmware from [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu/-/releases) page.
2. Plug the BlackPill into the ST-LINK V2, then connect the ST-LINK V2 to the computer.
3. Press the BOOT0 button on the BlackPill, then reset it to enter bootloader mode.
4. Launch STM32CubeProgrammer.
5. Click the **Connect** button on the right side of the window.
6. Select **Erasing & Programming** from the left side of the window (arrow pointing to a device icon).
7. Click **Browse** in the middle of the window and locate the firmware file (`.elf`).
8. Press **Start Programming**.
9. Wait for the firmware to be flashed.
10. Close STM32CubeProgrammer and reset the BlackPill.
11. A click sound should be heard from the relay module.

## Next Steps

If there are no plans to modify the firmware, skip to the ChassisTuner section.
