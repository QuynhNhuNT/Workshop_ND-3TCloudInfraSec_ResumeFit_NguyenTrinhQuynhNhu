---
title: "Worklog Week 9"
date: 2026-06-29
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Objectives of Week 9:
* Perform Load Testing on the infrastructure to evaluate Auto Scaling Group scaling performance.
* Create centralized CloudWatch Dashboards and audit administrative actions using CloudTrail.
* Analyze project spending trends via AWS Cost Explorer and implement cost-saving optimizations.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | References |
| --- | --- | --- | --- | --- |
| Mon | - Run load testing tools (like Apache Bench, Locust) against the ALB endpoint. | 15/06/2026 | 15/06/2026 | [Documentation](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-explorer-comparison.html) |
| Tue | - Observe Auto Scaling Group metrics to verify successful scale-up and scale-down behaviors. | 16/06/2026 | 16/06/2026 | [Reference](https://aws.amazon.com/solutions/implementations/distributed-load-testing-on-aws/) |
| Wed | - Build a centralized CloudWatch Dashboard displaying EC2 CPU metrics, ALB Request Counts, Lambda Latencies, and RDS Connections. | 17/06/2026 | 17/06/2026 | [Documentation](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html) |
| Thu | - Enable AWS CloudTrail auditing. Run IAM Access Analyzer to scan for over-permissive policies. | 18/06/2026 | 18/06/2026 | [Reference](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) |
| Fri | - Analyze AWS Billing dashboards and Cost Explorer charts. Terminate unused volumes and scale down DB instances to optimize costs. | 19/06/2026 | 19/06/2026 | [FCAJ Learning Hub](https://cloudjourney.awsstudygroup.com/) |

### Achievements in Week 9:
* The system passed stress testing and auto-scaled out under heavy simulation load.
* Completed a CloudWatch Dashboard for real-time monitoring of resource health.
* Shaved off 25% of infrastructure expenses through optimization cleanups.
