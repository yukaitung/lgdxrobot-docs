---
title: Assembling the Bottom Plate
weight: 6
---

## Motors

Insert the screws into the motor brackets and motors, then tighten them with a screwdriver. The motor shafts may face either upwards (top left of image) or downwards (right of image). This only affects the overall height of the robot. Repeat the process for the remaining motors, ensuring all shafts face the same direction.

![Image of the motors](../img/asm_bottom/motor_brackets.jpg)

Install the wheels onto the motors and tighten them using a hex key.

![Image of the wheels with wheel installed](../img/asm_bottom/wheels.jpg)

For a typical Mecanum wheel installation, the wheels should form an **X** pattern when viewed from above. Number all motors according to the reference image. The mounting hole for the camera indicates the forward direction.

![Image of the wheels position](../img/asm_bottom/position.jpg)

Secure the motors using the holes highlighted in green.

![Image of the install screw](../img/asm_bottom/screw_hole.jpg)

Insert M4 × 12 mm screws from the top of the bottom plate into the bracket holes. Secure the motors using M4 nuts on the opposite side.

![Image of the install screw](../img/asm_bottom/screw.jpg)

Repeat for all motors and verify that the installation is correct. It is recommended to label the motors with numbers on both the motors and the bottom plate.

Incorrect installation may cause the robot to behave abnormally.  
{.alert .alert-warning}

![Image of the chassis top view](../img/asm_bottom/complete_top.jpg)  
![Image of the chassis bottom view](../img/asm_bottom/complete_bottom.jpg)

## Controller Board

Insert M4 screws through the controller board and secure them with M4 nuts on the opposite side, creating a standoff-like spacing.

![Image of the install screws to the controller board](../img/asm_bottom/board_screw.jpg)

Install the controller board onto the chassis, ensuring the PH2.0 connector faces the front of the chassis.

![Image of the install controller board on the chassis](../img/asm_bottom/board_install.jpg)

The scrws should be inserted through the holes highlighted in green.

![Image of the install controller board on the chassis](../img/asm_bottom/board_install_hole.jpg)

Secure the board with additional M4 nuts.

![Image of the install controller board on the chassis](../img/asm_bottom/board_install_screw.jpg)

## Motors Controller Board Connections

Connect the PH2.0 connectors from the controller board to the motors according to the numbering. For example, **MJ1** on the controller board should be connected to **Motor 1 / Wheel 1**.

![Image of the connectors on the controller board](../img/asm_bottom/connect_motor1.jpg)
![Image of the connection of the motors](../img/asm_bottom/connect_motor2.jpg)

## Power Supply

### Motors Circuit

Connect the components according to the following image.

For **+J3** and **+ESTOP**, connect them to the **PH2.0 connector**.

The **“+”** symbol indicates the positive side, and the **number** indicates the negative pin.

![Image of the connect for the power supply on controller board side](../img/asm_bottom/power_connect_motor.jpg)
![Image of the connect for the power supply on controller board side](../img/asm_bottom/power_motors.jpg)

### Logic Circuit

Connect the components according to the following image.

For **+J2**, connect them to the **PH2.0 connector**.

The **“+”** symbol indicates the positive side, and the **number** indicates the negative pin.

Use the **USB** or **DC jack** to power the onboard computer.

![Image of the connect for the power supply on controller board side](../img/asm_bottom/power_connect_pc.jpg)
![Image of the connect for the power supply on PC side](../img/asm_bottom/power_pc.jpg)