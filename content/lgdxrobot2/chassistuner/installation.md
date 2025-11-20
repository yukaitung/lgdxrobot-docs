---
title: Installation
weight: 2
---

The software is available on the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner/-/releases) page of the ChassisTuner project. It provides binary releases for Linux on both AMD64 and ARM64 architectures.

Additionally, it is included in the LGDXRobot2 Desktop Docker image (`yukaitung/lgdxrobot2-desktop`).

## Instructions

The following instructions assume that Ubuntu 24.04 is being used.

1. Install the following packages:

```bash
sudo apt install libxkbcommon-x11-0 libxcb-cursor0 libxcb-icccm4 libxcb-keysyms1
```

2. Download the binary from the [Releases](https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner/-/releases) page.
3. Extract the downloaded archive.
4. Launch the program from `bin/ChassisTuner`.
