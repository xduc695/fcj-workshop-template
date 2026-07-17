---
title : "Configure Listener Rules for API Gateway"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.6.3. </b> "
---

For API requests from the client (e.g., `/api/accounts`) to be sent to the API Gateway backend instead of the Frontend Nginx, we configure a **Listener Rule** for routing.

---

### Steps to configure:

1. Open the Load Balancers administration page -> Click on your `pg-alb` name.
2. Select the **Listeners and rules** tab in the middle of the screen.
3. Click directly on **`HTTP:80`** (the blue link).
4. Select the **Rules** tab -> click the **Add rules** button.
5. Set parameters for the new Rule:
   - **Rule name**: Enter `api-rule`.
   - **Conditions**: Click **Add condition** -> select the type as **Path** -> enter the path as **`/api/*`** -> click **Next**.
   - **Actions**: Click **Forward to target groups** -> select Target Group **`tg-backend`** -> click **Next**.
![Configure Listener Rule](/images/h34.png)
   - **Priority**: Enter the number **`10`**.
![Configure Listener Rule](/images/h35.png)
6. Click the **Add rule** button to save.
