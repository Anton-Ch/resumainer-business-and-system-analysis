# Requirements Traceability Matrix

**Project ID:** `[project_id]`  
**Product Name:** [Product Name]  
**Date Created:** YYYY-MM-DD  
**Last Updated:** YYYY-MM-DD  
**Author:** [Author Name]  
**Version:** 1.0  
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
| FR | Functional Requirement |
| NFR | Non-Functional Requirement |
| CON | Constraint |
| UC | Use Case |
| UI | UI/UX Requirement |

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
| TR-001 | BO-XXX | FR-XXX | FR | [Use case] | [Screen] | [Entity] | [Component] | TC-XXX | Planned | Draft |

## 4. Details

## TR-001 [Trace Item Title]

*   **Business Objective:** BO-XXX
*   **Requirement ID:** FR-XXX
*   **Requirement Type:** FR
*   **Use Case / Workflow:** [Use case or workflow]
*   **UI Screen:** [Related screen]
*   **Data Entity:** [Related entity/table]
*   **Service / Component:** [Related service/component]
*   **Test Case:** TC-XXX
*   **Status:** Draft
*   **Traceability Notes:** [Explain why these items are connected]
*   **Gaps / Follow-up:** [Missing links or next steps]