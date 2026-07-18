---
title: "Week 11 Worklog"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Migrate the High-Concurrency Payment Gateway application to AWS Cloud infrastructure (ECS Fargate, RDS, ALB, S3 KMS Export).
* Perform simulated load testing (k6) and evaluate load capacity and data integrity through the CloudWatch monitoring system (Logs, Metrics, Alarms).
* Build detailed hands-on Workshop documentation guiding end-users on the AWS Console.
* Synthesize knowledge and complete 3 detailed reports on the *FCJ Community Day* technology event series.
* Systematize practical knowledge and complete progress reports on the 3 in-depth Blog articles published on the AWS Study Group VN community.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Deploy and test the production application infrastructure on AWS Cloud:<br> - **Practice:** <br>&emsp; + Package Docker Images (Backend & Frontend) and push to ECR.<br>&emsp; + Launch services on ECS Fargate.<br>&emsp; + Establish an isolated RDS PostgreSQL in a Private Subnet and load the schema via an EC2 Bastion Host.<br>&emsp; + Configure periodic RDS Snapshot exports to Amazon S3 using KMS Keys. | 06/29/2026 | 06/29/2026 | <https://calculator.aws/> |
| Tuesday | - Execute simulated load testing and performance monitoring on AWS:<br> - **Practice:** <br>&emsp; + Deploy k6 simulated load scenario with 100 VUs continuously creating 10,000 payment transactions.<br>&emsp; + Check ALB Target Group status (Frontend, Backend).<br>&emsp; + Monitor RequestCount charts and Alarm status on CloudWatch.<br>&emsp; + Check ALB logs and CloudWatch Log Streams (`/ecs/pg-logs`) to evaluate error rates. | 06/30/2026 | 06/30/2026 | |
| Wednesday | - Complete the hands-on Workshop documentation (Step-by-step):<br> - **Practice:** <br>&emsp; + Compile 10 sections of the practical guide (Workshop).<br>&emsp; + Describe detailed point-and-click steps on the AWS Console to build the full 3-tier secure architecture. | 07/01/2026 | 07/01/2026 | |
| Thursday | - Write Event 1 Report: AI, Cloud & Software Engineering Standards (AI Architecture, Prompt Engineering, Agent Systems). <br> - Write Event 2 Report: AWS Learning Path, GenAI Pipeline for Startups, and DevOps (Serverless Migration, 3-tier GenAI, DevOps Foundation). <br> - Write Event 3 Report: Real-time Architecture, GraphRAG, ML Network Security, and Career Transition (WebSocket, GraphRAG, LightGBM, DevOps). | 07/02/2026 | 07/02/2026 | |
| Friday | - Compile Blog 1: Automating CI/CD with GitHub Actions and Amazon ECS Express Mode (OIDC, auto-tag image, ECS AWS Fargate). <br> - Compile Blog 2: Disaster Recovery for Stateful Services on Amazon EKS using Velero (.tar.gz S3, EBS Snapshots, Pod stuck issues). <br> - Compile Blog 3: Cost Optimization with EC2 Capacity Manager and Amazon Athena (Parquet S3, Partition Projection, 3 FinOps SQL scenarios). | 07/03/2026 | 07/03/2026 | |

### Week 11 Achievements:

**1. AWS Application Infrastructure Deployment (Monday)**
* Packaged Backend Gradle and Frontend Nginx source code and pushed to AWS ECR. Successfully deployed to ECS Fargate clusters running safely within Private Subnets.
* Initialized a fully isolated RDS PostgreSQL database, connected seamlessly via JDBC, and loaded the SQL schema through a secure EC2 Bastion Host bridge.
* Established disaster recovery: configured IAM policies/roles allowing the export of KMS-protected compressed RDS Snapshot data to an S3 Bucket.
* Verified ALB successfully recognized the `Healthy` status on port 80 (Frontend) and port 8080 (Backend).
![Backend Target Health Status](/images/h48.png)
![Frontend Target Health Status](/images/h49.png)

**2. Simulated Load Testing & CloudWatch Monitoring (Tuesday)**
* Successfully accessed the application via the Application Load Balancer DNS to test business flows on the browser.
![High-Concurrency Payment Gateway Web](/images/h82.png)
![Account Auditing](/images/h84.png)
![Basic Simulated Test](/images/h85.png)
* Checked CloudWatch Log Group `/ecs/pg-logs`. Successfully extracted Spring Boot launch logs, recording connections to PostgreSQL and the Redis sidecar.
![Backend Log Streams](/images/h86.png)
* Monitored requests through ALB using the `RequestCount` metric (Sum, 1 minutes). The visual spike proved the traffic from the testing tool.
![RequestCount Metrics](/images/h87.png)
* **K6 Results:** The system successfully handled 100 VUs creating 10,000 transactions in 1 minute 50 seconds (99.78% success rate). The distributed lock mechanism preserved consistency (delta = 0.00).
![K6 Data Integrity Results](/images/h88.png)
* Alarm sensors reacted sensitively: AlarmLow (`CPU < 63%`) and AlarmHigh (`CPU > 70%`) were accurately triggered for Auto Scaling.
![CloudWatch Alarms Status](/images/h89.png)

**3. Completed 10-Part Workshop Documentation (Wednesday)**
* Documented detailed 10-step Workshop practical guides using precise professional English terminology matching the current AWS Console interface.
* Comprehensive guides ranging from VPC configuration, Security Groups, IAM Roles, ALB, ECS Clusters to setting up S3 Backup & Recovery, making it easy for end-users to follow and replicate the architecture.

**4. FCJ Community Day Event Reports (Thursday)**
* Packaged Event 1 article: AI Agent Architecture on AWS, Prompt Engineering, Token Economics.
* Completed Event 2 article: Procrastination iceberg, GenAI pipeline with Output Validators.
* Completed Event 3 article: Session management for WebSockets via DynamoDB, Docker Container layers, ML IDS networks, and 8 steps to learn DevOps.

**5. Blog Technical Reports (Friday)**
* **Blog 1 (DevOps):** Lean CI/CD solution, automated network setup, ALB, Auto Scaling with ECS Express Mode.
* **Blog 2 (Cloud Operations):** Disaster recovery using Velero, EKS Pod Identity, handling Pod scheduling errors.
* **Blog 3 (FinOps):** Managing storage beyond the 90-day Console limit, optimized Athena SQL functions for Cloud cost analysis.
