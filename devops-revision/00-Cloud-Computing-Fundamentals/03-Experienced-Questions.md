# ☁️ Cloud Computing — Experienced Level (40 Questions)

> **Style**: Hinglish ELI5 + Real-World Architecture Examples
> **Goal**: Yeh 40 questions **senior/architect level** ke hain — design decisions, trade-offs, aur production experience cover karte hain.

---

## 1. How do you design a cloud architecture for high availability?

**Architecture Blueprint**:
```
                    ┌─── Route53 (DNS + Health Check) ───┐
                    │                                      │
              ┌─────▼─────┐                        ┌──────▼──────┐
              │ Region A   │                        │  Region B    │
              │            │                        │  (DR/Active) │
              │ ┌────────┐ │                        │ ┌────────┐  │
              │ │  ALB   │ │                        │ │  ALB   │  │
              │ └───┬────┘ │                        │ └───┬────┘  │
              │  ┌──▼──┐┌──▼──┐                     │  ┌──▼──┐   │
              │  │AZ-1 ││AZ-2 │                     │  │AZ-1 │   │
              │  │EC2s ││EC2s │                     │  │EC2s │   │
              │  └──┬──┘└──┬──┘                     │  └──┬──┘   │
              │  ┌──▼──────▼──┐                     │  ┌──▼────┐ │
              │  │ RDS Multi-AZ│                     │  │Read   │ │
              │  │ Primary     │ ──── Replication ───│  │Replica│ │
              │  └────────────┘                     │  └───────┘ │
              └────────────────┘                    └────────────┘
```

**Key Strategies**:
- Multi-AZ deployment (AZs isolated from each other)
- Load Balancer with health checks
- Auto-scaling groups (min 2 instances)
- RDS Multi-AZ (automatic failover)
- Cross-region replication for DR
- Route53 failover routing policy

---

## 2. What are the security measures you implement in cloud deployments?

**Security Layers (Defense in Depth)** 🏰:

| Layer | Implementation | Tools |
|:---|:---|:---|
| **Identity** | IAM, MFA, SSO, RBAC | AWS IAM, Okta, Azure AD |
| **Network** | VPC, Security Groups, NACLs, Private Subnets | VPC, WAF, Shield |
| **Compute** | Hardened AMIs, patch management, no SSH | SSM, Inspector |
| **Data** | Encryption (rest + transit), key rotation | KMS, ACM |
| **Application** | Input validation, OWASP top 10 | WAF rules, code scanning |
| **Monitoring** | Continuous threat detection | GuardDuty, SecurityHub, CloudTrail |
| **Compliance** | Automated checks, audit trails | AWS Config, Conformance Packs |

**Principle**: "Assume breach — then design your security."

---

## 3. How do you perform cloud cost optimization?

**Cost Optimization Pyramid**:
```
         ┌─────────────────┐
         │   Architecture   │  ← Biggest savings (serverless, right service)
         ├─────────────────┤
         │   Right-Sizing   │  ← Match instance to workload
         ├─────────────────┤
         │  Pricing Models  │  ← Reserved, Spot, Savings Plans
         ├─────────────────┤
         │   Waste Removal  │  ← Kill idle resources, old snapshots
         └─────────────────┘
```

**Quick Wins**:
- 🗑️ Delete unused EBS volumes, old snapshots, unattached EIPs
- ⏰ Auto-shutdown dev/staging at night (cron + Lambda)
- 📉 S3 Lifecycle policies — move old data to Glacier
- 🏷️ Tag everything — find who's spending what
- 📊 Weekly cost review meetings

**Real Impact**: "Saved $15K/month by switching batch jobs to Spot instances and implementing S3 Intelligent-Tiering."

---

## 4. What is hybrid cloud, and what are its benefits?

**Hybrid Cloud Architecture**:
```
┌──────────────────┐         VPN/Direct Connect        ┌──────────────────┐
│   On-Premises     │◄────────────────────────────────►│   Public Cloud    │
│                   │                                   │                   │
│ • Legacy Apps     │    Data sync, workload sharing    │ • Web Apps        │
│ • Sensitive Data  │                                   │ • Analytics       │
│ • Compliance      │                                   │ • Burst Capacity  │
└──────────────────┘                                   └──────────────────┘
```

