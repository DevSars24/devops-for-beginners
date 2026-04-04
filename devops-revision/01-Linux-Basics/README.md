# 🐧 Module 01: Linux Basics for DevOps (Hinglish Edition)

Bhai, DevOps mein Linux nahi aata toh kuch nahi aata. Yeh "Home" hai humara, jahaan sab tools (Docker, K8s, Jenkins) chalte hain.

## 🚀 Core Pillars of Linux (ELI5)
Think of Linux as **The Language of Servers**. Agar aap server se baat karna chahte ho, toh aapko Linux aana chahiye.

### 1. File System Hierarchy (Ghar ka Layout)
- `/etc`: Configuration files (Yaani ghar ki settings).
- `/var/log`: System logs (Ghar ki CCTV recording, sab record hota hai error kahan hai).
- `/home`: Normal users ka kamra.
- `/root`: Superuser (Owner) ka secret locker.
- `/bin`: Zaroori tools (Chaku, hathoda, etc).

### 2. Essential Commands (Paisa Vasool Tools)
- **Search**: `grep -ri "error" /var/log/` (Poore log mein Error dhoondo). Netflix ke engineers ise real-time logs dekhne ke liye use karte hain.
- **Process Management**: `top` or `htop`. Agar koi app (Jaise Swiggy service) hang ho jaye, toh ID nikaalo aur `kill -9` kar do! 
- **Networking**: `netstat -tulnp`. Check karo kaun sa port (darwaza) open hai. 

### 3. Permissions & Ownership (Chabhi Kiske Paas Hai?)
- **chmod**: Permissions change karna. (Read = 4, Write = 2, Execute = 1).
- **chown**: Owner change karna. 
> [!IMPORTANT]
> **Real-World Case**: Agar aapne Jenkins ko script chalane ka permission nahi diya (`chmod +x`), toh pipeline fail ho jayegi!

---

## 🛠️ Hands-on Concepts to Practice
1. **Log Analysis**: Check karo `/var/log/syslog` mein last 50 lines kya hain using `tail -n 50`.
2. **Scripting**: Ek `.sh` file banao jo automatically folder create kare (Jaise logs backup ke liye).

---

## ❓ Interview Questions (Aise Jawab Do!)
> [!IMPORTANT]
> **Q1: Swapping kya hoti hai Linux mein?**
> *A: Simple! Jab RAM (Main memory) full ho jati hai, toh Linux Hard Disk ka ek portion use karne lagta hai data store karne ke liye. Ise Swapping kehte hain. Par dhyaan rahe, swapping system ko slow kar sakti hai!*

> [!TIP]
> **Q2: Load Average kya hota hai?**
> *A: Load Average dikhata hai ki CPU kitna busy hai. Agar load average 1.0 hai single core CPU pe, matlab CPU 100% busy hai. Agar load average zyada badh jaye, toh system "hang" hone lagta hai.*

---

## 📚 Resources
- [Linux Command Line Cheat Sheet](https://linuxconfig.org/linux-commands-cheat-sheet)
- [OverTheWire Bandit (Game to learn Linux)](https://overthewire.org/wargames/bandit/)
