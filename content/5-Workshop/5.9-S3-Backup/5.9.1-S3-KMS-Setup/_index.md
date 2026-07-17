---
title : "Create S3 Bucket & KMS Key"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.9.1. </b> "
---

We will create an S3 Bucket to store backup files and a KMS Key to encrypt the data.

---

### Step 1: Create an S3 Bucket
1. Access the **S3** service on the AWS Console -> click **Create bucket**.
2. Configure the information:
   - **Bucket name**: Enter a globally unique name (Example: **`pg-db-backups-<account-id>-ap-southeast-1-an`**).
   - **AWS Region**: Select **ap-southeast-1** (Singapore).
   - Leave other options as default. Click **Create bucket**.

---
![Tạo S3 Bucket](/images/h61.png)
### Step 2: Create a KMS Key (Customer Managed Key)
AWS does not allow using default keys (such as `aws/s3` or `aws/rds`) to export Snapshots to S3 because the Key Policy cannot be edited. We need to create a **Symmetric Customer Managed Key**:
1. Search and open the **Key Management Service (KMS)** service on the AWS Console.
2. In the left menu, select **Customer managed keys** -> click **Create key**.
3. Configuration:
   - **Key type**: Select **Symmetric**. Click **Next**.
   - **Alias**: Enter `pg-s3-export-key`. Click **Next**.
   - **Key administrators**: Check your current IAM user account. Click **Next**.
   - **Key users**: Check your user account. Click **Next** -> Click **Finish** to create the key.

![Tạo khóa KMS](/images/h62.png)
