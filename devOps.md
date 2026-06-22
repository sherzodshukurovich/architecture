# 🚀 DevOps Fundamentals

## Software Engineer → DevOps Engineer → Solution Architect Roadmap

> DevOps — Development va Operations jamoalarini birlashtiruvchi metodologiya bo'lib, dastur yaratish, test qilish, deploy qilish va monitoring qilish jarayonlarini avtomatlashtirishga qaratilgan.

---

# Mundarija

```txt
1. DevOps nima?
2. DevOps Lifecycle
3. Linux Fundamentals
4. Networking Fundamentals
5. Git & Version Control
6. CI/CD
7. Build Systems
8. Containers
9. Docker
10. Docker Compose
11. Kubernetes
12. Reverse Proxy
13. Nginx
14. Load Balancing
15. Infrastructure as Code
16. Configuration Management
17. Monitoring
18. Logging
19. Cloud Computing
20. Security in DevOps
21. DevSecOps
22. GitOps
23. Production Architecture
24. DevOps Roadmap
```

---

# 1. DevOps nima?

Oldin:

```txt
Developer
 ↓
Kod yozadi

Operations
 ↓
Deploy qiladi
```

Natijada:

```txt
Deploy muammolari
Environment muammolari
Server muammolari
```

---

## DevOps

Development va Operations birlashadi.

```txt
Developer
 ↓
Build
 ↓
Test
 ↓
Deploy
 ↓
Monitor
```

---

## Maqsad

* Tez deploy
* Kam xato
* Yuqori ishonchlilik
* Avtomatlashtirish

---

# 2. DevOps Lifecycle

```txt
Plan
 ↓
Code
 ↓
Build
 ↓
Test
 ↓
Release
 ↓
Deploy
 ↓
Monitor
 ↓
Feedback
```

---

# 3. Linux Fundamentals

DevOps asosining 80% Linux.

---

## File System

```txt
/
├── home
├── etc
├── var
├── usr
├── tmp
└── opt
```

---

## Muhim papkalar

### /etc

Konfiguratsiyalar.

```txt
nginx.conf
hosts
passwd
```

---

### /var

Loglar.

```txt
/var/log
```

---

### /home

Foydalanuvchi fayllari.

---

# Muhim komandalar

## Fayllar

```bash
ls
pwd
cd
cp
mv
rm
mkdir
touch
```

---

## Processlar

```bash
ps aux
top
htop
kill
```

---

## Disk

```bash
df -h
du -sh
```

---

## Tarmoq

```bash
ping
curl
netstat
ss
```

---

# 4. Networking Fundamentals

DevOps uchun juda muhim.

---

## IP

```txt
192.168.1.10
```

---

## DNS

```txt
google.com
↓
142.x.x.x
```

---

## Portlar

```txt
22 SSH
80 HTTP
443 HTTPS
5432 PostgreSQL
3306 MySQL
6379 Redis
```

---

## TCP

Ishonchli aloqa.

---

## UDP

Tezkor aloqa.

---

# 5. Git & Version Control

---

## Git Workflow

```txt
Developer
 ↓
Git
 ↓
Repository
```

---

## Muhim komandalar

```bash
git clone
git pull
git push
git merge
git rebase
git checkout
git branch
```

---

## Git Flow

```txt
main
develop
feature/*
hotfix/*
release/*
```

---

# 6. CI/CD

Continuous Integration

Continuous Delivery

Continuous Deployment

---

## CI

Kod yoziladi.

```txt
Push
 ↓
Tests
 ↓
Build
```

---

## CD

```txt
Build
 ↓
Deploy
```

---

## Pipeline

```txt
Code
 ↓
Build
 ↓
Test
 ↓
Deploy
```

---

## Mashhur tizimlar

* GitLab CI
* GitHub Actions
* Jenkins
* Azure DevOps

---

# 7. Build Systems

---

## Frontend

```bash
vite build
npm run build
```

---

## Backend

```bash
maven
gradle
```

---

# 8. Containers

---

## Muammo

Serverlarda:

```txt
Menda ishlaydi
Serverda ishlamaydi
```

---

## Yechim

Container.

---

## Container

```txt
Application
Dependencies
Runtime
```

barchasi bitta paket.

---

# 9. Docker

Eng mashhur container platformasi.

---

## Docker Architecture

```txt
Docker Client
 ↓
Docker Engine
 ↓
Containers
```

---

## Dockerfile

```dockerfile
FROM node:20

WORKDIR /app

COPY . .

RUN npm install

CMD ["npm","start"]
```

---

## Build

```bash
docker build -t app .
```

---

## Run

```bash
docker run app
```

---

## Images

Read Only Template.

---

## Containers

Image ishlayotgan holati.

---

# 10. Docker Compose

Bir nechta service.

---

## Misol

```txt
Frontend
Backend
PostgreSQL
Redis
```

---

## docker-compose.yml

```yaml
services:
  app:
  postgres:
  redis:
```

---

# 11. Kubernetes

Container Orchestration Platform.

---

## Muammo

1000 ta container bo'lsa?

