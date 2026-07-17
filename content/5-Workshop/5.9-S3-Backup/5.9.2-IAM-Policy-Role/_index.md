---
title : "Create IAM Policy & Role for RDS"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.9.2. </b> "
---

We will create security permissions that allow RDS to **assume role** to export data backups to S3.

---

### Step 1: Create a Custom IAM Policy (`rds-s3-export-policy`)
1. Open the **IAM** service -> click **Policies** in the left menu -> click **Create policy**.
2. Select the **JSON** tab, delete the sample code, and paste the JSON snippet below (replace the bucket name with the exact S3 Bucket name you created):
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ExportPolicy",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject*",
                "s3:ListBucket",
                "s3:GetObject*",
                "s3:DeleteObject*",
                "s3:GetBucketLocation"
            ],
            "Resource": [
                "arn:aws:s3:::pg-db-backups-<account-id>-ap-southeast-1-an",
                "arn:aws:s3:::pg-db-backups-<account-id>-ap-southeast-1-an/*"
            ]
        }
    ]
}
```
![police](/images/h63.png)
3. Click **Next** -> name the Policy **`rds-s3-export-policy`** -> click **Create policy**.

---

### Step 2: Create an IAM Role with Custom Trust Policy (`rds-s3-export-role`)
We need to configure an **IAM Role** to allow the RDS export service (`export.rds.amazonaws.com`) to perform assume role:
1. In the **IAM** service, select **Roles** in the left menu -> click **Create role**.
2. Select the **Custom trust policy** radio button (located at the bottom).
3. Replace the JSON code with the following snippet to allow RDS to assume role:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "export.rds.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
4. Click **Next** -> In the permissions assignment table, find and check the **`rds-s3-export-policy`** policy you created in Step 1. Click **Next**.
5. Name the Role: **`rds-s3-export-role`** -> Click **Create role** at the bottom.

![Tạo IAM Role thành công](/images/h64.png)
