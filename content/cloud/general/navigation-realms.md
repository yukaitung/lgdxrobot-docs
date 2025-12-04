---
title: Navigation - Realms
weight: 50
---

A *Realm* is essentially a map that defines the operational area of the fleet. The map can be generated through Nav2 mapping, but the image must be converted to PNG format.

## Creating a Realm

* Click the **Create Realm** button at the top right.
* Enter the realm settings.
* Click **Create**.

## Editing a Realm

* Click the **View** button on the right of the realm.
* Update the realm settings.
* Click **Update**.

## Deleting a Realm

* Switch to another realm using **Change the Realm**.
* Click the **View** button on the right of the realm.
* Click **Delete**.
* The system will verify that no entities are referencing the realm.
* Click **Delete** again to confirm.

## Settings

* **Name**: The name of the realm.
* **Description**: A description of the realm.
* **Waypoint Traffic Control**: Enables or disables traffic control within this realm. Traffic rules must be defined in the **Map Editor** after enabling this option.
* **Map**: The map image for the realm. The maximum file size is 16 MB, and only the `.png` format is supported.
* **Resolution (m)**: The size of each pixel in metres. This value can be found in the YAML file associated with the map.
* **Origin X (m)**: The X origin of the map in metres, taken from the associated YAML file.
* **Origin Y (m)**: The Y origin of the map in metres, taken from the associated YAML file.
* **Origin Rotation (rad)**: The rotation of the map in radians, also found in the associated YAML file.

The map image, resolution, and origin must be configured correctly to ensure proper display in the UI.
{.alert .alert-info}
