---
title: Establishing a Robot Connection
weight: 4
---

To connect a robot, we need to create a robot, download the certificates and launch the corrsopnding software in ROS2.

## Create a Robot

Navigate "Navigation" -> "Robots" and press "Create Robot".

Enter a robot name then press next.

`Realtime Exchange` means the robot starts a streaming to the server, uncheck it for polling.

`Hardware Protection` means the LGDXRobot Cloud verifies the serial number for motherboard and MCU when connecting, if the serial number does not match in the database, the connection will be refused.

Select LGDXRobot2 for robot type, enter 0 for remaining fields the press "Next" 

The chassis information does not affect the behaviour of the system, this page is subject to change.
{.alert .alert-warning}

Download every certificates and press "Next"

The system does not store the keys for robot, but you can renew the certificate to get a new one.
{.alert .alert-info}

## Establishing a Connection

Move all certificates to the robot computer. Then run below commands.


If connection ok