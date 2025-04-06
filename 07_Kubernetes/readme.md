# **📌 Week 7: Kubernetes Basics**  
Kubernetes (K8s) is an **orchestration tool** used to manage containerized applications across multiple servers. It automates deployment, scaling, networking, and management of containers.  

By the end of this week, you'll understand **Kubernetes architecture, Pods, Deployments, Services, and Ingress**.

---

## **🗓️ Day 36: Introduction to Kubernetes & Architecture**  
Before jumping into Kubernetes, let’s understand **why we need it**.  

### **🔹 Why Kubernetes?**
- **Manages Containers at Scale** → Automates deployment & scaling.
- **Self-healing** → If a container crashes, K8s restarts it.
- **Load Balancing** → Distributes traffic among containers.
- **Storage Orchestration** → Manages persistent storage.

### **🔹 Kubernetes Architecture**  
Kubernetes follows a **Master-Worker** architecture.

| Component | Description |
|-----------|------------|
| **Master Node** | Controls the cluster (API server, Scheduler, Controller Manager, etc.). |
| **Worker Nodes** | Run the containers (Pods). |
| **Kubelet** | Runs on each worker node, ensuring Pods are running. |
| **Kube Proxy** | Manages networking between Pods. |
| **etcd** | Stores cluster data (key-value store). |

### **🔹 Setting Up a Kubernetes Cluster (Minikube)**
Minikube allows running a single-node K8s cluster on your local machine.

#### **Installation:**
1️⃣ Install Minikube:
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
2️⃣ Start the cluster:
```bash
minikube start
```
3️⃣ Verify the setup:
```bash
kubectl get nodes
```

---

## **🗓️ Day 37: Kubernetes Pods & Deployments**  

A **Pod** is the smallest deployable unit in Kubernetes. A **Deployment** manages Pods and ensures they run as expected.

### **🔹 Creating a Pod (Manually)**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: nginx-container
      image: nginx
      ports:
        - containerPort: 80
```
Apply the Pod:
```bash
kubectl apply -f pod.yaml
```
Check running Pods:
```bash
kubectl get pods
```

### **🔹 Deployments (Managing Multiple Pods)**
A Deployment ensures a specified number of Pods run and can **auto-restart** if they fail.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx
          ports:
            - containerPort: 80
```
Apply it:
```bash
kubectl apply -f deployment.yaml
```
Verify:
```bash
kubectl get deployments
kubectl get pods
```

---

## **🗓️ Day 38: Services & Exposing Applications**  
