---
title : "Initialize PostgreSQL Database Instance"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.5.2. </b> "
---

We will launch an **RDS PostgreSQL DB Instance** in **Private Subnets**, configured without a **Public IP** address allocation.

---

### Steps to implement:

1. Select **Databases** in the left menu column of the RDS service -> click the **Create database** button -> select **Standard create**.
2. Configure parameters:
   - **Choose a database creation method**: Select **Standard create**.
   - **Engine options**: Select **PostgreSQL**.
   - **Templates**: Select **Production** (or **Free Tier**).
   - **Availability and durability**: Select **Multi-AZ DB instance deployment** (for high availability).
   - **Settings**:
     - **DB instance identifier**: Enter `pg-db`.
     - **Master username**: Enter `postgres`.
     - **Credentials management**: Select **Self managed** and uncheck **Auto generate password**.
     - **Master password**: Enter `12345678` (and confirm password).
![Database RDS 1](/images/h19.png)
   - **Instance configuration**:
     - **DB instance class**: Select **Burstable classes** (includes t instances).
     - **Instance type**: Select configuration **`db.t3.micro`** (or a suitable class to optimize cost).
   - **Storage**:
     - **Storage type**: Select **General Purpose SSD (gp3)**.
     - **Allocated storage**: `20` GB (or suitable capacity).
![Database RDS 2](/images/h20.png)
   - **Connectivity**:
     - **Virtual private cloud (VPC)**: Select **`pg-vpc`**.
     - **DB Subnet Group**: Select **`pg-db-subnet-group`** created in the previous step.
     - **Public access**: Select **No** (Only allow internal connections for absolute security).
     - **VPC security group**: Select **Choose existing**, check **`pg-ecs-sg`** and uncheck the default group `default`.
![Database RDS 2](/images/h21.png)
3. Click the **Create database** button at the bottom.
4. Wait 10-15 minutes for the database to finish initializing. When the status turns green **Available**, click on the database name `pg-db` and copy the **Endpoint** address in the Connectivity section (the address looks like `pg-db.xxxx.ap-southeast-1.rds.amazonaws.com`).
