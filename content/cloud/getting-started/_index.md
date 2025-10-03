---
title: Getting Started
layout: sub-section
weight: 2
---

This section explains how to set up LGDXRobot Cloud, including the fleet and workflow. After that, you can start your first job. This tutorial relies on the simulation, and LGDXRobot2 ROS2 is required. LGDXRobotics provides a Docker image for running ROS2 with all dependencies, so installing ROS2 separately is not necessary.

### Step 1: Create a Folder for Storing the Certificates

Create a folder for storing the certificates and remember its path.

### Step 2: Run the Docker Image

Run the following command to start the image. Replace `<path to keys>` with the folder you just created.

```bash
docker run --rm -it \
  -e PUID=1000 \
  -e PGID=1000 \
  -v <path to keys>:/config/keys \
  -p 3000:3000 \
  -p 3001:3001 yukaitung/lgdxrobot2.desktop:latest
```

Then, you can access the web interface at [http://localhost:3000/](http://localhost:3000/). If the terminal is closed, you can right-click on the desktop and relaunch it from the menu.
