---
title: "Worklog Tuần 3"
date: 2026-06-29
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
* Làm quen với dịch vụ lưu trữ đối tượng Amazon S3 và cấu hình bảo mật Bucket Policy.
* Triển khai cơ sở dữ liệu quan hệ RDS MySQL và cơ sở dữ liệu NoSQL DynamoDB.
* Sử dụng môi trường AWS Cloud9 và công cụ dòng lệnh AWS CLI để quản trị hệ thống nhanh chóng.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tạo Amazon S3 Bucket.<br>- Cấu hình Static Website Hosting để deploy giao diện web tĩnh.<br>- Cấu hình Bucket Policy phân quyền truy cập. | 04/05/2026 | 04/05/2026 | [Tài liệu](https://docs.aws.amazon.com/AmazonS3/latest/userguide/bucket-policies.html) |
| 3 | - Khởi tạo cơ sở dữ liệu RDS MySQL trong phân vùng Private Subnet để bảo mật.<br>- Thiết lập kết nối bảo mật từ EC2 đến RDS thông qua Security Group. | 05/05/2026 | 05/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html) |
| 4 | - Khởi tạo bảng dữ liệu NoSQL trong DynamoDB.<br>- Viết mã script kết nối đọc/ghi dữ liệu cơ bản. | 06/05/2026 | 06/05/2026 | [Tài liệu](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Security.html) |
| 5 | - Khởi tạo môi trường lập trình tích hợp AWS Cloud9 trên nền tảng Cloud. | 07/05/2026 | 07/05/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_GettingStarted.html) |
| 6 | - Thực hành cài đặt và cấu hình AWS CLI trên Cloud9.<br>- Viết kịch bản lệnh (script CLI) để tạo lập, quản lý và dọn dẹp tài nguyên tự động. | 08/05/2026 | 08/05/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 3:
* Deploy thành công website tĩnh lên S3 và biết cách viết Bucket Policy an toàn.
* Khởi tạo thành công database RDS MySQL nằm trong Private Subnet và kết nối bảo mật từ EC2.
* Tạo bảng DynamoDB và thao tác dữ liệu qua CLI.
* Thành thạo thao tác dòng lệnh AWS CLI và phát triển code trên Cloud9.
