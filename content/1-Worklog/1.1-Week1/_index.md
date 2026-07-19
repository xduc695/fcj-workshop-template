---
title: "Week 1 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Week 1 Objectives:

* Connect, get acquainted with First Cloud Journey members, and master the regulations.
* Gain a general understanding of AWS cloud computing and core services (Compute, Storage, Networking, Database).
* Initialize an AWS Free Tier 2025 account and complete tasks to receive $200 in practice credits.
* Familiarize with the AWS Management Console, install, and configure the AWS CLI.
* Practice setting up AWS Budgets for secure account cost monitoring and management.
* Understand the AWS Support system and the process of creating Support Cases.
* Research and practice core access management using IAM (Users, Groups, Policies, and Roles).
* Learn the AWS Well-Architected Framework and experiment with system security risk assessments.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Get acquainted with FCJ members. <br> - Read and note internship rules and regulations. | 20/04/2026 | 20/04/2026 | <https://rules.fcjuni.com/1-regulations/> |
| Tuesday | - Learn about AWS and basic service types:<br>&emsp; + Compute (EC2, Lambda) <br>&emsp; + Storage (S3, EBS) <br>&emsp; + Networking (VPC, Security Group) <br>&emsp; + Database (RDS, DynamoDB) | 21/04/2026 | 21/04/2026 | <https://cloudjourney.awsstudygroup.com/>|
| Wednesday | - Initialize AWS Free Tier 2025 account, complete 5 tasks to receive full credits.<br> - Understand the learning roadmap, identify services prone to high costs.<br> - **Practice:** <br>&emsp; + Install, configure, and use the AWS CLI to interact with the account. | 22/04/2026 | 22/04/2026 | <https://000001.awsstudygroup.com/> |
| Thursday | - Research AWS Budgets to configure cost management:<br> - **Practice:** <br>&emsp; + Quick configuration using Budget templates (Cost, Usage, RI, Savings Plans Budget).<br> - Learn the AWS Support system, the process of creating Support Cases, and selecting Severity levels. | 23/04/2026 | 23/04/2026 | <https://000007.awsstudygroup.com/><br><https://000009.awsstudygroup.com/> |
| Friday | - Learn about IAM Users, Groups, Policies, and Roles security identities.<br> - **Practice:** <br>&emsp; + Initialize Admin Group, Admin User, and set up Admin Role.<br>&emsp; + Configure Switch Role for OperatorUser.<br> - Learn about the AWS Well-Architected Framework.<br> - **Practice:**<br>&emsp; + Perform a security risk assessment using the AWS Well-Architected Tool. | 24/04/2026 | 24/04/2026 | <https://000002.awsstudygroup.com/><br> <https://aws.amazon.com/architecture/well-architected/>|

### Week 1 Achievements:

**1. Onboarding and Service Systematization (Monday & Tuesday)**
* Successfully connected and established communication channels with experts in the First Cloud AI Journey project, committing to the working culture.
* Clearly understood the AWS ecosystem with 4 core pillars: Compute (EC2, Lambda), Storage (S3, EBS), Networking (VPC), and Database (RDS, DynamoDB). Grasped the 6-month skill development roadmap.

**2. Account Initialization & AWS CLI Mastery (Wednesday)**
* Successfully initialized the AWS Free Tier 2025 account (Paid Plan) and completed 5 tasks to receive the full $200 practice Credits.
* Successfully identified "dangerous" services prone to unexpected costs (SageMaker, GPU Instances).
![AWS Free Tier Account](/images/1.png)
* Completed AWS CLI installation and configured security identities via `aws configure` (Access Key, Secret Key, Default Region).
* Proficiently used the command line to look up the account (`aws sts get-caller-identity`), check regions, list EC2 entities, and manage Key Pairs.
![AWS CLI Verification](/images/2.png)

**3. Cost Management (Budgets) & Support (Thursday)**
* Mastered and successfully deployed 4 types of budgets (Cost, Usage, RI, Savings Plans) via Budget Templates.
* Established smart alert Thresholds to proactively prevent financial risks.
![AWS Budgets Configuration](/images/3.png)
* Understood Support Plans, Severity level classification, and the interaction process for creating Support Cases.

**4. IAM Access Management & Architectural Assessment (Friday)**
* Established a centralized security structure: Created an AdminGroup, assigned Policies, and added the AdminUser instead of granting scattered permissions.
![IAM Group Initialization](/images/4.png)
![IAM Policies Setup](/images/5.png)
* Configured Trust Relationships for the AdminRole. Successfully performed the Switch Role operation for the OperatorUser, strictly enforcing the Least Privilege principle.
![Switch Role Success](/images/6.png)
* Deployed a system risk assessment using the AWS Well-Architected Tool. Based on the Security pillar, the tool detected 4 High risks and 1 Medium risk, creating a solid foundation for future infrastructure optimization.
![Well-Architected Tool Assessment](/images/10.png)
