---
title: Getting Started
layout: sub-section
weight: 3
---

This section explains how to set up LGDXRobot Cloud, configure the map and workflow, and then start the first automation job. This tutorial is suitable for both physical and simulated robots.

## Prerequisites

### Physical LGDXRobot2

* The robot’s onboard computer has LGDXRobot2 ROS 2 installed.

### Other Physical Robots

* The robot’s onboard computer has LGDXRobot Cloud Adaptor installed and configured.

### Simulation Robot

* Webots
* Docker running the LGDXRobot2 ROS 2 Docker image.

## Step 1: Create Folders

Create a folder to store the certificates. For the simulation, create an additional folder to share the Webots files.

## Step 2: Run the Docker Image

For the desktop image, access the web interface at <http://localhost:3000/> or at `https://<ip>:3001` for a remote computer. If the terminal is closed, right-click on the desktop and relaunch it from the menu.

### Physical Robot

```bash
docker run -d \
  --name lgdxrobot2 \
  -v <path to certificates folder>:/config/keys \
  -v /dev:/dev \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  -e PUID=1000 \
  -e PGID=1000 \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2-desktop:latest
```

### Simulation Robot

1. Save the [local simulation server script](https://github.com/cyberbotics/webots-server/blob/main/local_simulation_server.py) on the host computer.
2. [Define WEBOTS_HOME environment variable](https://cyberbotics.com/doc/guide/compiling-controllers-in-a-terminal).
3. Run the simulation server.

```bash
python3 <path>/local_simulation_server.py
```

4. Run the LGDXRobot2 ROS 2 Docker image.

```bash
docker run --rm -it \
  -e PUID=1000 \
  -e PGID=1000 \
  -v <path to certificates folder>:/config/keys \
  -v <path to Webots share folder>:/config/share \
  -p 3000:3000 \
  -p 3001:3001 yukaitung/lgdxrobot2.desktop:latest
```

5. Access the web interface at [http://localhost:3000/](http://localhost:3000/)
6. On the terminal in the container, set the environment variable:

```bash
export WEBOTS_SHARED_FOLDER=<path to Webots share folder>:/config/share
```

Click the blue button in the middle-left to expand the settings. Paste the command into the Clipboard section, then paste it directly into the terminal.
{.alert .alert-info}

When running the simulation, the Webots GUI opens automatically on the host machine.
