# Commercial "company brain", enterprise knowledge, AI second-brain and AI assistant products (catalogue as of 15 Nov 2026)

Scope: hosted products that let a business (especially SMBs) connect its own data and have AI answer from it. Weaker, stale, marginal, unverified-name or agency entries are in `company_brain_products_cache.md` (same folder).

**Legend used in every table**
- **Ver.** = verification level. **V** = facts in the row were confirmed this session from the linked source (date-stamped 2026 pages). **TD** = row comes from model training knowledge (cutoff mid-2026) and was NOT re-verified this session; treat price/connectors as indicative only. **V/TD** = existence/positioning verified, some cells from training knowledge.
- **Size** = target customer size: SMB (<50), Mid (50-1,000), Ent (1,000+).
- **Arabic**: "Y" = Arabic supported per source; "Y (LLM)" = underlying frontier LLM handles Arabic but no vendor statement about RTL UI/dialects found; "?" = unknown; "Native" = Arabic-first vendor.
- **API/MCP**: what the vendor exposes for agents/developers.
- Main-file count: ~150 entries. Cache-file count: ~95 entries. Combined: ~245.

---

## Q1. Enterprise search / work AI platforms (Glean, Copilot, Gemini Enterprise, ChatGPT, Claude, AWS Quick, Coveo, Sinequa, Lucidworks, GoSearch, Moveworks, etc.)

