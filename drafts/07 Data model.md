# Initial Data Model

## 1. Database Design Goal

The database should store structured user profile data, resume generation requests, generated resume versions, public resume links, AI model configuration, and admin-related user status and statistics information.

The schema should be normalized up to the third normal form.

## 2. Main Entities

### 2.1 User

Represents a registered account.

Possible attributes:
- id
- username
- email
- password_hash
- role_id
- status_id
- permission_id
- default_language_id
- secondary_language_id
- created_at
- updated_at
- deleted_at
- is_deleted

Relationships:
- One User has one Role.
- One User has one UserStatus.
- One User may have many ProfileSections.
- One User may have many ResumeGenerationRequests.
- One User may have many SavedResumes.

### 2.2 Role

Represents user role.

Possible values:
- USER
- ADMIN

Attributes:
- id
- code
- name

Relationships:
- One Role may be assigned to many Users.

### 2.3 UserStatus

Represents account status.

Possible values:
- ACTIVE
- INACTIVE

Attributes:
- id
- code
- name

Relationships:
- One UserStatus may be assigned to many Users.

### 2.4 UserPermission

Represents account permission for generation.

Possible values:
- ALLOWED
- FORBIDDEN

Attributes:
- id
- code
- name

Relationships:
- One UserPermission may be assigned to many Users.
### 2.5 Language

Represents supported content languages.

Possible values:
- EN
- RU

Attributes:
- id
- code
- name

Relationships:
- One Language may be used by many profile content records.
- One Language may be used by many resume versions.

### 2.6 Profile Data Modeling Decision

The generic ProfileSectionType / ProfileSection / ProfileSectionContent model was considered but is not used in the current MVP data model.

Instead, the system uses concrete profile-related entities. This approach makes the database model easier to understand, review, implement, and demonstrate in the Capstone project.

Reasons for this decision:
- The Capstone review requires clear entities, relationships, cardinality, and attributes.
- Concrete profile entities are easier to map to Java domain classes and JPA repositories.
- Separate tables make CRUD operations and validation rules easier to implement.
- The model becomes more readable for reviewers who need to understand the business meaning of each table.
- The future product may still introduce a more generic profile section model if dynamic profile sections become necessary.

The following abstract entities are intentionally excluded from the current MVP model:
- ProfileSectionType
- ProfileSection
- ProfileSectionContent
- ProfessionalSummary

The ProfessionalSummary entity is not created separately because the current model can store candidate positioning and short description through the Positioning entity.


### 2.7 Concrete Profile Entities

The system stores user profile data through separate concrete entities. Each entity represents a meaningful resume-related profile part.

#### 2.7.1 Contact

Represents one user contact method.

Possible attributes:
- id
- user_id
- type
- detail
- created_at
- updated_at

Possible contact types:
- phone
- email
- linkedin
- telegram
- whatsapp
- github
- portfolio
- website

Relationships:
- One Contact belongs to one User.
- One User may have many Contacts.

#### 2.7.2 Skill

Represents one professional skill of a user.

Possible attributes:
- id
- user_id
- title
- description
- sort_order
- created_at
- updated_at

Relationships:
- One Skill belongs to one User.
- One User may have many Skills.

#### 2.7.3 Value

Represents one professional or personal value that may be relevant for resume positioning.

Possible attributes:
- id
- user_id
- title
- description
- sort_order
- created_at
- updated_at

Relationships:
- One Value belongs to one User.
- One User may have many Values.

#### 2.7.4 Achievement

Represents one user achievement that may be used in adapted resumes.

Possible attributes:
- id
- user_id
- title
- description
- achievement_date
- related_context
- created_at
- updated_at

Relationships:
- One Achievement belongs to one User.
- One User may have many Achievements.

#### 2.7.5 Experience

Represents one work experience record.

Possible attributes:
- id
- user_id
- job_title
- company_name
- description
- employment_start
- employment_end
- is_current
- location
- created_at
- updated_at

Relationships:
- One Experience belongs to one User.
- One User may have many Experience records.

#### 2.7.6 Education

Represents one formal education record.

Possible attributes:
- id
- user_id
- degree
- specialization
- provider_name
- description
- study_start
- study_end
- location
- created_at
- updated_at

Possible education degree values:
- school
- college
- bachelor
- master
- phd
- certificate
- other

Relationships:
- One Education record belongs to one User.
- One User may have many Education records.

#### 2.7.7 Course

Represents one course or certificate.

Possible attributes:
- id
- user_id
- title
- provider
- course_description
- completion_date
- expiration_date
- certificate_url
- created_at
- updated_at

Relationships:
- One Course belongs to one User.
- One User may have many Courses.

#### 2.7.8 Project

Represents one professional, educational, volunteer, or portfolio project.

Possible attributes:
- id
- user_id
- title
- description
- project_url
- start_date
- end_date
- location
- created_at
- updated_at

Relationships:
- One Project belongs to one User.
- One User may have many Projects.

#### 2.7.9 Hobby

Represents one user hobby that may be included in selected resume versions if relevant.

Possible attributes:
- id
- user_id
- title
- description
- sort_order
- created_at
- updated_at

Relationships:
- One Hobby belongs to one User.
- One User may have many Hobbies.

#### 2.7.10 PersonalInformation

Represents general personal information that is usually stored once per user.

Possible attributes:
- id
- user_id
- city
- country
- ready_to_relocate
- ready_for_business_trips
- additional_information
- created_at
- updated_at

Relationships:
- One PersonalInformation record belongs to one User.
- One User has zero or one PersonalInformation record.

#### 2.7.11 Positioning

Represents one professional positioning variant of the user.

Examples:
- Business Analyst
- Junior Java Developer
- System Analyst
- Backend Developer

