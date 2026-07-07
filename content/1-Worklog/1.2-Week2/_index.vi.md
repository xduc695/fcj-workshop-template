---
title: "Worklog Tuần 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu tuần 2:

* Tìm hiểu sâu hơn về các dịch vụ mạng trên aws
* Làm quen cách tự thiết kế, khởi tạo một hệ thống mạng ảo (VPC) và thiết lập các kết nối an toàn (VPN) để kết nối dữ liệu.
* Học cách sử dụng Session Manager và triển khai truy cập trực tiếp vào máy chủ EC2 trong VPC thay thế cho SSH 
* Học cách sử dụng VPC Peering để kết nối hai VPC khác nhau, cho phép các máy chủ giao tiếp trực tiếp bằng IP nội bộ thay vì đi qua Internet.
* Học cách sử dụng Transit Gateway làm hub trung tâm và triển khai kết nối nhiều VPC thông qua một bộ định tuyến tập trung để đơn giản hóa kiến trúc mạng thay thế cho cách kết nối VPC Peering phức tạp.
* Học cách xây dựng hệ thống DNS hybrid và triển khai tích hợp hệ thống DNS on-premise với Amazon Route 53 thông qua Inbound/Outbound Endpoints và Resolver Rules.
### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Tìm hiểu sâu hơn về các dịch vụ mạng trên aws: <br>&emsp; + Amazon Virtual Private Cloud (VPC) <br>&emsp; + VPC Peering & Transit Gateway <br>&emsp; + VPN & Direct connect <br>&emsp; + Elastic Load Balancing                                                                                             | 24/04/2026   | 24/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 2   | - Làm quen với Amazon Virtual Private Cloud (Amazon VPC) và các thành phần cơ bản của Amazon VPC:<br>&emsp; + Subnets<br>&emsp; + Route Table<br>&emsp; + Internet Gateway<br>&emsp; + Nat Gateway<br> - Làm quen với tường lửa trong VPC với 2 lớp bảo mật chính: <br>&emsp; + Security Groups<br>&emsp; + Network ACLs<br> - Tìm hiểu thêm về VPC Resource Map<br> - **Thực hành:**<br>&emsp; + Khởi tạo VPC<br>&emsp; + Khởi tạo Subnet<br>&emsp; + Khởi tạo Internet Gateway<br>&emsp;+ Khởi tạo Route Table<br>&emsp;  + Khởi tạo Security Group<br>&emsp;  + Kích hoạt VPC Flow Logs để Giám sát Bảo mật<br> - Tiến hành triển khai Hạ tầng EC2 Production-Ready<br> - **Thực hành:**<br>&emsp; + Triển khai Amazon EC2 Instances<br>&emsp; + Tiến hành và kiểm tra kết nối SSH đến EC2<br>&emsp; + Khởi tạo Nat Gateway<br>&emsp;+ Sử dụng Reachability Analyzer để xem đảm bảo kết nối hoạt động <br>&emsp;  + Khởi Tạo và kết nối thông qua EC2 Instance Connect Endpoint<br>&emsp;  + Triển khai CloudWatch Monitoring & Alerting cho Tài nguyên VPC                                | 25/04/2026   | 25/04/2026      | <https://000003.awsstudygroup.com/> |
| 3   | - Tiến hành triển khai thiết lập môi trường AWS Site-to-Site VPN và Cấu hình Site to Site VPN<br> -  **Thực hành:** <br>&emsp; + Thiết lập VPC cho Site-to-Site VPN<br>&emsp; + Triển khai EC2 Instance cho Customer Gateway<br>&emsp; + Khởi tạo Virtual Private Gateway<br>&emsp; + Khởi tạo Customer Gateway<br>&emsp; + Thiết lập AWS Site-to-Site VPN Connection<br>&emsp; + Cấu hình Customer Gateway<br>&emsp; + Tiến hành tùy chỉnh AWS VPN Tunnel<br> - Tìm hiểu thêm cấu hình VPN Thay thế và Nâng cao Bảo mật cho môi trường production<br> - Hiểu thêm về Troubleshooting để tránh các sự cố về VPN Site-to-Site<br> - Đọc thêm Troubleshooting VPN Chính thức từ AWS troubleshooting VPN ở mức chuyên nghiệp<br> - Mở rộng tìm hiểu thêm về cách Kết nối VPN bằng strongSwan với Transit Gateway<br> - Tìm hiểu thêm về Infrastructure as Code Templates đặc biệt là CloudFormation để áp dụng nhanh việc tạo hạ tầng qua tự động hóa Triển khai VPC | 26/04/2026   | 26/04/2026      | <https://000003.awsstudygroup.com/> |
| 4   | - Tìm hiểu các khái niệm cơ bản về Amazon System Manager - Session Manager<br>- **Thực hành:** <br>&emsp; + Khởi tạo VPC Lab VPC<br>&emsp; + Khởi tạo Public subnet<br>&emsp; + Khởi tạo Private subnet<br>&emsp; + Khởi tạo các security group <br>&emsp; + Khởi Tạo Public EC2 Linux <br>&emsp; + Khởi Tạo Private Windows EC2<br>&emsp; + Tạo IAM Role cho phép máy chủ EC2 có thể giao tiếp với Session Manager<br>&emsp; + Tạo kết nối đến máy chủ EC2 Public<br>&emsp; + Kích hoạt tính năng DNS hostnames trên VPC để kết nối đến máy chủ Private<br>&emsp; + Khởi tạo 3 interface endpoint SSM để tiến hành kết nối đến máy chủ Private: endpoint ssm, endpoint ssmmessages, endpoint ec2messages<br>&emsp; + Tiến hành kết nối đến máy chủ Private Windows EC2<br>&emsp; + Cập nhật IAM Role cho phép quyền truy cập vào S3 cho EC2 instance<br>&emsp; + Khởi tạo S3 bucket để lưu trữ các session logs được gửi từ các EC2 instance<br>&emsp; + Khởi tạo S3 gateway endpoint<br>&emsp; + Tiến hành theo dõi session logs để xem các câu lệnh được lưu giữ<br>&emsp; + Cấu hình Port Forwarding cho kết nối RDP giữa máy của mình với máy chủ Private| 27/04/2026   | 27/04/2026      | <https://000058.awsstudygroup.com/> |
| 5   | - Làm quen và tiến hành thiết lập VPC Peering<br> - **Thực hành:** <br>&emsp; + Khởi tạo CloudFormation Templates để tạo nhanh 2 hạ tầng mạng VPC( My VPC và HG VPC)<br>&emsp; + Khởi tạo Security Group <br>&emsp; + Khởi tạo EC2 instance<br>&emsp; + Cấu hình Network ACL tại HG VPC để kiểm soát truy cập từ My VPC<br>&emsp; + Khởi tạo VPC Peering Connection giữa My VPC và HG VPC<br>&emsp; + Cập nhật Route Table trên cả 2 VPC để trỏ traffic sang Peering Connection<br>&emsp; +Kích hoạt DNS Resolution Support (Cross-Peer DNS) để phân giải Public DNS của EC2 qua kết nối Peering<br> - Làm quen và tiến hành triển khai Transit Gateway với 4 VPC<br> - **Thực hành:**<br>&emsp; + Khởi tạo Key Pair để sẵn sàng kết nối vào các máy chủ EC2 kiểm tra<br>&emsp; + Sử dụng CloudFormation Templates để triển khai nhanh 4 VPC<br>&emsp; + Khởi tạo Transit Gateway<br>&emsp; + Khởi tạo Transit Gateway Attachments (Kết nối 4 VPC vào TGW)<br>&emsp; + Khởi tạo và cấu hình Route Table cho Transit Gateway để quản lý luồng traffic giữa các VPC<br>&emsp; + Cấu hình Route Table cho từng VPC để định tuyến traffic thông qua Transit Gateway<br>&emsp; + Kiểm tra kết nối đến internet và giữa các VPC| 28/04/2026   | 28/04/2026      | <https://000019.awsstudygroup.com/> |
| 6   | - Làm quen và tiến hành thiết lập Hybrid DNS với Route 35 Resolver<br> - **Thực hành:** <br>&emsp; + Khởi tạo Key Pair để truy cập an toàn vào máy chủ EC2<br>&emsp; + Khởi tạo CloudFormation Templates để tạo nhanh 1 hạ tầng mạng VPC<br>&emsp; + Cấu hình Security Group để cấu hình và bảo mật quyền truy cập<br>&emsp; + Tiến hành kết nối đến máy chủ EC2 bằng giao thức RDP<br>&emsp; + Triển khai AWS Managed Microsoft AD (giả lập hệ thống DNS On-premises) trong Private Subnets<br>&emsp; + Cấu hình Route 53 Outbound Endpoint và Resolver Rules để định tuyến các truy vấn DNS từ AWS về phía AD<br>&emsp; + Cấu hình Route 53 Inbound Endpoint để cho phép môi trường giả lập On-premises phân giải được các tên miền trong AWS<br>&emsp; + Sử dụng nslookup hoặc Resolve-DnsName để phân giải tên miền giữa môi trường AWS và giả lập On-premise trên máy chủ ảo Windows| 29/04/2026   | 29/04/2026      | <https://000010.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

