# User Service (Go + Clean Architecture + REST)

## Overview

This project is a standalone **User Service** implemented in **Go**, following **Clean Architecture principles**.

The service is responsible for managing user-related operations such as creating, retrieving, updating, and deleting users. It exposes RESTful HTTP endpoints and follows a layered architecture to ensure scalability, maintainability, and testability.

---

## Architecture

The project follows Clean Architecture layering:

```text
cmd → adapter → usecase → repository → entity
```

### Layer Responsibilities

* **entity/**
  Core domain models and business rules related to users.

* **usecase/**
  Application business logic for user operations.

* **repository/**
  Data persistence abstraction layer.

* **adapter/http/**
  HTTP handlers and routing configuration.

* **cmd/**
  Application entry point and server bootstrap.

This ensures:

* Clear separation of concerns
* Dependency inversion
* Testable business logic
* Extensible service structure

---

## Project Structure

```text
apis-user-service-master/
│
├── cmd/
│   └── main.go
│
├── internal/
│   ├── adapter/
│   │   └── http/
│   │       ├── handler.go
│   │       └── router.go
│   │
│   ├── entity/
│   │   └── user.go
│   │
│   ├── repository/
│   │   └── user_repository.go
│   │
│   └── usecase/
│       └── user_usecase.go
│
├── go.mod
└── go.sum
```

---

## Domain Model

### User Entity

The core domain entity is:

* `User`

Typical fields may include:

* ID
* Name
* Email
* Password
* CreatedAt

All business rules related to user handling are encapsulated in the `usecase` layer.

---

## API Endpoints

The service exposes REST endpoints for user management.

Typical operations include:

```text
POST   /users
GET    /users
GET    /users/{id}
PUT    /users/{id}
DELETE /users/{id}
```

Routes are defined in:

```text
internal/adapter/http/router.go
```

Handlers are implemented in:

```text
internal/adapter/http/handler.go
```

---

## How to Run

### 1. Clone repository

```bash
git clone <your-repository-url>
cd apis-user-service-master
```

### 2. Install dependencies

```bash
go mod tidy
```

### 3. Run the service

```bash
go run cmd/main.go
```

The HTTP server starts on the port configured inside `main.go`.

---

## Design Principles

* Clean Architecture
* Repository pattern
* Layered service structure
* Interface-driven development
* Separation of domain and infrastructure

---

## What This Project Demonstrates

* REST API implementation in Go
* User management service design
* Clean Architecture in practice
* Proper separation of business logic and delivery layer
* Scalable backend microservice structure
