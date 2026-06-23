# 🌐 Internet & Networking Fundamentals

## HTTP, HTTPS, TCP/IP, UDP, DNS, SSL/TLS

> Ushbu hujjat Frontend Developer, Backend Developer, DevOps Engineer, System Designer va Solution Architect bo'lish uchun zarur bo'lgan Internet va Networking asoslarini tushuntiradi.

---

# Mundarija

```txt
1. Internet qanday ishlaydi?
2. DNS
3. IP Address
4. TCP/IP
5. UDP
6. HTTP
7. HTTPS
8. SSL/TLS
9. Portlar
10. URL Browserga kiritilganda nima sodir bo'ladi?
11. TCP va UDP taqqoslash
12. HTTP va HTTPS taqqoslash
13. Frontend va Backend bilan bog'liqligi
```

---

# 1. INTERNET QANDAY ISHLAYDI?

Internet — dunyodagi millionlab qurilmalar va serverlarni bog'lab turuvchi global tarmoq.

Masalan:

```txt
Sizning Browser
        ↓
     Internet
        ↓
     Server
```

Siz browserga:

```txt
https://google.com
```

yozasiz.

Browser quyidagi ishlarni bajaradi:

```txt
1. DNS orqali IP topadi
2. Server bilan TCP ulanish ochadi
3. TLS Handshake qiladi
4. HTTPS Request yuboradi
5. Server javob qaytaradi
6. HTML, CSS, JS yuklanadi
7. Sahifa render qilinadi
```

---

# 2. DNS (Domain Name System)

DNS internetning telefon daftari hisoblanadi.

Odamlar:

```txt
google.com
facebook.com
youtube.com
```

eslab qoladi.

Kompyuter esa:

```txt
142.250.190.14
31.13.71.36
```

kabi IP manzillar bilan ishlaydi.

---

## DNS vazifasi

Domainni IP ga aylantiradi.

```txt
google.com
↓
DNS
↓
142.250.190.14
```

---

## DNS ishlash jarayoni

Browser:

```txt
google.com
```

ochganda:

```txt
Browser Cache
 ↓
OS Cache
 ↓
Router Cache
 ↓
DNS Resolver
 ↓
Root DNS
 ↓
.com DNS
 ↓
google.com DNS
 ↓
IP qaytadi
```

---

## DNS Record Turlari

### A Record

Domain → IPv4

```txt
example.com
↓
93.184.216.34
```

---

### AAAA Record

Domain → IPv6

---

### CNAME

Alias yaratadi.

```txt
api.example.com
↓
example.com
```

---

### MX

Email server.

---

### TXT

SPF

DKIM

Domain Verification

---

### NS

Nameserver.

---

## Mashhur DNS xizmatlari

### Google DNS

```txt
8.8.8.8
8.8.4.4
```

---

### Cloudflare DNS

```txt
1.1.1.1
1.0.0.1
```

---

# 3. IP ADDRESS

Internetdagi har bir qurilmaning manzili.

---

## IPv4

32 bit.

Misol:

```txt
192.168.1.10
```

---

### IPv4 Tuzilishi

```txt
192.168.1.10
```

4 qismdan iborat.

Har biri:

```txt
0-255
```

oralig'ida.

---

## IPv6

128 bit.

Misol:

```txt
2001:db8::ff00:42:8329
```

---

## Nega IPv6 kerak?

IPv4:

```txt
4.3 milliard
```

adres beradi.

Internet uchun yetarli emas.

---

# 4. TCP/IP

Internetning asosiy aloqa modeli.

---

## TCP/IP modeli

```txt
Application Layer
Transport Layer
Internet Layer
Network Layer
```

---

## IP vazifasi

Paket qayerga borishini aniqlaydi.

```txt
Client
 ↓
IP
 ↓
Server
```

---

## TCP vazifasi

Ma'lumotni ishonchli yetkazadi.

---

## TCP xususiyatlari

```txt
Reliable
Ordered
Connection Oriented
Error Checking
```

---

## TCP Three Way Handshake

Ulanish ochish jarayoni.

```txt
Client → SYN → Server

Client ← SYN-ACK ← Server

Client → ACK → Server
```

Shundan keyin aloqa boshlanadi.

---

## TCP afzalliklari

```txt
Paket yo'qolmaydi
Tartib saqlanadi
Xatolar tekshiriladi
```

---

## TCP kamchiliklari

```txt
Qo'shimcha tekshiruvlar sabab sekinroq
```

---

## TCP ishlatiladigan joylar

```txt
HTTP
HTTPS
SSH
FTP
SMTP
PostgreSQL
MySQL
```

---

# 5. UDP

User Datagram Protocol.

---

## UDP qanday ishlaydi?

TCP kabi ulanish ochmaydi.

```txt
Client
 ↓
Data
 ↓
Server
```

---

## UDP xususiyatlari

```txt
Connectionless
Fast
Low Latency
No Guarantee
```

---

## UDP nimani kafolatlamaydi?

```txt
Paket yetib borishini
Paket tartibini
Qayta yuborishni
```

---

## UDP ishlatiladigan joylar

### Online Games

```txt
PUBG
CS2
DOTA
```

---

### Video Streaming

```txt
YouTube Live
Twitch
```

---

### Voice Calls

```txt
Telegram Calls
Zoom
Google Meet
```

---

### DNS

DNS so'rovlari ham odatda UDP orqali ishlaydi.

---

# 6. HTTP

