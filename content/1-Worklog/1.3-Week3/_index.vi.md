---
title: "Worklog Tuần 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu tuần 3:

* Tìm hiểu về dịch vụ Compute VM trên AWS
* Thực hành cơ bản với Amazon EC2, thiết lập môi trường ứng dụng Node.js trên đa nền tảng (Windows/Linux) kết hợp quản trị vòng đời máy chủ EC2 và kiểm soát quyền hạn nghiêm ngặt qua IAM
* Triển khai quản trị hạ tầng qua Tag và Resource Groups để quản lý tập trung, giúp tự động hóa vận hành và kiểm soát tài nguyên theo dự án hoặc môi trường
* Thiết lập hệ thống giám sát và quản trị tập trung thông qua việc phân tích chuyên sâu các thông số vận hành (Metrics) và nhật ký hệ thống (Logs), nhằm cấu hình các cơ chế phản hồi tự động giúp tối ưu hóa hiệu suất và kiểm soát chặt chẽ chi phí hạ tầng
* Thực hành theo dõi hiệu năng và trạng thái vận hành hệ thống AWS thông qua các chỉ số Metrics và nhật ký Logs, từ đó cấu hình các ngưỡng cảnh báo (Alarms) tự động nhằm ứng phó sự cố kịp thời và tối ưu hóa quản trị chi phí hạ tầng
* Thiết lập triển khai Auto Scaling Group cho hệ thống có khả năng tự động mở rộng và  Elastic Load Balancing để cân bằng tải nhằm đảm bảo tính sẵn sàng cao, tối ưu hóa hiệu suất vận hành và chi phí dựa trên lưu lượng truy cập thực tế của người dùng
* Thực hành triển khai website thực tế (WordPress/Prestashop) trên môi trường Lightsail kết hợp quản trị cơ sở dữ liệu độc lập và tham khảo xem thêm cách triển khai website Akaunting 
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                                                                       | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Tìm hiểu về dịch vụ Compute VM trên AWS<br>&emsp; + Amazon Elastic Compute Cloud (EC2) - Instance type, AMI, Backup, Key pair, Elastic block store, Instance store, User Data, Metadata, Auto Scaling Group<br>&emsp; + EFS/FSx <br>&emsp; + Lightsail  <br>&emsp; + MGN                                                                                                    | 01/05/2026   | 01/05/2026      |   <https://cloudjourney.awsstudygroup.com/> |
| 2   | - Thực hành cơ bản với Amazon EC2<br> - **Thực hành:** <br>&emsp; + Tạo VPC cho Linux Instances và Windows Instances<br>&emsp; + Tạo EC2 Instances Linux và Windows<br>&emsp; + Kết nối đến máy chủ Linux và Windows thông qua SSH và RDP<br>&emsp; + Tiến hành change instance type<br>&emsp; + Tạo và quản lý EBS Snapshots<br>&emsp; + Tạo AMI và tiến hành triển khai EC2 instance bằng AMI vừa tạo<br>&emsp; + Thực hành truy cập khi mất Key Pair EC2-Windows bằng SSM và Linux bằng User data<br>&emsp; + Tìm hiểu thêm về cách cấu hình giao diện Desktop cho EC2-Ubuntu 22.04, Amazon EBS Snapshots Archive, và cách chia sẽ custom AMI<br>&emsp; + Thiết lập môi trường ứng dụng Node.js trên đa nền tảng EC2(Windows/Linux)<br>&emsp; + Tiến hành cài đặt LAMP web server trên EC2 Linux<br>&emsp; + Cài đặt Node.js trên EC2 Linux<br>&emsp; + Tiến hành triển khai ứng dụng trên EC2 Linux<br>&emsp; + Cài đặt XAMPP trên EC2 Windows<br>&emsp; + Cài đặt Node.js trên EC2 Windows<br>&emsp; + Tiến hành triển khai ứng dụng trên EC2 Windows                            | 02/05/2026   | 02/05/2026      | <https://000004.awsstudygroup.com/> |
| 3   | - Tiến hành triển khai kiểm soát một số quyền hạn khi sử dụng dịch vụ EC2 qua IAM <br> - **Thực hành:** <br>&emsp; + Giới hạn sử dụng EC2 chỉ trên Region Singapore <br>&emsp; + Giới hạn sử dụng EC2 theo Instance Family<br>&emsp; + Giới hạn sử dụng EC2 theo Instance Type<br>&emsp; + Giới hạn sử dụng EBS volume storage type<br>&emsp; + Giới hạn quyền xóa EC2 theo địa chỉ IP của Doanh nghiệp<br>&emsp; + Giới hạn quyền xóa EC2 theo khoảng thời gian<br> - Tiến hành triển khai quản trị hạ tầng qua Tag và Resource Group <br> - **Thực hành:** <br>&emsp; + Gán tags cho EC2 instances<br>&emsp; + Thêm hoặc xóa tags<br>&emsp; + Lọc tài nguyên theo tags<br>&emsp; + Dùng AWS CLI đế thao tác với tags<br>&emsp; + Tạo Resource Groups và tìm kiếm theo tags       | 03/05/2026   | 03/05/2026      | <https://000027.awsstudygroup.com/> <br><https://000004.awsstudygroup.com/>|
| 4   | -  Thiết lập hệ thống giám sát và quản trị tập trung thông qua Amazon CloudWatch<br> - **Thực hành:** <br>&emsp; + Xem và phân tích các Metrics<br>&emsp; + Sử dụng các phép tìm kiếm và toán học trong Metrics<br>&emsp; + Tạo và sử dụng dynamic labels trong Metrics<br>&emsp; + Xem và cấu hình CloudWatch Logs<br>&emsp; + Tiến hành truy vấn logs từ máy chủ ec2 trong CloudWatch Logs Insights<br>&emsp; + Tiến hành tạo Metrics filters <br>&emsp; + Thiết lập Alarms cho Metrics vừa tạo<br>&emsp; +  Sử dụng CloudWatch Dashboards để tập trung quản lý các Metrics và Alarms<br>                                               | 04/05/2026   | 04/05/2026      | <https://000008.awsstudygroup.com/> |
| 5   | - Thực hành triển khai Auto Scaling Group  để đảm bảo khả năng mở rộng linh hoạt và Elastic Load Balancing để cân bằng tải, phân phối lượng request đến hệ thống<br> - **Thực hành:**<br>&emsp;+ Tạo AMIs và Launch Template để để cấu hình khởi tạo các EC2 instance<br>&emsp; + Thiết lập Target Group và Application Load Balancer<br>&emsp;+ Kiểm tra hoạt động của hệ thống với Load Balancer<br>&emsp; + Thiết lập Auto Scaling Group<br>&emsp; + Kiểm thử hệ thống với Manual Scaling<br>&emsp; + Kiểm thử hệ thống với Scheduled Scaling<br>&emsp; + Kiểm thử hệ thống với Dynamic Scaling<br>&emsp; + Đọc metrics của giải pháp Predictive Scaling                                                                           | 05/05/2026   | 05/05/2026      | <https://000006.awsstudygroup.com/> |
| 6   | - Thực hành triển khai website thực tế (WordPress/Prestashop) trên môi trường Lightsail kết hợp quản trị cơ sở dữ liệu độc lập và tham khảo xem thêm cách triển khai website Akaunting<br> - **Thực hành:**<br>&emsp; + Triển khai một database MySQL trên Lightsail<br>&emsp; + Triển khai WordPress và Prestashop E-Commerce Instance trên Lightsail<br>&emsp; + Cấu hình ubuntu cho WordPress Instance<br>&emsp; +    Cấu hình Networking cho WordPress và Prestashop E-Commerce Instance<br>&emsp; + Triển khai 2 Instances<br>&emsp; + Triển khai bảo mật ứng dụng<br>&emsp; + Tạo Bản Snapshot<br>&emsp; + Tiến hành dịch chuyển sang instance lớn hơn<br>&emsp; + Tạo cảnh báo sự cố                                                            | 06/05/2026   | 06/05/2026      | <https://000045.awsstudygroup.com/> |
### Kết quả đạt được tuần 3:

