# 🔐 Security Fundamentals

## Software Engineer → Senior Engineer → Architect uchun to'liq qo'llanma

> Security — bu faqat login va parol emas. Katta tizimlarda xavfsizlik Frontend, Backend, Database, Network, Infrastructure va Cloud darajalarida tashkil qilinadi.

---

# Mundarija

```txt
1. Security Fundamentals
2. CIA Triad
3. Authentication
4. Authorization
5. Password Security
6. Session Security
7. JWT Security
8. OAuth 2.0
9. OpenID Connect
10. Frontend Security
11. Backend Security
12. Database Security
13. API Security
14. Network Security
15. Infrastructure Security
16. OWASP Top 10
17. Security Headers
18. HTTPS & TLS
19. Rate Limiting
20. RBAC & ABAC
21. Audit Logs
22. Secrets Management
23. Cloud Security
24. Security Architecture
```

---

# 1. Security Fundamentals

Securityning asosiy maqsadi:

```txt
Confidentiality
Integrity
Availability
```

---

# 2. CIA Triad

Securityning eng muhim modeli.

---

## Confidentiality

Faqat ruxsat etilgan foydalanuvchilar ma'lumotni ko'ra olishi.

Misol:

```txt
Bank ma'lumotlari
Tibbiy ma'lumotlar
Passport ma'lumotlari
```

---

## Integrity

Ma'lumot o'zgarmagan bo'lishi kerak.

Misol:

```txt
Hisobda 1 000 000 so'm bor

Hacker:
10 000 000 ga o'zgartirdi
```

Integrity buzildi.

---

## Availability

Tizim doimo ishlashi kerak.

Misol:

```txt
Click
Payme
Telegram
```

24/7 ishlashi kerak.

---

# 3. Authentication

Kim ekanligini aniqlash.

---

## Misol

```txt
Login
Password
```

---

## Turlari

### Password

```txt
Username
Password
```

---

### OTP

```txt
SMS
Email
```

---

### Biometric

```txt
Face ID
Fingerprint
```

---

### MFA

Multi Factor Authentication

```txt
Password
+
SMS
```

---

# 4. Authorization

Nima qila olishini tekshirish.

---

Misol:

```txt
Admin
Manager
User
```

---

## Authentication

```txt
Kim?
```

---

## Authorization

```txt
Nima qila oladi?
```

---

# 5. Password Security

---

## Noto'g'ri

```txt
123456
qwerty
password
```

---

## To'g'ri

```txt
T8@xP!92#mK
```

---

## Password Hashing

Parol hech qachon databasega ochiq saqlanmaydi.

---

## Noto'g'ri

```txt
password123
```

---

## To'g'ri

```txt
$2b$10$...
```

---

## Algoritmlar

### BCrypt

Eng mashhur.

---

### Argon2

Eng xavfsiz.

---

### Scrypt

Kuchli.

---

## Ishlatmaslik kerak

```txt
MD5
SHA1
```

---

# 6. Session Security

---

## Session nima?

Serverda saqlanadigan foydalanuvchi holati.

---

```txt
User
 ↓
Session ID
 ↓
Server
```

---

## Session Hijacking

Hacker Session ID ni o'g'irlaydi.

---

## Himoya

```txt
HTTPS
Secure Cookie
HttpOnly
```

---

# 7. JWT Security

JSON Web Token.

---

## Tuzilishi

```txt
Header
Payload
Signature
```

---

## Misol

```txt
xxxxx.yyyyy.zzzzz
```

---

## Xavf

JWT o'g'irlanishi mumkin.

---

## Himoya

### Short Expiration

```txt
15 min
```

---

### Refresh Token

```txt
Access Token
Refresh Token
```

---

### Rotation

Har refreshda yangi token.

---

# 8. OAuth 2.0

Google Login.

GitHub Login.

Facebook Login.

---

## Flow

```txt
User
 ↓
Google
 ↓
Access Token
 ↓
Application
```

---

## Grant Types

### Authorization Code

Eng xavfsiz.

---

### Client Credentials

Server to Server.

---

# 9. OpenID Connect

OAuth ustiga qurilgan.

Identity beradi.

---

# 10. Frontend Security

---

# XSS

Cross Site Scripting

Eng mashhur hujum.

---

## Misol

```html
<script>
alert("Hacked")
</script>
```

---

## Xavf

```txt
Cookie Theft
Session Theft
```

---

## Himoya

### Escape HTML

### CSP

### React JSX

---

# CSRF

Cross Site Request Forgery

---

## Misol

User login bo'lib turibdi.

Hacker:

```html
<form action="/delete-user">
```

