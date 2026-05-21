# Change Request Log

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-20 
**Author:** Anton  
**Version:** 6.0  
**Status:** Active  
**Related BABOK Area:** 3.3 Plan Business Analysis Governance  

---

## 1. Description

This document tracks non-trivial **changes** to requirements, scope, architecture, data model, UI/UX, deployment, security, and project documentation.

It helps keep the project baseline controlled and explains why meaningful changes were introduced.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Use this log for meaningful changes only.
- Do not use this log for typos, small formatting edits, or minor wording improvements.
- Each change request must have a unique ID: `CR-001`, `CR-002`, `CR-003`.
- If a change is approved, update affected artifacts and mark the request as `Implemented` or `Closed`.
- If a change is valuable but not suitable for MVP, use `Postponed`.
- If a change affects a major project decision, create or update a Decision Log entry.

### 2.2 Change Type Values

| Value | Meaning | When to Use |
|---|---|---|
| Scope | Change affects MVP, stretch goals, post-MVP, or future scope | Adding/removing feature from MVP |
| Requirement | Change affects FR/NFR, user story, or acceptance criteria | Changing behavior or validation |
| Architecture | Change affects layers, frameworks, integrations, or system structure | Switching backend/frontend approach |
| Data Model | Change affects entities, tables, fields, or relationships | Adding table or field |
| UI/UX | Change affects screens, navigation, workflow, or layout | Changing resume review flow |
| Deployment | Change affects Docker, VPS, domain, server, or environment | Adding Flyway container |
| Security | Change affects auth, roles, permissions, secrets, or public access | Changing public link behavior |
| Process | Change affects BA workflow, governance, traceability, or planning | Adding readiness checklist |
| Documentation | Change affects documentation structure or repository organization | Updating repo paths |

### 2.3 Impact Values

| Value | Meaning                                                          | When to Use |
|-------|------------------------------------------------------------------|-------------|
| Low   | Documentation only or small isolated change                      | No major rework |
| Medium| Affects one area or several related artifacts                    | Moderate rework |
| High  | Affects multiple areas, implementation, or review strategy       | Significant rework |
| Critical| Affects core architecture, MVP viability, or capstone compliance | Must be handled urgently |

### 2.4 Decision Values

| Value | Meaning |
|-------|---------|
| Pending | Not yet decided |
| Approved | Accepted for implementation |
| Rejected | Not accepted |
| Postponed | Moved to later phase |
| Needs More Info | Cannot be decided without clarification |

### 2.5 Status Values

| Value | Meaning |
|-------|---------|
| Draft | Request is captured but not ready for review |
| Open | Request is ready for review |
| Approved | Request is approved but not implemented |
| Implemented | Change was applied |
| Closed | Change is complete and needs no further action |
| Rejected | Request was rejected |
| Postponed | Request was moved to later phase |

## 3. Summary Table

