Assistant: Hello, I am the NOT REAL ART & Arterial Assistant.

User: So knowing what you know about arterial.org there is a new project shaping up to create a 501(c)(3) type impact report about the organisation and its benefits to the art. This spans both arterial.org, Not Real Art, Artsville USA, the various projects that arterial is sponsoring, including art house classic black projects like remote series and many other initiatives, as well as our artwork archive database, first Friday's exhibition schedule, your collection of over 2,000 artists that we have and are supporting actively.

I have a PDF from art21's impact statement, which I believe is released yearly. What I would like to do is use Claude code and the tech stack that I'm using with Next.js Claude code to build an attractive web-based alternative or copy of such an attractively laid out and highly graphical and highly impactful report. I can provide that PDF file as part of the training data but basically I was going to try to either get Perplexity to research this and put data together and then put together the prompts and initiation for a Claude code project to build a web version of this based on content that we might gather. That content could live in a data or in a docs directory as a bunch of MD files that constitute different parts of such a report and the research results for each part or it could also be an Airtable. I have a boilerplate tech stack using Claude code and Airtable that's then deployed on Vercel for the actual production viewable web experience.

I want your advice and guidance on how to prompt Perplexity through that and how to analyze such a PDF report in order to build the project specification, user stories, layout, and directions for graphical user interface. I don't want you to design anything at this point; it's a matter of specifications. Those specifications will be added to GitHub in a project for this particular Git or a new repo for this particular project. That repo's README.md files and various memory.md file instructions will guide Claude code through the building process but we need to come up with the correct requirements first. Where do we start and how can you help? Can you use Perplexity calls for some of the larger research that would need to be done or do you want me to start by uploading a PDF, which is rather large, or at least adding it to the library somehow or providing your link to it, where you can analyze one of these PDFs in order to come up with the design and structure and layout for such an online impact report for arterial.org? 

Assistant: 

This is a well-defined project with clear deliverables. Let me break down a practical approach to getting started.

## Where We Start

There are **three parallel tracks** we can pursue, and I'd recommend tackling them simultaneously:

### Track 1: Analyze the Art21 Impact Report (Reference Model)

The Art21 PDF is your design reference — it establishes the **structural template** for what Arterial's report should look like. Here's what I recommend:

- **Upload the PDF to the knowledge base** so I can analyze it directly. This is preferable to a URL since these reports are often behind gates or rendered in ways that don't scrape well. Once it's in the training data, I can extract:
  - Section structure and hierarchy
  - Content categories (financials, reach metrics, program highlights, testimonials, etc.)
  - Data visualization types used (charts, infographics, stat callouts)
  - Layout patterns (hero sections, sidebars, pull quotes, image grids)
  - Tone and narrative arc

- Alternatively, if you can share a public URL, I can attempt to scrape it.

### Track 2: Research Comparable Non-Profit Impact Reports

Let me run Perplexity searches right now to understand what best-in-class 501(c)(3) arts organization impact reports typically contain, both in terms of content sections and design conventions.

### Track 3: Inventory Arterial's Existing Content & Data

This is where we map what Arterial *actually has* to report on. I already have substantial knowledge from the training data, but we need to be precise.

---

Let me start Tracks 2 and 3 now while you work on getting the Art21 PDF uploaded:

Tool: <PLUGIN_OUTPUT id="6a206435-a1ae-4ac9-a7c5-5a4cd2782638" type="string" />

Tool: <PLUGIN_OUTPUT id="31918be8-6934-4c12-9386-8aa337f8ef1b" type="string" />

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/579dbadc4d746ed6c005a17f01eae622","sources":[{"documentID":2673,"documentName":"Arterial Web Copy (Juergen).docx","sourceSummary":{"title":"Arterial Web Copy (Juergen).docx","description":"Arterial Web Copy (Juergen).docx","link":"Arterial Web Copy (Juergen).docx"},"chunks":[{"endOffset":2918,"startOffset":0}]},{"documentID":2682,"documentName":"Arterial_v2_100324.pdf","sourceSummary":{"title":"Arterial_v2_100324.pdf","description":"Arterial_v2_100324.pdf","link":"Arterial_v2_100324.pdf"},"chunks":[{"endOffset":5129,"startOffset":2412},{"endOffset":2912,"startOffset":0}]},{"documentID":23937,"documentName":"Arterial Becomes Fiscal Sponsor to Indie Arts Journalism Platform, NOT REAL ART","sourceSummary":{"title":"Arterial Becomes Fiscal Sponsor to Indie Arts Journalism Platform, NOT REAL ART","description":"https://arterial.org/not-real-art-brand/","image":"https://arterial.org/wp-content/uploads/2025/01/Arterial_Brand_Images_Events20190316-WEB_notrealart-conf-100_1400px.jpg","icon":{},"link":"https://arterial.org/not-real-art-brand/"},"chunks":[{"endOffset":5444,"startOffset":2457},{"endOffset":2957,"startOffset":0}]}]}</KB_QUERY_RESULT>

Assistant: Now let me pull the specific project accomplishments and metrics we have documented:

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/6d884043e97888e2f64335e3480c1133","sources":[{"documentID":24059,"documentName":"Arterial Grant Helps Complete Art Doc: The Underbelly Project","sourceSummary":{"title":"Arterial Grant Helps Complete Art Doc: The Underbelly Project","description":"https://arterial.org/underbelly-project-documentary/","image":"https://arterial.org/wp-content/uploads/2025/01/urbanexplorervic_underbelly_weownthenight_1.jpg","icon":{},"link":"https://arterial.org/underbelly-project-documentary/"},"chunks":[{"endOffset":2915,"startOffset":0}]},{"documentID":2682,"documentName":"Arterial_v2_100324.pdf","sourceSummary":{"title":"Arterial_v2_100324.pdf","description":"Arterial_v2_100324.pdf","link":"Arterial_v2_100324.pdf"},"chunks":[{"endOffset":5129,"startOffset":2412}]},{"documentID":24221,"documentName":"Arterial Supports Emmy Winning PBS Series Artbound","sourceSummary":{"title":"Arterial Supports Emmy Winning PBS Series Artbound","description":"https://arterial.org/arterial-announces-partnership-with-pbs-artbound-series/","image":"https://arterial.org/wp-content/uploads/2025/01/1719198592374-1.jpg","icon":{},"link":"https://arterial.org/arterial-announces-partnership-with-pbs-artbound-series/"},"chunks":[{"endOffset":2877,"startOffset":0}]},{"documentID":1633642,"documentName":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","sourceSummary":{"title":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":3}]},{"documentID":23938,"documentName":"ArtHousePitch_10-11-24_v2 copy (optimized).pdf","sourceSummary":{"title":"ArtHousePitch_10-11-24_v2 copy (optimized).pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":7}]}]}</KB_QUERY_RESULT>

Tool: <PLUGIN_OUTPUT id="42b99fc8-f094-4a91-9512-793e3d711646" type="string" />

Assistant: Let me grab the Art21 FY24 impact report directly and also look at how they present it on their web page:

Tool: <PLUGIN_OUTPUT id="95091391-6dfe-40f1-ba19-491dabf42bd0" type="string" />

Tool: <PLUGIN_OUTPUT id="d9ffb137-0fb3-4614-91e5-e2f44e5f1db1" type="string" />

