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

By default, Pods in Kubernetes **cannot be accessed externally**. **Services** allow communication between Pods and external clients.

### **🔹 Types of Services**
| Service Type | Description |
|-------------|------------|
| **ClusterIP** | Default; exposes the service internally. |
| **NodePort** | Exposes the service on a static port across nodes. |
| **LoadBalancer** | Uses a cloud provider’s load balancer (AWS, GCP, etc.). |

### **🔹 Creating a Service (NodePort Example)**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30008
```
Apply it:
```bash
kubectl apply -f service.yaml
```
Get the Service details:
```bash
kubectl get svc
```
Access the app in the browser:
```
http://<NODE_IP>:30008
```

---

## **🗓️ Day 39: ConfigMaps & Secrets (Managing Configuration)**  

Kubernetes provides **ConfigMaps** and **Secrets** to manage configurations separately from code.

### **🔹 ConfigMaps (Store Non-Sensitive Data)**
Used for environment variables, database URLs, etc.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  database_url: "mongodb://mongo:27017"
```
Apply it:
```bash
kubectl apply -f configmap.yaml
```
Use it in a Pod:
```yaml
env:
  - name: DATABASE_URL
    valueFrom:
      configMapKeyRef:
        name: app-config
        key: database_url
```

### **🔹 Secrets (Store Sensitive Data)**
Used for passwords, API keys, etc.

Create a secret:
```bash
kubectl create secret generic db-secret --from-literal=password=MySecurePass
```
Use it in a Pod:
```yaml
env:
  - name: DB_PASSWORD
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: password
```

---

## **🗓️ Day 40: Ingress Controllers (Advanced Routing)**  

Ingress is used to expose services externally **via domain names** instead of IP addresses.

### **🔹 Ingress Example**
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
    - host: myapp.local
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: nginx-service
                port:
                  number: 80
```
Apply it:
```bash
kubectl apply -f ingress.yaml
```
Verify:
```bash
kubectl get ingress
```
Update `/etc/hosts` (Linux/macOS):
```bash
echo "127.0.0.1 myapp.local" | sudo tee -a /etc/hosts
```
Now, you can access **http://myapp.local** 🎉

---

## **📌 Week 7 Summary (Kubernetes Basics Recap)**  
| Day | Topic | Summary |
|----|--------|---------|
| **36** | Kubernetes Architecture | Understanding Kubernetes components (Master, Worker, etc.). |
| **37** | Pods & Deployments | Deploying containerized apps in Kubernetes. |
| **38** | Services | Exposing applications using different service types. |
| **39** | ConfigMaps & Secrets | Managing configurations and sensitive data securely. |
| **40** | Ingress Controllers | Advanced routing with domain-based access. |

---

# **📌 Week 8: Kubernetes Advanced**  
This week focuses on **Helm, Operators, RBAC (Role-Based Access Control), and Kubernetes Networking**. These are essential for managing complex applications, securing access, and optimizing cluster networking.  

By the end of this week, you’ll understand **how to use Helm for package management, deploy custom Kubernetes Operators, implement RBAC for security, and manage advanced networking concepts**.

---

## **🗓️ Day 41: Helm - Kubernetes Package Manager**  
Helm is a package manager for Kubernetes, similar to **apt/yum** for Linux. It simplifies installing, upgrading, and managing applications.

### **🔹 Why Use Helm?**
- **Easier Deployments** → Install complex applications with one command.
- **Version Control** → Rollback to previous versions easily.
- **Reusable Templates** → Helm **Charts** allow defining reusable YAML templates.

### **🔹 Installing Helm**
```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```
Verify installation:
```bash
helm version
```

### **🔹 Using Helm Charts**
Helm **Charts** are packaged Kubernetes applications.

#### **Installing a Chart (Example: Nginx)**
```bash
helm repo add stable https://charts.helm.sh/stable
helm repo update
helm install my-nginx stable/nginx-ingress
```
List installed Helm releases:
```bash
helm list
```
#### **Uninstalling a Chart**
```bash
helm uninstall my-nginx
```

### **🔹 Creating Your Own Helm Chart**
1️⃣ Create a new chart:
```bash
helm create mychart
```
2️⃣ Structure of a Helm Chart:
```
mychart/
│── templates/         # YAML templates
│── values.yaml        # Default configuration
│── Chart.yaml         # Chart metadata
```
3️⃣ Install your custom chart:
```bash
helm install my-app mychart/
```
---

## **🗓️ Day 42: Kubernetes Operators**  

Kubernetes **Operators** extend Kubernetes capabilities by automating complex tasks like database backups and self-healing applications.

### **🔹 What is an Operator?**
An Operator is a **custom controller** that manages application lifecycles using **Custom Resource Definitions (CRDs)**.

| **Component** | **Description** |
|--------------|----------------|
| **Custom Resource (CR)** | A new resource type (e.g., `MyDatabase`). |
| **Custom Resource Definition (CRD)** | Defines the structure of CRs. |
| **Operator Controller** | Automates app-specific tasks (e.g., scaling, healing). |

### **🔹 Example: Deploying a MySQL Operator**
1️⃣ Install Operator SDK:
```bash
curl -LO https://github.com/operator-framework/operator-sdk/releases/download/v1.15.0/operator-sdk_linux_amd64
chmod +x operator-sdk_linux_amd64
sudo mv operator-sdk_linux_amd64 /usr/local/bin/operator-sdk
```
2️⃣ Apply MySQL Operator:
```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes-sigs/mysql-operator/main/deploy/crds/mysql_v1alpha1_mysqlcluster_crd.yaml
```
3️⃣ Deploy a MySQL Database:
```yaml
apiVersion: mysql.oracle.com/v1alpha1
kind: MySQLCluster
metadata:
  name: my-db
spec:
  replicas: 3
```
```bash
kubectl apply -f my-db.yaml
```
Verify:
```bash
kubectl get mysqlclusters
```

---

## **🗓️ Day 43: Role-Based Access Control (RBAC) in Kubernetes**  
