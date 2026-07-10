---
title: "Worklog Week 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Objectives of Week 5:
* Implement Serverless architecture using AWS Lambda and Amazon API Gateway.
* Research Artificial Intelligence (AI) integration by connecting and invoking Amazon Bedrock models.
* Practice secure sensitive information management using AWS Secrets Manager.

### Tasks to implement this week:
| Day | Task | Start Date | End Date | References |
| --- | --- | --- | --- | --- |
| Mon | - Write AWS Lambda serverless functions using Python/Node.js to run backend logic. | 18/05/2026 | 18/05/2026 | [Documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) |
| Tue | - Setup REST/HTTP APIs using API Gateway to serve as endpoints for Lambda functions. | 19/05/2026 | 19/05/2026 | [Reference](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-with-lambda-integration.html) |
| Wed | - Handle CORS and configure security on API Gateway endpoints using IAM Authorizers or Cognito. | 20/05/2026 | 20/05/2026 | [Documentation](https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html) |
| Thu | - Research Amazon Bedrock and request model access (Claude, Llama) on the console.<br>- Code Lambda to invoke Bedrock APIs. | 21/05/2026 | 21/05/2026 | [Reference](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) |
| Fri | - Use AWS Secrets Manager to store database credentials and external API keys securely instead of hardcoding them. | 22/05/2026 | 22/05/2026 | [FCAJ Learning Hub](https://cloudjourney.awsstudygroup.com/) |

### Achievements in Week 5:
* Successfully established a Serverless architecture flow (API Gateway -> Lambda).
* Integrated Amazon Bedrock to invoke LLM text generation directly from Lambda backend.
* Secured database connection credentials and api keys using AWS Secrets Manager.
