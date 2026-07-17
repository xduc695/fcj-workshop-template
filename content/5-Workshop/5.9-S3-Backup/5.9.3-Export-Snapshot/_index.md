---
title : "Take Snapshot & Export to Amazon S3"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.9.3. </b> "
---

We proceed to take an **RDS Snapshot** of `pg-db` and export that data to S3.

---

### Implementation steps:

1. **Take a manual RDS Snapshot:**
   - Go to the **RDS Console** -> Databases -> Select `pg-db`.
   - Click **Actions** -> Select **Take snapshot** -> Name it: `pg-db-snapshot-manual` -> Click **Take snapshot**.
![pg-db-snapshot-manual](/images/h65.png)
   - Wait for the snapshot status to change to **Available** (green).
2. **Export the Snapshot to S3:**
   - Go to RDS -> select **Snapshots** in the left menu -> select the **Manual** tab -> check the `pg-db-snapshot-manual` snapshot.
   - Click **Actions** -> Select **Export to Amazon S3**.
3. **Configure parameters:**
   - **Export identifier**: Enter `pg-db-export-to-s3`.
   - **S3 bucket**: Select your correct bucket: `pg-db-backups-<account-id>-ap-southeast-1-an`.
![Export to Amazon S3](/images/h66.png)
   - **IAM role**: Check **Choose an existing role** -> select the correct role **`rds-s3-export-role`** created in the previous step.
   - **Encryption (KMS key)**: Select the correct key **`pg-s3-export-key`** created in the previous step.
4. Click **Export to Amazon S3** to complete.
![Export to Amazon S3](/images/h67.png)
*The Export process will run in the background as compressed Parquet, stored securely in the S3 Bucket.*
![Export to Amazon S3 success](/images/h68.png)
