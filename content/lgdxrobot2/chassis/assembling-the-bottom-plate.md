---
title: Assembling the Bottom Plate
weight: 6
---

## Motors

Insert the screws into the motor brackets and motors, then tighten them with a screwdriver. The motor shafts may face either upwards (top left of image) or downwards (right of image). This only affects the overall height of the robot. Repeat the process for the remaining motors, ensuring all shafts face the same direction.

![Image of the motors](../img/asm_bottom/motor_brackets.png)

Install the wheels onto the motors and tighten them using a hex key.

![Image of the wheels with wheel installed](../img/asm_bottom/wheels.png)

For a typical Mecanum wheel installation, the wheels should form an **X** pattern when viewed from above. Number all motors according to the reference image. The mounting hole for the camera indicates the forward direction.

![Image of the wheels position](../img/asm_bottom/position.png)

Insert M4 × 12 mm screws from the top of the bottom plate into the bracket holes. Secure the motors using M4 nuts on the opposite side.

![Image of the install screw](../img/asm_bottom/screw.png)

Repeat for all motors and verify that the installation is correct. It is recommended to label the motors with numbers on both the motors and the bottom plate.

Incorrect installation may cause the robot to behave abnormally.  
{.alert .alert-warning}

![Image of the chassis top view](../img/asm_bottom/complete_top.png)  
![Image of the chassis bottom view](../img/asm_bottom/complete_bottom.png)

## Controller Board

Insert M4 screws through the controller board and secure them with M4 nuts on the opposite side, creating a standoff-like spacing.

![Image of the install screws to the controller board](../img/asm_bottom/board_screw.png)

Install the controller board onto the chassis, ensuring the PH2.0 connector faces the front of the chassis.

![Image of the install controller board on the chassis](../img/asm_bottom/board_install.png)

Secure the board with additional M4 nuts.

![Image of the install controller board on the chassis](../img/asm_bottom/board_install_screw.png)

## Power Supply

Place the two DC-DC buck converters near the centre of the bottom plate, and position the 18650 battery cases on the left and right sides.

The left side of the power supply is designated for the PC. Solder the following connections:  

**Power Supply → Power Switch → INA226 IN+ (No wired connection) INA226 IN- → DC-DC Buck Converter → DC Power Jack / USB**.

Warning: Ensure that the power supply’s positive terminal is connected to INA226 IN+. Incorrect wiring may cause a fire.
{.alert .alert-danger}

![Image of the connect for the power supply on PC side](../img/asm_bottom/power_pc.png)

The right side of the power supply is for the motors. Solder the following connections:  

**Power Supply → INA226 IN+ (No wired connection) INA226 IN- → Relay Module COM (No wired connection) Relay Module NO → Emergency Stop Button COM (No wired connection) Emergency Stop Button NC → DC-DC Buck Converter → XT30 Connector**, then connect to the boards.

Warning: Ensure that the power supply’s positive terminal is connected to INA226 IN+. Incorrect wiring may cause a fire.
{.alert .alert-danger}

![Image of the connect for the power supply on controller board side](../img/asm_bottom/power_motors.png)

Attach the batteries, power switch and emergency stop button to the bottom plate using adhesive or glue.

## Camera

Place the camera at the front of the chassis and secure it using a 1/4-inch tripod screw.

![Image of the installation of the camera](../img/asm_bottom/camera.png)
