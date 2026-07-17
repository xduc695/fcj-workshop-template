---
title : "Prepare Log Group & IAM Role"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

We need to create a **CloudWatch Log Group** and **IAM Task Execution Role** so Fargate can run successfully and write logs.

---

### Step 1: Create CloudWatch Log Group
Fargate uses the `awslogs` driver to write system logs, requiring the Log Group to be created in advance:
1. Search and select the **CloudWatch** service on the AWS Console.
2. In the left menu column, select **Log groups** -> click **Create log group**.
3. **Log group name**: Enter exactly **`/ecs/pg-logs`**.
4. **Retention setting**: Select **1 day** (or 1 week) to save space. Click **Create**.

![Create Log Group](/images/h36.png)

---

### Step 2: Create IAM Task Execution Role for Fargate (`ecsTaskExecutionRole`)
This Role grants permissions to the ECS Agent to pull Docker Images from ECR and push logs to CloudWatch:
1. Go to the **IAM** service -> select **Roles** in the left menu -> click **Create role**.
2. **Trusted entity type**: Select **AWS service**.
3. **Service or use case**: Select **Elastic Container Service** -> Select **Elastic Container Service Task** below. Click **Next**.
![IAM](/images/h37.png)
4. **Permissions policies**: Search and check the policy **`AmazonECSTaskExecutionRolePolicy`**. Click **Next**.
![IAM](/images/h38.png)
5. **Role name**: Enter exactly: **`ecsTaskExecutionRole`**.
6. Click **Create role** at the bottom.
