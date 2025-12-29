# Event Organization and Community Building Platform
## Cloud-native Solution on AWS with Microservices & AI Integration

---

Trong quá trình thực tập tại môi trường định hướng Amazon Web Services (AWS), dự án **Event Organization and Community Building Platform** được xây dựng với mục tiêu phát triển một nền tảng tổ chức sự kiện và kết nối cộng đồng hiện đại, tương tự như Luma.com, hoạt động hoàn toàn trên hạ tầng điện toán đám mây AWS.

Hệ thống cho phép người dùng tạo, quản lý và tham gia các sự kiện trực tuyến hoặc trực tiếp; quản lý cộng đồng; gửi thông báo; thống kê lượt tham gia; và tích hợp AI Chatbot nhằm hỗ trợ người dùng tra cứu thông tin sự kiện, giải đáp câu hỏi và nâng cao trải nghiệm.

Dự án được thiết kế theo kiến trúc cloud-native, đảm bảo:

- Khả năng mở rộng linh hoạt
- Tính sẵn sàng cao
- Bảo mật dữ liệu
- Tối ưu chi phí vận hành

Các dịch vụ AWS chính được sử dụng bao gồm: `Amazon S3`, `CloudFront`, `ECS`, `ALB`, `RDS`, `API Gateway`, `NAT Gateway`, `Route 53` và `CloudFormation`. Hệ thống được triển khai theo mô hình **Infrastructure as Code (IaC)** nhằm tự động hóa quá trình triển khai, dễ dàng mở rộng và bảo trì.

### Nội dung

- [01 – Mô tả vấn đề](01-Problem-Statement)
- [02 – Kiến trúc giải pháp](02-Solution-Architecture)
- [03 – Triển khai kỹ thuật](03-Technical-Implementation)
- [04 – Tiến độ & Mốc quan trọng](04-Timeline-&-Milestones)
- [05 – Ước tính ngân sách](05-Budget-Estimation)
- [06 – Đánh giá rủi ro](06-Risk-Assessment)
- [07 – Kết quả kỳ vọng](07-Expected-Outcomes)

---
# 1. Mô tả vấn đề
## 1. Mô tả vấn đề

### 1.1 Hiện trạng

Nhu cầu tổ chức sự kiện và xây dựng cộng đồng trực tuyến ngày càng gia tăng. Tuy nhiên, nhiều nền tảng hiện nay:

**Về phía ứng dụng**, các hệ thống hiện có thường:

- Khó mở rộng khi số lượng người dùng tăng cao, đặc biệt trong các giai đoạn cao điểm của sự kiện.
- Phát sinh chi phí vận hành lớn do hạ tầng thiếu tối ưu.
- Chưa đáp ứng tốt nhu cầu cá nhân hóa trải nghiệm người dùng.
- Thiếu sự tích hợp của các công nghệ AI nhằm hỗ trợ và tương tác với người dùng một cách thông minh.

**Ở khía cạnh người dùng**, nhu cầu thực tế ngày càng đa dạng:

- Người dùng có nhu cầu đăng tải, quảng bá và tổ chức sự kiện, nhưng thiếu một nền tảng tập trung với lượng người dùng đủ lớn để tiếp cận hiệu quả.
- Người tham gia gặp khó khăn trong việc tìm kiếm thông tin sự kiện phù hợp do giao diện phức tạp hoặc khả năng lọc và tìm kiếm còn hạn chế.
- Việc thiếu công cụ hỗ trợ thông minh khiến quá trình tra cứu thông tin mất nhiều thời gian, làm giảm trải nghiệm tổng thể.

Do đó, việc xây dựng một nền tảng có giao diện thân thiện, khả năng tìm kiếm nhanh chóng cùng với AI chatbot hỗ trợ chính xác và kịp thời là một yêu cầu cấp thiết trong bối cảnh hiện nay.

---

### 1.2. Các thách thức chính

Trong quá trình xây dựng và vận hành nền tảng tổ chức sự kiện và xây dựng cộng đồng trực tuyến, hệ thống phải đối mặt với nhiều thách thức quan trọng:

- **Quản lý lưu lượng truy cập lớn** trong thời gian diễn ra sự kiện, đặc biệt khi số lượng người tham gia tăng đột biến trong thời gian ngắn  
- **Đảm bảo hệ thống hoạt động ổn định và liên tục**, hạn chế tối đa tình trạng gián đoạn dịch vụ  
- **Bảo mật dữ liệu người dùng**, bao gồm thông tin cá nhân, dữ liệu sự kiện và lịch sử tương tác  
- **Tối ưu chi phí hạ tầng**, cân bằng giữa hiệu năng hệ thống và ngân sách vận hành  
- **Tăng cường mức độ tương tác của người dùng** thông qua việc tích hợp AI chatbot nhằm hỗ trợ tìm kiếm thông tin, tư vấn và giải đáp nhanh chóng  

