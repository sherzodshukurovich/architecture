# 🏛 Architecture Patterns
## Frontend Architect, Backend Engineer, System Designer va Solution Architect uchun batafsil qo‘llanma

> Architecture Pattern — bu dastur yoki tizimni qanday qismlarga bo‘lish, u qismlar bir-biri bilan qanday gaplashishi va biznes logika qayerda joylashishini belgilab beradigan umumiy arxitektura yechimidir.

---

# Mundarija

```txt
1. Architecture Pattern nima?
2. Nima uchun Architecture Pattern kerak?
3. MVC — Model View Controller
4. MVT — Model View Template
5. MVP — Model View Presenter
6. MVVM — Model View ViewModel
7. Layered Architecture
8. Clean Architecture
9. Hexagonal Architecture
10. Onion Architecture
11. Feature-Sliced Design
12. Component-Based Architecture
13. Monolithic Architecture
14. Modular Monolith
15. Microservices Architecture
16. Event-Driven Architecture
17. Serverless Architecture
18. CQRS
19. Event Sourcing
20. DDD — Domain Driven Design
21. Architecture Patternlarni solishtirish
22. Qaysi holatda qaysi pattern ishlatiladi?
23. Amaliy loyiha structure namunalari
24. Interview savollari
25. O‘rganish roadmap
```

---

# 1. Architecture Pattern nima?

Architecture Pattern — katta dasturiy tizimlarni tartibli, tushunarli, kengaytiriladigan va test qilinadigan holatda qurish uchun ishlatiladigan umumiy yechim.

Oddiy qilib aytganda, architecture pattern quyidagi savollarga javob beradi:

```txt
Kod qayerda turadi?
Business logic qayerda bo‘ladi?
UI qayerda bo‘ladi?
Database bilan kim ishlaydi?
API chaqiruvlar qayerda yoziladi?
State qayerda saqlanadi?
Modullar bir-biri bilan qanday gaplashadi?
Tizim katta bo‘lsa, uni qanday boshqaramiz?
```

Architecture Pattern faqat folder structure emas. U butun tizimning fikrlash modeli hisoblanadi.

---

# 2. Nima uchun Architecture Pattern kerak?

Kichik loyiha uchun hamma kodni bitta joyga yozish mumkin. Lekin loyiha kattalashgani sari muammolar chiqadi:

```txt
component ichida API chaqiriladi
component ichida business logic yoziladi
validatsiya har joyda takrorlanadi
state chalkashib ketadi
bir joyni o‘zgartirsangiz boshqa joy buziladi
kod test qilish qiyinlashadi
junior developer kodni tushunolmaydi
loyiha sekin rivojlanadi
```

Architecture Pattern quyidagilarni beradi:

```txt
Tartib
Mas'uliyatni ajratish
Test qilish osonligi
Kengaytirish imkoniyati
Kod qayta ishlatish imkoniyati
Texnik qarz kamayishi
Jamoada ishlash qulayligi
```

---

# 3. MVC — Model View Controller

## MVC nima?

MVC — eng mashhur arxitektura patternlardan biri. U dastur logikasini 3 qismga ajratadi:

```txt
Model
View
Controller
```

Diagramma:

```txt
User
 ↓
Controller
 ↓
Model
 ↓
Database
 ↓
Controller
 ↓
View
 ↓
User
```

---

## Model

Model — ma'lumotlar va business logic bilan ishlaydi.

Model vazifalari:

```txt
Database bilan ishlash
Data validation
Business rules
Entity logic
Relationshiplar
```

Misol:

```python
class User(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField(unique=True)
```

Bu yerda User — Model.

---

## View

View — foydalanuvchiga ko‘rinadigan qism.

View vazifalari:

```txt
HTML chiqarish
UI ko‘rsatish
Data render qilish
Userga natija ko‘rsatish
```

Misol:

```html
<h1>{{ user.name }}</h1>
<p>{{ user.email }}</p>
```

---

## Controller

Controller — Model va View orasidagi vositachi.

Controller vazifalari:

```txt
Request qabul qiladi
Kerakli Modelni chaqiradi
Natijani Viewga uzatadi
Response qaytaradi
```

Misol:

```php
class UserController {
    public function show($id) {
        $user = User::find($id);
        return view('user.show', ['user' => $user]);
    }
}
```

---

## MVC qachon ishlatiladi?

MVC ko‘p ishlatiladigan joylar:

```txt
Laravel
ASP.NET MVC
Spring MVC
Ruby on Rails
Express.js MVC style
```

---

## MVC afzalliklari

