---
title: "Worklog Tuần 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Thực hành quản trị và bảo mật tài nguyên AWS với IAM, trọng tâm vào việc áp dụng nguyên tắc đặc quyền tối thiểu, cấu hình IAM Role và thiết lập các Condition giới hạn truy cập để tăng cường an toàn hệ thống.
* Thực hành triển khai tính năng IAM Permission Boundary để thiết lập giới hạn đặc quyền tối đa cho người dùng, giúp quản lý phân quyền hiệu quả và ngăn chặn rủi ro privilege escalation trong hệ thống AWS.
* Thực hành kiểm soát truy cập và phân quyền tài nguyên EC2 dựa trên Resource Tag bằng AWS IAM, áp dụng nguyên tắc đặc quyền tối thiểu thông qua việc thiết lập các Policy với điều kiện ràng buộc cụ thể nhằm phục vụ công tác quản trị hệ thống phi tập trung.
* Thực hành triển khai AWS Security Hub và AWS Config để thiết lập trung tâm giám sát an ninh toàn diện, giúp đánh giá trạng thái tuân thủ của hệ thống dựa trên các tiêu chuẩn bảo mật cốt lõi (CIS, PCI DSS, AWS Foundational) và thực hiện quản lý, tùy chỉnh các cảnh báo rủi ro.
* Thực hành triển khai giải pháp mã hóa dữ liệu ở trạng thái lưu trữ trên Amazon S3 bằng AWS KMS, đồng thời thiết lập cơ chế giám sát an ninh toàn diện bằng cách tích hợp AWS CloudTrail để ghi nhật ký sự kiện và Amazon Athena để truy vấn dữ liệu kiểm toán.
* Tìm hiểu về dịch vụ cơ sở dữ liệu trên AWS.
* Thực hành ôn lại cú pháp SQL cơ bản trên W3Schools để phục vụ cho việc quản trị cơ sở dữ liệu.
* Thực hành triển khai và quản trị cơ sở dữ liệu quan hệ trên đám mây với Amazon RDS, kết nối từ EC2 và thực hiện các thao tác vận hành cốt lõi như Backup và Restore dữ liệu.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Thực hành quản trị và bảo mật tài nguyên AWS với IAM, cấu hình IAM Role và thiết lập Condition giới hạn truy cập <br> - **Thực hành:** <br>&emsp; + Tạo IAM Group quyền truy cập admin (EC2, RDS) <br>&emsp; + Tạo và kiểm tra IAM User <br>&emsp; + Tạo Admin IAM Role và Switch role <br>&emsp; + Cấu hình Role Condition theo IP và thời gian | 18/05/2026 | 18/05/2026 | <https://000044.awsstudygroup.com/> |
| Thứ 3 | - Thực hành triển khai tính năng IAM Permission Boundary <br> - **Thực hành:** <br>&emsp; + Tạo IAM policy giới hạn quyền tối đa <br>&emsp; + Giới hạn và kiểm tra quyền IAM User <br> - Thực hành kiểm soát truy cập EC2 dựa trên Resource Tag <br> - **Thực hành:** <br>&emsp; + Tạo IAM Policy kiểm soát EC2 bằng Resource Tag <br>&emsp; + Tạo IAM Role gắn policy <br>&emsp; + Tiến hành switch role kiểm tra quyền | 19/05/2026 | 19/05/2026 | <https://000030.awsstudygroup.com/><br><https://000028.awsstudygroup.com/> |
| Thứ 4 | - Thực hành triển khai AWS Security Hub và AWS Config <br> - **Thực hành:** <br>&emsp; + Kích hoạt cấu hình Security Hub và AWS Config <br>&emsp; + Kiểm tra rủi ro (CIS, PCI DSS, AWS Foundational) <br> - Thực hành giải pháp mã hóa dữ liệu S3 bằng KMS, CloudTrail và Athena<br> - **Thực hành:** <br>&emsp; + Tạo KMS Key <br>&emsp; + Tạo Bucket upload dữ liệu <br>&emsp; + Cấu hình CloudTrail <br>&emsp; + Dùng Athena truy vấn nhật ký <br>&emsp; + Kiểm thử bảo mật | 20/05/2026 | 20/05/2026 | <https://000018.awsstudygroup.com/><br><https://000033.awsstudygroup.com/> |
| Thứ 5 | - Tìm hiểu dịch vụ cơ sở dữ liệu trên AWS: <br>&emsp; + Database Concepts <br>&emsp; + Amazon RDS & Aurora <br>&emsp; + Amazon Redshift <br>&emsp; + Amazon ElastiCache | 21/05/2026 | 21/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thứ 6 | - Thực hành ôn lại SQL cơ bản trên W3Schools <br> - Thực hành triển khai quản trị RDBMS với Amazon RDS, Backup và Restore <br> - **Thực hành:** <br>&emsp; + Tạo hạ tầng VPC, SG cho EC2, RDS <br>&emsp; + Khởi tạo EC2 và RDS instance <br>&emsp; + Triển khai ứng dụng kết nối Node.js <br>&emsp; + Backup và Restore trên RDS | 22/05/2026 | 22/05/2026 | <https://www.w3schools.com/sql/default.asp><br><https://000005.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