---

### 1.3. Tác động đến các bên liên quan

Những hạn chế của các nền tảng hiện tại ảnh hưởng trực tiếp đến nhiều đối tượng liên quan:

- **Người tổ chức sự kiện**: Gặp khó khăn trong việc quản lý, quảng bá và theo dõi hiệu quả sự kiện, làm giảm chất lượng tổ chức  
- **Người tham gia**: Trải nghiệm không đồng nhất, khó tiếp cận thông tin sự kiện phù hợp và dễ bị gián đoạn trong quá trình sử dụng  
- **Doanh nghiệp**: Mất cơ hội mở rộng thị trường, hạn chế khả năng thu hút người dùng mới và giảm tiềm năng tăng trưởng  

---

### 1.4. Hệ quả đối với hoạt động kinh doanh

Nếu không có giải pháp phù hợp và kịp thời, các vấn đề nêu trên có thể dẫn đến nhiều hệ quả tiêu cực:

- Khó khăn trong việc **mở rộng quy mô và phát triển thị trường**  
- **Giảm mức độ hài lòng và lòng trung thành của người dùng**, ảnh hưởng trực tiếp đến uy tín thương hiệu  
- **Gia tăng chi phí vận hành** do hệ thống kém hiệu quả và thiếu khả năng tự động mở rộng  

Vì vậy, việc xây dựng một nền tảng hiện đại, ổn định, bảo mật và có khả năng mở rộng cao là yêu cầu thiết yếu để đảm bảo sự phát triển bền vững của doanh nghiệp trong môi trường số.

---

## 2. Kiến trúc giải pháp

### 2.1. Tổng quan kiến trúc

Hệ thống được thiết kế theo mô hình Cloud-native trên nền tảng AWS, áp dụng kiến trúc microservices và container hóa bằng Docker. Toàn bộ quy trình từ phát triển, triển khai đến vận hành được tự động hóa thông qua CI/CD pipeline.

Luồng hoạt động chính của hệ thống bao gồm:
- Luồng CI/CD: Source code được quản lý trên GitHub, sử dụng GitHub Actions để build ứng dụng, đóng gói Docker Image và đẩy lên Amazon ECR/Docker Hub, sau đó cập nhật ECS Task Definition.
- Luồng người dùng: Người dùng truy cập hệ thống thông qua Route 53, nội dung tĩnh được phân phối bằng CloudFront và S3, các request API được xử lý thông qua API Gateway và Application Load Balancer.
- Luồng xử lý backend: Các container backend chạy trong Amazon ECS (private subnet), kết nối với cơ sở dữ liệu Amazon RDS và được giám sát bằng CloudWatch.

Kiến trúc đảm bảo tính sẵn sàng cao, bảo mật, dễ mở rộng và phù hợp cho các hệ thống hiện đại.

![Solution-Architecture](/images/FirstCloudJourney/02-Solution-Architecture/Solution-Architecture.jpg)

---

### 2.2. Các dịch vụ AWS sử dụng

Các dịch vụ AWS chính được sử dụng trong hệ thống bao gồm:
- Amazon Route 53: Quản lý DNS và định tuyến người dùng.
- Amazon CloudFront: Phân phối nội dung (CDN) cho frontend.
- Amazon S3: Lưu trữ website tĩnh và tài nguyên frontend.
- Amazon API Gateway: Tiếp nhận và điều phối các request API.
- Application Load Balancer (ALB): Cân bằng tải cho các ECS Task.
- Amazon ECS (Elastic Container Service): Chạy các container backend.
- Amazon ECR / Docker Hub: Lưu trữ Docker Image.
- Amazon RDS: Cơ sở dữ liệu cho hệ thống.
- Amazon VPC: Thiết lập mạng riêng ảo.
- NAT Gateway và Internet Gateway: Quản lý kết nối Internet.
- Application Auto Scaling: Tự động mở rộng ECS Service.
- Amazon CloudWatch: Giám sát, logging và cảnh báo.
- GitHub Actions: Triển khai CI/CD.

---

### 2.3. Thiết kế các thành phần hệ thống

#### 2.3.1 CI/CD Pipeline

