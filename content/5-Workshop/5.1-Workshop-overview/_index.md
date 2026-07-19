---
title : "Introduction"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Introduction to High-Concurrency Payment Gateway System

The High-Concurrency Payment Gateway system deployed in this workshop is a microservices application built with **Spring Boot** (for Backend) and **React Vite** (for Frontend). The project includes the following component services:
- **API Gateway (Port 8080):** Receives all external requests and routes them to the corresponding internal services.
- **Account Service (Port 8082):** Manages customer accounts, registrations, and balances (Balance).
- **Payment Service (Port 8083):** Processes payment transactions and deposits/withdrawals, integrating an Idempotency mechanism using **Redis Distributed Lock**.
- **Transaction Service (Port 8084):** Manages transaction history and account reconciliation (Ledger).
- **Redis Cache/Lock:** Stores distributed locks to prevent duplicate transactions.

#### Secure Network Architecture Diagram (Private Subnet)

The deployment model on AWS applies an isolated security mechanism:

![diagram](/images/diagram.jpg)

#### Architectural highlights:
1. **Network Isolation:** Application Load Balancer (ALB) receives public traffic at the **Public Subnet** layer, while ECS Tasks and RDS PostgreSQL Database run entirely within the **Private Subnet** network to prevent the risk of port scanning or direct attacks.
2. **NAT Gateway:** ECS Tasks located in the Private Subnet do not have Public IPs but still connect Outbound to the Internet through the NAT Gateway to pull Docker images and push CloudWatch Logs.
3. **Monolithic Task:** 4 backend microservices are combined in a single Docker Image running simultaneously with a Redis container (sidecar) within the same ECS Task, helping to optimize Fargate operational costs.
4. **S3 Backup:** Securely backs up RDS PostgreSQL through the RDS Snapshot Export feature encrypted with a KMS Key to Amazon S3.