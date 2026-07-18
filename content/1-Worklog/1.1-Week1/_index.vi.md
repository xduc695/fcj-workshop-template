---
title: "Worklog Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Mục tiêu tuần 1:

* Kết nối, làm quen với các thành viên trong First Cloud Journey và nắm vững nội quy.
* Tìm hiểu tổng quan về điện toán đám mây AWS và các dịch vụ cơ bản (Compute, Storage, Networking, Database).
* Khởi tạo tài khoản AWS Free Tier 2025 và hoàn thành các nhiệm vụ để nhận 200$ credit thực hành.
* Làm quen giao diện AWS Management Console, cài đặt và cấu hình giao diện dòng lệnh AWS CLI.
* Thực hành thiết lập AWS Budget để giám sát và quản lý chi phí tài khoản an toàn.
* Tìm hiểu hệ thống AWS Support và quy trình khởi tạo yêu cầu hỗ trợ (Support Case).
* Nghiên cứu và thực hành quản trị quyền truy cập cốt lõi bằng IAM (User, Group, Policies và Role).
* Tìm hiểu AWS Well-Architected Framework và thử nghiệm đánh giá rủi ro bảo mật hệ thống.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Làm quen với các thành viên FCJ. <br> - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập. | 20/04/2026 | 20/04/2026 | <https://rules.fcjuni.com/1-regulations/> |
| Thứ 3 | - Tìm hiểu AWS và các loại dịch vụ cơ bản:<br>&emsp; + Compute (EC2, Lambda) <br>&emsp; + Storage (S3, EBS) <br>&emsp; + Networking (VPC, Security Group) <br>&emsp; + Database (RDS, DynamoDB) | 21/04/2026 | 21/04/2026 | <https://cloudjourney.awsstudygroup.com/>|
| Thứ 4 | - Khởi tạo tài khoản AWS Free Tier 2025, hoàn thành 5 nhiệm vụ để nhận đủ credit.<br> - Nắm bắt lộ trình học tập, nhận diện dịch vụ dễ phát sinh chi phí.<br> - **Thực hành:** <br>&emsp; + Cài đặt, cấu hình và sử dụng AWS CLI để tương tác với tài khoản. | 22/04/2026 | 22/04/2026 | <https://000001.awsstudygroup.com/> |
| Thứ 5 | - Nghiên cứu AWS Budget để cấu hình quản lý chi phí:<br> - **Thực hành:** <br>&emsp; + Cấu hình nhanh với Budget template (Cost, Usage, RI, Savings Plans Budget).<br> - Tìm hiểu hệ thống AWS Support và quy trình khởi tạo yêu cầu hỗ trợ (Support Case), cách chọn Severity level. | 23/04/2026 | 23/04/2026 | <https://000007.awsstudygroup.com/><br><https://000009.awsstudygroup.com/> |
| Thứ 6 | - Tìm hiểu về định danh bảo mật IAM User, Group, Policies và Role.<br> - **Thực hành:** <br>&emsp; + Khởi tạo Admin Group, Admin User và thiết lập Admin Role.<br>&emsp; + Thực hiện cấu hình Switch Role cho OperatorUser.<br> - Tìm hiểu về AWS Well-Architected Framework.<br> - **Thực hành:**<br>&emsp; + Triển khai đánh giá rủi ro bảo mật với công cụ AWS Well-Architected Tool. | 24/04/2026 | 24/04/2026 | <https://000002.awsstudygroup.com/><br> <https://aws.amazon.com/architecture/well-architected/>|

### Kết quả đạt được tuần 1:

**1. Khởi động và Hệ thống hóa Dịch vụ (Thứ 2 & Thứ 3)**
* Kết nối thành công và thiết lập kênh liên lạc với các chuyên gia trong dự án First Cloud AI Journey, cam kết tuân thủ văn hóa làm việc.
* Hiểu rõ hệ sinh thái AWS với 4 trụ cột lõi: Compute (EC2, Lambda), Storage (S3, EBS), Networking (VPC) và Database (RDS, DynamoDB). Nắm bắt lộ trình phát triển kỹ năng 6 tháng.

**2. Khởi tạo Tài khoản & Làm chủ AWS CLI (Thứ 4)**
* Khởi tạo thành công tài khoản AWS Free Tier 2025 (Gói Paid Plan) và hoàn tất 5 nhiệm vụ để nhận trọn vẹn $200 Credit thực hành.
* Nhận diện thành công các dịch vụ "nguy hiểm" dễ gây phát sinh chi phí (SageMaker, GPU Instances).
![AWS Free Tier Account](/images/1.png)
* Hoàn thành cài đặt AWS CLI, cấu hình định danh bảo mật thông qua `aws configure` (Access Key, Secret Key, Default Region).
* Sử dụng thành thạo dòng lệnh để tra cứu tài khoản (`aws sts get-caller-identity`), kiểm tra region, liệt kê thực thể EC2 và quản lý Key Pair.
![Kiểm tra AWS CLI](/images/2.png)

**3. Quản lý Chi phí (Budgets) & Hỗ trợ (Thứ 5)**
* Nắm vững và triển khai thành công 4 loại ngân sách (Cost, Usage, RI, Savings Plans) thông qua Budget Templates.
* Thiết lập ngưỡng cảnh báo (Thresholds) thông minh nhằm chủ động ngăn chặn rủi ro tài chính phát sinh.
![Cấu hình AWS Budgets](/images/3.png)
* Thấu hiểu các gói Support Plans, cách phân loại mức độ nghiêm trọng (Severity level) và quy trình tương tác tạo Support Case.

**4. Quản trị Phân quyền IAM & Đánh giá Kiến trúc (Thứ 6)**
* Thiết lập cấu trúc bảo mật tập trung: Tạo AdminGroup, gán Policies và thêm AdminUser thay vì phân quyền lẻ tẻ.
![Khởi tạo IAM Group](/images/4.png)
![Thiết lập IAM Policies](/images/5.png)
* Cấu hình Trust Relationship cho AdminRole. Thực hiện thao tác Switch Role thành công cho OperatorUser, áp dụng triệt để nguyên tắc đặc quyền tối thiểu (Least Privilege).
![Switch Role thành công](/images/6.png)
* Triển khai đánh giá rủi ro hệ thống bằng AWS Well-Architected Tool. Dựa trên trụ cột Bảo mật (Security), công cụ đã phát hiện 4 rủi ro cao (High risk) và 1 rủi ro trung bình (Medium risk), tạo tiền đề vững chắc cho việc tối ưu hạ tầng sau này.
![Đánh giá Well-Architected Tool](/images/10.png)
