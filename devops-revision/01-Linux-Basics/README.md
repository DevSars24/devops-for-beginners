# 🐧 Module 01: Linux Basics for DevOps

Linux is the backbone of almost all DevOps tools, from Docker to Kubernetes. mastering the terminal is your first step.

## 🔑 Key Concepts to Revise

- [ ] **File Permissions**: `chmod`, `chown`, `umask`.
- [ ] **Package Management**: `apt`, `yum`, `dnf`.
- [ ] **Process Management**: `ps`, `top`, `htop`, `kill`, `bg`, `fg`.
- [ ] **Networking**: `ifconfig`, `ip addr`, `netstat`, `nslookup`, `curl`, `wget`.
- [ ] **File Operations**: `ls`, `cd`, `mkdir`, `rm`, `cp`, `mv`, `find`, `grep`, `awk`, `sed`.
- [ ] **SSH & Key Management**: `ssh-keygen`, `ssh-copy-id`, `.ssh/config`.

---

## 🛠️ Hands-on Exercises

1. **Exercise 1**: Create a shell script to automate user creation and directory structure setup.
2. **Exercise 2**: Use `grep` and `awk` to extract specific IP addresses from a large log file.
3. **Exercise 3**: Set up password-less SSH between two Linux instances (or VMs).

---

## ❓ Interview Questions

> [!IMPORTANT]
> **Q1: Explain the difference between Hard Links and Soft Links.**
> *A: Soft links (symbolic) point to the filename, while hard links point to the inode (actual data). If the original file is deleted, a soft link breaks, but a hard link remains valid.*

> [!TIP]
> **Q2: How do you check if a port is open on a remote server?**
> *A: Use `nc -vz <ip> <port>` or `telnet <ip> <port>`.*

---

## 📚 Resources

| Resource | Link |
| :--- | :--- |
| Linux Journey | [https://linuxjourney.com/](https://linuxjourney.com/) |
| OverTheWire (Wargames) | [https://overthewire.org/wargames/](https://overthewire.org/wargames/) |
| Linux Survival | [https://linuxsurvival.com/](https://linuxsurvival.com/) |

---

*Keep iterating and practicing commands!*
