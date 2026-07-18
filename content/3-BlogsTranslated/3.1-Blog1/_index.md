---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Automating Container Application Deployment to Amazon ECS Express Mode using GitHub Actions

In the DevOps era, optimizing the CI/CD pipeline to shorten the time to market for products is a top priority. When an application is containerized, the manual packaging and deployment process is often error-prone and time-consuming. 

An automated solution using **GitHub Actions** combined with **Amazon ECS Express Mode** helps simplify the entire infrastructure from networking and load balancing to resource provisioning without manual configuration. This article summarizes the architecture, operational process, and practical experiences when building a secure CI/CD pipeline, fully automated from source code to the live running environment.

---

## 1. Core Advantages of the Solution

The system is designed to optimize deployment speed and eliminate potential security risks thanks to modern mechanisms:

- **Secure Authentication via OIDC:** Instead of storing static credentials like long-term AWS Access Keys in GitHub Secrets (which poses a risk of data leakage), the system establishes a trust mechanism through OpenID Connect (OIDC). Every time the workflow runs, GitHub Actions will automatically assume a short-term IAM role to interact with AWS.
- **Infrastructure Automation with ECS Express Mode:** The outstanding point of Express Mode is its ability to automatically set up and manage complex components including: Application Load Balancer (ALB), Target Groups, Security Groups, CPU-based Auto Scaling mechanisms, and providing a ready-to-use access URL with an identity certificate from AWS.
- **Precise Version Management (Traceability):** Once built, the Docker image will be automatically tagged based on the first 7 characters of the Commit SHA. This helps the development team easily trace source code, control versions, and perform quick rollbacks when an incident occurs.

---

## 2. System Operational Process

The automated processing flow is triggered as soon as developers interact with the source code repository:

- **CI Stage (Continuous Integration):** When code is pushed to the `main` branch, GitHub Actions triggers the workflow. The system uses OIDC to securely connect with AWS, proceeds to build the Docker image from the source code, tags it according to the Commit SHA, and pushes the image to the private Amazon ECR repository.
- **CD Stage (Continuous Deployment):** After the image is successfully pushed, the `amazon-ecs-deploy-express-service` Action will call the AWS API to update the service. ECS Express Mode will automatically initialize/update the server cluster, orchestrate Tasks running on the serverless AWS Fargate platform, and smoothly route traffic from the Load Balancer to the new container.

---
![CI/CD Architecture Diagram](/images/106.png)
## 3. Technology Selection and System Roles

| System Component | Technology Used | Role in Architecture |
| :--- | :--- | :--- |
| **CI/CD Pipeline** | GitHub Actions | Automates the entire process of building, tagging, pushing, and triggering application deployment |
| **Container Storage** | Amazon ECR | Centralized storage and secure management of Docker Image versions |
| **Container Orchestration** | Amazon ECS Express Mode | Automatically manages services, network configurations, and load balancing for containers |
| **Serverless Compute** | AWS Fargate | Provides computing resources to run containers without managing EC2 instances |
| **Identity & Access** | IAM & OIDC Provider | Passwordless authentication, granting short-term permissions according to the Least Privilege principle |

---

## 4. Technical Considerations for Practical Deployment

Through the process of practicing configuration and optimizing the pipeline, a number of key points need to be noted to ensure stable system operation:

### Minimum Permissions for IAM Policy
To ensure information security, the IAM Policies attached to the `github-actions-ecs-role` need to be tightened. Instead of using the wildcard character `*` for all resources, limit it exactly to the ARN of the specific Amazon ECR Repository and Amazon ECS Cluster to prevent a hacked repository from interfering with other resources.

![IAM OIDC Role](/images/78.png)

### Monitor the Automation Process on GitHub Actions
When pushing code to the main branch, the entire packaging process from building the Dockerfile, logging into ECR, to calling the deploy command to ECS Express Mode needs to be closely monitored via real-time logs for early detection of dependency conflicts or permission errors.

![GitHub Actions Workflow](/images/77.png)

### Check Service Status on Amazon ECS Express Mode
After the workflow reports success, Express Mode will automatically create routing and load balancing configurations. The container application running on AWS Fargate can now be accessed directly through the default endpoint provided by AWS.

![Amazon ECS Express Service](/images/79.png)

---

## 5. Conclusion

The combination of GitHub Actions and Amazon ECS Express Mode brings a lean, powerful, and highly secure CI/CD solution for containerized applications. By freeing the burden of managing network and server infrastructure, the development team can fully focus on optimizing source code, improving product quality, and accelerating application release.

Original article: https://aws.amazon.com/blogs/containers/automated-deployments-with-github-actions-for-amazon-ecs-express-mode/
