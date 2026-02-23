---
title: Bill of materials (BOM)
weight: 3
---

## Chassis

| Item Name | Quantity | Notes | Image |
|-----------|----------|-------|-------|
| LGDXRobot2 Chassis Plates | 1 | The instructions are provided on the next page. | ![Image of the chassis plates](../img/bom/chassis_plates.png) |
| GM37-520 DC Gear Motor (12V) | 4 | A gear ratio of at least **1:90** is recommended to ensure sufficient torque. The motor must include an **encoder**, and the **connector type is PH2.0**. | ![Image of the motors](../img/bom/chassis_motor.png) |
| Mounting Bracket for 37mm DC Gear Motor (with screws) | 4 | These brackets are sometimes included when purchasing the motor. | ![Image of the motor brackets](../img/bom/chassis_bracket.png) |
| Mecanum Wheel Set | 1 set (4 wheels) | It is recommended to choose wheels with a **75–80 mm diameter** and **32+ mm width**. The **coupler must be 6 mm** to fit the motor shaft. | ![Image of the wheels](../img/bom/chassis_wheel.png) |
| M4 Screws (12 mm length) | 44 | Only **20** screws must be exactly 12 mm in length; Longer screws may be used for the remaining **24** screws. | ![Image of the screws](../img/bom/chassis_screw.png) |
| M4 Nuts | 18 | — | ![Image of the nuts](../img/bom/chassis_nut.png) |
| M4 Standoffs (70 mm) | 8 | — | ![Image of the standoffs](../img/bom/chassis_standoff_70.png) |
| M4 Standoffs (35 mm) | 4 | — | ![Image of the standoffs](../img/bom/chassis_standoff_35.png) |
{.table .table-img}

## Controller Board

