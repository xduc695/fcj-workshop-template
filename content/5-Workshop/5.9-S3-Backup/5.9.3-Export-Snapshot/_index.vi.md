---
title : "Chụp Snapshot & Export sang Amazon S3"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.9.3. </b> "
---

Chúng ta tiến hành chụp **RDS Snapshot** của `pg-db` và thực hiện export dữ liệu đó sang S3.

---

### Các bước thực hiện:

1. **Chụp RDS Snapshot thủ công:**
   - Vào **RDS Console** -> Databases -> Chọn `pg-db`.
   - Click chọn **Actions** -> Chọn **Take snapshot** -> Đặt tên: `pg-db-snapshot-manual` -> Chọn **Take snapshot**.
![pg-db-snapshot-manual](/images/h65.png)
   - Chờ trạng thái snapshot chuyển sang **Available** (màu xanh).
2. **Thực hiện Export Snapshot sang S3:**
   - Vào RDS -> chọn mục **Snapshots** ở menu trái -> chọn tab **Manual** -> tích chọn bản snapshot `pg-db-snapshot-manual`.
   - Click chọn **Actions** -> Chọn **Export to Amazon S3**.
3. **Cấu hình thông số:**
   - **Export identifier**: Nhập `pg-db-export-to-s3`.
   - **S3 bucket**: Chọn đúng bucket của bạn: `pg-db-backups-<account-id>-ap-southeast-1-an`.
![Export to Amazon S3](/images/h66.png)
   - **IAM role**: Tích chọn **Choose an existing role** -> chọn đúng vai trò **`rds-s3-export-role`** đã tạo ở bước trước.
   - **Encryption (KMS key)**: Chọn đúng khóa **`pg-s3-export-key`** đã tạo ở bước trước.
4. Nhấn **Export to Amazon S3** để hoàn tất.
![Export to Amazon S3](/images/h67.png)
*Tiến trình Export sẽ chạy nền dưới dạng Parquet nén lưu trữ an toàn trong S3 Bucket.*
![Export to Amazon S3 success](/images/h68.png)
