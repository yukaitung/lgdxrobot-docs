---
title: Establishing a Robot Connection
weight: 5
---

Before running the first automation task, connect a robot to the system so that it can receive the task.

## Step 1: Connect a Robot

Ensure that the PATH is set up correctly and the terminal running SLAM mode is closed. The map file should be found in the current directory.

### Physical Robot

```bash
ros2 launch lgdxrobot2_bringup nav.launch.py \
  use_cloud:=True \
  map:=<Absolute path to the map yaml file> \
  cloud_address:=<Address of the cloud with port> \
  cloud_root_cert:="/config/keys/root.crt" \
  cloud_client_key:="/config/keys/My Robot.key" \
  cloud_client_cert:="/config/keys/My Robot.crt"
```

### Simulation Robot

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  use_cloud:=True \
  profile:='loc-sim' \
  cloud_address:=<Address of the cloud with port or 'host.docker.internal:5162'> \
  cloud_root_cert:="/config/keys/root.crt" \
  cloud_client_key:="/config/keys/My Robot.key" \
  cloud_client_cert:="/config/keys/My Robot.crt"
```

The map parameter can be omitted in simulation because it has a default map.
{.alert .alert-info}

## Step 2: Check the Connection

Click **Home** then click **Robots** on the top menu bar. If the connection is successful, the robot status will be displayed as **Idle**.

![Screenshot of the robot status](../img/connection/connection1.png)
