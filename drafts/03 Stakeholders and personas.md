# Stakeholders and Personas

## 1. Stakeholders

### 1.1 Registered User

A person who creates a profile, enters career information, generates adapted resumes, edits results, saves versions, downloads PDFs, and shares public links.

### 1.2 Recruiter / External Viewer

A person who opens a public resume link and views or downloads the resume. This user does not need to register.

### 1.3 Administrator

A user with elevated permissions who can view registered users, inspect created resumes, tokens usage statistics and deactivate users in case of abuse.

### 1.4 System Owner

The person responsible for operating and improving the platform. In the Capstone context, this is also the student developer.

### 1.5 AI Provider

An external AI service connected through OpenRouter. It receives prompts and returns generated resume content or translations.

### 1.6 Future Payment Provider

A future external service for subscription or pay-per-generation monetization. Not included in MVP implementation.

## 2. Primary Persona: Career Changer

### Name

Alex

### Background

Alex has several years of previous work experience and is transitioning into IT. He has transferable skills but struggles to present them properly for different IT roles.

### Goals

- Create a clear professional profile.
- Adapt resume for different junior or trainee roles.
- Emphasize transferable experience.
- Generate English and Russian resume versions.
- Save different resume versions for future use.

### Pain Points

- Hard to decide what information is relevant.
- Time-consuming to rewrite resumes manually.
- Difficult to phrase achievements professionally.
- Uncertainty about how to position career transition.
- Issues with propper wordings to pass ATS systems scorring of recruiters.
- Effortful task to prepare two versions of the resume in two different languages keeping the info consistant in both versions.

### Key Scenario

Alex applies for a Junior Java Developer role. He pastes the vacancy description, selects balanced adaptation, chooses English output, reviews the generated resume, edits several fields, saves it, downloads PDF, and shares a public links. Distinguished link for each language version of generated resume.

## 3. Secondary Persona: Experienced IT Specialist

### Name

Maria

### Background

Maria is a business analyst with several years of experience. She applies to different BA, system analyst, and product owner, project manager roles.

### Goals

- Keep several resume versions.
- Adapt professional summary and skills for different roles.
- Use existing resume versions as context for future generations.
- Quickly download print-ready PDF files.

### Pain Points

- Too many resume variants stored in different files.
- Hard to track which version was used for which vacancy.
- Needs both Russian and English versions.

## 4. External Viewer Persona: Recruiter

### Name

Daniel

### Background

Daniel is a recruiter who receives a public resume link from a candidate.

### Goals

- Quickly open the resume.
- Read it without registration.
- Download or save it.
- Copy text if needed.
- Use the resume in internal recruitment tools like ATS.

### Pain Points

- Broken links.
- Non-selectable text inside scanned PDFs.
- Too much irrelevant information.
- Poor formatting.

## 5. Admin Persona

### Name

System Admin

### Background

Admin supports the platform and monitors users.

### Goals

- View all registered users.
- View user profiles and generated resumes.
- Deactivate users who abuse AI generation.
- Keep user data manageable.
- Monitors token usage total and per user.

### Pain Points

- AI API abuse may create costs.
- Users may generate too many resumes.
- Need simple controls without complex admin workflows.

## 6. Stakeholder Prioritization

| Stakeholder                 | Priority | Reason                                  |
| --------------------------- | -------: | --------------------------------------- |
| Registered User             |     High | Main user and source of product value   |
| Recruiter / External Viewer |     High | Public resume sharing must be useful    |
| Administrator               |   Medium | Needed for control and abuse prevention |
| System Owner                |   Medium | Important for maintainability           |
| AI Provider                 |     High | External dependency, core of the flow   |
| Future Payment Provider     |      Low | Future scope, not MVP                   |
