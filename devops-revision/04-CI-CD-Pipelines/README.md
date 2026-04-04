# ⛓️ Module 04: CI/CD Pipelines (Jenkins & More)

Bhai, DevOps ka dil (heartbeat) hai **CI/CD**. Agar ye ruk gaya, toh coding ka koi fayda nahi kyunki code user tak pahunchega hi nahi! 

## 🏗️ The CI/CD Lifecycle (ELI5)
**Analogy**: Socho aap ek auto-parts ki factory chala rahe ho.
- **CI (Continuous Integration)**: Har purza (part) banne ke baad turant machine se test hota hai ki sahi bana ya nahi. Agar galat hai, toh factory turant red light dikhati hai. (Jenkins/GitHub Actions yahi karte hain).
- **CD (Continuous Delivery/Deployment)**: Agar part sahi hai, toh woh conveyor belt se automatically packaging ki taraf badh jata hai. 

### 🌟 Key Terms (Hinglish)
- **CI**: Code ko "Integrate" karke build aur test karna. (Puraani galti early dhoondna).
- **CD (Delivery)**: Code "Ready" hai deploy ke liye, bas manager ko ek button daban hai.
- **CD (Deployment)**: Building se direct Production! Koi human check nahi, sab automated. (Amazon har 1 sec mein aise hi deploy karta hai!).

---

## 🛠️ Jenkins on Ubuntu (Installation Steps)
Agar aap **GCP Compute Engine** ya kisi bhi Ubuntu VM pe Jenkins daalna chahte ho, toh ye commands copy-paste karo:

```bash
# 1. Update system and install Java (Jenkins needs it!)
sudo apt update
sudo apt install openjdk-17-jdk -y

# 2. Add Jenkins GPG Key and Repo
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# 3. Install Jenkins
sudo apt update
sudo apt install jenkins -y

# 4. Start and enable Jenkins service
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
> [!TIP]
> browser mein `http://<YOUR_IP>:8080` pe jao aur admin password `/var/lib/jenkins/secrets/initialAdminPassword` se lo.

---

## 📝 Working with Jenkinsfile (Pipeline as Code)
Modern DevOps mein hum manually button nahi click karte, hum code likhte hain pipeline chalane ke liye.
**Example Script**:
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { echo 'Building Application...' }
        }
        stage('Test') {
            steps { echo 'Running Automated Tests...' }
        }
        stage('Deploy') {
            steps { echo 'Deploying to GKE Cluster...' }
        }
    }
}
```

---

## ❓ Interview Questions (Best Way)
> [!IMPORTANT]
> **Q1: Jenkins Pipeline aur Freestyle project mein kya fark hai?**
> *A: Freestyle puraana tarika hai jahaan UI pe click karna padta tha. Pipeline "Code" ke form mein hota hai (Jenkinsfile), jise aap Git mein save kar sakte ho. Yeh zyada powerful aur scalable hai.*

> [!TIP]
> **Q2: 'Shift-Left' strategy CI/CD mein kaise help karti hai?**
> *A: Iska matlab hai Testing aur Security ko development ke starting mein hi check kar lena (Left side of the timeline). Isse bugs end mein nahi milte, pehle hi resolve ho jate hain.*

---

## 📚 Resources
- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [GitHub Actions: Start Here](https://github.com/features/actions)
- [Swiggy's Build Journey (Engineering Blog)](https://tech.swiggy.com/)
