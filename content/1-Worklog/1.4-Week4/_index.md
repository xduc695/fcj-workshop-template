---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

* Learn about storage services on AWS.
* Practice deploying a static website on S3 while mastering administration, security, and data redundancy skills through permission assignment, versioning, cross-region replication, and exploring access acceleration using CloudFront alongside S3 troubleshooting methods.
* Practice setting up automated backup and recovery plans for AWS resources using AWS Backup, combined with SNS notification configuration to monitor and ensure data safety.
* Practice deploying an AWS File Storage Gateway to establish a File Share system, facilitating seamless data connection and synchronization between On-premise environments and Amazon S3 cloud storage.
* Practice deploying a high-performance shared file storage system on a Windows environment with Amazon FSx, while mastering advanced administrative skills such as data deduplication, shadow copies, user quota allocation, and flexible resource expansion.
* Learn about security services on AWS.
* Practice basic access administration operations on AWS (IAM) by setting up Users, forming Groups, assigning Policies, and simultaneously applying advanced security mechanisms by Switching Roles according to the principle of least privilege.
* Practice optimal security methods to grant applications secure access to AWS services using IAM Roles, completely replacing the use of Access Keys, which carry the risk of data leakage.

### Tasks to be implemented this week:

| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Learn about storage services on AWS: <br>&emsp; + Amazon Simple Storage Service (S3) <br>&emsp; + Advanced S3 features<br>&emsp; + Snow Family <br>&emsp; + Storage Gateway <br>&emsp; + RTO/RPO <br>&emsp; + Disaster Recovery<br>&emsp; + AWS Backup | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tuesday | - Practice deploying static websites on S3, perform administration, security, and data redundancy skills<br> - **Practice:** <br>&emsp; + Create bucket, upload website source code <br>&emsp; + Enable static website hosting feature <br>&emsp; + Configure Block Public Access, public objects <br>&emsp; + Test Website operations <br>&emsp; + Perform Bucket Versioning <br>&emsp; + Copy S3 Objects to another region (CRR)<br> - Learn CloudFront. | 12/05/2026 | 12/05/2026 | <https://000057.awsstudygroup.com/> |
| Wednesday | - Practice setting up automated backups using AWS Backup and configuring SNS monitoring<br> - **Practice:** <br>&emsp; + Create Backup Plan, Configure notifications, Check backups<br> - Practice deploying AWS File Storage Gateway<br> - **Practice:** <br>&emsp; + Create Bucket and EC2 for Storage Gateway<br>&emsp; + Configure Storage Gateway, File Shares<br>&emsp; + Mapping Driver for Windows. | 13/05/2026 | 13/05/2026 | <https://000013.awsstudygroup.com/><br><https://000024.awsstudygroup.com/> |
| Thursday | - Deploy FSx on Windows environment<br> - **Practice:** <br>&emsp; + Create Multi-AZ file system, Create file share for Windows<br>&emsp; + Test and monitor performance<br>&emsp; + Enable data deduplication, shadow copies<br>&emsp; + Manage user Sessions, Enable quotas<br>&emsp; + Enable Continuously Available Share<br>&emsp; + Expand throughput and capacity<br> - Learn AWS CLI to deploy FSx. | 14/05/2026 | 14/05/2026 | <https://000025.awsstudygroup.com/> |
| Friday | - Learn about security services on AWS: IAM, Cognito, AWS Organizations, KMS, Security Hub<br> - Practice IAM access administration based on least privilege<br> - **Practice:** <br>&emsp; + Create IAM Group, IAM User, IAM Role<br>&emsp; + Switch IAM Role<br> - Practice optimal security methods using IAM Roles instead of Access Keys<br> - **Practice:** <br>&emsp; + Create EC2 Instance and S3 Bucket<br>&emsp; + Test S3 access via access keys<br>&emsp; + Create and Use IAM Role for application. | 15/05/2026 | 15/05/2026 | <https://cloudjourney.awsstudygroup.com/><br><https://000002.awsstudygroup.com/><br><https://000048.awsstudygroup.com>> |

### Week 4 Achievements:

