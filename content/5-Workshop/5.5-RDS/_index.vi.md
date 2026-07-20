---
title: "Cơ sở dữ liệu (RDS)"
date: 2026-07-10
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

# 5.5. Thiết lập Hệ Quản Trị Cơ Sở Dữ Liệu (RDS)

## 5.5.1. Cấu hình Secrets Manager

1. Truy cập **AWS Secrets Manager**, tạo secret tên `ResumeMatching-Secrets` để lưu trữ thông tin nhạy cảm.
2. Cấu hình phần **Secret value** với các trường Key/value như `HOST` (sẽ được cập nhật sau khi có RDS Endpoint), `PORT` (`5432`), `USERNAME`, `PASSWORD`, và `OPENAI_API_KEY` của ứng dụng.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Secret.jpg" alt="Tạo Secret" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cap_nhat_Secrets_manager.jpg" alt="Cập nhật Secrets Manager" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.5.2. Tạo RDS PostgreSQL

1. Truy cập giao diện **RDS**, chọn mục **Subnet groups** và tạo một subnet group tên `resumematching-dbsubnetgroup` trỏ vào VPC và gom 2 subnet `Private-DB-A`, `Private-DB-B` lại với nhau.
2. Tiến hành khởi tạo Database (DB identifier: `resume-matching-db`) với Engine là **PostgreSQL** và instance class là `db.t3.micro`.
3. Sau khi tạo thành công, copy Endpoint của Database và dán cập nhật vào khóa `HOST` trong Secrets Manager.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_DB_Subnet_Group.jpg" alt="Tạo DB Subnet Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_RDS_database.jpg" alt="Tạo RDS PostgreSQL" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
