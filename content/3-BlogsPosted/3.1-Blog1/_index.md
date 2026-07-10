---
title: "Blog 1"
date: 2026-07-10
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# SYSTEM MONITORING ON AWS: STREAMING CLOUDWATCH METRICS TO OPENTELEMETRY COLLECTOR IN VPC USING LAMBDA

Managing observability for large-scale cloud systems has always been a challenging problem, especially when enterprises want to balance cost, flexibility, and security. Although OpenTelemetry is gradually becoming the common standard helping organizations escape vendor lock-in, they face a significant technical barrier: how to stream metrics from AWS CloudWatch directly into internal collection systems strictly isolated within a VPC? To solve this problem, a solution using AWS Lambda as a data relay station from CloudWatch Metric Streams to the internal network has proven its outstanding effectiveness, ensuring data flows are always transmitted securely and in near real-time.

### KEY HIGHLIGHTS OF THIS PUSH-BASED OBSERVABILITY SOLUTION:

* **Shifting from Pull to Push model:** Using tools like Prometheus to continuously "pull" (poll) data causes API throttling, metric loss, and high costs. The "Push" model with CloudWatch Metric Streams completely solves this problem, enabling event-driven data transmission with sub-minute latency for real-time alerting.

* **Overcoming Amazon Data Firehose limitations:** Although Firehose supports pushing data to HTTP endpoints, it requires those to be public endpoints. To deliver data into a private subnet, AWS uses a Lambda Transform Function as a bridge. Firehose batches the data and invokes Lambda; then Lambda pushes metrics through the NLB deep into the VPC securely.

* **OpenTelemetry Collector is the heart of the system:** Running on Amazon EC2 instances inside the VPC, the Collector operates as a processing hub with 3 flexible components: Receivers (data ingestion), Processors (filtering, enriching data, masking sensitive data), and Exporters (sending data to diverse destinations like Grafana, AWS X-Ray, or Amazon OpenSearch).

* **Scalability and safe failover:** By using Network Load Balancer to distribute TCP traffic to EC2 instances, the system can easily scale horizontally. Additionally, an Amazon S3 bucket is configured as a failover destination for Firehose (though no storage costs are incurred if Lambda successfully pushes the data).

* **Cost optimization and eliminating Vendor Lock-in:** Using OpenTelemetry (Apache 2.0 license, completely free) helps enterprises eliminate the burden of third-party software licensing costs. Its standardization allows operations teams to freely switch monitoring backend platforms later without rebuilding the data collection pipeline.

### Solution Architecture Diagram

![CloudWatch Metric Stream to OpenTelemetry Collector Architecture](/images/3-BlogsPosted/blog1-cloudwatch-otel-architecture.png)

Overall, the clever combination of AWS services such as Lambda, Firehose, and Network Load Balancer has created a perfect bridge, closing the gap between public cloud services and closed internal networks. This architecture not only thoroughly addresses the latency and limitations of traditional APIs but also empowers technical teams to the fullest. By establishing an intelligent data transmission pipeline, enterprises can freely build a powerful, independent monitoring ecosystem that is budget-optimized and always ready to scale in the future without worrying about technology dependency risks.

Building a monitoring system is not hard — the challenge is making it secure, cost-effective, and technology-independent. What do you think about this Push-based architecture with Lambda and OpenTelemetry? If you are currently operating systems, is your biggest barrier the security story (getting metrics into a private VPC safely) or the infrastructure cost optimization problem? Let's discuss!

---

**Article link:** <https://www.facebook.com/groups/awsstudygroupfcj/permalink/2173544653410495/?rdid=CUzsR7GSYpgaIwjW>

**Reference guide:** <https://aws.amazon.com/vi/blogs/architecture/streaming-cloudwatch-metrics-to-vpc-based-opentelemetry-collectors-using-lambda/>