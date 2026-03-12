# Arterial Impact Report — Claude Code Instructions

## Project Identity

This is the **Arterial.org Impact Report** project — a web-based, scroll-driven annual impact report for Arterial, a 501(c)(3) non-profit media organization dedicated to human creativity. The report covers Arterial and its ecosystem of sub-projects: NOT REAL ART, Underbelly Project, Artbound/PBS, Classic Black, Arthouse, The Good Art, Artsville USA, Arterial Radio, and more.

The project is designed to be **vibe-coded**: built and edited entirely through Claude Code conversations. There is no CMS, no admin UI, no database for content management. Claude Code is the editing interface. Scott Power (Arterial's founder) or Juergen (the developer) describe changes in natural language, and Claude Code implements them directly.

## Tech Stack

```
Framework:          Astro 5.x (static site, scroll-driven single page)
Styling:            Tailwind CSS 4.x
Animation:          GSAP + ScrollTrigger (scroll-triggered reveals, counters, parallax)
                    + Lenis (smooth scroll library, pairs with GSAP)
Image optimization: Astro's built-in <Image> component (build-time optimization)
                    + Sharp (for compressing oversized uploads via script)
Stock images:       Unsplash API (for placeholders when custom assets are unavailable)
Deployment:         Vercel
Build tool:         Claude Code
Knowledge base:     RAG system (see Knowledge Base section below)
```

## Project Structure

```
/arterial-impact-report
├── CLAUDE.md                          # This file — Claude Code instructions
├── README.md                          # Project overview for humans (Scott, collaborators)
├── astro.config.mjs
├── package.json
├── tailwind.config.mjs
├── tsconfig.json
├── .env.local                         # API keys: UNSPLASH_ACCESS_KEY, GOOGLE_AI_API_KEY, etc.
│
├── /docs                              # Source documents, research, and project context
│   ├── /knowledge                     # Research documents, RAG tool analysis
│   ├── /reference                     # Design references (e.g., Art21 impact report PDF)
│   ├── /context                       # Project background and design conversations
│   ├── /arterial                      # Arterial-specific PDFs, pitch decks, web copy
│   └── /arthouse                      # Arthouse project documents
│
├── /content                           # RAG content corpus (all ingestible material)
│   ├── /documents                     # PDFs, DOCX, pitch decks, reports
│   │   ├── arterial/
│   │   ├── arthouse/
│   │   ├── not-real-art/
│   │   └── classic-black/
│   ├── /web                           # Crawled web content (markdown per page)
│   │   ├── arterial-org/
│   │   ├── notrealart-com/
│   │   ├── crewststudio-com/
│   │   ├── artsvilleusa-com/
│   │   └── classicblackmusic-org/
│   ├── /media                         # Image/video/audio descriptions and metadata
│   │   ├── images/
│   │   ├── video/
│   │   └── audio/
│   ├── /feeds                         # RSS feed snapshots
│   ├── /links                         # Sitemaps, URL lists, curated collections
│   ├── crawl-config.json              # FireCrawl URL targets and section mappings
│   └── _section-map.json              # Content-to-report-section index
│
├── /scripts
│   ├── optimize-image.ts              # Sharp-based compression for oversized uploads
│   ├── search-unsplash.ts             # Unsplash API search helper
│   ├── crawl-sites.ts                 # FireCrawl runner (reads crawl-config.json)
│   └── process-docs.ts               # PDF-to-markdown converter for /docs
│
├── /public
│   ├── /images                        # Optimized images organized by section
│   │   ├── /cover
│   │   ├── /programs
│   │   ├── /artists
│   │   ├── /events
│   │   ├── /headshots
│   │   └── /backgrounds
│   └── /logos                         # Arterial, NRA, project logos
│
└── /src
    ├── /pages
    │   └── index.astro                # Single-page report layout
    ├── /layouts
    │   └── BaseLayout.astro           # Root layout, fonts, metadata, GSAP init
    ├── /components
    │   └── /report
    │       ├── CoverSection.astro
    │       ├── MissionSection.astro
    │       ├── FounderLetterSection.astro
    │       ├── MetricsSection.astro
    │       ├── ProgramsSection.astro
    │       ├── NotRealArtSection.astro
    │       ├── ArtistCommunitySection.astro
    │       ├── DistributionSection.astro
    │       ├── LeadershipSection.astro
    │       ├── FinancialSection.astro
    │       ├── SupportersSection.astro
    │       ├── LookingAheadSection.astro
    │       └── /shared
    │           ├── StatCounter.astro      # Animated number counter (GSAP)
    │           ├── SectionWrapper.astro    # Consistent padding, scroll fade-in
    │           ├── PullQuote.astro
    │           ├── ProgramCard.astro
    │           ├── PieChart.astro
    │           └── DonorTierList.astro
    ├── /data
    │   └── /sections                  # Typed data files per section
    │       ├── cover.ts
    │       ├── mission.ts
    │       ├── founders-letter.ts
    │       ├── metrics.ts
    │       ├── programs.ts
    │       ├── not-real-art.ts
    │       ├── artist-community.ts
    │       ├── distribution.ts
    │       ├── leadership.ts
    │       ├── financial.ts
    │       ├── supporters.ts
    │       └── looking-ahead.ts
    ├── /lib
    │   ├── unsplash.ts                # Unsplash search helper
    │   └── image-utils.ts             # Image path helpers
    └── /types
        └── report.ts                  # Shared TypeScript types
```

## Report Sections

The report is a single-page scrolling site with 12 sections rendered in order:

| # | Section | Key Content |
|---|---------|-------------|
| 00 | Cover / Hero | Full-screen hero, Arterial logo, report title, fiscal year |
| 01 | Mission & Tenets | Three tenets (Access, Underrepresentation, Media exposure), vision, five key insights |
| 02 | Founder's Letter | Scott Power's year-in-review narrative |
| 03 | Year at a Glance | Key metrics as large animated counters (2,000+ artists, 6 podcasts, etc.) |
| 04 | Programs & Projects | Card grid: NRA, Underbelly, Artbound/PBS, Classic Black, Arthouse, The Good Art, Artsville USA, Arterial Radio |
| 05 | NOT REAL ART In Depth | Podcast network, grant program, school, exhibitions, artist database, Q+ART, Remote series |
| 06 | Artist Community | Featured artists, First Fridays, open calls, testimonials |
| 07 | Distribution & Partnerships | Random Media, PBS SoCal, Austin PBS, streaming plans |
| 08 | Leadership & Governance | Scott Power, Joshua Wattles bios, Crewest Studio |
| 09 | Financial Summary | 80/20 allocation visualization, revenue/expense charts |
| 10 | Supporters & Donors | Tiered donor recognition |
| 11 | Looking Ahead | Next FY goals, CTAs (donate, submit art, listen, watch, follow) |

## Architecture: Two Concerns

This project has two separable concerns that may live in one repo or be split:

### Concern 1: RAG Knowledge Base (the engine)
A persistent, queryable knowledge base about Arterial's entire business. This is the long-term asset. It ingests web content, documents, media metadata, RSS feeds, and sitemaps. It powers:
- This impact report (and future annual reports)
- Chatbots for Scott to query Arterial's institutional knowledge
- Any future content generation or analysis tools

### Concern 2: Impact Report (the output)
An Astro-based, scroll-driven website that renders the annual report. It consumes content from the RAG knowledge base and presents it visually with animations, charts, and images.

### Design Decision (TBD)
These can be built as:
- **One repo**: RAG setup scripts + report site together (simpler for POC)
- **Two repos**: A RAG management project (possibly with a Next.js admin interface for URL management, Airtable integration, scrape scheduling) + the Astro report site that queries it

For the initial proof of concept, keep them together. If the RAG system grows into a general-purpose tool for Scott's business, split it out.

## Knowledge Base & RAG System

See `/docs/knowledge/google-rag-tools-research.md` for the full technical analysis.

### Content Sources

The RAG corpus includes:
- **Crawled websites**: arterial.org, notrealart.com, school.notrealart.com, classicblackmusic.org, arthouseshow.com, crewststudio.com, artsvilleusa.com, and related domains
- **PDFs and documents**: Pitch decks, press releases, brand guidelines, web copy, crowdfunding frameworks
- **Media metadata**: Image descriptions, video/podcast episode metadata, audio content
- **RSS feeds**: notrealart.com blog feed, other relevant feeds
- **Research data**: Arts economy statistics, media underrepresentation data, public funding trends
- **Sitemaps and URL lists**: Managed via Airtable for curation and tracking

### RAG Options (pick one for POC)

**Option A — Pinecone + Claude Code Plugin (matches the Nate Herk video)**
- Install: `claude plugin install pinecone`
- Managed RAG via Pinecone Assistants (auto chunking, embedding, retrieval, citations)
- Query: `/pinecone:assistant-chat` for cited answers with page numbers
- Sync: `assistant-sync` for incremental document updates
- Free tier: 1 index, 100K vectors

**Option B — Gemini File Search (Google's managed RAG)**
- Fully managed: upload files, get retrieval with citations
- Metadata filtering per query (filter by report section, domain, content type)
- Near-zero cost at this scale (~$0.05 indexing, free storage)
- Limitation: requires Gemini as query LLM (can pass retrieved context to Claude for generation)

**Option C — Gemini Embedding 2 + Custom Vector Store**
- Multimodal: text + images + video + audio in one vector space
- Full control over pipeline but more infrastructure to manage
- Use Pinecone, ChromaDB, Weaviate, or Supabase pgvector as the store

### URL Management via Airtable

An Airtable base tracks which URLs to scrape, their status, and mapping to report sections. An n8n workflow or script reads this table, scrapes pending URLs via FireCrawl, and updates the status. This gives Scott (or Juergen) a visual interface for curating the knowledge base inputs without touching code.

### Content Loading Protocol

When working on a specific report section:

1. Query the RAG system for content relevant to this section
2. If RAG is not yet set up, fall back to loading files from `/content/` tagged for this section in `_section-map.json`
3. After completing a section, use `/compact` before moving to the next
4. Reference the RAG system for any factual claims about Arterial's programs, metrics, or history
5. Flag unverified numbers with `[VERIFY]` and unconfirmed narrative with `[DRAFT — NEEDS SCOTT'S REVIEW]`

## Design System

### Colors
- Primary brand colors: TBD (need from Scott / Arterial brand guidelines)
- Dark backgrounds: `#0a0a0a`, `#1a1a1a`
- Light backgrounds: `#fafafa`, `#ffffff`
- Accent: TBD

### Typography
- Headings: TBD (from brand guidelines)
- Body: TBD
- Stat numbers: `text-6xl md:text-8xl font-bold`
- Pull quotes: `text-2xl italic`

### Layout Rules
- Max content width: `max-w-7xl mx-auto`
- Section padding: `py-20 md:py-32`
- Each section is approximately full-viewport height
- Alternate light and dark background sections
- Images: `rounded-lg` or full-bleed depending on context

### Animation Conventions (GSAP + ScrollTrigger)
- Sections fade in on scroll (ScrollTrigger `whileInView` equivalent)
- Stat counters animate from 0 to target value over 1.5s when scrolled into view
- Parallax backgrounds on hero sections (subtle, `scrub: true`)
- Section pinning only where narratively justified (e.g., metrics section)
- No gratuitous animations — every animation should serve comprehension
- Use Lenis for smooth scroll behavior globally

## Image Handling

### When the user provides a new image:
1. Save to `/public/images/[section-name]/`
2. Run Sharp compression: resize to max 2000px wide, convert to WebP, quality 80
3. Use Astro's `<Image>` component with proper `width`, `height`, and `alt` attributes
4. Script: `npx ts-node scripts/optimize-image.ts [input-path] [output-name]`

### When the user asks for a placeholder image:
1. Search Unsplash: `npx ts-node scripts/search-unsplash.ts "[search terms]"`
2. Download and optimize the chosen image
3. Add comment: `<!-- PLACEHOLDER: Unsplash image, replace with custom asset -->`
4. Include Unsplash attribution as required by their API terms

### Scott's oversized uploads (20MB+):
- ALWAYS run through the optimize-image script before committing
- Never commit raw uploads larger than 500KB to the repo
- The Astro `<Image>` component handles responsive sizing at build time

## Editing Protocol

### Text changes:
- Find the section data file in `/src/data/sections/`
- Make the edit directly
- Do not change surrounding structure or styling unless asked

### Styling changes:
- Modify Tailwind classes only
- Stay within the design system defined above
- If the request conflicts with the design system, note the conflict and ask

### Adding a new section:
- Create a new data file in `/src/data/sections/`
- Create a new component in `/src/components/report/`
- Add it to `index.astro` in the correct position
- Follow existing section patterns for consistency

### Reordering sections:
- Change the import/render order in `/src/pages/index.astro`
- Do not rename files

### Adding a new program or sub-project:
- Add to the programs data file
- If it needs its own detailed section, create a new section following the NOT REAL ART pattern

## Crawl Configuration

The file `/content/crawl-config.json` defines all URLs to be crawled. Target domains include:

- `arterial.org` — full crawl, all pages
- `notrealart.com` — feature pages (exclude blog posts)
- `school.notrealart.com` — course listings
- `classicblackmusic.org` — program pages
- `arthouseshow.com` — if live
- `crewststudio.com` — Crewest Studio (Arterial partner)
- `artsvilleusa.com` — Artsville USA platform

Each crawl target includes a `reportSections` field mapping crawled pages to report sections they're relevant for.

## GitHub Workflow

- Use GitHub Issues to decompose work: one issue per report section
- Each issue lists its content sources, component path, data file, and acceptance criteria
- Claude Code works on one issue at a time to keep context focused
- Commit messages reference issues: `feat: add Programs section (closes #7)`
- PR-based workflow if Scott is also vibe-coding (prevents conflicts)

## Important Notes

- This is Scott's project. He is non-technical but visually oriented. Design integrity must be preserved regardless of what content changes he requests.
- All factual claims about Arterial must be sourced from the knowledge base, not hallucinated.
- The report is designed to be produced annually. Content changes each FY; structure remains stable.
- The RAG knowledge base is a long-term asset — it will power chatbots and other tools beyond this report.
