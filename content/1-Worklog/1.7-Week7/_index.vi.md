---
title: "Worklog Tuần 7"
date: 2026-06-29
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:
* Thiết kế bản vẽ kiến trúc hệ thống tổng thể (High-Level Design) cho sản phẩm cuối khóa.
* Khởi tạo hạ tầng mạng ảo VPC chính thức cho dự án với các Subnets phân vùng bảo mật rõ ràng.
* Phân quyền IAM Roles chi tiết cho các thành viên trong nhóm theo các vai trò cụ thể.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Họp nhóm thảo luận ý tưởng sản phẩm cuối khóa: Ứng dụng Hỗ trợ khách hàng tích hợp AI. | 01/06/2026 | 01/06/2026 | [Tài liệu](https://aws.amazon.com/architecture/well-architected/) |
| 3 | - Sử dụng công cụ vẽ (như Draw.io) để thiết kế sơ đồ kiến trúc High-Level Design (HLD) của dự án. | 02/06/2026 | 02/06/2026 | [Tài liệu tham khảo](https://aws.amazon.com/architecture/) |
| 4 | - Thiết lập sơ đồ thực thể mối quan hệ cơ sở dữ liệu (ERD) và các luồng tích hợp API. | 03/06/2026 | 03/06/2026 | [Tài liệu](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html) |
| 5 | - Triển khai hạ tầng mạng VPC chính thức cho dự án: tạo 2 Public Subnets, 2 Private Subnets nằm trên 2 Availability Zones khác nhau nhằm đảm bảo tính sẵn sàng cao (High Availability). | 04/06/2026 | 04/06/2026 | [Tài liệu tham khảo](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html) |
| 6 | - Tạo IAM Groups, Users và gán Roles phân quyền chi tiết cho nhóm phát triển dự án theo nguyên tắc đặc quyền tối thiểu. | 05/06/2026 | 05/06/2026 | [Tài liệu học tập](https://cloudjourney.awsstudygroup.com/) |

### Kết quả đạt được tuần 7:
* Hoàn thiện tài liệu kiến trúc High-Level Design (HLD) dự án.
* Thiết lập thành công hạ tầng mạng Multi-AZ VPC có tính sẵn sàng cao.
* Cấu hình phân quyền IAM chặt chẽ cho toàn bộ thành viên nhóm.
