---
title: "5.1 & 5.2 - Introduction & Prerequisites"
date: 2026-07-10
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

# 5.1. Introduction

This lab provides detailed instructions on how to comprehensively deploy the **Resume Fit** system on the AWS cloud platform. Resume Fit is an AI application that helps quickly and transparently evaluate the compatibility between candidate profiles (CVs) and job descriptions (JDs) to support recruitment decisions.

The system is designed following standard architecture on AWS, ensuring high scalability and availability. Core components include: Isolated Network (VPC), Flexible Compute Servers (EC2, Auto Scaling Group), Relational Database (RDS PostgreSQL), Object Storage (S3), Asynchronous Processing Queue (SQS), Monitoring Service (CloudWatch), and Secrets Management (Secrets Manager).

### Architecture Diagram

<div style="display: grid; grid-template-columns: 1fr; gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Blank diagram.jpg" alt="Architecture Diagram" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.15); transition: transform 0.3s ease;" onmouseover="this.style.transform='scale(1.01)'" onmouseout="this.style.transform='scale(1)'">
    <p style="text-align: center; color: #666; margin-top: 10px; font-style: italic;">Resume Fit AWS Architecture Overview</p>
  </div>
</div>

# 5.2. Prerequisites

* An AWS account with Administrator privileges.
* Basic AWS IAM configuration to grant permissions for services.
* Basic knowledge of Linux shell and Docker.
