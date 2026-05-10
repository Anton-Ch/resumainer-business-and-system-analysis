# Technical Constraints

## 1. Purpose

This document defines the technical constraints for the AI Resume Tailor Capstone project.

The purpose is to align the project idea with the mandatory Java course Capstone project requirements and avoid architecture decisions that may be rejected during review.

## 2. Mandatory Course Technology Stack

The application must be implemented using the following mandatory Java technologies:
- Servlets
- Spring Core
- Spring MVC
- JDBC
- Maven
- PostgreSQL

The application must follow:
- Layered Architecture
- MVC pattern
- DAO pattern for database access
- Java Code Convention
- SOLID principles
- DRY principles

## 3. Forbidden or Restricted Technologies

### 3.1 ORM Frameworks Are Not Allowed

The application must not use ORM frameworks.

Forbidden for this project:
- Hibernate
- JPA
- Spring Data JPA
- MyBatis, unless mentors explicitly allow it

Reason:
The course requirements explicitly require plain JDBC and manually implemented data access logic.

### 3.2 Spring Boot Is Not Assumed as Allowed

Spring Boot should not be assumed as allowed for the MVP unless mentors explicitly confirm it.

Recommended safe approach:
- Classic Spring MVC application
- WAR packaging
- Deployment to Apache Tomcat
- Manual Spring configuration through Java config or XML where appropriate

If mentors allow Spring Boot later, the architecture can be adjusted. However, the initial BA and architecture documents should stay compatible with the strict stack.

### 3.3 Dependency Minimization

Only necessary and actively used libraries should be added.

Avoid:
- unused helper libraries;
- unstable libraries;
- heavy frameworks that duplicate course requirements;
- libraries that hide required implementation details.

## 4. Database Constraints

### 4.1 Database Management System

The application must use PostgreSQL as the relational database.

### 4.2 Database Normalization

The database schema must be normalized up to at least the third normal form.

The schema should include:
- primary keys;
- foreign keys;
- clear relationships;
- normalized reference tables where appropriate;
- no duplicated reference values across business tables.

### 4.3 Recommended Table Count

The course recommends 6 to 8 related tables, but this is not a strict limit.

Because the AI Resume Tailor domain is more complex than a simple library application, the MVP database may exceed 8 tables. However, the ERD should clearly separate:
- core MVP tables;
- optional MVP stretch tables;
- future extension tables.

### 4.4 SQL Scripts

The project must include separate SQL scripts for database initialization. Those scripts should have Idempotence quality.

Required scripts:
- `schema.sql`
- `data.sql`

Recommended Flyway-based structure:
- `V1__initial_schema.sql`
- `V2__seed_reference_data.sql`
- `V3__seed_demo_users.sql`

If mentors expect exactly `schema.sql` and `data.sql`, keep copies or generate them from the same migration content.

## 5. JDBC Constraints

### 5.1 Plain JDBC

All database access must be implemented using plain JDBC.

### 5.2 Custom Thread-Safe Connection Pool

The project must include a manually implemented thread-safe Connection Pool.

The Connection Pool should:

- initialize a limited number of database connections;
- provide available connections to DAO classes;
- return connections back to the pool after use;
- be thread-safe;
- support graceful shutdown;
- read configuration from `application.properties` or equivalent config file.

### 5.3 PreparedStatements

All SQL queries must use `PreparedStatement`.

String concatenation for SQL parameters is not allowed.

### 5.4 Transaction Management

Critical operations must use standard JDBC transaction management.

Examples:
- user registration;
- resume generation request creation;
- saving generated resume draft;
- saving final resume with public link;
- admin status updates if several related records are affected.

## 6. Security Constraints

### 6.1 Password Hashing

Passwords must never be stored in plain text.

Recommended:
- BCrypt

### 6.2 Input Sanitization

The system must protect against:
- SQL injection;
- JavaScript injection;
- malicious script input in form fields;
- invalid file uploads;
- duplicate form submissions.

### 6.3 Public Resume Links

Public resume links must expose only saved public resume versions, not the full private user profile.

Public access must not expose:

- account email unless user included it in the saved resume;
- internal user ID;
- AI usage statistics;
- private drafts;
- deleted resumes.

## 7. Validation Constraints

The application must validate data on both:

- client side;
- server side.

Validation should include:

- required fields;
- email format;
- password rules;
- text length limits;
- file type and MIME type for uploaded photos;
- allowed values for dropdowns;
- safe resume public code format.

Server-side validation is mandatory even if client-side validation exists.

## 8. UI and Frontend Constraints

