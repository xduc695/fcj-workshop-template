---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Tự động hóa quy trình triển khai ứng dụng Container lên Amazon ECS Express Mode bằng GitHub Actions

Trong kỷ nguyên DevOps, việc tối ưu hóa pipeline CI/CD để rút ngắn thời gian đưa sản phẩm ra thị trường là ưu tiên hàng đầu. Khi ứng dụng được container hóa, quy trình đóng gói và triển khai thủ công thường dễ phát sinh lỗi và tốn thời gian. 

Giải pháp tự động hóa bằng **GitHub Actions** kết hợp với **Amazon ECS Express Mode** giúp đơn giản hóa toàn bộ hạ tầng từ mạng, tải cân bằng đến việc cấp phát tài nguyên mà không cần cấu hình thủ công. Bài viết này tổng hợp kiến trúc, quy trình vận hành và kinh nghiệm thực tế khi xây dựng pipeline CI/CD an toàn, tự động hóa hoàn toàn từ mã nguồn đến môi trường chạy live.

---

## 1. Các ưu điểm cốt lõi của giải pháp

Hệ thống được thiết kế nhằm tối ưu tốc độ triển khai và loại bỏ các rủi ro bảo mật tiềm ẩn nhờ vào các cơ chế hiện đại:

- **Xác thực an toàn qua OIDC:** Thay vì lưu trữ các thông tin xác thực tĩnh như AWS Access Key dài hạn trong GitHub Secrets (gây rủi ro lộ lọt dữ liệu), hệ thống thiết lập cơ chế tin cậy thông qua OpenID Connect (OIDC). Mỗi khi workflow chạy, GitHub Actions sẽ tự động assume một IAM role ngắn hạn để tương tác với AWS.
- **Tự động hóa hạ tầng với ECS Express Mode:** Điểm vượt trội của Express Mode là khả năng tự động thiết lập và quản lý các thành phần phức tạp bao gồm: Application Load Balancer (ALB), Target Groups, Security Groups, cơ chế Auto Scaling dựa trên CPU và cung cấp sẵn URL truy cập có chứng chỉ định danh từ AWS.
- **Quản lý phiên bản chính xác (Traceability):** Docker image khi build xong sẽ được gắn tag tự động dựa trên 7 ký tự đầu của Commit SHA. Điều này giúp đội ngũ phát triển dễ dàng truy vết mã nguồn, kiểm soát các phiên bản và thực hiện rollback (quay lui) nhanh chóng khi có sự cố.

---

## 2. Quy trình hoạt động của hệ thống

Luồng xử lý tự động hóa được kích hoạt ngay khi lập trình viên thực hiện tương tác với kho mã nguồn:

- **Giai đoạn CI (Tích hợp liên tục):** Khi code được đẩy lên nhánh `main`, GitHub Actions kích hoạt workflow. Hệ thống sử dụng OIDC để kết nối an toàn với AWS, tiến hành build Docker image từ mã nguồn, gắn tag theo Commit SHA và đẩy (push) image lên kho lưu trữ riêng tư Amazon ECR.
- **Giai đoạn CD (Triển khai liên tục):** Sau khi image được đẩy thành công, Action `amazon-ecs-deploy-express-service` sẽ gọi API của AWS để cập nhật dịch vụ. ECS Express Mode sẽ tự động khởi tạo/cập nhật cụm máy chủ, điều phối các Task chạy trên nền tảng AWS Fargate không máy chủ và định tuyến lưu lượng truy cập từ Load Balancer đến container mới một cách mượt mà.

---
![CI/CD Architecture Diagram](/images/106.png)
## 3. Lựa chọn công nghệ và vai trò hệ thống

| Thành phần hệ thống | Công nghệ sử dụng | Vai trò trong kiến trúc |
| :--- | :--- | :--- |
| **Pipeline CI/CD** | GitHub Actions | Tự động hóa toàn bộ quy trình build, tag, push và kích hoạt deploy ứng dụng |
| **Container Storage** | Amazon ECR | Lưu trữ tập trung và quản lý bảo mật các phiên bản Docker Image |
| **Container Orchestration** | Amazon ECS Express Mode | Tự động quản lý dịch vụ, cấu hình mạng và cân bằng tải cho container |
| **Serverless Compute** | AWS Fargate | Cung cấp tài nguyên tính toán để chạy container mà không cần quản lý EC2 |
| **Identity & Access** | IAM & OIDC Provider | Xác thực không mật khẩu, cấp quyền ngắn hạn theo nguyên tắc Least Privilege |

---

## 4. Lưu ý kỹ thuật khi triển khai thực tế

Qua quá trình thực hành cấu hình và tối ưu pipeline, một số điểm mấu chốt cần lưu ý để đảm bảo hệ thống vận hành ổn định:

### Cấp quyền tối thiểu cho IAM Policy
Để đảm bảo an toàn thông tin, các IAM Policy đính kèm vào `github-actions-ecs-role` cần được siết chặt. Thay vì sử dụng ký tự đại diện `*` cho tất cả tài nguyên, hãy giới hạn chính xác ARN của Amazon ECR Repository và Amazon ECS Cluster cụ thể để tránh việc một repository bị hack có thể can thiệp sang các tài nguyên khác.

![IAM OIDC Role](/images/78.png)

### Theo dõi tiến trình tự động hóa trên GitHub Actions
Khi đẩy code lên nhánh chính, toàn bộ tiến trình đóng gói từ build Dockerfile, đăng nhập ECR cho đến khi gọi lệnh deploy lên ECS Express Mode cần được giám sát chặt chẽ qua log realtime để phát hiện sớm các xung đột phụ thuộc hoặc lỗi phân quyền.

![GitHub Actions Workflow](/images/77.png)

### Kiểm tra trạng thái dịch vụ trên Amazon ECS Express Mode
Sau khi workflow báo thành công, Express Mode sẽ tự động tạo cấu hình định tuyến và cân bằng tải. Ứng dụng container chạy trên AWS Fargate lúc này có thể truy cập trực tiếp thông qua endpoint mặc định được AWS cấp sẵn.

![Amazon ECS Express Service](/images/79.png)

---

## 5. Lời kết

Việc kết hợp giữa GitHub Actions và Amazon ECS Express Mode mang lại một giải pháp CI/CD tinh gọn, mạnh mẽ và có độ an toàn cao cho các ứng dụng container hóa. Nhờ việc giải phóng gánh nặng quản lý hạ tầng mạng và máy chủ, đội ngũ phát triển có thể tập trung hoàn toàn vào việc tối ưu mã nguồn, nâng cao chất lượng sản phẩm và tăng tốc độ phát hành ứng dụng.

Bài viết gốc: https://aws.amazon.com/blogs/containers/automated-deployments-with-github-actions-for-amazon-ecs-express-mode/