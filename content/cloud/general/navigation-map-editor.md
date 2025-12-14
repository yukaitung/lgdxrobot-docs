---
title: Navigation - Map Editor
weight: 52
---

The *Map Editor* is a graphical editor used to configure waypoints and traffic rules for a Realm.

Traffic rules require **Waypoint Traffic Control** to be enabled in the Realm settings. Otherwise, traffic rules will be ignored. Traffic rules can be defined as single-way or bidirectional, but only straight-line rules are supported.

## Map Editor User Interface

![Map Editor UI](../img/navigation/map-editor/map-editor-ui.png)

* **Move**: Drag the map to reposition it.
* **Zoom**: Use the mouse wheel or the +/- buttons to zoom in or out.
* **Coordinates**: When the mouse is over the map, the map coordinates are displayed at the top centre.
* **Waypoints**: Blue circles represent waypoints. Click a waypoint to view its details.

## Creating a Waypoint

* Click the **Add Waypoint** button at the top left.
* Enter the waypoint settings.
* Click **Create**.
* The waypoint will appear on the map.

## Editing a Waypoint

* Click any waypoint on the map.
* The waypoint details will appear; click **Edit**.
* Update the waypoint settings.
* Click **Update**.

## Deleting a Waypoint

* Click any waypoint on the map.
* The waypoint details will appear; click **Edit**.
* Click **Delete**.
* The system will verify that no entities are referencing the waypoint.
* Click **Delete** again to confirm.

## Creating a Traffic Rule

* Click the **Traffic rules** dropdown at the top left.
* Select **Single-way traffic** or **Two-way traffic**.
* Click the waypoint to set as the starting point.
* Click the waypoint to set as the ending point.
* A blue line will appear on the map.  
  * If an arrow is displayed, the traffic is single-way in the direction of the arrow.  
  * If no arrow is shown, the traffic rule is bidirectional.

For single-way traffic, it is recommended to create a waypoint at each junction and define traffic rules accordingly to reduce the likelihood of Nav2 planning a route in the reverse direction.
{.alert .alert-info}

![Traffic Rules](../img/navigation/map-editor/map-editor-traffic.png)

## Editing / Deleting a Traffic Rule

* Click the **Traffic rules** dropdown at the top left.
* Select **Delete Traffic rule**.
* Click the traffic rule you want to delete.
* The traffic rule will be removed from the map.
* To edit a rule, create a new one with the updated direction.

## Update Waypoint Traffic Control

Click the **Update** button at the top right.

## Reset Waypoint Traffic Control

If traffic rules have been modified, the system saves a snapshot of the previous configuration.  
To reset the traffic control, click the **Reset** button at the top right, then click **Yes** to confirm.
