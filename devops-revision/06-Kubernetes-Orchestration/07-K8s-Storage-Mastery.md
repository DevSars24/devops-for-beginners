# 07: Kubernetes Storage Mastery (PV & PVC)

In Kubernetes, Pods are **ephemeral** (short-lived). If a Pod with a database restarts, its internal data is wiped. To provide **Persistent Storage**, Kubernetes uses a three-layer abstraction: **PersistentVolumes (PV)**, **PersistentVolumeClaims (PVC)**, and **StorageClasses (SC)**.

---

## 🏗️ The Three Pillars of Storage

| Storage Object | Purpose | Analogy |
| :--- | :--- | :--- |
| **PersistentVolume (PV)** | The actual physical storage (e.g., a disk on a GCP VM, or an Amazon EBS volume). | A **Fixed Plot of Land** in a city. |
| **PersistentVolumeClaim (PVC)** | A request for storage by a user. (e.g., "I need 10GB of storage"). | A **Developer's License** to use a piece of land. |
| **StorageClass (SC)** | A template for creating PVs automatically (Dynamic Provisioning). | The **City Zoning Ordinance** (e.g., "all new buildings must be office spaces"). |

---

## 🚀 Dynamic Storage Provisioning

In modern cloud environments (GKE, AKS, EKS), you don't manually create a PV for every application. You create a **StorageClass**, and when you create a **PVC**, Kubernetes will automatically create the PV for you at the same time.

### 🌟 Example: A PersistentVolumeClaim (PVC)
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: db-storage-pvc
spec:
  accessModes:
    - ReadWriteOnce # One node can mount it at a time
  resources:
    requests:
      storage: 10Gi # Requesting 10GB of disk space
  storageClassName: standard # Use a predefined StorageClass
```

---

## 🏗️ Mounting Storage to a Pod

Once you have a PVC, you can mount it to your application to ensure your data stays safe:

```yaml
spec:
  containers:
  - name: postgres-db
    image: postgres:15-alpine
    volumeMounts:
    - name: data-disk
      mountPath: /var/lib/postgresql/data # The app saves data HERE
  volumes:
  - name: data-disk
    persistentVolumeClaim:
      claimName: db-storage-pvc # Maps the PVC to this volume
```

---

## 🎤 Interview Preparation: Cracking the Storage

> [!IMPORTANT]
> **Q1: What is the difference between `ReadWriteOnce`, `ReadWriteMany`, and `ReadOnlyMany`?**
> *Answer: **ReadWriteOnce (RWO)** allows the volume to be mounted by ONE node at a time (standard for block storage like EBS). **ReadWriteMany (RWX)** allows the volume to be shared by MANY nodes simultaneously (ideal for shared file systems like NFS or Amazon EFS). **ReadOnlyMany (ROX)** allows many nodes to read the data, but none to write.*

> [!TIP]
> **Q2: Why use PVCs instead of direct volumes?**
> *Answer: **Abstraction and Portability**. A developer should only have to say "I need 10GB of fast storage." They shouldn't have to worry about whether that storage is coming from an AWS EBS volume, a local SSD, or a Google Cloud Persistent Disk. The administrator handles the PV and StorageClasses behind the scenes.*

---

## 📚 Next Steps
Congratulations! You have mastered the core pillars of Kubernetes. Now, let's learn how to apply these concepts in **Module 09: Cloud Managed Kubernetes (GKE, AKS, EKS)**.
