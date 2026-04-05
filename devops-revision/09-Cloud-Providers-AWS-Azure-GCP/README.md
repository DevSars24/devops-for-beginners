# ☁️ Module 09: Cloud Providers (Managed Kubernetes)

Welcome to the Cloud Managed Kubernetes section. This module explains how to deploy, manage, and scale Kubernetes clusters on the world's most popular cloud platforms: **Google Cloud (GKE)**, **Microsoft Azure (AKS)**, and **Amazon Web Services (EKS)**.

## 📖 Detailed Revision Guides

To master Cloud Managed Kubernetes, follow these high-quality, professional guides:

1. **[01-GKE-Mastery-Guide](./01-GKE-Mastery-Guide.md)**: Deep-dive into GKE Autopilot, Standard, Node Pools, and Node Auto-Provisioning (NAP).
2. **[02-AKS-Mastery-Guide](./02-AKS-Mastery-Guide.md)**: Mastering AKS Automatic, Standard, Pricing Tiers, and Networking (Azure CNI vs Kubenet).
3. **[03-EKS-Mastery-Guide](./03-EKS-Mastery-Guide.md)**: Implementing EKS Fargate, Managed Node Groups, IRSA, and Advanced Scaling with Karpenter.
4. **[04-Cloud-Comparison-Scaling](./04-Cloud-Comparison-Scaling.md)**: A comprehensive comparison of the "Big Three" and a summary of multi-level scaling strategies.

---

## 🏗️ Comparative Resource Reference

| Service Type | AWS | Microsoft Azure | Google Cloud (GCP) |
| :--- | :--- | :--- | :--- |
| **Containers** | ECS / EKS | AKS | GKE |
| **Compute** | EC2 | Virtual Machines | Compute Engine |
| **Scaling** | Karpenter / CAS | Cluster Autoscaler | NAP / Cluster Autoscaler |
| **Identity** | IAM (IRSA) | Azure Active Directory | Google IAM |
| **Storage** | EBS / EFS | Azure Disk / Files | Persistent Disk |

---

## 🛠️ Hands-on Concepts to Practice

- [ ] Create a GKE Autopilot cluster and deploy a web application.
- [ ] Implement **IAM Roles for Service Accounts (IRSA)** in an EKS cluster.
- [ ] Configure a **Node Pool** in AKS with specific VM sizes (e.g., memory-optimized).
- [ ] Scale a cluster's node pool automatically using the **Cluster Autoscaler**.
- [ ] Implement **Dynamic Storage Provisioning** across all three platforms.

---

## 🎤 Interview Preparation: Cloud Mastery

Each sub-guide above contains a **"Cracking the Interview"** section with targeted questions. Common topics include:
- The difference between EKS Fargate and Managed Node Groups.
- When to use GKE Autopilot vs. Standard.
- How to manage cross-cloud networking and security.
- Implementing cost-optimized scaling with Karpenter or NAP.

---

## 📚 Official Resources
- [GCP Architecture Framework](https://cloud.google.com/architecture/framework)
- [Microsoft Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/well-architected/)
- [AWS Well-Architected Tool](https://aws.amazon.com/architecture/well-architected/)
- [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/)
