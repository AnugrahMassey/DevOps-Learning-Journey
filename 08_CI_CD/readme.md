# **📌 Week 9: CI/CD Basics**  
This week, you will learn how to **automate software builds, testing, and deployments** using **Jenkins, GitHub Actions, and GitLab CI/CD**. These tools help ensure **reliable and repeatable software delivery**.

By the end of this week, you’ll understand:
✅ **What CI/CD is and why it’s important**  
✅ **Setting up Jenkins for CI/CD pipelines**  
✅ **Using GitHub Actions for automation**  
✅ **Using GitLab CI/CD for DevOps workflows**  
✅ **Building and deploying applications automatically**  

---

## **🗓️ Day 46: Introduction to CI/CD and Jenkins Setup**  

### **🔹 What is CI/CD?**
**Continuous Integration (CI)** → Developers frequently merge code into a shared repository, triggering **automated builds and tests**.  
**Continuous Deployment (CD)** → After testing, code is automatically deployed to production **without manual intervention**.  

### **🔹 Why CI/CD?**
✅ **Automates builds & testing**  
✅ **Reduces errors & improves code quality**  
✅ **Accelerates software releases**  

### **🔹 Setting Up Jenkins**
Jenkins is an open-source **automation server** used to build CI/CD pipelines.

#### **Installing Jenkins (Ubuntu)**
```bash
sudo apt update
sudo apt install openjdk-11-jdk -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
echo "deb http://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list
sudo apt update
sudo apt install jenkins -y
```
#### **Starting Jenkins**
```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
```
#### **Accessing Jenkins**
Visit:
```
http://localhost:8080
```
Retrieve Admin Password:
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
Follow the setup wizard to configure Jenkins.

---

## **🗓️ Day 47: Creating a CI/CD Pipeline with Jenkins**  

### **🔹 What is a Jenkins Pipeline?**
A **Jenkins Pipeline** is a script-based process defining how code moves from **development to production**.

### **🔹 Creating a Simple CI Pipeline**
1️⃣ Open Jenkins → **New Item** → Select **Pipeline**  
2️⃣ Define pipeline steps in a **Jenkinsfile**  

**Example Jenkinsfile (Build + Test)**  
```groovy
pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/your-username/sample-project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'make build'  # Replace with build command
            }
        }
        stage('Test') {
            steps {
                sh 'make test'  # Replace with test command
            }
        }
    }
}
```
3️⃣ Run the pipeline to see automated **build & testing**.

---

## **🗓️ Day 48: GitHub Actions - Automating Workflows**  

### **🔹 What are GitHub Actions?**
**GitHub Actions** allow you to define **CI/CD workflows** directly inside a GitHub repository.  

### **🔹 Creating a GitHub Actions Workflow**
1️⃣ In your GitHub repository, create:
```
.github/workflows/ci.yml
```
2️⃣ Define a CI/CD pipeline in **ci.yml**:

```yaml
name: CI Pipeline
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 16
      - name: Install dependencies
        run: npm install
      - name: Run Tests
        run: npm test
```
✅ This runs on **every code push**  
✅ Automatically **builds & tests the app**  

3️⃣ **Commit & Push** → GitHub will run the action automatically.

---

## **🗓️ Day 49: GitLab CI/CD - Automating Pipelines**  
