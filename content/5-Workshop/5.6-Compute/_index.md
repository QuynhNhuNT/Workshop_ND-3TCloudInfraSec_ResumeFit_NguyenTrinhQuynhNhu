---
title: "Compute & Server Configuration"
date: 2026-07-10
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

# 5.6. Compute Deployment and Server Configuration

## 5.6.1. Launch EC2 Backend Instance

1. Create an RSA **Key Pair** named `ResumeMatching-Key`.
2. In the EC2 Dashboard, launch an Instance named `ResumeMatching-Backend` using instance type `t3.micro` placed in the application VPC.
3. Wait for the Instance state to transition to `Running` and the Status checks to display `2/2 checks passed`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Key_Pair.jpg" alt="Create Key Pair" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_EC2_Backend.jpg" alt="Launch EC2 Backend" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.6.2. Connect and Install Software

1. Securely connect to the EC2 instance using **Systems Manager Fleet Manager**. Choose the running Managed node and click **Start terminal session**.
2. Execute the Git installation command to fetch the source code:
   ```bash
   sudo dnf install git
   ```
3. Install and start **Docker** to run containerized application:
   ```bash
   sudo dnf install -y docker
   sudo systemctl enable docker
   sudo systemctl start docker
   ```
4. Navigate to the `/opt` folder and clone the source code from GitHub:
   ```bash
   cd /opt
   sudo git clone http://github.com/thuanthien-tran/resume-fit.git
   sudo chown -R ssm-user /opt/resume-fit
   ```

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Connect_EC2_backend_bang_Systems_Manager.jpg" alt="Connect via Systems Manager" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cai_GIT.jpg" alt="Install Git" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cai_Docker.jpg" alt="Install Docker" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Kiem_tra_trang_thai_Docker.jpg" alt="Verify Docker Status" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div style="grid-column: span 2;">
    <img src="/images/5-Workshop/Clone_source_len_EC2.jpg" alt="Clone source code from GitHub" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
