---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# BREAKING THE 90-DAY LIMIT OF EC2 CAPACITY MANAGER WITH AMAZON ATHENA

In large-scale AWS infrastructure management, controlling and projecting server costs is always a thorny issue for enterprises. To assist engineers in monitoring resources, Amazon EC2 Capacity Manager provides a centralized view of capacity usage (On-Demand, Spot, ODCR) across accounts and Regions throughout the entire organization.

However, a major bottleneck during practical operation is: The system only stores a maximum of 90 days of historical data on the AWS Management Console. This causes a lot of difficulties when the FinOps team needs to analyze long-term yearly trends, plan budgets, or evaluate the effectiveness of previously purchased capacity reservation packages (ODCR). This article details the architecture, automated partitioning process, and practical SQL scenarios to master long-term infrastructure data.

---

## 1. Core Advantages of the Solution

The deployment architecture focuses on optimizing the system based on two important aspects: long-term storage capability and intelligent data querying capability on a large scale.

- **Overcoming Data Storage Limits:** The solution allows automatically packaging all infrastructure data (On-Demand, Spot, ODCR) hourly (`Hourly`) into optimized Parquet (Snappy) compressed files, helping enterprises store it permanently on Amazon S3 for yearly trend analysis.
- **Automation with Partition Projection:** Completely eliminates the operation of manual data scanning tools (AWS Glue Crawler) daily to update metadata. By setting the `TBLPROPERTIES` attribute in Athena, the system automatically calculates and identifies new date/time directory partitions right at query time.
- **Resource Segregation Security via Bucket Policy:** Applying strict condition clauses (`Condition`) such as `aws:SourceAccount` and `ArnLike` associated with specific export paths ensures that automatic data writing permissions are only granted exclusively to the EC2 Capacity Manager service following the Least Privilege principle.

---

## 2. System Operational Process

The system's data processing flow is clearly divided into two independent stages via AWS service configurations:

- **When Exporting Data (Data Export):** EC2 Capacity Manager receives the configuration, periodically scans hourly, aggregates resource usage data of all accounts/Regions, then compresses and pushes it directly to the S3 Bucket following the date/time directory partition structure (`y=YYYY/m=MM/d=DD/h=HH`).
- **When Querying (Querying):** The FinOps engineer executes SQL commands on Amazon Athena. At this time, Athena does not scan the entire bucket but relies on the Partition Projection configuration parameters to accurately calculate the directory path to be read, helping to return analytical results in just a few seconds with minimal scanned data.

---

![EC2 Capacity Manager](/images/105.png)
## 3. Technology Selection and Storage Scope

| System Component | Technology Used | Role in Architecture |
| :--- | :--- | :--- |
| **Data Collection** | EC2 Capacity Manager | Centralized collection of infrastructure usage data (On-Demand, Spot, ODCR) |
| **Data Storage** | Amazon S3 | Long-term historical data storage repository in Parquet (Snappy) compressed format |
| **Metadata Store** | AWS Glue Data Catalog | Stores the table structure definition (Schema) for Amazon Athena to reference |
| **Data Analytics** | Amazon Athena | Executes advanced SQL commands to filter and extract FinOps reports |

---

## 4. Cost Optimization (FinOps) Scenarios in Practical Deployment

The solution opens up deep infrastructure cost optimization capabilities through 3 practical SQL query scenarios applied directly on the system:

### Hunting Down Wasted ODCR Packages
The system uses advanced mathematical functions (`CAST`, `ROUND`) to filter and precisely locate the `reservationid` code of underperforming capacity reservation packages (utilization < 50%) that are still being billed, calculating the hourly deficit amount (`wasted_cost_usd`) so the enterprise can promptly cancel or reallocate resources.

### Identifying Peak Load Patterns (Peak Usage)
Mining the dataset belonging to the `Instance Usage` group to calculate the average number of actual running servers by each hour of the day (from 00h to 23h). This analytical process helps pinpoint precisely when the system reaches peak thresholds, serving as a basis for devising a reasonable resource package purchasing strategy.

### Smart Internal Resource Sharing
Queries drill down into data at the Availability Zone physical infrastructure area level (`az-id`) to find out which zone has surplus capacity. This data helps the enterprise proactively coordinate, share idle capacity with other teams for common use, and conduct a clean sweep of all experimental resources upon completion.

---

![Athena SQL Query Results](/images/103.png)
## 5. Conclusion

The combination of EC2 Capacity Manager, S3, and Athena brings a comprehensive infrastructure cost management and optimization solution that overcomes conventional storage limits. This approach helps enterprises shift from passively addressing incurred costs to proactively mastering data, optimizing infrastructure, and improving financial efficiency on the AWS cloud.

Original article: https://aws.amazon.com/vi/blogs/compute/maximize-amazon-ec2-capacity-reservations-with-capacity-manager-data-exports/
