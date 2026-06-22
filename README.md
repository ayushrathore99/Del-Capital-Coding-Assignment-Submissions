# Del-Capital-Coding-Assignment-Submissions
Del Capital Coding Assignment Submissions
# Account Aggregator Integration Platform

## Overview

This project implements a secure and scalable Account Aggregator (AA) Integration Platform using Digio's Account Aggregator APIs. The solution enables consent-driven retrieval of customer financial information from multiple Financial Information Providers (FIPs) and exposes normalized financial data to downstream Financial Information User (FIU) services.

The implementation follows modern backend engineering practices with a layered architecture, auditability, security controls, and compliance-focused data handling.

---

## Features

### Consent Management

* Create customer consent requests
* Track consent lifecycle
* Retrieve consent status
* Handle consent approval and rejection workflows

### Financial Data Retrieval

* Fetch customer financial data from FIPs
* Process asynchronous fetch requests
* Store fetched data securely
* Normalize heterogeneous FIP responses

### Compliance & Audit

* Complete audit trail of all operations
* Consent metadata persistence
* Fetch history tracking
* Regulatory compliance support

### Security

* Input validation
* DTO-based API contracts
* Secure credential management
* Database migration management
* CORS configuration
* PII minimization practices

### Reliability

* Retry mechanisms
* Error handling
* Transaction management
* Idempotent operations
* Structured logging

---

## Technology Stack

### Backend

* Java 21
* Spring Boot 3.x
* Spring Data JPA
* PostgreSQL
* Flyway Migration
* OpenAPI / Swagger
* Maven

### Frontend

* Angular
* TypeScript
* Bootstrap

### Database

* PostgreSQL

### DevOps

* Docker
* Docker Compose

---

## Project Structure

```text
AA-Account-Aggregator
│
├── backend
│   ├── controller
│   ├── service
│   ├── repository
│   ├── entity
│   ├── dto
│   ├── config
│   ├── client
│   ├── exception
│   └── audit
│
├── frontend
│   ├── components
│   ├── services
│   ├── pages
│   └── models
│
├── docs
├── screenshots
└── docker
```

---

## Architecture

```text
Customer
    │
    ▼
Angular Frontend
    │
    ▼
Spring Boot Backend
    │
    ▼
Digio Account Aggregator APIs
    │
    ▼
Financial Information Providers
    │
    ▼
PostgreSQL Database
```

---

## Database Schema

### Customer

| Column      | Description                |
| ----------- | -------------------------- |
| id          | Primary Key                |
| customer_id | Unique Customer Identifier |
| email       | Customer Email             |
| mobile      | Customer Mobile            |

### Consent

| Column      | Description              |
| ----------- | ------------------------ |
| id          | Primary Key              |
| consent_id  | Digio Consent Identifier |
| customer_id | Customer Reference       |
| status      | Consent Status           |
| created_at  | Creation Timestamp       |

### Fetch Session

| Column     | Description      |
| ---------- | ---------------- |
| id         | Primary Key      |
| session_id | Fetch Session ID |
| consent_id | Linked Consent   |
| status     | Fetch Status     |
| created_at | Timestamp        |

### Audit Logs

| Column           | Description    |
| ---------------- | -------------- |
| id               | Primary Key    |
| action           | Operation Type |
| request_payload  | Request Data   |
| response_payload | Response Data  |
| timestamp        | Event Time     |

---

## API Endpoints

### Create Consent

```http
POST /api/v1/consents
```

### Get Consent Status

```http
GET /api/v1/consents/{consentId}
```

### Initiate Data Fetch

```http
POST /api/v1/fetch
```

### Get Fetch Status

```http
GET /api/v1/fetch/{fetchId}
```

### Retrieve Accounts

```http
GET /api/v1/accounts/{customerId}
```

### Retrieve Transactions

```http
GET /api/v1/transactions/{accountId}
```

---

## Running the Application

### Clone Repository

```bash
git clone <repository-url>
cd AA-Account-Aggregator
```

### Backend Setup

```bash
cd backend

mvn clean install

mvn spring-boot:run
```

Backend will start on:

```text
http://localhost:8080
```

### Frontend Setup

```bash
cd frontend

npm install

ng serve
```

Frontend will start on:

```text
http://localhost:4200
```

---

## Database Setup

Create PostgreSQL database:

```sql
CREATE DATABASE account_aggregator;
```

Configure credentials in:

```properties
application.properties
```

Example:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/account_aggregator
spring.datasource.username=postgres
spring.datasource.password=password
```

---

## API Documentation

Swagger UI:

```text
http://localhost:8080/swagger-ui/index.html
```

OpenAPI Specification:

```text
http://localhost:8080/v3/api-docs
```

---

## Security Considerations

* Environment-based configuration
* No hardcoded credentials
* Request validation
* Layered architecture
* DTO isolation
* Secure database access
* Audit logging
* Principle of least privilege
* Sensitive data masking

---

## Compliance Considerations

* Consent-first data access
* Audit trail preservation
* Data retention support
* Customer authorization enforcement
* Traceability of financial data access
* Secure storage of consent metadata

---

## Screenshots

### Consent Creation

(Add screenshot)

### Consent Status Tracking

(Add screenshot)

### Data Fetch Dashboard

(Add screenshot)

### Swagger Documentation

(Add screenshot)

---

## Future Improvements

* JWT Authentication
* Role-Based Access Control (RBAC)
* Redis Caching
* Resilience4j Circuit Breakers
* Kafka Event Streaming
* Prometheus Metrics
* Grafana Dashboards
* Kubernetes Deployment

---

## Author

Ayush Rathore

Indian Institute of Technology Madras (IIT Madras)

Take-Home Assessment Submission Del Capital

---

## License

This project is submitted solely for evaluation purposes as part of the Del Capital Software Engineer Assessment.
