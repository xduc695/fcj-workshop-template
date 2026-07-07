---
title: "Event 3"
date: 2026-06-06
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
# Bài thu hoạch “First Cloud AI Journey”

### Mục Đích Của Sự Kiện

- Trang bị kiến thức kỹ thuật chuyên sâu về kiến trúc thời gian thực và đồng bộ mạng trong phát triển ứng dụng đám mây.
- Đóng gói ứng dụng, tối ưu hóa hạ tầng DevOps và quản lý phân lớp bộ nhớ lưu trữ hiệu quả.
- Giới thiệu giải pháp trí tuệ nhân tạo nâng cao qua kiến trúc đồ thị tri thức để vượt qua các giới hạn RAG truyền thống.
- Thiết kế hệ thống an ninh mạng thông minh đa tầng, kết hợp tường lửa và mô hình học máy real-time trên AWS.
- Định hướng lộ trình phát triển sự nghiệp thực chiến từ kỹ thuật viên hỗ trợ căn bản đến chuyên gia vận hành hệ thống cao cấp.

### Danh Sách Diễn Giả

- **Nguyễn Quốc Bảo** - Trình bày chủ đề **“Multiplayer in the Cloud: Connecting Godot Clients with AWS WebSockets”**, tập trung vào kiến trúc game serverless thời gian thực qua giao thức WebSocket và AWS API Gateway.
- **Bảo Huỳnh** - Trình bày chủ đề **“Docker – A containerization technology”**, tập trung vào bản chất đóng gói container, cơ chế phân lớp dữ liệu và tối ưu hóa tài nguyên DevOps so với máy ảo (VM).
- **Diễn giả 3** - Trình bày chủ đề **“GraphRAG: Build GraphRAG applications using Amazon Bedrock and Amazon Neptune”**, tập trung vào giải pháp kết hợp Đồ thị tri thức (Knowledge Graph) và cơ sở dữ liệu Vector để tối ưu hóa context cho LLM.
- **Lê Hoàng Gia Đại** - Trình bày chủ đề **“WAF + ML for Cyber Attack Detection: Machine Learning-based Network Intrusion Detection System (NIDS) on AWS”**, tập trung vào hệ thống phát hiện xâm nhập mạng thông minh bằng mô hình LightGBM kết hợp AWS WAF.
- **Trần Trung Vinh** - Trình bày chủ đề **“From IT Helpdesk to Senior Sysadmin”**, chia sẻ về lộ trình dịch chuyển sự nghiệp thực chiến, quản trị hạ tầng On-Premise đến tư duy hiện đại Modern DevOps.

### Nội Dung Nổi Bật

#### Kiến trúc kết nối thời gian thực cho ứng dụng và trò chơi

- **Thực trạng lựa chọn**: UDP/ENet tối ưu độ trễ thấp cho FPS/Racing nhưng phức tạp logic mạng; HTTP Polling đơn giản triển khai nhưng độ trễ cao và lãng phí overhead do gửi yêu cầu liên tục.
- **Kiến trúc Serverless WebSocket**: Chọn WebSocket làm giải pháp cốt lõi cho ứng dụng tương tác theo lượt (turn-based) nhờ giao tiếp hai chiều (Full-duplex) và đảm bảo truyền tải tin cậy. 
- **Luồng API Gateway & Lambda**: Định tuyến các gói tin JSON dựa trên toán tử `$request.body.action` thành các trạng thái tách biệt: `$connect` (lưu kết nối), `$disconnect` (thông báo đối thủ và xóa hàng chờ), và `$default` (xử lý logic trò chơi).
- **Mẫu cấu hình lưu trữ**: Quản lý session và trạng thái người chơi (`waiting` hoặc `matched`) theo thời gian thực trên bảng Amazon DynamoDB qua cấu trúc PK là `connectionId`.
- **Hạn chế và Định hướng**: Xử lý tình trạng treo kết nối ngầm (*GoneException*) và tính chất không lưu trạng thái (*Stateless Lambda*). Tương lai đề xuất chuyển dịch sang cụm máy chủ chuyên dụng luôn chạy **AWS GameLift** để đồng bộ liên tục tần suất cao và mô phỏng vật lý thời gian thực.

#### Công nghệ đóng gói ứng dụng và tối ưu hóa hạ tầng với Docker

