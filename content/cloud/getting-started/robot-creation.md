---
title: Robot Creation
weight: 2
---

A robot is required for most operations in this tutorial. You will therefore need to create a robot entry in the system and download the necessary certificates.

### Step 1: Navigate to the Robots Creation Page

Expand the **Navigation**, select **Robots** and click **Create Robot** button in the top-right corner.

### Step 2: Configure the Robot Name

Enter a robot name and press **Next**.

![](../img/robot1.png)

- **Hardware Protection**: When enabled, LGDXRobot Cloud verifies the serial numbers of the motherboard and MCU. If they don't match the records in the database, the connection will be rejected.

### Step 3: Enter Chassis Information

Select **LGDXRobot2** as the robot type. Enter `0` for the remaining fields, then press **Next**.

The chassis information does not affect system behaviour.
{.alert .alert-warning}

![](../img/robot2.png)

### Step 4: Download Certificates

Download all the certificates and press **Next**, then press **Done**.

The system does not store the robot's private keys. If lost, you can renew the certificates to generate new ones.
{.alert .alert-info}

![](../img/robot3.png)

### Step 5: Install Certificates

Move all certificates to the folder you created for storing the keys, or send them to the robot computer.
