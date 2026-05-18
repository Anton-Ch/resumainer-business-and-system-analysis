<!-- BABOK 7.1 — Data Dictionary | Проект: resumainer | 2026-05-17 -->

# DD-001 — ResumAIner MVP Data Dictionary — All Entities

| Атрибут | Значение |
|---------|----------|
| Тип | Data Dictionary |
| Проект | resumainer |
| Источник | governance_plans/reports/docs/04_domain-and-data-model/dbml_erd.md |
| Сущностей | 26 |
| Статус | draft |
| Версия | 1.0 |
| Дата | 2026-05-17 |

---

## Сущность: role

**Описание:** User role lookup. Defines system access level for each user account.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(20) | Да | UNIQUE, NOT NULL | Role code: USER, ADMIN |
| `name` | Varchar(50) | Да | NOT NULL | Display name: User, Admin |

**Бизнес-правила:**
- Seeded at deployment, not user-managed
- USER and ADMIN are the only valid values


## Сущность: user_status

**Описание:** Account status lookup. Controls whether a user can authenticate and use the system.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(20) | Да | UNIQUE, NOT NULL | Status code: ACTIVE, BLOCKED |
| `name` | Varchar(50) | Да | NOT NULL | Display name: Active, Blocked |

**Бизнес-правила:**
- BLOCKED status prevents login and generation
- User deletion uses soft-delete (is_deleted flag), not status change


## Сущность: user_permission

**Описание:** Generation permission lookup. Controls whether a user is allowed to generate resumes via AI.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(20) | Да | UNIQUE, NOT NULL | Permission code: ALLOWED, FORBIDDEN |
| `name` | Varchar(50) | Да | NOT NULL | Display name: Allowed, Forbidden |

**Бизнес-правила:**
- Admin sets permission per user in User Details page
- FORBIDDEN users can still log in and manage profile but cannot generate


## Сущность: response_status

**Описание:** Generation response status lookup. Tracks the lifecycle of an AI generation response from initial output to user approval.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(20) | Да | UNIQUE, NOT NULL | Status code: DRAFT, FINALIZED |
| `name` | Varchar(50) | Да | NOT NULL | Display name: Draft, Finalized |

**Бизнес-правила:**
- DRAFT = AI generated, user has not completed review
- FINALIZED = user reviewed and approved; triggers PDF generation
- Only FINALIZED responses can create a saved_resume record


## Сущность: language

**Описание:** Supported interface and resume languages lookup.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(10) | Да | UNIQUE, NOT NULL | Language code: EN, RU |
| `name` | Varchar(50) | Да | NOT NULL | Display name: English, Russian |

**Бизнес-правила:**
- Used for both interface language (DEC-023) and resume language (DEC-029)
- Dropdown selection ensures valid language identifiers for AI model


## Сущность: adaptation_level

**Описание:** Resume adaptation intensity lookup. Controls how aggressively the AI adapts the resume content to the target vacancy.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(20) | Да | UNIQUE, NOT NULL | Adaptation code: MINIMAL, BALANCED, MAXIMUM |
| `name` | Varchar(50) | Да | NOT NULL | Display name: Minimal, Balanced, Maximum |
| `description` | Text | Нет |  | Explanation of adaptation behavior at this level |

**Бизнес-правила:**
- Used in both generation requests and saved resumes for traceability
- Adaptation level affects AI prompt instructions


## Сущность: work_format

**Описание:** Preferred work format lookup. Normalized values for multi-select work format preference (DEC-022).

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `code` | Varchar(30) | Да | UNIQUE, NOT NULL | Format code: full-time, part-time, rotational_schedule, internship, offline, remote, hybrid, on_project_site |
| `name` | Varchar(50) | Да | NOT NULL | Display name: Full-time, Part-time, Remote, etc. |

**Бизнес-правила:**
- Values are predefined and seeded
- Used through user_work_format junction table (M:N)
- Frontend renders as checkbox group


## Сущность: resume_template

