# Governance Plan for ResumAIner

**Project ID:** `resumainer`
**Date:** 2026-05-10
**Chapter:** 3.3 Governance
**Author:** Anton
**Version:** 1.0
**Status:** Approved

***

### 1. Governance Objective

The primary goal of this Governance Plan is to establish formal, auditable, and transparent rules for decision-making, change management, and scope control. This is crucial to maintain stability while allowing the necessary flexibility of the Hybrid approach.

### 2. Roles and Authority Matrix (RACI)

The following roles define the authority structure for the project:

| Role                          | Decision Making Authority                          | Responsibility                                       | Accountability                                         |
| :---------------------------- | :------------------------------------------------- | :--------------------------------------------------- | :----------------------------------------------------- |
| **BA**                        | **Consulted** (Proposes solutions, flags risks).   | Eliciting, documenting, and proposing solutions.     | Ensuring documentation fidelity and process adherence. |
| **Mentor (Technical Lead)**   | **Approver** (Final technical sign-off).           | Reviewing all architecture and implementation plans. | Technical compliance and quality assurance.            |
| **Sponsor**                   | **Approver** (Final business sign-off).            | Funding, overall business mandate, risk acceptance.  | Project viability and ultimate business success.       |


*Note: All major changes must pass through the **Mentor** for technical approval and the **Sponsor** for business approval.*

### 3. Change Management Process (Change Request - CR)

Since the system is critical and uses a Hybrid model, all changes must be controlled.

1.  **Submission:** A stakeholder (BA, or Mentor) submits a Change Request (CR).
2.  **Impact Assessment:** BA documents the full scope of the change (inputs, required logic, affected modules).
3.  **Review & Analysis:** Mentor performs technical feasibility review; BA assesses impact on requirements and other modules.
4.  **Resolution:** The CR is presented to a **Change Approval Board (CAB)**.
5.  **Change Approval Board (CAB):** Consists of BA, Mentor, and Sponsor. The Sponsor must approve any change that impacts core business value, and the Mentor must approve any change that impacts the technical stack/architecture.
6.  **Implementation:** Only after approval the change can be introduced into the development cycle.

#### 3.1 Change Classification  
  
To keep the process lightweight, all changes are classified into three types:  
  
| Change Type                          | Description                                                                                                     | Approval Needed                                  |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| **Minor** documentation change       | Typos, formatting, wording clarification, repository path correction                                            | BA approval only                                 |
| **Requirement** change               | New, removed, or significantly modified FR/NFR, user flow, or data entity                                       | BA + Mentor review                               |
| **Scope** or **architecture** change | Any change affecting MVP scope, mandatory capstone stack, database structure, deployment model, or security model | BA + Mentor approval; Sponsor informed if needed |

#### 3.2 Decision Log  
  
All major decisions must be recorded in a Decision Log.  
  
Recommended location:    
`docs/09_decisions/decision_log.md`  
  
Each decision should include:  
- decision ID;  
- date;  
- decision title;  
- context;  
- selected option;  
- rejected alternatives;  
- rationale;  
- impact on scope, requirements, data model, or implementation.

##### Example of decision log table

| ID      | Date       | Title                         | Rationale                                             | Impact                                          | Status   |
| :------ | :--------- | :---------------------------- | :---------------------------------------------------- | :---------------------------------------------- | :------- |
| DEC-001 | 2026-05-10 | Use plain JDBC instead of ORM | Mandatory capstone requirement; no Hibernate allowed. | Affects DAO layer and Data Access architecture. | Approved |
| DEC-002 | 2026-05-10 | Decision Title                | Brief rationale here.                                 | Scope/Data Model/Impl impact.                   | Draft    |

#### 3.3 Change Request Log  
  
All non-trivial changes should be recorded in a Change Request Log.  
  
Recommended location:  
`docs/07_project-management/change_request_log.md`  
  
Each change request should include:  
- CR ID;  
- date;  
- requester;  
- description;  
- reason;  
- affected artifacts;  
- impact assessment;  
- decision;  
- status.

#### 3.4 De-scoping Rule  
  
If a feature is valuable but too complex for the MVP, it should not be deleted from the project vision. It should be moved to one of the following categories:  
- MVP Stretch Goal  
- Post-MVP  
- Future Scope  
  
This rule protects the MVP from *scope creep* while preserving useful ideas for future versions.

### 4. Conflict Resolution

When conflicts arise (e.g., business need vs. technical feasibility), the following escalation path must be followed:
1.  **BA:** Facilitates discussion, presents options with clear pros/cons, and documents the conflict.
2.  **Mentor:** Assesses the technical risk associated with each option.
3.  **Sponsor:** Makes the final, binding business decision, accepting the associated risk profile.

### 5. Governance Principles

*   **Traceability:** Every requirement (FR) must be linked back to a validated business need or a regulatory constraint.
*   **Single Source of Truth:** All requirements and decisions are logged in the project documentation repository.
*   **Non-Negotiables:** The core technical constraints (JDBC, Spring MVC, PostgreSQL, etc.) are non-negotiable and must guide all architectural decisions.