Assistant: Now let me also look at a couple of the best interactive web-based reports for structural/UX inspiration:

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/e7b0c46ece4e624f64c739db66065b1c","sources":[{"documentID":2673,"documentName":"Arterial Web Copy (Juergen).docx","sourceSummary":{"title":"Arterial Web Copy (Juergen).docx","description":"Arterial Web Copy (Juergen).docx","link":"Arterial Web Copy (Juergen).docx"},"chunks":[{"endOffset":8265,"startOffset":7370}]},{"documentID":2682,"documentName":"Arterial_v2_100324.pdf","sourceSummary":{"title":"Arterial_v2_100324.pdf","description":"Arterial_v2_100324.pdf","link":"Arterial_v2_100324.pdf"},"chunks":[{"endOffset":5129,"startOffset":2412},{"endOffset":18265,"startOffset":16638}]},{"documentID":1633642,"documentName":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","sourceSummary":{"title":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":3}]},{"documentID":1741432,"documentName":"Arthouse Crowdfunding Press Release - June 1.pdf","sourceSummary":{"title":"Arthouse Crowdfunding Press Release - June 1.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":2}]}]}</KB_QUERY_RESULT>

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/b5a6d810e026979ff32bbfc665b8588f","sources":[{"documentID":24218,"documentName":"Arterial Celebrates Black Excellence in Classical Music","sourceSummary":{"title":"Arterial Celebrates Black Excellence in Classical Music","description":"https://arterial.org/classic-black/","icon":{},"link":"https://arterial.org/classic-black/"},"chunks":[{"endOffset":2936,"startOffset":0},{"endOffset":5387,"startOffset":2436}]},{"documentID":2695,"documentName":"Arterial_pitch_deck_042723.pdf","sourceSummary":{"title":"Arterial_pitch_deck_042723.pdf","description":"Arterial_pitch_deck_042723.pdf","link":"Arterial_pitch_deck_042723.pdf"},"chunks":[{"endOffset":15148,"startOffset":12163},{"endOffset":12663,"startOffset":9668}]},{"documentID":2682,"documentName":"Arterial_v2_100324.pdf","sourceSummary":{"title":"Arterial_v2_100324.pdf","description":"Arterial_v2_100324.pdf","link":"Arterial_v2_100324.pdf"},"chunks":[{"endOffset":12493,"startOffset":9512}]}]}</KB_QUERY_RESULT>

Assistant: Excellent. I now have a comprehensive picture of both the reference model (Art21) and the full inventory of Arterial's content. Here's the complete framework:

---

## Arterial Impact Report — Project Specification Framework

### 1. RECOMMENDED APPROACH (Phased)

**Phase 1: Research & Content Gathering** (what we're doing now)
**Phase 2: Specification Document (README.md + memory.md)** for the GitHub repo
**Phase 3: Content Authoring** (MD files in `/docs` or Airtable records)
**Phase 4: Claude Code Build** (Next.js + Vercel deployment)

---

### 2. REFERENCE MODEL: Art21 Impact Report Structure

Based on the Art21 FY24 report, their structure is:

| Section | Purpose | Arterial Equivalent |
|---|---|---|
| Mission & Vision | Framing statement | Arterial's 3 tenets + vision |
| Executive Director Letter | Personal leadership narrative | Scott Power's letter |
| Board/Trustee Letter | Governance voice | Joshua Wattles or advisory board |
| Digital Engagement / Reach Metrics | Quantitative proof of impact | Podcast downloads, web traffic, social reach, artist database size |
| Production Highlights | Featured work from the year | Underbelly Project, Artbound, Classic Black, Arthouse development |
| Education | Programs that serve learning | NOT REAL ART School (free courses), Classic Black educational sessions |
| Community | Network size, events, collaborations | 2,000+ artist database, First Fridays, grant program, NRA community |
| Staff & Board | Organizational credibility | Leadership bios |
| Donors & Supporters | Acknowledgment + transparency | Donor recognition (tiered) |
| Financial Statements | 501(c)(3) compliance + trust | Revenue/expense summary, 80/20 allocation model |

---

### 3. PROPOSED SECTION STRUCTURE FOR ARTERIAL IMPACT REPORT

Based on research across best-in-class nonprofit arts reports, here's the recommended structure adapted for Arterial:

#### **Section 0: Cover / Hero**
- Report title, fiscal year, Arterial logo, tagline "Amplify Art"
- Full-bleed image or video background

#### **Section 1: Mission & Tenets**
- Three tenets (Access, Underrepresentation, Media exposure grows art economy)
- Vision statement
- The 5 key insights (creatives contribute ~$2T, etc.)

#### **Section 2: Founder's Letter**
- Scott Power's year-in-review narrative
- Personal tone, sets the theme for the year

#### **Section 3: Year at a Glance — Key Metrics**
- Stat callouts (large typography, animated counters on scroll):
  - 2,000+ artists in database
  - 6 podcasts, 300+ hours of programming
  - 6 grant recipients/year at $2,000 each
  - $12,000 documentary grant (Underbelly Project)
  - 200 attendees at Miami Art Week premiere
  - PBS partnership (SoCal + Austin interest)
  - X First Friday exhibitions
  - X free courses via NRA School
  - 80% of donations → programming

#### **Section 4: Programs & Projects**
Each as a feature card or expandable section with image, description, and impact:

- **NOT REAL ART** — Fiscal sponsorship, podcast network, grant, school, exhibitions
- **The Underbelly Project** — $12K grant, documentary completion, Miami Art Week premiere
- **Artbound (PBS SoCal)** — Emmy Award-winning series, premiere event support, Austin PBS interest
- **Classic Black** — Ric'key Pageot / Steinway Artist, fiscal sponsorship, video series + podcast, educational program for schools
- **Arthouse** — Unscripted TV series in development, crowdfunding campaign
- **The Good Art** — Lowbrow art movement documentary in development
- **Artsville USA** — Digital platform acquisition, American contemporary arts & crafts
- **Arterial Radio** — Internet-based talk radio channel in development

#### **Section 5: NOT REAL ART — In Depth**
Sub-sections:
- Podcast Network (6 shows, 300+ hours)
- Grant Program (since 2019, 6 recipients/year, $2K each)
- First Friday Exhibitions
- Artist Database (2,000+)
- NRA School (free courses: licensing, copyright, branding, pitching, career)
- Q+ART Series
- Remote Video Series

#### **Section 6: Artist Community & Exhibitions**
- Highlight reel of selected artists
- Exhibition themes and featured works
- Quotes/testimonials from grant recipients
- Open call process

#### **Section 7: Distribution & Partnerships**
- Random Media partnership (streaming distribution)
- PBS SoCal / Austin PBS
- Potential distribution: Roku, Hulu, Netflix, SiriusXM

#### **Section 8: Leadership & Governance**
- Scott Power bio
- Joshua Wattles bio
- Additional team/advisory as applicable
- Crewest Studio relationship

#### **Section 9: Financial Summary**
- Visual chart: 80% programming / 20% admin
- Revenue sources
- Giving model: restricted, unrestricted, endowment
- Four fundable programs (Arthouse, Artsville USA, Classic Black, The Good Art)

#### **Section 10: Supporters & Donors**
- Tiered recognition
- Patron groups

#### **Section 11: Looking Ahead**
- Goals for next fiscal year
- Calls to action: Donate, Submit Art, Listen, Watch, Follow

---

### 4. PERPLEXITY RESEARCH PROMPTS

Use these prompts to gather additional data you don't already have:

**Prompt 1 — Macro Arts Economy Data:**
> "What is the total economic contribution of creative industries to the US and global economy in 2023-2024? Include Bureau of Economic Analysis data, NEA reports, and UNESCO Creative Economy reports. Provide specific dollar figures and employment numbers."

**Prompt 2 — Media Underrepresentation:**
> "What data exists on arts programming representation in mainstream US media? What percentage of broadcast, cable, and streaming content is dedicated to visual and performing arts? Include any studies from FCC, Nielsen, or academic sources."

**Prompt 3 — Public Arts Funding Trends:**
> "What are the current trends in US public funding for the arts? Include NEA budget history, state arts agency funding levels, and comparison to other countries as percentage of GDP. Cover 2020-2024."

**Prompt 4 — Nonprofit Arts Impact Benchmarks:**
> "What metrics do mid-size 501(c)(3) arts nonprofits typically report in impact reports? What are benchmark numbers for podcast listenership, grant programs, artist community size, and educational program reach for organizations with budgets under $5M?"

**Prompt 5 — Street Art Documentary Context:**
> "What is the cultural significance of The Underbelly Project in NYC street art history? Include NYT coverage, art world reception, and the importance of documentation for ephemeral art projects."

---

### 5. TECH STACK SPECIFICATION (for README.md)

```
Framework: Next.js (App Router)
Styling: Tailwind CSS
Deployment: Vercel
Content Source: Option A — /docs directory with .md files per section
               Option B — Airtable (if dynamic updates needed)
Animations: Framer Motion (scroll-triggered counters, fade-ins)
Image handling: Next/Image with optimized assets in /public
Charts: Recharts or Chart.js for financial visualizations
Build tool: Claude Code
```

### 6. FILE STRUCTURE (for the repo)

```
/arterial-impact-report
├── README.md                    # Project overview, tech stack, build instructions
├── memory.md                    # Claude Code persistent context and instructions
├── SPECIFICATIONS.md            # This document (full requirements)
├── /docs
│   ├── 00-cover.md
│   ├── 01-mission-tenets.md
│   ├── 02-founders-letter.md
│   ├── 03-year-at-a-glance.md
│   ├── 04-programs-projects.md
│   ├── 05-not-real-art.md
│   ├── 06-artist-community.md
│   ├── 07-distribution-partnerships.md
│   ├── 08-leadership.md
│   ├── 09-financial-summary.md
│   ├── 10-supporters-donors.md
│   └── 11-looking-ahead.md
├── /public
│   ├── /images                  # Hero images, headshots, art samples
│   └── /logos                   # Arterial, NRA, project logos
├── /src
│   ├── /app                     # Next.js App Router pages
│   ├── /components              # Reusable UI components
│   └── /lib                     # Markdown parser, Airtable client, etc.
├── package.json
└── tailwind.config.js
```

### 7. USER STORIES

| ID | As a... | I want to... | So that... |
|---|---|---|---|
| US-01 | Potential donor | See Arterial's mission and impact at a glance | I can quickly assess whether to support the organization |
| US-02 | Grant applicant (artist) | Understand what programs exist and who has been supported | I can determine if I should apply |
| US-03 | Board member / advisor | Share a professional impact report with prospective partners | I can use it as a credibility tool |
| US-04 | PBS / media partner | See Arterial's programming breadth and distribution plans | I can evaluate collaboration potential |
| US-05 | IRS / compliance reviewer | Access financial statements and governance info | I can verify 501(c)(3) compliance |
| US-06 | General public / art enthusiast | Browse the programs and find content to watch/listen to | I can engage with Arterial's programming |
| US-07 | Arterial staff | Update report content annually without code changes | I can produce a new report each fiscal year |

---

### 8. NEXT STEPS

1. **Upload the Art21 PDF** to the knowledge base so I can do a granular layout and design pattern analysis (page-by-page structure, typography hierarchy, color usage, image-to-text ratios, etc.)

2. **Run the 5 Perplexity research prompts** above — I can do these for you right now if you want, or you can run them yourself for more control over the outputs.

3. **Confirm content source**: MD files in `/docs` vs. Airtable. My recommendation is MD files for v1 (simpler, faster to build, easier for Claude Code to work with) with Airtable as a v2 upgrade if annual updating becomes a workflow need.

4. **Identify missing data**: Specifically, you'll need Scott to provide or confirm:
   - Actual podcast download/listener numbers
   - Website traffic data
   - Total grants awarded to date (cumulative)
   - Total number of First Friday exhibitions held
   - Any financial data he's willing to make public
   - His founder's letter text

5. **Gather visual assets**: Logos, hero images, artist work samples, headshots, event photos.

Would you like me to run those Perplexity research prompts now? And should I proceed with any other specific analysis?

User: I've uploaded the report to the Knowledge Base. Can you find it? 

Assistant: 

Let me search for it in the knowledge base.

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/7913964aef6b9ea446e2e05a33f49e45","sources":[{"documentID":2673,"documentName":"Arterial Web Copy (Juergen).docx","sourceSummary":{"title":"Arterial Web Copy (Juergen).docx","description":"Arterial Web Copy (Juergen).docx","link":"Arterial Web Copy (Juergen).docx"},"chunks":[{"endOffset":2918,"startOffset":0},{"endOffset":5376,"startOffset":2418}]},{"documentID":23938,"documentName":"ArtHousePitch_10-11-24_v2 copy (optimized).pdf","sourceSummary":{"title":"ArtHousePitch_10-11-24_v2 copy (optimized).pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":7}]},{"documentID":2682,"documentName":"Arterial_v2_100324.pdf","sourceSummary":{"title":"Arterial_v2_100324.pdf","description":"Arterial_v2_100324.pdf","link":"Arterial_v2_100324.pdf"},"chunks":[{"endOffset":2912,"startOffset":0}]},{"documentID":1633642,"documentName":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","sourceSummary":{"title":"Arthouse Crowdfunding Comms Framework - Google Docs.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":3}]}]}</KB_QUERY_RESULT>

Assistant: That search returned only existing Arterial documents, not the Art21 PDF. Let me try more specific queries:

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/0c08aa44c3d400db788ce2a3ae7f6b63","sources":[{"documentID":19309492,"documentName":"Art21-Impact-Report-FY24.pdf","sourceSummary":{"title":"Art21-Impact-Report-FY24.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":3},{"pageNumber":14},{"pageNumber":7},{"pageNumber":27},{"pageNumber":2}]}]}</KB_QUERY_RESULT>

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/fa1e1c1d4fadb64c8d813f76211ec03c","sources":[{"documentID":19309492,"documentName":"Art21-Impact-Report-FY24.pdf","sourceSummary":{"title":"Art21-Impact-Report-FY24.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":24},{"pageNumber":25},{"pageNumber":26},{"pageNumber":23},{"pageNumber":20}]}]}</KB_QUERY_RESULT>

Assistant: Found it. The **Art21-Impact-Report-FY24.pdf** is in the knowledge base (document ID 19309492). I can now extract its full structure. Let me get the remaining sections:

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/3a16aec3e30870cc06de0605f0879686","sources":[{"documentID":19309492,"documentName":"Art21-Impact-Report-FY24.pdf","sourceSummary":{"title":"Art21-Impact-Report-FY24.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":15},{"pageNumber":18},{"pageNumber":19},{"pageNumber":17},{"pageNumber":16}]}]}</KB_QUERY_RESULT>

Tool: <KB_QUERY_RESULT>{"segmentKey":"knowledge-base/18d6b10fa058861b38bb7daee7d8f49e","sources":[{"documentID":19309492,"documentName":"Art21-Impact-Report-FY24.pdf","sourceSummary":{"title":"Art21-Impact-Report-FY24.pdf","description":"From Uploads","link":null},"chunks":[{"pageNumber":18},{"pageNumber":10},{"pageNumber":12},{"pageNumber":13},{"pageNumber":5}]}]}</KB_QUERY_RESULT>

