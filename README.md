# 🏋️‍♂️ Fitness App – Microservices Architecture

<p align="center">
  <img src="https://img.shields.io/badge/Architecture-Microservices-blueviolet" />
  <img src="https://img.shields.io/badge/Backend-Spring%20Boot-brightgreen" />
  <img src="https://img.shields.io/badge/Frontend-React%20(Vite)-61dafb" />
  <img src="https://img.shields.io/badge/Auth-Keycloak-orange" />
  <img src="https://img.shields.io/badge/Messaging-RabbitMQ-ff6600" />
  <img src="https://img.shields.io/badge/Database-MongoDB-4db33d" />
</p>

<p align="center">
A scalable, event-driven fitness tracking platform built using Spring Boot microservices and a modern React frontend.
</p>

---

## 🚀 Project Overview

This project is a **fitness activity tracking platform** designed using a **microservices architecture**.  
Users can log fitness activities, which are processed asynchronously to generate **AI-powered recommendations**.

The system focuses on:
- Scalability
- Loose coupling
- Clean separation of responsibilities
- Real-world backend architecture patterns

---

## ✨ Key Highlights (TL;DR)

- ⚙️ Spring Boot microservices architecture
- 🌐 API Gateway with centralized authentication
- 🔍 Service discovery using Netflix Eureka
- 🧠 AI-powered fitness recommendations
- 📨 Event-driven communication with RabbitMQ
- 🔐 Secure authentication via Keycloak
- ⚛️ Modern React frontend (Vite)

---

## 🧱 System Architecture

To ensure alignment across all devices, the following diagram is rendered in a monospaced environment:

```text
       [ User Browser ]
              |
              v
      [ React Frontend ]
              |
              v
      [ API Gateway ]  <------>  [ Keycloak Auth ]
              |
      ------------------
      |                |
      v                v
[ Eureka Server ] [ Config Server ]
      |                |
      ------------------
              |
      ------------------------------------------
      |                                        |
      v                                        v
[ Activity Service ]                    [ AI Service ]
      |                                        ^
      |-----> ( MongoDB )                      |-----> ( MongoDB )
      |                                        |
      |          [[ RabbitMQ ]]                |
      |                |                       |
      +---(Event)----->|----------(Consume)----+
```      

### Core Components

- **API Gateway**
  - Entry point for all client requests
  - Authentication & routing
- **Eureka Server**
  - Service discovery
- **Config Server**
  - Centralized configuration management
- **Activity Service**
  - Handles fitness activity CRUD
- **AI Service**
  - Generates recommendations asynchronously
- **Frontend**
  - User-facing React application

---

## 🧩 Backend Microservices

### 🏃 Activity Service
- Manages user fitness activities
- Persists data in **MongoDB**
- Publishes activity events to **RabbitMQ**
- Validates user context via Gateway

**Responsibilities**
- Create activity
- Fetch activity history
- Emit activity events

---

### 🤖 AI Service
- Consumes activity events from RabbitMQ
- Uses **Gemini AI** to generate insights
- Stores recommendations in MongoDB

**Responsibilities**
- Process fitness data
- Generate personalized recommendations
- Remain decoupled from core user flows

---

### 🌐 API Gateway
- Single entry point for all clients
- Handles authentication tokens
- Routes traffic to internal services
- Integrates with Keycloak

---

### ⚙️ Config Server
- Centralized configuration management
- Environment-specific YAMLs
- Reduces config duplication across services

---

### 🔍 Eureka Server
- Service registration and discovery
- Enables dynamic service communication
- Eliminates hard-coded service URLs

---

## 🎨 Frontend Application

<p align="left">
  <img src="https://img.shields.io/badge/React-⚛️-61dafb" />
  <img src="https://img.shields.io/badge/Vite-Build%20Tool-purple" />
</p>

### Features
- User authentication via Keycloak
- Activity creation and listing
- Activity detail views
- API abstraction layer
- Redux-based state management

---

## 🔄 Data & Event Flow

1. User logs a fitness activity via the frontend
2. Request flows through the API Gateway
3. Activity Service stores the activity in MongoDB
4. Activity event is published to RabbitMQ
5. AI Service consumes the event
6. AI recommendation is generated and stored
7. Recommendations can be retrieved asynchronously

This approach ensures:
- Non-blocking user flows
- Better scalability
- Fault isolation

---

## 🛠️ Tech Stack

### Backend
<p>
  <img src="https://img.shields.io/badge/Java-ED8B00?logo=java&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?logo=springboot&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring%20Cloud-6DB33F" />
</p>

### Frontend
<p>
  <img src="https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white" />
</p>

### Infrastructure & Tools
<p>
  <img src="https://img.shields.io/badge/MongoDB-4DB33D?logo=mongodb&logoColor=white" />
  <img src="https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white" />
  <img src="https://img.shields.io/badge/Keycloak-2C2C2C?logo=keycloak&logoColor=white" />
  <img src="https://img.shields.io/badge/Eureka-Netflix-red" />
</p>

---

## 🔐 Security & Authentication

- Authentication managed using **Keycloak**
- OAuth2 token-based security
- API Gateway validates tokens
- Services remain isolated from auth logic

---

## 🧠 Why Microservices?

This architecture was chosen to demonstrate:
- Independent service scaling
- Event-driven communication
- Clear ownership boundaries
- Production-grade backend patterns

It also allows easy future expansion like:
- Nutrition tracking
- Social features
- Wearable integrations

---

## 🚧 Future Improvements

- Docker & Kubernetes deployment
- Distributed tracing & observability
- Centralized logging
- CI/CD pipelines
- Rate limiting & caching

---

## 👤 Author Note

This project was built to explore **real-world backend architecture patterns**, not just feature development.

It demonstrates:
- System design thinking
- Asynchronous communication
- Security-first API design
- Clean separation of concerns

---

⭐ If you’re a recruiter or interviewer, this project reflects how I approach scalable backend systems in production-like environments.
