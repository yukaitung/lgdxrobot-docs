---
title: Installation
weight: 2
---

LGDXRobot2 ROS2 is available as Docker images for both AMD64 and ARM64 architectures. You can choose either the desktop images or the command-line images.

## Desktop Images

The desktop images include ROS2 GUI tools and provide a web interface suitable for remote control. After starting the container, you can access the web interface at [http://localhost:3000](http://localhost:3000).

### With Webots

```bash
docker run -it --name lgdxrobot2 yukaitung/lgdxrobot2.desktop:latest
```

### Without Webots

```bash
docker run -it --name lgdxrobot2 yukaitung/lgdxrobot2.desktop:latest-lite
```

## Command Line Images

### With Webots

```bash
docker run -it --name lgdxrobot2 yukaitung/lgdxrobot2:latest
```

### Without Webots

```bash
docker run -it --name lgdxrobot2 yukaitung/lgdxrobot2:latest-lite
```
