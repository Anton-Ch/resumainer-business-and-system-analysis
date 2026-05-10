# Business Context

## 1. Background

Modern job seekers often apply to many vacancies with slightly different requirements. A generic resume is usually not enough because recruiters and applicant tracking systems expect relevant keywords, clear positioning, and role-specific achievements.

At the same time, rewriting a resume manually for every vacancy is repetitive and inefficient. Candidates may also struggle to decide which details to include or exclude.

This project addresses that problem by combining:
- Structured profile data storage.
- AI-based resume adaptation.
- History of resume versions.
- PDF export.
- Public sharing links.

## 2. Current Situation

A typical user may already have:
- Work experience.
- Education.
- Courses and certificates.
- Skills.
- Projects.
- Achievements.
- Languages.
- Professional aspirations.
- Several possible career directions.

However, this information is usually scattered across documents, LinkedIn, notes, previous resumes, and personal memory.

## 3. Desired Future State

The user should be able to:
1. Register in the system.
2. Fill in a structured professional profile once.
3. Update profile sections over time.
4. Paste a target vacancy description.
5. Choose AI model and adaptation level.
6. Generate one or more resume versions.
7. Edit generated content before final saving.
8. Save final resume versions.
9. Download resume as a selectable-text PDF.
10. Share a permanent public resume link.

## 4. Business Objectives

### BO-001: Reduce resume adaptation effort

The system should reduce the amount of manual work required to adapt a resume for a specific vacancy.

### BO-002: Improve resume relevance

The system should help users align their resume content with the target vacancy while preserving factual accuracy.

### BO-003: Support structured career data

The system should store user career information in structured, agile and reusable sections.

### BO-004: Support multilingual resume versions

The system should support resume generation in Russian, English, or both by default or custom selected language.

### BO-005: Provide reusable resume history

The system should allow users to view, manage, and reuse previously generated resume versions.

### BO-006: Prepare for future monetization

The system should be designed so that future subscriptions or pay-per-generation billing can be added without major redesign.

### BO-007: Agile selection of AI models

The system should allow users to select specific model use: 
1) default and free provided by the system AI models via OpenRouter
2) availability to configure securely use of user's own OpenRouter API key and selected model
3) configure user's direct AI API providers and models (OpenAI, Anthropic, DeepSeek etc.)


## 5. Business Constraints

- The first version is a Capstone project, so implementation complexity must be controlled and beginner-friendly.
- The database should be normalized up to the third normal form.
- The application should be understandable for reviewers and demonstrable in a short presentation.
- AI integration should be isolated from the rest of the system to allow mock implementation if API access is limited.
- Payment functionality is out of MVP scope but should be considered in the architecture for easy future scalability.

## 6. Success Criteria

The project can be considered successful if:
- A user can create and edit a structured profile.
- A user can generate an adapted resume based on a vacancy.
- A user can save and view generated resume versions.
- A user can download a generated resume as PDF.
- A public resume link works.
- Admin can view users, their generated CVs, tokens usage statistics and block abusive users.
- Database schema clearly shows entities, relationships, cardinality, and attributes.
- UI prototype supports both basic and advanced scenarios.
