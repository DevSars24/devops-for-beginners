# 🚢 Module 06: Kubernetes Orchestration

Docker is for building containers; Kubernetes is for managing them at scale. It handles automated deployment, scaling, and management of containerized applications.

## 🏗️ Kubernetes Cluster Components
### 1. Control Plane (The "Brain")
- **API Server**: Central gateway that processes all requests.
- **Etcd**: Key-value store (the entire "memory" of the cluster).
- **Scheduler**: Decides which pods run on which nodes.
- **Controller Manager**: Maintains the desired state (e.g., if a pod crashes, restart it).

### 2. Worker Nodes (The "Execution")
- **Kubelet**: The "Agent" on each node that talks to the control plane.
- **Kube-proxy**: Handles networking and routing for the pods.
- **Pods**: The smallest deployable units in K8s (it contains one or more containers).

---

## 🔑 Crucial K8s Objects
| Object | Description | Analogy |
| :--- | :--- | :--- |
| **Pods** | Encapsulation of one or more containers. | A single shipping container. |
| **Deployment** | Manages the creation and scaling of pods. | The management of a fleet of containers. |
| **Service** | Provides a stable network IP/address for pods. | The "Receptionist" routing traffic. |
| **Ingress** | Rules to manage external traffic for services. | The "Main Gate" of a hotel. |
| **ConfigMaps/Secrets** | Store configuration/sensitive data separately. | Environment variables for the apps. |

---

## 🛠️ Most-Used Kubectl Commands
- `kubectl get pods`: List all running pods in the current namespace.
- `kubectl get nodes`: Check the health of cluster nodes.
- `kubectl apply -f manifest.yaml`: Create or update resources via a YAML file.
- `kubectl describe pod <name>`: Get detailed info about a specific pod (great for debugging!).
- `kubectl logs <pod-name>`: See the stdout/stderr logs of a pod.
- `kubectl exec -it <pod-name> -- bash`: Jump into a container inside a pod.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the difference between a Headless Service and a standard ClusterIP.**
> *A: A standard ClusterIP service provides a single IP address and load balances across pods. A Headless Service doesn't have an IP; it returns the IP addresses of the underlying pods directly via DNS (useful for stateful sets).*

> [!TIP]
> **Q2: What is the "Desired State" in Kubernetes?**
> *A: You define how your app should look (e.g., 5 copies running), and K8s constantly works to match the "Actual State" with the "Desired State."*

---

## 📚 Resources
- [Kubernetes Documentation](https://kubernetes.io/docs/home/)
- [K3s (Lightweight K8s)](https://k3s.io/)
- [Minikube (Local cluster)](https://minikube.sigs.k8s.io/)
- [Kubernetes Academy by VMware](https://kubernetes.academy/)
