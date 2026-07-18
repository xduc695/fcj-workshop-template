---
title: "Event 3"
date: 2026-06-06
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
# "FCJ Community Day - From Zero to Cloud Hero" Report

### Purpose of the Event

- Equip in-depth technical knowledge about real-time architecture and network synchronization in cloud application development.
- Containerize applications, optimize DevOps infrastructure, and efficiently manage storage memory tiers.
- Introduce advanced artificial intelligence solutions via knowledge graph architecture to overcome traditional RAG limitations.
- Design a multi-layered smart cybersecurity system, combining firewalls and real-time machine learning models on AWS.
- Orient a practical career development roadmap from basic support technician to senior system operations expert.

### List of Speakers

- **Nguyen Quoc Bao** - Presented the topic **“Multiplayer in the Cloud: Connecting Godot Clients with AWS WebSockets”**, focusing on real-time serverless game architecture via WebSocket protocol and AWS API Gateway.
- **Bao Huynh** - Presented the topic **“Docker – A containerization technology”**, focusing on the nature of containerization, data layering mechanisms, and DevOps resource optimization compared to virtual machines (VMs).
- **Viet Phat** - Presented the topic **“GraphRAG: Build GraphRAG applications using Amazon Bedrock and Amazon Neptune”**, focusing on the solution of combining Knowledge Graphs and Vector databases to optimize context for LLMs.
- **Le Hoang Gia Dai** - Presented the topic **“WAF + ML for Cyber Attack Detection: Machine Learning-based Network Intrusion Detection System (NIDS) on AWS”**, focusing on a smart network intrusion detection system using the LightGBM model combined with AWS WAF.
- **Tran Trung Vinh** - Presented the topic **“From IT Helpdesk to Senior Sysadmin”**, sharing about the practical career transition roadmap, from On-Premise infrastructure management to modern DevOps thinking.

### Highlights

#### Real-time connection architecture for applications and games

- **Current choices**: UDP/ENet optimizes low latency for FPS/Racing but has complex network logic; HTTP Polling is simple to deploy but has high latency and wastes overhead due to continuous requests.
- **Serverless WebSocket Architecture**: Choosing WebSocket as the core solution for turn-based interactive applications thanks to full-duplex communication and reliable transmission guarantees.
- **API Gateway & Lambda Flow**: Routing JSON packets based on the $request.body.action operator into separate states: $connect (save connection), $disconnect (notify opponent and clear queue), and $default (handle game logic).
- **Storage configuration model**: Managing session and player states (waiting or matched) in real-time on an Amazon DynamoDB table via the PK structure which is the connectionId.
- **Limitations and Directions**: Handling phantom connections (GoneException) and the stateless nature (Stateless Lambda). Future proposals involve moving to dedicated server clusters running **AWS GameLift** for high-frequency continuous synchronization and real-time physics simulation.

#### Application packaging technology and infrastructure optimization with Docker

- **The iceberg of Virtual Machine (VM) problems**: Each VM must run an independent OS, consuming fixed CPU/RAM, heavy OS update cycles, not optimized for compact Microservices architectures.
- **Nature of Docker Containers**: Technology that packages applications along with all dependencies into a single package, sharing the host operating system (Host OS) to help start instantly in milliseconds and achieve performance close to a real machine.
- **Layering mechanism**: Inheriting and reusing cache memory when building through the Dockerfile configuration file (read-only Base Image layers stack on top of each other, on top is a writable container layer).
- **Docker CLI system**: Clearly classified into 5 core feature groups: Image management, Container lifecycle control, system debugging interaction, multi-container orchestration (*docker-compose*), and Network/Volume resource partitioning.

#### Overcoming limitations of traditional RAG with GraphRAG

- **Traditional RAG limitations**: Searching based on independent vector similarity leads to fragmented data, completely losing the ability to transitively link contexts between discrete entities located in many different documents.
- **GraphRAG operating mechanism**: Using a knowledge graph model consisting of nodes and edges to map deep contextual relationships, helping LLMs understand multi-layered interconnected entities before feeding them into the coordinating prompt.
- **Two deployment approaches**:
  - *Fully Managed Route*: Using **Amazon Bedrock Knowledge Bases** to automate chunking, entity extraction, combining with **Amazon Neptune Analytics** to store and automatically discover graph contextual relationships.
  - *Custom Route*: Building a data processing pipeline via the **LlamaIndex** framework using Python code, customizing extraction structures and querying graph data flexibly using *Cypher Query* language.

#### Smart cybersecurity based on Machine Learning and AWS WAF

- **Security challenges**: The signature-based security layer of traditional web application firewalls (AWS WAF) is not enough to defend against modern attack variants or zero-day vulnerabilities.
- **Network Intrusion Detection System (NIDS)**: Deploying a multi-functional NIDS that simultaneously handles the roles of monitoring network traffic, analyzing anomalous behavior, detecting real-time alerts, and logging responses.
- **Model training**: Preprocessing the standardized *CSE-CIC-IDS2018* dataset through the steps: Discovery $\rightarrow$ Consolidation $\rightarrow$ Cleaning NaN/infinite data $\rightarrow$ Class balance to eliminate algorithm bias. Using PCA and Elbow methods to determine the optimal number of clusters.
- **Algorithm performance evaluation**: Parallel testing across models (Random Forest, MLP, 1D-CNN, XGBoost). The **LightGBM** algorithm gave the most comprehensively optimal results with an accuracy of **95.86%** and an AUC-ROC index of **0.9982**.
- **Complete Cloud-native Architecture**: Traffic flow is distributed by ALB and filtered through AWS WAF, network traffic copies on EC2 instances are extracted via **Amazon Kinesis Data Firehose** and stored in S3. The Lambda function triggers the LightGBM model for real-time analysis, automatically sending emergency alerts via **Amazon SNS** and displaying a monitoring dashboard.

