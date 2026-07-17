---
title : "Simulate Load & Test Alarm"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.8.3. </b> "
---

We will simulate sending a large number of requests to trigger the **CloudWatch Alarm** and receive an **Email notification**.

---

### Step 1: Trigger load simulation
Run the PowerShell Script from your personal computer (replace the DNS address of your ALB):
```powershell
k6 run -e VUS=100 -e ITERATIONS=10000 -e ACCOUNT_IDS="<YOUR_ACCOUNT_UUID>" -e PAYMENT_BASE_URL="http://<YOUR_ALB_URL>" -e ACCOUNT_BASE_URL="http://<YOUR_ALB_URL>" payment_system_k6.js
```

---
![send request from local PowerShell](/images/h79.png)
* Note: You can also use other benchmark tools to send requests.

### Step 2: Test the results
1. Wait for about 1-2 minutes.
2. Check the **CloudWatch Alarm** `pg-alb-high-request-alarm`: Status will turn red indicating **`In alarm`**.
![CloudWatch Alarm In Alarm](/images/h80.png)
3. Open your email inbox: You will receive an automated alert email from AWS SNS.

![CloudWatch Alarm In Alarm](/images/h81.png)