* Làm chủ kiến thức về Amazon VPC:

  * Phân biệt và thiết lập thành công Subnets (Public/Private), Route Table và cổng Gateway (Internet/NAT).
  * Thấu hiểu hàng rào bảo mật 2 lớp: Security Group (lọc máy chủ) và Network ACL (lọc tầng mạng).
  * Sử dụng VPC Resource Map để quản trị trực quan toàn bộ sơ đồ tài nguyên mạng.

* Mở rộng và Kết nối liên thông:

  * VPC Peering: Thiết lập kết nối ngang hàng trực tiếp giữa các VPC khác nhau.
  * Transit Gateway: Làm chủ mô hình định tuyến tập trung (Hub-and-Spoke) cho hệ thống quy mô lớn.

* Hiểu rõ Hybrid Cloud & High Availability:

  * VPN: Nắm vững cách tạo kênh truyền mã hóa Site-to-Site để kết nối an toàn với On-premises.
  * Direct Connect: Hiểu rõ giải pháp đường truyền vật lý riêng biệt cho doanh nghiệp.
  * ELB: Thấu hiểu cơ chế phân phối tải (Load Balancing) để đảm bảo hệ thống luôn sẵn sàng cao.


* Làm chủ kiến trúc và thiết lập hạ tầng mạng ảo (Amazon VPC):
  * Khởi tạo thành công VPC tùy chỉnh (ASG VPC) theo chuẩn Multi-AZ.
  * Phân bổ không gian mạng thành các Public và Private Subnet.
  * Cấu hình Internet Gateway (IGW) và liên kết Route Table để định tuyến luồng mạng.

