# **📌 Week 13: Deploying Kubernetes on Cloud (Day 66-70)**  
This week, you will learn how to deploy **Kubernetes on cloud providers** like **AWS (EKS), Google Cloud (GKE), and Azure (AKS)**. You will understand how to create a **Kubernetes cluster**, deploy applications, manage workloads, and configure networking and security on cloud-based Kubernetes platforms.

By the end of this week, you will understand:  
✅ **How to deploy Kubernetes clusters on AWS, GCP, and Azure**  
✅ **The architecture of managed Kubernetes services (EKS, GKE, AKS)**  
✅ **How to deploy, manage, and scale applications on cloud Kubernetes**  
✅ **How to configure networking, security, and monitoring in cloud-based Kubernetes**  

---

# **🗓️ Day 66: Introduction to Cloud-based Kubernetes**  

### **🔹 Why Use Kubernetes on the Cloud?**  
Deploying Kubernetes on cloud providers helps in:  
✅ **Eliminating manual setup** – Managed Kubernetes services handle cluster creation and updates.  
✅ **High availability** – Cloud providers offer auto-scaling and disaster recovery.  
✅ **Integration with cloud services** – Easily use cloud storage, networking, monitoring, etc.  
✅ **Security & Cost-efficiency** – Built-in role-based access control (RBAC) and cost management.

### **🔹 Managed Kubernetes Services**  
| **Cloud Provider** | **Managed Kubernetes Service** |
|------------------|--------------------------------|
| **AWS** | EKS (Elastic Kubernetes Service) |
| **Google Cloud** | GKE (Google Kubernetes Engine) |
| **Azure** | AKS (Azure Kubernetes Service) |

### **🔹 Key Concepts in Cloud-based Kubernetes**  
- **Control Plane** – Managed by the cloud provider (no need to manually manage master nodes).  
- **Worker Nodes** – Managed instances running containerized workloads.  
- **Cluster Auto-Scaling** – Automatically adds/removes nodes based on demand.  
- **Networking & Load Balancing** – Cloud providers integrate with external load balancers and private networking.

---

# **🗓️ Day 67: Deploying Kubernetes on AWS (EKS)**  

### **🔹 What is AWS EKS?**  
Amazon Elastic Kubernetes Service (EKS) is a **managed Kubernetes service** that provides a scalable, secure, and fully operational Kubernetes environment.

### **🔹 Steps to Deploy an EKS Cluster**  

#### ✅ **Step 1: Install AWS CLI & eksctl**  
Ensure you have the necessary tools installed:  
```bash
aws configure  # Set up AWS credentials
```
Install `eksctl` to manage EKS:  
```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /usr/local/bin
eksctl version
```

#### ✅ **Step 2: Create an EKS Cluster**  
```bash
eksctl create cluster --name my-cluster --region us-east-1 --nodegroup-name my-nodes --nodes 2 --nodes-min 1 --nodes-max 3
```
This command:  
✔️ Creates a **Kubernetes cluster** in AWS  
✔️ Deploys **2 worker nodes** (scalable between 1-3)  

#### ✅ **Step 3: Configure kubectl to Access the Cluster**  
```bash
aws eks --region us-east-1 update-kubeconfig --name my-cluster
kubectl get nodes
```

#### ✅ **Step 4: Deploy an Application on EKS**  
```bash
kubectl create deployment nginx-deploy --image=nginx
kubectl expose deployment nginx-deploy --port=80 --type=LoadBalancer
kubectl get svc
```

✅ **Your EKS cluster is now running a public Nginx service!** 🎉  

---

# **🗓️ Day 68: Deploying Kubernetes on Google Cloud (GKE)**  