```txt
Kod tartibli bo‘ladi
UI va business logic ajraladi
Katta web app uchun qulay
Jamoada ishlash osonlashadi
Test qilish osonlashadi
```

---

## MVC kamchiliklari

```txt
Kichik loyiha uchun ortiqcha murakkab bo‘lishi mumkin
Controller juda kattalashib ketishi mumkin
Modelda juda ko‘p logic yig‘ilib qolishi mumkin
```

Bunday holatlarda Service Layer qo‘shiladi.

---

# 4. MVT — Model View Template

## MVT nima?

MVT — Django frameworkida ishlatiladigan architecture pattern.

U 3 qismdan iborat:

```txt
Model
View
Template
```

Diagramma:

```txt
User
 ↓
URL Router
 ↓
View
 ↓
Model
 ↓
Database
 ↓
View
 ↓
Template
 ↓
User
```

---

## Model

Model database structure va data bilan ishlaydi.

```python
from django.db import models

class Product(models.Model):
    name = models.CharField(max_length=255)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    created_at = models.DateTimeField(auto_now_add=True)
```

Bu Product jadvalini ifodalaydi.

---

## View

Djangoda View odatda Controllerga o‘xshash vazifa bajaradi.

View vazifalari:

```txt
Requestni qabul qiladi
Modeldan data oladi
Templatega data yuboradi
Response qaytaradi
```

```python
from django.shortcuts import render
from .models import Product

def product_list(request):
    products = Product.objects.all()
    return render(request, 'products/list.html', {
        'products': products
    })
```

---

## Template

Template — HTML ko‘rinish.

```html
<h1>Products</h1>

{% for product in products %}
  <div>
    <h3>{{ product.name }}</h3>
    <p>{{ product.price }}</p>
  </div>
{% endfor %}
```

---

## MVC va MVT farqi

```txt
MVC:
Controller requestni boshqaradi
View UI chiqaradi

MVT:
View requestni boshqaradi
Template UI chiqaradi
```

Django ichida Controller vazifasining katta qismini framework o‘zi bajaradi.

---

## MVT qachon ishlatiladi?

```txt
Django web apps
Admin panels
CRM systems
ERP systems
Content management systems
```

---

## MVT afzalliklari

```txt
Tez development
Django ORM bilan kuchli integratsiya
Admin panel tayyor
Security yaxshi
Template system qulay
```

---

## MVT kamchiliklari

```txt
Frontend murakkab bo‘lsa, template yetarli bo‘lmasligi mumkin
React/Vue bilan ishlaganda API-first yondashuv kerak bo‘ladi
Katta tizimda Viewlar semirib ketishi mumkin
```

---

# 5. MVP — Model View Presenter

## MVP nima?

MVP — UI va business logicni ajratish uchun ishlatiladigan pattern.

```txt
Model
View
Presenter
```

Diagramma:

```txt
User
 ↓
View
 ↓
Presenter
 ↓
Model
 ↓
Presenter
 ↓
View
```

---

## Model

Model data va business logic bilan ishlaydi.

```txt
API
Database
Repository
Entity
```

---

## View

View faqat UI ko‘rsatadi.

View ichida business logic bo‘lmasligi kerak.

View vazifalari:

```txt
Button chiqarish
Input chiqarish
Loading ko‘rsatish
Error ko‘rsatish
Presenterga user action yuborish
```

---

## Presenter

Presenter asosiy logikani boshqaradi.

Presenter vazifalari:

```txt
Viewdan event oladi
Modelni chaqiradi
Natijani qayta ishlab Viewga beradi
```

---

## MVP misol

Login jarayoni:

```txt
User email/password yozadi
View submit eventni Presenterga yuboradi
Presenter AuthRepository.login() chaqiradi
Model API bilan ishlaydi
Presenter natijaga qarab Viewga loading/error/success beradi
```

---

## MVP qachon ishlatiladi?

```txt
Android eski arxitekturasi
Desktop applications
UI logic ko‘p bo‘lgan tizimlar
Test qilish muhim bo‘lgan loyihalar
```

---

## MVP afzalliklari

```txt
View juda yengil bo‘ladi
Business logic test qilish oson
UI almashtirish oson
Kod mas'uliyati aniq bo‘ladi
```

---

## MVP kamchiliklari

```txt
Presenterlar ko‘payib ketadi
Boilerplate ko‘p bo‘ladi
Kichik loyiha uchun og‘ir bo‘lishi mumkin
```

---

# 6. MVVM — Model View ViewModel

## MVVM nima?

MVVM zamonaviy frontend va mobile arxitekturalarda juda ko‘p ishlatiladi.

```txt
Model
View
ViewModel
```

Diagramma:

