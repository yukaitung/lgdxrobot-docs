---
title: How it Works
weight: 1
---

In fact, LGDXRobot Cloud is a web service that relays messages between the user and a robot running ROS 2. The **LGDXRobot Cloud Adaptor** acts as the intermediary between the cloud system and the robot, collecting data from the robot and sending commands back to it.

The Robot ROS Node describes the ROS 2 integration for the robot hardware.
{.alert .alert-info}

## From the Robot to the User

![Data Flow To User](../img/how-it-works/info-to-user.png)

LGDXRobot Cloud displays the robot’s status, including navigation data, location, and battery level. These data originate from the robot ROS node and Nav2. The LGDXRobot Cloud Adaptor collects the data and sends it to the API, which then forwards it to the front-end. Data requiring real-time delivery is pushed to a Redis queue. The front-end subscribes to this queue and updates the UI in real time.

## From the User to the Robot

![Data Flow To Robot](../img/how-it-works/command-to-robot.png)

When a user wants to command a robot, they create a Task on the front end. A Task consists of waypoints that specify the positions the robot must reach. The request is sent to the API and then forwarded to the LGDXRobot Cloud Adaptor. The LGDXRobot Cloud Adaptor sends the waypoints as navigation goals to Nav2. Nav2 plans the path, generates the appropriate velocity commands, and send them to robot ROS node. The robot moves accordingly. For the third-party system, it sends the commands directly to the API.
