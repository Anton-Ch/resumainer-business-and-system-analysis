# Business Goals and KPIs

**Project ID:** `resumainer`
**Product Name:** ResumAIner
**Date Created:** 2026-05-18
**Last Updated:** 2026-05-18
**Author:** Anton
**Version:** 1.0
**Status:** Approved
**Related BABOK Area:** 6.2 Define Future State (SMART Goals)

***

## 1. Description

This document defines the measurable business goals for the ResumAIner project. Each goal follows the **SMART** criteria — Specific, Measurable, Achievable, Relevant, and Time-bound. These goals translate the business need (BR-001) into quantifiable targets that will be used to evaluate project success.

## 2. Goal Overview

| ID     | Goal Title                                                            | Linked Business Need |
| ------ | --------------------------------------------------------------------- | -------------------- |
| BG-001 | Reduce resume adaptation time from manual hours to AI-powered minutes | BR-001               |

## 3. SMART Goal Details

### BG-001: Reduce Resume Adaptation Time

#### Description

Users currently spend 2-3 hours manually adapting each resume using fragmented tools (Word, ChatGPT, email). ResumAIner should reduce this to under 10 minutes by providing structured profile storage and AI-powered vacancy-specific generation, enabling users to apply to more vacancies with professionally adapted resumes.

#### SMART Verification

| Criteria       | Assessment                                                                                                                                               |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **S**pecific   | Reduce the time required to produce a vacancy-adapted resume                                                                                             |
| **M**easurable | Tracked as "time from vacancy input to ready-to-save resume" (minutes)                                                                                   |
| **A**chievable | AI-powered generation with structured profile data can produce results in under 10 minutes; manual review/edit is the remaining user-controlled variable |
| **R**elevant   | Directly addresses the core business need (BR-001) — reducing manual adaptation effort                                                                   |
| **T**ime-bound | Target deadline aligned with Capstone project delivery                                                                                                   |

#### KPIs

| #   | KPI                     | Metric                                       | Baseline (Current)                           | Target (Goal)                      | Deadline   |
| --- | ----------------------- | -------------------------------------------- | -------------------------------------------- | ---------------------------------- | ---------- |
| 1   | Resume adaptation time  | Time to generate an adapted resume (minutes) | 120-180 minutes (manual)                     | <10 minutes                        | 2026-06-31 |
| 2   | Multilingual generation | Languages supported for automated generation | 1-2 (manual translation or separate version) | 2 (Russian and English, automated) | 2026-06-31 |

#### Measurement Approach

| KPI                     | How to Measure                                                                                  | Frequency           |
| ----------------------- | ----------------------------------------------------------------------------------------------- | ------------------- |
| Resume adaptation time  | Track from "Generate Resume" button click to draft preview displayed; exclude user editing time | Per-generation      |
| Multilingual generation | Language options available and functional in the generation flow                                | Verified at release |

## 4. Dependencies and Assumptions

| Dependency / Assumption                                        | Impact on Goal                                                                        |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| AI API (OpenRouter) must be accessible and responsive          | Generation time depends on API response speed; target of <10 min includes API latency |
| User must complete structured profile before generation        | Goal assumes profile data is already entered, first setup time is separate            |
| AI output quality must be sufficient for meaningful adaptation | If AI output requires heavy editing, effective time savings are reduced               |

***

*This document is part of the ResumAIner business analysis portfolio. Goals and KPIs should be reviewed after MVP delivery to validate assumptions and refine targets for future iterations.*
