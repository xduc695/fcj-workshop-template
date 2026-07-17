---
title : "Initialize VPC with \"VPC and more\""
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

We use the automated configuration tool "VPC and more" to set up the entire Public and Private Subnets network diagram.

---

### Step 1: Create VPC
1. Log in to the AWS Console -> Search for and select the **VPC** service.
2. Click the **Create VPC** button in the upper right corner.
3. Configure the parameters:
   - **Resources to create**: Select **VPC and more**.
   - **Name tag auto-generation**: Enter prefix **`pg`**.
   - **IPv4 CIDR block**: Keep as **`10.0.0.0/16`**.
![cấu hình vpc 1](/images/h11.png)

   - **Number of Availability Zones (AZs)**: Select **2**.
   - **Number of Public Subnets**: Select **2**.
   - **Number of Private Subnets**: Select **2**.
   - **NAT Gateways**: Select **1 in 1 AZ**.
   - **VPC Endpoints**: Select **None**.
   - **DNS options**: Make sure both **Enable DNS resolution** and **Enable DNS hostnames** are checked.
![cấu hình vpc 2](/images/h75.png)
4. Click **Create VPC** at the bottom to initialize the VPC.

![Tạo VPC thành công](/images/h13.png)

---

### Step 2: Enable Public IP for Public Subnets
To ensure ALB and Bastion Host automatically receive a Public IP:
1. Click on **Subnets** in the left menu.
2. Check the first public subnet: `pg-subnet-public1-ap-southeast-1a`.
3. Click on **Actions** -> select **Edit subnet settings**.
4. Check **Enable auto-assign public IPv4 address**. Click **Save**.
![Bật IP Public](/images/h14.png)
5. Do the same for the second public subnet: `pg-subnet-public2-ap-southeast-1b`.
