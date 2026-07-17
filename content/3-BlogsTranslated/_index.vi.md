---
title: "Các bài blogs đã viết"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

###  [Blog 1 - Tự động hóa quy trình triển khai ứng dụng Container lên Amazon ECS Express Mode bằng GitHub Actions](3.1-Blog1/)
Bài viết này hướng dẫn cách xây dựng pipeline CI/CD hoàn toàn tự động và an toàn từ mã nguồn GitHub đến môi trường live trên AWS. Bạn sẽ tìm hiểu các ưu điểm cốt lõi như xác thực không mật khẩu qua OIDC, tự động hóa hạ tầng (ALB, Auto Scaling) nhờ ECS Express Mode, và cách quản lý phiên bản chính xác bằng Commit SHA nhằm tối ưu quy trình DevOps. Đồng thời, bài viết cũng chia sẻ các lưu ý thực tế về việc siết chặt phân quyền IAM Policy và cách giám sát log realtime của workflow để phát hiện sớm các lỗi xung đột.

###  [Blog 2 - Tối ưu quy trình Disaster Recovery cho Stateful Services trên Amazon EKS bằng Velero](3.2-Blog2/)
Blog này chia sẻ giải pháp sao lưu và phục hồi thảm họa (Disaster Recovery) toàn diện cho các ứng dụng có trạng thái (Stateful) chạy trên cụm Amazon EKS sử dụng công cụ mã nguồn mở Velero. Bài viết đi sâu vào kiến trúc xử lý song song (sao lưu cấu hình logic lên Amazon S3 và chụp ảnh đĩa vật lý EBS Snapshots), cơ chế xác thực an toàn với EKS Pod Identity, cùng tính năng khôi phục linh hoạt chéo Namespace. Bên cạnh đó, tác giả còn đúc kết các kinh nghiệm xử lý lỗi cú pháp trên môi trường Windows CMD và khắc phục tình trạng Pod bị kẹt ở trạng thái Pending khi lập lịch.

###  [Blog 3 - Bứt phá giới hạn 90 ngày của EC2 Capacity Manager với Amazon Athena](3.3-Blog3/)
Bài viết tập trung vào bài toán tối ưu chi phí hạ tầng (FinOps) quy mô lớn trên AWS bằng cách vượt qua giới hạn lưu trữ dữ liệu lịch sử 90 ngày của EC2 Capacity Manager. Bạn sẽ nắm được quy trình tự động đóng gói dữ liệu sang định dạng Parquet lưu trữ dài hạn trên Amazon S3 và tối ưu truy vấn bằng cơ chế Partition Projection trên Amazon Athena mà không cần quét thủ công. Đặc biệt, bài viết cung cấp 3 kịch bản SQL thực tế giúp doanh nghiệp dễ dàng săn tìm các gói tài nguyên ODCR lãng phí, nhận diện quy luật tải đỉnh và chủ động chia sẻ dung lượng trống nội bộ.