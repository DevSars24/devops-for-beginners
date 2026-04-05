# 🚢 Module 06: Kubernetes (K8s) Orchestration

While Docker is used to build and package containers, **Kubernetes** is the industry standard for managing them at scale. Kubernetes automates the deployment, scaling, and operational management of containerized applications across a cluster of servers.

## 🏗️ Kubernetes Cluster Architecture
Welcome to the Kubernetes Mastery section. This module covers everything from basic cluster architecture and pod development to advanced scaling, networking, and persistent storage management.

## 📖 Detailed Revision Guides

To master Kubernetes, follow these high-quality, professional guides in order:

1. **[01-K8s-Introduction-Architecture](./01-K8s-Introduction-Architecture.md)**: Understanding the Control Plane, Worker Nodes, and the "Brain" of the cluster.
2. **[02-K8s-Pods-Workloads](./02-K8s-Pods-Workloads.md)**: Mastering Pods, Deployments, and ReplicaSets for declarative updates.
3. **[03-K8s-Installation-KinD](./03-K8s-Installation-KinD.md)**: Setting up a local, multi-node Kubernetes cluster using KinD.
4. **[04-K8s-Services-Networking](./04-K8s-Services-Networking.md)**: Implementing ClusterIP, NodePort, LoadBalancer, and Ingress routing.
5. **[05-K8s-Config-Secrets](./05-K8s-Config-Secrets.md)**: Managing application configuration with ConfigMaps and Secrets.
6. **[06-K8s-Scaling-Resources](./06-K8s-Scaling-Resources.md)**: Optimizing resource requests/limits and implementing Horizontal Pod Autoscaling (HPA).
7. **[07-K8s-Storage-Mastery](./07-K8s-Storage-Mastery.md)**: Mastering PersistentVolumes, Claims, and Dynamic Storage Provisioning.

---

## 🛠️ Hands-on Concepts to Practice

- [ ] Deploy a multi-replica Nginx application using a Deployment.
- [ ] Expose a service internally (ClusterIP) and externally (NodePort).
- [ ] Implement a **Liveness Probe** to detect and restart unhealthy pods.
- [ ] Use a **ConfigMap** to inject environment variables into your application.
- [ ] Scale a deployment manually (`kubectl scale`) and automatically (`kubectl autoscale`).

---

## 🎤 Interview Preparation: Kubernetes Mastery

Each sub-guide above contains a **"Cracking the Interview"** section with targeted questions. Common topics include:
- The Kubernetes "Control Plane" components.
- The difference between a Deployment and a StatefulSet.
- How Kubernetes handles zero-downtime rolling updates.
- Managing persistent data in an ephemeral environment.

---

## 📚 Official Resources
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [Kubernetes Academy by VMware](https://kubernetes.academy/)
- [Kexplore (Interactive Visualization)](https://kexplore.io/)
- [K8s.af (Kubernetes Failure Stories)](https://k8s.af/)
- [Interactive Kubernetes Tutorials (Katacoda replacement)](https://killercoda.com/)
- [Certified Kubernetes Administrator (CKA) Guide](https://github.com/walidshaari/Kubernetes-Certified-Administrator)
