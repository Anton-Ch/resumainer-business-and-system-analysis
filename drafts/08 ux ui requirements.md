# UI/UX Requirements

## 1. UI Design Goal

The interface should help users create and maintain a structured professional profile, generate adapted resumes, review the result, and download or share final versions with minimal confusion.

The UI should be simple, consistent, and suitable for a Capstone demonstration.

## 2. Main Navigation

Suggested navigation for logged-in users:
- Dashboard
- My Profile
- Generate Resume
- Resume History
- Settings
- Admin Panel only for ADMIN users
- Logout

## 3. Key Pages

### 3.1 Landing Page

This is the only one page which should be done in Thymeleafe. All other should be in Vue rest app

Purpose:
- Explain what the application does.
- Provide link to Vue app.

Main elements:
- Product name.
- Short value proposition.
- Login button.
- Register button.
- Simple explanation of workflow.

### 3.2 Login Page

Main elements:
- Email field.
- Password field.
- Login button.
- Link to registration page.
- oAuath2 login via Google

### 3.3 Registration Page

Main elements:
- Username field.
- Email field.
- Password field.
- Confirm password field.
- Register button.
- oAuath2 register via Google
### 3.4 Dashboard

Purpose:
Show user progress and quick actions.

Main elements:
- Profile completion summary.
- Button: Edit Profile.
- Button: Generate New Resume.
- Recent saved resumes.
- Recent generation status.

### 3.5 My Profile Page

Purpose:
Allow user to manage structured profile data.

Suggested layout:
- Sidebar or tab list of profile sections.
- Main panel with selected section editor.
- Save button.
- Primary language field.
- Secondary language field.

Profile sections:
- Photo
- Contact details
- Skills
- Values
- Achievements
- Courses and certificates
- Hobbies
- Personal information
- Positioning
- Work experience
- Education
- Volunteering and projects
- Professional aspirations
- Languages

### 3.6 Generate Resume Page

Purpose:
Collect vacancy context and generation settings.

Main elements:
- AI model dropdown.
- Vacancy description textarea.
- Company information textarea.
- Adaptation level selector.
- Language selector.
- Generate Resume button.

Adaptation options:
- Minimal adaptation
- Balanced adaptation
- Maximum adaptation
- Generate all three variants

Language options:
- English
- Russian
- English and Russian

### 3.7 Resume Review Page

Purpose:
Allow user to review generated content before saving.

Main elements:
- Generated resume preview.
- Editable fields.
- Adaptation version tabs if several versions were generated with checkbox for selecting for final saving.
- Language tabs if several languages were generated.
- Save Final Version button.
- Cancel button.

### 3.8 Resume History Page

Purpose:
Allow user to manage saved resume versions.

Main elements:
- Table or card list of saved resumes.
- Resume title.
- Language.
- Adaptation level.
- Created date.
- Public link.
- Open details button.
- Download PDF button.
- Soft delete button.

### 3.9 Public Resume Page

Purpose:
Allow external viewers to view a saved resume.

Main elements:
- Resume preview or embedded PDF.
- Download PDF button.
- Candidate name and positioning.
- No private dashboard navigation.

### 3.10 Admin Panel

Purpose:
Allow admin to manage users and review generated resumes.

Main elements:
- User list with statistics.
- User status.
- Open user profile button.
- Open user resumes button.
- Set inactive button.

## 4. Basic UI Scenario

1. User logs in.
2. User opens My Profile.
3. User fills in required sections.
4. User opens Generate Resume.
5. User pastes vacancy description and company info.
6. User selects AI model, adaptation level, and language.
7. User generates resume.
8. User reviews and edits result.
9. User saves final version.
10. User downloads PDF and copy sharable permanent link.

## 5. Advanced UI Scenario

1. User selects Generate all three variants.
2. System displays minimal, balanced, and maximum adaptation versions.
3. User compares versions through tabs or cards.
4. User selects one version.
5. User edits final content.
6. User saves English and Russian versions separately.
7. System generates separate public links.

## 6. UI Principles

- Use clear labels.
- Avoid unnecessary form fields.
- Use cards for profile sections.
- Use tabs for language and adaptation versions.
- Use confirmation dialogs for delete/deactivate actions.
- Use consistent buttons and colors.
- Keep the first version minimalistic and readable.
- Use Bootstrap if server-rendered templates are used only for landing page with Thymeleafe.
- Use responsive layout for desktop-first but mobile-friendly display.

## 7. Suggested Wireframe List

The project should include schematic wireframes for:
- Landing page
- Login page
- Register page
- Dashboard
- My Profile page
- Generate Resume page
- Resume Review page
- Resume History page
- Public Resume page
- Admin Panel
