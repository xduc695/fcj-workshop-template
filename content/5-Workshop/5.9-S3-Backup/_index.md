---
title : "Integrate S3 Backup & Recovery"
date : 2024-01-01 
weight : 9
chapter : false
pre : " <b> 5.9. </b> "
---

In this section, we will set up the **S3 Backup & Recovery** solution for the database: Take an **RDS Snapshot** and export that data to an **Amazon S3 Bucket**, which is encrypted and protected by a **KMS Key**.

#### Implementation steps:

1. [Create S3 Bucket & KMS Key](5.9.1-S3-KMS-Setup/)
2. [Create IAM Policy & Role for RDS](5.9.2-IAM-Policy-Role/)
3. [Take Snapshot & Export to S3](5.9.3-Export-Snapshot/)
