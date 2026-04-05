# 01: Google Kubernetes Engine (GKE) Mastery Guide

Google Kubernetes Engine (GKE) is the gold standard for managed Kubernetes, as it was built by the same engineers who created Kubernetes. It offers a highly automated, secure, and scalable environment for your containers.

---

## 🏗️ GKE Overview & Management Modes

GKE provides two primary "operation modes" depending on how much control you want versus how much automation you need.

### 1. GKE Autopilot (Fully Managed)
- **Concept**: Google manages the entire cluster infrastructure, including nodes and scaling. You only pay for the pods you run.
- **Best For**: Teams that want to focus on code and not worry about managing VMs or node pools.
- **Scaling**: Fully automatic. No need to configure Cluster Autoscaler.

### 2. GKE Standard (Highly Customizable)
- **Concept**: You manage the node infrastructure. You have full control over node configurations, SSH access, and network settings.
- **Best For**: Complex workloads requiring custom hardware (GPUs, local SSDs) or specific kernel configurations.

---

## 🚀 Cluster Creation & Node Pools

### What is a Node Pool?
A **Node Pool** is a subset of worker nodes within a cluster that all have the same configuration (e.g., machine type, labels, disk size).
- **Example**: One node pool for "General Web Apps" (e2-medium) and another for "Heavy ML Processing" (n1-highmem with GPUs).

### Creating a GKE Cluster (CLI)
```bash
# Create a Standard cluster with 3 nodes
gcloud container clusters create "pro-devops-cluster" \
    --region "us-central1" \
    --num-nodes "3" \
    --machine-type "e2-medium" \
    --enable-autoscaling --min-nodes "1" --max-nodes "5"
```

---

## 📈 Auto-scaling in GKE

GKE offers the most advanced autoscaling features in the market:

1. **Horizontal Pod Autoscaler (HPA)**: Adjusts the number of pod replicas based on CPU/RAM.
2. **Cluster Autoscaler**: Automatically adds or removes VM nodes from your node pools when pods cannot be scheduled.
3. **Node Auto-Provisioning (NAP)**: An advanced version of Cluster Autoscaler that automatically creates **entirely new node pools** with the perfect machine type for your pending pods.

---

## 💾 Dynamic Storage Provisioning

In GKE, you don't need to manually create Persistent Disks. Use the `standard-rwo` StorageClass:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: gke-disk-pvc
spec:
  accessModes: [ReadWriteOnce]
  resources:
    requests:
      storage: 50Gi
  storageClassName: standard-rwo # Maps automatically to Google Persistent Disk
```

---

## 🎤 Interview Preparation: Cracking GKE

> [!IMPORTANT]
> **Q1: What is the difference between Regional and Zonal Clusters in GKE?**
> *Answer: A **Zonal Cluster** has a single control plane in one zone. If that zone fails, the control plane is down. A **Regional Cluster** has three control planes replicated across three different zones, providing higher availability (99.95% SLA) and ensuring the cluster remains manageable even during a zone outage.*

> [!TIP]
> **Q2: When should you choose GKE Autopilot over Standard?**
> *Answer: Choose **Autopilot** when you want to reduce operational overhead and only pay for your actual workload usage. Choose **Standard** if you need custom node configurations, specialized hardware, or need the "free tier" (Autopilot has a flat management fee per cluster).*

---

## 📚 Next Steps
Now that you've mastered GKE, let's look at the Microsoft equivalent: **Module 02: Azure Kubernetes Service (AKS) Mastery**.
