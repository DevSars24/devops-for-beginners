# 🐙 Module 03: Git & Version Control

In a professional development environment, Git is not just a "save" button; it's a **Time Machine** and a **Collaboration Hub**. It allows a team of engineers to work on the same codebase simultaneously without overwriting each other's work and to revert to previous versions if issues arise.

## 🏗️ Git Fundamentals (ELI5)

Think of Git as the **Life of a Drawing**.
1. **Workspace**: Your actual paper where you are sketching (The local machine).
2. **Staging Area**: You have completed the pencil sketch and are reviewing it (Checking your changes with `git add`).
3. **Local Repo**: You have finalized the sketch and put it into a folder (Committing your changes with `git commit`).
4. **Remote Repo**: You have sent a copy of the drawing to a shared server for your friends to see (Pushing to GitHub/GitLab).

### 🔑 Git Workflow in Professional Environments
- **Feature Branches**: Every new feature or bug fix should have its own branch (`git checkout -b feature/login-page`).
- **Merge Requests/PRs**: Code should be reviewed by another engineer before it is allowed into the `main` branch.
- **Labels & Tags**: Important releases should be marked with tags (e.g., `v1.0.0`) to make it easily accessible in the future.

---

## 🛠️ Advanced Commands (Becoming a Pro!)
- `git status`: Check the current state of your workspace.
- `git log --oneline --graph`: Highly recommended for visualizing the history of commits in a clean, graphical format.
- `git stash`: Temporarily "shelve" uncommitted changes (e.g., half-finished work) to switch contexts and address an urgent bug fix.
- `git cherry-pick`: Allows you to apply a specific commit from one branch to another without merging the entire branch (e.g., backporting a fix).

---

## ❓ Interview Preparation (Mastering the Discussion)

> [!IMPORTANT]
> **Q1: What is the difference between Merge and Rebase?**
> *Answer: **Merge** creates a new "Merge Commit" and combines the histories of two branches. **Rebase** rewinds the current branch to its base and reapplies each commit on top of the target branch. Rebase results in a cleaner, linear history, but it should be avoided on public/shared branches.*

> [!TIP]
> **Q2: How do you resolve a Merge Conflict?**
> *Answer: A conflict occurs when two different changes affect the same line of code. Git stops and asks for human intervention. You manually open the file, decide which version (or a combination of both) to keep, and then continue the merge process.*

---

## 📚 Resources
- [Learn Git Branching (Game)](https://learngitbranching.js.org/) — The best way to visualize Git flows.
- [Git Flight Rules](https://github.com/k88hudson/git-flight-rules) — A guide on how to fix common Git mistakes.
- [GitHub Skills](https://skills.github.com/) — Official interactive tutorials.
