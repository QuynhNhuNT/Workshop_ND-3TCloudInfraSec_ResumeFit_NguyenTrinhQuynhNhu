---
title: "Worklog Week 8"
date: 2026-06-29
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Objectives of Week 8:
* Deploy web servers on EC2 with ALB load balancing and RDS/DynamoDB database persistence.
* Build Backend REST APIs using API Gateway and AWS Lambda for serverless computation.
* Realize intelligent features by calling Large Language Models on Amazon Bedrock from Lambda.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | References |
| --- | --- | --- | --- | --- |
| Mon | - Set up EC2 instances hosting the Web Frontend and link them to the ALB. | 08/06/2026 | 08/06/2026 | [Documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/api-methods-run.html) |
| Tue | - Deploy Database engines (RDS or DynamoDB) in Private Subnets. Set up Security Group rules to limit connection access to EC2/Lambda. | 09/06/2026 | 09/06/2026 | [Reference](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerToRDS.html) |
| Wed | - Program Backend APIs on AWS Lambda and expose them using API Gateway. | 10/06/2026 | 10/06/2026 | [Documentation](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html) |
| Thu | - Assign IAM Role policies allowing Lambda to access DynamoDB and Amazon Bedrock.<br>- Code Lambda to invoke Claude models on Amazon Bedrock. | 11/06/2026 | 11/06/2026 | [Reference](https://docs.aws.amazon.com/bedrock/latest/userguide/bedrock-runtime_api.html) |
| Fri | - Code Web Frontend (React/Static HTML) to consume API Gateway endpoints.<br>- Run End-to-End integration tests between Web, API, DB, and AI. | 12/06/2026 | 12/06/2026 | [FCAJ Learning Hub](https://cloudjourney.awsstudygroup.com/) |

### Achievements in Week 8:
* Deployed front-facing EC2 web servers and isolated RDS/DynamoDB databases.
* Built a working serverless API flow integrated with Amazon Bedrock AI.
* Completed integration testing of the whole application flow.