```txt
View
 ↕
ViewModel
 ↕
Model
```

---

## Model

Model — data manbai.

```txt
API response
Database entity
Domain object
DTO
```

---

## View

View — UI.

Reactda View:

```tsx
function UserListView({ users }) {
  return (
    <div>
      {users.map(user => (
        <p key={user.id}>{user.name}</p>
      ))}
    </div>
  );
}
```

---

## ViewModel

ViewModel — View uchun tayyorlangan state va logic.

Reactda custom hook ko‘pincha ViewModel vazifasini bajaradi.

```tsx
function useUsersViewModel() {
  const { data, isLoading, error } = useQuery({
    queryKey: ['users'],
    queryFn: getUsers,
  });

  return {
    users: data ?? [],
    isLoading,
    error,
  };
}
```

View:

```tsx
function UsersPage() {
  const { users, isLoading, error } = useUsersViewModel();

  if (isLoading) return <p>Loading...</p>;
  if (error) return <p>Error</p>;

  return <UserListView users={users} />;
}
```

---

## MVVM qachon ishlatiladi?

```txt
React
Vue
Angular
SwiftUI
WPF
Android Architecture Components
```

---

## MVVM afzalliklari

```txt
UI va logic ajraladi
Custom hooklar orqali tartib yaxshi bo‘ladi
Testing osonlashadi
State boshqarish aniq bo‘ladi
```

---

## MVVM kamchiliklari

```txt
ViewModel juda kattalashib ketishi mumkin
Business logic noto‘g‘ri joyga yozilishi mumkin
Kichik componentlarda ortiqcha abstraction bo‘lishi mumkin
```

---

# 7. Layered Architecture

## Layered Architecture nima?

Layered Architecture — dastur kodini qatlamlarga bo‘lish usuli.

Eng ko‘p ishlatiladigan structure:

```txt
Presentation Layer
Application Layer
Domain Layer
Infrastructure Layer
```

yoki oddiyroq:

```txt
Controller
Service
Repository
Database
```

---

## Web app diagrammasi

```txt
Client
 ↓
Controller
 ↓
Service
 ↓
Repository
 ↓
Database
```

---

## Presentation Layer

Foydalanuvchi yoki tashqi tizim bilan aloqa qiladi.

Misollar:

```txt
React component
REST Controller
GraphQL Resolver
CLI command
```

---

## Service Layer

Business logic shu yerda bo‘ladi.

Misol:

```ts
class OrderService {
  async createOrder(dto: CreateOrderDto) {
    const user = await this.userRepository.findById(dto.userId);

    if (!user) {
      throw new Error('User not found');
    }

    const order = Order.create(dto);
    return this.orderRepository.save(order);
  }
}
```

---

## Repository Layer

Database bilan ishlaydi.

```ts
class UserRepository {
  async findById(id: string) {
    return db.user.findUnique({ where: { id } });
  }
}
```

---

## Layered Architecture afzalliklari

```txt
Tushunish oson
Jamoa uchun qulay
Ko‘p frameworklar shu yondashuvda
Test qilish osonroq
Mas'uliyat ajraladi
```

---

## Kamchiliklari

```txt
Layerlar orasida ortiqcha mapping ko‘payadi
Kichik app uchun og‘ir bo‘lishi mumkin
Noto‘g‘ri ishlatilsa Service layer semirib ketadi
```

---

# 8. Clean Architecture

## Clean Architecture nima?

Clean Architecture — biznes logikani framework, database va UI'dan mustaqil qilishga qaratilgan pattern.

Asosiy g‘oya:

```txt
Business logic tashqi texnologiyalarga bog‘liq bo‘lmasin.
```

Diagramma:

```txt
Frameworks & Drivers
        ↓
Interface Adapters
        ↓
Application Business Rules
        ↓
Enterprise Business Rules
```

Oddiyroq ko‘rinish:

```txt
UI
 ↓
Use Cases
 ↓
Domain
 ↑
Infrastructure
```

---

## Domain Layer

Eng muhim qatlam.

Bu yerda biznes qoidalar turadi.

Misol:

```ts
class Order {
  constructor(
    public id: string,
    public totalPrice: number,
    public status: 'created' | 'paid' | 'cancelled'
  ) {}

  pay() {
    if (this.status !== 'created') {
      throw new Error('Order cannot be paid');
    }

    this.status = 'paid';
  }
}
```

Bu class Reactga ham, NestJSga ham, PostgreSQLga ham bog‘liq emas.

---

## Use Case Layer

Application logic shu yerda.

