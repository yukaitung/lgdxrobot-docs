---
title: Setup
layout: sub-section
weight: 2
---

This section explains how to set up LGDXRobot Cloud step by step. LGDXRobot Cloud relies on machine-to-machine communication, so you must generate a root certificate and the corresponding key pairs. It also lists the required software dependencies and configuration steps. The setup process is divided into the following steps:

1. Generate Certificates
2. Install Software Dependencies
3. Configure LGDXRobot Cloud
4. Launch LGDXRobot Cloud

Before you start, make sure you have the following software installed:

* [.NET SDK](https://dotnet.microsoft.com/en-us/download/)
* [LibMan](https://learn.microsoft.com/en-us/aspnet/core/client-side/libman/libman-cli)
* [Docker](https://www.docker.com/)
* [Git](https://git-scm.com/)
* OpenSSL (Included in Git Installation / Linux)

Then clone the repository:

```bash
git clone https://gitlab.com/lgdxrobotics/lgdxrobot-cloud.git
```