# Risks, Assumptions, and Open Questions

## 1. Purpose

This document captures known risks, assumptions, and open questions for the AI Resume Tailor Capstone project.

The purpose is to control scope, reduce uncertainty, and prepare the project for business analysis, database design, UI design, and implementation planning.

## 2. Key Assumptions

### A-001: Java Spring Boot is not allowed

The project assumes that Spring Boot cannot be used for the Capstone implementation. just pure Java Spring Framework MVC without Spring Boot.

Impact:
Only classic Spring MVC is allowed, the architecture may need to be safely simplified.

### A-002: PostgreSQL is allowed

The project assumes that PostgreSQL can be used as the relational database.

Impact:
If another database is required, SQL scripts and some configuration details may need to change.

### A-003: External API integration is allowed

The project assumes that external AI API calls through OpenRouter are allowed.

Impact:
If external calls are not allowed, the AI integration should be replaced with a mock AI generation service for demonstration.

### A-004: Vue frontend is allowed

The project assumes that Vue is used with REST API architecture accepted. However landing page should be done with Thymeleaf.

Impact:
If Vue is not allowed, the UI should be implemented with Thymeleaf and Bootstrap.

### A-005: PDF generation is allowed

The project assumes that server-side PDF generation is acceptable.

Impact:
If PDF generation becomes too complex, the project may first implement printable HTML and add PDF export later.

### A-006: Google OAuth2 may is allowed

The project assumes that Google OAuth2 registration/login may be included if implementation time allows.

Impact:
If OAuth2 adds too much complexity, standard email/password authentication should remain the MVP priority.

## 3. Scope Risks

### R-001: MVP is too large

Risk:
The project includes authentication, profile CRUD, AI integration, PDF export, public links, admin panel, statistics, cover letters, ATS JSON, and possible Vue frontend.

Impact:
The project may become too large for the available time.

Mitigation:
Prioritize the end-to-end core workflow:
Profile data → vacancy input → AI generation → draft editing → saved resume → public link → PDF download.

### R-002: Cover letter may distract from core resume workflow

Risk:
Cover letter generation is useful but not central to the Capstone database and UI requirements.

Impact:
It may consume implementation time.

Mitigation:
Keep cover letter optional. Implement only after resume generation works. But provide design placeholder for cover letter functionality not visible to user yet.

### R-003: ATS JSON endpoint may increase complexity

Risk:
The public JSON endpoint adds another public output format and requires structured resume data.

Impact:
It may require additional validation and serialization work.

Mitigation:
Use the same saved resume content structure for both PDF and JSON output.

### R-004: User-owned API keys are too complex for MVP

Risk:
Securely storing and using user-provided API keys requires encryption, masking, deletion flow, and careful logging.

Impact:
This can significantly increase security complexity.

Mitigation:
Keep user-owned API keys in future scope. Use system-configured OpenRouter key in MVP.

### R-005: Vue + REST may take more time than Thymeleaf

Risk:
A separate frontend may require more setup, CORS, authentication handling, API design, and state management.

Impact:
Frontend may delay backend implementation.

Mitigation:
Confirm allowed stack early. Prepare fallback option: Thymeleaf + Bootstrap.

## 4. Technical Risks

### R-006: AI response may be inconsistent

Risk:
AI may return malformed, incomplete, or unexpected output.

Impact:
Generated resume draft may not be parsed correctly.

Mitigation:
Use structured prompt format and validate AI response before saving. If response from AI fails parsing - repeat attempts to get proper structured response withing 5 repeated attempts as fallback. If all attempts failed - generate response to user that currently unavailable and save it in db. 

### R-007: AI provider may be unavailable

Risk:
OpenRouter or selected model may be unavailable, rate-limited, or return errors.

Impact:
Resume generation may fail during demonstration.

Mitigation:
Implement fallback to other predefined model. If all failed - implement an graceful error message to user that all models failed to response.

### R-008: PDF generation may be difficult

Risk:
Generating beautiful, selectable, A4-friendly PDF files can be technically tricky.

Impact:
PDF may look poor or break formatting.

