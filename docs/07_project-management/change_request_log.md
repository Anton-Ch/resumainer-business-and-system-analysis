# Change Request Log

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-13  
**Author:** Anton  
**Version:** 2.0  
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
| CR-999 | YYYY-MM-DD | [Change title]                                             | [Type]        | [Requester] | [Affected area]                     | [Low/Medium/High/Critical] | Pending  | Draft       |

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