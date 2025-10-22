---
title: Assembling the Bottom Plate
weight: 6
---

## Motors

Insert the screws into the motor brackets and motors, then tighten them with a screwdriver. The motor shafts can face either up or down; this only changes the height of the robot. Repeat for the other motors, ensuring all shafts face the same direction.

Install the wheels onto the motors and tighten them using a hex key.

For a typical Mecanum wheel installation, the wheels should form an X pattern when viewed from above. Number all motors according to the reference image. The mounting hole for the camera indicates the forward direction.

Insert M4 × 12 mm screws from the top of the bottom plate into the bracket holes. Secure the motors using M4 nuts on the opposite side. Repeat for all motors and check that the installation is correct. It is recommended to tag the motors with numbers on both the motors and the bottom plate.

Incorrect installation may cause the robot to behave abnormally.
{.alert .alert-warning}

## Controller Board

Insert M4 screws through the controller board into the bottom plate, and secure the board with M4 nuts on the opposite side. Ensure the PH2.0 connector is facing the front of the chassis.

## Power Supply

Place the two DC-DC Buck Converters near the centre of the bottom plate, and position the 18650 battery cases on the left and right sides. Secure them using tape or hot glue.

The left side of the power supply is for the PC. Solder wires to connect:  

**Power Supply → Power Switch → INA226 → DC-DC Buck Converter → DC Power Jack / USB**, then connect to the PC.

The right side of the power supply is for the motors. Solder wires to connect:  

**Power Supply → INA226 → Relay Module (optional) → Emergency Stop Button → DC-DC Buck Converter → XT30 Connector**, then connect to the boards.

Attach the Power Switch and Emergency Stop Button to the bottom plate using adhesive or glue.

## Camera

Place the camera at the front of the chassis and secure it with a 1/4-inch tripod screw.