| CR ID  | Date       | Title                                                      | Type          | Requester   | Affected Area                       | Impact                     | Decision | Status      |
| ------ | ---------- | ---------------------------------------------------------- | ------------- | ----------- | ----------------------------------- | -------------------------- | -------- | ----------- |
| CR-001 | 2026-05-10 | Update repository structure in planning documents          | Documentation | BA          | Information Management, Governance  | Low                        | Approved | Implemented |
| CR-002 | 2026-05-11 | Update UI/UX terminology from Dashboard to Home            | UI/UX         | BA          | Elicitation, sitemap, UI docs       | Medium                     | Approved | Implemented |
| CR-003 | 2026-05-11 | Remove separate User Settings page from MVP                | Scope         | BA          | My Profile, navigation              | Medium                     | Approved | Implemented |
| CR-004 | 2026-05-11 | Add Resume Details page to user flow                       | Scope         | BA          | Resume flow, details page           | Medium                     | Approved | Implemented |
| CR-005 | 2026-05-11 | Refine admin page map                                      | Scope         | BA          | Admin pages                         | Medium                     | Approved | Implemented |
| CR-006 | 2026-05-11 | Change public resume behavior to direct PDF opening        | UI/UX         | BA          | Public access, PDF delivery         | Medium                     | Approved | Implemented |
| CR-007 | 2026-05-12 | Integrate resume listing into User Home                    | Scope         | BA          | User Home, navigation               | Medium                     | Approved | Implemented |
| CR-008 | 2026-05-12 | Update downstream UI requirements from elicitation results | Requirement   | BA          | UI/UX requirements, sitemap, flows  | Medium                     | Approved | Implemented |
| CR-009 | 2026-05-13 | Apply wireframe field findings to My Profile               | UI/UX         | BA          | My Profile, profile data fields     | Medium                     | Approved | Implemented |
| CR-010 | 2026-05-13 | Update Generate Resume fields from wireframe findings      | UI/UX         | BA          | Generate Resume, generation request | Medium                     | Approved | Implemented |
| CR-011 | 2026-05-13 | Replace full API key visibility with masked key handling   | Security      | BA          | AI Model Details, logging, admin UI | High                       | Approved | Implemented |
| CR-012 | 2026-05-13 | Clean validation inconsistencies from wireframe notes      | Requirement   | BA          | Validation rules, error messages    | Medium                     | Approved | Implemented |
| CR-013 | 2026-05-15 | Remove Resume Details pages (user and admin)                | Scope         | BA          | User and admin page maps, FR-009    | Medium                     | Approved | Implemented |
| CR-014 | 2026-05-16 | Replace PDF column with Details modal on User Home         | UI/UX         | BA          | User Home table, Resume Details modal, FR-008 | Medium                | Approved | Draft       |
| CR-015 | 2026-05-16 | Add Cover Letter generation and editing to MVP             | Scope         | BA          | Generate Resume, Resume Review, FR-001, new FR-011, FR-012 | Medium    | Approved | Draft       |
| CR-016 | 2026-05-16 | Expand Additional Info fields in My Profile                | Requirement   | BA          | My Profile, FR-007, Wireframe Field Requirements | Low                  | Approved | Draft       |
| CR-017 | 2026-05-18 | Add resume delete from User Home and public_url_link field | Requirement   | BA          | Requirements Log, ERD, Data Dictionary, Traceability Matrix, Risk Register, Decision Log | Medium | Approved | Implemented |
| CR-018 | 2026-05-18 | Add professional_title to resume_generation_response       | Requirement   | BA          | Requirements Log, Decision Log, ERD, Data Dictionary, Traceability Matrix | Low | Approved | Draft       |
| CR-019 | 2026-05-20 | Move profile picture from MVP to POST-MVP                  | Scope         | BA          | Requirements Log (FR-007), Wireframe Field Requirements, Decision Log | Low | Approved | Draft       |

## 4. Details

### CR-001 Update Repository Structure in Planning Documents

**Date:** 2026-05-10  
**Type:** Documentation  
**Requester:** Business Analyst  
**Status:** Implemented  
**Description:** Update planning artifacts to match the actual BA repository structure.  
**Reason:** Earlier drafts used placeholder paths.  
**Affected Artifacts:** `information_management_plan.md`, `governance_plan.md`  
**Impact Assessment:** Low. Documentation only.  
**Decision:** Approved  
**Resolution Date:** 2026-05-10  
**Follow-up Actions:** Keep future artifacts aligned with repository structure.

### CR-002 Update UI/UX Terminology from Dashboard to Home

**Date:** 2026-05-11  
**Type:** UI/UX  
**Status:** Implemented  
**Description:** Replace Dashboard terminology with `User Home` and `Admin Home`.  
**Reason:** Home page wording is clearer for main post-login pages.  
**Affected Artifacts:** `confirmed_elicitation_results.md`, `sitemap.md`, wireframes, UI docs  
**Impact Assessment:** Medium. Affects terminology across artifacts.  
**Decision:** Approved  
**Resolution Date:** 2026-05-11
**Follow-up Actions:** Ensure all future documents use "User Home" and "Admin Home" terminology consistently.
### CR-003 Remove Separate User Settings Page from MVP

**Date:** 2026-05-11  
**Type:** Scope  
**Status:** Implemented  
**Description:** Move settings into My Profile.  
**Reason:** Reduces page count and navigation complexity.  
**Affected Artifacts:** My Profile, sitemap, user flow  
**Impact Assessment:** Medium. Simplifies navigation.  
**Decision:** Approved  
**Resolution Date:** 2026-05-11
**Follow-up Actions:** Implement My Profile with integrated settings tabs/sections for interface language, resume language preferences, account settings, etc.
### CR-004 Add Resume Details Page to User Flow

**Date:** 2026-05-11  
**Type:** Scope  
**Status:** Implemented  
**Description:** Add Resume Details page for selected saved resume.  
**Reason:** Users need a focused place to view PDF, download it, and copy recruiter link.  
**Affected Artifacts:** Resume flow, sitemap, wireframes  
**Impact Assessment:** Medium. Adds one necessary user page.  
**Decision:** Approved  
**Resolution Date:** 2026-05-11
**Follow-up Actions:** Implement Resume Details page with PDF preview/download, public link copying, and navigation back to history.
### CR-005 Refine Admin Page Map

