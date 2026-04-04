# 🏗️ Module 07: Infrastructure as Code (Terraform)

Terraform allows you to build, change, and version infrastructure safely and efficiently. It uses a declarative language (HCL) to define your desired infrastructure across many providers (AWS, Azure, GCP).

## 🏘️ Core Concepts
### 1. The Declarative Approach
Unlike shell scripts (which say "Create a VPC, then create a Subnet"), Terraform scripts say "I want a VPC with this name and two subnets." Terraform handles how to get there.

### 2. State & Backend
- **Tfstate**: A JSON file that tracks the mapping between your configuration and real-world infrastructure.
- **Backend (Remote)**: Store state in S3 or Azure Blob to allow team collaboration and lock-protection.

### 3. Providers & Modules
- **Providers**: Plugins that talk to external APIs (e.g., `aws`, `google`, `azurerm`).
- **Modules**: Self-contained packages of Terraform configurations. (The "Reusable Components").

---

## 🛠️ The Terraform Workflow
1. `terraform init`: Initialize the working directory, download provider plugins. 
2. `terraform plan`: Preview the changes Terraform will make (Create, Update, Delete).
3. `terraform apply`: Execute the plan and build the infrastructure.
4. `terraform destroy`: Tear down all managed infrastructure.

---

## 🔑 Best Practices for Terraform
- Use **Variables** to avoid hardcoding (e.g., VPC CIDR, Instance Type).
- Use **Outputs** to display essential info (e.g., Public IP of a server).
- **Lock your state**: Use S3 + DynamoDB (or equivalent) for team projects.
- **Isolate Environments**: Use separate state files/folders for Dev, Staging, and Production.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain Terraform State and why it's critical.**
> *A: State is Terraform's "Ground Truth." It maps resources in your code to real resources in the cloud. Without it, Terraform wouldn't know which resources already exist or need updating.*

> [!TIP]
> **Q2: What is 'Configuration Drift'?**
> *A: Drift happens when someone changes the infrastructure manually (outside of Terraform). Running `terraform plan` will detect this and propose changes to bring the infra back to the "Desired State."*

---

## 📚 Resources
- [Terraform Documentation (HashiCorp)](https://developer.hashicorp.com/terraform/docs)
- [Terraform Registry](https://registry.terraform.io/) (Find modules & providers)
- [Learn Terraform (Interactive)](https://developer.hashicorp.com/terraform/tutorials)
- [Vikas Jha's Terraform Cheat Sheet](https://vjha.medium.com/terraform-cheat-sheet-3f41165f1a5f)