HyperText Transfer Protocol.

Browser va server o'rtasidagi aloqa tili.

---

## HTTP Lifecycle

```txt
Browser
 ↓
HTTP Request
 ↓
Server
 ↓
HTTP Response
 ↓
Browser
```

---

## HTTP Request

Tarkibi:

```txt
Method
URL
Headers
Body
```

---

## GET

Ma'lumot olish.

```http
GET /users
```

---

## POST

Ma'lumot yaratish.

```http
POST /users
```

---

## PUT

To'liq yangilash.

---

## PATCH

Qisman yangilash.

---

## DELETE

O'chirish.

---

## HTTP Status Codes

### 2xx

Muvaffaqiyat.

```txt
200 OK
201 Created
```

---

### 4xx

Client xatosi.

```txt
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

### 5xx

Server xatosi.

```txt
500 Internal Server Error
502 Bad Gateway
503 Service Unavailable
```

---

# 7. HTTPS

HTTPS = HTTP + TLS

---

## Muammo

HTTP ochiq ishlaydi.

```txt
Login
Password
Card Number
```

yo'lda o'qilishi mumkin.

---

## HTTPS yechimi

```txt
Encrypt
 ↓
Internet
 ↓
Decrypt
```

---

## HTTPS afzalliklari

### Confidentiality

Ma'lumot yashirin.

---

### Integrity

O'zgarmaganligi tekshiriladi.

---

### Authentication

Server haqiqiyligi tasdiqlanadi.

---

# 8. SSL/TLS

HTTPS ichidagi himoya qatlami.

---

## SSL

Eski texnologiya.

Bugungi kunda ishlatilmaydi.

---

## TLS

SSL ning zamonaviy versiyasi.

---

## TLS Handshake

```txt
Client
 ↓
Server Certificate
 ↓
Certificate Validation
 ↓
Key Exchange
 ↓
Session Key
 ↓
Encrypted Communication
```

---

## Certificate nima?

Server haqiqiyligini tasdiqlaydi.

---

Misol:

```txt
google.com
```

haqiqatan ham Google'ga tegishli ekanligini isbotlaydi.

---

## Certificate Authority

Mashhur CA lar:

```txt
Let's Encrypt
DigiCert
GlobalSign
Sectigo
```

---

# 9. PORTLAR

Bir serverda ko'plab servislar ishlaydi.

Portlar ularni ajratib turadi.

---

## Mashhur portlar

```txt
20   FTP Data
21   FTP
22   SSH
25   SMTP
53   DNS
80   HTTP
110  POP3
143  IMAP
443  HTTPS
3306 MySQL
5432 PostgreSQL
6379 Redis
27017 MongoDB
5672 RabbitMQ
9092 Kafka
```

---

# 10. URL KIRITILGANDA NIMA BO'LADI?

Misol:

```txt
https://google.com
```

---

## Jarayon

```txt
1. DNS Lookup
2. IP Topiladi
3. TCP Handshake
4. TLS Handshake
5. HTTPS Request
6. Server Response
7. HTML Parse
8. DOM Tree
9. CSSOM
10. Render Tree
11. Paint
12. Sahifa chiqadi
```

---

# 11. TCP vs UDP

| Xususiyat      | TCP         | UDP              |
| -------------- | ----------- | ---------------- |
| Tezlik         | Sekinroq    | Tezroq           |
| Reliability    | Yuqori      | Past             |
| Connection     | Bor         | Yo'q             |
| Packet Order   | Saqlanadi   | Kafolat yo'q     |
| Retransmission | Bor         | Yo'q             |
| Qo'llanish     | HTTP, HTTPS | Games, Streaming |

---

# 12. HTTP vs HTTPS

| Xususiyat   | HTTP              | HTTPS    |
| ----------- | ----------------- | -------- |
| Port        | 80                | 443      |
| Encryption  | Yo'q              | Bor      |
| Security    | Past              | Yuqori   |
| Login uchun | Xavfli            | To'g'ri  |
| Production  | Tavsiya etilmaydi | Majburiy |

---

# 13. FRONTEND BILAN BOG'LIQLIGI

React komponent:

```ts
fetch("https://api.example.com/users")
```

Aslida quyidagilar sodir bo'ladi:

```txt
DNS
↓
TCP
↓
TLS
↓
HTTPS
↓
JSON
```

---

## Frontend Developer bilishi kerak

### Networking

```txt
DNS
TCP/IP
HTTP
HTTPS
TLS
```

---

### Browser

```txt
DOM
CSSOM
Render Tree
Reflow
Repaint
```

---

### Security

```txt
HTTPS
JWT
Cookies
CORS
CSRF
XSS
```

---

# Xulosa

Internetning ishlash zanjiri:

```txt
DNS
↓
IP
↓
TCP
↓
TLS
↓
HTTPS
↓
Browser Render
```

Qisqa eslab qolish:

```txt
DNS     → Domainni IP ga aylantiradi
IP      → Qurilma manzili
TCP     → Ishonchli aloqa
UDP     → Tez aloqa
HTTP    → Browser va server tili
HTTPS   → Xavfsiz HTTP
TLS     → Shifrlash mexanizmi
```

Ushbu mavzularni mukammal tushungan dasturchi keyingi bosqichdagi:

* REST API
* GraphQL
* WebSocket
* OAuth 2.0
* JWT
* Browser Internals
* System Design
* Microservices Architecture

mavzularini ancha oson o'zlashtiradi.
