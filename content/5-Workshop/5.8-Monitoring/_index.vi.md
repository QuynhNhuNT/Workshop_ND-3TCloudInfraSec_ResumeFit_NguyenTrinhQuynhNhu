---
title: "Giám sát Hệ thống (Monitoring)"
date: 2026-07-10
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

# 5.8. Giám sát Hệ thống và Đảm bảo Tính sẵn sàng cao (Monitoring)

Việc giám sát là bắt buộc để đảm bảo luồng traffic được phân bổ chính xác và các quy tắc Scaling hoạt động đúng chuẩn.

## 5.8.1. Kiểm tra hoạt động của Auto Scaling Group

1. Truy cập dịch vụ **EC2**, điều hướng đến menu **Instances**.
2. Quan sát hệ thống tự động khởi tạo các EC2 mới có tên `ResumeMatching-ASG-Instance` phân bổ đều ở các Availability Zone khác nhau.
3. Một số máy chủ cũ có thể hiển thị trạng thái `Terminated`. Đây là minh chứng ASG đang hoạt động chính xác: tự động thu hồi máy chủ cũ và khởi chạy máy chủ mới khi có sự thay đổi cấu hình hoặc lỗi hệ thống.

## 5.8.2. Kiểm tra Health Check của Target Group

1. Tại mục **Load Balancing**, chọn **Target Groups**, nhấn chọn vào Target Group của hệ thống.
2. Chuyển sang tab **Targets** và quan sát bảng **Registered targets**.
3. Xác nhận cột `Health status` của các instance hiển thị trạng thái màu xanh `Healthy`, chứng minh máy chủ web đã khởi động và sẵn sàng nhận request từ Load Balancer.

<div style="display: grid; grid-template-columns: 1fr; gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Target_group_healthy_check.jpg" alt="Health Check Target Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.8.3. Giám sát hiệu suất qua CloudWatch

1. Truy cập **CloudWatch**, chọn menu **Metrics** để giám sát sâu các thông số.
2. **Đối với EC2**: Lọc Namespace EC2, chọn `CPUUtilization`. Quan sát biểu đồ để thấy các đỉnh gai xử lý (ví dụ `81.9%`) khi AI chạy tác vụ nặng, từ đó thiết lập Threshold mở rộng tự động cho ASG.
3. **Đối với ALB**: Lọc metric `RequestCount` và `TargetResponseTime`. Sự tương quan giữa việc tăng vọt lượng Request và sự thay đổi của thời gian phản hồi (ví dụ `660.4 ms`) giúp đánh giá tính trơn tru của trải nghiệm người dùng.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/CloudWatch_dang_monitor_EC2.jpg" alt="CloudWatch Monitor EC2" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/EC2_Metrics.jpg" alt="EC2 Metrics" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/CloudWatch_monitor_Load_Balancer.jpg" alt="CloudWatch Monitor Load Balancer" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ALB_Metrics.jpg" alt="ALB Metrics" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
