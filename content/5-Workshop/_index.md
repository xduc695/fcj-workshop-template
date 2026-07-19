---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
# Deploying High-Concurrency Payment Gateway on AWS ECS Fargate with Private Subnets, RDS PostgreSQL, and S3 Backup

#### Overview

In this workshop, we will manually build and deploy a complete, secure, and highly available cloud infrastructure on AWS for a **High-Concurrency Payment Gateway** application.

The system will be designed according to enterprise security standards, including **Public/Private Subnets** segregation, using an **Application Load Balancer (ALB)** to receive and route traffic, running **backend microservices** bundled with a **Redis sidecar** on **AWS ECS Fargate**, connecting to an internal **Amazon RDS PostgreSQL** database, and setting up an **S3 Backup & Recovery** mechanism via the **Snapshot Export** feature integrated with a **KMS Key**.

#### Practice content

1. [Workshop Overview](5.1-Workshop-overview/)
2. [Environment Preparation & AWS ECR](5.2-Prerequiste/)
3. [VPC Networking Setup](5.3-VPC-Networking/)
4. [Security Groups Setup](5.4-Security-Groups/)
5. [Initialize RDS PostgreSQL in Private Network](5.5-RDS-Database/)
6. [Application Load Balancer Configuration](5.6-Load-Balancer/)
7. [Deploy ECS Fargate](5.7-ECS-Fargate/)
8. [Configure CloudWatch Alarm & SNS Notification](5.8-CloudWatch-Alarm/)
9. [Integrate S3 Backup & Recovery](5.9-S3-Backup/)
10. [Verification & Acceptance](5.10-Verification/)
11. [Resource Cleanup](5.11-Cleanup/)