```ts
class PayOrderUseCase {
  constructor(private orderRepository: OrderRepository) {}

  async execute(orderId: string) {
    const order = await this.orderRepository.findById(orderId);
    order.pay();
    await this.orderRepository.save(order);
    return order;
  }
}
```

---

## Infrastructure Layer

Tashqi texnologiyalar bilan ishlaydi.

```txt
Database
HTTP Client
File Storage
Redis
Kafka
Email Service
```

---

## Clean Architecture dependency rule

Muhim qoida:

```txt
Ichki qatlam tashqi qatlamni bilmasligi kerak.
Tashqi qatlam ichki qatlamga bog‘lanadi.
```

Noto‘g‘ri:

```txt
Domain → PostgreSQL
```

To‘g‘ri:

```txt
Infrastructure → Domain
```

---

## Clean Architecture qachon ishlatiladi?

```txt
Enterprise systems
Banking systems
E-government systems
Healthcare systems
Katta business logicli loyihalar
Uzoq yashaydigan loyihalar
```

---

## Afzalliklari

```txt
Frameworkga qattiq bog‘lanib qolmaydi
Business logic mustaqil bo‘ladi
Test qilish juda qulay
Database almashtirish osonroq
Katta tizimlar uchun kuchli
```

---

## Kamchiliklari

```txt
Boilerplate ko‘p
Boshlanishida murakkab
Juniorlar uchun qiyin
Kichik CRUD app uchun ortiqcha
```

---

# 9. Hexagonal Architecture

## Hexagonal Architecture nima?

Hexagonal Architecture yana Ports and Adapters deb ham ataladi.

Asosiy g‘oya:

```txt
Application core tashqi dunyodan mustaqil bo‘ladi.
Tashqi tizimlar adapter orqali ulanadi.
```

Diagramma:

```txt
          REST API Adapter
                ↓
Database Adapter → Application Core ← Message Queue Adapter
                ↑
          CLI Adapter
```

---

## Port nima?

Port — application core tashqi dunyo bilan qanday gaplashishini belgilaydigan interface.

```ts
interface PaymentPort {
  pay(amount: number): Promise<void>;
}
```

---

## Adapter nima?

Adapter — portni real texnologiya bilan ulaydi.

```ts
class ClickPaymentAdapter implements PaymentPort {
  async pay(amount: number) {
    // Click API chaqiriladi
  }
}
```

Keyin Payme uchun boshqa adapter:

```ts
class PaymePaymentAdapter implements PaymentPort {
  async pay(amount: number) {
    // Payme API chaqiriladi
  }
}
```

Application core esa Click yoki Payme haqida bilmaydi.

---

## Hexagonal Architecture qachon ishlatiladi?

```txt
Payment systems
Multiple external integrations
Bank systems
Logistics systems
Government platforms
Microservices
```

---

## Afzalliklari

```txt
Integratsiyalarni almashtirish oson
Core business logic himoyalangan
Test qilish qulay
Tashqi service ishlamasa ham core test qilinadi
```

---

## Kamchiliklari

```txt
Interface va adapterlar ko‘payadi
Boshlanishida qiyin
Kichik app uchun ortiqcha
```

---

# 10. Onion Architecture

## Onion Architecture nima?

Onion Architecture Clean Architecturega o‘xshaydi. Farqi — dependency qatlamlari piyoz kabi ichkariga qarab yo‘naladi.

Diagramma:

```txt
Infrastructure
  Application Services
    Domain Services
      Domain Model
```

Eng ichkarida Domain turadi.

---

## Asosiy qoida

```txt
Hamma dependency ichkariga qaraydi.
Domain hech kimga bog‘liq emas.
```

---

## Qatlamlar

### Domain Model

```txt
Entity
Value Object
Business Rules
```

### Domain Services

```txt
Domain logic
Complex business operations
```

### Application Services

```txt
Use Cases
Commands
Queries
```

### Infrastructure

```txt
Database
External API
Messaging
File system
```

---

## Onion Architecture qachon ishlatiladi?

```txt
DDD loyihalar
Enterprise systems
Banking
Healthcare
Complex business apps
```

---

# 11. Feature-Sliced Design

## FSD nima?

Feature-Sliced Design — frontend loyihalarni feature va qatlamlarga ajratish arxitekturasi.

React loyihalar uchun juda foydali.

Structure:

```txt
src/
├── app
├── pages
├── widgets
├── features
├── entities
└── shared
```

---

## app

Application setup.

```txt
Providers
Router
Store
Global styles
App config
```

---

## pages

Route bilan bog‘langan sahifalar.

```txt
/users
/documents
/dashboard
```

---

## widgets

Katta UI bloklar.