Mitigation:
Start with simple PDF layout. Avoid complex design. Use printable HTML as fallback.

### R-009: Public URL code uniqueness

Risk:
Resume code generation must avoid collisions for the same username.

Impact:
Public links may conflict.

Mitigation:
Add a unique constraint on user_id + public_code or username + public_code.

### R-010: Database model may become inconsistent

Risk:
The project changed from generic profile section modeling to concrete profile entities, but some older references may remain.

Impact:
Documentation, ERD, and implementation may conflict.

Mitigation:
Update all documents to consistently use concrete profile entities and remove old ProfileSection references.

### R-011: Token statistics may not always be available

Risk:
Different models or providers may return usage data differently.

Impact:
Admin statistics may be incomplete.

Mitigation:
Make token fields nullable and store raw provider metadata if needed.

## 5. Data Model Risks

### R-012: Too many profile tables

Risk:
Concrete profile entities improve readability but increase the number of CRUD screens and repositories.

Impact:
Implementation workload increases.

Mitigation:
Use common patterns for CRUD:
- same controller style;
- same service style;
- reusable DTO style;
- reusable frontend form components.

### R-013: Multilingual profile data is postponed

Risk:
MVP relies on AI generation for multilingual output instead of storing localized profile fields.

Impact:
User cannot manually maintain precise English/Russian versions of profile data in MVP.

Mitigation:
Document this as a conscious MVP decision. Add localized content as future scope.

### R-014: Resume final content may be too unstructured

Risk:
If final resume is stored only as one large text field, JSON and PDF generation may become harder.

Impact:
ATS JSON and PDF sections may be difficult to generate reliably.

Mitigation:
Store final resume content as structured JSON or split it into resume section records.

Potential decision:
Use final_content_json instead of only final_content text.

## 6. Security and Privacy Risks

### R-015: Public resume links expose personal data

Risk:
Saved public resumes may include contact details and personal information.

Impact:
Private user data may be exposed if public links are shared unintentionally.

Mitigation:
Add is_public flag and allow user to disable public access.

### R-016: Admin can view sensitive user data

Risk:
Admin can view profiles and resumes.

Impact:
This creates privacy concerns.

Mitigation:
Document admin access as part of system scope. 

### R-017: API keys may leak through logs

Risk:
If future user API keys are implemented incorrectly, they may appear in logs.

Impact:
Security incident.

Mitigation:
Do not implement user API keys in MVP. Mask sensitive values in logs.

### R-018: Prompt injection through vacancy text

Risk:
Vacancy description may contain malicious instructions that try to override system prompt.

Impact:
AI may produce unsafe or incorrect output.

Mitigation:
System prompt should explicitly state that vacancy text is untrusted input and should never override system instructions.

## 7. UX Risks

### R-019: Profile form may overwhelm users

Risk:
The profile includes many sections.

Impact:
Users may abandon profile completion.

Mitigation:
Use dashboard progress, optional sections, and section-based editing.

### R-020: Three adaptation versions in two languages may overwhelm users

Risk:
Generating minimal, balanced, and maximum versions in English and Russian may produce too much content.

Impact:
User may struggle to compare versions.

Mitigation:
Use tabs and clear labels. Allow saving only selected variants. Both languages should be linked to one and the same selected adaptation level.

### R-021: Admin panel may become too complex

Risk:
Admin panel includes users, resumes, statuses, and token statistics.

Impact:
Implementation and UI may become too broad.

Mitigation:
Use a simple table-first admin interface.

## 8. Project Management Risks

### R-022: Overengineering

Risk:
The project may try to implement future product architecture instead of Capstone MVP.

Impact:
Core functionality may remain unfinished.

Mitigation:
Strictly separate 3 main implementation phases: 
1. MVP
2. Post-MVP
3. Future Scope
Usage of Agile would be beneficial. 
### R-023: Unclear reviewer expectations

Risk:
Reviewers may expect simpler database and UI artifacts.

Impact:
Too complex design may be harder to explain.

Mitigation:
Prepare a clear simplified ERD and explain future features separately.

