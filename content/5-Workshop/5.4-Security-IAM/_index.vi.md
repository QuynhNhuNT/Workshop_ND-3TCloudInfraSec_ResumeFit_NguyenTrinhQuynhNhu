---
title: "5.4 - Bảo mật & Quản lý Truy cập"
date: 2026-07-10
weight: 3
chapter: false
pre: " <b> 5.4. </b> "
---

# 5.4. Thiết lập Bảo mật và Quản lý Truy cập

## 5.4.1. Khởi tạo Security Groups

Thiết lập tường lửa ảo kiểm soát luồng giao thông mạng giữa các tài nguyên ở mức độ giao thức và cổng kết nối.

1. **ALB Security Group** (`ResumeMatching-ALB-SG`): Mở port HTTP (`80`) và HTTPS (`443`) (TCP) với Source là `0.0.0.0/0` để cho phép người dùng truy cập web.
2. **Backend Security Group** (`ResumeMatching-Backend-SG`): Cấu hình Inbound rule cho phép giao thức HTTP trên cổng TCP. Source được giới hạn chỉ nhận luồng từ `ResumeMatching-ALB-SG`.
3. **Worker Security Group** (`ResumeMatching-Worker-SG`): Tường lửa bảo vệ Worker Server xử lý tác vụ nền.
4. **Database Security Group** (`ResumeMatching-RDS-SG`): Mở port `5432` (PostgreSQL). Source chỉ cho phép nhận kết nối nội bộ từ Backend và Worker Security Group.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_ALB_Security_Group.jpg" alt="Tạo ALB Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Backend_Security_Group.jpg" alt="Tạo Backend Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tạo_Worker_Security_Group.jpg" alt="Tạo Worker Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Database_Security_Group.jpg" alt="Tạo Database Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.4.2. Cấu hình IAM Roles

Cấp quyền ủy quyền an toàn cho các máy chủ EC2 giao tiếp với các dịch vụ AWS khác mà không cần lưu trữ Hard-code Access Key.

1. Truy cập dịch vụ **IAM**, tạo role `ResumeMatching-Backend-Role` để cấp cho máy chủ backend chạy trên EC2.
2. Tạo role thứ hai mang tên `ResumeMatching-Worker-Role` dành riêng cho Worker server. Đính kèm các policy AWS Managed như `AmazonSQSFullAccess` và quyền thao tác với S3.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Backend_IAM_Role.jpg" alt="Tạo Backend IAM Role" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Worker_IAM_Role.jpg" alt="Tạo Worker IAM Role" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
