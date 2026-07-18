---
title : "Verification & Results"
date : 2024-01-01 
weight : 10
chapter : false
pre : " <b> 5.10. </b> "
---

After deploying all infrastructure components (VPC, RDS, ALB, ECS Fargate, CloudWatch Alarm, S3 Backup), this is the final step to test and verify the entire system's correctness and performance.

---

### Step 10.1: Verify Target Group Health Status
Before accessing the web UI, we must ensure that the Application Load Balancer has successfully registered and established connectivity to the Fargate Tasks running in the Private Subnets:
1. Go to the **EC2** service -> select **Target Groups** from the left navigation pane.
2. Verify the health status of both Target Groups:
   - **`tg-frontend`**: Under the **Targets** tab, the IP address list of the Frontend Task must show a **`Healthy`** status on port 80.
   - **`tg-backend`**: The IP address list of the Backend Task must show a **`Healthy`** status on port 8080.

![Backend Target Health](/images/h48.png)
![Frontend Target Health](/images/h49.png)

---

### Step 10.2: Access and Test the Web Interface
1. Go to the **EC2** service -> click **Load Balancers** -> select **`pg-alb`**.
2. Copy the **DNS name**
3. Paste this DNS address into your web browser to access the **High-Concurrency Payment Gateway** application:

![web](/images/h82.png)
![thanh toán và kiểm toán tài khoản](/images/h84.png)
![giả lập kiểm thử cơ bản](/images/h85.png)
---

### Step 10.3: Inspect Container Logs via CloudWatch
To monitor internal microservice activities and verify container-to-container communication:
1. Go to the **CloudWatch** console.
2. Select **Log groups** from the left pane -> click on the **`/ecs/pg-logs`** log group.
3. Check the **Log Streams** corresponding to each container:
   - **`backend/...`**: Contains logs from the Spring Boot services (API Gateway, Account Service, Payment Service, Transaction Service). Look for connection confirmation messages pointing to the database host and the Redis sidecar (`127.0.0.1:6379`).
   - **`redis/...`**: Contains execution logs of the Redis cache engine running alongside the Java container.
   - **`frontend/...`**: Shows access and error logs for the Nginx proxy serving static assets.

---
![Log Streams backend](/images/h86.png)
### Step 10.4: Check Request Metrics in CloudWatch
We can view real-time traffic statistics arriving at our Load Balancer:
1. In the **CloudWatch** console, go to **Metrics** -> **All metrics** in the left menu.
2. Search and select the **`RequestCount`** metric belonging to your Load Balancer **`pg-alb`** (or go to the **Graphed metrics** tab to adjust the time window).
3. Select **Sum** as the **Statistic** and **5 minutes** (or `1 minute`) as the **Period**. You should see the traffic visualization graph:

![Metrics](/images/h87.png)

- The graph will plot a sharp spike (e.g., reaching over 5500 requests) representing the load test script execution you ran via PowerShell.

---

### Step 10.5: Load Testing & Auto Scaling Results Assessment
After executing a high-concurrency load test using `k6`, we will review the achieved metrics to evaluate the robustness of our Microservices architecture on AWS.

1. **High Concurrency Handling:**
   - Based on the load test summary, the system successfully withstood an extreme scenario: **100 virtual users (VUs)** continuously generating **10,000 payment transactions**.
   - **Processing Speed:** The entire process of checking balances, deducting funds, and saving transaction history across 3 microservices was completed fully in just **1 minute and 50 seconds**.
   - The success rate reached **99.78%**. Only a tiny fraction (0.22%) of requests were actively blocked by the API Gateway and Redis Rate Limiter to protect the server from a global crash (Overload Protection).

2. **Absolute Data Integrity (Data Invariant & Distributed Lock):**
   - Observe the `PAYMENT INVARIANT CHECK` section in the output:
   - Even with thousands of transactions concurrently attempting to deduct money from the same account, the final balance in the database matched perfectly (Error margin `delta = 0.00`).
   - This result confirms that the **Redis Distributed Lock** mechanism and **Idempotency** functioned flawlessly, preventing any data loss or inconsistencies (Race Conditions).

![K6 Data Integrity Result](/images/h88.png)

3. **Monitoring and Auto Scaling (CloudWatch & Target Tracking):**
   - From the **CloudWatch Alarms** console, our configured sensors acted highly responsively:
     - **AlarmLow (`CPU < 63%`):** Transitioned to the `In alarm` state precisely when traffic subsided, triggering a scale-in to save costs.
     - **AlarmHigh (`CPU > 70%`):** Closely monitored. Thanks to the exceptional processing capability of the Fargate task (1 vCPU, 2GB RAM), the system consumed all 10,000 requests before reaching the time threshold required to trigger a scale-out.

![CloudWatch Alarms Status](/images/h89.png)

**Conclusion:** The High-Concurrency Payment Gateway system is now completely production-ready, successfully meeting the strictest standards for Reliability, Scalability, and Data Consistency.
