# Requirements Log

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-13  
**Last Updated:** 2026-05-15  
**Author:** Anton  
**Version:** 3.0  
**Status:** Active  
**Related BABOK Area:** 5.1 Trace Requirements / 5.3 Prioritize Requirements / 6.2 Specify and Model Requirements  

---

## 1. Description

This document is the main requirements register for the ResumAIner Capstone project.

It consolidates requirement tracking and requirement readiness checks in one lightweight artifact. Each requirement includes classification, scope, priority, status, acceptance criteria, affected areas, and implementation readiness checks.

This document replaces the separate working `requirement_readiness_checklist.md` artifact for this project. Readiness checks are now maintained inside each requirement detail section.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Use this document as the main source of truth for requirements tracking.
- Each requirement must have a stable unique ID.
- Do not delete historical requirements. Change their status instead.
- Keep requirements concise, testable, and traceable.
- Use only the controlled values defined in this document.
- Add new requirements to the Summary Table and create a corresponding entry in Details.
- Use the Readiness Check section to decide whether a requirement is ready for MVP implementation.
- Link important requirement changes to the Change Request Log.
- Link major requirement decisions to the Decision Log.
- Link implemented or planned verification to test cases when they become available.

### 2.2 ID Types

The requirement ID types follow the BABOK requirements classification schema.

| ID Prefix | Requirement Type           | Meaning                                                                                                       | When to Use                                                                                  |
| --------- | -------------------------- | ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| BR        | Business Requirement       | High-level business need, goal, or desired business outcome                                                   | Use for project goals and business value statements                                          |
| STK       | Stakeholder Requirement    | Need of a specific stakeholder or stakeholder group                                                           | Use when a user/admin/recruiter need must be captured before solution detail                 |
| FR        | Functional Requirement     | Solution behavior, capability, screen action, workflow, or system function                                    | Use for what the system must do                                                              |
| NFR       | Non-Functional Requirement | Quality, constraint, security, performance, usability, maintainability, deployment, or compliance requirement | Use for how well the system must work or under what constraints                              |
| TRN       | Transition Requirement     | Temporary requirement needed to move from current state to future state                                       | Use for migration, setup, deployment preparation, initial data, or one-time transition needs |

Note: BABOK defines Solution Requirements as a major requirement class. In this project, Solution Requirements are tracked through `FR` and `NFR` because this is more practical for development, testing, and traceability.

### 2.3 Priority Values

| Value | Meaning |
|---|---|
| High | Important for MVP success or core product value |
| Medium | Useful for MVP or important for polish, but not core-critical |
| Low | Nice to have or low urgency |

### 2.4 Scope Values

| Value | Meaning |
|---|---|
| MVP | Required for the first working version |
| MVP Stretch | Useful if time allows, but not required for MVP success |
| Post-MVP | Planned after MVP |
| Future Scope | Long-term idea |
| Out of Scope | Explicitly excluded |

### 2.5 Requirement Status Values

| Value | Meaning |
|---|---|
| Draft | Requirement is captured but not yet reviewed |
| Reviewed | Requirement was checked but not yet approved |
| Approved | Requirement is accepted for the current baseline |
| Implemented | Requirement is implemented in the application |
| Verified | Requirement is implemented and tested/confirmed |
| Postponed | Requirement is moved to later phase |
| Rejected | Requirement is not accepted |
| Superseded | Requirement was replaced by another requirement |

### 2.6 Readiness Values

| Value | Meaning |
|---|---|
| Ready | Requirement is clear enough for implementation planning |
| Needs Clarification | Requirement has gaps that should be resolved before implementation |
| Blocked | Requirement cannot move forward until an issue is resolved |
| Postponed | Requirement is intentionally moved out of current implementation scope |
| N/A | Readiness check does not apply |

### 2.7 Readiness Check Values

| Value | Meaning |
|---|---|
| Yes | Check is satisfied |
| No | Check is not satisfied |
| Partial | Check is partly satisfied but needs clarification |
| N/A | Check does not apply |

### 2.8 Source Values

