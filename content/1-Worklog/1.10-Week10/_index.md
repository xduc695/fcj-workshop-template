---
title: "Week 10 Worklog"
date: 2026-06-22
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Understand the process and practice deploying a disaster recovery backup system on Amazon EKS using Velero.
* Understand the process and practice deploying a long-term EC2 capacity data storage system for FinOps analysis using Amazon S3 and Amazon Athena.
* Research API Gateway mechanisms, Rate Limiting solutions, and the K8s orchestration platform.
* Practice configuring Resilience4j (Retry & Circuit Breaker) and API Gateway (LocalRateLimiter) to protect Microservices communication.
* Deploy Caching and advanced access control solutions using Redis to optimize performance.
* Set up a distributed Rate Limiting mechanism based on Redis at the API Gateway, applying user-specific policies via JWT identification.
* Solve Resource Contention (Concurrency Control) and Idempotency issues by using a Distributed Lock mechanism with Redis.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Practice configuring disaster recovery backup system on Amazon EKS using Velero: <br> - **Practice:** <br>&emsp; + Initialize Amazon S3 Bucket to store cluster configuration <br>&emsp; + Create IAM Policy, IAM Role and configure EKS Pod Identity Association <br>&emsp; + Install Snapshot Controller add-on and set up VolumeSnapshotClass <br>&emsp; + Deploy Velero Server using Helm Chart combined with ClusterRole <br>&emsp; + Deploy sample app (Stateful App) with gp3 volume in myprimary namespace <br>&emsp; + Execute Velero Backup to backup all resources <br>&emsp; + Apply Velero Restore with namespaceMapping to restore to myrestore <br>&emsp; + Verify data flow, fix CMD errors, Pod Pending errors, and clean up resources. | 06/22/2026 | 06/22/2026 | <https://aws.amazon.com/vi/blogs/containers/back-up-and-restore-your-amazon-eks-cluster-resources-using-velero/> |
| Tuesday | - Practice configuring long-term data storage system on Amazon EC2 using Capacity Manager and Amazon Athena (FinOps): <br> - **Practice:** <br>&emsp; + Initialize Amazon S3 Bucket for centralized data <br>&emsp; + Create S3 Bucket Policy granting write access to EC2 Capacity Manager <br>&emsp; + Set up hourly Data Export workflow in Parquet format <br>&emsp; + Initialize Database and configure External Table on Athena (Partition Projection) <br>&emsp; + Execute SQL to hunt for underperforming ODCRs <br>&emsp; + Query to analyze Peak Usage Patterns <br>&emsp; + Query AZ ID level to identify available capacity <br>&emsp; + Verify data flow and clean up resources. | 06/23/2026 | 06/23/2026 | <https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/> |
| Wednesday | - Configure fault tolerance solution chain with Resilience4j, API Gateway, and K8s: <br> - **Practice:** <br>&emsp; + Integrate Resilience4j dependency into Payment Service. <br>&emsp; + Configure Retry (max-attempts: 3) and Exponential Backoff. <br>&emsp; + Integrate @Retry and @CircuitBreaker into AccountServiceClient. <br>&emsp; + Setup paymentFallbackMethod when Account Service fails. <br>&emsp; + Initialize API Gateway service using Spring Cloud Gateway WebFlux. <br>&emsp; + Design LocalRateLimiterGatewayFilterFactory (Token Bucket In-memory). <br>&emsp; + Remove and clean up old Rate Limit configuration in Account Service. <br>&emsp; + Run PowerShell test scripts to validate Rate Limiting and Circuit Breaker. | 06/24/2026 | 06/24/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Thursday | - Practice Caching mechanisms and Rate Limiting with Redis:<br> - **Practice:** <br>&emsp; + Research Distributed Caching and strategies (Cache-Aside, Write-Through).<br>&emsp; + Configure Spring Boot Redis Starter to connect with Redis.<br>&emsp; + Apply Redis Rate Limiter using a Token Bucket structure at the API Gateway.<br>&emsp; + Analyze JWT to extract the User ID as a rate-limiting key for each Client. | 06/25/2026 | 06/25/2026 | <https://redis.io/docs/><br><https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Friday | - Practice Distributed Lock and Idempotency mechanisms:<br> - **Practice:** <br>&emsp; + Deploy Distributed Locks using Redisson at the Payment Service.<br>&emsp; + Integrate distributed locks into the payment flow to prevent balance contention.<br>&emsp; + Design an Idempotency Filter at the API Gateway and verify tokens at the Payment Service.<br>&emsp; + Use Redis to store the processing status of Idempotency Keys with TTL to avoid double charging. | 06/26/2026 | 06/26/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |

### Week 10 Achievements:

**1. Velero EKS Backup and Disaster Recovery (Monday)**
* Successfully configured Velero to package logical resources into compressed files on an S3 Bucket. Activated the Snapshot Controller to capture physical `gp3` Amazon EBS Snapshots.
* Verified the completed backup status through the Phase of the Backup Custom Resource.
![Velero Backup Completed](/images/100.png)
* Used `namespaceMapping` to shift all resources to a new namespace. AWS automatically initialized a new `gp3` volume attached to the Worker Node.
* Established EKS Pod Identity Association eliminating static credentials, applying Least Privilege ClusterRoles.
![EKS Pod Identity Association](/images/101.png)

**2. EC2 Capacity Manager & Athena FinOps (Tuesday)**
* Automated Capacity Manager to export infrastructure data (On-Demand, Spot, ODCR) hourly as Parquet (Snappy) to an S3 Bucket. Configured S3 Bucket Policy successfully.
* Verified the `LatestDeliveryStatus` field returned `delivered`.
![Capacity Manager Data Export Delivered](/images/102.png)
* Applied Partition Projection for the External Table, enabling Athena to automatically identify new partitions.
* Executed advanced SQL to hunt wasted ODCRs, extract Peak Usage, and locate available AZ ID capacity.
![Athena SQL Query Results](/images/103.png)

**3. API Gateway, Rate Limiting In-memory & Resilience4j (Wednesday)**
* Successfully integrated CircuitBreaker and Retry filters on the Payment Service's Feign Client. Configured `failureRateThreshold` and `slidingWindowSize` optimally to prevent false tripping.
* Deployed an API Gateway as a central transit point protecting the Microservices architecture. Integrated the Token Bucket In-Memory filter against DDoS efficiently.
* Cleaned up the old Rate Limit in Account Service ensuring Clean Code (SRP). PowerShell tests executed precise circuit breaking.

**4. Integrate Distributed Caching and JWT Rate Limiting (Thursday)**
* Offloaded direct queries to RDS PostgreSQL for static data (payment gateway configurations) using Redis Cache. Optimized core API latency to under 50ms.
* Built a custom Key Resolver to decrypt the `Authorization` header containing the JWT Token to extract a unique `userId`.
* Used Redis to store remaining tokens, accurately blocking requests exceeding the threshold (429 Error code) across parallel instances.

**5. Distributed Lock and Idempotency (Friday)**
* Established a Distributed Lock using Redis on the Payment Service based on the `payment_lock:{accountId}` key structure.
* Ensured balance data consistency, completely eliminating Race Conditions when multiple concurrent payment commands are sent.
* Integrated the Idempotency Key filter sent from Clients. Stored the key on Redis with status (`PROCESSING`/`COMPLETED`) and a 10-minute TTL. Returned prior results for consecutive duplicate requests.
