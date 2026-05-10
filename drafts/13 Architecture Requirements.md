# Architecture Requirements

## 1. Purpose

This document defines the initial architecture requirements for the AI Resume Tailor Capstone project.

The architecture must satisfy two groups of needs:
1. Product needs:
   - resume profile management;
   - AI-based resume adaptation;
   - saved resume versions;
   - public links;
   - PDF export;
   - admin monitoring.

2. Course requirements:
   - Servlets;
   - Spring Core;
   - Spring MVC;
   - JDBC;
   - Layered Architecture;
   - MVC;
   - DAO;
   - Maven;
   - PostgreSQL;
   - i18n;
   - testing;
   - documentation.

## 2. Architecture Style

The application must follow Layered Architecture and MVC.

Required backend layers:
1. Controller layer
2. Service layer
3. DAO layer
4. Model/domain layer
5. Configuration layer
6. Integration layer
7. Utility/support layer

## 3. High-Level Architecture

Recommended MVP architecture:

```text
User Browser
    |
    | HTTP
    v
Vue Frontend / Thymeleaf Fallback
    |
    | HTTP / Form Submit / AJAX
    v
Spring MVC Controllers
    |
    v
Service Layer
    |
    +--> AI Integration Service
    +--> PDF Generation Service
    +--> Public Link Service
    +--> Validation Services
    |
    v
DAO Layer
    |
    v
Custom JDBC Connection Pool
    |
    v
PostgreSQL Database
```

## 4. Deployment Architecture

Recommended Docker Compose deployment:

```text
VPS Server
    |
    +-- reverse proxy / host nginx / HTTPS layer
    |
    +-- Docker Compose network
          |
          +-- frontend container
          |     - Vue static build
          |     - served by nginx
          |
          +-- backend container
          |     - Spring MVC WAR
          |     - deployed on Apache Tomcat
          |
          +-- postgres container
          |     - PostgreSQL database
          |     - persistent volume
          |
          +-- flyway container
                - applies SQL migrations
                - exits after successful migration
```

Required MVP containers:
- Java backend container
- Vue frontend container
- PostgreSQL container

Recommended supporting container:

- Flyway migration container

## 5. Backend Architecture

### 5.1 Controller Layer

Responsibility:

- receive HTTP requests;
- validate request format;
- call Service layer;
- prepare model data or response DTOs;
- return view names or JSON responses;
- handle user-facing errors.

Controllers must not:

- contain business logic;
- call DAOs directly;
- build complex SQL;
- call OpenRouter directly;
- generate PDFs directly.

Suggested packages:

```text
com.airesume.controller
com.airesume.controller.admin
com.airesume.controller.publicview
```

### 5.2 Service Layer

Responsibility:

- implement business logic;
- coordinate DAO operations;
- validate business rules;
- manage transactions;
- call integrations through interfaces;
- prepare data for controllers.

Suggested services:

- UserService
- AuthService
- ProfileService
- ResumeGenerationService
- ResumeDraftService
- SavedResumeService
- PublicResumeService
- PdfService
- AdminUserService
- AiUsageLogService

Public service methods should have meaningful business names and Javadoc comments.

### 5.3 DAO Layer

Responsibility:

- execute SQL queries;
- use PreparedStatement;
- map ResultSet to domain objects;
- provide CRUD operations;
- keep SQL-related logic isolated.

DAO classes must not:

- contain UI logic;
- contain AI logic;
- contain business decision logic;
- manage HTTP sessions.

Suggested DAOs:

- UserDao
- RoleDao
- UserStatusDao
- UserPermissionDao
- ContactDao
- SkillDao
- ExperienceDao
- EducationDao
- CourseDao
- ProjectDao
- PersonalInformationDao
- PositioningDao
- ProfessionalAspirationDao
- UserLanguageDao
- AiModelDao
- ResumeGenerationRequestDao
- GeneratedResumeDraftDao
- SavedResumeDao
- PdfFileDao
- AiUsageLogDao