| Value | Meaning |
|---|---|
| Project Vision | Requirement comes from initial product vision |
| Elicitation Results | Requirement comes from confirmed elicitation results |
| Wireframe Review | Requirement comes from wireframe preparation or field-level review |
| Technical Constraint | Requirement comes from architecture or implementation constraints |
| Security Review | Requirement comes from security/privacy review |
| Governance Decision | Requirement comes from Decision Log or Change Request Log |
| Capstone Constraint | Requirement comes from Capstone expectations or delivery constraints |

## 3. Summary Table

| ID      | Type               | Title                                            | Source               | Priority   | Scope   | Status   | Readiness               |
| ------- | ------------------ | ------------------------------------------------ | -------------------- | ---------- | ------- | -------- | ----------------------- |
| BR-001  | Business           | Reduce manual resume adaptation effort           | Project Vision       | High       | MVP     | Approved | Ready                   |
| STK-001 | Stakeholder        | Recruiter can open shared resume without account | Elicitation Results  | High       | MVP     | Approved | Ready                   |
| FR-001  | Functional         | Generate AI-assisted resume draft                | Project Vision       | High       | MVP     | Approved | Needs Clarification     |
| FR-002  | Functional         | Manage contact details                           | Wireframe Review     | High       | MVP     | Approved | Ready                   |
| FR-003  | Functional         | Manage work experience                           | Wireframe Review     | High       | MVP     | Approved | Ready                   |
| FR-004  | Functional         | Manage projects and volunteering                 | Wireframe Review     | High       | MVP     | Approved | Ready                   |
| FR-005  | Functional         | Manage education                                 | Wireframe Review     | High       | MVP     | Approved | Ready                   |
| FR-006  | Functional         | Manage courses and certificates                  | Wireframe Review     | Medium     | MVP     | Approved | Ready                   |
| FR-007  | Functional         | Manage additional profile info and settings      | Wireframe Review     | Medium     | MVP     | Approved | Needs Clarification     |
| FR-008  | Functional         | View saved resumes on User Home                  | Elicitation Results  | High       | MVP     | Approved | Ready                   |
| FR-009  | Functional         | View resume details and PDF actions (superseded) | Governance Decision  | Low        | Post-MVP | Superseded | N/A       |
| FR-010  | Functional         | Admin manages AI model details                   | Elicitation Results  | Medium     | MVP     | Approved | Ready                   |
| FR-011  | Functional         | Generate and edit cover letter                   | Governance Decision  | Medium     | MVP     | Draft    | Needs Clarification     |
| FR-012  | Functional         | Include cover letter in generation request       | Governance Decision  | Medium     | MVP     | Draft    | Needs Clarification     |
| NFR-001 | Non-Functional     | Mask and protect saved API keys                  | Security Review      | High       | MVP     | Approved | Ready                   |
| TRN-001 | Transition         | Prepare initial active AI model configuration    | Technical Constraint | Medium     | MVP     | Draft    | Needs Clarification     |
| XX-XXX  | [Requirement Type] | [Requirement title]                              | [Source]             | [Priority] | [Scope] | Draft    | [Requirement Readiness] |

## 4. Details

### BR-001 Reduce Manual Resume Adaptation Effort

**Type:** Business Requirement  
**Source:** Project Vision  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The product shall reduce the amount of manual work required to adapt a resume for a specific vacancy.

**Business Value:**  
This is the core reason for the product. The system should help users generate relevant resume drafts faster than manual rewriting.

**Acceptance Criteria:**
- User can provide profile data.
- User can provide vacancy information.
- User can generate an adapted resume draft.
- User can review, edit, save, and download the final resume.

**Affected UI:**  
User Home, My Profile, Generate Resume, Resume Review.

**Affected Data:**  
Profile data, ResumeGenerationRequest, GeneratedResumeDraft, SavedResume, PdfFile.

**Related Artifacts:**  
Project Vision, Confirmed Elicitation Results, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
This requirement is implemented through a set of lower-level functional and non-functional requirements.

### STK-001 Recruiter Can Open Shared Resume Without Account

