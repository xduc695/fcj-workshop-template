---
title : "Set up Security Groups"
date : 2024-01-01 
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

In this section, we will create **Security Groups** to act as a virtual firewall controlling inbound/outbound traffic to the Application Load Balancer, ECS Tasks, and RDS Database.

---

### Step 4.1: Create Security Group for Application Load Balancer (`pg-alb-sg`)
The ALB will be the checkpoint receiving direct traffic from the Internet sent to the system:
1. Open the **EC2** service on the AWS Console -> Scroll down the left menu to the **Network & Security** section -> click on **Security Groups**.
2. Click the **Create security group** button on the right side of the screen.
3. Setup information:
   - **Security group name**: Enter `pg-alb-sg`.
   - **Description**: Enter `Allow HTTP traffic from internet`.
   - **VPC**: Click select **`pg-vpc`** (Absolutely do not select the default VPC).
4. **Configure Inbound rules:** Click **Add rule**:
   - **Type**: Select **HTTP** (port 80).
   - **Source**: Select **Anywhere-IPv4** (`0.0.0.0/0`) to allow access from everyone.
5. Click the **Create security group** button at the bottom.

![Tạo Security Group cho ALB](/images/h16.png)

---

### Step 4.2: Create Security Group for Containers & Database (`pg-ecs-sg`)
This Security Group will protect the Fargate Tasks running Frontend, combined Backend, and RDS PostgreSQL database in the Private network:
1. Go back to the Security Groups page -> Click the **Create security group** button.
2. Setup information:
   - **Security group name**: Enter `pg-ecs-sg`.
   - **Description**: Enter `Allow traffic from ALB and internal containers`.
   - **VPC**: Click select **`pg-vpc`**.
3. **Configure Inbound rules:** Add the following 4 specific rules to ensure strict authorization:
   - **Rule 1 (For Frontend):** Type: **HTTP** | Source: Select **Custom** -> select the Security Group **`pg-alb-sg`** just created in Step 4.1.
   - **Rule 2 (For Spring Boot Backend):** Type: Select **Custom TCP** | Port range: Enter `8080` | Source: Select **Custom** -> select the Security Group **`pg-alb-sg`**.
4. Click the **Create security group** button at the bottom.
![ Security Group cho ECS và RDS](/images/h17.png)
5. Go to Security Group **`pg-ecs-sg`** -> click **Edit inbound rules** -> Click **Add rule**:
    - **Rule 3 (For PostgreSQL Database):** Type: Select **PostgreSQL** (port 5432) | Source: Select **Custom** -> select this very Security Group **`pg-ecs-sg`** being created. (This method allows the Backend container associated with the SG to have permission to call RDS).
   - **Rule 4 (Internal connection):** Type: Select **All traffic** | Source: Select **Custom** -> select this very Security Group **`pg-ecs-sg`** being created. (Helps the Java container cross-connect with the Redis container sidecar on the same task).Click **Save rules**.