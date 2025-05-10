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

### **🔹 What is Google Kubernetes Engine (GKE)?**  
Google Kubernetes Engine (GKE) is a fully managed Kubernetes service with automatic scaling, security, and networking optimizations.

### **🔹 Steps to Deploy a GKE Cluster**  

#### ✅ **Step 1: Install Google Cloud SDK & Enable GKE API**  
```bash
gcloud auth login
gcloud config set project <your-project-id>
gcloud services enable container.googleapis.com
```

#### ✅ **Step 2: Create a GKE Cluster**  
```bash
gcloud container clusters create my-gke-cluster --num-nodes=2 --zone us-central1-a
gcloud container clusters get-credentials my-gke-cluster --zone us-central1-a
kubectl get nodes
```

#### ✅ **Step 3: Deploy an Application on GKE**  
```bash
kubectl create deployment hello-world --image=gcr.io/google-samples/hello-app:1.0
kubectl expose deployment hello-world --type=LoadBalancer --port=80
kubectl get svc
```
You will get an **external IP**, which you can use to access your application.

✅ **Your Kubernetes cluster is now running on GCP!** 🚀  

---

# **🗓️ Day 69: Deploying Kubernetes on Azure (AKS)**  
### **🔹 What is Azure Kubernetes Service (AKS)?**  
Azure Kubernetes Service (AKS) is Microsoft’s managed Kubernetes solution that integrates well with Azure’s security, networking, and monitoring tools.

### **🔹 Steps to Deploy an AKS Cluster**  

#### ✅ **Step 1: Install Azure CLI & Enable AKS**  
```bash
az login
az group create --name myResourceGroup --location eastus
```

#### ✅ **Step 2: Create an AKS Cluster**  
```bash
az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 2 --enable-addons monitoring --generate-ssh-keys
```
This creates a **2-node Kubernetes cluster** with monitoring enabled.

#### ✅ **Step 3: Connect to the Cluster**  
```bash
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
kubectl get nodes
```

#### ✅ **Step 4: Deploy an Application on AKS**  
```bash
kubectl create deployment demo-app --image=mcr.microsoft.com/azuredocs/aks-helloworld:v1
kubectl expose deployment demo-app --port=80 --type=LoadBalancer
kubectl get svc
```
✅ Your AKS cluster is now running a public application! 🌍  

---

# **🗓️ Day 70: Cloud Kubernetes Networking, Security & Scaling**  

### **🔹 Kubernetes Networking in the Cloud**  
- **Load Balancers** – Automatically created for public services (`LoadBalancer` type).  
- **Ingress Controllers** – Used for routing traffic within the cluster.  
- **Cloud VPC Integration** – Kubernetes nodes run inside cloud VPCs for isolation.

### **🔹 Security in Cloud Kubernetes**  
- **IAM & RBAC** – Control user access to Kubernetes resources.  
- **Pod Security Policies** – Restrict container privileges.  
- **Network Policies** – Define traffic rules between pods.  

### **🔹 Scaling in Managed Kubernetes**  
- **Cluster Auto-Scaling** – Adds/removes nodes based on demand.  
- **Horizontal Pod Autoscaler (HPA)** – Adjusts the number of pods dynamically.  
```bash
kubectl autoscale deployment nginx-deploy --cpu-percent=50 --min=2 --max=10
```

---

# **📌 Week 13 Summary: Deploying Kubernetes on Cloud**  

| Day | Topic | Summary |
|----|--------|---------|
| **66** | Cloud-based Kubernetes | Introduction to managed Kubernetes services (EKS, GKE, AKS) |
| **67** | Deploying Kubernetes on AWS (EKS) | Setting up a Kubernetes cluster using AWS EKS |
| **68** | Deploying Kubernetes on Google Cloud (GKE) | Creating and managing Kubernetes on GKE |
| **69** | Deploying Kubernetes on Azure (AKS) | Deploying Kubernetes clusters using Azure AKS |
| **70** | Cloud Kubernetes Networking & Security | Managing networking, security, and scaling in cloud Kubernetes |

---

# **🎯 What You Learned This Week**  
✅ How to **deploy Kubernetes on AWS, Google Cloud, and Azure**  
✅ How to **run applications using managed Kubernetes services**  
✅ How to **configure networking, security, and auto-scaling in cloud Kubernetes**  

---