# Risk Register

**Project ID:** `resumainer`  
**Product Name:** ResumAIner  
**Date Created:** 2026-05-10  
**Last Updated:** 2026-05-10  
**Author:** Anton  
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
| Compliance  | Risk related to mandatory capstone requirements             |

### 2.3 Probability Values

| Value | Meaning |
|---|---|
| Low | Unlikely to happen |
| Medium | Possible |
| High | Likely |

### 2.4 Impact Values

| Value | Meaning                                             |
| -------- | --------------------------------------------------- |
| Low | Minor inconvenience                                 |
| Medium | Noticeable rework or delay                          |
| High | Major rework, demo risk, or quality issue           |
| Critical | May block project completion or capstone compliance |

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
| RISK-001 | 2026-05-10 | MVP may become too large because of AI, PDF, public links, admin panel, ATS JSON, and future monetization ideas | Scope | High | High | Critical | Mitigate | BA | Open |
| RISK-002 | 2026-05-11 | UI/UX questionnaire may become too broad and difficult to analyze | UX | Medium | Medium | Medium | Mitigate | BA | Open |
| RISK-003 | 2026-05-11 | UI requirements may focus on visual preferences instead of functional screen-level decisions | UX | Medium | High | High | Mitigate | BA | Open |
| RISK-004 | 2026-05-11 | UI ideas may be accepted without checking implementation feasibility | Technical | Medium | High | High | Mitigate | BA / Developer | Open |
| RISK-005 | YYYY-MM-DD | [Risk description] | [Category] | [Low/Medium/High] | [Low/Medium/High/Critical] | [Low/Medium/High/Critical] | [Avoid/Mitigate/Transfer/Accept/Monitor] | [Owner] | Open |

## 4. Details

### RISK-001 MVP Scope Creep

*   **Date Identified:** 2026-05-10
*   **Category:** Scope
*   **Probability:** High
*   **Impact:** High
*   **Severity:** Critical
*   **Response Strategy:** Mitigate
*   **Owner:** BA
*   **Status:** Open
*   **Risk Description:** MVP may become too large because the project includes AI generation, PDF export, public links, admin panel, token statistics, ATS JSON endpoint, and future monetization ideas.
*   **Cause:** The product idea has strong expansion potential and combines several technically different areas.
*   **Impact if Occurs:** Development may become delayed, core functionality may remain unfinished, and the final demo may become weaker.
*   **Mitigation Plan:** Separate MVP, MVP Stretch, Post-MVP, and Future Scope. Use the Requirement Readiness Checklist before accepting requirements into MVP. Apply de-scoping rule from the Governance Plan.
*   **Trigger / Early Warning:** More than three MVP features remain unclear before development starts, or new features are added without removing/postponing existing ones.
*   **Contingency Plan:** Freeze MVP around the core flow: profile data → vacancy input → generated draft → review/edit → saved resume → public link → PDF download.

### RISK-002 UI/UX Questionnaire Scope Becomes Too Broad

*   **Date Identified:** 2026-05-11
*   **Category:** UX
*   **Probability:** Medium
*   **Impact:** Medium
*   **Severity:** Medium
*   **Response Strategy:** Mitigate
*   **Owner:** BA
*   **Status:** Open
*   **Risk Description:** The UI/UX questionnaire may become too broad and generate answers that are difficult to analyze or convert into practical UI requirements.
*   **Cause:** The product includes many possible pages, user roles, actions, states, and future features.
*   **Impact if Occurs:** Elicitation results may become noisy, making it harder to identify MVP screens and page-level requirements.
*   **Mitigation Plan:** Keep questions grouped by respondent role and screen. Use controlled answer values such as MVP, MVP Stretch, Post-MVP, Future Scope, Must Have, Should Have, and Not Needed.
*   **Trigger / Early Warning:** Respondents provide vague feedback or many answers cannot be converted into concrete UI decisions.
*   **Contingency Plan:** Reduce the questionnaire to the core MVP screens and move secondary questions to a follow-up review.

### RISK-003 UI Feedback Focuses on Visual Preferences Instead of Functional Decisions

*   **Date Identified:** 2026-05-11
*   **Category:** UX
*   **Probability:** Medium
*   **Impact:** High
*   **Severity:** High
*   **Response Strategy:** Mitigate
*   **Owner:** BA
*   **Status:** Open
*   **Risk Description:** Respondents may focus on colors, style, and general interface preferences instead of identifying required pages, blocks, actions, errors, empty states, and guidance.
*   **Cause:** UI/UX discussions often drift toward visual design instead of functional usability.
*   **Impact if Occurs:** Questionnaire results may not provide enough useful input for sitemap, wireframes, UI requirements, and acceptance criteria.
*   **Mitigation Plan:** Structure the questionnaire screen-by-screen and ask about page necessity, required blocks, key actions, errors, empty states, and user guidance before asking about visual preferences.
*   **Trigger / Early Warning:** Most feedback mentions visual style but does not clarify required functionality.
*   **Contingency Plan:** Conduct a follow-up review focused only on screen structure, workflow, and MVP actions.

### RISK-004 UI Requirements Are Not Checked for Implementation Feasibility

*   **Date Identified:** 2026-05-11
*   **Category:** Technical
*   **Probability:** Medium
*   **Impact:** High
*   **Severity:** High
*   **Response Strategy:** Mitigate
*   **Owner:** BA / Developer
*   **Status:** Open
*   **Risk Description:** UI ideas may be accepted into MVP without checking whether they are realistic within the selected architecture, timeline, and technical constraints.
*   **Cause:** User-facing features such as tabs, comparison views, PDF download, public pages, admin statistics, and ATS JSON may increase implementation complexity.
*   **Impact if Occurs:** MVP scope may become too difficult to implement, causing delays or unfinished features.
*   **Mitigation Plan:** Include Developer / Technical Reviewer questions in the questionnaire and check each significant UI requirement against complexity, data impact, validation, security, and deployment constraints.
*   **Trigger / Early Warning:** Several UI requirements are marked as MVP but have High or Critical implementation complexity.
*   **Contingency Plan:** Move complex UI features to MVP Stretch, Post-MVP, or Future Scope.

### RISK-005 [Risk Short Title Template]

*   **Date Identified:** YYYY-MM-DD
*   **Category:** [Scope / Technical / Data / Security / UX / Integration / Deployment / Schedule / Quality / Compliance]
*   **Probability:** [Low / Medium / High]
*   **Impact:** [Low / Medium / High / Critical]
*   **Severity:** [Low / Medium / High / Critical]
*   **Response Strategy:** [Avoid / Mitigate / Transfer / Accept / Monitor]
*   **Owner:** [Owner]
*   **Status:** Open
*   **Risk Description:** [What may happen]
*   **Cause:** [Why it may happen]
*   **Impact if Occurs:** [What will be affected]
*   **Mitigation Plan:** [How to reduce probability/impact]
*   **Trigger / Early Warning:** [How to know the risk is becoming real]
*   **Contingency Plan:** [What to do if the risk happens]