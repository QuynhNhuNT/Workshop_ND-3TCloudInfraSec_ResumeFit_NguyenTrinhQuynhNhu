---
title: "5.6 - Relational Database (RDS)"
date: 2026-07-10
weight: 5
chapter: false
pre: " <b> 5.6. </b> "
---

# 5.6. Relational Database Service (RDS) Setup

## 5.6.1. Configure Secrets Manager

1. Navigate to **AWS Secrets Manager**, and create a secret named `ResumeMatching-Secrets` to secure sensitive values.
2. Configure the **Secret value** containing key/value entries such as `HOST` (to be updated later with the RDS Endpoint), `PORT` (`5432`), `USERNAME`, `PASSWORD`, and the application's `OPENAI_API_KEY`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_Secret.jpg" alt="Create Secret" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Cap_nhat_Secrets_manager.jpg" alt="Update Secrets Manager" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.6.2. Create RDS PostgreSQL Database

1. Open the **RDS** console, select **Subnet groups** and create a database subnet group named `resumematching-dbsubnetgroup` referencing the project VPC, grouping subnets `Private-DB-A` and `Private-DB-B` together.
2. Proceed to initialize the Database (DB identifier: `resume-matching-db`) with the **PostgreSQL** Engine and instance class `db.t3.micro`.
3. Once successfully created, copy the Database Endpoint and update the `HOST` key value in Secrets Manager.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_DB_Subnet_Group.jpg" alt="Create DB Subnet Group" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_RDS_database.jpg" alt="Create RDS PostgreSQL" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