```txt
Header
Sidebar
UserTable
DashboardCards
```

---

## features

User actionga bog‘liq funksiyalar.

```txt
login
logout
create-user
delete-document
filter-table
```

---

## entities

Business entitylar.

```txt
user
document
role
permission
product
order
```

---

## shared

Umumiy qayta ishlatiladigan kod.

```txt
ui
api
lib
config
hooks
utils
```

---

## FSD dependency rule

```txt
app → pages → widgets → features → entities → shared
```

Pastki layer yuqoridagi layerni import qilmasligi kerak.

Noto‘g‘ri:

```txt
shared → features
```

To‘g‘ri:

```txt
features → shared
```

---

## FSD qachon ishlatiladi?

```txt
Katta React app
Admin panel
CRM
ERP
E-government frontend
Team bilan ishlanadigan frontend
```

---

## Afzalliklari

```txt
Frontend tartibli bo‘ladi
Featurelar mustaqil bo‘ladi
Kod topish oson
Scale qilish qulay
Jamoada ishlash yaxshi
```

---

## Kamchiliklari

```txt
Boshlanishida tushunish qiyin
Kichik app uchun ortiqcha
Layer qoidalarini buzish oson
```

---

# 12. Component-Based Architecture

## Component-Based Architecture nima?

UI kichik componentlarga bo‘linadi.

```txt
Page
 ├── Header
 ├── Sidebar
 ├── Table
 ├── Modal
 └── Form
```

---

## Component turlari

### Presentational Component

Faqat UI.

```tsx
function UserCard({ name, email }) {
  return (
    <div>
      <h3>{name}</h3>
      <p>{email}</p>
    </div>
  );
}
```

---

### Container Component

Data va logic bilan ishlaydi.

```tsx
function UserCardContainer({ userId }) {
  const { data } = useUser(userId);

  return <UserCard name={data.name} email={data.email} />;
}
```

---

## Qachon ishlatiladi?

```txt
React
Vue
Angular
Design system
Component library
Admin panel
```

---

# 13. Monolithic Architecture

## Monolith nima?

Monolith — barcha backend kod bitta application ichida bo‘ladi.

```txt
Frontend
 ↓
Backend Application
 ├── Auth
 ├── Users
 ├── Orders
 ├── Payments
 └── Reports
 ↓
Database
```

---

## Afzalliklari

```txt
Boshlash oson
Deploy qilish oson
Debug qilish oson
Transaction boshqarish oson
Kichik jamoa uchun qulay
```

---

## Kamchiliklari

```txt
Katta bo‘lsa sekinlashadi
Bitta moduldagi xato butun appga ta'sir qiladi
Scale qilish qiyinlashadi
Kod bazasi kattalashib ketadi
```

---

## Qachon ishlatish kerak?

```txt
Startup MVP
Kichik va o‘rta loyiha
Jamoa kichik bo‘lsa
Business hali tez o‘zgarayotgan bo‘lsa
```

---

# 14. Modular Monolith

## Modular Monolith nima?

Modular Monolith — bitta application, lekin ichida modullar aniq ajratilgan.

```txt
Application
 ├── Auth Module
 ├── User Module
 ├── Document Module
 ├── Notification Module
 └── Report Module
```

---

## Oddiy monolithdan farqi

Oddiy monolithda kod aralashib ketadi.

Modular monolithda har bir modul chegarasi aniq bo‘ladi.

---

## Module ichki structure

```txt
user/
├── controller
├── service
├── repository
├── dto
├── entity
└── module
```

---

## Afzalliklari

```txt
Monolith kabi oddiy deploy
Microservicega qaraganda oson
Modullar tartibli
Keyinchalik microservicega ajratish osonroq
```

---

## Kamchiliklari

```txt
Modul chegarasi buzilsa oddiy monolithga aylanadi
Database odatda bitta bo‘ladi
Juda katta scale uchun yetmasligi mumkin
```

---

## Qachon ishlatiladi?

```txt
O‘rta va katta enterprise loyihalar
Davlat tizimlari
CRM/ERP
Document management
Healthcare platform
```

Ko‘p real loyihalarda Modular Monolith Microservicesdan yaxshiroq boshlang‘ich tanlov bo‘ladi.

---

# 15. Microservices Architecture

## Microservices nima?

Microservices — tizim mustaqil servicelarga bo‘linadi.

```txt
API Gateway
 ├── Auth Service
 ├── User Service
 ├── Order Service
 ├── Payment Service
 ├── Notification Service
 └── Report Service
```

Har bir service mustaqil deploy qilinadi.

---

## Microservice xususiyatlari

