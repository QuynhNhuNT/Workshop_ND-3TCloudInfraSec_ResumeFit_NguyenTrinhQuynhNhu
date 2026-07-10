---
title: "Worklog Week 4"
date: 2026-06-29
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Objectives of Week 4:
* Configure Auto Scaling Groups (ASG) and Application Load Balancer (ALB) for high availability.
* Monitor resources, gather logs, and set up system alarms using Amazon CloudWatch.
* Manage DNS resolution using Route 53 and optimize network-level security (NACLs/Security Groups).

### Tasks to implement this week:
| Day | Task | Start Date | End Date | References |
| --- | --- | --- | --- | --- |
| Mon | - Create Launch Templates, configure Auto Scaling Groups (ASG) and Application Load Balancers (ALB) for load distribution. | 11/05/2026 | 11/05/2026 | [Documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html) |
| Tue | - Test Auto Scaling behavior by running a CPU stress script on active EC2 instances. | 12/05/2026 | 12/05/2026 | [Reference](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-load-balancer.html) |
| Wed | - Configure CloudWatch Metrics and create CloudWatch Alarms to send email alerts via SNS when CPU exceeds 80%. | 13/05/2026 | 13/05/2026 | [Documentation](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html) |
| Thu | - Collect application logs using the CloudWatch Logs Agent to track software exceptions. | 14/05/2026 | 14/05/2026 | [Reference](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) |
| Fri | - Purchase/Configure a domain name in Route 53, pointing its DNS alias to the ALB.<br>- Set up optimized NACLs and Security Groups to secure traffic flow. | 15/05/2026 | 15/05/2026 | [FCAJ Learning Hub](https://cloudjourney.awsstudygroup.com/) |

### Achievements in Week 4:
* Successfully configured ASG and ALB, enabling the application infrastructure to handle sudden traffic surges.
* Set up CloudWatch Alarms that automatically trigger email alerts upon anomalies.
* Pointed Route 53 domain alias to the ALB and enhanced security using customized network rules.
