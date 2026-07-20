---
title: "References"
date: 2026-07-20
weight: 11
chapter: false
pre: " <b> 5.11. </b> "
---

# 5.11. References

## 1. Source code and demo

*   **Demo Link (Resume Fit):** [http://resumematching-alb-1223673352.us-east-1.elb.amazonaws.com](http://resumematching-alb-1223673352.us-east-1.elb.amazonaws.com)
*   **Source Code Repository:** [https://github.com/thuanthien-tran/resume-fit](https://github.com/thuanthien-tran/resume-fit)

## 2. AWS services used by the project

The project leverages a robust suite of AWS services to deploy the Resume Fit application in a secure, scalable microservices architecture:
*   **Networking:** Amazon VPC, Internet Gateway, and NAT Gateways (providing outbound internet access for private subnets securely).
*   **Compute:** Amazon EC2 (t3.micro) for the backend servers, integrated with an Auto Scaling Group and Launch Template to dynamically adjust capacity based on traffic.
*   **Load Balancing:** Application Load Balancer (ALB) distributes incoming application traffic across multiple EC2 instances.
*   **Database:** Amazon RDS PostgreSQL (Single-AZ) stores candidate metadata and system configuration.
*   **Storage & Messaging:** Amazon S3 (object storage for CV/PDF files) and Amazon SQS (asynchronous queue processing for AI tasks).
*   **Security & Monitoring:** AWS Secrets Manager for securing database credentials and API keys, alongside Amazon CloudWatch for centralized logging and metrics monitoring.

## 3. Cost Breakdown

Below is the estimated monthly cost analysis for running the system architecture 24/7 (730 hours/month) in the **US East (N. Virginia) – us-east-1** region. The estimations are based on AWS On-Demand Pricing.

| No | AWS Service | Configuration | Quantity | Estimated Monthly Cost (USD) | Notes | Total (USD) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Amazon VPC | Public/Private Subnets, Route Tables | 1 | 0.00 | Foundational service | 0.00 |
| 2 | Internet Gateway | Internet access for VPC | 1 | 0.00 | Free of charge | 0.00 |
| 3 | NAT Gateway | 730 hours ($0.045/hr) | 2 | 32.85 | Excludes data processing fees | 65.70 |
| 4 | Security Group | Stateful virtual firewall | - | 0.00 | Free of charge | 0.00 |
| 5 | Amazon EC2 | t3.micro Linux ($0.0104/hr) | 3 | 7.59 | 1 Backend + 2 in ASG | 22.77 |
| 6 | Amazon EBS | gp3, 30GB/instance ($0.08/GB) | 3 | 2.40 | Attached to EC2s | 7.20 |
| 7 | Launch Template & ASG | Auto Scaling Configuration | 1 | 0.00 | Free orchestration service | 0.00 |
| 8 | Application Load Balancer | Base price ($0.0225/hr) | 1 | 16.43 | Excludes LCU usage fees | 16.43 |
| 9 | Target Group | Traffic routing for ALB | 1 | 0.00 | Free of charge | 0.00 |
| 10 | Amazon RDS | db.t3.micro Single-AZ ($0.017/hr)| 1 | 12.41 | Running 730 hours | 12.41 |
| 11 | RDS Storage | 20 GB gp3 ($0.115/GB-mo) | 1 | 2.30 | DB storage volume | 2.30 |
| 12 | Amazon S3 | Standard tier (5 GB) | 1 | 0.12 | $0.023/GB-mo | 0.12 |
| 13 | Amazon SQS | Standard & DLQ | 2 | 0.00 | Within Free Tier (<1M reqs) | 0.00 |
| 14 | AWS Secrets Manager | $0.40/secret/month | 1 | 0.40 | Stores DB password/API keys | 0.40 |
| 15 | AWS Systems Manager | Session Manager | - | 0.00 | Free SSH alternative | 0.00 |
| 16 | Amazon CloudWatch | Basic Metrics + Logs | - | 0.00 | Within Free Tier limits | 0.00 |
| **Total** | | | | | | **127.33** |

*Note: The actual total cost might vary slightly due to minor Data Transfer Out and ALB LCU charges. However, given the project's minimal traffic, these are negligible.*

### Evaluation and Optimization Proposals

*   **Total Estimated Monthly Cost:** Approximately **$127.33 USD**.
*   **Cost Structure Analysis:** The most expensive resource is the **NAT Gateway** ($65.70, over 51% of the total cost), followed by **Amazon EC2 & EBS Compute resources** ($29.97, ~23%).
*   **Suitability for AWS Credits Limit:** With an estimated monthly burn rate of $127.33, this architecture is **safely within** the $200 AWS Credits limit. There is a comfortable margin of ~$72 to absorb unexpected data transfer costs or temporary auto-scaling bursts.
*   **Cost Optimization Strategies (without altering the core architecture):**
    *   **Resource Scheduling:** Although estimated for 24/7 usage, configuring the Auto Scaling Group to scale in to a single instance and disabling one NAT Gateway during off-hours (if High Availability is not strictly required outside evaluation periods) can yield massive savings.
    *   **Reduce EBS Volume Size:** Provisioning 30 GB gp3 per t3.micro instance is likely oversized for a stateless web application container. Reducing this to 10 GB or 15 GB will immediately cut storage costs.
    *   **Implement VPC Endpoints:** For services like S3 and Secrets Manager, setting up VPC Gateway or Interface Endpoints allows private EC2 instances to route traffic internally via the AWS backbone. This bypasses the NAT Gateway data processing fees for these specific requests.

## 4. Development and deployment

The development and deployment lifecycle adhered to modern standard practices:
*   Source code version control was maintained centrally on **GitHub**.
*   The application was **containerized using Docker**, ensuring environmental consistency from local development machines directly to production EC2 instances.
*   Infrastructure deployment was executed via the AWS Console, heavily relying on **EC2 User Data** within the Launch Template to automatically install dependencies and pull the latest Docker image whenever the Auto Scaling Group scales out.

## 5. Cost and resource cleanup

Because this architecture relies on hourly-billed services (especially NAT Gateways, EC2, and ALB), systematic resource cleanup after the demonstration phase is critical to prevent unwanted credit consumption. Resources must be terminated in reverse-dependency order:
1. Delete the Auto Scaling Group and Launch Template to stop the continuous spawning of new instances.
2. Delete the Application Load Balancer and its Target Group.
3. Manually terminate any remaining EC2 instances.
4. Delete the Amazon RDS database instance and its associated automated snapshots.
5. Delete the NAT Gateways and subsequently release the Elastic IPs.
6. Finally, tear down the Internet Gateway, Route Tables, Subnets, and the VPC itself.
