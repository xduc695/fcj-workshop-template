---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
# High-Concurrency Payment Gateway Infrastructure on AWS
## 3-Tier Secure Networking with ECS Fargate and S3 Backup

### 1. Executive Summary
The **High-Concurrency Payment Gateway** project is designed to provide a highly secure, scalable, and resilient cloud infrastructure on AWS for a microservice-based payment application. The goal is to migrate the Payment Gateway from local development environments to a production-grade AWS architecture. The design utilizes a **3-tier VPC network (Public/Private Subnets)** to isolate critical systems. Computing workloads are run on serverless **AWS ECS Fargate** (hosting Frontend Nginx, Spring Boot Backend microservices, and a Redis sidecar cache), while transaction data is stored in a private **Amazon RDS PostgreSQL** instance. Real-time logging, alarms, and automated database backups are integrated using **Amazon CloudWatch**, **Amazon SNS**, and encrypted **Amazon S3** snapshot exports with customer-managed KMS keys.

### 2. Problem Statement
#### What’s the Problem?
Traditional payment processing systems deployed on-premises or single virtual machines face several key issues:
- **Security Vulnerabilities:** Databases and backend APIs containing sensitive financial and user credentials are directly exposed to the public Internet (using Public IPs).
- **Poor Scalability:** Inability to handle rapid spikes in transaction volumes (such as flash sales), leading to service latency or server crashes.
- **Lack of Monitoring:** Administrators lack real-time visibility and instant alerts when compute tasks crash or traffic surges.
- **Data Loss Risks:** Database backup processes are often manual, unencrypted, and stored insecurely, posing a threat to business continuity.

#### The Solution
This AWS-based architecture resolves these challenges:
- **Network Isolation:** All backend containers and the RDS database run in isolated **Private Subnets**, communicating outbound only through a **NAT Gateway**.
- **Serverless Compute:** Deploying application layers on **AWS ECS Fargate** eliminates virtual machine (EC2) OS patching and management overhead.
- **High Availability & Routing:** An **Application Load Balancer (ALB)** in **Public Subnets** intercepts public HTTP traffic (port 80), routing API queries (`/api/*`) to the backend API Gateway (port 8080) and serving static files via the Frontend Nginx containers.
- **Real-time Alerting:** A **CloudWatch Alarm** triggers an **Amazon SNS** topic to dispatch email alerts to administrators if traffic exceeds the defined threshold (RequestCount > 100 requests/minute).
- **Secure Backup:** Database Snapshots are taken and exported to an **Amazon S3 Bucket**, encrypted with a custom-managed symmetric **KMS Key** to ensure enterprise-grade security.
- **EC2 Bastion Host:** A temporary jump box is deployed in the Public Subnet only during initial schema seeding, and terminated immediately after to minimize cost and attack surface.

#### Benefits and Return on Investment
- **Compliance and Security:** Isolation of network resources and KMS data encryption align the platform with financial data security principles.
- **Self-Healing Infrastructure:** Load balancer health checks monitor Fargate tasks, automatically recreating unhealthy tasks to maintain uptime.
- **Cost Efficiency:** By leveraging Fargate serverless containers and stopping idle components, monthly infrastructure costs are optimized. Operational costs are estimated at $100 to $120 per month for load testing, offering a superior ROI compared to provisioning physical servers on-premises.

### 3. Solution Architecture
The architecture implements a 3-tier networking layout (Public, Private App, Private DB) within a custom AWS VPC:
![diagram](/images/diagram.jpg)

#### AWS Services Used
- **Amazon VPC**: Drives network virtualization (4 Subnets, Route Tables, Internet Gateway, and NAT Gateway).
- **AWS ECS Fargate**: Serverless container orchestration for Nginx Frontend and Java Backend.
- **Amazon RDS (PostgreSQL)**: Fully-managed relational database isolated in Private Subnets.
- **Amazon S3**: Secure object storage hosting compressed database snapshots.
- **AWS KMS**: Manages the symmetric Customer Managed Key to encrypt snapshot exports.
- **Amazon CloudWatch**: Collects log streams from tasks (`/ecs/pg-logs`) and evaluates traffic thresholds.
- **Amazon SNS**: Distributes real-time email notifications.
- **Amazon EC2**: Provisions the temporary Bastion Host for DB initialization.

#### Component Design
- **Frontend Task**: Runs an Nginx web server hosting the NextGenPay static interface, receiving traffic from the ALB on port 80.
- **Backend Task**: A Multi-Container Task enclosing the Java/Spring Boot combined microservices (API Gateway, Account, Payment, Transaction services) and a Redis sidecar cache communicating on `localhost`.
- **Database & Backup**: RDS PostgreSQL instance storing user balances and transactions. Manual snapshots are captured and exported to the S3 bucket, encrypted via `pg-s3-export-key`.

