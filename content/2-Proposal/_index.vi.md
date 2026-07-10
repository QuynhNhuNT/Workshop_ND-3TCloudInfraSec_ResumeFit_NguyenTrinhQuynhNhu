---
title: "Bản đề xuất"
date: 2026-07-10
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

### AI Resume Matching & Interview Preparation Platform

**1. Tổng quan dự án**

* **Mục tiêu:** Ứng dụng Web đánh giá độ phù hợp CV và JD dựa trên hạ tầng AWS chuẩn kiến trúc 3-Tier.
* **Xử lý AI:** Cụm EC2 (Backend + Worker) chịu trách nhiệm phân tích CV và JD bằng cách gọi API OpenAI qua Internet để tối ưu lượng token tiêu thụ và tiết kiệm chi phí.

**2. Kiến trúc hạ tầng đám mây (AWS)**

![AI Resume Matching & Interview Preparation Platform Architecture](/images/2-Proposal/resume-matching-architecture.png)

* **Lớp Biên & Toàn Cầu (Global):**
  * Mạng phân phối nội dung (CloudFront), tường lửa WAF và dịch vụ xác thực đang trong trạng thái dự kiến (Planned but not deployed - AWS account verification required), không phải là các dịch vụ đang hoạt động thực tế.
  * Sử dụng Amazon S3 (Amazon Simple Storage Service) cho lưu trữ chung.
  * Người dùng (Users) tương tác qua Internet Gateway (1) hoặc "tải lên qua Pre-signed URL" trực tiếp đến một S3 storage riêng (S3 CV/JD Storage) (5).

* **Mạng & Cân Bằng Tải (Inbound):**
  * VPC 10.0.0.0/16 làm nền tảng.
  * Internet Gateway (IGW) làm cửa ngõ duy nhất kết nối với Internet cho cả lưu lượng Inbound và Outbound (thông qua NAT Gateway).
  * Application Load Balancer (ALB) nằm giữa các Vùng Sẵn Sàng (Availability Zones), nhận lưu lượng từ IGW và phân phối đến cụm Auto Scaling Group.

* **Tầng Ứng Dụng (Application):**
  * Cụm EC2 (Backend + Worker) được đặt trong các Private App Subnets kín (Private App Subnet A & Private App Subnet B), xuyên qua 2 Vùng Sẵn Sàng (AZ A & AZ B) và được quản lý bởi một Auto Scaling Group (ASG) để tự co giãn theo tải.
  * Giao tiếp nội bộ: EC2 (AZ A) kết nối với dịch vụ S3 storage và SQS (6), sau đó là Dead Letter Queue (DLQ).
  * Luồng API OpenAI (AZ B) được thực hiện bằng cách EC2 (AZ B) đi ra ngoài qua NAT Gateway của Public Subnet B để gọi Internet Gateway. (Lưu ý: NAT Gateway được bố trí ở cả hai Public Subnet A và Public Subnet B để tối ưu định tuyến).

* **Mạng Outbound & Nội Bộ:**
  * Có **hai NAT Gateway**, một trong Public Subnet A và một trong Public Subnet B, đảm bảo khả năng dự phòng cao (High Availability) cho lưu lượng Outbound từ các Private Subnets.
  * Giao tiếp đến SQS và S3 được hiển thị qua mạng, không sử dụng VPC Endpoints.

* **Tầng Cơ Sở Dữ Liệu (Database):**
  * Dùng Amazon RDS PostgreSQL với cấu hình Multi-AZ.
  * Có hai Private DB Subnets (Private DB Subnet A & Private DB Subnet B) được bảo vệ bởi một Security Group.
  * RDS Primary (Master) ở AZ A. RDS Standby Replica ở AZ B với dữ liệu được đồng bộ liên tục (đồng bộ hóa dữ liệu thời gian thực).
  * Luồng kết nối: EC2 ở AZ A kết nối trực tiếp đến RDS Primary (7). EC2 ở AZ B kết nối đến RDS Standby Replica thông qua một RDS Endpoints.

* **Quản Lý & Giám Sát:**
  * Một cụm "Quản Lý & Bảo Mật" (Regional Vùng Bảo mật & Quản lý) bao gồm AWS Systems Manager, Amazon CloudWatch (logs) và AWS Secrets Manager (API Key).

* **Triển Khai (Deployment):**
  * Nguồn mã đặt tại GitHub (Manual Deployment) được chỉ định là triển khai thủ công. Không sử dụng AWS CodeBuild hay AWS CodePipeline tự động trong kiến trúc hiện tại.