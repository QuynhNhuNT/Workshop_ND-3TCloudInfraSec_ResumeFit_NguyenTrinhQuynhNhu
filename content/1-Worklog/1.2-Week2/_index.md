---
title: "Worklog Week 2"
date: 2026-06-29
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Objectives of Week 2:
* Master foundational concepts of VPC, Subnets, Security Groups, and EC2.
* Practice building basic network infrastructure and launching EC2 virtual servers.
* Understand AWS resource permission delegation (IAM Role for EC2) and monitor service costs.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | References |
| --- | --- | --- | --- | --- |
| Mon | - Study concepts of VPC, Public/Private Subnets, Internet Gateway (IGW), and Route Tables to establish an isolated network environment. | 27/04/2026 | 27/04/2026 | [Documentation](https://docs.aws.amazon.com/vpc/index.html) |
| Tue | - Launch an Amazon EC2 instance.<br>- Configure Security Groups to allow SSH (Port 22) and HTTP (Port 80) traffic. | 28/04/2026 | 28/04/2026 | [Reference](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) |
| Wed | - Learn about IAM Roles and how they differ from IAM Users.<br>- Create an IAM Role for S3 Read-Only access and attach it to the EC2 instance. | 29/04/2026 | 29/04/2026 | [Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) |
| Thu | - Connect to the EC2 instance via SSH using a Key Pair from the local machine.<br>- Install Nginx/Apache web server on EC2 to serve a basic webpage. | 30/04/2026 | 30/04/2026 | [Reference](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| Fri | - Check billing details for EC2 on the Billing Console.<br>- Complete the 3 foundational labs outlined in the online learning path. | 01/05/2026 | 01/05/2026 | [FCAJ Learning Hub](https://cloudjourney.awsstudygroup.com/) |

### Achievements in Week 2:
* Understood VPC virtual network structure and successfully launched EC2 instances.
* Implemented secure IAM Roles for EC2 permissions (preventing Access Keys storage on servers).
* Successfully completed 3 foundational labs and accessed the Nginx web server from the Internet.
