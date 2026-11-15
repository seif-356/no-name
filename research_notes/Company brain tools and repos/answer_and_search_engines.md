# AI Answer Engines & Search Engines for a "Company Brain" (catalogue, as of 15 Nov 2026)

Scope: hosted and open-source AI answer engines, search engine infrastructure, search APIs for agents, and open-source "Perplexity clones" that could be used or cloned to build a company brain (an AI that answers from a company's own data, with citations) for small Egyptian/Arabic businesses.

**How the data was gathered.** GitHub star counts, SPDX license, last-push date and archived flag for every repo row come from the GitHub REST search API, queried on 2026-11-15 (`api.github.com/search/repositories`, with `repo:` qualifiers and topic queries). Each repo row links to its GitHub page, which is the source for those numbers. "NOASSERTION" means GitHub could not detect one SPDX license. Usually that is a dual or custom license (e.g. MIT core plus a proprietary enterprise folder, or a "modified Apache" license). Check before you fork. Pricing comes from vendor pages and 2026 comparison blogs cited inline; "?" means I did not verify it this session.

**Relevance key (for a company brain for small Egyptian/Arabic businesses):** **H** = could be the core of the product or a direct template to clone; **M** = a useful component or reference; **L** = marginal (the weakest entries are in the cache file `answer_and_search_engines_cache.md`).

---

## Q1. Which AI answer engines exist (hosted/commercial), and which are relevant to a company brain?

### Takeaway
The hosted consumer market has consolidated around Perplexity, ChatGPT Search, Google AI Mode/Gemini, Copilot, Brave (Ask Brave), Kagi and a long tail of Chinese engines. Phind shut down on 16 Jan 2026, and You.com pivoted from a consumer engine to selling enterprise search APIs. For a company brain, the most relevant hosted products are the enterprise "answer from your company data" products: Glean, Onyx Cloud, Dust, GoSearch, Guru, Perplexity Enterprise (Internal Knowledge Search), Gemini Enterprise, Amazon Quick, M365 Copilot and Notion AI. They show the price ceiling ($20–50+/user/month) that an Egyptian SMB product would undercut.

### Cited Findings

**Status/discontinuation facts**
- Phind (developer AI search) shut down on 16 Jan 2026 with about two weeks' notice. Coverage attributes it to competition from frontier-model products — [intelligenttools.co](https://intelligenttools.co/blog/improved-phind-shutdown-post); [HN thread](https://news.ycombinator.com/item?id=46595637); [agentsai.fyi](https://agentsai.fyi/agents/phind)
- You.com pivoted from consumer search to enterprise AI and web search APIs. It says it runs its own index and queries "400+ sources" for research answers — [The New Stack](https://thenewstack.io/how-you-com-survived-chatgpt-with-a-pivot-to-enterprise-ai/)
- Yahoo launched "Yahoo Scout", a new AI answer engine, on 27 Jan 2026 — [felladrin/awesome-ai-web-search](https://github.com/felladrin/awesome-ai-web-search) (links the [Yahoo press release](https://www.yahooinc.com/press/introducing-yahoo-scout-a-new-ai-answer-engine))
- Perplexity pricing in 2026: Free $0, Pro $20/mo, Max $200/mo, Enterprise Pro $40/seat/mo, Enterprise Max $325/seat/mo. The API is billed separately from $1 per million tokens, and the small API credit bundled with Pro was removed in early 2026 — [CloudZero](https://www.cloudzero.com/blog/perplexity-pricing/); [Coworker](https://coworker.ai/blog/perplexity-enterprise-pricing). Perplexity's own pricing page shows $17/mo and $167/mo, which are probably annual-billing equivalents — [perplexity.ai/hub/pricing](https://www.perplexity.ai/hub/pricing) (conflict noted)
- Perplexity Enterprise includes org-wide "Internal Knowledge Search" across connected apps and files, plus SOC 2 Type II and HIPAA compliance — [Coworker](https://coworker.ai/blog/perplexity-enterprise-pricing)
- Kagi plans: Starter $5/mo (300 searches), Professional $10/mo (unlimited), Ultimate $25/mo — [cloro.dev](https://cloro.dev/blog/ai-search-engines/) citing [help.kagi.com](https://help.kagi.com/kagi/plans/plan-types.html)
- Brave's AI answers and "Ask Brave" (follow-ups plus a Deep Research mode) are free. Ask Brave chats expire after 24 hours of inactivity by default — [TinyFish](https://www.tinyfish.ai/blog/best-ai-search-engine)
- Glean is priced at "$50+/user/month" with no true self-hosting, according to its open-source competitor Onyx (a biased source) — [Onyx blog](https://onyx.app/insights/glean-alternatives). Glean lists more than 275 connectors — [BenchLM](https://benchlm.ai/blog/posts/glean-ai-alternatives)
- 2026 lists of Glean alternatives name Onyx, PipesHub, Dust, Microsoft 365 Copilot, GoSearch, Workato, Kestra, Guru ($25/seat/mo), Perplexity Enterprise, SearchBlox SearchAI, Amazon Quick, Notion AI Enterprise Search and Gemini Enterprise — [Kestra](https://kestra.io/resources/ai/glean-alternatives); [BenchLM](https://benchlm.ai/blog/posts/glean-ai-alternatives); [Dust](https://dust.tt/blog/glean-alternatives-ai-enterprise-search); [PromptQL](https://promptql.io/blog/glean-alternatives-for-company-knowledge)
- GoSearch: Free, Pro $20/user/mo, Enterprise quoted (35-user minimum), 100+ permission-aware connectors — [GoSearch](https://www.gosearch.ai/blog/perplexity-enterprise-pricing-alternatives/)

**Catalogue: hosted AI answer engines (consumer/web)**
Launch dates come from the felladrin timeline ([awesome-ai-web-search](https://github.com/felladrin/awesome-ai-web-search)) unless noted otherwise.

| # | Name | URL | One-line description | OSS? | Pricing (if known) | Relevance |
|---|---|---|---|---|---|---|
| 1 | Perplexity | https://perplexity.ai | The reference cited answer engine; also sells the Sonar/Search API and the Comet browser | No | Free / $20 Pro / $200 Max / Ent $40–325 seat | M (benchmark UX, Arabic answers; also has Internal Knowledge Search) |
| 2 | ChatGPT Search / Deep Research | https://chatgpt.com | OpenAI's web-grounded chat (Oct 2024) and Deep Research (Feb 2025) | No | Free tier; Plus $20; Go $8 ([CloudZero](https://www.cloudzero.com/blog/perplexity-pricing/)) | M (competitor; what SMB users already use) |
| 3 | Google AI Mode / Gemini / Gemini Deep Research | https://gemini.google.com | Google's AI search answers and Gemini chat with grounding | No | Free + Google One AI tiers | M |
| 4 | Microsoft Copilot (Bing) | https://copilot.microsoft.com | Copilot search/chat on the Bing index | No | Free + M365 | M |
| 5 | Brave Search "Answer with AI" / Ask Brave | https://search.brave.com | AI answers above an independent index, with a Deep Research mode | No (browser is OSS; search is not) | Free | M |
| 6 | Brave Leo | https://brave.com/leo | Brave browser's built-in assistant | No | Free / Leo Premium | L |
| 7 | Kagi Assistant / FastGPT / Universal Summarizer | https://kagi.com/assistant | Paid ad-free search with multi-LLM assistant and lenses | No | $5 / $10 / $25 per mo | M (lenses = scoped search idea) |
| 8 | You.com | https://you.com | Was a consumer engine; now enterprise research and search APIs | No | API PAYG + Enterprise ([you.com/pricing](https://you.com/pricing)) | M (as API) |
| 9 | Phind | https://phind.com | Developer answer engine. **DISCONTINUED 16 Jan 2026** | No | — | L (cache) |
| 10 | Exa (Websets / Exa Agent) | https://exa.ai | Neural search engine with its own index; Websets list-builder and research agent | No (SDK/MCP OSS) | See Q3 | M |
| 11 | Andi | https://andisearch.com | Conversational search assistant (2022) | No | Free | L |
| 12 | Genspark | https://genspark.ai | Agentic search engine generating "Sparkpages" (2024) | No | Freemium | L |
| 13 | Felo | https://felo.ai | Multilingual AI search from Japan (2024); good at non-English | No | Freemium | M (multilingual/Arabic UX ref) |
| 14 | iAsk.ai | https://iask.ai | Free AI search engine (2024) | No | Free/Pro | L |
| 15 | Liner | https://liner.com | AI research/search assistant with highlights (2023) | No | Freemium | L |
| 16 | Consensus | https://consensus.app | Answer engine over scientific papers | No | Freemium | L |
| 17 | SciSpace (Typeset) | https://typeset.io | Research-paper AI search/QA | No | Freemium | L |
| 18 | Elicit | https://elicit.com | AI research assistant over papers | No | Freemium | L |
| 19 | Arc Search | https://arc.net/search | "Browse for me" mobile answer pages (Jan 2024) | No | Free | L |
| 20 | DuckDuckGo Search Assist / Duck.ai | https://duck.ai | Private AI answers and anonymous chat with several LLMs | No | Free | L |
| 21 | Mistral Le Chat (web search) | https://chat.mistral.ai | Mistral's chat with web search; also Le Chat Enterprise | No | Freemium | M (EU-hosted option) |
| 22 | Poe Web-Search | https://poe.com/Web-Search | Quora's multi-bot platform with a web-search bot | No | Freemium | L |
| 23 | Metaso (秘塔AI搜索) | https://metaso.cn | Leading Chinese AI search engine | No | Free | L |
| 24 | Kimi | https://kimi.ai | Moonshot AI chat with strong search and long context | No | Free | L |
| 25 | Doubao | https://doubao.com | ByteDance AI assistant with search | No | Free | L |
| 26 | Tiangong (天工) | https://tiangong.cn | Kunlun AI search | No | Free | L |
| 27 | 纳米AI (360) | https://n.cn | 360's AI search | No | Free | L |
| 28 | DeepSeek Chat (web search) | https://chat.deepseek.com | Chat with web search since Dec 2024 | No (models open) | Free | M (cheap model, decent Arabic) |
| 29 | Qwen Chat | https://chat.qwen.ai | Alibaba chat with web search (Jan 2025) | No (models open) | Free | M |
| 30 | Z.ai | https://chat.z.ai | Zhipu GLM chat with search (Jul 2025) | No (models open) | Free | L |
| 31 | Venice | https://venice.ai | Privacy-first uncensored AI with search | No | Freemium | L |
| 32 | Proton Lumo | https://lumo.proton.me | Privacy-focused assistant with web search (Jul 2025) | No | Freemium | L |
| 33 | Yahoo Scout | https://scout.yahoo.com | Yahoo's AI answer engine, launched 27 Jan 2026 | No | Free | L |
| 34 | MiroThinker / MiroMind DR | https://dr.miromind.ai | Hosted demo of the open MiroThinker deep-research agent | Model OSS | Free | M |
| 35 | Grok (DeepSearch) | https://grok.com | xAI chat with X/web DeepSearch | No | Freemium | L |
| 36 | Monica Search | https://monica.so | AI search app (2024) | No | Freemium | L |
| 37 | Msty | https://msty.app | Desktop LLM app with web search (local models) | No (free app) | Free/paid | L |
| 38 | T3 Chat | https://t3.chat | Fast multi-model chat with search | No | $8/mo | L |
| 39 | LMArena Search Arena | https://lmarena.ai | Side-by-side evaluation of search-enabled LLMs | No | Free | M (pick an answer model for Arabic) |
| 40 | Morphic (hosted) | https://morphic.sh | Hosted version of the OSS Morphic engine (see Q4) | Yes (Apache-2.0) | Free | H (via OSS) |
| 41 | Scira (hosted) | https://scira.ai | Hosted version of OSS Scira (see Q4) | Yes (AGPL-3.0) | Freemium | H (via OSS) |
| 42 | Khoj Cloud | https://app.khoj.dev | Hosted "AI second brain" over web plus your docs (see Q4) | Yes (AGPL-3.0) | Free/paid | H |

**Catalogue: hosted "company brain" / enterprise answer engines (answer from internal data with citations)**

| # | Name | URL | One-line description | OSS? | Pricing | Relevance |
|---|---|---|---|---|---|---|
| 43 | Glean | https://glean.com | The category leader in enterprise AI search, assistant and agents; permission-aware, 275+ connectors | No | $50+/user/mo (per Onyx) | M (feature benchmark; too pricey for EG SMB) |
| 44 | Onyx Cloud | https://onyx.app | Hosted version of OSS Onyx (ex-Danswer) | Core OSS | Free community; cloud $20/user/mo annual ([Onyx](https://onyx.app/insights/glean-alternatives)) | H |
| 45 | Dust | https://dust.tt | Agent workspace over company knowledge with semantic search and deep-dive agent | No | ? (quote/seat) | M |
| 46 | GoSearch | https://gosearch.ai | Permission-aware company search across 100+ apps plus agents | No | Free / $20 Pro / Ent | M (price anchor) |
| 47 | Guru | https://getguru.com | Verified-knowledge base with AI enterprise search | No | from $25/seat/mo ([BenchLM](https://benchlm.ai/blog/posts/glean-ai-alternatives)) | M |
| 48 | Perplexity Enterprise | https://perplexity.ai/enterprise | Web plus internal knowledge search with SOC 2 and HIPAA | No | $40 / $325 seat | M |
| 49 | Gemini Enterprise (ex-Google Agentspace) | https://cloud.google.com/gemini-enterprise | Google's enterprise search, chat and agents across Workspace and third-party apps | No | ? | M |
| 50 | Microsoft 365 Copilot | https://microsoft.com/microsoft-365/copilot | Graph-grounded enterprise assistant | No | ? | M |
| 51 | Amazon Quick (Suite) | https://aws.amazon.com/quicksuite | AWS's current path for enterprise agents and knowledge work (successor to Q Business) | No | ? | M |
| 52 | Notion AI Enterprise Search | https://notion.com/product/ai | Answers from Notion plus Slack, Teams, Drive and Jira | No | Notion Business/Ent | M |
| 53 | SearchBlox SearchAI | https://searchblox.com | Managed or self-managed enterprise search with hybrid retrieval, RAG and agents; fixed-cost quote | No | Custom fixed cost | M |
| 54 | Moveworks (ServiceNow) | https://moveworks.com | IT/HR AI agent plus enterprise search | No | Enterprise | L |
| 55 | Coworker | https://coworker.ai | "Context" enterprise agent across tools | No | ? | L |
| 56 | PromptQL | https://promptql.io | Positions itself as a "Company Brain" capturing team learnings | No | ? | M (closest name match) |
| 57 | Kestra | https://kestra.io | OSS orchestration positioned as a Glean alternative for AI pipelines | Yes (Apache-2.0) | OSS / EE | L |
| 58 | Vectara | https://vectara.com | RAG-as-a-service platform with grounded, cited answers | No (OSS demo app) | Freemium/Ent | M |
| 59 | Coveo | https://coveo.com | Enterprise AI search and relevance platform (commerce, support) | No | Enterprise | L |
| 60 | Algolia (AI Search / Ask AI) | https://algolia.com | Hosted search with NeuralSearch and generative answers | No | Usage-based | M (hosted alt to Meilisearch) |
| 61 | kapa.ai | https://kapa.ai | Cited-answer bot over technical docs | No | Enterprise | L |
| 62 | Inkeep | https://inkeep.com | AI answers and support agent over docs | No | ? | L |

### Inferences
- The SaaS price ceiling for a "company brain" sits around $20–$50/user/month (GoSearch $20, Onyx cloud $20, Guru $25, Perplexity Ent $40, Glean $50+). That is high for Egyptian SMBs, which suggests room for a cheaper, Arabic-first, WhatsApp-native product built on OSS (Onyx, Khoj, RAGFlow, Morphic/Scira-style UIs).
- Phind's shutdown, You.com's pivot and the Tavily acquisition (Q3) show that thin consumer answer engines are fragile. Defensibility comes from owning private-data connectors and locale (Arabic and Egyptian dialect, local apps), not from web search.

### Gaps
- I verified none of these hosted products' Arabic or Egyptian-dialect answer quality this session. No benchmark found.
- Prices for Dust, Gemini Enterprise, Amazon Quick and M365 Copilot were not verified this session.
- I found no Arabic-native hosted answer engine (an Egyptian or Gulf "Perplexity") in this session's searches; the search returned only Arabic GEO/SEO agencies and RAG guides. Treat this as unconfirmed absence, not proof that none exists.

---

## Q2. Which search engine infrastructure can power one? Which support hybrid/vector search and Arabic tokenization?

### Takeaway
For a small Arabic company brain, the strongest self-hostable choices are Meilisearch (explicit Arabic segmentation and normalization plus hybrid search), Elasticsearch/OpenSearch (mature built-in Arabic analyzer, BM25 plus kNN hybrid), Postgres + pgvector + ParadeDB (one database for app data, BM25 and vectors), Typesense (has an `ar` locale but weaker Arabic handling according to Meilisearch's own comparison), and Manticore, Vespa or Infinity for heavier hybrid workloads. RAGFlow and Qdrant/Milvus/Weaviate/Chroma/LanceDB cover the vector side.

### Cited Findings
- Meilisearch's language docs list **Arabic: article (ال) segmentation; normalization = decomposition, digit conversion, nonspacing-marks (diacritics) removal** — [Meilisearch docs](https://www.meilisearch.com/docs/resources/help/language). Its tokenizer is the separate OSS library charabia — [meilisearch/charabia](https://github.com/meilisearch/charabia)
- Meilisearch claims "optimized tokenization for … Hebrew, Arabic" and describes Typesense as "Unicode-based (limited CJK)" (a vendor comparison, so biased) — [Meilisearch vs Typesense](https://www.meilisearch.com/docs/resources/comparisons/typesense)
- Typesense lists Arabic locale code `ar` with right-to-left "special character normalization", and supports `pre_segmented_query` for custom tokenization — [Typesense locale guide](https://typesense.org/docs/guide/locale.html)
- Meilisearch normalizes per language based on "the dialect with the biggest number of users" (no competing normalizations) — [Meilisearch blog](https://www.meilisearch.com/blog/improving-meilisearchs-language-support)
- Arabic RAG best practice: unify Arabic letter variants (alef/yaa/taa marbuta), strip diacritics and tatweel, chunk on document structure, rerank — [Plugsky](https://plugsky.com/articles/how-to-build-arabic-ai-with-rag); reranking helps Arabic RAG because of high lexical variance — [arXiv 2506.06339](https://arxiv.org/html/2506.06339v1)
- Onyx's 2026 comparison lists Elasticsearch as "Partial (AGPL core)", Meilisearch MIT and Typesense GPL-3 — [Onyx](https://onyx.app/insights/glean-alternatives). GitHub reports Meilisearch's license as NOASSERTION (MIT core plus enterprise-edition files) — [GitHub](https://github.com/meilisearch/meilisearch)

**Catalogue: search/retrieval engines** (GitHub stats as of 2026-11-15)

| # | Name | URL | Description | License | ★ | Last push | Hybrid/vector? | Arabic? | Pricing | Rel. |
|---|---|---|---|---|---|---|---|---|---|---|
| 63 | Meilisearch | https://github.com/meilisearch/meilisearch | Fast typo-tolerant search API with "AI-powered hybrid search" | NOASSERTION (MIT core + EE) | 59,865 | 2026-11-12 | Yes (hybrid) | **Yes**: ال segmentation, diacritic removal | OSS; Meilisearch Cloud paid | **H** |
| 64 | Elasticsearch | https://github.com/elastic/elasticsearch | Distributed RESTful search engine (Lucene) | NOASSERTION (AGPL/SSPL/ELv2 triple) | 78,703 | 2026-11-15 | Yes (BM25 + kNN, RRF) | Yes: built-in `arabic` analyzer (Lucene; docs not re-fetched) | OSS / Elastic Cloud | **H** |
| 65 | OpenSearch | https://github.com/opensearch-project/OpenSearch | Apache-2.0 fork of Elasticsearch | Apache-2.0 | 14,011 | 2026-11-14 | Yes (neural/hybrid search) | Yes: Lucene `arabic` analyzer (inherited; not re-verified) | OSS / AWS | **H** |
| 66 | Typesense | https://github.com/typesense/typesense | "Open Source alternative to Algolia + Pinecone" | GPL-3.0 | 27,132 | 2026-11-13 | Yes (vector + hybrid) | Partial: `ar` locale, RTL normalization | OSS / Typesense Cloud | **H** |
| 67 | ParadeDB (pg_search) | https://github.com/paradedb/paradedb | "One Postgres for app data, full-text search, vector retrieval" | AGPL-3.0 | 9,511 | 2026-11-15 | Yes (with pgvector) | Tantivy-based tokenizers (Arabic stemmer support unverified) | OSS / cloud | **H** |
| 68 | pgvector | https://github.com/pgvector/pgvector | Vector similarity search for Postgres | PostgreSQL (NOASSERTION) | 23,681 | 2026-11-14 | Vector (+ Postgres FTS for hybrid) | Postgres FTS has no Arabic snowball dictionary by default (unverified) | OSS | **H** |
| 69 | pgvectorscale | https://github.com/timescale/pgvectorscale | DiskANN extension complementing pgvector | PostgreSQL | 3,161 | 2026-10-14 | Vector | n/a | OSS | M |
| 70 | Manticore Search | https://github.com/manticoresoftware/manticoresearch | "Full-text, vector, and hybrid search with real-time indexing and SQL" | GPL-3.0 | 12,081 | 2026-11-14 | Yes | ? (has ICU/morphology; Arabic not verified) | OSS | M |
| 71 | Vespa | https://github.com/vespa-engine/vespa | "The AI search platform": big-data serving, tensors, hybrid ranking | Apache-2.0 | 7,180 | 2026-11-15 | Yes (best-in-class) | Via Lucene linguistics module (unverified) | OSS / Vespa Cloud | M |
| 72 | Apache Solr | https://github.com/apache/solr | Classic Lucene search server | Apache-2.0 | 1,701 | 2026-11-14 | Yes (dense vector) | Yes: Arabic normalization/stem filters (Lucene; not re-fetched) | OSS | M |
| 73 | Apache Lucene | https://github.com/apache/lucene | Core Java search library underlying ES/OS/Solr | Apache-2.0 | 3,612 | 2026-11-13 | Yes (HNSW) | Yes (ArabicAnalyzer; not re-fetched) | OSS | M |
| 74 | Infinity (infiniflow) | https://github.com/infiniflow/infinity | "AI-native database … fast hybrid search of dense, sparse, tensor, full-text" (RAGFlow's engine) | Apache-2.0 | 4,765 | 2026-11-15 | Yes | ? | OSS | M |
| 75 | Tantivy | https://github.com/quickwit-oss/tantivy | Lucene-inspired full-text library in Rust | MIT | 16,441 | 2026-11-11 | BM25 only | Snowball stemmers (Arabic likely; unverified) | OSS | M |
| 76 | Orama | https://github.com/oramasearch/orama | In-browser/edge search engine and RAG pipeline: full-text, vector, hybrid | NOASSERTION (Apache-2.0 per site) | 10,608 | 2026-10-18 | Yes | Has stemmers for many languages incl. Arabic (unverified) | OSS / Orama Cloud | M |
| 77 | OramaCore | https://github.com/oramasearch/oramacore | "Complete runtime for … answer engines, copilots, and search" | AGPL-3.0 | 265 | 2026-11-04 | Yes | ? | OSS | M |
| 78 | SeekStorm | https://github.com/SeekStorm/SeekStorm | Vector and lexical search, in-process library and multi-tenant server (Rust) | Apache-2.0 | 1,938 | 2026-11-12 | Yes | ? | OSS | M |
| 79 | Qdrant | https://github.com/qdrant/qdrant | High-performance vector DB/search engine | Apache-2.0 | 35,562 | 2026-11-14 | Yes (dense + sparse hybrid) | via embeddings | OSS / Cloud | **H** (vector side) |
| 80 | Milvus | https://github.com/milvus-io/milvus | Cloud-native vector DB | Apache-2.0 | 46,664 | 2026-11-14 | Yes | via embeddings | OSS / Zilliz | M |
| 81 | Weaviate | https://github.com/weaviate/weaviate | Vector DB combining vector and structured filters, hybrid BM25 | BSD-3 (NOASSERTION) | 16,948 | 2026-11-14 | Yes | via embeddings | OSS / Cloud | M |
| 82 | Chroma | https://github.com/chroma-core/chroma | "Search infrastructure for AI" (embedding DB) | Apache-2.0 | 29,685 | 2026-11-13 | Yes | via embeddings | OSS / Cloud | M |
| 83 | LanceDB | https://github.com/lancedb/lancedb | Embedded multimodal retrieval library | Apache-2.0 | 11,901 | 2026-11-15 | Yes (FTS + vector) | ? | OSS / Cloud | M |
| 84 | Marqo | https://github.com/marqo-ai/marqo | Was a tensor search engine; now e-commerce search and discovery | Apache-2.0 | 5,024 | 2026-09-03 | Yes | via embeddings | OSS / Cloud | L |
| 85 | txtai | https://github.com/neuml/txtai | All-in-one embeddings DB, semantic search and LLM workflows | Apache-2.0 | 13,400 | 2026-11-13 | Yes | via embeddings | OSS | M |
| 86 | Bleve | https://github.com/blevesearch/bleve | Go text/numeric/geo/vector indexing library | Apache-2.0 | 11,255 | 2026-11-13 | Yes | Has an `ar` analyzer (unverified this session) | OSS | M |
| 87 | Sonic | https://github.com/valeriansaliou/sonic | Lightweight schema-less search backend (IDs only) | MPL-2.0 | 21,381 | 2026-11-10 | No | Supports many languages via stopwords (unverified) | OSS | L |
| 88 | ZincSearch | https://github.com/zincsearch/zincsearch | Lightweight Go Elasticsearch alternative | NOASSERTION | 17,935 | 2026-09-16 | No | ? | OSS | L |
| 89 | Quickwit | https://github.com/quickwit-oss/quickwit | Cloud-native search engine for observability/logs | Apache-2.0 | 11,793 | 2026-11-14 | No | n/a | OSS | L |
| 90 | Pagefind | https://github.com/Pagefind/pagefind | Static, low-bandwidth site search | MIT | 5,558 | 2026-11-14 | No | Multilingual stemming (unverified) | OSS | L |
| 91 | Fess | https://github.com/codelibs/fess | Self-hosted enterprise and site search server on OpenSearch; crawls web/file/DB/cloud; "20+ languages" | Apache-2.0 | 1,151 | 2026-11-15 | Via OpenSearch | Likely, via OpenSearch analyzers (Fess is Japanese-made and multilingual) | OSS | M |
| 92 | Searchkick | https://github.com/ankane/searchkick | Rails gem for intelligent search on ES/OpenSearch | MIT | 6,721 | 2026-11-11 | Via backend | Via backend | OSS | L |
| 93 | Algolia | https://algolia.com | Hosted search with NeuralSearch hybrid | Proprietary | — | — | Yes | Supports Arabic per Algolia docs (unverified) | Usage-based | M |
| 94 | Coveo | https://coveo.com | Enterprise relevance platform | Proprietary | — | — | Yes | ? | Enterprise | L |
| 95 | Azure AI Search | https://azure.microsoft.com/products/ai-services/ai-search | Hosted hybrid search used by Azure RAG accelerators | Proprietary | — | — | Yes | Has Lucene/Microsoft Arabic analyzers (unverified) | Usage-based | M |

### Inferences
- Simplest Arabic-friendly stack for an SMB product: **Postgres (pgvector + ParadeDB) or Meilisearch** for hybrid keyword + vector search, plus a multilingual embedding model and a reranker. Apply Arabic normalization in your own ingestion layer (alef/yaa/taa-marbuta unification, tatweel and diacritic stripping) instead of relying on the engine. Meilisearch is the only engine whose docs I confirmed list Arabic-specific segmentation (ال).
- Elasticsearch/OpenSearch remain the most battle-tested choice for Arabic morphology (Lucene Arabic analyzer plus light stemming), but they cost more in RAM and operations than a solo founder may want.
- Typesense's Arabic support looks shallower (locale tag plus normalization). Test Egyptian-dialect queries before choosing it.

### Gaps
- I did not re-fetch the Elasticsearch, OpenSearch, Solr, Lucene, Bleve, Orama, Manticore or Vespa Arabic docs this session. Their Arabic support is stated from long-standing documented features but should be re-verified.
- No benchmark found comparing Arabic or Egyptian-dialect retrieval quality across these engines.
- ParadeDB/Tantivy Arabic stemming support is unverified.

---

## Q3. Which search APIs exist for agents (for adding live web answers next to company data)?

### Takeaway
As of Nov 2026 the main agent search APIs are Tavily (acquired by Nebius, Feb 2026, $275M), Exa, Brave Search API, Parallel, Linkup, You.com API, Perplexity Search/Sonar API, Firecrawl Search, Jina (s.jina.ai), Serper, SerpApi (sued by Google, Dec 2025), SearchApi.io, DataForSEO, ScrapingDog and newer entrants (Keirolabs, Valyu, Desearch, Tako, Querit, Sofya, Keenable, cloro, Context.dev). The Bing Search API was retired on 11 Aug 2025. Typical prices are $1–$8 per 1,000 queries. Several offer free MCP servers (Parallel since Apr 2026, Exa, Firecrawl keyless).

### Cited Findings
- Nebius agreed to acquire Tavily (announced 10 Feb 2026); Bloomberg and Yahoo reported a $275M deal — [Nebius newsroom](https://nebius.com/newsroom/nebius-announces-agreement-to-acquire-tavily-to-add-agentic-search-to-its-ai-cloud-platform); [Yahoo Finance](https://finance.yahoo.com/news/nebius-agrees-acquire-tavily-275-145527432.html); [Tavily blog](https://www.tavily.com/blog/tavily-is-joining-nebius)
- "The Bing Search API was retired on August 11, 2025" — [Linkup blog](https://www.linkup.so/blog/tavily-alternative-web-search-api-comparison)
- SerpAPI carries legal risk: Google filed a DMCA lawsuit against it in Dec 2025 (per competitor Linkup) — [Linkup blog](https://www.linkup.so/blog/tavily-alternative-web-search-api-comparison)
- Pricing table (Keirolabs, a competitor, Nov 2026): Serper $1/1k (to $0.30), 2,500 free; SerpApi $15 Starter, 250/mo free; Brave $5/1k, own 30B+ page index, LLM Context API; Tavily $5–8/1k, 1,000 free credits; Exa $7/1k (+$1/1k contents); Firecrawl $0.99/1k credits, 1,000 free/mo; Parallel $1/1k (Turbo), 5,000/mo free; Linkup $5–6/1k; You.com $5/1k, 100 queries/day free; Perplexity $5–12/1k + tokens, free tier paused early 2026 — [Keirolabs](https://keirolabs.cloud/blog/web-search-apis-for-agents-2026)
- Firecrawl's (biased) comparison: Exa $7/1k, Tavily $8/1k PAYG, Parallel $1–5/1k, SerpAPI $75+/5k, ScrapingDog $0.29–1.00/1k, Serper $0.30–1.00/1k, Brave $5/1k with $5 free monthly credits — [Firecrawl blog](https://www.firecrawl.dev/blog/best-web-search-apis)
- Parallel runs its own index with Search, Extract, Task, FindAll and Monitor APIs. Its Search MCP at `search.parallel.ai/mcp` works without an API key — [Braintrust](https://www.braintrust.dev/articles/best-web-search-apis-mcps-ai-agents-2026). It has been free with no auth since Apr 2026 — [Keirolabs](https://keirolabs.cloud/blog/web-search-apis-for-agents-2026)
- Exa's hosted MCP `mcp.exa.ai/mcp` works anonymously at lower rate limits; Exa runs separate indexes for people, companies and research — [Braintrust](https://www.braintrust.dev/articles/best-web-search-apis-mcps-ai-agents-2026); [Exa blog](https://exa.ai/blog/best-ai-search-apis)
- Linkup claims a 94% F-score on Verified SimpleQA, SOC 2 Type II, zero data retention on every plan, and a "customer-defined index" (point Linkup at your own sources). Plans run $30/mo (10K credits) to $500/mo — [Linkup](https://www.linkup.so/blog/tavily-alternative-web-search-api-comparison)
- AIMultiple's 2026 agentic search benchmark (/20): Keirolabs 15.2, Brave 14.89, Firecrawl 14.58, Exa 14.39, Tavily 13.67, Perplexity 12.96 — [Keirolabs citing AIMultiple](https://keirolabs.cloud/blog/web-search-apis-for-agents-2026). Each vendor's own blog claims #1 on a different benchmark (Tavily: SealQA/SimpleQA; Brave: 85.3% at $18 per 1k questions), so treat all vendor benchmarks as marketing — [Tavily](https://www.tavily.com/blog/tavily-vs-exa-vs-parallel-vs-firecrawl-vs-perplexity-vs-brave-choosing-the-right-web-search-api); [Brave](https://brave.com/search/api/)
- More agent search APIs (with launch dates) in felladrin's list: Serply, Olostep, SearchApi, DataForSEO, Jina, JigsawStack AI Search, ScrapeUnblocker, Tako, AI Search API, cloro, Desearch, Crawlberg, Context.dev, TalorData, Sofya, Keenable, Zoom Search, Querit, looot, CrawlerData, Perceptlayer — [awesome-ai-web-search](https://github.com/felladrin/awesome-ai-web-search)

**Catalogue: search APIs for agents**

| # | Name | URL | Description | OSS? | Pricing | Rel. |
|---|---|---|---|---|---|---|
| 96 | Tavily (Nebius) | https://tavily.com | Search, Extract, Crawl, Map and Research APIs for agents; acquired by Nebius in 2026 | SDK/MCP OSS ([tavily-mcp](https://github.com/tavily-ai/tavily-mcp) ★2,488; [tavily-python](https://github.com/tavily-ai/tavily-python) ★1,430) | $5–8/1k; 1,000 free credits | H |
| 97 | Exa | https://exa.ai | Neural search with its own index; contents, highlights, Deep Search, Websets | MCP OSS ([exa-mcp-server](https://github.com/exa-labs/exa-mcp-server) ★5,234, MIT) | $7/1k (+contents) | H |
| 98 | Brave Search API | https://brave.com/search/api | Independent 30B+ page index; web/news/image/local plus LLM Context endpoint | MCP OSS ([brave-search-mcp-server](https://github.com/brave/brave-search-mcp-server) ★1,581) | $5/1k; $5 free credit/mo | H |
| 99 | Parallel Web Systems | https://parallel.ai | Objective-based agent search on its own index; Task/FindAll/Monitor APIs | SDK OSS | $1–5/1k; 5,000 free/mo; free MCP | H |
| 100 | Linkup | https://linkup.so | Agent search API with /research, SOC 2, ZDR, custom-source index | SDK OSS | $30–500/mo plans | H |
| 101 | You.com Search/Research API | https://you.com/pricing | Own-index web search, contents, cited research answers | No | ~$5/1k; 100/day free | M |
| 102 | Perplexity Search API / Sonar | https://docs.perplexity.ai | Raw search results or synthesized cited answers (Sonar) | MCP OSS ([perplexityai/modelcontextprotocol](https://github.com/perplexityai/modelcontextprotocol) ★2,629) | $1/M tokens + per-request fee; no free tier | M |
| 103 | Firecrawl Search | https://firecrawl.dev | Search, scrape, crawl and parse to markdown; keyless MCP | Yes, core AGPL-3.0 ([firecrawl](https://github.com/firecrawl/firecrawl) ★201,841; [MCP](https://github.com/firecrawl/firecrawl-mcp-server) ★7,821) | $16/mo annual; 1,000 free credits/mo | H (also ingests customer websites) |
| 104 | Jina Reader / s.jina.ai | https://jina.ai/reader | URL-to-markdown (r.jina.ai) and search (s.jina.ai); also embeddings and rerankers | Reader OSS ([jina-ai/reader](https://github.com/jina-ai/reader) ★12,257, Apache-2.0; [MCP](https://github.com/jina-ai/MCP) ★913) | Free tier + tokens | H (multilingual embeddings/rerankers matter for Arabic) |
| 105 | Serper | https://serper.dev | Cheap Google SERP JSON API | No | $1/1k → $0.30; 2,500 free | M |
| 106 | SerpApi | https://serpapi.com | Structured SERP for 40+ engines (oldest, 2017); **sued by Google, Dec 2025** | No | $15+ Starter; 250 free/mo | M (legal risk) |
| 107 | SearchApi.io | https://searchapi.io | SERP API (2024) | No | ? | L |
| 108 | DataForSEO | https://dataforseo.com | SEO/SERP data APIs | No | Usage-based | L |
| 109 | ScrapingDog | https://scrapingdog.com | SERP and scraping API | No | $0.29–1.00/1k | L |
| 110 | Keirolabs | https://keirolabs.cloud | Search plus extraction plus embeddings on its own index; tops AIMultiple 2026 | No | $0.03–0.10/1k lite; 750 free | M |
| 111 | Valyu | https://valyu.ai (URL unverified) | Search API including proprietary/financial data; 73% on FinanceBench per Keirolabs | No | ? | L |
| 112 | Olostep | https://olostep.com | Scrape + search API | No | ? | L |
| 113 | JigsawStack AI Search | https://jigsawstack.com/ai-search | AI search API | No | ? | L |
| 114 | Tako | https://tako.com | Knowledge/data-viz search API | No | ? | L |
| 115 | Desearch | https://desearch.ai/web-search-api | Decentralized (Bittensor) search API | No | ? | L |
| 116 | Google Gemini Grounding with Google Search | https://ai.google.dev | Built-in grounding tool in the Gemini API | No | Per-grounded-request | M |
| 117 | OpenAI web search tool | https://platform.openai.com | Built-in web search in the Responses API | No | Per call | M |
| 118 | Anthropic Claude web search tool | https://docs.anthropic.com | Built-in server-side web search tool for Claude | No | Per search | M |
| 119 | Grounding with Bing (Azure AI Agents) | https://learn.microsoft.com/azure/ai-services/agents | Replacement path after the Bing Search API retirement | No | Per call | L |
| 120 | Ollama Web Search API | https://ollama.com | Web search API for local-model users (launch date unverified) | No | Free tier (unverified) | M |
| 121 | SearXNG (self-hosted metasearch as API) | https://github.com/searxng/searxng | Free metasearch aggregating 70+ engines with a JSON API; the default backend of most OSS Perplexity clones | AGPL-3.0, ★39,557, pushed 2026-11-14 | Free (self-host) | **H** (zero-cost web search for EG SMB product) |
| 122 | search2ai | https://github.com/fatwang2/search2ai | Self-hosted search gateway for agents with provider fallback, REST and MCP | MIT, ★1,288, pushed 2026-11-11 | Free | M |
| 123 | AnySearch MCP / skill | https://github.com/anysearch-ai/anysearch-mcp-server | Unified real-time search MCP (web plus vertical) | Apache-2.0, ★2,065 (skill ★6,894) | ? | M |
| 124 | Crawl4AI (Cloud) | https://github.com/unclecode/crawl4ai | OSS LLM-friendly crawler, plus a hosted search/extract API | Apache-2.0, ★87,370 | 1,000 free credits/mo (cloud) | H (ingest SMB websites) |

### Inferences
- For an Egyptian SMB company brain, web search is secondary. Self-hosted SearXNG (free) or a cheap API (Brave $5/1k, Parallel/Serper ~$1/1k) is enough. Spend the budget on private-data ingestion instead.
- Vendor consolidation and legal risk are real: Tavily is now owned by Nebius, SerpAPI is being sued, and the Bing API is gone. Put an abstraction layer (e.g. search2ai, or LangChain/LlamaIndex retrievers) in front of any web search provider.

### Gaps
- Arabic and Egypt-locale result quality of each search API was not tested. Brave, Exa and Parallel run their own indexes, and their Arabic coverage is unknown.
- I did not verify the status of the Google Programmable Search (Custom Search JSON) API in 2026.
- Valyu's URL and pricing, Ollama Web Search pricing, and Jina's ownership status were not verified this session.

---

## Q4. Which open-source "Perplexity clones" and company-data answer engines exist on GitHub, and how active are they?

### Takeaway
The most-starred OSS answer engine is **Perplexica, now renamed Vane** (`ItzCrazyKns/Vane`, ★38.2k, MIT, last push 2026-09-01). It is followed by **Khoj** (★38.1k, AGPL, which already answers from personal docs plus the web), **Scira** (ex-MiniPerplx, ★11.9k, AGPL), **Morphic** (★9.3k, Apache-2.0, still very active), MindSearch, FreeAskInternet, LLM-Answer-Engine, Farfalle (stale since 2024) and OpenPerplex (stale). For a company brain specifically, the "answer from internal data" OSS platforms matter more: **Onyx** (★33.4k), **RAGFlow** (★94.2k), **AnythingLLM** (★68.3k), **Open WebUI** (★158.7k), **Dify** (★161.2k), **SurfSense** (★16.9k), **PipesHub** (★4.1k), **Xyne** (★0.7k), **SWIRL** (★3.0k) and Kotaemon (★25.9k). Several former favourites are now archived: LLocalSearch, Lepton search_with_lepton, Weaviate Verba, h2oGPT, Cognita, LangChain open_deep_research, Airweave, Whoogle, and even Flowise.

### Cited Findings
- Perplexica was renamed Vane: the felladrin list still links `ItzCrazyKns/Perplexica`, while the GitHub API returns `ItzCrazyKns/Vane`, "Vane is an AI-powered answering engine", ★38,212 — [GitHub Vane](https://github.com/ItzCrazyKns/Vane); [felladrin list](https://github.com/felladrin/awesome-ai-web-search)
- Scira's repo describes itself as "(Formerly MiniPerplx) … minimalistic AI-powered search engine" — [GitHub](https://github.com/zaidmukaddam/scira)
- Onyx calls itself "the strongest open-source Glean alternative", with 40+ connectors, AI chat, agents and deep research, "MIT-licensed". GitHub reports NOASSERTION, i.e. mixed MIT and EE licensing — [Onyx](https://onyx.app/insights/glean-alternatives); [GitHub](https://github.com/onyx-dot-app/onyx)
- PipesHub is described as "the emerging open-source contender" with a knowledge-graph architecture, but "less mature" — [Onyx](https://onyx.app/insights/glean-alternatives). Its repo: "Permission-aware search and cited answers across 3…[0+ apps]" — [GitHub](https://github.com/pipeshub-ai/pipeshub-ai)
- Xyne: "AI-first Search & Answer Engine for work. Open-source alternative to Glean." — [GitHub](https://github.com/xynehq/xyne)
- SWIRL: "AI Search & RAG Without Moving Your Data. Get instant answers from your company's knowledge across 100+ apps" — [GitHub](https://github.com/swirlai/swirl-search)
- Onyx published a RAG benchmark on company-internal documents — [EnterpriseRAG-Bench](https://github.com/onyx-dot-app/EnterpriseRAG-Bench) (★633, MIT)
- The felladrin awesome list (★1.5k, updated 6 Nov 2026) catalogues 80+ OSS AI web-search projects in a timeline, and new clones keep appearing in 2026 (Lorph, Verity, Chutes Search, lilbee, Caesar, ENZO) — [awesome-ai-web-search](https://github.com/felladrin/awesome-ai-web-search)

**Catalogue A: OSS answer engines / Perplexity clones (web-first)** (★, license, last push and archived flag via GitHub API, 2026-11-15)

| # | Name | URL | Description | License | ★ | Last push | Status | Rel. |
|---|---|---|---|---|---|---|---|---|
| 125 | Vane (ex-Perplexica) | https://github.com/ItzCrazyKns/Vane | AI answering engine on SearXNG, local or cloud LLMs, focus modes, file uploads | MIT | 38,212 | 2026-09-01 | Active | **H** (best MIT base to clone) |
| 126 | Khoj | https://github.com/khoj-ai/khoj | "AI second brain"; answers from web or your docs; agents and automations; self-hostable | AGPL-3.0 | 38,126 | 2026-08-02 | Active | **H** |
| 127 | Scira (ex-MiniPerplx) | https://github.com/zaidmukaddam/scira | Minimalist AI search on the Vercel AI SDK with many search tools | AGPL-3.0 | 11,945 | 2026-08-12 | Active | **H** (UI template; AGPL caveat) |
| 128 | Morphic | https://github.com/miurla/morphic | AI search with generative UI (Next.js, AI SDK; Tavily/Exa/SearXNG) | Apache-2.0 | 9,332 | 2026-11-13 | Very active | **H** (permissive license) |
| 129 | MindSearch (InternLM) | https://github.com/InternLM/MindSearch | Multi-agent web search framework (like Perplexity Pro) | Apache-2.0 | 6,944 | 2025-07-04 | Slowing | M |
| 130 | FreeAskInternet | https://github.com/nashsu/FreeAskInternet | Free, private, local search aggregator and answer generator | Apache-2.0 | 8,740 | 2024-04-18 | Stale | M |
| 131 | LLM Answer Engine (Developers Digest) | https://github.com/developersdigest/llm-answer-engine | Perplexity-inspired answer engine (Next.js, Groq, Brave/Serper) | MIT | 5,041 | 2026-04-29 | Maintained | M |
| 132 | Farfalle | https://github.com/rashadphz/farfalle | Self-hostable AI search with local or cloud LLMs | Apache-2.0 | 3,541 | 2024-09-27 | Stale | M |
| 133 | Fireplexity (Firecrawl) | https://github.com/firecrawl/fireplexity | OSS Perplexity-like engine with real-time citations on Firecrawl | No license detected | 1,979 | 2025-08-22 | Demo | M |
| 134 | TurboSeek (Nutlope/Together) | https://github.com/Nutlope/turboseek | AI search engine inspired by Perplexity | No license detected | 1,662 | 2026-10-23 | Active | M |
| 135 | MemFree | https://github.com/memfreeme/memfree | Hybrid AI search engine (web plus your bookmarks/docs) and page generator | MIT | 1,513 | 2026-07-06 | Active | **H** (hybrid private + web) |
| 136 | OpenSearch-AI (Supermemory) | https://github.com/supermemoryai/opensearch-ai | SearchGPT/Perplexity clone personalised with your memory | No license detected | 1,332 | 2026-10-02 | Active | M |
| 137 | Gemini-Search | https://github.com/ammaarreshi/Gemini-Search | Perplexity-style clone with Gemini 2.0 Flash plus Google grounding | MIT | 2,070 | 2025-01-04 | Stale | M |
| 138 | Clarity AI | https://github.com/mckaywrigley/clarity-ai | Early Perplexity clone (2023) | MIT | 1,423 | 2024-03-28 | Stale | L |
| 139 | Omniplex | https://github.com/Omniplex-ai/omniplex | Open-source Perplexity (Next.js, Firebase) | AGPL-3.0 | 1,068 | 2024-07-07 | Stale | L |
| 140 | OpenPerplex (backend) | https://github.com/YassKhazzan/openperplex_backend_os | OSS AI search engine backend (Groq, Cohere rerank, Serper) | No license | 889 | 2024-08-04 | Stale | L |
| 141 | Lepton search_with_lepton | https://github.com/leptonai/search_with_lepton | Conversational search demo (~500 lines) | Apache-2.0 | 8,043 | 2025-12-02 | **Archived** (Lepton acquired by NVIDIA, unverified) | M (minimal reference) |
| 142 | LLocalSearch | https://github.com/nilsherzig/LLocalSearch | Local search aggregator using LLM agents | Apache-2.0 | 5,933 | 2026-03-24 | **Archived** | L |
| 143 | MiniSearch | https://github.com/felladrin/MiniSearch | Minimalist web search with an in-browser AI assistant | Apache-2.0 | 608 | 2026-11-15 | Active | M (runs in browser) |
| 144 | Cognito AI Search | https://github.com/kekePower/cognito-ai-search | Search page powered by LLMs and SearXNG | MIT | 284 | 2026-05-11 | Maintained | M |
| 145 | Spy Search | https://github.com/JasonHonKL/spy-search | LLM search engine "faster than Perplexity" | MIT | 388 | 2026-05-23 | Maintained | L |
| 146 | Sensei | https://github.com/jjleng/sensei | "Yet another open source Perplexity" | Apache-2.0 | 464 | 2024-10-20 | Stale | L |
| 147 | nanoPerplexityAI | https://github.com/Yusuke710/nanoPerplexityAI | Simplest OSS implementation of perplexity.ai | MIT | 340 | 2025-01-24 | Stale | M (teaching reference) |
| 148 | Perplexideez | https://github.com/brunostjohn/perplexideez | Search the web and your self-hosted apps with local AI agents | AGPL-3.0 | 573 | 2024-11-17 | Stale | L |
| 149 | Search-with-AI (isou) | https://github.com/yokingma/search_with_ai | LLM-based conversational search with multiple engines | ? (not returned by API) | ? | ? | ? | L |
| 150 | SearchWala | https://github.com/SandeepAi369/SearchWala | Private meta-search and answer engine in Rust (17 engines, consensus ranking) | Apache-2.0 | 46 | 2026-11-10 | New | L |

**Catalogue B: OSS deep-research agents (multi-step cited reports; useful for "research my company docs" features)**

| # | Name | URL | License | ★ | Last push | Notes | Rel. |
|---|---|---|---|---|---|---|---|
| 151 | GPT Researcher | https://github.com/assafelovic/gpt-researcher | Apache-2.0 | 30,694 | 2026-11-12 | Autonomous research on web **or local docs** with citations | **H** |
| 152 | STORM (Stanford) | https://github.com/stanford-oval/storm | MIT | 31,881 | 2025-09-30 | Wikipedia-style cited reports | M |
| 153 | DeerFlow (ByteDance) | https://github.com/bytedance/deer-flow | MIT | 85,352 | 2026-11-14 | Long-horizon research/coding SuperAgent harness | M |
| 154 | Tongyi DeepResearch (Alibaba) | https://github.com/Alibaba-NLP/DeepResearch | Apache-2.0 | 20,140 | 2026-02-27 | Open deep-research agent and model | M |
| 155 | dzhng/deep-research | https://github.com/dzhng/deep-research | MIT | 19,902 | 2026-04-11 | Minimal iterative deep-research agent | M |
| 156 | Local Deep Research | https://github.com/LearningCircuit/local-deep-research | MIT | 9,582 | 2026-11-15 | Claims ~95% SimpleQA with local Qwen; local + cloud LLMs; searches local docs | **H** (local/private) |
| 157 | Local Deep Researcher (LangChain) | https://github.com/langchain-ai/local-deep-researcher | MIT | 9,410 | 2026-10-15 | Fully local web research with Ollama | M |
| 158 | MiroThinker | https://github.com/MiroMindAI/MiroThinker | Apache-2.0 | 8,454 | 2026-07-06 | Deep-research agent and models | M |
| 159 | Open Deep Research (nickscamara) | https://github.com/nickscamara/open-deep-research | NOASSERTION | 6,299 | 2025-05-07 | Firecrawl-based deep-research clone | L |
| 160 | Jina node-DeepResearch | https://github.com/jina-ai/node-DeepResearch | Apache-2.0 | 5,243 | 2026-11-13 | Search, read and reason until answered | M |
| 161 | u14app deep-research | https://github.com/u14app/deep-research | MIT | 4,686 | 2026-06-18 | Any-LLM deep research with SSE API and MCP | M |
| 162 | OpenDeepSearch (Sentient) | https://github.com/sentient-agi/OpenDeepSearch | Apache-2.0 | 3,833 | 2025-04-04 | Search-powered LLM agent | L |
| 163 | Gemini Fullstack LangGraph Quickstart | https://github.com/google-gemini/gemini-fullstack-langgraph-quickstart | Apache-2.0 | 18,367 | 2026-06-14 | Google's reference research agent (React + LangGraph) | M |
| 164 | Automated AI Web Researcher (Ollama) | https://github.com/TheBlewish/Automated-AI-Web-Researcher-Ollama | MIT | 3,019 | 2026-09-02 | Local automated researcher | L |
| 165 | LangChain open_deep_research | https://github.com/langchain-ai/open_deep_research | MIT | 12,677 | 2026-08-10 | **Archived** | L |

**Catalogue C: OSS "company brain" / enterprise answer platforms (answer from internal data with citations), the most directly relevant group**

| # | Name | URL | Description | License | ★ | Last push | Rel. |
|---|---|---|---|---|---|---|---|
| 166 | Onyx (ex-Danswer) | https://github.com/onyx-dot-app/onyx | Open-source AI platform: enterprise search over 40+ connectors, chat, agents, deep research, permission-aware | NOASSERTION (MIT + EE) | 33,399 | 2026-11-14 | **H** (closest OSS Glean) |
| 167 | RAGFlow | https://github.com/infiniflow/ragflow | Deep-document-understanding RAG engine with cited chunks; now "context infrastructure" | Apache-2.0 | 94,161 | 2026-11-13 | **H** (strong PDF/table parsing) |
| 168 | AnythingLLM | https://github.com/Mintplex-Labs/anything-llm | Local-first all-in-one doc chat, agents and workspaces | MIT | 68,287 | 2026-11-13 | **H** (easiest SMB deploy) |
| 169 | Open WebUI | https://github.com/open-webui/open-webui | Self-hosted chat UI with RAG, web search (SearXNG etc.) and knowledge bases | NOASSERTION (custom BSD with branding clause) | 158,674 | 2026-11-14 | **H** (UI; check branding license) |
| 170 | Dify | https://github.com/langgenius/dify | Agentic workflow and RAG pipeline platform with knowledge bases | NOASSERTION (modified Apache-2.0) | 161,171 | 2026-11-15 | **H** (multi-tenant restrictions in license) |
| 171 | SurfSense | https://github.com/MODSetter/SurfSense | Air-gapped, privacy-focused OSS NotebookLM/Perplexity alternative connected to Slack, Notion, etc. | Apache-2.0 | 16,875 | 2026-11-14 | **H** |
| 172 | PipesHub | https://github.com/pipeshub-ai/pipeshub-ai | Context layer and enterprise AI search with permission-aware cited answers across 30+ apps | Apache-2.0 | 4,117 | 2026-11-15 | **H** |
| 173 | Xyne | https://github.com/xynehq/xyne | AI-first search and answer engine for work (Glean alternative), built on Vespa | Apache-2.0 | 698 | 2026-11-09 | **H** |
| 174 | SWIRL | https://github.com/swirlai/swirl-search | Federated AI search and RAG over 100+ apps without moving data | Apache-2.0 | 3,049 | 2026-11-14 | M |
| 175 | Kotaemon | https://github.com/Cinnamon/kotaemon | Clean RAG UI for chatting with docs, with citations and hybrid retrieval | Apache-2.0 | 25,909 | 2026-07-14 | **H** (cited answers UI) |
| 176 | PrivateGPT (Zylon) | https://github.com/zylon-ai/private-gpt | API layer for private AI on local models: RAG, tools, MCP, text-to-SQL | Apache-2.0 | 57,635 | 2026-11-13 | M |
| 177 | DocsGPT | https://github.com/arc53/DocsGPT | Private AI platform for agents, assistants and enterprise search | MIT | 18,375 | 2026-11-14 | **H** |
| 178 | LobeHub (ex-Lobe Chat) | https://github.com/lobehub/lobehub | Super-agents for teams; knowledge base, chat in team channels | NOASSERTION | 85,532 | 2026-11-15 | M |
| 179 | Cherry Studio | https://github.com/CherryHQ/cherry-studio | Desktop AI workspace with knowledge bases and web search | AGPL-3.0 | 53,523 | 2026-11-15 | M |
| 180 | HuggingFace chat-ui | https://github.com/huggingface/chat-ui | Codebase powering HuggingChat (web search, tools) | Apache-2.0 | 11,035 | 2026-11-14 | M |
| 181 | R2R (SciPhi) | https://github.com/SciPhi-AI/R2R | Production agentic RAG with REST API | MIT | 8,095 | 2025-11-07 | M (slowing) |
| 182 | Fess | https://github.com/codelibs/fess | (see #91) Enterprise search server; crawls file shares and DBs | Apache-2.0 | 1,151 | 2026-11-15 | M |
| 183 | Coco AI (server + app) | https://github.com/infinilabs/coco-app | Personal/enterprise AI search and assistant (Coco server ★150) | MIT | 728 | 2026-08-06 | M |
| 184 | Sycamore (Aryn) | https://github.com/aryn-ai/sycamore | LLM-powered search and analytics over unstructured data | Apache-2.0 | 606 | 2026-08-01 | L |
| 185 | Kwipu | https://github.com/benmaster82/Kwipu | Local Graph-RAG Q&A across Markdown notes | MIT | 612 | 2026-11-02 | L |
| 186 | OpenDocuments | https://github.com/joungminsung/OpenDocuments | Self-hosted RAG doc search across GitHub, Notion, Drive, local files | MIT | 127 | 2026-07-26 | M |
| 187 | Azure chat-with-your-data accelerator | https://github.com/Azure-Samples/chat-with-your-data-solution-accelerator | RAG pattern on Azure AI Search | MIT | 1,188 | 2026-11-03 | L |

**Catalogue D: RAG/answer frameworks, document parsers and supporting components (to build your own)**

| # | Name | URL | License | ★ | Last push | Role | Rel. |
|---|---|---|---|---|---|---|---|
| 188 | LlamaIndex | https://github.com/run-llama/llama_index | MIT | 52,904 | 2026-11-14 | Doc processing / RAG framework with citation query engines | **H** |
| 189 | LangChain | https://github.com/langchain-ai/langchain | MIT | 149,521 | 2026-11-14 | Agent/RAG framework | M |
| 190 | Haystack | https://github.com/deepset-ai/haystack | Apache-2.0 | 27,008 | 2026-11-14 | Production RAG pipelines (hybrid retrievers, rerankers) | **H** |
| 191 | LightRAG | https://github.com/HKUDS/LightRAG | MIT | 40,699 | 2026-11-14 | Fast graph-based RAG | M |
| 192 | RAG-Anything | https://github.com/HKUDS/RAG-Anything | MIT | 24,541 | 2026-11-12 | Multimodal RAG on LightRAG | M |
| 193 | Microsoft GraphRAG | https://github.com/microsoft/graphrag | MIT | 36,648 | 2026-11-09 | Graph RAG for global questions | M |
| 194 | Docling | https://github.com/docling-project/docling | MIT | 70,594 | 2026-11-14 | PDF/Office parsing to markdown/JSON | **H** |
| 195 | MinerU | https://github.com/opendatalab/MinerU | NOASSERTION | 83,683 | 2026-11-13 | PDF/Office to LLM-ready markdown | M (check Arabic OCR) |
| 196 | MarkItDown | https://github.com/microsoft/markitdown | MIT | 195,406 | 2026-11-07 | Office files to Markdown | **H** |
| 197 | Unstructured | https://github.com/Unstructured-IO/unstructured | Apache-2.0 | 15,742 | 2026-11-14 | Document ETL | M |
| 198 | Mem0 | https://github.com/mem0ai/mem0 | Apache-2.0 | 68,979 | 2026-11-06 | Memory layer for agents | M |
| 199 | Graphiti (Zep) | https://github.com/getzep/graphiti | Apache-2.0 | 32,813 | 2026-11-15 | Real-time temporal knowledge graphs | M |
| 200 | Cognee | https://github.com/topoteretes/cognee | Apache-2.0 | 33,321 | 2026-11-14 | AI memory / knowledge-graph platform | M |
| 201 | Supermemory | https://github.com/supermemoryai/supermemory | MIT | 31,623 | 2026-11-13 | Memory/context engine and API | M |
| 202 | Vercel AI Chatbot | https://github.com/vercel/chatbot | NOASSERTION | 21,052 | 2026-11-03 | Next.js chat template (base of many clones) | M |
| 203 | assistant-ui | https://github.com/assistant-ui/assistant-ui | MIT | 13,208 | 2026-11-15 | React chat UI with citations/sources components | M |
| 204 | Ollama | https://github.com/ollama/ollama | MIT | 186,989 | 2026-11-14 | Local model runtime (Qwen/GLM etc. for Arabic) | M |
| 205 | Langfuse | https://github.com/langfuse/langfuse | NOASSERTION (MIT core) | 37,438 | 2026-11-14 | Observability and evals for answer quality | M |

### Inferences
- **Best clone candidates by license.** Permissive: Vane (MIT), Morphic (Apache-2.0), LLM-Answer-Engine (MIT), MemFree (MIT), and on the company-data side AnythingLLM (MIT), RAGFlow, SurfSense, PipesHub, Xyne and Kotaemon (all Apache-2.0). Copyleft or restricted: Khoj and Scira (AGPL-3.0; offering them as SaaS requires publishing your modifications), Dify (modified Apache with multi-tenant/branding limits), Open WebUI (branding clause), Onyx (EE features are proprietary).
- **Activity signal (pushed within ~2 weeks of 2026-11-15):** Morphic, Onyx, RAGFlow, AnythingLLM, SurfSense, PipesHub, Xyne, SWIRL, DocsGPT, GPT Researcher and Local Deep Research are clearly alive. Vane (Sept), Khoj (Aug) and Scira (Aug) are alive but slower. Farfalle, OpenPerplex, Clarity, Omniplex, FreeAskInternet and Sensei are effectively abandoned.
- The fastest path to an MVP for an Egyptian SMB company brain looks like: AnythingLLM, Onyx or RAGFlow as the backend; Docling/MarkItDown for Arabic PDFs and Office files; Meilisearch or pgvector+ParadeDB for hybrid retrieval; a Morphic/Vane-style cited-answer UI; SearXNG for optional web search. This is my synthesis, not a sourced recommendation.

### Gaps
- GitHub search did not return LibreChat (`danny-avila/LibreChat`), Quivr (`QuivrHQ/quivr`), Casibase, Kortix Suna, Microsoft kernel-memory, search_with_ai or LeetTools, so their stars are unverified (they may be renamed or the index missed them).
- None of these OSS projects was tested for Arabic right-to-left UI, Arabic PDF/OCR parsing, or Egyptian-dialect retrieval. The Arabic quality of Docling/MinerU OCR is a key open question.
- The "awesome-perplexity-clones" list named in the brief was not found under that name. The closest equivalents are felladrin/awesome-ai-web-search (★1,518) and ianwieds/awesome-ai-search (★1, created Nov 2026).