### Takeaway
The category is dominated by suite assistants (Microsoft 365 Copilot $30/user, Copilot Business $21; Gemini Enterprise Business from $21; ChatGPT Business $20-25; AWS Quick $20-40 + $250/account) and Glean (no public price; est. $60-65/user, median contract ~$98.9k/yr, 100-250 seat minimums). For SMBs, the published-price, self-serve options are GoSearch ($8-20), Onyx Cloud ($20), Dust (EUR 24), Notion Business ($20) and Sentra Team ($16, 2-20 people). Key 2025-26 corporate events: ServiceNow closed Moveworks (2025); Amazon Q Business evolved into "AWS Quick" (Quick Suite); Google Agentspace became Gemini Enterprise; Elastic deprecated Workplace Search in 9.0.

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 1 | Glean | https://www.glean.com | Permission-aware enterprise search + assistant + agent platform on a knowledge graph | Ent (often 100-250 seat min.) | No rate card. Est. $45-50/user base + ~$15 Work AI (Metronome); median contract $98,890/yr over 174 deals (Vendr); 12% premium support; FlexCredits meter agent runs (~7 credits median, ~114 p90); learned memories draw credits from 7 Nov 2026 | 275+ apps | ? | Yes: Glean MCP server documented for 22 hosts (ChatGPT, Claude Code, Cursor, Gemini Enterprise, Copilot Studio); APIs | V — [Sentra Glean alternatives](https://www.sentra.app/articles/glean-alternatives); [Sentra company brain ranking](https://www.sentra.app/articles/best-company-brain-platforms); [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 2 | Microsoft 365 Copilot (+ Copilot Business) | https://www.microsoft.com/microsoft-365-copilot | AI assistant grounded in Microsoft Graph (mail, files, Teams, SharePoint) | SMB-Ent | Enterprise $30/user/mo annual on top of M365; Copilot Business $21/user/mo annual or $25.20 monthly; $18 first-year promo on annual plans bought by 31 Dec 2026; no seat minimum since Jan 2024 | Microsoft Graph + Graph connectors | Y (TD: Copilot supports Arabic) | Copilot Studio agents; MCP in Copilot Studio (TD) | V (pricing) — [Sentra](https://www.sentra.app/articles/glean-alternatives); [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 3 | Microsoft Copilot Studio | https://www.microsoft.com/microsoft-copilot/microsoft-copilot-studio | Low-code builder for custom agents over company data | Mid-Ent | Not verified this session | Power Platform connectors, SharePoint, Dataverse | Y (TD) | Yes (MCP host per Glean docs list) | V/TD — listed in [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives); MCP host per [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 4 | Google Gemini Enterprise (formerly Agentspace) | https://cloud.google.com/gemini-enterprise | Google's enterprise search, chat and agent platform, sold via Google Cloud | SMB-Ent | Business from $21/seat/mo (1-300 seats on product page, up to 500 in docs), 30-day trial up to 5 seats; Standard/Plus from $30; PAYG option with $0 seat fee for 20+ seats; Google removed public prices from product page early Oct 2026 | Drive, Gmail, Calendar, Chat, Sites + ~30 third-party on Business; ~140 connectors on Standard/Plus incl. OneDrive, Outlook, SharePoint | Y (LLM) | Custom connectors and custom MCP servers on Standard/Plus; Agent Marketplace | V — [insearch.ai](https://insearch.ai/gemini-enterprise-vs-chatgpt-enterprise); [CData](https://www.cdata.com/blog/glean-alternatives-enterprise-ai) (rebrand) |
| 5 | Google Cloud Agent Search / Vertex AI Search | https://cloud.google.com/generative-ai-app-builder/pricing | Usage-priced search/RAG building block for your own app | Mid-Ent (dev teams) | Usage-based (queries, generation, storage) | GCS, BigQuery, websites, third-party | Y (LLM) | API | V — [benchlm](https://benchlm.ai/blog/posts/glean-ai-alternatives) |
| 6 | ChatGPT Business / Enterprise (Company Knowledge) | https://chatgpt.com/business | OpenAI's workspace product; "Company Knowledge" answers across connected apps with source permissions | SMB-Ent | Business $20/seat/mo annual, $25 monthly; min 2, max 200 paid seats for workspaces created since 24 Aug 2026; Enterprise custom pricing | Company Knowledge plugin; each member connects own app accounts (Drive, SharePoint, Slack, GitHub etc. - TD for list) | Y (LLM) | MCP connectors/apps (TD) ; API separate | V — [insearch.ai](https://insearch.ai/gemini-enterprise-vs-chatgpt-enterprise) |
| 7 | Claude Team / Enterprise (Anthropic) | https://claude.com/pricing | Claude workspace with connectors and Projects over company docs | SMB-Ent | Not verified this session (check vendor page) | Google Workspace, M365, Slack, remote MCP connectors (TD) | Y (LLM) | Yes - MCP native (TD) | V/TD — listed as suite assistant/bundled incumbent in [Sentra](https://www.sentra.app/articles/glean-alternatives) and [Slite](https://slite.com/learn/company-brain-solutions) |
| 8 | AWS Quick (formerly Amazon Q Business; "Amazon Quick Suite") | https://aws.amazon.com/quick/pricing/ | AWS agentic workspace: chat, research, shared knowledge bases, custom agents, BI | SMB-Ent | Sources conflict: AWS page lists Essentials $3, Professional $20, Enterprise $40/user/mo; others list Free/Plus/Max standalone plans + Professional $20 and Enterprise $40 plus $250/AWS account/mo (6 plans as of Nov 2026) | Slack, M365, Google, QuickBooks, + AWS sources | ? | Custom chat agents; AWS APIs (MCP: TD) | V — [AWS](https://aws.amazon.com/quick/pricing/); [The Rundown](https://www.therundown.ai/tools/amazon-quick-suite); [Elephas](https://elephas.app/resources/amazon-quick-pricing); [AWS builder post (rename)](https://builder.aws.com/content/3IwreNAmkr4eL9wtB7pudMfARxy/amazon-quick-aws-just-launched-a-dollar20month-rival-to-microsoft-copilot-and-chatgpt-enterprise) |
| 9 | Coveo (Workplace) | https://www.coveo.com | Enterprise/commerce/service search with relevance engine; generative answering add-on | Ent | By request; Workplace seat-based, annual or 3-year terms; each unit includes 100k queries/mo | Large connector library (TD) | ? | APIs | V — [Sentra](https://www.sentra.app/articles/glean-alternatives) |
| 10 | Lucidworks (Fusion) | https://lucidworks.com | Self-hostable AI search platform | Ent | Not published; runs on AKS/EKS/GKE | Many (TD) | ? | APIs | V — [Sentra](https://www.sentra.app/articles/glean-alternatives) |
| 11 | Sinequa (ChapsVision) | https://www.sinequa.com | French enterprise search / RAG platform for regulated industries; acquired by ChapsVision (2024, TD) | Ent | Not published | 200+ (TD) | Y (TD: strong multilingual NLP) | APIs | TD |
| 12 | GoSearch | https://www.gosearch.ai | AI enterprise search with indexed + federated retrieval; self-serve | SMB-Mid | Free (10 searches/day), Starter $8, Pro $20/user/mo; Enterprise custom (BYO cloud/on-prem, SSO, audit logs) | 100+ | ? | Enterprise configurable models (MCP: ?) | V — [Sentra](https://www.sentra.app/articles/glean-alternatives); [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 13 | Moveworks (ServiceNow) | https://www.moveworks.com | Employee-service AI assistant for IT/HR requests + enterprise search; acquisition by ServiceNow completed 2025 | Ent | Custom quote | ITSM/HRIS, M365, Slack etc. | Y (TD: 100+ languages) | Agent Studio (TD) | V — [Moveworks press release](https://www.moveworks.com/us/en/company/news/press-releases/servicenow-completes-acquisition-of-moveworks); [Sentra](https://www.sentra.app/articles/glean-alternatives) |
| 14 | Onyx Cloud (ex-Danswer) | https://onyx.app | Open-source enterprise search + AI chat; hosted cloud option | SMB-Mid | Community Edition free (MIT); Business $20/user/mo annual; Enterprise (SSO, on-prem) via sales | 40+ (TD) | Y (LLM) | API; MCP (TD) | V — [Sentra](https://www.sentra.app/articles/glean-alternatives); [cognee](https://www.cognee.ai/glean-alternatives) |
| 15 | Dust | https://dust.tt | No-code agent workspace over company data; model-agnostic | SMB-Ent (10-5,000+) | Pro EUR 24/user/mo yearly or EUR 30 monthly (8,000 credits/seat); Max EUR 120/150 (Dust's own blog says "from $29") | Slack, Notion, Drive, Salesforce, Snowflake, BigQuery, GitHub, 100+ | Y ("ask in any language") | Yes - MCP support + API | V — [Dust blog](https://dust.tt/blog/glean-alternatives-ai-enterprise-search); [Sentra](https://www.sentra.app/articles/glean-alternatives); $40M Series B May 2026, 3,000 orgs per [Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026) |
| 16 | Atlassian Rovo | https://www.atlassian.com/software/rovo | AI search, chat and agents across Jira/Confluence + third-party connectors | SMB-Ent | Included site-wide on eligible Standard/Premium/Enterprise Cloud sites | Jira, Confluence, third-party connectors (org admin) | ? | Rovo MCP (TD) | V — [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 17 | Perplexity Enterprise | https://www.perplexity.ai/enterprise | Web + internal research assistant | SMB-Ent | Enterprise Pro $40/user/mo; Max $325 | Drive, SharePoint, file uploads (TD) | Y (LLM) | API (Sonar) | V — [benchlm](https://benchlm.ai/blog/posts/glean-ai-alternatives) |
| 18 | SearchBlox SearchAI | https://www.searchblox.com | Managed/self-managed enterprise search with hybrid retrieval, RAG, knowledge graph, agents | Mid-Ent | Fixed-cost custom quote | Many | ? | API | V — [benchlm](https://benchlm.ai/blog/posts/glean-ai-alternatives) |
| 19 | Hebbia | https://www.hebbia.com | AI document analysis for investing, banking, legal | Mid-Ent (finance) | Per seat (Professional + Lite seats); no minimum published | Data rooms, uploads | ? | ? | V — [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 20 | Tricky Wombat | https://www.trickywombat.ai | Project-scoped AI search with clustering pipeline; runs alongside other tools | SMB-Mid | Not found | Uploads | ? | ? | V (self-described) — [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 21 | CData Connect AI | https://www.cdata.com/ai/ | Governed connectivity layer letting any agent query databases/SaaS | Mid-Ent | Not verified | 300+ data sources (TD) | n/a | Yes - MCP (TD) | V — [CData](https://www.cdata.com/blog/glean-alternatives-enterprise-ai) |
| 22 | Slack AI / Slack enterprise search | https://slack.com/ai | AI search, recaps and answers over Slack + connected apps | SMB-Ent | Bundled in paid Slack plans (TD) | Slack, Drive, Salesforce, etc. (TD) | ? | Slack MCP server (TD) | V/TD — named as bundled incumbent in [Slite](https://slite.com/learn/company-brain-solutions) |
| 23 | Box AI | https://www.box.com/ai | Q&A and agents over Box content | SMB-Ent | Included in Business+ tiers (TD) | Box | Y (LLM) | Box AI API; Box MCP server (TD) | TD |
| 24 | Dropbox Dash | https://dash.dropbox.com | Universal AI search across apps for teams | SMB-Mid | TD | Dropbox, Google, M365, Slack etc. | ? | ? | TD |
| 25 | Writer (Knowledge Graph / AI HQ) | https://writer.com | Enterprise gen-AI platform with graph-based RAG over company data | Ent | Custom (TD) | Drive, SharePoint, Notion, Confluence (TD) | Y (TD) | API | TD |
| 26 | Cohere North | https://cohere.com/north | Secure agentic workspace for enterprises, private deploy | Ent | Custom | M365, Google, Salesforce (TD) | Y (Cohere has Arabic-tuned models, TD) | API | TD |
| 27 | Mistral Le Chat Enterprise | https://mistral.ai/products/le-chat | EU-hosted assistant with enterprise connectors and agents | SMB-Ent | TD | Drive, SharePoint, Gmail (TD) | Y (Mistral Saba Arabic model, TD) | API, MCP (TD) | TD |
| 28 | Kore.ai | https://kore.ai | Enterprise agent platform (search + work assistant + CX) | Ent | Custom | 100+ (TD) | Y (TD) | API | TD |
| 29 | Leena AI | https://leena.ai | Employee-service AI agent for HR/IT knowledge | Mid-Ent | Custom | HRIS/ITSM | ? | ? | V (listed) — [Tracxn KM list](https://tracxn.com/d/trending-business-models/startups-in-knowledge-management/__1UBPYM20gtsM_yazkJM5u1mq1ak0IfcwhqrUv3NYOKA/companies) |
| 30 | Vectara | https://www.vectara.com | RAG-as-a-service platform for grounded answers | Mid-Ent (dev) | Free tier + usage (TD) | Upload/API | Y (TD) | API | TD |
| 31 | Contextual AI | https://contextual.ai | Enterprise RAG agent platform | Ent | Custom (TD) | Many | ? | API | TD |

