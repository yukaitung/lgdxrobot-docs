---
title: Setting Up the Map
weight: 3
---

After creating a robot, you can set up the map on LGDXRobot Cloud using SLAM mode. The system will then receive map data from the robot running the NAV2 stack. SLAM mode is supported on only one robot. If a second robot tries to connect, it will be refused.

### Step 1: Enter SLAM Mode on LGDXRobot Cloud

Expand the **Navigation**, select **Realms** and click **View** link for **First Realm**. Then press **Start SLAM** button on the top right. The system will display *Awaiting Robot...*

### Step 2: Launch NAV2 Stack

Ensure that the PATH is set up correctly for the ROS2 environment. (You can ignore this step if you are using the Docker image.)

```bash
cd lgdx_ws
. install/setup.bash
```

Launch the NAV2 stack in SLAM mode:

```bash
ros2 launch lgdxrobot2_bringup simulation_nav.launch.py slam:=True profile:='sim-slam'
```

If you are using the Docker image, click the blue button in the middle-left to expand the settings. Paste the command into the Clipboard section, then you can paste it directly into the terminal.
{.alert .alert-info}

Next, launch the LGDXRobot2 Agent node to connect to the cloud.

```bash
ros2 run lgdxrobot2_agent lgdxrobot2_agent_node --ros-args \
  -p cloud_enable:=true \
  -p cloud_slam_enable:=true \
  -p sim_enable:=true \
  -p cloud_address:=host.docker.internal:5162 \
  -p cloud_root_cert:="/config/keys/root.crt" \
  -p cloud_client_key:="/config/keys/My Robot.key" \
  -p cloud_client_cert:="/config/keys/My Robot.crt"
```

If you are using a physical robot, remove `-p cloud_slam_enable:=true` and add `-p mcu_enable:=true`.

Also, if you are hosting the cloud on a different computer, replace host.docker.internal with the IP address of that computer. Update the paths for `cloud_root_cert`, `cloud_client_key`, and `cloud_client_cert` to point to the certificates you downloaded.

### Step 3: Complete the Exploration

If the connection is working, you will see the interface as shown below. The map will appear in the middle. If it does not, click the **Refresh** button at the top middle, or restart the NAV2 stack and the LGDXRobot2 Agent node.

![](../img/map1.png)

To start exploration, press the **Set Goal** button at the top. Then set the goal by clicking on the gray area of the map and dragging the mouse to the desired position.

After finishing the exploration, press the **Update Realm** button in the top-right corner, then press **Update** to save the map. This will update the map on the cloud and save the map file on the robot. The robot will also stop navigating at the same time.

You will be redirected to the details page for **First Realm**. Verify the map image and configuration.

## Step 4: Setup Realm (Optional)

If you do not want to use SLAM mode, you can set up the map manually. Download the map image below.

![](../img/map2.png)

On the details page for **First Realm**, click the **Browse...** button to upload the map image. Then update the other fields according to the table below.

| Parameter   | Value   |
|------------|---------|
| Resolution | 0.05    |
| Origin X   | -0.951  |
| Origin Y   | -1.11   |
{.table}

![](../img/map3.png)

Press **Update** to save the map.

## Step 5: Setup Waypoints

We need to set up some waypoints for the robot to navigate through. Expand the **Navigation**, select **Waypoints** and select **Create Waypoint** in the top-right corner.

Create two waypoints using the data below. After entering the position for waypoint **A**, press **Create**, then press **Create Waypoint** again to create waypoint **B**.

| Name | X   | Y    | Rotation |
|------|-----|------|----------|
| A    | 0   | 0    | 0        |
| B    | 6.5 | 8.5  | 3.14159265 |
{.table}

![](../img/map4.png)

Both waypoints should now be created and visible on the interface.

![](../img/map5.png)
