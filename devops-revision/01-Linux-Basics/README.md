# 🐧 Module 01: Linux Basics for DevOps

In the world of DevOps, Linux is the foundational environment where almost every modern tool—including Docker, Kubernetes, and Jenkins—resides. Mastering the Linux command line is the first step toward becoming a proficient DevOps engineer.

## 🚀 Core Pillars of Linux

Think of Linux as **The Language of Servers**. To manage infrastructure effectively, you must speak this language fluently.

### 1. File System Hierarchy (The System Layout)
Understanding where files live is critical for troubleshooting:
- `/etc`: Contains system-wide **configuration files** (the "settings" of your server).
- `/var/log`: Stores **system logs**. This is the first place to look (CCTV for your server) when something goes wrong.
- `/home`: The directory for **personal files** of non-root users.
- `/root`: The home directory for the **Superuser** (Administrator).
- `/bin`: Essential **binary tools** (executables like `ls`, `cp`, and `grep`).

### 2. Essential Commands (The Engineer's Toolbox)
- **Log Analysis**: `grep -ri "error" /var/log/` (Search recursively for "error" in all logs). SREs use this to identify issues in real-time.
- **Process Management**: `top` or `htop`. If a service (e.g., a web API) hangs, use these to find the Process ID (PID) and terminate it with `kill -9 <PID>`.
- **Networking**: `netstat -tulnp`. Check which ports are "listening" for connections (vital for security audits).

### 3. Permissions & Ownership (Who has the keys?)
- **chmod**: Modify file permissions. (Read = 4, Write = 2, Execute = 1).
- **chown**: Change file or directory ownership.

> [!IMPORTANT]
> **Real-World Case**: If you don't grant a CI/CD tool (like Jenkins) execution permissions (`chmod +x script.sh`), your deployment pipeline will fail.

---

## 🛠️ Hands-on Practice
1. **Analyze Logs**: View the last 50 entries in your system log using `tail -n 50 /var/log/syslog`.
2. **Bash Scripting**: Create a `.sh` file that automates a simple task, such as creating a timestamped backup directory.

---

## ❓ Interview Preparation (Mastering the Discussion)

> [!IMPORTANT]
> **Q1: What is "Swapping" in Linux?**
> *Answer: Swapping occurs when the physical memory (RAM) is full. The system moves inactive pages from RAM to a designated area on the hard disk (Swap space). While it prevents crashes, heavy swapping can significantly slow down system performance.*

> [!TIP]
> **Q2: What does "Load Average" represent?**
> *Answer: Load Average represents the average system load over a period of time (1, 5, and 15 minutes). On a single-core CPU, a load of 1.0 means the CPU is at 100% capacity. Monitoring this helps identify resource bottlenecks.*

---

## 📚 Resources
- [Linux Command Line Cheat Sheet](https://linuxconfig.org/linux-commands-cheat-sheet)
- [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) — A gamified way to learn Linux.
