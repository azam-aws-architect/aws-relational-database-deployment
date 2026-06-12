# AWS Secure Relational Database Infrastructure Deployment (MySQL RDS)

## 📌 Project Overview
This project demonstrates the successful architecture, deployment, and testing of a highly secure and scalable relational database infrastructure on AWS. Utilizing Amazon RDS (MySQL Engine), the infrastructure was connected and tested live via an isolated AWS EC2 Ubuntu instance using the Native MySQL Command-Line Client to simulate enterprise production workloads.

## 🏗️ Architectural Components

*   **Database Tier:** Amazon RDS MySQL Cluster (Free Tier Optimized) hosting the dynamic healthcare microservice engine `healthvitals_app`.
*   **Compute Tier:** AWS EC2 Ubuntu Instance utilized as a secure jump box/database client to maintain strict operational management.
*   **Security Configuration:** Stateful AWS Security Groups configured with strict ingress rules (Port 3306 restricted for safe administration and Port 22/80 for system dependencies).
*   **Data Tier:** Structured schema execution implementing relational tables (`patients`) with live dynamic reading/writing pipelines.

## 🚀 Step-by-Step Implementation

1. **RDS Cluster Provisioning:** Deployed a highly scalable MySQL engine instance on Amazon RDS.
2. **Network Security Engineering:** Created and modified AWS Security Group rules to safely map out inbound/outbound MySQL/Aurora TCP traffic over Port 3306.
3. **Database Client Assembly:** Updated the EC2 Linux repository cache (`apt update`) and provisioned the `mysql-client-core` environment.
4. **Cloud Database Handshake:** Established a live network pipe using the active AWS Endpoint routing:
```bash
   mysql -h healthvitals-db-easy.c05emmowc4i1.us-east-1.rds.amazonaws.com -u admin -p
mysql> SELECT * FROM patients;
+------------+--------------+-----+-------------+--------------------------+
| patient_id | patient_name | age | blood_group | status                   |
+------------+--------------+-----+-------------+--------------------------+
|          1 | Muhammad Ali |  34 | O+          | Stable Under Observation |
+------------+--------------+-----+-------------+--------------------------+
1 row in set (0.00 sec)
