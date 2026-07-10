---
title: "5.4 - Security & Access Management"
date: 2026-07-10
weight: 3
chapter: false
pre: " <b> 5.4. </b> "
---

# 5.4. Security and Access Management

## 5.4.1. Initialize Security Groups

Configure virtual firewalls to control network traffic between resources at the protocol and port level.

1. **ALB Security Group** (`ResumeMatching-ALB-SG`): Open HTTP (`80`) and HTTPS (`443`) ports (TCP) with Source `0.0.0.0/0` to allow web access.
2. **Backend Security Group** (`ResumeMatching-Backend-SG`): Configure Inbound rules to allow HTTP protocol on TCP. The Source is restricted to traffic originating only from `ResumeMatching-ALB-SG`.
3. **Worker Security Group** (`ResumeMatching-Worker-SG`): Virtual firewall safeguarding the background Worker Server.
4. **Database Security Group** (`ResumeMatching-RDS-SG`): Open port `5432` (PostgreSQL). The Source strictly allows internal connections only from the Backend and Worker Security Groups.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_ALB_Security_Group.jpg" alt="Create ALB Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Backend_Security_Group.jpg" alt="Create Backend Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tạo_Worker_Security_Group.jpg" alt="Create Worker Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Database_Security_Group.jpg" alt="Create Database Security Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.4.2. Configure IAM Roles

Provide secure authorization for EC2 instances to communicate with other AWS services without hard-coding static Access Keys.

1. Navigate to the **IAM** service, create a role named `ResumeMatching-Backend-Role` to associate with the backend EC2 server.
2. Create a second role named `ResumeMatching-Worker-Role` dedicated to the Worker server. Attach AWS Managed policies like `AmazonSQSFullAccess` and appropriate S3 manipulation policies.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Backend_IAM_Role.jpg" alt="Create Backend IAM Role" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_Worker_IAM_Role.jpg" alt="Create Worker IAM Role" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
