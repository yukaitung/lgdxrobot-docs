---
title: Automation - Triggers
weight: 103
---

A *Trigger* is a third-party API call that is invoked at the beginning of a progress. The trigger can include data that will be passed in the call.

## Creating a Trigger

* Click the **Create Trigger** button at the top right.
* Enter the trigger settings.
* Click **Create**.

## Updating a Trigger

* Click the **View** button on the right of the trigger.
* Update the trigger settings.
* Click **Update**.

## Deleting a Trigger

* Click the **View** button on the right of the trigger.
* Click **Delete**.
* The system validates that the trigger is not used by any flow.
* Press **Delete** to confirm.

## Settings

* **Name**: The name of the trigger.
* **URL**: The URL of the API call.
* **Method**: The HTTP method to use for the API call.
* **Body**: The body of the API call containing custom data.
  * **Key**: The key of the data.
  * **Value**: The value of the data.
  * **Custom Value**: The custom value of the data.
* The trigger can include an API Key:
  * **Insert Location**: Where the API Key should be inserted.
    * **Body**: The API Key is inserted in the body.
      * **JSON Key Name**: The name of the JSON key for the API Key.
      * **API Key**: The API Key to insert; search the name to find it.
    * **Header**: The API Key is inserted in the header.
      * **Header Field Name**: The name of the header for the API Key.
      * **API Key**: The API Key to insert; search the name to find it.
