---
title: "Blogs Posted"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

This section lists and introduces the blogs I have posted to [AWS Study Group](https://www.facebook.com/groups/awsstudygroupfcj):

###  [Blog 1 - SYSTEM MONITORING ON AWS: STREAMING CLOUDWATCH METRICS TO OPENTELEMETRY COLLECTOR IN VPC USING LAMBDA](3.1-Blog1/)
This blog introduces a push-based observability solution using AWS Lambda as a secure relay station to stream metrics from CloudWatch Metric Streams directly to an internal OpenTelemetry Collector isolated inside a private VPC subnet.

###  [Blog 2 - BUILDING AN AI GATEWAY TO GOVERN AMAZON BEDROCK WITH API GATEWAY](3.2-Blog2/)
This blog shares practical design experience building an AI Gateway using Amazon API Gateway, Lambda Authorizers, and Lambda Integrations to authorize client calls, manage tenant isolation, rate limit requests, and govern large language model (LLM) costs on Amazon Bedrock.

###  [Blog 3 - A VERY COOL FEATURE OF AWS LAKE FORMATION](3.3-Blog3/)
This blog discusses the new capability in AWS Lake Formation to issue temporary credentials via the GetTemporaryDataLocationCredentials() API, allowing big data engines like EMR Spark to directly read and write files in S3 based on unified Lake Formation permissions.