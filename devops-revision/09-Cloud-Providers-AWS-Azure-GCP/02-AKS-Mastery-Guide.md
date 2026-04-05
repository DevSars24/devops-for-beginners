# 02: Azure Kubernetes Service (AKS) Mastery Guide

Azure Kubernetes Service (AKS) is Microsoft's managed Kubernetes offering. It integrates deeply with Azure Active Directory (AAD), Azure DevOps, and Azure Monitor, making it the top choice for enterprise organizations already using Microsoft technologies.

---

## 🏗️ AKS Management Modes

Like GKE, AKS offers tiers based on the level of management you require.

### 1. AKS Automatic (Fully Managed)
- **Concept**: Microsoft handles the node management, patching, and scaling. It’s the "Serverless-like" experience for Kubernetes.
- **Best For**: Rapid development and reduced operational overhead.

### 2. AKS Standard (Managed Infrastructure)
- **Concept**: You have control over node pools, availability sets, and network configurations.
- **Best For**: Production workloads that need specific VM sizes or advanced networking (like Azure CNI).

---

## 🚀 Node Pools & Pricing Tiers

### 1. System vs. User Node Pools
- **System Node Pools**: Dedicated for running critical system pods (like CoreDNS or Metrics Server). You should run at least 2-3 nodes here for high availability.
- **User Node Pools**: Dedicated for your application workloads. These can be scaled to zero if not in use.

### 2. Global Pricing Tiers
- **Free Tier**: No management fee per cluster. Recommended for POCs and development.
- **Standard Tier**: Includes a 99.95% SLA for the API server (Uptime SLA) and professional support. Recommended for production.

---

## 📈 Auto-scaling & Upgrades in AKS

AKS has unique features for maintaining a healthy cluster:

1. **Cluster Autoscaler (CAS)**: Monitors Pods that can't be scheduled due to lack of resources and adds more VM nodes to the node pool.
2. **Horizontal Pod Autoscaling (HPA)**: Scales the number of pod replicas based on CPU/RAM.
3. **Upgrade Channels**: Automate cluster upgrades by selecting a channel:
   - **None**: No automatic upgrades (Manual).
   - **Stable**: Upgrades to the latest stable N-1 version.
   - **Rapid**: Upgrades to the latest stable N version.

---

## 💾 Storage & Networking Excellence

AKS provides high-performance storage options:
- **Azure Disk**: Performance-oriented block storage (Standard, Premium, Ultra).
- **Azure Files**: Shared file storage (Ideal for multi-node read/write).
- **Dynamic Provisioning**: Use the `managed-csi` StorageClass to automatically create Azure Disks when a PVC is created.

---

## 🎤 Interview Preparation: Cracking AKS

> [!IMPORTANT]
> **Q1: How does AKS handle security and identity?**
> *Answer: AKS uses **Azure Active Directory (AAD) Integration**. You can use Role-Based Access Control (RBAC) to allow users to log in to the cluster using their existing company credentials. Furthermore, **Azure Workload Identity** allows individual Pods to securely access other Azure services (like Key Vault or SQL) without using hardcoded passwords.*

> [!TIP]
> **Q2: What is the difference between Azure CNI and Kubenet networking?**
> *Answer: **Kubenet** is simpler but uses an internal network bridge (needs fewer IP addresses). **Azure CNI** (Advanced) gives every Pod a "Real" IP address from your Azure Virtual Network (VNet). CNI is faster and allows better integration with on-premise networks but requires a larger IP address pool.*

---

## 📚 Next Steps
Now that you've mastered AKS, let's explore the Amazon equivalent: **Module 03: Amazon Elastic Kubernetes Service (EKS) Mastery**.
