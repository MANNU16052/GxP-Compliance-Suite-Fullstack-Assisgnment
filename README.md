✅ Updated README.md (Ready-to-use)
# 📦 GxP Compliance Suite (QMS/DMS/TMS Sample)

Full-stack reference project demonstrating **QMS/DMS/TMS** with:

- ✅ Spring Boot + MySQL (backend)  
- 🔑 JWT Authentication (Spring Security)  
- 👥 Role-based access (`USER` / `ADMIN`)  
- 📂 Document CRUD + status update workflow  
- 📢 Mock Notification service with **Resilience4j** (Circuit breaker + Retry)  
- 🎨 React Dashboard (upload, list, approve)  
- 🐳 Docker support (Backend & Frontend)  

Project Structure:

gxp-compliance-suite/
├── backend/ # Spring Boot application
│ ├── src/main/java/com/stacklab/gxp/
│ │ ├── GxpApplication.java
│ │ ├── controller/ # REST controllers
│ │ ├── security/ # JWT, filters, UserDetails
│ │ ├── service/ # Business services
│ │ ├── repo/ # Spring Data JPA repositories
│ │ └── model/ # Entity classes
│ ├── src/main/resources/
│ │ ├── application.yml # DB + JPA configs
│ │ └── static/ # Static resources (if any)
│ ├── pom.xml # Maven dependencies
│ └── Dockerfile # Docker build file for backend
│
├── frontend/ # React (Vite) application
│ ├── src/
│ │ ├── components/ # Reusable UI components
│ │ ├── pages/ # Dashboard, Login, Register
│ │ ├── services/ # API calls (Axios)
│ │ └── App.jsx
│ ├── package.json # NPM dependencies
│ └── Dockerfile # Docker build file for frontend
│
├── screenshots/ # Project screenshots
│ └── dashboard.png
│
└── README.md # Documentation

---

## 🚀 Quick Start (Local)

### 1. Database (MySQL)
Start MySQL locally and create database:
```sql
CREATE DATABASE gxpdb;


Update credentials in backend/src/main/resources/application.yml:

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/gxpdb
    username: root
    password: yourpassword

2. Backend (Spring Boot)
cd backend
mvn clean install
mvn spring-boot:run


Backend will start at:
👉 http://localhost:8080

3. Frontend (React + Vite)
cd frontend
npm install
npm run dev


Frontend will start at:
👉 http://localhost:5173

4. Default Users (Seed)

Click “Seed Admin/User” button on frontend OR insert manually into DB.

Admin → admin / admin123 (ROLE_ADMIN)

User → user1 / user123 (ROLE_USER)

🔑 Authentication Flow

Register → POST /api/auth/register

Login → POST /api/auth/login → returns JWT token

Use JWT in Authorization: Bearer <token> header for all APIs.

📂 API Endpoints
Auth

POST /api/auth/register → Create user

POST /api/auth/login → Login & get JWT

Documents

GET /api/documents?status=PENDING → List pending docs

POST /api/documents → Upload new doc (USER/ADMIN)

PATCH /api/documents/{id}/status → Approve/Reject (ADMIN)

🐳 Docker Setup (Optional)
Backend
cd backend
docker build -t gxp-backend .
docker run -p 8080:8080 gxp-backend

Frontend
cd frontend
docker build -t gxp-frontend .
docker run -p 5173:5173 gxp-frontend

🖼️ Frontend Preview

Dashboard page after login:


(Upload docs, list them, approve as Admin)

🛠️ Tech Stack

Backend: Spring Boot, Spring Security, JWT, JPA/Hibernate, Resilience4j

Frontend: React, Vite, TailwindCSS

Database: MySQL / H2 (for local dev)

Deployment: Docker

📌 Notes

Use Postman collection (gxp-compliance-suite.postman_collection.json) to test APIs quickly.
Adjust application.yml for your DB credentials.
