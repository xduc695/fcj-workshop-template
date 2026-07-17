---
title : "Launch ECS Services"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.7.3. </b> "
---

In this section, we will create an **ECS Cluster** and launch **ECS Services** in the **Private Subnets**.

---

### Step 1: Create ECS Cluster
1. Select **Clusters** in the left menu -> click **Create cluster**.
2. **Cluster name**: Enter `pg-cluster`.
3. **Infrastructure**: Select **Fargate only (serverless)**. Click **Create**.

---

![Create ECS Cluster](/images/h41.png)
![Successfully created ECS Cluster](/images/h42.png)
### Step 2: Launch Backend Service (`pg-backend-service`)
1. Go to Cluster `pg-cluster` -> **Services** tab -> select **Create**.
2. Configuration:
   - **Task definition family**: Select **`pg-backend`** (latest revision).
   - **Service name**: Enter `pg-backend-service`.
   - **Task definition revision**: Enter `1`.
![`pg-backend-service](/images/h43.png)
   - **Deployment configuration**: 
     - **Health check grace period**: Enter `300`.
   - **Networking**:
     - **VPC**: Select **`pg-vpc`**.
     - **Subnets**: Check **only your 2 Private Subnets** (Example: `pg-subnet-private1...` and `pg-subnet-private2...`). *Please uncheck the Public Subnets*.
     - **Security group**: Select **Use existing Security group** -> select **`pg-ecs-sg`** (remove the default group `default`).
     - **Public IP**: Ensure **Turned off** is selected.
![`pg-backend-service](/images/h44.png)
   - **Load balancing**:
     - **Load balancer type**: Select **Application Load Balancer**.
     - **Load balancer**: Select **`pg-alb`**.
     - **Container to load balance**: Select the container `backend:8080:8080`.
![`pg-backend-service](/images/h45.png)
     - **Listener**: Select **Use an existing listener** -> select **`HTTP:80`**.
     - **Target group**: Select **Use an existing target group** -> select **`tg-backend`**.
![`pg-backend-service](/images/h46.png)  
   - **Service auto scaling**:
     - **Minimum number of tasks**: **`1`**.
     - **Maximum number of tasks**: **`5`**.
     - **Scaling policy type**: Select **Target tracking**.
     - **Policy name** : Enter **`cpu-auto-scaling`**.
     - **ECS service metric**: Select **ECSServiceAverageCPUUtilization**.
     - **Target value**: Enter **`70`**.
     - **Scale-out cooldown period**: Enter **`60`**.
     - **Scale-in cooldown period**: Enter **`300`**.
     - **Turn off scale-in**: Uncheck 
![`pg-backend-service](/images/h71.png) 
3. Click **Create**.

---

### Step 3: Launch Frontend Service (`pg-frontend-service`)
1. Return to the Cluster -> click **Create** for the second service.
2. Configuration:
   - **Task definition family**: **`pg-frontend`** | **Service name**: `pg-frontend-service` | **Task definition revision**: `1`.
   - **Networking**: VPC `pg-vpc`, select only 2 **Private Subnets**, Security Group `pg-ecs-sg`, Public IP: **Turned off**.
   - **Load balancing**:
     - **Load balancer**: Select `pg-alb`.
     - **Container**: Select the container `frontend:80:80`.
     - **Listener**: Select **Use an existing listener** -> select **`HTTP:80`**.
     - **Target group**: Select **Use an existing target group** -> select **`tg-frontend`**.
3. Click **Create**.

*Wait for about 1-2 minutes, the status of both Services will change to Running (green color). Now you can use the ALB's DNS to access the web interface!*
![pg-backend-service](/images/h48.png)
![pg-backend-service](/images/h49.png)
![Successfully run and deploy Fargate service](/images/h47.png)
