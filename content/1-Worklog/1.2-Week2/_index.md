---
title: "Week 2 Worklog"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
### Week 2 Objectives:

* Gain a deeper understanding of network services on AWS.
* Learn how to design and initialize a virtual network (VPC) and establish secure connections (VPN) for data transmission.
* Learn to use Session Manager and deploy direct access to EC2 instances in a VPC as an alternative to SSH.
* Learn to use VPC Peering to connect two different VPCs, allowing servers to communicate directly using private IPs instead of routing through the Internet.
* Learn to use Transit Gateway as a central hub and connect multiple VPCs via a centralized router to simplify network architecture, replacing complex VPC Peering meshes.
* Learn how to build a hybrid DNS system and integrate an on-premise DNS system with Amazon Route 53 via Inbound/Outbound Endpoints and Resolver Rules.

### Tasks to be implemented this week:

| Day | Task | Start Date | End Date | Resource Links |
| --- | --- | --- | --- | --- |
| Monday | - Deep dive into AWS networking services: <br>&emsp; + Amazon Virtual Private Cloud (VPC) <br>&emsp; + VPC Peering & Transit Gateway <br>&emsp; + VPN & Direct Connect <br>&emsp; + Elastic Load Balancing | 27/04/2026 | 27/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tuesday | - Get familiar with Amazon VPC and core components: Subnets, Route Tables, IGW, NAT Gateway.<br> - Get familiar with VPC firewalls: Security Groups, Network ACLs.<br> - Learn about VPC Resource Map.<br> - **Practice:**<br>&emsp; + Initialize VPC, Subnet, IGW, Route Table, Security Group.<br>&emsp; + Enable VPC Flow Logs.<br> - Deploy a Production-Ready EC2 Infrastructure.<br> - **Practice:**<br>&emsp; + Deploy EC2 Instances and verify SSH connection.<br>&emsp; + Initialize NAT Gateway.<br>&emsp; + Use Reachability Analyzer.<br>&emsp; + Initialize and connect via EC2 Instance Connect Endpoint.<br>&emsp; + Deploy CloudWatch Monitoring & Alerting. | 28/04/2026 | 28/04/2026 | <https://000003.awsstudygroup.com/> |
| Wednesday | - Deploy and configure an AWS Site-to-Site VPN environment.<br> - **Practice:** <br>&emsp; + Set up VPC for VPN, EC2 Customer Gateway.<br>&emsp; + Initialize Virtual Private Gateway and Customer Gateway.<br>&emsp; + Establish AWS Site-to-Site VPN Connection.<br>&emsp; + Customize AWS VPN Tunnel.<br> - Learn advanced VPN security configurations and Troubleshooting.<br> - Expand on connecting VPN using strongSwan with Transit Gateway.<br> - Learn Infrastructure as Code (CloudFormation). | 29/04/2026 | 29/04/2026 | <https://000003.awsstudygroup.com/> |
| Thursday | - Learn Amazon System Manager - Session Manager.<br>- **Practice:** <br>&emsp; + Initialize VPC, Subnets, Security Groups.<br>&emsp; + Create Public Linux EC2 and Private Windows EC2.<br>&emsp; + Create IAM Role for EC2 to communicate with Session Manager.<br>&emsp; + Create SSM Endpoints and connect to Private Windows server.<br>&emsp; + Update IAM Role for S3 access.<br>&emsp; + Initialize S3 bucket for session logs.<br>&emsp; + Configure Port Forwarding for RDP.<br> - Set up Hybrid DNS with Route 53 Resolver.<br> - **Practice:** <br>&emsp; + Deploy AWS Managed Microsoft AD (simulating On-premises DNS).<br>&emsp; + Configure Route 53 Outbound Endpoint and Resolver Rules.<br>&emsp; + Configure Route 53 Inbound Endpoint.<br>&emsp; + Cross-resolve domain names. | 30/04/2026 | 30/04/2026 | <https://000058.awsstudygroup.com/> <br><https://000010.awsstudygroup.com/>|
| Friday | - Set up VPC Peering.<br> - **Practice:** <br>&emsp; + Quickly create 2 VPCs via CloudFormation.<br>&emsp; + Create VPC Peering Connection and update Route Tables.<br>&emsp; + Enable DNS Resolution Support (Cross-Peer DNS).<br> - Deploy Transit Gateway with 4 VPCs.<br> - **Practice:**<br>&emsp; + Use CloudFormation to rapidly deploy 4 VPCs.<br>&emsp; + Create Transit Gateway and Transit Gateway Attachments.<br>&emsp; + Configure Route Tables for Transit Gateway and each VPC.<br>&emsp; + Test inter-network connectivity. | 01/05/2026 | 01/05/2026 | <https://000019.awsstudygroup.com/><br><https://000020.awsstudygroup.com/> |

