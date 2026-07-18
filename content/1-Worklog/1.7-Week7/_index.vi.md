---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Củng cố kiến thức về CI/CD và tìm hiểu cấu trúc file YAML dùng để xây dựng pipeline trên GitHub Actions.
* Xây dựng cấu trúc cơ sở dữ liệu phục vụ cho dự án nhóm (High-Concurrency Payment Gateway).
* Nghiên cứu và tổng hợp các dịch vụ chính cần sử dụng trong mô hình kiến trúc của dự án nhóm.
* Tìm hiểu quy trình và tiến hành thực hành triển khai tự động lên Amazon ECS Express Mode bằng GitHub Actions.
* Tổng hợp kiến thức đã tìm hiểu về triển khai tự động với GitHub Actions cho Amazon ECS Express Mode để viết bài chia sẻ lên cộng đồng.
* Tìm hiểu quy trình cách triển khai định tuyến endpoint đa Region cho Amazon Aurora DSQL.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Tìm hiểu về CI/CD và cấu trúc pipeline GitHub Actions: <br>&emsp; + Ôn tập khái niệm CI/CD <br>&emsp; + Tìm hiểu vai trò của GitHub Actions <br>&emsp; + Tìm hiểu cấu trúc file YAML trong pipeline <br>&emsp; + Phân tích các thành phần chính của workflow | 01/06/2026 | 01/06/2026 | |
| Thứ 3 | - Xây dựng cấu trúc cơ sở dữ liệu cho dự án High-Concurrency Payment Gateway: <br>&emsp; + Xác định các bảng chính trong hệ thống <br>&emsp; + Thiết kế bảng người dùng, khách hàng, tài khoản, giao dịch, lịch sử số dư... <br>&emsp; + Bổ sung bảng audit log, notification, outbox event <br>&emsp; + Tạo khóa ngoại, ràng buộc và index | 02/06/2026 | 02/06/2026 | |
| Thứ 4 | - Nghiên cứu và tổng hợp các dịch vụ chính trong mô hình kiến trúc dự án nhóm:<br>&emsp; + Xác định các thành phần chính của hệ thống <br>&emsp; + Tìm hiểu dịch vụ backend, frontend, cơ sở dữ liệu, lưu trữ, bảo mật, định tuyến | 03/06/2026 | 03/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thứ 5 | - Thực hành triển khai tự động lên Amazon ECS Express Mode bằng GitHub Actions <br> - **Thực hành:** <br>&emsp; + Fork và clone repository mẫu <br>&emsp; + Tạo Amazon ECR repository <br>&emsp; + Cấu hình IAM Role, Policy, OIDC Provider <br>&emsp; + Cấu hình GitHub Repository Variables <br>&emsp; + Chạy workflow build và push Docker image <br>&emsp; + Triển khai lên Amazon ECS Express Mode | 04/06/2026 | 04/06/2026 | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/> |
| Thứ 6 | - Viết bài chia sẻ về triển khai tự động với GitHub Actions cho Amazon ECS Express Mode: <br>&emsp; + Tóm tắt nội dung bài AWS Blog <br>&emsp; + Hệ thống quy trình CI/CD và phân tích vai trò các thành phần <br>&emsp; + Tổng hợp các bước thực hành và lỗi phát sinh <br> - Tìm hiểu quy trình triển khai định tuyến endpoint đa Region cho Amazon Aurora DSQL: <br>&emsp; + Tìm hiểu mô hình Aurora DSQL multi-Region, Route 53 health checks, cơ chế lựa chọn endpoint, cấu hình và failover | 05/06/2026 | 05/06/2026 | <https://awsstudygroup.com/2026/03/30/trien-khai-tu-dong-voi-github-actions-cho-amazon-ecs-express-mode/><br><https://awsstudygroup.com/2026/01/09/trien-khai-dinh-tuyen-endpoint-da-region-cho-amazon-aurora-dsql/> |

### Kết quả đạt được tuần 7:

**1. CI/CD & GitHub Actions (Thứ 2)**
* Củng cố vững chắc kiến thức về CI/CD: Nắm được vai trò cốt lõi của CI/CD trong tự động hóa quy trình phát triển và triển khai phần mềm. Hiểu cách GitHub Actions sử dụng workflow để tự động thực hiện các bước build, test và deploy.
* Hiểu cấu trúc file YAML trong pipeline: Nắm rõ các thành phần chính của file workflow như `name`, `on`, `jobs`, `steps`, `uses` và `run`. Biết cách phân tích luồng hoạt động cơ bản của một pipeline.

**2. Thiết kế Cơ sở Dữ liệu Hệ thống (Thứ 3)**
* Xây dựng cấu trúc cơ sở dữ liệu cho dự án nhóm (High-Concurrency Payment Gateway): Xác định được các bảng chính như người dùng, khách hàng, tài khoản, giao dịch, thông báo và nhật ký hệ thống (audit log, outbox event).
* Thiết lập khóa chính, khóa ngoại, ràng buộc dữ liệu chặt chẽ và đánh index tối ưu hóa truy vấn cho hệ thống giao dịch tải cao.

**3. Kiến trúc Dự án Nhóm (Thứ 4)**
* Tổng hợp các dịch vụ chính trong mô hình kiến trúc: Xác định các thành phần cốt lõi của hệ thống bao gồm backend, frontend, cơ sở dữ liệu, lưu trữ, bảo mật và định tuyến.
* Hiểu sâu sắc vai trò của từng dịch vụ trên AWS, tạo cơ sở vững chắc để lựa chọn, điều chỉnh và hoàn thiện kiến trúc cho các Sprint tiếp theo.

**4. Triển khai CI/CD với Amazon ECS Express Mode (Thứ 5)**
* Triển khai thành công pipeline CI/CD tự động bằng GitHub Actions: Workflow tự động thực hiện các bước build Docker image, tag image theo commit, push lên Amazon ECR và triển khai service lên Amazon ECS Express Mode.
* Kiểm chứng luồng triển khai thành công thông qua log workflow.
![GitHub Actions Workflow](/images/77.png)
* Cấu hình cơ chế xác thực an toàn bằng IAM Role và OIDC: Tạo IAM Role `github-actions-ecs-role` để GitHub Actions assume role. Sử dụng OIDC Provider để hạn chế lưu trữ AWS Access Key dài hạn, tăng cường bảo mật tuyệt đối cho pipeline.
![IAM OIDC Role](/images/78.png)
* Triển khai container lên Amazon ECS Express Mode: ECS tạo service, task và endpoint chạy ứng dụng thành công. Docker image được quản lý chuẩn xác trên ECR.
![Amazon ECS Express Service](/images/79.png)

**5. Kiến thức Mở rộng & Cộng đồng (Thứ 6)**
* Viết bài chia sẻ kỹ thuật: Tổng hợp các bước triển khai tự động với GitHub Actions, phân tích vai trò của Docker, ECR, ECS Express Mode và OIDC. Biên soạn bài viết chất lượng chia sẻ lên cộng đồng, đúc kết các lỗi thường gặp và cách xử lý.
* Định tuyến endpoint đa Region với Amazon Aurora DSQL: Hiểu mô hình kiến trúc multi-Region, vai trò của Route 53 health checks trong việc giám sát endpoint. Nắm bắt cơ chế lựa chọn endpoint có độ trễ thấp nhất để tối ưu kết nối và khả năng failover tự động giữa các Region.