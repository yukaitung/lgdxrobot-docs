---
title: Development
weight: 2
---

The first publicly released robot is LGDXRobot2, though it may seem unusual that the project starts with **2**. This is because the first robot was originally part of another project and was eventually redesigned into LGDXRobot2.

## LGDXRobot

LGDXRobot was originally built as part of my university project in 2021. The aim was to design a robot capable of collecting and sorting rubbish for recycling. The chassis was purchased from an online store, while the robot’s body was hand-crafted from cardboard. It included three containers for different types of waste, and the robot identified each item, opened the appropriate container, and picked it up automatically.

The robot ran on an Nvidia Jetson Nano using ROS Melodic, with object detection powered by the [jetson-inference](https://github.com/dusty-nv/jetson-inference) framework. It also featured a remote control interface that streamed system status, logs, and live images from the robot.

The source code is available in the [GitLab](https://gitlab.com/groups/lgdxrobotics/-/inactive)

| Description | Media |
|-------------|-------|
| The image LGDXRobot and remote control interface | ![The image LGDXRobot and remote-control interface](../img/development/lgdxrobot1.jpg) |
| LGDXRobot avoids collisions, identify and pick up rubbish. (2x speed) | {{< video "../img/development/lgdxrobot1-collecting-rubbish.webm" >}} |
{.table}

## LGDXRobot2

After graduating, the robot no longer served its original purpose, so I decided to repurpose it as a general-purpose chassis. I first redesigned the controller board using a more cost-effective STM32 microcontroller. Then I redeveloped the ROS package using ROS 2 Humble. I also experimented with better wheels and a more powerful computer. However, since Intel dropped support for the RealSense T265 camera, I was unable to achieve satisfactory SLAM performance.

![The image LGDXRobot2](../img/development/lgdxrobot2.png)

## LGDXRobot2 R2

I kept thinking about redesigning the chassis, and one day I finally had the enthusiasm to make it happen. I first designed the new controller board in KiCad and then redesigned the chassis in FreeCAD to make better use of the available space. I also bought a LiDAR sensor and relied on it for SLAM. On the software side, the ChassisTuner UI was redesigned, and the system was upgraded to ROS 2 Jazzy (and more features). The SLAM results are significantly better than before, and the project has since been shared on Reddit and LinkedIn.

![The image LGDXRobot2 R2](../img/development/lgdxrobot2-r2.png)

## LGDXRobot2 R3 (Current Version)

LGDXRobot2 (v3) includes several hardware upgrades. The controller board now integrates an IMU and features a refined component layout. Furthermore, the chassis has been adjusted to accommodate an onboard NUC.
