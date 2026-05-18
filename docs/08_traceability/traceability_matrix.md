# Requirements Traceability Matrix

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-18  
**Author:** Anton  
**Version:** 4.0  
**Status:** Active  
**Related BABOK Area:** 3.4 Plan Business Analysis Information Management  

---

## 1. Description

This document maintains **traceability** between business objectives, requirements, workflows, UI screens, data entities, test cases, and implementation references.

The goal is to ensure that project scope remains controlled and that each important requirement can be traced from business value to implementation and verification.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Add a row for each important requirement or requirement group.
- Keep traceability lightweight and useful.
- Do not block development because of excessive traceability detail.
- Update implementation references after development starts.
- Use `N/A` when a column is not applicable.
- Use stable IDs for business objectives, requirements, use cases, and tests.

### 2.2 Requirement Type Values

| Value | Meaning |
|---|---|
| BR | Business Requirement |
| STK | Stakeholder Requirement |
| FR | Functional Requirement |
| NFR | Non-Functional Requirement |
| TRN | Transition Requirement |

### 2.3 Trace Status Values

| Value | Meaning |
|---|---|
| Draft | Trace row is incomplete or not reviewed |
| Reviewed | Trace row was checked |
| Approved | Trace row is stable enough for baseline |
| Implemented | Related functionality is implemented |
| Verified | Related test or review confirms implementation |
| Superseded | Trace row was replaced by a newer one |

### 2.4 Test Coverage Values

| Value | Meaning |
|---|---|
| Not Started | No test case identified yet |
| Planned | Test case is planned but not implemented |
| Covered | Test case exists or manual test is documented |
| Not Applicable | Testing does not apply directly |


## 3. Summary Table

| Trace ID | Business Objective | Requirement ID | Requirement Type | Use Case / Workflow | UI Screen | Data Entity | Service / Component | Test Case | Test Coverage | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| TR-001 | BO-001 | BR-001 | BR | End-to-end resume adaptation workflow | User Home, My Profile, Generate Resume, Resume Review | Profile data, ResumeGenerationRequest, GeneratedResumeDraft, SavedResume, PdfFile | ProfileService, ResumeGenerationService, SavedResumeService, PdfService | TC-001 | Planned | Approved |
| TR-002 | BO-004 | STK-001 | STK | Recruiter opens public resume link | Public PDF Resume Link | SavedResume, PdfFile, PublicCode | PublicResumeService, PdfService | TC-002 | Planned | Approved |
| TR-003 | BO-001 | FR-001 | FR | Generate AI-assisted resume draft | Generate Resume, Resume Review | ResumeGenerationRequest, GeneratedResumeDraft, AiModel, AiUsageLog | ResumeGenerationService, AiClient, AiUsageLogService | TC-003 | Planned | Draft |
| TR-004 | BO-002 | FR-002 | FR | Complete contact profile | My Profile / Contact Details | ContactDetails | ProfileService, ContactDetailsDao | TC-004 | Planned | Approved |
| TR-005 | BO-002 | FR-003 | FR | Manage work experience | My Profile / Work Experience | WorkExperience | ProfileService, WorkExperienceDao | TC-005 | Planned | Approved |
| TR-006 | BO-002 | FR-004 | FR | Manage projects and volunteering | My Profile / Projects & Volunteering | Project | ProfileService, ProjectDao | TC-006 | Planned | Approved |
| TR-007 | BO-002 | FR-005 | FR | Manage education | My Profile / Education | Education | ProfileService, EducationDao | TC-007 | Planned | Approved |
| TR-008 | BO-002 | FR-006 | FR | Manage courses and certificates | My Profile / Courses & Certificates | CourseCertificate | ProfileService, CourseCertificateDao | TC-008 | Planned | Approved |
| TR-009 | BO-002 | FR-007 | FR | Manage additional profile info and settings | My Profile / Additional Info | AdditionalProfileInfo | ProfileService, AdditionalInfoDao | TC-009 | Planned | Draft |
| TR-010 | BO-003 | FR-008 | FR | View saved resumes on User Home | User Home | SavedResume, PdfFile | SavedResumeService, PdfService | TC-010 | Planned | Approved |
| TR-011 | BO-003 | FR-009 | FR | View resume PDF and actions from User Home (superseded) | User Home | SavedResume, PdfFile, PublicCode | SavedResumeService, PdfService, PublicResumeService | TC-011 | Not Applicable | Superseded |
| TR-012 | BO-005 | FR-010 | FR | Admin manages AI model details | AI Model Details | AiModel | AiModelService, AiModelDao | TC-012 | Planned | Approved |
| TR-013 | BO-005 | NFR-001 | NFR | Protect saved API keys | AI Model Details | AiModel | AiModelService, Security/Logging Components | TC-013 | Planned | Approved |
| TR-014 | BO-005 | TRN-001 | TRN | Prepare initial active AI model configuration | AI Models, AI Model Details | AiModel | AiModelService, Migration/Seed Script | TC-014 | Not Started | Draft |
| TR-015 | BO-001 | FR-011 | FR | Generate and edit cover letter | Resume Review, Resume Details modal | SavedResume (cover_letter), ResumeGenerationRequest (cover_letter) | ResumeGenerationService, AiClient | TC-015 | Not Started | Draft |
| TR-016 | BO-001 | FR-012 | FR | Include cover letter in generation request | Generate Resume | ResumeGenerationRequest (include_cover_letter) | ResumeGenerationService | TC-016 | Not Started | Draft |
| TR-017 | BO-003 | FR-013 | FR | Delete saved resume from User Home | User Home (Resume Details modal) | SavedResume (is_deleted, deleted_at) | SavedResumeService | TC-017 | Not Started | Draft |
| TR-999 | BO-XXX | FR-XXX | FR | [Use case] | [Screen] | [Entity] | [Component] | TC-XXX | Not Started | Draft |

