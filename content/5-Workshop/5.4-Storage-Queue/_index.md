---
title: "Storage & Queue Services"
date: 2026-07-10
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

# 5.4. Storage and Queue Services

## 5.4.1. Initialize S3 Bucket

1. Switch to the **S3** service, and click **Create bucket** to create storage space for candidate CVs and documents.
2. Define a bucket name following the pattern `resume-matching-storage-[AWS-ACCOUNT-ID]-us-east-1`.
3. Under the **Permissions** tab, modify the **Cross-origin resource sharing (CORS)** configuration. Add the JSON structure specifying `AllowedMethods` to include `GET`, `PUT`, and `POST` to enable the web application to upload files directly to the bucket.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_S3.jpg" alt="Create S3 Bucket" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Bo_sung_CORS_S3.jpg" alt="Configure CORS S3" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Create_Folder_S3.jpg" alt="Create S3 Folder" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>

## 5.4.2. Initialize SQS Queues

Utilize message queuing to decouple heavy AI processing workloads from the main web server response cycle.

1. Navigate to the **SQS** interface. Create a Standard queue named `ResumeMatching-DLQ` (Dead Letter Queue) to catch messages that fail during processing.
2. Initialize the main queue named `ResumeMatching-Queue`.
3. Enable the **Dead-letter queue** feature on the main queue, point it to the ARN of `ResumeMatching-DLQ`, and set `Maximum receives` to `3`.

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px;">
  <div>
    <img src="/images/5-Workshop/Tao_queue.jpg" alt="Initialize SQS Queue" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
  <div>
    <img src="/images/5-Workshop/Tao_main_queue.jpg" alt="Create Main Queue with DLQ" style="width: 100%; border-radius: 12px; box-shadow: 0 4px 12px rgba(0,0,0,0.1);">
  </div>
</div>