**Date:** 2026-05-11  
**Type:** Scope  
**Status:** Implemented  
**Description:** Confirm admin pages: Admin Home, Users, User Details, Resumes, Resume Details, AI Models, AI Model Details.  
**Reason:** Admin needs management pages for users, resumes, usage, and AI models.  
**Affected Artifacts:** Admin sitemap, admin wireframes, UI requirements  
**Impact Assessment:** Medium. Expands admin scope but supports required oversight.  
**Decision:** Approved  
**Resolution Date:** 2026-05-11
**Follow-up Actions:** Implement all admin pages: Admin Home, Users, User Details, Resumes, Resume Details (admin), AI Models, AI Model Details.
### CR-006 Change Public Resume Behavior to Direct PDF Opening

**Date:** 2026-05-11  
**Type:** UI/UX  
**Status:** Implemented  
**Description:** Public recruiter link opens PDF directly.  
**Reason:** Recruiters need fast viewing, printing, text copying, and saving.  
**Affected Artifacts:** Public access flow, PDF delivery, Resume Details  
**Impact Assessment:** Medium. Simplifies recruiter flow.  
**Decision:** Approved  
**Resolution Date:** 2026-05-11
**Follow-up Actions:** Implement public URL routing to serve PDF files directly with appropriate caching and access controls.
### CR-007 Integrate Resume Listing into User Home

**Date:** 2026-05-12  
**Type:** Scope  
**Status:** Implemented  
**Description:** Remove separate Resume History page and integrate resume listing table into User Home.  
**Reason:** Faster access and fewer navigation steps.  
**Affected Artifacts:** User Home, navigation, sitemap, wireframes  
**Impact Assessment:** Medium. Simplifies page map.  
**Decision:** Approved  
**Resolution Date:** 2026-05-12
**Follow-up Actions:** Implement User Home with integrated searchable/sortable table with filter of user's resumes including PDF download and details access.
### CR-008 Update Downstream UI Requirements from Elicitation Results

**Date:** 2026-05-12  
**Type:** Requirement  
**Status:** Implemented  
**Description:** Align UI/UX requirements, sitemap, and flows with confirmed elicitation decisions.  
**Reason:** Prevents contradictions between elicitation and design artifacts.  
**Affected Artifacts:** UI/UX requirements, sitemap, user flows, wireframes  
**Impact Assessment:** Medium. Improves consistency.  
**Decision:** Approved  
**Resolution Date:** 2026-05-12
**Follow-up Actions:** Use updated requirements as basis for wireframe creation and UI implementation.
### CR-009 Apply Wireframe Field Findings to My Profile

**Date:** 2026-05-13  
**Type:** UI/UX  
**Status:** Implemented  
**Description:** Add concrete fields, validation, and section structure from wireframe preparation to My Profile documentation.  
**Reason:** Wireframes clarified actual fields needed for profile data entry.  
**Affected Artifacts:** `confirmed_elicitation_results.md`, `wireframe_field_requirements.md`, readiness checklist, traceability matrix  
**Impact Assessment:** Medium. Adds field-level clarity.  
**Decision:** Approved  
**Resolution Date:** 2026-05-13
**Follow-up Actions:** Use updated My Profile field requirements as the basis for profile wireframes, validation logic, and test case preparation.
### CR-010 Update Generate Resume Fields from Wireframe Findings

**Date:** 2026-05-13  
**Type:** UI/UX  
**Status:** Implemented  
**Description:** Add `Additional comments for AI` and clean Generate Resume validation rules.  
**Reason:** Wireframe notes clarified generation input fields and removed unrelated validation items.  
**Affected Artifacts:** Generate Resume, generation request fields, readiness checklist, traceability matrix  
**Impact Assessment:** Medium. Improves form accuracy.  
**Decision:** Approved  
**Resolution Date:** 2026-05-13
**Follow-up Actions:** Update Generate Resume wireframes, validation scenarios, and traceability links to reflect the finalized generation input fields.
### CR-011 Replace Full API Key Visibility with Masked Key Handling

**Date:** 2026-05-13  
**Type:** Security  
**Status:** Implemented  
**Description:** Replace full API key display with masked key display. Admin can replace or delete the key but cannot view it in full after saving.  
**Reason:** API keys are secrets and should not be exposed or logged.  
**Affected Artifacts:** Decision Log, Risk Register, AI Model Details requirements  
**Impact Assessment:** High. Reduces security risk.  
**Decision:** Approved  
**Resolution Date:** 2026-05-13
**Follow-up Actions:** Apply masked API key handling in UI design, implementation requirements, security test cases, and risk mitigation tracking.
### CR-012 Clean Validation Inconsistencies from Wireframe Notes

