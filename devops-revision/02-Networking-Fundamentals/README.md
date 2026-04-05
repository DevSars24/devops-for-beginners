# 🌐 Module 02: Networking for DevOps

In DevOps, networking is the "Road" on which all your data traffic travels. Understanding how servers communicate is essential for building scalable and secure systems.

## 🛰️ The OSI Model (ELI5)

Think of the OSI model as the **E-commerce Delivery Lifecycle**.
1. **Physical Layer**: The delivery truck traveled on the road (The hardware/cables/Wi-Fi).
2. **Network Layer**: The package had your address and Pincode (IP Address).
3. **Transport Layer**: Checking whether the package arrived intact (TCP/UDP protocols).
4. **Application Layer**: You opened the Amazon app and used its features (HTTP/DNS).

### 🔑 Key Concepts for Technical Discussions
- [ ] **DNS (Domain Name System)**: Often called the "Phonebook" of the internet. It converts human-readable domains (google.com) into machine-readable IP addresses (142.250.x.x).
- [ ] **VPC (Virtual Private Cloud)**: A private, isolated section of a public cloud. In GCP and AWS, VPCs are the standard for network-level isolation.
- [ ] **Load Balancing**: Imagine a sudden surge of 10,000 orders on an app like **Zomato**. A single server would crash. A Load Balancer automatically distributes this traffic across multiple servers (e.g., 10 servers) to prevent downtime.

---

## 🛠️ Essential Commands (Networking Cheat Sheet)
- `ping <domain>`: A basic connectivity test (Is the target reachable?).
- `dig <domain>` or `nslookup`: Troubleshoot DNS resolution issues (A common interview topic!).
- `netstat -tulnp`: Identify which applications are "listening" on specific ports.
- `curl -v http://example.com`: Inspect HTTP requests and responses in detail (Request headers, status codes, and response body).

---

## ❓ Interview Preparation (Mastering the Discussion)

> [!IMPORTANT]
> **Q1: What is the difference between TCP and UDP?**
> *Answer: TCP (Transmission Control Protocol) is **connection-oriented** and reliable. Use it for data that must be complete, like file downloads (via a Three-way handshake). UDP (User Datagram Protocol) is **connectionless** and faster, but it may lose some data. This makes it ideal for real-time applications like video calls and gaming.*

> [!TIP]
> **Q2: What is Subnetting?**
> *Answer: Subnetting is the process of dividing a large network into smaller, more manageable sub-networks (subnets). For example, separating an organization's network by department (Engineering, Finance, Support) for better security and performance.*

---

## 📚 Resources
- [Networking for Beginners (YouTube)](https://www.youtube.com/watch?v=S7EZueX_p8Y)
- [Cloudflare: Understanding the Network Layer](https://www.cloudflare.com/learning/network-layer/what-is-networking/)
- [High Performance Browser Networking by Ilya Grigorik](https://hpbn.co/)
