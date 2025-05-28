# 🚀 Kriyadocs DevOps Assessment – Infrastructure Automation & CI/CD Deployment

This submission addresses the DevOps/SysOps case study outlined by Kriyadocs by delivering a fully automated deployment workflow and secure infrastructure setup using modern DevOps tooling.

---

## 📌 What I Did

### 1. 🚀 Infrastructure Provisioning with Terraform
I used **Terraform** to provision the following infrastructure on **AWS**:
- **VPC** and **Public Subnet** for isolated networking
- **Internet Gateway** and **Route Table** for outbound connectivity
- **Security Group** with rules to allow **SSH (22)**, **HTTP (80)**, and **HTTPS (443)**
- **EC2 instance** (Ubuntu, `t2.micro`) using AMI `ami-084568db4383264d4`
- Attached a **30 GB EBS volume** to the instance
- Outputted the **EC2 public IP** for access

This setup ensures that all resources are reproducible and version-controlled using Terraform.

---

### 2. ⚙️ Application Deployment Using Apache2 + FastAPI

- I deployed a **FastAPI** application to the EC2 instance.
- Configured **Apache2** as a reverse proxy to forward HTTP traffic to Uvicorn running the FastAPI app on port 8000.
- Managed the FastAPI application using a **systemd service**, allowing lifecycle control via `systemctl`.

---

### 3. 🌐 DNS Management with Route 53

- Created a **custom subdomain**: `api.kriyadocs.boopathy98.xyz`
- Configured an **A Record** in **Amazon Route 53** pointing the domain to the EC2 public IP
- Ensured domain propagation was completed before enabling HTTPS

---

### 4. 🔒 SSL Encryption with Certbot

- Installed and configured **Certbot** on the EC2 instance
- Used Certbot’s **Apache plugin** to:
  - Automatically generate and install a **Let's Encrypt SSL certificate**
  - Enable **HTTPS**
  - Redirect HTTP to HTTPS

---

### 5. 🔁 CI/CD Automation with GitHub Actions

- Implemented a **GitHub Actions CI/CD pipeline** to automate:
  - Code deployment to the EC2 instance
  - Remote SSH connection using a secure GitHub secret (`boopathy.pem`)
  - Pulling the latest code and restarting the FastAPI service

This ensures every push to the `main` branch triggers a fresh deployment to production.

---

## ✅ Outcome

- Fully automated infrastructure deployment with **Terraform**
- FastAPI application served securely via **Apache2 reverse proxy with SSL**
- Domain managed with **Route 53** and secured with **HTTPS**
- **CI/CD pipeline** using GitHub Actions for zero-downtime deployments

---

## 🧑‍💼 Author

**Boopathy**  
🌐 https://api.kriyadocs.boopathy98.xyz/
📧 sboopathys98@gmail.com