### Inferences
- For a small business, the realistic "hosted company brain" shortlist from this group is: Copilot Business ($21) if on M365, Gemini Enterprise Business ($21) if on Google, ChatGPT Business ($20-25) or Claude Team if model-first, plus independent layers GoSearch/Onyx/Dust at $8-30. Glean, Coveo, Sinequa, Lucidworks, Moveworks are effectively enterprise-only.
- Usage metering (Glean FlexCredits, Dust credits, Notion Custom Agent credits, AWS account fee) is replacing pure seat pricing in 2026, which makes SMB cost forecasting harder.
- MCP is now table-stakes: Glean, Dust, Gemini Enterprise (higher editions), Sentra, Coworker, Notion, Mem, Tana all expose MCP.

### Gaps
- Claude Team/Enterprise and ChatGPT Enterprise current prices not verified this session.
- Arabic UI/RTL support for Glean, GoSearch, Onyx, Coveo, Rovo not found.
- Elastic Workplace Search end-of-support date conflicts: 15 Jan 2027 ([Sentra](https://www.sentra.app/articles/glean-alternatives)) vs 15 Jul 2027 ([Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives)); entry moved to cache.

---

## Q2. Knowledge bases / wikis with AI (Guru, Notion AI, Slite, Tettra, Confluence/Rovo, Bloomfire, Document360, Sana, Lore, Stack Overflow for Teams, etc.)

### Takeaway
Knowledge bases have repositioned as "governed knowledge layers" for AI (Guru), "company brains" (Slite Agent) or agent platforms (Notion Agent). Notion Business ($20/member) now bundles Notion Agent, AI meeting notes and Enterprise Search (beta), with Custom Agents billed at $10/1,000 credits. Guru no longer publishes prices. Sana was absorbed by Workday (closed 4 Nov 2025, ~$1.1B).

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 32 | Guru | https://www.getguru.com | "Governed knowledge layer for enterprise AI": verified cards, expiry, AI search, agents | Mid-Ent | No longer published (one package incl. strategy services); benchlm cites "starts $25/seat" - conflicting | Slack, Teams, Chrome, Drive, Confluence, Zendesk etc. (TD) | ? | API; MCP (TD) | V — [getguru.com](https://www.getguru.com/); [Sentra](https://www.sentra.app/articles/glean-alternatives); conflict: [benchlm](https://benchlm.ai/blog/posts/glean-ai-alternatives) |
| 33 | Notion AI / Notion Agent | https://www.notion.com | Workspace wiki/docs with AI agent, meeting notes, enterprise search across connected apps | SMB-Ent | Business $20/member/mo incl. Notion Agent, AI Meeting Notes, Enterprise Search (beta); Custom Agents $10 per 1,000 credits | Slack, GitHub, Drive (TD: Jira, Teams, SharePoint) | ? (TD: RTL support limited) | Notion MCP server (read-write) | V — [Sentra](https://www.sentra.app/articles/glean-alternatives); [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 34 | Slite (Slite Agent) | https://slite.com | Self-maintaining AI knowledge base positioned as a "company brain"; agent drafts doc fixes when reality drifts | SMB-Mid | See https://slite.com/pricing (not captured) | Slack, Linear, GitHub, Drive (V/TD) | ? (UI in EN/FR/DE/ES/JA/NL locales) | Permission-aware access for third-party agents; MCP (TD) | V — [Slite](https://slite.com/learn/company-brain); [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 35 | Confluence + Rovo | https://www.atlassian.com/software/confluence | Wiki with Rovo AI search/agents | SMB-Ent | Rovo included on eligible Cloud plans | Jira, third-party via Rovo | ? | Rovo MCP (TD) | V — [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| 36 | Bloomfire | https://bloomfire.com | Knowledge-sharing platform with AI search/answers | Mid-Ent | Custom (TD) | SharePoint, Drive, Slack (TD) | ? | API (TD) | V (listed) — [Tracxn](https://tracxn.com/d/trending-business-models/startups-in-knowledge-management/__1UBPYM20gtsM_yazkJM5u1mq1ak0IfcwhqrUv3NYOKA/companies) |
| 37 | Sana (Workday) | https://sanalabs.com | AI knowledge assistant + learning platform; Workday acquisition (~$1.1B) completed 4 Nov 2025 | Mid-Ent | Previously had self-serve tier (TD); post-acquisition likely bundled into Workday | 100+ (TD) | ? | API (TD) | V — [Workday newsroom](https://newsroom.workday.com/2025-11-04-Workday-Completes-Acquisition-of-Sana); [Futurum](https://futurumgroup.com/insights/is-workdays-1-1b-sana-acquisition-enough-to-dominate-the-ai-agent-race/) |
| 38 | Document360 | https://document360.com | Knowledge base software with "Eddy" AI assistant for internal/external docs | SMB-Mid | Tiered; free trial (TD) | Zendesk, Intercom, Freshdesk, Slack (TD) | Y (TD: multilingual KB incl. RTL) | API (TD) | TD |
| 39 | Tettra | https://tettra.com | Lightweight internal wiki with AI Q&A in Slack ("Kai") | SMB | TD | Slack, Drive, GitHub (TD) | ? | ? | TD — status in 2026 not verified |
| 40 | Stack Overflow for Teams (Stack Internal) | https://stackoverflow.co/teams/ | Internal Q&A knowledge base for engineering with AI answers; rebranded "Stack Internal" in 2025 (TD) | Mid-Ent | Free/Basic/Business tiers (TD) | Slack, Teams, Jira (TD) | ? | API; MCP server (TD) | TD |
| 41 | Shelf | https://shelf.io | Knowledge management for gen-AI/CX, content quality for RAG | Ent | Custom | CCaaS/CRM | ? | API | V (named) — [getmacha Guru guide](https://www.getmacha.com/blog/guru-complete-guide) |
| 42 | KMS Lighthouse | https://kmslh.com | Knowledge management for contact centers with AI | Mid-Ent | Custom | CRM/CCaaS | ? (Israel-based, TD multilingual) | ? | V (domain) — [kmslh.com](https://kmslh.com/blog/best-ai-powered-knowledge-management/) |
| 43 | ClickUp Brain | https://clickup.com/ai | AI over ClickUp tasks/docs plus connected apps ("Connected Search") | SMB-Mid | Add-on per user (TD) | Drive, Slack, GitHub, etc. (TD) | Y (TD: ClickUp UI not RTL) | ClickUp API; MCP (TD) | V (ClickUp listed in KM leaders) — [Tracxn](https://tracxn.com/d/trending-business-models/startups-in-knowledge-management/__1UBPYM20gtsM_yazkJM5u1mq1ak0IfcwhqrUv3NYOKA/companies); product details TD |
| 44 | Taskade (Genesis / EVE) | https://www.taskade.com | AI workspace: notes, projects, agents; "clone a living knowledge dashboard" | SMB | Pro ~$10/mo for up to 10 users (vendor claim) | Imports, integrations | ? | API (TD) | V — [Taskade blog](https://www.taskade.com/blog/ai-second-brain-tools) |
| 45 | Docsie | https://www.docsie.io | Documentation/knowledge portal with AI | SMB-Mid | TD | ? | ? | ? | V (domain) — [Docsie](https://www.docsie.io/vs/guru-vs-slite/) |
| 46 | Helpjuice | https://helpjuice.com | Knowledge base software with AI search/writer | SMB-Mid | From ~$120-$249/mo (TD) | Slack, Zendesk, Salesforce (TD) | Y (TD: multilingual) | API | TD |
| 47 | Slab | https://slab.com | Team wiki with unified search across tools and AI answers | SMB-Mid | Free/Startup/Business (TD) | Drive, GitHub, Slack, Asana (TD) | ? | API | TD |
| 48 | Nuclino | https://www.nuclino.com | Lightweight team wiki with "Sidekick" AI | SMB | Free; Starter/Business (TD) | Limited | ? | API | TD |
| 49 | GitBook | https://www.gitbook.com | Docs/knowledge platform with AI search, MCP for docs | SMB-Mid | Free + paid sites (TD) | GitHub, GitLab | ? | Auto MCP server for published docs (TD) | TD |
| 50 | Archbee | https://www.archbee.com | Docs portal with AI answers | SMB | TD | GitHub | ? | API | TD |
| 51 | Coda AI (Superhuman/Grammarly) | https://coda.io | Doc-as-app with AI; Coda acquired by Grammarly (2024), group renamed Superhuman (2025) (TD) | SMB-Mid | TD | Packs (Slack, Jira, etc.) | ? | API | TD |
| 52 | Trainual | https://trainual.com | SOP/onboarding playbooks for small businesses with AI | SMB | Per-seat tiers (TD) | HRIS, Slack | ? | API | TD |
| 53 | Happeo | https://www.happeo.com | Intranet with AI search over Google Workspace | Mid | Custom (TD) | Google Workspace, M365 | ? | ? | TD |
| 54 | Simpplr | https://www.simpplr.com | AI-powered employee intranet | Mid-Ent | Custom | M365, Google, ServiceNow (TD) | Y (TD: multilingual) | ? | TD |
| 55 | Capacity | https://capacity.com | AI support automation + knowledge base for internal/external | SMB-Mid | TD | 100s via iPaaS (TD) | ? | API | TD |
| 56 | eGain | https://www.egain.com | Knowledge hub for customer service with AI | Ent | Custom | CRM/CCaaS | Y (TD) | API | TD |
| 57 | Spekit | https://www.spekit.com | Sales enablement + just-in-time knowledge with AI | Mid | Custom (TD) | Salesforce, Slack | ? | ? | TD |
| 58 | Starmind | https://www.starmind.ai | Expert-finding/knowledge network with AI | Ent | Custom | M365, Slack | ? | ? | TD |
| 59 | Zendesk Knowledge + AI agents | https://www.zendesk.com | Help center KB that powers Zendesk AI agents | SMB-Ent | Per agent + per automated resolution (TD) | Zendesk ecosystem | Y (TD: Arabic supported) | API | TD |

### Inferences
- The incumbents' defensibility argument has shifted from "where docs live" to "governance and verification of what AI says" (Guru tagline: "Stop running your business on confidently wrong AI").
- For SMBs already on Notion, Notion Business is the lowest-friction company brain; Slite/Guru suit teams that will maintain verified pages.

### Gaps
- "Lore" (named by user) could not be identified as a current company-knowledge product; moved to cache.
- Slite, Tettra, Document360, Stack Internal 2026 pricing not captured.
- Arabic/RTL support for Notion, Slite, Guru not confirmed.

---

## Q3. Second-brain / personal-to-team memory (Mem, Reflect, Tana, Capacities, Heptabase, Saner, Recall, NotebookLM, Supermemory, Rewind/Limitless, Granola, etc.)

### Takeaway
By Nov 2026 most second-brain apps (Notion, Capacities, Tana, Heptabase, Mem, Recall, BrainTube) ship MCP servers so Claude/ChatGPT can query them; several (Tana, Supermemory Brain, MemoryLake) explicitly market a personal-to-team "shared brain". Limitless (ex-Rewind) was acquired by Meta: Pendant sales stopped 5 Dec 2025 and Rewind was sunset. Mem relaunched as Mem 2.0 in early 2026.

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors / capture | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 60 | Mem (Mem 2.0) | https://get.mem.ai | AI-native notes app that auto-organizes and answers from your notes; relaunched early 2026 | Individual-SMB | Free (25 messages + 25 new notes/mo); Plus $9/mo; Pro $29/mo (checked 7 Nov 2026) | Quick capture, email forward, voice, meeting transcripts | ? | MCP (read-write) | V — [Taskade](https://www.taskade.com/blog/ai-second-brain-tools); [Littlebird](https://littlebird.ai/blog/best-second-brain-apps); [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 61 | Reflect | https://reflect.app | Networked daily notes with backlinks, end-to-end encryption, AI assistant | Individual | TD (~$10/mo) | Calendar, Kindle (TD) | ? | ? | V — [Littlebird](https://littlebird.ai/blog/best-second-brain-apps) |
| 62 | Tana | https://tana.inc | Supertag outliner that turns meetings into typed, permissioned team context for people and agents | Individual-SMB team | Free tier; paid (TD) | Meeting capture, calendar | ? | MCP server (read-write, e.g. Claude Code) | V — [Tana blog](https://tana.inc/blog/best-second-brain-apps-2026); [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 63 | Capacities | https://capacities.io | Object-typed notes (people, books, meetings) with AI assistant | Individual | Free + Pro (TD) | Readwise, calendar (TD) | ? | MCP (read-write) | V — [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026); [Littlebird](https://littlebird.ai/blog/best-second-brain-apps) |
| 64 | Heptabase | https://heptabase.com | Visual whiteboard knowledge base with AI | Individual | Paid (TD ~$9-12/mo) | PDFs, web | ? | MCP (read-write) | V — [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 65 | Saner.AI | https://www.saner.ai | AI second brain for notes, tasks and emails; ADHD-friendly | Individual | Free + paid (TD) | Gmail, calendar, Drive (TD) | ? | ? | V — [Saner.AI](https://www.saner.ai/blogs/10-best-second-brain-ai-apps) |
| 66 | Recall | https://www.getrecall.ai | Save-and-chat for articles, videos, podcasts; knowledge graph | Individual | Free $0 (unlimited saves, 10 AI summaries/mo, MCP/API); Plus $12/mo ($10 yearly); Max $48/mo ($38 yearly) | Browser extensions (Chrome/Firefox/Edge/Safari); iOS/Android beta | ? | MCP (8 tools, read-only as of Nov 2026); API | V — [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 67 | NotebookLM (+ NotebookLM Enterprise) | https://notebooklm.google | Google's source-grounded research notebook over a fixed set of sources | Individual-Ent | Free with Google account; Enterprise via Google Cloud (TD) | Drive, PDFs, web, YouTube | Y (TD: Arabic supported) | Enterprise API (TD) | V — [Saner](https://www.saner.ai/blogs/10-best-second-brain-ai-apps); [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 68 | Supermemory / Supermemory Brain | https://supermemory.ai/brain/ | Memory API for developers + "Brain": Slack-native shared team memory that learns in real time | SMB / dev | TD | Slack; API ingestion | ? | Yes - API + MCP | V — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software); [Slite](https://slite.com/learn/company-brain) |
| 69 | Granola | https://www.granola.ai | AI meeting notepad; team spaces & chat over meeting history | Individual-SMB | Free + Business per user (TD) | Calendar, Zoom/Meet/Teams audio, Slack, Notion, HubSpot (TD) | ? | MCP (TD); Merge UCL connects Granola in one click (V) | V/TD — [Merge X post](https://x.com/merge_api/status/2117649727835525382) |
| 70 | Littlebird | https://littlebird.ai | Auto-captures your active window and meetings into an encrypted cloud memory | Individual | TD | Screen + meetings | ? | ? | V (self-described) — [Littlebird](https://littlebird.ai/blog/best-second-brain-apps) |
| 71 | MemoryLake | https://memorylake.ai | Portable memory layer across ChatGPT/Claude/Gemini; personal "Memory Passport" + team memory; git-like versioning | Individual-SMB | Free personal tier | Enterprise connectors | ? | MCP, CLI, REST | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 72 | BrainTube | https://brain-tube.com | Compiled knowledge base from videos, podcasts, articles queryable by any AI | Individual | Free plan incl. MCP | YouTube, podcasts, web | ? | MCP read-write | V (self-described) — [BrainTube](https://brain-tube.com/compare/best-second-brain-apps-2026) |
| 73 | Obsidian (+ AI plugins / MCP) | https://obsidian.md | Local Markdown vault; with filesystem MCP becomes AI-readable brain | Individual | Free; Sync/Publish paid | Plugins | Y (RTL supported, TD) | Via community MCP | V — [Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026) |
| 74 | Limitless (ex-Rewind) - ACQUIRED by Meta | https://www.limitless.ai | Wearable Pendant + meeting memory; Meta acquisition; Pendant no longer sold since 5 Dec 2025; Rewind and non-Pendant features sunset; existing users get Unlimited free through 2026 | n/a (closed to new) | n/a | n/a | n/a | Developer API (legacy) | V — [limitless.ai](https://www.limitless.ai/) |
| 75 | Otter.ai | https://otter.ai | Meeting transcription + AI chat across a company's meeting history | SMB-Ent | Free/Pro/Business/Enterprise (TD) | Zoom, Teams, Meet, Salesforce, HubSpot (TD) | ? (TD: limited languages) | API, MCP (TD) | TD |
| 76 | Fireflies.ai | https://fireflies.ai | Meeting notetaker with "AskFred" over all meetings | SMB-Mid | Free + Pro/Business (TD) | Zoom, Teams, Meet, CRMs | Y (TD: 60+ languages incl. Arabic) | API, MCP (TD) | TD |
| 77 | Read AI | https://www.read.ai | Meeting, email and message copilot with cross-source search | SMB-Mid | Free + paid (TD) | Gmail, Outlook, Slack, Zoom (TD) | ? | ? | TD |
| 78 | Logseq | https://logseq.com | Open-source outliner second brain | Individual | Free | Local | ? | Plugins | V (listed) — [Saner](https://www.saner.ai/blogs/10-best-second-brain-ai-apps) |
| 79 | MyMind | https://mymind.com | Private visual save-everything brain with AI tagging | Individual | Paid (TD) | Browser | ? | ? | V (listed) — [Saner](https://www.saner.ai/blogs/10-best-second-brain-ai-apps) |

### Inferences
- Personal brains are converging on the same plumbing as company brains (MCP read/write, team sharing). For a 5-20 person SMB, Tana, Notion, Mem or Supermemory Brain can act as a lightweight company brain without an enterprise contract.
- Meta's Limitless deal removed one of the few "capture everything" products; Littlebird/screen-capture tools fill the gap.

### Gaps
- Granola, Reflect, Capacities, Heptabase, Tana prices not verified this session.
- Arabic support for nearly all second-brain apps unknown.

---

## Q4. The 2026 "company brain" wave (Hyper, Sentra, Coworker, Gyld, Klikflo, company-brain.ai, Agently, Multiplier, Growy, Merge for Workforce, Cerenovus, Savant, ClickUp Brain, Dust, Onyx Cloud, etc.)

### Takeaway
"Company Brain" was formalized as idea #05 in Y Combinator's Summer 2026 Request for Startups (Tom Blomfield), citing Garry Tan's open-source GBrain (MIT, released 5 Apr 2026, ~23.6K stars); antecedents were Foundation Capital's "context graphs" essay (22 Dec 2025) and Karpathy's "LLM wiki" gist. A cohort of agent-first vendors now sells MCP-served, permissioned, versioned company memory: Hyper (YC Spring 2026), Sentra ($16/user Team plan), Coworker (OM2), Gyld, Klikflo, Company Brain (company-brain.ai), Sento, Carrara, Pletor, Merge for Workforce's Universal Context Layer, plus developer memory infra (Mem0, Zep, Cognee, Letta). Typical managed pricing: ~$10-100/seat/mo, increasingly usage or per-agent.

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 80 | Hyper | https://www.ycombinator.com/companies (Hyper, YC S/Spring 2026) | "The self-driving company brain": reads Slack, Notion, Gmail, calendars, PRs; synthesizes and dedupes into a continuously updated company picture fed back to your AI tools | SMB-Mid | Not found ($1K MRR in 12 days reported) | Slack, Notion, Gmail, Calendar, GitHub PRs | ? | Plugs into existing AI tools (MCP implied) | V — [Startground YC Spring 2026 list](https://startground.com/y-combinator-spring-2026-startups/); [Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026); [Colrows](https://colrows.com/blogs/yc-company-brain-rfs/) |
| 81 | Sentra (sentra.app) | https://www.sentra.app | Managed organization memory: resolves email/chat/meetings/docs/ERP/CRM/HRIS/BI into time-stamped facts; raises contradictions; serves people and agents (not Sentra.io the security company) | SMB-Ent | Team plan 2-20 people $16/user/mo; Enterprise custom | 200+ integrations (email, Slack, meetings, docs, GitHub, Linear, CRM, ERP, HRIS, BI) | ? | MCP + REST; SOC 2 Type II, ISO 27001; cloud/VPC/air-gapped | V — [Sentra ranking](https://www.sentra.app/articles/best-company-brain-platforms); [Sentra Glean alternatives](https://www.sentra.app/articles/glean-alternatives) |
| 82 | Coworker (coworker.ai) | https://coworker.ai | Enterprise AI coworker built on "OM2" living organizational memory; search + multi-step task execution | Mid-Ent | Not found | 50+ connectors | ? | Coworker MCP; SOC 2 Type II, GDPR | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 83 | Gyld | https://gyld.ai | Knowledge layer assembled from existing apps, exposed as MCP servers to Claude/ChatGPT/Codex/Cursor; per-source private/team/company permissions | SMB (founders, eng teams) | Not found | Your existing apps (selected sources only) | ? | MCP-first | V — [Gyld blog](https://gyld.ai/blog/best-company-brain-software-in-2026-9-tools-that-give-ai-real-business-context); [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 84 | Klikflo | https://klikflo.com (URL not verified) | Auto-assembles an operating model of the business from tools, docs and communications | SMB-Mid | Not found | Tools, documents, comms | ? | Yes (agent access) | V (named) — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 85 | Company Brain (company-brain.ai) | https://www.company-brain.ai | Delivers products, processes, business rules, team and brand voice to any AI via MCP | SMB | Not found | Company content | ? | MCP | V — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 86 | Merge for Workforce - Universal Context Layer | https://www.merge.dev/workforce | Governed company context + capabilities delivered through employees' existing AI tools; one-click Slack/Granola/Notion into a shared brain; started with token-spend control | Mid-Ent | Not found | Merge's unified-API catalog (Slack, Granola, Notion, HRIS, CRM, etc.) | ? | Works with any AI tool/agent (MCP); SOC 2 Type II, ISO 27001 | V — [Merge blog](https://www.merge.dev/blog/universal-context-layer); [Merge company-brain explainer](https://www.merge.dev/blog/what-is-a-company-brain-how-it-gives-enterprise-ai-company-context) |
| 87 | MultiplierAI | https://multiplierai.ai | Revenue-scoped "company brain": agents (Recon, Strategist, Closer) map AI-search demand and build assets; client-owned database | SMB-Mid | Not found (service-led) | AI answer engines, pipeline data | ? | ? | V (self-described) — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 88 | Sento | https://www.sentohq.com | Governed context layer: owned, versioned knowledge entities read by your existing assistants over MCP; couriers refresh numbers | SMB-Mid (10-200 people) | Early access; free 1-hour onboarding | Notetakers, Slack, existing sources | ? | MCP | V — [Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026) |
| 89 | Carrara | (URL not captured) | Dedicated company brain: shared memory in Neon Postgres replicated to a native macOS app; human-approved memories | SMB | Not found | ? | ? | Custom MCP server | V — [Slite solutions](https://slite.com/learn/company-brain-solutions) |
| 90 | Pletor | (URL not captured) | Dedicated company brain, model/platform-independent | SMB-Mid | Not found | ? | ? | ? | V (named only) — [Slite solutions](https://slite.com/learn/company-brain-solutions) |
| 91 | Plek AI | https://www.ycombinator.com/companies/industry/ai | "AI company brain for private-equity value creation" (YC F2026, 2 employees) | PE portfolios | Not found | Employee census uploads etc. | ? | ? | V — [YC directory](https://www.ycombinator.com/companies/industry/ai) |
| 92 | PromptQL (Hasura) | https://promptql.io | Permissioned data/agent layer framing the brain as a model over company data agents query | Mid-Ent | TD | Databases, SaaS | ? | API/MCP | V (named) — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 93 | Vectorize | https://vectorize.io | RAG-pipeline platform; published "how to build a company brain" guide | Dev teams | Free + usage (TD) | Many sources | ? | API, MCP (TD) | V (named) — [MultiplierAI](https://multiplierai.ai/resources/company-brain-software) |
| 94 | Mem0 (platform) | https://mem0.ai | Most-adopted agent memory library (~67.8K GitHub stars, Apache 2.0) with hosted platform | Dev | Free + paid hosted (TD) | Conversation ingestion | n/a | Hosted MCP server with 11 tools; API | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 95 | Zep | https://www.getzep.com | "Unified context layer for enterprise data": temporal context graph per user/account; Graphiti OSS | Dev / Mid-Ent | TD | Chat, business data | n/a | API; SOC 2 Type II, HIPAA BAA, VPC | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| 96 | Cognee | https://www.cognee.ai | Open-source graph memory "for agents, teams and people" (~32.8K stars, Apache 2.0) + enterprise BYOC | Dev / Mid-Ent | OSS free; Enterprise (SSO, SLA, BYOC) | Slack, GitHub, Linear | n/a | Cognee MCP (remember/recall/forget) | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms); [cognee](https://www.cognee.ai/glean-alternatives) |
| 97 | Dust (repeat; see #15) | https://dust.tt | Agent-first workspace; frequently ranked as a company brain | SMB-Ent | EUR 24-30 | 100+ | Y | MCP | V |
| 98 | Onyx Cloud (repeat; see #14) | https://onyx.app | OSS Glean-clone, hosted | SMB-Mid | $20 | 40+ | Y (LLM) | API | V |
| 99 | ClickUp Brain (repeat; see #43) | https://clickup.com/ai | Bundled-incumbent brain | SMB-Mid | TD | TD | ? | TD | TD |

Context facts:
- YC Summer 2026 RFS "Company Brain" by Tom Blomfield asks for "Garry's G-Brain, but for every business in the world" and says it is not company search or "a chatbot bolted onto a wiki" — [Slite](https://slite.com/learn/company-brain).
- GBrain open-sourced 5 Apr 2026 under MIT; 23.6K stars; Hyper "$1K MRR in 12 days" — [Colrows](https://colrows.com/blogs/yc-company-brain-rfs/) (vendor blog; traction figure unverified elsewhere).
- Slite survey: 70% of teams know the term, 20% have one — [Slite](https://slite.com/learn/company-brain).
- Managed platforms ~$10-$100/seat/mo; agent-first products increasingly priced per usage/agent — [MultiplierAI citing Slite](https://multiplierai.ai/resources/company-brain-software).
- Slite's four families: self-hosted patterns (GBrain, Sylph), memory SDKs (mem0, Letta, Zep), bundled incumbents (Notion AI, Rovo, Slack AI, Glean, ChatGPT/Claude Enterprise), dedicated brains (Slite Agent, Carrara, Pletor) — [Slite solutions](https://slite.com/learn/company-brain-solutions).

### Inferences
- Nearly all "comparison" content in this category is vendor-authored (Sentra, Slite, Gyld, Sento, MultiplierAI, Dust, Tana); rankings are self-serving and should be weighted accordingly.
- The SMB-relevant, published-price entrants are few: Sentra Team ($16, 2-20 people) is the only explicit SMB tier found; Sento offers free onboarding in early access.
- The wave splits into "auto-ingest" (Hyper, Sentra, Coworker, Klikflo) vs "governed/curated" (Sento, Carrara, Slite, Guru) — a key buying question is "how expensive is a wrong answer?" ([Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026)).

### Gaps
- Agently, Growy, Cerenovus, Savant (named by user) could not be verified this session as company-brain vendors; parked in cache with notes.
- Hyper's own domain and pricing not found. Klikflo, Carrara, Pletor URLs not confirmed.
- No Arabic support statements found for any 2026-wave vendor.

---

## Q5. SMB "chatbot on your docs" builders (Chatbase, CustomGPT, Botpress, Voiceflow, Stack AI, Mendable, DocsBot, SiteGPT, Elfsight, Tidio Lyro, etc.)

### Takeaway
A crowded, cheap tier ($15-$150/mo entry) of no-code builders lets an SMB upload docs/websites and deploy a chatbot on web/WhatsApp. Pricing models split between message credits (Chatbase, Botsonic, YourGPT), per-resolution (Intercom Fin $0.99, eesel ~$0.40/ticket) and platform + AI spend (Botpress). Most are customer-facing rather than internal company brains, but many can be used internally.

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors / channels | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 100 | Chatbase | https://www.chatbase.co | No-code AI agent trained on your data, multi-model, human handoff | SMB-Mid | Free (50 msg/mo); Hobby $40; Standard $150 (4,000 credits, 3 members, API); Pro $500 | Website, files, Notion, Stripe, Zendesk, Slack, WhatsApp (TD) | Y (TD: 95+ languages) | API | V — [Chatbase](https://www.chatbase.co/blog/best-chatbot-software); [Docuyond](https://docuyond.com/blog/ai-chatbot-pricing-small-business); [filipkonecny](https://filipkonecny.com/blog/best-business-ai-agent/) |
| 101 | CustomGPT.ai | https://customgpt.ai | RAG chatbot builder with citations and anti-hallucination focus | SMB-Mid | $99 then $499 tier (5x jump) | 1,400+ doc formats, sitemaps, Drive (TD) | Y (TD: 90+ languages) | API; MCP server (TD) | V — [HelpJet](https://helpjet.com/blog/chatbase-alternatives) |
| 102 | Botpress | https://botpress.com | Developer-friendly agent builder with knowledge bases | SMB-Ent | Free; Plus $89 + AI spend; Team $495 + AI spend; Enterprise from $2,000 + AI spend | Web, WhatsApp, Messenger, Slack, Teams | Y (TD) | API, SDK | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 103 | Voiceflow | https://www.voiceflow.com | Collaborative agent design platform with knowledge base | SMB-Ent | Free + Pro/Business (TD) | Web, voice, APIs | Y (TD) | API | TD |
| 104 | Stack AI | https://www.stack-ai.com | No-code enterprise AI agent/workflow builder over company data | Mid-Ent | Free + Enterprise (TD) | SharePoint, Drive, Notion, Salesforce, DBs (TD) | ? | API | TD |
| 105 | DocsBot AI | https://docsbot.ai | ChatGPT-style bots trained on docs for support and internal Q&A | SMB | From ~$19-49/mo (TD) | Website, Drive, Notion, Zendesk (TD) | Y (TD) | API | TD |
| 106 | SiteGPT | https://sitegpt.ai | Website-trained chatbot for support | SMB | $259 plan caps 40k msgs/mo; $39/mo extra to remove branding (Reddit user report) | Website, files | ? | API (TD) | V (weak, Reddit) — [Reddit](https://www.reddit.com/r/ChatGPT/comments/1r1i2n5/chatbase_alternative_heres_what_i_found_after/) |
| 107 | Tidio (Lyro AI agent) | https://www.tidio.com | SMB live chat + Lyro AI agent answering from your FAQ/knowledge | SMB | Free + Lyro add-on per conversation (TD) | Shopify, WordPress, Messenger, Instagram (TD) | Y (TD) | API | TD |
| 108 | Intercom Fin | https://www.intercom.com/fin | AI agent resolving support from your help content; works with any helpdesk | SMB-Ent | $0.99 per resolution (50/mo min); $29/seat if using Intercom helpdesk | Zendesk, Salesforce, Intercom | Y (TD: 45 languages incl. Arabic) | API, MCP (TD) | V — [IrisAgent](https://irisagent.com/blog/best-chatbase-alternatives/); [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 109 | Jotform AI Agents | https://www.jotform.com/ai/agents/ | No-code agents trained on your docs across web, phone, WhatsApp | SMB | Free; Bronze $34, Silver $39, Gold $99 (annual) | Forms, web, WhatsApp, voice | Y (TD) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 110 | Lindy | https://www.lindy.ai | AI agents + workflow automation incl. knowledge-base agents | SMB | Free; Pro $49.99 (5,000 credits); Business $199.99 (20,000) | Gmail, Slack, CRMs, 1,000s via integrations | ? | API/webhooks | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 111 | Botsonic (Writesonic) | https://writesonic.com/botsonic | No-code chatbot trained on your data | SMB | Starter $16; Professional $41; Advanced $249 (annual) | Web, files, Drive (TD) | Y (TD) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 112 | Ingest AI | https://ingestai.io | Data ingestion + AI chatbots | SMB | Basic $25; Pro $60 (annual) | Notion, Drive, websites (TD) | ? | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 113 | Denser AI | https://denser.ai | Knowledge automation chatbots/search for support | SMB-Mid | Starter $29; Standard $119; Business $399 (annual) | Web, docs | ? | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 114 | YourGPT | https://yourgpt.ai | Branded ChatGPT-like chatbot on your data | SMB | Essential $39; Professional $79; Advanced $349 (annual) | Web, WhatsApp, Telegram | Y (TD) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 115 | eesel AI | https://www.eesel.ai | AI trained on company knowledge for helpdesk + internal Slack/Teams answers | SMB-Mid | Pay-as-you-go ~$0.40/ticket, no seat fees; $50 trial | Zendesk, Freshdesk, Confluence, Drive, Notion, Slack | ? | ? | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 116 | HelpJet | https://helpjet.com | Helpdesk + AI bot trained on your KB | SMB | Free (1 bot, 100 interactions); Pro $29/mo (~$23 annual; 3 bots, 1,000 interactions) | KB, website | ? | ? | V — [HelpJet](https://helpjet.com/blog/chatbase-alternatives) |
| 117 | Landbot | https://landbot.io | No-code chatbot builder (web, WhatsApp) with AI | SMB | Starter EUR 40; Pro EUR 100; WhatsApp Pro EUR 200; Business EUR 400 (20% off annual) | Web, WhatsApp | Y (TD) | API | V — [HelpJet](https://helpjet.com/blog/chatbase-alternatives) |
| 118 | Chat Data | https://www.chat-data.com | Chatbase-like builder with more channels + live handoff | SMB | TD | Web, WhatsApp, Slack, Discord | ? | API | V (self-described) — [Chat Data](https://www.chat-data.com/vs/chatbase) |
| 119 | SiteSpeak AI | https://sitespeak.ai | Website chatbot for AI customer support | SMB | TD | Website | ? | ? | V (self-described) — [SiteSpeak](https://sitespeak.ai/chatbase-alternative) |
| 120 | Docuyond | https://docuyond.com | Agent trained on your KB to deflect support questions | SMB | Not captured | Docs | ? | ? | V (self-described) — [Docuyond](https://docuyond.com/blog/ai-chatbot-pricing-small-business) |
| 121 | Teammates.ai | https://teammates.ai | AI teammates for support, sales, recruiting in 50+ languages | SMB-Mid | Free plan available | Web, WhatsApp, voice | Y (50+ languages; active in Saudi market) | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 122 | ManyChat | https://manychat.com | Social/DM automation (Instagram, WhatsApp, Messenger) with AI | SMB | Free; Pro from $15/mo | IG, FB, WhatsApp, TikTok | Y (TD) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 123 | Ada | https://www.ada.cx | Enterprise AI customer service agent | Ent | Contact sales | CRM/helpdesk | Y (TD: 50+ languages) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 124 | Yellow.ai | https://yellow.ai | Omnichannel enterprise conversational AI | Mid-Ent | Free version; contact sales | 100+ channels | Y (TD: strong in MENA/India) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 125 | Haptik (Jio) | https://www.haptik.ai | Enterprise conversational AI for CX | Ent | Contact sales | WhatsApp, web | Y (TD: active in MENA) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| 126 | Fini | https://www.usefini.com | AI support agent focused on ticket resolution and backend actions | Mid | TD | Zendesk, Intercom, Salesforce | ? | ? | V (self-described) — [Fini](https://www.usefini.com/guides/top-chatbase-alternatives) |
| 127 | Decagon | https://decagon.ai | Enterprise AI customer support agents | Ent | Custom | Helpdesks, CRMs | ? | API | V (named) — [Fini](https://www.usefini.com/guides/top-chatbase-alternatives) |
| 128 | IrisAgent | https://irisagent.com | AI support automation over tickets/KB | Mid | Flexible usage/resolution plans | Zendesk, Salesforce, Jira | ? | ? | V (self-described) — [IrisAgent](https://irisagent.com/blog/best-chatbase-alternatives/) |
| 129 | Gorgias AI Agent | https://www.gorgias.com | E-commerce helpdesk AI agent trained on store data | SMB-Mid | Per resolution (TD) | Shopify, BigCommerce | ? | API | TD |
| 130 | HubSpot Breeze (Customer Agent / Knowledge) | https://www.hubspot.com/products/artificial-intelligence | SMB CRM's AI agents answering from KB and CRM | SMB-Mid | Included/credits in Service Hub (TD) | HubSpot | Y (TD) | API, MCP (TD) | TD |
| 131 | Freshworks Freddy AI | https://www.freshworks.com/freddy-ai/ | AI agents for Freshdesk/Freshservice | SMB-Mid | Per session/agent (TD) | Freshworks | Y (TD: Arabic supported) | API | TD |
| 132 | Crisp (MagicReply/AI agent) | https://crisp.chat | SMB chat inbox with AI trained on KB | SMB | From ~$45-95/mo per workspace (TD) | Web, WhatsApp, IG | Y (TD) | API | TD |
| 133 | Kapa.ai | https://www.kapa.ai | AI assistant trained on technical docs for dev-tool companies | Mid | Custom | Docs, GitHub, Discourse, Slack | ? | API, MCP (TD) | TD |
| 134 | Inkeep | https://inkeep.com | AI search/chat on docs + internal support copilot | Mid | Custom (TD) | Docs, Slack, Zendesk | ? | API, MCP (TD) | TD |

### Inferences
- For an SMB wanting an internal company brain on a budget, eesel AI (Slack/Teams + helpdesk), Chatbase, CustomGPT and Lindy are the most adaptable; most others are optimized for external customer support.
- Credit-based plans can silently stop the bot when credits run out ([IrisAgent](https://irisagent.com/blog/best-chatbase-alternatives/)); per-resolution pricing rises with success.

### Gaps
- Voiceflow, Stack AI, DocsBot, Tidio Lyro, Elfsight current prices not verified. Mendable status (believed folded into Firecrawl, TD) moved to cache. Elfsight moved to cache (widget-level, marginal).

---

## Q6. MENA / Arabic vendors (DXwand, WideBot, Gaia, Arabic.ai, Mozn, Maqsam, Arabot, Lucidya, etc.)

### Takeaway
Arabic-first vendors are mostly customer-service/conversational-AI platforms with knowledge mining (DXwand, WideBot, Labiba, Arabot, Hams.ai, Elbi) or sovereign enterprise AI (Mozn, Arabic.ai, HUMAIN). Data residency in-Kingdom is a primary buying criterion; Arabic.ai joined Microsoft's Saudi Arabia East Azure region (in-Kingdom residency from Nov 2026) and received a HUMAIN investment (Sep 2026). No MENA vendor positions explicitly as a "company brain" yet.

### Cited Findings

| # | Name | URL | One-line description | Size | Pricing (public) | Key connectors / channels | Arabic | API/MCP | Ver. / Source |
|---|---|---|---|---|---|---|---|---|---|
| 135 | DXwand | https://dxwand.com | Cairo/Dubai conversational AI + knowledge mining for customer service and employee assistance; dialect-aware | Mid-Ent, gov | Annual subscriptions $50k-$400k by volume (2024); >$5M ARR in 2023; $4M Series A (Shorooq, Algebra) Jan 2024 | Omnichannel text+voice | Native (multiple dialects) | API (TD) | V — [TechCrunch](https://techcrunch.com/2024/01/25/dxwand-raises-4m-to-scale-its-conversational-ai-platform-for-enterprises-in-mena/) |
| 136 | WideBot | https://widebot.ai | Arabic-first "AI-as-a-service" conversational/enterprise AI; Riyadh + Cairo | SMB-Ent | Not found; $3M pre-Series A (Feb 2025) | WhatsApp, web, Messenger (TD) | Native | API (TD) | V — [WideBot blog](https://widebot.ai/blog?6088891a_page=4&a0359bf4_page=2); [LinkedIn brief](https://www.linkedin.com/pulse/technology-transaction-brief-egyptian-ai-startup-widebot-closes-xv07f) |
| 137 | Arabic.AI | https://arabic.ai | Arabic enterprise LLM/AI platform; Azure Saudi Arabia East strategic partner (Oct 2026, residency from Nov 2026); HUMAIN investment Sep 2026; Lenovo MoU at LEAP 2026 | Ent, gov | Not found | Azure | Native | API (TD) | V — [Arabic.ai newsroom](https://arabic.ai/company/newsroom/) |
| 138 | MOZN | https://www.mozn.ai | Sovereign Arabic-native enterprise AI (public finance, fraud, regulation, procurement); Riyadh | Ent, gov | Not found | On-prem/sovereign | Native | ? | V — [Mozn](https://www.mozn.ai/industries/public-sector) |
| 139 | Maqsam | https://maqsam.com | Call-center/customer-service software with an Arabic AI agent automating support and sales | SMB-Mid | Not found | Telephony, WhatsApp (TD) | Native | API (TD) | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 140 | Arabot | https://arabot.io | Arabic AI conversational platform | Mid-Ent | Not found | Web, WhatsApp (TD) | Native | API (TD) | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 141 | Lucidya | https://lucidya.com | AI-native CX management: social listening, omnichannel engagement, autonomous support | Mid-Ent | Not found | Social, WhatsApp, email | Native | API (TD) | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 142 | Labiba | https://labiba.ai | Conversational AI, voice agents, customer engagement for Saudi orgs | Mid-Ent, gov | Not found | Voice, chat | Native | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 143 | Labeah AI | (URL not captured) | Arabic-native chatbots, callbots, voice AI for government/enterprise in KSA | Ent, gov | Not found | Voice, chat | Native | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 144 | Hams.ai | https://hams.ai | AI customer-service platform for Saudi enterprises: voice, chat, WhatsApp in Arabic + English | Mid-Ent | Not found | Voice, chat, WhatsApp | Native | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 145 | Elbi (Elbetron) | https://a-i.sa | Bilingual assistant answering from approved documents on chat/voice/WhatsApp; data kept in KSA | SMB-Mid | Not found (cost guide published) | Docs, WhatsApp, voice | Native (Saudi dialect) | ? | V (self-described) — [Elbi](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 146 | LeapAI | (URL not captured) | Saudi CX platform: omnichannel contact center, WhatsApp Business, AI chatbots, integrations | SMB-Mid | Not found | WhatsApp, contact center | Native | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 147 | Sarj AI | (URL not captured) | Enterprise AI automation for customer interactions, document intelligence, back-office | Mid-Ent | Not found | ? | Native (KSA market) | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 148 | HUMAIN Chat (ALLaM) | https://humain.ai | Saudi Arabic-first consumer chat app (launched Aug 2025) on ALLaM; HUMAIN also invests in Arabic.ai | Consumer (not deployable for business) | n/a | n/a | Native | ? | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/); [Arabic.ai](https://arabic.ai/company/newsroom/) |
| 149 | Wittify.ai | https://wittify.ai | Arabic-first conversational AI platform for voice/text/multimodal agents | SMB-Mid | Not found | Voice, text | Native | ? | V — [VentureRadar](https://www.ventureradar.com/startups/arabic%20ai) |
| 150 | Munsit | (URL not captured) | Arabic speech recognition, 25+ dialects, built/hosted in UAE (component, not a brain) | Dev | Not found | API | Native | API | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |
| 151 | Wati | https://www.wati.io | AI-supported WhatsApp business messaging (marketing, sales, support with KB bot) | SMB | Tiered (TD) | WhatsApp, Shopify, HubSpot | Y (widely used in GCC) | API | V — [Elbi shortlist](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/) |

### Inferences
- An Arabic-speaking SMB wanting an internal company brain today would likely combine a global brain (Copilot/Gemini/ChatGPT/Claude, whose LLMs handle Arabic) with an Arabic-first customer-facing vendor (Elbi, WideBot, Maqsam, Hams.ai) — there is a visible gap for an Arabic-first internal company brain.
- Sovereignty (in-Kingdom hosting) increasingly decides procurement in KSA government, banking, healthcare ([Elbi](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/)).

### Gaps
- "Gaia" (named by user) not identified as a MENA knowledge AI vendor this session — parked in cache.
- MAGNiTT/Wamda were not queried (tool-call budget); 2026 funding rounds for DXwand/WideBot not found beyond 2024/2025 rounds.
- No public pricing for any MENA enterprise vendor except DXwand's 2024 contract range.
