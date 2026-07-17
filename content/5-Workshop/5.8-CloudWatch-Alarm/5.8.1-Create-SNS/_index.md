---
title : "Create SNS Topic & Subscribe Email"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.8.1. </b> "
---

We will create an **SNS Topic** so AWS has a channel to send automated email notifications.

---

### Steps to configure:

1. Search and open the **Simple Notification Service (SNS)** service on the AWS Console.
2. Click on **Topics** in the left menu -> click the **Create topic** button.
3. Topic Configuration:
   - **Type**: Select **Standard**.
   - **Name**: Enter `pg-alerts`.
![sns](/images/h50.png)
   - Click the **Create topic** button at the bottom.
4. **Create Subscription to subscribe Email:**
   - On the details page of the newly created `pg-alerts` topic, click the **Create subscription** button in the bottom table.
   - **Protocol**: Select **Email**.
   - **Endpoint**: Enter your **actual email address**.
   - Click the **Create subscription** button.
![sns](/images/h51.png)
5. **Confirm Subscription:**
   - Open your email inbox, find the email sent from AWS Notifications with the subject *"AWS Notification - Subscription Confirmation"*.
   - Open the email and click the **Confirm Subscription** link to activate.

![Confirm SNS email](/images/h52.png)
