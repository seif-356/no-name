# Assemble an Egyptian company brain from open parts

A solo founder in Egypt can build a done-for-you "company brain" service almost entirely from commercially usable open-source parts, and the market data says the timing is right. The working recipe is: parse and OCR a client's messy files (Docling, MarkItDown, an Arabic-capable OCR tier), normalize Arabic text and deduplicate records (CAMeL Tools, Splink, OpenRefine), write everything into an Obsidian-compatible Markdown vault as the client-owned source of truth, index that vault with Meilisearch or Postgres + pgvector using Arabic-strong embeddings (BGE-M3, Snowflake arctic-embed-l-v2.0) and a reranker (bge-reranker-v2-m3), answer with an Arabic-first open model (Jais 3, Gemma 4, Egypt's own Karnak) on a single 128 GB desktop, and serve answers through a web chat (AnythingLLM, Onyx, Open WebUI) and the official WhatsApp Cloud API. Hosted rivals price at roughly **$16-50 per user per month** (Sentra Team $16, Onyx Cloud $20, GoSearch $20, Guru $25, Perplexity Enterprise $40, Glean $50+), and Lore charges **$350/month for 5 seats**; Growy already sells exactly the done-for-you model to operations-heavy businesses, and Riyadh's Gaia raised a **$1.5M pre-seed (Sep 2026)** for a sovereign on-prem AI layer. Those are proof the business exists, not proof it is taken: no vendor found positions as an Arabic-first internal company brain, no Arabic creator teaches the Obsidian/LLM-wiki pattern, and no Arabic-specific agent skills or MCP servers turned up. Egypt's data-protection regulations (MCIT Decree 816/2025, compliance deadline **1 Nov 2026**) require a licence for cross-border transfer of personal data, and Azure, AWS and GCP have no Egypt region, so "your data never leaves your office" becomes a selling point rather than a cost. The rest of this report gives the recommended starter stack, then a raw catalogue of roughly 1,400 entries by category with links; about 1,700 weaker entries sit in cache files listed near the end.

**How to read the marks in this report.** Star counts marked "(API)" were pulled live from the GitHub API on 15 Nov 2026 by the research notes. Star counts marked "~" come from an awesome-list snapshot of unknown date or from social posts and are **unverified**. Prices marked "(unverified)" come from model training knowledge rather than a 2026 source; other prices come from 2026 vendor or comparison pages (many written by competitors) and should still be re-checked before quoting to a client.

## A starter stack a solo founder can run from one office box

The stack below is a synthesis of the notes, not a sourced vendor recommendation. Each layer was chosen for three things: a licence that lets you sell a service on top, documented Arabic handling, and the ability to run on-premise in Egypt.

