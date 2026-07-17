---
title : "Tạo S3 Bucket & KMS Key"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.9.1. </b> "
---

Chúng ta sẽ tạo S3 Bucket làm nơi lưu trữ các backup files và KMS Key để mã hóa dữ liệu.

---

### Bước 1: Tạo S3 Bucket
1. Truy cập dịch vụ **S3** trên AWS Console -> nhấp chọn **Create bucket**.
2. Thiết lập thông tin:
   - **Bucket name**: Nhập tên duy nhất toàn cầu (Ví dụ: **`pg-db-backups-<account-id>-ap-southeast-1-an`**).
   - **AWS Region**: Chọn **ap-southeast-1** (Singapore).
   - Các tùy chọn khác giữ nguyên mặc định. Nhấn **Create bucket**.

---
![Tạo S3 Bucket](/images/h61.png)
### Bước 2: Tạo Khóa KMS (Customer Managed Key)
AWS không cho phép sử dụng các khóa mặc định (như `aws/s3` hay `aws/rds`) để xuất Snapshot sang S3 vì không thể chỉnh sửa Key Policy. Chúng ta cần tạo một **Symmetric Customer Managed Key**:
1. Tìm kiếm và mở dịch vụ **Key Management Service (KMS)** trên AWS Console.
2. Menu trái, chọn **Customer managed keys** -> nhấp **Create key**.
3. Thiết lập:
   - **Key type**: Chọn **Symmetric**. Nhấn **Next**.
   - **Alias**: Nhập `pg-s3-export-key`. Nhấn **Next**.
   - **Key administrators**: Tích chọn tài khoản người dùng IAM hiện tại của bạn. Nhấn **Next**.
   - **Key users**: Tích chọn tài khoản người dùng của bạn. Nhấn **Next** -> Nhấp **Finish** để tạo khóa.

![Tạo khóa KMS](/images/h62.png)
