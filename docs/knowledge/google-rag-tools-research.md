---
name: Google RAG Tools Research
description: Research on Google's new tools for building RAG systems, based on YouTube video analysis
type: research
source: https://www.youtube.com/watch?v=hem5D1uvy-w
date: 2026-03-12
---

# Google RAG Tools Research

## Video Summary

**Title:** "Google's New Model + Claude Code Just Changed RAG Forever"
**Channel:** Nate Herk | AI Automation (https://www.youtube.com/@nateherk)
**URL:** https://www.youtube.com/watch?v=hem5D1uvy-w

The video demonstrates how Google's newly released **Gemini Embedding 2** model (released March 10, 2026) combined with **Claude Code** can dramatically simplify building RAG (Retrieval-Augmented Generation) systems. Nate Herk walks through building a full visual search engine from scratch using Claude Code to orchestrate the process. The key insight is that you no longer need to build chunking or ingestion pipelines yourself -- Claude Code handles the orchestration while Google's new embedding model handles multimodal understanding natively.

The video shows Claude Code extracting content from images, generating descriptions, and building out a Pinecone vector database -- all through natural language instructions rather than manual pipeline construction.

---

## Google Tools & APIs for Building RAG Systems

### 1. Gemini Embedding 2 (NEW -- March 2026)

Google's first **natively multimodal embedding model** that maps text, images, video, audio, and documents into a single unified vector space.

**Key capabilities:**
- Processes text (up to 8,192 input tokens), images (up to 6 per request, PNG/JPEG), video (up to 120 seconds, MP4/MOV), and audio natively
- Handles interleaved multimodal input (e.g., image + text in a single request)
- Supports 100+ languages
- Uses Matryoshka Representation Learning (MRL) for flexible vector sizes: 3,072, 1,536, or 768 dimensions
- Reduces latency by up to 70% compared to multi-model pipelines
- Outperforms Amazon Nova 2 and Voyage Multimodal 3.5 on benchmarks
- Available as `gemini-embedding-2-preview` via Gemini API and Vertex AI

**Relevance to impact report project:** This model could embed PDFs, crawled web pages, and any images/infographics from source documents into a single searchable vector space. However, it requires building your own vector store (e.g., Pinecone, ChromaDB) and retrieval pipeline.

### 2. Gemini File Search Tool (November 2025)

A **fully managed RAG system** built directly into the Gemini API. This is the simpler, more turnkey option.

**Key capabilities:**
- Automatic chunking, embedding, indexing, and retrieval -- no vector DB needed
- Supports 20+ file formats: PDF, DOCX, TXT, HTML, JSON, Excel, PowerPoint, Markdown, CSV, code files, Jupyter notebooks, LaTeX, XML, ZIP archives
- Built-in citations showing which document sections were used
- Metadata tagging and filtering for documents
- Configurable chunking (token limits and overlap)
- Works within the standard `generateContent` API
- Structured output support (Gemini 3+ models)

**Pricing:**
- Indexing: $0.15 per 1M tokens (one-time cost when documents are uploaded)
- Storage: Free
- Query-time embeddings: Free
- Retrieved document tokens: Standard context token pricing

**Storage limits:**
| Tier | Storage Limit |
|------|--------------|
| Free | 1 GB |
| Tier 1 | 10 GB |
| Tier 2 | 100 GB |
| Tier 3 | 1 TB |

- Max file size: 100 MB per document
- Recommended max per store: 20 GB for optimal latency
- Max 10 stores per project
- Backend storage ~3x input size (includes embeddings)

**Limitations:**
- Only available via Gemini API (NOT Vertex AI API)
- Cannot combine with Google Search or URL Context tools in same request
- No web crawling -- files must be uploaded or imported
- Black-box indexing with limited debugging
- Project-level permissions only (no granular IAM)

### 3. Vertex AI RAG Engine

Google Cloud's enterprise-grade RAG solution with more customization.

**Key differences from File Search:**
- Supports custom chunking strategies and algorithms
- Works with Vertex AI Model Garden (including open-source models)
- Integrates with GCS, Google Drive, Jira, Slack connectors
- Granular IAM access control
- More debugging/inspection capability
- Higher cost and complexity

**Best for:** Enterprise deployments needing fine-grained control, custom models, or integration with existing Google Cloud infrastructure.

### 4. Vertex AI Search

A separate service with actual **web crawling** capabilities. Can index URLs and web pages directly. More oriented toward search applications than document Q&A.

---

## Step-by-Step Process (from video and related tutorials)

### Approach A: Gemini File Search (Managed RAG -- Simplest)

1. **Get a Gemini API key** from Google AI Studio (https://aistudio.google.com)
2. **Install the Google GenAI SDK:**
   ```bash
   pip install google-genai
   ```
3. **Create a File Search Store:**
   ```python
   client = genai.Client(api_key=os.environ["GEMINI_API_KEY"])
   store = client.file_search_stores.create(
       config={'display_name': 'impact-report-knowledge'}
   )
   ```
4. **Upload documents** (PDFs, DOCX, HTML, etc.):
   ```python
   operation = client.file_search_stores.upload_to_file_search_store(
       file='document.pdf',
       file_search_store_name=store.name,
       config={
           'display_name': 'source-doc',
           'chunking_config': {
               'white_space_config': {
                   'max_tokens_per_chunk': 200,
                   'max_overlap_tokens': 20
               }
           }
       }
   )
   ```
5. **Query with RAG context:**
   ```python
   response = client.models.generate_content(
       model="gemini-2.5-flash",
       contents="What are the key impacts described in these documents?",
       config=types.GenerateContentConfig(
           tools=[types.Tool(
               file_search=types.FileSearch(
                   file_search_store_names=[store.name]
               )
           )]
       )
   )
   ```
6. **Access citations** via `response.candidates[0].grounding_metadata`

### Approach B: Gemini Embedding 2 + Custom Vector Store (from video)

1. **Set up a vector database** (Pinecone, ChromaDB, etc.)
2. **Use Claude Code** to orchestrate the pipeline:
   - Point Claude Code at your document collection
   - Claude Code extracts content, generates descriptions for images
   - Uses Gemini Embedding 2 API to generate embeddings
   - Stores embeddings in vector database
3. **Build retrieval logic** to query the vector store
4. **Feed retrieved context** into your LLM of choice (Claude, Gemini, etc.)

---

## Feasibility for the Arterial Impact Report Project

### Project Requirements Recap

The impact report project needs to:
- Crawl and process web content from multiple nonprofit/arts organization sites
- Process PDFs and documents (reports, publications, research)
- Build a knowledge base for generating a comprehensive impact report
- Generate section-by-section content grounded in source material

### Option 1: Gemini File Search (Recommended for evaluation)

**Pros:**
- Extremely low setup cost and complexity
- Handles PDFs and documents natively with automatic chunking
- Built-in citations for source attribution (critical for an impact report)
- Free storage, cheap indexing ($0.15/1M tokens)
- No infrastructure to manage
- Could be set up via n8n workflow (template exists: https://n8n.io/workflows/11197)

**Cons:**
- Requires Gemini as the query-time LLM (cannot use Claude for RAG queries directly)
- No web crawling -- must download/convert web content to files first
- 100 MB per-file limit
- Cannot combine File Search with other tools in same API call
- Limited debugging when retrieval quality is poor
- 10 stores per project limit

**Hybrid approach:** Use Gemini File Search for retrieval, then pass the retrieved context + citations to Claude for final report generation. This is architecturally viable -- retrieve with Gemini, generate with Claude.

### Option 2: Gemini Embedding 2 + Custom Pipeline

**Pros:**
- Multimodal -- can embed images, charts, infographics from reports
- Use any LLM for generation (Claude works perfectly)
- Full control over chunking, retrieval, and ranking
- Can handle web-crawled content directly

**Cons:**
- Requires building and managing a vector database
- More complex pipeline to build and maintain
- Higher ongoing infrastructure cost
- Overkill if the content is primarily text-based PDFs and web pages

### Option 3: Stick with Per-Section Context Loading (Current Approach)

**Pros:**
- Simplest architecture, already designed
- No external dependencies beyond Claude API
- Full control over what context goes into each section
- No retrieval quality concerns -- context is hand-curated per section

**Cons:**
- Manual curation of context per section
- Cannot easily scale to large document collections
- May miss relevant connections across documents
- More token-intensive (loading full context rather than relevant chunks)

### Recommendation

**A RAG system IS the right approach for this project.** The corpus will grow beyond the initial estimate as we add more domains (crewststudio.com, artsvilleusa.com, RSS feeds, sitemaps). More importantly, Scott wants a **persistent, queryable knowledge base about his entire business** — not just content for one report. This knowledge base will power:

1. This impact report (and future annual reports)
2. Chatbots for Scott to query Arterial's institutional knowledge
3. Any future content generation or analysis tools

---

## Pinecone Plugin for Claude Code (from the video approach)

The video demonstrates using the **Pinecone Plugin for Claude Code** — an official integration that brings vector database operations directly into the Claude Code workflow.

### Setup (3 steps)

1. **Get a Pinecone API key**: Sign up at https://www.pinecone.io (free tier available)
2. **Set environment variable**:
   ```bash
   export PINECONE_API_KEY=your-api-key-here
   ```
3. **Install the plugin in Claude Code**:
   ```bash
   claude plugin install pinecone
   ```
   Then restart Claude Code.

### Pinecone Assistant (Managed RAG)

Pinecone Assistants handle the full RAG pipeline automatically — no custom chunking, embedding, or retrieval code needed.

**Supported document formats**: PDF, Markdown, TXT, DOCX, JSON

**Key commands in Claude Code:**
- `/pinecone:assistant-chat` — Query with cited answers (includes page numbers)
- `/pinecone:assistant-context` — Extract relevant snippets for custom workflows
- `assistant-sync` — Sync only new or modified documents (incremental updates)

**What it handles automatically:**
- Document chunking
- Embedding generation
- Index management
- Retrieval and ranking
- Citation with page numbers

**Limitation**: Requires `uv` package manager installed for assistant commands.

### Vector Database Operations

For more custom control:
- `/pinecone:query` — Semantic search with metadata filtering (integrated indexes only)
- Index creation, vector upsert, namespace management
- Natural language commands: "list my Pinecone indexes", "build an assistant from PDFs"

### Recommended Folder Structure for RAG Content

Based on the video approach and multimodal embedding capabilities:

```
/content
├── /documents              # PDFs, DOCX, pitch decks, reports
│   ├── arterial/
│   ├── arthouse/
│   ├── not-real-art/
│   └── classic-black/
├── /web                    # Crawled web content (markdown files)
│   ├── arterial-org/
│   ├── notrealart-com/
│   ├── crewststudio-com/
│   ├── artsvilleusa-com/
│   └── classicblackmusic-org/
├── /media                  # Image descriptions, video metadata
│   ├── images/             # AI-generated descriptions of key images
│   ├── video/              # Podcast/video episode metadata and transcripts
│   └── audio/              # Audio content descriptions
├── /feeds                  # RSS feed snapshots
│   └── notrealart-rss/
├── /links                  # Sitemaps, URL lists, curated link collections
│   ├── sitemaps/
│   └── url-lists/
├── crawl-config.json       # FireCrawl configuration
└── _section-map.json       # Content-to-report-section index
```

---

## Integration with Claude Code

### Approach A: Pinecone Plugin (Recommended for POC)

This is the simplest path and matches what the video demonstrates:

1. Install Pinecone plugin in Claude Code
2. Create a Pinecone Assistant
3. Upload all content files (crawled markdown, PDFs, documents)
4. Query the assistant for each report section
5. Claude Code generates the section using retrieved context + citations

```
[Content Sources]
    --> [FireCrawl / PDF extraction: Convert to markdown/text]
    --> [Pinecone Assistant: Upload documents]
    --> [Claude Code + /pinecone:assistant-chat: Query per section]
    --> [Generate report section with cited sources]
```

### Approach B: Gemini File Search (Alternative)

Google's managed RAG with richer metadata filtering:

```python
from google import genai
client = genai.Client()

# Create a store
store = client.file_search_stores.create(
    config={'display_name': 'arterial-knowledge'}
)

# Upload with metadata tags
client.file_search_stores.upload_to_file_search_store(
    file='document.pdf',
    file_search_store_name=store.name,
    config={
        'display_name': 'arterial-pitch-deck',
        'chunking_config': {
            'white_space_config': {
                'max_tokens_per_chunk': 200,
                'max_overlap_tokens': 20
            }
        }
    }
)

# Add custom metadata for filtering
client.file_search_stores.import_file(
    file_search_store_name=store.name,
    file_name=sample_file.name,
    custom_metadata=[
        {"key": "report_section", "string_value": "programs"},
        {"key": "source_domain", "string_value": "arterial.org"},
        {"key": "content_type", "string_value": "web_crawl"}
    ]
)

# Query with metadata filter
response = client.models.generate_content(
    model="gemini-2.5-flash",
    contents="What are Arterial's key program initiatives?",
    config=types.GenerateContentConfig(
        tools=[types.Tool(
            file_search=types.FileSearch(
                file_search_store_names=[store.name],
                metadata_filter="report_section=\"programs\""
            )
        )]
    )
)
```

**Gemini File Search supported formats**: PDF, DOCX, XLSX, PPTX, JSON, SQL, LaTeX, Jupyter notebooks, HTML, CSS, XML, CSV, Markdown, plain text, 100+ programming languages, ZIP archives.

### Approach C: Gemini Embedding 2 + Custom Vector Store (Advanced)

For multimodal search (text + images + video in one query):
1. Use Gemini Embedding 2 API to generate embeddings
2. Store in Pinecone, ChromaDB, Weaviate, or Supabase pgvector
3. Build custom retrieval logic
4. Full control but more infrastructure to manage

---

## Costs Estimate (for Arterial project scale)

### Pinecone (from the video approach)
| Component | Estimated Cost |
|-----------|---------------|
| Pinecone free tier | $0/month (1 index, 100K vectors) |
| Pinecone Starter (if free tier exceeded) | $25/month |
| Claude API (report generation) | Existing cost, unchanged |

### Gemini File Search (alternative)
| Component | Estimated Cost |
|-----------|---------------|
| Indexing | ~$0.05 (negligible for small corpus) |
| Storage | Free |
| Query tokens (retrieval) | ~$0.50-2.00 for full report generation |
| Claude API (report generation) | Existing cost, unchanged |
| **Total additional cost** | **~$0.55-2.05 one-time** |

---

## Prerequisites

### For Pinecone + Claude Code Plugin:
- Pinecone account (free tier available)
- Pinecone API key
- Claude Code with plugin support
- `uv` package manager (for assistant commands)
- Source documents in supported formats (PDF, DOCX, Markdown, TXT, JSON)

### For Gemini File Search:
- Google AI Studio account (free)
- Gemini API key
- Python 3.9+ with `google-genai` package
- Source documents in supported formats

### For either approach:
- Web content must be pre-crawled and saved as files (no built-in web crawling in either system)
- FireCrawl, crawl4ai, or similar tool for web scraping
- An Airtable (optional) for managing the URL list and scrape schedule

---

## URL Management via Airtable

For managing which URLs to scrape and tracking what's been ingested:

**Proposed Airtable structure:**
| Field | Type | Purpose |
|-------|------|---------|
| URL | URL | The page to scrape |
| Domain | Single select | arterial.org, notrealart.com, etc. |
| Content Type | Single select | page, blog, rss-feed, sitemap, about, program |
| Report Sections | Multi-select | Which report sections this content maps to |
| Scrape Status | Single select | pending, scraped, failed, needs-rescrape |
| Last Scraped | Date | When this URL was last processed |
| Relevance Score | Number (1-10) | AI-assigned or manual relevance rating |
| Notes | Long text | Manual notes on content |
| Output File | Text | Path to the resulting markdown file in /content |

This Airtable serves as the "URL management interface" — a curated, filterable list of everything that should feed into the knowledge base. An n8n workflow or script reads this table, scrapes pending URLs, and updates the status.

---

## Key Sources

- Video: [Google's New Model + Claude Code Just Changed RAG Forever](https://www.youtube.com/watch?v=hem5D1uvy-w) — Nate Herk
- Pinecone Plugin for Claude Code — https://www.pinecone.io/blog/pinecone-plugin-for-claude-code/
- Pinecone Claude Code Plugin (GitHub) — https://github.com/pinecone-io/pinecone-claude-code-plugin
- Gemini API File Search Documentation — https://ai.google.dev/gemini-api/docs/file-search
- Google Codelab: Gemini File Search for RAG — https://codelabs.developers.google.com/gemini-file-search-for-rag
- Gemini Embedding 2 Announcement — https://blog.google/innovation-and-ai/models-and-research/gemini-models/gemini-embedding-2/
- n8n Template: RAG with Gemini File Search — https://n8n.io/workflows/11197
- Anthropic RAG Cookbook (Pinecone) — https://github.com/anthropics/claude-cookbooks/blob/main/third_party/Pinecone/rag_using_pinecone.ipynb
