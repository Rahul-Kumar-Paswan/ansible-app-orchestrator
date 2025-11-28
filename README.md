# 🚀 Ansible Automated Spring Boot Deployment — Multi-EC2 | MySQL | Vault

[![GitHub Repo](https://img.shields.io/badge/GitHub-Repo-181717?logo=github)](https://github.com/Rahul-Kumar-Paswan/YourRepoName)
![Ansible](https://img.shields.io/badge/Ansible-Automation-red?logo=ansible)
![Spring Boot](https://img.shields.io/badge/SpringBoot-Java-brightgreen?logo=spring)
![MySQL](https://img.shields.io/badge/MySQL-Database-blue?logo=mysql)
![AWS](https://img.shields.io/badge/AWS-EC2-orange?logo=amazon-aws)
![MIT License](https://img.shields.io/badge/License-MIT-yellow)

---

## 📌 Project Overview

This project demonstrates **professional DevOps automation** by deploying a **Spring Boot application** (`rahulverse-user-portal`) across **multiple EC2 web servers** with a **single MySQL database server** using **Ansible roles and playbooks**.  

**Key highlights:**

- Infrastructure: 3-tier architecture (web + DB).  
- Deployment automation via **Ansible roles** (`mysql`, `springboot`).  
- Secrets management using **Ansible Vault**.  
- Proof-of-concept screenshots included.  
- Designed to be **scalable** for additional web servers.  

This project is meant for a **portfolio showcase** of real-world DevOps practices.

---

## 📁 Project Structure
```text
.
├── ansible
│ ├── ansible.cfg
│ ├── inventory
│ │ └── hosts.ini
│ ├── playbook
│ │ ├── app-deploy.yml
│ │ └── mysql-deploy.yml
│ ├── roles
│ │ ├── mysql
│ │ └── springboot
│ └── vault
│ └── vault_pass.txt
└── rahulverse-user-portal
├── pom.xml
├── src
└── screenshots
```

---


**Roles used:**

- `mysql` — Installs MySQL, configures DB, users, remote access, and ensures secure credentials via Vault.  
- `springboot` — Deploys Spring Boot app, configures systemd service, connects to MySQL DB.  

---

## 🛠️ Prerequisites

- **Ansible ≥ 2.9**  
- **Python3** on target servers  
- **EC2 instances** with SSH access  
- **Vault password file** (`ansible/vault/vault_pass.txt`)  
- **JDK 11+** installed on web servers  

---

## ⚡ Setup and Deployment

1. **Encrypt secrets using Vault** (already done in this project):
```bash
ansible-vault encrypt ansible/roles/mysql/vars/main.yml
ansible-vault encrypt ansible/roles/springboot/vars/main.yml
```

2. **Inventory example** (ansible/inventory/hosts.ini):
```yaml
[webserver]
web-1 ansible_host=<PUBLIC_IP> ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/key.pem
web-2 ansible_host=<PUBLIC_IP> ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/key.pem

[dbserver]
db ansible_host=<PUBLIC_IP> ansible_user=ubuntu ansible_ssh_private_key_file=/path/to/key.pem
```

3. **Run MySQL deployment first:**
```bash
ansible-playbook -i ansible/inventory/hosts.ini ansible/playbook/mysql-deploy.yml --vault-password-file ansible/vault/vault_pass.txt
```

4. **Deploy Spring Boot application:**
```bash
ansible-playbook -i ansible/inventory/hosts.ini ansible/playbook/app-deploy.yml --vault-password-file ansible/vault/vault_pass.txt
```

5. **Verify application:**
Access your web server public IP in browser: http://<WEB_SERVER_IP>:8080/

---

## 🔧 Adding More Web Servers

- Add new web server(s) to the **[webserver]** group in `hosts.ini`.
- Run the app deployment playbook again — it will automatically deploy the app to the newly added servers.

---

## 💡 Future Enhancements

- CI/CD integration with **Jenkins / GitHub Actions**
- Containerization using **Docker** for web and DB services
- Load Balancer and auto-scaling with **AWS ELB / ASG**
- Monitoring with **Prometheus / Grafana**

---

## 📝 Author & Portfolio

**Rahul Paswan**

- **GitHub:** https://github.com/Rahul-Kumar-Paswan  
- **Portfolio:** https://rahulpaswanverse.vercel.app  

---

## 📝 License

**MIT License © 2025 Rahul Paswan**  
This project is licensed under the **MIT License**.