**Описание:** Resume HTML template catalog (Post-MVP ready). Each record represents a template layout for resume PDF generation.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `name` | Varchar(100) | Да | NOT NULL | Template display name: Default Two-Page Template |
| `html_file_path` | Varchar(500) | Да | NOT NULL | File system path to template HTML file |
| `description` | Text | Нет |  | Template description and use cases |
| `is_active` | Boolean | Да | NOT NULL, DEFAULT true | Whether template is available for use |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Post-MVP feature: users choose template (ATS-friendly, Human-friendly)
- MVP: single default template seeded in data.sql
- saved_resume.template_id FK is nullable for MVP backward compatibility


## Сущность: users

**Описание:** Registered user accounts. Stores authentication data and access control references. Profile data is stored in separate profile tables (DEC-021).

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `username` | Varchar(100) | Да | UNIQUE, NOT NULL | URL-friendly username for public resume links |
| `email` | Varchar(255) | Да | UNIQUE, NOT NULL | Registration email (not exposed on resumes) |
| `password_hash` | Varchar(255) | Да | NOT NULL | BCrypt password hash |
| `role_id` | Integer | Да | FK → role.id, NOT NULL | User role reference |
| `status_id` | Integer | Да | FK → user_status.id, NOT NULL | Account status reference |
| `permission_id` | Integer | Да | FK → user_permission.id, NOT NULL | Generation permission reference |
| `default_language_id` | Integer | Нет | FK → language.id | Default interface language |
| `secondary_language_id` | Integer | Нет | FK → language.id | Secondary interface language |
| `is_privileged` | Boolean | Да | NOT NULL, DEFAULT false | Privileged user — can access hidden AI models (DEC-024) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Account creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last profile update timestamp |
| `deleted_at` | Timestamp | Нет |  | Soft-delete timestamp |
| `is_deleted` | Boolean | Да | NOT NULL, DEFAULT false | Soft-delete flag |

**Бизнес-правила:**
- Table name is plural (users) to avoid PostgreSQL reserved word conflict
- Email is used for authentication; resume_email in contact_detail is for resume display
- Username is part of public resume URL: /{username}/{public_code}
- Deactivation uses status_id = BLOCKED, not record deletion
- is_privileged grants access to hidden/payed AI models (DEC-024)


## Сущность: contact_detail

**Описание:** User profile contact information. One-to-one with users. Contains all resume-relevant contact data (DEC-021).

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, UNIQUE, NOT NULL | User reference (1:1) |
| `full_name` | Varchar(255) | Да | NOT NULL | User's full name for resume display |
| `phone` | Varchar(50) | Нет |  | Contact phone number |
| `resume_email` | Varchar(255) | Нет |  | Email shown on resumes (may differ from account email) |
| `location` | Varchar(255) | Нет |  | City and country for resume |
| `professional_title` | Varchar(255) | Нет |  | Professional headline: Business Analyst, Junior Java Developer |
| `linkedin_url` | Varchar(150) | Нет |  | LinkedIn profile URL (DEC-026: max 150 chars for vanity URL) |
| `portfolio_url` | Varchar(500) | Нет |  | Portfolio or personal website URL |
| `telegram` | Varchar(100) | Нет |  | Telegram username |
| `whatsapp` | Varchar(50) | Нет |  | WhatsApp phone number |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- One user has exactly one contact_detail record (created on registration)
- full_name is required for resume generation
- linkedin_url max 150 chars per LinkedIn vanity URL limit (DEC-026)


## Сущность: work_experience

**Описание:** User work history records. Each entry represents one job position held by the user.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User reference |
| `job_title` | Varchar(255) | Да | NOT NULL | Position/job title |
| `company_name` | Varchar(255) | Да | NOT NULL | Employer name |
| `description` | Text | Да | NOT NULL | Role description: responsibilities, achievements |
| `location` | Varchar(255) | Нет |  | Work location: city, remote |
| `start_date` | Date | Да | NOT NULL | Employment start date |
| `end_date` | Date | Нет |  | Employment end date; NULL = current job |
| `is_current` | Boolean | Да | NOT NULL, DEFAULT false | Flag: currently employed here |
| `company_url` | Varchar(500) | Нет |  | Post-MVP: company profile URL (DEC-027) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Auto-sorted by start_date DESC, end_date DESC NULLS FIRST (DEC-012)
- description is confirmed required for useful resume generation
- is_current = true if end_date is NULL
- company_url is Post-MVP: not used in MVP generation flow


