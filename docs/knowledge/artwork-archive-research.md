# Artwork Archive Rolling Submissions System — Research Report

**Research Date:** 2026-03-14
**Source:** GitHub repository [JuergenB/artwork-archive](https://github.com/JuergenB/artwork-archive)
**Purpose:** Document the AI-powered submission infrastructure supporting NOT REAL ART exhibitions

---

## 1. What It Is

The **Artwork Archive Rolling Submissions System** is an automated pipeline that processes artwork submissions for NOT REAL ART exhibitions and other Arterial programs. It handles the full journey from artist submission to AI-enriched, archive-ready records.

This is a **no-code project** — all logic lives in n8n workflow nodes backed by Airtable, with no application code.

**Created:** March 10, 2026 | **Last pushed:** March 13, 2026
**Activity:** 15 commits and 71 issues in 4 days — extremely active development.

---

## 2. How It Relates to First Friday and NOT REAL ART

This is the **operational backbone** for NOT REAL ART's open-call exhibition program, including the First Friday series. The system:

1. **Accepts artist submissions** via Paperform embedded on exhibition websites (each exhibition = a "Campaign")
2. **AI-enriches every submission** — Perplexity researches each artist, GPT-4o classifies artwork images, GPT-4.1 generates structured artist profiles
3. **Generates exhibition relevance hypotheses** — AI assesses how each artwork connects to the exhibition's curatorial theme
4. **Exports to Artwork Archive** (planned Phase C) — produces CSV files compatible with the Artwork Archive exhibition platform for launching online exhibitions

The "Campaign" abstraction makes it multi-exhibition: each First Friday show, grant cycle, or partner exhibition is a separate campaign with its own notification templates, CRM tags, and curatorial context.

---

## 3. Tech Stack

| Layer | Technology |
|-------|-----------|
| Workflow automation | n8n Cloud (3 workflows) |
| Database | Airtable (7 tables) |
| Submission forms | Paperform (webhook integration) |
| CRM | ActiveCampaign |
| Email | Gmail (OAuth2) |
| AI — Artist research | Perplexity `sonar-deep-research` |
| AI — Citation validation | GPT-4o-mini |
| AI — Profile formatting | GPT-4.1 (JSON Schema strict mode) |
| AI — Image classification | GPT-4o Vision |
| AI — Relevance scoring | GPT-4o-mini |
| AI — Email generation | GPT-4o |

No application servers, no compiled code, no build step.

---

## 4. Key Features

### Intake Pipeline (V1.4)
- Webhook receives Paperform submissions
- Normalizes data, upserts Campaign/Artist/Artwork records in Airtable
- Sends branded admin notification emails
- Syncs contacts to ActiveCampaign CRM

### AI Enrichment Pipeline (V0.9)
- Artist research via Perplexity with identity anchors and disambiguation
- AI citation validation (filters wrong-person links)
- Bio quality evaluation (flags profiles needing human review)
- Structured artist profile generation (GPT-4.1 with JSON Schema strict mode)
- Artwork image classification (GPT-4o Vision with anti-hallucination architecture)
- Exhibition relevance hypothesis generation

### Pipeline Operations Hub
- Real-time progress tracking via Pipeline Actions and Pipeline Runs tables

### Partner Organizations (In Progress)
- New system for gallery/organization partnerships bringing curated artist groups into NRA exhibitions

### Quality Controls
- Gibberish detection
- Data quality scoring
- Identity anchor extraction
- Anti-hallucination prompting for vision models

---

## 5. Database / Data Model

7 Airtable tables in the `AA Rolling Submissions` base:

| Table | Fields | Purpose |
|-------|--------|---------|
| **Artists** | 32 | Artist profiles, AI-enriched bios, social links, status tracking |
| **Artworks** | 30 | Artwork details, AI-classified medium/tags/subject, relevance hypothesis |
| **Campaigns** | 13 | Exhibition definitions, email templates, CRM config, embed codes |
| **Partner Organizations** | ~20 | Gallery/org profiles, curator details, exhibition preferences |
| **Pipeline Actions** | ~6 | Real-time enrichment progress dashboard |
| **Pipeline Runs** | ~8 | Enrichment run history and metrics |
| **Import Log** | 10 | Submission import tracking |

**Status flow:** `Pending - Imported` → `Pending - Enriched` → `Exported` (with `Needs Review`, `On Hold`, `Error` branches)

---

## 6. Current State and Roadmap

| Phase | Status |
|-------|--------|
| A: Foundation (Intake + Enrichment) | ✅ Complete |
| B: Operations Hub (progress tracking) | ✅ Complete |
| C: Export Pipeline (Airtable → Artwork Archive CSV) | Planned — blocked on field mapping |
| D: Future Improvements (Slack, analytics, model eval) | Backlog |
| E: Partner Organizations | In progress |

22 open issues remain, covering export pipeline, partner onboarding, duplicate detection, social media discovery, and model evaluation.

---

## 7. Impact Report Relevance

This system should be featured in multiple report sections:

- **NOT REAL ART In Depth (Section 06):** Technology infrastructure powering NRA's open-call exhibition program. Demonstrates how Arterial uses AI to scale art curation.
- **Programs & Projects (Section 04):** Part of NRA's tech stack enabling First Friday and other exhibitions at scale.
- **Artist Community (Section 07):** Every submitting artist gets a researched profile, validated citations, and classified artwork images.
- **Looking Ahead (Section 12):** Phase C (online exhibitions), Phase E (partner organizations), and analytics dashboard as next-FY goals.
- **Metrics (Section 03):** Submission counts, artists enriched, artworks classified — all quantifiable impact metrics.

**Key narrative:** Arterial built an AI-powered submission pipeline that transforms raw artist submissions into curated, archive-ready records — replacing manual curation work with automated research, image analysis, and quality controls, allowing a small nonprofit to operate at the scale of a much larger institution.
