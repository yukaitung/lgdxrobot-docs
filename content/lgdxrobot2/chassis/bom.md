---
title: Bill of materials (BOM)
weight: 3
---

## Chassis

| Item Name | Quantity | Notes |
|------------|-----------|--------|
| LGDXRobot2 Chassis Plates | 1 | The instrustion is on the next page |
| GM37-520 DC Gear Motor (12V) | 4 | A gear ratio of at least **1:90** is recommended to ensure sufficient torque. The motor must include an **encoder**, and the **connector type is PH2.0**. |
| Mounting Bracket for 37mm DC Gear Motor (with screws) | 4 | These brackets are sometimes included when purchasing the motor. |
| Mecanum Wheel Set | 1 set (4 wheels) | It is recommended to choose wheels with a **75–80 mm diameter** and **32+ mm width**. The **coupler must be 6 mm** to fit the motor shaft. |
| M4 Screws (12 mm length) | 44 | Only **20** screws must be exactly 12 mm in length; you may use other lengths for the remaining **24**. |
| M4 Nuts | 18 | — |
| M4 Standoffs (70 mm) | 8 | — |
| M4 Standoffs (35 mm) | 8 | — |
{.table}

## Controller Board

| Item Name | Quantity | Notes |
|-----------|----------|-------|
| LGDXRobot2 Controller Board | 1 | The instructions are provided on the next page. |
| BlackPill (STM32F411CEU6) | 1 | [Official GitHub (not an affiliate link)](https://github.com/WeActStudio/WeActStudio.MiniSTM32F4x1) |
| TB6612FNG Module | 2 | — |
| INA226 Module | 2 | Optional. The **shunt resistor** must be **R010** to support high current. |
| Relay Module | 1 | — |
| 3.5 mm Red LED | 1 | — |
| 3.5 mm Green LED | 1 | — |
| Resistor (220 Ω) | 1 | — |
| Resistor (4.7 kΩ) | 1 | — |
| 2.54 mm (0.1 inch) Header Strip (Female) | Total 68 pins | Optional if you want to **solder** modules on the board. |
| XT30 Connector (Male & Female) | 1 | Optional if you want to **solder** wires on the board. |
| PH2.0 Connector (Female) | 4 | — |
| PH2.0 Cable (15cm) | 4 | — |
{.table}

## Power Supply

| Item | Quantity | Notes |
|------|-----------|--------|
| 18650 Battery | 8 | — |
| 18650 Battery Case | 2 | — |
| 18650 Battery Protection Board | 2 | Optional |
| 12V DC-DC Buck Converter | 1 | — |
| 5V DC-DC Buck Converter | 1 | You may choose another voltage if you are using NUC. |
| DC Power Jack / USB Cable | 1 | Depends on the power input for your computer |
{.table}

You may design your own power supply, but please note that the motor voltage is 12 V.
{.alert .alert-info}

## Miscellaneous

| Item | Quantity | Notes |
|------|----------|-------|
| Emergency Stop Button | 1 | — |
| Power Switch | 1 | — |
| Cables | Suitable length | — |
{.table}

## Computer (NUC)

You can either choose the NUC setting or the Single Board Computer (SBC) setting.
{.alert .alert-info}

| Item | Quantity | Notes |
|------|----------|-------|
| NUC | 1 | Only Slim Kit is supported. (37mm height) |
| M3 Screws (10 mm length) | 2 | — |
{.table}

## Computer (SBC)

| Item | Quantity | Notes |
|------|----------|-------|
| Raspberry Pi or NVIDIA Jetson Nano | 1 | — |
| M2.5 Screws (8 mm length) | 4 | — |
| M2.5 Standoffs (16 mm) | 4 | — |
{.table}

## Sensors

| Item | Quantity | Notes |
|------|----------|-------|
| RPLIDAR A1 or C1 | 1 | — |
| M2.5 Screws (8 mm length) | 4 | — |
| RealSense D435 Camera | 1 | Optional |
| 1/4-Inch Tripod Screw | 1 | Optional |
{.table}

## Tools (Not installed on the robot)

| Item | Quantity | Notes |
|------|----------|-------|
| Hex Key Set | 1 | — |
| 7 mm Wrench | 1 | — |
| Crosshead Screwdriver | 1 | — |
| Soldering Iron | 1 | — |
| Solder Paste | 1 | — |
| Hot Glue Gun / Strong Double Sided Tape | 1 | — |
| ST-LINK V2 | 1 | For flashing the MCU firmware. |
{.table}
