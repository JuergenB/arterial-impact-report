# Getting Started

Step-by-step setup guide for the Arterial project ecosystem.

This guide covers two audiences:
- **Scott (founder):** Understand what services are needed and how you'll interact with the system
- **Juergen (developer):** Set up the full development environment across all three repositories

---

## Open Decisions (Not Yet Finalized)

The following infrastructure and business decisions are still under discussion:

### Account Ownership & Licensing Model

| Option | How It Works | Pros | Cons |
|--------|-------------|------|------|
| **Scott owns everything** | Scott signs up for all services, owns billing, shares API keys with dev | Full ownership and portability | Scott manages 10+ accounts and API keys |
| **Polymash licenses to Scott** | Polymash (Juergen) owns and manages all infrastructure; Scott pays a monthly fee with zero signups | Zero admin burden for Scott | Dependency on Polymash; less portability |
| **Hybrid** | Scott owns identity accounts (GitHub, Vercel); Polymash manages AI/API infrastructure with dedicated Arterial keys and usage monitoring | Balance of ownership and convenience | More complex billing |

**To decide:**
- Does Scott want to own accounts or rent infrastructure?
- If Polymash licenses, what's the monthly fee structure?
- How are AI API costs (which vary with usage) passed through — flat fee, usage-based, or capped?

### Pricing

| Item | Notes |
|------|-------|
| Development cost | TBD — scope depends on RAG app complexity and report design |
| Ongoing hosting/infrastructure | ~$100–150/mo for AI APIs + hosting (varies with usage) |
| AI API usage monitoring | Need dedicated API keys per project to track and charge back usage |
| Maintenance & updates | Annual report refresh, knowledge base updates, bug fixes |

### Dedicated API Keys for Arterial

