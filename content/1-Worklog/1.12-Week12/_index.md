---
title: "Week 12 Worklog"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
{{% notice warning %}} 
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

### Week 12 Objectives:

* Implement Caching and advanced access control solutions using Redis to optimize performance, prevent transaction duplication, and safeguard system resources.
* Establish a distributed Rate Limiting mechanism based on Redis at the API Gateway, applying flexible rate limit policies per user identified through JWT.
* Address concurrency control and transaction duplication (Idempotency) using Redis-based Distributed Locks and Idempotency Token filters.
* Migrate the Payment Gateway Microservices application to AWS cloud infrastructure, build a detailed step-by-step hands-on guide (Workshop), and complete the project proposal incorporating a 3-tier secure architecture diagram.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | ---------- | --------------- | ------------------ |
| 2 | - Research database caching with Redis:<br>&emsp; + Understand distributed cache principles and patterns (Cache-Aside, Write-Through).<br>&emsp; + Configure Spring Boot Redis Starter dependency. | 07/03/2026 | 07/03/2026 | <https://redis.io/docs/> |
| 3 | - Implement distributed Rate Limiting at the API Gateway:<br>&emsp; + Apply Redis Rate Limiter utilizing Token Bucket algorithms.<br>&emsp; + Implement JWT parsing filter to extract the unique User ID as the rate limit key resolver. | 07/04/2026 | 07/04/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 4 | - Implement Distributed Locking at the Payment Service:<br>&emsp; + Research Redlock algorithm and integrate Redis-based locks (Spring Integration Redis or Redisson).<br>&emsp; + Enforce distributed locking on account balance modification to prevent concurrent race conditions. | 07/05/2026 | 07/05/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 5 | - Build transaction idempotency controls:<br>&emsp; + Design Idempotency Filters on the API Gateway and Payment Service.<br>&emsp; + Store client-provided idempotency keys on Redis with a strict Time-to-Live (TTL: 10 mins). | 07/06/2026 | 07/07/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| 6 | - Deploy and validate application workloads on AWS:<br>&emsp; + Push Nginx and Spring Boot Docker images to ECR, and launch Fargate services.<br>&emsp; + Instantiate private RDS PostgreSQL and seed schema via EC2 Bastion jump box.<br>&emsp; + Design KMS-encrypted snapshot exports to Amazon S3 buckets. | 07/08/2026 | 07/08/2026 | <https://calculator.aws/> |
| 7 | - Write documentation and proposal reports:<br>&emsp; + Author 10-step workshop instructions on AWS Console using standard English technical terms.<br>&emsp; + Rewrite Project Proposal with Mermaid 3-tier architecture and budget spreadsheets. | 07/09/2026 | 07/10/2026 | [Proposal Page](file:///D:/aws/fcj-workshop-template/content/2-Proposal/_index.md) |

### Week 12 Achievements:

* **Integrated Redis Caching:**
  * Reduced direct reads to RDS PostgreSQL for static and slow-moving metadata (payment options, product tables) by caching records on Redis.
  * Achieved API response latency below 50ms for core endpoints.

* **Deployed JWT-based Redis Rate Limiter on API Gateway:**
  * Developed a custom Key Resolver that decodes the `Authorization` JWT header to extract the unique `userId`.
  * Used Redis to track token replenishment and request rates globally, intercepting overload bursts (HTTP 429) reliably across multiple load-balanced gateway tasks.

* **Prevented Balance Inconsistency using Distributed Locks:**
  * Configured Redis-backed distributed locks on Payment Service using lock keys structured as `payment_lock:{accountId}`.
  * Completely eliminated balance write race conditions when multiple payment actions target the same account concurrently.

* **Implemented Transaction Idempotency Checks:**
  * Added Idempotency filters that validate unique Client Transaction Tokens, storing keys on Redis with state tracking (`PROCESSING`/`COMPLETED`) and TTL (10 minutes).
  * Blocked duplicate transaction attempts, protecting the core financial workflow.

* **Successfully Deployed Application on AWS Infrastructure:**
  * Published Docker images for Frontend Nginx and Backend Spring Boot + Redis sidecar to ECR, launching them as serverless tasks inside isolated Private Subnets on ECS Fargate.
  
  ![Successfully deployed tasks on ECS Fargate](/images/h47.png)

  * Provisioned private RDS PostgreSQL database and seeded schema scripts through a temporary EC2 Bastion host using EC2 Instance Connect.
  * Verified application connectivity through the Application Load Balancer DNS to test the user interface.
  
  ![NextGenPay UI running on ALB DNS](/images/h69.png)

  * Implemented backup routines: ran manual RDS snapshots, assigned IAM policies/roles, and executed secure snapshot exports to S3 encrypted with a custom KMS key.

* **Finalized Project Proposal and Workshop Documents:**
  * Wrote 10 comprehensive workshop pages using standardized English terminology matching the AWS Console.
  * Formulated the project proposal featuring Mermaid architecture layout and operational budget estimates (~$100/month).
  * Executed PowerShell load test scripts and verified metric peaks in CloudWatch:

  ![RequestCount metric peak in CloudWatch](/images/h70.png)
