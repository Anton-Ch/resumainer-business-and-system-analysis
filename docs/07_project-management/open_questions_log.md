# Open Questions Log

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-10  
**Author:** Anton  
**Version:** 1.0  
**Status:** Active  
**Related BABOK Area:** 3.2 Plan Stakeholder Engagement / 3.3 Plan Business Analysis Governance  

---

## 1. Description

This document tracks unresolved **questions** that may affect scope, requirements, architecture, data model, UI/UX, deployment, security, or project delivery.

The goal is to prevent hidden assumptions and make uncertainty visible until a decision is made.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Use this log for questions that may affect project decisions.
- Do not use this log for minor personal reminders.
- Each question must have a unique ID: `OQ-001`, `OQ-002`, `OQ-003`.
- If a question results in a decision, link it to a Decision Log entry.
- If a question results in a change, link it to a Change Request.
- Close questions only after an answer is documented.

### 2.2 Question Category Values

| Value               | Meaning                                                                 | When to Use                              |
| ------------------- | ----------------------------------------------------------------------- | ---------------------------------------- |
| Scope               | Question affects MVP, stretch goals, or future scope                    | Is feature X in MVP?                     |
| Requirement         | Question affects FR/NFR or acceptance criteria                          | What should happen in edge case?         |
| Architecture        | Question affects system structure or technology                         | Is Vue allowed?                          |
| Data Model          | Question affects entities, fields, relationships, or storage            | Should resume be stored as JSON?         |
| UI/UX               | Question affects screens, workflows, or user interaction                | Should public link open PDF or web page? |
| Deployment          | Question affects server, Docker, domain, or environment                 | How to deploy on VPS?                    |
| Security            | Question affects authentication, authorization, secrets, or public data | Can public link expose contact info?     |
| Process             | Question affects documentation, governance, traceability, or workflow   | How to review requirements?              |
| Capstone Constraint | Question affects mandatory capstone rules                               | Is external API allowed?                 |

### 2.3 Impact Values

| Value | Meaning                                                              |
|---|---|
| Low | Answer has minor documentation impact                                |
| Medium | Answer affects one requirement, screen, or artifact                  |
| High | Answer affects MVP, architecture, data model, or implementation plan |
| Critical | Answer may block implementation or capstone compliance               |

### 2.4 Question Status Values

| Value | Meaning |
|---|---|
| Open | Question is unresolved |
| In Review | Question is being clarified |
| Answered | Answer is known and recorded |
| Converted | Question became a decision or change request |
| Closed | No further action is required |

## 3. Summary Table

| OQ ID | Date | Question | Category | Owner | Impact | Target Resolution | Status | Answer / Decision Link |
|---|---|---|---|---|---|---|---|---|
| OQ-001 | 2026-05-10 | Is Vue allowed for the final Capstone implementation? | Architecture | BA / Mentor | High | Before dev repository creation | Open | N/A |
| OQ-002 | YYYY-MM-DD | [Question text] | [Category] | [Owner] | [Low/Medium/High/Critical] | YYYY-MM-DD | Open | [DEC/CR link or N/A] |

## 4. Details

### OQ-001 Is Vue Allowed for the Final Capstone Implementation?

*   **Date:** 2026-05-10
*   **Category:** Architecture
*   **Owner:** BA / Mentor
*   **Status:** Open
*   **Question:** Is Vue allowed for the final Java Capstone implementation, or should the project use Thymeleaf/JSP for all UI pages?
*   **Why It Matters:** This affects frontend architecture, routing, deployment, Docker Compose structure, and the amount of work required for integration.
*   **Options Considered:**
    *   Option A: Spring MVC backend + Vue frontend.
    *   Option B: Spring MVC + Thymeleaf/JSP for all pages.
    *   Option C: Hybrid approach with Thymeleaf landing page and Vue app for authenticated UI.
*   **Answer / Decision:** N/A
*   **Related Artifacts:**
    *   `architecture_requirements.md`
    *   `technical_constraints.md`
    *   `ui_ux_requirements.md`
*   **Follow-up Actions:** Ask mentor or validate capstone requirements before development repository creation.

### OQ-002 [Question Short Title Template]

*   **Date:** YYYY-MM-DD
*   **Category:** [Scope / Requirement / Architecture / Data Model / UI/UX / Deployment / Security / Process / Capstone Constraint]
*   **Owner:** [Owner]
*   **Status:** Open
*   **Question:** [Full question]
*   **Why It Matters:** [Impact if unresolved]
*   **Options Considered:** [Option A / Option B / Option C]
*   **Answer / Decision:** [Answer or N/A]
*   **Related Artifacts:** [Files, requirements, decisions]
*   **Follow-up Actions:** [What should happen next]