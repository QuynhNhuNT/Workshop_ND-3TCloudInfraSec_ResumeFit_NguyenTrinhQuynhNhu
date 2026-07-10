---
title: "5.10 - Application Testing"
date: 2026-07-10
weight: 9
chapter: false
pre: " <b> 5.10. </b> "
---

# 5.10. Testing the Resume Fit Application

## 5.10.1. Verify Backend and Database Connectivity via ALB

1. Test using the ALB API endpoint (e.g., `http://[ALB-DNS-Name]/api/ready`) to receive the JSON response `{"status": "ready"}` proving the Backend and Database have successfully connected.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Test_hoat_dong_bang_DNS_cua_ALB.jpg" alt="Test ALB DNS" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tien_hanh_kiem_tra_cac_ket_noi.jpg" alt="Check Database connection" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.10.2. Step-by-Step UI Flow Walkthrough

### 1. Register & Login to System
Access the Frontend Domain/IP. Create an account and log in via the **Register** and **Login** screens to enter your workspace.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_dang_ky.jpg" alt="Register Screen" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">User Registration UI</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_dang_nhap.jpg" alt="Login Screen" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">User Login UI</p>
  </div>
</div>

### 2. Job Description (JD) Management
Create and manage the catalog of Job Descriptions (JDs) for profile matching.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_sach_JD.jpg" alt="JD List" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">List of Managed Job Descriptions</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_1_tao_ten_cong_viec_ung_tuyen.jpg" alt="Create Job" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Step 1: Initialize Job Position Details</p>
  </div>
</div>

### 3. Upload CV & JD for Analysis
Run the core workflow: upload candidate CVs (PDF/Docx format) mapping to the selected JD.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_2_upload_CV_JD.jpg" alt="Upload CV & JD" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Step 2: Select Job Description and Upload Candidate CV</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_2_upload_CV_JD_Part-2.jpg" alt="Confirm upload" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Review files before initiating system analysis</p>
  </div>
</div>

### 4. AI Resume Matching Reports
Initiate the analysis. The AI backend (Worker) invokes the OpenAI API to yield a comprehensive **Candidate Analysis Report**:

* **Score Analysis**: Overview of rank level compatibility and overall matching percentage (e.g., 60%).
* **Skill Analysis**: Highlights missing professional skills (e.g., Cybersecurity, C#, ELK, etc.).
* **Recommendation & Interview Questions**: Automatically generates technical interview questions tailored precisely to the candidate's actual projects found in their CV.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_buoc_3_xem_ket_qua_ung_vien.jpg" alt="Report overview" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Step 3: Overview of CV evaluation results</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_phan_tich_diem_so.jpg" alt="Score chart" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Detailed score analysis charts</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_phan_tich_ung_vien.jpg" alt="Candidate weaknesses/strengths" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Candidate SWOT and detailed breakdown</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_muc_do_phu_hop.jpg" alt="Compatibility details" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Job role compatibility details</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_ky_nang.jpg" alt="Skills breakdown" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Matching skills vs. missing gaps</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_khuyen_nghi.jpg" alt="Recruitment recommendation" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">AI recommendation summary on candidate</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_cau_hoi_phong_van.jpg" alt="Interview questions" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Generated technical interview questions</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_gia_van_ban_trich_xuat.jpg" alt="Extracted text" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Raw text extracted from candidate CV</p>
  </div>
</div>

### 5. Candidate Catalog, Ranking & Debugger
The system logs matching history and ranks candidates based on their suitability to help HR make quick comparisons.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_danh_sach_CV.jpg" alt="CV Inventory" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Manage CV database inventory</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_lich_su_danh_gia_CV_JD.jpg" alt="Evaluation logs" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Chronological match history logs</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_xep_hang_ung_vien_phu_hop.jpg" alt="Ranking board" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">Candidate matching rank leaderboard</p>
  </div>
  <div>
    <img src="/images/5-Workshop/giao diện/giao_dien_thong_tin_go_loi_debugger.jpg" alt="Developer Debugger logs" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
    <p style="text-align: center; color: #666; font-style: italic; margin-top: 8px;">System debugger and container logs console</p>
  </div>
</div>
