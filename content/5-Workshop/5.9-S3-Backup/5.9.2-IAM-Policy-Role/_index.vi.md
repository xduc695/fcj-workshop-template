---
title : "Tạo IAM Policy & Role cho RDS"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.9.2. </b> "
---

Chúng ta sẽ tạo các quyền bảo mật cho phép RDS **assume role** để thực hiện export data backup lên S3.

---

### Bước 1: Tạo IAM Policy tùy chỉnh (`rds-s3-export-policy`)
1. Mở dịch vụ **IAM** -> nhấp chọn **Policies** ở menu trái -> click **Create policy**.
2. Chọn tab **JSON**, xóa code mẫu và dán đoạn JSON dưới đây vào (thay thế tên bucket bằng tên S3 Bucket chính xác bạn đã tạo):
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
3. Nhấn **Next** -> đặt tên Policy là **`rds-s3-export-policy`** -> nhấn **Create policy**.

---

### Bước 2: Tạo IAM Role với Custom Trust Policy (`rds-s3-export-role`)
Chúng ta cần cấu hình một **IAM Role** cho phép dịch vụ xuất của RDS (`export.rds.amazonaws.com`) thực hiện assume role:
1. Tại dịch vụ **IAM**, chọn **Roles** ở menu trái -> click **Create role**.
2. Chọn ô tròn **Custom trust policy** (nằm ở dưới cùng).
3. Thay thế đoạn code JSON bằng đoạn mã sau để cho phép RDS assume role:
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
4. Nhấn **Next** -> Tại bảng gán permissions, tìm và tích chọn chính sách **`rds-s3-export-policy`** bạn vừa tạo ở Bước 1. Nhấn **Next**.
5. Đặt tên Role là: **`rds-s3-export-role`** -> Nhấp **Create role** ở dưới cùng.

![Tạo IAM Role thành công](/images/h64.png)
