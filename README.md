# Arterial Impact Report

A web-based annual impact report for [Arterial.org](https://arterial.org), a 501(c)(3) non-profit media organization dedicated to human creativity.

## What This Is

This project generates a visually rich, scroll-driven impact report — similar to what organizations like Art21 produce as annual PDFs — but as a fast, interactive, mobile-friendly website. It covers Arterial's full ecosystem:

- **NOT REAL ART** — Podcast network, grant program, school, exhibitions, artist database
- **The Underbelly Project** — Documentary grant and film completion
- **Artbound / PBS** — Emmy Award-winning series partnership
- **Classic Black** — Classical music program with Ric'key Pageot
- **Arthouse** — Unscripted TV series in development
- **The Good Art** — Lowbrow art movement documentary
- **Artsville USA** — Digital platform for American contemporary arts & crafts
- **Arterial Radio** — Internet-based arts talk radio
- **Crewest Studio** — Partner creative space

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
| Framework | [Astro](https://astro.build) 5.x |
| Styling | [Tailwind CSS](https://tailwindcss.com) 4.x |
| Animation | [GSAP](https://gsap.com) + ScrollTrigger + [Lenis](https://lenis.darkroom.engineering/) |
| Images | Astro `<Image>` (build-time optimization) + Sharp |
| Deployment | [Vercel](https://vercel.com) |
| Knowledge base | Gemini File Search (managed RAG) + Gemini Embedding 2 |
| Content scraping | [FireCrawl](https://firecrawl.dev) |
| Build tool | [Claude Code](https://claude.ai/claude-code) |

## Report Sections

The report is a single scrolling page with these sections:

0. **Cover** — Full-screen hero with Arterial branding
1. **Mission & Tenets** — Access, Underrepresentation, Media exposure grows the art economy
2. **Founder's Letter** — Scott Power's year-in-review narrative
3. **Year at a Glance** — Animated key metrics (2,000+ artists, 6 podcasts, 300+ hours, etc.)
4. **Programs & Projects** — Card grid of all Arterial initiatives
5. **NOT REAL ART** — Deep dive into the NRA ecosystem
6. **Artist Community** — Featured artists, First Fridays, open calls
7. **Distribution & Partnerships** — Random Media, PBS, streaming plans
8. **Leadership** — Scott Power, Joshua Wattles, advisory
9. **Financial Summary** — 80/20 program-to-admin allocation, revenue/expense charts
10. **Supporters & Donors** — Tiered recognition
11. **Looking Ahead** — Next FY goals and calls to action

## Getting Started

See **[GETTING-STARTED.md](./GETTING-STARTED.md)** for the complete step-by-step setup guide, including where to get each API key and how to build the RAG knowledge base.

### Prerequisites

- Node.js 18+
- A Google AI API key (for Gemini File Search / RAG)
- An Unsplash API key (for placeholder images)
- A FireCrawl API key (for web scraping, optional if content is already crawled)

### Setup

```bash
# Clone the repo
git clone https://github.com/[org]/arterial-impact-report.git
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
