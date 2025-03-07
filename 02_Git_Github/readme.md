
---

# **📌 Week 1: Git & GitHub (Day 1-7)**
This week, you will learn **Git**, a version control system, and **GitHub**, a platform for hosting and collaborating on Git repositories.

By the end of this week, you will know how to:
✅ Set up Git and GitHub
✅ Create & manage repositories
✅ Work with branches, merges & pull requests
✅ Use GitHub Actions for automation

---

## **📅 Day 1: Introduction to Git & GitHub**

### **🔹 What is Git?**
Git is a **distributed version control system (VCS)** that helps track changes in source code efficiently.

### **🔹 What is GitHub?**
GitHub is a **cloud-based Git repository hosting service** that enables collaboration, issue tracking, and CI/CD automation.

### **🔹 Setting Up Git**
1. Install Git → [Download Git](https://git-scm.com/downloads)
2. Configure Git:
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```
3. Create a local repo:
   ```bash
   mkdir my-project && cd my-project
   git init
   ```
4. Create and commit a file:
   ```bash
   echo "Hello, Git!" > hello.txt
   git add hello.txt
   git commit -m "Initial commit"
   ```
5. Push to GitHub:
   ```bash
   git remote add origin <repo_url>
   git branch -M main
   git push -u origin main
   ```

---

## **📅 Day 2: Git Workflow & Basic Commands**

### **🔹 Git Workflow**
1. **Working Directory** → Local folder where files are create
2. **Staging Area** → Files added using `git add` before committing
3. **Repository** → Commits stored with version history
4. **Remote Repository** → Hosted on GitHub for collaboration

### **🔹 Basic Git Commands**
| Command | Description |
|---------|------------|
| `git status` | Check the status of the working directory |
| `git add <file>` | Stage a file for commit |
| `git commit -m "message"` | Save changes to the repository |
| `git log` | View commit history |
| `git diff` | View unstaged changes |

---

## **📅 Day 3: Branching & Merging**

### **🔹 What is Branching?**
Branching allows you to create multiple versions of a project for parallel development.

### **🔹 Commands for Branching**
| Command | Description |
|---------|------------|
| `git branch` | List all branches |
| `git branch <branch-name>` | Create a new branch |
| `git checkout <branch-name>` | Switch to a branch |
| `git switch <branch-name>` | Alternative way to switch branches |
| `git merge <branch-name>` | Merge a branch into the current branch |

### **🔹 Example: Create & Merge a Branch**
```bash
git branch feature-1
git checkout feature-1
echo "New feature" > feature.txt
git add feature.txt
git commit -m "Added feature"
git checkout main
git merge feature-1
git branch -d feature-1
```

---

## **📅 Day 4: GitHub Collaboration (Forks, Clones & PRs)**

### **🔹 Forking & Cloning**
- **Fork**: Create a copy of a repository in your GitHub account.
- **Clone**: Download a GitHub repository locally.

```bash
git clone <repo_url>
```

### **🔹 Pull Requests (PRs)**
A Pull Request is a way to contribute changes to a project.

#### **Steps to Create a PR:**
1. Fork the repository
2. Clone it locally
3. Create a new branch and make changes
4. Push the changes to GitHub
5. Open a Pull Request on GitHub

---

## **📅 Day 5: Git Reset, Revert & Rebase**

### **🔹 Undoing Changes in Git**
| Command | Action |
|---------|--------|
| `git reset --soft HEAD~1` | Undo last commit (keep changes staged) |
| `git reset --mixed HEAD~1` | Undo last commit (keep changes unstaged) |
| `git reset --hard HEAD~1` | Undo last commit (delete changes) |
| `git revert <commit-id>` | Create a new commit that undoes a previous commit |
| `git rebase <branch-name>` | Move commits from one branch onto another |

---

## **📅 Day 6: Git Stash, Tags & Hooks**

### **🔹 Git Stash**
Stashing temporarily saves uncommitted changes without committing them.

```bash
git stash
git stash pop   # Apply stashed changes
git stash list  # View stashed changes
```

### **🔹 Git Tags**
Tags mark specific commits (e.g., software releases).

```bash
git tag -a v1.0 -m "Version 1.0"
git push origin v1.0
```

### **🔹 Git Hooks**
Hooks automate tasks like running tests before committing.

```bash
cp pre-commit .git/hooks/
chmod +x .git/hooks/pre-commit
```

---

## **📅 Day 7: GitHub Actions (CI/CD Basics)**

### **🔹 What is GitHub Actions?**
GitHub Actions allows you to automate workflows (e.g., CI/CD pipelines).

### **🔹 Create a CI/CD Workflow**
1. Go to your GitHub repo → **Actions** tab
2. Click **New Workflow**
3. Add a `.github/workflows/main.yml` file in your repo:

```yaml
name: CI Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

4. Commit & push this file → GitHub will trigger a pipeline on every push!

---

# **📌 Week 1 Summary**
✔ Git installation & configuration
✔ Git workflow & basic commands
✔ Branching, merging & pull requests
✔ Undoing changes with reset, revert & rebase
✔ Stashing, tagging & hooks
✔ Introduction to GitHub Actions for CI/CD

---