#### Career transition roadmap to Modern DevOps

- **Launchpad from basic positions**: Accumulating problem-solving thinking under high pressure, communication skills to handle problems directly with users from the IT Helpdesk role as a core foundation moving towards a systems engineer.
- **On-Premise infrastructure reality**: Understanding the complexity of operating physical servers, advanced command-line administration on major Linux distributions (*RedHat, CentOS, Debian*), managing SAN/NAS storage, and setting up server virtualization tiers with *VMware vSphere (ESXi)*.
- **The 4 levels of DevOps thinking progression**: 
  1. *On-Premise*: Manually managing physical hardware, slow and costly infrastructure scaling.
  2. *Cloud Mindset*: Migrating infrastructure to the AWS cloud, using flexible resources under a pay-as-you-go model.
  3. *Infrastructure as Code (IaC)*: Fully automating repeatable infrastructure setup and configuration through source code using the **Terraform** tool.
  4. *DevOps Culture*: Breaking down the isolation between Dev and Ops teams through CI/CD workflows, containerization, and comprehensive workflow automation.

### What Was Learned

#### Systems Thinking and Career Development

- **Erasing starting point prejudices**: Starting from a basic IT Helpdesk is not a barrier, but the best environment to practice practical troubleshooting skills to accumulate Root Cause Analysis thinking.
- **Mastering the Modern DevOps roadmap**: Clearly defining an 8-step core learning map from Linux/Networking, Git, Cloud, Containerization, CI/CD automation, Infrastructure as Code (IaC), Kubernetes orchestration to monitoring visualization (Observability).
- **The journey to overcome corporate interviews**: Understanding clearly that the biggest competitive weapon does not lie in mere theory, but in practical experience derived from real projects, how to dissect cloud architecture diagrams, and system disaster scenario handling skills.

#### Technical Architecture and Operations

- **Real-time connection model**: Grasping the state data flow of the WebSocket protocol, understanding how API Gateway coordinates workflows and pushes real-time data to multiple player IDs simultaneously.
- **Layered packaging thinking with Docker**: Understanding how to break down a bulky application into lightweight containers, mastering application lifecycle management mechanisms, and how to optimize image sizes through Docker layers cache.
- **Advanced AI pipeline optimization**: Approaching modern GraphRAG architecture, knowing how to coordinate Amazon Neptune's knowledge graph database with Amazon Bedrock to thoroughly solve the traditional RAG's transitive context loss problem.
- **Multi-layered smart security and analysis**: Mastering the process of setting up a complete cloud security architecture on AWS, how to preprocess and balance large datasets to train real-time machine learning models for detecting malicious network intrusions.

### Application to Work

- **Applying WebSocket to Projects**: Researching piloting the transition of the data update mechanism from traditional HTTP Polling to the Serverless WebSocket protocol using AWS API Gateway for real-time interactive modules in the current project.
- **Containerizing the entire application**: Applying standard Dockerfiles to package the current project's source code, optimizing layers to speed up the system build/deploy process in the CI/CD pipeline.
- **Setting up security infrastructure**: Practicing pilot configuration of Web ACLs on AWS WAF to prevent application-layer attack techniques (SQLi, XSS, Bot) and configuring CloudWatch Alarms to monitor workflows.

### Experience During the Event

Participating in the **First Cloud AI Journey (Event 3)** was a practical technology experience journey, comprehensive and delving into the most difficult technical problems of businesses in the digital age.

#### Practical and in-depth technical content
- Unlike purely theoretical seminars, the event provided real GDScript, Python source code, actual layered Dockerfile configuration files, and cloud infrastructure architecture diagrams in the form of icebergs extracted from real operating systems.
- Approaching visual machine learning model comparison charts (Confusion Matrix, PCA dimensionality reduction charts), helping listeners clearly understand the technical reasons behind choosing the LightGBM algorithm for the cybersecurity system.

#### Approaching vivid visual diagrams
- Attendees directly observed the Amazon Neptune Graph Explorer management interface, witnessing raw text data entities being extracted by AI and transformed into an incredibly vivid network of graph knowledge nodes.
- The complete Cloud-native architecture diagram on AWS showed the clear flow of packets from when hackers attack through the WAF shield until the system automatically pushes real-time alerts to the admin's phone.

#### Inspiring action and career orientation
- The final sharing session brought a humane closeness, hitting the bewildered psychology about the future orientation of technology students. The story stepping out of the basic IT Helpdesk position of the speaker ignited a strong fire of commitment.
- The perfect combination of trending technology problems (GenAI, DevOps, Security) and orientation advice helped me completely change my mindset: there are no boundaries or limits to development, all good engineers are forged through manually configuring and debugging in practical labs.

#### Lessons learned
- Solid technical skills and workflow automation thinking (Docker, IaC, CI/CD) are vital factors to eliminate subjective human errors and ensure the consistency of cloud systems.
- AI no longer stops at simple Q&A tools; combining AI with knowledge graph data structures (GraphRAG) creates a leap in complex information processing capabilities for businesses.
- Your starting point in the tech industry does not determine your future position; the Builder spirit, ready to engage, practice continuously, troubleshoot practically, and break out of the comfort zone, is the key to opening the door to becoming a senior expert.

### Some pictures from the event
![Event 3](/images/b8.jpg)
![Event 3](/images/b9.jpg)
![Event 3](/images/b10.jpg)
> Overall, the First Cloud AI Journey (Event 3) brought explosive energy for action along with a huge volume of top-notch practical knowledge. The event established a comprehensive development philosophy: Master your own infrastructure, bravely face cybersecurity challenges, and continuously upgrade your capabilities through every smallest practical action.