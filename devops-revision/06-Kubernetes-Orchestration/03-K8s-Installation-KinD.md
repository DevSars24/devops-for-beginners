# 03: Installing a Local K8s Cluster (KinD)

Setting up a full Kubernetes cluster is hard. For development and testing environments, we use lightweight alternatives. The most popular one is **KinD (Kubernetes in Docker)**.

---

## 🏗️ What is KinD?

**KinD** is a tool for running local Kubernetes clusters using Docker container "nodes."
- **Fast**: Spin up a multi-node cluster in minutes.
- **Lightweight**: Ideal for CI/CD pipelines and local development.
- **Flexible**: You can define the number of Control Plane and Worker Nodes.

### Alternative Local Cluster Tools:
| Tool | Best For |
| :--- | :--- |
| **Minikube** | Single-node clusters on a VM. |
| **K3d** | Like KinD, but uses K3s (very lightweight). |
| **Docker Desktop** | Built-in single-node cluster (Easiest to start). |

---

## 🔌 Installing KinD on Linux/Mac

Before you start, ensure you have **Docker** and **kubectl** installed.

### 1. Install the KinD Binary
```bash
# On macOS (Homebrew)
brew install kind

# On Linux (Binary)
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.18.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### 2. Create Your First Cluster
```bash
# Create a single-node cluster
kind create cluster --name my-local-cluster
```

### 3. Verify the Cluster
```bash
kubectl cluster-info --context kind-my-local-cluster
kubectl get nodes
```

---

## 🏗️ Creating a Multi-Node Cluster

In production, you never run only one node. Let's simulate a real cluster with **1 Control Plane** and **3 Worker Nodes**.

Create a file named `kind-config.yaml`:
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
- role: worker
```

**Create the cluster using the config**:
```bash
kind create cluster --config kind-config.yaml --name multi-node-cluster
```

---

## 🎤 Interview Preparation: Cracking the Environment

> [!IMPORTANT]
> **Q1: Why is multi-node testing important in local development?**
> *Answer: Some Kubernetes features (like **Anti-Affinity** or **Node Selection**) only work when multiple nodes are available. Testing with a single-node cluster (like Docker Desktop) might hide bugs related to scheduling or cross-node networking.*

> [!TIP]
> **Q2: What is "Context" in `kubectl`?**
> *Answer: A Context is a set of access parameters (Cluster, User, and Namespace). If you are working on a local KinD cluster and a production GKE cluster, you use `kubectl config use-context <name>` to switch between them. This prevents you from running a "delete" command on the wrong cluster!*

---

## 📚 Next Steps
Now that your cluster is running, let's learn how to **Module 04: Connect Your Pods with Services & Ingress**.
