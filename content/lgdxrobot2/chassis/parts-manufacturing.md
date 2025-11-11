---
title: Parts Manufacturing
weight: 4
---

The parts are designed by LGDXRobotics and require manufacturing. The full set of files is available in the **LGDXRobot2 Design** repository ([GitLab](https://gitlab.com/yukaitung/lgdxrobot2-design) | [GitHub](https://github.com/yukaitung/lgdxrobot2-design)) and does not require any additional software to open.

## Chassis

The plates are manufactured by laser-cutting acrylic sheets. The DXF files are located in the `Chassis/Exports` folder. Send these files to a laser-cutting service and specify a thickness of 4 mm for the plates.

![Image of the plates](../img/manufacturing/plates.png)

## Controller Board

The controller board can be manufactured by any PCB manufacturer. The Gerber files are located in the `Board/Exports` folder. Compress the files into a ZIP archive and send them to the manufacturer. Ensure the board has two layers, and leave other options as default. You may choose any colour for the PCB.

![Image of controller plates](../img/manufacturing/board.png)

It is possible to create the controller board manually by soldering the components and wiring them on a prototype board, but this is not recommended as it can be difficult to debug.