```txt
Mustaqil service
Mustaqil deploy
Mustaqil database bo‘lishi mumkin
Service-to-service communication
Monitoring talab qiladi
DevOps kuchli bo‘lishi kerak
```

---

## Communication turlari

### Synchronous

```txt
Service A → HTTP/gRPC → Service B
```

### Asynchronous

```txt
Service A → Kafka/RabbitMQ → Service B
```

---

## Afzalliklari

```txt
Har service alohida scale qilinadi
Katta jamoalar parallel ishlaydi
Texnologiyalarni alohida tanlash mumkin
Bitta service xatosi butun tizimni yiqitmasligi mumkin
```

---

## Kamchiliklari

```txt
Murakkab deployment
Monitoring qiyin
Distributed transaction muammosi
Network latency
Data consistency qiyin
DevOps talabi yuqori
```

---

## Qachon ishlatiladi?

```txt
Juda katta traffic
Katta engineering team
Mustaqil business domainlar
Har modul alohida scale qilinishi kerak bo‘lsa
DevOps va monitoring tayyor bo‘lsa
```

---

# 16. Event-Driven Architecture

## Event-Driven Architecture nima?

Tizimda servicelar eventlar orqali gaplashadi.

```txt
Producer
 ↓
Event Broker
 ↓
Consumer
```

Misol:

```txt
Order Created
 ↓
Payment Service
Notification Service
Inventory Service
```

---

## Event nima?

Event — tizimda sodir bo‘lgan fakt.

```txt
UserRegistered
OrderCreated
PaymentCompleted
DocumentApproved
FileUploaded
```

---

## Brokerlar

```txt
Kafka
RabbitMQ
NATS
Redis Streams
```

---

## Afzalliklari

```txt
Servicelar bir-biridan ajraladi
Real-time tizimlar uchun qulay
Scalability yaxshi
Background processlar uchun kuchli
```

---

## Kamchiliklari

```txt
Debug qilish qiyin
Event yo‘qolmasligini nazorat qilish kerak
Duplicate event bo‘lishi mumkin
Event ordering muammo bo‘lishi mumkin
Eventual consistency tushunish kerak
```

---

## Qachon ishlatiladi?

```txt
Notification system
Payment system
Order processing
Audit log
Real-time analytics
IoT systems
```

---

# 17. Serverless Architecture

## Serverless nima?

Serverless — serverni o‘zingiz boshqarmaysiz, provider boshqaradi.

Misollar:

```txt
AWS Lambda
Google Cloud Functions
Azure Functions
Cloudflare Workers
```

---

## Serverless flow

```txt
HTTP Request
 ↓
API Gateway
 ↓
Lambda Function
 ↓
Database/Storage
```

---

## Afzalliklari

```txt
Server boshqarish shart emas
Auto scale
Kam trafficda arzon
Tez prototyping
```

---

## Kamchiliklari

```txt
Cold start
Vendor lock-in
Debug qilish qiyinroq
Long-running process uchun mos emas
```

---

# 18. CQRS

## CQRS nima?

CQRS — Command Query Responsibility Segregation.

Ya'ni yozish va o‘qish modellari ajratiladi.

```txt
Command = write
Query = read
```

Diagramma:

```txt
Write Side
Command → Handler → Database

Read Side
Query → Handler → Read Model/Cache
```

---

## Command

Tizim holatini o‘zgartiradi.

```txt
CreateUserCommand
ApproveDocumentCommand
PayOrderCommand
```

---

## Query

Faqat ma'lumot o‘qiydi.

```txt
GetUserByIdQuery
GetDocumentListQuery
GetDashboardStatsQuery
```

---

## CQRS qachon kerak?

```txt
Read va write talablari juda farq qilsa
Dashboard ko‘p o‘qilsa
Complex reporting bo‘lsa
High performance kerak bo‘lsa
DDD bilan ishlansa
```

---

## Afzalliklari

```txt
Read modelni optimizatsiya qilish mumkin
Write logic aniq bo‘ladi
Katta tizimlarda tartib beradi
Scalability yaxshi
```

---

## Kamchiliklari

```txt
Murakkablik oshadi
Data sync muammo bo‘lishi mumkin
Eventual consistency kerak bo‘ladi
Kichik CRUD uchun ortiqcha
```

---

# 19. Event Sourcing

## Event Sourcing nima?

Oddiy database holatni saqlaydi.

Event Sourcing esa holat o‘zgarishlar tarixini saqlaydi.

Oddiy usul:

```txt
Order status = paid
```

Event Sourcing:

```txt
OrderCreated
PaymentStarted
PaymentCompleted
OrderPaid
```

Holat eventlardan qayta tiklanadi.

