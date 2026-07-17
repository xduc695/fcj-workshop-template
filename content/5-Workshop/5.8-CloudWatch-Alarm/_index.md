---
title : "Configure CloudWatch Alarm & SNS Notification"
date : 2024-01-01 
weight : 8
chapter : false
pre : " <b> 5.8. </b> "
---

In this section, we will set up a real-time **Email notification** system using **Amazon SNS** in coordination with **Amazon CloudWatch Alarm** when the number of requests to the **Application Load Balancer (ALB)** exceeds the configured **threshold**.

#### Steps to configure:

1. [Create SNS Topic & Subscribe Email](5.8.1-Create-SNS/)
2. [Create CloudWatch Alarm for RequestCount](5.8.2-Create-Alarm/)
3. [Simulate Load & Test Alarm](5.8.3-Load-Testing/)
