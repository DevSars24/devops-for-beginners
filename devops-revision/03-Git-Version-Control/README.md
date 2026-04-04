# 🐙 Module 03: Git & Version Control

Git is more than just "saving code." In DevOps, it's about collaboration, history, and automated triggers for pipelines.

## 🏗️ Git Fundamentals
- **Workspace**: Your local machine.
- **Staging Area**: Files you're preparing to commit.
- **Local Repository**: Committed changes on your machine.
- **Remote Repository**: Shared repository (GitHub, GitLab, Bitbucket).

---

## 🔑 Best Practices for DevOps
| Practice | Description |
| :--- | :--- |
| **Atomic Commits** | Each commit should represent one logical change. |
| **Descriptive Messages** | Explain "Why" you made the change, not just "What." |
| **Branching Strategy** | Use GitFlow, Trunk-Based Development, or Feature Branching. |
| **Pull Requests** | Use for code review and automated CI checks. |

---

## 🛠️ Advanced Git Commands
- `git status` / `git log --oneline --graph`: Check history.
- `git diff`: Compare changes between working directory and staging.
- `git checkout -b <branch>`: Create and switch to a new branch.
- `git stash`: Save uncommitted changes for later.
- `git rebase main`: Update your feature branch with the latest from main.
- `git cherry-pick <commit-hash>`: Apply a specific commit to your current branch.
- `git revert <commit-hash>`: Create a new commit that undoes a previous one.

---

## ❓ Interview Questions
> [!IMPORTANT]
> **Q1: Explain Merge vs Rebase.**
> *A: `git merge` creates a new "merge commit" that combines histories. `git rebase` re-writes history by placing your changes on top of the target branch's latest commit, resulting in a cleaner linear history.*

> [!TIP]
> **Q2: How do you fix a commit message after you've pushed?**
> *A: Use `git commit --amend` to change the message locally, then `git push --force` to update the remote. (Caution: only do this on your private branch!)*

---

## 📚 Resources
- [Git Documentation](https://git-scm.com/doc)
- [Pro Git (Book)](https://git-scm.com/book/en/v2)
- [Learn Git Branching (Interactive)](https://learngitbranching.js.org/)
- [Atlassian Git Tutorials](https://www.atlassian.com/git)