### 4. Technical Implementation
#### Implementation Phases
The project execution is organized into 4 logical phases:
1. **Application Packaging & Design:** Compile the Gradle Spring Boot project and static assets into Docker images, pushing them to ECR Private Repositories. Model the 3-tier VPC configuration.
2. **Infrastructure provisioning:** Initialize the VPC, Route Tables, NAT Gateway, Security Groups, and RDS PostgreSQL instance. Access the private RDS database via a Bastion Host to execute schema creation.
3. **Container Deployment:** Configure ALB Target Groups and Listener Rules, create ECS Task Definitions JSON, and spin up Frontend and Backend Fargate services.
4. **Monitoring & Secure Backup:** Set up CloudWatch Alarms for the RequestCount metric and bind it to the SNS alerts topic. Create the KMS Key, apply appropriate IAM Policies, and export DB snapshots to S3.

#### Technical Requirements
- **Container Registry & Compute:** AWS ECR (2 private repositories), AWS ECS (Fargate cluster, Task execution role, Task Definitions with multi-container definitions).
- **Secure Networking:** Custom VPC with 2 Public and 2 Private Subnets, NAT Gateway, Route Tables routing outbound traffic, and Security Groups enforcing least privilege (restricting DB ingress to EC2 Bastion and ECS tasks).
- **Relational Storage & Backup:** Amazon RDS PostgreSQL, Amazon S3 for archival storage, AWS KMS Symmetric Key, and IAM Roles allowing the RDS Export service to assume permissions.

### 5. Timeline & Milestones
- **Week 1:** Package the source code as Docker images and publish to AWS ECR. Set up the custom 3-tier VPC network, NAT Gateway, and Security Groups.
- **Week 2:** Create the RDS PostgreSQL instance in Private Subnets. Spin up the Bastion Host to seed database schemas. Define ALB Target Groups and Listener Rules.
- **Week 3:** Register ECS Task Definitions for Frontend and Backend services, launching them inside the Fargate cluster. Create CloudWatch Alarms and associate SNS email alerts.
- **Week 4:** Set up the Customer Managed KMS Key, configure IAM policies, and run the RDS Snapshot export to S3. Run end-to-end load tests using PowerShell and conduct resource cleanup.

### 6. Budget Estimation
Estimated infrastructure costs for running the environment for 1 month:

#### Infrastructure Costs
- **VPC NAT Gateway:** ~$32.40/month ($0.045/hour in 1 AZ).
- **Application Load Balancer:** ~$16.20/month ($0.0225/hour).
- **Amazon RDS (db.t3.micro Multi-AZ PostgreSQL):** ~$26.28/month (db.t3.micro instance with 20GB gp3 storage).
- **AWS ECS Fargate Tasks (vCPU & RAM):** ~$30.00/month (Backend task 1 vCPU/2GB RAM and Frontend task 0.25 vCPU/0.5GB RAM running continuously).
- **AWS KMS Key:** $1.00/month.
- **Amazon S3 & CloudWatch Logs:** ~$3.00/month (log storage and compressed snapshot size).
- **Amazon SNS:** $0.00/month (within Free Tier limits).

**Total Estimated Cost:** ~$110.00/month (~$1,320.00/year).

### 7. Risk Assessment
#### Risk Matrix
- **Request Overload (Flash Sales):** High impact, medium probability.
- **Database Connection Failure:** Critical impact, low probability.
- **Access Credentials Leak:** Critical impact, low probability.

#### Mitigation Strategies
- **Request Overload:** CloudWatch Alarm alerts administrators via SNS email, allowing them to manually or automatically scale Fargate task replicas.
- **Database Failure:** RDS is deployed as Multi-AZ, allowing automatic failover to a standby node if the primary database crashes.
- **Access Credentials Leak:** Enforce strict IAM policies and use KMS key policies that only allow the RDS export engine to decrypt data for S3 transport.

### 8. Expected Outcomes
#### Technical Improvements
- **Comprehensive Network Security:** Completely removes public interfaces from database and backend servers, isolating them using strict Security Groups.
- **Centralized Logs & Metrics:** All microservices consolidate logs to CloudWatch Log Streams, providing a centralized dashboard for performance monitoring.
- **Resilient Backups:** Compressed snapshots are encrypted and securely exported to S3, assuring reliable disaster recovery.

#### Long-term Value
Establishes a solid cloud architecture template to deploy future microservices. Enables easy transition to Infrastructure as Code (IaC) using Terraform or CloudFormation for automatic environment replication.