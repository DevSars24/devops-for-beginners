# 🐧 Module 01: Linux Basics for DevOps

Linux is the absolute backbone of DevOps. Whether you're configuring a server, building a Docker image, or managing a Kubernetes node, you are interacting with Linux.

## 🚀 Core Pillars of Linux
### 1. File System Hierarchy
- `/etc`: Configuration files (e.g., `nginx.conf`, `hosts`).
- `/var/log`: System and application logs.
- `/home`: User directories.
- `/root`: Home directory for the superuser.
- `/bin` & `/sbin`: Executable binaries.

### 2. Essential CLI Cheat Sheet
- **Navigation**: `pwd`, `ls -lah`, `cd -` (go back to previous dir).
- **File Manipulation**: `touch`, `mkdir -p` (create nested dirs), `cp -r`, `mv`, `rm -rf`.
- **Content Viewing**: `cat`, `less`, `head`, `tail -f` (follow logs in real-time).
- **Search**: `find / -name "config.yaml"`, `grep -ri "error" /var/log/`.

### 3. Permissions & Ownership (`chmod`, `chown`)
- **Reading Permissions**: `rwx r-x r--` (754)
- **Changing Permissions**: `chmod 755 script.sh`
- **Changing Ownership**: `sudo chown root:root file.txt`

### 4. Process & Resource Management
- **Monitor**: `top`, `htop` (interactive monitor), `ps aux`.
- **Control**: `kill -9 <PID>`, `nice`, `renice`.
- **Systemd**: `systemctl start/stop/status/restart/enable nginx`.

---

## 🛠️ Hands-on Exercises
1. **Automation**: Write a script that checks if `nginx` is running; if not, restart it and log the event.
2. **Analysis**: Use `awk` to print only the second column of a CSV file.
3. **Networking**: Check which ports are listening using `netstat -tulnp` or `ss -lntp`.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: What is the difference between a Process and a Thread?**
> *A: A process is an independent program execution with its own memory space. A thread is a subset of a process that shares the same memory space, making it lighter and faster to create.*

> [!TIP]
> **Q2: How do you find and delete files older than 30 days?**
> *A: `find /path/to/files -type f -mtime +30 -delete`*

---

## 📚 Resources
- [Linux Journey](https://linuxjourney.com/)
- [The Linux Command Line (PDF)](https://linuxcommand.org/tlcl.php)
- [Explainshell.com](https://explainshell.com/) (Great for deconstructing complex commands)
