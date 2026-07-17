---
title : "Configure Routing for NAT Gateway"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

To ensure that Fargate Tasks running in Private Subnets can connect Outbound to the Internet to pull Docker Images from ECR and push logs to CloudWatch, we need to configure the NAT Gateway into the Route Table of the Private Subnets.

---

### Steps to configure Private Route Table:

1. At the **VPC** service, click on **Route Tables** in the left menu.
2. Find and click on the **Private Route Table** (which is the Route Table associated with your 2 Private Subnets).
3. Look down to the configuration area below, select the **Routes** tab -> click the **Edit routes** button.
4. Check if this route exists:
   - **Destination**: `0.0.0.0/0`
   - **Target**: Select **NAT Gateway** -> choose the exact NAT Gateway ID just generated automatically like `pg-nat...`.
5. If it doesn't exist, click on **Add route** to add it manually:
   - **Destination**: Enter `0.0.0.0/0`.
   - **Target**: Select **NAT Gateway** and choose the corresponding NAT Gateway ID.
6. Click the **Save changes** button to save.

![Xác nhận NAT route](/images/h15.png)
