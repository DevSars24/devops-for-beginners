# ⛓️ Module 04: CI/CD Pipelines (Jenkins & More)

In modern software development, **CI/CD** is the heartbeat of the lifecycle. Without a robust pipeline, code remains stagnant on developers' machines. A well-designed pipeline ensures that every code change is automatically tested, built, and delivered to the end-user with minimal manual intervention.

## 🏗️ The CI/CD Lifecycle (ELI5)

Think of it as an **Automated Car Factory**.
- **CI (Continuous Integration)**: Every small part (like a door or a mirror) is immediately tested by a machine as soon as it's made. If the part is flawed, a red light flashes, and it's fixed immediately.
- **CD (Continuous Delivery/Deployment)**: If the part passes the test, it's automatically moved along a conveyor belt to the assembly line. In **Delivery**, a human presses a final button to ship the car. In **Deployment**, the car is automatically sent to the dealership without any human intervention.

### 🌟 Key Concepts and Abbreviations
- **CI**: The practice of automating the integration of code changes from multiple contributors into a single software project.
- **CD (Delivery)**: Code is always in a "ready-to-deploy" state. A manual trigger is needed for the final production push.
- **CD (Deployment)**: Every change that passes the automated tests is deployed to production automatically. (Industry leaders like Amazon and Netflix deploy thousands of times per day!).

---

## 🛠️ Jenkins on Ubuntu (Installation Guide)

Follow these steps to set up Jenkins on an Ubuntu Linux system (e.g., a GCP Compute Engine instance):

```bash
# 1. Update the system and install the Java Runtime Environment (Jenkins is a Java application)
sudo apt update
sudo apt install openjdk-17-jdk -y

# 2. Add the Jenkins GPG Key and Software Repository
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# 3. Install Jenkins
sudo apt update
sudo apt install jenkins -y

# 4. Start and enable the Jenkins service
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
> [!TIP]
> Access Jenkins in your browser at `http://<YOUR_IP>:8080`. You will need the initial admin password located at: `/var/lib/jenkins/secrets/initialAdminPassword`.

---

## 📝 Working with Pipelines (Pipeline as Code)

In modern DevOps, we avoid manual configurations in the UI. Instead, we use a **Jenkinsfile** to define our pipeline stages in code.

**Example Jenkinsfile (Declarative Pipeline)**:
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { echo 'Building the application source...' }
        }
        stage('Test') {
            steps { echo 'Running automated unit and integration tests...' }
        }
        stage('Deploy') {
            steps { echo 'Deploying to the Kubernetes cluster (GKE/EKS)...' }
        }
    }
}
```

---

## ❓ Interview Preparation (Mastering the Discussion)

> [!IMPORTANT]
> **Q1: What is the difference between a Jenkins Pipeline and a Freestyle Project?**
> *Answer: A **Freestyle project** is the legacy method where configuration is done through the Jenkins UI. A **Pipeline** is defined as code (using a Jenkinsfile), allowing it to be version-controlled, easily shared, and scaled for complex workflows.*

> [!TIP]
> **Q2: What is the "Shift-Left" strategy in CI/CD?**
> *Answer: "Shifting-Left" means moving testing and security checks earlier in the development lifecycle (further "left" on the project timeline). This allows developers to catch and resolve bugs before they reach the expensive stages of staging or production.*

---

## 📚 Resources
- [Jenkins Documentation](https://www.jenkins.io/doc/) — The official guide.
- [GitHub Actions: Quickstart](https://docs.github.com/en/actions/quickstart) — Modern cloud-native CI/CD.
- [The Phoenix Project](https://www.google.com/search?q=The+Phoenix+Project+book) — A must-read novel about DevOps principles.
