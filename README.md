# 🔗 Secure URL Shortener API

A production-style backend application built using **Spring Boot** that allows users to generate short URLs, redirect users to original URLs, and track URL usage. The application also implements secure user authentication using **JWT (JSON Web Token)** and password encryption with **BCrypt**.

---

## 🚀 Project Overview

Long URLs are difficult to share, remember, and manage. This application solves that problem by generating unique short URLs that redirect users to the original destination.

In addition to URL shortening, the application provides secure user registration and login functionality using Spring Security and JWT-based authentication.

---

## ✨ Features

### 👤 User Management
- User Registration
- User Login
- BCrypt Password Encryption
- JWT Token Generation

### 🔗 URL Management
- Generate Short URLs
- Redirect to Original URLs
- Track URL Click Count
- Store URL Mappings in MySQL

### 🔒 Security
- Spring Security Integration
- Password Encryption using BCrypt
- JWT Authentication

### 🗄️ Database
- MySQL Integration
- Spring Data JPA
- Hibernate ORM

---

## 🛠️ Technologies Used

- Java 17
- Spring Boot
- Spring Security
- JWT (JSON Web Token)
- Spring Data JPA
- Hibernate
- MySQL
- Lombok
- Maven

---

## 📂 Project Structure

```text
src
│
├── main
│   ├── java
│   │   └── com.urlshortener
│   │       │
│   │       ├── UrlShortenerApplication.java
│   │       │
│   │       ├── config
│   │       │   ├── SecurityConfig.java
│   │       │   └── JwtUtil.java
│   │       │
│   │       ├── controller
│   │       │   ├── AuthController.java
│   │       │   └── UrlController.java
│   │       │
│   │       ├── dto
│   │       │   ├── UrlRequest.java
│   │       │   └── UrlResponse.java
│   │       │
│   │       ├── entity
│   │       │   ├── UserEntity.java
│   │       │   └── UrlEntity.java
│   │       │
│   │       ├── exception
│   │       │   └── UrlNotFoundException.java
│   │       │
│   │       ├── repository
│   │       │   ├── UserRepository.java
│   │       │   └── UrlRepository.java
│   │       │
│   │       └── service
│   │           ├── UrlService.java
│   │           └── UrlServiceImpl.java
│   │
│   └── resources
│       └── application.properties
│
└── pom.xml
```

---

## ⚙️ Database Configuration

Create a MySQL database:

```sql
CREATE DATABASE url_shortener;
```

Configure `application.properties`:

```properties
server.port=8088

spring.datasource.url=jdbc:mysql://localhost:3306/url_shortener
spring.datasource.username=root
spring.datasource.password=YOUR_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

## 🔑 Authentication APIs

### Register User

**POST**

```http
/auth/register
```

Request Body:

```json
{
  "username": "john",
  "password": "password123"
}
```

Response:

```text
User Registered
```

---

### Login User

**POST**

```http
/auth/login
```

Request Body:

```json
{
  "username": "john",
  "password": "password123"
}
```

Response:

```text
JWT_TOKEN
```

---

## 🌐 URL APIs

### Create Short URL

**POST**

```http
/api/urls
```

Request Body:

```json
{
  "originalUrl": "https://www.google.com"
}
```

Response:

```json
{
  "originalUrl": "https://www.google.com",
  "shortCode": "abc123"
}
```

---

### Redirect to Original URL

**GET**

```http
/api/urls/{shortCode}
```

Example:

```http
/api/urls/abc123
```

Behavior:

```text
Redirects to:
https://www.google.com
```

---

## 🔄 Application Workflow

```text
User Registers
       │
       ▼
User Logs In
       │
       ▼
JWT Token Generated
       │
       ▼
Create Short URL
       │
       ▼
Store URL Mapping in MySQL
       │
       ▼
Access Short URL
       │
       ▼
Retrieve Original URL
       │
       ▼
Redirect User
       │
       ▼
Increase Click Count
```

---

## 📊 Database Tables

### users

| Column | Type |
|----------|----------|
| id | BIGINT |
| username | VARCHAR |
| password | VARCHAR |

### url_mapping

| Column | Type |
|----------|----------|
| id | BIGINT |
| original_url | VARCHAR |
| short_code | VARCHAR |
| click_count | BIGINT |

---

## ▶️ Running the Application

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd url-shortener
```

Run the application:

```bash
mvn spring-boot:run
```

Application will start on:

```text
http://localhost:8088
```

---

## 🧪 Testing Using Postman

### Register User

```http
POST http://localhost:8088/auth/register
```

### Login User

```http
POST http://localhost:8088/auth/login
```

### Create Short URL

```http
POST http://localhost:8088/api/urls
```

### Redirect URL

```http
GET http://localhost:8088/api/urls/{shortCode}
```

---

## 🎯 Learning Outcomes

This project helped me gain practical experience in:

- Spring Boot REST API Development
- Layered Architecture
- Spring Security
- JWT Authentication
- BCrypt Password Encryption
- Spring Data JPA
- Hibernate ORM
- MySQL Integration
- Exception Handling
- DTO Pattern
- Repository Pattern
- Dependency Injection
- Maven Build Management

---

## 👨‍💻 Author

**Yerravalla Shilpa Reddy**

Java Developer | Spring Boot Enthusiast  | Backend

---

## 📜 License

This project is developed for educational and portfolio purposes.

