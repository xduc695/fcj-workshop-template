---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Package application source code using Docker and push Docker Images to Amazon ECR.
* Establish a 3-tier VPC network (Public/Private Subnets), IGW, NAT Gateway, and secure Security Groups.
* Initialize an Amazon RDS PostgreSQL database in a Private Subnet and load the schema via an EC2 Bastion Host.
* Deploy serverless container workloads on AWS ECS Fargate and set up an Application Load Balancer (ALB).
* Configure CloudWatch Alarms, SNS Notifications, and export RDS Snapshots to an S3 Bucket encrypted with a KMS Key.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Application Packaging and ECR Repository Management:<br>&emsp; + Package Backend (Spring Boot) and Frontend (Nginx) using Docker.<br>&emsp; + Initialize Amazon ECR Repositories (pg-backend, pg-frontend).<br>&emsp; + Build and push Docker Images from local environment to Amazon ECR. | 29/06/2026 | 29/06/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.2-prerequiste/> |
| Tuesday | - VPC Network Infrastructure and Security Groups Setup:<br>&emsp; + Create a 3-tier VPC across 2 Availability Zones (AZs) with Public/Private Subnets.<br>&emsp; + Configure Internet Gateway (IGW) and NAT Gateway for outbound connectivity.<br>&emsp; + Set up isolated Security Groups for ALB, ECS Fargate, RDS, and Bastion Host. | 30/06/2026 | 30/06/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.3-vpc-networking/><br><https://xduc695.github.io/fcj-workshop-template/5-workshop/5.4-security-groups/> |
| Wednesday | - Initialize RDS PostgreSQL Database and Bastion Host:<br>&emsp; + Create DB Subnet Group and initialize Amazon RDS PostgreSQL in Private Subnet.<br>&emsp; + Launch an EC2 Bastion Host in Public Subnet.<br>&emsp; + Securely connect via Bastion Host to initialize SQL Schema for RDS. | 01/07/2026 | 01/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.5-rds-database/> |
| Thursday | - Load Balancer Configuration and ECS Fargate Deployment:<br>&emsp; + Create Target Groups and public Application Load Balancer (ALB).<br>&emsp; + Create ECS Cluster, define Task Definitions (backend with Redis sidecar).<br>&emsp; + Deploy ECS Services on Fargate and configure ECS Service Auto Scaling. | 02/07/2026 | 02/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.6-load-balancer/><br><https://xduc695.github.io/fcj-workshop-template/5-workshop/5.7-ecs-fargate/> |
| Friday | - CloudWatch Alarms Monitoring and S3 Backup KMS Setup:<br>&emsp; + Configure Amazon SNS Topic for sending email alerts during high load.<br>&emsp; + Set up CloudWatch Alarms monitoring CPU utilization thresholds.<br>&emsp; + Create S3 Bucket, KMS Key, and perform manual RDS Snapshot Export to S3. | 03/07/2026 | 03/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.8-cloudwatch-alarm/><br><https://xduc695.github.io/fcj-workshop-template/5-workshop/5.9-s3-backup/> |

### Week 11 Achievements:

**1. Container Packaging and ECR Repository Standardization (Monday)**
* Successfully packaged Spring Boot Backend and Nginx Frontend application source code into Docker containers, optimizing image size and setting unified environment variables.
* Initialized ECR Repositories (pg-backend, pg-frontend), tagged and pushed all Docker Images from local development environment to Amazon ECR securely.

**2. 3-Tier VPC Network Infrastructure & Security Groups Setup (Tuesday)**
* Successfully planned a 3-tier VPC network partitioned across 2 Availability Zones (AZs), with clear subnets for Public Subnets, Private App Subnets, and Private DB Subnets.
* Configured Internet Gateway (IGW) for receiving inbound public traffic and NAT Gateway for handling outbound internet traffic from Private Subnets.
* Established strict layered Security Groups firewall rules, applying Least Privilege principles between ALB, ECS Fargate, RDS, and Bastion Host.

**3. RDS PostgreSQL Database & Bastion Host Initialization (Wednesday)**
* Initialized Amazon RDS PostgreSQL database completely isolated within Private DB Subnets, setting up DB Subnet Groups and secure storage configurations.
* Deployed an EC2 Bastion Host in Public Subnet as a secure management bridge. Connected via SSH through Bastion Host to successfully initialize SQL Schema and baseline data for RDS.

**4. Application Load Balancer (ALB) & ECS Fargate Container Deployment (Thursday)**
* Created public Application Load Balancer (ALB), setting up Target Groups and Listener Rules to accurately route traffic to service ports.
* Created ECS Cluster, defined Task Definitions for Backend (with integrated Redis sidecar container for caching and lock) and Nginx Frontend.
* Successfully deployed ECS Services on serverless AWS ECS Fargate. ALB verified Healthy target status on port 80 (Frontend) and port 8080 (Backend).
![Backend Target Health Status](/images/h48.png)
![Frontend Target Health Status](/images/h49.png)

**5. CloudWatch Alarms Monitoring & KMS-Encrypted RDS Snapshot Export to S3 (Friday)**
* Created Amazon S3 Data Bucket and Customer Managed KMS Key. Successfully exported RDS Snapshot to S3 with encryption at rest.
![Create S3 Bucket](/images/h61.png)
![Create KMS Key](/images/h62.png)
![pg-db-snapshot-manual](/images/h65.png)
![Export to Amazon S3 success](/images/h68.png)
* Configured Amazon SNS Topic for email alert subscriptions. Set up CloudWatch Alarms monitoring CPU utilization metrics to ensure automated response during peak loads.
![sns](/images/h50.png)
![Create CloudWatch Alarm](/images/h74.png)
