# User Workflows

## 1. Basic Scenario: Generate One Resume Version

### Actor

Registered User

### Goal

Generate one adapted resume version for a target (provided description) vacancy.

### Preconditions

- User is registered.
- User is logged in.
- User has filled in at least the required profile sections.

### Main Flow

1. User opens the dashboard.
2. User goes to the profile section.
3. User fills in or updates professional profile data.
4. User opens the resume generation page.
5. User selects an AI model from the dropdown.
6. User pastes the target vacancy description.
7. User pastes optional company information.
8. User selects adaptation level: Balanced adaptation.
9. User selects resume language: English.
10. User clicks Generate Resume.
11. System sends structured prompt to the AI provider.
12. System receives generated resume content.
13. System displays generated resume preview.
14. User edits generated fields if needed.
15. User clicks Save Final Version.
16. System saves resume version.
17. System generates a public URL.
18. User downloads the resume as PDF.

### Postconditions

- Resume version is saved.
- PDF can be downloaded.
- Public link can be opened by external viewers.

## 2. Advanced Scenario: Generate Three Adaptation Versions

### Actor

Registered User

### Goal

Generate minimal, balanced, and maximum adaptation versions in both languages and choose the best one.

### Preconditions

- User is registered.
- User is logged in.
- User profile contains enough structured data.
- User has a target job description.

### Main Flow

1. User opens the resume generation page.
2. User selects AI model.
3. User pastes job description and company information.
4. User selects adaptation option: Generate all three variants.
5. User selects language: English and Russian.
6. User clicks Generate Resume.
7. System generates:
   - Minimal adaptation version.
   - Balanced adaptation version.
   - Maximum adaptation version.
8. System displays the three generated variants in both languages.
9. User compares versions.
10. User selects one preferred version.
11. User edits generated fields.
12. User saves final English version.
13. User saves final Russian version.
14. System creates separate public links for each language version.
15. User downloads PDFs.

### Postconditions

- Selected resume versions are saved.
- Each saved language version has its own public link.
- PDFs are available for download.

## 3. Public Resume Viewing Scenario

### Actor

Recruiter / External Viewer

### Goal

Open and view a candidate resume through a public link.

### Preconditions

- Resume version exists.
- Resume version is not soft deleted.
- Resume public link is active.

### Main Flow

1. External viewer opens a public URL.
2. System validates username and resume code.
3. System opens the saved resume PDF or public resume page.
4. External viewer reads the resume.
5. External viewer downloads PDF if needed.
6. External viewer can select and copy text from the PDF.

### Postconditions

- Resume is viewed without registration.
- Resume text remains selectable.

## 4. Admin Abuse Control Scenario

### Actor

Admin

### Goal

Deactivate a user who abuses AI generation.

### Preconditions

- Admin is logged in.
- User exists in the system.

### Main Flow

1. Admin opens the admin panel.
2. Admin opens the list of users.
3. Admin searches or selects a user.
4. Admin opens user details.
5. Admin reviews user profile and generated resumes.
6. Admin changes user status to inactive.
7. System prevents inactive user from logging in returning explaining message or generating new resumes.

### Postconditions

- User status is inactive.
- User cannot use AI generation.
