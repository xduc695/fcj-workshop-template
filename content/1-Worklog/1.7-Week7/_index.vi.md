---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Củng cố kiến thức về CI/CD và tìm hiểu cấu trúc file YAML dùng để xây dựng pipeline trên GitHub Actions.
* Xây dựng cấu trúc cơ sở dữ liệu phục vụ cho dự án nhóm (hệ thống ngân hàng chịu tải cao).
* Nghiên cứu và tổng hợp các dịch vụ chính cần sử dụng trong mô hình kiến trúc của dự án nhóm.
* Tìm hiểu quy trình và tiến hành thực hành triển khai tự động lên Amazon ECS Express Mode bằng GitHub Actions.
* Tổng hợp kiến thức đã tìm hiểu về triển khai tự động với GitHub Actions cho Amazon ECS Express Mode để viết bài chia sẻ lên cộng đồng.
* Tìm hiểu quy trình cách triển khai định tuyến endpoint đa Region cho Amazon Aurora DSQL.
### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 1   | - Tìm hiểu về CI/CD và cấu trúc pipeline GitHub Actions: <br>&emsp; + Ôn tập khái niệm CI/CD <br>&emsp; + Tìm hiểu vai trò của GitHub Actions <br>&emsp; + Tìm hiểu cấu trúc file YAML trong pipeline <br>&emsp; + Tìm hiểu cấu trúc file YAML trong pipeline <br>&emsp; + Phân tích các thành phần chính của workflow                                                                                           | 29/05/2026   | 29/05/2026      |
| 2   | - Xây dựng cấu trúc cơ sở dữ liệu cho dự án ngân hàng chịu tải cao: <br>&emsp; + Xác định các bảng chính trong hệ thống <br>&emsp; + Thiết kế bảng người dùng, khách hàng và tài khoản ngân hàng <br>&emsp; + hiết kế bảng chuyển khoản, giao dịch và lịch sử số dư <br>&emsp; + Bổ sung bảng audit log, notification và outbox event <br>&emsp; + Tạo khóa ngoại, ràng buộc dữ liệu và index hỗ trợ chịu tải                                           | 30/05/2026   | 30/05/2026      | 
| 3   | - Nghiên cứu và tổng hợp các dịch vụ chính trong mô hình kiến trúc dự án nhóm:<br>&emsp; + Xác định các thành phần chính của hệ thống <br>&emsp; + Tìm hiểu dịch vụ backend, frontend và cơ sở dữ liệu <br>&emsp; + Tìm hiểu dịch vụ lưu trữ, bảo mật và định tuyến <br>&emsp; + Tổng hợp vai trò của từng dịch vụ trong kiến trúc dự án | 31/05/2025   | 31/05/2025      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu quy trình và tiến hành thực hành triển khai tự động lên Amazon ECS Express Mode bằng GitHub Actions, nhằm xây dựng pipeline CI/CD tự động cho ứng dụng container hóa, giúp tự động build Docker image, đẩy image lên Amazon ECR và triển khai service lên Amazon ECS Express Mode <br> - **Thực hành:** <br>&emsp; + Fork và clone repository mẫu từ AWS Blog <br>&emsp; + Tạo Amazon ECR repository để lưu trữ Docker image <br>&emsp; + Cấu hình IAM Role, IAM Policy và OIDC Provider để GitHub Actions xác thực an toàn với AWS <br>&emsp; + Tạo các IAM Role cần thiết cho Amazon ECS Express Mode <br>&emsp; + Cấu hình GitHub Repository Variables cho workflow triển khai <br>&emsp; + Chạy GitHub Actions workflow để build, tag và push Docker image lên Amazon ECR <br>&emsp; + Triển khai ứng dụng container lên Amazon ECS Express Mode  <br>&emsp; + Kiểm tra triển khai, xử lý lỗi và dọn dẹp tài nguyên AWS sau khi hoàn tất                | 01/06/2026   | 01/06/2026      | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/> |
| 5   | - Tổng hợp kiến thức về triển khai tự động với GitHub Actions cho Amazon ECS Express Mode để xây dựng bài chia sẻ lên cộng đồng: <br>&emsp; + Tóm tắt nội dung chính của bài AWS Blog về Amazon ECS Express Mode <br>&emsp; + Hệ thống lại quy trình CI/CD: build Docker image, push lên Amazon ECR và deploy lên Amazon ECS Express Mode <br>&emsp; + Phân tích vai trò của các thành phần: GitHub Actions, Docker, Amazon ECR, Amazon ECS Express Mode, IAM Role và OIDC <br>&emsp; + Tổng hợp các bước thực hành đã triển khai và các lỗi phát sinh trong quá trình thực hiện <br>&emsp; + Biên soạn bài viết chia sẻ theo hướng dễ hiểu, ngắn gọn và phù hợp để đăng lên cộng đồng                                                                                         | 02/06/2025   | 02/06/2025      | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/> |
| 6   | - Tìm hiểu quy trình triển khai định tuyến endpoint đa Region cho Amazon Aurora DSQL: <br>&emsp; + Tìm hiểu mô hình Aurora DSQL multi-Region và các endpoint theo từng Region <br>&emsp; + Tìm hiểu vai trò của Route 53 health checks trong việc giám sát trạng thái endpoint <br>&emsp; + Tìm hiểu cơ chế lựa chọn endpoint healthy có độ trễ thấp nhất <br>&emsp; + Tìm hiểu cách cấu hình file DSQL và tạo health checks cho các endpoint <br>&emsp; + Tìm hiểu cách kiểm tra kết nối, failover và tích hợp connection manager vào ứng dụng| 03/06/2025   | 03/06/2025      | <https://awsstudygroup.com/2026/01/09/trien-khai-dinh-tuyen-endpoint-da-region-cho-amazon-aurora-dsql/> |

