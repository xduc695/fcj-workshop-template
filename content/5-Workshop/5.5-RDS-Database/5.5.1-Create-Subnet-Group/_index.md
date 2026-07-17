---
title : "Create DB Subnet Group"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.5.1. </b> "
---

The **DB Subnet Group** specifies the subnets that the RDS instance is allowed to use. We will restrict RDS to run only in **Private Subnets**.

---

### Steps to implement:

1. Search for and select the **RDS** service on the AWS Console search bar.
2. In the left menu column, click on **Subnet groups** -> click the **Create DB subnet group** button.
3. Setup parameters:
   - **Name**: Enter `pg-db-subnet-group`.
   - **Description**: Enter `DB Subnet Group for payment gateway`.
   - **VPC**: Click select **`pg-vpc`**.
   - **Add subnets**:
     - **Availability Zones**: Select 2 AZs (e.g., `ap-southeast-1a` and `ap-southeast-1b`).
     - **Subnets**: Check the 2 **Private Subnets** with IP ranges **`10.0.128.0/20`** and **`10.0.144.0/20`** (automatically created from the VPC step).

![Tạo DB Subnet Group](/images/h18.png)
4. Click the **Create** button at the bottom.
