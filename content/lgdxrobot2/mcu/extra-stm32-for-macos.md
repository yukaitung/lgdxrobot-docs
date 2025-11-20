---
title: Extra - STM32 for macOS
weight: 90
---

macOS plays a crucial role in the development of the LGDXRobot2. This tutorial describes how to install the necessary tools and compile any STM32 firmware on macOS. It assumes the Mac is running on Apple Silicon and that the ST-Link is connected to the Mac.

1. Install the following tools:

* [STM32CubeIDE for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=stmicroelectronics.stm32-vscode-extension)
* [STM32Cube](https://www.st.com/en/development-tools/stm32cubemx.html)

2. STM32Cube includes the compilers for STM32 MCUs, but they are not added to the PATH. Run the following command to locate the compiler:

```bash
find ~ -type f -name "arm-none-eabi-gcc" 2>/dev/null
```

3. Note the path to the `bin` folder:

```bash
/Users/<user>/Library/Application Support/stm32cube/bundles/gnu-tools-for-stm32/<version>/bin/arm-none-eabi-gcc
```

4. In Visual Studio Code, press `Ctrl+Cmd+P` to open the command palette, and search for `Preferences: Open Settings (JSON)`. Then, add the path to the `bin` folder to the `cmake.environment.PATH` variable:

```json
"cmake.environment": {
  "PATH": "<path the bin folder>:${env.PATH}"
}
``` 

5. Switch to the `STM32CubeIDE` tab, select the `Setup STM32CubeIDE project(s)` option, and choose the correct device and project. Then press `Save and Close`.

![Setup STM32CubeIDE project(s)](../img/extra/stm32-setting.png)

6. Switch to the `Run and Debug` tab, press `Run and Debug`. A dropdown menu will appear. Select the GDB Server for the corresponding debugger.

7. Visual Studio Code will automatically compile and flash the firmware to the MCU, then launch the debugger.