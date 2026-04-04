# 🌐 Module 02: Networking Fundamentals

As a DevOps engineer, you must understand how data moves across the network. From DNS lookups to Load Balancers, networking is everywhere.

## 🛰️ The OSI Model (Simplified)
Knowing which layer a tool operates on is crucial for troubleshooting.
1. **Physical Layer**: Hubs, Cables.
2. **Data Link Layer**: Switches, MAC addresses.
3. **Network Layer**: Routers, IP Addresses (IPv4, IPv6).
4. **Transport Layer**: TCP (three-way handshake), UDP (best effort).
5. **Session/Presentation Layer**: SSL/TLS encryption.
6. **Application Layer**: HTTP, DNS, SMTP, FTP.

---

## 🔑 Key Networking Pillars
- [ ] **DNS (Domain Name System)**: Translating domain names (like google.com) to IP addresses.
- [ ] **DHCP**: Assigning IP addresses dynamically to devices on a network.
- [ ] **VPC (Virtual Private Cloud)**: Isolating network resources in the cloud.
- [ ] **Subnetting**: Dividing a larger network into smaller, manageable sub-networks (CIDR notation).
- [ ] **Firewalls & Security Groups**: Controlling inbound and outbound traffic.
- [ ] **Load Balancing**: Distributing incoming traffic across multiple servers (L4 vs L7).

---

## 🛠️ Essential Networking Commands
- `ping google.com`: Test connectivity.
- `dig google.com` or `nslookup google.com`: Troubleshoot DNS issues.
- `curl -v http://example.com`: Detailed HTTP request/response.
- `netstat -tulnp`: List all listening ports.
- `traceroute 8.8.8.8`: Map the path packets take to a destination.
- `tcpdump -i eth0`: Capture network packets for analysis.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the difference between TCP and UDP.**
> *A: TCP is connection-oriented, reliable, and ensures packets arrive in order (used for HTTP, SSH). UDP is connectionless, faster, and doesn't guarantee delivery (used for Video Streaming, DNS).*

> [!TIP]
> **Q2: What happens when you type 'google.com' in your browser?**
> *A: 1. Browser checks cache. 2. OS checks hosts file. 3. DNS lookup. 4. TCP 3-way handshake. 5. SSL/TLS handshake. 6. HTTP request. 7. Server response.*

---

## 📚 Resources
- [Cloudflare's Learning Center](https://www.cloudflare.com/learning/)
- [Computer Networking: A Top-Down Approach](https://jim.uta.edu/utacourses/cse3441/notes/Ch1_v7.pdf) (Classic Book)
- [Cisco Networking Academy](https://www.netacad.com/)
