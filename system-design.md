# 🏗️ System Design

## Software Engineer → System Architect → Solution Architect Roadmap

> System Design — millionlab foydalanuvchilar ishlatadigan tizimlarni loyihalash san'ati. Bu faqat kod yozish emas, balki tizimning scalability, reliability, performance, security va maintainability tomonlarini rejalashtirishdir.

---

# Mundarija

```txt
1. System Design Fundamentals
2. Requirements Gathering
3. Capacity Planning
4. Scalability
5. Availability
6. Reliability
7. Load Balancing
8. Reverse Proxy
9. Caching
10. Database Design
11. Replication
12. Sharding
13. Message Queues
14. Event Driven Architecture
15. API Gateway
16. Microservices
17. Service Discovery
18. Distributed Systems
19. CAP Theorem
20. Consistency Models
21. Distributed Transactions
22. CDN
23. Search Systems
24. Monitoring & Observability
25. Security Architecture
26. Real World System Design
```

---

# 1. SYSTEM DESIGN NIMA?

System Design — katta tizimlarni loyihalash jarayoni.

Masalan:

```txt
Telegram
Instagram
YouTube
Payme
Click
Uzum
Netflix
```

---

## System Design maqsadi

```txt
Scalability
Reliability
Availability
Performance
Security
Maintainability
```

---

# 2. REQUIREMENTS GATHERING

Har qanday dizayn:

```txt
Requirements
↓
Architecture
↓
Implementation
```

---

## Functional Requirements

Tizim nima qila oladi?

Misol:

```txt
User Registration
Login
Messaging
Payments
Notifications
```

---

## Non Functional Requirements

Tizim qanchalik yaxshi ishlaydi?

```txt
Performance
Scalability
Availability
Latency
Security
```

---

# 3. CAPACITY PLANNING

---

## Misol

1 million user.

---

### Daily Active Users

```txt
1 000 000
```

---

### Requests per Day

```txt
50 000 000
```

---

### Requests per Second

```txt
≈ 600 RPS
```

---

Shundan keyin:

```txt
Serverlar
Database
Redis
Storage
```

hisoblanadi.

---

# 4. SCALABILITY

Tizim o'sganda ishlashda davom etishi.

---

## Vertical Scaling

Server kuchaytiriladi.

```txt
CPU ↑
RAM ↑
Disk ↑
```

---

### Afzallik

Oson.

---

### Kamchilik

Chegara bor.

---

## Horizontal Scaling

Yangi serverlar qo'shiladi.

```txt
Server1
Server2
Server3
Server4
```

---

### Afzallik

Cheksiz o'sish mumkin.

---

### Kamchilik

Murakkab.

---

# 5. AVAILABILITY

Tizim ishlash foizi.

---

## 99%

```txt
3.65 kun downtime
```

---

## 99.9%

```txt
8.76 soat
```

---

## 99.99%

```txt
52 daqiqa
```

---

## 99.999%

```txt
5 daqiqa
```

---

# 6. RELIABILITY

Tizim ishonchliligi.

---

Misol:

```txt
Bank tizimi
```

Pul yo'qolmasligi kerak.

---

# 7. LOAD BALANCER

---

## Muammo

1 ta server.

```txt
Users
 ↓
Server
```

Server yiqiladi.

---

## Yechim

```txt
Users
 ↓
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

---

### Least Connections

Eng kam yuklangan.

---

### IP Hash

IP bo'yicha.

---

# 8. REVERSE PROXY

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

# 9. CACHING

Eng muhim System Design mavzularidan biri.

---

## Muammo

Har safar databasega murojaat.

---

## Yechim

```txt
User
 ↓
Redis
 ↓
Database
```

---

## Cache Aside

Eng mashhur pattern.

```txt
Request
 ↓
Cache
 ↓
Miss
 ↓
Database
 ↓
Cache
```

---

## Write Through

Cache va DB birga yoziladi.

---

## Write Back

Avval cache.

Keyin DB.

---

# 10. DATABASE DESIGN

---

## SQL

```txt
PostgreSQL
MySQL
```

---

## NoSQL

```txt
MongoDB
Redis
Cassandra
```

---

# SQL qachon?

```txt
Transactions
Relations
Consistency
```

---

# NoSQL qachon?

```txt
Massive Scale
Flexible Schema
```

---

# 11. REPLICATION

---

## Master Replica

```txt
Master
 ↓
Replica
 ↓
Replica
```

---

## Write

Master.

---

## Read

Replica.

---

# 12. SHARDING

Database bo'linadi.

---

## Misol

```txt
Shard 1
Users A-M

Shard 2
Users N-Z
```

---

## Nega?

Bitta database yetmay qoladi.

---

# 13. MESSAGE QUEUES

---

## Muammo

Email yuborish uzoq vaqt oladi.

---

## Yechim

```txt
User
 ↓
API
 ↓
Queue
 ↓
Worker
```

---

## Mashhur tizimlar

```txt
RabbitMQ
Kafka
SQS
```

---

# 14. EVENT DRIVEN ARCHITECTURE

---

## Misol

```txt
Order Created
 ↓
