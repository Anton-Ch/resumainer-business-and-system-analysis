# Requirements Log

**Project ID:** `[project_id]`  
**Product Name:** [Product Name]  
**Date Created:** YYYY-MM-DD  
**Last Updated:** YYYY-MM-DD  
**Author:** [Author Name]  
**Version:** 1.0  
**Status:** Active  
**Related BABOK Area:** 5.1 Trace Requirements / 5.3 Prioritize Requirements / 6.2 Specify and Model Requirements  

---

## 1. Description

This document is the main requirements register for the project.

It consolidates requirement tracking and requirement readiness checks in one lightweight artifact. Each requirement includes classification, scope, priority, status, acceptance criteria, affected UI/data areas, and implementation readiness checks.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Use this document as the main source of truth for requirements tracking.
- Each requirement must have a stable unique ID.
- Do not delete historical requirements. Change their status instead.
- Keep requirements concise, testable, and traceable.
- Use only the controlled values defined in this document.
- Add new requirements to the Summary Table and create a corresponding entry in Details.
- Use the Readiness Check section to decide whether a requirement is ready for implementation planning.
- Link important requirement changes to the Change Request Log.
- Link major requirement decisions to the Decision Log.
- Link implemented or planned verification to test cases when they become available.

### 2.2 ID Types

The requirement ID types follow the BABOK requirements classification schema.

| ID Prefix | Requirement Type | Meaning | When to Use |
|---|---|---|---|
| BR | Business Requirement | High-level business need, goal, or desired business outcome | Use for project goals and business value statements |
| STK | Stakeholder Requirement | Need of a specific stakeholder or stakeholder group | Use when a user/admin/recruiter need must be captured before solution detail |
| FR | Functional Requirement | Solution behavior, capability, screen action, workflow, or system function | Use for what the system must do |
| NFR | Non-Functional Requirement | Quality, constraint, security, performance, usability, maintainability, deployment, or compliance requirement | Use for how well the system must work or under what constraints |
| TRN | Transition Requirement | Temporary requirement needed to move from current state to future state | Use for migration, setup, deployment preparation, initial data, or one-time transition needs |

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

| ID | Type | Title | Source | Priority | Scope | Status | Readiness |
|---|---|---|---|---|---|---|---|
| FR-999 | Functional | [Requirement title] | [Source] | [Priority] | [Scope] | Draft | Needs Clarification |

## 4. Details

### FR-999 [Requirement Title Template]

**Type:** Functional Requirement  
**Source:** [Project Vision / Elicitation Results / Wireframe Review / Technical Constraint / Security Review / Governance Decision / Capstone Constraint]  
**Priority:** [High / Medium / Low]  
**Scope:** [MVP / MVP Stretch / Post-MVP / Future Scope / Out of Scope]  
**Status:** Draft  
**Readiness:** Needs Clarification  

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
