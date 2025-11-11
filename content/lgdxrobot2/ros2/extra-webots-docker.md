---
title: Extra - Native Webots For Docker
weight: 11
---

The LGDXRobot2 ROS2 Docker image allows you to deploy all dependencies in one go, but it does not include Webots. Running Webots inside Docker may be slow. Fortunately, Webots is flexible and can run on the simulation via network.

1. Create a folder for sharing Webots files

```bash
mkdir -p ~/webots_share
```

2. Start the Docker container and mount the shared folder

```bash
docker run -d  \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v ~/webots_share:/config/webots_share \
  -p 3000:3000 \
  -p 3001:3001 yukaitung/lgdxrobot2.desktop:latest
```

3. Set environment variables inside the container

```bash
export WEBOTS_SHARED_FOLDER=~/webots_share:/config/webots_share
```

4. Save the [local simulation server script](https://github.com/cyberbotics/webots-server/blob/main/local_simulation_server.py) on the host machine.
5. Run the local simulation server on the host machine.

```bash
export WEBOTS_HOME=/Applications/Webots.app # macOS
python3 /Users/sam/Develop/keys/local_simulation_server.py
```

6. Run the simulation in the container. When you run the simulation in the container, the Webots GUI will open automatically on your host machine.