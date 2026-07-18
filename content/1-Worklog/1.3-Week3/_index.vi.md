---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu tuần 3:

* Tìm hiểu về dịch vụ Compute VM trên AWS.
* Thực hành cơ bản với Amazon EC2, thiết lập môi trường ứng dụng Node.js trên đa nền tảng (Windows/Linux) kết hợp quản trị vòng đời máy chủ EC2 và kiểm soát quyền hạn nghiêm ngặt qua IAM.
* Triển khai quản trị hạ tầng qua Tag và Resource Groups để quản lý tập trung, giúp tự động hóa vận hành và kiểm soát tài nguyên theo dự án hoặc môi trường.
* Thiết lập hệ thống giám sát và quản trị tập trung thông qua việc phân tích chuyên sâu các thông số vận hành (Metrics) và nhật ký hệ thống (Logs), nhằm cấu hình các cơ chế phản hồi tự động giúp tối ưu hóa hiệu suất và kiểm soát chặt quy chi phí hạ tầng.
* Thiết lập triển khai Auto Scaling Group cho hệ thống có khả năng tự động mở rộng và Elastic Load Balancing để cân bằng tải nhằm đảm bảo tính sẵn sàng cao.
* Thực hành triển khai website thực tế (WordPress/Prestashop) trên môi trường Lightsail kết hợp quản trị cơ sở dữ liệu độc lập.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Tìm hiểu về dịch vụ Compute VM trên AWS<br>&emsp; + Amazon Elastic Compute Cloud (EC2) - Instance type, AMI, Backup, Key pair, Elastic block store, Instance store, User Data, Metadata, Auto Scaling Group<br>&emsp; + EFS/FSx <br>&emsp; + Lightsail <br>&emsp; + MGN | 04/05/2026 | 04/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thứ 3 | - Thực hành cơ bản với Amazon EC2<br> - **Thực hành:** <br>&emsp; + Tạo VPC cho Linux và Windows Instances<br>&emsp; + Khởi tạo và kết nối EC2 qua SSH/RDP<br>&emsp; + Tiến hành change instance type<br>&emsp; + Tạo và quản lý EBS Snapshots, Custom AMI<br>&emsp; + Thực hành truy cập khi mất Key Pair (Zero-Key Recovery) bằng SSM và User Data<br>&emsp; + Cài đặt giao diện Desktop cho EC2 Ubuntu<br>&emsp; + Thiết lập môi trường LAMP, XAMPP, Node.js và triển khai ứng dụng trên đa nền tảng EC2. | 05/05/2026 | 05/05/2026 | <https://000004.awsstudygroup.com/> |
| Thứ 4 | - Kiểm soát quyền hạn dịch vụ EC2 qua IAM <br> - **Thực hành:** <br>&emsp; + Giới hạn EC2 theo Region, Instance Type, Storage type<br>&emsp; + Giới hạn quyền xóa EC2 theo IP và thời gian<br> - Quản trị hạ tầng qua Tag và Resource Group <br> - **Thực hành:** <br>&emsp; + Gán, sửa, xóa tags cho EC2<br>&emsp; + Dùng AWS CLI thao tác tags<br>&emsp; + Tạo Resource Groups quản lý tập trung. | 06/05/2026 | 06/05/2026 | <https://000027.awsstudygroup.com/> <br><https://000004.awsstudygroup.com/>|
| Thứ 5 | - Thiết lập hệ thống giám sát với Amazon CloudWatch<br> - **Thực hành:** <br>&emsp; + Xem, phân tích Metrics (Search, Math, Dynamic labels)<br>&emsp; + Truy vấn Logs từ máy chủ EC2 trong Logs Insights<br>&emsp; + Tạo Metrics filters <br>&emsp; + Thiết lập Alarms gửi cảnh báo<br>&emsp; + Sử dụng CloudWatch Dashboards tập trung. | 07/05/2026 | 07/05/2026 | <https://000008.awsstudygroup.com/> |
| Thứ 6 | - Triển khai Auto Scaling Group và Elastic Load Balancing<br> - **Thực hành:**<br>&emsp;+ Tạo AMI, Launch Template, Target Group, ALB<br>&emsp; + Thiết lập và kiểm thử Manual, Scheduled, Dynamic, Predictive Scaling<br> - Triển khai website trên môi trường Lightsail<br> - **Thực hành:**<br>&emsp; + Triển khai MySQL, WordPress, Prestashop<br>&emsp; + Thiết lập Static IP, cấu hình Networking<br>&emsp; + Triển khai bảo mật, Snapshots và Scale-up<br>&emsp; + Tạo cảnh báo sự cố Lightsail. | 08/05/2026 | 08/05/2026 | <https://000006.awsstudygroup.com/><br><https://000045.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* Nắm vững nền tảng Compute (Amazon EC2, Lightsail) và các loại lưu trữ (EBS, Instance Store, EFS/FSx).
* Hiểu rõ cơ chế tự động hóa quy mô (ASG) và cân bằng tải (ELB).
* Nắm bắt quy trình di chuyển máy chủ (MGN) và quản trị tập trung.

