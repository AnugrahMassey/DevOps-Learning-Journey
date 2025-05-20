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

**Goal:** Understand how to limit access in systems through user roles.

#### 🧩 What is RBAC?

Role-Based Access Control defines:

* **Who** can access
* **What** resources
* **What actions** they can perform

#### ⚙️ RBAC in Different Tools:

* **Linux**: `sudo`, user groups
* **Kubernetes**: Roles, ClusterRoles, RoleBindings
* **AWS IAM**: Users, Roles, Policies

#### 🧪 Practice:

* Create a new Linux user and limit them using groups.
* In Kubernetes:

  ```yaml
  kind: Role
  apiVersion: rbac.authorization.k8s.io/v1
  ...
  ```

---

### ✅ **Day 78: Secure CI/CD Pipelines**

**Goal:** Secure your automation pipelines to avoid vulnerabilities.

#### 🛡️ Security Considerations:

* Avoid leaking secrets in logs.
* Use secrets management plugins or encrypted variables.
* Validate code with security linters.
* Use signed artifacts and containers.

#### 🧰 Tools:

* GitHub Actions Secrets
* Snyk, Trivy – security scanners
* OPA, Conftest – policy as code

#### 🧪 Practice:

* Add secret variables in GitHub Actions.
* Run `trivy image nginx` to scan a Docker image.

---

### ✅ **Day 79: Compliance Standards & Tools**

**Goal:** Understand industry standards and tools for achieving compliance.

#### 🔒 Popular Standards:

* **ISO/IEC 27001** – Security management
* **SOC2** – Data privacy
* **PCI-DSS** – Payment data protection
* **HIPAA** – Health information

#### ⚙️ Tools to Help:

* **OpenSCAP** – Compliance scanning
* **Aqua Security**, **Prisma Cloud**, **Checkov**
* **AWS Config** – compliance rules in AWS

#### 🧪 Practice:

* Read about a compliance policy your project would need.
* Run `checkov` on a Terraform or Kubernetes config.

---

### ✅ **Day 80: Final Project + Recap**

**Goal:** Apply what you learned in a hands-on security enhancement task.

#### 🛠️ Mini-Project Idea:

* Create a GitHub Actions pipeline that:

  * Uses secrets securely
  * Scans Docker images
  * Applies RBAC to Kubernetes deployment
  * Logs audit activity

#### 🧠 Recap:

* Secrets should never be hard-coded.
* RBAC controls **who** can do **what**.
* CI/CD pipelines can leak secrets — secure them.
* Use scanning tools regularly.
* Know the compliance standard that applies to your work.

---

## 📝 Week 15 Summary:

| Day | Topic                | Focus                                      |
| --- | -------------------- | ------------------------------------------ |
| 76  | Secrets Management   | Store and retrieve sensitive data securely |
| 77  | RBAC                 | Limit user access based on roles           |
| 78  | Secure Pipelines     | Harden CI/CD pipelines and prevent leaks   |
| 79  | Compliance Standards | Learn policies and tools for audits        |
| 80  | Project & Recap      | Hands-on implementation of secure pipeline |

---
