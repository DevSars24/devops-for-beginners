# 05: Kubernetes ConfigMaps & Secrets

In modern software development, you must separate **Configuration** from the **Code**. This allows you to use the same Docker image across Dev, Staging, and Production environments by simply injecting different settings.

---

## 🏗️ ConfigMap: Shared Application Settings

A **ConfigMap** stores non-sensitive configuration data (e.g., API URLs, feature flags, or environment variables).

- **Key-Value Pairs**: Data is stored as standard keys and values.
- **Dynamic Updates**: If you update a ConfigMap, you can configure your app to pick up those changes without a restart (if using the "Volume" method).

### 🌟 Example: A ConfigMap YAML
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-settings
data:
  API_URL: "https://api.myapp.com"
  LOG_LEVEL: "debug"
```

---

## 🏗️ Secret: Sensitive Application Settings

A **Secret** stores confidential data like API keys, passwords, and database credentials.

- **Base64 Encoded**: Secrets are encoded in Base64 (but NOT encrypted by default! Always use encryption-at-rest or a 3rd party vault like HashiCorp Vault).
- **Mountable**: Mounted into pods as environment variables or files in a volume.

### 🌟 Example: A Secret YAML
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: db-credentials
type: Opaque
data:
  DB_PASSWORD: "cGFzc3dvcmQ=" # 'password' in Base64
```

---

## 🚀 Injecting Config into Pods

You can use both ConfigMaps and Secrets in your Deployment:

```yaml
spec:
  containers:
  - name: my-app
    image: my-app:v1.0
    env:
    - name: APP_CONFIG_URL
      valueFrom:
        configMapKeyRef:
          name: app-settings
          key: API_URL
    - name: DATABASE_PW
      valueFrom:
        secretKeyRef:
          name: db-credentials
          key: DB_PASSWORD
```

---

## 🎤 Interview Preparation: Cracking the Configuration

> [!IMPORTANT]
> **Q1: Why should you avoid storing configuration inside the Docker image?**
> *Answer: **Portability**. If your Database IP is hardcoded in the image, you have to build a new image for every environment (Dev, Prod, QA). If you use ConfigMaps, you build **One Image** and inject the correct configuration at runtime, making your CI/CD pipeline much cleaner.*

> [!TIP]
> **Q2: Are Kubernetes Secrets "secure" by default?**
> *Answer: **No!** Kubernetes Secrets are only **Base64 encoded**, which any developer can decode. To make them production-grade, you must enable **Encryption-at-Rest** in the API server or use a more robust secret management tool like **AWS Secrets Manager**, **Azure Key Vault**, or **HashiCorp Vault**.*

---

## 📚 Next Steps
Now that your apps are configured, let's learn how to **Module 06: Scale Your Apps & Manage Resources**.
