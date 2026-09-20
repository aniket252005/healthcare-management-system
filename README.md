# Healthcare & Hospital Management System

A robust, enterprise-grade Healthcare & Hospital Management System built with **Spring Boot** and a modern **Microservices Architecture**. The system streamlines patient care, doctor scheduling, consultation workflows, inventory management, recommendations, community forums, and real-time alerts.

---

## 👨‍💻 Author & Maintainer

- **Author**: Aniket Dileep Pandey
- **GitHub**: [@aniket252005](https://github.com/aniket252005)
- **Profile**: [https://github.com/aniket252005](https://github.com/aniket252005)

---

## 🏛 Architecture Overview

The application is structured into decoupled, independently scalable microservices:

| Service | Description | Port |
| :--- | :--- | :--- |
| **EurecaServerDiscovery** | Netflix Eureka Service Discovery & Registry | `8761` |
| **configServer** | Centralized Spring Cloud Config Server | `8888` |
| **api-gateway** | Spring Cloud API Gateway for routing & filtering | `8080` |
| **security-microservice** | Authentication & Authorization service (JWT-based) | `8081` |
| **patient** | Patient profiles, medical history & appointment booking | `8082` |
| **doctor** | Doctor profiles, specialties, schedules & consultations | `8083` |
| **administrative** | Administrative controls, staff management & hospital operations | `8084` |
| **inventory** | Pharmaceutical inventory, medicine supplies & stock tracking | `8085` |
| **notification** | Real-time WebSocket notifications & alerts | `8086` |
| **recommendation** | Health recommendations & treatment analytics | `8087` |
| **community** | Patient-doctor community forum & health discussions | `8088` |

---

## 🛠 Tech Stack

- **Backend**: Java 17+, Spring Boot 3.x
- **Microservices Framework**: Spring Cloud (Eureka Discovery Server, Spring Cloud Gateway, Spring Cloud Config Server)
- **Inter-service Communication**: OpenFeign declarative REST client
- **Fault Tolerance**: Resilience4j (Circuit Breaker, Fallbacks, Rate Limiting)
- **Security**: Spring Security 6 with JSON Web Tokens (JWT) & Role-Based Access Control (`ROLE_PATIENT`, `ROLE_DOCTOR`, `ROLE_ADMINISTRATIVE`)
- **Real-time Communication**: Spring WebSocket / STOMP
- **Data Persistence**: Spring Data JPA / Hibernate
- **Database**: MySQL
- **Build Tool**: Gradle

---

## 🚀 Getting Started

### Prerequisites

- **Java JDK 17** or later installed and configured (`JAVA_HOME`)
- **MySQL Server** running locally or via Docker
- **Git**

### 1. Clone the Repository

```bash
git clone https://github.com/aniket252005/healthcare-management-system.git
cd healthcare-management-system
```

### 2. Configure the Database & Config Server

1. Create the necessary databases in MySQL (or configure credentials in your configuration properties).
2. Review `configServer/src/main/resources/application.properties` to ensure the git configuration repository points to:
   ```properties
   spring.cloud.config.server.git.uri=https://github.com/aniket252005/config_server.git
   ```

### 3. Startup Order

To allow services to register and fetch configurations properly, start the services in the following order:

1. **Eureka Discovery Server**
   ```bash
   cd EurecaServerDiscovery
   ./gradlew bootRun
   ```
2. **Config Server**
   ```bash
   cd ../configServer
   ./gradlew bootRun
   ```
3. **API Gateway**
   ```bash
   cd ../api-gateway
   ./gradlew bootRun
   ```
4. **Security Microservice**
   ```bash
   cd ../security-microservice
   ./gradlew bootRun
   ```
5. **Business Microservices** (can be launched in parallel):
   - `patient`
   - `doctor`
   - `administrative`
   - `inventory`
   - `notification`
   - `recommendation`
   - `community`

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