**Benefits**:
- **Flexibility**: Sensitive data on-prem, scalable workloads on cloud
- **Compliance**: Meet data residency requirements (RBI, GDPR)
- **Cloud Bursting**: Spike aaya? Public cloud pe burst karo
- **Gradual Migration**: Slowly move to cloud, no big bang
- **Cost Balance**: Capital-heavy on-prem + pay-as-you-go cloud

---

## 5. Explain the role of APIs in cloud integration.

**APIs = Cloud ka Nervous System** 🧠: Services ek doosre se APIs ke through baat karti hain.

**Integration Patterns**:
```
Mobile App  ──► API Gateway ──► Microservice A ──► Database
                    │
Web App    ────────┘──────────► Microservice B ──► S3
                                      │
                               Microservice C ◄──┘ (Event-driven)
```

**API Types in Cloud**:
- **REST APIs**: HTTP-based, JSON data (most common)
- **GraphQL**: Client decides kya data chahiye
- **gRPC**: Fast, binary — microservices ke beech
- **WebSockets**: Real-time two-way communication

**API Gateway Benefits**: Rate limiting, auth, caching, monitoring — sab ek jagah.

---

## 6. How do you approach cloud service selection for an organization?

**Decision Framework** (RASCAL):

| Step | Action | Question |
|:---|:---|:---|
| **R**equirements | Business needs samjho | Kya build karna hai? Performance needs? |
| **A**rchitecture | Service model choose karo | IaaS vs PaaS vs SaaS? Serverless? |
| **S**ecurity | Compliance check karo | GDPR/HIPAA apply hota hai? |
| **C**ost | Total cost of ownership | On-demand vs Reserved? Data transfer costs? |
| **A**vailability | SLA review karo | 99.9% enough hai ya 99.99% chahiye? |
| **L**ock-in | Portability assess karo | Proprietary services kitne use ho rahe? |

---

## 7. Discuss the challenges of multi-cloud strategies.

**Multi-Cloud Reality Check**:

| Challenge | Reality | Mitigation |
|:---|:---|:---|
| **Complexity** | 3 clouds = 3 consoles, 3 IAMs, 3 billing | Use Terraform + single pane (Pulumi) |
| **Skills** | Team ko AWS bhi aana chahiye, Azure bhi | Specialize per team, cross-train |
| **Networking** | Cross-cloud communication = latency + cost | Minimize cross-cloud data transfer |
| **Security** | Consistent policies across clouds mushkil | Cloud-agnostic security tools (Prisma) |
| **Cost** | Discount programs provider-specific | Reserved instances per cloud |

**When Multi-Cloud Makes Sense**: Vendor lock-in avoid karna, best-of-breed services lena (GCP BigQuery + AWS EC2), regulatory requirements.

---

## 8. What is the role of automation in cloud management?

**Everything-as-Code**:
```
Infrastructure → Terraform/CloudFormation
Configuration  → Ansible/Chef
Pipeline       → Jenkinsfile/GitHub Actions YAML
Policy         → OPA (Open Policy Agent)
Security       → Security-as-Code (GuardDuty rules)
Monitoring     → Grafana dashboards as code
```

**Automation Impact**: "We reduced deployment time from 4 hours (manual) to 8 minutes (automated pipeline) and eliminated 95% of configuration-related incidents."

---

## 9. How do you implement CI/CD pipelines in the cloud?

**Production-Grade Pipeline**:
```
Developer Push → GitHub → GitHub Actions/Jenkins
      │
      ▼
┌─────────────┐    ┌──────────┐    ┌──────────┐    ┌────────────┐
│  Build &     │───►│  Unit     │───►│ Security │───►│ Integration│
│  Lint        │    │  Tests    │    │  Scan    │    │  Tests     │
└─────────────┘    └──────────┘    └──────────┘    └──────┬─────┘
                                                          │
      ┌───────────────────────────────────────────────────┘
      ▼
┌──────────┐    ┌───────────┐    ┌──────────────┐
│  Staging  │───►│  E2E      │───►│  Production  │
│  Deploy   │    │  Tests    │    │  Deploy      │
└──────────┘    └───────────┘    │  (Blue/Green)│
                                  └──────────────┘
```

