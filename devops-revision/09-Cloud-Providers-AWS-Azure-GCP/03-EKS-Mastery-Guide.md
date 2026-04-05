# 03: Amazon Elastic Kubernetes Service (EKS) Mastery Guide

Amazon Elastic Kubernetes Service (EKS) is the most widely used managed Kubernetes platform, known for its deep integration with the vast AWS ecosystem and its high standards of security and scalability.

---

## 🏗️ EKS Overview & Management Modes

EKS offers flexibility by allowing you to choose how you want to manage your worker nodes.

### 1. EKS Fargate (Serverless)
- **Concept**: You don't manage any EC2 instances. Every Pod runs on a fully isolated, dedicated VM. You only pay for the CPU and RAM each Pod uses.
- **Best For**: Applications where you don't want any server management or need strong pod-level isolation for security.
- **Scaling**: There is no "Node Scaling" to configure; Pods are launched as needed.

### 2. EKS Managed Node Groups
- **Concept**: AWS manages the EC2 instances for you, including patching, updates, and scaling.
- **Best For**: Performance-heavy apps that need local access to EBS volumes or custom instance types (like GPUs).
- **Scaling**: Managed automatically by the AWS EKS control plane.

---

## 🚀 IAM Roles for Service Accounts (IRSA)

One of EKS's most powerful features is its integration with AWS Identity and Access Management (IAM).
- **The Old Way**: Give all nodes in a cluster permissions to access S3/DynamoDB. (Insecure!)
- **The IRSA Way**: Assign a specific **IAM Role** directly to a **Kubernetes Service Account**. Only the Pods using that service account can access those AWS resources.

---

## 📈 Auto-scaling in EKS

EKS relies on standard Kubernetes scaling tools, but with AWS-specific implementations:

1. **Horizontal Pod Autoscaler (HPA)**: Scales the number of pod replicas based on CPU/RAM.
2. **Karpenter (Advanced Autoscaling)**: An open-source, flexible, high-performance Kubernetes cluster autoscaler built by AWS. It provisions the **exactly right** EC2 instances for your workload in seconds, circumventing many of the limitations of the traditional Cluster Autoscaler.

---

## 💾 Storage & Networking in EKS

### 1. Networking (VPC CNI)
By default, EKS uses the **Amazon VPC CNI plugin**, which allows Pods to have the same IP addresses as the VPC's internal network. This provides low latency and high performance.

### 2. Storage (EBS & EFS)
- **EBS (Elastic Block Store)**: Used for high-performance block storage (Standard, gp3, io2).
- **EFS (Elastic File System)**: Used for shared, elastic file storage that multiple Pods can access at once from different nodes.
- **EBS CSI Driver**: Essential for dynamic provisioning of EBS volumes via PVCs.

---

## 🎤 Interview Preparation: Cracking EKS

> [!IMPORTANT]
> **Q1: How do you authorize a user to access an EKS Cluster?**
> *Answer: EKS uses **AWS IAM** for authentication (proving who you are) but uses **Kubernetes RBAC** for authorization (proving what you can do). You must map IAM users or roles to Kubernetes groups using the `aws-auth` ConfigMap (legacy) or the newer **EKS Access Entries**.*

> [!TIP]
> **Q2: Why use Karpenter instead of the standard Cluster Autoscaler?**
> *Answer: **Karpenter is faster and smarter**. While the Cluster Autoscaler is limited to existing EC2 Auto Scaling Groups, Karpenter scans all 600+ EC2 instance types and picks the most cost-effective one for your pods in real-time. This significantly improves cluster efficiency and decreases cold-start times.*

---

## 📚 Next Steps
Now that you've mastered EKS, let's look at the **Cloud Deployment Mode Comparison & Summaries**.
