---
title: "Worklog Tuần 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:
* Nắm vững kiến thức nền tảng về VPC, Subnets, Security Groups và EC2.
* Thực hành tạo lập hạ tầng mạng cơ bản và chạy máy chủ ảo EC2.
* Hiểu sâu về phân quyền tài nguyên AWS (IAM Role cho EC2) và kiểm soát chi phí dịch vụ.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu khái niệm VPC, Public Subnet, Private Subnet, Internet Gateway (IGW) và Route Table để thiết lập môi trường mạng cô lập. | 27/04/2026 | 27/04/2026 | [Tài liệu](https://docs.aws.amazon.com/vpc/index.html) |
| 3 | - Khởi tạo máy chủ ảo Amazon EC2.<br>- Cấu hình Security Group cho phép truy cập SSH (Port 22) và HTTP (Port 80) từ Internet. | 28/04/2026 | 28/04/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| 4 | - Tìm hiểu IAM Roles và sự khác biệt với IAM Users.<br>- Tạo một IAM Role cấp quyền truy cập S3 Read-Only và gán (attach) vào EC2 Instance. | 29/04/2026 | 29/04/2026 | [Tài liệu](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) |
| 5 | - Thực hành kết nối SSH vào EC2 bằng Key Pair từ máy cá nhân.<br>- Cài đặt web server Nginx/Apache trên EC2 để chạy thử website cơ bản. | 30/04/2026 | 30/04/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| 6 | - Kiểm tra chi phí dịch vụ EC2 phát sinh trên Billing Console.<br>- Hoàn thành 3 bài lab cơ bản trong lộ trình video hướng dẫn trực tuyến. | 01/05/2026 | 01/05/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 2:
* Hiểu cấu trúc mạng ảo VPC và khởi chạy thành công máy chủ ảo EC2.
* Thực hiện phân quyền an toàn cho EC2 thông qua IAM Role (không cần lưu Access Key trên máy chủ).
* Hoàn thành xuất sắc 3 bài lab nền tảng, truy cập thành công website Nginx từ Internet.