### R-024: Time pressure

Risk:
The project may not have enough time for full implementation.

Impact:
Incomplete demo.

Mitigation:
Implement in vertical slices:
1. Auth.
2. Profile minimum data.
3. Vacancy input.
4. AI generation.
5. Draft review.
6. Save resume.
7. Public link.
8. PDF.
9. Real AI integration.
10. Admin statistics.

## 9. Open Questions

### OQ-001: Is Vue allowed for the Capstone?

Decision needed:
Can the application use Spring Boot REST API + Vue frontend, or should it use Thymeleaf?

Decision made: allowed
### OQ-002: Is external AI API usage allowed?

Decision needed:
Can the app call OpenRouter during demonstration?

Decision made: allowed

### OQ-003: Is Google OAuth2 required or optional?

Decision needed:
Should Google OAuth2 be part of MVP or future scope?

Decision made: optional
### OQ-004: Should final resume content be stored as text or JSON?

Decision needed:
Choose between:
- final_content as text;
- final_content_json as JSON;
- separate saved resume section table.

Recommended:
Use structured JSON for saved resume content if ATS JSON endpoint is required.

### OQ-005: Should cover letter be MVP or post-MVP?

Decision needed:
Cover letter is useful but should not block core resume generation.

Recommended:
Keep as optional MVP stretch goal.

Decision made: cover letter should be MVP

### OQ-006: Should ATS JSON endpoint be MVP or post-MVP?

Decision needed:
The feature is interesting and portfolio-friendly, but it increases scope.

Recommended:
Include it only if saved resume content is structured.

Decision made: ATS JSON endpoint should be post-MVP

### OQ-007: How detailed should token statistics be?

Decision needed:
Minimum:
- prompt tokens;
- completion tokens;
- total tokens;
- model.

Advanced:
- cost estimate;
- provider;
- latency;
- raw metadata.

Decision made: Minimum

### OQ-008: Should inactive users be blocked from login or only generation?

Current requirement:
Inactive users shall not be allowed to login.

Alternative:
Inactive users may log in but cannot generate resumes.

Decision needed:
Choose one behavior and keep it consistent.

Decision made: shall not be allowed to login

### OQ-009: Should forbidden users be separate from inactive users?

Current model:
UserStatus controls account access.
UserPermission controls generation access.

Decision needed:
Confirm that both are needed.

Recommended:
Keep both:
- UserStatus = account access.
- UserPermission = AI generation access.

Decision made: both are needed

### OQ-010: Should profile entities support soft delete?

Decision needed:
Some documents mention profile section soft delete, but the current concrete entity model does not consistently define is_deleted for all profile entities.

Recommended:
Either:
- add is_deleted and deleted_at to all user-owned profile entities;
- or keep hard delete for simple MVP profile records.

Decision made: profile entities should support soft delete
### OQ-011: Should vacancy and company data have separate entities?

Current scope:
Vacancy description and company information are stored with generation request.

Possible improvement:
Create TargetVacancy entity.

Decision needed:
If users need to reuse vacancies, create separate TargetVacancy.
If not, store vacancy data in ResumeGenerationRequest.

Decision made: should be separate entities but no reuse for simplicity

### OQ-012: Should public resume open PDF directly or a web page with embedded PDF?

Decision needed:
Option A:
Public link opens a resume web page with Download PDF button.

Option B:
Public link directly opens PDF.

Recommended:
Use public web page first. It is easier to extend and can include PDF and JSON links.

Decision made: open PDF directly

## 10. Critical Decisions Before Implementation

Before coding, the following decisions should be finalized:

1. Spring Boot REST + Vue or Spring MVC + Thymeleaf.
2. Real OpenRouter integration or mock AI provider for MVP demo.
3. Saved resume storage format: text, JSON, or section table.
4. Cover letter: MVP or stretch goal.
5. ATS JSON endpoint: MVP or future scope.
6. OAuth2: MVP or future scope.
7. Token statistics level.
8. Soft delete strategy for profile entities.
9. Public resume page behavior.
10. Final ERD entity list.