**Type:** Stakeholder Requirement  
**Source:** Elicitation Results  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
Recruiters and external viewers need to open a shared resume link without registration or login.

**Business Value:**  
The public link makes the generated resume useful outside the system and supports real job application workflows.

**Acceptance Criteria:**
- Recruiter can open a public resume link without authentication.
- Public link opens the saved PDF directly.
- PDF text is selectable.
- Recruiter can view, copy text, print, and save the PDF.
- Private profile data, drafts, token usage, and admin data are not exposed.

**Affected UI:**  
Public PDF Resume Link.

**Affected Data:**  
Saved Resume, pdf file, public resume code/link.

**Related Artifacts:**  
Confirmed Elicitation Results, Decision Log, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
This stakeholder requirement is supported by public access and PDF-related functional requirements.

### FR-001 Generate AI-Assisted Resume Draft

**Type:** Functional Requirement  
**Source:** Project Vision  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Needs Clarification  

**Description:**  
The system shall generate an AI-assisted resume draft based on user profile data, vacancy information, selected language, adaptation level, and selected AI model.

**Business Value:**  
This requirement supports the core product value: reducing manual resume adaptation effort.

**Acceptance Criteria:**
- User can submit required generation fields.
- System validates required fields before generation.
- System creates a resume generation request.
- System can generate a draft using a mock AI provider.
- System can later use real OpenRouter integration if allowed and stable.
- System displays the generated draft for user review.
- System handles empty output, timeout, unavailable provider, and inactive model errors.

**Affected UI:**  
Generate Resume, Resume Review.

**Affected Data:**  
ResumeGenerationRequest, GeneratedResumeDraft, AiModel, AiUsageLog.

**Related Artifacts:**  
Confirmed Elicitation Results, Wireframe Field Requirements, Open Questions Log, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Partial
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Partial

**Notes:**  
Requirement is feasible if AI integration is isolated behind an interface and mock generation is implemented first.

### FR-002 Manage Contact Details

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow a registered user to create, view, update, and save contact details in My Profile.

**Business Value:**  
Contact details provide candidate identity and communication information for generated resumes.

**Acceptance Criteria:**
- User can enter full name, email, phone, and location.
- User can optionally enter professional title, LinkedIn URL, portfolio URL, Telegram, and WhatsApp.
- System validates required fields, email format, URL format, and length limits.
- Saved contact details can be used in resume generation.

**Affected UI:**  
My Profile / Contact Details.

**Affected Data:**  
ContactDetails.

**Related Artifacts:**  
Wireframe Field Requirements, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
This is a core profile section for MVP.

### FR-003 Manage Work Experience

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow a registered user to add, edit, delete, and view work experience records in My Profile.

**Business Value:**  
Work experience is one of the most important sources for resume generation.

**Acceptance Criteria:**
- User can add a work experience record.
- User can edit an existing record.
- User can delete a record.
- Job title, company name, start date, and role/job description are required.
- End date is optional for current role.
- End date cannot be earlier than start date.
- Work experience records are sorted automatically.

**Affected UI:**  
My Profile / Work Experience.

**Affected Data:**  
WorkExperience.

**Related Artifacts:**  
Wireframe Field Requirements, Decision Log, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
Repeatable section uses card list + Add/Edit form pattern.

### FR-004 Manage Projects and Volunteering

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow a registered user to add, edit, delete, and view project and volunteering records in My Profile.

**Business Value:**  
Projects and volunteering help demonstrate practical experience and portfolio value.

**Acceptance Criteria:**
- User can add, edit, and delete project records.
- Project name and description are required.
- Role, start date, end date, and project URL are optional.
- End date cannot be earlier than start date.
- Project records are sorted automatically.

**Affected UI:**  
My Profile / Projects & Volunteering.

**Affected Data:**  
Project.

**Related Artifacts:**  
Wireframe Field Requirements, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
Volunteering is handled together with projects for MVP simplicity.

**Default Role Value:** If the user does not specify a role for a project entry, the system defaults to "Participant" at the UI/code level (DEC-031).

