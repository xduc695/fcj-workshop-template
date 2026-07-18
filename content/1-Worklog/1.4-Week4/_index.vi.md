---
title: "Worklog Tuần 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Tìm hiểu về dịch vụ lưu trữ trên AWS.
* Thực hành triển khai website tĩnh trên S3, đồng thời nắm vững các kỹ năng quản trị, bảo mật và dự phòng dữ liệu qua việc phân quyền, quản lý phiên bản, sao chép liên vùng và tìm hiểu tăng tốc truy cập bằng CloudFront với cách khắc phục sự cố S3.
* Thực hành thiết lập kế hoạch sao lưu và khôi phục tự động cho các tài nguyên AWS bằng AWS Backup, kết hợp cấu hình thông báo qua AWS SNS để giám sát và đảm bảo an toàn dữ liệu.
* Thực hành triển khai AWS File Storage Gateway nhằm thiết lập hệ thống chia sẻ tệp (File Share), giúp kết nối và đồng bộ dữ liệu liền mạch giữa môi trường On-premise và lưu trữ đám mây Amazon S3.
* Thực hành triển khai hệ thống lưu trữ tệp dùng chung hiệu năng cao trên môi trường Windows với Amazon FSx, đồng thời làm chủ các kỹ năng quản trị nâng cao như chống trùng lặp dữ liệu, shadow copy, phân bổ hạn mức người dùng và mở rộng tài nguyên linh hoạt.
* Tìm hiểu về dịch vụ bảo mật trên AWS.
* Thực hành các thao tác quản trị truy cập cơ bản trên AWS (IAM) thông qua việc thiết lập User, phân nhóm Group, gán Policy và đồng thời áp dụng cơ chế bảo mật nâng cao bằng cách Switch Role theo nguyên tắc đặc quyền tối thiểu.
* Thực hành phương pháp bảo mật tối ưu để cấp quyền cho ứng dụng truy cập an toàn vào các dịch vụ AWS bằng IAM Role, thay thế hoàn toàn cho việc sử dụng Access Key tiềm ẩn rủi ro lộ lọt dữ liệu.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Tìm hiểu về dịch vụ lưu trữ trên AWS: <br>&emsp; + Amazon Simple Storage Service (S3) <br>&emsp; + Các tính năng S3 nâng cao<br>&emsp; + Snow Family <br>&emsp; + Storage Gateway <br>&emsp; + RTO/RPO <br>&emsp; + Disater Recovery<br>&emsp; + AWS Backup | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thứ 3 | - Thực hành triển khai website tĩnh trên S3, thực hiện các kỹ năng quản trị, bảo mật và dự phòng dữ liệu<br> - **Thực hành:** <br>&emsp; + Tạo bucket, tải source code website lên <br>&emsp; + Kích hoạt tính năng lưu trữ website tĩnh <br>&emsp; + Cấu hình Block Public Access, public object <br>&emsp; + Kiểm Tra hoạt động Website <br>&emsp; + Thực hiện Bucket Versioning <br>&emsp; + Sao chép S3 Object sang region khác (CRR)<br> - Tìm hiểu CloudFront. | 12/05/2026 | 12/05/2026 | <https://000057.awsstudygroup.com/> |
| Thứ 4 | - Thực hành thiết lập sao lưu tự động bằng AWS Backup và cấu hình SNS giám sát<br> - **Thực hành:** <br>&emsp; + Tạo Backup Plan, Cấu hình thông báo, Kiểm tra sao lưu<br> - Thực hành triển khai AWS File Storage Gateway<br> - **Thực hành:** <br>&emsp; + Tạo Bucket và EC2 cho Storage Gateway<br>&emsp; + Cấu hình Storage Gateway, File Shares<br>&emsp; + Mapping Driver cho Windows. | 13/05/2026 | 13/05/2026 | <https://000013.awsstudygroup.com/><br><https://000024.awsstudygroup.com/> |
| Thứ 5 | - Triển khai FSx trên môi trường Windows<br> - **Thực hành:** <br>&emsp; + Tạo Multi-AZ file system, Tạo file share cho Windows<br>&emsp; + Kiểm tra và giám sát hiệu năng<br>&emsp; + Kích hoạt chống dữ liệu trùng lặp, shadow copies<br>&emsp; + Quản lý Session người dùng, Kích hoạt hạn ngạch<br>&emsp; + Kích hoạt chia sẻ Truy cập liên tục<br>&emsp; + Mở rộng thông lượng và dung lượng<br> - Tìm hiểu AWS CLI triển khai FSx. | 14/05/2026 | 14/05/2026 | <https://000025.awsstudygroup.com/> |
| Thứ 6 | - Tìm hiểu về dịch vụ bảo mật trên AWS: IAM, Cognito, AWS Organization, KMS, Security Hub<br> - Thực hành quản trị truy cập IAM theo đặc quyền tối thiểu<br> - **Thực hành:** <br>&emsp; + Tạo IAM Group, IAM User, IAM Role<br>&emsp; + Chuyển đổi IAM Role (Switch Role)<br> - Thực hành phương pháp bảo mật tối ưu sử dụng IAM Role thay vì Access Key<br> - **Thực hành:** <br>&emsp; + Tạo EC2 Intance và S3 Bucket<br>&emsp; + Test truy cập S3 bằng access key<br>&emsp; + Tạo và Sử dụng IAM Role cho ứng dụng. | 15/05/2026 | 15/05/2026 | <https://cloudjourney.awsstudygroup.com/><br><https://000002.awsstudygroup.com/><br><https://000048.awsstudygroup.com>|

### Kết quả đạt được tuần 4:

