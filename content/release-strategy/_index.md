---
title: Release Strategy
description: Documentation for the release strategy
homepage: 
weight: 3
---

Release Strategy is the main GitLab CI/CD pipeline for releasing distributions for LGDXRobotics. It aggregates the .deb files from the projects and publishes them to APT repositories, as well as Docker images to Docker Hub.

## Components

* The project that builds the .deb files
* [Release Strategy Front](https://gitlab.com/lgdxrobotics/release-strategy-front) for releasing APT repositorie.
* [Release Strategy Docker](https://gitlab.com/lgdxrobotics/release-strategy-docker) for releasing Docker images.

## Participating Projects

* LGDXRobot2 ChassisTuner
* LGDXRobot2 ROS 2
* LGDXRobot2 Support
* LGDXRobot Cloud Adapter
