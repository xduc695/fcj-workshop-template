---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.8. </b> "
---
### Week 8 Objectives:

* Create database, deploy DTO models, standardize API Responses, and build a Global Exception Handling mechanism for the High-Concurrency Payment Gateway project.
* Research and deploy a solution to optimize EC2 operational costs by automating instance start/stop schedules using AWS Lambda.
* Research Serverless architecture and practice building an automated image processing system using AWS Lambda, performing CRUD operations on Amazon DynamoDB.
* Research and practice deploying a Web Front-end application connected to a Serverless Backend system by configuring Amazon API Gateway as an intermediate request router.
* Research and practice using the open-source AWS SAM framework to model applications using YAML syntax, automating the conversion process to CloudFormation.
* Research the Amazon Cognito service and practice integrating a user management, authentication, and authorization solution.
* Research and practice deploying monitoring, testing, and optimization solutions for Serverless systems using Amazon CloudWatch combined with AWS X-Ray.
* Design and deploy a Payment Service ensuring High Concurrency processing capabilities, integrating an Idempotency mechanism to prevent double-spending.

### Tasks to be implemented this week:
| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Design data structures and deploy core components for the High-Concurrency Payment Gateway project:<br>&emsp; + Database Schema (Optimal structure design)<br>&emsp; + DTO (Standardized object model)<br>&emsp; + API Response (Defined response structure)<br>&emsp; + Global Exception Handling<br>&emsp; + Performance Optimization<br> - Design and deploy the Payment Service ensuring High Concurrency:<br>&emsp; + Separate Transactions from HTTP Calls, optimize Connection Pool<br>&emsp; + Idempotency Mechanism (prevent double-spending)<br>&emsp; + Inter-service Error Handling<br>&emsp; + Data Consistency | 06/08/2026 | 06/08/2026 | <https://github.com/LonggTran/high-concurrency-payment-gateway> |
| Tuesday | - Research EC2 cost optimization through automated start/stop using AWS Lambda: <br> - **Practice:** <br>&emsp; + Create Tags for EC2 Instances <br>&emsp; + Create Role for Lambda Function <br> &emsp; + Create Lambda Function for Stop instances <br> &emsp; + Create Lambda Function for Start instances<br> &emsp; + Check cost optimization results<br> - Research Serverless architecture, practice image processing and DynamoDB CRUD: <br> - **Practice:** <br>&emsp; + Create Image Processing Lambda Function <br>&emsp; + Create S3 Bucket <br> &emsp; + Create IAM Policy and test Lambda Function <br>&emsp; + Create and Manage DynamoDB Table <br> &emsp; + Create Lambda Function to write data to DynamoDB | 06/09/2026 | 06/09/2026 | <https://000022.awsstudygroup.com/><br><https://000078.awsstudygroup.com/> |
| Wednesday | - Practice deploying Web Front-end connected to Serverless Backend via API Gateway and AWS SAM: <br> - **Practice:** <br>&emsp; + Deploy front-end host with S3 Static website hosting (based on SAM) <br>&emsp; + Create DynamoDB table <br>&emsp; + Deploy Lambda functions for read/write/delete and image processing (based on SAM) <br>&emsp; + Configure API Gateway to interact with Lambda functions <br>&emsp; + Create GET/POST/DELETE APIs <br>&emsp; + Install and enable CORS <br>&emsp; + Test APIs with Postman and Front-end | 06/10/2026 | 06/10/2026 | <https://000079.awsstudygroup.com/><br><https://000080.awsstudygroup.com/> |
| Thursday | - Research Amazon Cognito and integrate secure authentication for Web Front-end: <br> - **Practice:** <br>&emsp; + Create User Pool <br>&emsp; + Create API and Lambda functions to handle registration and login via SAM<br>&emsp; + Perform registration and login on the web to test front-end | 06/11/2026 | 06/11/2026 | <https://000081.awsstudygroup.com/> |
| Friday | - Research Serverless monitoring, testing, and optimization using CloudWatch and X-Ray: <br> - **Practice:** <br>&emsp; + Debug with CloudWatch logs <br>&emsp; + Create custom metrics with CloudWatch metric <br>&emsp; + Create alarms with CloudWatch Alarm <br>&emsp; + Trace Lambda function requests with X-ray | 06/12/2026 | 06/12/2026 | <https://000085.awsstudygroup.com/> |