Assistant: I now have the full Art21 FY24 Impact Report extracted from the knowledge base. Here's my complete structural analysis:

---

## Art21 FY24 Impact Report — Complete Structural Analysis

### Document Identity
- **File:** Art21-Impact-Report-FY24.pdf (document ID: 19309492)
- **Fiscal Year:** October 1, 2023 – September 30, 2024
- **Approximate page count:** ~50 pages
- **Format:** PDF, designed for both print and digital download

---

### Page-by-Page Structure

| Pages | Section | Content Type | Layout Pattern |
|---|---|---|---|
| Cover | Cover | Full-bleed production still, title, year | Single image, minimal text |
| p.1 | Inside cover | Production still caption | Image-dominant |
| p.2 | Table of Contents | Full TOC listing all sections | Single-column text list |
| p.2 | Mission & Vision | Mission statement + vision statement | Text block, likely large type, with a production still below |
| pp.3–4 | Letter from Executive Director (Tina Kukielski) | ~400 words, personal narrative about "the unknown" as thematic thread | Long-form text with signature, small portrait, 1 production still |
| pp.5–6 | Letter from Board of Trustees (Bill Gautreaux) | ~500 words, perspective on growth, digital presence, film library highlights | Same pattern as ED letter, 3 production stills in margin/sidebar |
| pp.7–8 | **Digital Engagement** | Key metrics: 11 new films, 1.9M sessions, 29M+ impressions, 26M+ social video views | **Large stat callouts** (big numbers), likely infographic treatment |
| pp.9–10 | Filming Locations | Interactive-style map showing 20 filming locations across 4 continents, 6 languages | **Map graphic** with numbered legend, small location photos |
| pp.11–12 | Licensing info | Content licensed in 24 cities, 11 countries | QR code, supplementary to map |
| pp.13–14 | **Curatorial** | Narrative about studio visits, global scope of curatorial work | Text + production stills |
| p.15 | READ | Online editorial/article platform mention | Brief text |
| pp.16–18 | **Production** overview | 6 Extended Play films + 5 New York Close Up films + Season 12 production started | Narrative text, behind-the-scenes photos (4 stills in grid) |
| pp.19–20 | Festival Highlights + Filmmaker Highlight | List of festival selections (PalmSprings, BlackStar, DOC NYC, etc.) + spotlight on Andrea Yu-Chieh Chung | Likely a grid/list of festival logos + portrait + bio text |
| pp.21–22 | **Art in the Twenty-First Century** | Season 12 details: 3 episodes, 12 artists, international scope. "The only series on television in the US to focus exclusively on contemporary visual art." | Hero statement in large type, behind-the-scenes photo |
| pp.23–24 | **Extended Play** | 6 film titles listed, nearly 50 festival selections noted | Film title list with thumbnail stills, pull quote |
| pp.25–26 | **New York Close Up** | 5 film titles listed, focus on early-career NYC artists | Same layout: title list + thumbnails |
| pp.27–28 | **Education** intro + Art21 Educators | Yearlong professional development program, Summer Institute in NYC | Narrative + event photo |
| pp.29 | Art21 Ambassadors | Partnership with SFMOMA, Barry McGee event, ~100 educators | Event photos |
| pp.30–31 | Teaching with Contemporary Art / Resources | Educator Guides (6 released), 10 educator-authored articles, playlists | **Educator Guide sample pages** embedded as visual elements — these are essentially mini artist profiles with bio, media/materials, key words, teaching connections, and related artists |
| pp.33–34 | **Public Programs** | Programs in Chicago, Atlanta, NYC. Spotlight: Big Night of Shorts (Sept 2024), Naudline Pierre at The Met Cloisters, virtual event with SETI Institute | Event photos, program spotlight callout box |
| pp.35–36 | **Community: A New Era** | Spring Gala raised $675K. "Art21 for Everyone" campaign: goal to grow budget from $2.1M (FY20) to $4M (FY26). Key achievements listed as bullet points: 50% more educational programs, new Lifelong Learners program (65+), digitized Seasons 1–2 raw footage, added closed captioning/descriptive audio | **Campaign progress narrative** with bullet-point achievements, quote from supporter, gala photo |
| pp.37–38 | **Staff & Board of Trustees** | Full staff list (15 names with titles) + Board list (17+ names with roles) + In Memoriam (founder Susan Sollins) + interns | Two-column layout, names and titles |
| pp.39–40 | **Filmmakers** | Comprehensive list of all filmmakers across all three series | Multi-column name list |
| pp.41–42 | **Committees + Patron Groups** | Three patron tiers described: Insiders (young collectors), Studio Circle (art/film enthusiasts), Contemporary Council (invitation-only collectors). Event highlights listed | Descriptive paragraphs per tier + event highlight boxes with photos |
| pp.43–48 | **Donors** | Tiered donor lists: $100K+, $50K–99K, $25K–49K, $15K–24K, $10K–14K, $5K–9K, $1K–4K, $250–999, $1–249, In-Kind | **Multi-column name lists** organized by giving level, standard nonprofit format |
| pp.49–50 | **Financial Statements** | Statement of Activities (revenue $4,497,439 / expenses $3,643,252 / change in net assets +$854,187 / ending net assets $9,050,482). Two pie charts: Revenue breakdown (Foundations 48%, Individuals 25%, Special Events 20%, Government 4%, Contributed Nonfinancial Assets 2%, Corporate 1%) and Expense breakdown (Program Services 76%, Fundraising 15%, Management/General 9%) | **Pie chart pair** + line-item table |
| Back cover | Closing / CTA | "Your support makes this possible. DONATE TODAY" + QR code + contact info (address, email, phone, newsletter URL) | Minimal, production still background, QR code |

---

### Design Patterns Observed (from text extraction)

1. **Consistent header/footer:** Every page spread includes section name + "Art21" + "Impact Report" + page number
2. **Large stat numbers:** Digital engagement section uses oversized typography for metrics (1.9M, 29M, 26M)
3. **Pull quotes:** Supporter/stakeholder quotes set off in large italic type with attribution (Pool-Eckert, Zabor, Power quotes all appear this way)
4. **Production stills as primary imagery:** Every section uses behind-the-scenes photography, not polished gallery shots
5. **Educator Guide embeds:** Full educator guide pages appear as visual elements within the Education section, functioning as both content and design texture
6. **Map graphic:** A custom illustrated world map with numbered location pins
7. **Pie charts:** Clean, simple two-chart financial summary
8. **Two-column donor lists:** Standard tiered format
9. **QR codes:** Used for licensing info and donation CTA

---

### What This Means for the Arterial Report

Here's a direct mapping of what to replicate, adapt, or skip:

**Replicate directly:**
- Cover → hero section with full-bleed image
- Mission/Vision → concise, prominently placed
- Founder's letter → Scott Power's narrative
- Key metrics section with large animated counters
- Program spotlights with image + description + impact
- Financial summary with pie charts (80/20 allocation)
- Tiered donor recognition
- Closing CTA with donate link

