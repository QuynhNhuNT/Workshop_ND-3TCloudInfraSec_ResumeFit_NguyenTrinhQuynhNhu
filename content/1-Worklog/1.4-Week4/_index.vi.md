---
title: "Worklog Tuần 4"
date: 2026-06-29
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:
* Cấu hình co giãn tự động Auto Scaling Group (ASG) và cân bằng tải ALB để hệ thống chịu tải tốt.
* Giám sát tài nguyên, thu thập log và thiết lập cảnh báo hệ thống bằng CloudWatch.
* Quản lý phân giải tên miền với Route 53 và thiết lập bảo mật mạng nâng cao (NACLs/Security Groups).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tạo Launch Template, cấu hình Auto Scaling Group (ASG) và Application Load Balancer (ALB) để cân bằng tải và co giãn. | 11/05/2026 | 11/05/2026 | [Tài liệu](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| 3 | - Thực hiện kiểm thử tính năng co giãn tự động của ASG bằng cách chạy script ép tải CPU của các EC2 máy chủ. | 12/05/2026 | 12/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-load-balancer.html) |
| 4 | - Cấu hình CloudWatch Metrics, tạo CloudWatch Alarm để gửi email cảnh báo tự động qua SNS khi CPU vượt quá 80%. | 13/05/2026 | 13/05/2026 | [Tài liệu](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) |
| 5 | - Thu thập log ứng dụng web bằng CloudWatch Logs Agent để theo dõi các sự cố ứng dụng. | 14/05/2026 | 14/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| 6 | - Mua/Cấu hình tên miền trong Route 53, trỏ tên miền về địa chỉ DNS của ALB.<br>- Thiết lập tối ưu hóa NACLs và Security Groups để thắt chặt bảo mật. | 15/05/2026 | 15/05/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 4:
* Cấu hình thành công ASG và ALB giúp hệ thống tự động co giãn khi CPU tăng cao.
* Thiết lập CloudWatch Alarms gửi thông báo qua email thành công khi có sự cố.
* Trỏ tên miền Route 53 về ALB thành công và tăng tính bảo mật nhờ tối ưu hóa NACLs.
