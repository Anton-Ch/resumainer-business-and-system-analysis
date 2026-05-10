# Initial Requirements

## 1. Functional Requirements

### FR-001: User registration

The system shall allow a new user to register an account using username, email, and password or register via google account (oauth2).

### FR-002: User authentication

The system shall allow registered users to log in and log out.

### FR-003: User role support

The system shall support at least two roles:
- USER
- ADMIN

### FR-004: User status support

The system shall support user statuses:
- ACTIVE
- INACTIVE

Inactive users shall not be allowed to login.

### FR-005: User permission for generations

The system shall support user permission statuses for generations:
- ALLOWED
- FORBIDEN

FORBIDEN users shall not be allowed to generate resumes.

### FR-006: Profile section management

The system shall allow users to create, view, update, and soft delete structured profile section records.

### FR-007: Admin resume review

The system shall allow admins to view generated resumes created by users.

### FR-008: AI model selection

The system shall allow users to choose an AI model from a predefined list.

### FR-009: Vacancy input

The system shall allow users to enter a job description and company information for resume adaptation.

### FR-010: Adaptation level selection

The system shall allow users to choose minimal, balanced, maximum, or all adaptation levels.

### FR-011: Resume language selection

The system shall allow users to generate resumes in Russian, English, or both languages.

### FR-012: Resume generation request

The system shall create a resume generation request containing selected options, vacancy text, and user profile context alongside with predefined system prompt and preconfigured request prompt.

### FR-013: AI resume generation

The system shall send a structured prompt to the selected AI provider and receive generated resume content.

### FR-014: Resume draft preview

The system shall display generated draft resume content for user review before final saving.

### FR-015: Resume draft editing

The system shall allow users to edit generated draft resume fields before saving the final version.

### FR-016: Resume version saving

The system shall allow users to save final resume versions.

### FR-017: Resume history

The system shall allow users to view a list of saved resume versions.

### FR-018: Resume soft delete

The system shall allow users to soft delete their saved resume versions.

### FR-019: Public resume URL

The system shall generate a permanent public URL for each saved resume version.

### FR-020: Public resume access

The system shall allow external viewers to open a saved resume through a public URL without registration.

### FR-021: PDF generation

The system shall generate a print-friendly A4 PDF for each saved resume version.

### FR-022: Selectable PDF text

The generated PDF shall contain selectable text.

### FR-023: Admin user management

The system shall allow admins to view all users and change user status.

### FR-024: Admin user statistics

The system shall allow admins to view all users statistics, including number of created resumes, with detailed breakdown of tokens in + tokens out + total tokens, fields edited before final save, model used.

### FR-025: Interface language switching  
  
The system shall allow users to switch the application interface language between English and Russian.  
  
### FR-026: Profile CRUD through JDBC DAO layer  
  
The system shall allow users to create, view, update, and delete profile-related records using DAO classes based on plain JDBC.  
  
### FR-027: Pagination for long lists  
  
The system shall provide pagination for long lists, including resume history, admin user list, and admin resume list.  
  
### FR-028: Public ATS JSON endpoint  
  
The system shall provide a public JSON endpoint for each public saved resume using the following URL pattern:  
  
`/{username}/{resumeCode}/json`  
  
The endpoint shall return structured resume data suitable for machine parsing.  
  
### FR-029: Database migration execution  
  
The system deployment shall support database initialization and migration through versioned SQL migration scripts.  
  
### FR-030: Docker Compose deployment  
  
The system shall be deployable through Docker Compose with separate services for backend, frontend, and PostgreSQL database.  
  
### FR-031: Admin generation permission management  
  
The system shall allow admins to change whether a user is allowed to generate AI-based resumes.  
  
### FR-032: Client-side and server-side validation  
  
The system shall validate user input on both client and server sides and display clear validation messages.  
  
### FR-033: Duplicate form submission protection  
  
The system shall protect critical form submissions from accidental duplicate submission.  
  
### FR-034: File upload validation  
  
The system shall validate uploaded profile photos by file extension, MIME type, and size.  
  
