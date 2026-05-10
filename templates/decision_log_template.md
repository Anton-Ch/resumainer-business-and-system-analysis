# Decision Log

**Project ID:** `[project_id]`  
**Product Name:** [Product Name]  
**Date Created:** YYYY-MM-DD  
**Last Updated:** YYYY-MM-DD  
**Author:** [Author Name]  
**Version:** 1.0  
**Status:** Active  
**Related BABOK Area:** 3.3 Plan Business Analysis Governance  

---

## 1. Description

This document records major business analysis, system analysis, architecture, scope, and implementation **decisions** made during the project.

It explains the context, selected option, rejected alternatives, rationale, and expected impact of each decision.

The purpose is to make important decisions transparent, auditable, and reusable for future project explanation, development handoff, and portfolio presentation.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Record only meaningful decisions that affect scope, requirements, architecture, data model, UI/UX, deployment, security, or project process.
- Do not record minor wording or formatting changes here.
- Do not delete decisions after they are made.
- If a decision changes, mark the old decision as `Superseded` and create a new decision.
- Use `Change Request Log` if a decision causes a non-trivial change to approved artifacts.
- Use consistent decision IDs: `DEC-001`, `DEC-002`, `DEC-003`.

### 2.2 Decision Type Values

| Value | Meaning | When to Use |
|---|---|---|
| Architecture | Decision about system structure, layers, frameworks, or backend/frontend approach | Choosing Spring MVC, Tomcat, REST style |
| Scope | Decision about MVP, stretch goals, post-MVP, or future scope | Moving a feature out of MVP |
| Requirement | Decision affecting FR/NFR or acceptance criteria | Adding/removing/changing requirements |
| Data Model | Decision about entities, tables, relationships, or storage format | Choosing JSON vs structured tables |
| UI/UX | Decision about screens, flows, layout, or user interaction | Choosing wizard flow or tabs |
| Deployment | Decision about hosting, Docker, server, domain, or environment | Choosing Docker Compose on VPS |
| Security | Decision about authentication, authorization, secrets, public access | Choosing BCrypt or session handling |
| Process | Decision about BA process, governance, documentation, or workflow | Creating traceability matrix or readiness checklist |

### 2.3 Decision Status Values

| Value | Meaning | When to Use |
|---|---|---|
| Proposed | Decision is suggested but not approved | Early candidate decision |
| Approved | Decision is accepted and active | Main state for accepted decisions |
| Superseded | Decision was replaced by a newer decision | Historical record remains |
| Rejected | Decision option was considered but not selected | Use for rejected decision records if needed |

## 3. Summary Table

| ID | Date | Type | Title | Rationale | Impact | Status |
|---|---|---|---|---|---|---|
| DEC-001 | YYYY-MM-DD | Architecture | [Decision title] | [Brief rationale] | [Scope/Data/Implementation impact] | Proposed |

## 4. Details

## DEC-001 [Decision Title]

*   **Date:** YYYY-MM-DD
*   **Type:** Architecture
*   **Status:** Proposed
*   **Context:** [Why is this decision needed?]
*   **Selected Option:** [What was chosen?]
*   **Rejected Alternatives:** [What else was considered?]
*   **Rationale:** [Why this option was chosen]
*   **Impact:**
    *   **Scope:** [Impact on MVP or future scope]
    *   **Requirements:** [Affected FR/NFR if any]
    *   **Data Model:** [Affected entities/tables if any]
    *   **Implementation:** [Affected layers, technologies, or patterns]
    *   **Risks:** [New or reduced risks]
*   **Follow-up Actions:** [Optional next steps]