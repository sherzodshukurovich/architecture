# 🗄️ Database Design

## Software Engineer → Database Engineer → System Architect Roadmap

> Database Design — bu ma'lumotlarni saqlash, boshqarish, qidirish va millionlab foydalanuvchilarga xizmat ko'rsatadigan tizimlarni loyihalash san'atidir.

---

# Mundarija

```txt
1. Database Fundamentals
2. Relational Databases
3. Database Design Process
4. ER Modeling
5. Keys
6. Relationships
7. Normalization
8. Denormalization
9. Indexing
10. Query Optimization
11. Transactions
12. ACID
13. Isolation Levels
14. Locks
15. Database Architecture
16. Replication
17. Partitioning
18. Sharding
19. NoSQL
20. Redis
21. Caching
22. Database Security
23. Backup & Recovery
24. High Availability
25. Database Design Patterns
26. Real World Database Design
```

---

# 1. DATABASE FUNDAMENTALS

## Database nima?

Database — ma'lumotlarni saqlovchi tizim.

Misol:

```txt
Userlar
Mahsulotlar
Buyurtmalar
To'lovlar
Hujjatlar
```

---

## Database Management System

DBMS.

Misollar:

```txt
PostgreSQL
MySQL
Oracle
SQL Server
MongoDB
Redis
```

---

## Nega Database kerak?

Faylga yozish:

```txt
users.txt
orders.txt
```

katta tizimlarda ishlamaydi.

Database:

* Tez qidiradi
* Xavfsiz
* Concurrent ishlaydi
* Backup qo'llab-quvvatlaydi

---

# 2. RELATIONAL DATABASE

Eng mashhur database turi.

---

## Asosiy tushuncha

Data:

```txt
Table
 ↓
Rows
 ↓
Columns
```

---

## Misol

Users Table

| id | name | email                                 |
| -- | ---- | ------------------------------------- |
| 1  | Ali  | [ali@mail.com](mailto:ali@mail.com)   |
| 2  | Vali | [vali@mail.com](mailto:vali@mail.com) |

---

## SQL

Structured Query Language.

---

## CREATE

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255)
);
```

---

## INSERT

```sql
INSERT INTO users(name,email)
VALUES('Ali','ali@mail.com');
```

---

## SELECT

```sql
SELECT * FROM users;
```

---

## UPDATE

```sql
UPDATE users
SET name='Vali'
WHERE id=1;
```

---

## DELETE

```sql
DELETE FROM users
WHERE id=1;
```

---

# 3. DATABASE DESIGN PROCESS

Har qanday database dizayni:

```txt
Requirements
 ↓
Entities
 ↓
Relationships
 ↓
Normalization
 ↓
Indexes
 ↓
Optimization
```

---

## Misol

Online Shop.

---

### Entities

```txt
User
Product
Order
Category
Payment
```

---

# 4. ER MODELING

Entity Relationship Diagram.

---

## Entity

Obyekt.

```txt
User
Product
Order
```

---

## Attribute

Entity xususiyatlari.

```txt
User
 ├ id
 ├ name
 ├ email
```

---

## ER Diagram

```txt
User
 ↓
Order
 ↓
Product
```

---

# 5. KEYS

Database yuragi.

---

## Primary Key

Har qator uchun unique.

```sql
id SERIAL PRIMARY KEY
```

---

## Foreign Key

Bog'lanish.

```sql
user_id
```

---

## Candidate Key

Primary bo'lishi mumkin bo'lgan key.

---

## Composite Key

Bir nechta ustundan.

```txt
user_id
product_id
```

---

# 6. RELATIONSHIPS

---

## One To One

```txt
User
 ↓
Passport
```

---

## One To Many

```txt
User
 ↓
Orders
```

---

## Many To Many

```txt
Students
 ↓