**Key Practices**: Feature flags, canary deployments, automated rollback, post-deploy smoke tests.

---

## 10. What are the key considerations for migrating on-premises applications to the cloud?

**Migration Checklist**:
- [ ] Application assessment (dependencies, architecture, cloud-readiness)
- [ ] Data inventory (size, sensitivity, compliance requirements)
- [ ] Network planning (VPN/Direct Connect bandwidth)
- [ ] Security mapping (on-prem controls → cloud equivalents)
- [ ] Cost modeling (TCO comparison — on-prem vs cloud)
- [ ] Migration strategy per app (6 R's — Rehost, Refactor, etc.)
- [ ] Rollback plan (agar kuch galat ho toh wapas jaana)
- [ ] Team training (cloud skills development)
- [ ] Post-migration optimization (right-sizing after 30 days data)

---

## 11. How do you handle performance monitoring in cloud applications?

**Observability Stack**:

| Pillar | What | Tool |
|:---|:---|:---|
| **Metrics** | Numbers over time (CPU, latency) | Prometheus, CloudWatch |
| **Logs** | Event records | ELK Stack, CloudWatch Logs |
| **Traces** | Request journey across services | X-Ray, Jaeger, OpenTelemetry |
| **Dashboards** | Visual overview | Grafana, Datadog |
| **Alerts** | Anomaly notifications | PagerDuty, OpsGenie |

**4 Golden Signals** (Google SRE):
1. **Latency** — 95th percentile response time
2. **Traffic** — requests per second
3. **Errors** — 5xx error rate
4. **Saturation** — CPU/Memory/Disk utilization

---

## 12. Discuss your experience with serverless architectures.

**Serverless Decision Matrix**:

| ✅ Good Fit | ❌ Bad Fit |
|:---|:---|
| Event-driven processing | Long-running compute (ML training) |
| APIs with variable traffic | Predictable constant load |
| Cron jobs, scheduled tasks | WebSocket-heavy applications |
| Image/video processing | Apps needing full OS control |
| Prototyping & MVPs | Latency-sensitive (cold starts) |

**Cold Start Mitigation**: Provisioned concurrency, smaller packages, keep-warm pings.

**Production Example**: "Our notification system uses Lambda — processes 2M events/day. Cost? $45/month vs $400/month for EC2."

---

## 13. What is the role of artificial intelligence in cloud computing?

**AI + Cloud Integration**:

| AI in Cloud | Example |
|:---|:---|
| **AIOps** | Automated anomaly detection, self-healing |
| **Cost Optimization** | AI predicts usage patterns, recommends savings |
| **Security** | ML-based threat detection (GuardDuty) |
| **ML Platforms** | SageMaker, Vertex AI — train models at scale |
| **Pre-built AI** | Rekognition (image), Comprehend (text), Translate |
| **Auto-scaling** | Predictive scaling based on ML forecasts |

---

## 14. How do you manage identity and access in cloud environments?

**IAM Best Practices**:

```
Root Account
  └── Admin OU
        ├── Dev OU → Dev accounts (limited permissions)
        ├── Staging OU → Staging accounts
        └── Prod OU → Production accounts (strict policies)
              └── IAM Roles (not users) for services
```

**Key Principles**:
- **Least Privilege**: Minimum permissions needed
- **No Long-lived Credentials**: Use IAM Roles, not access keys
- **MFA Everywhere**: Especially root and admin
- **SSO**: One login for all accounts (AWS SSO / Azure AD)
- **SCPs**: Service Control Policies at org level
- **Regular Access Reviews**: Quarterly audit — remove unused

---

## 15. What are the best practices for data governance in the cloud?

**Data Governance Framework**:

| Pillar | Action |
|:---|:---|
| **Classification** | Label data: Public, Internal, Confidential, Restricted |
| **Access Control** | RBAC — classified data = limited access |
| **Encryption** | Confidential/Restricted = mandatory encryption |
| **Retention** | Define how long to keep data (legal requirements) |
| **Quality** | Validation, deduplication, cleansing pipelines |
| **Lineage** | Track where data came from and where it goes |
| **Audit** | Log all data access for compliance |

---

## 16. Explain the concept of edge computing in relation to cloud services.

**Edge + Cloud Architecture**:
```
IoT Devices/Users ──► Edge Nodes (local processing) ──► Cloud (heavy processing + storage)
        │                    │                               │
   Real-time data      Quick decisions                 Deep analytics
   (sensors, cameras)  (< 1ms response)               (ML training, reporting)
```

**Use Cases**: Autonomous vehicles (can't wait for cloud response), factory automation, AR/VR, smart cities.

**Key Providers**: AWS Outposts, Azure Stack Edge, Google Distributed Cloud.

---

## 17. How do you handle vendor lock-in in cloud computing?

**Lock-in Spectrum**:
```
High Lock-in ◄──────────────────────────► Low Lock-in

DynamoDB    Aurora    RDS PostgreSQL    Docker/K8s    Open-source on VMs
Proprietary ═════════════════════════════════════════ Portable
```

**Strategies**: Containerize (Docker/K8s), use IaC (Terraform), prefer managed open-source (RDS PostgreSQL over DynamoDB), abstract cloud-specific APIs behind interfaces.

---

## 18. What are the implications of GDPR on cloud deployments?

**GDPR Compliance Checklist for Cloud**:
- [ ] Data Processing Agreement (DPA) with cloud provider
- [ ] Data residency — EU data in EU regions
- [ ] User consent before data collection
- [ ] Right to erasure — delete user data on request
- [ ] Data portability — export data in standard formats
- [ ] Breach notification — 72 hours to report
- [ ] Privacy by design — encrypt, minimize, anonymize
- [ ] DPO (Data Protection Officer) appointed

**Penalty**: Up to €20M or 4% of global annual revenue — whichever is higher! 😱

---

## 19. How do you ensure compliance with industry standards in cloud applications?

**Compliance Automation**:
```
Regulatory Standard (HIPAA/PCI/SOC2)
         ↓
Define Rules → AWS Config Rules / Azure Policy
         ↓
Continuous Monitoring (Real-time compliance check)
         ↓
Auto-Remediation (Non-compliant? Auto-fix!)
         ↓
Reports & Dashboard (Auditor-ready)
```

**Key Tools**: AWS Config, Azure Policy, GCP Organization Policy, Cloud Custodian, Prisma Cloud.

---

## 20. Discuss your experience with cloud service orchestration and management tools.

**Orchestration Toolkit**:

| Category | Tool | Purpose |
|:---|:---|:---|
| **IaC** | Terraform | Multi-cloud infrastructure provisioning |
| **Container Orchestration** | Kubernetes (EKS/GKE/AKS) | Container lifecycle management |
| **Configuration** | Ansible | Server configuration automation |
| **Workflow** | AWS Step Functions, Airflow | Multi-step process orchestration |
| **Monitoring** | Prometheus + Grafana | Metrics collection + visualization |
| **Cost** | CloudHealth, Spot.io | Multi-cloud cost optimization |
| **CI/CD** | ArgoCD, GitHub Actions | GitOps deployments |

---

## 21. How do you implement and manage multi-tenancy in cloud applications?

**Multi-Tenancy Models**:

| Model | Isolation | Cost | Complexity |
|:---|:---|:---|:---|
| **Shared DB, Shared Schema** | Low (row-level) | $ | Low |
| **Shared DB, Separate Schema** | Medium | $$ | Medium |
| **Separate DB per Tenant** | High | $$$ | High |

**Implementation**: Tenant ID in every table, Row-Level Security (RLS) in PostgreSQL, separate encryption keys per tenant, tenant-aware caching.

---

## 22. What strategies do you use for cloud data migration?

**Data Migration Pipeline**:
```
Source DB → Assessment → Schema Convert → Full Load → CDC (Change Data Capture) → Cutover
                                                          │
                                            Continuous sync until cutover ✅
```

**Tools**: AWS DMS, Azure Database Migration Service, Google Database Migration Service, Striim.

**Key Tip**: "Never do a big-bang cutover. Use CDC for continuous replication, test thoroughly, then switch DNS. Keep rollback ready for 48 hours."

---

## 23. How do you address application performance tuning in the cloud?

**Performance Optimization Checklist**:
- [ ] **Caching**: Redis/ElastiCache — reduce DB hits by 80%
- [ ] **CDN**: Static assets via CloudFront — global fast delivery
- [ ] **DB Optimization**: Query tuning, read replicas, connection pooling
- [ ] **Right instance type**: Compute-optimized for CPU-heavy, Memory-optimized for in-memory
- [ ] **Async processing**: SQS/SNS for non-blocking operations
- [ ] **Code profiling**: Find bottleneck functions (X-Ray, flame graphs)
- [ ] **Auto-scaling**: Scale based on actual metrics, not just CPU

---

## 24. What are the risks associated with cloud computing?

**Risk Matrix**:

| Risk | Probability | Impact | Mitigation |
|:---|:---|:---|:---|
| **Data Breach** | Medium | Critical | Encryption, IAM, monitoring |
| **Downtime** | Low | High | Multi-AZ, multi-region, SLA review |
| **Vendor Lock-in** | High | Medium | Containers, IaC, open standards |
| **Cost Overrun** | High | Medium | Budgets, alerts, right-sizing |
| **Compliance Violation** | Medium | Critical | Automated compliance checks |
| **Data Loss** | Low | Critical | Backups, replication, versioning |

---

## 25. How do you implement secure access controls in cloud environments?

**Zero Trust Architecture**:
```
"Never trust, always verify" 🔒

User → MFA → Identity Provider → Policy Engine → Access Decision
                                       │
                              Check: Role + Context + Device + Location
                                       │
                              ├── Allowed → Least privilege access
                              └── Denied → Log & Alert
```

**Implementation**: SSO (Okta/Azure AD), conditional access policies, just-in-time access, privileged access management (PAM).

---

## 26. Discuss your experience with cloud-native tools and frameworks.

**Cloud-Native Landscape** (CNCF):

| Category | Tools |
|:---|:---|
| **Runtime** | Docker, containerd, CRI-O |
| **Orchestration** | Kubernetes, Nomad |
| **Service Mesh** | Istio, Linkerd |
| **CI/CD** | ArgoCD, Flux, Tekton |
| **Observability** | Prometheus, Grafana, Jaeger |
| **Storage** | Rook, Longhorn |
| **Security** | Falco, OPA, cert-manager |
| **Serverless** | Knative, OpenFaaS |

---

## 27. How do you leverage cloud services for disaster recovery?

**DR Architecture (Warm Standby)**:
```
Primary (Mumbai)                    DR (Singapore)
┌──────────────┐                   ┌──────────────┐
│ Full capacity │   Cross-region   │ Scaled-down   │
│ Active traffic│◄──replication──►│ Standby       │
│ RDS Primary   │                  │ RDS Read      │
│ EC2 ASG (10)  │                  │ EC2 ASG (2)   │
└──────────────┘                   └──────────────┘
        │                                  │
        └──── Route53 Health Check ────────┘
              (Auto-failover if primary down)
```

**RPO**: ~seconds (cross-region replication). **RTO**: ~5 minutes (scale up standby).

---

## 28. What is the role of observability in cloud architecture?

**Observability = Monitoring + Context + Understanding**

```
         Observability
        ┌─────┬─────┬─────┐
     Metrics  Logs  Traces
        │      │      │
    "What"  "Why"  "Where"
   happened happened in the
                    flow
```

**Observability helps answer**: "Why is the checkout page slow for users in Mumbai?" — not just "CPU is high."

**Tools**: OpenTelemetry (unified collection), Grafana (visualize), Loki (logs), Tempo (traces).

---

## 29. How do you handle compliance with health data regulations in the cloud?

**HIPAA on Cloud — Key Controls**:

| Requirement | Implementation |
|:---|:---|
| **PHI Encryption** | AES-256 at rest, TLS 1.2+ in transit |
| **Access Control** | RBAC, MFA, audit logs on all PHI access |
| **Audit Trail** | CloudTrail + CloudWatch Logs — immutable |
| **BAA** | Business Associate Agreement with cloud provider |
| **Data Backup** | Encrypted backups, tested quarterly |
| **Incident Response** | Documented plan, <24hr breach notification |

**Use HIPAA-eligible services only**: Not all cloud services are HIPAA-eligible. Check provider's compliance page.

---

## 30. What are the key metrics you monitor in cloud applications?

**Dashboard Essentials**:

| Category | Metrics |
|:---|:---|
| **Performance** | P50/P95/P99 Latency, Throughput (RPS) |
| **Errors** | 4xx rate, 5xx rate, Error budget remaining |
| **Resources** | CPU%, Memory%, Disk I/O, Network I/O |
| **Business** | Active users, Orders/min, Revenue/hour |
| **Cost** | Daily spend, cost per transaction |
| **Availability** | Uptime %, health check pass rate |

**Alert Thresholds**: SLO-based alerting > static thresholds. "Alert when error budget burn rate exceeds 2x."

---

## 31. How do you manage and orchestrate microservices in the cloud?

**Microservices Management Stack**:
```
┌────────────────────────────────────────┐
│           API Gateway (Kong/APIGW)      │  ← Entry point
├────────────────────────────────────────┤
│           Service Mesh (Istio)          │  ← Service-to-service
├───────────┬──────────┬─────────────────┤
│ Service A │ Service B│ Service C       │  ← Business logic
│ (Node.js) │ (Python) │ (Go)           │
├───────────┴──────────┴─────────────────┤
│           Kubernetes (EKS/GKE)          │  ← Orchestration
├────────────────────────────────────────┤
│     Observability (Prometheus+Grafana)  │  ← Monitoring
└────────────────────────────────────────┘
```

---

## 32. What are the advantages and disadvantages of using a cloud broker?

| Pros ✅ | Cons ❌ |
|:---|:---|
| Multi-cloud comparison | Extra cost (broker fees) |
| Cost optimization insights | Added dependency |
| Simplified management | May not support all services |
| Vendor-neutral advice | Broker could become single point of failure |
| Compliance assistance | May slow down decision-making |

**When to use**: Large enterprises managing 3+ cloud providers. **When to skip**: Small teams using single provider.

---

## 33. How do you handle data privacy concerns in cloud computing?

**Privacy Engineering Practices**:
- **Data Minimization**: Collect only what you need — don't hoard
- **Anonymization**: Remove PII where possible (analytics ke liye anonymized data use karo)
- **Encryption**: At rest + in transit + application-level for sensitive fields
- **Access Controls**: Need-to-know basis — DBA ko prod customer data access mat do unnecessarily
- **Data Residency**: Indian users ka data India mein (RBI, GDPR equivalent)
- **Right to Delete**: User bole "delete my data" → actually delete within 30 days
- **Privacy Impact Assessment**: New feature launch se pehle privacy review

---

## 34. Discuss your experience with implementing monitoring solutions in the cloud.

**Production Monitoring Setup**:
```
Application → OpenTelemetry SDK → Collector
                                      │
                        ┌─────────────┼─────────────┐
                        ▼             ▼             ▼
                   Prometheus     Loki          Tempo
                   (Metrics)     (Logs)        (Traces)
                        │             │             │
                        └─────────────┼─────────────┘
                                      ▼
                                   Grafana
                                 (Dashboards)
                                      │
                                      ▼
                              PagerDuty/Slack
                                (Alerts)
```

**Key Learnings**: Start with 4 golden signals, add business metrics, use SLO-based alerting instead of static thresholds.

---

## 35. How do you optimize cloud resource usage?

**Optimization Cycle**:
```
Monitor → Analyze → Recommend → Implement → Verify → Monitor (repeat)
```

**Top Optimizations**:
1. **Right-sizing**: t3.xlarge → t3.medium (if CPU < 30%)
2. **Spot/Preemptible**: Batch jobs, CI runners — 60-90% savings
3. **Auto-scaling**: Min instances based on non-peak, max for peak
4. **Storage tiering**: S3 Intelligent-Tiering auto-moves data
5. **Reserved capacity**: 1-year RI for steady-state workloads
6. **Architecture**: Serverless for sporadic workloads, containers for rest

---

## 36. What is your approach to managing cloud vendor relationships?

**Vendor Management Framework**:
- **SLA Tracking**: Monthly performance review against SLA
- **Cost Reviews**: Quarterly business reviews with account team
- **Escalation Path**: Defined contacts for critical issues
- **Contract Negotiation**: EDP (Enterprise Discount Program) for large spend
- **Multi-vendor leverage**: "Azure offers this cheaper" — negotiation tool
- **Technical Partnership**: TAM (Technical Account Manager) for architecture reviews

---

## 37. How do you ensure application reliability in the cloud?

**Reliability Engineering Practices**:

| Practice | Implementation |
|:---|:---|
| **Redundancy** | Multi-AZ, multi-region deployment |
| **Chaos Engineering** | Randomly kill instances (Netflix Chaos Monkey) |
| **Circuit Breakers** | Prevent cascade failures (Hystrix pattern) |
| **Graceful Degradation** | Feature X down? Show cached content |
| **Health Checks** | Deep health checks (DB, dependencies) |
| **Error Budgets** | 0.1% error allowed — balance reliability vs velocity |
| **Runbooks** | Documented procedures for common failures |
| **Post-Mortems** | Blameless analysis after incidents |

---

## 38. Explain how you would implement an API gateway in a cloud environment.

**API Gateway Architecture**:
```
Clients (Web/Mobile/IoT)
          │
          ▼
┌─────────────────────┐
│    API Gateway       │  ← AWS API Gateway / Kong / Apigee
│                     │
│ • Authentication    │  (OAuth2, JWT validation)
│ • Rate Limiting     │  (1000 req/min per user)
│ • Caching          │  (Cache GET responses)
│ • Request Transform│  (Header manipulation)
│ • Logging          │  (Every request logged)
│ • Routing          │  (/users → User Service)
│                     │  (/orders → Order Service)
└────────┬────────────┘
         │
    ┌────▼────┬──────────┐
    ▼         ▼          ▼
User Svc  Order Svc  Payment Svc
```

**Key Considerations**: Custom domain + SSL, versioning (v1/v2), throttling per client, WebSocket support for real-time.

---

## 39. How do you assess and mitigate cloud security risks?

**Security Assessment Process**:
1. **Threat Modeling**: STRIDE methodology — identify threats per component
2. **Vulnerability Scanning**: Automated scans (Inspector, Qualys)
3. **Penetration Testing**: Annual third-party pen test
4. **Compliance Audit**: AWS Config rules, CIS Benchmarks
5. **Risk Register**: Document risks, assign owners, track remediation
6. **Incident Response Plan**: Tested quarterly with tabletop exercises

**STRIDE Model**:
| Threat | Example | Mitigation |
|:---|:---|:---|
| **S**poofing | Fake identity | MFA, strong auth |
| **T**ampering | Modify data | Integrity checks, encryption |
| **R**epudiation | Deny actions | Audit logs, CloudTrail |
| **I**nformation Disclosure | Data leak | Encryption, access control |
| **D**enial of Service | DDoS attack | Shield, WAF, rate limiting |
| **E**levation of Privilege | Unauthorized access | Least privilege, RBAC |

---

## 40. Discuss your experience with using Infrastructure as Code (IaC) tools.

**IaC Tool Comparison**:

| Tool | Language | Cloud Support | Best For |
|:---|:---|:---|:---|
| **Terraform** | HCL | Multi-cloud | Production infra, most popular |
| **CloudFormation** | JSON/YAML | AWS only | Deep AWS integration |
| **Pulumi** | Python/TS/Go | Multi-cloud | Devs who prefer real languages |
| **Bicep** | Bicep DSL | Azure only | Azure-native deployments |
| **CDK** | Python/TS | AWS (primary) | Devs who prefer code over config |

**Production IaC Workflow**:
```
Code Change → PR Review → Terraform Plan (preview) → Approval → Terraform Apply → Verify
```

**Best Practices**:
- State file in remote backend (S3 + DynamoDB lock)
- Modular code — reusable modules for VPC, ECS, RDS
- Environment separation — dev/staging/prod with same code
- Drift detection — regularly check if manual changes happened
- CI/CD for infra — GitOps approach

---

> [!IMPORTANT]
> **Interview Pro Tips**:
> 1. Questions ke answers mein **real experience** batao — "In my last project, we..."
> 2. **Trade-offs** discuss karo — "We chose X over Y because..."
> 3. **Numbers** do — "Reduced latency by 40%, saved $10K/month"
> 4. **Architecture diagrams** whiteboard pe banaao — visual answers strong lagti hain
> 5. **Failure stories** share karo — "Once our deployment failed because... and we learned..."