yuboradi.

---

## Himoya

```txt
CSRF Token
SameSite Cookie
```

---

# Clickjacking

---

## Misol

Invisible iframe.

---

## Himoya

```txt
X-Frame-Options
```

---

# 11. Backend Security

---

# SQL Injection

Eng xavfli hujumlardan biri.

---

## Noto'g'ri

```sql
SELECT * FROM users
WHERE username='$username'
```

---

## Hujum

```sql
' OR 1=1 --
```

---

## Himoya

```txt
Prepared Statements
ORM
Parameterized Queries
```

---

# Command Injection

---

## Misol

```bash
rm -rf /
```

---

# Himoya

Input Validation.

---

# SSRF

Server Side Request Forgery.

---

# 12. Database Security

---

## Encryption At Rest

Diskdagi ma'lumot shifrlanadi.

---

## Encryption In Transit

Trafik shifrlanadi.

---

## Backup Security

Backup ham shifrlanishi kerak.

---

# 13. API Security

---

## API Key

```txt
X-API-Key
```

---

## JWT

Bearer Authentication.

---

## Rate Limiting

Spam requestlardan himoya.

---

## Input Validation

Har doim tekshirish.

---

# 14. Network Security

---

## Firewall

Trafik filtri.

---

## VPN

Xavfsiz tunnel.

---

## IDS

Intrusion Detection System.

---

## IPS

Intrusion Prevention System.

---

# 15. HTTPS & TLS

---

## Muammo

HTTP ochiq.

---

## Yechim

HTTPS.

---

## TLS Handshake

```txt
Client
 ↓
Certificate
 ↓
Public Key
 ↓
Session Key
 ↓
Encrypted Traffic
```

---

# 16. OWASP Top 10

Har bir dasturchi bilishi kerak.

---

## Top Risklar

```txt
Broken Access Control
Cryptographic Failures
Injection
Insecure Design
Security Misconfiguration
Vulnerable Components
Authentication Failures
Integrity Failures
Logging Failures
SSRF
```

---

# 17. Security Headers

---

## CSP

Content Security Policy.

---

## X-Frame-Options

Clickjackingdan himoya.

---

## HSTS

Faqat HTTPS.

---

## X-Content-Type-Options

MIME hujumlardan himoya.

---

# 18. Rate Limiting

---

## Misol

```txt
100 request
per minute
```

---

## Himoya

```txt
Redis
Nginx
API Gateway
```

---

# 19. RBAC

Role Based Access Control.

---

```txt
Admin
Manager
User
```

---

## Misol

```txt
Admin
Create User

User
Read Only
```

---

# 20. ABAC

Attribute Based Access Control.

---

## Misol

```txt
Department
Position
Region
```

ga qarab ruxsat.

---

# 21. Audit Logs

Kim nima qilganini yozib borish.

---

## Misol

```txt
User:
Ali

Action:
Delete User

Date:
2026-06-22
```

---

# 22. Secrets Management

---

## Noto'g'ri

```js
const password = "123456"
```

---

## To'g'ri

```txt
.env
Vault
Secrets Manager
```

---

# 23. Cloud Security

---

## IAM

Identity Access Management.

---

## Bucket Security

S3 public bo'lmasligi kerak.

---

## Security Groups

Firewall.

---

# 24. Security Architecture

Enterprise tizim:

```txt
Internet
 ↓
WAF
 ↓
Load Balancer
 ↓
API Gateway
 ↓
Auth Service
 ↓
Application
 ↓
Database
```

---

# React Developer uchun

Bilishi shart:

✅ XSS

✅ CSRF

✅ JWT

✅ OAuth

✅ HTTPS

✅ CSP

✅ Secure Cookies

---

# Backend Developer uchun

Bilishi shart:

✅ SQL Injection

✅ SSRF

✅ Authentication

✅ Authorization

✅ JWT Rotation

✅ Rate Limiting

---

# System Architect uchun

Bilishi shart:

✅ OWASP Top 10

✅ RBAC

✅ ABAC

✅ Secrets Management

✅ Audit Logs

✅ Zero Trust

✅ Security Architecture

✅ Cloud Security

---

# Production Checklist

```txt
HTTPS
JWT Rotation
RBAC
Rate Limiting
CSP
Audit Logs
Encryption
Backup
WAF
Monitoring
```

---

# Yakuniy Maqsad

Ushbu bo'limni o'zlashtirgach siz:

✔ Frontend Security

✔ Backend Security

✔ API Security

✔ Database Security

✔ Cloud Security

✔ Enterprise Security Architecture

asoslarini professional darajada tushunadigan darajaga chiqasiz.