**1. Cơ bản về Lưu trữ & Bảo vệ Dữ liệu (Thứ 2)**
* Làm chủ hệ sinh thái lưu trữ lõi trên AWS: Nắm vững kiến trúc, cách vận hành và các tính năng quản trị nâng cao của Amazon S3.
* Giải pháp di chuyển và lưu trữ lai: Nắm bắt giải pháp kết nối, đồng bộ dữ liệu giữa môi trường On-premise và Cloud qua Storage Gateway và AWS Snow Family.
* Chiến lược Bảo vệ dữ liệu & Phục hồi sau thảm họa (Disaster Recovery): Thấu hiểu các chỉ số kinh doanh cốt lõi RTO và RPO để đảm bảo tính liên tục cho hệ thống thông qua AWS Backup.

**2. Lưu trữ S3 & Dự phòng Dữ liệu (Thứ 3)**
* Thực hành Lưu trữ & Phân quyền cơ bản với S3: Triển khai thành công static website và thiết lập cơ chế kiểm soát truy cập thông qua Block Public Access và ACL. Thực hiện thao tác quản lý và di chuyển Object giữa các S3 Bucket.
![Static Website](/images/50.png)
* Thực hành Dự phòng & Bảo vệ dữ liệu S3: Áp dụng tính năng Versioning để kiểm soát thay đổi và phòng tránh rủi ro xóa/ghi đè dữ liệu.
![Bucket Versioning](/images/51.png)
* Cấu hình thành công cơ chế Cross-Region Replication (CRR), đảm bảo tính sẵn sàng cao và phục hồi dữ liệu sau thảm họa.
![S3 Replication](/images/52.png)
![S3 Replication](/images/53.png)
![S3 Replication](/images/54.png)
* Nghiên cứu & Tối ưu hóa hệ thống: Tìm hiểu cơ chế hoạt động của Amazon CloudFront trong việc tăng tốc độ phân phối nội dung và giảm độ trễ cho website.

**3. AWS Backup & File Storage Gateway (Thứ 4)**
* Thiết lập và tự động hóa sao lưu với AWS Backup: Khởi tạo thành công Backup Plan với quy tắc sao lưu định kỳ và Backup Vault an toàn. Cấu hình gán tài nguyên Resource Assignments tự động thông qua việc sử dụng Tags.
![Backup Plan](/images/55.png)
* Giám sát và cảnh báo an toàn dữ liệu với AWS SNS: Thiết lập thành công cơ chế tự động gửi email thông báo khi tiến trình Backup hoặc Restore hoàn tất nhằm phản ứng nhanh với sự cố.
![Email Notification](/images/56.png)
![Backup completed successfully](/images/57.png)
* Triển khai hạ tầng Hybrid Storage: Khởi tạo EC2 AMI Storage Gateway, thiết lập Security Groups và cấp phát EBS Volume làm bộ nhớ đệm Cache. Tích hợp thành công Storage Gateway với Amazon S3 Bucket.
![Hybrid Storage](/images/58.png)
* Thiết lập và vận hành File Share: Cấu hình giao thức SMB cho môi trường Windows, Mapping Driver thành công trên máy On-premise. Đồng bộ tự động lưu trữ an toàn trên Amazon S3.
![File Share](/images/59.png)
![S3](/images/60.png)

**4. Lưu trữ Tệp Tập trung Amazon FSx (Thứ 5)**
* Kiểm thử và Giám sát hiệu năng FSx for Windows File Server: Thực hiện ánh xạ File Share vào máy chủ Windows và kiểm thử Read/Write performance bằng công cụ DiskSpd. Giám sát qua CloudWatch Dashboard và thiết lập High Throughput Alarm.
![DiskSpd](/images/61.png)
* Tối ưu hóa và Dự phòng dữ liệu: Kích hoạt Data Deduplication để tiết kiệm dung lượng. Triển khai Shadow Copies hỗ trợ tính năng Restore previous versions.
![Shadow Copies](/images/62.png)
![High Throughput Alarm](/images/63.png)
* Quản trị truy cập và Phân bổ tài nguyên: Quản lý User Sessions và Open Files, thiết lập User Quotas kiểm soát hạn mức lưu trữ, cấu hình Continuously Available Share, nâng cấp Storage Capacity/Throughput Capacity không gián đoạn.

**5. Định danh & Bảo mật Chuyên sâu IAM (Thứ 6)**
* Mô hình bảo mật cốt lõi: Nắm vững Mô hình Trách nhiệm Chia sẻ (Shared Responsibility Model), hiểu rõ các dịch vụ IAM, Cognito, AWS Organizations, KMS và Security Hub.
* Quản trị định danh và phân quyền cơ bản: Khởi tạo IAM Group và IAM User an toàn, loại bỏ hoàn toàn việc sử dụng tài khoản Root. Thiết lập Inline Policy cấp quyền sts:AssumeRole một cách chặt chẽ.
* Bảo mật nâng cao và kiểm soát đặc quyền: Khởi tạo IAM Role cung cấp các phiên truy cập tạm thời. Thực hành kỹ thuật Switch Role tuân thủ tuyệt đối nguyên tắc Least Privilege (Đặc quyền tối thiểu).
![Least Privilege](/images/64.png)
![Switch Role](/images/65.png)
* Nhận diện rủi ro bảo mật (Access Key): Kiểm thử kết nối ứng dụng tới S3 qua Access Key và Secret Access Key, nhận thức rủi ro khi hardcode xác thực tĩnh vào mã nguồn.
![Application Access Key](/images/66.png)
* Triển khai bảo mật tối ưu (IAM Role): Cấp policy AmazonS3FullAccess cho IAM Role (Trusted Entity EC2). Áp dụng Role cho máy chủ, giúp ứng dụng tự động upload file an toàn tuyệt đối, loại bỏ nguy cơ lộ lọt dữ liệu.
![Application IAM Role](/images/67.png)