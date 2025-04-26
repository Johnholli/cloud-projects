# 🚀 Deploy WordPress on Ubuntu EC2
![Ec2-ubuntu-graphic](https://github.com/user-attachments/assets/5b264806-9dfb-44e1-967e-50a504a064f3)

<a href="https://img.shields.io/badge/AWS-EC2-orange"><img src="https://img.shields.io/badge/AWS-EC2-orange" alt="AWS EC2"/></a>
  <a href="https://img.shields.io/badge/Linux-Ubuntu-blue"><img src="https://img.shields.io/badge/Linux-Ubuntu-blue" alt="Ubuntu"/></a>
  <a href="https://img.shields.io/badge/CMS-WordPress-blueviolet"><img src="https://img.shields.io/badge/CMS-WordPress-blueviolet" alt="WordPress"/></a>

> **Role:** Junior Cloud Engineer  
> **Goal:** Spin up a fully-functional WordPress site in AWS, learn core cloud skills, and showcase a production-ready deployment.

---

## 🛠️ Tech Stack & Tools

| Layer        | Service / Package            |
|--------------|------------------------------|
| **Compute**  | AWS EC2 (Ubuntu 22.04 LTS)   |
| **Network**  | VPC, Security Groups         |
| **SSH**      | OpenSSH key-pair auth        |
| **Web**      | Apache 2.4                   |
| **Database** | MySQL 8                      |
| **Runtime**  | PHP 8.x + extensions (curl, gd, mbstring, xml, zip) |
| **App**      | WordPress 6.x                |

---

## 📈 Architecture

```mermaid
flowchart TD
    Client[User Browser] -->|HTTP 80| ALB{{Application Load Balancer}}
    ALB --> EC2[Ubuntu EC2 Auto-Scaling Group]
    EC2 -->|PHP ↔ MySQL| RDS[(Amazon RDS MySQL)]
    EC2 -- SSH 22 --> Bastion[Jump Host]
    subgraph VPC
      ALB & EC2 & RDS & Bastion
    end
```
