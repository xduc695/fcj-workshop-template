---
title: "Week 9 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---
### Week 9 Objectives:

* Review and consolidate all core knowledge learned on the AWS Cloud.
* Research AWS AppSync and practice building a GraphQL API to manipulate real-time data with DynamoDB.
* Research and practice deploying Front-end source code to the AWS Amplify Hosting service to quickly publish a website.
* Practice packaging applications using Docker and deploying them on AWS EC2 connected to Amazon ECR and an RDS database.
* Research the Amazon ECS service and practice configuring Clusters, Task Definitions, and Services to deploy containerized applications combined with an ALB.
* Learn about the Outbox Pattern to ensure inter-service data consistency, combined with Resilience4j to enhance fault tolerance.
* Research AWS infrastructure design standards and learn how to use the Draw.io tool.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Review core knowledge learned on the AWS Cloud: <br>&emsp; + Review networking (VPC, VPC Peering, Transit Gateway, ELB). <br>&emsp; + Review Compute VM (EC2). <br>&emsp; + Review databases (RDS and DynamoDB). <br>&emsp; + Review storage (S3 and EBS). <br>&emsp; + Review security (IAM and Security Groups).<br> - Research AWS AppSync, practice building GraphQL APIs for real-time DynamoDB data: <br> - **Practice:** <br>&emsp; + Create DynamoDB Resolvers <br>&emsp; + Create DynamoDB table and GraphQL API <br>&emsp; + Perform queries or data mutations by defining Resolvers <br>&emsp; + Create more complex objects with AWS AppSyncDynamoDB | 06/15/2026 | 06/15/2026 | <https://cloudjourney.awsstudygroup.com/><br><https://000086.awsstudygroup.com/> |
| Tuesday | - Practice deploying front-end web applications to the cloud using AWS Amplify Hosting: <br> - **Practice:** <br>&emsp; + Package Front-end source code using yarn build <br>&emsp; + Compress the entire build product directory into a .zip file format <br>&emsp; + Initialize the application on the AWS Amplify Console using the manual method (Deploy without Git) <br>&emsp; + Drag and drop the .zip file to publish the website <br>&emsp; + Access and verify the web interface<br> - Practice Docker packaging and EC2 deployment connected to ECR and RDS: <br> - **Practice:** <br>&emsp; + Install Dependencies, deploy and test locally <br>&emsp; + Create DB Subnet Group and RDS Instance <br>&emsp; + Configure EC2 Instance <br>&emsp; + Deploy and test the Application on Docker Images and Docker Compose <br>&emsp; + Create and push Images to ECR and Docker Hub | 06/16/2026 | 06/16/2026 | <https://000015.awsstudygroup.com/> |
| Wednesday | - Research Amazon ECS and practice configuring Clusters, Tasks, Services to deploy containerized applications with ALB: <br> - **Practice:** <br>&emsp; + Upload Docker frontend image to ECR <br>&emsp; + Register namespace in Cloud Map <br>&emsp; + Create ECS Cluster <br>&emsp; + Create ECS backend and frontend Task Definitions <br>&emsp; + Create Target Group <br>&emsp; + Configure Application Load Balancer <br>&emsp; + Implement rolling deployment and Service Scaling with Backend <br>&emsp; + Verify results | 06/17/2026 | 06/17/2026 | <https://000016.awsstudygroup.com/> |
| Thursday | - Research Outbox Pattern theory and fault tolerance solutions with Resilience4j: <br>&emsp; + Understand the principles of Transactional Outbox Pattern architecture to ensure Data Consistency. <br>&emsp; + Research the operation mechanism and configuration parameters of Retry (automatic retries) and Timeout (disconnecting overdue connections). <br>&emsp; + Understand the principles and states (Closed, Open, Half-Open) of Circuit Breakers in Resilience4j. | 06/18/2026 | 06/18/2026 | |
| Friday | - Research AWS infrastructure design standards and explore the Draw.io diagram design tool: <br>&emsp; + Discover the core principles within the AWS Well-Architected Framework. <br>&emsp; + Research the standardized AWS Architecture Icons representing networking, computing, and databases. <br>&emsp; + Learn how to use Draw.io to familiarize yourself with drag-and-drop operations, linking resources, and managing layers when drawing architectural diagrams. | 06/19/2026 | 06/19/2026 | <https://youtu.be/l8isyDe-GwY?si=dS13yhJKd8bE55na> |

### Week 9 Achievements:

**1. Review & AppSync GraphQL Deployment (Monday)**
* Successfully systematized the theory of Amazon VPC, ELB, EC2, S3, EBS, RDS, DynamoDB, IAM, and Security Groups.
* Initialized GraphQL API (`AWSAppSyncTutorial`), building a GraphQL Schema file to manage `Post` and `Comment`. Linked AppSync with DynamoDB table, authorized via IAM Role.
* Programmed Request/Response Mapping Templates (VTL) to map GraphQL Mutations (`addPost`, `updatePost`, `deletePost`) and Queries. Integrated `expectedVersion` to prevent conflicts.
* Successfully executed Queries and Mutations on the Console, syncing data in real-time.
![GraphQL API Execution Result](/images/92.png)
![DynamoDB Item Verification](/images/93.png)

**2. Amplify Hosting & Docker EC2 (Tuesday)**
* Packaged the web source code into a `.zip` file, initialized the application on the Amplify Console (Deploy without Git). Amplify automatically allocated a domain.
![AWS Amplify Deployment Success](/images/94.png)
![Website UI via Amplify Domain](/images/95.png)
* Packaged Frontend/Backend into Docker Images, established a `my-network` internal network connecting Amazon RDS and mapping ports via Nginx. Optimized using `docker-compose.app.yml`.
* Attached IAM Role, pushed Docker Images to Amazon ECR and public Docker Hub. Authentication flow and DB queries operated smoothly on port 3000.
![Docker Application Verification](/images/96.png)
![ECR Container Images Storage](/images/97.png)

**3. Amazon ECS Cluster & ALB Deployment (Wednesday)**
* Established the `FCJ-Lab-cluster` on AWS Fargate. Registered configurations in `fcjresbar-task-fe` and `fcjresbar-task-be`.
![ECS Cluster Task Definitions](/images/98.png)
* Activated two Frontend and Backend services on the ECS cluster (ACTIVE state). Successfully configured Application Load Balancer and Service Scaling.
![ECS Cluster Services](/images/99.png)

**4. Outbox Pattern & Resilience4j Research (Thursday)**
* Mastered the Transactional Outbox Pattern using an intermediate table (`Outbox Table`) and Message Relay/Debezium ensuring transaction integrity (ACID).
* Understood Retry (`waitDuration`), Timeout mechanisms preventing bottlenecks (Thread Starvation), and the 3 Circuit Breaker states (`Closed`, `Open`, `Half-Open`) protecting services.

**5. AWS Architecture & Draw.io (Friday)**
* Absorbed the 6 core pillars of the AWS Well-Architected Framework (High Availability, Multi-AZ, Scalability).
* Identified AWS Architecture Icons. Proficient in Draw.io operations, layer management preparing for complex architectural diagrams.
