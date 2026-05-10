# Change Request Log

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-10  
**Author:** Anton  
**Version:** 1.0  
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
| -------- | ---------------------------------------------------------------- | ------------------------ |
| Low | Documentation only or small isolated change                      | No major rework |
| Medium | Affects one area or several related artifacts                    | Moderate rework |
| High | Affects multiple areas, implementation, or review strategy       | Significant rework |
| Critical | Affects core architecture, MVP viability, or capstone compliance | Must be handled urgently |

### 2.4 Decision Values

| Value | Meaning |
|---|---|
| Pending | Not yet decided |
| Approved | Accepted for implementation |
| Rejected | Not accepted |
| Postponed | Moved to later phase |
| Needs More Info | Cannot be decided without clarification |

### 2.5 Status Values

| Value | Meaning |
|---|---|
| Draft | Request is captured but not ready for review |
| Open | Request is ready for review |
| Approved | Request is approved but not implemented |
| Implemented | Change was applied |
| Closed | Change is complete and needs no further action |
| Rejected | Request was rejected |
| Postponed | Request was moved to later phase |

## 3. Summary Table

| CR ID | Date | Title | Type | Requester | Affected Area | Impact | Decision | Status |
|---|---|---|---|---|---|---|---|---|
| CR-001 | 2026-05-10 | Update repository structure in planning documents | Documentation | BA | Information Management, Governance | Low | Approved | Implemented |
| CR-002 | YYYY-MM-DD | [Change title] | [Type] | [Requester] | [Affected area] | [Low/Medium/High/Critical] | Pending | Draft |

## 4. Details

### CR-001 Update Repository Structure in Planning Documents

*   **Date:** 2026-05-10
*   **Type:** Documentation
*   **Requester:** Business Analyst
*   **Status:** Implemented
*   **Description:** Update the Information Management Plan and related planning artifacts to match the actual GitHub repository folder structure.
*   **Reason:** Earlier drafts used placeholder documentation paths that did not match the final professional BA repository layout.
*   **Affected Artifacts:**
    *   `information_management_plan.md`
    *   `governance_plan.md`
*   **Impact Assessment:** Low. Documentation only. No impact on the data model or Java implementation.
*   **Decision:** Approved
*   **Resolution Date:** 2026-05-10
*   **Follow-up Actions:** Keep all future planning artifacts aligned with the actual repository structure.

### CR-002 [Change Title Template]

*   **Date:** YYYY-MM-DD
*   **Type:** [Scope / Requirement / Architecture / Data Model / UI/UX / Deployment / Security / Process / Documentation]
*   **Requester:** [Student / Mentor / Reviewer / Self-review]
*   **Status:** Draft
*   **Description:** [What exactly needs to be changed?]
*   **Reason:** [Why is this change necessary?]
*   **Affected Artifacts:** [List files, requirements, diagrams, or modules]
*   **Impact Assessment:** [Low/Medium/High/Critical and explanation]
*   **Decision:** [Pending / Approved / Rejected / Postponed / Needs More Info]
*   **Resolution Date:** [YYYY-MM-DD or N/A]
*   **Follow-up Actions:** [What should happen next]