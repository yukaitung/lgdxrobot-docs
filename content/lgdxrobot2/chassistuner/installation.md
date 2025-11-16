---
title: Installation
weight: 2
---

LGDXRobot2 ChassisTuner only distributes binary releases for Linux on both amd64 and arm64. Also, it is included in the [LGDXRobot2 Desktop Docker image](https://hub.docker.com/r/yukaitung/lgdxrobot2.desktop).

Only the latest version of the binary is retained, and the download links for all releases point to the same file.
{.alert .alert-info}

## Instructions

1. Ensure that you have Ubuntu 24.04 with the Desktop environment installed.
2. Install the following packages:

```bash
sudo apt install libxkbcommon-x11-0 libxcb-cursor0 libxcb-icccm4 libxcb-keysyms1
```

3. Download the binary from the [GitLab releases page](https://gitlab.com/yukaitung/lgdxrobot2-chassistuner/-/releases).
4. Extract the downloaded archive.
5. Launch the binary from `build/ChassisTuner-<arch>/bin/ChassisTuner`.
