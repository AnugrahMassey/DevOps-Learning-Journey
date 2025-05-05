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


### **🔹 What is Microsoft Azure?**  
Azure is **Microsoft’s cloud platform**, providing a vast range of services for computing, networking, AI, and storage.

### **🔹 Key Azure Services**  

| **Category** | **Service** | **Purpose** |
|-------------|------------|-------------|
| **Compute** | Azure Virtual Machines (VMs) | Virtualized compute resources |
| **Storage** | Azure Blob Storage | Scalable object storage |
| **Networking** | Azure Virtual Network (VNet) | Secure networking for Azure resources |
| **Database** | Azure SQL Database | Managed relational database service |
| **Security** | Azure Active Directory | Identity and access management |

### **🔹 Creating an Azure VM**  
1️⃣ Log in to **Azure Portal → Virtual Machines → Create**  
2️⃣ Choose an **OS** (e.g., Ubuntu 22.04)  
3️⃣ Select a **VM size** (e.g., Standard_B1s)  
4️⃣ Configure **networking and firewall rules**  
5️⃣ Generate **SSH keys** and connect to VM:  
```bash
ssh -i my-azure-key.pem azureuser@<public-ip>
```

---

# **🗓️ Day 64: Introduction to Google Cloud Platform (GCP)**  

### **🔹 What is GCP?**  
Google Cloud Platform (GCP) offers **cloud computing services** for **AI, networking, compute, and storage**.

### **🔹 Key GCP Services**  

| **Category** | **Service** | **Purpose** |
|-------------|------------|-------------|
| **Compute** | Compute Engine | Virtual machines |
| **Storage** | Cloud Storage | Object storage |
| **Networking** | VPC (Virtual Private Cloud) | Network management |
| **Database** | Cloud SQL | Managed database service |
| **Security** | IAM (Identity and Access Management) | User access control |

### **🔹 Creating a VM in GCP**  
1️⃣ Open **Google Cloud Console → Compute Engine**  
2️⃣ Click **Create Instance**  
3️⃣ Choose **Machine Type** (e.g., e2-micro – Free Tier)  
4️⃣ Configure **firewall rules**  
5️⃣ Click **Create** and connect via SSH:  
```bash
gcloud compute ssh instance-name
```

---

# **🗓️ Day 65: Cloud Networking & Security Basics**  

### **🔹 What is Cloud Networking?**  
Cloud networking involves managing **virtual networks, security groups, load balancers, and firewalls** in cloud environments.

### **🔹 Key Networking Concepts**  

| **Concept** | **Description** |
|-------------|----------------|
| **VPC (Virtual Private Cloud)** | A private cloud network for resources |
| **Subnets** | Smaller divisions within a VPC |
| **Security Groups** | Firewall rules to allow/block traffic |
| **Load Balancer** | Distributes incoming traffic across servers |
| **VPN (Virtual Private Network)** | Secure encrypted connection to cloud resources |

### **🔹 Configuring Security Groups in AWS**  
1️⃣ Go to **AWS EC2 → Security Groups**  
2️⃣ Click **Create Security Group**  
3️⃣ Add **Inbound Rule**:  
   - **SSH (22) → My IP**  
   - **HTTP (80) → Anywhere**  
4️⃣ Assign Security Group to an EC2 instance.

---

# **📌 Week 12 Summary: Cloud Computing Basics Recap**  

| Day | Topic | Summary |
|----|--------|---------|
| **61** | Cloud Computing Basics | Introduction to cloud computing models and benefits. |
| **62** | AWS Fundamentals | Setting up EC2, IAM, and security configurations. |
| **63** | Azure Fundamentals | Deploying VMs and understanding core services. |
| **64** | GCP Fundamentals | Setting up Compute Engine and networking. |
| **65** | Cloud Networking & Security | Understanding VPCs, subnets, security groups, and load balancers. |

---

# **🎯 What You Learned This Week**  
✅ What **Cloud Computing** is and its benefits  
✅ How to create and manage **AWS EC2, Azure VMs, and GCP Compute Engine**  
✅ Basics of **cloud networking, security groups, and load balancing**  
✅ The differences between **IaaS, PaaS, and SaaS**  

---