---
title: "Translated Blogs"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

###  [Blog 1 - Automating Container Application Deployment to Amazon ECS Express Mode using GitHub Actions](3.1-Blog1/)
This article guides you on how to build a fully automated and secure CI/CD pipeline from GitHub source code to a live environment on AWS. You will learn about core advantages such as passwordless authentication via OIDC, infrastructure automation (ALB, Auto Scaling) thanks to ECS Express Mode, and precise version management using Commit SHA to optimize the DevOps process. Additionally, the article shares practical considerations regarding tightening IAM Policy permissions and how to monitor workflow logs in real-time to detect conflict errors early.

###  [Blog 2 - Optimizing Disaster Recovery for Stateful Services on Amazon EKS using Velero](3.2-Blog2/)
This blog shares a comprehensive disaster recovery backup and restore solution for stateful applications running on an Amazon EKS cluster using the open-source tool Velero. The article delves into the parallel processing architecture (backing up logic configurations to Amazon S3 and taking physical disk EBS Snapshots), the secure authentication mechanism with EKS Pod Identity, and the flexible cross-namespace recovery feature. Besides, the author also summarizes experiences in handling syntax errors in the Windows CMD environment and fixing the situation where Pods are stuck in the Pending state during scheduling.

###  [Blog 3 - Breaking the 90-day Limit of EC2 Capacity Manager with Amazon Athena](3.3-Blog3/)
This article focuses on the problem of optimizing large-scale infrastructure costs (FinOps) on AWS by overcoming the 90-day historical data storage limit of EC2 Capacity Manager. You will understand the process of automatically packing data into Parquet format for long-term storage on Amazon S3 and optimizing queries using the Partition Projection mechanism on Amazon Athena without manual scanning. In particular, the article provides 3 practical SQL scenarios to help enterprises easily hunt down wasted ODCR resource packages, identify peak load patterns, and proactively share internal unused capacity.
