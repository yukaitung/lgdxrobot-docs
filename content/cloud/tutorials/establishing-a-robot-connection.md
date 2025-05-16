---
title: Establishing a Robot Connection
weight: 4
---

To connect a robot, you need to create a robot entry in the system, download the required certificates, and launch the corresponding software in ROS2.

## Create a Robot

Navigate to **Navigation -> Robots** and click **Create Robot**.

Enter a robot name and press **Next**.

![](../img/robot1.png)

- **Realtime Exchange**: When enabled, the robot continuously streams data to the server. Disable it for polling-based communication.
- **Hardware Protection**: When enabled, LGDXRobot Cloud verifies the serial numbers of the motherboard and MCU. If they don't match the records in the database, the connection will be rejected.

Select **LGDXRobot2** as the robot type. Enter `0` for the remaining fields, then press **Next**.

The chassis information does not affect system behaviour. This page is subject to change.
{.alert .alert-warning}

![](../img/robot2.png)

Download all the certificates and press **Next**, then **Done**.

The system does not store the robot's private keys. If lost, you can renew the certificates to generate new ones.
{.alert .alert-info}

![](../img/robot3.png)

## Establishing a Connection

Move all certificates to the robot computer, then run the following commands:

```bash
cd lgdx ws
. install/setup.bash
ros2 run lgdxrobot2_daemon lgdxrobot2_daemon_node --ros-args -p cloud_enable:=true -p cloud_address:=192.168.1.10:5162 -p cloud_root_cert:=/home/user/key/rootCA.crt -p cloud_client_key:=/home/user/key/Robot1.key -p cloud_client_cert:=/home/user/key/Robot1.crt
```

| Parameter           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| cloud_enable        | Enables or disables cloud communication. Set to `true` to enable it.        |
| cloud_address       | IP address and port of the cloud server to connect to (e.g., `192.168.1.10:5162`). |
| cloud_root_cert     | Path to the root CA certificate. Used to verify the server's identity.       |
| cloud_client_key    | Path to the client’s private key. Used for TLS mutual authentication.        |
| cloud_client_cert   | Path to the client’s certificate. Used with the key to authenticate the robot. |
{.table}

If the connection is working, the terminal will show: `Connect to the cloud, start data exchange.`

![](../img/robot4.png)

And the robot in Robots will be shown as online.

![](../img/robot5.png)
