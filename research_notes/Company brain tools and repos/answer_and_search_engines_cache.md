# AI Answer & Search Engines: CACHE of weaker, stale, duplicate and marginal entries (as of 15 Nov 2026)

Companion to `answer_and_search_engines.md`. Nothing here is a strong candidate for an Egyptian/Arabic SMB company brain, but everything is kept so nothing is lost. Repo stats (★, SPDX license, last push, archived flag) come from the GitHub REST search API on 2026-11-15; each row links to its repo. Closed-source launch dates come from [felladrin/awesome-ai-web-search](https://github.com/felladrin/awesome-ai-web-search) unless noted.

## Q1. Hosted answer engines: marginal, regional, niche or discontinued

### Takeaway
A long tail of consumer AI search apps, mostly regional (China, Vietnam), niche (academic) or thin wrappers. One is confirmed dead (Phind) and Neeva died earlier. None is a company-brain base.

### Cited Findings
| # | Name | URL | Description | OSS? | Status / pricing | Why cached |
|---|---|---|---|---|---|---|
| C1 | Phind | https://phind.com | Developer answer engine | No | **Shut down 16 Jan 2026** — [intelligenttools.co](https://intelligenttools.co/blog/improved-phind-shutdown-post) | Discontinued |
| C2 | Neeva | https://neeva.com | Ad-free AI search | No | Shut down in 2023 (consumer); acquired by Snowflake (from training knowledge, not re-verified) | Discontinued |
| C3 | Pi (Inflection) | https://pi.ai | Personal chatbot with web answers (2023) | No | Free | Not search-focused |
| C4 | Xdash AI | https://xdash.ai | Free real-time AI search (2024) | No | ? | Tiny |
| C5 | ThinkAny | https://thinkany.ai | AI search engine (2024) | No | ? | Tiny |
| C6 | AyeSoul | https://ayesoul.com | AI search (2024) | No | ? | Tiny |
| C7 | uncovr | https://uncovr.app | AI answer engine (2024) | No | ? | Tiny |
| C8 | AI Hay | https://ai-hay.vn | Vietnamese AI Q&A search (2024) | No | ? | Regional |
| C9 | Deepfind | https://deepfind.co | Privacy-first AI search (2024) | No | ? | Tiny |
| C10 | Ithy | https://ithy.com | Combines several LLMs' answers (2025) | No | ? | Wrapper |
| C11 | ColomboAI | https://colomboai.com | AI search/social (2025) | No | ? | Tiny |
| C12 | GetAskAI | https://getaskai.com | Launched Jul 2026 on Product Hunt | No | ? | Brand new |
| C13 | Monica Search | https://monica.so | Search inside the Monica assistant | No | Freemium | Wrapper |
| C14 | Komo | https://komo.ai | AI search engine (status unverified) | No | ? | Unverified |
| C15 | Devv.ai | https://devv.ai | Developer AI search (status unverified in 2026) | No | ? | Unverified/possibly stale |
| C16 | HuggingChat | https://huggingface.co/chat | Hosted chat-ui with web search | OSS code | Free | Covered via chat-ui in main file |
| C17 | Metaso / Kimi / Doubao / Tiangong / 纳米AI / Baidu AI Search | various | Chinese AI search engines | No | Free | Chinese-market only (listed in main as L) |
| C18 | Bocha (博查) | https://bochaai.com | Chinese multi-model AI search and search API | No | ? | China-focused |
| C19 | Undermind | https://undermind.ai | Deep scientific literature search | No | ? | Academic niche |
| C20 | Scite | https://scite.ai | Citation-context answers over papers | No | Paid | Academic niche |
| C21 | Ecosia AI / Qwant / Mojeek | ecosia.org / qwant.com / mojeek.com | European/alternative engines adding AI answers (Mojeek has an independent index and API) | No | Free | Marginal |
| C22 | Dashworks | https://dashworks.ai | AI knowledge assistant; acquired by HubSpot (training knowledge, unverified) | No | — | Likely discontinued as standalone |
| C23 | Mendable | https://mendable.ai | Docs answer bot; team became Firecrawl (training knowledge, unverified) | No | — | Likely discontinued |
| C24 | Sana | https://sanalabs.com | Enterprise AI knowledge assistant; acquired by Workday (training knowledge, unverified) | No | Enterprise | Enterprise-priced |
| C25 | Hebbia | https://hebbia.ai | AI search for finance/legal documents | No | Enterprise | Enterprise-priced |
| C26 | Atlassian Rovo | https://atlassian.com/software/rovo | AI search and agents across Atlassian plus connectors | No | Bundled | Atlassian-centric |
| C27 | Slack AI search | https://slack.com/ai | Answers from Slack history | No | Add-on | Slack-centric (most EG SMBs use WhatsApp) |
| C28 | Writer Knowledge Graph | https://writer.com | Graph RAG inside Writer's enterprise platform | No | Enterprise | Enterprise-priced |
| C29 | Cohere North | https://cohere.com/north | Enterprise agent workspace with search | No | Enterprise | Enterprise-priced |
| C30 | Lucidworks / Sinequa / Yext | lucidworks.com / sinequa.com / yext.com | Legacy enterprise search vendors adding gen-AI answers | No | Enterprise | Enterprise-priced |
| C31 | Workato (Glean alternative per Kestra) | https://workato.com | Automation with enterprise search agents | No | Enterprise | Marginal — [Kestra](https://kestra.io/resources/ai/glean-alternatives) |
| C32 | Moveworks | https://moveworks.com | IT/HR agent plus search | No | Enterprise | Enterprise-priced — [Moveworks](https://www.moveworks.com/us/en/resources/blog/glean-alternatives-for-enterprise-it-teams) |
| C33 | xPrivo | https://github.com/xprivo/ai-chat | Self-hostable privacy-first assistant with web search; AGPL-3.0, ★138, pushed 2026-05-06 | Yes | Free | Small |
| C34 | Maple (Maple Privacy Labs) | https://maple.ai | Private AI chat with search (2025) | partly | ? | Marginal |

### Inferences
- The consumer-search long tail is crowded and shrinking (Phind shut down, You.com left consumer search). It is not a sensible market for an Egyptian startup to compete in. Company data is the moat.

### Gaps
- The status of Komo, Devv, Dashworks, Mendable and Neeva comes from training knowledge and was not re-verified this session.

---

## Q2. Search infrastructure: marginal or stale engines

### Takeaway
These engines are either stale, observability-only, ID-only, or have no vector or Arabic story. They are kept for completeness.

### Cited Findings
| # | Name | URL | License | ★ | Last push | Why cached |
|---|---|---|---|---|---|---|
| C35 | Toshi | https://github.com/toshi-search/Toshi | MIT | 4,259 | 2026-06-28 | Rust full-text server on Tantivy; small, no vectors |
| C36 | lnx | https://github.com/lnx-search/lnx | MIT | 1,459 | 2025-10-14 | "Search database without the AI bullshit"; no vectors, slowing |
| C37 | ItemsAPI | https://github.com/itemsapi/itemsapi | none | 312 | 2020-12-31 | **Archived** faceted search API |
| C38 | Bertsearch | https://github.com/Hironsan/bertsearch | MIT | 898 | 2023-05-01 | ES + BERT demo; stale |
| C39 | Elastic Search UI | https://github.com/elastic/search-ui | Apache-2.0 | 1,983 | 2026-11-12 | Front-end library only |
| C40 | Typesense InstantSearch adapter | https://github.com/typesense/typesense-instantsearch-adapter | MIT | 532 | 2026-11-13 | UI adapter only |
| C41 | Meilisearch charabia | https://github.com/meilisearch/charabia | MIT | 361 | 2026-08-13 | Tokenizer library (Arabic support is in Meilisearch itself; useful as a standalone Arabic tokenizer) |
| C42 | Endee | https://github.com/endee-io/endee | none | 1,290 | 2026-10-07 | **Archived** vector DB |
| C43 | Jina Serve | https://github.com/jina-ai/serve | Apache-2.0 | 21,852 | 2025-03-24 | Multimodal serving framework; stale |
| C44 | YaCy | https://github.com/yacy/yacy_search_server | NOASSERTION | 4,109 | 2026-11-03 | P2P web search / intranet appliance; dated UX |
| C45 | YaCy Expert | https://github.com/yacy/yacy_expert | LGPL-2.1 | 692 | 2025-01-19 | YaCy + LLM answers; stale |
| C46 | Mwmbl | https://github.com/mwmbl/mwmbl | AGPL-3.0 | 1,893 | 2026-11-13 | Non-profit OSS web index; tiny coverage |
| C47 | Marginalia Search | https://github.com/MarginaliaSearch/MarginaliaSearch | NOASSERTION | 2,239 | 2026-11-14 | Small-web index; not for company data |
| C48 | Stract | https://github.com/StractOrg/stract | AGPL-3.0 | 2,372 | 2025-03-24 | **Archived** OSS web search engine |
| C49 | Whoogle | https://github.com/benbusby/whoogle-search | MIT | 11,552 | 2026-08-14 | **Archived** Google-proxy metasearch |
| C50 | SearXNG-docker | https://github.com/searxng/searxng-docker | AGPL-3.0 | 3,259 | 2026-03-28 | **Archived** (Docker setup moved into the main repo, presumably) |
| C51 | Websurfx | https://github.com/neon-mmd/websurfx | AGPL-3.0 | 1,232 | 2026-11-06 | Rust SearXNG alternative; smaller ecosystem |
| C52 | LibreX | https://github.com/hnhx/librex | AGPL-3.0 | 847 | 2024-08-01 | JS-free metasearch; stale |
| C53 | LibreY | https://github.com/Ahwxorg/LibreY | ? | ? | ? | LibreX fork; not returned by API |
| C54 | 4get | https://git.lolcat.ca/lolcat/4get (unverified) | ? | ? | ? | Proxy metasearch; marginal |
| C55 | iveely.search | https://github.com/Fanping/iveely.search | none | 348 | 2018-03-30 | Dead Java search engine |
| C56 | AskAITools CE | https://github.com/askaitools/askaitools-community-edition | Apache-2.0 | 355 | 2024-07-11 | Search engine for AI products; stale |
| C57 | Ocular | https://github.com/OcularEngineering/ocular | NOASSERTION | 444 | 2024-09-03 | Org AI search/chat; stale |
| C58 | GerevAI | https://github.com/GerevAI/gerev | MIT | 2,805 | 2023-12-29 | AI enterprise search; **abandoned** since 2023 |
| C59 | Volcengine SearchCLI | https://github.com/volcengine/SearchCLI | Apache-2.0 | 1,193 | 2026-11-11 | CLI for ByteDance cloud AI search; China cloud |
| C60 | XiaoyaoSearch | https://github.com/dtsola/xiaoyaosearch | NOASSERTION | 1,024 | 2026-10-02 | Local file AI search (Chinese desktop) |
| C61 | Mango Finder | https://github.com/moyangzhan/mango-finder | NOASSERTION | 254 | 2026-11-11 | Natural-language desktop file search |
| C62 | Omnibox | https://github.com/import-ai/omnibox | Apache-2.0 | 1,555 | 2026-11-13 | "Anything to memory" personal KB |

### Inferences
- If you need a Rust embedded engine, Tantivy, SeekStorm or LanceDB (main file) beat Toshi and lnx.

### Gaps
- I did not verify Arabic support for any engine in this cache.

---

## Q3. Search APIs: marginal SERP and scraping vendors and helpers

### Takeaway
These are commodity SERP resellers, tiny new entrants and unofficial wrappers. Use them only if price or coverage beats the main options.

### Cited Findings
Launch dates and types from [awesome-ai-web-search "Tools for AI Agents"](https://github.com/felladrin/awesome-ai-web-search); Bing retirement from [Linkup](https://www.linkup.so/blog/tavily-alternative-web-search-api-comparison).

| # | Name | URL | Type | Notes / why cached |
|---|---|---|---|---|
| C63 | Bing Web Search API | https://www.microsoft.com/bing/apis | Search API | **Retired 11 Aug 2025** |
| C64 | Serply | https://serply.io | SERP API (2023) | Commodity |
| C65 | ScrapeUnblocker | https://scrapeunblocker.com | Scrape + search (2025) | Commodity |
| C66 | AI Search API | https://aisearchapi.io | Search API (2025) | Tiny |
| C67 | cloro | https://cloro.dev | SERP API (Dec 2025); also tracks AI-engine answers | Tiny |
| C68 | Crawlberg | https://github.com/xberg-io/crawlberg | Scrape + crawl (2026) | Tiny |
| C69 | Context.dev | https://context.dev | Scrape + search (2026) | Tiny |
| C70 | TalorData | https://talordata.com | SERP API (May 2026) | Tiny |
| C71 | Sofya | https://sofya.co | Search API (Jun 2026) | Tiny |
| C72 | Keenable | https://keenable.ai | Search API (Jun 2026) | Tiny |
| C73 | Zoom Search | https://github.com/goofrey/zoom-search | Search + answer (Jul 2026) | Tiny |
| C74 | Querit | https://querit.ai/en | Search API (Aug 2026) | Tiny |
| C75 | looot | https://looot.ai | Search API (Sep 2026) | Tiny |
| C76 | CrawlerData | https://crawlerdata.com | SERP API (Oct 2026) | Tiny |
| C77 | Perceptlayer | https://perceptlayer.com | SERP API (Oct 2026) | Tiny |
| C78 | Bright Data SERP API | https://brightdata.com | SERP and proxy | Enterprise scraping |
| C79 | Oxylabs (Web Scraper API, AI-Search-py, Google AI Mode scraper) | https://github.com/oxylabs/web-scraper-api | Scraping/SERP | Repos ★501 / ★423 (archived) / ★3,632; scraping vendor |
| C80 | Scrapeless | https://github.com/scrapeless-ai/perplexity-scraper | Scraping | Scrapes Perplexity answers; marginal |
| C81 | ValueSERP / Zenserp / Serpstack / SerpWow / Scale SERP | various | SERP APIs | Commodity, not verified in 2026 |
| C82 | Webz.io / NewsAPI | webz.io / newsapi.org | News/web data APIs | Niche |
| C83 | Spider.cloud / ScrapingBee / Apify | spider.cloud / scrapingbee.com / apify.com | Scraping platforms | Ingestion helpers, not search |
| C84 | Browserbase | https://browserbase.com | Headless browser (~$39/mo+) — [Keirolabs](https://keirolabs.cloud/blog/web-search-apis-for-agents-2026) | Not search |
| C85 | BrowserCash Teracrawl | https://github.com/BrowserCash/teracrawl | MIT, ★290, pushed 2025-12-03 | LLM-optimized crawler API; small |
| C86 | LangSearch | https://langsearch.com (unverified) | Free web search + rerank API (training knowledge) | Unverified |
| C87 | Kagi Search API | https://help.kagi.com/kagi/api | Paid search API (beta; training knowledge) | Unverified pricing |
| C88 | Mojeek API | https://mojeek.com/services/search/web-search-api | Independent-index API | Small index |
| C89 | Metaso / Zhipu / Bocha search APIs | various | Chinese AI search APIs | China-focused |
| C90 | xAI Live Search | https://docs.x.ai | Grok API web/X search | Niche |
| C91 | tavily-go (unofficial) | https://github.com/diverged/tavily-go | MIT, ★3, 2024 | Unofficial wrapper |
| C92 | Linkup Python SDK | https://github.com/LinkupPlatform/linkup-python-sdk | MIT, ★46 | SDK only |
| C93 | Parallel SDK (Python) | https://github.com/parallel-web/parallel-sdk-python | MIT, ★31 | SDK only |
| C94 | exa-py | https://github.com/exa-labs/exa-py | MIT, ★239 | SDK only |
| C95 | Exa Company Researcher | https://github.com/exa-labs/company-researcher | MIT, ★1,541, pushed 2026-09-27 | Demo app (company research from web) |
| C96 | Perplexity MCP (community) | https://github.com/jsonallen/perplexity-mcp ; https://github.com/DaInfernalCoder/perplexity-mcp | MIT, ★310 / ★296 | Superseded by the official MCP |
| C97 | Perplexity Web MCP (unofficial) | https://github.com/jacob-bd/perplexity-web-mcp | MIT, ★209 | Uses the web UI; ToS risk |
| C98 | helallao/perplexity-ai (unofficial API) | https://github.com/helallao/perplexity-ai | MIT, ★2,024 | Unofficial wrapper plus account generator; ToS risk |
| C99 | escapeWu/perplexity-ai | https://github.com/escapeWu/perplexity-ai | MIT, ★181 | Pro-account pool proxy; ToS risk |
| C100 | nathanrchn/perplexityai | https://github.com/nathanrchn/perplexityai | none, ★288, 2024 | Unofficial; stale |
| C101 | Perplexity API cookbook | https://github.com/perplexityai/api-cookbook | MIT, ★201 | Examples |
| C102 | Perplexity pplx-garden / pplx-kernels | https://github.com/perplexityai/pplx-garden | MIT, ★956 / ★616 | Inference infrastructure, not search |
| C103 | Agent-Reach | https://github.com/Panniantong/Agent-Reach | MIT, ★111,821, pushed 2026-11-08 | Agent tool for reading/searching Twitter, Reddit, YouTube; social, not company data |
| C104 | AnySearch skill | https://github.com/anysearch-ai/anysearch-skill | Apache-2.0, ★6,894 | Duplicate of the AnySearch MCP in main |
| C105 | Scrapling | https://github.com/D4Vinci/Scrapling | BSD-3, ★102,995 | Scraper (ingestion), not search |
| C106 | ScrapeGraphAI | https://github.com/ScrapeGraphAI/Scrapegraph-ai | MIT, ★32,786 | LLM scraper (ingestion) |
| C107 | browser-use | https://github.com/browser-use/browser-use | MIT, ★121,044 | Browser agent, not search |
| C108 | pi-web-access | https://github.com/nicobailon/pi-web-access | MIT, ★1,804 | Web search extension for the Pi coding agent |

### Inferences
- Unofficial Perplexity wrappers (C97–C100) carry terms-of-service and ban risk and should not underpin a product.

### Gaps
- Pricing and status of C81–C90 were not verified this session.

---

## Q4. OSS Perplexity clones and adjacent repos: stale, tiny, duplicate or off-topic

### Takeaway
Many hobby and demo clones (dozens created in 2024–2026), mostly unmaintained or under 1k stars, plus off-topic repos that matched "perplexity" (system-prompt leaks, GEO/AEO tools, perplexity-metric ML). Several notable projects are now **archived**.

### Cited Findings

**Archived / discontinued notable repos** (GitHub `archived=true` as of 2026-11-15)
| # | Name | URL | License | ★ | Last push | Note |
|---|---|---|---|---|---|---|
| C109 | FlowiseAI/Flowise | https://github.com/FlowiseAI/Flowise | NOASSERTION | 55,570 | 2026-08-13 | **Archived**. Visual agent/RAG builder; check for a successor before use |
| C110 | Weaviate Verba | https://github.com/weaviate/Verba | BSD-3 | 7,692 | 2026-06-08 | **Archived** RAG chatbot (Weaviate's Elysia ★1,922 may be the successor) |
| C111 | h2oGPT | https://github.com/h2oai/h2ogpt | Apache-2.0 | 11,918 | 2025-10-09 | **Archived** private doc chat |
| C112 | TrueFoundry Cognita | https://github.com/truefoundry/cognita | Apache-2.0 | 4,409 | 2026-03-13 | **Archived** RAG framework |
| C113 | Pinecone Canopy | https://github.com/pinecone-io/canopy | Apache-2.0 | 1,033 | 2024-11-13 | **Archived** |
| C114 | Airweave | https://github.com/airweave-ai/airweave | MIT | 6,545 | 2026-06-05 | **Archived** context retrieval layer for agents |
| C115 | btahir open-deep-research | https://github.com/btahir/open-deep-research | MIT | 2,139 | 2025-12-15 | **Archived** |
| C116 | VikParuchuri researcher | https://github.com/VikParuchuri/researcher | MIT | 83 | 2022-12-28 | **Archived** (2022 Google + GPT-3 cited answers, historically first) |
| C117 | Scourhead | https://github.com/zachrattner/scourhead | MIT | 80 | 2025-11-13 | **Archived** |
| C118 | mem0 Chrome extension | https://github.com/mem0ai/mem0-chrome-extension | MIT | 677 | 2026-03-23 | **Archived** |
| C119 | PleasePrompto google-ai-mode-skill | https://github.com/PleasePrompto/google-ai-mode-skill | none | 294 | 2026-09-10 | **Archived** |

**Small / stale Perplexity clones and AI web-search apps**
| # | Name | URL | License | ★ | Last push |
|---|---|---|---|---|---|
| C120 | OpenPerplex front-end | https://github.com/YassKhazzan/openperplex_front | none | 170 | 2024-08-03 |
| C121 | Fyin | https://github.com/shadowfax92/Fyin | AGPL-3.0 | 236 | 2024-10-09 |
| C122 | ask.py (LeetTools) | https://github.com/pengfeng/ask.py | MIT | 283 | 2025-06-17 |
| C123 | OpenPlexity-Pages | https://github.com/alexfazio/OpenPlexity-Pages | MIT | 257 | 2026-02-16 |
| C124 | perplexed | https://github.com/philfung/perplexed | MIT | 148 | 2025-11-19 |
| C125 | LocalPlexity | https://github.com/legraphista/localplexity | AGPL-3.0 | 21 | 2024-08-12 |
| C126 | Heurist Search | https://github.com/heurist-network/gpt-search-web | MIT | 35 | 2026-05-13 |
| C127 | Verity | https://github.com/rupeshs/verity | none | 53 | 2026-03-01 |
| C128 | Ubiquité | https://github.com/edoigtrd/ubiquite | AGPL-3.0 | 50 | 2025-11-14 |
| C129 | Lorph | https://github.com/AL-MARID/Lorph | MIT | 34 | 2026-05-20 |
| C130 | Chutes Search | https://github.com/chutesai/chutes-search | MIT | 3 | 2026-06-27 |
| C131 | lilbee | https://github.com/tobocop2/lilbee | MIT | 71 | 2026-11-15 |
| C132 | Caesar agent | https://github.com/jasonzliang/caesar-agent | Apache-2.0 | 20 | 2026-11-09 |
| C133 | NanoSage | https://github.com/masterFoad/NanoSage | Apache-2.0 | 265 | 2026-10-26 |
| C134 | RabbitHoles | https://github.com/AsyncFuncAI/rabbitholes | MIT | 158 | 2025-04-29 |
| C135 | LLM Websearch (Jay4242) | https://github.com/Jay4242/llm-websearch | GPL-3.0 | 48 | 2026-01-27 |
| C136 | WebRover | https://github.com/hrithikkoduri/WebRover | MIT | 1,025 | 2026-10-19 |
| C137 | Local GenAI Search | https://github.com/nikolamilosevic86/local-genAI-search | GPL-3.0 | 95 | 2024-08-19 |
| C138 | Freelexity | https://github.com/TheGuyDangerous/Freelexity | NOASSERTION | 7 | 2025-03-28 |
| C139 | aisight (iOS/macOS) | https://github.com/tx2z/aisight | MIT | 4 | 2026-11-12 |
| C140 | dalpat/answer-engine | https://github.com/dalpat/answer-engine | none | 1 | 2026-07-14 |
| C141 | lukefwalton/answer-engine | https://github.com/lukefwalton/answer-engine | Apache-2.0 | 3 | 2026-10-08 (site search that "cites its sources or declines plainly"; interesting pattern) |
| C142 | answerstack | https://github.com/mturac/answerstack | MIT | 0 | 2026-10-26 (6-stage answer-engine core: intent, hybrid retrieval…) |
| C143 | Wisp | https://github.com/Yuuzulight/Wisp | none | 0 | 2026-10-19 (answer layer on SearXNG) |
| C144 | gainsay | https://github.com/salpenr/gainsay | MIT | 0 | 2026-07-20 (cited answers from web + your docs, surfaces disagreement) |
| C145 | polymathy | https://github.com/Skelf-Research/polymathy | GPL-3.0 | 0 | 2026-07-02 |
| C146 | neuroseek | https://github.com/Avik-creator/neuroseek | none | 1 | 2025-08-05 |
| C147 | answerloom | https://github.com/YashMahawa/answerloom | MIT | 0 | 2026-06-23 (static cited answer packs from local docs) |
| C148 | Ask-the-Web-103 | https://github.com/AdilShamim8/Ask-the-Web-103 | MIT | 10 | 2026-11-14 |
| C149 | MiniPerplexity | https://github.com/paritoshtripathi935/MiniPerplexity | MIT | 7 | 2026-10-31 |
| C150 | Perplexity-Clone (JonniTech) | https://github.com/JonniTech/Perplexity-Clone | none | 13 | 2026-01-30 |
| C151 | Morphic on Render (example) | https://github.com/render-examples/morphic | NOASSERTION | 0 | 2026-07-15 (deploy template; duplicate of Morphic) |
| C152 | Mistral Perflexity (HF Space) | https://huggingface.co/spaces/ginigen/Mistral-Perflexity | ? | — | 2024 |
| C153 | SearchPhi | https://github.com/AstraBert/SearchPhi | ? | ? | not returned by API |
| C154 | Search with AI (isou) | https://github.com/yokingma/search_with_ai | ? | ? | not returned by API (also listed in main) |
| C155 | LeetTools | https://github.com/leettools-dev/leettools | ? | ? | not returned by API |
| C156 | OperativeAI | https://github.com/vincentdnl/operativeai | ? | ? | 2024 (not queried) |
| C157 | Pravah | https://github.com/jayshah5696/pravah | ? | ? | 2024 (not queried) |
| C158 | Looq / Alisia / Chat WebUI / SootiAI / RAGify Search / LLM Pigeon / ENZO / VSA | see felladrin list | ? | ? | small hobby projects 2024–2026 |
| C159 | MyDeviceAI / Sidekick / LLocal | see felladrin list | ? | ? | on-device apps with web search |
| C160 | KoboldCpp | https://github.com/LostRuins/koboldcpp | AGPL-3.0 | ? | local LLM runner with web search; off-topic |
| C161 | Limopola / Newelle / DeepChat / AIlice | https://github.com/qwersyk/Newelle (★1,501) ; https://github.com/ThinkInAIXYZ/deepchat (★6,392) ; https://github.com/myshell-ai/AIlice (★1,418) | GPL-3.0 / Apache-2.0 / MIT | see ★ | desktop assistants with web search |
| C162 | WebPilot | https://github.com/webpilot-ai/Webpilot | GPL-3.0 | 1,859 | 2026-08-18 (browser AI copilot) |
| C163 | ChatLima | https://github.com/brooksy4503/chatlima | ? | ? | 2025 multi-model chat with search |
| C164 | Spy Search, Sensei | (main file) | — | — | duplicates |
| C165 | Mindsearch-like research libs: Search-R1 | https://github.com/PeterGriffinJin/Search-R1 | Apache-2.0 | 5,579 | 2025-11-13 (RL training for search-calling LLMs; research) |
| C166 | WebThinker | https://github.com/RUC-NLPIR/WebThinker | MIT | 1,473 | 2025-12-08 (NeurIPS 2025 research) |
| C167 | DeepRetrieval | https://github.com/pat-jj/DeepRetrieval | MIT | 719 | 2025-10-12 (research) |
| C168 | AgentLaboratory | https://github.com/SamuelSchmidgall/AgentLaboratory | MIT | 5,930 | 2025-08-20 (research automation) |
| C169 | OpenDeepResearcher (mshumer) | https://github.com/mshumer/OpenDeepResearcher | MIT | 2,790 | 2025-05-02 (stale) |
| C170 | CAMEL OWL | https://github.com/camel-ai/owl | none | 20,194 | 2026-11-09 (general multi-agent) |
| C171 | smolagents | https://github.com/huggingface/smolagents | Apache-2.0 | 30,375 | 2026-11-10 (agent library; includes a search-agent example) |
| C172 | AdalFlow | https://github.com/SylphAI-Inc/AdalFlow | MIT | 4,235 | 2026-11-01 (LLM app library) |
| C173 | KAG (OpenSPG) | https://github.com/OpenSPG/KAG | Apache-2.0 | 9,173 | 2026-01-28 (knowledge-augmented generation) |
| C174 | nano-graphrag | https://github.com/gusye1234/nano-graphrag | MIT | 4,008 | 2026-01-27 |
| C175 | RAGApp | https://github.com/ragapp/ragapp | Apache-2.0 | 4,441 | 2025-01-22 (stale) |
| C176 | Kiln | https://github.com/Kiln-AI/Kiln | NOASSERTION | 5,280 | 2026-11-13 (evals/RAG/fine-tuning tool) |
| C177 | aichat | https://github.com/sigoden/aichat | Apache-2.0 | 10,574 | 2026-02-23 (CLI with RAG) |
| C178 | Chat LangChain | https://github.com/langchain-ai/chat-langchain | MIT | 6,479 | 2026-11-15 (docs Q&A reference app) |
| C179 | Hayhooks | https://github.com/deepset-ai/hayhooks | Apache-2.0 | 155 | 2026-11-13 (serve Haystack pipelines as REST/MCP) |
| C180 | Vectara Answer | https://github.com/vectara/vectara-answer | Apache-2.0 | 272 | 2025-05-08 (UI for Vectara RAG) |
| C181 | Sourcebot | https://github.com/sourcebot-dev/sourcebot | MIT | 4,030 | 2026-11-10 (code search only) |
| C182 | AnythingMCP | https://github.com/HelpCode-ai/anythingmcp | AGPL-3.0 | 791 | 2026-11-14 (MCP gateway, 600+ connectors; possibly useful for connectors) |
| C183 | Arize Phoenix / OpenLIT | https://github.com/Arize-ai/phoenix (★12,295) ; https://github.com/openlit/openlit (★3,077) | NOASSERTION / Apache-2.0 | — | observability (duplicate role of Langfuse) |
| C184 | Bragai bRAG-langchain / NirDiamant RAG_Techniques | https://github.com/bragai/bRAG-langchain (★4,201) ; https://github.com/NirDiamant/RAG_Techniques (★30,340) | NOASSERTION | — | tutorials, not products |
| C185 | Danielskry Awesome-RAG | https://github.com/Danielskry/Awesome-RAG | CC0-1.0 | 1,429 | awesome list |
| C186 | frutik awesome-search | https://github.com/frutik/awesome-search | none | 1,570 | awesome list (e-commerce search) |
| C187 | ianwieds awesome-ai-search | https://github.com/ianwieds/awesome-ai-search | CC0-1.0 | 1 | created Nov 2026; answer engines, search APIs, deep research |
| C188 | Self-Hosting Guide | https://github.com/mikeroyal/Self-Hosting-Guide | none | 23,559 | 2025-06-27 (general) |
| C189 | MemoryKeeper and other niche apps | — | — | — | omitted |

**Off-topic matches for "perplexity" (kept only to record they were excluded)**
- System-prompt leak collections, which include Perplexity's prompts and are useful only as a reference for answer-engine prompt design: [x1xhlol/system-prompts-and-models-of-ai-tools](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools) (★144,674), [asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks) (★71,419), [elder-plinius/CL4R1T4S](https://github.com/elder-plinius/CL4R1T4S) (★52,805), [dontriskit/awesome-ai-system-prompts](https://github.com/dontriskit/awesome-ai-system-prompts) (★6,295).
- AI browsers (Comet/Atlas alternatives): [BrowserOS](https://github.com/browseros-ai/BrowserOS) (★14,346, AGPL), [BrowserOperator](https://github.com/BrowserOperator/browser-operator-core) (★515), [VibeSurf](https://github.com/vibesurf-ai/VibeSurf) (★483), [BrowserPilot](https://github.com/ai-naymul/BrowserPilot) (★180), [comet-mcp](https://github.com/hanzili/comet-mcp) (★181).
- Multi-AI desktop wrappers: [lencx/Noi](https://github.com/lencx/Noi) (★9,074), [py-gpt](https://github.com/szczyglis-dev/py-gpt) (★2,026), [AISuperDomain](https://github.com/win4r/AISuperDomain) (★1,997), [Simplexity](https://github.com/inulute/simplexity-ai-app) (★637), [AI Gate](https://github.com/inulute/ai-gate) (★221), [Heat](https://github.com/nathanborror/Heat) (★325), [Complexity extension](https://github.com/pnd280/complexity) (★1,238), [MCP-SuperAssistant](https://github.com/srbhptl39/MCP-SuperAssistant) (★2,636), [Proxima](https://github.com/Zen4-bit/Proxima) (★1,210).
- GEO/AEO tools (optimizing to be cited *by* answer engines; relevant to marketing, not to building one): [elmo](https://github.com/elmohq/elmo) (★601), [geo-optimizer-skill](https://github.com/Auriti-Labs/geo-optimizer-skill) (★1,327), [limelit open](https://github.com/limelit-co/open) (★444), [oneglanse](https://github.com/oneglanse/oneglanse) (★258), [ansvisor](https://github.com/ansvisor/ansvisor) (★240), [geo-aeo-tracker](https://github.com/danishashko/geo-aeo-tracker) (★328), [GetCito](https://github.com/ai-search-guru/getcito-worlds-first-open-source-aio-aeo-or-geo-tool) (★428), [awesome-seo](https://github.com/i365dev/awesome-seo) (★2,855), [awesome-geo](https://github.com/luka2chat/awesome-geo) (★131), [Canonry](https://github.com/Canonry/canonry) (★209), [aeo.js](https://github.com/rubenmarcus/aeo.js) (★147), [dualmark](https://github.com/dodopayments/dualmark) (★124), [geo-doctor](https://github.com/Fangx-AI/geo-doctor) (★609), [geolook](https://github.com/aigclink/geolook) (★818). Arabic-market GEO agencies also exist, e.g. [zaher.ai](https://zaher.ai/blog) ("Arabic AI answers lean on Arabic sources").
- Perplexity-the-metric ML repos: [Cherry_LLM](https://github.com/tianyi-lab/Cherry_LLM), [lmppl](https://github.com/asahi417/lmppl), [EleutherAI/lm_perplexity](https://github.com/EleutherAI/lm_perplexity).
- Repomix (★29,270), chatgpt-shell, gp.nvim, parrot.nvim, aicommit2 and similar dev tools that merely support the Perplexity API.

### Inferences
- The clone ecosystem is broad but shallow. Most clones are weekend projects around the same pattern (search API, then scrape, then rerank, then a cited LLM answer). Cloning the pattern is trivial; the work for a company brain is in connectors, permissions, Arabic document parsing and evaluation.
- Notable archivals in 2025–2026 (Flowise, Verba, h2oGPT, Cognita, Airweave, LLocalSearch, Lepton search, Whoogle, LangChain open_deep_research) argue for choosing actively maintained bases (Onyx, RAGFlow, AnythingLLM, Morphic).

### Gaps
- Stars and licenses were not retrieved for C153–C163 (not queried, or not returned by the GitHub search API).
- I could not determine why Flowise is archived (GitHub shows archived=true with last push 2026-08-13). Verify before relying on it.
