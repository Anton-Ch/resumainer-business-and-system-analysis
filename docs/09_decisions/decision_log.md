# [[Без названия]]


# Decision Log

**Project ID:** `resumainer`
**Product Name:** ResumAIner
**Date Created:** 2026-05-10
**Last Updated:** 2026-05-15
**Author:** Anton
**Version:** 2.0
**Status:** Active
**Related BABOK Area:** 3.3 Plan Business Analysis Governance

---

## 1. Description

This document records major business analysis, system analysis, architecture, scope, security, and implementation decisions made during the project.

Each decision includes context, selected option, rejected alternatives, rationale, impact, and follow-up actions.

## 2. Usage Rules and Controlled Values

### 2.1 Usage Rules

- Record only meaningful decisions that affect scope, requirements, architecture, data model, UI/UX, deployment, security, or project process.
- Do not record minor wording or formatting changes here.
- Do not delete decisions after they are made.
- If a decision changes, mark the old decision as `Superseded` and create a new decision.
- Use `Change Request Log` if a decision causes a non-trivial change to approved artifacts.
- Use consistent decision IDs: `DEC-001`, `DEC-002`, `DEC-003`.

### 2.2 Decision Type Values

| Value | Meaning |
|---|---|
| Architecture | System structure, layers, frameworks, backend/frontend approach |
| Scope | MVP, stretch goals, post-MVP, or future scope |
| Requirement | FR/NFR, acceptance criteria, or business rule decision |
| Data Model | Entities, tables, fields, relationships, or storage format |
| UI/UX | Screens, flows, layout, interaction, or page behavior |
| Deployment | Hosting, Docker, server, domain, or environment |
| Security | Authentication, authorization, secrets, public access, API keys |
| Process | BA workflow, governance, documentation, or implementation sequence |

### 2.3 Decision Status Values

| Value | Meaning |
|---|---|
| Proposed | Decision is suggested but not approved |
| Approved | Decision is accepted and active |
| Superseded | Decision was replaced by a newer decision |
| Rejected | Decision option was considered but not selected |

## 3. Summary Table

| ID | Date | Type | Title | Rationale | Impact | Status |
|---|---|---|---|---|---|---|
| DEC-001 | 2026-05-10 | Architecture | Use plain JDBC instead of ORM | Mandatory capstone constraint; ORM is not allowed | Affects DAO layer, transaction handling, and object mapping | Approved |
| DEC-002 | 2026-05-11 | Scope | Landing Page is mandatory for MVP | Needed for visitor understanding and login/register entry | Adds Landing Page to MVP scope | Approved |
| DEC-003 | 2026-05-11 | UI/UX | Replace Dashboard terminology with Home page | Home is clearer for main post-login pages | Affects UI labels, sitemap, and documentation | Approved |
| DEC-004 | 2026-05-11 | Scope | Move User Settings into My Profile | Reduces page count and navigation complexity | Eliminates separate Settings page | Approved |
| DEC-005 | 2026-05-12 | Scope | Integrate resume listing into User Home | Faster access to saved resumes | Eliminates separate Resume History page | Approved |
| DEC-006 | 2026-05-11 | UI/UX | Public recruiter link opens PDF directly | Recruiters need fast PDF viewing, printing, and saving | Changes public access behavior | Approved |
| DEC-007 | 2026-05-11 | Architecture | Use hybrid frontend approach | Thymeleaf is enough for Landing Page; Vue fits main app dynamics | Affects frontend architecture and deployment | Approved |
| DEC-008 | 2026-05-13 | Security | Mask saved API keys in AI Model Details | Prevents accidental secret exposure | Affects admin UI, logging, and model settings | Approved |
| DEC-009 | 2026-05-11 | Process | Use mock AI generation before real OpenRouter integration | Reduces external dependency risk | Affects implementation sequence and testing | Approved |
| DEC-010 | 2026-05-13 | UI/UX | Use wireframe field findings as approved input | Field-level details were confirmed during wireframe preparation | Affects My Profile and Generate Resume requirements | Approved |
| DEC-011 | 2026-05-13 | UI/UX | Use card list + Add/Edit form for repeatable profile sections | Clear and reusable pattern for profile records | Affects Work Experience, Projects, Education, Courses | Approved |
| DEC-012 | 2026-05-13 | UI/UX | Use automatic sorting for repeatable profile sections | Reduces manual ordering effort and keeps resumes logical | Affects profile list display and query ordering | Approved |
| DEC-013 | 2026-05-13 | Data Model | Use simplified Additional Info table for MVP | Keeps profile data manageable within MVP timeline | Affects profile data model and My Profile scope | Approved |
| DEC-014 | 2026-05-15 | Scope | Remove Resume Details pages (user and admin) | Pages add no value; PDF actions belong in list views and post-save flow | Eliminates user and admin Resume Details pages; PDF actions from User Home and Resumes table | Approved |
| DEC-015 | 2026-05-16 | UI/UX | Resume Details as modal popup on User Home | Provides PDF link copy, download, and cover letter in one place without a separate page | Replaces PDF action column with Details column + modal popup | Approved |
| DEC-016 | 2026-05-16 | Scope | Cover letter generation is MVP | Less implementation effort than post-MVP phase | Cover letter is generated by LLM, editable in Resume Review, viewable in Details modal | Approved |
| DEC-017 | 2026-05-16 | Architecture | HTML-to-PDF generation on Java server side | Easier to maintain structured layout with HTML templates than direct PDF generation | Resume generated as HTML first, then converted to PDF on Java backend | Approved |
| DEC-018 | 2026-05-16 | Scope | Courses and Certificates section is mandatory for MVP | System targets users with practical experience and completed courses | Courses section stays in MVP scope, FR-006 priority unchanged (Medium) | Approved |
| DEC-019 | 2026-05-16 | Data Model | Two-page default HTML resume template for all resumes | Ensures consistent visual quality and even content spreading | Standard two-page layout; separate technical approach doc needed for content distribution rules | Approved |

