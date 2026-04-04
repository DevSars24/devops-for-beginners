# ☁️ Module 00: Cloud Computing Fundamentals

Understanding the "Why" and "How" of the Cloud before diving into specific providers like AWS or Azure.

## 🌟 What is Cloud Computing?
At its simplest, cloud computing is the delivery of computing services—including servers, storage, databases, networking, software, analytics, and intelligence—over the Internet ("the cloud") to offer faster innovation, flexible resources, and economies of scale.

### 🔑 Key Cloud Concepts
- [ ] **On-Demand Self-Service**: Provision resources without human intervention from the provider.
- [ ] **Broad Network Access**: Capabilities are available over the network through standard mechanisms.
- [ ] **Resource Pooling**: The provider's resources are pooled to serve multiple consumers (Multi-tenancy).
- [ ] **Rapid Elasticity**: Automatically scale up or down based on demand.
- [ ] **Measured Service**: Pay-as-you-go pricing model.

---

## 🏗️ Service Models (SPI Model)
| Model | Description | Analogy (The Pizza Analogy) |
| :--- | :--- | :--- |
| **IaaS** (Infrastructure) | You manage OS, Apps, Data. Provider manages Hardware. | Buying a frozen pizza and baking it at home. |
| **PaaS** (Platform) | You manage Data and Apps. Provider manages OS/Runtime. | Pizza delivery (they cook it, you provide the table/drinks). |
| **SaaS** (Software) | Provider manages everything. You just use the app. | Dining out at a pizza restaurant. |

---

## 🌍 Deployment Models
1. **Public Cloud**: Resources owned and operated by a third-party (AWS, Azure, GCP).
2. **Private Cloud**: Resources used exclusively by one business or organization.
3. **Hybrid Cloud**: Combines public and private clouds, allowing data/apps to be shared between them.
4. **Multi-Cloud**: Using multiple cloud providers to avoid vendor lock-in.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the Shared Responsibility Model.**
> *A: In the cloud, security is shared. The provider is responsible for "Security OF the Cloud" (hardware, datacenters), and the customer is responsible for "Security IN the Cloud" (data, OS configuration, IAM).*

> [!TIP]
> **Q2: What is the difference between Scalability and Elasticity?**
> *A: Scalability is the ability to handle increased load (Vertical vs Horizontal). Elasticity is the ability to automatically grow or shrink based on that load in real-time.*

---

## 📚 Resources
- [NIST Definition of Cloud Computing](https://csrc.nist.gov/publications/detail/sp/800-145/final)
- [AWS Cloud Essentials](https://aws.amazon.com/training/digital/aws-cloud-practitioner-essentials/)
- [Microsoft Azure Fundamentals](https://learn.microsoft.com/en-us/training/paths/az-900-describe-cloud-concepts/)
