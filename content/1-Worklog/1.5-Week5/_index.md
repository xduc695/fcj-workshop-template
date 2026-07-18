---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

* Practice administering and securing AWS resources with IAM, focusing on applying the principle of least privilege, configuring IAM Roles, and setting up access-limiting Conditions to enhance system security.
* Practice deploying the IAM Permission Boundary feature to establish maximum privilege limits for users, helping to efficiently manage permission allocation and prevent privilege escalation risks in the AWS system.
* Practice controlling access and delegating EC2 resource permissions based on Resource Tags using AWS IAM, applying the principle of least privilege by setting up Policies with specific constraints for decentralized system administration.
* Practice deploying AWS Security Hub and AWS Config to establish a comprehensive security monitoring center, evaluating the system's compliance status based on core security standards (CIS, PCI DSS, AWS Foundational) and managing/customizing risk alerts.
* Practice deploying data encryption at rest solutions on Amazon S3 using AWS KMS, while establishing a comprehensive security monitoring mechanism by integrating AWS CloudTrail for event logging and Amazon Athena for auditing data queries.
* Learn about database services on AWS.
* Practice reviewing basic SQL syntax on W3Schools to prepare for database administration.
* Practice deploying and administering relational databases in the cloud with Amazon RDS, connecting from EC2, and performing core operational tasks such as data Backup and Restore.

### Tasks to be implemented this week:

| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Practice AWS IAM administration, configuring IAM Roles, and setting up access-limiting Conditions <br> - **Practice:** <br>&emsp; + Create IAM Group with admin access (EC2, RDS) <br>&emsp; + Create and check IAM User permissions <br>&emsp; + Create Admin IAM Role and Switch role <br>&emsp; + Configure Role Conditions based on IP and time | 05/18/2026 | 05/18/2026 | <https://000044.awsstudygroup.com/> |
| Tuesday | - Practice deploying IAM Permission Boundary <br> - **Practice:** <br>&emsp; + Create IAM policy limiting maximum permissions <br>&emsp; + Apply and test limits on IAM User <br> - Practice EC2 access control based on Resource Tags <br> - **Practice:** <br>&emsp; + Create IAM Policy controlling EC2 via Resource Tags <br>&emsp; + Create IAM Role and attach policy <br>&emsp; + Switch role and verify access | 05/19/2026 | 05/19/2026 | <https://000030.awsstudygroup.com/><br><https://000028.awsstudygroup.com/> |
| Wednesday | - Practice deploying AWS Security Hub and AWS Config <br> - **Practice:** <br>&emsp; + Enable and configure Security Hub and AWS Config <br>&emsp; + Evaluate risks (CIS, PCI DSS, AWS Foundational) <br> - Practice data encryption on S3 using KMS, CloudTrail, and Athena<br> - **Practice:** <br>&emsp; + Create KMS Key <br>&emsp; + Create Bucket and upload data <br>&emsp; + Configure CloudTrail <br>&emsp; + Use Athena to query logs <br>&emsp; + Test security | 05/20/2026 | 05/20/2026 | <https://000018.awsstudygroup.com/><br><https://000033.awsstudygroup.com/> |
| Thursday | - Learn AWS database services: <br>&emsp; + Database Concepts <br>&emsp; + Amazon RDS & Aurora <br>&emsp; + Amazon Redshift <br>&emsp; + Amazon ElastiCache | 05/21/2026 | 05/21/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Friday | - Review basic SQL on W3Schools <br> - Practice deploying and managing RDBMS with Amazon RDS, Backup and Restore <br> - **Practice:** <br>&emsp; + Create VPC, Security Groups for EC2, RDS <br>&emsp; + Initialize EC2 and RDS instance <br>&emsp; + Deploy Node.js application <br>&emsp; + Backup and Restore on RDS | 05/22/2026 | 05/22/2026 | <https://www.w3schools.com/sql/default.asp><br><https://000005.awsstudygroup.com/> |

### Week 5 Achievements:

**1. Advanced Access Security (Monday)**
* Mastered configuring and controlling access with IAM Roles: Successfully deployed the Switch Role mechanism, ensuring temporary administrative access under the principle of least privilege.
* Configured and verified the effectiveness of Conditions; the system automatically blocked access (Access Denied) for incorrect IP addresses or outside permitted timeframes.
![IAM Condition](/images/68.png)

**2. Privilege Management & Resource Tags (Tuesday)**
* Successfully deployed IAM Permission Boundaries: Established maximum permissions policies, tightly controlling and overriding Full Access policies of Users. The system allowed valid EC2 operations in Singapore while automatically disabling all administrative actions in Tokyo.
![IAM Permission Boundary](/images/69.png)
* Successfully implemented decentralized EC2 administration based on Resource Tags: Built IAM Policies forcing users to manage resources only when possessing exact identifier tags (e.g., Team=Alpha). Successfully blocked invalid tag launches and denied access when attempting to modify Resource Tags.
![IAM Resource Tags](/images/70.png)

**3. Comprehensive Security Monitoring & Data Encryption (Wednesday)**
* Established a security monitoring center (Security Hub): Fully integrated AWS Security Hub with AWS Config to automatically scan, detect vulnerabilities, and evaluate based on 3 international standards (AWS Foundational, CIS, PCI DSS).
* Managed and customized risk alerts via the Dashboard interface to analyze severity levels.
![Security Hub](/images/71.png)
* Deployed data Encryption at Rest solutions: Set up automatic encryption for Amazon S3 (SSE-KMS) using a Customer Managed Key from AWS KMS. The system successfully blocked unauthorized internal access without KMS decryption rights and denied direct Public access. Securely shared encrypted data via Presigned URLs.
![Access Denied](/images/73.png)
* Established comprehensive data security auditing workflows: Configured AWS CloudTrail to automatically log S3 Data Events. Integrated Amazon Athena to execute SQL queries for detailed historical event tracing from the log repository.
![Amazon Athena](/images/72.png)

**4. Cloud Database Concepts (Thursday)**
* Systematized foundational knowledge of Databases (Relational, Non-relational, In-memory, Data Warehouse). Understood the Cloud-native architecture of Amazon Aurora.
* Grasped concepts of Amazon Redshift (OLAP, Petabyte processing) and Amazon ElastiCache (Redis/Memcached for offloading the main Database).

**5. RDBMS & Amazon RDS Operations (Friday)**
* Reviewed and solidified SQL fundamentals (DML, DDL, JOIN, GROUP BY) via W3Schools.
![SQL](/images/74.png)
* Deployed Amazon RDS databases: Initialized an RDS database instance and established seamless connection from a Node.js application via environmental configuration files. Successfully executed SQL to import sample datasets.
![RDS](/images/75.png)
* Operated Data Backup and Restore processes: Manually initialized a DB Snapshot. Successfully restored a new DB instance from the existing Snapshot, updated the new Endpoint into the Connection String to ensure uninterrupted application operations.
![Restore](/images/76.png)