Possible attributes:
- id
- user_id
- title
- description
- is_primary
- created_at
- updated_at

Relationships:
- One Positioning record belongs to one User.
- One User may have many Positioning records.

#### 2.7.12 ProfessionalAspiration

Represents the user's professional goals and target career direction.

Possible attributes:
- id
- user_id
- target_role
- target_industry
- description
- created_at
- updated_at

Relationships:
- One ProfessionalAspiration belongs to one User.
- One User may have many ProfessionalAspirations.

#### 2.7.13 UserLanguage

Represents one language known by the user and the user's proficiency level in that language.

Possible attributes:
- id
- user_id
- language_id
- proficiency
- created_at
- updated_at

The proficiency field is stored as varchar to allow flexible values such as:
- A1
- A2
- B1
- B2
- C1
- C2
- Native
- Fluent
- Intermediate

Relationships:
- One UserLanguage record belongs to one User.
- One UserLanguage record references one Language.
- One User may have many UserLanguage records.
- One Language may be referenced by many UserLanguage records.

Suggested constraint:
- The pair user_id + language_id should be unique.

### 2.8 Profile Data Localization Approach

The current MVP model does not store localized content through the generic ProfileSectionContent table.

For the MVP, user profile data is stored through concrete profile entities. Multilingual resume generation is handled during the AI generation process. The AI can generate the final resume in the selected target language based on available profile data and the vacancy description.

This decision keeps the first version of the system simpler and easier to implement.

Future versions may introduce localized profile content if needed. Possible future approaches may include:
- separate translation tables for each major profile entity;
- generic localized content tables;
- additional language-specific columns;
- AI-assisted translation workflow with manual review.

### 2.9 AiModel

Represents available AI models.

Attributes:
- id
- provider
- model_code
- display_name
- is_active
- created_at
- updated_at

Relationships:
- One AiModel may be used in many ResumeGenerationRequests.
- One AiModel may be used in many TranslationRequests.

### 2.10 AdaptationLevel

Represents resume adaptation intensity.

Possible values:
- MINIMAL
- BALANCED
- MAXIMUM

Attributes:
- id
- code
- name
- description

Relationships:
- One AdaptationLevel may be used in many ResumeGenerationRequests.
- One AdaptationLevel may be used in many SavedResumes.

### 2.11 ResumeGenerationRequest

Represents one user request to generate resume content.

Attributes:
- id
- user_id
- ai_model_id
- vacancy_description
- company_information
- requested_language_mode
- requested_adaptation_mode
- status
- error_message
- created_at
- completed_at

Relationships:
- One ResumeGenerationRequest belongs to one User.
- One ResumeGenerationRequest uses one AiModel.
- One ResumeGenerationRequest may produce many GeneratedResumeDrafts.

### 2.12 GeneratedResumeDraft

Represents AI-generated draft content before final saving.

Attributes:
- id
- resume_generation_request_id
- adaptation_level_id
- language_id
- generated_content
- created_at
- updated_at

Relationships:
- One GeneratedResumeDraft belongs to one ResumeGenerationRequest.
- One GeneratedResumeDraft has one AdaptationLevel.
- One GeneratedResumeDraft has one Language.
- One GeneratedResumeDraft may become one SavedResume.

### 2.13 SavedResume

Represents a final saved resume version.

Attributes:
- id
- user_id
- source_draft_id
- adaptation_level_id
- language_id
- title
- final_content
- public_code
- is_public
- is_deleted
- created_at
- updated_at
- deleted_at

Relationships:
- One SavedResume belongs to one User.
- One SavedResume may be based on one GeneratedResumeDraft.
- One SavedResume has one AdaptationLevel.
- One SavedResume has one Language.
- One SavedResume may have one or many PdfFiles.

### 2.14 PdfFile

Represents generated PDF file metadata.

Attributes:
- id
- saved_resume_id
- file_path
- file_name
- mime_type
- file_size
- created_at
- is_deleted

Relationships:
- One PdfFile belongs to one SavedResume.



## 3. Important Relationships and Cardinality

| Relationship                                    | Cardinality        |
| ----------------------------------------------- | ------------------ |
| User to ProfileSection                          | One-to-many        |
| User to ResumeGenerationRequest                 | One-to-many        |
| ResumeGenerationRequest to GeneratedResumeDraft | One-to-many        |
| GeneratedResumeDraft to SavedResume             | Zero-or-one to one |
| User to SavedResume                             | One-to-many        |
| SavedResume to PdfFile                          | One-to-many        |
| AiModel to ResumeGenerationRequest              | One-to-many        |
| Role to User                                    | One-to-many        |
| UserStatus to User                              | One-to-many        |

## 4. Public Resume Code Rule

Each saved resume version should have a unique public code per user.

Allowed alphabet:
`QWRYUPASEDFGHJKZXCVBNM`

Rules:
- Code length: 4 characters.
- No repeated letters inside one code.
- Code must be unique for the same username.
- Different users may technically have the same code because username is part of the public URL.
- Public URL pattern: `/{username}/{public_code}`

## 5. Soft Delete Strategy

Soft delete should be used for:
- SavedResume
- User account deactivation through status

Suggested fields:
- is_deleted
- deleted_at

User deactivation should use UserStatus instead of deleting the user record.

## 6. Notes for 3NF

To support 3NF:
- Do not store role name directly in User; use Role table.
- Do not store status name directly in User; use UserStatus table.
- Do not duplicate language names in content tables; use Language table.
- Do not hardcode adaptation levels in resume records; use AdaptationLevel table.
- Do not store AI model display names in request records; use AiModel table.
- Keep profile section type definitions separate from user-created profile content.
