---
title : "Initialize RDS PostgreSQL in Private Network"
date : 2024-01-01 
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

In this section, we will set up **Amazon RDS PostgreSQL** running completely isolated in **Private Subnets** and use an **EC2 Bastion Host** in the **Public Subnet** to perform the initial database schema initialization.

#### Steps to implement:

1. [Create DB Subnet Group](5.5.1-Create-Subnet-Group/)
2. [Initialize PostgreSQL Database Instance](5.5.2-Create-RDS-Instance/)
3. [Initialize Database via Bastion Host](5.5.3-Initialize-Database/)
