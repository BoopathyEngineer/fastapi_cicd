# 🚀 Kriyadocs DevOps Assessment – Infrastructure Provisioning & FastAPI Deployment

This submission fulfills the Kriyadocs DevOps case study by implementing a complete infrastructure-as-code and deployment pipeline using **Terraform**, **Apache2**, **FastAPI**, and **Let's Encrypt SSL** on **AWS EC2**. The goal was to build a reliable, repeatable setup aligned with Kriyadocs' infrastructure expectations.

---

## 📦 Stack Used

- **Infrastructure Provisioning**: Terraform
- **Cloud Provider**: AWS (Ubuntu EC2)
- **Web Server**: Apache2 (reverse proxy)
- **App**: FastAPI (Python)
- **SSL**: Certbot (Let's Encrypt)
- **Service Management**: systemd

---

## 🏗️ What This Project Covers

✅ Provisions:
- VPC, Public Subnet, Internet Gateway
- EC2 instance (Ubuntu) with 30 GB EBS
- Security Group with ports `22`, `80`, `443` open

✅ Deploys:
- Python FastAPI app with `systemd` as a managed service
- Apache2 reverse proxy on EC2
- Domain `api.kriyadocs.boopathy98.xyz` with HTTPS

✅ Documents:
- Complete deployment steps
- SSL configuration
- Terraform module breakdown

---

## 📁 Repository Structure

deploy_fastapi/
├── terraform/
│ ├── main.tf
│ ├── outputs.tf
│ ├── variable.tf
│ ├── terraform.tfstate
│ ├── terraform.tfstate.backup
│ └── tf.vars
├── README.md
