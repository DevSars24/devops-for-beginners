# 02: Kubernetes Objects (Pods & Workloads)

In Kubernetes, you interact with the cluster by creating **Objects**. This guide focuses on the most crucial workload objects: **Pods**, **Deployments**, and **ReplicaSets**.

---

## 🚀 The Pod: The Smallest Building Block

A **Pod** is a group of one or more containers (e.g., a main web app and a helper "sidecar" container) that share a common network and storage.

- **Atomic Unit**: Pods are the smallest deployable units.
- **Ephemeral**: Pods are born and die. If a Pod is deleted, its data and its IP address are gone too.
- **Resource Limits**: You can define how much CPU and Memory a Pod can use.

### 🌟 Example: A Simple Pod YAML
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-web-app
spec:
  containers:
  - name: web-container
    image: nginx:alpine
    ports:
    - containerPort: 80
```

---

## 🏗️ ReplicaSet: The "Backup" System

A **ReplicaSet** ensures that a specific number of Pod replicas are running at any given time.
- If a Pod crashes, the ReplicaSet starts a new one.
- You rarely create ReplicaSets directly; they are managed automatically by **Deployments**.

---

## 🚢 Deployment: The Master Orchestrator

A **Deployment** is a higher-level object that manages ReplicaSets and Pods. It provides **Declarative Updates** for your application.

### Why Use a Deployment?
1. **Scaling**: Effortlessly scale your app from 2 to 200 replicas.
2. **Rolling Updates**: Update your image version without downtime. Kubernetes will replace one old pod with a new one until the entire fleet is updated.
3. **Self-Healing**: If a worker node fails, the Deployment will automatically reschedule those pods to a healthy node.
4. **Rollbacks**: If a new version has a bug, you can instantly revert to a previous version.

### 🌟 Example: A Deployment YAML
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-todo-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: todo
  template:
    metadata:
      labels:
        app: todo
    spec:
      containers:
      - name: app
        image: node:18-alpine
        ports:
        - containerPort: 3000
```

---

## 🎤 Interview Preparation: Cracking the Workloads

> [!IMPORTANT]
> **Q1: Why should we use a Deployment instead of creating Raw Pods?**
> *Answer: **Raw Pods are not self-healing**. If a raw pod crashes or the node it's on fails, it's gone forever. A **Deployment** ensures that the "Desired State" is maintained; it will automatically replace pods to ensure your application remains available.*

> [!TIP]
> **Q2: Explain "Liveness" vs. "Readiness" Probes.**
> *Answer: A **Liveness Probe** checks if the application is still running (if it fails, K8s restarts the pod). A **Readiness Probe** checks if the app is ready to handle traffic (if it fails, K8s stops sending user traffic to that pod). Essential for zero-downtime deployments!*

---

## 📚 Next Steps
Now that you can define workloads, let's learn how to **Module 03: Install a Local K8s Cluster (KinD)**.
