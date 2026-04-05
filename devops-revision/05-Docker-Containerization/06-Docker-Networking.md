# 06: Docker Networking Models & Commands

Docker provides a way for containers to communicate with each other, the host, and the outside world via **Docker Networking**. By default, Docker sets up three network types.

---

## 🏗️ The Three Standard Networking Models

| Model | Use Case | Analogy |
| :--- | :--- | :--- |
| **Bridge** | Default. Used for containers to communicate with each other on the same host. | An **Internal Intercom System** in an office building. |
| **Host** | The container shares the host's networking stack directly. No isolation. | An **Open Door** where the office and the street are the same. |
| **Overlay** | Used for multi-host communication (e.g., Docker Swarm or Kubernetes clusters). | A **Private Tunnel** connecting two different office buildings. |
| **None** | No networking. The container is isolated. | A **Soundproof Room** with no windows or doors. |

---

## 🛠️ Common Docker Networking Commands

| Command | Action |
| :--- | :--- |
| **`docker network ls`** | List all Docker networks on the host. |
| **`docker network inspect <net_name>`** | View details (IP addresses of connected containers). |
| **`docker network create <net_name>`** | Create a new user-defined bridge network. |
| **`docker network connect <net> <container>`** | Connect a running container to a network. |
| **`docker network disconnect <net> <container>`** | Disconnect a container from a network. |
| **`docker network rm <net_name>`** | Delete a network. |

---

## 🌟 Hands-on: Creating a Custom Network

To connect two containers (e.g., a Web app and a Database), it's a best practice to create a **custom network**.

```bash
# 1. Create a custom bridge network
docker network create my-net

# 2. Run a Redis database container on the network
docker run -d --name redis-db --network my-net redis:alpine

# 3. Run a Web App container on the SAME network
# Now, the 'web-app' can ping 'redis-db' by its CONTAINER NAME!
docker run -d --name web-app --network my-net my-custom-app
```

**Key Benefit**: You don't need to worry about IP addresses. Docker's internal DNS handles everything.

---

## 🎤 Interview Preparation: Cracking the Networking

> [!IMPORTANT]
> **Q1: Can two containers on different bridge networks communicate by default?**
> *Answer: No. By default, containers on different networks are isolated for security. You must either connect one container to both networks or use an Overlay network.*

> [!TIP]
> **Q2: Why should you use user-defined bridge networks instead of the default "bridge"?**
> *Answer: User-defined bridge networks provide **Automatic DNS resolution**. In the default bridge, you have to use IP addresses or the `--link` (legacy) command to allow containers to talk to each other. In a custom network, they can communicate by name.*

---

## 📚 Next Steps
Now that your containers can talk, let's learn how to **Module 07: Use Docker Compose for Multi-Container Apps**.
