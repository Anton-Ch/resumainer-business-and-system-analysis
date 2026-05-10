# AI context

## 1. Purpose of AI Integration

The application uses AI to generate adapted resume versions based on:
- structured user profile data;
- target vacancy description;
- optional company information;
- selected resume language;
- selected adaptation level;
- selected AI model.

AI is not the system of record. The database remains the source of truth for user profile data, resume generation requests, generated drafts, saved resumes, and public resume versions.

## 2. AI Integration Principle

AI integration should be isolated from the core application logic.

The application should not directly call OpenRouter from controllers. Instead, AI calls should be handled through a dedicated service layer.

Suggested structure:
- Controller receives user request.
- Service validates input and builds resume generation request.
- PromptBuilder prepares structured prompt.
- AiGenerationService sends the request to the selected provider.
- AiResponseParser parses AI output.
- ResumeDraftService saves generated draft.
- User reviews and edits draft.
- SavedResumeService saves final resume version.

## 3. OpenRouter Role

OpenRouter is used as the first AI gateway because it allows access to multiple models through one API-compatible integration.

MVP assumption:
- The system owner configures OpenRouter API access.
- Users select from a predefined list of active models stored in the database.
- Users do not provide their own API keys in the MVP.

Post-MVP assumption:
- Users may configure their own OpenRouter API key.
- Users may configure direct provider keys for OpenAI, Anthropic, DeepSeek, Grok, or other providers.
- User-provided keys should be encrypted and never displayed back in full after saving.

## 4. AI Model Selection

The user should be able to select an AI model from a dropdown list.

The model list should be stored in the database through the AiModel entity.

Suggested AiModel fields:
- id
- provider
- model_code
- display_name
- is_free
- is_active
- max_context_tokens
- notes
- created_at
- updated_at

Example model selection options:
- system default free model;
- system default balanced model;
- system default high-quality model.

The exact model list should remain configurable and should not be hardcoded in business logic.

## 5. Prompt Types

The application should distinguish several prompt layers.

### 5.1 System Prompt

Defines the AI role and global rules.

Example responsibility:
- act as professional resume writer;
- preserve factual accuracy;
- do not invent experience;
- adapt wording to the target vacancy;
- return structured output;
- keep resume concise and recruiter-friendly.

### 5.2 Request Prompt

Defines the specific generation task.

Example responsibility:
- generate resume for a given vacancy;
- use selected language;
- use selected adaptation level;
- use provided user profile data;
- use provided vacancy description;
- use company information if available.

### 5.3 User Custom Prompt

Post-MVP optional feature.

The user may add a custom instruction with lower priority than the system prompt and main request prompt.

Example:
- “Make the tone more formal.”
- “Emphasize business analysis experience.”
- “Do not include hobbies.”

## 6. Resume Adaptation Levels

### 6.1 Minimal Adaptation

Purpose:
Create a conservative resume version close to the user's original profile.

Expected behavior:
- Light rewording.
- No major restructuring.
- Emphasis on relevant skills.
- Low risk of over-adaptation.

### 6.2 Balanced Adaptation

Purpose:
Create a resume that is clearly adapted to the vacancy while preserving natural and factual presentation.

Expected behavior:
- Reorder sections if useful.
- Emphasize matching experience.
- Adapt summary, skills, and achievements.
- Keep content realistic.

### 6.3 Maximum Adaptation

Purpose:
Create a highly targeted resume version for the vacancy.

Expected behavior:
- Strong focus on vacancy requirements.
- More aggressive prioritization of relevant experience.
- Less relevant information may be shortened or omitted.
- Can invent facts a little bit to sound realistic without being too much lie.

## 7. Language Generation

The system should support:
- English resume generation;
- Russian resume generation;
- English and Russian resume generation.

For the MVP, multilingual generation may be handled directly by AI during resume generation.

Future versions may store localized user profile content separately.

Important rule:
The English and Russian versions of the same resume should be consistent in meaning, even if phrasing is adapted naturally for each language.

## 8. ATS-Oriented Output

The application should support an ATS-oriented representation of saved resume data.

MVP feature:
- Permanent public JSON endpoint:
  `/{username}/{resumeCode}/json`

Purpose:
- Provide a machine-readable resume version.
- Reduce parsing issues caused by PDF formatting.
- Allow recruiters or automated tools to access structured resume data.

The PDF should include a short note that an ATS-friendly JSON version is available at the public JSON URL.

Post-MVP:
Add other output formats like:
- Permanent public JSON endpoint:
  `/{username}/{resumeCode}/md`
- `/{username}/{resumeCode}/txt`
- `/{username}/{resumeCode}/xml`
and other possible if needed. MVP should be designed from start for such expansions in the future.  

## 9. AI Output Format

For easier parsing, AI should return structured content.

Suggested output structure:
- candidate_name
- target_title
- professional_summary
- skills
- work_experience
- education
- courses_certificates
- projects
- achievements
- languages
- personal_information
- professional_aspirations
- cover_letter (if requested and was checked by user at request stage)

The AI output should be validated before saving.

## 10. Cover Letter Generation

If the user selects the cover letter option, the system should generate a cover letter for the same vacancy.

Cover letter should be connected to the same ResumeGenerationRequest.

Suggested behavior:
- Cover letter generation is optional.
- Cover letter should use the same profile, company and vacancy context.
- Cover letter should be editable before final saving.
- Cover letter should not be required for saving a resume.

## 11. AI Usage Statistics

The system should store AI usage statistics for admin review and future monetization.

Suggested tracked fields:
- user_id
- ai_model_id
- resume_generation_request_id
- prompt_tokens
- completion_tokens
- total_tokens
- request_status
- error_message
- created_at
- completed_at

Possible entity:
- AiUsageLog

Admin should be able to view:
- total resumes generated by user;
- tokens in;
- tokens out;
- total tokens;
- model used;
- generation status;
- generation date.

## 12. Error Handling

The system should handle:
- AI provider unavailable;
- invalid API key;
- model not available and automatic fallback till system finds available and working AI model out of predefined list;
- rate limit exceeded;
- malformed AI response;
- empty AI response;
- timeout;
- inactive user;
- user without generation permission.

User-facing errors should be understandable and not expose internal API details.

Example:
“Resume generation failed because the AI provider is currently unavailable. Please try again later or select another model.”

## 13. Security Considerations

The system should not expose:
- system prompt;
- API keys;
- raw provider error details;
- prompt injections via profile data passed to AI;
- private profile data outside saved public resume versions.

If user-provided API keys are added in future versions:
- keys must be encrypted at rest;
- keys must not be logged;
- keys must not be returned to frontend after saving;
- users should be able to delete or replace keys.

## 14. MVP AI Scope

MVP should include:
- predefined OpenRouter model list;
- AI resume generation;
- adaptation level support;
- language selection;
- optional cover letter generation if implementation time allows;
- AI usage logging;
- admin visibility of usage statistics.

MVP should not include:
- user-provided API keys;
- direct integrations with many AI providers;
- advanced prompt marketplace;
- full AI memory from previous resume versions;
- AI scoring of resume quality;
- AI ATS score prediction.

## 15. Future AI Extensions

Future versions may include:
- user-owned OpenRouter key;
- direct provider key configuration;
- resume quality scoring;
- ATS keyword matching;
- AI suggestions for missing profile data;
- reuse of previous resume versions as context;
- custom user prompt;
- model fallback;
- generation cost estimation;
- subscription-based usage limits.