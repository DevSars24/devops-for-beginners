# 04: Kubernetes Services & Networking

In Kubernetes, Pods are **ephemeral** (short-lived). Their IP addresses change every time they are restarted. To provide a **stable network address** for a group of Pods, we use a **Service**.

---

## 🏗️ What is a Service?

A **Service** is an abstraction that defines a logical set of Pods and a policy to access them. It acts as a **Load Balancer** for a group of Pods.

### 🌟 Example: A ClusterIP Service
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-web-service
spec:
  selector:
    app: todo # Matches the labels in the Deployment
  ports:
  - protocol: TCP
    port: 80 # Service port
    targetPort: 3000 # Pod port
```

---

## 🏗️ The Three Standard Service Types

| Model | Use Case | Analogy |
| :--- | :--- | :--- |
| **ClusterIP** | Default. Used for internal communication between services. | An **Internal Extension** in an office building. |
| **NodePort** | Exposes the service on a specific port (30000-32767) on all nodes. | A **Side Door** that allows people to enter the building from the street. |
| **LoadBalancer** | Exposes the service externally using a cloud provider's Load Balancer (GCP/AWS). | The **Main Entrance** of a skyscraper with a doorman. |
| **ExternalName** | Maps a service to a DNS name (e.g., `google.com`) outside the cluster. | A **Forwarding Address**. |

---

## 🚀 Intro to Ingress

A **Service** can only handle L4 traffic (TCP/UDP). For L7 (HTTP/HTTPS) routing, we use **Ingress**.
- **Path-based Routing**: `domain.com/users` goes to Service A, `domain.com/orders` goes to Service B.
- **SSL/TLS Termination**: Manege certificates in one place for all services.
- **Host-based Routing**: `dev.app.com` goes to one service, `prod.app.com` goes to another.

**Analogy**: If a Service is a **Hotel Room**, then Ingress is the **Reception Desk** 🏨. The receptionist checks your ID (SSL/Auth) and tells you which room (Service) to go to.

---

## 🎤 Interview Preparation: Cracking the Networking

> [!IMPORTANT]
> **Q1: How do Pods find other Pods in the same cluster?**
> *Answer: Kubernetes uses an **Internal DNS Service (CoreDNS)**. When you create a service named `my-api`, Kubernetes creates a DNS entry for it. Other pods can simply reach it at `http://my-api` or `http://my-api.default.svc.cluster.local`.*

> [!TIP]
> **Q2: Why should you use Ingress instead of many LoadBalancer services?**
> *Answer: **Cost and Complexity**. Each `LoadBalancer` service creates a cloud resource that costs money ($15-$30/month). An **Ingress** allows you to use a **single Load Balancer** to route traffic to hundreds of internal services based on the URL path or hostname.*

---

## 📚 Next Steps
Now that your apps can talk, let's learn how to **Module 05: Manage Configurations & Secrets**.
