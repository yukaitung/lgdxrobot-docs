---
title: Setting Up the Map
weight: 3
---

After creating a robot, the next step is setting up the map on LGDXRobot Cloud using SLAM mode. The system will then receive map data from the robot running the Nav2 stack. SLAM mode is supported on only one robot. If a second robot tries to connect, it will be disconnected.

## Step 1: Enter SLAM Mode on LGDXRobot Cloud

Expand the **Navigation**, select **Realms** and click **View** link for **First Realm**. Then press **Start SLAM** button on the top right. The system will display *Awaiting Robot...*

## Step 2: Launch Nav2 Stack and Connect to Cloud

### Physical Robot

```bash
ros2 launch lgdxrobot2_bringup slam.launch.py \
  slam:=True \
  profile:='slam' \
  use_cloud:=True \
  cloud_address:=<Address of the cloud with port> \
  cloud_root_cert:="/config/keys/root.crt" \
  cloud_client_key:="/config/keys/My Robot.key" \
  cloud_client_cert:="/config/keys/My Robot.crt"
```

### Simulation Robot

```bash
ros2 launch lgdxrobot2_bringup webots_nav.launch.py \
  slam:=True \
  profile:='slam-sim' \
  use_cloud:=True \
  cloud_address:=<Address of the cloud with port or 'host.docker.internal:port'> \
  cloud_root_cert:="/config/keys/root.crt" \
  cloud_client_key:="/config/keys/My Robot.key" \
  cloud_client_cert:="/config/keys/My Robot.crt"
```

Click the blue button in the middle-left to expand the settings. Paste the command into the Clipboard section, then  paste it directly into the terminal.
{.alert .alert-info}

If there is any errors, it is likely that the [alt_names] section in the certificate configuration does not include the IP address of the computer hosting the LGDXRobot Cloud.
{.alert .alert-info}

## Step 3: Complete the Exploration

If the connection is working, the map will appear in the middle. If it does not, click the **Refresh** button at the top middle.

![Screenshot of the SLAM mode](../img/map/map1.png)

To start exploration, press the **Set Goal** button at the top. Then set the goal by clicking on the gray area of the map and dragging the mouse to the desired position.

After finishing the exploration, press the **Update Realm** button in the top-right corner, then press **Update** to save the map. This will update the map on the cloud and save the map file on the robot. The robot will also stop navigating at the same time.

## Step 4: Setup Realm (Optional)

To set up the map manually. Download the map image below.

![Picture of simulated map](../img/map/map2.png)

On the details page for **First Realm**, click the **Browse...** button to upload the map image. Then update the other fields according to the table below.

| Parameter   | Value   |
|------------|---------|
| Resolution | 0.05    |
| Origin X   | -0.951  |
| Origin Y   | -1.11   |
{.table}

![Screenshot of the realm details page](../img/map/map3.png)

Press **Update** to save the map.

## Step 5: Setup Waypoints

Waypoints are required for the robot to navigate through. Expand the **Navigation**, select **Waypoints** and select **Create Waypoint** in the top-right corner.

Create two waypoints using the data below. After entering the position for waypoint **A**, press **Create**, then press **Create Waypoint** again to create waypoint **B**.

| Name | X   | Y    | Rotation |
|------|-----|------|----------|
| A    | 0   | 0    | 0        |
| B    | 6.5 | 8.5  | 3.14159265 |
{.table}

![Screenshot of the waypoint details page](../img/map/map4.png)

Both waypoints should now be created and visible on the interface.

![Screenshot of the waypoints page](../img/map/map5.png)
