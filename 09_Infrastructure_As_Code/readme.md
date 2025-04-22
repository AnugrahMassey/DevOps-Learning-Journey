# **📌 Week 10: Infrastructure as Code (IaC)**  
This week, you will learn how to **automate infrastructure provisioning** using **Terraform, Ansible, and AWS CloudFormation**.  

By the end of this week, you’ll understand:
✅ **What Infrastructure as Code (IaC) is and why it’s important**  
✅ **How to use Terraform to provision cloud infrastructure**  
✅ **How to automate server configuration with Ansible**  
✅ **How AWS CloudFormation simplifies cloud infrastructure management**  

---

## **🗓️ Day 51: Introduction to Infrastructure as Code (IaC)**  

### **🔹 What is Infrastructure as Code (IaC)?**
Infrastructure as Code (IaC) is the **process of managing and provisioning infrastructure** (servers, networks, databases) using **code instead of manual processes**.

### **🔹 Why Use IaC?**
✅ **Automates infrastructure provisioning**  
✅ **Reduces manual errors**  
✅ **Improves scalability and consistency**  
✅ **Makes infrastructure reusable and version-controlled**  

### **🔹 Popular IaC Tools**
| **Tool** | **Purpose** |
|---------|-------------|
| **Terraform** | Automates cloud infrastructure provisioning |
| **Ansible** | Automates server configuration and management |
| **CloudFormation** | AWS-native IaC tool for managing cloud resources |

---

## **🗓️ Day 52: Getting Started with Terraform**  

### **🔹 What is Terraform?**
Terraform is an **open-source IaC tool** that allows you to define and provision infrastructure using a **declarative configuration language**.

### **🔹 Installing Terraform**
#### **On Linux/macOS:**
```bash
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
sudo apt update && sudo apt install terraform -y
```
#### **On Windows (via Chocolatey)**
```powershell
choco install terraform
```

### **🔹 Creating a Simple Terraform Script**
1️⃣ Create a new directory:
```bash
mkdir terraform-demo && cd terraform-demo
```
2️⃣ Create a file called `main.tf`:
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0" # Amazon Linux 2 AMI
  instance_type = "t2.micro"
}

output "instance_ip" {
  value = aws_instance.example.public_ip
}
```
3️⃣ **Initialize Terraform**:
```bash
terraform init
```
4️⃣ **Plan the infrastructure**:
```bash
terraform plan
```
5️⃣ **Apply the configuration**:
```bash
terraform apply
```
6️⃣ **Destroy the infrastructure** when no longer needed:
```bash
terraform destroy
```

---

## **🗓️ Day 53: Terraform Advanced Features**  

### **🔹 Understanding Terraform State**
Terraform maintains a **state file (`terraform.tfstate`)** to track the current state of infrastructure.

#### **Common Terraform Commands**
| Command | Description |
|---------|-------------|
| `terraform init` | Initializes a Terraform working directory |
| `terraform plan` | Shows what will change before applying |
| `terraform apply` | Creates or updates infrastructure |
| `terraform destroy` | Removes infrastructure |

### **🔹 Terraform Modules**
Terraform **modules** allow you to **reuse configurations**.
Example:
```hcl
module "ec2_instance" {
  source       = "./modules/ec2"
  instance_type = "t2.micro"
}
```

### **🔹 Terraform Variables**
```hcl
variable "instance_type" {
  default = "t2.micro"
}
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = var.instance_type
}
```

---

## **🗓️ Day 54: Ansible - Configuration Management**  