### 8.1 Interface Localization

The interface must support at least two languages:
- English
- Russian

Users should be able to switch interface language.

Localization strings should be stored in resource files.

### 8.2 Frontend Technology

The course recommends Thymeleaf or JSP for server-side rendering.

However, other frontend technologies are allowed if they preserve architectural clarity.

Preferred MVP plan, mentors allowed using Vue:
- Spring MVC backend exposes REST-like endpoints.
- Vue frontend consumes backend endpoints.
- A minimal Thymeleaf landing page may be used if needed for course compliance.

### 8.3 Responsiveness and Browser Support

The UI must work correctly in modern browsers:

- Chrome
- Firefox
- Edge

The UI should support at least laptop and tablet screen sizes.

## 9. Testing Constraints

The project must include unit tests.

Required:
- JUnit 5 or compatible framework;
- Mockito or similar mocking library;
- tests for Service layer;
- tests for DAO layer;
- at least 50% coverage for Service and DAO layers;
- positive scenarios;
- negative scenarios;
- boundary value tests;
- validation and business rule tests.

Recommended:

- JaCoCo coverage report.

## 10. Logging and Error Handling Constraints

The application must use centralized logging.

Recommended:
- SLF4J + Log4j2

The application must handle exceptions across:
- Controller layer;
- Service layer;
- DAO layer;
- AI integration layer;
- PDF generation layer.

User-facing errors must be readable and should not expose technical implementation details.

## 11. Documentation Constraints

The project must include:
- README.md
- setup instructions
- database initialization instructions
- description of architecture
- description of used design patterns
- Javadoc for public service interfaces and public methods
- `.gitignore`
- remote Git repository

## 12. Design Pattern Constraints

The project must meaningfully use at least two design patterns.

Recommended for this project:

### Strategy

Use for selecting resume generation strategy:

- minimal adaptation;
- balanced adaptation;
- maximum adaptation.

### Builder

Use for building complex AI prompts or resume generation requests.

Additional possible patterns:

- Factory Method for AI provider client creation;
- Template Method for common DAO logic;
- Facade for resume generation workflow;
- Interceptor for logging or access checks.

## 13. Deployment Constraints

### 13.1 MVP Deployment Target

The MVP should be deployable on a VPS server with a purchased domain name.

### 13.2 Docker Compose Deployment

The final MVP deployment should use Docker Compose.

Required containers:
- Java web application container
- Vue frontend container
- PostgreSQL database container

Recommended additional container:
- Flyway migration container

### 13.3 Recommended Production-Friendly Beginner Setup

Recommended deployment architecture:

- `tomcat` container for Spring MVC WAR application
- `nginx` container for built Vue static frontend
- `postgres` container for PostgreSQL database
- `flyway/flyway` container for database migrations
- optional `nginx reverse proxy` or host-level reverse proxy for HTTPS and domain routing

Reason:
Tomcat directly matches Servlet/Spring MVC WAR deployment and is beginner-friendly compared to a full Java EE application server.

### 13.4 Configuration

All environment-specific values must be externalized:
- database URL;
- database username;
- database password;
- OpenRouter API key;
- file storage path;
- allowed frontend origin;
- public base URL;
- active profile or environment name.

Configuration may be provided through:
- `.env` file for Docker Compose;
- environment variables;
- `application.properties` or `application.yml`;
- mounted configuration file.

Sensitive values must not be committed to Git.

## 14. Database Migration Constraint

The MVP should use minimal but useful Flyway database migration support.

Recommended approach:
- keep versioned SQL migration files in Git;
- run migrations automatically through a Flyway Docker Compose service before the Java application starts;
- store schema history in PostgreSQL through Flyway metadata table;
- keep `schema.sql` and `data.sql` compatibility if required by mentors.

This keeps database versioning clear without adding unnecessary complexity to the Java runtime.

## 15. Technical Constraints Summary

| Area | Constraint |
|---|---|
| Backend | Servlets, Spring Core, Spring MVC |
| Database access | Plain JDBC only |
| ORM | Not allowed |
| Database | PostgreSQL |
| Build | Maven |
| Architecture | Layered Architecture + MVC |
| DB scripts | SQL scripts required |
| Migration tool | Minimal Flyway usage recommended |
| Server | Apache Tomcat recommended |
| Frontend | Vue if allowed, Thymeleaf fallback |
| Deployment | Docker Compose on VPS |
| Testing | JUnit 5, Mockito, 50% Service/DAO coverage |
| Security | BCrypt, PreparedStatement, input sanitization |
| Documentation | README, Javadoc, setup guide |