## 4. Details

### DEC-001 Use Plain JDBC Instead of ORM

**Date:** 2026-05-10  
**Type:** Architecture  
**Status:** Approved  
**Context:** The Capstone requires database access through plain JDBC and demonstration of DAO pattern, SQL handling, transactions, and custom Connection Pool.  
**Selected Option:** Plain JDBC with DAO layer and manual Connection Pool.  
**Rejected Alternatives:** Hibernate, JPA, Spring Data JPA, MyBatis.  
**Rationale:** Plain JDBC is required and demonstrates direct database access skills.  
**Impact:** Requires DAO classes, SQL scripts, ResultSet mapping, and explicit transaction handling.  
**Follow-up Actions:** Keep architecture and requirements documents free of ORM-based assumptions.

### DEC-002 Landing Page Is Mandatory for MVP

**Date:** 2026-05-11  
**Type:** Scope  
**Status:** Approved  
**Context:** UI/UX elicitation confirmed that the Landing Page is essential for explaining product value and converting visitors to users.
**Selected Option:** Landing Page is included in MVP.  
**Rejected Alternatives:** Optional or post-MVP Landing Page.  
**Rationale:** Visitors need a clear entry point and short product explanation before login/register.  
**Impact:** Adds Landing Page to MVP and frontend scope.  
**Follow-up Actions:** Implement Landing Page with product value, short “How it works”, and login/register links.

### DEC-003 Replace Dashboard Terminology with Home Page

**Date:** 2026-05-11  
**Type:** UI/UX  
**Status:** Approved  
**Context:** UI/UX elicitation found "Dashboard" terminology confusing; "Home page" is clearer for main post-login pages.
**Selected Option:** Use `User Home` and `Admin Home`.  
**Rejected Alternatives:** Generic `Dashboard` wording.  
**Rationale:** Home page wording is clearer for main post-login pages.  
**Impact:** Affects sitemap, UI labels, wireframes, and documentation.  
**Follow-up Actions:** Use Home terminology consistently.

### DEC-004 Move User Settings into My Profile

**Date:** 2026-05-11  
**Type:** Scope  
**Status:** Approved 
**Context:** UI/UX elicitation confirmed that separate User Settings page increases navigation complexity without sufficient benefit.
**Selected Option:** User settings are sections inside My Profile.  
**Rejected Alternatives:** Separate User Settings page.  
**Rationale:** Reduces navigation complexity and keeps user-owned data in one place.  
**Impact:** Eliminates separate Settings page and expands My Profile structure.  
**Follow-up Actions:** Add language, account, and resume preference settings to My Profile.

### DEC-005 Integrate Resume Listing into User Home

**Date:** 2026-05-12  
**Type:** Scope  
**Status:** Approved
**Context:** Updated elicitation results showed it is more logical to display user's resumes directly in User Home for quick access rather than separate page.
**Selected Option:** User Home includes searchable/sortable resume listing table.  
**Rejected Alternatives:** Separate Resume History page.  
**Rationale:** Users need fast access to saved resumes after login.  
**Impact:** Eliminates separate Resume History page and expands User Home.  
**Follow-up Actions:** User Home must support resume search, sorting, details access, PDF download, and link copying.

