---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Tại đây sẽ là phần liệt kê, giới thiệu các blogs mà tôi đã đăng trên [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj):

###  [Blog 1 - GIÁM SÁT HỆ THỐNG TRÊN AWS: ĐƯA CLOUDWATCH METRICS VÀO OPENTELEMETRY COLLECTOR TRONG VPC BẰNG LAMBDA](3.1-Blog1/)
Blog này giới thiệu giải pháp sử dụng AWS Lambda làm trạm trung chuyển dữ liệu từ CloudWatch Metric Streams đến hệ thống thu thập dữ liệu nội bộ (OpenTelemetry Collector) được cô lập nghiêm ngặt trong phân vùng mạng riêng (Private Subnet) của VPC một cách an toàn và tức thời.

###  [Blog 2 - XÂY DỰNG AI GATEWAY QUẢN TRỊ AMAZON BEDROCK BẰNG API GATEWAY](3.2-Blog2/)
Blog này chia sẻ trải nghiệm thực chiến thiết kế lớp bảo vệ AI Gateway sử dụng Amazon API Gateway kết hợp với Lambda Authorizer và Lambda Integration nhằm xác thực cuộc gọi API, phân tách môi trường người dùng, kiểm soát chi phí và quản trị các cuộc gọi LLM đến Amazon Bedrock.

###  [Blog 3 - MỘT TÍNH NĂNG KHÁ HAY CỦA AWS LAKE FORMATION](3.3-Blog3/)
Blog này phân tích tính năng mới của AWS Lake Formation cho phép cấp phát thông tin xác thực tạm thời (temporary credentials) thông qua API GetTemporaryDataLocationCredentials(), giúp các công cụ xử lý dữ liệu như EMR Spark đọc/ghi trực tiếp file lưu trữ trên S3 dựa trên cấu hình phân quyền tập trung.