## Сущность: education

**Описание:** Formal education records: universities, colleges, degrees, programs.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User reference |
| `institution_name` | Varchar(255) | Да | NOT NULL | School, university, or institution name |
| `degree` | Varchar(100) | Да | NOT NULL | Degree or qualification: Bachelor, Master, PhD, etc. |
| `field_of_study` | Varchar(255) | Нет |  | Major or specialization: Information Systems |
| `education_type` | Varchar(150) | Нет |  | Optional: University, College, etc. |
| `description` | Text | Нет |  | Additional education details |
| `start_date` | Date | Да | NOT NULL | Study start date |
| `end_date` | Date | Нет |  | Graduation date; NULL = still studying; allows future dates |
| `location` | Varchar(255) | Нет |  | Institution location |
| `gpa_grade` | Varchar(20) | Нет |  | GPA or grade (text for flexible format) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- start_date (year) is required per confirmed elicitation decision
- end_date can be NULL (still studying) or in the future (planned graduation)
- degree field is free text to allow 'Other' values


## Сущность: project

**Описание:** Projects and volunteering records. Captures personal, academic, professional, and volunteer experience.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User reference |
| `project_name` | Varchar(255) | Да | NOT NULL | Project or activity name |
| `role` | Varchar(255) | Нет |  | User's role in project; code default = Participant (DEC-031) |
| `description` | Text | Да | NOT NULL | Project description and contributions |
| `location` | Varchar(255) | Нет |  | Project location |
| `start_date` | Date | Нет |  | Project start date |
| `end_date` | Date | Нет |  | End date; NULL = ongoing; allows future dates |
| `project_url` | Varchar(500) | Нет |  | Project URL or repository link |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Volunteering handled together with projects under the same entity for MVP simplicity
- If role is NULL, code defaults to Participant / Участник (DEC-031)
- end_date allows future dates for planned project completions


## Сущность: course_certificate

**Описание:** Courses, certificates, and professional training records. Mandatory section per DEC-018.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User reference |
| `name` | Varchar(255) | Да | NOT NULL | Course or certificate name |
| `provider` | Varchar(255) | Да | NOT NULL | Provider or issuer: Coursera, Udemy |
| `description` | Text | Нет |  | Course description and details |
| `course_focus` | Varchar(255) | Нет |  | Optional: key skills/topics covered (user input) |
| `start_date` | Date | Да | NOT NULL | Course start date |
| `end_date` | Date | Нет |  | Completion date; NULL = in progress |
| `credential_url` | Varchar(500) | Нет |  | Link to credential or certificate verification |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Mandatory section per DEC-018 — target users are professionals with completed courses
- Two-page template limits: Page 1 max 7 most relevant courses; Page 2 adjusts based on work experience count (DEC-019)
- course_focus is user-provided, not AI-generated


## Сущность: additional_profile_info

**Описание:** Simplified additional profile data (DEC-013). Single table replaces 7 normalized tables for MVP. Stores free-text fields, resume language preferences, and personal information.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, UNIQUE, NOT NULL | User reference (1:1) |
| `skills` | Text | Нет |  | Free-text: skills list (comma-separated or free form) |
| `languages` | Text | Нет |  | Free-text: languages with proficiency levels |
| `professional_aspirations` | Text | Нет |  | Target career direction and goals |
| `achievements` | Text | Нет |  | Key professional and personal achievements |
| `general_information` | Text | Нет |  | AI context: any job-related info to help resume generation |
| `default_resume_language_id` | Integer | Нет | FK → language.id | Default resume generation language (DEC-029) |
| `additional_resume_language_id` | Integer | Нет | FK → language.id | Additional resume generation language (DEC-029) |
| `ready_for_relocation` | Varchar(20) | Нет |  | Relocation readiness: Yes, No, Not specified |
| `ready_for_business_trips` | Varchar(20) | Нет |  | Business trip readiness: Yes, No, Not specified |
| `date_of_birth` | Date | Нет |  | Date of birth |
| `citizenship` | Varchar(150) | Нет |  | Optional: user's citizenship |
| `photo_file_path` | Varchar(500) | Нет |  | Profile photo file path (optional per confirmed requirement) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Simplified MVP design (DEC-013): skills, languages, aspirations, achievements are text fields, not separate tables
- Resume language IDs are FKs to language table (DEC-029) — dropdown selection on frontend
- Relocation/travel readiness uses controlled dropdown values
- Photo is optional despite wireframe asterisk (confirmed decision)
- preferred_work_format moved to separate junction table user_work_format (DEC-022)


