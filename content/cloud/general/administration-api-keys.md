---
title: Administration - API Keys
weight: 153
---

This page stores the secrets for the API keys that are used to access this system or third-party systems.

* **LGDXRobot Cloud API Keys**: API keys used by third-party systems to access LGDXRobot Cloud.
* **Third-Party API Keys**: API keys used by LGDXRobot Cloud to access third-party systems when triggering a trigger that requires an API key.

## Creating an API Key

* Click the **Create API Key** button at the top right.
* Enter the API key settings.
* Click **Create**.

## API Key Creation Settings

* **API Key Category**: The category of the API key, which cannot be changed after creation.
* **Name**: The name of the API key.
* **Secret**: The secret of the API key, which is generated automatically for LGDXRobot Cloud API Keys.

## Viewing an API Key Secret

* Click the **View** button on the right of the API key.
* Navigate to the **API Key Secret** section.
* Click **Press here to show secret** to reveal the secret.

An activity log will be created when the secret is revealed.
{.alert .alert-info}

## Updating an API Key

* Click the **View** button on the right of the API key.
* Update the API key settings.
* Click **Update** in the corresponding section; otherwise, the setting will not be updated.

## API Key Update Settings

* **Name**: The name of the API key.
* **Update Secret** (Third-Party API Keys Only): The updated secret of the API key.

## Deleting an API Key

* Click the **View** button on the right of the API key.
* Click **Delete**.
* Click **Delete** to confirm.

The system does not validate whether the API key is used by any running task, and deleting it may disrupt the task.
{.alert .alert-warning}
