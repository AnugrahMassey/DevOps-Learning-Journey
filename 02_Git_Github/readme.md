
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