Source code được lưu trữ trên GitHub. GitHub Actions tự động thực hiện các bước:
1. Build ứng dụng.
2. Build Docker Image.
3. Push image lên Amazon ECR/Docker Hub.
4. Cập nhật ECS Task Definition và triển khai phiên bản mới.

#### 2.3.2 Frontend

Frontend được triển khai dưới dạng static website trên Amazon S3 và phân phối thông qua CloudFront nhằm giảm độ trễ và tăng hiệu năng.

#### 2.3.3 Backend

Backend được triển khai dưới dạng container trong Amazon ECS, chạy ở private subnet và chỉ nhận traffic từ Application Load Balancer.

#### 2.3.4 Database

Amazon RDS được triển khai trong private subnet, chỉ cho phép ECS Service truy cập thông qua Security Group.

---

### 2.4. Kiến trúc bảo mật

Hệ thống áp dụng nhiều lớp bảo mật:
- Phân tách public subnet và private subnet.
- ECS và RDS không có public IP.
- Security Group giới hạn luồng truy cập giữa các thành phần.
- IAM Role được sử dụng để phân quyền tối thiểu cho ECS và GitHub Actions.
- CloudFront giúp hạn chế truy cập trực tiếp vào S3.

---

### 2.5. Thiết kế khả năng mở rộng

Hệ thống hỗ trợ mở rộng linh hoạt:
- ECS Service tự động scale dựa trên CPU và Memory.
- ALB phân phối đều lưu lượng truy cập.
- Kiến trúc hỗ trợ triển khai đa Availability Zone.
- CI/CD cho phép triển khai nhanh và giảm downtime.

---

# 3. Triển khai kỹ thuật
### 3.1. Các giai đoạn triển khai

Quá trình triển khai hệ thống được chia thành các giai đoạn rõ ràng nhằm đảm bảo tính đồng bộ và giảm rủi ro trong quá trình phát triển:

#### Giai đoạn 1: Phát triển cục bộ
- Hệ thống gồm 4 microservices:
  - User + Page Service
  - AI Chat Service
  - Notification Service
  - Event Service
- Phân công nhân sự:
  - 01 thành viên phát triển User Service
  - 01 thành viên phát triển Page Service và AI Chat Service
  - 01 thành viên phát triển Notification Service và Event Service
- Toàn bộ các service được phát triển và chạy độc lập trên môi trường local của từng thành viên.
- Các thành viên thực hiện demo chéo để kiểm tra logic và luồng xử lý.

#### Giai đoạn 2: Tích hợp hệ thống
- Sau khi hoàn thành từng service, source code được gom về một máy để:
  - Chạy đồng thời toàn bộ backend services.
  - Kết nối với frontend dùng chung.
  - Kiểm thử luồng nghiệp vụ tổng thể trên môi trường local.

#### Giai đoạn 3: Triển khai thủ công lên AWS
- Các service backend được đóng gói bằng Docker.
- Triển khai thủ công lên AWS (ECS, RDS, ALB).
- Cấu hình mạng, environment variables và security group.
- Kiểm thử hệ thống trên môi trường cloud.

#### Giai đoạn 4: Tự động hóa triển khai
- Sử dụng AWS CloudFormation để mô tả hạ tầng dưới dạng mã (Infrastructure as Code).
- Chuẩn hóa quá trình deploy.
- Giảm lỗi cấu hình thủ công và tăng khả năng tái sử dụng.

---

### 3.2. Yêu cầu kỹ thuật

- Ngôn ngữ & Framework:
  - Backend: Java Spring Boot (microservices)
  - Frontend: ReactJS (dùng chung cho toàn hệ thống)
- Công nghệ:
  - Docker & Docker Compose
  - RESTful API
- Hạ tầng:
  - AWS ECS, ECR, RDS, ALB, VPC
  - CloudFormation
- Công cụ hỗ trợ:
  - Git & GitHub
  - GitHub Actions (CI/CD)
- Môi trường:
  - Local development
  - AWS Cloud environment

---

### 3.3. Phương pháp phát triển

Hệ thống được phát triển theo phương pháp:
- **Microservices Architecture**: Mỗi service đảm nhiệm một nghiệp vụ riêng biệt.
- **Phát triển song song**: Các thành viên làm việc độc lập trên từng service.
- **Incremental Development**: Hoàn thiện từng chức năng nhỏ và kiểm thử liên tục.
- **DevOps-oriented**: Kết hợp phát triển và triển khai tự động.

Frontend được phát triển chung, kết nối đến các backend service thông qua API Gateway / Load Balancer.