**Date:** 2026-05-13  
**Type:** Requirement  
**Status:** Implemented  
**Description:** Resolve inconsistencies in required fields, validation rules, and error messages found during wireframe review.  
**Reason:** Work Experience description and Education start year are required; profile picture is optional; Generate Resume validation must match actual fields.  
**Affected Artifacts:** `wireframe_field_requirements.md`, `confirmed_elicitation_results.md`, readiness checklist  
**Impact Assessment:** Medium. Improves requirement quality and testability.  
**Decision:** Approved  
**Resolution Date:** 2026-05-13
**Follow-up Actions:** Use the cleaned validation rules as the source of truth for UI validation, error message design, QA checks, and acceptance criteria.

### CR-013 Remove Resume Details Pages from MVP (User and Admin)

**Date:** 2026-05-15  
**Type:** Scope  
**Requester:** Business Analyst  
**Status:** Implemented  
**Description:** Remove both user and admin Resume Details pages from MVP. PDF viewing, download, and public link copying are handled directly from User Home table and the post-save flow after Resume Review for users. Admin can view generated and saved resume PDFs the same way — from the Resumes table without a separate detail page.  
**Reason:** Neither page provides standalone value. All functions (PDF preview, download, public link access) are accessible from list/table views — User Home for users, Resumes table for admin.  
**Affected Artifacts:** `requirements_log.md`, `confirmed_elicitation_results.md`, `decision_log.md`, `traceability_matrix.md`, `risk_register.md`, `sitemap.md`  
**Impact Assessment:** Medium. Eliminates two pages from MVP but all functions remain available through table-level actions.  
**Decision:** Approved  
**Resolution Date:** 2026-05-15
**Follow-up Actions:** Mark FR-009 as Superseded. Remove Resume Details from user and admin page maps in Confirmed Elicitation Results. Update sitemap to remove both user and admin Resume Details entries. Supersede TR-011.

### CR-014 Replace PDF Column with Details Modal on User Home

**Date:** 2026-05-16
**Type:** UI/UX
**Requester:** Business Analyst
**Status:** Draft
**Description:** Replace the Link to PDF column in the User Home resume table with a Details column. Each row shows an `Open details` button that opens a modal popup containing: (1) public PDF link for copying, (2) PDF download button, (3) cover letter text for copying.
**Reason:** Wireframe refinement showed that a modal provides all resume output actions in one place without cluttering the table or requiring a separate page. Cover letter display is included because cover letter is now MVP.
**Affected Artifacts:** `requirements_log.md` (FR-008), `wireframe_field_requirements.md`, `traceability_matrix.md` (TR-010), `decision_log.md` (DEC-015)
**Impact Assessment:** Medium. Changes User Home table column structure and adds modal component.
**Decision:** Approved
**Resolution Date:** N/A
**Follow-up Actions:** Update FR-008 acceptance criteria to reflect modal behavior. Update Wireframe Field Requirements. Add cover letter to modal content.

### CR-015 Add Cover Letter Generation and Editing to MVP

**Date:** 2026-05-16
**Type:** Scope
**Requester:** Business Analyst
**Status:** Draft
**Description:** Add cover letter generation to MVP. LLM generates cover letter text as part of the resume generation process. User can view and edit the cover letter in Resume Review before saving.
**Reason:** Cover letter was already visible in wireframes. Generating alongside the resume is less effort than post-MVP. LLM already has the context needed.
**Affected Artifacts:** `requirements_log.md` (FR-001, new FR-011, FR-012), `decision_log.md` (DEC-016), `traceability_matrix.md`, `wireframe_field_requirements.md`
**Impact Assessment:** Medium. Adds cover letter field to generation flow but reuses existing infrastructure.
**Decision:** Approved
**Resolution Date:** N/A
**Follow-up Actions:** Create FR-011 and FR-012. Update FR-001. Add cover letter to Generate Resume and Resume Review field requirements. Add trace rows.

### CR-016 Expand Additional Info Fields in My Profile

**Date:** 2026-05-16
**Type:** Requirement
**Requester:** Business Analyst
**Status:** Draft
**Description:** Add new fields to Additional Info section: Date of Birth, Ready for relocation (dropdown), Ready for business trips (dropdown), Preferred work format (checkbox group: full-time, part-time, offline, remote, hybrid, on-site project based).
**Reason:** Wireframes show these fields are needed for complete profile data supporting resume generation and candidate positioning.
**Affected Artifacts:** `requirements_log.md` (FR-007), `wireframe_field_requirements.md` (Section 4.6), `traceability_matrix.md` (TR-009)
**Impact Assessment:** Low. Expands existing section without adding new pages.
**Decision:** Approved
**Resolution Date:** N/A
**Follow-up Actions:** Update FR-007 description and acceptance criteria. Add validation rules to Wireframe Field Requirements. Update TR-009 trace notes.

