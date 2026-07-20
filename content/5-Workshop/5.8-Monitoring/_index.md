---
title: "System Monitoring"
date: 2026-07-10
weight: 8
chapter: false
pre: " <b> 5.8. </b> "
---

# 5.8. System Monitoring and High Availability (Monitoring)

Monitoring is mandatory to ensure traffic is correctly distributed and Auto Scaling rules trigger as expected.

## 5.8.1. Verify Auto Scaling Group Operations

1. Access the **EC2** service, and navigate to the **Instances** menu.
2. Observe the system automatically creating new EC2 instances named `ResumeMatching-ASG-Instance` distributed evenly across different Availability Zones.
3. Some older instances may display a `Terminated` status. This proves that the ASG is functioning correctly: automatically reclaiming old instances and launching new ones upon configuration updates or instance failure.

## 5.8.2. Verify Target Group Health Checks

1. Under the **Load Balancing** section, select **Target Groups** and click on the system's Target Group.
2. Switch to the **Targets** tab and observe the **Registered targets** table.
3. Confirm that the `Health status` column displays a green `Healthy` status for the instances, proving the web server has started and is ready to accept requests from the Load Balancer.

<div style="display: grid; grid-template-columns: 1fr; gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Target_group_healthy_check.jpg" alt="Target Group Health Check" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.8.3. Performance Monitoring via CloudWatch

1. Access **CloudWatch** and select the **Metrics** menu to monitor deeper parameters.
2. **For EC2**: Filter for the EC2 Namespace, and choose `CPUUtilization`. Observe the graphs to spot usage spikes (e.g., `81.9%`) when the AI executes heavy tasks, which helps you set scaling thresholds for the ASG.
3. **For ALB**: Filter metrics for `RequestCount` and `TargetResponseTime`. The correlation between the spike in request count and the change in response time (e.g., `660.4 ms`) helps evaluate the smoothness of the user experience.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/CloudWatch_dang_monitor_EC2.jpg" alt="CloudWatch Monitor EC2" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/EC2_Metrics.jpg" alt="EC2 Metrics" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/CloudWatch_monitor_Load_Balancer.jpg" alt="CloudWatch Monitor Load Balancer" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/ALB_Metrics.jpg" alt="ALB Metrics" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