---

### 3.4. Chiến lược kiểm thử

Chiến lược kiểm thử được áp dụng theo nhiều mức:

- **Unit Test**:
  - Kiểm thử các hàm xử lý nghiệp vụ trong từng service.
- **Integration Test**:
  - Kiểm tra giao tiếp giữa các service và frontend.
- **Manual Test**:
  - Test trực tiếp trên môi trường local và cloud.
- **Deployment Test**:
  - Kiểm tra service sau khi deploy lên AWS.
- **Monitoring**:
  - Theo dõi log và trạng thái service bằng CloudWatch.

---

### 3.5. Kế hoạch triển khai

Kế hoạch triển khai được thực hiện theo hai bước:

#### Triển khai thủ công
- Build Docker Image tại local.
- Push image lên Amazon ECR.
- Tạo ECS Task Definition và ECS Service thủ công.
- Kiểm tra hệ thống hoạt động ổn định.

#### Triển khai tự động
- Sử dụng CloudFormation để khởi tạo hạ tầng.
- Kết hợp CI/CD pipeline để:
  - Build và push image tự động.
  - Cập nhật ECS Service khi có thay đổi code.
- Đảm bảo triển khai nhanh, nhất quán và dễ rollback.

---

# 4. Tiến độ & Cột mốc

## Project Timeline

- Tuần 1–2: Phân tích & thiết kế  
- Tuần 3–4: Hạ tầng AWS  
- Tuần 5–6: Backend & Frontend  
- Tuần 7: AI Chatbot  
- Tuần 8: Kiểm thử & hoàn thiện  

## Key Milestones

- Hoàn thành kiến trúc  
- Deploy hạ tầng AWS  
- Hoàn thiện chức năng chính  
- Tích hợp AI Chatbot  
- Nghiệm thu hệ thống  

## Dependencies

- Hạ tầng AWS  
- Phối hợp nhóm  
- Thời gian tích hợp AI  

## Resource Allocation

- Kiến trúc sư & phân tích  
- DevOps & Cloud Engineer  
- Backend & Frontend Developer  
- Tester  

---

# 5. Budget Estimation

## Infrastructure Costs

- Compute & Container: ~105 USD/tháng  
- Network & API: ~165 USD/tháng  
- Storage & Database: ~57 USD/tháng  
- Monitoring: ~10 USD/tháng  

**Tổng:** ~337 USD/tháng  

## Development Costs

- 3 sinh viên  
- 2–3 tháng  
- Công cụ mã nguồn mở  
- Chi phí trực tiếp gần như 0  

## Operational Costs

- CI/CD & Auto Scaling  
- Không cần DevOps riêng  
- Chi phí thấp  

## ROI Analysis

- Hiệu năng cao  
- Khả năng mở rộng tốt  
- Giá trị học tập rất cao  

---

# 6. Risk Assessment

## Risk Matrix

| ID | Risk | Impact | Level |
|----|------|--------|-------|
| R1 | System overload | High | High |
| R2 | Deploy error | Medium | Medium |
| R3 | DB connection loss | High | Medium |
| R4 | Security attack | High | Medium |
| R5 | Network misconfig | Medium | Low |
| R6 | AWS service issue | Medium | Low |

## Mitigation Strategies

- Auto Scaling & CloudFront  
- Chuẩn hóa CI/CD  
- Security Group & IAM  
- Infrastructure as Code  

## Contingency Plans

- ECS Task restart  
- RDS snapshot backup  
- Rollback Task Definition  
- S3 + CloudFront fallback  

---

# 7. Expected Outcomes

## Success Metrics

- API response < 300ms  
- ~1M request/day  
- Uptime ≥ 99%  

## Business Benefits

- Giảm chi phí vận hành  
- Dễ mở rộng  
- Trải nghiệm người dùng tốt hơn  

## Technical Improvements

- Microservices  
- Docker & CI/CD  
- Cloud-native security  
- Real-time monitoring  

## Long-term Value

- Nền tảng mở rộng production  
- Dễ tích hợp AI & analytics  
- Giá trị học tập và tái sử dụng cao  

---

## Phụ lục

### Thông số kỹ thuật
- Java Spring Boot, ReactJS  
- Docker, ECS, RDS, ALB  

### Tính toán chi phí
- Ước tính theo 1M request/ngày  

### Sơ đồ kiến trúc
- Solution Architecture Diagram  

### Tài liệu tham khảo
- AWS Documentation  
- Cloud-native Architecture Best Practices  