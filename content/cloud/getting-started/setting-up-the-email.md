---
title: Setting Up the Email
weight: 7
---

LGDXRobot Cloud relies on email notifications for incidents, but these emails are only sent to a specific group of users. The user can opt in to email notifications and test the functionality.

## Step 1: Navigate to The User Settings Page

Expand the **Administration**, select **Users** and click the **View** link for the account.

## Step 2: Enable Email Notifications

Press **Add Role** button, then search for **Email Receipient** and click **Update**.

![Screenshot of the user settings page](../img/email/email1.png)

## Step 3: Test Email Notifications

Create a new task with the same details as task just created. Then expand the **Automation**, select **Tasks** and choose **Running** from the **Select Task Category** dropdown.

Click the **View** for the task just created.

![Screenshot of the tasks page](../img/email/email2.png)

Next, click the **Abort** button at the end of the task details page, and then click **Abort** again in the confirmation dialog.

![Screenshot of the task details page](../img/email/email3.png)

The task will be aborted, and an email is sent.

![Screenshot of the email](../img/email/email4.png)