**1. Cơ bản về EC2 & Môi trường Ứng dụng (Thứ 3)**
* Phân biệt các loại lưu trữ và vận hành đa nền tảng thành công trên Amazon Linux 2023 và Windows Server 2025.
* Làm chủ kỹ thuật Change Instance Type để linh hoạt tối ưu hóa hiệu năng.
![EC2](/images/27.png)
* Thiết lập môi trường ứng dụng: Triển khai thành công LAMP Stack, Node.js trên Linux và XAMPP, Node.js trên Windows.
![EC2](/images/28.png)
![EC2](/images/29.png)
* Quản trị lưu trữ và tối ưu hóa triển khai: Làm chủ EBS Snapshots, dùng Sysprep chuẩn hóa Windows và tạo Custom AMI để rút ngắn thời gian thiết lập.
![EC2](/images/30.png)
* Cứu hộ hệ thống (Zero-Key Recovery): Khôi phục quyền truy cập Windows bằng SSM Run Command và phục hồi Linux SSH bằng User Data.
![EC2](/images/31.png)

**2. Kiểm soát Quyền hạn & Quản trị Tài nguyên (Thứ 4)**
* Tối ưu tài nguyên & chi phí: Thiết lập IAM Policy giới hạn khởi tạo EC2 bắt buộc tại Region Singapore, đúng cấu hình (t3.small, t3.large) và loại đĩa (gp3).
![EC2](/images/32.png)
* Bảo mật Zero-Trust: Chặn quyền xóa (Terminate) EC2 theo IP công ty và giới hạn khung giờ, áp dụng nguyên tắc đặc quyền tối thiểu.
![EC2](/images/33.png)
* Quản trị định danh tài nguyên: Gán, sửa, xóa Tag tự động bằng AWS CLI để lọc và tìm kiếm máy chủ nhanh chóng.
![EC2](/images/34.png)
* Quản lý hạ tầng tập trung: Khởi tạo Tag-based Resource Group để gom cụm và quản lý tài nguyên tự động theo dự án/môi trường.
![EC2](/images/35.png)

**3. Giám sát & Quản trị Tập trung CloudWatch (Thứ 5)**
* Phân tích chuyên sâu: Truy vấn Logs Insights thành công, bóc tách lỗi (ERROR, WARN) và cấu hình trực quan hóa CloudWatch Metrics.
![CloudWatch](/images/36.png)
* Tự động hóa cảnh báo: Xây dựng Metric Filters chuyển đổi Log thành số liệu đếm. Cấu hình SNS gửi Email cảnh báo sự cố tự động.
![CloudWatch](/images/37.png)
* Xây dựng CloudWatch Dashboards theo dõi toàn cảnh sức khỏe hệ thống.

**4. Cân bằng tải & Auto Scaling Group (Thứ 6 - Phần 1)**
* Thiết lập Application Load Balancer (ALB) và Target Group để phân phối lưu lượng, đảm bảo tính High Availability.
![ALB](/images/39.png)
* Vận hành Auto Scaling Group (ASG): Ép tải ứng dụng bằng script và nghiệm thu thành công khả năng Dynamic Scaling (tự động mở rộng máy chủ). Nắm vững Manual, Scheduled và Predictive Scaling.
![ASG](/images/40.png)
![ASG](/images/41.png)

**5. Triển khai & Vận hành Amazon Lightsail (Thứ 6 - Phần 2)**
* Triển khai thành công website WordPress và PrestaShop. Vận hành MySQL độc lập với Static IP ổn định.
![EC2](/images/42.png)
![EC2](/images/44.png)
![EC2](/images/43.png)
![EC2](/images/45.png)
* Vận hành nâng cao: Siết chặt bảo mật bằng cách đóng cổng SSH, tạo Automated Snapshots dự phòng và Scale-up hạ tầng an toàn.
![EC2](/images/46.png)
![EC2](/images/47.png)
![EC2](/images/48.png)
* Cấu hình Alarms gửi Email cảnh báo khi chỉ số CPU trên Lightsail vượt ngưỡng.
![EC2](/images/49.png)