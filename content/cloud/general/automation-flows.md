---
title: Automation - Flows
weight: 101
---

A *Flow* is a sequence of steps that defines the automation workflow when the robot executes a task. A flow allows adding new steps such as loading or unloading an object, or even call third-party APIs using *Triggers*.

## Creating a Flow

* Click the **Create Flow** button at the top right.
* Enter the flow settings.
* Click **Create**.

## Updating a Flow

* Click the **View** button on the right of the flow.
* Update the flow settings.
* Click **Update**.

## Deleting a Flow

* Click the **View** button on the right of the flow.
* Click **Delete**.
* The system validates that the flow is not used by any task.
* Press **Delete** to confirm.

## Settings

* **Name**: The name of the flow.
* **Flow Details**: The sequence of steps that defines the flow.
  * **Progress**: The step representing the current progress. Enter a progress name to search for it.
  * **Proceed Condition**: The component that receives the next token and determines whether to proceed to the next step.
  * **Trigger**: The trigger that will be invoked at the beginning of the progress.
  * **Reorder**: Use the up and down arrows to change the order of steps.
  * **Remove**: Click the bin icon to remove the step.
  * **Add Progress**: Click the **Add Progress** button to add a new progress step.

1: The 'Moving' progress should be included in the flow for the robot to navigate. \
2: An external API call is required when using 'API' as the proceed condition.
{.alert .alert-info}