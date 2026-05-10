# Scope and MVP

## 1. Product Scope

The application helps users store structured career data and generate adapted resume versions for specific vacancies using AI in double languages.

## 2. MVP Scope

The MVP should include only the functionality required to demonstrate the full end-to-end resume generation workflow with dual language versions.

## 3. MVP Features

### MVP-001: User registration and login

Users can register, log in, and log out.

### MVP-002: User profile management

Users can create and update structured profile information.

Profile sections:
- Photo
- Contact details
- Skills
- Values (optional)
- Achievements (optional)
- Courses and certificates (optional)
- Hobbies (optional)
- Personal information
- Positioning
- Professional summary (optional)
- Work experience
- Education
- Volunteering and projects (optional)
- Professional aspirations
- Languages

### MVP-003: AI model selection

Users can choose an AI model from a predefined dropdown list of free models from OpenRouter.

Post MVP:
Users can choose an AI model from own preferences and own OpenRouter key.
Users can choose an AI model from main suppliers (OpenAI, Anthropic, DeepSeek), providing own API keys and specifying model name.

### MVP-004: Vacancy input

Users can paste a job description and company information into a text field for saving in DB and using by AI for adoptation later. Company + Vacancy data should be stored in db to show user input for adoptation when resume created.

### MVP-005: Adaptation level selection

Users can choose one of the following options before AI generates:
- Minimal adaptation
- Balanced adaptation
- Maximum adaptation
- Generate all three variants for user to select final version

### MVP-006: Resume language selection

Users can choose:
- English
- Russian
- English and Russian

### MVP-007: Resume generation

The system generates resume content based on:
- User profile data.
- Vacancy description.
- Selected AI model.
- Selected adaptation level.
- Selected language.

### MVP-008: Generated resume review and editing

Users can edit generated resume fields before final saving.

### MVP-009: Resume version saving

Users can save final resume versions in the system.

### MVP-010: Resume history

Users can view and edit all generated resumes, open details, and soft delete resume versions.

### MVP-011: Public resume link

Each saved resume version has a permanent public URL.

Example pattern:
`/{username}/{resumeCode}`

The resume code is a 4-letter code generated from the allowed alphabet:
`QWRYUPASEDFGHJKZXCVBNM`

The code must not contain repeated letters.

### MVP-012: PDF download

Users and external viewers can download a saved resume as a print-friendly A4 PDF.

The PDF must contain selectable text, not a scanned image.

### MVP-013: Admin panel

Admin can:
- View all registered users.
- Open user profiles.
- View generated resumes with in + out + total tokens spent + model info.
- Set user status to inactive.

### MVP-014: Cover letter
If checked user can get ai generated cover letter for given vacancy.

### MVP-015: ATS tailored json page
This permanent url: `/{username}/{resumeCode}/json`
Should return pure json adopted for best parsing by AI ATS systems to avoid any parsing issues from PDF. Link to this json should be added to pdf as note where to find ATS first format in json `/{username}/{resumeCode}/json`



## 4. Out of Scope for MVP

The following features should be designed for future easy extension but not implemented in the first version:
- Payment system.
- Subscription plans.
- Pay-per-generation billing.
- Advanced AI usage limits.
- Resume analytics.
- Recruiter accounts.
- Team accounts.
- Full ATS optimization scoring.
- Complex template designer.
- Deep AI memory based on all previous resumes.
- Full audit trail for every field edit.
- Advanced i18n for all interface elements if time is limited. If further implementation of i18n for selecting language will cause more pain - include it at MVP
- Allow user to select with check box previously generated resumes as references for AI
- Add a section for custom user prompt for AI with lower priority than system prompt and general request prompt

## 5. Future Scope

Future versions may include:
- Monthly subscription.
- Paid generation packages.
- Usage limits by user plan.
- Resume templates.
- AI-powered translation for each profile section.
- AI suggestions for missing profile data.
- Context reuse from previously generated resumes.
- Recruiter view analytics.
- Multiple public resume themes.
- Export to DOCX.
- LinkedIn profile import.

## 6. MVP Principle

The MVP should prove the full value chain:

Profile data → vacancy input → AI adaptation → editable resume → saved version → public link → PDF download.