### FR-005 Manage Education

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow a registered user to add, edit, delete, and view education records in My Profile.

**Business Value:**  
Education is a standard resume section and supports candidate background context.

**Acceptance Criteria:**
- User can add, edit, and delete education records.
- Institution name, degree/qualification, and start year are required.
- Field of study, end year, location, description, and GPA/grade are optional.
- End year cannot be earlier than start year.
- Education records are sorted automatically.

**Affected UI:**  
My Profile / Education.

**Affected Data:**  
Education.

**Related Artifacts:**  
Wireframe Field Requirements, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
Start year is required based on confirmed elicitation decision.

### FR-006 Manage Courses and Certificates

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow a registered user to add, edit, delete, and view courses and certificates in My Profile.

**Business Value:**  
Courses and certificates support professional development evidence, especially for career transition and junior roles.

**Acceptance Criteria:**
- User can add, edit, and delete course/certificate records.
- Course/certificate name, provider/issuer, and start date are required.
- End date, credential URL, skills/topics, and description are optional.
- End date cannot be earlier than start date.
- Records are sorted automatically.

**Affected UI:**  
My Profile / Courses & Certificates.

**Affected Data:**  
CourseCertificate.

**Related Artifacts:**  
Wireframe Field Requirements, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
This section is important for portfolio and learning evidence.
Courses section is mandatory for MVP per DEC-018. Page distribution: page 1 shows max 7 most relevant courses; page 2 — if 5+ work experience records exist, max 5 courses; if fewer than 5 work experience records, max 8 courses.

### FR-007 Manage Additional Profile Info and Settings

**Type:** Functional Requirement  
**Source:** Wireframe Review  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Needs Clarification  

**Description:**  
The system shall allow a registered user to manage additional profile information and basic settings inside My Profile.

**Business Value:**  
Additional info provides useful AI context and keeps user settings in one place without a separate settings page.

**Acceptance Criteria:**
- User can enter optional skills, languages, professional aspirations, achievements, and general AI context.
- User can set default resume language and optional additional resume language.
- User can manage URL-friendly username.
- User can enter date of birth.
- User can select Ready for relocation (dropdown: Yes / No / Not specified).
- User can select Ready for business trips and rotational schedule (dropdown: Yes / No / Not specified).
- User can select Preferred work format (checkbox group: full-time, part-time, offline, remote, hybrid, on-site project based).
- Profile picture is optional.
- Username must be unique and URL-friendly.
- Date of birth must be a valid date.

**Affected UI:**  
My Profile / Additional Info.

**Affected Data:**  
AdditionalProfileInfo, User.

**Related Artifacts:**  
Wireframe Field Requirements, Decision Log, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Partial
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Partial

**Notes:**  
Needs final dropdown values for languages and username validation rules.

### FR-008 View Saved Resumes on User Home

**Type:** Functional Requirement  
**Source:** Elicitation Results  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall show saved/generated resumes in a searchable and sortable table on User Home.

**Business Value:**  
Users need quick access to all generated resumes without a separate Resume History page.

**Acceptance Criteria:**
- User Home shows saved resumes in a searchable and sortable table.
- Table includes a Details column with an `Open details` button for each resume row.
- Clicking `Open details` opens a modal popup on User Home.
- Modal contains: (1) public PDF resume link for copying, (2) PDF download button, (3) cover letter text for copying.
- Empty state is shown when no resumes exist.
- No-results state is shown when search returns no matches.

**Affected UI:**  
User Home, Resume Details modal.

**Affected Data:**  
SavedResume, PdfFile, CoverLetter.

**Related Artifacts:**  
Confirmed Elicitation Results, Decision Log (DEC-015, DEC-016), Change Request Log (CR-014), Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Partial
- Testable: Partial

**Notes:**  
This requirement replaced a separate Resume History page. It now provides resume actions through a Details column modal per DEC-015/CR-014. Cover letter display added to modal because cover letter is MVP (DEC-016). The direct PDF download from table was replaced with Details column + modal approach.

### FR-009 View Resume Details and PDF Actions (Superseded)