## Сущность: user_work_format

**Описание:** Junction table for many-to-many relationship between users and preferred work formats (DEC-022).

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User reference |
| `work_format_id` | Integer | Да | FK → work_format.id, NOT NULL | Work format reference |

**Бизнес-правила:**
- Composite unique constraint on (user_id, work_format_id)
- One user can have multiple work formats (checkbox group on frontend)
- Follows 3NF — enables querying by format


## Сущность: ai_model

**Описание:** AI provider model configurations. Stores provider connection details, API keys, and visibility settings.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `provider` | Varchar(255) | Да | NOT NULL | AI provider name: OpenRouter |
| `model_code` | Varchar(255) | Да | NOT NULL | Provider model code: deepseek/deepseek-v4-pro |
| `display_name` | Varchar(255) | Да | NOT NULL | Human-readable model display name |
| `provider_api_url` | Varchar(500) | Нет |  | API base URL for provider |
| `api_key_encrypted` | Varchar(512) | Нет |  | Encrypted API key (NFR-001) |
| `is_active` | Boolean | Да | NOT NULL, DEFAULT true | Whether model is available for generation |
| `is_paid` | Boolean | Да | NOT NULL, DEFAULT false | Flag: model requires payment |
| `is_hidden` | Boolean | Да | NOT NULL, DEFAULT false | Hidden from non-privileged users (DEC-024) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- API key is masked after saving, never logged (NFR-001)
- is_paid marks paid models for admin awareness
- is_hidden controls visibility to non-privileged users (DEC-024)
- Admin manages Visibility dropdown (Visible/Hidden) in AI Model Details page


## Сущность: resume_generation_request

**Описание:** User's request to generate an adapted resume. Captures all input parameters for traceability and re-generation.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User who submitted the request |
| `ai_model_id` | Integer | Да | FK → ai_model.id, NOT NULL | AI model used for generation |
| `vacancy_description` | Text | Да | NOT NULL | Vacancy description pasted by user |
| `company_description` | Text | Нет |  | Optional company context |
| `additional_comments` | Text | Нет |  | Additional instructions for AI |
| `include_cover_letter` | Boolean | Да | NOT NULL, DEFAULT false | Whether to generate cover letter |
| `language_id` | Integer | Да | FK → language.id, NOT NULL | Target resume language |
| `adaptation_level_id` | Integer | Да | FK → adaptation_level.id, NOT NULL | Adaptation intensity |
| `language_mode` | Varchar(20) | Да | NOT NULL, DEFAULT 'default' | Language mode: 'default', 'additional', 'both' |
| `status` | Varchar(30) | Да | NOT NULL, DEFAULT 'pending' | Processing status: pending, processing, completed, failed |
| `error_message` | Text | Нет |  | Error details if generation failed |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Request creation timestamp |
| `completed_at` | Timestamp | Нет |  | Generation completion timestamp |

**Бизнес-правила:**
- Each request produces exactly one response (1:1)
- Status transitions: pending → processing → completed | failed
- Vacancy description is required — it's the core input for AI adaptation
- include_cover_letter flag triggers additional AI output (DEC-016)


## Сущность: resume_generation_response