Event
 ↓
Email Service
 ↓
Notification Service
 ↓
Analytics Service
```

---

## Afzallik

Loose Coupling.

---

# 15. API GATEWAY

Microservices kirish nuqtasi.

---

```txt
Frontend
 ↓
API Gateway
 ↓
User Service
 ↓
Order Service
 ↓
Payment Service
```

---

## Vazifalari

* Authentication
* Rate Limiting
* Logging
* Routing

---

# 16. MICROSERVICES

---

## Monolith

```txt
Frontend
 ↓
Backend
 ↓
Database
```

---

## Microservices

```txt
User Service
Order Service
Payment Service
Notification Service
```

---

## Afzallik

Independent Deployment.

---

## Kamchilik

Murakkab.

---

# 17. SERVICE DISCOVERY

---

## Muammo

Servis IP o'zgaradi.

---

## Yechim

```txt
Consul
Eureka
Kubernetes DNS
```

---

# 18. DISTRIBUTED SYSTEMS

Bir nechta server ishlaydi.

---

## Muammolar

```txt
Network Failure
Latency
Consistency
Replication
```

---

# 19. CAP THEOREM

---

## Consistency

Hammasida bir xil data.

---

## Availability

Doim javob beradi.

---

## Partition Tolerance

Network muammolariga chidamli.

---

## Formula

```txt
C + A + P

faqat 2 tasi tanlanadi
```

---

# 20. CONSISTENCY MODELS

---

## Strong Consistency

Hammasi bir xil.

---

## Eventual Consistency

Bir oz vaqt o'tib tenglashadi.

---

Misollar:

```txt
Facebook Likes
Instagram Likes
```

---

# 21. DISTRIBUTED TRANSACTIONS

---

## Muammo

Order Service

Payment Service

Inventory Service

Bir transaction.

---

## Yechim

### Saga Pattern

```txt
Step1
Step2
Step3
```

Agar xato:

```txt
Rollback
```

---

# 22. CDN

Content Delivery Network.

---

## Misol

```txt
User (Tashkent)
 ↓
Nearest CDN
 ↓
Image
```

---

## Mashhur

```txt
Cloudflare
CloudFront
Akamai
```

---

# 23. SEARCH SYSTEMS

---

## Database qidiruvi

Yaxshi emas.

---

## Elasticsearch

```txt
Full Text Search
```

---

## Misollar

```txt
Google
Telegram Search
YouTube Search
```

---

# 24. MONITORING & OBSERVABILITY

---

## Metrics

```txt
CPU
RAM
Latency
Errors
```

---

## Monitoring

```txt
Prometheus
Grafana
```

---

## Logging

```txt
ELK
Loki
```

---

## Tracing

```txt
Jaeger
Zipkin
```

---

# 25. SECURITY ARCHITECTURE

---

## Layered Security

```txt
Internet
 ↓
WAF
 ↓
Load Balancer
 ↓
API Gateway
 ↓
Application
 ↓
Database
```

---

## Himoya

```txt
HTTPS
JWT
RBAC
Rate Limiting
Encryption
```

---

# 26. REAL WORLD SYSTEM DESIGN

---

# Telegram

```txt
Users
 ↓
Gateway
 ↓
Message Service
 ↓
Kafka
 ↓
Storage
```

---

# YouTube

```txt
Upload
 ↓
Queue
 ↓
Video Processing
 ↓
CDN
```

---

# Instagram

```txt
Upload
 ↓
Storage
 ↓
CDN
 ↓
Feed Service
```

---

# Uber

```txt
Drivers
 ↓
Location Service
 ↓
Matching Service
 ↓
Payments
```

---

# Payme

```txt
User
 ↓
Gateway
 ↓
Payment Service
 ↓
Transaction Service
 ↓
Audit Logs
```

---

# System Design Interview Framework

Har qanday tizim:

## 1

Requirements

---

## 2

Capacity Estimate

---

## 3

High Level Design

---

## 4

Database Design

---

## 5

API Design

---

## 6

Scaling

---

## 7

Caching

---

## 8

Security

---

## 9

Monitoring

---

# System Architect bilishi kerak

✅ Load Balancer

✅ Reverse Proxy

✅ Redis

✅ Database Scaling

✅ Replication

✅ Sharding

✅ Kafka

✅ RabbitMQ

✅ CDN

✅ API Gateway

✅ Microservices

✅ CAP Theorem

✅ Distributed Systems

✅ Monitoring

✅ Security Architecture

---

# Production Checklist

```txt
Load Balancer
Redis
Replication
Backups
Monitoring
Logging
HTTPS
CDN
Rate Limiting
WAF
```

---

# Yakuniy Maqsad

Ushbu bo'lim tugagach siz:

✔ Large Scale Systems

✔ Distributed Systems

✔ Caching

✔ Database Scaling

✔ Microservices

✔ Event Driven Architecture

✔ Security Architecture

✔ Production Infrastructure

✔ High Availability Systems

ni professional darajada tushunadigan bo'lasiz.

Bu bilimlar sizni Senior Engineer darajasidan System Architect va Solution Architect darajasiga olib chiqadi.