## 4. Details

### TR-001 Business Value Trace

**Business Objective:** BO-001 Reduce manual resume adaptation effort  
**Requirement ID:** BR-001  
**Requirement Type:** BR  
**Use Case / Workflow:** End-to-end resume adaptation workflow  
**UI Screen:** User Home, My Profile, Generate Resume, Resume Review  
**Data Entity:** Profile data, ResumeGenerationRequest, GeneratedResumeDraft, SavedResume, PdfFile  
**Service / Component:** ProfileService, ResumeGenerationService, SavedResumeService, PdfService  
**Test Case:** TC-001  
**Status:** Approved  
**Traceability Notes:** This trace connects the main business requirement with the complete MVP value chain: profile data, vacancy input, generated draft, review/edit, saved resume, PDF download (from User Home), and public sharing.  
**Gaps / Follow-up:** Define final end-to-end demo test after implementation plan is created.

### TR-002 Recruiter Public Resume Access

**Business Objective:** BO-004 Support recruiter-friendly resume sharing  
**Requirement ID:** STK-001  
**Requirement Type:** STK  
**Use Case / Workflow:** Recruiter opens public resume link  
**UI Screen:** Public PDF Resume Link  
**Data Entity:** SavedResume, PdfFile, PublicCode  
**Service / Component:** PublicResumeService, PdfService  
**Test Case:** TC-002  
**Status:** Approved  
**Traceability Notes:** This trace connects recruiter needs with direct public PDF access without registration. It also supports the privacy rule that only the saved resume PDF is exposed.  
**Gaps / Follow-up:** Define public URL validation and not-found/private/deleted resume behavior.

### TR-003 AI Resume Generation

**Business Objective:** BO-001 Reduce manual resume adaptation effort  
**Requirement ID:** FR-001  
**Requirement Type:** FR  
**Use Case / Workflow:** Generate AI-assisted resume draft  
**UI Screen:** Generate Resume, Resume Review  
**Data Entity:** ResumeGenerationRequest, GeneratedResumeDraft, AiModel, AiUsageLog  
**Service / Component:** ResumeGenerationService, AiClient, AiUsageLogService  
**Test Case:** TC-003  
**Status:** Draft  
**Traceability Notes:** This trace connects the core resume generation feature with vacancy input, model selection, draft generation, and review flow.  
**Gaps / Follow-up:** Define final acceptance criteria for mock AI generation, real OpenRouter integration, timeout handling, and empty response handling.

### TR-004 Contact Details

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-002  
**Requirement Type:** FR  
**Use Case / Workflow:** Complete contact profile  
**UI Screen:** My Profile / Contact Details  
**Data Entity:** ContactDetails  
**Service / Component:** ProfileService, ContactDetailsDao  
**Test Case:** TC-004  
**Status:** Approved  
**Traceability Notes:** Contact details provide candidate identity and contact information for generated resumes.  
**Gaps / Follow-up:** Confirm final username/public URL validation rules if username is stored with contact or account settings.