* Nắm vững nền tảng Compute (Amazon EC2 & Storage)

  * Hiểu rõ quy trình khởi tạo Instance qua các thành phần: Instance Type, AMI, Key Pair và User Data.
  * Phân biệt các loại lưu trữ: EBS (lưu trữ bền vững), Instance Store (lưu trữ tạm thời) và giải pháp lưu trữ file dùng chung (EFS/FSx).
  * Làm chủ cơ chế bảo vệ dữ liệu bằng EBS Snapshot và nhân bản hệ thống nhanh chóng qua Custom AMI.

* Học cách tối ưu hóa khả năng mở rộng và triển khai:

  * Auto Scaling Group (ASG): Thấu hiểu các cơ chế tự động điều chỉnh số lượng máy chủ (Manual, Dynamic, Predictive) để đảm bảo tính sẵn sàng cao và tối ưu chi phí.
  * AWS Lightsail: Tìm hiểu cách triển khai ứng dụng trọn gói (all-in-one) đơn giản và nhanh chóng.
  * AWS MGN: Tìm hiểu về quy trình di chuyển máy chủ từ môi trường ngoài lên đám mây.

* Vận hành đa nền tảng với Amazon EC2:

  * Khởi tạo và cấu hình thành công máy chủ trên cả hai hệ điều hành Amazon Linux 2023 và Windows Server 2025.
  * Làm chủ kỹ thuật Change Instance Type giúp linh hoạt tối ưu hóa hiệu năng và chi phí theo nhu cầu thực tế của dự án.