- **Tảng băng vấn đề của Máy ảo (VM)**: Mỗi VM bắt buộc chạy một OS độc lập, tiêu tốn CPU/RAM cố định, chu kỳ cập nhật OS nặng nề, không tối ưu cho kiến trúc Microservices nhỏ gọn.
- **Bản chất Docker Container**: Công nghệ đóng gói ứng dụng cùng toàn bộ thư viện phụ thuộc (*dependencies*) vào một gói duy nhất, chia sẻ chung hệ điều hành máy chủ (Host OS) giúp khởi động tức thì trong mili-giây và đạt hiệu năng tiệm cận máy thật.
- **Cơ chế cấu trúc phân lớp (Layers)**: Kế thừa và tái sử dụng bộ nhớ cache khi build thông qua tệp cấu hình Dockerfile (các lớp Base Image chỉ đọc xếp chồng lên nhau, trên cùng là một lớp `writable container layer` có quyền ghi).
- **Hệ thống lệnh Docker CLI**: Phân loại rõ ràng thành 5 nhóm tính năng cốt lõi: quản lý Image, kiểm soát vòng đời Container, tương tác gỡ lỗi hệ thống, điều phối phối hợp nhiều container (*docker-compose*) và phân vùng tài nguyên Network/Volume.

#### Khắc phục giới hạn của RAG truyền thống bằng GraphRAG

- **Giới hạn RAG truyền thống**: Tìm kiếm dựa trên độ tương đồng vector độc lập bị phân mảnh dữ liệu, hoàn toàn mất khả năng liên kết ngữ cảnh bắc cầu giữa các thực thể rời rạc nằm trong nhiều tài liệu khác nhau.
- **Cơ chế vận hành GraphRAG**: Sử dụng mô hình đồ thị tri thức bao gồm các đỉnh (Nodes) và cạnh (Edges) để ánh xạ mối quan hệ ngữ cảnh sâu sắc, giúp LLM hiểu được các thực thể có tính liên kết đa tầng trước khi đưa vào prompt điều phối.
- **Hai luồng tiếp cận triển khai**:
  - *Luồng quản lý hoàn toàn (Fully Managed Route)*: Sử dụng **Amazon Bedrock Knowledge Bases** để tự động hóa khâu cắt đoạn (*Chunk*), trích xuất thực thể, kết hợp **Amazon Neptune Analytics** để lưu trữ và tự động khám phá quan hệ ngữ cảnh đồ thị.
  - *Luồng tùy biến mã nguồn mở (Custom Route)*: Xây dựng pipeline xử lý dữ liệu qua framework **LlamaIndex** bằng mã Python, tự định nghĩa cấu trúc trích xuất và truy vấn dữ liệu đồ thị linh hoạt bằng ngôn ngữ *Cypher Query*.

#### An ninh mạng thông minh dựa trên Học máy và AWS WAF

- **Thách thức an ninh**: Lớp bảo mật dựa trên bộ quy tắc cố định (Signature-based) của tường lửa ứng dụng web truyền thống (AWS WAF) không đủ để chống lại các biến thể tấn công hiện đại hoặc lỗ hổng zero-day.
- **Hệ thống phát hiện xâm nhập mạng (NIDS)**: Triển khai NIDS đa chức năng đảm nhận đồng thời vai trò giám sát lưu lượng mạng, phân tích hành vi bất thường, phát hiện cảnh báo real-time và ghi log phản hồi.
- **Huấn luyện mô hình**: Tiền xử lý dữ liệu chuẩn hóa *CSE-CIC-IDS2018* qua các bước: Khám phá $\rightarrow$ Hợp nhất $\rightarrow$ Làm sạch dữ liệu NaN/vô hạn $\rightarrow$ Cân bằng nhãn dữ liệu (*Class balance*) để loại bỏ hiện tượng thiên vị thuật toán. Sử dụng phương pháp PCA và Elbow để xác định số cụm tối ưu.
- **Đánh giá hiệu năng thuật toán**: Thử nghiệm song song qua các mô hình (Random Forest, MLP, 1D-CNN, XGBoost). Thuật toán **LightGBM** cho kết quả tối ưu toàn diện nhất với độ chính xác đạt **95.86%** và chỉ số AUC-ROC đạt **0.9982**.
- **Kiến trúc Cloud-native hoàn chỉnh**: Luồng traffic được ALB phân phối và lọc qua AWS WAF, bản sao lưu lượng mạng trên các thực thể EC2 được trích xuất qua **Amazon Kinesis Data Firehose** lưu vào S3. Hàm Lambda kích hoạt mô hình LightGBM phân tích thời gian thực, tự động gửi cảnh báo khẩn cấp qua **Amazon SNS** và hiển thị dashboard giám sát.

#### Lộ trình dịch chuyển sự nghiệp sang Modern DevOps