### FR-035: Service method documentation  
  
The system shall provide Javadoc comments for public service interface methods.

## 2. Non-Functional Requirements

### NFR-001: Security

The system shall protect user accounts with secure password hashing.

### NFR-002: Authorization

The system shall restrict profile and resume management to the owner of the data, except for admin access.

### NFR-003: Data privacy

The system shall not expose private profile data through public links unless it belongs to a saved public resume version.

### NFR-004: Maintainability

The system shall use a layered architecture to separate controllers, services, repositories, domain entities, DTOs, and integrations.

### NFR-005: AI integration isolation

The AI provider integration shall be isolated behind a service interface to allow replacing OpenRouter with another provider or a mock implementation.

### NFR-006: Database normalization

The database schema shall be normalized up to the third normal form.

### NFR-007: PDF usability

The PDF shall be optimized for A4 printing and text selection.

### NFR-008: Extensibility for payments

The system architecture shall allow future integration of subscriptions or pay-per-generation without redesigning core user and resume entities.

### NFR-009: UI simplicity

The interface shall minimize unnecessary actions and use clear labels, consistent layout, and common UI patterns.

### NFR-010: Error handling

The system shall provide clear error messages for failed AI generation, invalid public links, inactive users, and validation errors.

### NFR-011: Extensibility for ai models selection

The system architecture shall allow future integration of user's own API keys usage of main providers such as OpenAI, Anthropic, DeepSeek, Grok for generation resumes.

### NFR-012: Required Java technology stack compliance  
  
The system shall comply with the mandatory Java course technology stack: Servlets, Spring Core, Spring MVC, JDBC, Maven, and PostgreSQL.  
  
### NFR-013: Plain JDBC data access  
  
The system shall use plain JDBC for database access. ORM frameworks such as Hibernate, JPA, and Spring Data JPA shall not be used.  
  
### NFR-014: Custom thread-safe Connection Pool  
  
The system shall use a manually implemented thread-safe JDBC Connection Pool.  
  
### NFR-015: DAO pattern compliance  
  
The system shall use the DAO pattern for database operations. Each DAO shall provide CRUD operations and required custom queries for its entity.  
  
### NFR-016: SQL injection protection  
  
All SQL queries shall use PreparedStatement or equivalent safe parameter binding. SQL string concatenation with user input shall not be used.  
  
### NFR-017: Database migration maintainability  
  
The system shall keep database schema changes in versioned SQL migration files. Minimal Flyway usage is recommended for applying migrations consistently across local and VPS environments.  
  
### NFR-018: Dockerized deployment  
  
The MVP shall be deployable through Docker Compose using separate containers for Java backend, Vue frontend, and PostgreSQL database.  
  
### NFR-019: VPS deployment readiness  
  
The MVP shall be ready for deployment on a VPS server with a custom domain name.  
  
### NFR-020: Centralized logging  
  
The system shall use centralized logging through SLF4J and Log4j2 or an equivalent logging stack.  
  
### NFR-021: Test coverage  
  
The system shall include unit tests for Service and DAO layers with at least 50% coverage.  
  
### NFR-022: Cross-browser compatibility  
  
The user interface shall work correctly in modern versions of Chrome, Firefox, and Edge.  
  
### NFR-023: Responsive interface  
  
The user interface shall display correctly on laptop and tablet screen sizes.  
  
### NFR-024: Dependency minimization  
  
The system shall include only necessary and actively used dependencies. Outdated, unstable, or unused dependencies shall be avoided.  
  
### NFR-025: Javadoc documentation  
  
Public service interfaces, public service methods, and important public classes shall include Javadoc comments.  
  
### NFR-026: Design pattern usage  
  
The system shall meaningfully apply at least two design patterns and document why they were used.  
  
### NFR-027: Configuration externalization  
  
Environment-specific parameters shall be stored outside source code in configuration files, environment variables, or Docker Compose `.env` files.  
  
### NFR-028: Sensitive data protection  
  
Passwords, API keys, database credentials, and other sensitive values shall not be committed to Git and shall not be logged.