* Thiết lập kết nối Internet an toàn cho máy chủ nội bộ:
  * Khởi tạo và cấp phát Elastic IP.
  * Triển khai NAT Gateway giúp máy chủ tại Private Subnet truy cập Internet một chiều an toàn (không phơi nhiễm ra ngoài).

* Triển khai và vận hành hệ thống máy chủ ảo (Amazon EC2):
  * Khởi tạo các EC2 Instances (Amazon Linux 2) trên cả hai môi trường Public và Private.
  * Thực hành thành thạo luồng kết nối SSH nhảy (Jump) từ máy cá nhân -> EC2 Public -> EC2 Private.

![VPC](/images/11.png)

* Quản trị truy cập và bảo mật mạng đa tầng (Security & Access Control):
  * Cấu hình Security Groups và Network ACLs theo nguyên tắc đặc quyền tối thiểu (chỉ mở cổng thiết yếu).
  * Triển khai truy cập máy chủ nâng cao (Zero-Trust) qua EIC Endpoint và Session Manager, loại bỏ hoàn toàn việc mở public port 22.

![Security Group](/images/12.png)

* Triển khai hệ thống giám sát, phân tích và cảnh báo (Monitoring & Analytics):
  * Ứng dụng VPC Reachability Analyzer để kiểm tra và khắc phục sự cố (troubleshoot) kết nối mạng.
  * Kích hoạt VPC Flow Logs để lưu vết toàn bộ lưu lượng IP ra/vào.
  * Thiết lập CloudWatch Monitoring bao gồm: Dashboard, Metric Filters và Alarms cảnh báo sự cố.

![CloudWatch](/images/13.png)

![CloudWatch](/images/14.png)

* Thiết lập môi trường mạng On-premise mô phỏng:

  * Khởi tạo thành công mạng nội bộ chi nhánh (Branch Office VPC) 
  * Triển khai máy chủ EC2 đóng vai trò thiết bị Customer Gateway (CGW).
  
* Cấu hình hạ tầng kết nối AWS Site-to-Site VPN:

  * Khởi tạo Virtual Private Gateway (VGW) trên AWS 
  * Thiết lập kết nối VPN bằng cơ chế định tuyến tĩnh (Static Routing).
  * Kích hoạt Route Propagation để tự động đồng bộ bảng định tuyến giữa hai mạng.

![VPN](/images/15.png)

* Vận hành Customer Gateway & Khắc phục sự cố (Troubleshooting):

  * Khắc phục thành công sự cố tương thích OS bằng cách chủ động sử dụng Libreswan thay thế cho OpenSwan trên Amazon Linux 2023.
  * Cấu hình IPsec Tunnel và nghiệm thu thành công: Hai máy chủ ở hai mạng khác nhau đã ping thông suốt với nhau bằng Private IP qua đường hầm bảo mật.

![VPN](/images/16.png)

* Nghiên cứu Kiến thức học hỏi và tìm hiểu thêm:

  * Nắm bắt lý thuyết các giải pháp cấp doanh nghiệp: Kết nối VPN tập trung qua Transit Gateway, định tuyến BGP và quy trình khắc phục sự cố VPN chuẩn AWS.
  * Tìm hiểu tư duy tự động hóa hạ tầng (IaC) thông qua AWS CloudFormation.

