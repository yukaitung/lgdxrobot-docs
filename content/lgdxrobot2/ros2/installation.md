---
title: Installation
weight: 2
---

LGDXRobot2 ROS2 is available as Docker images for both **AMD64** and **ARM64** architectures. It provides web interface access for GUI tools such as **rqt** and **RViz2**.

## Permission Configuration

The host machine must be configured to allow access to the USB devices used by the robot. The corresponding udev rules are stored in the `udev` folder. Copy the rules to `/etc/udev/rules.d` and reload them using the commands below:


```bash
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Desktop Images

The desktop images include ROS2 GUI tools and provide a web interface suitable for remote control. After starting the container, you can access the web interface at [http://localhost:3000](http://localhost:3000). For external access, use `https://<host-ip>:3001`.

The image may require access to USB devices, so it is necessary to mount the host's `/dev` and pass the appropriate cgroup rules. Below are the groups for the corresponding devices. You can remove the `--device-cgroup-rule` options if they are not needed.

| Major Number | Device |
|-------------|--------|
| 81          | Realsense |
| 189         | Realsense |
| 188         | LiDAR (ttyUSB) |
| 166         | Controller Board (ttyACM) |
| 13          | Joystick |
{.table}

### Simulation Only

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2.desktop:latest
```

### Basic Usage

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v /dev:/dev \
  --device-cgroup-rule='c 81:* rwm' \
  --device-cgroup-rule='c 189:* rwm' \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2.desktop:latest
```

### With Realsense IMU

Realsense IMU requires privileged mode.

Privileged mode is recommended for development purposes only.
{.alert .alert-warning}

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v /dev:/dev \
  --device-cgroup-rule='c 81:* rwm' \
  --device-cgroup-rule='c 189:* rwm' \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  --privileged \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2.desktop:latest
```

### For Older Hardware

For older version of Ubuntu, you may need to use the `security-opt` option.

Privileged mode and `--security-opt` are suitable for development purposes only.
{.alert .alert-warning}

```bash
docker run -d \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v /dev:/dev \
  --device-cgroup-rule='c 81:* rwm' \
  --device-cgroup-rule='c 189:* rwm' \
  --device-cgroup-rule='c 188:* rwm' \
  --device-cgroup-rule='c 166:* rwm' \
  --device-cgroup-rule='c 13:* rwm' \
  --privileged \
  --security-opt seccomp=unconfined \
  -p 3000:3000 \
  -p 3001:3001 \
  yukaitung/lgdxrobot2.desktop:latest
```