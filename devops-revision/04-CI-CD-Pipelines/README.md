# ⛓️ Module 04: CI/CD Pipelines

CI/CD is the heartbeat of DevOps. It automates testing, building, and deploying code, ensuring fast delivery and high quality.

## 🏗️ The CI/CD Lifecycle
### 1. Continuous Integration (CI)
- Developers merge code frequently to the main branch.
- Automated builds and tests run on every merge.
- Goal: Find bugs early and ensure the codebase is always functional.

### 2. Continuous Delivery (CD)
- Once code passes CI, it is automatically prepared for release.
- Deployment to staging/production is still manual (click of a button).

### 3. Continuous Deployment (CD)
- Every change that passes automated tests is automatically deployed to production.
- No human intervention required.

---

## 🔑 Popular CI/CD Tools
- `Jenkins`: The classic open-source automation server.
- `GitHub Actions`: Integration built-in to GitHub (YAML-based).
- `GitLab CI`: Top-to-bottom integrated DevOps platform.
- `CircleCI`: Fast, cloud-native CI/CD for teams.
- `AWS CodePipeline`: Automated release pipelines in AWS.

---

## 🛠️ Pipeline Stages (Best Practices)
- **Source**: Fetch code from Git.
- **Build**: Compile code, install dependencies (e.g., `npm install`).
- **Test**: Run Unit, Integration, and Security tests (e.g., `npm test`).
- **Deploy**: Build a container image and push to an environment.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain the difference between Continuous Delivery and Continuous Deployment.**
> *A: In Continuous Delivery, the code is always ready for production, but the release is manual. In Continuous Deployment, every successful commit is automatically deployed to users in production.*

> [!TIP]
> **Q2: What is 'Shift-Left' in the context of CI/CD?**
> *A: It means moving critical tasks (like security testing and performance monitoring) earlier in the development lifecycle (to the left) to catch issues before they reach production.*

---

## 📚 Resources
- [Martin Fowler's Continuous Integration Guide](https://martinfowler.com/articles/continuousIntegration.html)
- [Harness.io (DevOps & CI/CD)](https://harness.io/blog/continuous-integration-cicd)
- [Introduction to GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)
