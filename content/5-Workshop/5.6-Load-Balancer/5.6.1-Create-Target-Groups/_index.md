---
title : "Create Target Groups"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.6.1. </b> "
---

We need to create 2 **Target Groups** corresponding to the Frontend (port 80) and Backend (port 8080).

---

### Steps to configure:

1. **Create Target Group for Backend (`tg-backend`):**
   - Go to the **EC2** service -> scroll down the left menu to the **Load Balancing** section -> click on **Target Groups** -> click **Create target group**.
   - **Choose a target type**: Select **IP addresses** (Required for ECS Fargate).
   - **Target group name**: Enter `tg-backend`.
   - **Protocol & Port**: Select **HTTP** and enter port **`8080`** (Port of API Gateway).
![tg-backend configuration 1](/images/h28.png)
   - **VPC**: Select **`pg-vpc`**.
   - **Health check path**: Enter **`/actuator/health`** (To check the status of Spring Boot).
![tg-backend configuration 1](/images/h29.png)
   - Click **Next** -> Click the **Create target group** button.

2. **Create Target Group for Frontend (`tg-frontend`):**
   - Go back to the **Target Groups** page -> click **Create target group**.
   - **Choose a target type**: Check **IP addresses**.
   - **Target group name**: Enter `tg-frontend`.
   - **Protocol & Port**: Select **HTTP** and enter port **`80`**.
   - **VPC**: Click to select **`pg-vpc`**.
   - **Health check path**: Enter **`/`**.
   - Click **Next** -> Click the **Create target group** button (Skip the IP registration step on the next page, the ECS Service will automatically register the Task's IP when launched).
![Target Groups list](/images/h30.png)