### TR-005 Work Experience

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-003  
**Requirement Type:** FR  
**Use Case / Workflow:** Manage work experience  
**UI Screen:** My Profile / Work Experience  
**Data Entity:** WorkExperience  
**Service / Component:** ProfileService, WorkExperienceDao  
**Test Case:** TC-005  
**Status:** Approved  
**Traceability Notes:** Work experience is a core resume source section and must support add/edit/delete, required description, validation, and automatic sorting.  
**Gaps / Follow-up:** Confirm final employment type values only if employment type is added to MVP.

### TR-006 Projects and Volunteering

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-004  
**Requirement Type:** FR  
**Use Case / Workflow:** Manage projects and volunteering  
**UI Screen:** My Profile / Projects & Volunteering  
**Data Entity:** Project  
**Service / Component:** ProfileService, ProjectDao  
**Test Case:** TC-006  
**Status:** Approved  
**Traceability Notes:** Projects and volunteering support practical experience, portfolio positioning, and career-change evidence.  
**Gaps / Follow-up:** Confirm whether project type is needed in MVP.

### TR-007 Education

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-005  
**Requirement Type:** FR  
**Use Case / Workflow:** Manage education  
**UI Screen:** My Profile / Education  
**Data Entity:** Education  
**Service / Component:** ProfileService, EducationDao  
**Test Case:** TC-007  
**Status:** Approved  
**Traceability Notes:** Education supports formal background in resume generation. Start year is required.  
**Gaps / Follow-up:** Confirm valid year range rules.

### TR-008 Courses and Certificates

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-006  
**Requirement Type:** FR  
**Use Case / Workflow:** Manage courses and certificates  
**UI Screen:** My Profile / Courses & Certificates  
**Data Entity:** CourseCertificate  
**Service / Component:** ProfileService, CourseCertificateDao  
**Test Case:** TC-008  
**Status:** Approved  
**Traceability Notes:** Courses and certificates support professional development and career-change evidence.  
**Gaps / Follow-up:** Confirm whether certificate type is needed in MVP.

### TR-009 Additional Info and Settings

**Business Objective:** BO-002 Maintain structured user profile data  
**Requirement ID:** FR-007  
**Requirement Type:** FR  
**Use Case / Workflow:** Manage additional profile info and settings  
**UI Screen:** My Profile / Additional Info  
**Data Entity:** AdditionalProfileInfo  
**Service / Component:** ProfileService, AdditionalInfoDao  
**Test Case:** TC-009  
**Status:** Draft  
**Traceability Notes:** Additional Info stores simplified profile context and user preferences for MVP, including skills, languages, aspirations, achievements, resume language settings, general AI context, optional profile picture, and username.  
**Gaps / Follow-up:** Confirm language dropdown values, username uniqueness rules, and final field length limits.

### TR-010 User Home Resume Listing

**Business Objective:** BO-003 Reuse and manage saved resume versions  
**Requirement ID:** FR-008  
**Requirement Type:** FR  
**Use Case / Workflow:** View saved resumes on User Home  
**UI Screen:** User Home  
**Data Entity:** SavedResume, PdfFile  
**Service / Component:** SavedResumeService, PdfService  
**Test Case:** TC-010  
**Status:** Approved  
**Traceability Notes:** User Home replaces the separate Resume History page and provides saved resume table, search, sorting, pagination, and a Details column. Clicking `Open details` opens a modal popup with PDF link copy, PDF download, and cover letter text per DEC-015/CR-014.  
**Gaps / Follow-up:** Define minimum search/sort behavior and pagination threshold.

### TR-011 Resume Details and PDF Actions (Superseded)

**Business Objective:** BO-003 Reuse and manage saved resume versions  
**Requirement ID:** FR-009 (Superseded)  
**Requirement Type:** FR  
**Use Case / Workflow:** View resume PDF and actions from User Home  
**UI Screen:** User Home  
**Data Entity:** SavedResume, PdfFile, PublicCode  
**Service / Component:** SavedResumeService, PdfService, PublicResumeService  
**Test Case:** TC-011  
**Status:** Superseded  
**Traceability Notes:** This trace is superseded. The Resume Details page was removed per DEC-014 / CR-013. PDF actions (download, public link copy) are handled directly from User Home (TR-010) and the post-save success flow.  
**Gaps / Follow-up:** Verify that TR-010 covers all required PDF actions from User Home.

### TR-012 Admin AI Model Management