If Polymash manages infrastructure, each AI service needs a **dedicated API key for Arterial** (separate from Polymash's own keys) to enable usage monitoring and chargeback:

- Anthropic API (Claude models for automations and agents — separate from Claude Code subscription)
- OpenAI API (GPT-4o, GPT-4.1 for classification, scoring, and automation tasks)
- Google AI / Gemini API (embeddings, retrieval)
- Replicate (image generation)
- Pinecone (vector database)
- FireCrawl (web scraping)

> **Important distinction:** Claude Code (the $100/mo subscription) covers interactive development sessions. But AI models used in **automations, LLM agents, and background pipelines** (e.g., n8n workflows, batch processing, the RAG app's classification features) require separate **Anthropic API** and/or **OpenAI API** keys with their own billing. These are not covered by the Claude Code subscription.

---

## Overview: What You Need

| # | Service | What It Does | Cost | Decision |
|---|---------|-------------|------|----------|
| 1 | **Claude Code** | AI that builds and edits the project interactively (Scott's vibe-coding tool) | $100/mo subscription | Scott's own account (Juergen uses his own during development) |
| 2 | **Anthropic API** | Claude models in automations, agents, pipelines | Pay-per-use (~$5–25/mo) | Dedicated Arterial key needed |
| 3 | **OpenAI API** | GPT-4o/4.1 for classification, scoring, automation | Pay-per-use (~$5–25/mo) | Dedicated Arterial key needed |
| 4 | **GitHub** | Stores the code, tracks tasks | Free | Scott needs account |
| 5 | **Replicate** | Generates images using AI models | ~$0.003–$0.05/image | Ownership TBD |
| 6 | **Pinecone** | Stores the knowledge base (vector database) | Free tier | Ownership TBD |
| 7 | **Google AI Studio** | Powers AI embeddings and search | Free tier | Ownership TBD |
| 8 | **Airtable** | Project config, crawl targets, content management | Free / Team plan (Scott has) | Scott's existing account |
| 9 | **Unsplash** | Stock photos for placeholders | Free | Ownership TBD |
| 10 | **FireCrawl** | Scrapes website content for the knowledge base | Free (500 pages) | Ownership TBD |
| 11 | **Vercel** | Hosts and deploys websites | Free | Ownership TBD |
| 12 | **Cursor** | Code editor with AI features (Scott's future use) | Free | Scott (Phase 4) |

---

## Where to Record API Keys

As you sign up for each service below, you'll get an API key (a long string of characters like a password). Record every key in ONE secure, shared location:

**Recommended: Shared Dropbox folder**
```
Dropbox/Arterial Impact Report/
├── API Keys/              # Text file or spreadsheet with all keys
├── Brand Assets/          # Logos, fonts, brand guidelines
├── Source Documents/      # PDFs, pitch decks — feed into the knowledge base
├── Photos & Media/        # Images, video stills — for report sections
└── Scott Review/          # Drafts for Scott to review and annotate
```

Create a file like `API Keys/api-keys.txt` with this template:

```
Arterial Project — API Keys
==================================
KEEP THIS FILE PRIVATE. Do not email or share outside Dropbox.

# AI Models (for automations — separate from Claude Code subscription)
ANTHROPIC_API_KEY=          (from console.anthropic.com)
OPENAI_API_KEY=             (from platform.openai.com)
GOOGLE_AI_API_KEY=          (from aistudio.google.com)

# Image Generation
REPLICATE_API_TOKEN=        (from replicate.com/account/api-tokens)

# Knowledge Base
PINECONE_API_KEY=           (from app.pinecone.io)

# Project Data
AIRTABLE_PERSONAL_ACCESS_TOKEN=  (from airtable.com/create/tokens)
AIRTABLE_BASE_ID=                (from Airtable API docs, starts with "app")

# Web Scraping
FIRECRAWL_API_KEY=          (from firecrawl.dev)

# Workflow Automation
N8N_API_KEY=                (from n8n cloud settings)

# Stock Images
UNSPLASH_ACCESS_KEY=        (from unsplash.com/developers)
```

**Alternative:** If both Scott and Juergen use 1Password or Bitwarden, create a shared vault called "Arterial Dev."

**Never** put API keys in email, Slack, or text messages.

---

## Service-by-Service Signup Instructions

### 1. Anthropic (Claude) — The AI that powers everything

**What it does:** Claude Code is the AI tool that builds and edits the entire system. When you type instructions in plain English ("change the headline to..."), Claude Code writes the code. This is the most important account — and the core of the vibe-coding workflow that Scott will use to maintain and evolve his projects independently.

**Cost:** $100/month (Claude Max subscription) — **Scott's own account**

**Why Scott needs his own Claude Max subscription:** The entire purpose of this system is for Scott to have a vibe-coding environment where he can make changes himself — update report content, add new documents to the knowledge base, launch new presentation sites, and evolve the platform without needing a developer for every edit. Claude Code with a Max subscription ($100/mo) is what makes this possible. The $20/mo Pro plan has usage limits too strict for real project work.

**Why Max ($100/mo) and not Pro ($20/mo):** Pro has a short context window and strict usage limits. When working on a project this size, you'll hit Pro's limits within minutes, causing frustrating pauses where you have to wait. Max provides the extended context window and higher usage that makes vibe-coding practical. The $200/mo tier exists but is more than needed for Scott's use.

**Step-by-step:**

1. Go to [claude.ai](https://claude.ai)
2. Click **Sign Up** (use your email or Google account)
3. Verify your email if prompted
4. Once logged in, click your profile icon (bottom-left) → **Settings** → **Subscription**
5. Select **Claude Max** at **$100/month**
6. Enter payment information and confirm
7. You now have access to Claude's most capable models with extended context

**Separate API key** (for automated pipelines — Juergen will set this up):

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign in with the same account
3. Click **API Keys** in the left sidebar
4. Click **Create Key**
5. Name it `arterial`
6. **Copy the key immediately** — you will never see it again after closing this dialog
7. Paste it into your shared API keys file as `ANTHROPIC_API_KEY=sk-ant-...`
8. Go to **Settings** → **Billing** → add a payment method
9. Set a **monthly spend limit of $25** (this is separate from the $100/mo subscription and covers API usage by automated pipelines)

**Gotchas:**
- The Claude Max subscription ($100/mo) and the API key billing are separate charges on the same account
- The API key is shown only ONCE when created. If you lose it, delete it and create a new one
- The $25/mo API spend limit is a safety net — actual usage will likely be much less
- During development, Juergen uses his own Claude Code subscription. Scott's subscription is for when Scott takes over day-to-day editing and maintenance

---

### 2. OpenAI — AI models for automations and pipelines

**What it does:** GPT-4o and GPT-4.1 models are used in automated workflows — classifying artwork images, scoring content quality, generating structured data, and other tasks that run in the background without human interaction. These are separate from Claude Code (which is interactive).

**Cost:** Pay-per-use. Budget **$5–25/month** depending on automation volume. Set a monthly spending cap.

**Step-by-step:**

1. Go to [platform.openai.com](https://platform.openai.com)
2. Click **Sign Up** (email or Google account)
3. Verify your email
4. Go to **Settings** → **Billing** → **Add payment method**
5. Add **$25 in prepaid credits** to start
6. Set a **monthly spending limit of $25** under **Settings** → **Limits**
7. Go to **API Keys** (left sidebar) or [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
8. Click **Create new secret key**
9. Name it `arterial`
10. **Copy the key immediately** — you will never see it again
11. Paste it into your shared API keys file as `OPENAI_API_KEY=sk-...`

**Gotchas:**
- OpenAI API is completely separate from a ChatGPT subscription — you need API credits even if you pay for ChatGPT Plus
- The key is shown only ONCE when created
- Prepaid credits expire after 12 months if unused

---

### 3. GitHub — Code repository and task tracking

**What it does:** GitHub stores the project's code and tracks all tasks (issues). Think of it as the project's filing cabinet and to-do list combined.

**Cost:** Free

**Step-by-step:**

1. Go to [github.com](https://github.com)
2. Click **Sign Up** and create an account (use your email)
3. Choose the **Free** plan
4. Juergen will invite you as a collaborator to the `arterial-impact-report` repository
5. Accept the invitation (you'll get an email)
6. No API key needed — GitHub uses your login

**Gotchas:**
- None. This is the simplest signup.

---

### 4. Replicate — AI image generation

**What it does:** Replicate lets the AI generate images for the report — hero backgrounds, artistic illustrations, placeholder graphics — using models like Flux, SDXL, and Ideogram. Each model has different strengths (see the model comparison table in README.md).

**Cost:** Pay-per-use. Prepay credits in advance. Budget **$20 to start** (generates hundreds of images with fast models).

**Step-by-step:**

1. Go to [replicate.com](https://replicate.com)
2. Click **Sign Up** (email or sign in via GitHub)
3. Check your email and click the verification link
4. Click your **profile icon** (top-right) → **Billing**
5. Click **Add payment method** → enter your credit card
6. **Prepay $20** in credits (you can always add more later)
7. Now get your API token:
   - Click your **profile icon** → **Account** (or go directly to [replicate.com/account/api-tokens](https://replicate.com/account/api-tokens))
   - You'll see a default token already generated (starts with `r8_`)
   - Click the **copy button** next to the token
8. Paste it into your shared API keys file as `REPLICATE_API_TOKEN=r8_...`

**Cost examples:**
| What | Model | Cost per image |
|------|-------|---------------|
| Quick placeholder | Flux Schnell | ~$0.003 |
| High-quality hero image | Flux Dev | ~$0.01 |
| Production-quality image | Flux Pro | ~$0.05 |
| Text-heavy graphic | Ideogram v2 | ~$0.03 |

**Gotchas:**
- The free tier only allows ~2–5 runs per model before requiring prepaid credits
- Credits don't expire but are non-refundable
- If your token is accidentally exposed publicly, Replicate auto-disables it and emails you
- Each API call deducts from your prepaid balance immediately

---

### 5. Pinecone — Knowledge base (vector database)

**What it does:** Pinecone stores the project's "AI memory" — all the information about Arterial's programs, history, and ecosystem. When the AI needs to write accurate content about Arterial, it searches Pinecone to find the real facts instead of making things up.

**Cost:** Free (Starter plan)

**Step-by-step:**

1. Go to [app.pinecone.io](https://app.pinecone.io/?sessionType=signup)
2. Click **Sign Up** (email and password, or sign in via Google/GitHub)
3. You're automatically on the **Starter (free)** plan — no credit card needed
4. Once logged in, you'll see a project dashboard
5. Click **API Keys** in the left sidebar
6. Click **Create API Key**
7. Name it `arterial-impact-report`
8. **Copy the key immediately** — you will never see it again after closing this dialog
9. Paste it into your shared API keys file as `PINECONE_API_KEY=...`

**What you get on the free plan:**
- 2 GB storage (enough for ~100,000 documents)
- 5 vector indexes
- 2 million write operations/month
- 1 million read operations/month
- More than sufficient for this project

**Gotchas:**
- **The key is shown ONCE.** If you close the dialog without copying it, you must delete the key and create a new one.
- Free tier is limited to US East region (AWS us-east-1) — this is fine for our use case
- To delete a key, you must have at least 2 keys created first

---

### 6. Google AI Studio — Gemini API for embeddings and search

**What it does:** Google's Gemini API creates the "embeddings" (AI-readable representations) of Arterial's content, which get stored in Pinecone. It also powers the search/retrieval system that finds relevant content when building report sections.

**Cost:** Free

**Step-by-step:**

1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Sign in with a **Google account** (Gmail works)
3. Click **Get API Key** in the top navigation (or go directly to [aistudio.google.com/api-keys](https://aistudio.google.com/api-keys))
4. Click **Create API key**
5. Google will auto-create a project for you if this is your first time
6. **Copy the key** that appears in the dialog
7. Paste it into your shared API keys file as `GOOGLE_AI_API_KEY=...`

**What you get on the free tier:**
- 5–15 requests per minute (depending on model)
- ~1,000 requests per day
- Full access to Gemini models including embeddings
- No credit card required

**Gotchas:**
- Free tier data may be used by Google to improve their products (acceptable for non-sensitive project data)
- If you need higher rate limits later, you can enable billing in the same dashboard — but free tier is sufficient for development

---

### 7. Airtable — Project data and configuration

**What it does:** Airtable serves as the structured data layer for this project — managing crawl targets (which URLs to scrape), content source metadata, report section configuration, and a verification queue for items that need Scott's review. Scott already has a team Airtable account.

**Cost:** Free tier or Scott's existing Team plan

**Step-by-step:**

1. Go to [airtable.com](https://airtable.com) and sign in (Scott's existing account)
2. Create a new base called **"Arterial Knowledge Base"**
3. Get your **Personal Access Token**:
   - Go to [airtable.com/create/tokens](https://airtable.com/create/tokens)
   - Click **Create new token**
   - Name it `arterial-rag`
   - Under **Scopes**, select: `data.records:read`, `data.records:write`, `schema.bases:read`
   - Under **Access**, select the "Arterial Knowledge Base" base
   - Click **Create token**
   - **Copy the token immediately** — you will never see it again
4. Paste it into your shared API keys file as `AIRTABLE_PERSONAL_ACCESS_TOKEN=pat...`
5. Get your **Base ID**:
   - Open the base → click **Help** (?) → **API Documentation**
   - The Base ID is in the URL and starts with `app`
   - Paste it as `AIRTABLE_BASE_ID=app...`

**Gotchas:**
- Airtable deprecated the old "API key" in 2024 — use **Personal Access Tokens** instead
- Token is shown only ONCE when created
- Table IDs will be populated after Juergen creates the required tables

---

### 8. n8n — Workflow automation

**What it does:** n8n is a workflow automation platform that runs background processes — watching Dropbox folders for new files, orchestrating AI enrichment pipelines, scheduling web scrapes, and connecting services together. It's the glue that makes the knowledge base self-maintaining.

**Cost:** Free (self-hosted) or ~$20/mo (n8n Cloud starter). Polymash already has an n8n Cloud instance at polymash.app.n8n.cloud.

**Step-by-step (if creating a dedicated Arterial instance):**

1. Go to [n8n.io](https://n8n.io)
2. Click **Get Started Free**
3. Sign up with email
4. Choose **n8n Cloud** (managed hosting, no server setup)
5. Select the **Starter** plan ($20/mo — 2,500 executions/month)
6. Once your instance is running, get your API key:
   - Go to **Settings** → **API** in the n8n dashboard
   - Click **Create API Key**
   - Copy the key
7. Paste it into your shared API keys file as `N8N_API_KEY=...`
8. Note your instance URL (e.g., `arterial.app.n8n.cloud`)

**Alternatively:** Use Polymash's existing n8n Cloud instance with dedicated Arterial workflows (simplifies management, covered under licensing agreement if applicable).

**Gotchas:**
- n8n Cloud plans are based on execution count, not time — a simple workflow that runs daily uses ~30 executions/month
- Self-hosted is free but requires a server (not recommended unless Scott has DevOps resources)
- API key grants full access to all workflows — treat it like a password

---

### 9. Unsplash — Stock placeholder images

**What it does:** Unsplash provides high-quality stock photos that we use as temporary placeholders while building the report. These get replaced with custom images or AI-generated art later.

**Cost:** Free

**Step-by-step:**

1. Go to [unsplash.com/developers](https://unsplash.com/developers)
2. Click **Register as a developer**
3. If you don't have an Unsplash account, create one first (email + password)
4. Fill in the application form:
   - **Application name:** `Arterial Impact Report`
   - **Description:** `Annual impact report for Arterial.org, a 501(c)(3) non-profit`
   - **Use case:** Select the option closest to "Website/app" or "Internal tool"
5. Accept the API terms
6. You'll be redirected to your application settings page
7. Find and copy the **Access Key** (not the Secret Key)
8. Paste it into your shared API keys file as `UNSPLASH_ACCESS_KEY=...`

**What you get:**
- 50 requests per hour (plenty for fetching placeholder images)
- No credit card required
- Must include photo attribution on publicly visible projects (Unsplash terms)

**Gotchas:**
- You need to register as a "developer" even though you're not writing code — it's just how Unsplash grants API access
- The Access Key and Secret Key are different — you only need the **Access Key**

---

### 10. FireCrawl — Web scraping for the knowledge base

**What it does:** FireCrawl visits Arterial's websites (arterial.org, notrealart.com, etc.) and converts the pages into text that the AI can read and store in the knowledge base. This is how the AI learns about Arterial's programs.

**Cost:** Free to start (500 pages). $16/month if you need more.

**Step-by-step:**

1. Go to [firecrawl.dev](https://firecrawl.dev)
2. Click **Sign Up** (email + password)
3. No credit card required for the free tier
4. Once logged in, navigate to **API Keys** in the dashboard
5. Click **Create API Key**
6. Copy the key
7. Paste it into your shared API keys file as `FIRECRAWL_API_KEY=fc-...`

**What you get on the free tier:**
- 500 one-time credits (1 credit = 1 web page scraped)
- 2 concurrent requests
- Sufficient for initial content ingestion of all Arterial properties

**When to upgrade:**
- When the 500 free credits are used up and you need to re-scrape or scrape additional sites
- Hobby plan: $16/month for 3,000 pages/month

**Gotchas:**
- Free credits are one-time, not monthly — once used, they don't refill
- Each page scraped costs 1 credit, regardless of page size

---

### 11. Vercel — Website hosting and auto-deploy

**What it does:** Vercel hosts the final website and automatically publishes updates whenever code is pushed to GitHub. Every code change triggers a new deployment within ~2 minutes.

**Cost:** Free (Hobby plan)

**Step-by-step:**

1. Go to [vercel.com](https://vercel.com)
2. Click **Sign Up**
3. Choose **Continue with GitHub** (this links your GitHub account)
4. Authorize Vercel to access your GitHub repositories
5. Once logged in, click **Add New Project**
6. Select the `arterial-impact-report` repository from the list
7. Vercel auto-detects Astro and configures build settings
8. Click **Deploy**
9. Your site will be live at a `*.vercel.app` URL within ~2 minutes
10. Every future push to the `main` branch on GitHub auto-deploys

**No API key needed** — Vercel connects directly to GitHub. Environment variables (API keys) are added in the Vercel dashboard under **Settings** → **Environment Variables** when you're ready to deploy.

**What you get on the free Hobby plan:**
- Unlimited deployments
- 100 GB bandwidth/month (more than enough for an annual report)
- Automatic HTTPS/SSL
- Preview deployments for every Git push

**Gotchas:**
- The Hobby plan is for personal/non-commercial projects. If Arterial needs commercial terms, upgrade to Pro ($20/user/month) — but Hobby is fine for now
- If you exceed 100GB bandwidth in a month (extremely unlikely for a report site), new deployments pause until the next billing cycle

---

### 12. Cursor — Code editor (Phase 4, for Scott)

**What it does:** Cursor is a code editor (like Microsoft Word, but for code) that has AI built in. This is where Scott will eventually open the project, see the files, and use Claude Code to make edits. It also has a "Go Live" feature that shows you the website updating in real-time as changes are made.

**Cost:** Free

**When to install:** Not yet. Scott installs Cursor during Phase 4 (Design Polish & Onboarding), after Juergen has built most of the project. The instructions below are for reference.

**Step-by-step:**

1. Go to [cursor.com](https://cursor.com)
2. Click **Download** (macOS version)
3. Open the downloaded `.dmg` file and drag Cursor to your Applications folder
4. Launch Cursor
5. It may ask to import settings from VS Code — click **Skip** if you haven't used VS Code before

**Install the Go Live extension (free):**

6. In Cursor, press **Cmd+Shift+X** to open the Extensions panel
7. Search for **"Live Server"** by Ritwick Dey
8. Click **Install**
9. After installing, you'll see a **"Go Live"** button in the bottom-right status bar
10. Clicking **Go Live** launches a local web server that auto-refreshes whenever files change — you see edits in real-time

**Install Claude Code extension:**

11. In the Extensions panel (Cmd+Shift+X), search for **"Claude Code"**
12. Click **Install**
13. After installing, Claude Code appears in the sidebar
14. Sign in with your Anthropic account (the one with the Max subscription from Step 1)
15. You can now type instructions in plain English and Claude Code edits the project

**Gotchas:**
- Cursor is a fork of VS Code — if you've used VS Code before, it will feel identical
- The free Cursor plan is all you need (Cursor's own AI features are separate from Claude Code)
- Go Live is great for previewing static HTML changes; for the Astro project, `npm run dev` (which Juergen sets up) provides its own hot-reload

---

## Developer Setup (Juergen)

These additional steps are for Juergen's development environment. Scott does NOT need these.

### Clone the Repo

```bash
git clone https://github.com/JuergenB/arterial-impact-report.git
cd arterial-impact-report
```

### Set Up Environment Variables

```bash
cp .env.example .env.local
```

Open `.env.local` and paste in the API keys from the shared Dropbox file.

### Install Dependencies

```bash
npm install
```

### Install the Pinecone Plugin for Claude Code

This gives Claude Code direct access to the vector database:

```bash
claude plugin install pinecone
```

Then restart Claude Code (or Cursor).

### Run the Development Server

```bash
npm run dev
```

Visit `http://localhost:4321` to see the report.

### Claude Code Desktop Notifications (CCNotify)

Optional but highly recommended. Sends macOS desktop notifications when Claude Code tasks complete or need your input — especially useful when sub-agents are running long tasks.

**Prerequisites:**

```bash
brew install terminal-notifier
```

**Install CCNotify:**

1. Clone the CCNotify repo into your Claude config directory:
   ```bash
   git clone https://github.com/dazuiba/CCNotify.git ~/.claude/ccnotify
   ```

2. Add hooks to your `~/.claude/settings.json` (inside the `"hooks"` object):
   ```json
   {
     "hooks": {
       "UserPromptSubmit": [
         { "hooks": [{ "type": "command", "command": "~/.claude/ccnotify/ccnotify.py UserPromptSubmit" }] }
       ],
       "Stop": [
         { "hooks": [{ "type": "command", "command": "~/.claude/ccnotify/ccnotify.py Stop" }] }
       ],
       "Notification": [
         { "hooks": [{ "type": "command", "command": "~/.claude/ccnotify/ccnotify.py Notification" }] }
       ]
     }
   }
   ```

3. Restart Claude Code. You'll now get macOS notifications when:
   - A task finishes ("job done, duration: 45s")
   - Claude needs permission to run a command
   - Claude is waiting for your input

### Build the RAG Knowledge Base

This is Phase 2 work. Open Claude Code and follow the approach from [Nate Herk's video](https://www.youtube.com/watch?v=hem5D1uvy-w):

1. **Switch Claude Code to plan mode**
2. **Tell it what you want:**
   > "I want to use Gemini's new Embeddings 2 model to create a Pinecone vector database filled with documents, images, and text about Arterial.org and its sub-projects. The content is in the /content folder. Please build me a plan to set this up. Use the API keys from .env.local."
3. **Review and approve the plan**
4. **Drop content into `/content/`:**
   - PDFs and documents → `/content/documents/`
   - Crawled web pages (markdown) → `/content/web/`
   - Image/video/audio metadata → `/content/media/`
5. **Claude Code creates the Pinecone index and ingests everything**

#### Quick Test

Once ingestion is done, test the knowledge base:

```
/pinecone:assistant-chat What are Arterial's main programs and initiatives?
```

You should get a cited answer referencing your uploaded documents.

### Deploy to Vercel

1. Push to GitHub (auto-deploys if Vercel is connected)
2. Or deploy manually:
   ```bash
   npx vercel
   ```
3. Add your environment variables in the Vercel dashboard under Settings → Environment Variables

---

## Making Changes (Phase 4 — Scott's Workflow)

Once Cursor is set up and the project is built:

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

---

## Folder Structure

```
arterial-impact-report/
├── .env.example          # Template — copy to .env.local
├── .env.local            # Your API keys (gitignored, never committed)
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

---

## Troubleshooting

**Claude Code doesn't recognize the Pinecone plugin:**
- Make sure you ran `claude plugin install pinecone`
- Restart Claude Code / Cursor after installing
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

**Claude Code hits usage limits (Pro plan):**
- This is why Max ($100/mo) is recommended — Pro limits are too restrictive for project-scale work
- If on Pro, wait for the limit to reset or upgrade to Max

**Desktop notifications not working (Juergen):**
- Verify `terminal-notifier` is installed: `which terminal-notifier`
- Check `~/.claude/ccnotify/ccnotify.log` for errors
- Ensure hooks are configured in `~/.claude/settings.json`