**Type:** Functional Requirement  
**Source:** Governance Decision  
**Priority:** Low  
**Scope:** Post-MVP  
**Status:** Superseded  
**Readiness:** N/A  

**Description:**  
This requirement is superseded. The Resume Details page was removed. PDF viewing, download, and public link copying are handled directly from User Home (FR-008) and the post-save flow after Resume Review.

**Business Value:**  
N/A — requirement is superseded.

**Acceptance Criteria:**
- N/A. Requirement is superseded by FR-008.

**Affected UI:**  
N/A.

**Affected Data:**  
N/A.

**Related Artifacts:**  
Decision Log — DEC-014; Change Request Log — CR-013.

**Readiness Check:**
- Business value clear: N/A
- Acceptance criteria clear: N/A
- Technically feasible: N/A
- UI/workflow identified: N/A
- Data impact identified: N/A
- Testable: N/A

**Notes:**  
Superseded by DEC-014 / CR-013 (2026-05-15). Resume Details page removed from MVP. PDF and public link actions are provided by FR-008 (User Home) and the post-save success flow.

### FR-010 Admin Manages AI Model Details

**Type:** Functional Requirement  
**Source:** Elicitation Results  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall allow an admin to view and manage AI model details.

**Business Value:**  
Admin needs control over available AI models used for resume generation.

**Acceptance Criteria:**
- Admin can view AI model details.
- Admin can edit display name and provider base URL.
- Admin can replace API key.
- Admin can delete API key.
- Admin can activate or deactivate model.
- Saved API key is masked and cannot be viewed in full after saving.

**Affected UI:**  
AI Models, AI Model Details.

**Affected Data:**  
AiModel.

**Related Artifacts:**  
Confirmed Elicitation Results, Decision Log, Risk Register, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
Security behavior is also covered by NFR-001.

### NFR-001 Mask and Protect Saved API Keys

**Type:** Non-Functional Requirement  
**Source:** Security Review  
**Priority:** High  
**Scope:** MVP  
**Status:** Approved  
**Readiness:** Ready  

**Description:**  
The system shall protect saved API keys by masking them in the UI, preventing full key display after saving, and avoiding key exposure in logs.

**Business Value:**  
Protects secrets and prevents accidental exposure of provider credentials.

**Acceptance Criteria:**
- Saved API key is shown only as masked value.
- Admin can replace API key.
- Admin can delete API key.
- Admin cannot view saved API key in full after saving.
- API key is not logged.
- Error messages do not expose API key values.

**Affected UI:**  
AI Model Details.

**Affected Data:**  
AiModel.

**Related Artifacts:**  
Decision Log, Risk Register, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Yes
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Yes

**Notes:**  
This requirement supports DEC-008 and closes the API key exposure risk.

### FR-011 Generate and Edit Cover Letter

**Type:** Functional Requirement  
**Source:** Governance Decision  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Draft  
**Readiness:** Needs Clarification

**Description:**  
The system shall generate a cover letter alongside the resume draft and allow the user to review and edit it before saving the final version.

**Business Value:**  
Cover letter reduces the effort required to apply for a vacancy. Generating it alongside the resume is more efficient than adding it post-MVP since the LLM already has the vacancy and profile context.

**Acceptance Criteria:**
- System generates cover letter text as part of the resume generation process.
- Cover letter text is displayed in the Resume Review screen alongside generated resume fields.
- User can edit the generated cover letter before saving.
- Saved resume includes the final cover letter version.
- Cover letter text is viewable in the Resume Details modal on User Home.
- User can copy cover letter text from the modal.

**Affected UI:**  
Resume Review, Resume Details modal, Generate Resume.

**Affected Data:**  
ResumeGenerationRequest (cover_letter field), SavedResume (cover_letter field).

**Related Artifacts:**  
Decision Log (DEC-016), Change Request Log (CR-015), Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Partial
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Partial

**Notes:**  
Cover letter generation reuses the same AI generation flow as resume draft. The LLM receives the same vacancy and profile context and produces cover letter as additional output. Cover letter format and length rules should be defined during implementation.

