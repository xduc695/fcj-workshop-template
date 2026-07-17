---
title : "Initialize Database via EC2 Bastion Host"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.5.3. </b> "
---

Because the RDS database is locked in Private Subnets, personal computers at home cannot connect directly to load the schema. We will set up an **EC2 Bastion Host** as a temporary bridge in the Public network.

---

### Step 1: Launch EC2 Bastion Host
1. Search for and select the **EC2** service -> select **Instances** -> click the **Launch instances** button.
2. Setup parameters:
   - **Name**: Enter `pg-bastion`.
   - **OS**: Select **Amazon Linux 2023** (Free Tier eligible version).
   - **Instance type**: Select `t2.micro` (or `t3.micro`).
   - **Key pair**: Select **Proceed without a key pair** (we will connect directly via the web browser).
![Cấu hình ec2 1](/images/h22.png)
   - **Network settings**: Click **Edit**:
     - **VPC**: Select **`pg-vpc`**.
     - **Subnet**: Select the first public subnet (E.g., `pg-subnet-public1-ap-southeast-1a`).
     - **Auto-assign public IP**: Select **Enable**.
     - **Security group**: Select **Create security group** -> Name it: `pg-bastion-sg` -> Inbound rule section: Must select Source as **`0.0.0.0/0`** (Anywhere IPv4) for SSH port 22 to use the EC2 Instance Connect feature on the browser.
![Cấu hình ec2 2](/images/h23.png)
3. Click the **Launch instance** button.

---

### Step 2: Allow Bastion Host to access RDS
1. Go to Security Group **`pg-ecs-sg`** -> click **Edit inbound rules** -> Click **Add rule**:
   - **Type**: Select **PostgreSQL** (port 5432).
   - **Source**: Select **Custom** -> select the **`pg-bastion-sg`** Security Group of the Bastion Host just created. Click **Save rules**.

---

### Step 3: Login and run SQL commands via browser
![Cấu hình Cho phép Bastion Host truy cập RDS](/images/h24.png)
1. At the EC2 Instances page, select the `pg-bastion` virtual machine -> click the **Connect** button at the top corner.
![connect ec2](/images/h25.png)
2. Select the **EC2 Instance Connect** tab -> click the **Connect** button. A black Linux terminal screen will display directly on your browser!
3. Run the following commands in the terminal to install the postgresql client and load data:
   ```bash
   # 1. Install psql client
   sudo dnf install postgresql15 -y

   # 2. Create file containing initialization SQL commands
   cat << 'EOF' > init.sql
   CREATE DATABASE paymentservice;
   CREATE DATABASE accountservice;
   CREATE DATABASE transactionservice;
   EOF
   
   # 3. Execute the command to load the database to RDS (replace <rds-endpoint> with your RDS Endpoint address)
   # When the system asks for Password, enter: yourpassword (when typing the password will be hidden, just type correctly and press Enter)
   psql -h <rds-endpoint> -U postgres -d postgres -f init.sql
   ```  
![ Cài đặt psql client](/images/h26.png)  
![ Tạo và thực thi nạp db lên rds](/images/h27.png)
   *A successful load will report `CREATE DATABASE` for 3 databases.*

4. **Terminate EC2 Bastion Host after finishing loading:**
   - Go back to the EC2 Instances management page -> Select virtual machine `pg-bastion` -> Select **Instance state** -> select **Terminate instance** to delete the virtual machine to avoid incurring costs.