**Adapt (Arterial doesn't have the equivalent yet, but should build toward):**
- Art21's "Filming Locations" map → Arterial's geographic reach map (LA, NYC, Asheville, Miami Art Week, etc.)
- Art21's festival selection list → Arterial's distribution/partnership list (Random Media, PBS SoCal, Austin PBS)
- Art21's Educator Guides → Arterial/NRA School course spotlights
- Art21's patron groups → Arterial's giving model (restricted, unrestricted, endowment)

**Skip (not applicable to Arterial at this stage):**
- Extensive filmmaker lists (Art21 has dozens; Arterial has a handful of key production partners)
- Committee structures (Arterial's governance is simpler)
- The depth of Art21's 24-year institutional history

---

### Immediate Next Steps

1. **Do you want me to draft the SPECIFICATIONS.md file** based on everything above, formatted for the GitHub repo and ready for Claude Code to consume?

2. **Do you want me to run the 5 Perplexity research prompts** I outlined earlier to gather the macro arts economy data, media underrepresentation stats, and public funding trends that would populate Arterial's "why we exist" framing?

3. **Should I draft the memory.md file** with Claude Code-specific instructions, referencing the tech stack (Next.js App Router, Tailwind, Framer Motion, Vercel)?

Tell me which of these to prioritize and I'll produce them.

User: Now I think I'd like to keep chatting on this for a bit. I think one of the things is that I would like for this tool to be available to Scott to basically make changes and edits, etc., but that might be challenging. He is very visual and would want to upload images, etc., etc. I don't know how we could generate this, perhaps using appropriate imagery from lookups on an API that I have with Replicate to generate some images, but also using Unsplash, which I have used in several other projects and I have an API key for.

The idea here would be to basically pre-populate the entire narrative and the entire PDF report with the graphics, data, and background imagery, even if it means that that imagery isn't directly coming from our material or our own image libraries. However, we also have Dropbox integration and files stored elsewhere with a lot of imagery for both a not real art website and build-outs for Arterial, etc. For example, if I put together a large folder of hundreds of images to choose from, then could an AI designer be smart enough to pick the correct ones? Or is there a separate process where the image descriptions could be added somehow so that a PDF generator or a Report Generator would be smart enough to pick images that are relevant, at least as a starting point?

The other thing that I need to mention is that Scott is very undisciplined in terms of preparing any images for the web. That means that he will upload or drag and drop a 20 MB image into a spot that needs to load on the web. That is unreasonable for this sort of thing. There needs to be image compression or a utility to basically web-optimize the images that are being chosen so that the load speed for this report is not inadequately affected. This again sort of comes down to whether we have to build an online database or something like that for imagery to select from.

In an ideal world, I could see that there might be an Airtable or Supabase that has the images, has full-res, half-res, thumbnail versions of it, does analysis of the image, and has descriptions and tags of the subject matter so that when the report runs it could select the right ones. I know this is a little more ambitious, but you see where I'm going with this. The second challenge is that when Scott then views the report, the text of each page needs to be editable for him somehow, and the images need to be replaceable somehow so that he can swap and put different images in place. Just think about that and add it as a sort of large set of requirements to this project as we continue to think about it. 

Assistant: 

This is a significant expansion of scope, but it's practical and I can see exactly where you're headed. Let me think through this systematically and lay out the requirements as concrete specifications.

---

## Expanded Requirements: Image Management + Editorial CMS Layer

### The Core Problem

You're building two things, not one:

1. **A web-based impact report** (the public-facing output)
2. **An editorial/authoring tool** that lets Scott (a non-technical, visually-oriented user) manage the content and images of that report without touching code

These are fundamentally different concerns and need to be addressed separately in the architecture, even if they share the same codebase and deployment.

---

### REQUIREMENT BLOCK A: Image Asset Pipeline

#### A1. Image Storage & Processing

The system needs a central image repository that:

- Accepts raw uploads of any size (Scott's 20MB files)
- Automatically generates optimized derivatives on upload:
  - **Full-res archive** (original, stored but never served to web)
  - **Web-optimized** (max 2000px wide, WebP format, quality 80, typically 100-300KB)
  - **Thumbnail** (400px wide, WebP, quality 75, typically 20-50KB)
  - **Blur placeholder** (20px wide base64-encoded, for progressive loading)
- Stores all four versions with a reference back to the original

**Implementation options (ranked by complexity):**

| Option | Pros | Cons |
|---|---|---|
| **Cloudinary** (recommended) | Automatic transforms via URL params, free tier generous, no custom processing code needed, has an upload widget Scott can use | Third-party dependency, costs scale with usage |
| **Vercel Blob + Sharp** | Native to your deployment stack, Sharp handles compression at build/upload time | You have to build the processing pipeline yourself |
| **Supabase Storage + Edge Functions** | You already know Supabase, can run Sharp in edge functions on upload | More moving parts, storage costs |
| **Airtable attachments** | Scott already knows Airtable (if he uses it) | Airtable attachment URLs expire, no built-in transforms, not designed for this |

**My recommendation:** Cloudinary. It solves the "Scott drags in a 20MB TIFF" problem at the infrastructure level. Every image gets a base URL, and you append transform parameters (`/w_2000,f_webp,q_80/`) to get the derivative you need. No pre-processing required. The Next.js `<Image>` component can work with Cloudinary's loader directly.

#### A2. Image Metadata & Tagging

Each image in the repository needs structured metadata:

```
{
  id: string,
  cloudinary_public_id: string,
  original_filename: string,
  uploaded_by: string,
  uploaded_at: datetime,
  
  // Descriptive metadata
  title: string,
  description: string,           // human-written or AI-generated
  ai_description: string,        // auto-generated on upload
  tags: string[],                 // e.g., ["event", "miami", "underbelly-project", "screening"]
  category: enum,                 // "event-photo", "artwork", "headshot", "production-still", "logo", "background"
  
  // Relational metadata
  related_program: string,        // "classic-black", "underbelly", "arthouse", "nra-grant", etc.
  related_artist: string,
  related_event: string,
  
  // Technical metadata (auto-extracted)
  width: number,
  height: number,
  aspect_ratio: string,
  dominant_color: string,         // for placeholder/background tinting
  file_size_original: number,
  
  // Usage tracking
  used_in_sections: string[],     // which report sections currently reference this image
  is_approved: boolean            // Scott has reviewed and approved for use
}
```

**Where this metadata lives:** This is where Airtable or Supabase comes in — not for the image files themselves (Cloudinary handles that), but for the metadata catalog. I'd lean toward **Supabase** here because:
- It gives you a proper relational database (Postgres)
- The free tier is sufficient
- You can build a simple admin UI against it
- Airtable's API rate limits (5 requests/second) become a problem when loading a report with 40+ images

However, if Scott already uses Airtable and is comfortable with its interface, you could use Airtable as the editorial interface and sync to Supabase, or just use Airtable directly with aggressive caching.

#### A3. AI Image Analysis on Upload

When an image is uploaded, automatically run:

1. **Cloudinary's AI tagging** (built-in, returns tags like "person", "outdoor", "painting", "crowd")
2. **A vision model call** (via Replicate or OpenAI's vision API) to generate:
   - A 1-2 sentence description
   - Suggested tags mapped to your taxonomy (program names, event names, categories)
   - A relevance score against each report section

This means Scott can drag-and-drop 50 images into the system and the system pre-tags them all. He then reviews/corrects, rather than writing metadata from scratch.

#### A4. AI Image Selection for Report Sections

Each report section has a defined `image_spec` in its markdown or data record:

```yaml
# In the section's .md frontmatter or Airtable/Supabase record:
image_slots:
  - slot_id: "hero"
    required: true
    preferred_category: "event-photo"
    preferred_tags: ["miami", "underbelly-project", "screening"]
    preferred_orientation: "landscape"
    preferred_aspect_ratio: "16:9"
    min_width: 1600
  - slot_id: "sidebar-portrait"
    required: false
    preferred_category: "headshot"
    preferred_tags: ["scott-power"]
    preferred_orientation: "portrait"
```

At build time (or in the CMS UI), the system:
1. Queries the image database filtered by the slot's criteria
2. Ranks matches by tag overlap, category match, and aspect ratio fit
3. Presents the top 3-5 options for that slot
4. Scott picks one, or the system auto-selects the top match

**For the initial pre-populated version** (before Scott has uploaded his own images), you fill these slots with:
- Unsplash API images (using the tag-based search endpoint you already have access to)
- Replicate-generated images (for abstract/artistic backgrounds where stock photos feel wrong)
- Placeholder images with clear "REPLACE THIS" overlay text

---

### REQUIREMENT BLOCK B: Editorial / CMS Layer for Scott

#### B1. What Scott Needs to Edit

For each report section, Scott needs to be able to:

| Content Type | Edit Method |
|---|---|
| **Headline text** | Inline text editing (click to edit) |
| **Body text** | Rich text editor (bold, italic, links — no code) |
| **Pull quotes** | Editable text field + attribution field |
| **Stat numbers** | Simple number input (e.g., "2000" for artist count) |
| **Stat labels** | Text field (e.g., "Artists in our database") |
| **Images** | Click to open image picker → browse library or upload new |
| **Image captions** | Text field below each image |
| **Section order** | Drag-and-drop to reorder sections |
| **Section visibility** | Toggle to show/hide a section (for drafting) |

#### B2. What Scott Should NOT Have Access To

- CSS / styling controls (these are locked to the design system)
- Layout structure changes (column counts, grid, spacing)
- Font choices, color palette
- Component code
- Deployment settings

This is important. The design integrity of the report must be preserved regardless of what Scott edits.

#### B3. Implementation Options for the CMS

| Option | How it works | Pros | Cons |
|---|---|---|---|
| **Tina CMS** (recommended) | Git-backed headless CMS with visual editing, built specifically for Next.js. Scott edits in a visual overlay on the actual rendered page. Changes commit to the repo or save to a data layer. | Scott sees the real page while editing. Open source. Designed for Next.js. No separate admin UI to build. | Learning curve for setup. Git-based workflow may confuse Scott (can be abstracted away). |
| **Sanity.io** | Separate studio UI (sanity.io/studio) where Scott edits structured content. Next.js fetches via API. | Very polished editing experience. Great image handling. Real-time preview. | Separate interface from the report itself. Free tier has limits. Another service to manage. |
| **Payload CMS** | Self-hosted headless CMS, can run alongside Next.js. | Full control. No vendor lock-in. Rich admin UI. | You have to host it. Heavier setup. |
| **Custom admin with Supabase** | Build a simple /admin route in the Next.js app with forms that write to Supabase. | Fully custom to Scott's needs. No extra dependencies. | You build everything from scratch. More dev time. |
| **Airtable as CMS** | Scott edits in Airtable (which he may already know). Next.js reads from Airtable API at build time or via ISR. | Familiar spreadsheet-like interface. Easy for non-technical users. Image attachments supported. | API rate limits. Attachment URLs expire (need to proxy/cache). Not a real CMS — no preview. |

**My recommendation:** **Tina CMS** if Scott can handle editing on the rendered page (most intuitive for a visual person), or **Airtable** if he needs the simplest possible entry point and you handle the preview/rendering layer.

#### B4. Image Replacement Workflow (for Scott)

When Scott clicks on an image in the report:

1. **A modal opens** showing:
   - Current image
   - "AI Suggested" alternatives (3-5 images from the library matching the slot's criteria)
   - "Browse Library" button → opens full image grid, filterable by tags/category
   - "Upload New" button → drag-and-drop or file picker → auto-processes → adds to library → selects it

2. **On selection:**
   - The slot updates immediately in preview
   - The metadata record updates the `used_in_sections` field
   - Cloudinary serves the correct derivative for the slot dimensions

3. **No resizing, cropping, or optimization is required from Scott.** The system handles all of that via Cloudinary transforms and Next.js `<Image>` component.

---

### REQUIREMENT BLOCK C: Pre-Population Strategy

For the v1 launch, before Scott has supplied all final assets:

#### C1. Text Content
- Pre-populate from the existing training data (Arterial web copy, press releases, project descriptions)
- I can draft all 12 section markdown files based on what we've already gathered
- Every text block is tagged with `[DRAFT — NEEDS SCOTT'S REVIEW]` or similar

#### C2. Images — Fallback Hierarchy

For each image slot, the system checks in order:

1. **Scott's approved selection** (from the image library) → use this
2. **AI-selected match from uploaded library** (tagged but not yet reviewed) → use this with a subtle "unreviewed" badge
3. **Unsplash API result** matching the slot's tags → use this with "Placeholder — Unsplash" attribution text
4. **Replicate-generated image** (for abstract/artistic backgrounds) → use this with "AI Generated — Replace" badge
5. **Solid color block** using Arterial's brand palette with section title overlay → last resort

This means the report always renders fully, even with zero custom images uploaded.

#### C3. Data/Metrics
- Pre-populate with confirmed numbers from training data (2,000+ artists, 6 podcasts, 300+ hours, $12K Underbelly grant, 200 Miami attendees, etc.)
- Flag any numbers that need verification with `[VERIFY]`

---

### REQUIREMENT BLOCK D: Build & Deployment

#### D1. Revised Tech Stack

```
Framework:          Next.js 14+ (App Router)
Styling:            Tailwind CSS
Animation:          Framer Motion (scroll-triggered counters, fade-ins, parallax)
CMS:                Tina CMS (or Airtable — decision needed)
Image hosting:      Cloudinary (upload, transform, serve)
Image metadata DB:  Supabase (Postgres) or Airtable
Auth (admin):       Supabase Auth or NextAuth (so only Scott can edit)
Deployment:         Vercel
Image generation:   Replicate API (fallback/artistic backgrounds)
Stock images:       Unsplash API (fallback/placeholder)
PDF export:         Optional v2 — Puppeteer or @react-pdf/renderer
Build tool:         Claude Code
```

#### D2. Revised File Structure

```
/arterial-impact-report
├── README.md
├── memory.md
├── SPECIFICATIONS.md
├── /docs                          # Markdown content files
│   ├── 00-cover.md
│   ├── ...
│   └── 11-looking-ahead.md
├── /public
│   └── /logos
├── /src
│   ├── /app
│   │   ├── page.tsx               # Main report (public view)
│   │   ├── /admin                 # Scott's editing interface
│   │   │   ├── page.tsx
│   │   │   └── /api               # Upload, save, image-select endpoints
│   │   └── layout.tsx
│   ├── /components
│   │   ├── /report                # Report section components
│   │   ├── /editor                # Inline editing components
│   │   ├── /image-picker          # Image selection modal
│   │   └── /ui                    # Shared UI primitives
│   ├── /lib
│   │   ├── cloudinary.ts          # Upload, transform, URL generation
│   │   ├── supabase.ts            # Image metadata CRUD
│   │   ├── unsplash.ts            # Fallback image search
│   │   ├── replicate.ts           # AI image generation
│   │   ├── image-ai.ts            # Vision API for auto-tagging
│   │   ├── markdown.ts            # MD parser for content files
│   │   └── content.ts             # Content fetching layer (MD or CMS)
│   └── /types
│       ├── report.ts              # Section, ImageSlot, Metric types
│       └── image.ts               # Image metadata types
├── /scripts
│   ├── seed-images.ts             # Bulk import from Dropbox folder
│   ├── analyze-images.ts          # Run AI tagging on all uploaded images
│   └── generate-placeholders.ts   # Fetch Unsplash/Replicate for empty slots
├── package.json
├── tailwind.config.js
└── .env.local                     # API keys: Cloudinary, Supabase, Unsplash, Replicate
```

---

### REQUIREMENT BLOCK E: Dropbox Bulk Import

You mentioned Dropbox integration with existing image folders. A one-time (or periodic) import script:

1. Authenticates with Dropbox API
2. Scans a specified folder (e.g., `/Arterial/Impact Report Images/`)
3. For each image:
   - Downloads to temp storage
   - Uploads to Cloudinary (which handles optimization)
   - Runs AI vision analysis
   - Creates a metadata record in Supabase/Airtable with auto-generated tags and description
4. Logs results: "Imported 247 images. 189 auto-tagged successfully. 58 need manual review."

Scott can then go into the admin UI and review/tag the flagged ones.

---

### Open Decisions Needed

Before the spec is finalized, you and Scott need to decide:

| Decision | Option A | Option B | My Lean |
|---|---|---|---|
| CMS approach | Tina CMS (visual, on-page editing) | Airtable (spreadsheet editing, separate from site) | Tina if Scott can adapt; Airtable if he can't |
| Image metadata store | Supabase | Airtable | Supabase (more robust, no rate limits) |
| Image hosting | Cloudinary | Vercel Blob + Sharp | Cloudinary (handles Scott's oversized files automatically) |
| Auth | Supabase Auth | NextAuth | Supabase Auth (simpler if already using Supabase) |
| Content source (v1) | Markdown files in repo | Supabase/Airtable records | Markdown for v1, migrate to DB if needed |
| PDF export needed? | Yes (v2) | No | Defer to v2 |

---

### What I Can Do Next

1. **Draft the 12 markdown content files** (`/docs/00-cover.md` through `11-looking-ahead.md`) using all the Arterial data I've extracted — these would be the pre-populated narrative content

2. **Draft SPECIFICATIONS.md** — the complete requirements document incorporating everything from both our conversations, formatted for the GitHub repo

3. **Draft memory.md** — Claude Code instructions including tech stack, file structure, component patterns, and design constraints derived from the Art21 analysis

4. **Run the Perplexity research prompts** to gather macro data (arts economy, media underrepresentation, public funding) that would strengthen the "why Arterial matters" sections

5. **Draft the Supabase schema** for the image metadata table

Which of these do you want first?

User: There could also be a world in which the entire system is simply vibe-coded using Claude Code, and an entire website is put together with content and images based on Claude Code's best judgment. Then let Scott vibe code any adjustments and changes. If he wants to change the layout or look and feel or replace certain images and backgrounds, perhaps there could be a utility for him to just specify or drag an image into the conversation, and then let Claude Code make that and apply that change on a page-by-page basis. Perhaps that would simplify things. 

Assistant: 

You're right — this dramatically simplifies the architecture. Let me think through what this actually means in practice.

---

## The Vibe-Coded Approach: What Changes

Instead of building a CMS, image pipeline, metadata database, and admin UI, you build **one thing**: a well-structured Next.js site that Claude Code can modify on demand.

The editing interface *is* Claude Code itself. Scott describes what he wants in natural language, optionally drags in an image, and Claude Code makes the change directly in the codebase.

This eliminates:
- Tina CMS / Sanity / any CMS layer
- Supabase or Airtable for image metadata
- The image picker modal and admin UI
- Auth system for editing
- The entire `/admin` route

What remains:
- Next.js + Tailwind + Framer Motion site deployed on Vercel
- Cloudinary (still needed — Scott's 20MB files still need to be served properly on the web)
- The content files (markdown or directly in components)
- A well-structured `memory.md` that teaches Claude Code the project's conventions

---

## How Scott's Editing Workflow Would Actually Work

### Scenario 1: Scott wants to change text

Scott opens Claude Code (or a Claude interface connected to the repo) and says:

> "On the Programs section, change the Underbelly Project description to: 'Arterial awarded a $12,000 grant enabling the completion of this 15-year documentary project. The film premiered at Wynwood Walls during Miami Art Week on December 1, 2024.'"

Claude Code opens the relevant file, finds the Underbelly section, replaces the text, commits. Vercel auto-deploys. Done.

### Scenario 2: Scott wants to replace an image

Scott drags an image into the Claude Code conversation and says:

> "Use this image as the hero background on the Underbelly Project section."

Claude Code needs to:
1. Upload the image to Cloudinary (via API call or CLI)
2. Get back the Cloudinary URL
3. Update the component/content file to reference the new URL
4. Commit and deploy

**This is where the one real infrastructure dependency remains.** Claude Code can't serve a 20MB raw file directly from the `/public` folder without killing page load. So you still need *some* image optimization layer. Cloudinary is the simplest because Claude Code can upload via their REST API or Node SDK and get back a URL that auto-optimizes.

**Alternative:** If you want zero external services, you could use Next.js `<Image>` with `next/image` optimization (which Vercel provides natively). Scott's images go into `/public/images/`, and Next.js handles resizing/WebP conversion at request time. The downside is that `/public` gets bloated with 20MB originals, and the first load of each image is slow while Vercel generates the optimized version. But it works without any API keys.

### Scenario 3: Scott wants to change layout or look

> "Make the financial section use a dark background with white text. Put the two pie charts side by side on desktop and stacked on mobile."

Claude Code modifies the Tailwind classes and component structure. This is straightforward vibe coding.

### Scenario 4: Scott wants a different background image but doesn't have one

> "I don't like the background on the Mission section. Can you find something more abstract and painterly, maybe in blues and greens?"

Claude Code could:
- Search Unsplash via API and present options (if you wire up a simple script)
- Generate one via Replicate
- Or simply suggest: "I've updated it with this Unsplash image: [URL]. Take a look and let me know if you want something different."

### Scenario 5: Scott wants to add a new section

> "Add a section about Arterial Radio between the Programs section and the Artist Community section. It should mention that it's an internet-based talk radio channel dedicated to the arts, currently in development. Use a dark gradient background."

Claude Code creates a new component, adds it to the page layout, populates the content. Standard vibe coding.

---

## What the memory.md Needs to Contain for This to Work

The `memory.md` becomes the single most important file in the project. It needs to be comprehensive enough that *any* Claude Code session (whether initiated by you or Scott) produces consistent results. Here's what it must cover:

### 1. Project Identity
```
This is the Arterial.org FY2024 Impact Report.
Arterial is a 501(c)(3) non-profit media organization dedicated to human creativity.
The report is a single-page scrolling website deployed on Vercel.
```

### 2. Tech Stack & Conventions
```
- Next.js 14+ App Router
- Tailwind CSS (no custom CSS files)
- Framer Motion for scroll animations
- TypeScript throughout
- Images served via Cloudinary (account: [account-name])
  - Upload via: npx cloudinary upload [filepath] (or Node SDK)
  - All image URLs follow pattern: https://res.cloudinary.com/[cloud-name]/image/upload/[transforms]/[public-id]
  - Default transforms for hero images: w_1920,f_auto,q_80
  - Default transforms for inline images: w_1200,f_auto,q_80
  - Default transforms for thumbnails: w_400,f_auto,q_75
- If no Cloudinary setup exists, place images in /public/images/ and use next/image component
  - IMPORTANT: Run `sharp` compression script before committing large images
```

### 3. Design System
```
Color palette:
  - Primary: [Arterial brand colors — need from Scott]
  - Dark backgrounds: #0a0a0a, #1a1a1a
  - Light backgrounds: #fafafa, #ffffff
  - Accent: [TBD]
  
Typography:
  - Headings: [Font family — need from Scott/brand guidelines]
  - Body: [Font family]
  - Stat numbers: text-6xl md:text-8xl font-bold
  - Pull quotes: text-2xl italic
  
Layout rules:
  - Max content width: max-w-7xl mx-auto
  - Section padding: py-20 md:py-32
  - Each section is a full-viewport-height (or near) block
  - Alternate between light and dark background sections
  - Images use rounded-lg or rounded-none depending on context
  
Animation conventions:
  - Sections fade in on scroll (Framer Motion whileInView)
  - Stat counters animate from 0 to value over 1.5s when in view
  - No animation should be gratuitous or distracting
```

### 4. Content Structure
```
The report consists of 12 sections rendered in order on a single page:

00-cover: Full-screen hero with Arterial logo, report title, fiscal year
01-mission: Three tenets, vision statement, five key insights
02-founders-letter: Scott Power's narrative letter
03-year-at-a-glance: Key metrics displayed as large animated counters
04-programs: Card grid of all programs (NRA, Underbelly, Artbound, Classic Black, Arthouse, The Good Art, Artsville USA, Arterial Radio)
05-not-real-art: Detailed section on NRA ecosystem (podcasts, grant, school, exhibitions, artist database)
06-artist-community: Featured artists, First Fridays, open calls
07-distribution: Random Media, PBS partnerships, streaming plans
08-leadership: Scott Power, Joshua Wattles bios
09-financial: 80/20 allocation, revenue/expense visualization
10-supporters: Tiered donor recognition
11-looking-ahead: Goals, CTA, donate link

Each section's content is stored in /src/data/sections/ as individual .ts files
exporting a typed object with: title, subtitle, body (MDX or JSX), images[], metrics[], quotes[]
```

### 5. Image Handling Instructions for Claude Code
```
When the user provides a new image:
1. If Cloudinary is configured: upload via SDK, use returned URL
2. If not: save to /public/images/[section-name]/, run compression:
   - Install sharp if not present
   - Resize to max 2000px wide
   - Convert to WebP
   - Quality 80
   - Save as [descriptive-name].webp
3. Update the relevant section's data file with the new image path
4. Always use next/image component with width, height, and alt text

When the user asks for a placeholder or stock image:
1. Search Unsplash API: GET https://api.unsplash.com/search/photos?query=[terms]&orientation=[landscape|portrait]
2. Use the regular URL (not raw) with Unsplash attribution
3. Note in a comment: // PLACEHOLDER: Unsplash image, replace with custom asset
```

### 6. Editing Protocol
```
When the user asks to change text:
- Find the section data file in /src/data/sections/
- Make the edit
- Do not change surrounding structure or styling unless asked

When the user asks to change styling:
- Modify Tailwind classes only
- Stay within the design system defined above
- If the request conflicts with the design system, note the conflict and ask

When the user asks to add a section:
- Create a new data file in /src/data/sections/
- Create a new component in /src/components/report/
- Add it to the page layout in the correct position
- Follow existing section patterns for consistency

When the user asks to reorder sections:
- Change the import order in the main page.tsx
- Do not rename files
```

---

## What Gets Simpler vs. What Gets Harder

### Simpler:
- **Architecture:** No CMS, no database, no admin UI, no auth
- **Build time:** Dramatically faster to v1. Claude Code can scaffold the entire site in a focused session.
- **Maintenance:** It's just a Next.js repo. No services to maintain beyond Vercel (and optionally Cloudinary).
- **Cost:** Near zero. Vercel free tier + Cloudinary free tier handles this easily.

### Harder (or at least different):
- **Scott's learning curve:** He needs to be comfortable working in Claude Code. He needs to describe what he wants clearly. He can't just click a button.
- **No visual preview during editing:** Scott types a request, Claude Code makes the change, Vercel deploys (1-2 minutes), then Scott sees the result. There's no live WYSIWYG preview. This may frustrate a visual person.
- **Image management is manual:** There's no browseable image library. Scott needs to have his images on his computer (or Dropbox) and drag them in. There's no tagging, no search, no "show me all event photos."
- **No undo button:** If Claude Code makes a change Scott doesn't like, he says "undo that" and Claude Code reverts. But there's no visual version history. Git provides this technically, but Scott won't use Git.
- **Consistency risk:** If Scott works in Claude Code without you, he might make requests that break the design system. The memory.md mitigates this, but doesn't eliminate it.

---

## A Practical Middle Ground

Given that Scott is visual and undisciplined with files, here's what I'd actually recommend:

### For v1: Pure vibe-coded build
- You build the full report in Claude Code using the spec and content we've gathered
- Pre-populate with Unsplash images and the existing Arterial/NRA imagery we can source
- Deploy to Vercel
- Share the live URL with Scott for review

### For Scott's edits: A simple image compression utility + Claude Code
- Build a single utility script (`/scripts/optimize-image.ts`) that Scott can reference:
  - Claude Code runs it automatically whenever Scott provides an image
  - It uses Sharp to resize, compress, convert to WebP
  - It outputs to `/public/images/` with a clean filename
- The memory.md instructs Claude Code to always run this script when handling new images

### For image sourcing (when Scott doesn't have an image):
- Include a simple `/scripts/search-unsplash.ts` that Claude Code can call:
  - Takes a search query, returns 5 URLs with previews
  - Claude Code presents them to Scott: "Here are 5 options for the Programs hero image. Which do you prefer, or should I search for something else?"

### Defer entirely:
- CMS / admin UI
- Image metadata database
- AI auto-tagging
- Dropbox bulk import

These become v2 features *only if* the vibe-coding workflow proves too limiting in practice.

---

## Revised Tech Stack (Simplified)

```
Framework:          Next.js 14+ (App Router)
Styling:            Tailwind CSS
Animation:          Framer Motion
Image optimization: Sharp (local script) + next/image (runtime)
Image hosting:      Cloudinary (optional) or /public + Vercel Image Optimization
Stock images:       Unsplash API (for placeholders)
Deployment:         Vercel
Build tool:         Claude Code
CMS:                None. Claude Code is the CMS.
Database:           None.
Auth:               None.
```

---

## Revised File Structure (Simplified)

```
/arterial-impact-report
├── README.md
├── memory.md                          # Claude Code instructions (critical)
├── SPECIFICATIONS.md                  # Full requirements reference
├── /scripts
│   ├── optimize-image.ts             # Sharp-based compression utility
│   └── search-unsplash.ts            # Unsplash API search helper
├── /public
│   ├── /images
│   │   ├── /cover
│   │   ├── /programs
│   │   ├── /artists
│   │   ├── /events
│   │   ├── /headshots
│   │   └── /backgrounds
│   └── /logos
├── /src
│   ├── /app
│   │   ├── page.tsx                  # Single-page report layout
│   │   └── layout.tsx                # Root layout, fonts, metadata
│   ├── /components
│   │   └── /report
│   │       ├── CoverSection.tsx
│   │       ├── MissionSection.tsx
│   │       ├── FounderLetterSection.tsx
│   │       ├── MetricsSection.tsx
│   │       ├── ProgramsSection.tsx
│   │       ├── NotRealArtSection.tsx
│   │       ├── ArtistCommunitySection.tsx
│   │       ├── DistributionSection.tsx
│   │       ├── LeadershipSection.tsx
│   │       ├── FinancialSection.tsx
│   │       ├── SupportersSection.tsx
│   │       ├── LookingAheadSection.tsx
│   │       └── /shared
│   │           ├── StatCounter.tsx       # Animated number counter
│   │           ├── SectionWrapper.tsx     # Consistent padding, fade-in
│   │           ├── PullQuote.tsx
│   │           ├── ProgramCard.tsx
│   │           ├── PieChart.tsx
│   │           └── DonorTierList.tsx
│   ├── /data
│   │   └── /sections
│   │       ├── cover.ts
│   │       ├── mission.ts
│   │       ├── founders-letter.ts
│   │       ├── metrics.ts
│   │       ├── programs.ts
│   │       ├── not-real-art.ts
│   │       ├── artist-community.ts
│   │       ├── distribution.ts
│   │       ├── leadership.ts
│   │       ├── financial.ts
│   │       ├── supporters.ts
│   │       └── looking-ahead.ts
│   ├── /lib
│   │   ├── cloudinary.ts             # Optional: upload helper
│   │   └── unsplash.ts              # Search helper
│   └── /types
│       └── report.ts                 # Shared types
├── package.json
├── tailwind.config.js
├── tsconfig.json
└── .env.local                        # UNSPLASH_ACCESS_KEY, CLOUDINARY_* (if used)
```

---

## Next Steps

Given this simplified approach, the priority order shifts:

1. **Draft memory.md** — this is now the single most critical artifact. It needs to be comprehensive enough for both you and Scott to get consistent results from Claude Code.

2. **Draft the 12 data files** (`/src/data/sections/*.ts`) — pre-populated with all the Arterial content we have.

3. **Draft SPECIFICATIONS.md** — trimmed down from the CMS version, focused on the vibe-coded approach.

4. **Run the Perplexity research prompts** — to fill in macro data for the "why Arterial matters" framing.

5. **Build** — at that point you have everything Claude Code needs to scaffold the entire site.

Which of these should I start producing?

User: When you do a Perplexity search on the best tech stack for creating this sort of a website, are we positive that it is Tailwind CSS and Frame of Motion and Next.js 14 plus? Or are there other boilerplate templates and frameworks to generate website-like code in the way we have in mind for this. 

Assistant: 

Good question. Let me research this properly rather than assume the stack I proposed is optimal for this specific use case.

Tool: <PLUGIN_OUTPUT id="a4beab0b-ce7b-4a8a-96c7-66e561d1202c" type="string" />

Tool: <PLUGIN_OUTPUT id="50967010-a16b-4c12-9a16-c01838a584cb" type="string" />

Tool: <PLUGIN_OUTPUT id="ac9e32cc-5b62-40f4-9517-d2ec7b92e732" type="string" />

Assistant: 

Tool: <PLUGIN_OUTPUT id="4b0a1f11-ce38-4825-9c3a-22f3c4219e4c" type="string" />

Tool: <PLUGIN_OUTPUT id="c610f492-690f-426d-a179-62c1b966faf3" type="string" />

Assistant: 

Tool: <PLUGIN_OUTPUT id="23caf583-d7f8-42ba-b27d-6235b1d846be" type="string" />

Tool: <PLUGIN_OUTPUT id="3888e17f-fcfe-45d0-8126-7a715a5b8a84" type="string" />

Assistant: This changes the picture significantly. Here's the honest assessment:

---

## Tech Stack Evaluation: Is Next.js + Tailwind + Framer Motion the Right Choice?

**Short answer: No, it's probably not the optimal stack for this specific project.** Here's why, and what the alternatives are.

### What This Project Actually Is

This is a **single-page, scroll-driven, image-heavy, mostly-static visual report**. It has:
- 12 sections rendered vertically
- Scroll-triggered animations (fade-ins, counter animations, parallax)
- Large images and background imagery
- Minimal interactivity (no forms, no user accounts, no dynamic data fetching)
- Content that changes once per year (or when Scott vibe-codes edits)

It is **not**:
- A web application with routing, auth, or state management
- A data-driven dashboard with real-time updates
- A multi-page site with complex navigation

This distinction matters because it determines how much framework overhead is justified.

---

### The Contenders

#### 1. Astro + Tailwind + GSAP ScrollTrigger

**This is the strongest fit for this project.** Here's why:

| Factor | Assessment |
|---|---|
| **Bundle size** | Astro ships zero JavaScript by default. Only the animation code (GSAP ~23KB gzipped) reaches the browser. A Next.js build sends 80-120KB of React runtime before your first line of content renders. For a visual report where load speed and smoothness matter, this is a real difference. |
| **Architecture match** | Astro is built for content-driven, mostly-static sites. That's exactly what this is. Next.js is built for web applications. Using Next.js here is like using a pickup truck to deliver a letter — it works, but it's more than you need. |
| **Animation capability** | GSAP with ScrollTrigger is the industry standard for scroll-driven animation. It handles pinning, scrubbing, parallax, counter animations, and staggered reveals. It's framework-agnostic, so it works natively in Astro without wrappers. Framer Motion is React-specific and has documented performance issues under complex animation loads. |
| **Claude Code compatibility** | This is the unexpected finding. Astro has an **official MCP server** for Claude Code, meaning Claude Code has direct access to current Astro documentation during code generation. Next.js does not have this. Multiple reports confirm full Astro sites scaffolded in under an hour via Claude Code. |
| **Image handling** | Astro has built-in `<Image>` and `<Picture>` components that auto-optimize at build time (resize, format conversion, lazy loading). No Cloudinary required for basic optimization. Scott's 20MB file gets processed during build, not at runtime. |
| **Deployment** | Deploys to Vercel identically to Next.js. No change to your deployment workflow. |
| **Starter templates** | AstroWind (4.9K GitHub stars) is a Tailwind + Astro landing page template with scroll animation support built in. |

**Downsides of Astro:**
- If you later need to add interactive features (a donor portal, a form, an image upload widget), Astro uses "islands" architecture — you'd embed a React/Svelte/Vue component just for that interactive piece. This is actually fine architecturally, but it's a different mental model than "everything is React."
- Your existing boilerplate and muscle memory is Next.js. There's a switching cost.
- If Scott later wants the report to pull from Airtable dynamically (not at build time), Astro can do this via SSR mode, but it's less natural than Next.js.

#### 2. Next.js + Tailwind + GSAP (not Framer Motion)

If you stick with Next.js, **swap Framer Motion for GSAP**. The reasons:

- GSAP ScrollTrigger is purpose-built for exactly the scroll-driven animations this report needs (pinning sections, scrub-based progress, viewport-triggered counters). Framer Motion's `whileInView` is simpler but far less capable.
- GSAP performs better under load. Multiple sources document Framer Motion frame drops in complex nested animations.
- GSAP is ~23KB gzipped. Framer Motion is larger and you're paying for gesture/drag/layout animation features you'll never use in a static report.

**If you go this route**, the stack becomes: Next.js 14+ (App Router) + Tailwind + GSAP + ScrollTrigger. This works. It's just heavier than necessary.

#### 3. SvelteKit + Tailwind + GSAP

SvelteKit benchmarks significantly better than Next.js for this type of project:
- 15-42KB gzipped bundle vs. 80-120KB for Next.js
- No virtual DOM overhead — Svelte compiles to direct DOM manipulation
- 1.2s time to interactive vs. 2.8s in comparative tests
- Svelte's reactivity model is simpler than React's hooks

**The problem:** Claude Code's support for SvelteKit is not as well-documented as Astro. You don't have the MCP server advantage. And neither you nor Scott has SvelteKit experience (I'm assuming), so the vibe-coding workflow becomes riskier — Claude Code might produce code that neither of you can troubleshoot.

#### 4. No-Code: Vev or Webflow

These came up in the research and deserve mention. Vev in particular is built specifically for interactive annual reports with scroll animations.

**Why this might make sense for Scott:** He could visually design and edit the report himself. No code, no Claude Code, no deployment pipeline.

**Why this probably doesn't work:** You lose all control over performance, customization, and deployment. The output isn't a codebase you own. And the vibe-coding workflow with Claude Code — which is the core of your strategy — doesn't apply.

---

### My Revised Recommendation

**Primary recommendation: Astro + Tailwind + GSAP ScrollTrigger**

```
Framework:          Astro 5.x
Styling:            Tailwind CSS 4.x
Animation:          GSAP + ScrollTrigger (scroll-triggered reveals, counters, parallax)
                    + Lenis (smooth scroll, lightweight, pairs with GSAP)
Image optimization: Astro's built-in <Image> component (build-time optimization)
                    + Sharp (for Scott's oversized uploads, run via script)
Stock images:       Unsplash API
Deployment:         Vercel
Build tool:         Claude Code (with Astro MCP server for documentation access)
Starter template:   AstroWind (fork and customize) or clean Astro + Tailwind init
```

**Fallback recommendation: Next.js + Tailwind + GSAP ScrollTrigger**

If you're uncomfortable switching frameworks or if Claude Code's Astro output proves unreliable in practice, stick with Next.js but replace Framer Motion with GSAP. You already know the framework, your boilerplate exists, and the performance penalty (heavier bundle, slower initial load) is acceptable for a report that's not competing on Core Web Vitals.

```
Framework:          Next.js 14+ (App Router)
Styling:            Tailwind CSS
Animation:          GSAP + ScrollTrigger (NOT Framer Motion)
                    + Lenis (smooth scroll)
Image optimization: next/image (runtime optimization via Vercel)
                    + Sharp script for pre-processing Scott's uploads
Stock images:       Unsplash API
Deployment:         Vercel
Build tool:         Claude Code
```

---

### Key Takeaway on Animation Library

Regardless of framework choice, **GSAP + ScrollTrigger replaces Framer Motion** for this project. This is the clearest finding from the research:

| Capability | GSAP ScrollTrigger | Framer Motion |
|---|---|---|
| Scroll-triggered section reveals | Native, precise control over start/end points | `whileInView` — works but limited control |
| Animated number counters | Timeline-based, scrub to scroll position | Requires custom hook, no native scroll binding |
| Parallax backgrounds | ScrollTrigger scrub with y-offset — standard pattern | No native parallax. Requires `useScroll` + `useTransform` chain |
| Section pinning (sticky sections during scroll) | `pin: true` — one line | Not supported natively |
| Performance under load | Direct DOM manipulation, GPU accelerated, no VDOM | React reconciliation overhead, documented frame drops |
| Bundle size | ~23KB core + ~8KB ScrollTrigger | ~30KB+ and you use a fraction of the API |
| Framework dependency | None — works in Astro, Next, Svelte, vanilla | React only |

---

### Decision Point

Before I draft the spec files, you need to make one call:

**Astro or Next.js?**

If you want, I can have Claude Code scaffold a minimal proof-of-concept in Astro (single page, 3 sections, GSAP scroll animations, Tailwind, deployed to Vercel) so you can evaluate the developer experience and Claude Code's output quality before committing. That would take very little effort and would answer the question empirically rather than theoretically.

User: Let's talk about inputs in order to get the correct and best possible language and content from research that we need to first conduct on Arterial and its sub-projects. 

1. I would like a proposal on providing some URLs and domains as starting points. These would need to be crawled and become part of the knowledge base. For example there is Not Real Art, which is a magazine-style site and has several feature pages as well as a blog. For the most part we can ignore the blog but the feature pages highlight things like:
- the exhibitions that are being run
- the team that is part of the work
- the series, like Remote, which is a video series about public art
- the Not Real Art School
There are a number of initiatives that we could get information about and I would like to have the ability to supply a list of URLs so that they would be scanned. We have the knowledge base in the same documents folder, possibly the readme.md files that we could generate using FireCrawl as a result of these PDFs.
My idea here is to let me generate a configuration file with URLs to scan and the application should produce more documents as fodder for generating the report. Obviously Arterial.org itself is another major candidate and every single page on that site ought to be scanned for content and relevance. How this information is stored is to be determined. I suppose it could be local.md files but it could also be an Airtable where we perhaps produce a relevance score and associate what is scanned with the report segments as potential candidates for being included in generating the language.

2. I would also like to enhance the spec with the ability to have a docs folder where we can drag existing PDFs and text documents into as a form of repository for the latest Arterial-related projects. The idea would be that if we are starting to vibe code and we have an existing PDF that we are emulating, that document folder is scanned for all resources related to the project. Perhaps we could use GitHub as a planning tool to then create issues for each page or for each section of the report before executing it. This would keep the Claude Code context window intact and flexible. 

3. All of this content gathering is really creating a knowledge base that almost approaches building a RAG system; however I don't know whether that is overkill or how to best design a RAG approach. We have Airtable, a database built into n8n, and we have Supabase but I'm wondering about it being overkill or using resources to build such a knowledge base. For other projects this might also be useful but I would just as well have a more simple approach. However I am cognizant of the fact that if we are asking an AI to write based on a bunch of content that is disparate, a RAG system may be advantageous. 

Assistant: 

Let me research the practical options for content gathering, RAG approaches at this scale, and how to structure this efficiently before giving you a detailed response.

Tool: <PLUGIN_OUTPUT id="f60fa3c0-c691-426e-9f41-63c5bdda8504" type="string" />

Tool: <PLUGIN_OUTPUT id="b943b87a-03e7-4677-9593-fcd960b63202" type="string" />

Tool: <PLUGIN_OUTPUT id="650e0124-b6f3-4fb9-821b-838082789fb1" type="string" />

Assistant: 

Tool: <PLUGIN_OUTPUT id="775ef1c2-c046-4b76-a99b-7e9a8de66208" type="string" />

Tool: <PLUGIN_OUTPUT id="23b5baaf-35ee-42f9-a526-48bc0c203247" type="string" />

Assistant: 

Tool: <PLUGIN_OUTPUT id="e34859d5-94d4-4a20-89cd-4d4c053f3c9b" type="string" />

Tool: <PLUGIN_OUTPUT id="ce4ebbdb-01d7-4514-90e1-9425453018e9" type="string" />

Assistant: Now I have a clear picture of the content landscape. Here's the detailed plan:

---

## Content Gathering System: Specification

### 1. URL Crawling via FireCrawl

#### 1A. Target Domains and URL Map

Here is the complete inventory of URLs to crawl, organized by domain and priority:

**arterial.org** (crawl entire domain)
```
https://arterial.org/                          # Homepage
https://arterial.org/about/                    # Mission, tenets, vision
https://arterial.org/blog/                     # Blog index
https://arterial.org/donate/                   # Giving model, 80/20 allocation
https://arterial.org/arthouse/                 # Arthouse TV series
https://arterial.org/classic-black/            # Classic Black program
https://arterial.org/artsville-usa/            # Artsville USA acquisition
https://arterial.org/arterial-radio/           # Arterial Radio
https://arterial.org/underbelly-project-documentary/  # Underbelly grant
https://arterial.org/arterial-announces-partnership-with-pbs-artbound-series/
https://arterial.org/not-real-art-brand/       # NRA fiscal sponsorship
```

**notrealart.com** (selective crawl — feature pages only, exclude blog posts)
```
https://notrealart.com/                        # Homepage
https://notrealart.com/exhibitions/            # First Fridays exhibition listing
https://notrealart.com/podcast-network/        # Podcast network overview
https://notrealart.com/grant/                  # Grant program details
https://notrealart.com/remote/                 # Remote video series
https://notrealart.com/about/                  # About / team
https://notrealart.com/year-in-review-2025/    # Year in review (useful for metrics)
```

**school.notrealart.com** (selective)
```
https://school.notrealart.com/                 # School homepage, course listings
```

**classicblackmusic.org** (selective)
```
https://www.classicblackmusic.org/             # Homepage
https://www.classicblackmusic.org/about-classic-black/  # Video series
```

**arthouseshow.com** (if live)
```
https://arthouseshow.com/                      # Arthouse TV show
```

#### 1B. Crawl Configuration File

Create a `crawl-config.json` at the project root:

```json
{
  "apiKey": "${FIRECRAWL_API_KEY}",
  "outputDir": "./content/crawled",
  "defaults": {
    "formats": ["markdown"],
    "onlyMainContent": true,
    "blockAds": true,
    "timeout": 30000
  },
  "targets": [
    {
      "id": "arterial-org",
      "url": "https://arterial.org",
      "method": "crawl",
      "maxDiscoveryDepth": 3,
      "excludePaths": ["/privacy-policy", "/wp-admin/*", "/wp-json/*"],
      "reportSections": ["mission", "programs", "leadership", "financial", "distribution"]
    },
    {
      "id": "notrealart-features",
      "method": "batch",
      "urls": [
        "https://notrealart.com/",
        "https://notrealart.com/exhibitions/",
        "https://notrealart.com/podcast-network/",
        "https://notrealart.com/grant/",
        "https://notrealart.com/remote/",
        "https://notrealart.com/about/",
        "https://notrealart.com/year-in-review-2025/"
      ],
      "reportSections": ["not-real-art", "artist-community", "programs"]
    },
    {
      "id": "nra-school",
      "method": "batch",
      "urls": [
        "https://school.notrealart.com/"
      ],
      "reportSections": ["not-real-art"]
    },
    {
      "id": "classic-black",
      "method": "batch",
      "urls": [
        "https://www.classicblackmusic.org/",
        "https://www.classicblackmusic.org/about-classic-black/"
      ],
      "reportSections": ["programs"]
    },
    {
      "id": "arthouse-show",
      "method": "batch",
      "urls": [
        "https://arthouseshow.com/"
      ],
      "reportSections": ["programs"]
    }
  ]
}
```

Note the `reportSections` field on each target. This is the link between crawled content and the report sections it's relevant to. When the crawl script runs, it tags each output file with these section associations.

#### 1C. Crawl Script Output Structure

The script produces one markdown file per crawled page, saved with metadata frontmatter:

```
/content/crawled/
├── arterial-org/
│   ├── _index.md                    # arterial.org homepage
│   ├── about.md                     # arterial.org/about
│   ├── arthouse.md                  # arterial.org/arthouse
│   ├── classic-black.md
│   ├── artsville-usa.md
│   ├── underbelly-project-documentary.md
│   ├── not-real-art-brand.md
│   ├── arterial-radio.md
│   ├── pbs-artbound.md
│   └── donate.md
├── notrealart-features/
│   ├── _index.md
│   ├── exhibitions.md
│   ├── podcast-network.md
│   ├── grant.md
│   ├── remote.md
│   ├── about.md
│   └── year-in-review-2025.md
├── nra-school/
│   └── _index.md
├── classic-black/
│   ├── _index.md
│   └── about-classic-black.md
└── arthouse-show/
    └── _index.md
```

Each file has frontmatter like:

```yaml
---
source_url: "https://arterial.org/classic-black/"
crawl_target: "arterial-org"
crawled_at: "2025-01-15T14:30:00Z"
report_sections: ["programs"]
title: "Arterial Celebrates Black Excellence in Classical Music"
word_count: 1247
relevance_notes: ""
---

[markdown content from FireCrawl]
```

The `relevance_notes` field starts empty. It can be populated later — either manually or by an AI pass that reads each file and writes a 1-2 sentence summary of what's useful for the report.

---

### 2. The /docs Folder: Manual Document Repository

Separate from the crawled content, the `/docs` folder holds PDFs, text files, and other materials that you or Scott drag in manually. These are source documents that don't come from web crawling.

```
/docs/
├── reference/
│   └── Art21-Impact-Report-FY24.pdf           # Design reference
├── arterial/
│   ├── Arterial_v2_100324.pdf                 # Confidential pitch deck
│   ├── Arterial_pitch_deck_042723.pdf         # Earlier pitch deck
│   └── Arterial-Web-Copy.docx                 # Web copy document
├── arthouse/
│   ├── ArtHousePitch_10-11-24.pdf             # Pitch document
│   ├── Arthouse-Crowdfunding-Press-Release.pdf
│   ├── Arthouse-Crowdfunding-Comms-Framework.pdf
│   ├── Arthouse-Brand-Guidelines.pdf
│   └── Arthouse-Donor-List-Workflow.pdf
└── _manifest.json
```

The `_manifest.json` indexes every document with metadata:

```json
[
  {
    "filename": "Arterial_v2_100324.pdf",
    "path": "docs/arterial/Arterial_v2_100324.pdf",
    "type": "pdf",
    "description": "Arterial confidential pitch deck, October 2023",
    "report_sections": ["mission", "programs", "financial", "leadership"],
    "confidential": true,
    "notes": "Contains program descriptions, budget figures, donor model. Do not reproduce budget numbers publicly without approval."
  }
]
```

**Why the manifest matters for Claude Code:** When Claude Code starts a build session, it reads `_manifest.json` to understand what documents exist, what they contain, and which report sections they're relevant to — without loading every PDF into context. It then selectively reads only the documents relevant to the section it's currently working on.

**Processing PDFs for Claude Code consumption:** PDFs can't be read natively by Claude Code during a build. You have two options:

1. **Pre-convert to markdown:** Run a script that uses a PDF-to-text library (like `pdf-parse` or `pdfjs-dist`) to extract text from each PDF and save it as a companion `.md` file alongside the original. Claude Code reads the `.md` version.

2. **Use this assistant (me) to process them:** Upload PDFs here, I extract the content, and you save the output as markdown files in `/docs`. This is what we've already done with the Art21 report.

I'd recommend option 1 as a script in `/scripts/process-docs.ts` so it's repeatable whenever Scott drops a new PDF in.

---

### 3. RAG vs. Simpler Approaches: Honest Assessment

Here's the calculation:

**Total content corpus size estimate:**
- Crawled web pages: ~30-40 pages × ~1,000 words average = ~35,000 words
- Existing documents (PDFs, text): ~50,000 words across all the docs we've identified
- Total: ~85,000 words ≈ ~110,000 tokens

**Claude's context window:** ~200,000 tokens (Claude Code with Sonnet)

**The math:** Your entire content corpus fits within roughly 55% of Claude Code's context window. This is the critical insight.

#### Do You Need RAG?

**No. Not for this project.**

A RAG system (vector embeddings, retrieval pipeline, reranking) solves the problem of: "I have too much content to fit in context, so I need to retrieve only the relevant chunks." You don't have that problem. Your corpus is small enough to work with directly.

**What you need instead is structured context loading.** That means:

1. **Don't load everything at once.** Claude Code's performance degrades as context fills. Loading 110K tokens of source material leaves only 90K for reasoning, code generation, and conversation. That's tight.

2. **Load per-section.** When Claude Code is building the "Programs" section, it loads only:
   - The crawled pages tagged with `report_sections: ["programs"]`
   - The docs manifest entries tagged with `report_sections: ["programs"]`
   - The specific content from those files

   This might be 15,000-20,000 tokens instead of 110,000. Claude Code has plenty of room to reason and write.

3. **Use the `memory.md` to orchestrate this.** The memory.md file tells Claude Code:

```markdown
## Content Loading Protocol

When working on a specific report section:

1. Read `/content/_section-map.json` to find which crawled pages 
   and docs are relevant to this section
2. Load ONLY those files into context
3. After completing the section, use /compact before moving to 
   the next section
4. Do not attempt to load all content files at once

Section-to-content mapping is defined in:
- Crawled files: frontmatter `report_sections` field
- Docs: `_manifest.json` `report_sections` field
```

#### When Would RAG Make Sense?

RAG would become relevant if:
- The artist database (2,000+ artists) needed to be searchable and quotable in the report
- You were generating multiple reports across different time periods from the same corpus
- The content corpus grew to 500,000+ tokens (5x current size)
- You wanted a chatbot on the impact report site that could answer questions about Arterial

None of these are current requirements. If any of them become requirements later, you can add a RAG layer then. Supabase with pgvector is the right choice at that point because you already use Supabase. But building it now is premature engineering.

---

### 4. GitHub Issues as Claude Code Task Decomposition

This is the right approach for keeping Claude Code's context window clean. Here's how to structure it:

#### Issue Template for Each Report Section

Create a GitHub issue for each section with this structure:

```markdown
## Section: [04] Programs & Projects

### Content Sources
- Crawled: `content/crawled/arterial-org/arthouse.md`
- Crawled: `content/crawled/arterial-org/classic-black.md`
- Crawled: `content/crawled/arterial-org/underbelly-project-documentary.md`
- Crawled: `content/crawled/arterial-org/pbs-artbound.md`
- Crawled: `content/crawled/arterial-org/artsville-usa.md`
- Crawled: `content/crawled/arterial-org/arterial-radio.md`
- Doc: `docs/arthouse/ArtHousePitch_10-11-24.pdf`
- Doc: `docs/arterial/Arterial_v2_100324.pdf` (program descriptions only)

### Component
`/src/components/report/ProgramsSection.tsx` (or `.astro`)

### Data File
`/src/data/sections/programs.ts`

### Design Reference
Art21 FY24 report pp.16-26: Production section with program cards, 
behind-the-scenes images, festival highlights list.

### Content Requirements
- Card-style layout for each program
- Each card: program name, 1-2 sentence description, key metric, image
- Programs to include: NOT REAL ART (fiscal sponsorship), Underbelly Project, 
  Artbound/PBS, Classic Black, Arthouse, The Good Art, Artsville USA, Arterial Radio
- Pull quote from Scott Power on one of the programs

### Image Requirements
- 1 hero/background image for the section
- 1 image per program card (8 total)
- Source: Unsplash placeholders initially, tagged for replacement

### Acceptance Criteria
- [ ] All 8 programs listed with accurate descriptions
- [ ] Descriptions sourced from crawled content and docs, not hallucinated
- [ ] Responsive layout: 2-column grid on desktop, single column on mobile
- [ ] Scroll-triggered fade-in animation on each card
- [ ] Images have proper alt text
- [ ] Section matches design system defined in memory.md
```

#### The Claude Code Workflow Per Issue

```
1. Open Claude Code
2. /clear (start fresh)
3. Claude Code reads memory.md (automatic, always loaded)
4. Tell Claude Code: "Work on GitHub issue #4 — Programs section"
5. Claude Code reads the issue, identifies content sources
6. Claude Code loads ONLY the listed content files
7. Claude Code builds the component, data file, and integrates it
8. Claude Code commits with message: "feat: add Programs section (closes #4)"
9. /compact (save summary before next section)
10. Move to next issue
```

This keeps each section build within ~30,000-40,000 tokens of context (memory.md + section content + generated code), well within the window.

#### Full Issue List

| Issue # | Section | Priority | Dependencies |
|---|---|---|---|
| #1 | Project setup: Astro/Next.js init, Tailwind, GSAP, file structure | P0 | None |
| #2 | Shared components: SectionWrapper, StatCounter, PullQuote, ProgramCard | P0 | #1 |
| #3 | Section 00: Cover / Hero | P1 | #1, #2 |
| #4 | Section 01: Mission & Tenets | P1 | #2 |
| #5 | Section 02: Founder's Letter | P1 | #2 |
| #6 | Section 03: Year at a Glance (Metrics) | P1 | #2 |
| #7 | Section 04: Programs & Projects | P1 | #2 |
| #8 | Section 05: NOT REAL ART In Depth | P1 | #2 |
| #9 | Section 06: Artist Community & Exhibitions | P2 | #2 |
| #10 | Section 07: Distribution & Partnerships | P2 | #2 |
| #11 | Section 08: Leadership & Governance | P2 | #2 |
| #12 | Section 09: Financial Summary | P2 | #2 |
| #13 | Section 10: Supporters & Donors | P2 | #2 |
| #14 | Section 11: Looking Ahead & CTA | P2 | #2 |
| #15 | Full-page integration, scroll behavior, navigation | P1 | #3-#14 |
| #16 | Image optimization: Sharp script, Unsplash fallbacks | P1 | #1 |
| #17 | Vercel deployment configuration | P0 | #1 |

---

### 5. The Content-to-Section Mapping Index

This is the glue file that connects everything. Create `/content/_section-map.json`:

```json
{
  "cover": {
    "crawled": [],
    "docs": [],
    "notes": "No content sources needed. Logo, title, and hero image only."
  },
  "mission": {
    "crawled": [
      "content/crawled/arterial-org/about.md",
      "content/crawled/arterial-org/_index.md"
    ],
    "docs": [
      "docs/arterial/Arterial-Web-Copy.docx"
    ],
    "notes": "Three tenets, vision statement, five key insights. Use exact language from Arterial web copy."
  },
  "founders-letter": {
    "crawled": [
      "content/crawled/arterial-org/about.md"
    ],
    "docs": [],
    "notes": "Scott Power needs to write or approve this. Draft based on his bio and Arterial's 2024 accomplishments."
  },
  "metrics": {
    "crawled": [
      "content/crawled/notrealart-features/podcast-network.md",
      "content/crawled/notrealart-features/grant.md",
      "content/crawled/notrealart-features/exhibitions.md",
      "content/crawled/notrealart-features/year-in-review-2025.md",
      "content/crawled/arterial-org/not-real-art-brand.md"
    ],
    "docs": [
      "docs/arterial/Arterial-Web-Copy.docx"
    ],
    "notes": "Confirmed numbers: 2000+ artists, 6 podcasts, 300+ hours, $12K Underbelly grant, 200 Miami premiere attendees, 6 grant recipients/year at $2K each. Flag any unconfirmed numbers with [VERIFY]."
  },
  "programs": {
    "crawled": [
      "content/crawled/arterial-org/arthouse.md",
      "content/crawled/arterial-org/classic-black.md",
      "content/crawled/arterial-org/underbelly-project-documentary.md",
      "content/crawled/arterial-org/pbs-artbound.md",
      "content/crawled/arterial-org/artsville-usa.md",
      "content/crawled/arterial-org/arterial-radio.md",
      "content/crawled/arterial-org/not-real-art-brand.md"
    
