
# One Place Subscription 💳

> A web application for managing and tracking recurring subscriptions in one place.

---

## Description

OnePlaceSubscription (OPS) is a fullstack web application built as a final examination project for the AP Graduate in Computer Science programme at Copenhagen Business Academy (Erhvervsakademi København), 2026.

The application allows users to register, log in securely, and manage their recurring subscriptions — either by adding them manually or by connecting a bank account via a PSD2-compatible API (sandbox environment) that automatically identifies recurring payments from transaction history.

---

## Purpose

Many consumers today hold a range of recurring subscriptions across streaming, software, fitness and other services. Keeping track of what is being paid, and when payments are due, can be difficult. OPS consolidates all subscriptions in one place and provides a clear monthly and annual expense overview.

This project demonstrates applied knowledge of REST API design, JWT-based authentication, layered Spring Boot architecture, and external API integration using the PSD2 standard.

---

## Features

- **User registration and login** — secure account creation and authentication via JWT
- **Manual subscription management** — create, view, edit and delete subscriptions with name, amount, payment date and category
- **PSD2 bank integration (mock)** — connect a bank account via GoCardless/Nordigen sandbox, automatically detect recurring payments and import them as subscriptions
- **Monthly and annual overview** — total expense calculations per category and per time period

---

## Tech Stack

| Layer | Technology                              |
|---|-----------------------------------------|
| Backend | Java 21, Spring Boot 3, Spring Security |
| Frontend | Thymeleaf                               |
| Authentication | JWT (JSON Web Token)                    |
| Database | PostgreSQL                              |
| ORM | Spring Data JPA / Hibernate             |
| External API | GoCardless / Nordigen (PSD2 sandbox)    |
| Build tool | Maven                                   |
| Version control | Git / GitHub                            |

---

## Project Structure

```
src/
├── main/
│   ├── java/com/subtracker/
│   │   ├── config/          # Security config, JWT filter
│   │   ├── controller/      # REST controllers
│   │   ├── dto/             # Request/response DTOs
│   │   ├── entity/          # JPA entities
│   │   ├── repository/      # Spring Data repositories
│   │   ├── service/         # Business logic
│   │   └── util/            # JWT utility, helpers
│   └── resources/
│       ├── templates/       # Thymeleaf templates
│       └── application.properties
```

---

## Installation

### Prerequisites

- Java 17 or higher
- Maven 3.8+
- PostgreSQL 14+
- A GoCardless/Nordigen developer account (free, no CVR required) for PSD2 sandbox access

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/mridrisisci/OnePlaceSubscription.git
cd OnePlaceSubscription
```

**2. Create the database**
```sql
CREATE DATABASE subtracker;
```

**3. Configure environment**

Create an `application.properties` file in `src/main/resources/` or set the following environment variables:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/subtracker
spring.datasource.username=YOUR_DB_USER
spring.datasource.password=YOUR_DB_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

jwt.secret=YOUR_JWT_SECRET
jwt.expiration=86400000

nordigen.secret-id=YOUR_NORDIGEN_SECRET_ID
nordigen.secret-key=YOUR_NORDIGEN_SECRET_KEY
```

**4. Build and run**
```bash
mvn clean install
mvn spring-boot:run
```

**5. Access the application**

Open your browser and navigate to `http://localhost:8080`

---

## Usage

1. Register a new account at `/register`
2. Log in at `/login`
3. Add subscriptions manually via the dashboard
4. Connect your bank account (sandbox) to automatically import recurring transactions
5. View your monthly and annual subscription overview on the dashboard

---

## Domain Model

| Entity | Description |
|---|---|
| `User` | Account holder with login credentials |
| `Subscription` | A recurring payment, manual or imported |
| `Category` | Label for grouping subscriptions |
| `BankAccount` | Connected sandbox bank account (one per user) |
| `Transaction` | Raw PSD2 transaction data used for matching |

---

## License

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

You are free to view and use this code for non-commercial purposes. Any use of this code to provide a network service requires the complete source code of that service to be made publicly available under the same license.

See [LICENSE](LICENSE) for full terms.

---

## Author

**Idris**
AP Graduate in Computer Science — Cphbusiness, 2026
SOC Analyst Intern @ AevenGroup

GitHub: [@mridrisisci](https://github.com/mridrisisci)

---

## Status

🚧 **In active development** — Examination project, April–May 2026****