**1. Bảo mật Truy cập Nâng cao (Thứ 2)**
* Thành thạo cấu hình và kiểm soát truy cập với IAM Role: Triển khai thành công cơ chế Switch Role, đảm bảo cấp quyền quản trị tạm thời theo nguyên tắc đặc quyền tối thiểu.
* Cấu hình và kiểm chứng hiệu quả các ràng buộc (Condition); hệ thống tự động chặn truy cập (Access Denied) khi sai địa chỉ IP hoặc ngoài khung giờ cho phép.
![IAM Condition](/images/68.png)

**2. Quản trị Đặc quyền & Resource Tags (Thứ 3)**
* Triển khai thành công IAM Permission Boundary: Thiết lập chính sách giới hạn quyền tối đa (Maximum Permissions), ghi đè và kiểm soát chặt chẽ các policy Full Access của User. Hệ thống cấp quyền EC2 hợp lệ tại Singapore và tự động vô hiệu hóa mọi thao tác tại Tokyo.
![IAM Permission Boundary](/images/69.png)
* Thực hiện thành công phân quyền quản trị EC2 phi tập trung dựa trên Resource Tag: Xây dựng chuỗi IAM Policy buộc người dùng chỉ được quản lý tài nguyên khi gắn chính xác bộ thẻ định danh (ví dụ: Team=Alpha). Tự động chặn đứng các yêu cầu sai thẻ và từ chối quyền truy cập khi cố tình chỉnh sửa Resource Tag.
![IAM Resource Tags](/images/70.png)

**3. Giám sát An ninh Toàn diện & Mã hóa Dữ liệu (Thứ 4)**
* Thiết lập trung tâm giám sát an ninh (Security Hub): Tích hợp hoàn thiện AWS Security Hub với AWS Config để tự động quét, phát hiện lỗ hổng và đánh giá theo 3 bộ tiêu chuẩn quốc tế (AWS Foundational, CIS, PCI DSS).
* Quản lý và tùy chỉnh cảnh báo rủi ro qua giao diện Dashboard để phân tích mức độ nghiêm trọng.
![Security Hub](/images/71.png)
* Triển khai giải pháp mã hóa dữ liệu lưu trữ (Encryption at Rest): Thiết lập cơ chế mã hóa tự động cho Amazon S3 (SSE-KMS) bằng Customer Managed Key từ AWS KMS. Hệ thống chặn đứng mọi nỗ lực truy cập từ người dùng nội bộ không có quyền giải mã KMS và từ chối các truy cập Public trực tiếp. Thực hiện chia sẻ dữ liệu mã hóa an toàn qua Presigned URL.
![Access Denied](/images/73.png)
* Thiết lập luồng giám sát an ninh dữ liệu: Cấu hình AWS CloudTrail tự động ghi nhận Data Events trên S3. Tích hợp Amazon Athena thực thi truy vấn SQL tra cứu chi tiết lịch sử sự kiện từ kho dữ liệu log.
![Amazon Athena](/images/72.png)

**4. Khái niệm Cơ sở Dữ liệu Đám mây (Thứ 5)**
* Hệ thống hóa toàn diện kiến thức nền tảng về Database (Relational, Non-relational, In-memory, Data Warehouse). Hiểu rõ cơ chế kiến trúc Cloud-native của Amazon Aurora.
* Nắm bắt khái niệm Amazon Redshift (OLAP, xử lý Petabyte) và Amazon ElastiCache (Redis/Memcached giảm tải cho Database chính).

**5. Vận hành RDBMS & Amazon RDS (Thứ 6)**
* Ôn tập và củng cố vững chắc nền tảng SQL (DML, DDL, JOIN, GROUP BY) thông qua W3Schools.
![SQL](/images/74.png)
* Triển khai cơ sở dữ liệu Amazon RDS: Khởi tạo RDS database instance và thiết lập liên kết thông suốt từ ứng dụng Node.js thông qua file môi trường cấu hình. Thực thi SQL import thành công bộ dữ liệu mẫu.
![RDS](/images/75.png)
* Vận hành quy trình Backup và Restore dữ liệu: Khởi tạo DB Snapshot thủ công. Thực hiện Restore thành công một DB instance mới từ bản Snapshot, cập nhật Endpoint mới vào Connection String để ứng dụng hoạt động không gián đoạn.
![Restore](/images/76.png)