---

## Afzalliklari

```txt
To‘liq audit trail
Har bir o‘zgarish tarixi bor
Oldingi holatni tiklash mumkin
Event replay qilish mumkin
```

---

## Kamchiliklari

```txt
Juda murakkab
Query qilish qiyin
Event versioning kerak
Jamoa tajribali bo‘lishi kerak
```

---

## Qachon ishlatiladi?

```txt
Banking
Payment systems
Audit muhim bo‘lgan tizimlar
Legal systems
Trading platforms
```

---

# 20. DDD — Domain Driven Design

## DDD nima?

DDD — murakkab business domainlarni to‘g‘ri model qilish yondashuvi.

Asosiy g‘oya:

```txt
Kod business tiliga yaqin bo‘lishi kerak.
```

---

## Entity

Identityga ega object.

```ts
class User {
  constructor(public id: string, public name: string) {}
}
```

Ikki user name bir xil bo‘lishi mumkin, lekin id boshqa.

---

## Value Object

Identity yo‘q, qiymat bilan belgilanadi.

```ts
class Money {
  constructor(public amount: number, public currency: string) {}
}
```

---

## Aggregate

Bir nechta objectlarni bitta consistency boundary ichida boshqaradi.

```txt
Order Aggregate
 ├── Order
 ├── OrderItem
 └── DeliveryAddress
```

---

## Domain Service

Entityga sig‘maydigan business logic.

```txt
PaymentCalculator
DeliveryPriceCalculator
DocumentApprovalPolicy
```

---

## Repository

Domain objectlarni saqlash va olish abstractioni.

```ts
interface OrderRepository {
  findById(id: string): Promise<Order>;
  save(order: Order): Promise<void>;
}
```

---

## Bounded Context

Domainning mustaqil chegarasi.

Misol:

```txt
E-commerce:
- Catalog Context
- Order Context
- Payment Context
- Delivery Context
```

Har bir contextda bir xil so‘z boshqa ma'noda bo‘lishi mumkin.

---

## DDD qachon kerak?

```txt
Business logic murakkab bo‘lsa
Katta enterprise tizim bo‘lsa
Ko‘p modul bo‘lsa
Domain ekspertlar bilan ishlansa
Uzoq yashaydigan loyiha bo‘lsa
```

---

# 21. Architecture Patternlarni solishtirish

| Pattern | Asosiy maqsad | Qayerda ishlatiladi | Murakkablik |
|---|---|---|---|
| MVC | UI, logic, data ajratish | Web apps | O‘rta |
| MVT | Django web structure | Django | O‘rta |
| MVP | UI logic ajratish | Mobile/Desktop | O‘rta |
| MVVM | UI state va logic ajratish | React/Vue/Angular | O‘rta |
| Layered | Qatlamlarga bo‘lish | Backend apps | Oson |
| Clean | Business logicni mustaqil qilish | Enterprise | Qiyin |
| Hexagonal | Core va adapterlarni ajratish | Integratsiya ko‘p tizimlar | Qiyin |
| Onion | Domain markazda | DDD systems | Qiyin |
| FSD | Frontendni featurelarga bo‘lish | React apps | O‘rta |
| Monolith | Bitta app | MVP/Small app | Oson |
| Modular Monolith | Bitta app, aniq modullar | Enterprise start | O‘rta |
| Microservices | Mustaqil servicelar | Katta tizimlar | Qiyin |
| Event-Driven | Eventlar orqali aloqa | Real-time/async | Qiyin |
| CQRS | Read/write ajratish | High scale systems | Qiyin |
| Event Sourcing | Holatni eventlardan tiklash | Audit systems | Juda qiyin |
| DDD | Business domain model qilish | Complex business | Qiyin |

---

# 22. Qaysi holatda qaysi pattern ishlatiladi?

## Kichik CRUD app

```txt
MVC yoki Layered Architecture
```

## Django loyiha

```txt
MVT
```

## React admin panel

```txt
MVVM + Feature-Sliced Design + Component-Based Architecture
```

## Enterprise backend

```txt
Layered Architecture + Clean Architecture
```

## Ko‘p external integration bor tizim

```txt
Hexagonal Architecture
```

## Murakkab business logic

```txt
DDD + Clean Architecture + Onion Architecture
```

## Startup MVP

```txt
Modular Monolith
```

## Juda katta traffic

```txt
Microservices + Event-Driven Architecture
```

## Payment yoki banking

```txt
DDD + CQRS + Event Sourcing + Event-Driven Architecture
```

## Notification system

```txt
Event-Driven Architecture + Queue
```

---

# 23. Amaliy loyiha structure namunalari

