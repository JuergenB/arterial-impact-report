# Arterial Impact Report / Arterial Knowledge Base

This project has two goals:

1. **Arterial Impact Report** — The first and most important deliverable. A visually rich, scroll-driven annual impact report for [Arterial.org](https://arterial.org), a 501(c)(3) non-profit media organization dedicated to human creativity. Similar to what organizations like Art21 produce as annual PDFs, but as a fast, interactive, mobile-friendly website.

2. **Arterial Knowledge Base (RAG)** — A persistent, AI-queryable knowledge base covering Arterial's entire business. "RAG" stands for *Retrieval-Augmented Generation* — a technique where AI doesn't rely on its own memory alone but retrieves real facts from a curated library of your documents, websites, and data before generating any answer. Think of it as giving AI a research assistant that reads everything Arterial has ever published, so every answer is grounded in real information rather than guesswork. This knowledge base can be used to instantiate different projects — the impact report is the first, but future annual reports, chatbots, content generation tools, and other deliverables will draw from the same knowledge base.

> **Note:** These two concerns may eventually be split into separate repositories — the knowledge base as shared infrastructure and the impact report as one of its consumers. For now they live together as a single proposal.

## What It Covers

The report and knowledge base span Arterial's full ecosystem:

**Flagship initiatives (this year's top priorities):**
- **Arthouse** — Unscripted TV series ("House Hunters for art"), showrunner Stacy Schneider (300+ HGTV episodes), Chicago pilot filmed, $150K Indiegogo campaign, Fractured Atlas partnership, targeting Netflix/Hulu/Apple TV
- **NOT REAL ART** — 200-episode podcast network (4.9★), $12K/yr grant program (co-founded with Channing Dungey, 36 recipients), NRA School, 30+ First Friday online exhibitions, 175+ Q+ART artist profiles, Remote video series, AI-powered artwork submission pipeline

**Major active programs:**
- **First Friday & Artwork Archive** — Monthly curated online exhibitions (30+ since 2023), powered by AI submission pipeline (n8n + Airtable + GPT-4o/Perplexity), open calls via ArtCall.org
- **Artsville USA** — Asheville/WNC arts platform (Arterial subsidiary). "Tale of Two Cities" exhibition at NOAFA with 40+ artists, hurricane recovery narrative. Louise Glickman Grant & Residency ($10K, launching 2026)
- **Classic Black** — Classical music program with Steinway Artist Ric'key Pageot (Madonna's touring pianist, youngest Cirque du Soleil music director). Sold-out concerts, documentary in development

**Distribution & partnerships:**
- **Artbound / PBS** — Multi-Emmy Award-winning PBS SoCal series (7 Emmys 2024–2025, Season 15). Arterial is financial sponsor
- **The Underbelly Project** — Documentary about secret 2009–2010 subway art installation (100+ street artists). $12K Arterial grant, premiered Miami Art Week Dec 2024
- **Random Media** — LA-based indie distributor, Arterial's path to streaming platforms

**In development:**
- **The Good Art** — Lowbrow/Pop Surrealism art movement documentary
- **Arterial Radio** — Internet-based arts talk radio channel
- **Ready To Roll** — Documentary about concert roadies (Crewest Studio)

**Infrastructure:**
- **Crewest Studio** — Co-founded by Scott Power and Man One (Alex Poli). Production company; predecessor Crewest Gallery (2002–2012) was the first LA gallery to legitimize graffiti as contemporary art (100+ exhibitions, 2,000+ artists, 20+ countries)

## How It Works

This project is **vibe-coded** — built and edited through conversations with [Claude Code](https://claude.ai/claude-code). There is no traditional CMS or admin panel. To make changes:

1. Open Claude Code in this repository
2. Describe what you want to change in plain English
3. Claude Code makes the edit, optimizes images if needed, and commits
4. Vercel auto-deploys the updated site

**Examples of what you can say:**
- "Change the Underbelly Project description to say it premiered on December 1, 2024"
- "Replace the hero image on the Programs section with this photo" *(drag image into chat)*
- "Add a new section about Arterial Radio between Programs and Artist Community"
- "Make the financial section darker with white text"
- "Find me a background image of a concert hall for the Classic Black section"

## Knowledge Base (RAG)

Behind the report is a **RAG (Retrieval-Augmented Generation) knowledge base** — a searchable, AI-queryable repository of everything related to Arterial and its ecosystem. This approach was inspired by [this video on Google's Gemini Embedding 2 + Claude Code for RAG](https://www.youtube.com/watch?v=hem5D1uvy-w).

**Content sources:**
- **Websites**: arterial.org, notrealart.com, school.notrealart.com, classicblackmusic.org, crewststudio.com, artsvilleusa.com, arthouseshow.com, and related domains
- **Documents**: PDFs, pitch decks, press releases, brand guidelines, web copy
- **Media**: Images, video descriptions, podcast metadata
- **Research**: Arts economy statistics, media representation data, public funding trends
- **URLs & feeds**: Managed via Airtable — curated lists of pages to scrape, RSS feeds, sitemaps

**The knowledge base serves multiple purposes:**
1. **Report generation**: Grounding every section of the impact report in real Arterial data
2. **Chatbot / Q&A**: Scott can query his entire business knowledge conversationally
3. **Future reports**: The same corpus powers next year's report with updated data
4. **Content discovery**: Finding connections across Arterial's sprawling ecosystem of projects

**RAG architecture options** (see `docs/knowledge/google-rag-tools-research.md` for full analysis):
- **Pinecone + Claude Code plugin**: Vector database with managed RAG assistants, cited answers with page numbers. Install: `claude plugin install pinecone`
- **Gemini File Search**: Google's fully managed RAG — automatic chunking, embedding, retrieval. Near-zero cost at this scale.
- **Gemini Embedding 2**: Multimodal embeddings (text + images + video + audio in one vector space) for custom pipelines

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Build tool | [Claude Code](https://claude.ai/claude-code) |
| Code editor | [Cursor](https://cursor.com) (VS Code fork with AI integration) |
| Live preview | Go Live extension (hot-reload in Cursor) |
| Framework | [Astro](https://astro.build) 5.x |
| Styling | [Tailwind CSS](https://tailwindcss.com) 4.x |
| Animation | [GSAP](https://gsap.com) + ScrollTrigger + [Lenis](https://lenis.darkroom.engineering/) |
| Images | Astro `<Image>` (build-time optimization) + Sharp |
| Image generation | [Replicate](https://replicate.com) (Flux, SDXL, Ideogram, and more) |
| Deployment | [Vercel](https://vercel.com) |
| Vector database | [Pinecone](https://pinecone.io) (RAG vector store, free tier) |
| Embeddings & retrieval | [Gemini](https://ai.google.dev) File Search (managed RAG) + Gemini Embedding 2 |
| Content scraping | [FireCrawl](https://firecrawl.dev) |
| File sharing & assets | [Dropbox](https://dropbox.com) (shared asset storage between Scott and dev) |
| Auto-ingest pipeline | Dropbox folder watch → auto-scrape and index into RAG (planned) |

### Image Generation Models (via Replicate)

Replicate provides access to multiple image generation models, each with different strengths. Use this table to choose the right model for the task:

| Model | Best For | Text Rendering | Characters | Backgrounds | Conceptual | Speed |
|-------|----------|:-:|:-:|:-:|:-:|-------|
| **Flux Schnell** (`black-forest-labs/flux-schnell`) | Fast iteration, drafts | Fair | Good | Good | Good | ~3s |
| **Flux Dev** (`black-forest-labs/flux-dev`) | High-quality hero images | Fair | Very Good | Very Good | Very Good | ~15s |
| **Flux Pro** (`black-forest-labs/flux-1.1-pro`) | Production-quality output | Good | Excellent | Excellent | Excellent | ~20s |
| **Ideogram v2** (`ideogram-ai/ideogram-v2`) | Text-heavy graphics, logos | Excellent | Good | Good | Good | ~15s |
| **SDXL** (`stability-ai/sdxl`) | Stylized art, illustrations | Poor | Good | Excellent | Good | ~10s |
| **Recraft v3** (`recraft-ai/recraft-v3`) | Design assets, icons, text | Excellent | Fair | Good | Fair | ~10s |
| **Google Imagen 3** (when available) | Photorealism, text in scenes | Very Good | Excellent | Very Good | Very Good | ~12s |

**Quick guide by task:**
- **Section hero backgrounds** → Flux Dev or Flux Pro (photorealistic, high-res)
- **Text overlays / typographic graphics** → Ideogram v2 or Recraft v3 (reliable text rendering)
- **Artist portraits / character illustrations** → Flux Pro or Google Imagen 3
- **Abstract / artistic backgrounds** → SDXL or Flux Dev (style control)
- **Conceptual illustrations** (e.g., "creativity connecting communities") → Flux Pro or Flux Dev
- **Quick placeholders during development** → Flux Schnell (fastest)

## Report Sections

The report is a single scrolling page with these sections:

0. **Cover** — Full-screen hero with Arterial branding
1. **Mission & Tenets** — Access, Underrepresentation, Media exposure grows the art economy
2. **Founder's Letter** — Scott Power's year-in-review narrative
3. **Year at a Glance** — Animated key metrics (200 podcast episodes, 36 grant recipients, 30+ exhibitions, 7 Emmys, etc.)
4. **Programs & Projects** — Card grid (priority order: NRA, Arthouse, Artsville USA, Classic Black, Artbound/PBS, Underbelly, Good Art, Arterial Radio)
5. **NOT REAL ART In Depth** — Podcast network, grant program, NRA School, Q+ART, Remote series, artist database
6. **First Friday & Artwork Archive** — 30+ curated online exhibitions, AI-powered submission pipeline, open calls
7. **Arthouse In Depth** — TV series, production team, Chicago pilot, partnerships, distribution strategy
8. **Artsville USA In Depth** — "Tale of Two Cities" at NOAFA, Virtual Gallery, podcast, Louise Glickman Grant & Residency
9. **Classic Black** — Ric'key Pageot, concerts, documentary, Black excellence in classical music
10. **Artist Community** — Featured artists, open calls, testimonials, 2019 Creators Conference
11. **Distribution & Partnerships** — Random Media, PBS SoCal, Austin PBS, Fractured Atlas, Art Share LA, streaming plans
12. **Leadership** — Scott Power, Channing Dungey Power, Joshua Wattles, Man One / Crewest Studio
13. **Financial Summary** — 80/20 allocation, revenue/expense charts, grant and campaign totals
14. **Supporters & Donors** — Tiered recognition
15. **Looking Ahead** — Artwork-archive exports, Artsville PAVE, Arterial Radio, Arthouse network deals

## Getting Started

See **[GETTING-STARTED.md](./GETTING-STARTED.md)** for the complete step-by-step setup guide, including where to get each API key and how to build the RAG knowledge base.

### Prerequisites

**Accounts needed** (see [GETTING-STARTED.md](./GETTING-STARTED.md) for step-by-step signup instructions):

- [Anthropic Claude](https://claude.ai) — Max subscription ($100/mo) for Claude Code
- [GitHub](https://github.com) — Free account for code and issue tracking
- [Replicate](https://replicate.com) — AI image generation (prepaid credits, ~$20 to start)
- [Pinecone](https://pinecone.io) — Vector database for RAG knowledge base (free tier)
- [Google AI Studio](https://aistudio.google.com) — Gemini API for embeddings (free tier)
- [Unsplash](https://unsplash.com/developers) — Stock placeholder images (free tier)
- [FireCrawl](https://firecrawl.dev) — Web scraping (free tier, 500 pages)
- [Vercel](https://vercel.com) — Website hosting and auto-deploy (free tier)
- [Cursor](https://cursor.com) — Code editor with Go Live extension (free)

**Developer tools:** Node.js 18+, Git

### Setup

```bash
# Clone the repo
git clone https://github.com/JuergenB/arterial-impact-report.git
cd arterial-impact-report

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env.local
# Edit .env.local with your API keys

# Run development server
npm run dev
```

### Environment Variables

```
REPLICATE_API_TOKEN=        # Replicate for AI image generation
UNSPLASH_ACCESS_KEY=        # Unsplash API for placeholder images
GOOGLE_AI_API_KEY=          # Gemini API for RAG / File Search
FIRECRAWL_API_KEY=          # FireCrawl for web scraping (optional)
```

### Build & Deploy

```bash
# Build for production
npm run build

# Preview production build locally
npm run preview
```

Deployment to Vercel happens automatically on push to `main`.

## Content Management

### Updating report text
Edit the data files in `/src/data/sections/` — each section has its own TypeScript file with typed content (headlines, body text, metrics, quotes, image references).

### Adding images
1. Place images in `/public/images/[section-name]/`
2. Run `npx ts-node scripts/optimize-image.ts [path]` to compress
3. Reference in the section data file

Or just tell Claude Code: "Use this image for the Programs hero" and drag it into the chat.

### Refreshing the knowledge base
1. Edit `/content/crawl-config.json` to add/remove URLs
2. Run `npx ts-node scripts/crawl-sites.ts`
3. Processed markdown files appear in `/content/crawled/`

### Adding source documents
Drop PDFs or text files into `/docs/arterial/` (or the appropriate subfolder). Run `npx ts-node scripts/process-docs.ts` to convert them to markdown for the knowledge base.

## References & Inspiration

- **Video**: [Google's New Model + Claude Code Just Changed RAG Forever](https://www.youtube.com/watch?v=hem5D1uvy-w) — Nate Herk's walkthrough of building RAG with Gemini Embedding 2, Pinecone, and Claude Code
- **Art21 FY24 Impact Report** — Design reference for section structure, layout patterns, and visual hierarchy (see `docs/reference/`)
- **Pinecone Plugin for Claude Code** — [Official docs](https://www.pinecone.io/blog/pinecone-plugin-for-claude-code/)
- **Gemini File Search API** — [Google docs](https://ai.google.dev/gemini-api/docs/file-search)
- **Gemini Embedding 2** — [Announcement](https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-embedding-2/)

## Project Background

See `/docs/project-background-chat.md` for the full design conversation that shaped this project, including:
- Art21 FY24 impact report structural analysis
- Content inventory of Arterial's existing assets
- Tech stack evaluation (why Astro over Next.js)
- CMS vs. vibe-coding decision
- RAG vs. simpler content loading analysis

## License

Private repository. Content is proprietary to Arterial / NOT REAL ART.
