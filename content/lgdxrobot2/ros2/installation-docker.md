---
title: Installation - Docker
weight: 3
---

LGDXRobot2 ROS 2 is available as Docker images for both AMD64 and ARM64 architectures. It provides web interface access for GUI tools such as rqt, RViz2 and ChassisTuner.

## Permission Configuration

The host machine must be configured to allow access to the USB devices used by the robot. It can be done by installing the `LGDXRobot2 UDEV` package. It can be obtained from [here](https://gitlab.com/lgdxrobotics/lgdxrobot2-support/-/packages/53942608).

## Desktop Docker Image

The desktop images include ROS 2 GUI tools and provide a web interface suitable for remote control. After the container is started, the web interface becomes accessible at [http://localhost:3000](http://localhost:3000). For external access, the address `https://<host-ip>:3001` should be used.

The image may require access to USB devices, so it is necessary to mount the host's `/dev` and pass the appropriate cgroup rules. Below are the groups for the corresponding devices. The `--device-cgroup-rule` options may be removed if they are not required.

| Major Number | Device |
|-------------|--------|
| 81          | Camera (Optional) |
| 189         | Camera (Optional) |
| 188         | LiDAR (ttyUSB) |
| 166         | Controller Board (ttyACM) |
| 13          | Joystick |
{.table}

### Physical Robot

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v /dev:/dev \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2-desktop:latest
```

### Simulation

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2-desktop:latest
```

## Command-line Image

The command-line image is a smaller image that includes only the LGDXRobot2 ROS 2 packages.

```bash
docker run -it \
  --name lgdxrobot2 \
  yukaitung/lgdxrobot2-base:latest \
  bash
```

## Full Image

The full image includes the desktop image, Realsense ROS 2 and dependencies for building LGDXRobot2 packages.

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2-desktop:latest-full
```