* Triển khai Truy cập Zero-Trust với AWS Session Manager:

  * Khởi tạo và gán thành công IAM Role (AmazonSSMManagedInstanceCore) cấp quyền cho EC2 giao tiếp với Session Manager.
  * Khởi tạo các VPC Endpoints (ssm, ssmmessages, ec2messages) để thiết lập luồng kết nối hoàn toàn khép kín qua mạng nội bộ cho máy chủ Private.

  * Kết nối shell an toàn đến cả máy chủ Public và Private trực tiếp trên trình duyệt. Loại bỏ hoàn toàn sự phụ thuộc vào Bastion Host và giảm thiểu gánh nặng quản lý SSH Keys.

![Session Manager](/images/17.png)

* Lưu vết kiểm toán và kết nối nâng cao:

  * Cấu hình S3 Bucket và S3 Gateway Endpoint để tự động lưu vết toàn bộ nhật ký phiên làm việc (Session Logs), đáp ứng yêu cầu kiểm toán bảo mật.

![S3](/images/18.png)

  * Ứng dụng AWS CLI để thực hiện Port Forwarding, thiết lập kết nối Remote Desktop (RDP) an toàn vào máy chủ Private thông qua localhost.

![RDP](/images/19.png)

* Áp dụng AWS CloudFormation để tự động hóa hạ tầng (IaC):

  * Khởi tạo tự động 2 kiến trúc mạng (My VPC, HG VPC) và các máy chủ EC2 tương ứng bằng template AWS CloudFormation.

* Thiết lập kết nối nội bộ (VPC Peering):

  * Thiết lập thành công kết nối VPC Peering và cập nhật Route Table trên cả 2 VPC, cho phép các máy chủ giao tiếp trực tiếp qua mạng nội bộ AWS thay vì Internet.

![VPC Peering](/images/20.png)

* Bảo mật đa lớp và Phân giải tên miền:

  * Cấu hình Network ACL và Security Group để chặn hoàn toàn luồng Ping từ Internet, chỉ cho phép truy cập nội bộ chéo giữa 2 dải mạng (CIDR).

  * Kích hoạt Cross-Peer DNS để EC2 tự động phân giải Public DNS thành Private IP, đảm bảo dữ liệu di chuyển an toàn tuyệt đối.

![DNS](/images/21.png)

* Tối ưu hóa kiến trúc mạng bằng AWS Transit Gateway:
  * Triển khai thành công AWS Transit Gateway làm bộ định tuyến trung tâm (Hub), thay thế giải pháp VPC Peering phức tạp để kết nối 4 VPC độc lập.

* Kết nối hạ tầng tập trung:
  * Tạo các Transit Gateway Attachments, kết nối thành công toàn bộ 4 VPC vào chung một mạng lưới duy nhất.

![Transit Gateway](/images/22.png)

* Quản lý định tuyến và Kiểm thử:

  * Cấu hình Transit Gateway Route Tables (thiết lập Associations và Propagations) để quản lý luồng dữ liệu tập trung, đồng thời cập nhật Route Table tại từng VPC nhánh trỏ về Transit Gateway để tạo thành mạng Hub-and-Spoke hoàn chỉnh

  * Nghiệm thu thành công: Máy chủ từ VPC này có thể kết nối (ping, SSH) trực tiếp sang máy chủ của VPC khác thông qua mạng nội bộ AWS.

![Transit Gateway](/images/23.png)

* Triển khai môi trường giả lập DNS On-premises:
  * Tinh chỉnh Security Group theo nguyên tắc bảo mật, kết nối an toàn vào máy chủ Windows (RDGW) thông qua giao thức RDP.
  * Triển khai thành công dịch vụ AWS Managed Microsoft AD (giả lập hệ thống DNS On-premises) với tên miền nội bộ onprem.example.com đặt tại Private Subnet.

![Microsoft AD](/images/24.png)

* Xây dựng kiến trúc Hybrid DNS luồng hai chiều:
  * Khởi tạo Route 53 Outbound Endpoint và cấu hình Resolver Rules (Forward): Định tuyến tự động các truy vấn tên miền từ hạ tầng AWS trỏ về máy chủ DNS On-premises (Directory Service).
  * Khởi tạo Route 53 Inbound Endpoint: Mở cổng giao tiếp nhận các truy vấn DNS từ hệ thống On-premises gửi ngược vào AWS để phân giải các Private Hosted Zone.

![Route 53](/images/25.png)

* Kiểm thử và Nghiệm thu:
  * Nghiệm thu phân giải tên miền chéo: Kết nối RDP vào máy chủ RDGW và sử dụng dòng lệnh truy vấn thành công IP của tên miền On-premises (onprem.example.com).

![Route 53](/images/26.png)