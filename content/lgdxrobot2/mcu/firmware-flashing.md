---
title: Firmware Flashing and Usage
weight: 3
---

The firmware can be found in the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu/-/releases) page for the MCU project.

## Prerequisites

* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)

## Flashing

1. Download the latest firmware from [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-mcu/-/releases) page.
2. Connect the USB-C Port on the BlackPill to the computer.
3. Press the BOOT0 button on the BlackPill, then reset it to enter bootloader mode.  
4. Launch STM32CubeProgrammer.  
5. On the right-hand side of the window, the drop-down menu shows **ST-LINK**. Change it to **USB** and click **Connect**.
6. Select **Erasing & Programming** from the left side of the window (arrow pointing to a device icon).
7. Click **Browse** in the middle of the window and locate the firmware file (`.elf`).
8. Press **Start Programming**.
9. Wait for the firmware to be flashed.
10. Close STM32CubeProgrammer and reset the BlackPill.

## Usage

The robot needs to calibrate the IMU, so it must be placed on a flat surface.

1. After powering on the controller, wait approximately 3 seconds for the calibration to complete.
2. A clicking sound will be heard from the relay.
3. The red LED will turn off.

## Next Steps

If there are no plans to modify the firmware, skip to the ChassisTuner section.
