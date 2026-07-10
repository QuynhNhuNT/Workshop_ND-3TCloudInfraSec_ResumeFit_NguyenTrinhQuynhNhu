---
title: "Worklog Tuần 9"
date: 2026-06-29
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:
* Kiểm thử khả năng chịu tải của hệ thống (Load Testing) để đánh giá khả năng co giãn của ASG.
* Xây dựng màn hình giám sát tập trung CloudWatch Dashboards và kiểm toán lịch sử gọi API bằng CloudTrail.
* Rà soát tài nguyên phát sinh thông qua Cost Explorer và tiến hành tối ưu hóa chi phí dự án.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Sử dụng các công cụ stress test (như Apache Bench, Locust) để tạo tải ảo lên website chạy qua ALB. | 15/06/2026 | 15/06/2026 | [Tài liệu](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-comparison.html) |
| 3 | - Theo dõi hành vi tự động scale-up và scale-down của Auto Scaling Group trên màn hình quản trị AWS. | 16/06/2026 | 16/06/2026 | [Tài liệu tham khảo](https://aws.amazon.com/solutions/implementations/distributed-load-testing-on-aws/) |
| 4 | - Thiết lập CloudWatch Dashboard tổng hợp hiển thị: CPU Utilization của EC2, Request Count của ALB, Latency của Lambda và DB Connection. | 17/06/2026 | 17/06/2026 | [Tài liệu](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| 5 | - Cấu hình AWS CloudTrail ghi nhận các API log. Kiểm tra IAM Access Analyzer để đảm bảo không có quyền truy cập dư thừa. | 18/06/2026 | 18/06/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| 6 | - Kiểm tra bảng chi phí qua AWS Billing/Cost Explorer. Tối ưu hóa kích thước DB Instance, xóa bỏ các tài nguyên không dùng để tránh lãng phí. | 19/06/2026 | 19/06/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 9:
* Hệ thống vượt qua bài kiểm tra chịu tải và tự động scale-up thành công.
* Hoàn thiện CloudWatch Dashboard giúp theo dõi tình trạng tài nguyên thời gian thực.
* Giảm thiểu 25% chi phí phát sinh thông qua rà soát và tối ưu hóa tài nguyên.