---

## Yechim

Kubernetes.

---

## Kubernetes Architecture

```txt
Master Node
 ↓
Worker Nodes
 ↓
Pods
```

---

## Pod

Eng kichik birlik.

---

## Deployment

Podlarni boshqaradi.

---

## Service

Tarmoq orqali ulaydi.

---

## Ingress

Tashqi trafik.

---

## ConfigMap

Konfiguratsiyalar.

---

## Secret

Maxfiy ma'lumotlar.

---

# 12. Reverse Proxy

---

## Misol

```txt
User
 ↓
Nginx
 ↓
Application
```

---

## Vazifalari

* SSL
* Routing
* Caching
* Compression

---

# 13. Nginx

Eng mashhur web server.

---

## Reverse Proxy

```nginx
location /api {
 proxy_pass http://backend;
}
```

---

## Static Files

```txt
HTML
CSS
JS
Images
```

---

## SSL

```txt
HTTPS
```

---

# 14. Load Balancing

---

## Muammo

Bitta server yuklanib qoladi.

---

## Yechim

```txt
Load Balancer
 ↓
Server1
Server2
Server3
```

---

## Algoritmlar

### Round Robin

Ketma-ket.

### Least Connections

Eng kam yuklangan server.

---

# 15. Infrastructure as Code

Infrastructure ham kod.

---

## Terraform

Eng mashhur.

---

## Misol

```hcl
resource "aws_instance" "web" {
}
```

---

# 16. Configuration Management

---

## Ansible

Serverlarni boshqaradi.

---

## Misol

```yaml
Install Nginx
Install Docker
```

---

# 17. Monitoring

Production kuzatish.

---

## Metrics

* CPU
* RAM
* Network
* Disk

---

## Prometheus

Metric yig'adi.

---

## Grafana

Dashboard.

---

# 18. Logging

---

## Nega kerak?

Muammo topish uchun.

---

## ELK Stack

```txt
Elasticsearch
Logstash
Kibana
```

---

## Loki

Grafana log tizimi.

---

# 19. Cloud Computing

---

## AWS

Eng mashhur.

---

### EC2

Virtual Server.

### RDS

Database.

### S3

Storage.

### EKS

Kubernetes.

---

## Azure

Microsoft Cloud.

---

## Google Cloud

Google Cloud Platform.

---

# 20. Security in DevOps

---

## HTTPS

Majburiy.

---

## Secrets

Parollar Gitga tushmasligi kerak.

---

## Vault

Secret Management.

---

## IAM

Access Control.

---

# 21. DevSecOps

Security DevOps ichiga qo'shiladi.

---

## SAST

Static Analysis.

---

## DAST

Dynamic Analysis.

---

## Dependency Scan

Kutubxonalarni tekshirish.

---

# 22. GitOps

Infrastructure Git orqali boshqariladi.

---

## Workflow

```txt
Git
 ↓
ArgoCD
 ↓
Kubernetes
```

---

# 23. Production Architecture

Enterprise tizim:

```txt
Internet
 ↓
Cloudflare
 ↓
Load Balancer
 ↓
Nginx
 ↓
Frontend
 ↓
API Gateway
 ↓
Microservices
 ↓
Redis
 ↓
PostgreSQL
 ↓
S3
```

---

# Monitoring Architecture

```txt
Application
 ↓
Prometheus
 ↓
Grafana
```

---

# Logging Architecture

```txt
Application
 ↓
ELK
 ↓
Dashboard
```

---

# 24. DevOps Roadmap

## Boshlang'ich

* Linux
* Networking
* Git

---

## Junior DevOps

* Docker
* Docker Compose
* CI/CD
* Nginx

---

## Middle DevOps

* Kubernetes
* Terraform
* Monitoring
* Logging

---

## Senior DevOps

* AWS
* Azure
* GCP
* GitOps
* DevSecOps

---

# React Developer uchun

Bilishi kerak:

✅ Linux

✅ Git

✅ Nginx

✅ Docker

✅ CI/CD

✅ HTTPS

---

# Full Stack uchun

Bilishi kerak:

✅ Docker

✅ Kubernetes

✅ Redis

✅ PostgreSQL

✅ Monitoring

---

# Solution Architect uchun

Bilishi kerak:

✅ Kubernetes

✅ Terraform

✅ AWS

✅ GitOps

✅ DevSecOps

✅ High Availability

✅ Disaster Recovery

---

# Production Checklist

```txt
HTTPS
Docker
CI/CD
Monitoring
Logging
Backup
Redis
Nginx
Firewall
Rate Limiting
```

---

# Yakuniy Maqsad

Ushbu bo'lim tugagach siz:

✔ Linux

✔ Networking

✔ Docker

✔ Kubernetes

✔ CI/CD

✔ Monitoring

✔ Logging

✔ Cloud

✔ DevSecOps

✔ Production Infrastructure

asoslarini professional darajada tushunadigan darajaga chiqasiz.

Bu bilimlar System Design, Cloud Architecture va Solution Architecture uchun poydevor bo'lib xizmat qiladi.
