---
title : "Configure Application Load Balancer"
date : 2024-01-01 
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

In this section, we will set up a public **Application Load Balancer (ALB)** to route traffic from the Internet: By default, it forwards to the Frontend (port 80), and API requests with the path `/api/*` will be forwarded to the API Gateway Backend (port 8080).

#### Steps to configure:

1. [Create Target Groups](5.6.1-Create-Target-Groups/)
2. [Initialize Application Load Balancer](5.6.2-Create-ALB/)
3. [Configure Listener Rules for API Gateway](5.6.3-Configure-Listener-Rules/)
