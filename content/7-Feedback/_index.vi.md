---
title: "Chia sẻ, đóng góp ý kiến"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

> Dưới đây là những chia sẻ và đóng góp ý kiến chân thành của tôi sau chuỗi 12 tuần gắn bó với chương trình First Cloud AI Journey (FCAJ). Quá trình hoàn thành dự án High-Concurrency Payment Gateway, các Workshop và bài Blog đã để lại cho tôi nhiều trải nghiệm quý giá.

### Đánh giá chung

**1. Môi trường làm việc và học tập**  
Môi trường cộng đồng FCAJ mang tính thực chiến cực kỳ cao (hands-on). Khác với các khóa học lý thuyết truyền thống, việc phải tự tay cấu hình từ VPC, EC2, ALB đến ECS Fargate và RDS giúp tôi cảm nhận rõ áp lực và trách nhiệm của một kỹ sư Cloud thực thụ. Không gian hỏi đáp trên nhóm Discord/Slack luôn sôi nổi, giúp giải quyết các lỗi hóc búa (như sập server do load testing bằng k6) một cách nhanh chóng.

**2. Sự hỗ trợ của Mentor / Ban tổ chức**  
Tôi vô cùng ấn tượng với triết lý "Không làm thay, chỉ chỉ hướng" của các mentor. Khi tôi gặp lỗi về phân quyền IAM Policy cho bucket S3 KMS, mentor không gửi file JSON đáp án mà chỉ đưa tài liệu và từ khóa để tôi tự debug. Điều này ban đầu khá "ức chế" nhưng lại chính là cách tốt nhất để rèn luyện tư duy tự giải quyết vấn đề (Root Cause Analysis). 

**3. Sự phù hợp giữa chương trình và thực tế doanh nghiệp**  
Chương trình bám sát 100% nhu cầu của doanh nghiệp hiện đại. Những kiến thức như triển khai kiến trúc Serverless (Lambda, API Gateway), tối ưu chi phí (FinOps), và đặc biệt là hệ thống chịu tải cao với Redis (Rate Limiting, Idempotency) là những "vũ khí" cực kỳ giá trị mà trường đại học hiếm khi dạy sâu. Khối lượng kiến thức hoàn toàn vượt ngoài mong đợi ban đầu của tôi.

**4. Cơ hội học hỏi & phát triển kỹ năng**  
Ngoài kỹ năng cấu hình AWS, tôi còn được rèn luyện rất nhiều "kỹ năng mềm của dân kỹ thuật". Đó là việc tham gia dịch các bài Blog chuyên sâu về GraphRAG, NIDS; viết Proposal ngân sách rõ ràng mạch lạc; và viết tài liệu Workshop (Documenting) sao cho người đi sau có thể dễ dàng làm theo. Các sự kiện FCJ Community Day (Event 1, 2, 3) cũng truyền cảm hứng mạnh mẽ về lộ trình vươn lên thành chuyên gia DevOps và cách bẻ gãy sự trì hoãn tâm lý.

**5. Văn hóa & tinh thần Builder**  
Tinh thần "Go Build" và "Fail Fast, Learn Faster" thấm nhuần trong suốt 12 tuần. Mọi người đều chia sẻ tinh thần không ngại mắc lỗi, sẵn sàng xé nháp cấu hình lại hệ thống khi bị sập. Việc chia sẻ kiến thức (knowledge sharing) được đề cao, minh chứng qua việc mọi người đều public Worklog để chéo học hỏi lẫn nhau.

### Một số câu hỏi khác

- **Điều bạn hài lòng nhất?**  
Sự thay đổi về tư duy. Tôi không còn code theo cảm tính ("vibe code") mà đã biết tư duy theo chuẩn kiến trúc, nghĩ đến bảo mật (Private Subnet), hiệu năng (Caching), và chi phí trước khi bắt tay vào làm.
- **Điều bạn nghĩ cộng đồng cần cải thiện?**  
  Mặc dù tài liệu hướng dẫn rất chi tiết, nhưng đối với các bạn mới bắt đầu làm quen với AWS, việc cấu hình CLI hay xử lý lỗi phân quyền có thể hơi khó khăn. Cộng đồng có thể bổ sung thêm các bài viết hướng dẫn xử lý một số lỗi thường gặp (troubleshooting guide) và cung cấp thêm tài liệu tham khảo sâu hơn để giúp các bạn thực tập sinh dễ dàng vượt qua các rào cản kỹ thuật ban đầu.
- **Có khuyên bạn bè tham gia không?**  
Chắc chắn 100%. Đây không phải là một chương trình "cưỡi ngựa xem hoa". Những ai thực sự muốn chịu "khổ luyện" để trưởng thành và có một portfolio (bộ Workshop + Proposal) cực kỳ nặng ký đi xin việc thì nhất định phải tham gia FCJ.

### Đề xuất & mong muốn
- **Đề xuất cải thiện:** Tổ chức thêm các buổi chia sẻ ngắn (Showcase hoặc các buổi thảo luận nhóm nhỏ) định kỳ. Đây sẽ là cơ hội rất tốt để các bạn thực tập sinh trao đổi về cách vượt qua khó khăn khi deploy, chia sẻ mẹo gỡ lỗi và cùng nhau học hỏi để cải thiện kỹ năng của mình tốt hơn.
- **Định hướng tương lai:** Tôi dự định sẽ tiếp tục tự học và nâng cấp hệ thống hiện tại của mình lên mức độ cao hơn (như thử sức tự động hóa hạ tầng). Đồng thời, tôi sẽ cố gắng trau dồi các kỹ năng chuyên môn còn thiếu và tích lũy thêm kinh nghiệm thực tế để chuẩn bị sẵn sàng cho các cơ hội nghề nghiệp sắp tới trong lĩnh vực Cloud và DevOps.