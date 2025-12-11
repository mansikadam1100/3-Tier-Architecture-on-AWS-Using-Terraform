# 🚀 3-Tier Architecture on AWS Using Terraform

This project deploys a complete **3-Tier Architecture** on AWS using **Terraform**.  
The setup includes a **Web Tier (Public Subnet)**, **App Tier (Private Subnet)**, and **Database Tier (Private Subnet)** with secure routing, NAT Gateway, and Internet access for required layers.

---

## 🏗️ Architecture Overview

![](./img/3%20tier%20diagram.png)

### **VPC Setup**
- Custom VPC (`10.0.0.0/16`)
- Three subnets:
  - Public Subnet (Web Tier)
  - Private Subnet (App Tier)
  - Private Subnet (DB Tier)
- High Availability using different AZs

### **Networking Components**
- Internet Gateway (IGW)
- NAT Gateway for private instances
- Public Route Table → IGW
- Private Route Table → NAT Gateway

### **Compute**
- EC2 Web Server (public)
- EC2 App Server (private)
- EC2 DB Server (private)

### **Security**
- Security Group allowing:
  - SSH (22)
  - HTTP (80)
  - HTTPS (443)

---

## 📁 Project Structure
```
├── main.tf
├── variables.tf
├── outputs.tf
├── README.md
```

---

## ⚙️ Requirements

| Tool | Version |
|------|---------|
| Terraform | v1.5+ |
| AWS CLI | v2 |
| AWS Account | Required |
| SSH Key | Must exist in AWS EC2 panel |

---

## 🔧 How to Use

### **1️⃣ Clone the Repo**

```sh
git clone https://github.com/mansikadam1100/terraform-3tier-architecture.git

cd terraform-3tier-architecture

2️⃣ Configure AWS Credentials
aws configure


Enter:

AWS Access Key
AWS Secret Key
Region
Output format

3️⃣ Initialize Terraform
terraform init

4️⃣ Validate
terraform validate

5️⃣ Deploy
terraform apply --auto-approve
```
🌐 Outputs
---
After deployment Terraform prints:

Web Server Public IP

App Server Private IP

DB Server Private IP

Example:
web_public_ip = "13.xxx.xxx.xxx"
app_private_ip = "10.0.2.10"
db_private_ip  = "10.0.3.12"

🧹 Destroy Infrastructure
--
terraform destroy --auto-approve



# 📸 Screenshots

---

## 1️⃣ Terraform Apply Output

![](./img/3-tier1.png)


## 2️⃣ S3 Bucket (Terraform Backend)

![](./img/3%20s3bucket.png)

---

## 3️⃣ EC2 Instances

![](./img/3instance.png)

---

## 4️⃣ VPC Overview

![](./img/3vpc.png)

---

## 5️⃣ Subnets (Public, App, DB)

![](./img/3subnet.png)

---

## 6️⃣ Route Tables

![](./img/3route%20table.png)

---

## 7️⃣ Internet Gateway (IGW)

![](./img/3internet%20geteway.png)

---

## 8️⃣ NAT Gateway

![](./img/3nat%20gateway.png)

---
## 🖼️ 3-Tier Architecture Diagram (ASCII)

                  ┌────────────────────────┐
                  │        Internet         │
                  └───────────┬────────────┘
                              │
                   ┌──────────▼──────────┐
                   │   Internet Gateway   │
                   └──────────┬──────────┘
                              │
                  ┌───────────▼────────────┐
                  │     Public Subnet       │
                  ├─────────────────────────┤
                  │   EC2 Web Server        │
                  └───────────┬────────────┘
                              │
                   ┌──────────▼──────────┐
                   │     NAT Gateway      │
                   └──────────┬──────────┘
                              │
         ┌────────────────────▼────────────────────┐
         │                Private RT                │
         └──────────────┬───────────────┬─────────┘
                        │               │
           ┌────────────▼───┐  ┌────────▼────────┐
           │ Private Subnet │  │ Private Subnet   │
           │   App Tier     │  │    DB Tier       │
           ├────────────────┤  ├──────────────────┤
           │ EC2 App Server │  │ EC2 DB Server    │
           └────────────────┘  └──────────────────┘

## 📌 Features

✔ Fully automated 3-tier infrastructure
✔ Modular, scalable architecture
✔ Secure private networking
✔ NAT-enabled outbound access
✔ Reusable Terraform variables
✔ AWS best-practice design

## 🧑‍💻 Author

mansi Kadam
Terraform | AWS | DevOps | Cloud Projects