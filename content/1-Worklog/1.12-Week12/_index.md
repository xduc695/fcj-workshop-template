---
title: "Week 12 Worklog"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Week 12 Objectives:

* Execute simulated load testing (k6) and evaluate load capacity through CloudWatch monitoring system (Logs, Metrics, Alarms).
* Complete detailed 10-part hands-on Workshop documentation guiding end-users on AWS Console.
* Compile Project Proposal, operational cost estimates, FCJ Community Day event reports, and technical Blog posts.
* Conduct Self-Evaluation and author Feedback report sharing internship experiences.
* Perform final checks, package all documentation, and hand over project on GitHub Repository.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Simulated Load Testing and Performance Monitoring:<br>&emsp; + Deploy k6 load test scenario with 100 VUs continuously creating 10,000 payment transactions.<br>&emsp; + Check ALB Target Group status, RequestCount charts, and CloudWatch Alarms.<br>&emsp; + Inspect CloudWatch Log Streams (/ecs/pg-logs) to evaluate latency and data integrity. | 06/07/2026 | 06/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.10-verification/> |
| Tuesday | - Finalize Practical Workshop Documentation (Parts 1 - 5):<br>&emsp; + Draft detailed sections for Overview, Prerequisites, VPC Networking, Security Groups, and RDS Database.<br>&emsp; + Describe step-by-step point-and-click instructions on AWS Console for end-users. | 07/07/2026 | 07/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/> |
| Wednesday | - Finalize Practical Workshop Documentation (Parts 6 - 10):<br>&emsp; + Draft sections for Load Balancers, ECS Fargate, CloudWatch Alarms, S3 KMS Backup, and Verification.<br>&emsp; + Standardize technical English terminology and audit resource links. | 08/07/2026 | 08/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/> |
| Thursday | - Proposal Authoring and Editing Event / Blog Reports:<br>&emsp; + Write new Project Proposal integrating 3-tier secure architecture diagram and cost estimation table.<br>&emsp; + Edit and compile 03 event summary reports for FCJ Community Day (AI, GenAI, WebSockets).<br>&emsp; + Edit and compile 03 in-depth Blog posts on DevOps, Cloud Operations, and FinOps. | 09/07/2026 | 09/07/2026 | <https://xduc695.github.io/fcj-workshop-template/2-proposal/><br><https://xduc695.github.io/fcj-workshop-template/3-blogstranslated/><br><https://xduc695.github.io/fcj-workshop-template/4-eventparticipated/> |
| Friday | - Self-Evaluation and Final Repository Packaging:<br>&emsp; + Perform Self-Evaluation and author Feedback report sharing internship experiences.<br>&emsp; + Audit image rendering, Markdown formatting, and Hugo site structure.<br>&emsp; + Commit and push all source code to GitHub Repository ready for final review. | 10/07/2026 | 10/07/2026 | <https://xduc695.github.io/fcj-workshop-template/6-self-evaluation/><br><https://xduc695.github.io/fcj-workshop-template/7-feedback/> |

### Week 12 Achievements:

**1. Simulated Load Testing and CloudWatch Monitoring (Monday)**
* Successfully accessed application via Application Load Balancer DNS to test business flows on browser.
![High-Concurrency Payment Gateway Web](/images/h82.png)
![Account Auditing](/images/h84.png)
![Simulated Test](/images/h85.png)
* Inspected CloudWatch Log Group /ecs/pg-logs. Successfully extracted Spring Boot startup logs, recording connections to PostgreSQL and Redis sidecar.
![Backend Log Streams](/images/h86.png)
* Monitored request traffic through ALB via RequestCount metric (Sum, 1 minutes). Visual spike demonstrated traffic from load test tool.
![RequestCount Metrics](/images/h87.png)
* **K6 Results:** System successfully handled 100 VUs creating 10,000 transactions in 1 minute 50 seconds (99.78% success rate). Distributed lock preserved data consistency (delta = 0.00).
![K6 Data Integrity Results](/images/h88.png)
* Watch the visual demonstration of web interface operation and k6 load testing execution at [System Demo & Load Testing Video](https://drive.google.com/file/d/1J2bgKGyZWc86H7bJlQ3_K-vSoPuC1VAp/view?usp=sharing).
* Alarm sensors reacted sensitively: AlarmLow (CPU < 63%) and AlarmHigh (CPU > 70%) triggered accurately for Auto Scaling.
![CloudWatch Alarms Status](/images/h89.png)

**2. 10-Part Workshop Documentation Series (Tuesday - Wednesday)**
* Documented detailed 10-part Workshop practical guide using precise technical English terminology from VPC setup to ECS Fargate and S3 KMS Backup.

**3. Proposal Document & FCJ Event / Blog Reports (Thursday)**
* Wrote brand new Proposal page integrating Mermaid 3-tier architecture diagram and detailed operational cost estimates (~100 USD/month).
* Completed 03 FCJ Community Day event reports and 03 technical Blog articles published to AWS Study Group VN community.

**4. Self-Evaluation & Final Repository Packaging (Friday)**
* Completed Self-Evaluation report and Feedback article in bilingual English - Vietnamese.
* Audited 100% of image files, ensuring clean rendering across all Markdown documents.
* Local Hugo build succeeded without errors, providing clean visual documentation ready for final project handover.
