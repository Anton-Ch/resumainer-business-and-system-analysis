# Spec Kit Handoff Plan

## 1. Purpose

This document describes how business and system analysis artifacts should be transformed into inputs for Spec-Driven Development using Spec Kit.

The main goal is to avoid jumping directly from vague ideas to code. Business analysis should define the problem, scope, users, workflows, data model, risks, and requirements first. Spec Kit should then transform clarified requirements into implementation specifications, plans, and tasks.

## 2. Overall Workflow

Suggested workflow:
1. Prepare initial draft input files in `drafts/`.
2. Analyze project context.
3. Review created BA/SA artifacts.
4. Double check, correct and approve key decisions.
5. Prepare refined PRD and functional specification.
6. Use Spec Kit to create implementation specifications.
7. Develop implementation plan.
8. Write task breakdown.
9. Implement project feature by feature.
10. Keep documentation updated after each major decision.

## 3. Draft Input Artifacts for BA/SA Analysis

Initial input files:
1. Project vision.md
2. Business context.md
3. Stakeholders and personas.md
4. Scope and mvp.md
5. User workflows.md
6. Requirements.md
7. Data model.md
8. ux ui requirements.md
9. Al context.md
10. Risks assumptions.md
11. Spec kit handoff plan.md
12. Technical Constraints.md
13. Architecture Requirements.md

## 4. Expected BA/SA Analysis Outputs

BA/SA analysis should help produce refined outputs as per BABOK which may include:
- business requirements document;
- stakeholder analysis;
- user stories;
- use cases;
- functional requirements;
- non-functional requirements;
- risk register;
- open questions register;
- acceptance criteria;
- data model recommendations;
- erd;
- wireframes;
- UI scenario analysis;
- implementation readiness assessment.

## 5. Finalization Review Stage

Before using Spec Kit, the following artifacts should be finalized and reviewed:

### 5.1 MVP Scope

Confirm:
- what is definitely included;
- what is stretch goal;
- what is future scope.

### 5.2 Data Model

Confirm:
- final entity list;
- relationships;
- cardinality;
- mandatory and optional attributes;
- soft delete strategy;
- 3NF compliance.

### 5.3 Architecture

Confirm:
- Spring MVC REST + Vue + Thymeleaf (hybrid approach).

### 5.4 AI Integration

Confirm:
- real OpenRouter integration;
- token usage logging;
- error handling.

### 5.5 Resume Storage Format

Confirm:
- text;
- JSON;
- separate resume section table.

Recommended:
Use structured JSON for saved resume content if ATS JSON endpoint is included.
Or provide in design to versions: human-friendly and ats-friendly

## 6. Spec Kit Feature Breakdown

The project should be split into clear features.

### Feature 1: User Authentication and Authorization

Includes:
- registration;
- login;
- logout;
- password hashing;
- roles;
- user status;
- generation permission.

### Feature 2: User Profile Management

Includes:
- CRUD for contact data;
- CRUD for skills;
- CRUD for experience;
- CRUD for education;
- CRUD for courses;
- CRUD for projects;
- CRUD for languages;
- CRUD for positioning;
- CRUD for aspirations;
- personal information.

### Feature 3: Resume Generation Request

Includes:
- vacancy description input;
- company information input;
- AI model selection;
- adaptation level selection;
- language selection;
- request creation;
- request status tracking.

### Feature 4: AI Integration

Includes:
- OpenRouter client;
- mock AI provider;
- prompt builder;
- AI response parser;
- error handling;
- token usage logging.

### Feature 5: Resume Draft Review

Includes:
- displaying generated draft;
- editing generated fields;
- comparing adaptation variants;
- selecting final version.

### Feature 6: Saved Resume Management

Includes:
- save final resume;
- resume history;
- resume details;
- soft delete;
- edit saved resume if allowed.

### Feature 7: Public Resume Sharing

Includes:
- public URL generation;
- public resume page;
- public PDF download;
- public JSON endpoint if included.

### Feature 8: PDF Export

Includes:
- A4 layout;
- selectable text;
- consistent formatting;
- download action.

### Feature 9: Admin Panel

Includes:
- user list;
- user details;
- user status update;
- generation permission update;
- resume review;
- AI usage statistics.

### Feature 10: Optional Cover Letter

Includes:
- checkbox during generation;
- AI cover letter generation;
- cover letter preview;
- cover letter editing;
- cover letter saving.

## 7. Suggested Spec Kit Order

Considered implementation order:
1. Main landing Thymeleaf page.
2. Authentication and authorization.
3. Core data model and migrations.
4. Basic profile CRUD.
5. Resume generation request form.
6. Mock AI generation.
7. Draft preview and editing.
8. Save final resume.
9. Resume history.
10. Public resume page.
11. PDF export.
12. OpenRouter real integration.
13. Token usage statistics.
14. Admin panel.
15. ATS JSON endpoint.
16. Cover letter.

Reason:
This order reduces risk because the application becomes demonstrable before real AI integration is completed.

## 8. Spec Quality Rules

Each Spec Kit feature specification considered to include:
- user story;
- business goal;
- functional requirements;
- non-functional requirements;
- acceptance criteria;
- data entities affected;
- API endpoints or page routes;
- validation rules;
- error cases;
- security considerations;
- test scenarios.

## 9. Acceptance Criteria Template

Each feature should use clear acceptance criteria.

Example format:

