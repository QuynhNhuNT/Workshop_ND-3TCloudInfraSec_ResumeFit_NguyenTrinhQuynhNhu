---
title: "5.10 - Kiểm thử Ứng dụng"
date: 2026-07-10
weight: 9
chapter: false
pre: " <b> 5.10. </b> "
---

# 5.10. Kiểm thử Ứng dụng Resume Fit

## 5.10.1. Kiểm tra kết nối Backend và Database qua ALB

1. Kiểm thử thông qua endpoint API của ALB (ví dụ: `http://[ALB-DNS-Name]/api/ready`) để nhận về phản hồi JSON `{"status": "ready"}` chứng minh toàn bộ Backend và Database đã được liên kết thành công.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Test_hoat_dong_bang_DNS_cua_ALB.jpg" alt="Test ALB DNS" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tien_hanh_kiem_tra_cac_ket_noi.jpg" alt="Kiểm tra kết nối DB" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.10.2. Trải nghiệm luồng giao diện người dùng (UI Flow)

### 1. Đăng ký & Đăng nhập Hệ thống
Truy cập Domain/IP của Frontend. Tại giao diện **Đăng ký** và **Đăng nhập hệ thống**, tiến hành tạo tài khoản và đăng nhập vào không gian làm việc.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_dang_ky.jpg" alt="Giao diện Đăng ký" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Giao diện Đăng ký tài khoản</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_dang_nhap.jpg" alt="Giao diện Đăng nhập" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Giao diện Đăng nhập hệ thống</p>
  </div>
</div>

### 2. Quản lý Yêu cầu tuyển dụng (JD)
Khởi tạo và quản lý danh sách các mô tả công việc (Job Descriptions - JD) phục vụ mục đích matching.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_sach_JD.jpg" alt="Danh sách JD" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Trang danh sách quản lý các JD</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_1_tao_ten_cong_viec_ung_tuyen.jpg" alt="Tạo công việc ứng tuyển" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Bước 1: Khởi tạo thông tin vị trí công việc tuyển dụng</p>
  </div>
</div>

### 3. Tải lên CV & JD phân tích
Chạy luồng công việc chính: tải lên CV của ứng viên (định dạng PDF/Docx) tương ứng với vị trí JD đã chọn.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_2_upload_CV_JD.jpg" alt="Tải lên CV & JD" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Bước 2: Giao diện chọn JD và Tải lên CV ứng viên</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_2_upload_CV_JD_Part-2.jpg" alt="Xác nhận tải file" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Kiểm tra thông tin trước khi yêu cầu hệ thống phân tích</p>
  </div>
</div>

### 4. Kết quả đánh giá và Phân tích từ AI (AI Resume Matching Reports)
Yêu cầu hệ thống phân tích. Trình xử lý AI (Worker) sẽ sử dụng OpenAI API để đưa ra **Báo cáo chi tiết ứng viên** vô cùng trực quan:

* **Tổng quan điểm số**: Độ khớp cấp bậc và tổng quan phần trăm phù hợp (Ví dụ: 60%).
* **Phân tích kỹ năng**: Phân loại các kỹ năng chuyên môn còn thiếu (Cybersecurity, C#, ELK, etc.).
* **Khuyến nghị & Câu hỏi phỏng vấn**: Tự động tạo các câu hỏi phỏng vấn kỹ thuật bám sát theo chính ngữ cảnh dự án thực tế trong CV của ứng viên.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_3_xem_ket_qua_ung_vien.jpg" alt="Kết quả đánh giá" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Bước 3: Tổng quan kết quả đánh giá CV</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_phan_tich_diem_so.jpg" alt="Phân tích điểm số" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Biểu đồ chi tiết phân tích điểm số mức độ phù hợp</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_phan_tich_ung_vien.jpg" alt="Phân tích ứng viên" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Đánh giá điểm mạnh/điểm yếu của ứng viên</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_muc_do_phu_hop.jpg" alt="Đánh giá mức độ phù hợp" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Chi tiết độ phù hợp theo yêu cầu của công việc</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_ky_nang.jpg" alt="Đánh giá kỹ năng" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Các kỹ năng đạt được và kỹ năng cần cải thiện</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_khuyen_nghi.jpg" alt="Khuyến nghị tuyển dụng" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Khuyến nghị từ AI đối với hồ sơ ứng viên</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_cau_hoi_phong_van.jpg" alt="Cảnh bản câu hỏi phỏng vấn" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Bộ câu hỏi phỏng vấn kỹ thuật tự động sinh ra</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_van_ban_trich_xuat.jpg" alt="Văn bản trích xuất" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Nội dung text thô trích xuất từ CV của ứng viên</p>
  </div>
</div>

### 5. Danh sách ứng viên, Xếp hạng & Debugger
Hệ thống hỗ trợ lưu trữ lịch sử các lượt match và xếp hạng độ phù hợp để nhà tuyển dụng dễ dàng so sánh các hồ sơ ứng viên.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_sach_CV.jpg" alt="Danh sách CV" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Quản lý kho CV của ứng viên</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_lich_su_danh_gia_CV_JD.jpg" alt="Lịch sử đánh giá" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Lịch sử đánh giá các ứng viên</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_xep_hang_ung_vien_phu_hop.jpg" alt="Xếp hạng ứng viên" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Xếp hạng độ phù hợp của ứng viên theo JD</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_thong_tin_go_loi_debugger.jpg" alt="Thông tin gỡ lỗi" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Trang thông tin gỡ lỗi hệ thống (Developer logs/debug info)</p>
  </div>
</div>