**Описание:** AI generation output and user-reviewed edits. Status tracks lifecycle: DRAFT (AI output) → FINALIZED (user approved).

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `generation_request_id` | Integer | Да | FK → resume_generation_request.id, UNIQUE, NOT NULL | Source request (1:1) |
| `status_id` | Integer | Да | FK → response_status.id, NOT NULL | Response status: DRAFT or FINALIZED |
| `professional_summary` | Text | Нет |  | AI-generated and user-reviewed professional summary |
| `professional_aspirations` | Text | Нет |  | AI-generated and user-reviewed career aspirations |
| `cover_letter` | Text | Нет |  | Generated and user-edited cover letter (DEC-016) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Response creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Only FINALIZED responses can create a saved_resume record
- cover_letter stored here (not in saved_resume) because it's AI-generated output (DEC-028)
- Multi-value sections (experience, education, etc.) stored in generation_response_* tables


## Сущность: generation_response_experience

**Описание:** Reviewed and edited work experience items from a generation response. Each row represents one work entry in the final resume.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Parent generation response |
| `job_title` | Varchar(255) | Да | NOT NULL | Job title in generated resume |
| `company_name` | Varchar(255) | Да | NOT NULL | Company name in generated resume |
| `description` | Text | Да | NOT NULL | AI-generated and user-reviewed description |
| `location` | Varchar(255) | Нет |  | Work location in generated resume |
| `is_first_page` | Boolean | Да | NOT NULL, DEFAULT true | Page 1 (primary) or Page 2 (additional) placement (DEC-030) |
| `start_date` | Date | Да | NOT NULL | Start date in generated resume |
| `end_date` | Date | Нет |  | End date; NULL = current |
| `order_in_resume` | Integer | Да | NOT NULL, DEFAULT 0 | Fixed display order (DEC-030) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- start_date is required — work experience without start date has no resume value
- is_first_page=true → primary experience on page 1; false → Additional work experience on page 2
- order_in_resume is fixed (not user-reorderable) as per DEC-030


## Сущность: generation_response_education

**Описание:** Reviewed education items from a generation response. Compact format for resume template.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Parent generation response |
| `institution_name` | Varchar(255) | Да | NOT NULL | Institution name in generated resume |
| `degree` | Varchar(100) | Да | NOT NULL | Degree in generated resume |
| `field_of_study` | Varchar(255) | Нет |  | Field of study in generated resume |
| `start_date` | Date | Да | NOT NULL | Start date in generated resume |
| `end_date` | Date | Нет |  | End date in generated resume |
| `location` | Varchar(255) | Нет |  | Institution location |
| `gpa_grade` | Varchar(20) | Нет |  | GPA or grade |
| `order_in_resume` | Integer | Да | NOT NULL, DEFAULT 0 | Fixed display order (DEC-030) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- No description field — education uses compact format in resume template (DEC-030)
- order_in_resume is fixed (not user-reorderable) as per DEC-030


## Сущность: generation_response_course

**Описание:** Reviewed course/certificate items from a generation response. Compact format for resume template.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Parent generation response |
| `name` | Varchar(255) | Да | NOT NULL | Course name in generated resume |
| `provider` | Varchar(255) | Да | NOT NULL | Provider name in generated resume |
| `is_first_page` | Boolean | Да | NOT NULL, DEFAULT true | Page 1 (primary) or Page 2 (additional) placement (DEC-030) |
| `course_focus` | Varchar(255) | Нет |  | Skills/topics covered |
| `order_in_resume` | Integer | Да | NOT NULL, DEFAULT 0 | Fixed display order (DEC-030) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- No description field — courses use compact format in resume template (DEC-030)
- is_first_page=true → primary courses on page 1; false → additional courses on page 2
- order_in_resume is fixed (not user-reorderable) as per DEC-030


## Сущность: generation_response_project

**Описание:** Reviewed project/volunteering items from a generation response.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Parent generation response |
| `project_name` | Varchar(255) | Да | NOT NULL | Project name in generated resume |
| `role` | Varchar(255) | Нет |  | User's role in project |
| `description` | Text | Да | NOT NULL | Project description in generated resume |
| `location` | Varchar(255) | Нет |  | Project location |
| `start_date` | Date | Да | NOT NULL | Project start date |
| `end_date` | Date | Нет |  | Project end date |
| `order_in_resume` | Integer | Да | NOT NULL, DEFAULT 0 | Fixed display order (DEC-030) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- start_date is required — project without start date has no resume value
- order_in_resume is fixed (not user-reorderable) as per DEC-030