### Week 2 Achievements:

* Mastered Amazon VPC knowledge:
  * Successfully differentiated and configured Subnets (Public/Private), Route Tables, and Gateways (Internet/NAT).
  * Understood the 2-layer security barrier: Security Groups (instance-level filtering) and Network ACLs (network-level filtering).
  * Used VPC Resource Map for visual administration of the entire network resource topology.

* Expansion and Interconnectivity:
  * VPC Peering: Established direct peer-to-peer connections between different VPCs.
  * Transit Gateway: Mastered the centralized routing model (Hub-and-Spoke) for large-scale systems.

* Understood Hybrid Cloud & High Availability:
  * VPN: Mastered creating encrypted Site-to-Site tunnels to securely connect with On-premises environments.
  * Direct Connect: Understood the dedicated physical connection solution for enterprises.
  * ELB: Understood the Load Balancing mechanism to ensure high system availability.

**1. VPC and EC2 Architecture (Tuesday)**
* Mastered architecture and virtual network setup (Amazon VPC): Successfully initialized a custom Multi-AZ VPC, allocated Public/Private Subnets. Configured Internet Gateway (IGW) and NAT Gateway for secure internet access for private instances.
* Deployed and operated virtual servers (Amazon EC2): Initialized EC2 Instances in both Public and Private environments.
![VPC](/images/11.png)
* Access management and multi-layer network security: Configured Security Groups, deployed advanced access via EIC Endpoints.
![Security Group](/images/12.png)
* Deployed monitoring and alerting systems: Applied VPC Reachability Analyzer, VPC Flow Logs, and CloudWatch Monitoring.
![CloudWatch](/images/13.png)
![CloudWatch](/images/14.png)

**2. Site-to-Site VPN Infrastructure (Wednesday)**
* Set up a simulated On-premise network environment using an EC2 instance acting as the Customer Gateway (CGW). Initialized a Virtual Private Gateway (VGW) on AWS.
![VPN](/images/15.png)
* Configured VPN using static routing and successfully troubleshot issues using Libreswan. Both networks pinged seamlessly through the IPsec tunnel.
![VPN](/images/16.png)

**3. AWS Session Manager & Auditing (Thursday - Part 1)**
* Deployed Zero-Trust access with AWS Session Manager via IAM Roles and VPC Endpoints (ssm, ssmmessages, ec2messages) as a replacement for SSH.
![Session Manager](/images/17.png)
* Configured an S3 Bucket and S3 Gateway Endpoint to automatically log session activities (Session Logs) for security auditing.
![S3](/images/18.png)
* Applied Port Forwarding to establish a secure RDP connection to the Private Windows server.
![RDP](/images/19.png)

**4. VPC Peering & Transit Gateway (Friday)**
* Successfully established a VPC Peering internal connection between My VPC and HG VPC.
![VPC Peering](/images/20.png)
* Configured Cross-Peer DNS to resolve Public DNS names across the two VPCs.
![DNS](/images/21.png)
* Optimized network architecture using AWS Transit Gateway as a central router for 4 independent VPCs.
![Transit Gateway](/images/22.png)
* Successfully managed routing flows (Associations/Propagations), ensuring branch servers could ping and SSH smoothly.
![Transit Gateway](/images/23.png)

**5. Hybrid DNS with Route 53 & Microsoft AD (Thursday - Part 2)**
* Successfully deployed AWS Managed Microsoft AD (simulating an On-premises DNS).
![Microsoft AD](/images/24.png)
* Configured Route 53 Outbound Endpoint and Inbound Endpoint for bidirectional domain resolution synchronization.
![Route 53](/images/25.png)
* Successfully tested cross-domain resolution from AWS servers to the On-premises network.
![Route 53](/images/26.png)