**Business Objective:** BO-005 Support controlled AI model configuration  
**Requirement ID:** FR-010  
**Requirement Type:** FR  
**Use Case / Workflow:** Admin manages AI model details  
**UI Screen:** AI Model Details  
**Data Entity:** AiModel  
**Service / Component:** AiModelService, AiModelDao  
**Test Case:** TC-012  
**Status:** Approved  
**Traceability Notes:** AI Model Details allows admin to view and manage model metadata, provider settings, active status, and API key replacement/deletion.  
**Gaps / Follow-up:** Define exact validation rules for provider base URL, model code, and active/inactive model behavior.

### TR-013 API Key Protection

**Business Objective:** BO-005 Support controlled AI model configuration  
**Requirement ID:** NFR-001  
**Requirement Type:** NFR  
**Use Case / Workflow:** Protect saved API keys  
**UI Screen:** AI Model Details  
**Data Entity:** AiModel  
**Service / Component:** AiModelService, Security/Logging Components  
**Test Case:** TC-013  
**Status:** Approved  
**Traceability Notes:** Saved API keys must be masked, never logged, and available only for replacement or deletion after saving.  
**Gaps / Follow-up:** Define storage/encryption approach and logging exclusions during implementation.

### TR-014 Initial AI Model Configuration

**Business Objective:** BO-005 Support controlled AI model configuration  
**Requirement ID:** TRN-001  
**Requirement Type:** TRN  
**Use Case / Workflow:** Prepare initial active AI model configuration  
**UI Screen:** AI Models, AI Model Details  
**Data Entity:** AiModel  
**Service / Component:** AiModelService, Migration/Seed Script  
**Test Case:** TC-014  
**Status:** Draft  
**Traceability Notes:** The system needs at least one configured active AI model before generation can be demonstrated reliably.  
**Gaps / Follow-up:** Confirm whether seed data is created through SQL migration, admin UI, or manual setup before demo.

### TR-015 Cover Letter Generation

**Business Objective:** BO-001 Reduce manual resume adaptation effort
**Requirement ID:** FR-011
**Requirement Type:** FR
**Use Case / Workflow:** Generate and edit cover letter
**UI Screen:** Resume Review, Resume Details modal
**Data Entity:** SavedResume (cover_letter), ResumeGenerationRequest (cover_letter)
**Service / Component:** ResumeGenerationService, AiClient
**Test Case:** TC-015
**Status:** Draft
**Traceability Notes:** Cover letter is generated alongside resume draft. User can edit cover letter text in Resume Review before saving. Cover letter is viewable in the Resume Details modal on User Home per DEC-016/CR-015.
**Gaps / Follow-up:** Define cover letter generation prompt, max length, and whether cover letter generation is always on or toggleable.

### TR-016 Cover Letter in Generation Request

**Business Objective:** BO-001 Reduce manual resume adaptation effort
**Requirement ID:** FR-012
**Requirement Type:** FR
**Use Case / Workflow:** Include cover letter in generation request
**UI Screen:** Generate Resume
**Data Entity:** ResumeGenerationRequest (include_cover_letter)
**Service / Component:** ResumeGenerationService
**Test Case:** TC-016
**Status:** Draft
**Traceability Notes:** Generation request must include cover letter generation instruction for the AI. Cover letter output is stored separately from resume content.
**Gaps / Follow-up:** Define prompt format for cover letter generation and error handling if cover letter fails but resume succeeds.

### TR-017 Resume Delete from User Home

**Business Objective:** BO-003 Reuse and manage saved resume versions
**Requirement ID:** FR-013
**Requirement Type:** FR
**Use Case / Workflow:** Delete saved resume from User Home
**UI Screen:** User Home (Resume Details modal)
**Data Entity:** SavedResume (is_deleted, deleted_at)
**Service / Component:** SavedResumeService
**Test Case:** TC-017
**Status:** Draft
**Traceability Notes:** Resume delete action is initiated from the Resume Details modal. Soft-delete sets `is_deleted = true`. Public URL returns HTTP 410 Gone for deleted resumes.
**Gaps / Follow-up:** Define exact confirmation UI behavior and 410 page design.

### TR-999 [Trace Item Title Template]

**Business Objective:** BO-XXX  
**Requirement ID:** FR-XXX  
**Requirement Type:** [BR / STK / FR / NFR / TRN]  
**Use Case / Workflow:** [Use case or workflow]  
**UI Screen:** [Related screen]  
**Data Entity:** [Related entity/table]  
**Service / Component:** [Related service/component]  
**Test Case:** TC-XXX  
**Status:** Draft  
**Traceability Notes:** [Explain why these items are connected]  
**Gaps / Follow-up:** [Missing links or next steps]

---

*This traceability matrix follows the Information Management Plan structure and conventions for the ResumAIner project.*
ss