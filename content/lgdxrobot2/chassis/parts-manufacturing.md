---
title: Parts Manufacturing
weight: 4
---

The parts are designed by LGDXRobotics and require manufacturing. The design files can be found in the [lgdxrobot2-design](https://gitlab.com/yukaitung/lgdxrobot2-design) repository. These files do not require any additional software to open.

## Chassis

The plates are manufactured by laser cutting acrylic sheets. The DXF files are located in the `Chassis/Exports` folder. Send these files to a laser cutting service and specify a thickness of 4 mm for the plates.

## Controller Board

The controller board can be manufactured by any PCB manufacturer. The Gerber files are located in the `Board/Exports` folder. Compress the files into a ZIP archive and send them to the manufacturer. Ensure the board has two layers, and leave other options as default. You may select any colour for the PCB.

It is possible to create the controller board manually by soldering the components and wiring on a prototype board, but this is not recommended as it can be difficult to debug.
