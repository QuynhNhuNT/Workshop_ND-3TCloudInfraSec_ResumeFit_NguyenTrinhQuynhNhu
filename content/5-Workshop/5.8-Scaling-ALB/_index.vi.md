---
title: "5.8 - Tự động mở rộng & Cân bằng tải"
date: 2026-07-10
weight: 7
chapter: false
pre: " <b> 5.8. </b> "
---

# 5.8. Thiết lập Tự động mở rộng và Cân bằng tải

## 5.8.1. Cấu hình AMI và Launch Template

1. Chuẩn hóa môi trường EC2 vừa cài đặt bằng cách tạo ra một Amazon Machine Image (AMI) mang tên `ResumeMatching-Backend-AMI`.
2. Từ AMI này, tạo một **Launch Template** mang tên `ResumeMatching-LT` chứa các cấu hình phần cứng, mạng và bảo mật chuẩn.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_AMIs.jpg" alt="Tạo AMI" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_launch_template.jpg" alt="Tạo Launch Template" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.8.2. Auto Scaling Group (ASG)

1. Tạo Auto Scaling Group `ResumeMatching-ASG` và liên kết với Launch template `ResumeMatching-LT`.
2. Chỉnh sửa Desired capacity lên thành `2`. ASG sẽ tự động launch ra các EC2 instances mới ở trạng thái Initializing nhằm phục vụ dự phòng và mở rộng.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_ASG.jpg" alt="Tạo Auto Scaling Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ASG_tao_them_EC2.jpg" alt="ASG Khởi tạo thêm Instance" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ASG_tao_EC2_moi_sau khi_cap_nhat_AMI.jpg" alt="ASG thay thế EC2 mới sau khi cập nhật AMI" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.8.3. Target Group và Application Load Balancer

1. Tạo một **Target Group** tên `ResumeMatching-TG`, dạng `Instance` giao thức HTTP trên cổng `8080` (hoặc `80` tùy cấu hình container nội bộ).
2. Khởi tạo **Application Load Balancer (ALB)** tên `ResumeMatching-ALB`. Lựa chọn Scheme là `Internet-facing` để nhận traffic từ ngoài internet, lắng nghe tại 2 Availability Zones và định tuyến giao thông vào mạng thông qua Target Group trên.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_target_group.jpg" alt="Tạo Target Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_ALB.jpg" alt="Tạo Application Load Balancer" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
