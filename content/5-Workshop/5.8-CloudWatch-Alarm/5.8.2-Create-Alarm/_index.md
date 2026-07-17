---
title : "Create CloudWatch Alarm for RequestCount"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.8.2. </b> "
---

We will set up a **CloudWatch Alarm** to monitor the total number of requests sent to the ALB.

---

### Steps to configure:

1. Search and open the **CloudWatch** service on the AWS Console.
2. Left menu column, select **Alarms** -> select **All alarms** -> click the **Create alarm** button in the right corner.
3. Click select **Select metric**:
   - Select the **ApplicationELB** section -> then select **Per AppELB Metrics**.
   - Enter to search and check the metric line named **`RequestCount`** corresponding to your **`pg-alb`** Load Balancer.
   - Click the **Select metric** button at the bottom.
![Alarms](/images/h72.png)
4. **Configure Metric and Alarm Threshold (IMPORTANT):**
   - **Statistic**: Select **`Sum`** - *Absolutely do not select Average*.
   - **Period**: Select **`1 minute`** (For the system to update quickly every minute).
   - **Threshold type**: Select **Static**.
   - **Whenever RequestCount is...**: Select **Greater than threshold** | **than...**: Enter **`1000`** (Alarm when there are over 1000 requests/minute).
![Alarms](/images/h73.png)
   - Click **Next**.
5. **Configure Actions:**
   - **Alarm state trigger**: Select **In alarm**.
   - **Send a notification to the following SNS topic**: Select **Select an existing SNS topic** -> Click to select your **`pg-alerts`** topic.
   - *Ensure that the Actions enabled feature is activated*. Click **Next**.
![Alarms](/images/h56.png)
6. **Name the Alarm:** Enter `pg-alb-high-request-alarm`. 
Click **Next** -> Click **Create alarm** at the bottom.

![Create CloudWatch Alarm](/images/h74.png)