If the table count must be reduced for the final ERD, some profile entities can be combined into a smaller MVP schema.

### 5.4 Model / Domain Layer

Responsibility:

- represent business entities;
- store entity fields;
- contain minimal domain helper methods where useful.

Domain classes should not depend on:

- Servlet API;
- database connection classes;
- frontend DTOs;
- OpenRouter client classes.

Suggested package:

```text
com.airesume.model
```

### 5.5 DTO Layer

Responsibility:

- transfer data between frontend/controller and backend;
- define request/response shapes;
- protect domain objects from direct exposure.

Suggested DTOs:

- RegisterUserRequest
- LoginRequest
- ProfileSectionDto
- ResumeGenerationRequestDto
- GeneratedResumeDraftDto
- SavedResumeDto
- AdminUserStatsDto

### 5.6 Configuration Layer

Responsibility:

- configure Spring context;
- configure MVC;
- configure i18n;
- configure database;
- configure connection pool;
- configure application properties;
- configure security/session settings.

Suggested package:

```text
com.airesume.config
```

## 6. Frontend Architecture

### 6.1 Preferred Option: Vue Frontend

If mentors allow Vue, the frontend should be implemented as a separate Vue application.

Responsibilities:

- render dashboard;
- render profile forms;
- render resume generation form;
- render resume review screens;
- render resume history;
- render admin panel.

The Vue application should communicate with Spring MVC controllers through HTTP endpoints.

### 6.2 Fallback Option: Thymeleaf + Bootstrap

If mentors do not allow Vue or REST-first architecture, implement all pages with Thymeleaf and Bootstrap.

This fallback is safer for strict Spring MVC course review.

### 6.3 Hybrid Option

A hybrid approach may be used:

- Thymeleaf landing page;
- Vue authenticated application;
- Spring MVC backend.

This should be confirmed with mentors before implementation.

## 7. Database Architecture

### 7.1 Database Type

The system must use PostgreSQL.

### 7.2 Database Access

The system must use plain JDBC through DAO classes.

### 7.3 Connection Management

The system must use a custom thread-safe Connection Pool.

The pool should be used by all DAO classes.

### 7.4 Migration Management

The project should use minimal Flyway support for database schema versioning.

Recommended migration files:

```text
db/migration/V1__initial_schema.sql
db/migration/V2__seed_reference_data.sql
db/migration/V3__seed_demo_data.sql
```

Flyway should be run:

- by Maven plugin during local development; or
- by Docker Compose migration container in deployment.

### 7.5 Transaction Boundaries

Transactions should be controlled in the Service layer.

Examples:

- registering a user;
- generating and saving AI draft;
- saving final resume and public code;
- updating user status and logging admin action.

## 8. AI Integration Architecture

### 8.1 Integration Isolation

OpenRouter integration must be isolated behind an interface.

Suggested interface:

```text
AiClient
```

Possible implementations:

- OpenRouterAiClient
- MockAiClient

### 8.2 Prompt Construction

Prompt construction should be isolated in a dedicated component.

Suggested component:

```text
ResumePromptBuilder
```

### 8.3 Response Parsing

AI response parsing should be isolated from the controller and service orchestration.

Suggested component:

```text
AiResumeResponseParser
```

### 8.4 Mock Mode

The system should support mock AI generation for development and demonstration.

Reason:

External AI provider may be unavailable, slow, or restricted during final review.

## 9. PDF Generation Architecture

PDF generation should be isolated in a dedicated service.

Suggested service:

```text
PdfGenerationService
```

Responsibilities:

- receive saved resume content;
- generate A4-friendly PDF;
- preserve selectable text;
- store file metadata;
- return download path or stream.

PDF generation should not be implemented inside controllers.

## 10. Public Resume Architecture

Public resume access should be separated from authenticated user dashboard logic.

Suggested controller:

```text
PublicResumeController
```

Public routes:

```text
/{username}/{resumeCode}
/{username}/{resumeCode}/download
/{username}/{resumeCode}/json
```