### DEC-006 Public Recruiter Link Opens PDF Directly

**Date:** 2026-05-11  
**Type:** UI/UX  
**Status:** Approved  
**Context:** UI/UX elicitation confirmed that recruiters prefer direct PDF access without intermediate web page.
**Selected Option:** Public link serves the saved PDF directly.  
**Rejected Alternatives:** Public web wrapper page before PDF.  
**Rationale:** Recruiters need direct viewing, printing, copying text, and saving PDF.  
**Impact:** Public access flow serves PDF, not HTML.  
**Follow-up Actions:** Implement public URL routing with safe access checks.

### DEC-007 Use Hybrid Frontend Approach

**Date:** 2026-05-11  
**Type:** Architecture  
**Status:** Approved  
**Context:** UI/UX elicitation confirmed need for simple landing page but dynamic UI for authenticated sections.
**Selected Option:** Thymeleaf only for Landing Page; Vue for main application if feasible.  
**Rejected Alternatives:** Pure Thymeleaf/JSP or pure Vue for everything.  
**Rationale:** Landing Page is simple; authenticated UI needs dynamic forms, tables, and review flows.  
**Impact:** Affects frontend structure, Docker Compose, and backend endpoint design.  
**Follow-up Actions:** Validate Vue feasibility before implementation baseline.

### DEC-008 Mask Saved API Keys in AI Model Details

**Date:** 2026-05-13  
**Type:** Security  
**Status:** Approved  
**Context:** UI/UX elicitation confirmed that administrators need to see full API keys for oversight and management.
**Selected Option:** Saved API keys are always masked; admin can replace or delete the key, but cannot view it in full after saving.  
**Rejected Alternatives:** Showing full API keys in admin UI; logging API keys.  
**Rationale:** API keys are secrets. Displaying or logging them creates unnecessary security risk.  
**Impact:** Affects AI Model Details UI, logging rules, and admin model settings.  
**Follow-up Actions:** Define API key storage, masking, replacement, deletion, and logging rules.

### DEC-009 Use Mock AI Generation Before Real OpenRouter Integration

**Date:** 2026-05-11  
**Type:** Process  
**Status:** Approved  
**Context:** UI/UX elicitation confirmed that mock AI generation should be used initially to reduce dependency risk.
**Selected Option:** Implement mock AI generation first.  
**Rejected Alternatives:** Starting with real OpenRouter integration immediately.  
**Rationale:** Protects MVP development from external API dependency and allows earlier vertical slice testing.  
**Impact:** Affects implementation sequence and testing.  
**Follow-up Actions:** Build AI integration behind an interface with mock and OpenRouter implementations.

### DEC-010 Use Wireframe Field Findings as Approved Input

**Date:** 2026-05-13  
**Type:** UI/UX  
**Status:** Approved  
**Context:** During wireframes preparation updated information arised on fields to be used.
**Selected Option:** Use field-level wireframe findings as approved input for UI/UX requirements and data model drafts.  
**Rejected Alternatives:** Keeping only high-level page descriptions.  
**Rationale:** Wireframe preparation clarified actual fields, validation rules, error messages, and data model needs.  
**Impact:** Affects My Profile, Generate Resume, validation requirements, and traceability.  
**Follow-up Actions:** Create `wireframe_field_requirements.md` and update related logs/matrices.

### DEC-011 Use Card List + Add/Edit Form Pattern for Repeatable Profile Sections

**Date:** 2026-05-13  
**Type:** UI/UX  
**Status:** Approved  
**Context:** During wireframes preparations decision was made to use card list
**Selected Option:** Repeatable sections use a card list with Add/Edit form.  
**Rejected Alternatives:** One large form for all records; table-only editing.  
**Rationale:** Card lists are clearer for profile records and easier to review on wireframes.  
**Impact:** Applies to Work Experience, Projects & Volunteering, Education, Courses & Certificates.  
**Follow-up Actions:** Reflect this pattern in wireframes and UI requirements.

### DEC-012 Use Automatic Sorting for Repeatable Profile Sections

**Date:** 2026-05-13  
**Type:** UI/UX  
**Status:** Approved  
**Context:** During wireframes preparations decision was made on how to sort cards.
**Selected Option:** Sort repeatable profile records automatically.  
**Rejected Alternatives:** Manual ordering in MVP.  
**Rationale:** Automatic sorting keeps records consistent and reduces implementation/UI complexity.  
**Impact:** Affects display logic and DAO/service query ordering.  
**Follow-up Actions:** Define sorting rules in wireframe field requirements.

