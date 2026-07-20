---
title: "Compute & Cấu hình Server"
date: 2026-07-10
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

# 5.6. Triển khai Compute và Cấu hình Server

## 5.6.1. Khởi tạo EC2 Backend Instance

1. Tạo một khóa **Key Pair** (`ResumeMatching-Key`) kiểu RSA.
2. Tại EC2 Dashboard, khởi chạy một Instance có tên `ResumeMatching-Backend` với Instance type là `t3.micro` đặt trong VPC ứng dụng.
3. Đợi trạng thái Instance chuyển sang `Running` và Status check hiển thị `2/2 checks passed`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Key_Pair.jpg" alt="Tạo Key Pair" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_EC2_Backend.jpg" alt="Khởi tạo EC2 Backend" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.6.2. Kết nối và cài đặt phần mềm

1. Truy cập EC2 từ xa an toàn bằng **Systems Manager Fleet Manager**. Chọn Managed node đang Running và nhấn **Start terminal session**.
2. Thực thi lệnh cài đặt **Git** để kéo mã nguồn:
   ```bash
   sudo dnf install git
   ```
3. Tiến hành cài đặt và khởi động **Docker** để chạy ứng dụng dạng container:
   ```bash
   sudo dnf install -y docker
   sudo systemctl enable docker
   sudo systemctl start docker
   ```
4. Điều hướng tới thư mục `/opt` và tải source code từ GitHub:
   ```bash
   cd /opt
   sudo git clone http://github.com/thuanthien-tran/resume-fit.git
   sudo chown -R ssm-user /opt/resume-fit
   ```

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Connect_EC2_backend_bang_Systems_Manager.jpg" alt="Kết nối bằng Systems Manager" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cai_GIT.jpg" alt="Cài đặt Git" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cai_Docker.jpg" alt="Cài đặt Docker" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Kiem_tra_trang_thai_Docker.jpg" alt="Kiểm tra trạng thái Docker" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Clone_source_len_EC2.jpg" alt="Clone source code từ Github" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
