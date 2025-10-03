---
title: Establishing a Robot Connection
weight: 5
---

Before running the first automation task, you need to connect a robot to the system so that it can receive the automation task.

## Step 1: Connect a Robot

Close all terminal windows running the NAV2 stack and the LGDXRobot2 Agent node. Then, run both nodes with different configurations.

NAV2 stack:

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py
```

LGDXRobot2 Agent node:

```bash
ros2 run lgdxrobot2_agent lgdxrobot2_agent_node --ros-args \
  -p cloud_enable:=true \
  -p sim_enable:=true \
  -p cloud_address:=host.docker.internal:5162 \
  -p cloud_root_cert:="/config/keys/root.crt" \
  -p cloud_client_key:="/config/keys/My Robot.key" \
  -p cloud_client_cert:="/config/keys/My Robot.crt"
```

Ensure `cloud_slam_enable` is disabled in the LGDXRobot2 Agent node, and update the other parameters to match your environment.

### Step 2: Check the Connection

Click **Home** then click **Robots** on the top menu bar. If the connection is successful, the robot status will be displayed as **Idle**.

![](../img/connection1.png)