The public controller must validate:

- username exists;
- resume code exists for the user;
- resume is public;
- resume is not soft deleted.

## 11. Admin Architecture

Admin functionality should be separated from normal user functionality.

Suggested package:

```text
com.airesume.controller.admin
com.airesume.service.admin
```

Admin features:

- user list;
- user status management;
- generation permission management;
- user resume review;
- AI usage statistics.

## 12. Security Architecture

### 12.1 Authentication

MVP-safe option:

- session-based authentication.

Optional future/stretched option:

- Google OAuth2, only if mentors confirm it and time allows.

### 12.2 Authorization

Authorization should check:

- user role;
- user status;
- user generation permission;
- resource ownership.

### 12.3 Password Security

Use BCrypt for password hashing.

### 12.4 Input Security

All input should be validated and sanitized.

Required protections:

- PreparedStatement for SQL;
- HTML escaping in views;
- file upload validation;
- duplicate form submission protection;
- length limits for long text fields;
- safe public code validation.

## 13. i18n Architecture

The interface must support at least:

- English;
- Russian.

Recommended implementation:

- resource bundles;
- locale resolver;
- language switcher;
- localized validation messages;
- localized navigation and buttons.

Resume content language selection is separate from interface language.

Example:

- interface language: Russian;
- generated resume language: English.

## 14. Logging Architecture

Use centralized logging.

Recommended:

- SLF4J + Log4j2

Log:

- authentication failures;
- validation errors that may indicate tampering;
- AI provider failures;
- PDF generation failures;
- database exceptions;
- admin actions;
- unexpected exceptions.

Do not log:

- passwords;
- API keys;
- full sensitive resume content unless necessary for debugging and only in development;
- raw OpenRouter keys.

## 15. Design Patterns

The project should use at least two meaningful design patterns.

Recommended patterns:

### 15.1 Strategy

Use for adaptation level logic.

Example strategies:

- MinimalAdaptationStrategy
- BalancedAdaptationStrategy
- MaximumAdaptationStrategy

### 15.2 Builder

Use for building complex prompts.

Example:

- ResumePromptBuilder

### 15.3 Factory Method

Use for selecting AI client implementation.

Example:

- OpenRouter client
- Mock client

### 15.4 Facade

Use for orchestrating resume generation.

Example:

- ResumeGenerationFacade

## 16. Testing Architecture

Tests should cover:

- Service layer business logic;
- DAO layer database operations;
- validation rules;
- public code generation;
- permission checks;
- AI mock integration;
- PDF service behavior at basic level.

Required:

- JUnit 5;
- Mockito or similar;
- at least 50% coverage for Service and DAO layers.

Recommended:

- Testcontainers only if mentors allow and it does not violate dependency minimization;
- otherwise use a dedicated test PostgreSQL database or controlled test schema.

## 17. Recommended Package Structure

```text
com.airesume
  config
  controller
    admin
    publicview
  service
    impl
    admin
  dao
    impl
  model
  dto
  integration
    ai
    pdf
  security
  validation
  util
  exception
```

## 18. MVP Architecture Decision

Recommended MVP architecture:

- Spring MVC backend packaged as WAR
- Apache Tomcat as Java servlet container
- Plain JDBC DAO layer
- Custom thread-safe Connection Pool
- PostgreSQL database
- Flyway SQL migrations
- Vue frontend if mentors allow
- Thymeleaf fallback if Vue is rejected
- Docker Compose deployment on VPS

## 19. Architecture Decision Records to Create Later

Recommended ADR files:

- ADR-001: Use plain JDBC instead of ORM
- ADR-002: Use Apache Tomcat for WAR deployment
- ADR-003: Use Docker Compose for MVP deployment
- ADR-004: Use Flyway for database migrations
- ADR-005: Use Vue frontend with Spring MVC backend
- ADR-006: Use mock AI provider fallback
- ADR-007: Store saved resume content as structured JSON