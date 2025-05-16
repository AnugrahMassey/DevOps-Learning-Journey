# 🚨 **Week 15: Security & Compliance (Days 76–80)**

Security is essential in any DevOps lifecycle. This week focuses on building secure infrastructure and practices to protect systems, data, and pipelines.

---

### ✅ **Day 76: Secrets Management**

**Goal:** Understand how to store and manage sensitive data (like API keys, passwords) securely.

#### 🔐 What are Secrets?

Secrets are confidential information such as:

* API keys
* SSH private keys
* Database passwords
* OAuth tokens

####⚙️ Best Practices

* Never store secrets in code or Git repositories.
* Use environment variables for development.
* In production, use secret managers.

#### 🔧 Tools for Secrets Management:

* **HashiCorp Vault**: Advanced secret storage with access control.
* **AWS Secrets Manager** / **SSM Parameter Store**
* **Kubernetes Secrets**
* **Docker Secrets (Swarm)**

#### 🧪 Practice:

* Store a dummy password in an environment variable.
* Use `kubectl create secret` to create a secret in Kubernetes.
* Try AWS Secrets Manager via console or CLI.

---

### ✅ **Day 77: Role-Based Access Control (RBAC)**