### CR-017 Add Resume Delete from User Home and public_url_link Field

**Date:** 2026-05-18
**Type:** Requirement
**Requester:** Business Analyst
**Status:** Implemented
**Description:** Add user-facing resume delete capability from User Home and add `public_url_link` varchar(200) field to `saved_resume` table for storing ready-made public resume URLs.

**Reason:** Users need to delete saved resumes directly from User Home. The delete button ("Delete this resume") is placed in the Open Details modal. After clicking, the button changes to a confirmation prompt with a new "Confirm deletion" button. Additionally, `public_url_link` is needed to store the generated public link for direct access. The existing `is_deleted` boolean field in `saved_resume` (default: false) is set to true on deletion to deactivate the link. If a recruiter or external visitor accesses a deleted resume link, the system returns HTTP 410 Gone with a custom page stating "Пользователь решил удалить данное резюме. Больше оно не доступно."

**Affected Artifacts:** `requirements_log.md`, `dbml_erd.md`, `mermaid_erd.md`, `plantuml_erd.puml`, `data_dictionary.md`, `traceability_matrix.md`, `risk_register.md`, `decision_log.md`

**Impact Assessment:** Medium. Adds new user-facing delete flow, a new DB field, and custom HTTP 410 handling.

**Decision:** Approved

**Resolution Date:** 2026-05-18

**Follow-up Actions:** Create FR-013. Update ERD files with `public_url_link`. Update Data Dictionary. Add trace row TR-017. Add risk RISK-011. [Completed 2026-05-18]

### CR-018 Add professional_title to resume_generation_response

**Date:** 2026-05-18
**Type:** Requirement
**Requester:** Business Analyst
**Status:** Draft
**Description:** Add `professional_title` varchar(250) NOT NULL field to `resume_generation_response` table. The AI model generates the most relevant professional title matching the target vacancy and stores it in this field.

**Reason:** The generated resume needs a professional title that is specifically adapted to the target vacancy, distinct from the user's general `professional_title` in `contact_detail`. The AI model determines the best-fit title based on the vacancy requirements.

**Affected Artifacts:** `requirements_log.md` (FR-001), `dbml_erd.md`, `mermaid_erd.md`, `plantuml_erd.puml`, `data_dictionary.md`, `traceability_matrix.md` (TR-003), `decision_log.md`

**Impact Assessment:** Low. Adds one field to existing table; uses existing AI generation flow.

**Decision:** Approved

**Resolution Date:** N/A

**Follow-up Actions:** Update FR-001 affected data. Add DEC-033. Update ERDs and Data Dictionary. Update TR-003 trace notes.

### CR-019 Move Profile Picture from MVP to POST-MVP

**Date:** 2026-05-20
**Type:** Scope
**Requester:** Business Analyst
**Status:** Draft
**Description:** Move profile picture (photo_file_path) from MVP scope to POST-MVP. Profile picture is not supported by current HTML templates and is not required for resume generation.

**Reason:** The profile picture field (optional in FR-007) is not used by current one-page or two-page HTML templates. Keeping it in MVP creates unnecessary UI and data handling complexity without delivering resume output value. Deferred to POST-MVP when templates may support photos.

**Affected Artifacts:** `requirements_log.md` (FR-007), `wireframe_field_requirements.md`, `decision_log.md` (DEC-050)

**Impact Assessment:** Low. Removes optional field from MVP scope.

**Decision:** Approved

**Resolution Date:** N/A

**Follow-up Actions:** Update FR-007 acceptance criteria. Remove photo_file_path from MVP scope.

### CR-999 [Change Title Template]

**Date:** YYYY-MM-DD  
**Type:** [Scope / Requirement / Architecture / Data Model / UI/UX / Deployment / Security / Process / Documentation]  
**Requester:** [Student / Mentor / Reviewer / Self-review]  
**Status:** Draft  
**Description:** [What exactly needs to be changed?]  
**Reason:** [Why is this change necessary?]  
**Affected Artifacts:** [List files, requirements, diagrams, or modules]  
**Impact Assessment:** [Low/Medium/High/Critical and explanation]  
**Decision:** [Pending / Approved / Rejected / Postponed / Needs More Info]  
**Resolution Date:** [YYYY-MM-DD or N/A]  
**Follow-up Actions:** [What should happen next]

---

*This change request log follows the Information Management Plan structure and conventions for the ResumAIner project.*