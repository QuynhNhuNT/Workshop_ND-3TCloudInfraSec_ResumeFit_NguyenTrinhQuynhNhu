---
title: "Worklog Tuần 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:
* Triển khai mô hình lập trình Serverless bằng cách sử dụng AWS Lambda và Amazon API Gateway.
* Nghiên cứu tích hợp Trí tuệ nhân tạo (AI) thông qua việc kết nối và sử dụng Amazon Bedrock.
* Thực hành quản lý và lưu trữ thông tin nhạy cảm bảo mật cao với AWS Secrets Manager.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Viết hàm AWS Lambda bằng Python/Node.js để xử lý dữ liệu backend Serverless. | 18/05/2026 | 18/05/2026 | [Tài liệu](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| 3 | - Thiết lập REST/HTTP API trong API Gateway làm cổng kết nối ứng dụng với Lambda. | 19/05/2026 | 19/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html) |
| 4 | - Xử lý CORS và cấu hình bảo mật API Gateway (sử dụng IAM Authorizers hoặc Cognito). | 20/05/2026 | 20/05/2026 | [Tài liệu](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) |
| 5 | - Tìm hiểu Amazon Bedrock và đăng ký quyền truy cập mô hình ngôn ngữ lớn (Claude, Llama).<br>- Viết mã Lambda gọi Bedrock LLM API. | 21/05/2026 | 21/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |
| 6 | - Tạo Secret trên AWS Secrets Manager lưu trữ thông tin mật khẩu database và API Keys thay vị trí hardcode trong mã nguồn. | 22/05/2026 | 22/05/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 5:
* Xây dựng thành công kiến trúc Serverless (API Gateway -> Lambda).
* Tích hợp thành công Amazon Bedrock gọi mô hình LLM từ code Lambda phục vụ tính năng thông minh.
* Đảm bảo an toàn thông tin nhạy cảm nhờ AWS Secrets Manager.
