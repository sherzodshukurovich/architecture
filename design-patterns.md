
# 🎯 Design Patterns

## Software Engineer → Senior Engineer → Architect uchun to'liq qo'llanma

> Design Pattern — dasturiy ta'minotda qayta-qayta uchraydigan muammolar uchun sinovdan o'tgan yechimdir.

---

# Mundarija

```txt
1. Design Pattern nima?
2. Nima uchun kerak?
3. SOLID va Design Patterns
4. GoF (Gang Of Four)
5. Creational Patterns
6. Structural Patterns
7. Behavioral Patterns
8. Enterprise Patterns
9. Frontend Patterns
10. Backend Patterns
11. Microservice Patterns
12. Pattern Selection Guide
```

---

# Design Pattern nima?

Pattern bu tayyor kod emas.

Pattern bu:

```txt
Muammo
↓
Takrorlanuvchi vaziyat
↓
Sinovdan o'tgan yechim
```

Misol:

Siz 100 ta joyda object yaratmoqchisiz.

Har safar:

```js
new User()
```

qilish o'rniga Factory Pattern ishlatiladi.

---

# Nima uchun kerak?

Design Patterns:

* Kodni soddalashtiradi
* Reusability oshiradi
* Test qilishni osonlashtiradi
* Scalability beradi
* Maintenance osonlashadi

---

# GoF (Gang Of Four)

1994 yilda chiqarilgan mashhur kitob.

23 ta pattern mavjud.

---

## 3 ta katta guruh

```txt
Creational
Structural
Behavioral
```

---

# CREATIONAL PATTERNS

Object yaratish bilan shug'ullanadi.

---

# 1. Singleton Pattern

## Maqsad

Application davomida faqat bitta instance yaratish.

---

## Muammo

```js
const db1 = new Database()
const db2 = new Database()
```

Ko'p object yaralmoqda.

---

## Yechim

```txt
Application
↓
Single Instance
↓
Reuse
```

---

## Misollar

* Redux Store
* Zustand Store
* Logger
* Config Service

---

## Afzalliklari

* Memory tejaydi

---

## Kamchiliklari

* Global State hosil qiladi

---

# 2. Factory Pattern

## Maqsad

Object yaratishni markazlashtirish.

---

## Muammo

```js
new Admin()
new User()
new Manager()
```

---

## Yechim

```txt
Factory
 ↓
Admin
User
Manager
```

---

## React misoli

```txt
FieldFactory
 ↓
Input
Select
Checkbox
```

---

## Real loyihalar

Dynamic Form Builder

---

# 3. Abstract Factory

Bir nechta Factorylarni boshqaradi.

---

## Misol

```txt
UI Factory
 ↓
Dark Theme Factory
Light Theme Factory
```

---

# 4. Builder Pattern

Murakkab objectlarni bosqichma-bosqich yaratadi.

---

## Muammo

```js
new User(
  name,
  email,
  phone,
  role,
  address
)
```

---

## Yechim

```txt
Builder
 ↓
SetName()
 ↓
SetEmail()
 ↓
Build()
```

---

## Misol

Axios Config Builder

---

# 5. Prototype Pattern

Mavjud objectdan nusxa olish.

---

## Misol

```js
const copy = {...user}
```

---

# STRUCTURAL PATTERNS

Objectlar o'rtasidagi bog'lanishni tashkil qiladi.

---

# 6. Adapter Pattern

Mos kelmaydigan interfeyslarni moslashtiradi.

---

## Muammo

Backend:

```json
{
  "first_name":"Ali"
}
```

Frontend:

```js
user.name
```

kutmoqda.

---

## Yechim

```txt
API
↓
Adapter
↓
UI
```

---

## React misoli

```txt
UserAdapter
```

---

# 7. Facade Pattern

Murakkab tizimni soddalashtirish.

---

## Muammo

```txt
Auth API
User API
Role API
```

---

## Yechim

```txt
UserService
 ↓
All APIs
```

---

## Real misol

```ts
AuthService.login()
```

---

# 8. Decorator Pattern

Objectga yangi imkoniyat qo'shadi.

---

## Misol

```txt
Button
↓
LoadingButton
↓
PermissionButton
```

---

## React

Higher Order Components.

---

# 9. Proxy Pattern

Asl objectga vositachi.

---

## Misollar

* Cache
* Authentication
* API Gateway

---

# 10. Composite Pattern

Tree struktura.

---

## Misol

```txt
Folder
 ├── File
 ├── File
 └── Folder
```

---

# 11. Bridge Pattern

Abstraction va Implementationni ajratadi.

---

# 12. Flyweight Pattern

Memory tejash uchun.

---

## Misol

1000 ta marker.

Bitta style.

---

