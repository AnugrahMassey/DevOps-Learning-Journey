# **📌 Week 12: Cloud Computing Basics (Day 61-65)**  
This week, you'll dive into **Cloud Computing** and its fundamentals, specifically focusing on **AWS, Azure, and GCP**. You'll explore how to provision and manage cloud resources, understand cloud service models, and set up basic cloud infrastructure.  

By the end of this week, you’ll understand:  
✅ **What Cloud Computing is and why it's important**  
✅ **The differences between IaaS, PaaS, and SaaS**  
✅ **How to create and manage cloud resources on AWS, Azure, and GCP**  
✅ **Cloud networking concepts like VPC, Subnets, and Security Groups**  

---

# **🗓️ Day 61: Introduction to Cloud Computing**  

### **🔹 What is Cloud Computing?**  
Cloud computing refers to the **on-demand availability of computing resources** (servers, storage, databases, networking, software, etc.) over the internet, eliminating the need for local hardware.

### **🔹 Characteristics of Cloud Computing**  
✅ **On-Demand Self-Service** – Users can provision resources as needed.  
✅ **Broad Network Access** – Services are accessible over the internet.  
✅ **Resource Pooling** – Providers share resources among multiple users.  
✅ **Rapid Elasticity** – Resources can scale up/down automatically.  
✅ **Measured Service** – Pay only for what you use.

### **🔹 Cloud Computing Service Models**  
| **Model** | **Description** | **Examples** |
|-----------|---------------|--------------|
| **IaaS (Infrastructure as a Service)** | Provides virtualized computing resources like VMs, storage, networking | AWS EC2, Google Compute Engine, Azure VMs |
| **PaaS (Platform as a Service)** | Provides a development platform with tools to build applications | AWS Elastic Beanstalk, Google App Engine, Azure App Services |
| **SaaS (Software as a Service)** | Delivers software over the internet, managed by the provider | Gmail, Dropbox, Microsoft 365 |

### **🔹 Deployment Models of Cloud Computing**  
| **Deployment Model** | **Description** |
|----------------------|---------------|
| **Public Cloud** | Resources are shared among multiple users (AWS, Azure, GCP) |
| **Private Cloud** | Dedicated cloud infrastructure for a single organization |
| **Hybrid Cloud** | A combination of public and private clouds |

### **🔹 Why Use Cloud Computing?**  
✅ **Cost-effective** – No need for expensive hardware.  
✅ **Scalability** – Easily increase/decrease resources.  
✅ **Security & Reliability** – Managed security and redundancy.  

---

# **🗓️ Day 62: Introduction to AWS and Core Services**  

### **🔹 What is AWS?**  
Amazon Web Services (AWS) is **one of the leading cloud platforms** offering over 200+ services, including computing, storage, networking, databases, and AI.

### **🔹 Key AWS Services**  

| **Category** | **Service** | **Purpose** |
|-------------|------------|-------------|
| **Compute** | EC2 (Elastic Compute Cloud) | Virtual machines for running applications |
| **Storage** | S3 (Simple Storage Service) | Scalable object storage for files |
| **Networking** | VPC (Virtual Private Cloud) | Isolated cloud network for AWS resources |
| **Database** | RDS (Relational Database Service) | Managed relational database service |
| **IAM & Security** | IAM (Identity and Access Management) | User authentication and access control |

### **🔹 Creating an AWS EC2 Instance**  

1️⃣ **Log in to AWS Console → EC2 Dashboard**  
2️⃣ Click **Launch Instance**  
3️⃣ Choose an **Amazon Machine Image (AMI)** (e.g., Ubuntu 22.04)  
4️⃣ Select an **Instance Type** (e.g., t2.micro – Free Tier)  
5️⃣ Configure networking (assign a Security Group)  
6️⃣ Add **storage** (default: 8GB SSD)  
7️⃣ **Launch and connect via SSH**:  
```bash
ssh -i my-key.pem ubuntu@<public-ip>
```

### **🔹 Configuring IAM for Security**  
1️⃣ Go to **IAM → Users → Create User**  
2️⃣ Assign **permissions** (AdministratorAccess for full access)  
3️⃣ Generate **Access Key & Secret**  
4️⃣ Use AWS CLI to log in:  
```bash
aws configure
```

---

# **🗓️ Day 63: Introduction to Azure and Core Services**  

