# Getting Started

Step-by-step setup guide for the Arterial Impact Report project.

## Prerequisites

You need:
- **Node.js 18+** — [Download](https://nodejs.org)
- **Claude Code** — Paid account required. [Install in VS Code](https://marketplace.visualstudio.com/items?itemName=anthropic.claude-code) or use the CLI.
- **Git** — For cloning and committing changes
- A **code editor** — VS Code recommended (Claude Code integrates with it)

## Step 1: Clone the Repo

```bash
git clone https://github.com/JuergenB/arterial-impact-report.git
cd arterial-impact-report
```

## Step 2: Set Up API Keys

Copy the example environment file:

```bash
cp .env.example .env.local
```

Then open `.env.local` and add your keys. Here's where to get each one:

### Required for RAG Knowledge Base

| Key | Where to Get It | Free Tier? |
|-----|----------------|------------|
| `PINECONE_API_KEY` | [pinecone.io](https://www.pinecone.io) → Sign up → API Keys | Yes (1 index, 100K vectors) |
| `GOOGLE_AI_API_KEY` | [aistudio.google.com](https://aistudio.google.com) → Get API Key | Yes (generous limits) |

### Required for Content Generation

| Key | Where to Get It | Free Tier? |
|-----|----------------|------------|
| `ANTHROPIC_API_KEY` | [console.anthropic.com](https://console.anthropic.com) → API Keys | No (pay-per-use) |

### Optional but Recommended

| Key | Where to Get It | Purpose | Free Tier? |
|-----|----------------|---------|------------|
| `OPENROUTER_API_KEY` | [openrouter.ai](https://openrouter.ai) → Account → API Keys | Multi-model chat access | Yes (limited) |
| `FIRECRAWL_API_KEY` | [firecrawl.dev](https://firecrawl.dev) → Sign up | Web scraping | Yes (500 pages/month) |
| `UNSPLASH_ACCESS_KEY` | [unsplash.com/developers](https://unsplash.com/developers) → New Application | Placeholder images | Yes (50 req/hour) |
| `AIRTABLE_API_KEY` | [airtable.com/account](https://airtable.com/account) → API | URL management | Yes |
| `AIRTABLE_BASE_ID` | Your Airtable base URL contains it: `airtable.com/BASE_ID/...` | URL management | — |

## Step 3: Install the Pinecone Plugin for Claude Code

This gives Claude Code direct access to your vector database:

```bash
claude plugin install pinecone
```

Then restart Claude Code (or VS Code).

## Step 4: Install Dependencies

```bash
npm install
```

## Step 5: Build the RAG Knowledge Base

This is where the magic happens. Open Claude Code and follow the approach from [Nate Herk's video](https://www.youtube.com/watch?v=hem5D1uvy-w):

1. **Switch Claude Code to plan mode**
2. **Tell it what you want:**
   > "I want to use Gemini's new Embeddings 2 model to create a Pinecone vector database filled with documents, images, and text about Arterial.org and its sub-projects. The content is in the /content folder. Please build me a plan to set this up. Use the API keys from .env.local."
3. **Review and approve the plan**
4. **Drop content into `/content/`:**
   - PDFs and documents → `/content/documents/`
   - Crawled web pages (markdown) → `/content/web/`
   - Image/video/audio metadata → `/content/media/`
5. **Claude Code creates the Pinecone index and ingests everything**

### Quick Test

Once ingestion is done, test the knowledge base:

```
/pinecone:assistant-chat What are Arterial's main programs and initiatives?
```

You should get a cited answer referencing your uploaded documents.

## Step 6: Run the Report Site (Development)

```bash
npm run dev
```

Visit `http://localhost:4321` to see the report.

## Step 7: Deploy to Vercel

1. Push to GitHub (auto-deploys if Vercel is connected)
2. Or deploy manually:
   ```bash
   npx vercel
   ```
3. Add your environment variables in the Vercel dashboard under Settings → Environment Variables

## Making Changes

### Edit text
Tell Claude Code what to change:
> "Change the Programs section headline to 'Amplifying Art Across America'"

### Replace an image
Drag an image into the Claude Code chat:
> "Use this as the hero image for the Cover section"

### Add a section
> "Add a new section about Arterial Radio between Programs and Artist Community. It should mention it's an internet-based talk radio channel dedicated to the arts."

### Refresh the knowledge base
Drop new documents into `/content/` and tell Claude Code:
> "New documents have been added to /content/documents/arterial/. Please ingest them into the Pinecone database."

## Folder Structure

```
arterial-impact-report/
├── .env.example          # Template — copy to .env.local
├── .env.local            # Your API keys (gitignored)
├── CLAUDE.md             # Claude Code instructions (read automatically)
├── README.md             # Project overview
├── GETTING-STARTED.md    # This file
│
├── docs/                 # Project documentation
│   ├── reference/        # Design references (Art21 PDF)
│   ├── knowledge/        # RAG research and video transcript
│   └── context/          # Background conversations
│
├── content/              # RAG knowledge base content
│   ├── documents/        # PDFs, DOCX, pitch decks
│   ├── web/              # Crawled website content (markdown)
│   ├── media/            # Image/video/audio descriptions
│   ├── feeds/            # RSS feed snapshots
│   └── links/            # Sitemaps, URL lists
│
├── scripts/              # Utility scripts
├── public/               # Static assets (images, logos)
└── src/                  # Astro site source code
    ├── pages/
    ├── components/
    ├── data/
    └── lib/
```

## Troubleshooting

**Claude Code doesn't recognize the Pinecone plugin:**
- Make sure you ran `claude plugin install pinecone`
- Restart Claude Code / VS Code after installing
- Verify your `PINECONE_API_KEY` is set in `.env.local`

**Pinecone assistant commands fail:**
- Install `uv` package manager: `curl -LsSf https://astral.sh/uv/install.sh | sh`
- Restart your terminal after installing

**Images are too large / slow to load:**
- Run the optimization script: `npx ts-node scripts/optimize-image.ts [path-to-image]`
- Or tell Claude Code: "This image is too large, please optimize it"

**Site won't build:**
- Check `npm run build` output for errors
- Make sure all referenced images exist in `/public/images/`
