---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Solidify knowledge of CI/CD and learn the YAML file structure used to build pipelines on GitHub Actions.
* Build the database structure for the group project (High-Concurrency Payment Gateway).
* Research and summarize the main services required in the group project's architectural model.
* Learn the workflow and practice automated deployment to Amazon ECS Express Mode using GitHub Actions.
* Summarize the knowledge gained about automated deployment with GitHub Actions for Amazon ECS Express Mode to write a community sharing post.
* Learn the process of deploying multi-Region endpoint routing for Amazon Aurora DSQL.

### Tasks to be implemented this week:

| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Learn about CI/CD and GitHub Actions pipeline structure: <br>&emsp; + Review CI/CD concepts <br>&emsp; + Understand the role of GitHub Actions <br>&emsp; + Learn YAML structure in pipelines <br>&emsp; + Analyze core components of a workflow | 06/01/2026 | 06/01/2026 | |
| Tuesday | - Build database structure for the High-Concurrency Payment Gateway project: <br>&emsp; + Identify main tables in the system <br>&emsp; + Design tables for users, customers, accounts, transactions, balance history... <br>&emsp; + Add tables for audit logs, notifications, outbox events <br>&emsp; + Create foreign keys, constraints, and indexes | 06/02/2026 | 06/02/2026 | |
| Wednesday | - Research and summarize main services in the group project architecture:<br>&emsp; + Identify core system components <br>&emsp; + Learn about backend, frontend, database, storage, security, and routing services | 06/03/2026 | 06/03/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thursday | - Practice automated deployment to Amazon ECS Express Mode using GitHub Actions <br> - **Practice:** <br>&emsp; + Fork and clone the sample repository <br>&emsp; + Create Amazon ECR repository <br>&emsp; + Configure IAM Role, Policy, OIDC Provider <br>&emsp; + Configure GitHub Repository Variables <br>&emsp; + Run workflow to build and push Docker image <br>&emsp; + Deploy to Amazon ECS Express Mode | 06/04/2026 | 06/04/2026 | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/> |
| Friday | - Write a sharing post about automated deployment with GitHub Actions for Amazon ECS Express Mode: <br>&emsp; + Summarize the AWS Blog content <br>&emsp; + Systematize the CI/CD workflow and analyze component roles <br>&emsp; + Summarize practice steps and errors encountered <br> - Learn the process of deploying multi-Region endpoint routing for Amazon Aurora DSQL: <br>&emsp; + Understand Aurora DSQL multi-Region model, Route 53 health checks, endpoint selection mechanism, configuration, and failover | 06/05/2026 | 06/05/2026 | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/><br><https://awsstudygroup.com/2026/01/09/trien-khai-dinh-tuyen-endpoint-da-region-cho-amazon-aurora-dsql/> |

### Week 7 Achievements:

**1. CI/CD & GitHub Actions (Monday)**
* Solidified CI/CD knowledge: Grasped the core role of CI/CD in automating software development and deployment processes. Understood how GitHub Actions uses workflows to automatically execute build, test, and deploy steps.
* Understood YAML file structure in pipelines: Grasped the main components of a workflow file such as `name`, `on`, `jobs`, `steps`, `uses`, and `run`. Knew how to analyze the basic execution flow of a pipeline.

**2. System Database Design (Tuesday)**
* Built the database structure for the group project (High-Concurrency Payment Gateway): Identified main tables including users, customers, accounts, transactions, notifications, and system logs (audit log, outbox event).
* Established primary keys, foreign keys, strict data constraints, and optimized indexes for high-concurrency transaction queries.

**3. Group Project Architecture (Wednesday)**
* Summarized the main services in the architectural model: Identified core system components including backend, frontend, database, storage, security, and routing.
* Deeply understood the role of each service on AWS, establishing a solid foundation to select, adjust, and perfect the architecture for upcoming Sprints.

**4. CI/CD Deployment with Amazon ECS Express Mode (Thursday)**
* Successfully deployed an automated CI/CD pipeline using GitHub Actions: The workflow automatically executed steps to build a Docker image, tag the image based on commits, push it to Amazon ECR, and deploy the service to Amazon ECS Express Mode.
* Verified the successful deployment flow via the workflow logs.
![GitHub Actions Workflow](/images/77.png)
* Configured secure authentication using IAM Roles and OIDC: Created the `github-actions-ecs-role` IAM Role for GitHub Actions to assume. Utilized the OIDC Provider to eliminate the long-term storage of AWS Access Keys, ensuring absolute pipeline security.
![IAM OIDC Role](/images/78.png)
* Deployed containerized applications to Amazon ECS Express Mode: ECS successfully created the service, task, and endpoint to run the application. The Docker image was accurately managed on ECR.
![Amazon ECS Express Service](/images/79.png)

**5. Extended Knowledge & Community (Friday)**
* Wrote technical sharing posts: Summarized the automated deployment steps with GitHub Actions, analyzing the roles of Docker, ECR, ECS Express Mode, and OIDC. Compiled a high-quality article for the community, encapsulating common errors and their solutions.
* Multi-Region endpoint routing with Amazon Aurora DSQL: Understood the multi-Region architecture and the role of Route 53 health checks in monitoring endpoints. Grasped the mechanism for selecting the lowest-latency endpoint to optimize connections and enable automatic failover between Regions.
