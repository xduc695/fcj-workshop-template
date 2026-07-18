---
title: "Worklog Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Mục tiêu tuần 12:

* Biên soạn và hoàn thiện Bản đề xuất dự án (Proposal) với sơ đồ kiến trúc 3 lớp bảo mật và bảng dự toán chi phí vận hành trên AWS Cloud.
* Thực hiện tự đánh giá năng lực cá nhân (Self-Evaluation) sau 12 tuần thực tập, nhìn nhận khách quan các kỹ năng đạt được và định hướng cải thiện.
* Viết báo cáo chia sẻ và đóng góp ý kiến (Feedback) nhằm cải thiện chất lượng chương trình thực tập.
* Tổng kiểm tra, rà soát lỗi và đóng gói toàn bộ hệ thống tài liệu báo cáo thực tập cuối khóa trên GitHub Repository.

### Các công việc cần triển khai trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| Thứ 2 | - Hoàn thiện tài liệu Bản đề xuất dự án (Proposal):<br> - **Thực hành:** <br>&emsp; + Viết lại toàn bộ Bản đề xuất (Proposal).<br>&emsp; + Tích hợp sơ đồ kiến trúc khối tĩnh bằng Mermaid (3 lớp bảo mật).<br>&emsp; + Xây dựng bảng tính toán chi phí vận hành chi tiết bằng AWS Pricing Calculator. | 06/07/2026 | 06/07/2026 | [Bản đề xuất](file:///D:/aws/fcj-workshop-template/content/2-Proposal/_index.vi.md) |
| Thứ 3 | - Biên soạn báo cáo Tự đánh giá (Self-Evaluation):<br> - **Thực hành:** <br>&emsp; + Tổng hợp các kỹ năng chuyên môn (Hard skills) và kỹ năng mềm (Soft skills).<br>&emsp; + Đánh giá khách quan mức độ hoàn thành (Khá, Tốt, Trung bình).<br>&emsp; + Phân tích sâu các điểm cần cải thiện (Quản lý thời gian, tối ưu code). | 07/07/2026 | 07/07/2026 | [Tự đánh giá](file:///D:/aws/fcj-workshop-template/content/3-SelfEvaluation/_index.vi.md) |
| Thứ 4 | - Biên soạn báo cáo Chia sẻ, đóng góp ý kiến (Feedback):<br> - **Thực hành:** <br>&emsp; + Viết đánh giá về lộ trình 12 tuần thực tập kiến trúc AWS Microservices.<br>&emsp; + Đề xuất cải thiện tài liệu và quy trình hỗ trợ sinh viên.<br>&emsp; + Biên dịch song ngữ Anh - Việt cho phần chia sẻ. | 08/07/2026 | 08/07/2026 | [Feedback](file:///D:/aws/fcj-workshop-template/content/7-Feedback/_index.vi.md) |
| Thứ 5 | - Rà soát và tổng hợp toàn bộ Repository tài liệu:<br> - **Thực hành:** <br>&emsp; + Khớp nối lại toàn bộ timeline từ Tuần 1 đến Tuần 11.<br>&emsp; + Kiểm tra hiển thị hình ảnh, định dạng Markdown, cấu trúc thẻ Shortcodes Hugo.<br>&emsp; + Xóa bỏ các hình ảnh Workshop cũ, cập nhật hình ảnh đúng ngữ cảnh hệ thống. | 09/07/2026 | 09/07/2026 | |
| Thứ 6 | - Đóng gói hệ thống Báo cáo thực tập cuối khóa:<br> - **Thực hành:** <br>&emsp; + Sửa lỗi chính tả, chuẩn hóa văn phong kỹ thuật (Technical Writing).<br>&emsp; + Chạy lệnh build kiểm thử Hugo server local.<br>&emsp; + Commit và Push toàn bộ source code lên GitHub, chuẩn bị nghiệm thu. | 10/07/2026 | 10/07/2026 | |

### Kết quả đạt được tuần 12:

**1. Hoàn thiện Bản đề xuất dự án Proposal (Thứ 2)**
* Viết mới hoàn toàn trang chủ Bản đề xuất (Proposal) tích hợp sơ đồ kiến trúc Mermaid trực quan. Kiến trúc thể hiện rõ 3 phân vùng bảo mật: Public Subnet (ALB, Bastion), Private Subnet (ECS Fargate), và Secure Subnet (RDS).
* Trình bày bảng dự toán chi phí vận hành chi tiết bám sát nhu cầu thực tế (~100 USD/tháng), giúp báo cáo mang tính khả thi cao.

**2. Báo cáo Tự đánh giá Năng lực (Thứ 3)**
* Phân bổ tỷ lệ đánh giá khách quan và trung thực: Các mục đạt mức Khá chiếm đa số, Trung bình và Tốt ngang nhau.
* Nhìn nhận trực diện các điểm cần cải thiện, đặc biệt là kỹ năng quản trị thời gian khi triển khai các dịch vụ AWS phức tạp và tư duy Clean Code trong dự án quy mô lớn.

**3. Báo cáo Chia sẻ, Đóng góp ý kiến (Thứ 4)**
* Hoàn thiện phân hệ `7-Feedback` cả bản Tiếng Việt và Tiếng Anh.
* Đúc kết lại toàn bộ giá trị nhận được từ chương trình: sự thay đổi về tư duy thiết kế hệ thống, khả năng tự học DevOps, và làm chủ AWS Cloud.

**4. Tổng kiểm tra Hệ thống Repository (Thứ 5)**
* Đã cấu trúc, sắp xếp và chuẩn hóa lại toàn bộ lịch trình 12 tuần theo đúng mốc thời gian thực tế, không có sự chồng chéo.
* Rà soát thành công 100% các file ảnh, gỡ bỏ các hình ảnh tồn đọng từ các workshop cũ (các file mã `h*`) và tối ưu hóa thư mục tài nguyên.

**5. Đóng gói Báo cáo Cuối khóa (Thứ 6)**
* Chuẩn hóa xong văn phong kỹ thuật Tiếng Anh và Tiếng Việt đồng bộ 1:1 trên toàn bộ các Modules (Worklog, Blogs, Events, Proposal).
* Hệ thống biên dịch Hugo build thành công không có lỗi, giao diện website báo cáo trực quan, khoa học, sẵn sàng bàn giao nghiệm thu đồ án thực tập.