**1. Storage & Data Protection Basics (Monday)**
* Mastered the core storage ecosystem on AWS: Mastered the architecture, operational mechanisms, and advanced administrative features of Amazon S3.
* Migration and Hybrid Storage Solutions: Grasped connectivity and data synchronization solutions between On-premise environments and the Cloud via Storage Gateway and AWS Snow Family.
* Data Protection & Disaster Recovery Strategies: Understood the core business metrics RTO and RPO to ensure system continuity via AWS Backup.

**2. S3 Storage & Data Redundancy (Tuesday)**
* Basic S3 Storage & Permissions Practice: Successfully deployed a static website and established access control mechanisms via Block Public Access and ACLs. Performed object management and migration between S3 Buckets.
![Static Website](/images/50.png)
* S3 Data Protection & Redundancy Practice: Applied Versioning to control changes and prevent risks of accidental data deletion/overwriting.
![Bucket Versioning](/images/51.png)
* Successfully configured Cross-Region Replication (CRR), ensuring high availability and disaster recovery for data.
![S3 Replication](/images/52.png)
![S3 Replication](/images/53.png)
![S3 Replication](/images/54.png)
* System Research & Optimization: Researched Amazon CloudFront's operational mechanism in accelerating content delivery and reducing website latency.

**3. AWS Backup & File Storage Gateway (Wednesday)**
* Automated Backup Setup with AWS Backup: Successfully initialized a Backup Plan with periodic backup rules and secure Backup Vaults. Configured automatic Resource Assignments using Tags.
![Backup Plan](/images/55.png)
* Data Safety Monitoring and Alerting with AWS SNS: Successfully established automated email notifications when Backup or Restore processes complete to respond rapidly to incidents.
![Email Notification](/images/56.png)
![Backup completed successfully](/images/57.png)
* Hybrid Storage Infrastructure Deployment: Initialized an EC2 AMI Storage Gateway, set up Security Groups, and allocated EBS Volumes as Cache buffers. Successfully integrated Storage Gateway with Amazon S3 Buckets.
![Hybrid Storage](/images/58.png)
* File Share Setup and Operations: Configured the SMB protocol for Windows environments, successfully Mapping the Driver on an On-premise machine. Achieved automatic data synchronization to Amazon S3 for safe storage.
![File Share](/images/59.png)
![S3](/images/60.png)

**4. Amazon FSx Centralized File Storage (Thursday)**
* Performance Testing and Monitoring FSx for Windows File Server: Mapped the File Share to a Windows server and tested Read/Write performance using the DiskSpd tool. Monitored via CloudWatch Dashboards and set up High Throughput Alarms.
![DiskSpd](/images/61.png)
* Data Optimization and Redundancy: Enabled Data Deduplication to save space. Deployed Shadow Copies to support restoring previous versions.
![Shadow Copies](/images/62.png)
![High Throughput Alarm](/images/63.png)
* Access Governance and Resource Allocation: Managed User Sessions and Open Files, set up User Quotas to control storage limits, configured Continuously Available Shares, and upgraded Storage Capacity/Throughput Capacity seamlessly.

**5. In-depth IAM Identity & Security (Friday)**
* Core Security Models: Mastered the Shared Responsibility Model, fully grasping IAM, Cognito, AWS Organizations, KMS, and Security Hub services.
* Basic Identity and Permissions Administration: Initialized secure IAM Groups and IAM Users, completely eliminating the use of Root accounts. Set up Inline Policies to strictly grant `sts:AssumeRole` permissions.
* Advanced Security and Privilege Control: Initialized IAM Roles providing temporary access sessions. Practiced Switch Role techniques in absolute compliance with the Least Privilege principle.
![Least Privilege](/images/64.png)
![Switch Role](/images/65.png)
* Security Risk Identification (Access Keys): Tested application connectivity to S3 via Access Keys and Secret Access Keys, recognizing the severe risks of hardcoding static credentials into source code.
![Application Access Key](/images/66.png)
* Optimal Security Deployment (IAM Role): Granted the AmazonS3FullAccess policy to an IAM Role (Trusted Entity EC2). Applied the Role to a server, allowing applications to securely automate file uploads while entirely eliminating data leakage risks.
![Application IAM Role](/images/67.png)
