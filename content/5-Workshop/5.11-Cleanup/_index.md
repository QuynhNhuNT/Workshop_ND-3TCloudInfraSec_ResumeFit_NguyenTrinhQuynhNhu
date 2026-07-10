---
title: "5.11 - Clean up Resources"
date: 2026-07-10
weight: 10
chapter: false
pre: " <b> 5.11. </b> "
---

# 5.11. Clean up Resources (Clean up)

After completing the workshop and testing, to avoid incurring unnecessary storage and infrastructure maintenance costs on AWS, proceed with cleaning up resources in the following order:

1. Delete the Auto Scaling Group to prevent the system from automatically relaunching servers, then manually Terminate any remaining EC2 Instances.
2. Delete the Application Load Balancer and Target Group.
3. Delete the RDS Database (uncheck final Snapshot creation if data retention is unnecessary) and the RDS Subnet Group.
4. Delete the NAT Gateways, wait for the status to transition to Deleted, then Release the Elastic IPs.
5. Tear down VPC Endpoints, Route Tables, Internet Gateways, Subnets, and finally delete the VPC itself.
6. Empty all objects within the S3 bucket, then proceed to Delete the Bucket.
7. Delete Secrets Manager secrets.
8. Delete SQS Queues.
9. Delete Key Pairs and IAM Roles created for the lab.
