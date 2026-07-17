---
title : "Initialize Application Load Balancer"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.6.2. </b> "
---

We will initialize a public **Application Load Balancer (ALB)** located in 2 **Public Subnets** to receive access requests from the Internet.

---

### Steps to configure:

1. In the left menu column of EC2, click on **Load Balancers** -> click the **Create load balancer** button.
2. Select the **Application Load Balancer** type -> click **Create**.
3. Configure the parameters:
   - **Load balancer name**: Enter `pg-alb`.
   - **Scheme**: Select **Internet-facing** (Receive public traffic).
![Target Groups configuration](/images/h31.png)
   - **Network mapping**:
     - **VPC**: Select **`pg-vpc`**.
     - **Mappings**: Check both of your **2 Public Subnets** (`pg-subnet-public1...` in AZ 1a and `pg-subnet-public2...` in AZ 1b).
![Target Groups configuration](/images/h32.png)
   - **Security groups**: Select the Security Group **`pg-alb-sg`** (and remove the default group `default`).
   - **Listeners and routing**:
     - Default listener port: **HTTP:80** -> Select the action to forward to Target Group **`tg-frontend`**.
![Target Groups configuration](/images/h33.png)
4. Click the **Create load balancer** button at the bottom of the page and wait for the Load Balancer status to change to **Active**.