### FR-012 Include Cover Letter in Generation Request

**Type:** Functional Requirement  
**Source:** Governance Decision  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Draft  
**Readiness:** Needs Clarification

**Description:**  
The system shall include cover letter generation as part of the resume generation request. The generation request shall instruct the AI to produce a cover letter alongside the adapted resume content.

**Business Value:**  
Cover letter generation must be explicitly requested as part of the AI generation call. Without this requirement, the AI would not produce cover letter output.

**Acceptance Criteria:**
- Generation request includes a flag or instruction for cover letter generation.
- AI prompt includes cover letter generation instructions.
- Cover letter output is stored separately from resume content.
- System handles cases where cover letter generation fails while resume generation succeeds.

**Affected UI:**  
Generate Resume (optional toggle for cover letter generation), Resume Review.

**Affected Data:**  
ResumeGenerationRequest (include_cover_letter).

**Related Artifacts:**  
Decision Log (DEC-016), FR-011, Traceability Matrix.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Partial
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Partial

**Notes:**  
This requirement works together with FR-011. The generation request should include cover letter as a requested output alongside the resume adaptation.

**Generated Content Page Placement:** Generated work experience entries and course entries are placed on page 1 (primary, more relevant) or page 2 (additional) of the resume. Page placement is controlled by `is_first_page` flag in `generation_response_experience` and `generation_response_course` tables. AI model assigns relevance and placement during generation (DEC-030).

### TRN-001 Prepare Initial Active AI Model Configuration

**Type:** Transition Requirement  
**Source:** Technical Constraint  
**Priority:** Medium  
**Scope:** MVP  
**Status:** Draft  
**Readiness:** Needs Clarification  

**Description:**  
The project shall include initial AI model configuration data required for the MVP to run after deployment.

**Business Value:**  
The system needs at least one active AI model configuration for resume generation to work in demo or production-like environment.

**Acceptance Criteria:**
- Initial model configuration can be inserted through migration or seed data.
- At least one active AI model exists after setup.
- API key is provided through secure configuration, not committed to Git.
- Mock model/provider is available for stable demo flow.

**Affected UI:**  
AI Models, AI Model Details.

**Affected Data:**  
AiModel.

**Related Artifacts:**  
Technical Constraints, Deployment Plan, Decision Log.

**Readiness Check:**
- Business value clear: Yes
- Acceptance criteria clear: Partial
- Technically feasible: Yes
- UI/workflow identified: Yes
- Data impact identified: Yes
- Testable: Partial

**Notes:**  
Needs final setup approach for environment variables, seed data, and demo mode.

### FR-999 [Requirement Title Template]

**Type:** [Functional Requirement / Non Functional Requirement / Transition Requirement / Stakeholder Requirement / Business Requirement]  
**Source:** [Project Vision / Elicitation Results / Wireframe Review / Technical Constraint / Security Review / Governance Decision / Capstone Constraint]  
**Priority:** [High / Medium / Low]  
**Scope:** [MVP / MVP Stretch / Post-MVP / Future Scope / Out of Scope]  
**Status:** [Draft]  
**Readiness:** [Needs Clarification  / Ready]

**Description:**  
[Write a concise requirement description.]

**Business Value:**  
[Explain why this requirement matters.]

**Acceptance Criteria:**
- [Criterion 1]
- [Criterion 2]
- [Criterion 3]

**Affected UI:**  
[Related screen/page/section or N/A.]

**Affected Data:**  
[Related entity/table/data object or N/A.]

**Related Artifacts:**  
[Decision Log, Change Request Log, Traceability Matrix, Risk Register, etc.]

**Readiness Check:**
- Business value clear: [Yes / No / Partial / N/A]
- Acceptance criteria clear: [Yes / No / Partial / N/A]
- Technically feasible: [Yes / No / Partial / N/A]
- UI/workflow identified: [Yes / No / Partial / N/A]
- Data impact identified: [Yes / No / Partial / N/A]
- Testable: [Yes / No / Partial / N/A]

**Notes:**  
[Additional notes, assumptions, gaps, or follow-up actions.]
