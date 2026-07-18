---
title: "Week 3 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Week 3 Objectives:

* Learn about Compute VM services on AWS.
* Practice basic operations with Amazon EC2, set up Node.js application environments on cross-platform (Windows/Linux), combine EC2 server lifecycle management, and strictly control permissions via IAM.
* Deploy infrastructure governance through Tags and Resource Groups for centralized management, helping to automate operations and control resources by project or environment.
* Set up a centralized monitoring and management system by deeply analyzing operational metrics and system logs to configure automated response mechanisms for performance optimization and tight cost control.
* Deploy Auto Scaling Groups for systems capable of automatically scaling and Elastic Load Balancing to balance loads, ensuring high availability.
* Practice deploying real-world websites (WordPress/Prestashop) in the Lightsail environment combined with independent database management.

### Tasks to be implemented this week:

| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Learn about Compute VM services on AWS<br>&emsp; + Amazon EC2 - Instance type, AMI, Backup, Key pair, EBS, Instance store, User Data, Metadata, Auto Scaling Group<br>&emsp; + EFS/FSx <br>&emsp; + Lightsail <br>&emsp; + MGN | 05/04/2026 | 05/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tuesday | - Basic practices with Amazon EC2<br> - **Practice:** <br>&emsp; + Create VPCs for Linux and Windows Instances<br>&emsp; + Initialize and connect to EC2 via SSH/RDP<br>&emsp; + Perform instance type changes<br>&emsp; + Create and manage EBS Snapshots, Custom AMIs<br>&emsp; + Practice access recovery when Key Pair is lost (Zero-Key Recovery) using SSM and User Data<br>&emsp; + Install Desktop GUI for EC2 Ubuntu<br>&emsp; + Set up LAMP, XAMPP, Node.js environments and deploy applications on cross-platform EC2. | 05/05/2026 | 05/05/2026 | <https://000004.awsstudygroup.com/> |
| Wednesday | - Control EC2 service permissions via IAM <br> - **Practice:** <br>&emsp; + Limit EC2 by Region, Instance Type, Storage type<br>&emsp; + Restrict EC2 termination rights by IP and time<br> - Infrastructure governance via Tags and Resource Groups <br> - **Practice:** <br>&emsp; + Assign, modify, delete tags for EC2<br>&emsp; + Use AWS CLI to manipulate tags<br>&emsp; + Create Resource Groups for centralized management. | 05/06/2026 | 05/06/2026 | <https://000027.awsstudygroup.com/> <br><https://000004.awsstudygroup.com/>|
| Thursday | - Set up monitoring systems with Amazon CloudWatch<br> - **Practice:** <br>&emsp; + View, analyze Metrics (Search, Math, Dynamic labels)<br>&emsp; + Query EC2 logs in Logs Insights<br>&emsp; + Create Metrics filters <br>&emsp; + Set up Alarms to send notifications<br>&emsp; + Use centralized CloudWatch Dashboards. | 05/07/2026 | 05/07/2026 | <https://000008.awsstudygroup.com/> |
| Friday | - Deploy Auto Scaling Groups and Elastic Load Balancing<br> - **Practice:**<br>&emsp;+ Create AMIs, Launch Templates, Target Groups, ALBs<br>&emsp; + Set up and test Manual, Scheduled, Dynamic, and Predictive Scaling<br> - Deploy websites in the Lightsail environment<br> - **Practice:**<br>&emsp; + Deploy MySQL, WordPress, Prestashop<br>&emsp; + Set up Static IPs, configure Networking<br>&emsp; + Deploy security, Snapshots, and Scale-ups<br>&emsp; + Create Lightsail incident alarms. | 05/08/2026 | 05/08/2026 | <https://000006.awsstudygroup.com/><br><https://000045.awsstudygroup.com/> |

### Week 3 Achievements:

* Mastered Compute platforms (Amazon EC2, Lightsail) and storage types (EBS, Instance Store, EFS/FSx).
* Understood auto-scaling mechanisms (ASG) and load balancing (ELB).
* Grasped server migration processes (MGN) and centralized management.

**1. EC2 Basics & Application Environments (Tuesday)**
* Successfully differentiated storage types and operated cross-platform on Amazon Linux 2023 and Windows Server 2025.
* Mastered the Change Instance Type technique to flexibly optimize performance.
![EC2](/images/27.png)
* Set up application environments: Successfully deployed LAMP Stack and Node.js on Linux, and XAMPP and Node.js on Windows.
![EC2](/images/28.png)
![EC2](/images/29.png)
* Storage management and deployment optimization: Mastered EBS Snapshots, used Sysprep to standardize Windows, and created Custom AMIs to shorten setup times.
![EC2](/images/30.png)
* System rescue (Zero-Key Recovery): Restored Windows access using SSM Run Command and recovered Linux SSH using User Data.
![EC2](/images/31.png)

**2. Access Control & Resource Management (Wednesday)**
* Resource & cost optimization: Set up IAM Policies limiting EC2 launches strictly to the Singapore Region, with specific configurations (t3.small, t3.large) and disk types (gp3).
![EC2](/images/32.png)
* Zero-Trust Security: Blocked EC2 termination rights based on company IPs and timeframes, applying the principle of least privilege.
![EC2](/images/33.png)
* Resource identity governance: Assigned, modified, and deleted Tags automatically using AWS CLI to filter and search servers quickly.
![EC2](/images/34.png)
* Centralized infrastructure management: Initialized Tag-based Resource Groups to automatically cluster and manage resources by project/environment.
![EC2](/images/35.png)

**3. Centralized Monitoring & Governance with CloudWatch (Thursday)**
* In-depth analysis: Successfully queried Logs Insights, extracted errors (ERROR, WARN), and visually configured CloudWatch Metrics.
![CloudWatch](/images/36.png)
* Automated alerting: Built Metric Filters converting Logs into countable metrics. Configured SNS to send automated incident alert emails.
![CloudWatch](/images/37.png)
* Built CloudWatch Dashboards to monitor the overall health of the system.

**4. Load Balancing & Auto Scaling Group (Friday - Part 1)**
* Set up Application Load Balancer (ALB) and Target Groups to distribute traffic, ensuring High Availability.
![ALB](/images/39.png)
* Operated Auto Scaling Group (ASG): Stress-tested the application using scripts and successfully verified Dynamic Scaling capabilities (auto-scaling servers). Mastered Manual, Scheduled, and Predictive Scaling.
![ASG](/images/40.png)
![ASG](/images/41.png)

**5. Deploying & Operating Amazon Lightsail (Friday - Part 2)**
* Successfully deployed WordPress and PrestaShop websites. Operated independent MySQL with stable Static IPs.
![EC2](/images/42.png)
![EC2](/images/44.png)
![EC2](/images/43.png)
![EC2](/images/45.png)
* Advanced operations: Tightened security by closing the SSH port, created Automated Snapshots for backups, and performed safe infrastructure Scale-ups.
![EC2](/images/46.png)
![EC2](/images/47.png)
![EC2](/images/48.png)
* Configured Alarms to send email alerts when CPU metrics on Lightsail exceeded thresholds.
![EC2](/images/49.png)
