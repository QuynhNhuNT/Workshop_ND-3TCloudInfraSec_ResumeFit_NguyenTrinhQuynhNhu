---
title: "Worklog Tuần 8"
date: 2026-06-29
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:
* Triển khai máy chủ Web trên EC2 kết hợp ALB điều phối và RDS/DynamoDB lưu trữ dữ liệu.
* Viết API logic xử lý thông qua API Gateway kết hợp Lambda backend để xử lý serverless.
* Hiện thực hóa tính năng thông minh bằng cách tích hợp gọi các mô hình AI trên Amazon Bedrock.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Dựng máy chủ EC2 chứa mã nguồn Web Frontend và kết nối qua ALB. | 08/06/2026 | 08/06/2026 | [Tài liệu](https://docs.aws.amazon.com/bedrock/latest/userguide/api-methods-run.html) |
| 3 | - Triển khai Database (RDS Postgres hoặc DynamoDB) trong Private Subnets. Cấu hình Security Group chỉ cho phép kết nối từ EC2 hoặc Lambda. | 09/06/2026 | 09/06/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerToRDS.html) |
| 4 | - Phát triển Backend API trên AWS Lambda. Tạo API Gateway làm cổng kết nối. | 10/06/2026 | 10/06/2026 | [Tài liệu](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html) |
| 5 | - Cấu hình phân quyền IAM Role cho Lambda truy cập DynamoDB và Amazon Bedrock.<br>- Tích hợp Lambda với mô hình AI Claude trên Amazon Bedrock. | 11/06/2026 | 11/06/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/bedrock/latest/userguide/bedrock-runtime_api.html) |
| 6 | - Viết code giao diện (React/HTML tĩnh) kết nối với API Gateway.<br>- Kiểm thử kết nối End-to-End từ Client đến Database và AI. | 12/06/2026 | 12/06/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 8:
* Triển khai thành công hạ tầng máy chủ EC2 và RDS/DynamoDB an toàn.
* Xây dựng hoàn chỉnh luồng xử lý API Serverless backend kết hợp AI Bedrock.
* Kết nối thành công toàn bộ hệ thống từ Client đến Database và mô hình AI.