## React MVVM + FSD

```txt
src/
├── app/
│   ├── providers/
│   ├── router/
│   └── store/
├── pages/
│   └── users/
├── widgets/
│   └── user-table/
├── features/
│   ├── create-user/
│   └── delete-user/
├── entities/
│   └── user/
│       ├── api/
│       ├── model/
│       └── ui/
└── shared/
    ├── ui/
    ├── api/
    ├── hooks/
    └── utils/
```

---

## NestJS Layered Architecture

```txt
src/
├── modules/
│   └── users/
│       ├── users.controller.ts
│       ├── users.service.ts
│       ├── users.repository.ts
│       ├── dto/
│       └── entities/
├── common/
├── config/
└── main.ts
```

---

## Clean Architecture Backend

```txt
src/
├── domain/
│   ├── entities/
│   ├── value-objects/
│   └── services/
├── application/
│   ├── use-cases/
│   ├── commands/
│   └── queries/
├── infrastructure/
│   ├── database/
│   ├── repositories/
│   ├── external-services/
│   └── messaging/
└── presentation/
    ├── controllers/
    └── resolvers/
```

---

## Modular Monolith

```txt
src/
├── auth/
├── users/
├── roles/
├── documents/
├── notifications/
├── reports/
└── shared/
```

Har modul ichida:

```txt
module/
├── controller
├── service
├── repository
├── entity
├── dto
└── tests
```

---

# 24. Interview savollari

## Basic

```txt
MVC nima?
MVC va MVT farqi nima?
MVVM Reactda qanday ko‘rinadi?
Layered Architecture nima?
Service layer nima uchun kerak?
Repository pattern nima?
```

## Middle

```txt
Clean Architecture dependency rule nima?
Hexagonal Architectureda Port va Adapter nima?
FSD dependency rule qanday?
Monolith va Modular Monolith farqi nima?
Microservices qachon kerak emas?
Event-Driven Architectureda duplicate event muammosi qanday hal qilinadi?
```

## Senior

```txt
DDD qachon ishlatiladi?
Bounded Context nima?
CQRS qanday muammoni hal qiladi?
Event Sourcing qachon kerak?
Microservicesda distributed transaction qanday hal qilinadi?
Saga Pattern nima?
Clean Architecture bilan Onion Architecture farqi nima?
Katta React loyihada arxitektura qanday tuziladi?
```

---

# 25. O‘rganish roadmap

## 1-bosqich

```txt
MVC
MVT
MVP
MVVM
```

Maqsad: UI, data va logic ajratishni tushunish.

---

## 2-bosqich

```txt
Layered Architecture
Repository Pattern
Service Layer
Component-Based Architecture
```

Maqsad: real web app structure tushunish.

---

## 3-bosqich

```txt
Feature-Sliced Design
Clean Architecture
Hexagonal Architecture
Onion Architecture
```

Maqsad: katta frontend va backend tizimlarni tartibli qurish.

---

## 4-bosqich

```txt
Monolith
Modular Monolith
Microservices
Event-Driven Architecture
```

Maqsad: system design darajasiga chiqish.

---

## 5-bosqich

```txt
DDD
CQRS
Event Sourcing
Saga Pattern
Distributed Systems
```

Maqsad: enterprise va high-load tizimlarni loyihalash.

---

# Yakuniy xulosa

Architecture Patternlarni o‘rganishdan asosiy maqsad — kodni chiroyli yozish emas, balki katta tizimni uzoq muddat boshqariladigan holatda qurish.

Yaxshi arxitektura quyidagilarni beradi:

```txt
Tartibli kod
Kam texnik qarz
Oson testing
Oson scaling
Oson onboarding
Oson refactoring
Business logic himoyasi
Texnologiyadan mustaqillik
```

Frontend Architect uchun eng muhimlari:

```txt
MVVM
Component-Based Architecture
Feature-Sliced Design
Clean Architecture principles
Micro Frontend basics
```

Backend/System Architect uchun eng muhimlari:

```txt
Layered Architecture
Clean Architecture
Hexagonal Architecture
Modular Monolith
Microservices
Event-Driven Architecture
DDD
CQRS
Event Sourcing
```

Eng yaxshi amaliy yo‘l:

```txt
Avval MVC/MVT/MVVM tushuniladi.
Keyin Layered Architecture va Repository Pattern o‘rganiladi.
Keyin Reactda FSD bilan admin panel qilinadi.
Keyin backendda Clean Architecture bilan API yoziladi.
Keyin Modular Monolith qilinadi.
Keyin Microservices va Event-Driven Architecturega o‘tiladi.
```
