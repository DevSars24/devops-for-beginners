# 06: Kubernetes Scaling & Resource Management

In a shared cluster, one application can consume all the CPU/RAM, causing others to crash (the "Noisy Neighbor" problem). Kubernetes allows you to manage resources and scale your application automatically based on demand.

---

## 🏗️ Managing Resources: Requests & Limits

To prevent resource exhaustion, you must define **Resources** for every container.

| Resource Type | What it is |
| :--- | :--- |
| **Requests** | The **Minimum** amount of CPU/RAM the container needs to start. The Scheduler uses this to find a suitable node. |
| **Limits** | The **Maximum** amount of CPU/RAM the container is allowed to use. If it exceeds the limit, it will be slowed down (CPU) or killed (RAM). |

### 🌟 Example: A Container with Resource Constraints
```yaml
spec:
  containers:
  - name: web-app
    image: my-app:v1.0
    resources:
      requests:
        memory: "64Mi"
        cpu: "250m" # 1/4th of a CPU core
      limits:
        memory: "128Mi"
        cpu: "500m" # 1/2 of a CPU core
```

---

## 🚀 Scaling Your Application Automatically

Kubernetes provides three main ways to scale your application:

### 1. HPA (Horizontal Pod Autoscaler)
Adds or removes **Pods** based on CPU/RAM usage.
- **Analogy**: Adding more **Checkout Counters** in a supermarket when the lines get long.

### 2. VPA (Vertical Pod Autoscaler)
Increases or decreases the **CPU/RAM** (Requests/Limits) of existing Pods. Useful for apps that can't be replicated easily (like databases).
- **Analogy**: Making a **Bigger Truck** when you have more cargo to carry.

### 3. Cluster Autoscaler (CA)
Adds or removes **Worker Nodes** (VMs) to the cluster if there isn't enough space to run new Pods.
- **Analogy**: Building an **Entire New Supermarket** when the existing one is too small.

---

## 🛠️ Most-Used Scaling Commands

| Command | Action |
| :--- | :--- |
| **`kubectl scale deployment/my-app --replicas=5`** | Manually scale a deployment to 5 replicas. |
| **`kubectl autoscale deployment/my-app --cpu-percent=50 --min=1 --max=10`** | Create an HPA that scales between 1-10 pods if CPU exceeds 50%. |
| **`kubectl get hpa`** | Monitor the status of your autoscale policies. |

---

## 🎤 Interview Preparation: Cracking the Scaling

> [!IMPORTANT]
> **Q1: What happens if a Pod exceeds its Memory Limit?**
> *Answer: The pod will be **OOMKilled** (Out Of Memory Killed) by the Kubernetes kernel. Unlike CPU (which is just throttled/slowed down), memory is a hard resource. If a pod takes more than its share, it is terminated immediately to protect the node's stability.*

> [!TIP]
> **Q2: Why should we use HPA for web applications?**
> *Answer: **Cost and Reliability**. During high traffic (e.g., a Black Friday sale), HPA will automatically add pods to handle the load. During low traffic (e.g., in the middle of the night), it will remove them, reducing your cloud billing.*

---

## 📚 Next Steps
Now that your apps are scaling, let's learn how to **Module 07: Manage Persistent Storage with PV/PVC**.
