---
title: "5.5 - Lưu trữ & Hàng đợi"
date: 2026-07-10
weight: 4
chapter: false
pre: " <b> 5.5. </b> "
---

# 5.5. Thiết lập Dịch vụ Lưu trữ và Hàng đợi

## 5.5.1. Khởi tạo S3 Bucket

1. Chuyển sang dịch vụ **S3**, nhấn **Create bucket** để tạo nơi lưu trữ CV và tài liệu của ứng viên.
2. Đặt tên bucket có dạng `resume-matching-storage-[AWS-ACCOUNT-ID]-us-east-1`.
3. Tại tab **Permissions**, tiến hành chỉnh sửa **Cross-origin resource sharing (CORS)**. Thêm nội dung JSON để cấu hình `AllowedMethods` bao gồm: `GET`, `PUT`, `POST` nhằm cho phép ứng dụng web tải file lên bucket.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_S3.jpg" alt="Tạo S3 Bucket" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Bo_sung_CORS_S3.jpg" alt="Cấu hình CORS S3" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Create_Folder_S3.jpg" alt="Tạo thư mục trong S3" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.5.2. Khởi tạo SQS Queues

Sử dụng hàng đợi để tách biệt luồng xử lý AI nặng nề ra khỏi luồng phản hồi web chính.

1. Chuyển đến giao diện **SQS**. Tạo một hàng đợi Standard có tên `ResumeMatching-DLQ` (Dead Letter Queue) dùng để hứng các message bị lỗi trong quá trình xử lý.
2. Khởi tạo hàng đợi chính mang tên `ResumeMatching-Queue`.
3. Bật tính năng **Dead-letter queue** trên hàng đợi chính, trỏ đến ARN của `ResumeMatching-DLQ` và thiết lập `Maximum receives` = `3`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_queue.jpg" alt="Khởi tạo SQS Queue" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_main_queue.jpg" alt="Tạo Main Queue và gán DLQ" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
