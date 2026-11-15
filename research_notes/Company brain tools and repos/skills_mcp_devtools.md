# Skills, MCP servers, plugins and AI dev tools for a company brain service (catalogue as of 15 Nov 2026)

Notes for the report writer:
- **Where star counts come from.** Most counts are copied from the `jqueryscript/awesome-claude-code` README ([jq list](https://github.com/jqueryscript/awesome-claude-code)), pulled raw on 2026-11-15. That list's snapshot date is unknown, so treat the numbers as approximate. Some look inflated, for example ECC at 222k and andrej-karpathy-skills at 175k. Other counts are cited inline. The GitHub API, GraphQL and shields.io were all blocked in this session, so I could not verify any star count independently.
- **Where descriptions come from.** One-line descriptions are paraphrased from the awesome-list entries cited. The main ones are [punkpeye/awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) ("PP list"), [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) ("HRH list"), [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) ("Composio skills list"), [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) and [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills).
- **Unverified entries.** Anything marked "(prior knowledge; not re-verified)" is a well-known project. I did not re-check it this session.
- **"Helps with" tags.** Each entry ends with tags: connectors, documents, search, memory, whatsapp, arabic, deploy, devtool, governance.
- **Weaker entries.** Weaker, duplicate and marginal entries are in `skills_mcp_devtools_cache.md`.

## 1. Agent Skills ecosystem (official repos, marketplaces, document/research/data skills)

### Takeaway
Agent Skills (folders with a `SKILL.md` file) are now an open standard ([agentskills.io](http://agentskills.io)) shared by Claude, Codex, Gemini CLI, Cursor and others.
- **Official sources:** anthropics/skills (about 150k stars), Anthropic's plugin marketplaces (claude-plugins-official, knowledge-work-plugins, financial-services), Google's google/skills and OpenAI's new openai/plugins repo. OpenAI deprecated its openai/skills repo.
- **Discovery:** the big catalogues are the awesome-lists, skills.sh / officialskills.sh, sickn33's 1,900+ skill catalogue and vercel-labs/add-skill.
- **For a company brain:** the most useful skills are the Anthropic document skills (docx, pdf, xlsx, pptx), Google Workspace `gws` skills, Notion skills, research skills and memory/second-brain skills.

### Cited Findings

**Official / vendor skill repos and plugin marketplaces**
- **anthropics/skills.** https://github.com/anthropics/skills, about 150.6k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
  - Anthropic's reference skills plus the Agent Skills spec and template.
  - Includes the production docx, pdf, pptx and xlsx skills that power Claude's file creation.
  - Install with `/plugin marketplace add anthropics/skills`, then `/plugin install document-skills@anthropic-agent-skills` ([repo README](https://raw.githubusercontent.com/anthropics/skills/main/README.md)).
  - Helps with: documents, devtool.
- **docx skill.** https://github.com/anthropics/skills/tree/main/skills/docx. Creates, edits and analyzes Word documents, including tracked changes, comments and formatting preservation ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: documents.
- **pdf skill.** https://github.com/anthropics/skills/tree/main/skills/pdf. Extracts text and tables, creates PDFs, merges and splits files, and handles forms ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: documents.
- **xlsx skill.** https://github.com/anthropics/skills/tree/main/skills/xlsx. Handles formulas, formatting, data analysis and charts ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: documents, data.
- **pptx skill.** https://github.com/anthropics/skills/tree/main/skills/pptx. Builds decks with layouts, templates and charts ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: documents.
- **mcp-builder skill.** https://github.com/anthropics/skills/tree/main/skills/mcp-builder. A guide to building high-quality MCP servers for external APIs; useful for building custom Odoo, Zoho or WhatsApp connectors ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: connectors.
- **skill-creator.** https://github.com/anthropics/skills/tree/main/skills/skill-creator. An interactive skill-authoring tool ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: devtool.
- **internal-comms skill.** https://github.com/anthropics/skills/tree/main/skills/internal-comms. Writes status reports, newsletters and FAQs in company formats ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: documents.
- **webapp-testing skill.** https://github.com/anthropics/skills/tree/main/skills/webapp-testing. Playwright UI testing ([travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: devtool.
- **anthropics/claude-plugins-official.** https://github.com/anthropics/claude-plugins-official, about 30.1k stars.
  - The official Claude Code plugin marketplace.
  - Third-party submissions moved to claude.ai/directory/manage, and `marketplace.json` is being reduced to Anthropic's own plugins.
  - Install with `/plugin install {name}@claude-plugins-official` ([repo README](https://raw.githubusercontent.com/anthropics/claude-plugins-official/main/README.md); stars from [jq list](https://github.com/jqueryscript/awesome-claude-code)).
  - Helps with: connectors, devtool.
- **anthropics/knowledge-work-plugins.** https://github.com/anthropics/knowledge-work-plugins, about 20.6k stars. Open-source plugins for knowledge workers in Claude Cowork and Claude Code ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: connectors, documents.
- **anthropics/financial-services.** https://github.com/anthropics/financial-services, about 31.1k stars. Reference agents, skills and data connectors for financial-services workflows ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: connectors, documents.
- **anthropics/claude-cookbooks (skills folder).** https://github.com/anthropics/claude-cookbooks/tree/main/skills, about 45.4k stars for the whole repo ([jq list](https://github.com/jqueryscript/awesome-claude-code); [travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: devtool.
- **Claude Skills API.** `/v1/skills` lets you upload custom skills through the API ([travisvn list](https://github.com/travisvn/awesome-claude-skills) → https://platform.claude.com/docs/en/api/beta/skills). Helps with: deploy.
- **openai/skills (deprecated).** https://github.com/openai/skills.
  - Codex skill catalogue with `.system`, `.curated` and `.experimental` folders, installed with `$skill-installer`.
  - Deprecated in favour of https://github.com/openai/plugins and the Codex "Build plugins" guide ([repo README](https://raw.githubusercontent.com/openai/skills/main/README.md)).
  - Helps with: devtool.
- **openai/plugins.** https://github.com/openai/plugins. The current home for Codex skill and plugin examples ([openai/skills README](https://raw.githubusercontent.com/openai/skills/main/README.md)). Helps with: devtool.
- **google/skills.** https://github.com/google/skills, about 13.7k stars. Agent Skills for Google products ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: connectors.
- **Google Workspace CLI skills.** gws-drive, gws-gmail, gws-sheets, gws-docs, gws-calendar, gws-slides, gws-tasks and gws-admin-reports. Official skills for driving Workspace through the `gws` CLI ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills) → https://officialskills.sh/googleworkspace). Helps with: connectors (Drive/Gmail/Sheets).
- **Notion official skills.** Listed under "Skills by Notion" ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: connectors.
- **Microsoft official skills.** Listed under "Skills by Microsoft" ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: connectors.
- **Supabase skill.** supabase/postgres-best-practices ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: deploy, data.
- **Neon skills.** neon-postgres, claimable-postgres and egress-optimizer ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: deploy.
- **ClickHouse skills.** Best practices, chdb-sql, chdb-datastore and clickhousectl ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: data.
- **Firecrawl skills.** firecrawl-build, -scrape, -search, -interact and -alexandria ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: search, ingestion.
- **Stripe skills.** stripe-best-practices and upgrade-stripe ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)). Helps with: connectors.
- **huggingface/skills.** https://github.com/huggingface/skills, about 10.7k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **vercel-labs/agent-skills.** https://github.com/vercel-labs/agent-skills, about 27.9k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: deploy.
- **vercel-labs/add-skill.** https://github.com/vercel-labs/add-skill, about 22.3k stars. Installs agent skills from any git repo onto your coding agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **MiniMax-AI/skills.** https://github.com/MiniMax-AI/skills, about 12.6k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **trailofbits/skills.** https://github.com/trailofbits/skills, about 5.7k stars. Security-audit skills ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: governance.
- **NVIDIA/SkillSpector.** https://github.com/NVIDIA/SkillSpector, about 8.4k stars. Security scanner for agent skills that flags vulnerabilities and risky instructions; useful before installing community skills into a company brain ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: governance.

**Skill directories / marketplaces / awesome lists**
- **agentskills.io.** http://agentskills.io. The Agent Skills open standard, referenced by both Anthropic and OpenAI ([anthropics/skills README](https://raw.githubusercontent.com/anthropics/skills/main/README.md); [openai/skills README](https://raw.githubusercontent.com/openai/skills/main/README.md)).
- **skills.sh.** https://skills.sh. A skills directory with per-repo badges (shown on the anthropics/skills README) ([repo README](https://raw.githubusercontent.com/anthropics/skills/main/README.md)).
- **officialskills.sh.** https://officialskills.sh. A directory of vendor-official skills, used as the link target in the VoltAgent list ([VoltAgent list](https://github.com/VoltAgent/awesome-agent-skills)).
- **VoltAgent/awesome-agent-skills.** https://github.com/VoltAgent/awesome-agent-skills. Large list with official skills from Anthropic, Google, Stripe, Supabase, Notion, Microsoft, OpenAI, Neon, ClickHouse, Firecrawl, Sentry, Hugging Face and others (the README is about 244 KB). Helps with: discovery.
- **travisvn/awesome-claude-skills.** https://github.com/travisvn/awesome-claude-skills. Curated list plus official documentation links.
- **ComposioHQ/awesome-claude-skills.** https://github.com/ComposioHQ/awesome-claude-skills.
  - Includes Composio-powered app-automation skills for Notion, Slack, Zoho CRM, WhatsApp, Teams, Box and others, plus a "Connect" skill for 1,000+ apps.
  - Helps with: connectors, whatsapp.
- **BehiSecc/awesome-claude-skills.** https://github.com/BehiSecc/awesome-claude-skills. Another curated list (README downloaded 2026-11-15).
- **sickn33/agentic-awesome-skills.** https://github.com/sickn33/agentic-awesome-skills, about 43.7k stars. Catalogue of 1,900+ skills with a CLI, a local MCP server and plugins for skill discovery ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: discovery.
- **sickn33/antigravity-awesome-skills.** https://github.com/sickn33/antigravity-awesome-skills, about 40.7k stars. 130+ skills for Claude Code, Antigravity and Cursor ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **numman-ali/openskills.** https://github.com/numman-ali/openskills, about 10.4k stars. Universal skills loader for any coding agent ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **AgenticResourceRegistry.** https://github.com/AgenticResourceRegistry/AgenticResourceRegistry, about 4.5k stars. Self-hosted registry for sharing skills, agent files and MCP resources across a team; a good internal skill store for a company brain ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: governance, deploy.

**Community skill packs relevant to a company brain (docs, research, data, knowledge)**
- **obra/superpowers.** https://github.com/obra/superpowers, about 227.6k stars. Core skills library covering TDD, debugging and collaboration patterns ([jq list](https://github.com/jqueryscript/awesome-claude-code); [travisvn list](https://github.com/travisvn/awesome-claude-skills)). Helps with: devtool.
- **mattpocock/skills.** https://github.com/mattpocock/skills, about 128.5k stars. "Skills for Real Engineers" ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **addyosmani/agent-skills.** https://github.com/addyosmani/agent-skills, about 59.3k stars. Production engineering skills ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **K-Dense-AI/scientific-agent-skills.** https://github.com/K-Dense-AI/scientific-agent-skills, about 28.2k stars. Skills for research, analysis, finance and writing ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: research.
- **Imbad0202/academic-research-skills.** https://github.com/Imbad0202/academic-research-skills, about 31.3k stars. Runs a research → write → review → revise loop ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: research.
- **mvanhorn/last30days-skill.** https://github.com/mvanhorn/last30days-skill, about 41.8k stars. Researches a topic across Reddit and X over the last 30 days ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: search.
- **muratcankoylan/Agent-Skills-for-Context-Engineering.** https://github.com/muratcankoylan/Agent-Skills-for-Context-Engineering, about 16.5k stars. Context engineering and multi-agent architecture skills ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory, devtool.
- **kepano/obsidian-skills.** https://github.com/kepano/obsidian-skills, about 35.6k stars. Skills from the Obsidian CEO; a markdown-vault knowledge base ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory, documents.
- **teng-lin/notebooklm-py.** https://github.com/teng-lin/notebooklm-py, about 18.8k stars. Unofficial NotebookLM API plus an agent skill ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents, search.
- **PleasePrompto/notebooklm-skill.** https://github.com/PleasePrompto/notebooklm-skill, about 7.0k stars. Lets Claude Code query NotebookLM notebooks ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **AgriciDaniel/claude-obsidian.** https://github.com/AgriciDaniel/claude-obsidian, about 6.8k stars. Self-organizing "second brain" wiki vault for Claude plus Obsidian ([jq list](https://github.com/jqueryscript/awesome-claude-code); [HRH list](https://github.com/hesreallyhim/awesome-claude-code)). Helps with: memory.
- **eugeniughelbur/obsidian-second-brain.** https://github.com/eugeniughelbur/obsidian-second-brain, about 4.9k stars. Persistent agent memory in an Obsidian vault with semantic search ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **breferrari/obsidian-mind.** https://github.com/breferrari/obsidian-mind, about 4.6k stars. Obsidian vault memory for Claude Code, Codex and Gemini CLI ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **coleam00/second-brain-skills.** https://github.com/coleam00/second-brain-skills, about 781 stars. Turns Claude Code into a second-brain workspace ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **tronghieu/agent-skills.** https://github.com/tronghieu/agent-skills. "Agent Skills for Knowledge Work", aimed at cognitive tasks rather than coding ([HRH list](https://github.com/hesreallyhim/awesome-claude-code)). Helps with: documents.
- **yusufkaraaslan/Skill_Seekers.** https://github.com/yusufkaraaslan/Skill_Seekers.
  - Turns docs sites, GitHub repos, PDFs, videos, Confluence and Notion into Claude skills.
  - Also available as an MCP server ([travisvn list](https://github.com/travisvn/awesome-claude-skills); [PP list](https://github.com/punkpeye/awesome-mcp-servers)).
  - Helps with: documents, ingestion.
- **virgiliojr94/book-to-skill.** https://github.com/virgiliojr94/book-to-skill, about 5.9k stars. Turns a PDF book into a skill ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **coffeefuelbump/csv-data-summarizer-claude-skill.** https://github.com/coffeefuelbump/csv-data-summarizer-claude-skill. Analyzes CSVs automatically and produces insights and charts ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: data cleaning.
- **sanjay3290/ai-skills.** https://github.com/sanjay3290/ai-skills. Includes deep-research (via the Gemini Deep Research agent) and a read-only multi-connection postgres skill ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: research, data.
- **michalparkola/tapestry-skills-for-claude-code.** https://github.com/michalparkola/tapestry-skills-for-claude-code. Includes article-extractor and tapestry, which interlinks documents into knowledge networks ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: documents, knowledge graph.
- **Composio skills list, built-in skills.** Invoice Organizer, File Organizer, Meeting Insights Analyzer, Lead Research Assistant and Content Research Writer ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: documents.
- **Composio skills list, "WhatsApp Automation" skill.** Messages, media, templates, groups and business profiles, via Composio ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: whatsapp.
- **Composio skills list, "Zoho CRM Automation" skill.** Leads, contacts, deals and modules ([Composio skills list](https://github.com/ComposioHQ/awesome-claude-skills)). Helps with: connectors (Zoho).
- **czlonkowski/n8n-skills.** https://github.com/czlonkowski/n8n-skills, about 5.4k stars. Skills for building n8n workflows ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: connectors, automation.
- **deanpeters/Product-Manager-Skills.** https://github.com/deanpeters/Product-Manager-Skills, about 5.1k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **coreyhaines31/marketingskills.** https://github.com/coreyhaines31/marketingskills, about 33.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: business.
- **alirezarezvani/claude-skills.** https://github.com/alirezarezvani/claude-skills, about 18.0k stars. Real-world skills collection ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **JimLiu/baoyu-skills.** https://github.com/JimLiu/baoyu-skills, about 24.7k stars. Writing, presentations and publishing skills ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **OpenSenseNova/SenseNova-Skills.** https://github.com/OpenSenseNova/SenseNova-Skills, about 4.5k stars. Office-assistant productivity skills ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **blader/humanizer.** https://github.com/blader/humanizer, about 24.1k stars. Removes signs of AI writing ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **OthmanAdi/planning-with-files.** https://github.com/OthmanAdi/planning-with-files, about 23.3k stars. Manus-style persistent markdown planning ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **forrestchang/andrej-karpathy-skills.** https://github.com/forrestchang/andrej-karpathy-skills, about 175.2k stars (the count looks suspicious). A single CLAUDE.md file of coding guardrails ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool.
- **safishamsi/graphify.** https://github.com/safishamsi/graphify, about 67.0k stars. Codebase knowledge-graph skill for many agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: knowledge graph.
- **Lum1104/Understand-Anything.** https://github.com/Lum1104/Understand-Anything, about 59.1k stars. Turns a codebase into an interactive knowledge graph ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: knowledge graph.
- **nicobailon/visual-explainer.** https://github.com/nicobailon/visual-explainer, about 8.8k stars. Generates HTML pages for data tables, architecture overviews and reports ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: documents.
- **joeseesun/qiaomu-anything-to-notebooklm.** https://github.com/joeseesun/qiaomu-anything-to-notebooklm, about 5.5k stars. Turns PDFs, web pages, YouTube videos and WeChat articles into NotebookLM inputs ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: ingestion.
- **bradautomates/claude-video.** https://github.com/bradautomates/claude-video, about 14.5k stars. Video frames and transcripts for question answering ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: ingestion.

### Inferences
- A company brain can ship its own skills as an internal Claude Code / Cowork plugin marketplace. The pieces are an internal repo with `.claude-plugin/marketplace.json`, Anthropic's docx/pdf/xlsx skills for document output, the `gws` skills or an MCP for Google Workspace, and mcp-builder to generate custom ERP/CRM connectors.
- Skill supply-chain risk is real given the number of community packs. Run a scanner such as NVIDIA SkillSpector and keep a private registry such as AgenticResourceRegistry before letting staff install community skills.

### Gaps
- **No Arabic-specific skills.** I found none in any list searched (anthropics, Composio, travisvn, VoltAgent, HRH, jq).
- **Unverified marketplaces.** "skillsmp" and "claude-plugins.dev"-style marketplaces were named in the brief. I did not verify their current URLs or catalogue sizes this session.
- **Star counts are approximate.** I could not query the GitHub API.

## 2. MCP servers and MCP registries

### Takeaway
- **Official reference servers.** The official modelcontextprotocol/servers repo now keeps only 7 reference servers: Everything, Fetch, Filesystem, Git, Memory, Sequential Thinking and Time. Google Drive, Postgres, Slack, GitHub, Redis and SQLite were archived.
- **Where to find servers now.** The official MCP Registry plus independent registries:
  - Glama: about 121k servers listed; another source says about 99k.
  - Smithery: 26k+; part of Arcade since August 2026.
  - PulseMCP: about 21.7k.
  - mcp.so: about 20.5k.
- **Community connectors exist for:**
  - WhatsApp (personal and Business API)
  - Odoo (5+ servers)
  - Excel
  - Gmail, Drive and Microsoft 365
  - Zoho Mail
  - Vector databases and graph memory

### Cited Findings

**Registries / directories**
- **Official MCP Registry.** https://registry.modelcontextprotocol.io. The canonical list of published servers ([modelcontextprotocol/servers README](https://raw.githubusercontent.com/modelcontextprotocol/servers/main/README.md); [registry](https://registry.modelcontextprotocol.io/)). Helps with: discovery.
- **Glama.** https://glama.ai/mcp/servers. Shows "121,232 servers" ([glama](https://glama.ai/mcp/servers)). Another source reports 98,962 servers, graded on license, quality and maintenance ([Scalekit](https://www.scalekit.com/blog/mcp-registry-vs-managed-mcp-integrations)). The two counts conflict; most likely they were taken at different dates. Helps with: discovery.
- **Smithery.** https://smithery.ai.
  - 26,000+ servers; part of Arcade.dev since August 2026 ([Scalekit](https://www.scalekit.com/blog/mcp-registry-vs-managed-mcp-integrations); [Arcade blog](https://www.arcade.dev/blog/smithery-joins-arcade/)).
  - Another directory guide lists 7K+ ([Linkly](https://linklyhq.com/blog/mcp-server-directories)). The counts conflict.
  - Helps with: discovery, hosting.
- **PulseMCP.** https://www.pulsemcp.com. 21,705 servers labelled official, reference or community ([Scalekit](https://www.scalekit.com/blog/mcp-registry-vs-managed-mcp-integrations)). Helps with: discovery.
- **mcp.so.** https://mcp.so. 20,487 servers (1,435 remote), 395 clients, 268 agent skills and 177 CLI tools ([mcp.so](https://mcp.so/)). Helps with: discovery.
- **punkpeye/awesome-mcp-servers.** https://github.com/punkpeye/awesome-mcp-servers. The largest awesome list (the README is about 1.6 MB as of 2026-11-15), with Glama score badges ([raw README](https://raw.githubusercontent.com/punkpeye/awesome-mcp-servers/main/README.md)). Helps with: discovery.
- **wong2/awesome-mcp-servers.** https://github.com/wong2/awesome-mcp-servers. Does not accept PRs (README note) ([raw README](https://raw.githubusercontent.com/wong2/awesome-mcp-servers/main/README.md)).
- **appcypher/awesome-mcp-servers.** https://github.com/appcypher/awesome-mcp-servers. Classic list (about 63 KB) ([raw README](https://raw.githubusercontent.com/appcypher/awesome-mcp-servers/main/README.md)).

**Official reference servers (modelcontextprotocol/servers)**
All of the following come from the [servers README](https://raw.githubusercontent.com/modelcontextprotocol/servers/main/README.md).
- **Filesystem.** Secure file operations with configurable access. Helps with: documents.
- **Memory.** Persistent memory based on a knowledge graph (stores a local `memory.jsonl`, per [InfraNodus](https://infranodus.com/docs/llm-memory-tools-comparison)). Helps with: memory.
- **Fetch.** Fetches web content and converts it for LLM use. Helps with: search/ingestion.
- **Git.** Read, search and manipulate repos.
- **Sequential Thinking**, **Time** and **Everything** (test server).
- **Archived servers.** Google Drive, PostgreSQL, Slack (now maintained by Zencoder at https://github.com/zencoderai/slack-mcp-server), GitHub, GitLab, Redis, SQLite, Sentry, Puppeteer, Brave Search (replaced by the official https://github.com/brave/brave-search-mcp-server) and others, all at https://github.com/modelcontextprotocol/servers-archived.
- **Official SDKs.** TypeScript, Python, Go, Java, Kotlin, C#, PHP, Ruby, Rust and Swift (e.g. https://github.com/modelcontextprotocol/python-sdk). Helps with: building custom connectors.

**WhatsApp MCP servers** (all from the [PP list](https://github.com/punkpeye/awesome-mcp-servers))
- **lharries/whatsapp-mcp.** https://github.com/lharries/whatsapp-mcp. Searches personal WhatsApp messages and contacts and sends to people or groups (Python/Go). Helps with: whatsapp.
- **edouard-claude/whatsapp-mcp.** https://github.com/edouard-claude/whatsapp-mcp. Full-featured personal WhatsApp in Rust/Go, with local full-text search. Helps with: whatsapp, search.
- **loglux/whatsapp-mcp-stream.** https://github.com/loglux/whatsapp-mcp-stream. WhatsApp integration with a web admin UI (QR login, status). Helps with: whatsapp.
- **nakulben/whatsapp-mcp.** https://github.com/nakulben/whatsapp-mcp. Creates, validates and sends WhatsApp Business templates via the Meta Cloud API. Helps with: whatsapp (official API).
- **gambot-ai/gambot-mcp.** https://github.com/gambot-ai/gambot-mcp. WhatsApp Business API messages and templates plus CRM contacts and leads. Helps with: whatsapp, CRM.
- **wsapi-chat/wsapi-mcp.** https://github.com/wsapi-chat/wsapi-mcp. WhatsApp through the WSAPI REST API: messages, media, chats, groups and communities. Helps with: whatsapp.
- **wazionapps/mcp-server.** https://github.com/wazionapps/mcp-server. WhatsApp Business messages, workflows and campaigns. Helps with: whatsapp.
- **chatmaid/mcp.** https://github.com/chatmaid/mcp. Chatmaid WhatsApp API: send to contacts and groups and read replies. Helps with: whatsapp.
- **Infobip/mcp.** https://github.com/infobip/mcp. Official Infobip server covering SMS, RCS, WhatsApp and Viber. Helps with: whatsapp (enterprise CPaaS).
- **kudosity/mcp.** https://github.com/kudosity/mcp. SMS, MMS and WhatsApp messaging with delivery reports. Helps with: whatsapp.
- **drsound/markdown-to-whatsapp.** https://github.com/drsound/markdown-to-whatsapp. Converts Markdown to WhatsApp formatting. Helps with: whatsapp output.
- **grzgrzgrz3/pingwa-client.** https://github.com/grzgrzgrz3/pingwa-client. Two-way WhatsApp notifications and questions from agents. Helps with: whatsapp, human-in-the-loop.

**ERP / CRM (Odoo, Zoho, HubSpot, etc.)**
- **ivnvxd/mcp-server-odoo.** https://github.com/ivnvxd/mcp-server-odoo. Odoo business data access, record management and workflow automation ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Odoo).
- **tuanle96/mcp-odoo.** https://github.com/tuanle96/mcp-odoo. Odoo 16-19 with nothing to install on the Odoo side; reads, approval-gated writes and diagnostics ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Odoo), governance.
- **rosenvladimirov/odoo-claude-mcp.** https://github.com/rosenvladimirov/odoo-claude-mcp. Self-hosted server suite for Odoo 15-19 plus GitHub, Portainer, OCA and Teams ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Odoo).
- **twtrubiks/odoo19-mcp-server.** https://github.com/twtrubiks/odoo19-mcp-server. Odoo 19 via JSON-RPC: CRUD and model inspection ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Odoo).
- **minhhq-a1/odoo-pulse.** https://github.com/minhhq-a1/odoo-pulse. One-call business-analysis reports on Odoo, such as the sales pipeline ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Odoo), analytics.
- **SirGreed808/zoho-mail-mcp.** https://github.com/SirGreed808/zoho-mail-mcp. Read, search and send Zoho Mail ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Zoho).
- **Albretsen/MCPEmails.** https://github.com/Albretsen/MCPEmails. Email across Gmail, Fastmail, iCloud, Yahoo, Zoho and any IMAP/SMTP mailbox ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (email).
- **penmadebykisss/amocrm-kommo-mcp.** https://github.com/penmadebykisss/amocrm-kommo-mcp. amoCRM / Kommo leads, contacts, tasks and sales analytics ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Kommo is a WhatsApp-centric CRM. Helps with: CRM, whatsapp-adjacent.
- **SynderAccounting/gl-importer-plugin.** https://github.com/SynderAccounting/gl-importer-plugin. Imports CSV/XLSX accounting data into QuickBooks ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (accounting).
- **HubSpot official MCP.** Present as a plugin connector in this session's environment, though it failed to connect here. Description: (prior knowledge; not re-verified) HubSpot offers a remote MCP server at developers.hubspot.com. Helps with: CRM.

**Google Workspace / Microsoft 365 / email**
- **isaacphi/mcp-gdrive.** https://github.com/isaacphi/mcp-gdrive. Reads Google Drive and edits Sheets ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Drive).
- **A1-x-Tech/mcp-google-drive.** https://github.com/A1-x-Tech/mcp-google-drive. Drive search, upload, export, share and comment ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **A1-x-Tech/mcp-google-gmail.** https://github.com/A1-x-Tech/mcp-google-gmail. Gmail search, read, send, drafts and labels ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **vakharwalad23/google-mcp.** https://github.com/vakharwalad23/google-mcp. Gmail, Calendar, Drive and Tasks in one server ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **alexneamtu/gmail-mcp.** https://github.com/alexneamtu/gmail-mcp. Self-hosted multi-account Gmail over Streamable HTTP for Claude and Codex ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **churichard/fluxmail.** https://github.com/churichard/fluxmail. Self-hosted email for Gmail, Microsoft 365 and IMAP: read, search, draft and schedule ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **elie222/inbox-zero.** https://github.com/elie222/inbox-zero. Finds emails that need a reply or follow-up ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **softeria/ms-365-mcp-server.** https://github.com/softeria/ms-365-mcp-server. Microsoft 365 via Graph: Outlook, files, Excel and calendar ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (M365).
- **nitin27may/ms-graph-mcp.** https://github.com/nitin27may/ms-graph-mcp. Outlook, Teams, OneDrive, SharePoint, OneNote, Planner and Entra ID ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **agentmail-to/agentmail-mcp.** https://github.com/agentmail-to/agentmail-mcp. Creates email inboxes for agents on the fly ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **zencoderai/slack-mcp-server.** https://github.com/zencoderai/slack-mcp-server. Successor to the official Slack reference server ([servers README](https://raw.githubusercontent.com/modelcontextprotocol/servers/main/README.md)). Helps with: connectors (Slack).
- **Grey-Iris/easy-notion-mcp.** https://github.com/Grey-Iris/easy-notion-mcp. Markdown-first Notion access that converts markdown to Notion blocks ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors (Notion).
- **Notion, Slack, Google Drive/Docs/Sheets, Gmail and Calendar remote MCP connectors.** All are available as first-party claude.ai connectors in this session's tool environment (observed in the session tool list, not web-sourced). Helps with: connectors.

**Excel / spreadsheets / tabular**
- **haris-musa/excel-mcp-server.** https://github.com/haris-musa/excel-mcp-server. Workbook creation, formulas, charts and pivots without Excel installed ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: documents.
- **sbroenne/mcp-server-excel.** https://github.com/sbroenne/mcp-server-excel. Automates the Excel app on Windows: Power Query, DAX, VBA and pivots ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **PSU3D0/spreadsheet-mcp.** https://github.com/PSU3D0/spreadsheet-mcp. Token-efficient xlsx analysis and editing in Rust ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **AirSaiga/Precis.** https://github.com/AirSaiga/Precis. Local data-quality workbench for Excel/CSV with schema validation ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: data cleaning.
- **haiiibin/data-profiler-mcp.** https://github.com/haiiibin/data-profiler-mcp. Profiles CSV, Parquet, Excel and JSON files ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: data cleaning.
- **julien040/anyquery.** https://github.com/julien040/anyquery. Queries apps with SQL from one local binary, and also connects to Postgres, MySQL and SQLite ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors, search.

**Databases / vector stores / graph**
- **qdrant/mcp-server-qdrant.** https://github.com/qdrant/mcp-server-qdrant ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: search, memory.
- **chroma-core/chroma-mcp.** https://github.com/chroma-core/chroma-mcp. Official server for local and cloud Chroma ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: search.
- **weaviate/mcp-server-weaviate.** https://github.com/weaviate/mcp-server-weaviate. Collections as a knowledge base and chat memory ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **zilliztech/mcp-server-milvus.** https://github.com/zilliztech/mcp-server-milvus ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **neo4j-contrib/mcp-neo4j.** https://github.com/neo4j-contrib/mcp-neo4j. Queries, knowledge-graph memory and Aura management ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: memory, knowledge graph.
- **devopam/MCPg.** https://github.com/devopam/MCPg. Postgres introspection, AST-validated queries and NL→SQL ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: data.
- **alexander-zuev/supabase-mcp-server.** https://github.com/alexander-zuev/supabase-mcp-server. Supabase SQL ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: deploy/data.
- **Snowflake-Labs/mcp.** https://github.com/Snowflake-Labs/mcp. Cortex Agents, SQL and semantic views ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **Aiven-Open/mcp-aiven.** https://github.com/Aiven-Open/mcp-aiven. Postgres, Kafka, ClickHouse and OpenSearch on Aiven ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).

**Knowledge / RAG platforms as MCP**
- **graphlit/graphlit-mcp-server.** https://github.com/graphlit/graphlit-mcp-server. Ingests Slack, Discord, websites, Google Drive, Linear and GitHub, then searches them ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: connectors, search (closest to an off-the-shelf company brain).
- **ragieai/ragie-mcp-server.** https://github.com/ragieai/ragie-mcp-server. Retrieves from a Ragie knowledge base connected to Google Drive, Notion and Jira ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: search.
- **topoteretes/cognee (cognee-mcp).** https://github.com/topoteretes/cognee/tree/dev/cognee-mcp. Graph and vector memory with ingestion from many sources ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: memory.

**Documents / PDF / OCR**
- **arjunprabhulal/superpdf.** https://github.com/arjunprabhulal/superpdf. Reads, converts, edits and compares PDFs locally, with OCR and Markdown tables ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: documents.
- **drolosoft/go-docs-mcp.** https://github.com/drolosoft/go-docs-mcp. Reads, searches, OCRs and extracts from PDF, DOCX, CSV and images ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: documents.
- **LightSpeedPlusOne/invovate-mcp-server.** https://github.com/LightSpeedPlusOne/invovate-mcp-server. Multilingual PDF/UBL invoices, including right-to-left scripts ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: documents, arabic (RTL).
- **Docling / MarkItDown / MinerU / Marker.** Common document-to-markdown converters, each with MCP integrations. Sources: (prior knowledge; not re-verified)
  - https://github.com/docling-project/docling
  - https://github.com/microsoft/markitdown
  - https://github.com/opendatalab/MinerU
  - https://github.com/datalab-to/marker
  - Helps with: documents, ingestion.

**Arabic / MENA-specific**
- **mohsinmshabbir/datasaudi-mcp.** https://github.com/mohsinmshabbir/datasaudi-mcp. Saudi GDP, inflation, trade and population statistics from GASTAT/DataSaudi ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: arabic/MENA data.
- **a-y-ibrahim/after-effects-mcp.** https://github.com/a-y-ibrahim/after-effects-mcp. After Effects control with Arabic text support ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Marginal.

**Messaging beyond WhatsApp (Telegram, etc.)**
- **chigwell/telegram-mcp.** https://github.com/chigwell/telegram-mcp ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: messaging.
- **chaindead/telegram-mcp.** https://github.com/chaindead/telegram-mcp ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **chenhg5/cc-connect.** https://github.com/chenhg5/cc-connect, about 15.5k stars. Bridges local coding agents to Feishu, DingTalk, Slack, Telegram, Discord, LINE and WeChat Work ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: messaging.

### Inferences
- For a WhatsApp-first company brain, there are two routes:
  - **Official route:** a Meta Cloud API / BSP server such as Infobip, nakulben, gambot or wazion. Choose this for anything customer-facing.
  - **Personal-account route:** lharries or edouard-claude, built on unofficial WhatsApp Web libraries. This carries ToS and ban risk; that is my inference, not something these sources state.
- Five or more independent Odoo MCP servers exist. A builder should be able to fork one with approval-gated writes (tuanle96) rather than write one from scratch.
- Since the official Drive, Postgres and Slack reference servers are archived, use first-party remote connectors (claude.ai connectors, Google/Microsoft official servers) or maintained community servers.

### Gaps
- **No Arabic NLP or OCR MCP server found.** My search for Arabic document-parsing tools returned only irrelevant results.
- **No dedicated Zoho CRM / Zoho Books MCP in the PP list.** Only Zoho Mail. Zoho's own MCP offering, if any, was not verified.
- **Star counts for MCP servers** were not available (GitHub API blocked).

## 3. MCP gateways and connector platforms

### Takeaway
The connector market has consolidated:
- Pipedream was acquired by Workday (announced November 2025).
- Smithery joined Arcade (August 2026).

For a solo builder:
- **Hosted catalogue with managed OAuth:** Composio (1,000+ toolkits; free tier of 100K calls/month) or Pipedream Connect (3,000+ apps).
- **Personal use:** Zapier MCP (9,000+ apps, but every call draws on the task budget).
- **Self-hosted:** n8n, Docker MCP Gateway, MetaMCP, MCPJungle, 1MCP and similar.

### Cited Findings
- **Composio.** https://composio.dev.
  - 1,000+ toolkits and 50,000+ tools; managed in-chat OAuth; free 100K tool calls/month; SOC 2 and ISO 27001 ([Composio vs Pipedream](https://composio.dev/content/composio-vs-pipedream)).
  - Per-team MCP Gateway endpoint with SSO and per-user/per-role permissions ([Elaichi](https://elaichi.ai/blog/pipedream-mcp-alternatives/)).
  - Pro plan $29/mo ([Swytchcode](https://www.swytchcode.com/content/zapier-mcp-alternatives-in-2026)).
  - Self-hosting only on Enterprise ([DataToRAG](https://datatorag.com/blog/composio-vs-zapier-mcp)).
  - Helps with: connectors (Gmail, Notion, Slack, Zoho, WhatsApp, etc.).
- **Pipedream Connect / MCP.** https://pipedream.com/connect.
  - 3,000+ apps and 10,000+ tools with managed OAuth; Startup plan $99/mo annual ([Swytchcode](https://www.swytchcode.com/content/zapier-mcp-alternatives-in-2026)).
  - Acquired by Workday, announced November 2025 ([Composio](https://composio.dev/content/composio-vs-pipedream)).
  - Has a newer gateway product, "Conduit" ([Elaichi](https://elaichi.ai/blog/pipedream-mcp-alternatives/)).
  - Helps with: connectors.
- **Zapier MCP.** https://zapier.com/mcp.
  - 9,000+ apps and 40,000+ actions through one Streamable HTTP URL ([Swytchcode](https://www.swytchcode.com/content/zapier-mcp-alternatives-in-2026)).
  - Each call uses two tasks ([Elaichi](https://elaichi.ai/blog/pipedream-mcp-alternatives/)).
  - Google coverage is limited to Gmail, Docs, Sheets, Drive and Calendar, as Zap-shaped actions ([DataToRAG](https://datatorag.com/blog/composio-vs-zapier-mcp)).
  - Helps with: connectors.
- **Arcade.dev.** https://arcade.dev. Per-user OAuth and agent authorization; 100+ integrations (8,000+ tools); $25/mo plus usage ([Speakeasy](https://www.speakeasy.com/blog/choosing-an-mcp-gateway)). Now owns Smithery ([Scalekit](https://www.scalekit.com/blog/mcp-registry-vs-managed-mcp-integrations)). Helps with: connectors, governance.
- **Metorial.** https://metorial.com. Per-user identity, tracing, access control, a free Dev tier of 500K calls, and on-prem. Its open-source https://github.com/metorial/mcp-containers packages MCP servers ([Metorial](https://metorial.com/for-ai-crawlers/zapier-mcp-alternatives)). Helps with: connectors, governance.
- **Docker MCP Gateway / MCP Toolkit.** Free; full infrastructure control; configured with verbose YAML ([Speakeasy](https://www.speakeasy.com/blog/choosing-an-mcp-gateway)). Helps with: deploy, self-host.
- **Speakeasy (Gram).** https://www.speakeasy.com. Generates MCP servers from OpenAPI specs in minutes ([Speakeasy](https://www.speakeasy.com/blog/choosing-an-mcp-gateway)). Helps with: building custom connectors (e.g. an Odoo/Zoho REST API to MCP).
- **TrueFoundry MCP Gateway.** Enterprise governance; $499/mo ([Speakeasy](https://www.speakeasy.com/blog/choosing-an-mcp-gateway)). Helps with: governance.
- **Willow.** Governance gateway; free tier, then $15/seat ([Speakeasy](https://www.speakeasy.com/blog/choosing-an-mcp-gateway)).
- **n8n.** https://n8n.io. Self-hosted workflows exposed as MCP tools ([Swytchcode](https://www.swytchcode.com/content/zapier-mcp-alternatives-in-2026)). Helps with: connectors, self-host, WhatsApp nodes (prior knowledge).
- **Paragon (ActionKit)** and **Nango.** Integrations you embed in your own product; Nango lets you own the integration code ([Swytchcode](https://www.swytchcode.com/content/zapier-mcp-alternatives-in-2026)).
- **Kong AI Gateway for MCP** ([Composio blog index](https://composio.dev/content/composio-vs-pipedream)). Also named: **Workato Enterprise MCP**, **Natoma** and **Elaichi** ([Elaichi](https://elaichi.ai/blog/pipedream-mcp-alternatives/)). **Runlayer** ([Metorial](https://metorial.com/for-ai-crawlers/zapier-mcp-alternatives)). Helps with: governance.
- **DataToRAG.** https://datatorag.com. MIT-licensed core; Google Workspace RAG/MCP; Docker Compose with Postgres; passed Google CASA Tier 2 ([DataToRAG](https://datatorag.com/blog/composio-vs-zapier-mcp)). Helps with: connectors (Google), documents.
- **AnythingMCP.** https://anythingmcp.com, repo https://github.com/HelpCode-ai/anythingmcp. Self-hosted gateway that turns REST, SOAP and GraphQL APIs and SQL into MCP ([PP list](https://github.com/punkpeye/awesome-mcp-servers); [AnythingMCP](https://anythingmcp.com/vs/alternatives-to-zapier-mcp)). Helps with: connectors (legacy ERP).
- **MetaMCP.** https://github.com/metatool-ai/metatool-app. Unified middleware MCP server with a GUI ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: self-hosted gateway.
- **MCPJungle.** https://github.com/duaraghav8/MCPJungle. Self-hosted MCP registry for enterprise agents ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **1MCP.** https://github.com/1mcp-app/agent. Aggregates many MCP servers into one ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **Lunar MCPX.** https://github.com/TheLunarCompany/lunar/tree/main/mcpx. Open-source gateway for managing MCP servers at scale ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **pluggedin-mcp-proxy.** https://github.com/VeriTeknik/pluggedin-mcp-proxy ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **magg.** https://github.com/sitbon/magg. Meta-MCP server that lets LLMs discover and install servers ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **api7/aisix.** https://github.com/api7/aisix. Self-hosted MCP gateway with per-tool ACLs, guardrails and rate limits ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: governance.
- **withoneai/mcp.** https://github.com/withoneai/mcp. Authenticated API calls across Gmail, Slack, Stripe, Notion and more ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **WayStation-ai/mcp.** https://github.com/waystation-ai/mcp. Connects MCP hosts to Notion, Slack, Monday and Airtable ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **Klavis AI**, **CData Connect AI** and **Merge MCP.** Named in the brief, but none appeared in my search results or in the PP list grep. Sources: (prior knowledge; not re-verified)
  - Klavis: https://github.com/Klavis-AI/klavis, open-source hosted MCP servers.
  - CData Connect AI: https://www.cdata.com/ai/, 300+ enterprise data sources via MCP.
  - Merge Agent Handler / MCP: https://www.merge.dev.
  - Helps with: connectors (ERP/CRM/HRIS).

### Inferences
- **Cheapest path for a solo builder:** Composio's free tier for SaaS breadth. Add self-hosted n8n for WhatsApp/ERP flows and a self-hosted gateway (MetaMCP or Docker MCP Gateway) to put internal MCP servers behind one URL.
- **For multi-user company deployment,** the deciding factors are per-user identity and audit logging (Arcade, Metorial, Composio Enterprise), more than catalogue size.

### Gaps
- Current pricing and connector counts for Klavis, CData Connect AI and Merge MCP were not verified this session.
- Several comparison pages are written by competing vendors (Composio, Elaichi, Metorial, Swytchcode, DataToRAG), so their claims are biased.

## 4. Coding agents and AI dev tools for a solo builder

### Takeaway
- **Benchmark leader:** Claude Code with Opus 5.5 led Terminal-Bench 4.0 at 64.8% (October 2026). Codex with GPT-6.1 Sol scored 58.2% at $1.92 per task.
- **Leading open-source agents:** opencode (about 176-200k stars), Gemini CLI (about 105k), Codex CLI (about 91k), Cline (about 66.6k) and Roo/Kilo.
- **Reported changes:** Cursor acquired Continue, and Gemini CLI's free serving ended in June 2026, replaced by the Antigravity CLI. Both come from a single source.

### Cited Findings
- **Claude Code.** https://github.com/anthropics/claude-code, about 132.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Top Terminal-Bench 4.0 entry at 64.8% with Opus 5.5 (max) ([MorphLLM](https://www.morphllm.com/ai-coding-agent)). Helps with: devtool.
- **claude-code-action.** https://github.com/anthropics/claude-code-action, about 8.0k stars. GitHub PR and issue agent ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: devtool/CI.
- **Claude Agent SDK (Python).** https://github.com/anthropics/claude-code-sdk-python, about 7.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: building the company-brain agent itself.
- **claude-code-security-review.** https://github.com/anthropics/claude-code-security-review, about 5.2k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: governance.
- **OpenAI Codex CLI.** https://github.com/openai/codex, about 91.0k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). 58.2% on Terminal-Bench 4.0 with GPT-6.1 Sol at $1.92/task ([MorphLLM](https://www.morphllm.com/ai-coding-agent)). Helps with: devtool.
- **Gemini CLI.** https://github.com/google-gemini/gemini-cli, about 105.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Per [MorphLLM](https://www.morphllm.com/ai-coding-agent), its free serving ended June 18, 2026, and the free Google option is now the Antigravity CLI (single source).
- **Google Antigravity.** Google's agentic IDE, reviewed alongside the others in [Jan Marshal's Feb 2026 ranking video](https://www.youtube.com/watch?v=NAWcnIebQ-o).
- **opencode.** https://github.com/anomalyco/opencode. About 176k stars per the [jq list](https://github.com/jqueryscript/awesome-claude-code), or 199,640 per [MorphLLM](https://www.morphllm.com/ai-coding-agent); the counts differ. MIT, any provider. Helps with: devtool.
- **Cline.** https://github.com/cline/cline, 66,566 stars, Apache-2.0, BYOK, Plan/Act modes, with a CLI and SDK ([MorphLLM](https://www.morphllm.com/ai-coding-agent)).
- **Roo Code.** https://github.com/RooCodeInc/Roo-Code, 24,294 stars. A Cline fork; roocode.com now redirects to Roomote, the team's hosted product from $99/mo ([MorphLLM](https://www.morphllm.com/ai-coding-agent)).
- **Kilo Code.** https://kilo.ai. A fork of Cline and Roo; 500+ hosted models; $8M seed ([wetheflywheel](https://wetheflywheel.com/en/guides/open-source-ai-coding-agents-2026/); [Kilo](https://kilo.ai/kilo-code/best-ai-coding-assistant)).
- **Continue.dev.** https://github.com/continuedev/continue, 34,559 stars. Reportedly acquired by Cursor; the open-source extension remains ([MorphLLM](https://www.morphllm.com/ai-coding-agent); single source).
- **OpenHands.** https://github.com/All-Hands-AI/OpenHands. About 65k stars and an $18.8M Series A ([wetheflywheel](https://wetheflywheel.com/en/guides/open-source-ai-coding-agents-2026/); figures probably from 2025).
- **Aider.** https://github.com/Aider-AI/aider, about 40.4k stars. Terminal pair programmer with deep git auto-commit ([wetheflywheel](https://wetheflywheel.com/en/guides/open-source-ai-coding-agents-2026/)).
- **Cursor.** https://cursor.com. "Default AI IDE"; Pro plan $20/mo ([Faros](https://www.faros.ai/blog/best-ai-coding-agents-2026); [MorphLLM](https://www.morphllm.com/ai-coding-agent)).
- **GitHub Copilot (agent mode and CLI).** Pro $10/mo with 1,500 AI credits ([MorphLLM](https://www.morphllm.com/ai-coding-agent)).
- **Windsurf**, **Zed**, **Amp** and **Warp.** Covered in 2026 comparisons ([MorphLLM](https://www.morphllm.com/ai-coding-agent); [Jan Marshal video](https://www.youtube.com/watch?v=NAWcnIebQ-o)).
- **charmbracelet/crush.** https://github.com/charmbracelet/crush, about 25.3k stars. Terminal coding agent ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **QwenLM/qwen-code.** https://github.com/QwenLM/qwen-code, about 25.2k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **earendil-works/pi.** https://github.com/earendil-works/pi, about 63.5k stars. Minimal terminal coding harness ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **v0, Lovable, Bolt and Replit Agent.** App builders for fast front ends and admin UIs. Sources: (prior knowledge; not re-verified this session)
  - https://v0.app
  - https://lovable.dev
  - https://bolt.new
  - https://replit.com
  - Helps with: deploy, UI.

**Claude Code workflow, orchestration and UI tools**
- **garrytan/gstack.** https://github.com/garrytan/gstack, about 116.2k stars. Opinionated agent roles for product, engineering, QA and release ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **affaan-m/ECC.** https://github.com/affaan-m/ECC, about 222.0k stars (count unverified). Harness optimisation covering skills, memory and security ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **farion1231/cc-switch.** https://github.com/farion1231/cc-switch, about 132.1k stars. Desktop switcher for Claude Code, Codex and OpenCode configs and providers ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **ruvnet/claude-flow.** https://github.com/ruvnet/claude-flow, about 59.4k stars. Multi-agent orchestration ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **Yeachan-Heo/oh-my-claudecode.** https://github.com/Yeachan-Heo/oh-my-claudecode, about 39.1k stars. Team multi-agent orchestration ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **wshobson/agents.** https://github.com/wshobson/agents, about 36.7k stars. Production subagents ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **musistudio/claude-code-router.** https://github.com/musistudio/claude-code-router, about 35.0k stars. Routes Claude Code to other models ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **router-for-me/CLIProxyAPI.** https://github.com/router-for-me/CLIProxyAPI, about 51.2k stars. Wraps CLI agents behind OpenAI-, Gemini- and Claude-compatible endpoints ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **SuperClaude_Framework.** https://github.com/SuperClaude-Org/SuperClaude_Framework, about 23.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **EveryInc/compound-engineering-plugin.** https://github.com/EveryInc/compound-engineering-plugin, about 25.1k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **BloopAI/vibe-kanban.** https://github.com/BloopAI/vibe-kanban, about 27.0k stars. Kanban board for parallel agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **davila7/claude-code-templates.** https://github.com/davila7/claude-code-templates, about 28.0k stars. CLI to configure and monitor Claude Code ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **getAsterisk/claudia.** https://github.com/getAsterisk/claudia, about 22.1k stars. GUI for Claude Code ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **slopus/happy.** https://github.com/slopus/happy, about 21.9k stars. Mobile and web client for Claude Code ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **siteboon/claudecodeui (CloudCLI).** https://github.com/siteboon/claudecodeui, about 11.9k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **getpaseo/paseo.** https://github.com/getpaseo/paseo, about 17.4k stars. Self-hosted interface for multiple agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **smtg-ai/claude-squad.** https://github.com/smtg-ai/claude-squad, about 7.8k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **automazeio/ccpm.** https://github.com/automazeio/ccpm, about 8.2k stars. Project management via GitHub Issues and worktrees ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **builderz-labs/mission-control.** https://github.com/builderz-labs/mission-control, about 6.2k stars. Self-hosted control plane for agent tasks and cost ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **BeehiveInnovations/zen-mcp-server.** https://github.com/BeehiveInnovations/zen-mcp-server, about 11.6k stars. Claude Code plus Gemini/OpenAI/Ollama working together ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **ryoppippi/ccusage.** https://github.com/ryoppippi/ccusage, about 16.1k stars. Claude Code usage analysis ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **Maciek-roboblog/Claude-Code-Usage-Monitor.** https://github.com/Maciek-roboblog/Claude-Code-Usage-Monitor, about 8.2k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **getagentseal/codeburn.** https://github.com/getagentseal/codeburn, about 8.0k stars. Token-cost TUI ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **sirmalloc/ccstatusline.** https://github.com/sirmalloc/ccstatusline, about 10.7k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **shanraisshan/claude-code-best-practice.** https://github.com/shanraisshan/claude-code-best-practice, about 65.8k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **shareAI-lab/learn-claude-code.** https://github.com/shareAI-lab/learn-claude-code, about 76.5k stars. Build a Claude-Code-like harness from scratch ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **Waishnav/devspace.** https://github.com/Waishnav/devspace, about 5.2k stars. Self-hosted MCP giving ChatGPT/Claude access to approved local projects ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **Tencent/BrowserSkill.** https://github.com/Tencent/BrowserSkill, about 5.9k stars. Lets agents use your logged-in browser ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: connectors to sites without APIs.
- **SawyerHood/dev-browser.** https://github.com/SawyerHood/dev-browser, about 6.3k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **hesreallyhim/awesome-claude-code.** https://github.com/hesreallyhim/awesome-claude-code. A major curated list (README about 243 KB). **jqueryscript/awesome-claude-code.** https://github.com/jqueryscript/awesome-claude-code. A list with star counts. Helps with: discovery.

### Inferences
- **Solo-builder stack:**
  - Claude Code as the primary agent.
  - Codex or Gemini/Antigravity as second opinions, via zen-mcp-server or claude-delegator.
  - Cursor as an IDE if preferred.
  - Lovable or v0 for admin UIs.
  - ccusage/codeburn for cost tracking.
- **Open-source BYOK options (opencode, Cline, Kilo)** let you serve local or regional models if data residency is an issue for a Gulf/MENA client. That is my inference.

### Gaps
- **Single-source claims.** Continue's acquisition by Cursor and the end of Gemini CLI's free serving each come from one vendor blog (MorphLLM). Verify both.
- **Not researched.** Current pricing for Windsurf, Lovable, Bolt, v0 and Replit Agent.

## 5. Context engineering and memory tooling

### Takeaway
**Memory layers.** These have matured into distinct designs, with these approximate GitHub stars on 28 Sep 2026:
- Mem0: about 66.2k; extracted facts.
- Graphiti/Zep: about 31.3k; bi-temporal graph.
- Cognee: about 31.1k; knowledge graph built from sources.
- Supermemory: about 31.0k; memory plus document retrieval and connector sync.
- Letta: about 25.0k; agent harness with git-tracked memory files.

**Coding-side context tools:**
- claude-mem: about 82.2k stars.
- Spec Kit: about 70.8k (Feb 2026).
- Task Master: about 25.5k.
- OpenSpec: about 24.9k.
- GSD: about 16.7k.
- context-mode, headroom and codegraph-style compressors and graphs.

### Cited Findings
**Agent memory platforms**
- **Mem0.** https://github.com/mem0ai/mem0, about 66.2k stars and $24M raised ([Mnemoverse, 28 Sep 2026](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
  - Self-reports 94.4 on LongMemEval and 92.5 on LoCoMo; an independent 2025 run scored it 49.0 ([InfraNodus](https://infranodus.com/docs/llm-memory-tools-comparison)).
  - Free tier of 10,000 adds; Starter $19 ([InfraNodus](https://infranodus.com/docs/llm-memory-tools-comparison)).
  - Offers the OpenMemory MCP server ([Cognee](https://www.cognee.ai/mem0-vs-zep)).
  - Helps with: memory.
- **elvismdev/mem0-mcp-selfhosted.** https://github.com/elvismdev/mem0-mcp-selfhosted. Self-hosted mem0 for Claude Code on Qdrant ([PP list](https://github.com/punkpeye/awesome-mcp-servers)). Helps with: memory.
- **Graphiti / Zep.** https://github.com/getzep/graphiti, about 31.3k stars ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
  - Bi-temporal knowledge graph that keeps a validity window on every fact. Runs on Neo4j, FalkorDB, embedded FalkorDBLite or Neptune ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
  - Zep Cloud Flex plan $125 ([InfraNodus](https://infranodus.com/docs/llm-memory-tools-comparison)).
  - Graphiti MCP server ([Cognee](https://www.cognee.ai/mem0-vs-zep)).
  - Helps with: memory, knowledge graph ("what was true when").
- **Cognee.** https://github.com/topoteretes/cognee, about 31.1k stars, $7.5M seed, Apache-2.0 ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
  - Remember, recall, improve and forget operations; connects to Slack, GitHub and Linear; aimed at memory shared across many agents.
  - Mem0 import adapter ([Coworker](https://coworker.ai/blog/mem0-vs-zep-vs-letta); [Cognee](https://www.cognee.ai/mem0-vs-zep)).
  - Helps with: memory, connectors.
- **Supermemory.** https://github.com/supermemoryai/supermemory, about 31.0k stars, MIT ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
  - Syncs Google Drive, Gmail, Notion, OneDrive and GitHub.
  - Shut down its own company-brain app in September 2026 to focus on the engine ([Coworker](https://coworker.ai/blog/mem0-vs-zep-vs-letta)).
  - Has a Claude Code / OpenCode memory plugin ([Supermemory blog](https://supermemory.ai/blog/mem0-alternatives/)).
  - Helps with: memory, connectors, search.
- **Letta (formerly MemGPT).** https://github.com/letta-ai/letta, about 25.0k stars; source moved to letta-ai/letta-code (about 3.5k) ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)).
- **letta-ai/claude-subconscious.** https://github.com/letta-ai/claude-subconscious, about 2.8k stars. Background agent that watches Claude Code sessions ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **Coworker.ai.** https://coworker.ai. Permission-aware company graph ("OM2") built from 50+ connected tools, with a self-hosted option on AWS/GCP ([Coworker](https://coworker.ai/blog/mem0-vs-zep-vs-letta)). Helps with: a direct competitor or reference for a company brain.
- **Mnemoverse** (memory reached first through MCP) ([Mnemoverse](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3)), plus **Hindsight** and **LangMem**, named as Mem0 alternatives ([Coworker](https://coworker.ai/blog/mem0-vs-zep-vs-letta)). Also **InfraNodus**, a knowledge-graph layer over MCP ([InfraNodus](https://infranodus.com/docs/llm-memory-tools-comparison)).
- **NevaMind-AI/memU.** https://github.com/NevaMind-AI/memU, about 13.9k stars. Personal agent memory ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **campfirein/cipher.** https://github.com/campfirein/cipher, about 4.9k stars. Memory layer for coding agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **CaviraOSS/LongMemory.** https://github.com/CaviraOSS/LongMemory, about 4.5k stars ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **tigerless-labs/agent-memory.** https://github.com/tigerless-labs/agent-memory, about 4.5k stars. Shared Markdown store with scheduled consolidation ([jq list](https://github.com/jqueryscript/awesome-claude-code)).

**Coding-context / context-engineering tools**
- **thedotmack/claude-mem.** https://github.com/thedotmack/claude-mem, about 82.2k stars. Captures and compresses everything Claude does during a session and re-injects it ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: memory.
- **github/spec-kit.** https://github.com/github/spec-kit.
  - Spec-driven development with `/speckit.constitution`, `.specify`, `.plan`, `.tasks` and `.implement`; installed with `uv tool install specify-cli` ([Augment](https://www.augmentcode.com/tools/best-spec-driven-development-tools)).
  - About 70.8k stars as of Feb 2026 ([Hightower/Medium](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)).
  - Helps with: devtool.
- **Task Master AI.** https://github.com/eyaltoledano/claude-task-master, about 25.5k stars. MIT with Commons Clause; MCP support ([Hightower/Medium](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)).
- **OpenSpec.** https://github.com/Fission-AI/OpenSpec, about 24.9k stars (Feb 2026). Change isolation reduces context bloat ([Hightower/Medium](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)). The repo URL is from prior knowledge.
- **GSD (Get Stuff Done).** https://github.com/gsd-build/get-shit-done, about 16.7k stars, MIT ([Hightower/Medium](https://medium.com/@richardhightower/agentic-coding-gsd-vs-spec-kit-vs-openspec-vs-taskmaster-ai-where-sdd-tools-diverge-0414dcb97e46)).
- **BMAD-METHOD.** https://github.com/bmad-code-org/BMAD-METHOD. Collaborative requirements and specification method ([devopstales](https://devopstales.github.io/ai/ai-software-development-spec-vs-vibe/); [Augment](https://www.augmentcode.com/tools/best-spec-driven-development-tools)). The repo URL is from prior knowledge.
- **Amazon Kiro** and **Augment Cosmos.** Spec-driven IDE/agents ([Augment](https://www.augmentcode.com/tools/best-spec-driven-development-tools)).
- **mksglu/context-mode.** https://github.com/mksglu/context-mode, about 23.0k stars. MCP server that sandboxes tool output and indexes session memory ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Related repo claude-context-mode (about 17.4k) claims "315 KB becomes 5.4 KB".
- **headroomlabs-ai/headroom.** https://github.com/headroomlabs-ai/headroom, about 62.8k stars. Compresses tool outputs, logs and retrieval chunks before they reach the model ([jq list](https://github.com/jqueryscript/awesome-claude-code)). Helps with: RAG cost.
- **colbymchenry/codegraph.** https://github.com/colbymchenry/codegraph, about 54.9k stars. Local code knowledge graph for many agents ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **trailhq/Trail-Code.** https://github.com/trailhq/Trail-Code, about 10.1k stars. Maps calls and stores team decisions ([jq list](https://github.com/jqueryscript/awesome-claude-code)).
- **DeusData/codebase-memory-mcp.** https://github.com/DeusData/codebase-memory-mcp. Indexes a repo into a persistent local knowledge graph ([PP list](https://github.com/punkpeye/awesome-mcp-servers)).
- **Context7 (Upstash).** https://github.com/upstash/context7. Up-to-date library docs over MCP. (prior knowledge; not re-verified; it did not appear in the jq star list grep.) Helps with: devtool.
- **Serena (Oraios).** https://github.com/oraios/serena. LSP-based semantic code retrieval and editing over MCP. (prior knowledge; not re-verified.) Helps with: devtool.
- **Anthropic engineering guides:** "Effective Context Engineering for AI Agents", "How We Built Our Multi-Agent Research System", "Building Effective Agents" and "Steering Claude Code: Skills, Hooks, Rules, Subagents" ([HRH list](https://github.com/hesreallyhim/awesome-claude-code)). Links: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents and https://www.anthropic.com/engineering/multi-agent-research-system.

### Inferences
- **Memory choices for a company brain:**
  - Graphiti/Zep for facts that change over time (prices, owners, policies), since "what was true on date X" matters for business records.
  - Cognee or Supermemory to ingest documents from Drive, Gmail and Notion.
  - Mem0 for per-user preferences.
- **Supermemory's exit from the consumer company-brain app** suggests that a standalone horizontal company brain is a hard business. Vertical or regional positioning (WhatsApp-first, Arabic, Odoo/Zoho) may be the differentiator. This is my inference.

### Gaps
- **Vendor benchmarks conflict.** Mem0 reports 94.4 on LongMemEval versus 49.0 in an independent 2025 run.
- **Star counts unconfirmed.** I could not confirm current stars for Context7, Serena, BMAD or Task Master as of Nov 2026.
- **Arabic support unknown.** None of the memory vendors document Arabic-specific retrieval quality. I found no source on this.
