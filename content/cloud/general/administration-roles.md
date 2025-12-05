---
title: Administration - Roles
weight: 152
---

LGDXRobot Cloud allows you to create roles to define customised access control for users. A role contains a list of scopes that determine what the user can access. The access can be fine-grained, such as specific permissions (read, write, delete) within a controller, or broad, such as access to everything in the system.

The Email Recipient role is a special role that allows the user to receive email notifications from the system. It does not grant any system access.
{.alert .alert-info}

## Creating a Role

* Click the **Create Role** button at the top right.
* Enter the role settings.
* Click **Create**.

## Updating a Role

* Click the **View** button on the right of the role.
* Update the role settings.
* Click **Update**.

## Deleting a Role

* Click the **View** button on the right of the role.
* Click **Delete**.
* Click **Delete** to confirm.

The system will prevent a system role from being deleted.
{.alert .alert-info}

## Settings

* **Name**: The name of the role.
* **Description**: The description of the role.
* **Scopes**: The scopes assigned to the role.
  * **Area**: The category of functionality that can be accessed.
  * **Controller**: The feature within the category that can be accessed.
  * **Permission**: The specific action that can be performed.
  * **Remove**: Click the bin icon to remove the scope.
  * **Add Scope**: Click the **Add Scope** button to add a new scope.

The permission field is mandatory.
{.alert .alert-info}
