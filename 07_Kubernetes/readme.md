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

RBAC controls **who can access what** in the cluster, improving security.

### **🔹 RBAC Components**
| **Component** | **Description** |
|--------------|----------------|
| **Role** | Defines permissions within a namespace. |
| **ClusterRole** | Defines permissions across the entire cluster. |
| **RoleBinding** | Assigns a **Role** to a user or service account. |
| **ClusterRoleBinding** | Assigns a **ClusterRole** to a user or service account. |

### **🔹 Example: Creating an RBAC Role**
1️⃣ Define a Role that allows reading Pods:
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
  - apiGroups: [""]
    resources: ["pods"]
    verbs: ["get", "watch", "list"]
```
```bash
kubectl apply -f role.yaml
```
2️⃣ Create a RoleBinding to assign the Role to a user:
```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: pod-reader-binding
  namespace: default
subjects:
  - kind: User
    name: my-user
    apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```
```bash
kubectl apply -f rolebinding.yaml
```
Check permissions:
```bash
kubectl auth can-i list pods --as=my-user
```

---

## **🗓️ Day 44: Kubernetes Networking - Services, DNS, and Network Policies**  

Networking in Kubernetes ensures that **Pods can communicate** with each other and external clients.

### **🔹 Key Networking Concepts**
| **Component** | **Description** |
|--------------|----------------|
| **Pod Networking** | Every Pod gets a unique IP address. |
| **Cluster Networking** | Network plugins (CNI) handle traffic routing. |
| **Services** | Expose Pods inside or outside the cluster. |
| **Ingress** | Manages external access using hostnames. |

### **🔹 Kubernetes DNS**
Kubernetes has **built-in DNS** to allow service discovery.

Check Pod’s DNS resolution:
```bash
kubectl run -it --rm dns-test --image=busybox -- nslookup my-service.default.svc.cluster.local
```

### **🔹 Network Policies (Security Rules)**
Network Policies control traffic **between Pods**.

1️⃣ Deny all traffic by default:
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-all
spec:
  podSelector: {}
  policyTypes:
    - Ingress
```
```bash
kubectl apply -f deny-all.yaml
```

2️⃣ Allow traffic only from specific Pods:
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-from-app
spec:
  podSelector:
    matchLabels:
      app: database
  ingress:
    - from:
        - podSelector:
            matchLabels:
              app: backend
```
```bash
kubectl apply -f allow-from-app.yaml
```

---

## **🗓️ Day 45: Kubernetes Logging & Monitoring**  
Monitoring and logging help track cluster health and troubleshoot issues.

### **🔹 Logging with kubectl**
View logs of a Pod:
```bash
kubectl logs my-pod
```
Stream logs:
```bash
kubectl logs -f my-pod
```

### **🔹 Centralized Logging with ELK Stack**
**ELK (Elasticsearch, Logstash, Kibana)** collects and visualizes logs.

1️⃣ Deploy ELK:
```bash
helm repo add elastic https://helm.elastic.co
helm install elasticsearch elastic/elasticsearch
helm install kibana elastic/kibana
```
2️⃣ View logs in Kibana:
```
http://<KIBANA_IP>:5601
```

### **🔹 Monitoring with Prometheus & Grafana**
Install Prometheus:
```bash
helm install prometheus prometheus-community/kube-prometheus-stack
```
Install Grafana:
```bash
helm install grafana grafana/grafana
```
Access Grafana:
```
http://<GRAFANA_IP>:3000
```

---

## **📌 Week 8 Summary (Kubernetes Advanced Recap)**  
| Day | Topic | Summary |
|----|--------|---------|
| **41** | Helm | Package manager for Kubernetes. |
| **42** | Operators | Automating complex applications. |
| **43** | RBAC | Securing cluster access. |
| **44** | Networking | Services, DNS, and Network Policies. |
| **45** | Logging & Monitoring | Tracking cluster health with ELK, Prometheus & Grafana. |

---

This concludes **Week 8: Kubernetes Advanced**. You now have a **strong grasp of Helm, Operators, RBAC, Kubernetes Networking, and Monitoring**. 🎯  
