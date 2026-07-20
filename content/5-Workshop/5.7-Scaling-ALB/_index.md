---
title: "Auto Scaling & Load Balancing"
date: 2026-07-10
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

# 5.7. Auto Scaling and Load Balancing Configuration

## 5.7.1. Configure AMI and Launch Template

1. Standardize the configured EC2 environment by creating an Amazon Machine Image (AMI) named `ResumeMatching-Backend-AMI`.
2. From this AMI, create a **Launch Template** named `ResumeMatching-LT` containing standard hardware, networking, and security configurations.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_AMIs.jpg" alt="Create AMI" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_launch_template.jpg" alt="Create Launch Template" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.7.2. Auto Scaling Group (ASG)

1. Create an Auto Scaling Group named `ResumeMatching-ASG` and link it to the `ResumeMatching-LT` Launch Template.
2. Edit the Desired capacity to `2`. The ASG will automatically launch new EC2 instances in an `Initializing` state for redundancy and scaling.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_ASG.jpg" alt="Create Auto Scaling Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ASG_tao_them_EC2.jpg" alt="ASG Scaling Out Instance" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ASG_tao_EC2_moi_sau khi_cap_nhat_AMI.jpg" alt="ASG Replacing Instance after AMI update" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.7.3. Target Group and Application Load Balancer

1. Create a **Target Group** named `ResumeMatching-TG` with target type `Instance` using HTTP protocol on port `8080` (or `80` depending on container config).
2. Initialize an **Application Load Balancer (ALB)** named `ResumeMatching-ALB`. Select the Scheme as `Internet-facing` to receive traffic from the internet, listen across 2 Availability Zones, and route traffic to the backend instances via the Target Group.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_target_group.jpg" alt="Create Target Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_ALB.jpg" alt="Create Application Load Balancer" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
