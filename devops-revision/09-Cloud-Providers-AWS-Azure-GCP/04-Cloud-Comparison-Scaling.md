# 04: Cloud Comparison & Advanced Scaling Summary

When designing a production-grade infrastructure, choosing the right cloud provider and scaling strategy is essential. This guide summarizes the differences between GKE, AKS, and EKS and covers common scaling patterns.

---

## 🏗️ The "Big Three" Comparison Table

| Feature | GKE (Google) | AKS (Microsoft) | EKS (Amazon) |
| :--- | :--- | :--- | :--- |
| **Ease of Use** | Highest (Best automation) | Medium | Medium (Requires more configuration) |
| **Management Modes** | Autopilot & Standard | Automatic & Standard | Fargate & Managed Node Groups |
| **Autoscaling** | NAP (Node Auto-Provisioning) | Cluster Autoscaler | Karpenter (Advanced) |
| **Identity** | Google Cloud IAM | Azure Active Directory | AWS IAM (with IRSA) |
| **Upgrade Channel** | Best (Multi-channel) | Good | Manual or Managed |
| **Ecosystem** | Best for Data/AI | Best for Enterprise/Office | Best for Market Reach/Scale |

---

## 📈 Auto-scaling Strategies: A Comprehensive Guide

In a high-traffic production environment (like a global E-commerce platform), you need three levels of scaling:

### 1. Pod-Level (HPA)
Scales the number of Pods based on metrics like CPU, Memory, or Custom Metrics (e.g., number of messages in a queue).
- **Pro-Tip**: Use **Custom Metrics** (like Requests Per Second) instead of just CPU, as CPU is a lagging indicator.

### 2. Node-Level (Cluster Autoscaler)
Adds or removes entire VM instances to the cluster when Pods are in a "Pending" state due to lack of resources.
- **Pro-Tip**: Ensure your pods have **Resources Requests** defined, or the Autoscaler won't know when to add a new node.

### 3. Vertical Scaling (VPA)
Automatically adjusts the CPU and Memory **Requests** of your Pods based on actual usage over time.
- **Pro-Tip**: Use VPA for stateful applications and memory-hungry workloads that cannot be sharded/replicated.

---

## 💾 Dynamic Storage & Provisioning Summary

Every cloud provider uses the same underlying Kubernetes storage primitives (PV/PVC).

- **GKE**: Use `pd-balanced` or `pd-ssd` for high-performance block storage.
- **AKS**: Use `managed-csi` for Azure Disks or `azure-file-csi` for shared storage.
- **EKS**: Use the **EBS CSI Driver** for block storage and the **EFS CSI Driver** for shared, multi-node storage.

---

## ❓ Knowledge Checks: Final Review

1. **Which cloud provider offers "Node Auto-Provisioning" (NAP)?** (Answer: GKE)
2. **What tool is an alternative to the standard AWS Cluster Autoscaler?** (Answer: Karpenter)
3. **What is the difference between Fargate (EKS) and Managed Node Groups?** (Answer: Fargate is serverless/pod-level isolation; Managed Nodes are EC2 instances managed by AWS).
4. **How do you securely allow a Pod in EKS to access S3?** (Answer: Assign an IAM Role to a Service Account - IRSA).

---

## 📚 Final Resources
- [GKE vs AKS vs EKS: A Technical Comparison](https://www.stackrox.com/post/2022/07/aks-vs-eks-vs-gke-comparison/)
- [Karpenter Official Site](https://karpenter.sh/)
- [The Multi-Cloud Architecture Guide](https://cloud.google.com/architecture/best-practices-for-running-multicloud-workloads)
- [CNCF Cloud Native Landscape](https://landscape.cncf.io/)
