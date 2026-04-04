# ☁️ Module 09: Cloud Providers (AWS, Azure, GCP)

While Cloud Fundamentals (Module 00) taught us the concepts, this module is about implementation on the "Big Three" providers.

## 🏗️ Comparative Resource Guide
| Service Type | AWS | Azure | GCP |
| :--- | :--- | :--- | :--- |
| **Compute** | EC2 | Virtual Machines | Compute Engine |
| **Containers** | ECS/EKS | AKS | GKE |
| **Serverless** | Lambda | Azure Functions | Cloud Functions |
| **Storage** | S3 | Blob Storage | Cloud Storage |
| **Database** | RDS/DynamoDB | SQL Database/Cosmos DB | Cloud SQL/Firestore |
| **Networking** | VPC | Virtual Network | VPC Network |

---

## 🔑 AWS Deep-Dive (Primary focus for most)
### 1. IAM (Identity & Access Management)
The "Root" of cloud security. Control who can access what.
- **Users**: Individuals.
- **Groups**: Collection of users with same permissions.
- **Roles**: Temporary permissions for services (e.g., allow EC2 to access S3).

### 2. VPC (Virtual Private Cloud)
Your isolated slice of the AWS Cloud.
- **Subnets**: Public (Internet access) vs Private (No direct internet).
- **IGW** (Internet Gateway): Connects VPC to the Internet.
- **NAT Gateway**: Allows private subnets to reach the Internet (for updates) without direct access.

---

## 🛠️ Hands-on Concepts to Practice
- Provision an EC2 instance and connect via SSH.
- Set up an S3 bucket with restricted permissions.
- Create a VPC with one public and one private subnet.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: What is a VPC Peering?**
> *A: A networking connection between two VPCs that allows them to communicate using private IP addresses as if they were on the same network.*

> [!TIP]
> **Q2: Explain S3 storage classes.**
> *A: S3 Standard (normal use), S3 Intelligent-Tiering (auto-switch based on use), S3 Standard-IA (Infrequent Access), and S3 Glacier (Archive/Cold Storage).*

---

## 📚 Resources
- [AWS Documentation](https://docs.aws.amazon.com/)
- [Microsoft Learn for Azure](https://learn.microsoft.com/en-us/training/azure/)
- [Google Cloud Training](https://cloud.google.com/learn)
- [A Cloud Guru (Best platform for certifications)](https://www.pluralsight.com/cloud-guru)
