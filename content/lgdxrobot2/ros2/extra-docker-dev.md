---
title: Extra - Docker for Development
weight: 10
---

The LGDXRobot2 ROS2 Docker image comes with development tools installed, allowing you to develop your own ROS2 packages. This tutorial shows how to build your own ROS2 package. It is based on the [ROS2 documentation](https://docs.ros.org/en/jazzy/Tutorials/Beginner-Client-Libraries/Creating-A-Workspace/Creating-A-Workspace.html).

1. Create a workspace on your host machine and clone the tutorials

```bash
mkdir -p ~/my_ws/src
cd ~/my_ws/src
git clone https://github.com/ros/ros_tutorials.git -b jazzy
```

2. Start the Docker container and mount the workspace

```bash
docker run -d  \
  --name lgdxrobot2 \
  -e PUID=1000 \
  -e PGID=1000 \
  -v ~/my_ws/src:/config/my_ws/src \
  -p 3000:3000 \
  -p 3001:3001 yukaitung/lgdxrobot2-desktop:latest
```

3. You can now visit [http://localhost:3000](http://localhost:3000) to access the web interface.
4. In the terminal, run the following command to gain access to the workspace. Any error messages can be safely ignored.

```bash
sudo chown -R 1000:1000 ~/my_ws
```

5. Install dependencies and build the workspace

```bash
cd my_ws
rosdep install -i --from-path src --rosdistro jazzy -y
colcon build
```

6. Source the workspace

```bash
source install/local_setup.bash
```

7. Start the example node. It will open a window demonstrating the tutorial package.

```bash
ros2 run turtlesim turtlesim_node
```
