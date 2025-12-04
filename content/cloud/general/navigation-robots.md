---
title: Navigation - Robots
weight: 53
---

A *Robot* is a device that belongs to a Realm and can execute Tasks.

## Creating a Robot

* Click the **Create Robot** button at the top right.
* Enter the Robot Details settings and press **Next**.
* Enter the Chassis settings and press **Next**.
* Press **Download** to download the Root Certificate, Robot Private Key, and Robot Public Key files.  
  The input fields allow you to change the file names before downloading.
* Press **Next** after the files have been downloaded.
* Press **Done** in the final step.
* Send the downloaded files to the robot.

The system does not store the key pair files, but they can be regenerated if lost.
{.alert .alert-info}

## Viewing a Robot

* Click the **View** button on the right of the robot.
* The robot details will appear.
  * **Status**: Displayed next to the robot name.
  * **Assigned Tasks**: The list of tasks currently assigned to the robot.
  * **Robot Data**: When online, the robot’s data is displayed in a table.
  * A tab menu at the bottom allows switching between views:
    * **Robot**: The Robot Details settings.
    * **System**: System information for the PC and MCU.
    * **Chassis**: The Chassis Details settings.
    * **Certificates**: Certificate information.
    * **Activity Logs**: A history of changes made to the robot.
    * **Delete Robot**: The function to delete the robot.

This page has real-time capabilities.
{.alert .alert-info}

## Editing a Robot

* Click the **View** button on the right of the robot.
* The robot details will appear.
* Select the **Robot** tab to edit Robot Details settings and press **Update** to save the changes.
* Select the **Chassis** tab to edit the Chassis Details settings and press **Update** to save the changes.
* Select the **Certificates** tab to renew the certificates, then press **Renew Certificates** to start the process.

## Deleting a Robot

* Click the **View** button on the right of the robot.
* The robot details will appear.
* Select the **Delete Robot** tab to delete the robot.
* The system will verify that no entities are referencing the robot.
* Click **Delete** again to confirm.

## Settings

### Robot Details

* **Name**: The name of the robot.
* **Hardware Protection**: Enables hardware protection, requiring the PC and MCU serial numbers to match.  
  If the serial numbers are incorrect, the robot will be disconnected.

### Chassis Details

* **Robot Type**: The type of robot.
* **Chassis Length X (m)**: The X-axis length of the robot chassis in metres.
* **Chassis Length Y (m)**: The Y-axis length of the robot chassis in metres.
* **Chassis Wheel Count**: The number of wheels on the robot chassis.
* **Chassis Wheel Radius (m)**: The radius of the wheels in metres.
* **Battery Count**: The number of batteries.
* **Battery Maximum Voltage (V)**: The maximum voltage of the batteries.
* **Battery Minimum Voltage (V)**: The minimum voltage of the batteries.

These settings do not affect system behaviour at this time.
{.alert .alert-info}