### Scenario: User saves generated resume

Given the user is logged in  
And the user has generated a resume draft  
When the user edits the draft and clicks Save Final Version  
Then the system saves the final resume  
And the resume appears in Resume History  
And the resume receives a public URL  
And the user can download a PDF version

## 10. Definition of Done

A feature is done when:
- code is implemented;
- database changes are applied;
- validation is implemented;
- authorization is checked;
- error handling is present;
- UI supports the scenario;
- integration and unit test created;
- basic tests or manual test cases are documented;
- documentation is updated.

## 11. Portfolio Documentation Plan

The GitHub repository should show both BA and developer value. 

Decided to do 3 GitHub repositories:

1. General portfolio repository — short overview and quick-glance explanation of the portfolio project with links to separate BA and Java Development repositories.
2. BA portfolio repository — full showcase of my Business Analysis and System Analysis skills on this project.
3. Java developer portfolio repository — full showcase of my Java development skills on this project as well as Vue for front-end part.

All the docs mainly intended to be saved in markdown format for better readability in Github.

Repository structure:

### 11.1 General Portfolio Repository

Purpose:
Provide a short, minimalistic recruiter-friendly overview of the whole project and direct readers to the detailed BA and Java repositories.

Planned structure:
- `/README.md`
  - project overview
  - problem statement
  - product idea
  - short MVP description
  - key features
  - screenshots or mockups
  - links to BA portfolio repository
  - links to Java developer repository
  - short explanation of my role, learning goals and demonstrated skills

- `/assets/`
  - screenshots
  - diagrams
  - preview images
  - demo GIFs, if available

- `/docs/`
  - short project summary
  - short architecture overview
  - roadmap (updatable at each reasonable step)
  - repository navigation guide

### 11.2 Business/System Analysis Portfolio Repository

Purpose:
Show the project from the perspective of a Business Analyst / System Analyst: problem understanding, stakeholder analysis, requirements, workflows, data modeling, risks, and product thinking.

Planned structure:
- `/README.md`
  - BA case study overview
  - project context
  - business problem
  - solution concept
  - BA artifacts navigation
  - my role as Business Analyst / System Analyst

- `/docs/project-context/`
  - project vision
  - business context
  - goals and objectives
  - scope and MVP
  - assumptions and constraints

- `/docs/stakeholders-and-users/`
  - stakeholders
  - personas
  - user needs
  - user objectives
  - user problems and pain points

- `/docs/requirements/`
  - business requirements
  - functional requirements
  - non-functional requirements
  - business rules
  - acceptance criteria
  - open questions

- `/docs/workflows/`
  - user workflows
  - use cases
  - basic scenario
  - advanced scenario
  - admin scenario
  - public resume viewing scenario

- `/docs/data-modeling/`
  - initial data model
  - entity descriptions
  - relationships and cardinality
  - ERD
  - 3NF explanation
  - data dictionary

- `/docs/ui-ux-analysis/`
  - UI/UX requirements
  - wireframes
  - user scenarios
  - page descriptions
  - UX decisions

- `/docs/system-analysis/`
  - architecture overview
  - API requirements
  - security requirements
  - AI integration requirements
  - PDF generation requirements
  - public URL logic
  - ATS JSON endpoint requirements

- `/docs/risk-management/`
  - risks
  - assumptions
  - constraints
  - open questions
  - mitigation plan

- `/docs/ai-related/`
  - prompt strategy
  - AI integration context
  - OpenRouter context

### 11.3 Java Developer Portfolio Repository

Purpose:
Show the project from the perspective of a Java Developer: architecture, backend implementation, database integration, REST API, MVC flow, Spring Security, AI integration, PDF generation, testing, and deployment readiness.

Planned structure:

- `/README.md`
  - project overview
  - tech stack
  - implemented features
  - setup guide
  - demo scenario
  - screenshots
  - API documentation link
  - database setup guide

- `/src/`
  - application source code

- `/docs/architecture/`
  - backend architecture
  - layered architecture explanation
  - package structure
  - main technical decisions
  - Spring Boot / Spring MVC flow

- `/docs/database/`
  - database schema
  - ERD
  - migration scripts explanation
  - JPA entity overview
  - normalization notes

- `/docs/api/`
  - REST API design, if REST is used
  - endpoint list
  - request and response examples
  - error response structure
  - authentication flow

- `/docs/security/`
  - Spring Security configuration
  - authentication
  - authorization
  - roles and permissions
  - password hashing
  - public routes
  - admin-only routes

- `/docs/ai-integration/`
  - OpenRouter integration design
  - AI service interface
  - prompt builder
  - mock AI provider
  - error handling
  - token usage logging

- `/docs/pdf-generation/`
  - PDF generation approach
  - A4 layout rules
  - selectable text requirement
  - public PDF download flow

- `/docs/testing/`
  - manual test scenarios
  - unit test plan
  - integration test plan
  - API test examples

- `/docs/spec-kit/`
  - feature specifications
  - implementation plans
  - task breakdowns
  - development roadmap

- `/docs/deployment/`
  - local setup
  - environment variables
  - database configuration
  - OpenRouter API key configuration
  - future deployment plan

## 12. Common Rule

Prevent Spec Kit to generate implementation tasks before these decisions are stable:
- MVP scope;
- database model;
- architecture pattern;
- resume storage format;
- public URL behavior;
- AI integration approach.