![EC2](/images/27.png)

* Thiết lập môi trường ứng dụng chuyên sâu:

  * Linux: Triển khai thành công LAMP Stack, Node.js và vận hành ổn định ứng dụng CRUD "User Management" trên Port 5000.
  * Windows: Cấu hình môi trường XAMPP, Node.js và đồng bộ hóa thành công dữ liệu ứng dụng trên nền tảng Windows Server.

![EC2](/images/28.png)
![EC2](/images/29.png)
* Quản trị lưu trữ và Sao lưu dữ liệu:

  * Thực hiện tạo EBS Snapshots định kỳ cho các Volume hệ thống, đảm bảo an toàn dữ liệu.
  * Nghiên cứu ứng dụng EBS Snapshot Archive – giải pháp tối ưu chi phí lưu trữ dài hạn (tiết kiệm đến 75%).

* Tối ưu hóa quy trình triển khai:

  * Sử dụng Sysprep chuẩn hóa Windows trước khi tạo Image, đảm bảo tính nhất quán và tránh xung đột SID khi nhân bản.
  * Khởi tạo thành công Custom AMI, giúp rút ngắn thời gian thiết lập hạ tầng và sẵn sàng cho việc chia sẻ liên tài khoản (Cross-account).

![EC2](/images/30.png)

* Bảo mật và Kiểm soát truy cập:

  * Thiết lập Security Groups đa tầng theo nguyên tắc Least Privilege, kiểm soát chặt chẽ lưu lượng ra/vào.

  * Gán IAM Role (AmazonSSMManagedInstanceCore) cho phép quản trị máy chủ an toàn thông qua Systems Manager (SSM) mà không cần quản lý Key Pair truyền thống.

* Cứu hộ hệ thống (Zero-Key Recovery):

  * Windows: Khôi phục quyền truy cập bằng cách reset mật khẩu Administrator thông qua SSM Run Command.

  * Linux: Cứu hộ quyền SSH bằng kỹ thuật thay thế Public Key thông qua User Data trong quá trình khởi tạo lại máy chủ.

![EC2](/images/31.png)

* Nghiên cứu & Phát triển (R&D)
   * Trải nghiệm người dùng: Nghiên cứu quy trình cài đặt giao diện Desktop (GUI) và xRDP trên Ubuntu để tối ưu hóa việc quản trị trực quan.
   * Phân phối hạ tầng: Nắm vững cơ chế chia sẻ AMI giữa các AWS Account, phục vụ mục tiêu mở rộng hệ thống trong tương lai.

* Tối ưu tài nguyên & chi phí:
   * Giới hạn khởi tạo EC2 bắt buộc chỉ tại Region Singapore.
   * Chỉ cho phép khởi tạo máy chủ đúng cấu hình quy định (t3.small, t3.large) và dùng loại ổ đĩa tiết kiệm chi phí (gp3).

![EC2](/images/32.png)

* Bảo mật Zero-Trust (AWS IAM):

   * Chặn quyền xóa (Terminate) EC2 nếu truy cập ngoài địa chỉ IP của công ty.
   * Khóa quyền xóa EC2 theo các mốc thời gian giới hạn cụ thể.
   * Áp dụng nguyên tắc Đặc quyền tối thiểu (Least Privilege) và quản lý phân quyền tập trung qua IAM Group.

![EC2](/images/33.png)

* Quản trị định danh tài nguyên (AWS Tags):

   * Thực hiện thành thạo việc gán, sửa, xóa Tag (Owner, Environment) cho tài nguyên đơn lẻ và hàng loạt; ứng dụng Tag để lọc/tìm kiếm máy chủ EC2 nhanh chóng.

   * Tự động hóa bằng AWS CLI: Ứng dụng dòng lệnh để tự động hóa việc dán nhãn ngay trong lúc khởi tạo tài nguyên mới (EC2, EBS Volume).

