---
title: "Week 12 Worklog"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Week 12 Objectives:

* Complete detailed 10-part hands-on Workshop documentation guiding end-users on the AWS Console.
* Synthesize knowledge and complete FCJ Community Day event reports and in-depth technical Blog posts.
* Perform simulated load testing (k6) and evaluate load capacity through CloudWatch monitoring (Logs, Metrics, Alarms).
* Compile Project Proposal, operational cost estimates, and perform Self-Evaluation.
* Conduct final review, package all documentation, and hand over project on GitHub Repository.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Finalize Practical Workshop Documentation (Step-by-step):<br>&emsp; + Compile 10 sections of hands-on Workshop guide.<br>&emsp; + Detail point-and-click steps on AWS Console from VPC, RDS, ALB to ECS Fargate and S3 Backup. | 06/07/2026 | 06/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/> |
| Tuesday | - Event Reporting and Technical Blog Writing:<br>&emsp; + Write 03 event summary reports for FCJ Community Day (AI, GenAI, WebSockets).<br>&emsp; + Author 03 technical Blog posts on DevOps, Cloud Operations, and FinOps. | 07/07/2026 | 07/07/2026 | <https://xduc695.github.io/fcj-workshop-template/3-blogstranslated/><br><https://xduc695.github.io/fcj-workshop-template/4-eventparticipated/> |
| Wednesday | - Load Testing and Performance Reporting:<br>&emsp; + Deploy k6 load test scenario with 100 VUs creating 10,000 transactions.<br>&emsp; + Monitor ALB RequestCount charts and CloudWatch Alarm statuses.<br>&emsp; + Evaluate data integrity and inspect system log streams. | 08/07/2026 | 08/07/2026 | <https://xduc695.github.io/fcj-workshop-template/5-workshop/5.10-verification/> |
| Thursday | - Finalize Project Proposal:<br>&emsp; + Author 3-tier secure architecture proposal document.<br>&emsp; + Build operational cost estimation table using AWS Pricing Calculator. | 09/07/2026 | 09/07/2026 | <https://xduc695.github.io/fcj-workshop-template/2-proposal/> |
| Friday | - Self-Evaluation and Project Finalization:<br>&emsp; + Conduct Self-Evaluation after 12 weeks of internship.<br>&emsp; + Write Feedback report sharing internship experiences.<br>&emsp; + Final check and push all source code and documents to GitHub Repository. | 10/07/2026 | 10/07/2026 | <https://xduc695.github.io/fcj-workshop-template/6-self-evaluation/><br><https://xduc695.github.io/fcj-workshop-template/7-feedback/> |

### Week 12 Achievements:

**1. Workshop Documentation Series and Blog Reports (Monday - Tuesday)**
* Documented detailed 10-part Workshop practical guide using precise technical English terminology.
* Completed 03 FCJ Community Day event reports and 03 technical Blog articles published to AWS Study Group VN community.

**2. Simulated Load Testing and CloudWatch Monitoring (Wednesday)**
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
* Alarm sensors reacted sensitively: AlarmLow (CPU < 63%) and AlarmHigh (CPU > 70%) triggered accurately for Auto Scaling.
![CloudWatch Alarms Status](/images/h89.png)

**3. Proposal & Self-Evaluation (Thursday - Friday)**
* Wrote brand new Proposal page integrating Mermaid 3-tier architecture diagram and detailed operational cost estimates (~100 USD/month).
* Completed Self-Evaluation report and Feedback article in bilingual English - Vietnamese.

**4. Final Review & Repository Packaging (Friday)**
* Audited 100% of image files, ensuring clean rendering across all Markdown documents.
* Local Hugo build succeeded without errors, providing clean visual documentation ready for final project handover.
