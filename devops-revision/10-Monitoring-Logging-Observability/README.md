# 📊 Module 10: Monitoring, Logging & Observability

Observability is about understanding what's happening inside your system by looking at its external outputs (Logs, Metrics, Traces).

## 🏔️ The Three Pillars of Observability
### 1. Metrics (What happened?)
Quantitative data about processes (e.g., CPU %, Error rates, Request duration).
- **Tool**: Prometheus.

### 2. Logging (Why did it happen?)
Qualitative, timestamped records of events (e.g., application errors, user logins).
- **Tool**: ELK Stack (Elasticsearch, Logstash, Kibana) or EFK (Fluentd).

### 3. Tracing (Where did it happen?)
Tracking the journey of a single request through different microservices.
- **Tool**: Jaeger, Zipkin.

---

## 🔑 Crucial Monitoring Concepts
- **Pull vs Push**: Prometheus "pulls" metrics from servers. Cloudwatch "pushes" metrics from AWS.
- **Alerting**: Automatically notifying developers when a metric crosses a critical threshold (e.g., Error rate > 5%).
- **Dashboards**: Visual representations of metrics for quick analysis. (Tool: Grafana).

---

## 🛠️ The ELK/EFK Stack (Simplified)
| Component | Function | Analogy |
| :--- | :--- | :--- |
| **Logstash / Fluentd** | Collect and transform logs. | The "Garbage Truck" collecting files. |
| **Elasticsearch** | Store and index logs for searching. | The "Warehouse" with an index. |
| **Kibana** | Visualize logs in a web UI. | The "Storefront" display. |

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the 'Golden Signals' of Monitoring.**
> *A: 1. Latency (time taken), 2. Traffic (demand), 3. Errors (failure rate), 4. Saturation (how full is your service).*

> [!TIP]
> **Q2: What is 'White-Box Monitoring' vs 'Black-Box Monitoring'?**
> *A: White-Box is monitoring internal application state (e.g., JVM memory). Black-Box is testing external behavior from the outside (e.g., is the website page loading?).*

---

## 📚 Resources
- [Prometheus Documentation](https://prometheus.io/docs/introduction/overview/)
- [Grafana University (Free)](https://grafana.com/tutorials/)
- [The Site Reliability Workbook (Google)](https://sre.google/workbook/monitoring/)
- [Elasticsearch Guide](https://www.elastic.co/guide/index.html)