### Kết quả đạt được tuần 7:

* Củng cố kiến thức về CI/CD và GitHub Actions:
  * Nắm được vai trò của CI/CD trong tự động hóa quy trình phát triển và triển khai phần mềm.
  * Hiểu cách GitHub Actions sử dụng workflow để tự động thực hiện các bước build, test hoặc deploy.

* Hiểu cấu trúc file YAML trong pipeline:
  * Nắm được các thành phần chính của file workflow như `name`, `on`, `jobs`, `steps`, `uses` và `run`.
  * Biết cách phân tích luồng hoạt động cơ bản của một pipeline trên GitHub Actions.

* Thiết kế được cấu trúc cơ sở dữ liệu cho hệ thống ngân hàng chịu tải cao:
  * Xác định được các bảng chính như người dùng, khách hàng, tài khoản, giao dịch, thông báo và nhật ký hệ thống.
  * Thiết lập được khóa chính, khóa ngoại, ràng buộc dữ liệu và index hỗ trợ truy vấn.

* Tổng hợp được các dịch vụ chính trong mô hình kiến trúc dự án nhóm:
  * Xác định được các thành phần chính của hệ thống như backend, frontend, cơ sở dữ liệu, lưu trữ, bảo mật và định tuyến.
  * Hiểu được vai trò của từng dịch vụ trong quá trình triển khai và vận hành hệ thống.
  * Có cơ sở để lựa chọn, điều chỉnh và hoàn thiện kiến trúc dự án ở các bước tiếp theo.

* Triển khai thành công pipeline CI/CD tự động với GitHub Actions cho Amazon ECS Express Mode:

  * Workflow GitHub Actions tự động thực hiện các bước: build Docker image, tag image theo commit, push image lên Amazon ECR và triển khai service lên Amazon ECS Express Mode.
  * Kiểm chứng quá trình triển khai thông qua log workflow trên GitHub Actions, đảm bảo các bước build, push và deploy được thực hiện đúng quy trình.

![GitHub Actions Workflow](/images/77.png)

* Cấu hình thành công cơ chế xác thực an toàn giữa GitHub Actions và AWS bằng IAM Role và OIDC:

  * Tạo và cấu hình IAM Role `github-actions-ecs-role` để GitHub Actions có thể assume role khi triển khai.
  * Sử dụng OIDC Provider nhằm hạn chế việc lưu trữ AWS Access Key dài hạn trong GitHub Repository, góp phần tăng cường an toàn cho pipeline triển khai.

![IAM OIDC Role](/images/78.png)

* Triển khai thành công ứng dụng container lên Amazon ECS Express Mode:

  * Docker image được lưu trữ thành công trên Amazon ECR.
  * ECS Express Mode tạo service, task và endpoint để chạy ứng dụng container trên AWS.
  * Kiểm tra được trạng thái service, task và endpoint sau khi triển khai.

![Amazon ECS Express Service](/images/79.png)

* Hoàn thành việc tổng hợp kiến thức về triển khai tự động với GitHub Actions cho Amazon ECS Express Mode:

  * Nắm được nội dung chính của bài AWS Blog và vai trò của mô hình trong quy trình CI/CD hiện đại.
  * Hệ thống lại được luồng triển khai tự động: từ GitHub Actions, build Docker image, push lên Amazon ECR đến deploy lên Amazon ECS Express Mode.
  * Phân tích được vai trò của các thành phần chính như GitHub Actions, Docker, Amazon ECR, Amazon ECS Express Mode, IAM Role và OIDC.
  * Tổng hợp được các bước triển khai, lỗi thường gặp và cách xử lý trong quá trình thực hiện.
  * Biên soạn được bài viết chia sẻ ngắn gọn, dễ hiểu và phù hợp để đăng lên cộng đồng.

* Nắm được quy trình định tuyến endpoint đa Region cho Amazon Aurora DSQL:

  * Hiểu được mô hình Aurora DSQL multi-Region và cách các endpoint theo từng Region hỗ trợ kết nối cơ sở dữ liệu.
  * Nắm được vai trò của Route 53 health checks trong việc giám sát trạng thái endpoint.
  * Hiểu cơ chế lựa chọn endpoint healthy có độ trễ thấp nhất để tối ưu kết nối.
  * Biết cách cấu hình file DSQL, tạo health checks và kiểm tra khả năng failover giữa các Region.





