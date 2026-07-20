---
title: "Giới thiệu"
date: 2026-07-10
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

# 5.1. Giới thiệu

Bài lab này hướng dẫn chi tiết cách triển khai toàn diện hệ thống **Resume Fit** trên nền tảng đám mây AWS. Resume Fit là một ứng dụng AI giúp đánh giá độ phù hợp giữa Hồ sơ ứng viên (CV) và Yêu cầu công việc (JD) một cách nhanh chóng, minh bạch nhằm hỗ trợ ra quyết định tuyển dụng.

Hệ thống được thiết kế theo kiến trúc chuẩn trên AWS, đảm bảo tính mở rộng và sẵn sàng cao, bao gồm các thành phần cốt lõi: Mạng cô lập (VPC), Máy chủ tính toán linh hoạt (EC2, Auto Scaling Group), Cơ sở dữ liệu quan hệ (RDS PostgreSQL), Lưu trữ đối tượng (S3), Hàng đợi xử lý bất đồng bộ (SQS), Dịch vụ giám sát (CloudWatch) và Dịch vụ Quản lý Secret (Secrets Manager).

### Sơ đồ kiến trúc (Architecture Diagram)

<div style="display: grid; grid-template-columns: 1fr; gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Blank diagram.jpg" alt="Architecture Diagram" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.15); transition: transform 0.3s ease;" onmouseover="this.style.transform='scale(1.01)'" onmouseout="this.style.transform='scale(1)'">
    <p style="text-align: center; color: #666; margin-top: 10px; font-style: italic;">Tổng quan kiến trúc Resume Fit trên AWS</p>
  </div>
</div>