| Layer | Default pick | Alternatives / fallbacks | Why |
|---|---|---|---|
| Ingestion: files | [Docling](https://github.com/docling-project/docling) (MIT) + [MarkItDown](https://github.com/microsoft/markitdown) (MIT) | Unstructured (Apache-2.0), Kreuzberg (MIT), Apache Tika, Pandoc | MIT top to bottom, broadest format coverage, native chunkers |
| Ingestion: websites | [Crawl4AI](https://github.com/unclecode/crawl4ai) (Apache-2.0) | Firecrawl (AGPL core), Jina Reader | Permissive self-host crawler |
| Ingestion: WhatsApp history | [whatstk](https://github.com/lucasrodes/whatstk), [chat-miner](https://github.com/joweich/chat-miner) + [faster-whisper](https://github.com/SYSTRAN/faster-whisper) for voice notes | WhatsR (anonymizes), Pustur parser (Node) | Exported .txt/.zip chats into tables |
| Ingestion: SaaS/ERP | [n8n](https://github.com/n8n-io/n8n) or [Activepieces](https://github.com/activepieces/activepieces) + Odoo MCP servers | Nango, Airbyte, dlt, Composio | Odoo/Zoho/Drive/Excel are the common SMB sources |
| Arabic OCR | Gemini Flash-class API or Azure AI Document Intelligence for scans today | Self-hosted Qari-OCR, dots.ocr; Baseer (on-prem, commercial); Falcon-OCR-Arabic once weights ship | Best measured Arabic accuracy; see below |
| Cleanup | [CAMeL Tools](https://github.com/CAMeL-Lab/camel_tools) normalization, [Splink](https://github.com/moj-analytical-services/splink) (MIT) dedup, [OpenRefine](https://openrefine.org) for human review | PyArabic, Maha, RapidFuzz, ftfy, charset-normalizer | Alef/yaa/taa-marbuta unification, tatweel/diacritic stripping, name matching |
| Storage (system of record) | Obsidian-compatible Markdown vault in git, one note per entity/policy/SOP, plus Postgres for structured rows | [GBrain](https://github.com/garrytan/gbrain) (MIT, Markdown-first, Postgres-backed) | Human-auditable, client-owned, readable by any agent via filesystem MCP |
| Search index | [Meilisearch](https://github.com/meilisearch/meilisearch) hybrid search | Postgres + [pgvector](https://github.com/pgvector/pgvector) + [ParadeDB](https://github.com/paradedb/paradedb); Elasticsearch/OpenSearch for heavy use | Only engine with documented Arabic ال segmentation and diacritic removal |
| Embeddings + reranker | [BGE-M3](https://huggingface.co/BAAI/bge-m3) (MIT) or [arctic-embed-l-v2.0](https://huggingface.co/Snowflake/snowflake-arctic-embed-l-v2.0) (Apache-2.0) + [bge-reranker-v2-m3](https://huggingface.co/BAAI/bge-reranker-v2-m3) (Apache-2.0) | Qwen3-Embedding + Qwen3-Reranker; Namaa-ARA-Reranker | Top commercially licensed scores on the Arabic retrieval leaderboard |
| Answer model | [Jais-3-7B / 32B](https://huggingface.co/inception42) (Apache 2.0) | Gemma 4 12B/31B (Apache 2.0), Qwen3.8-27B (agents/tools), Karnak-40B (Egyptian, licence unclear); DeepSeek V4.1 Flash API for non-personal queries | Arabic-first, Egyptian dialect in training |
| Serving | [Ollama](https://github.com/ollama/ollama) / [llama.cpp](https://github.com/ggml-org/llama.cpp); [vLLM](https://github.com/vllm-project/vllm) for concurrency; [TEI](https://github.com/huggingface/text-embeddings-inference) for embeddings; [LiteLLM](https://github.com/BerriAI/litellm) gateway | MLX/LM Studio on Mac, SGLang, LocalAI | One box, OpenAI-compatible API, API fallback |
| Web chat | [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) (MIT) | Onyx (MIT core + EE), Open WebUI (branding clause), Kotaemon (cited answers), Morphic/Vane UIs | Easiest SMB deployment; permissive licence |
| WhatsApp | Official [WhatsApp Business Cloud API](https://developers.facebook.com/docs/whatsapp/cloud-api) direct or via a BSP (360dialog, Twilio, Unifonic, Infobip) | [Evolution API](https://github.com/evolution-foundation/evolution-api) in Cloud-API mode; [Chatwoot](https://github.com/chatwoot/chatwoot) for human handoff | Sanctioned; unofficial Baileys-based servers risk number bans |
| Local hardware | Mac Studio M5 Max 128 GB ($5,399) or AMD Ryzen AI Halo 128 GB ($3,999) | DGX Spark, RTX 5090 desktop, used 3x RTX 3090 | Runs 30B dense or ~120B MoE models for a small team |
| In-country hosting | Huawei Cloud Cairo region; Telecom Egypt RDH; e& Egypt Mokattam | Arab Computers, Cloud4Rain, MomentumX | No Azure/AWS/GCP region in Egypt |

### Why each default won

**Parsing and OCR.** Docling is MIT "top to bottom", supports pluggable OCR backends and ships structure-aware chunkers, while Marker's weights carry a revenue-capped OpenRAIL-M licence and PyMuPDF is AGPL ([LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers)). Those parsers do not solve Arabic scans on their own. On the 400-page Misraj-DocOCR Arabic benchmark the lowest word error rates were **Baseer 0.25, Gemini 2.5 Pro 0.37, Azure Document Intelligence 0.44, dots.ocr 0.50** and Qari 0.76, with Azure posting the lowest character error rate (0.27); the benchmark's author also built Baseer, a disclosed conflict ([Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026)). TII's 270M-parameter **Falcon-OCR-Arabic** scored 81.9% text accuracy, second only to Gemini 3.5 Flash (84.3%), and ranked first on official documents, forms, receipts and invoices, but its weights were not downloadable as of Oct-Nov 2026 ([Hugging Face](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic)). English leaderboards mislead here: Chandra OCR 2 tops olmOCR-Bench yet scores about 62% on the Arabic benchmark. The practical rule is Docling for born-digital files, a Gemini- or Azure-class API for scanned Arabic now, and Qari-OCR (open, handwriting in v0.3) or dots.ocr as free self-hosted fallbacks ([arXiv](https://arxiv.org/html/2506.02295v1)).

**Arabic cleanup.** CAMeL Tools provides letter-variant normalization, tatweel removal, Buckwalter transliteration, morphology and dialect identification across 25 city dialects ([LREC 2020](https://aclanthology.org/2020.lrec-1.868.pdf)). Arabic RAG guides recommend unifying alef/yaa/taa-marbuta variants, stripping diacritics and tatweel, chunking on document structure and always reranking ([Plugsky](https://plugsky.com/articles/how-to-build-arabic-ai-with-rag)), because Arabic's lexical variance makes rerankers unusually valuable ([arXiv 2506.06339](https://arxiv.org/html/2506.06339v1)). Apply the same normalization at index and query time, and test whether aggressive folding (such as ة→ه) hurts your embedder. For customer and supplier lists, add a transliteration key as a blocking column, then run Splink (MIT, DuckDB locally) for probabilistic matching ([Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/)).

**The Markdown vault as system of record.** Every parser above emits Markdown, and the most-copied "AI that knows your business" recipe on social video in 2025-2026 is a Markdown vault (Obsidian) read by Claude Code or Cowork, popularized as Karpathy's "LLM wiki". Garry Tan's **GBrain** is the open-source production version: Markdown-first, Postgres-backed, MIT, with a dedicated company-brain tutorial ([GitHub](https://github.com/garrytan/gbrain); [tutorial](https://github.com/garrytan/gbrain/blob/master/docs/tutorials/company-brain.md)); Y Combinator's Summer 2026 Request for Startups cited it when asking for "Garry's G-Brain, but for every business in the world" ([Slite](https://slite.com/learn/company-brain)). A plain vault with a filesystem MCP server becomes an AI-readable brain ([Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026)). For a done-for-you service, the vault gives the client files they own and can audit, lets you version every change in git, and makes the search index a disposable, rebuildable derivative. Useful helpers include [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) (~35.6k stars), [claude-obsidian](https://github.com/AgriciDaniel/claude-obsidian) (~6.8k) and [obsidian-second-brain](https://github.com/eugeniughelbur/obsidian-second-brain) (~4.9k).

**Search and embeddings.** Meilisearch documents Arabic article (ال) segmentation plus decomposition, digit conversion and diacritic removal, and supports hybrid keyword + vector search ([Meilisearch docs](https://www.meilisearch.com/docs/resources/help/language)); Typesense only offers an `ar` locale with RTL normalization ([Typesense](https://typesense.org/docs/guide/locale.html)). On the Arabic retrieval leaderboard, the top embedders are jina-embeddings-v4 (75.51), EmbeddingGemma-300m (75.37) and Snowflake arctic-embed-l-v2.0 (75.35), and the top reranker is BAAI bge-reranker-v2-m3 (87.44); jina v3 is licensed CC-BY-NC, so the safe commercial default is arctic-embed or BGE-M3 plus bge-reranker-v2-m3 ([Navid-AI leaderboard](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard)). These embedders run on CPU, so embedding is nearly free locally.

**The model.** **Jais 3** (Apache 2.0, released Oct 2026) comes in six sizes from 0.9B to 375B-A23B with 512K context, names Egyptian dialect in training and evaluation, and ships GGUF and MLX builds ([IFM](https://ifm.ai/blog/jais3/)); Jais-3-32B is the best open-weight model on SILMA's Arabic Broad Leaderboard at 8.99 ([SILMA](https://silma.ai/arabic-llm-leaderboard)). Egypt's **Karnak-40B** from the MCIT-backed Applied Innovation Center sits **#1 on the Open Arabic LLM Leaderboard (79.29)** and targets MSA plus Egyptian colloquial, but its licence was not captured, so check it before commercial use ([OALL](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard); [AIC](https://www.aic.gov.eg/news/43/)). **Gemma 4 31B** (Apache 2.0) scores 82.6 Arabic average and fits a 24 GB card at 4-bit ([Gemma 4 card](https://ai.google.dev/gemma/docs/core/model_card_4)). Vendor tables disagree with each other, so build a 50-100 question Egyptian-Arabic eval from a pilot client's real questions before choosing.

**WhatsApp.** Baileys-based servers (Evolution API in Baileys mode, WAHA) are cheap but operate outside WhatsApp's business terms and can get numbers banned, while the Cloud API costs money and is sanctioned ([oncloudapi](https://oncloudapi.com/blogs/evolution-api-vs-whatsapp-cloud-api-ban-risk-business-safety)). Evolution API can run in official Cloud API mode and already integrates with Chatwoot, Typebot, Dify and n8n ([GitHub](https://github.com/evolution-foundation/evolution-api)). Baileys is MIT but depends on GPLv3 libsignal, so isolate it behind a process boundary if you use it at all ([WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/)). Meta's per-message pricing for Egypt was not fetched in the research.

## Egypt's PDPL turns local hosting into the sales pitch

The Executive Regulations of Egypt's Personal Data Protection Law (Law 151/2020) were issued by **MCIT Decree No. 816 of 2025** and set tiered licences for processing, cross-border transfer, direct marketing and CCTV, with consent, DPO and breach-reporting duties ([JD Supra](https://www.jdsupra.com/legalnews/egypt-s-personal-data-protection-regime-4744548/)); the **compliance deadline was 1 November 2026** ([Lexis Middle East](https://www.lexismiddleeast.com/eJournal/2026-03-05_1/en)). The regulations generally prohibit transferring, storing or processing personal data outside Egypt without a licence or permit from the Personal Data Protection Center, plus consent unless an exception applies ([Ibrachy & Dermarkar](https://id.com.eg/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/)). Licence fees scale with record count: **exempt for 1-10,000 records**, capped at **EGP 2,000,000 per year** above 5 million records, with cross-border licensing at 50% of the base fee (same source).

The implication for this service is direct but needs a lawyer's confirmation: sending a client's customer or employee data in prompts to OpenRouter, DeepSeek or a US/EU cloud reads as cross-border processing, while an office box or in-country hosting avoids the question. **Azure, AWS and GCP have no Egypt region** (nearest are UAE, Qatar and South Africa); **Huawei Cloud Cairo** is the hyperscaler with a local region, and Telecom Egypt's Regional Data Hub and e& Egypt's Mokattam site are Tier III options ([MomentumX](https://momentumx.cloud/egypt-cloud-providers-2026/); [Arizton](https://www.arizton.com/market-reports/egypt-data-center-market)). A severe fire at a Telecom Egypt Cairo data centre caused national outages, so on-prem plus an off-site encrypted backup is prudent ([Arizton](https://www.arizton.com/market-reports/egypt-data-center-market)). A hybrid that routes only anonymized or non-personal questions to cheap APIs is the pragmatic middle path; [Microsoft Presidio](https://github.com/microsoft/presidio) can strip PII first, though its Arabic recognizers need extending.

Cost is not the reason to go local. For a 20-person SMB using about 60M input and 15M output tokens a month, DeepSeek V4.1 Flash at $0.038/$0.50 per million costs roughly **$10/month** and Qwen3.8-27B roughly **$37/month**, while a $3,999 Ryzen AI Halo or $5,399 Mac Studio amortizes to **$111-150/month** over three years, and an always-on rented RTX 5090 costs **$300-1,015/month** (the notes' own arithmetic on [OpenRouter](https://openrouter.ai/deepseek/deepseek-v4.1-flash-1017), [AI Engineer](https://theaiengineer.substack.com/p/mac-studio-vs-dgx-spark-vs-rtx-5090) and [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai) prices). Local wins on PDPL simplicity, offline resilience and access to Egyptian-dialect models such as Karnak that are not on every API. The box can be priced into the setup fee and owned by the client.

## Done-for-you rivals already exist, but none is Arabic-first

"Company brain" became a named category in 2026: Y Combinator listed it as idea #05 in its Summer 2026 Request for Startups, citing GBrain (MIT, 5 Apr 2026), and Slite's survey found 70% of teams know the term but only 20% have one ([Slite](https://slite.com/learn/company-brain); [Colrows](https://colrows.com/blogs/yc-company-brain-rfs/)). Managed platforms charge roughly **$10-100 per seat per month**, increasingly metered by usage or agent ([MultiplierAI](https://multiplierai.ai/resources/company-brain-software)). Almost every comparison page in this space is written by a vendor (Sentra, Slite, Gyld, Sento, Dust, MultiplierAI), so treat rankings as marketing. The buying question that matters for a done-for-you service is Sento's: "how expensive is a wrong answer?", which splits the field into auto-ingest brains (Hyper, Sentra, Coworker) and governed, curated brains (Sento, Slite, Guru) ([Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026)). A human-curated vault sold as a service sits firmly in the second camp.

### Correction: Growy, Lore and Gaia do exist

The research notes recorded these three as "not found"; the user supplied the following corrections, which this report adopts. **Growy** ([growy.app](https://growy.app)) sells done-for-you company brains for operations-heavy businesses, which is the closest known analogue to this founder's planned service and worth studying for packaging and pricing. **Gaia** ([gaia.sa](https://gaia.sa)) is a Riyadh company that raised a **$1.5M pre-seed in Sep 2026** for a sovereign, on-prem enterprise AI layer, the nearest regional competitor on the "data stays in-country" pitch. **Lore** is an AI knowledge base for companies under about 300 staff, priced at **Pro $350/month for 5 seats and Business $750/month for 10 seats** according to [brewsterconsulting.io](https://brewsterconsulting.io); Lore's own URL was not captured.

### Enterprise search and work-AI platforms

| Name | What it is | Public price (2026) | Notes |
|---|---|---|---|
| [Glean](https://www.glean.com) | Permission-aware enterprise search + agents, 275+ apps | No rate card; est. $45-65/user; median contract $98,890/yr; 100-250 seat minimums | MCP server for 22 hosts ([Sentra](https://www.sentra.app/articles/glean-alternatives)) |
| [Microsoft 365 Copilot / Copilot Business](https://www.microsoft.com/microsoft-365-copilot) | Assistant over Microsoft Graph | $30/user; Business $21 annual ($18 promo to 31 Dec 2026) | No seat minimum |
| [Copilot Studio](https://www.microsoft.com/microsoft-copilot/microsoft-copilot-studio) | Low-code agents over company data | Not verified | MCP host |
| [Gemini Enterprise](https://cloud.google.com/gemini-enterprise) (ex-Agentspace) | Google's enterprise search/chat/agents | Business from $21/seat; Standard/Plus from $30 | ~140 connectors on higher tiers; custom MCP |
| [Vertex AI Search / Agent Search](https://cloud.google.com/generative-ai-app-builder/pricing) | Usage-priced RAG building block | Usage-based | API |
| [ChatGPT Business / Enterprise](https://chatgpt.com/business) | "Company Knowledge" across connected apps | $20 annual / $25 monthly; 2-200 seats | |
| [Claude Team / Enterprise](https://claude.com/pricing) | Claude workspace with connectors and Projects | Not verified | MCP-native |
| [AWS Quick](https://aws.amazon.com/quick/pricing/) (ex-Amazon Q Business) | Agentic workspace + BI | $3-40/user; +$250/AWS account (sources conflict) | |
| [Coveo](https://www.coveo.com) | Enterprise relevance + generative answering | By request | Enterprise |
| [Lucidworks Fusion](https://lucidworks.com) | Self-hostable AI search | Not published | Enterprise |
| [Sinequa](https://www.sinequa.com) (ChapsVision) | Regulated-industry search/RAG | Not published | Multilingual (unverified) |
| [GoSearch](https://www.gosearch.ai) | Indexed + federated AI search | Free; Starter $8; Pro $20; Enterprise custom | Self-serve SMB option |
| [Moveworks](https://www.moveworks.com) (ServiceNow) | IT/HR assistant + search | Custom | Acquisition closed 2025 |
| [Onyx Cloud](https://onyx.app) (ex-Danswer) | Hosted OSS Glean alternative | CE free; Business $20/user | 40+ connectors |
| [Dust](https://dust.tt) | No-code agent workspace over company data | Pro EUR 24-30; Max EUR 120-150 | MCP; $40M Series B May 2026 |
| [Atlassian Rovo](https://www.atlassian.com/software/rovo) | Search/agents over Jira/Confluence | Included in eligible Cloud plans | |
| [Perplexity Enterprise](https://www.perplexity.ai/enterprise) | Web + Internal Knowledge Search | $40 Pro / $325 Max per seat | SOC 2, HIPAA |
| [SearchBlox SearchAI](https://www.searchblox.com) | Hybrid search + RAG + agents | Fixed-cost quote | |
| [Hebbia](https://www.hebbia.com) | Document AI for finance/legal | Per seat | |
| [Tricky Wombat](https://www.trickywombat.ai) | Project-scoped AI search | Not found | |
| [CData Connect AI](https://www.cdata.com/ai/) | Governed agent access to 300+ sources | Not verified | MCP |
| [Slack AI](https://slack.com/ai) | Answers over Slack + apps | Bundled (unverified) | |
| [Box AI](https://www.box.com/ai) | Q&A and agents over Box | Bundled (unverified) | |
| [Dropbox Dash](https://dash.dropbox.com) | Universal AI search | Unverified | |
| [Writer](https://writer.com) | Graph-based enterprise RAG | Custom (unverified) | |
| [Cohere North](https://cohere.com/north) | Private agentic workspace | Custom | Arabic-tuned models (unverified) |
| [Mistral Le Chat Enterprise](https://mistral.ai/products/le-chat) | EU-hosted assistant | Unverified | Mistral Saba Arabic model (unverified) |
| [Kore.ai](https://kore.ai) | Enterprise agent platform | Custom | |
| [Leena AI](https://leena.ai) | HR/IT employee agent | Custom | |
| [Vectara](https://www.vectara.com) | RAG-as-a-service | Free tier + usage (unverified) | |
| [Contextual AI](https://contextual.ai) | Enterprise RAG agents | Custom (unverified) | |

### Knowledge bases and wikis with AI

| Name | What it is | Price | Notes |
|---|---|---|---|
| [Guru](https://www.getguru.com) | "Governed knowledge layer" with verified cards | No longer published (one source says $25/seat) | |
| [Notion AI / Notion Agent](https://www.notion.com) | Wiki + agent + enterprise search | Business $20/member; Custom Agents $10/1,000 credits | Read-write Notion MCP |
| [Slite](https://slite.com) | Self-maintaining "company brain" KB | See vendor | |
| [Confluence + Rovo](https://www.atlassian.com/software/confluence) | Wiki with AI | Rovo included | |
| [Bloomfire](https://bloomfire.com) | Knowledge sharing with AI | Custom (unverified) | |
| [Sana](https://sanalabs.com) (Workday) | Knowledge assistant + learning | Bundled into Workday | ~$1.1B deal closed 4 Nov 2025 |
| [Document360](https://document360.com) | KB with "Eddy" AI | Tiered (unverified) | RTL support (unverified) |
| [Tettra](https://tettra.com) | Slack-centric wiki with AI Q&A | Unverified | 2026 status unknown |
| [Stack Overflow for Teams](https://stackoverflow.co/teams/) | Internal Q&A | Unverified | |
| [Shelf](https://shelf.io) | Content quality for gen-AI/CX | Custom | |
| [KMS Lighthouse](https://kmslh.com) | Contact-centre KM | Custom | |
| [ClickUp Brain](https://clickup.com/ai) | AI over tasks/docs + connected search | Add-on (unverified) | |
| [Taskade](https://www.taskade.com) | AI workspace and agents | Pro ~$10/mo for 10 users (vendor claim) | |
| [Docsie](https://www.docsie.io) | Docs portal with AI | Unverified | |
| [Helpjuice](https://helpjuice.com) | KB with AI search | ~$120-249/mo (unverified) | |
| [Slab](https://slab.com) | Team wiki + unified search | Unverified | |
| [Nuclino](https://www.nuclino.com) | Lightweight wiki with AI | Unverified | |
| [GitBook](https://www.gitbook.com) | Docs with AI and auto-MCP | Unverified | |
| [Archbee](https://www.archbee.com) | Docs portal with AI | Unverified | |
| [Coda AI](https://coda.io) | Doc-as-app with AI | Unverified | |
| [Trainual](https://trainual.com) | SOP/onboarding for small businesses | Per seat (unverified) | Good model for SOP capture |
| [Happeo](https://www.happeo.com) | Intranet with AI search | Custom | |
| [Simpplr](https://www.simpplr.com) | AI intranet | Custom | |
| [Capacity](https://capacity.com) | Support automation + KB | Unverified | |
| [eGain](https://www.egain.com) | Customer-service knowledge hub | Custom | |
| [Spekit](https://www.spekit.com) | Just-in-time enablement | Custom | |
| [Starmind](https://www.starmind.ai) | Expert finding | Custom | |
| [Zendesk Knowledge + AI agents](https://www.zendesk.com) | Help-centre KB powering agents | Per agent/resolution (unverified) | Arabic (unverified) |

### Second brains and personal-to-team memory

| Name | What it is | Price | Notes |
|---|---|---|---|
| [Mem 2.0](https://get.mem.ai) | Self-organizing AI notes | Free; Plus $9; Pro $29 | Read-write MCP |
| [Reflect](https://reflect.app) | Encrypted networked notes | ~$10/mo (unverified) | |
| [Tana](https://tana.inc) | Supertag outliner, team context for agents | Free + paid | Read-write MCP |
| [Capacities](https://capacities.io) | Object-typed notes | Free + Pro | MCP |
| [Heptabase](https://heptabase.com) | Visual whiteboard KB | ~$9-12 (unverified) | MCP |
| [Saner.AI](https://www.saner.ai) | Notes, tasks, email brain | Free + paid | |
| [Recall](https://www.getrecall.ai) | Save-and-chat knowledge graph | Free; Plus $12; Max $48 | Read-only MCP |
| [NotebookLM](https://notebooklm.google) | Source-grounded notebooks | Free; Enterprise via Cloud | Arabic (unverified) |
| [Supermemory Brain](https://supermemory.ai/brain/) | Slack-native team memory + memory API | Unverified | Company-brain app shut Sep 2026 to focus on engine ([Coworker](https://coworker.ai/blog/mem0-vs-zep-vs-letta)) |
| [Granola](https://www.granola.ai) | AI meeting notepad with team spaces | Unverified | |
| [Littlebird](https://littlebird.ai) | Screen + meeting auto-capture | Unverified | |
| [MemoryLake](https://memorylake.ai) | Portable memory across assistants | Free personal | MCP, CLI, REST |
| [BrainTube](https://brain-tube.com) | KB from videos/podcasts | Free incl. MCP | |
| [Obsidian](https://obsidian.md) | Local Markdown vault | Free; Sync/Publish paid | RTL (unverified); community MCP |
| [Limitless](https://www.limitless.ai) | Acquired by Meta; Pendant sales ended 5 Dec 2025 | n/a | Closed to new users |
| [Otter.ai](https://otter.ai) | Meeting transcripts + chat | Tiers (unverified) | |
| [Fireflies.ai](https://fireflies.ai) | Notetaker with "AskFred" | Tiers (unverified) | Arabic among 60+ languages (unverified) |
| [Read AI](https://www.read.ai) | Meeting/email copilot | Unverified | |
| [Logseq](https://logseq.com) | Open-source outliner | Free | |
| [MyMind](https://mymind.com) | Private visual save-everything | Paid | |

### The 2026 company-brain wave

| Name | What it is | Price | Notes |
|---|---|---|---|
| **[Growy](https://growy.app)** | Done-for-you company brains for operations-heavy businesses | Not captured | Closest model for this service (user correction) |
| **[Gaia](https://gaia.sa)** | Riyadh sovereign on-prem enterprise AI layer | Not captured | $1.5M pre-seed Sep 2026 (user correction) |
| **Lore** | AI knowledge base for companies under ~300 staff | Pro $350/mo (5 seats); Business $750/mo (10 seats) | Per [brewsterconsulting.io](https://brewsterconsulting.io) (user correction) |
| Hyper (YC Spring 2026) | "Self-driving company brain" from Slack, Notion, Gmail, PRs | Not found | "$1K MRR in 12 days" (vendor blog, unverified) ([Startground](https://startground.com/y-combinator-spring-2026-startups/)) |
| [Sentra](https://www.sentra.app) | Managed org memory as time-stamped facts; flags contradictions | Team $16/user (2-20 people) | Only explicit SMB tier found; MCP + REST |
| [Coworker](https://coworker.ai) | "OM2" organizational memory + task execution | Not found | 50+ connectors |
| [Gyld](https://gyld.ai) | Knowledge layer from existing apps served as MCP | Not found | Per-source permissions |
| [Klikflo](https://klikflo.com) | Auto-assembled operating model of the business | Not found | URL unverified |
| [Company Brain](https://www.company-brain.ai) | Products, rules, brand voice to any AI via MCP | Not found | |
| [Merge for Workforce](https://www.merge.dev/workforce) | Universal Context Layer | Not found | SOC 2, ISO 27001 |
| [MultiplierAI](https://multiplierai.ai) | Revenue-scoped brain, service-led | Not found | |
| [Sento](https://www.sentohq.com) | Governed, versioned knowledge entities over MCP | Early access; free onboarding | Targets 10-200 people |
| Carrara | Neon Postgres memory + macOS app; human-approved memories | Not found | URL not captured |
| Pletor | Model-independent dedicated brain | Not found | URL not captured |
| Plek AI | Company brain for private-equity value creation (YC F2026) | Not found | [YC](https://www.ycombinator.com/companies/industry/ai) |
| [PromptQL](https://promptql.io) (Hasura) | Permissioned data/agent layer | Unverified | |
| [Vectorize](https://vectorize.io) | RAG pipelines; "how to build a company brain" guide | Free + usage (unverified) | |
| [Mem0](https://mem0.ai) | Agent memory library + hosted platform | Free + paid | Hosted MCP |
| [Zep](https://www.getzep.com) | Temporal context graph (Graphiti) | Unverified | |
| [Cognee](https://www.cognee.ai) | Open-source graph memory + enterprise BYOC | OSS free | MCP |

### SMB "chatbot on your docs" builders (many deploy to WhatsApp)

| Name | Price | Channels / notes |
|---|---|---|
| [Chatbase](https://www.chatbase.co) | Free; Hobby $40; Standard $150; Pro $500 | Web, WhatsApp (unverified) |
| [CustomGPT.ai](https://customgpt.ai) | $99, then $499 | Citations focus |
| [Botpress](https://botpress.com) | New plans since May 2026: Plus $150/mo, Team $750/mo (older: $89/$495 + AI spend) | Web, WhatsApp |
| [Voiceflow](https://www.voiceflow.com) | Pro ~$60; Business ~$150 | Chat + voice |
| [Stack AI](https://www.stack-ai.com) | Unverified | Enterprise no-code |
| [DocsBot AI](https://docsbot.ai) | ~$19-49 (unverified) | |
| [SiteGPT](https://sitegpt.ai) | $259 plan (Reddit report) | |
| [Tidio Lyro](https://www.tidio.com) | Per conversation (unverified) | |
| [Intercom Fin](https://www.intercom.com/fin) | $0.99 per resolution | Arabic among 45 languages (unverified) |
| [Jotform AI Agents](https://www.jotform.com/ai/agents/) | Free; $34-99 annual | Web, phone, WhatsApp |
| [Lindy](https://www.lindy.ai) | Prices conflict: $29.99-49.99/user; Business $199.99 | |
| [Botsonic](https://writesonic.com/botsonic) | $16-249 | |
| [Ingest AI](https://ingestai.io) | $25-60 | |
| [Denser AI](https://denser.ai) | $29-399 | |
| [YourGPT](https://yourgpt.ai) | $39-349 | WhatsApp, Telegram |
| [eesel AI](https://www.eesel.ai) | ~$0.40/ticket, no seats | Internal Slack/Teams answers |
| [HelpJet](https://helpjet.com) | Free; Pro $29 | |
| [Landbot](https://landbot.io) | EUR 40-400; WhatsApp Pro EUR 200 | WhatsApp |
| [Chat Data](https://www.chat-data.com) | Unverified | WhatsApp, Slack, Discord |
| [SiteSpeak AI](https://sitespeak.ai) | Unverified | |
| [Docuyond](https://docuyond.com) | Not captured | |
| [Teammates.ai](https://teammates.ai) | Free plan | 50+ languages; active in Saudi |
| [ManyChat](https://manychat.com) | Free; Pro from $15 | IG, FB, WhatsApp, TikTok |
| [Ada](https://www.ada.cx) | Contact sales | Enterprise |
| [Yellow.ai](https://yellow.ai) | Free + sales | Strong in MENA (unverified) |
| [Haptik](https://www.haptik.ai) | Contact sales | WhatsApp; MENA (unverified) |
| [Fini](https://www.usefini.com) | Unverified | |
| [Decagon](https://decagon.ai) | Custom | |
| [IrisAgent](https://irisagent.com) | Usage/resolution | |
| [Gorgias AI Agent](https://www.gorgias.com) | Per resolution (unverified) | E-commerce |
| [HubSpot Breeze](https://www.hubspot.com/products/artificial-intelligence) | Credits (unverified) | |
| [Freshworks Freddy AI](https://www.freshworks.com/freddy-ai/) | Unverified | Arabic (unverified) |
| [Crisp](https://crisp.chat) | ~$45-95 (unverified) | WhatsApp |
| [Kapa.ai](https://www.kapa.ai) | Custom | Docs |
| [Inkeep](https://inkeep.com) | Custom | Docs |

Credit-based plans can silently stop a bot when credits run out ([IrisAgent](https://irisagent.com/blog/best-chatbase-alternatives/)), a useful contrast to sell against with a flat monthly retainer.

### MENA and Arabic-first vendors

| Name | What it is | Notes |
|---|---|---|
| [DXwand](https://dxwand.com) | Cairo/Dubai conversational AI + knowledge mining, dialect-aware | Contracts $50k-400k/yr (2024); $4M Series A Jan 2024 ([TechCrunch](https://techcrunch.com/2024/01/25/dxwand-raises-4m-to-scale-its-conversational-ai-platform-for-enterprises-in-mena/)) |
| [WideBot](https://widebot.ai) | Arabic-first AI-as-a-service, Riyadh + Cairo | $3M pre-Series A Feb 2025 |
| [Arabic.AI](https://arabic.ai) | Arabic enterprise LLM platform | Azure Saudi region partner; HUMAIN investment Sep 2026 ([newsroom](https://arabic.ai/company/newsroom/)) |
| [MOZN](https://www.mozn.ai) | Sovereign Arabic enterprise AI | Government focus |
| [Maqsam](https://maqsam.com) | Call centre + Arabic AI agent | |
| [Arabot](https://arabot.io) | Arabic conversational platform | |
| [Lucidya](https://lucidya.com) | AI-native CX and social listening | |
| [Labiba](https://labiba.ai) | Saudi conversational/voice AI | |
| Labeah AI | KSA chatbots/callbots | URL not captured |
| [Hams.ai](https://hams.ai) | Saudi voice/chat/WhatsApp support | |
| [Elbi](https://a-i.sa) | Answers from approved documents on chat/voice/WhatsApp; data in KSA | Closest MENA analogue on the customer-facing side |
| LeapAI | Saudi CX + WhatsApp Business | URL not captured |
| Sarj AI | Document intelligence + back office | URL not captured |
| [HUMAIN Chat](https://humain.ai) (ALLaM) | Saudi consumer Arabic chat | Not deployable |
| [Wittify.ai](https://wittify.ai) | Arabic voice/text agents | |
| Munsit | Arabic ASR, 25+ dialects (UAE) | Component |
| [Wati](https://www.wati.io) | WhatsApp business messaging with KB bot | Widely used in GCC |
| **[Gaia](https://gaia.sa)** | Sovereign on-prem enterprise AI (Riyadh) | $1.5M pre-seed Sep 2026 |

The notes' inference holds: an Arabic SMB today would pair a global brain with an Arabic customer-facing vendor, leaving a visible gap for an Arabic-first internal company brain ([Elbi](https://a-i.sa/blog/best-ai-chatbot-platforms-saudi-arabia/)).


## Open-source platforms you can fork or deploy

About 50 active open-source platforms can be deployed as a company brain. None of them ships WhatsApp natively, so the practical setup is a channel layer (the official WhatsApp Cloud API, Evolution API in Cloud-API mode, Chatwoot or n8n) in front of the platform's API. Several of the most popular platforms use custom licences that restrict white-label resale, so check the licence before you rebrand one for a client. Star counts below are from the GitHub API on 15 Nov 2026.

| Repo | Stars (API) | Licence | Fit for this service |
|---|---|---|---|
| [langgenius/dify](https://github.com/langgenius/dify) | 161.2k | Custom (check before resale) | Workflows plus RAG; cloud, VPC or self-host |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | 158.7k | Custom (branding clause) | Best-known local ChatGPT-style UI with knowledge bases |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | 94.2k | Apache-2.0 | Strongest document parsing among the platforms |
| [Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) | 68.3k | MIT | Easiest small-business deployment; permissive licence |
| [zylon-ai/private-gpt](https://github.com/zylon-ai/private-gpt) | 57.6k | Apache-2.0 | Private API layer on local models |
| [LibreChat-AI/LibreChat](https://github.com/LibreChat-AI/LibreChat) | 47.1k | MIT | Multi-model chat with agents, MCP and skills |
| [lfnovo/open-notebook](https://github.com/lfnovo/open-notebook) | 42.0k | MIT | Open-source NotebookLM alternative |
| [khoj-ai/khoj](https://github.com/khoj-ai/khoj) | 38.1k | AGPL-3.0 | Self-hostable second brain over docs plus web |
| [Tencent/WeKnora](https://github.com/Tencent/WeKnora) | 37.4k | Custom | RAG plus a self-maintaining wiki |
| [onyx-dot-app/onyx](https://github.com/onyx-dot-app/onyx) | 33.4k | MIT core + enterprise | Top fork candidate: connectors and permissions |
| [garrytan/gbrain](https://github.com/garrytan/gbrain) | 33.0k | MIT | Markdown-first brain; the YC "company brain" reference |
| [labring/FastGPT](https://github.com/labring/FastGPT) | 30.0k | Custom | Knowledge-base platform with visual workflows |
| [Cinnamon/kotaemon](https://github.com/Cinnamon/kotaemon) | 25.9k | Apache-2.0 | Clean document Q&A with cited answers |
| [1Panel-dev/MaxKB](https://github.com/1Panel-dev/MaxKB) | 23.2k | GPL-3.0 | Enterprise knowledge-base agent platform |

**Frameworks and building blocks.** These are mostly permissively licensed:
- **Pipelines:** [LlamaIndex](https://github.com/run-llama/llama_index), [LangChain/LangGraph](https://github.com/langchain-ai/langgraph), [Haystack](https://github.com/deepset-ai/haystack), [DSPy](https://github.com/stanfordnlp/dspy), [txtai](https://github.com/neuml/txtai).
- **Graph retrieval:** [LightRAG](https://github.com/HKUDS/LightRAG), [Microsoft GraphRAG](https://github.com/microsoft/graphrag), [Cognee](https://github.com/topoteretes/cognee), [Graphiti](https://github.com/getzep/graphiti).
- **Memory:** [Mem0](https://github.com/mem0ai/mem0), [Letta](https://github.com/letta-ai/letta), [Supermemory](https://github.com/supermemoryai/supermemory).

**Vector stores.** The low-maintenance choices for a small deployment:
- **[pgvector](https://github.com/pgvector/pgvector):** one Postgres for app data, permissions and vectors.
- **[Qdrant](https://github.com/qdrant/qdrant):** a single container with strong filtering.
- **[LanceDB](https://github.com/lancedb/lancedb) or sqlite-vec:** embedded, with no server to run.
- **OpenSearch or Elasticsearch:** when you need per-document security and Arabic full-text analysis.

**Evaluation and monitoring.** Use these before showing a client accuracy numbers:
- **Answer-quality testing:** [Ragas](https://github.com/explodinggradients/ragas), [DeepEval](https://github.com/confident-ai/deepeval), [promptfoo](https://github.com/promptfoo/promptfoo).
- **Tracing:** [Langfuse](https://github.com/langfuse/langfuse), [Phoenix](https://github.com/Arize-ai/phoenix).
- **Personal-data redaction:** [Presidio](https://github.com/microsoft/presidio).

**Lists to mine for more:** [awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps), [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted), [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques).

Full table: 391 strong repos in `research_notes/.../open_source_rag_repos.md`; 991 weaker, archived or stale repos in the cache file.

## Answer engines and search infrastructure (Perplexity-, Meilisearch- and Mem-style)

**Hosted answer engines** have consolidated around Perplexity, ChatGPT Search, Google AI Mode/Gemini, Copilot, Brave and Kagi. [Phind](https://www.phind.com) shut down on 16 Jan 2026, and You.com pivoted to selling enterprise search APIs. Hosted "answer from company data" products cost $20–50+ per user per month, which is the price ceiling you undercut.

**Open-source Perplexity clones:**

| Repo | Stars (API) | Licence | Note |
|---|---|---|---|
| [ItzCrazyKns/Vane](https://github.com/ItzCrazyKns/Vane) (formerly Perplexica) | 38.2k | MIT | Web plus local-file answer engine on SearXNG |
| [khoj-ai/khoj](https://github.com/khoj-ai/khoj) | 38.1k | AGPL-3.0 | Already answers from personal docs plus the web |
| [zaidmukaddam/scira](https://github.com/zaidmukaddam/scira) (formerly MiniPerplx) | 11.9k | AGPL-3.0 | Search UI |
| [miurla/morphic](https://github.com/miurla/morphic) | 9.3k | Apache-2.0 | Very active; permissive |
| MindSearch, FreeAskInternet, LLM-Answer-Engine | — | Various | Older clones; Farfalle and OpenPerplex are stale |

**Search infrastructure for Arabic:**
- **[Meilisearch](https://github.com/meilisearch/meilisearch):** documented Arabic segmentation of ال and diacritic removal, plus hybrid keyword and vector search. Best default.
- **Elasticsearch / [OpenSearch](https://github.com/opensearch-project/OpenSearch):** a mature built-in Arabic analyzer and BM25 + kNN hybrid search.
- **Postgres + pgvector + [ParadeDB](https://github.com/paradedb/paradedb):** one database for everything.
- **[Typesense](https://github.com/typesense/typesense):** has an `ar` locale, but weaker Arabic handling.
- **For heavier hybrid workloads:** [Manticore](https://github.com/manticoresoftware/manticoresearch), [Vespa](https://github.com/vespa-engine/vespa), Infinity.

**Search APIs for live web answers.** These typically cost $1–8 per 1,000 queries:
- **APIs:** [Tavily](https://tavily.com) (acquired by Nebius, Feb 2026), [Exa](https://exa.ai), [Brave Search API](https://brave.com/search/api/), [Parallel](https://parallel.ai), [Linkup](https://www.linkup.so), [Perplexity Sonar](https://docs.perplexity.ai), [Firecrawl Search](https://www.firecrawl.dev), [Jina](https://jina.ai), [Serper](https://serper.dev), SerpApi.
- **Retired:** the Bing Search API, on 11 Aug 2025.

**Mem-style second brains** (Mem, Reflect, Tana, Capacities, Heptabase, Recall, NotebookLM, Supermemory) are covered under the company-brain products section above.

Full tables: 213 rows in `answer_and_search_engines.md`, plus 194 in its cache.

## Data cleanup, OCR and Arabic tools (your 70% package)

| Step | Recommended | Also consider | Watch out |
|---|---|---|---|
| PDF/Office parsing | [Docling](https://github.com/docling-project/docling) (MIT), [MarkItDown](https://github.com/microsoft/markitdown) (MIT) | [Unstructured](https://github.com/Unstructured-IO/unstructured), [MinerU](https://github.com/opendatalab/MinerU), [Marker](https://github.com/datalab-to/marker) | Marker weights are revenue-capped; PyMuPDF is AGPL |
| Arabic OCR | Gemini Flash-class API, Azure Document Intelligence | [Qari-OCR](https://huggingface.co/NAMAA-Space), [dots.ocr](https://github.com/rednote-hilab/dots.ocr), Baseer (Misraj), [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR) | Benchmarks are vendor-run; English leaders can fall to ~62% on Arabic |
| Web crawling | [Crawl4AI](https://github.com/unclecode/crawl4ai) (Apache-2.0) | [Firecrawl](https://github.com/firecrawl/firecrawl) (AGPL), Jina Reader, [Crawlee](https://github.com/apify/crawlee) | AGPL can force you to release your code |
| SaaS sync | [Nango](https://github.com/NangoHQ/nango), [Airbyte](https://github.com/airbytehq/airbyte), [dlt](https://github.com/dlt-hub/dlt) | Merge, Unified.to, Paragon, Composio | Integration counts are vendor claims |
| WhatsApp history | [whatstk](https://github.com/lucasrodes/whatstk), whatsapp-chat-parser, WhatsR | — | Untested on exports from Arabic-locale phones |
| WhatsApp serving | Official Cloud API | [Evolution API](https://github.com/EvolutionAPI/evolution-api) in Cloud-API mode, [Chatwoot](https://github.com/chatwoot/chatwoot) | Baileys/WAHA mode risks number bans |
| Dedup / entity resolution | [Splink](https://github.com/moj-analytical-services/splink) (MIT) | [dedupe](https://github.com/dedupeio/dedupe), [Zingg](https://github.com/zinggAI/zingg) (AGPL), [OpenRefine](https://openrefine.org) | Normalize Arabic names first |
| Arabic normalization | [CAMeL Tools](https://github.com/CAMeL-Lab/camel_tools) | [PyArabic](https://github.com/linuxscout/pyarabic), Farasa | — |
| Chunking / graphs | [Chonkie](https://github.com/chonkie-inc/chonkie), Docling chunkers | GraphRAG, LightRAG, Graphiti, [Neo4j LLM Graph Builder](https://github.com/neo4j-labs/llm-graph-builder), Cognee | Graph tools are untested on Arabic |
| Embeddings / reranking | arctic-embed-l-v2.0, BGE-M3, EmbeddingGemma-300m; bge-reranker-v2-m3 | jina-embeddings-v4 (top score), Namaa ARA-Reranker | jina v3/v4 are listed as non-commercial |

Full tables: 219 rows in `data_ingestion_cleanup.md`, plus 106 in its cache.

## Local models, serving and hosting

These are already set out in the starter stack and the PDPL section above. In short:
- **Arabic-first models:** Jais 3 (Apache 2.0, Egyptian dialect in training) and Karnak (#1 on the Open Arabic LLM Leaderboard; licence unconfirmed). Fanar-2-27B is Apache 2.0. ALLaM-7B has only a 4K context and unclear commercial terms.
- **General local models:** Gemma 4 and Qwen3.5–3.8 (both Apache 2.0) are the best general local options.
- **Serving software:**
  - [Ollama](https://github.com/ollama/ollama) or [llama.cpp](https://github.com/ggml-org/llama.cpp) on one box.
  - [vLLM](https://github.com/vllm-project/vllm) or [SGLang](https://github.com/sgl-project/sglang) for many concurrent users.
  - [LiteLLM](https://github.com/BerriAI/litellm) as a gateway in front of local and API models.

Full tables: 128 entries in `local_models_hosting.md`, plus 118 in its cache.

## Skills, MCP servers and developer tools

- **Skills are a shared standard** ([agentskills.io](http://agentskills.io)) across Claude, Codex, Gemini CLI and Cursor.
  - [anthropics/skills](https://github.com/anthropics/skills) has production docx, pdf, xlsx and pptx skills, plus `mcp-builder` for writing your own Odoo, Zoho or WhatsApp connectors.
  - Google publishes official Workspace skills.
  - [NVIDIA SkillSpector](https://github.com/NVIDIA/SkillSpector) scans community skills for risky instructions before you install them.
  - Discovery lists: [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills), [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills), skills.sh.
- **MCP servers:**
  - The official [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) repo keeps only 7 reference servers.
  - Registries hold far more: Glama (~99–121k), Smithery (26k+), PulseMCP (~21.7k), mcp.so (~20.5k), plus the official registry.
  - Servers exist for WhatsApp (12; prefer the Business-API ones), Odoo (5), Excel, Microsoft 365 and Zoho Mail.
  - **No Arabic NLP/OCR MCP server was found.** That is a gap you could fill.
- **Gateways:**
  - [Composio](https://composio.dev): 1,000+ toolkits; free tier of 100K calls a month.
  - Pipedream: 3,000+ apps.
  - Zapier MCP: 9,000+ apps; each call costs 2 tasks.
  - Self-hosted options: [MetaMCP](https://github.com/metatool-ai/metamcp) and MCPJungle.
- **Coding agents for a solo builder:**
  - Claude Code led Terminal-Bench 4.0 at 64.8% (Oct 2026), ahead of Codex at 58.2%.
  - Alternatives: opencode, Gemini CLI, Cline, Roo, Aider.
- **Memory and context tools.** Star counts here come from community lists and are unverified:
  - Mem0 (~66k), Graphiti/Zep (~31k; it tracks when each fact was true), Cognee (~31k), Letta (~25k).
  - claude-mem (~82k), Spec Kit (~71k), Task Master (~25k).

Full lists: about 250 entries in `skills_mcp_devtools.md`, plus about 520 in its cache.

## Agents and workflow automation (for the 30% custom work)

| Need | Recommended | Notes |
|---|---|---|
| Workflow automation hub | [n8n](https://github.com/n8n-io/n8n) (210k stars, fair-code; cloud from €20/mo) | De facto standard; huge Arabic creator coverage |
| Truly open alternative | [Activepieces](https://github.com/activepieces/activepieces) (25.5k, MIT core) | Friendliest fully open option |
| Hosted, non-technical | Zapier (from $19.99/mo; Agents from ~$33/mo), Make (from $9/mo), Gumloop ($37/mo) | Zapier costs the most at volume |
| Visual agent builders | Dify (161k), [Langflow](https://github.com/langflow-ai/langflow) (157k), [Sim](https://github.com/simstudioai/sim) (30k, Apache-2.0) | **Flowise is dead**: archived Aug 2026, with unpatched advisories |
| General agents | Claude Cowork, Manus and Genspark (~$20/mo and up); OSS: OpenClaw (394k), Hermes Agent (263k), Kortix CompanyOS (formerly Suna) | OpenAI retired Operator, and its Agent Builder shuts down 30 Nov 2026 |
| Frameworks (developer-only) | LangGraph, CrewAI, Agno, OpenAI Agents SDK, Claude Agent SDK, Pydantic AI, Mastra | Only if you build custom agents |
| Browser automation | [Browser Use](https://github.com/browser-use/browser-use) (121k), [Skyvern](https://github.com/Skyvern-AI/skyvern) (AGPL; business workflows), Playwright MCP | For clients' systems that have no API |

Full tables: 241 rows in `agents_automation.md`, plus 487 in its cache.

## Reels, videos and creators

- **The dominant recipe in 2025–2026 social content** is Claude Code or Cowork plus an Obsidian/Markdown vault, often framed as "Karpathy's LLM Wiki". This is the same architecture as the starter stack above.
- **Other common recipes:** n8n + Supabase RAG agents, Notion AI agents, NotebookLM and GBrain.
- **How each platform is used:** Instagram reels mostly use a "comment BRAIN and I'll DM you" funnel, while YouTube carries the full walkthroughs.
- **English creators to follow:**
  - YouTube: Nate Herk (~1.1M subscribers), Cole Medin, Matthew Berman, Matt Wolfe, Liam Ottley, IndyDevDan, AI Jason, Chase AI, Jack Roberts, Ben AI, Greg Isenberg.
  - Instagram/TikTok repo posters: Nick Saraev, Varun Mayya, @nocode.joshua.
  - X: @akshay_pachaar, @_avichawla, @AlphaSignalAI.
- **Arabic, mostly Egyptian, creators:** Mohamed Al Assaal (878K subscribers), Yasser Seleem, مدرسة الذكاء الاصطناعي (Arabian AI School, 158K), Abu Bakr Soliman (RAG/CrewAI), Ibrahem | AI بالعربي, Codezilla, Bassem Magdy.
  - **No Arabic content on "company brain" was found.** The closest framing is the "digital employee" (موظف رقمي). That is an open content angle for marketing your service in Egypt.
- **Tools the posts keep pointing to:** GBrain, the Karpathy LLM-Wiki pattern, Graphify, InfraNodus, Cognee, claude-mem, Recall, Rowboat, Context7, Firecrawl MCP, NotebookLM.

Full lists: about 335 posts and creators in `social_reels_creators.md`, plus about 180 in its cache. X, Threads, TikTok and Instagram are only partly indexed by search engines, so coverage there is incomplete.

## Full catalogue index

The report above covers the most useful items. Everything the research found is in Markdown files next to this report, with links. The strong entries are in the main files; the weaker, stale, archived or duplicate entries were kept in the cache files rather than deleted.

| Topic | Main file (strong) | Cache file (weaker) | Unique links (main / cache) |
|---|---|---|---|
| Company-brain products | [company_brain_products.md](../research_notes/Company%20brain%20tools%20and%20repos/company_brain_products.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/company_brain_products_cache.md) | 195 / 119 |
| Answer and search engines | [answer_and_search_engines.md](../research_notes/Company%20brain%20tools%20and%20repos/answer_and_search_engines.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/answer_and_search_engines_cache.md) | 246 / 225 |
| Open-source RAG repos | [open_source_rag_repos.md](../research_notes/Company%20brain%20tools%20and%20repos/open_source_rag_repos.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/open_source_rag_repos_cache.md) | 406 / 1,183 |
| Data cleanup, OCR, Arabic | [data_ingestion_cleanup.md](../research_notes/Company%20brain%20tools%20and%20repos/data_ingestion_cleanup.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/data_ingestion_cleanup_cache.md) | 262 / 125 |
| Local models and hosting | [local_models_hosting.md](../research_notes/Company%20brain%20tools%20and%20repos/local_models_hosting.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/local_models_hosting_cache.md) | 142 / 107 |
| Skills, MCP, dev tools | [skills_mcp_devtools.md](../research_notes/Company%20brain%20tools%20and%20repos/skills_mcp_devtools.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/skills_mcp_devtools_cache.md) | 287 / 522 |
| Agents and automation | [agents_automation.md](../research_notes/Company%20brain%20tools%20and%20repos/agents_automation.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/agents_automation_cache.md) | 262 / 492 |
| Reels and creators | [social_reels_creators.md](../research_notes/Company%20brain%20tools%20and%20repos/social_reels_creators.md) | [cache](../research_notes/Company%20brain%20tools%20and%20repos/social_reels_creators_cache.md) | 332 / 273 |
| **Total** | | | **~4,500 unique links, including ~2,950 GitHub repos** |

## Limitations

- **The 10,000 target was not reached.** About 4,500 unique links were collected. Beyond that, the remaining results were mostly duplicates and near-empty repos.
- **Star counts are uneven.**
  - Open-source RAG repos, plus part of the answer-engine and agent tables, have star counts pulled live from the GitHub API on 15 Nov 2026.
  - Skills, MCP and memory-tool counts come from community lists of unknown date. A few look inflated.
- **Some entries come from background knowledge.** About a third to a half of the entries in the local-model, data-cleanup and products files are marked as such, not re-checked in 2026. Confirm licences and prices before quoting them to a client.
- **The Arabic benchmarks are run by vendors.** Misraj built both the Misraj-DocOCR benchmark and Baseer, and TII built Falcon-OCR-Arabic. There is no independent Arabic OCR comparison yet.
- **The PDPL reading is not legal advice.** Confirm the cross-border licensing implications with Egyptian counsel.
- **Social platforms are only partly indexed.** X, Threads, TikTok and Instagram coverage is a sample, not a census.
- **This report was finished after an interruption.** A usage limit stopped the writing midway, and the sections from "Open-source platforms you can fork or deploy" onward were completed from the research notes' summaries rather than a full re-read of every table.
