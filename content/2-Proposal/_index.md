---
title: "Proposal"
date: 2026-07-10
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

### AI Resume Matching & Interview Preparation Platform

**1. Project Overview**

* **Goal:** A Web application that evaluates the matching degree between Resumes (CVs) and Job Descriptions (JDs), deployed on a standard AWS 3-Tier architecture.
* **AI Processing:** An EC2 cluster (Backend + Worker) is responsible for analyzing CVs and JDs by invoking OpenAI APIs via the Internet to optimize token consumption and minimize costs.

**2. Cloud Infrastructure Architecture (AWS)**

![AI Resume Matching & Interview Preparation Platform Architecture](/images/2-Proposal/resume-matching-architecture.png)

* **Edge & Global Layer:**
  * Content Delivery Network (CloudFront), WAF firewall, and authentication service are currently planned but not deployed (AWS account verification required), meaning they are not active production services yet.
  * Amazon S3 (Amazon Simple Storage Service) is used for general storage.
  * Users interact via the Internet Gateway (1) or upload files directly via Pre-signed URLs to a dedicated S3 storage (S3 CV/JD Storage) (5).

* **Networking & Load Balancing (Inbound):**
  * VPC 10.0.0.0/16 serves as the foundation.
  * Internet Gateway (IGW) acts as the single entry point connecting to the Internet for both Inbound and Outbound traffic (via NAT Gateway).
  * An Application Load Balancer (ALB) is positioned across Availability Zones, receiving traffic from the IGW and distributing it to the Auto Scaling Group.

* **Application Tier (Compute):**
  * The EC2 cluster (Backend + Worker) is placed within isolated Private App Subnets (Private App Subnet A & Private App Subnet B), spanning across 2 Availability Zones (AZ A & AZ B) and managed by an Auto Scaling Group (ASG) to auto-scale based on load.
  * Internal Communication: EC2 (AZ A) connects to the S3 storage service and SQS (6), backed by a Dead Letter Queue (DLQ).
  * OpenAI API flow (AZ B) is executed by EC2 (AZ B) routing outbound traffic through the NAT Gateway of Public Subnet B to reach the Internet Gateway. (Note: NAT Gateways are deployed in both Public Subnet A and Public Subnet B to ensure routing optimization).

* **Outbound & Internal Networking:**
  * There are **two NAT Gateways**, one in Public Subnet A and one in Public Subnet B, ensuring High Availability for Outbound traffic originating from the Private Subnets.
  * Communication to SQS and S3 is handled directly over the network, without utilizing VPC Endpoints.

* **Database Tier:**
  * Relational Database Service (RDS) running PostgreSQL configured with Multi-AZ.
  * Two Private DB Subnets (Private DB Subnet A & Private DB Subnet B) are secured under a Security Group.
  * RDS Primary (Master) is situated in AZ A. RDS Standby Replica is located in AZ B with real-time data replication (dashed line).
  * Connection flow: EC2 in AZ A connects directly to the RDS Primary (7). EC2 in AZ B connects to the RDS Standby Replica via RDS Endpoints.

* **Management & Monitoring:**
  * A dedicated Management & Security zone (Regional Security & Management) hosts AWS Systems Manager, Amazon CloudWatch (logs), and AWS Secrets Manager (API Key).

* **Deployment:**
  * Source code is hosted on GitHub (Manual Deployment), designated as a manual deployment workflow. No automated AWS CodeBuild or AWS CodePipeline is used in the current architecture.