Courses
```

---

## Junction Table

```txt
student_courses
```

---

# 7. NORMALIZATION

Takror ma'lumotlarni kamaytiradi.

---

## 1NF

Har ustun atomik.

❌

```txt
Ali,Vali
```

✅

```txt
Ali
Vali
```

---

## 2NF

Partial dependency bo'lmasligi kerak.

---

## 3NF

Transitive dependency bo'lmasligi kerak.

---

## BCNF

3NF ning kuchliroq versiyasi.

---

# Nima uchun kerak?

```txt
Data Integrity
Less Duplication
Easy Maintenance
```

---

# 8. DENORMALIZATION

Performance uchun.

---

## Misol

Normal:

```txt
Orders
Users
Products
```

---

Denormalized:

```txt
Orders
user_name
product_name
```

---

## Afzallik

Tezroq.

---

## Kamchilik

Takror data.

---

# 9. INDEXING

Database performance yuragi.

---

## Muammo

1 million user.

```sql
SELECT * FROM users
WHERE email='test@mail.com'
```

---

## Indexsiz

```txt
Full Table Scan
```

O(n)

---

## Index bilan

```txt
B Tree Search
```

O(log n)

---

## Index Types

### B-Tree

Default.

---

### Hash Index

Exact Search.

---

### GIN

JSONB.

Full Text Search.

---

### GiST

Geospatial.

---

# 10. QUERY OPTIMIZATION

---

## EXPLAIN

```sql
EXPLAIN ANALYZE
SELECT * FROM users;
```

---

## Muammolar

* Missing Index
* N+1 Queries
* Full Table Scan

---

# 11. TRANSACTIONS

Bir nechta operation bitta blok.

---

## Misol

Bank o'tkazmasi.

```txt
Ali → Vali
```

---

## Jarayon

```txt
Debit
Credit
```

---

## Transaction

Hammasi ishlaydi yoki hammasi bekor.

---

# 12. ACID

---

## Atomicity

Hammasi yoki hech narsa.

---

## Consistency

Database qoidalari buzilmaydi.

---

## Isolation

Transactionlar bir-biriga xalaqit bermaydi.

---

## Durability

Saqlangan data yo'qolmaydi.

---

# 13. ISOLATION LEVELS

---

## Read Uncommitted

Eng xavfli.

---

## Read Committed

Default.

---

## Repeatable Read

Barqaror.

---

## Serializable

Eng xavfsiz.

---

# 14. LOCKS

---

## Pessimistic Lock

Oldindan bloklaydi.

---

## Optimistic Lock

Version bilan ishlaydi.

---

# 15. DATABASE ARCHITECTURE

```txt
Application
 ↓
Database Server
 ↓
Storage
```

---

# 16. REPLICATION

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

# 17. PARTITIONING

Bitta katta table bo'linadi.

---

## Misol

```txt
orders_2024
orders_2025
orders_2026
```

---

# 18. SHARDING

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

## Nima uchun?

Millionlab userlar.

---

# 19. NoSQL

Schema-less.

---

## MongoDB

Document.

```json
{
  "name":"Ali"
}
```

---

## Cassandra

Distributed.

---

## DynamoDB

AWS.

---

# SQL vs NoSQL

## SQL

```txt
Strong Consistency
Relations
ACID
```

---

## NoSQL

```txt
Flexible
Fast Scaling
```

---

# 20. REDIS

In-memory database.

---

## Nega ishlatiladi?

```txt
Cache
Session
Queue
Rate Limiting
```

---

## Data Types

```txt
String
Hash
List
Set
Sorted Set
```

---

# 21. CACHING

---

## Muammo

Database yuklanadi.

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

## Cache Aside Pattern

Eng mashhur.

---

# 22. DATABASE SECURITY

---

## Encryption At Rest

Diskdagi data.

---

## Encryption In Transit

HTTPS/TLS.

---

## Row Level Security

User faqat o'z datasini ko'radi.

---

# 23. BACKUP & RECOVERY

---

## Full Backup

Hammasi.

---

## Incremental Backup

Faqat o'zgarganlar.

---

## Point In Time Recovery

Ma'lum vaqtga qaytish.

---

# 24. HIGH AVAILABILITY

---

## Muammo

Database o'chib qoldi.

---

## Yechim

```txt
Primary
 ↓
Replica
 ↓
Failover
```

---

# 25. DATABASE DESIGN PATTERNS

---

## Soft Delete

```sql
deleted_at
```

---

## Audit Trail

Kim nima qildi.

---

## Versioning

Hujjat tarixini saqlash.

---

## Multi Tenant

Bir database.

Ko'p kompaniya.

---

# 26. REAL WORLD DATABASE DESIGN

---

# HR System

```txt
Users
Roles
Departments
Employees
Positions
```

---

# E-Commerce

```txt
Users
Products
Categories
Orders
Payments
```

---

# Hospital System

```txt
Patients
Doctors
Appointments
Prescriptions
```

---

# Document Management System

```txt
Users
Roles
Documents
Templates
Versions
Files
Audit Logs
```

---

# Telegram

```txt
Users
Chats
Messages
Media
Groups
```

---

# System Architect bilishi kerak

✅ ER Modeling

✅ Normalization

✅ Denormalization

✅ Indexing

✅ Query Optimization

✅ Transactions

✅ ACID

✅ Isolation Levels

✅ Replication

✅ Sharding

✅ Redis

✅ Caching

✅ Backup

✅ High Availability

---

# Production Checklist

```txt
Primary Key
Foreign Keys
Indexes
Transactions
Redis
Replication
Backups
Monitoring
Encryption
Audit Logs
```

---

# Yakuniy Maqsad

Ushbu bo'limni tugatgach siz:

✔ Database Design

✔ PostgreSQL

✔ MySQL

✔ Redis

✔ Query Optimization

✔ Database Scaling

✔ High Availability

✔ Distributed Databases

✔ Enterprise Database Architecture

ni professional darajada tushunadigan bo'lasiz.

Bu bilimlar Backend Architecture, System Design va Solution Architecture uchun poydevor hisoblanadi.