- **Bệ phóng từ vị trí cơ bản**: Tích lũy tư duy xử lý sự cố dưới áp lực cao, kỹ năng giao tiếp xử lý vấn đề trực tiếp với người dùng từ vai trò IT Helpdesk để làm nền tảng cốt lõi hướng lên kỹ sư hệ thống.
- **Thực tế hạ tầng On-Premise**: Thấu hiểu độ phức tạp khi vận hành máy chủ vật lý, quản trị dòng lệnh chuyên sâu trên các bản phân phối Linux lớn (*RedHat, CentOS, Debian*), quản lý lưu trữ SAN/NAS và thiết lập tầng ảo hóa máy chủ với *VMware vSphere (ESXi)*.
- **Tiến trình 4 cấp độ tư duy DevOps**: 
  1. *On-Premise*: Quản lý thủ công phần cứng vật lý, mở rộng hạ tầng chậm và tốn kém chi phí.
  2. *Cloud Mindset*: Dịch chuyển hạ tầng lên đám mây AWS, sử dụng tài nguyên linh hoạt theo mô hình trả phí theo lượng sử dụng thực tế.
  3. *Infrastructure as Code (IaC)*: Tự động hóa hoàn toàn khâu thiết lập, cấu hình hạ tầng lặp lại thông qua mã nguồn sử dụng công cụ **Terraform**.
  4. *DevOps Culture*: Phá vỡ sự cô lập giữa team Dev và Ops thông qua luồng quy trình CI/CD, đóng gói container và tự động hóa workflows toàn diện.

### Những Gì Học Được

#### Tư Duy Hệ Thống và Phát Triển Sự Nghiệp

- **Xóa bỏ định kiến xuất phát điểm**: Điểm bắt đầu từ IT Helpdesk cơ bản không phải là rào cản, mà là môi trường rèn luyện kỹ năng xử lý sự cố thực tế tốt nhất để tích lũy tư duy phân tích nguyên nhân gốc rễ (Root Cause Analysis).
- **Làm chủ lộ trình Modern DevOps**: Xác định rõ bản đồ học tập 8 bước cốt lõi từ Linux/Networking, Git, Đám mây, Đóng gói Container, tự động hóa CI/CD, viết hạ tầng bằng code (IaC), điều phối Kubernetes cho đến trực quan hóa giám sát (Observability).
- **Hành trình vượt qua phỏng vấn tập đoàn**: Hiểu rõ rằng vũ khí cạnh tranh lớn nhất không nằm ở lý thuyết suông, mà nằm ở kinh nghiệm thực chiến bước ra từ các dự án thực tế, cách bóc tách sơ đồ kiến trúc đám mây và kỹ năng xử lý kịch bản thảm họa hệ thống.

#### Kiến Trúc Kỹ Thuật và Vận Hành

- **Mô hình kết nối thời gian thực**: Nắm bắt luồng di chuyển dữ liệu trạng thái của giao thức WebSocket, hiểu cách API Gateway điều phối workflows và push dữ liệu real-time tới nhiều ID người chơi đồng thời.
- **Tư duy đóng gói phân lớp với Docker**: Hiểu cách bóc tách một ứng dụng cồng kềnh thành các container nhẹ nhàng, làm chủ cơ chế quản lý vòng đời ứng dụng và cách tối ưu dung lượng ảnh thông qua Docker layers cache.
- **Tối ưu hóa pipeline AI nâng cao**: Tiếp cận kiến trúc GraphRAG hiện đại, biết cách phối hợp cơ sở dữ liệu đồ thị tri thức của Amazon Neptune cùng Amazon Bedrock để giải quyết triệt để bài toán mất ngữ cảnh bắc cầu của RAG truyền thống.
- **Bảo mật và Phân tích thông minh đa tầng**: Nắm vững quy trình thiết lập kiến trúc an ninh đám mây hoàn chỉnh trên AWS, cách tiền xử lý và cân bằng tập dữ liệu lớn phục vụ huấn luyện mô hình học máy real-time phát hiện xâm nhập mạng độc hại.

### Ứng Dụng Vào Công Việc

- **Ứng dụng WebSocket vào Project**: Nghiên cứu pilot chuyển đổi cơ chế cập nhật dữ liệu từ HTTP Polling truyền thống sang giao thức Serverless WebSocket sử dụng AWS API Gateway cho các module tương tác thời gian thực trong dự án hiện tại.
- **Container hóa toàn bộ ứng dụng**: Áp dụng Dockerfile tiêu chuẩn để đóng gói mã nguồn project hiện tại, tối ưu hóa các lớp layer để tăng tốc độ quy trình build/deploy hệ thống trong pipeline CI/CD.
- **Nâng cấp giải pháp AI tri thức**: Thử nghiệm tích hợp mô hình kiến trúc GraphRAG mã nguồn mở bằng framework LlamaIndex để tối ưu hóa context, tăng độ chính xác phản hồi cho module Chatbot tra cứu thông tin nội bộ của dự án.
- **Thiết lập hạ tầng bảo mật**: Thực hành pilot cấu hình Web ACLs trên AWS WAF để ngăn chặn các kỹ thuật tấn công tầng ứng dụng (SQLi, XSS, Bot) và cấu hình CloudWatch Alarm theo dõi workflows.
- **Xây dựng hệ thống Lab thực hành**: Triển khai Modern DevOps Roadmap vào workflow cá nhân, tự cấu hình các mô hình mạng VPC Peering, Transit Gateway và tự động hóa hạ tầng bằng script Terraform để tích lũy kinh nghiệm thực chiến.

