# 🐙 Module 03: Git & Version Control (Hinglish Edition)

Bhai, Git sirf "save" button nahi hai. Yeh ek **Time Machine** hai jo aapko purane version pe le ja sakti hai agar code fat jaye.

## 🏗️ Git Fundamentals (ELI5)
**Analogy**: Socho aap ek Drawing bana rahe ho. 
1. **Workspace**: Aapka paper (Jahaan aap drawing kar rahe ho).
2. **Staging Area**: Aapne pencil se drawing kar li, ab aap check kar rahe ho ki sahi bani ya nahi (In commits ko hum "Add" karte hain).
3. **Local Repo**: Aapne drawing final karke dabba mein rakh di (Commit).
4. **Remote Repo**: Aapne drawing apne dost ko dikhane ke liye server base pe bhej di (Push).

### 🔑 Git Flow in Real-World (Best Way)
- **Feature Branch**: Har new feature ke liye naya branch banao. (`git checkout -b feature/login`).
- **Merge Requests/PRs**: Code bina review ke merge nahi hota (Amazon/Facebook mein to mandatory hai!).
- **Labels & Tags**: `v1.0`, `v2.0` - Release ko mark karna zaroori hai.

---

## 🛠️ Advanced Commands (Pro Bano!)
- `git status`: Check karo kaam kahan tak pahuncha.
- `git log --oneline --graph`: History ko sundar tarike se dekho.
- `git stash`: Agar aapka ek kaam adhoora hai aur aapko doosre urgent bug pe kaam karna hai, toh code ko side mein rakh do `git stash` se! 
- `git cherry-pick`: Socho aapne feature-A mein ek bahut achha bug fix kiya. Ab aapko wahi fix feature-B mein chahiye bina merge kiye - toh bas commit ID uthao aur `cherry-pick` kar lo.

---

## ❓ Interview Questions (Aise Jawab Do!)
> [!IMPORTANT]
> **Q1: Merge aur Rebase mein kya antar hai?**
> *A: Merge ek naya "Merge Commit" banata hai aur upar history combine karta hai. Rebase purane commits ko doosre branch ke starting point ke baad move kar deta hai. Rebase se history linear aur saaf (clean) rehti hai.*

> [!TIP]
> **Q2: Conflict kaise resolve karte hain?**
> *A: Jab do log ek hi line ko modify kar dete hain, toh Git confused ho jata hai. Humein manually code file khol ke chuna hota hai ki kaunsa version rakhna hai (`Accept Incoming` or `Accept Current`).*

---

## 📚 Resources
- [Learn Git Branching (Game)](https://learngitbranching.js.org/)
- [Git Flight Rules (Solutions to common problems)](https://github.com/k88hudson/git-flight-rules)