| Item Name | Quantity | Notes | Image |
|-----------|----------|-------|-------|
| LGDXRobot2 Controller Board | 1 | The instructions are provided on the next page. | ![Image of the controller board](../img/bom/controller_cb.png) |
| BlackPill (STM32F411CEU6) | 1 | [Official GitHub (not an affiliate link)](https://github.com/WeActStudio/WeActStudio.MiniSTM32F4x1) | ![Image of the BlackPill](../img/bom/controller_mcu.png) |
| TB6612FNG Module | 2 | — | ![Image of the TB6612FNG](../img/bom/controller_tb6612.png) |
| ICM-20948 | 1 | Must be V1 as the pins of V2 is not compatible with the controller board. | ![Image of the ICM-20948](../img/bom/controller_icm20948.png) |
| Relay Module | 1 | Triggers when the input is high. | ![Image of the Relay Module](../img/bom/controller_relay.png) |
| 3.5 mm Red LED | 1 | — | ![Image of the LED](../img/bom/controller_led.png) |
| Resistor (220 Ω) | 1 | — | ![Image of the resistor](../img/bom/controller_resistor_220.png) |
| Resistor (10 kΩ) | 3 | — | ![Image of the resistor](../img/bom/controller_resistor_10k.png) |
| Resistor (68 kΩ) | 3 | — | ![Image of the resistor](../img/bom/controller_resistor_68k.png) |
| Capacitor (0.1 µF) | 3 | — | ![Image of the capacitor](../img/bom/controller_capacitor.png) |
| 2.54 mm (0.1 inch) Header Strip (Female) | Suitable | — | ![Image of the header strip](../img/bom/controller_header_strip.png) |
| XT30 Connector (Male & Female) | 1 | Optional for soldering wires onto the board. | ![Image of the XT30 connector](../img/bom/controller_xt30.png) |
| PH2.0 2P Connector (Female) | 3 | — | ![Image of the PH2.0 connector](../img/bom/controller_ph202pf.png) |
| PH2.0 2P Cable (Male) | 3 | — | ![Image of the PH2.0 cable](../img/bom/controller_ph202pm.png) |
| PH2.0 6P Connector (Female) | 4 | — | ![Image of the PH2.0 connector](../img/bom/controller_ph206pf.png) |
| PH2.0 6P Cable (~15 cm) | 4 | The keys face opposite directions. | ![Image of the PH2.0 cable](../img/bom/controller_ph206pm.png) |
{.table .table-img}

## Power Supply

| Item Name | Quantity | Notes | Image |
|-----------|----------|-------|-------|
| 18650 Battery | 8 | — | ![Image of the battery](../img/bom/power_battery.png) |
| 18650 Battery Holder | 2 | 4 batteries in series. | ![Image of the battery holder](../img/bom/power_holder.png) |
| 18650 Battery Protection Board | 2 | Optional | ![Image of Battery Protection Board](../img/bom/bms.jpg) |
| 12V DC-DC Buck Converter | 1 | For the motors. | ![Image of the DC-DC Buck Converter](../img/bom/power_12v.png) |
| 5V / 12V DC-DC Buck Converter. | 1 | For the onboard computer, choose the voltage that matches the input voltage of the computer | ![Image of the DC-DC Buck Converter](../img/bom/power_5v.png) |
| DC Power Jack / USB Cable | 1 | Depends on the power input for the computer. | — |
{.table .table-img}

A custom power supply may be designed, but note that the motor voltage is 12 V.
{.alert .alert-info}

## Miscellaneous

| Item Name | Quantity | Notes | Image |
|-----------|----------|-------|-------|
| Emergency Stop Button | 1 | — | ![Image of Emergency Stop Button](../img/bom/e-stop.jpg) |
| Power Switch | 1 | — | ![Image of Power Switch](../img/bom/power-switch.jpg) |
| Cables | Suitable length | — | ![Image of the cables](../img/bom/cable.png) |
{.table .table-img}

## Onboard Computer

Either the NUC setting or the Single Board Computer (SBC) setting may be chosen.
{.alert .alert-info}

### NUC

| Item | Quantity | Notes |
|------|----------|-------|
| NUC | 1 | Only Slim Kit is supported. (37mm height) |
| M3 Screws (10 mm length) | 2 | — |
{.table}

### SBC

| Item | Quantity | Notes |
|------|----------|-------|
| Raspberry Pi or NVIDIA Jetson Nano | 1 | — |
| M2.5 Screws (8 mm length) | 4 | — |
| M2.5 Standoffs (16 mm) | 4 | — |
{.table}

## Sensors

| Item Name | Quantity | Notes | Image |
|-----------|----------|-------|-------|
| RPLIDAR A1 or C1 | 1 | — | ![Image of the RPLIDAR](../img/bom/lidar.png) |
| M2.5 Screws (8 mm length) | 4 | — |
| Camera | 1 | Optional, it was originally designed for the Realsense D435, but any camera that can be fitted in the chassis is acceptable.
| 1/4-Inch Tripod Screw | 1 | Optional | ![Image of Tripod Screw](../img/bom/tripod-screw.jpg) |
{.table .table-img}

## Tools (Not installed on the robot)

| Item |
|------|
| Hex Key Set |
| 7 mm Wrench |
| Crosshead Screwdriver |
| Soldering Iron |
| Solder Paste |
| Hot Glue Gun / Strong Double Sided Tape |
{.table}

## Notes for the Onboard Computer

The minimum requirement for the onboard computer is a Raspberry Pi 5 4GB. It is capable of running SLAM on Nav2 with the RViz GUI, as well as computationally intensive Nav2 plugins. The recommended screen resolution is 1920 × 1080. Please refer to [this video](https://www.youtube.com/watch?v=PddIeZP-wgw) for instructions on using a custom power supply with a Raspberry Pi 5.

The power supply listed here is for stepping down to 12V / 5V. If the onboard computer is powered by 19V, the component should be modified, for example by using a step-up converter.

Although the Raspberry Pi 4 or Nvidia Jetson Nano (older version) can technically be used, this is not recommended due to insufficient computational power. The robot’s movement is jittery.
