---
title: Getting Started
layout: sub-section
weight: 3
---

This section explains how to set up LGDXRobot Cloud, configure the map and workflow, and then start your first automation job. This tutorial is suitable for both physical and simulated robots, and it uses the LGDXRobot2 Docker image.

## Prerequisites

### Physical Robot

* LGDXRobot2 with LGDXRobot2 ROS 2 installed

### Simulation Robot

* LGDXRobot2 ROS 2
* Webots

## Step 1: Create a Folders

Create a folder to store the certificates, and if you are using simulation, create an additional folder to share the Webots files.

## Step 2: Run the Docker Image

### Physical Robot

```bash
docker run -d \
  --name lgdxrobot2 \
  -v <path to keys>:/config/keys \
  -v /dev:/dev \
  --device-cgroup-rule='c 81:* rwm' \
  --device-cgroup-rule='c 189:* rwm' \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  --privileged \
  -e PUID=1000 \
  -e PGID=1000 \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2-desktop:latest
```

### Simulation Robot

```bash
docker run --rm -it \
  -e PUID=1000 \
  -e PGID=1000 \
  -v <path to keys>:/config/keys \
  -v <path to Webots files>:/config/share \
  -p 3000:3000 \
  -p 3001:3001 yukaitung/lgdxrobot2.desktop:latest
```

For the desktop image, access the web interface at <http://localhost:3000/> or at `https://<ip>:3001` for a remote computer. If the terminal is closed, right-click on the desktop and relaunch it from the menu.