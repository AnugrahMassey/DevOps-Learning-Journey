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
