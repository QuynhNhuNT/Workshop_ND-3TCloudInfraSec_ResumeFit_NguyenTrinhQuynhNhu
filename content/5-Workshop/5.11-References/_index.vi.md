---
title: "Tài liệu tham khảo (References)"
date: 2026-07-20
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

# 5.11. Tài liệu tham khảo (References)

## 1. Source code and demo

*   **Link demo Resume Fit:** [http://resumematching-alb-1223673352.us-east-1.elb.amazonaws.com](http://resumematching-alb-1223673352.us-east-1.elb.amazonaws.com)
*   **Link source code Resume Fit:** [https://github.com/thuanthien-tran/resume-fit](https://github.com/thuanthien-tran/resume-fit)

## 2. AWS services used by the project

Dự án sử dụng một tập hợp các dịch vụ của AWS để xây dựng kiến trúc microservices và triển khai ứng dụng Resume Fit một cách an toàn, có khả năng mở rộng:
*   **Networking:** Amazon VPC, Internet Gateway, NAT Gateway (cung cấp kết nối internet một chiều cho các subnet riêng tư).
*   **Compute:** Amazon EC2 (t3.micro) dùng làm máy chủ backend xử lý tác vụ, Auto Scaling Group kết hợp Launch Template đảm bảo hệ thống tự động mở rộng theo lưu lượng.
*   **Load Balancing:** Application Load Balancer (ALB) dùng để phân phối lưu lượng truy cập từ người dùng đến các EC2 instances.
*   **Database:** Amazon RDS PostgreSQL (Single-AZ) lưu trữ dữ liệu ứng viên và cấu hình hệ thống.
*   **Storage & Messaging:** Amazon S3 (lưu trữ file CV/PDF) và Amazon SQS (xử lý hàng đợi bất đồng bộ cho các tác vụ AI phân tích CV).
*   **Security & Monitoring:** AWS Secrets Manager để bảo mật thông tin nhạy cảm (DB credentials, API keys) và Amazon CloudWatch để thu thập log, theo dõi metrics.

## 3. Cost Breakdown

Dưới đây là bảng phân tích chi phí dự tính hàng tháng khi vận hành kiến trúc hệ thống 24/7 (730 giờ/tháng) tại khu vực **US East (N. Virginia) – us-east-1**. Tất cả tính toán dựa trên mức giá On-Demand của AWS Pricing Calculator.

| STT | AWS Service | Configuration | Quantity | Estimated Monthly Cost (USD) | Notes | Total (USD) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Amazon VPC | Public/Private Subnets, Route Tables | 1 | 0.00 | Dịch vụ cơ bản không tính phí | 0.00 |
| 2 | Internet Gateway | Kết nối mạng công cộng | 1 | 0.00 | Không tính phí khởi tạo | 0.00 |
| 3 | NAT Gateway | 730 giờ ($0.045/giờ) | 2 | 32.85 | Không tính Data Processing fee | 65.70 |
| 4 | Security Group | Tường lửa ảo | - | 0.00 | Dịch vụ miễn phí | 0.00 |
| 5 | Amazon EC2 | t3.micro Linux ($0.0104/giờ) | 3 | 7.59 | 1 Backend + 2 ASG | 22.77 |
| 6 | Amazon EBS | gp3, 30GB/instance ($0.08/GB) | 3 | 2.40 | Gắn kèm EC2 instances | 7.20 |
| 7 | Launch Template & ASG | Cấu hình Auto Scaling | 1 | 0.00 | Không tính phí dịch vụ điều phối | 0.00 |
| 8 | Application Load Balancer | Base price ($0.0225/giờ) | 1 | 16.43 | Chưa bao gồm phí LCU | 16.43 |
| 9 | Target Group | Phân phối cho ALB | 1 | 0.00 | Dịch vụ miễn phí | 0.00 |
| 10 | Amazon RDS | db.t3.micro Single-AZ ($0.017/giờ)| 1 | 12.41 | Chạy 730 giờ | 12.41 |
| 11 | RDS Storage | 20 GB gp3 ($0.115/GB-mo) | 1 | 2.30 | Dung lượng lưu trữ DB | 2.30 |
| 12 | Amazon S3 | Standard tier (5 GB) | 1 | 0.12 | $0.023/GB-mo | 0.12 |
| 13 | Amazon SQS | Standard & DLQ | 2 | 0.00 | Nằm trong Free Tier (<1M reqs) | 0.00 |
| 14 | AWS Secrets Manager | $0.40/secret/tháng | 1 | 0.40 | Lưu trữ DB password/API keys | 0.40 |
| 15 | AWS Systems Manager | Session Manager | - | 0.00 | Miễn phí truy cập máy chủ | 0.00 |
| 16 | Amazon CloudWatch | Basic Metrics + Logs | - | 0.00 | Nằm trong Free Tier | 0.00 |
| **Tổng** | | | | | | **127.33** |

*Ghi chú: Tổng chi phí thực tế có thể chênh lệch nhẹ dựa trên phí Data Transfer Out và LCU của ALB, tuy nhiên lưu lượng truy cập dự kiến rất thấp nên có thể bỏ qua trong ước tính này.*

### Đánh giá và Đề xuất tối ưu

*   **Tổng chi phí triển khai mỗi tháng:** Ước tính khoảng **$127.33 USD**.
*   **Phân tích cấu trúc chi phí:** Dịch vụ chiếm tỷ trọng chi phí cao nhất là **NAT Gateway** ($65.70, chiếm hơn 51% tổng chi phí), tiếp theo là chi phí cho **Amazon EC2 & EBS** ($29.97, chiếm khoảng 23%).
*   **Đánh giá mức độ phù hợp với AWS Credits:** Với tổng chi phí dự kiến ~$127.33/tháng, hệ thống **hoàn toàn phù hợp và an toàn** nằm trong giới hạn tài trợ AWS Credits 200 USD. Dự án vẫn còn dư khoảng $72 để dự phòng cho các chi phí phát sinh nhỏ lẻ như Data Transfer Out, LCU hoặc mở rộng Auto Scaling khi cần thiết.
*   **Đề xuất tối ưu chi phí (không thay đổi kiến trúc hiện tại):**
    *   **Tối ưu hóa thời gian chạy (Resource Scheduling):** Mặc dù hệ thống được ước tính chạy 24/7, có thể cấu hình Auto Scaling thu hẹp (scale in) xuống 1 instance và cấu hình lại Route Table để tạm tắt 1 NAT Gateway vào ngoài giờ hành chính, giúp cắt giảm đáng kể chi phí duy trì.
    *   **Giảm dung lượng ổ cứng EBS:** Cấu hình 30 GB EBS gp3 cho mỗi EC2 t3.micro có phần dư thừa đối với ứng dụng web đơn giản hoặc Docker container nhỏ. Có thể giảm mức dung lượng xuống 10 GB hoặc 15 GB để tiết kiệm chi phí lưu trữ block storage.
    *   **Sử dụng VPC Endpoints:** Đối với dịch vụ S3 và Secrets Manager, có thể thiết lập VPC Gateway/Interface Endpoints để các máy chủ trong Private Subnet truy cập trực tiếp qua mạng nội bộ AWS. Giải pháp này giúp giảm lưu lượng Data Processing đi qua NAT Gateway.

## 4. Development and deployment

Quá trình phát triển và triển khai hệ thống tuân theo các tiêu chuẩn kỹ thuật hiện đại:
*   Mã nguồn được quản lý và kiểm soát phiên bản (Version Control) thông qua **GitHub**: [Tìm hiểu về GitHub](https://github.com/about)
*   Ứng dụng backend được đóng gói (containerized) bằng **Docker**, đảm bảo tính đồng nhất tuyệt đối giữa môi trường phát triển cục bộ và môi trường máy chủ EC2 thực tế trên cloud. Tham khảo: [Docker trên AWS](https://aws.amazon.com/docker/)
*   Tài nguyên hạ tầng (Infrastructure) được cấp phát thông qua AWS Console, kết hợp sử dụng User Data trong cấu hình Launch Template để tự động cài đặt môi trường, pull Docker image và chạy ứng dụng mỗi khi một EC2 instance mới được Auto Scaling sinh ra.
    *   Tham khảo: [Chạy lệnh trên EC2 bằng User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html)
    *   Tham khảo: [AWS Auto Scaling Groups](https://docs.aws.amazon.com/autoscaling/ec2/userguide/AutoScalingGroup.html)
    *   Tham khảo: [Tạo Launch Template cho Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-launch-template.html)

## 5. Cost and resource cleanup

Vì hệ thống triển khai nhiều dịch vụ tính phí theo giờ (đặc biệt là NAT Gateway, EC2 và ALB), việc dọn dẹp tài nguyên (Resource Cleanup) sau khi hoàn tất demo đồ án là cực kỳ quan trọng để tránh lãng phí ngân sách AWS Credits. Quá trình dọn dẹp cần được thực hiện triệt để theo thứ tự ngược lại với quy trình triển khai:
1. Xóa Auto Scaling Group và Launch Template để ngăn chặn hệ thống tiếp tục sinh ra EC2 instance mới. Tham khảo: [Xóa Auto Scaling Group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/delete-auto-scaling-group.html)
2. Xóa Application Load Balancer và Target Group đi kèm. Tham khảo: [Xóa ALB](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/application-load-balancer-getting-started.html#delete-load-balancer)
3. Chấm dứt thủ công các máy chủ EC2 (Terminate Instance) còn sót lại. Tham khảo: [Terminate EC2 Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/terminating-instances.html)
4. Xóa database Amazon RDS và loại bỏ các snapshot/backup đi kèm. Tham khảo: [Xóa RDS Instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DeleteInstance.html)
5. Xóa các NAT Gateway và giải phóng Elastic IP (Release EIP) ngay lập tức. Tham khảo: [Xóa NAT Gateway](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html#nat-gateway-deleting)
6. Xóa Internet Gateway, Route Tables, Subnets và cuối cùng là xóa hoàn toàn VPC. Tham khảo: [Xóa VPC](https://docs.aws.amazon.com/vpc/latest/userguide/delete-vpc.html)