### DEC-013 Use Simplified Additional Info Table for MVP

**Date:** 2026-05-13  
**Type:** Data Model  
**Status:** Approved  
**Context:** During wireframes preparations Additional Info section of Profile page was simplified for MVP
**Selected Option:** Use a simplified Additional Info model for MVP.  
**Rejected Alternatives:** Fully normalized separate tables for every additional profile item.  
**Rationale:** Simplifies MVP implementation while preserving useful AI context.  
**Impact:** Affects profile data model and My Profile scope.  
**Follow-up Actions:** Keep fields clear and migrate to normalized structures only if needed later.

### DEC-014 Remove Resume Details Pages (User and Admin)

**Date:** 2026-05-15
**Type:** Scope
**Status:** Approved
**Context:** Wireframe review revealed that neither user nor admin Resume Details pages provide standalone value. All functions — PDF preview, download, public link copying — can be performed directly from table-level actions (User Home for users, Resumes table for admin) or the post-save success flow after Resume Review.
**Selected Option:** Remove both user and admin Resume Details pages. PDF viewing, download, and public link actions are available from User Home table and the admin Resumes table. Post-save flow offers immediate PDF preview and link copy.
**Rejected Alternatives:** Keeping dedicated Resume Details pages for user or admin.
**Rationale:** Eliminates unnecessary pages that add navigation complexity and implementation effort without incremental value. Admin can view any generated and saved resume PDF the same way as a user — from the list view.
**Impact:**
- **Scope:** Eliminates both user and admin Resume Details pages from MVP.
- **Requirements:** FR-009 is superseded; FR-008 covers PDF and public link actions from User Home.
- **Data Model:** No data model change; SavedResume and PdfFile remain.
- **UI/UX:** User Home table and admin Resumes table provide direct PDF actions; post-save flow shows PDF preview and link copy.
- **Risks:** Reduces UI scope and implementation effort.

### DEC-015 Resume Details as Modal Popup on User Home

**Date:** 2026-05-16
**Type:** UI/UX
**Status:** Approved
**Context:** Early wireframes showed PDF actions as a direct Link to PDF column in the User Home resume table. Refined wireframe design revealed a Details column with an `Open details` button, leading to a modal popup containing PDF link copy, PDF download, and cover letter text.
**Selected Option:** Replace the Link to PDF column with a Details column. Clicking `Open details` opens a modal popup with PDF link copy, PDF download, and cover letter display.
**Rejected Alternatives:** Direct PDF download column; separate Resume Details page; no modal with all actions in table row.
**Rationale:** Modal provides all resume output actions (PDF link, download, cover letter) in one focused view without navigating away from User Home. Cover letter display is included because cover letter is MVP.
**Impact:**
- **Scope:** No new page; modal replaces both the separate Resume Details page (already removed in DEC-014) and the simple PDF column.
- **Requirements:** FR-008 acceptance criteria updated to reflect modal behavior.
- **Data Model:** No change.
- **UI/UX:** User Home table has Details column; clicking opens modal.
- **Risks:** Reduces need for a separate page; modal complexity is manageable.
**Follow-up Actions:** Update FR-008 acceptance criteria and User Home wireframe field requirements.

### DEC-016 Cover Letter Generation Is MVP

**Date:** 2026-05-16
**Type:** Scope
**Status:** Approved
**Context:** During wireframe refinement, the question arose whether cover letter generation should remain part of MVP or be moved to post-MVP. The cover letter feature was already visible in the Resume Review wireframe and in the Resume Details modal.
**Selected Option:** Include cover letter generation in MVP. LLM generates cover letter text as part of the resume generation process. User can edit the generated cover letter before saving. Cover letter is viewable in the Resume Details modal and can be copied.
**Rejected Alternatives:** Post-MVP cover letter generation; manual cover letter entry without AI generation.
**Rationale:** Generating the cover letter at the same time as the resume requires less implementation effort than adding it as a separate post-MVP feature. The LLM already has the vacancy context and profile data — asking it to generate a cover letter as additional output adds minimal complexity.
**Impact:**
- **Scope:** Cover letter moves from stretch/future to MVP.
- **Requirements:** New FR-011 (Cover letter generation) and FR-012 (Cover letter in generation request).
- **Data Model:** Cover letter text field in generation request and saved resume.
- **UI/UX:** Cover letter field in Resume Review; cover letter display in Details modal.
- **Risks:** Slightly increases generation complexity but managed within existing generation flow.
**Follow-up Actions:** Create FR-011 and FR-012. Add cover letter to generation request data model and Resume Review UI requirements.

