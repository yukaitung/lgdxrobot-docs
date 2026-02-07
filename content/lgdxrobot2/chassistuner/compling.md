---
title: Compling
weight: 3
---

The ChassisTuner provides two compilation options: the official Qt Installer, and aqtinstall (used for GitLab CI/CD).

## Official Qt Installer

1. Download the [Qt Installer](https://www.qt.io/download-qt-installer) and install the following packages:

* Qt 6.10
* Qt Serial Port
* Qt Graphs

2. Clone the [lgdxrobot2-chassistuner](https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner) repository.

```bash
git clone --recurse-submodules https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner
```

3. Open the project in Qt Creator.
4. Press **Run** to build and launch the application.

## aqtinstall

1. Setup the environment variables:

**Run the following commands on an AMD64 system:**

```bash
export QT_VERSION=6.10.0
export QT_PATH=/opt/Qt
export QT_GCC=$QT_PATH/$QT_VERSION/gcc_64
PATH="$PATH:$QT_PATH/Tools/CMake/bin:$QT_PATH/Tools/Ninja:$QT_PATH/$QT_VERSION/gcc_64/bin"
```

**Run the following commands on an ARM64 system:**

```bash
export QT_VERSION=6.10.0
export QT_PATH=/opt/Qt
export QT_GCC=$QT_PATH/$QT_VERSION/gcc_arm64
PATH="$PATH:$QT_PATH/Tools/CMake/bin:$QT_PATH/Tools/Ninja:$QT_PATH/$QT_VERSION/gcc_arm64/bin"
```

2. Install the required system packages:


```bash
sudo apt install libxkbcommon-dev libxkbfile-dev libgl-dev libvulkan-dev python3-pip # Buildtime dependencies
sudo apt install libxkbcommon-x11-0 libxcb-cursor0 libxcb-icccm4 libxcb-keysyms1 # Runtime dependencies
```

3. Install `aqtinstall` via **pip** and set it to the **PATH**
4. Use `aqtinstall` to install the following packages:

**Run the following commands on an AMD64 system:**

```bash
aqt install-qt -O "$QT_PATH" linux desktop "$QT_VERSION" linux_gcc_64 -m qtgraphs qtserialport qtquick3d qtshadertools
aqt install-tool -O "$QT_PATH" linux desktop tools_cmake
aqt install-tool -O "$QT_PATH" linux desktop tools_ninja
```

**Run the following commands on an ARM64 system:**

```bash
aqt install-qt -O "$QT_PATH" linux_arm64 desktop "$QT_VERSION" linux_gcc_arm64 -m qtgraphs qtserialport qtquick3d qtshadertools
aqt install-tool -O "$QT_PATH" linux_arm64 desktop tools_cmake
aqt install-tool -O "$QT_PATH" linux_arm64 desktop tools_ninja
```

5. Clone the repository.

```bash
git clone https://gitlab.com/lgdxrobotics/lgdxrobot2-chassistuner.git
```

6. Navigate to the project directory in the terminal.
7. Build the application:

```bash
qt-cmake . -G Ninja -B ./build -DCMAKE_BUILD_TYPE=Release
cmake --build ./build
```
