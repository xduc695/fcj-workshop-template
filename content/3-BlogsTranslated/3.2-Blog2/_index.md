---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# Optimizing Disaster Recovery for Stateful Services on Amazon EKS using Velero

Ensuring high availability and data safety is always a vital problem for systems running on the Kubernetes platform. When accidentally deleting a namespace in a production environment or encountering errors during a cluster upgrade, manually re-establishing all resources will consume a lot of time and effort from the operations team. 

The disaster recovery backup and restore solution using the open-source tool Velero helps automate the packaging of logic configurations to Amazon S3, while simultaneously taking physical disk snapshots of stateful applications in the form of Amazon EBS Snapshots. This article details the architecture, operational process, and important technical considerations drawn from the practical deployment of the solution on the Amazon EKS system.

---

## 1. Core Advantages of the Solution

The deployment architecture focuses on optimizing the system based on two important aspects: the ability to preserve data integrity and tightening infrastructure safety standards.

- **Security via EKS Pod Identity:** Instead of using static credentials (long-term AWS Access Keys) or abusing the system's default supreme `cluster-admin` privileges, the solution establishes a short-term delegation mechanism via EKS Pod Identity. Combined with a custom `ClusterRole`, Velero is only allowed minimal interaction with the truly necessary apiGroups according to the Least Privilege principle.
- **Synchronous Backup of Two Components:** Unlike common solutions that only store soft configurations, Velero processes in parallel both logic configuration files (Deployments, PVCs, Secrets... compressed and pushed to Amazon S3) and actual data stored in the gp3 disk (frozen and cast into Amazon EBS Snapshots).
- **Flexible Cross-Namespace Recovery:** The `namespaceMapping` feature allows for the rapid re-establishment of the entire application and pulling back historical data from an old snapshot to an independent new partition (`myrestore`) without affecting the original environment.

---

## 2. System Operational Process

The system's data processing flow is clearly divided into two independent stages via Kubernetes Custom Resources:

- **When Backing Up (Backup):** The Velero controller receives the request, scans through the Kubernetes API to collect all resource definitions in the specified namespace, and pushes the compressed file to the S3 Bucket. For the persistent physical disk partition, the system simultaneously calls the AWS API to trigger the physical disk snapshot process (EBS Snapshot) to freeze the data state at the time of backup.
- **When Restoring (Restore):** When performing a restore to a new namespace, AWS automatically analyzes the configuration data stored on S3, reads the old snapshot information from the previous backup process to "cast" a completely new `gp3` disk. This new disk is automatically mounted to the Worker Node for the application to seamlessly continue writing data appending to the historical file without interruption.

---
![Backup restore](/images/104.png)
## 3. Technology Selection and Storage Scope

| System Component | Technology Used | Role in Architecture |
| :--- | :--- | :--- |
| **Control Plane Backup** | Amazon S3 | Centralized storage of logical resource definition files in `.tar.gz` format |
| **Data Plane Backup** | Amazon EBS Snapshots | Stores the actual data (Stateful) of the application following the Block Storage mechanism |
| **Identity & Access** | EKS Pod Identity | Manages identity and grants short-term permissions for Pods via IAM Role |
| **Orchestration** | Velero Server & Helm | Manages the lifecycle of the resource backup and restore process in the cluster |

---

## 4. Technical Considerations for Practical Deployment

During the process of practicing the solution configuration, the system encounters some specific issues that need to be adjusted directly on the infrastructure:

### Characteristics of the Windows CMD Environment
Because the original documentation is fully optimized for the Linux environment, when executing commands on Windows CMD, it is necessary to convert all environment variable syntax to the `%VARIABLE%` format. In addition, the process of generating YAML configuration manifest files from the terminal needs to be wrapped in a block of parentheses or use implicit PowerShell commands to avoid errors with breaking special characters.

![EKS Pod Identity Association](/images/101.png)
### Pod Stuck in Pending State Error (FailedScheduling)
This error occurs because the AWS sample deployment file defaults to configuring the picky node attribute (`nodeSelector` bound to EKS Auto Mode). If the actual infrastructure is operating a normal Standard Node Group cluster, the Pod will not be able to be scheduled. Proactively omitting this node filtering configuration line in the deployment file will help the application quickly transition to the `Running` state and receive the disk smoothly.

---

![Velero Backup Completed](/images/100.png)
## 5. Conclusion

The combination of Velero and Amazon EKS through the Pod Identity authentication mechanism brings a comprehensive disaster recovery solution for stateful applications in Cloud environments. This approach not only meets the strict enterprise security standards but also significantly reduces the operational burden for Operations teams when the system faces major incidents.

Original article: https://aws.amazon.com/blogs/containers/back-up-and-restore-your-amazon-eks-cluster-resources-using-velero/
