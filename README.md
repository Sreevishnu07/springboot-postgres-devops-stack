# Spring Boot + PostgreSQL DevOps Stack

Production-style multi-container Spring Boot + PostgreSQL deployment using Docker Compose with healthchecks, persistent volumes, networking, and container orchestration.

---

# Project Overview

This project demonstrates how to containerize and orchestrate a backend infrastructure stack using:

* Spring Boot
* PostgreSQL
* Docker
* Docker Compose

The application is packaged as an executable JAR using Maven, containerized using Docker, and orchestrated alongside PostgreSQL using Docker Compose.

---

# Tech Stack

| Technology     | Purpose                                    |
| -------------- | ------------------------------------------ |
| Spring Boot    | Backend application framework              |
| PostgreSQL     | Relational database                        |
| Maven          | Build automation and dependency management |
| Docker         | Containerization                           |
| Docker Compose | Multi-container orchestration              |
| Tomcat         | Embedded application server                |

---

# Features

* Multi-container architecture
* Spring Boot containerization
* PostgreSQL database container
* Docker Compose orchestration
* Internal container networking
* Persistent PostgreSQL storage using Docker volumes
* PostgreSQL healthchecks
* Environment variable based configuration
* Restart policies for resiliency
* Production-style infrastructure setup

---

# Architecture

```text
Browser/Postman
        ↓
localhost:8083
        ↓
Spring Boot Container
        ↓
Docker Internal Network
        ↓
PostgreSQL Container
        ↓
Persistent Docker Volume
```

---

# Project Structure

```text
postgre-springboot-docker/
│
├── docker-compose.yml
│
└── spring-app/
    │
    ├── Dockerfile
    ├── pom.xml
    ├── mvnw
    ├── mvnw.cmd
    ├── src/
    └── target/
```

---

# Docker Compose Configuration

The project uses Docker Compose for:

* Service orchestration
* Networking
* Healthchecks
* Persistent storage
* Startup dependency management

Services:

* `springboot-app`
* `postgres`

---

# Spring Boot Configuration

Environment variables are injected through Docker Compose.

Example:

```properties
spring.datasource.url=${SPRING_DATASOURCE_URL}
spring.datasource.username=${SPRING_DATASOURCE_USERNAME}
spring.datasource.password=${SPRING_DATASOURCE_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

---

# Docker Concepts Demonstrated

## Dockerfile

Used to:

* Build custom Spring Boot image
* Package executable JAR
* Configure runtime environment

## Docker Compose

Used to:

* Run multiple containers
* Manage networking
* Configure services
* Handle dependencies
* Create persistent storage

## Docker Volumes

Used for PostgreSQL persistence:

```yaml
volumes:
  - postgres_data:/var/lib/postgresql/data
```

## Healthchecks

PostgreSQL healthchecks ensure Spring Boot waits until the database is ready.

```yaml
healthcheck:
  test: ["CMD-SHELL", "pg_isready -U myuser -d my_db"]
```

---

# Getting Started

## Prerequisites

Install:

* Docker
* Docker Compose
* Java 17
* Maven (optional if using Maven Wrapper)

---

# Build Spring Boot Application

From the `spring-app` directory:

```bash
mvnw.cmd clean package
```

This generates:

```text
target/spring-app-0.0.1-SNAPSHOT.jar
```

---

# Run The Stack

From the project root:

```bash
docker compose up --build
```

---

# Access Application

Open:

```text
http://localhost:8083
```

Expected response:

```text
Spring Boot + PostgreSQL + Docker Compose Working
```
---

# Key DevOps Learnings

This project demonstrates important DevOps concepts such as:

* Infrastructure as Code
* Containerization
* Multi-service orchestration
* Persistent storage
* Service discovery
* Health monitoring
* Environment-based configuration
* Build pipelines
* Container networking

---

# Author
## - Sree Vishnu A S
Built as a hands-on DevOps learning project focused on containerized backend infrastructure and orchestration.
