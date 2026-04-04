# 🏠 Module 08: Configuration Management (Ansible)

While Terraform builds the house (Servers, VPCs), Ansible decorates the interior (installs software, configures apps). It's an "Agentless" tool that connects via SSH to manage your infrastructure.

## 🏘️ Ansible Core Components
### 1. The Inventory
A simple file Listing the IP addresses or hostnames of the servers you want to manage.

### 2. Playbooks (YAML files)
Describe the "Desired State" for your servers (e.g., "Install Apache, copy this config, start service").

### 3. Roles
The highest level of abstraction. Group playbooks, variables, and templates into reusable components.

### 4. Modules
Reusable scripts that do the actual work (e.g., `apt`, `yum`, `copy`, `service`, `git`).

---

## 🔑 Crucial Features
- **Idempotency**: Running a playbook twice results in no changes if the server is already in the desired state. (The "Golden Rule").
- **Agentless**: No need to install software on the destination servers; Ansible just uses SSH.
- **Variables & Templates**: Use Jinja2 to create dynamic configuration files.

---

## 🛠️ Essential Ansible Commands
- `ansible all -m ping`: Simple connectivity check.
- `ansible-playbook -i inventory.ini site.yml`: Run a playbook.
- `ansible-galaxy install role_name`: Install roles from the community (Galaxy).
- `ansible-vault encrypt file.yml`: Encrypt sensitive files (like passwords).

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain 'Idempotency' in Ansible.**
> *A: It means an operation can be applied multiple times without changing the result beyond the initial application. If a service is already running, Ansible won't restart it unless told to do so.*

> [!TIP]
> **Q2: What is the difference between Ansible Ad-hoc commands and Playbooks?**
> *A: Ad-hoc commands are one-off tasks (e.g., rebooting a server). Playbooks are structured YAML files for repeatable, complex automation.*

---

## 📚 Resources
- [Ansible Documentation](https://docs.ansible.com/)
- [Ansible Galaxy (Community Roles)](https://galaxy.ansible.com/)
- [Jeff Geerling's Ansible for DevOps](https://www.ansiblefordevops.com/) (The Bible of Ansible)
