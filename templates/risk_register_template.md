# Risk Register

**Project ID:** `[project_id]`  
**Product Name:** [Product Name]  
**Date Created:** YYYY-MM-DD  
**Last Updated:** YYYY-MM-DD  
**Author:** [Author Name]  
**Version:** 1.0  
**Status:** Active  
**Related BABOK Area:** 3.1 Plan Business Analysis Approach / 3.3 Plan Business Analysis Governance  

---

## 1. Description

This document identifies, assesses, and tracks project **risks** that may affect scope, requirements, architecture, implementation, testing, deployment, or final presentation.

The purpose is to make risks visible early and define practical mitigation strategies.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Add risks that may meaningfully affect project success.
- Do not add every minor inconvenience.
- Keep mitigation actions practical.
- Update risk status as the project evolves.
- If a risk becomes an issue, create a change request or decision if needed.

### 2.2 Risk Category Values

| Value       | Meaning                                                     |
| ----------- | ----------------------------------------------------------- |
| Scope       | Risk related to uncontrolled feature growth or unclear MVP  |
| Technical   | Risk related to implementation, framework, or architecture  |
| Data        | Risk related to database model, migration, or data quality  |
| Security    | Risk related to auth, permissions, secrets, or public data  |
| UX          | Risk related to usability, navigation, or user confusion    |
| Integration | Risk related to external APIs or third-party services       |
| Deployment  | Risk related to Docker, VPS, domain, or runtime environment |
| Schedule    | Risk related to time, workload, or project deadlines        |
| Quality     | Risk related to testing, maintainability, or defects        |
| Compliance  | Risk related to mandatory project requirements              |

### 2.3 Probability Values

| Value | Meaning |
|---|---|
| Low | Unlikely to happen |
| Medium | Possible |
| High | Likely |

### 2.4 Impact Values

| Value | Meaning |
|---|---|
| Low | Minor inconvenience |
| Medium | Noticeable rework or delay |
| High | Major rework, demo risk, or quality issue |
| Critical | May block project completion or course compliance |

### 2.5 Severity Values

| Value | Meaning |
|---|---|
| Low | Low priority risk |
| Medium | Should be monitored |
| High | Requires mitigation |
| Critical | Requires immediate attention |

### 2.6 Response Strategy Values

| Value | Meaning |
|---|---|
| Avoid | Change plan to remove the risk |
| Mitigate | Reduce probability or impact |
| Transfer | Move responsibility or dependency elsewhere |
| Accept | Acknowledge and proceed without active mitigation |
| Monitor | Watch the risk and act if it grows |

### 2.7 Risk Status Values

| Value | Meaning |
|---|---|
| Open | Risk is active |
| Monitoring | Risk is being watched |
| Mitigated | Mitigation was applied |
| Accepted | Risk is accepted |
| Closed | Risk is no longer relevant |

## 3. Summary Table

| Risk ID | Date | Risk | Category | Probability | Impact | Severity | Response Strategy | Owner | Status |
|---|---|---|---|---|---|---|---|---|---|
| RISK-001 | YYYY-MM-DD | [Risk description] | Scope | Medium | High | High | Mitigate | [Owner] | Open |

## 4. Details

### RISK-001 [Risk Short Title]

*   **Date Identified:** YYYY-MM-DD
*   **Category:** Scope
*   **Probability:** Medium
*   **Impact:** High
*   **Severity:** High
*   **Response Strategy:** Mitigate
*   **Owner:** [Owner]
*   **Status:** Open
*   **Risk Description:** [What may happen]
*   **Cause:** [Why it may happen]
*   **Impact if Occurs:** [What will be affected]
*   **Mitigation Plan:** [How to reduce probability/impact]
*   **Trigger / Early Warning:** [How to know the risk is becoming real]
*   **Contingency Plan:** [What to do if the risk happens]