### Trải Nghiệm Trong Event

Tham gia sự kiện **First Cloud AI Journey (Event 3)** là một hành trình trải nghiệm công nghệ thực chiến, mang tính bao quát và đào sâu vào những bài toán kỹ thuật hóc búa nhất của doanh nghiệp thời đại số.

#### Hàm lượng kỹ thuật thực tế và chuyên sâu
- Khác với các buổi hội thảo lý thuyết suông, sự kiện mang tới các đoạn mã nguồn GDScript, Python, tệp cấu hình Dockerfile cấu trúc phân lớp thực tế, sơ đồ kiến trúc hạ tầng đám mây dạng tảng băng trôi bóc tách từ các hệ thống vận hành thực tế.
- Được tiếp cận các biểu đồ so sánh mô hình học máy trực quan (Confusion Matrix, biểu đồ giảm chiều dữ liệu PCA), giúp người nghe thấu hiểu rõ lý do kỹ thuật đằng sau việc lựa chọn thuật toán LightGBM cho hệ thống an ninh mạng.

#### Tiếp cận sơ đồ trực quan sống động
- Người tham dự được quan sát trực tiếp giao diện quản lý Graph Explorer của Amazon Neptune, chứng kiến các thực thể dữ liệu văn bản thô được AI bóc tách và chuyển hóa thành mạng lưới các nút kết nối tri thức đồ thị vô cùng sống động.
- Sơ đồ kiến trúc Cloud-native hoàn chỉnh trên AWS chỉ ra luồng đi mạch lạc của gói tin từ khi hacker tấn công qua lớp lá chắn WAF cho đến khi hệ thống tự động đẩy cảnh báo real-time qua điện thoại của admin.

#### Truyền cảm hứng hành động và định hướng nghề nghiệp
- Phiên chia sẻ cuối cùng mang lại sự gần gũi đầy tính nhân văn, đánh trúng tâm lý hoang mang về định hướng tương lai của sinh viên công nghệ. Câu chuyện bước ra từ vị trí IT Helpdesk cơ bản của diễn giả đã thắp lên ngọn lửa dấn thân mạnh mẽ.
- Sự kết hợp hoàn hảo giữa các bài toán công nghệ xu hướng (GenAI, DevOps, Security) cùng các lời khuyên định hướng giúp tôi thay đổi hoàn toàn tư duy: không có ranh giới hay giới hạn nào cho sự phát triển, mọi kỹ sư giỏi đều được tôi luyện qua việc tự tay cấu hình và gỡ lỗi tại các phòng lab thực hành.

#### Bài học rút ra
- Kỹ năng chuyên môn vững chắc và tư duy tự động hóa workflows (Docker, IaC, CI/CD) là yếu tố sống còn để loại bỏ lỗi chủ quan của con người, đảm bảo tính nhất quán của hệ thống đám mây.
- AI không còn dừng lại ở mức công cụ hỏi đáp đơn giản; việc kết hợp AI cùng cấu trúc dữ liệu đồ thị tri thức (GraphRAG) tạo nên bước nhảy vọt về năng lực xử lý thông tin phức tạp cho doanh nghiệp.
- Điểm xuất phát của bạn trong ngành công nghệ không quyết định vị trí tương lai; chính tinh thần Builder sẵn sàng dấn thân, liên tục thực hành, gỡ lỗi thực chiến và phá vỡ vùng an toàn mới là chìa khóa mở cánh cửa trở thành một chuyên gia cao cấp.

> Tổng thể, sự kiện First Cloud AI Journey (Event 3) đã mang lại nguồn năng lượng hành động bùng nổ cùng khối lượng kiến thức thực chiến đỉnh cao. Sự kiện xác lập một triết lý phát triển toàn diện: Hãy làm chủ hạ tầng của chính mình, dũng cảm đối mặt với các thách thức an ninh mạng và liên tục nâng cấp năng lực bản thân qua từng hành động thực tế nhỏ nhất.