### Week 8 Achievements:

**1. High-Concurrency Payment Gateway Architecture Code (Monday)**
* Designed data structures and initialized the Database Schema optimally, accurately establishing primary keys, foreign keys, and Constraints to preserve data integrity.
* Deployed the DTO object model and defined a unified JSON Base Response structure standardizing output data and HTTP Status Codes.
* Built a centralized Global Exception Handling mechanism (`ControllerAdvice`) to format error messages and hide sensitive information.
* Optimized high-load processing and Connection Pools: Separated Transaction logic from HTTP Calls, rapidly freeing DB connections to prevent bottlenecks.
* Deployed an Idempotency Mechanism against duplication, integrating `Unique Constraints` to prevent double-spending. Built inter-service error handling and strict HTTP Timeouts.

**2. EC2 Auto-Stop & Serverless Image Processing (Tuesday)**
* Automated EC2 schedules: Attached `environment_auto: true` Tags, created IAM Role `dc-common-lambda-role`, programmed 2 Lambda functions (`auto-start`, `auto-stop`) in Python (Boto3) connecting to Slack. Configured EventBridge Rules.
* Result: EC2 successfully transitioned states, Slack channel received real-time notifications reporting accurate instance IDs.
![EC2 Stopped](/images/80.png)
![Slack message](/images/81.png)
* Initialized 2 S3 Buckets, configured Event Triggers. Deployed the `resize-image` Lambda to automatically resize and sync to the destination bucket.
![S3 Resize Successful](/images/82.png)
* Programmed the `book_create` Lambda function to write `put_item` data to the `Books` DynamoDB On-demand table. Successful Test Event.
![DynamoDB Explore Items](/images/83.png)

**3. API Gateway, CORS & SAM Automation (Wednesday)**
* Configured S3 Static Website Hosting to distribute the Front-end publicly. Initialized a REST API Gateway (Lambda Proxy Integration) supporting binary `multipart/form-data`, enabled CORS.
* Postman testing returned 200 OK, Front-end linked to endpoints displayed full real-time CRUD features.
![Postman API Test Result](/images/84.png)
![Front-end Interface Verification](/images/85.png)
* Automated infrastructure using AWS SAM YAML (`template.yaml`). Synced via CloudFormation `sam deploy` command, packaging 4 Lambda functions (`books_list`, `book_create`, `book_delete`, `resize_image`).
![Postman Integration Verification](/images/86.png)
![Front-end System Validation](/images/87.png)

**4. Amazon Cognito Authentication & Authorization (Thursday)**
* Initialized a User Pool with Email identification. Configured App Client for the `ALLOW_USER_PASSWORD_AUTH` flow. Programmed 3 Lambda functions (`Register`, `Confirm`, `Login`). Automated SAM synchronization.
* Front-end Testing: Sent Registration confirmation code to email and successfully logged in to accurately receive secure Tokens.
![Cognito Verification Mail](/images/88.png)
![Front-end Authentication Success](/images/89.png)

**5. Monitoring & Analytics with CloudWatch, X-Ray (Friday)**
* Leveraged Log Streams to extract runtime errors (e.g., incorrect table name configurations). Defined custom metrics pushed via the `put_metric_data` method.
![CloudWatch Log Debugging](/images/90.png)
* Established CloudWatch Alarms and Amazon SNS to send warning emails when the `staging` environment exceeded DynamoDB connection error thresholds.
* Enabled AWS X-Ray (using the `aws_xray_sdk` library), plotting call architecture maps to track detailed interaction request latencies.
![AWS X-Ray Trace Service Map & Timeline](/images/91.png)