## Сущность: generation_response_skill

**Описание:** Reviewed skill groups from a generation response. Skills are organized into groups with individual skill names.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Parent generation response |
| `skill_group` | Varchar(255) | Да | NOT NULL | Skill group name: Leadership, Reporting |
| `skill_name` | Varchar(255) | Да | NOT NULL | Individual skill: Team Leadership, Process Improvement |
| `order_in_resume` | Integer | Да | NOT NULL, DEFAULT 0 | Fixed display order (DEC-030) |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Record creation timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Example structure: group 'Leadership' contains skills 'Team Leadership', 'Process Improvement'
- Skills are grouped for organized display in resume template
- order_in_resume is fixed (not user-reorderable) as per DEC-030


## Сущность: saved_resume

**Описание:** Finalized saved resume record. Created after user approves (FINALIZEs) the generation response. Stores metadata and PDF file path.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | Resume owner |
| `generation_request_id` | Integer | Да | FK → resume_generation_request.id, NOT NULL | Source generation request |
| `response_id` | Integer | Да | FK → resume_generation_response.id, NOT NULL | Finalized response |
| `template_id` | Integer | Нет | FK → resume_template.id | Post-MVP: template used for PDF |
| `adaptation_level_id` | Integer | Да | FK → adaptation_level.id, NOT NULL | Adaptation level used |
| `language_id` | Integer | Да | FK → language.id, NOT NULL | Resume language |
| `title` | Varchar(255) | Да | NOT NULL | Resume title for user identification |
| `public_code` | Varchar(4) | Да | NOT NULL | 4-char public code for sharing URL |
| `pdf_file_path` | Varchar(500) | Нет |  | Server path to generated PDF file |
| `is_deleted` | Boolean | Да | NOT NULL, DEFAULT false | Soft-delete flag |
| `deleted_at` | Timestamp | Нет |  | Soft-delete timestamp |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Save timestamp |
| `updated_at` | Timestamp | Нет |  | Last update timestamp |

**Бизнес-правила:**
- Generated only from FINALIZED responses
- public_code: 4 chars from QWRYUPASEDFGHJKZXCVBNM, no repeated letters, unique per user (DEC-019)
- Public URL pattern: /{username}/{public_code}
- Composite unique index on (user_id, public_code)
- All resumes are public by design — is_public flag not needed (DEC-028)
- pdf_file_path replaces separate pdf_file table (DEC-017)
- Top-level text fields (professional_summary, professional_aspirations, cover_letter) stored in resume_generation_response


## Сущность: ai_usage_log

**Описание:** AI token usage log. One row per API call. Powers statistics on User Home and Admin Home dashboards.

| Атрибут | Тип данных | Обязательный | Ограничения | Описание |
|---------|-----------|--------------|-------------|----------|
| `id` | Integer | Да | PK, AUTO_INCREMENT | Unique identifier |
| `user_id` | Integer | Да | FK → users.id, NOT NULL | User who made the request |
| `ai_model_id` | Integer | Да | FK → ai_model.id, NOT NULL | AI model used |
| `generation_request_id` | Integer | Нет | FK → resume_generation_request.id | Related generation request |
| `generation_response_id` | Integer | Нет | FK → resume_generation_response.id | Related generation response |
| `tokens_sent` | Integer | Да | NOT NULL, DEFAULT 0 | Prompt/input tokens |
| `tokens_generated` | Integer | Да | NOT NULL, DEFAULT 0 | Completion/output tokens |
| `cost` | Decimal | Нет |  | Post-MVP: request cost |
| `created_at` | Timestamp | Да | NOT NULL, DEFAULT now() | Log entry timestamp |

**Бизнес-правила:**
- One row per API call for granular tracking
- token counters power dashboard stats: Total tokens sent/generated
- cost field reserved for Post-MVP billing/analytics

---

## Трассировка

| Связь | Артефакт |
|-------|----------|
| Источник (4.3) | governance_plans/reports/docs/04_domain-and-data-model/dbml_erd.md |
| Реестр (5.1) | регистрация автоматическая |