![EC2](/images/34.png)

* Quản lý hạ tầng tập trung (Resource Groups):

   * Khởi tạo thành công Tag-based Resource Group để gom cụm tự động các máy chủ có chung thẻ định danh.
   * Chuyển từ việc quản lý đơn lẻ từng máy chủ sang quản lý tập trung theo nhóm/dự án/môi trường.

![EC2](/images/35.png)

* Giám sát & Phân tích chuyên sâu (Metrics & Logs):

  * CloudWatch Metrics: Vận dụng thành thạo Search/Math Expressions để lọc, sắp xếp và trực quan hóa các thông số máy chủ. Cấu hình tự động đổi tên nhãn (Dynamic Labels).

  * Logs Insights: Truy vấn thành công dữ liệu nhật ký hệ thống bằng ngôn ngữ query, bóc tách chính xác các sự kiện lỗi (ERROR, WARN) và lưu trữ câu lệnh mẫu.

![CloudWatch](/images/36.png)

* Tự động hóa cảnh báo & Quản trị tập trung:

  * Metric Filters: Thiết lập bộ lọc tự động chuyển đổi dữ liệu dạng văn bản (Log text) thành các chỉ số đo lường được (Count Metrics).

  * Alarms & SNS: Cấu hình hệ thống tự động gửi Email cảnh báo khi số lượng lỗi ứng dụng vượt ngưỡng.

  * Dashboards: Xây dựng thành công bảng điều khiển trung tâm để theo dõi toàn cảnh sức khỏe hệ thống và các cảnh báo trên một giao diện duy nhất.

![CloudWatch](/images/37.png)
![CloudWatch](/images/38.png)

* Chuẩn hóa hạ tầng & Cân bằng tải:

  * Tạo Custom AMI và Launch Template để đóng gói và tự động hóa việc nhân bản máy chủ.

  * Thiết lập Application Load Balancer (ALB) và Target Group để phân phối lưu lượng, đảm bảo hệ thống luôn sẵn sàng (High Availability).

![ALB](/images/39.png)
* Kiểm thử & Vận hành Auto Scaling Group (ASG):

  * Manual & Scheduled Scaling: Thành thạo tăng/giảm số lượng máy chủ thủ công và thiết lập lịch trình mở rộng tự động theo các khung giờ cố định.

  * Dynamic Scaling: Tự viết đoạn script JavaScript gửi hàng nghìn requests/lượt để ép tải ứng dụng. Nghiệm thu thành công việc ASG tự động sinh thêm máy chủ khi phát hiện quá tải.

  * Predictive Scaling: Tích hợp Custom Metrics và đọc hiểu biểu đồ dự báo (Forecast) để ASG tự chuẩn bị trước tài nguyên dựa trên lịch sử truy cập.

![ASG](/images/40.png)
![ASG](/images/41.png)

* Triển khai & Quản trị Website thực tế trên Amazon Lightsail Workshop:

  * Thiết lập thành công website WordPress và cửa hàng PrestaShop trên môi trường Lightsail.

  * Vận hành máy chủ MySQL độc lập với tính năng sẵn sàng cao (High-Availability) để bảo vệ dữ liệu.

  * Gán IP tĩnh (Static IP) đảm bảo địa chỉ truy cập website luôn ổn định.

![EC2](/images/42.png)
![EC2](/images/44.png)
![EC2](/images/43.png)
![EC2](/images/45.png)
* Bảo mật & Vận hành nâng cao trên Amazon Lightsail Workshop :

  * Siết chặt bảo mật bằng cách đóng hoàn toàn cổng SSH (Port 22) sau khi hoàn tất cấu hình.

  * Thiết lập sao lưu tự động (Automated Snapshots) và Snapshot thủ công để dự phòng dữ liệu.

  * Nâng cấp hạ tầng từ Instance nhỏ sang lớn hơn (Scale-up) thông qua Snapshot mà không mất dữ liệu.

![EC2](/images/46.png)
![EC2](/images/47.png)
![EC2](/images/48.png)

* Giám sát & Cảnh báo trên Amazon Lightsail Workshop:

  * Cấu hình Alarms tự động gửi Email khi chỉ số CPU vượt ngưỡng cho phép.

  * Theo dõi và phân tích hiệu năng hệ thống theo thời gian thực thông qua CloudWatch Metrics.

![EC2](/images/49.png)