# BEHAVIORAL PATTERNS

Objectlarning o'zaro ishlashi.

---

# 13. Observer Pattern

Eng muhim patternlardan biri.

---

## Misol

```txt
Store
 ↓
Subscribers
```

---

## React

```txt
Redux
Zustand
React Query
```

hammasi Observer ishlatadi.

---

# 14. Strategy Pattern

Algoritmni runtime almashtirish.

---

## Misol

```txt
Payment
 ↓
Click
Payme
Stripe
```

---

## React

Validation Strategy.

---

# 15. Command Pattern

Buyruqni object sifatida saqlaydi.

---

## Misol

Undo / Redo.

---

# 16. State Pattern

Statega qarab xatti-harakat o'zgaradi.

---

## Misol

```txt
Draft
Approved
Rejected
```

---

# 17. Chain Of Responsibility

Bir nechta handler ketma-ket ishlaydi.

---

## Misol

```txt
Request
 ↓
Auth
 ↓
Role
 ↓
Validation
```

---

# 18. Mediator Pattern

Objectlar to'g'ridan-to'g'ri emas, markaz orqali gaplashadi.

---

## Misol

Event Bus.

---

# 19. Iterator Pattern

Collection bo'ylab yurish.

---

## Misol

```js
forEach()
map()
filter()
```

---

# 20. Visitor Pattern

Objectlarni o'zgartirmasdan yangi operatsiya qo'shish.

---

# ENTERPRISE PATTERNS

---

# 21. Repository Pattern

Database yoki API bilan ishlashni abstraktsiya qiladi.

---

## Muammo

Component:

```txt
Axios
```

chaqirmoqda.

---

## Yechim

```txt
Component
 ↓
Repository
 ↓
API
```

---

## React

```txt
UserRepository
```

---

# 22. Service Pattern

Business Logic markazi.

---

## Misol

```txt
UserService
OrderService
```

---

# 23. Dependency Injection

Dependency tashqaridan beriladi.

---

## Muammo

```txt
UserService
 ↓
new Api()
```

---

## Yechim

```txt
Api
 ↓
Inject
 ↓
UserService
```

---

# 24. Unit Of Work

Bir nechta operationni transaction sifatida bajaradi.

---

# 25. Specification Pattern

Murakkab filterlarni birlashtiradi.

---

# FRONTEND PATTERNS

React uchun eng muhimlari.

---

## Container Pattern

```txt
Container
 ↓
Presentational
```

---

## Compound Component

```txt
Modal
 ├ Header
 ├ Body
 └ Footer
```

---

## Custom Hook Pattern

```txt
useUsers()
useAuth()
```

---

## Provider Pattern

```txt
ThemeProvider
AuthProvider
```

---

## Render Props

Komponentga funksiyani prop sifatida berish.

---

# BACKEND PATTERNS

---

## CQRS

```txt
Write
↓
Command

Read
↓
Query
```

---

## Event Sourcing

```txt
Events
 ↓
State
```

---

## Saga Pattern

Microservice transactionlari.

---

# MICROSERVICE PATTERNS

---

## API Gateway

```txt
Frontend
 ↓
Gateway
 ↓
Services
```

---

## Circuit Breaker

Xato servislardan himoya.

---

## Retry Pattern

Qayta urinish.

---

## Bulkhead Pattern

Izolyatsiya.

---

## Service Discovery

Servislarni topish.

---

# React Developer uchun eng muhim Patternlar

## Top Priority

```txt
Singleton
Factory
Adapter
Facade
Observer
Strategy
Repository
Service
Dependency Injection
```

---

# Frontend Architect uchun

```txt
MVVM
Repository
Service
Observer
Adapter
Facade
Factory
CQRS
DDD
```

---

# System Architect uchun

```txt
CQRS
Event Sourcing
Saga
Circuit Breaker
Repository
Unit Of Work
Specification
```

---

# O'rganish ketma-ketligi

1. Singleton
2. Factory
3. Adapter
4. Facade
5. Observer
6. Strategy
7. Repository
8. Service
9. Dependency Injection
10. MVVM
11. CQRS
12. Event Sourcing
13. Saga

---

# Yakuniy Maqsad

Agar siz:

✅ Factory

✅ Adapter

✅ Facade

✅ Observer

✅ Strategy

✅ Repository

✅ Service

✅ Dependency Injection

✅ MVVM

✅ CQRS

ni chuqur tushunsangiz, Senior Frontend Engineer darajasiga chiqasiz.

Agar ularga qo'shimcha ravishda:

✅ DDD

✅ Event Sourcing

✅ Saga

✅ Microservice Patterns

ni ham tushunsangiz, System Architect yoki Solution Architect yo'liga o'tasiz.