### DEC-017 HTML-to-PDF Generation on Java Server Side

**Date:** 2026-05-16
**Type:** Architecture
**Status:** Approved
**Context:** PDF generation is required for resume download. Two approaches were considered: generating PDF directly on the Java side, or rendering HTML first and converting to PDF. Wireframe confirmation and technical review favored HTML-first approach.
**Selected Option:** Resume is generated as HTML first using a structured template with replaceable sections. The HTML is then converted to PDF on the Java backend using a PDF generation library. Vue does not handle PDF creation.
**Rejected Alternatives:** Direct PDF generation in Java without HTML intermediate; client-side PDF generation in Vue.
**Rationale:** HTML templates are easier to create, maintain, and review for layout correctness. The structured two-page template ensures consistent output. Java-side conversion keeps PDF logic centralized and avoids browser-dependent behavior.
**Impact:**
- **Scope:** PDF generation approach is defined and stable.
- **Architecture:** PDF library required on Java backend.
- **Data Model:** No change. PDF metadata stored in existing PdfFile entity.
- **UI/UX:** Resume Review generates synchronized HTML preview (not separate PDF preview).
**Follow-up Actions:** Create a separate technical approach document for the two-page HTML template and even content spreading rules.

### DEC-018 Courses and Certificates Section Is Mandatory for MVP

**Date:** 2026-05-16
**Type:** Scope
**Status:** Approved
**Context:** During wireframe review, the question arose whether Courses and Certificates should remain optional or become mandatory for the MVP profile. The target users for the system are professionals with practical experience and completed courses, not complete beginners.
**Selected Option:** Courses and Certificates section is mandatory for MVP. Users must provide at least some course/certificate records for the resume generation to produce meaningful output.
**Rejected Alternatives:** Making Courses optional; removing Courses from MVP.
**Rationale:** The system is designed for users who have courses and practical experience to adapt their resumes for specific vacancies. Excluding or making Courses optional weakens the core value proposition for the target audience.
**Impact:**
- **Scope:** Courses section stays in MVP with mandatory status.
- **Requirements:** FR-006 priority stays Medium but scope confirmed MVP.
- **Data Model:** No change.
- **UI/UX:** Courses section prominently placed in profile flow.
**Follow-up Actions:** Reflect mandatory status in FR-006 notes.

### DEC-019 Two-Page Default HTML Resume Template

**Date:** 2026-05-16
**Type:** Data Model
**Status:** Approved
**Context:** The project needs a consistent resume output format. Wireframes confirmed that a two-page layout is acceptable. A standard template ensures all generated resumes have consistent visual quality and professional appearance.
**Selected Option:** All generated resumes use a standard two-page HTML template. Content is spread evenly across two pages. A separate technical approach document (Approach for Even Spreading A4) explains how sections, courses count, and work experience records are distributed to maintain visual balance.
**Rejected Alternatives:** One-page only template; dynamic page count; no template standard.
**Rationale:** A standard template ensures consistent quality, simplifies PDF generation (DEC-017), and is easier to review and maintain. Two pages provide enough space for profile sections, work experience, education, courses, and projects without feeling cramped.
**Impact:**
- **Scope:** Template approach is defined.
- **Data Model:** No change to entities.
- **Implementation:** Requires HTML template with section placeholders and content distribution logic.
**Follow-up Actions:** Create the Approach for Even Spreading A4 document with page 1 and page 2 section mapping and distribution rules.
**Follow-up Items:**
- Page 1: max 7 most relevant courses.
- Page 2: if 5+ work experience records, max 5 courses; if fewer than 5 work experience records, max 8 courses.

---

 
**Date:** YYYY-MM-DD
**Type:** [Architecture / Scope / Requirement / Data Model / UI/UX / Deployment / Security / Process]
**Status:** Proposed
**Context:** [Why is this decision needed?]
**Selected Option:** [What was chosen?]
**Rejected Alternatives:** [What else was considered?]
**Rationale:** [Why this option was chosen]
**Impact:**
- **Scope:** [Impact on MVP or future scope]
- **Requirements:** [Affected FR/NFR if any]
- **Data Model:** [Affected entities/tables if any]
- **Requirements:** [Affected layers, technologies, or patterns]
- **Risks:** [New or reduced risks]
**Follow-up Actions:** [Optional next steps]
 
***
*This decision log follows the Information Management Plan structure and conventions for the ResumAIner project. Decisions are recorded with full context for auditability and reuse.*