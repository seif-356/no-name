# Data Ingestion & Cleanup — Cache of Weaker / Niche / Stale / Duplicate Entries (Nov 2026)

Companion to `data_ingestion_cleanup.md`. These entries are lower-confidence, niche, research-grade, stale, superseded, or duplicates of better options, but are kept so nothing is lost. Same column legend: OSS (Y/P/N), Arabic (Y/P/N/?), Step codes, Src (link = seen this session; K = prior knowledge, verify).

## Parsing / OCR (marginal or niche)

### Takeaway
Mostly older OCR engines, research models, academic-only tools and hosted converters with little Arabic evidence.

### Cited Findings

| # | Name | URL | OSS | License | Description | Arabic | Step | Src | Why cached |
|---|---|---|---|---|---|---|---|---|---|
| C1 | TrOCR (Microsoft) | https://huggingface.co/microsoft/trocr-base-printed | Y | MIT | Transformer line-level OCR | P (needs Arabic fine-tune) | OCR | [LinkedIn list](https://www.linkedin.com/posts/aboniasojasingarayar_ocr-opensource-documentai-activity-7391736028996313088-gLfu) | Line-level only, older |
| C2 | Calamari OCR | https://github.com/Calamari-OCR/calamari | Y | Apache-2.0 | Line OCR, used for historical/RTL scripts | P | OCR | K | Research/niche |
| C3 | OCRopus / ocropy | https://github.com/ocropus/ocropy | Y | Apache-2.0 | Legacy OCR toolkit | P | OCR | K | Stale |
| C4 | docTR (Mindee) | https://github.com/mindee/doctr | Y | Apache-2.0 | Detection+recognition OCR library | P (Arabic vocab partial, K) | OCR | K | Weaker on Arabic |
| C5 | MMOCR (OpenMMLab) | https://github.com/open-mmlab/mmocr | Y | Apache-2.0 | OCR research toolbox | ? | OCR | K | Low maintenance |
| C6 | Sakhr OCR | https://www.sakhr.com | N | Commercial | Legacy Arabic OCR vendor | Y | OCR | K | Visibility/maintenance unclear |
| C7 | Amazon Bedrock Data Automation | https://aws.amazon.com/bedrock/bda/ | N | Commercial | Managed multimodal doc extraction | ? | PARSE | K | Arabic unverified |
| C8 | Adobe PDF Extract API | https://developer.adobe.com/document-services/apis/pdf-extract/ | N | Commercial | Structured PDF extraction JSON | ? | PARSE | K | Arabic unverified |
| C9 | Mathpix | https://mathpix.com | N | Commercial | STEM/PDF OCR to Markdown/LaTeX | P | OCR | K | STEM-focused |
| C10 | appjsonify | https://github.com/hitachi-nlp/appjsonify | Y | ? | Academic PDF to JSON | N | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) | Academic niche |
| C11 | DocXChain (Alibaba) | https://github.com/AlibabaResearch/AdvancedLiterateMachinery | Y | Apache-2.0 | Doc structure toolchain | ? | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) | Niche |
| C12 | pdf2md (Node) | https://github.com/opendocsg/pdf2md | Y | MIT | JS PDF to Markdown | N | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) | Text-layer only |
| C13 | markitdown-go | https://github.com/ | Y | ? | Go port of MarkItDown | N | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) | Port |
| C14 | MegaParse | https://github.com/QuivrHQ/MegaParse | Y | Apache-2.0 | LLM-assisted parser by Quivr | ? | PARSE | K | Low activity |
| C15 | LLMWhisperer | https://unstract.com/llmwhisperer/ | N | Commercial | Layout-preserving text for LLMs | ? | PARSE | K | Duplicate of Unstract |
| C16 | pdfminer.six | https://github.com/pdfminer/pdfminer.six | Y | MIT | Classic PDF text extraction (slow: 227s vs 8s PyMuPDF on 7,031 pages) | P | PARSE | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) | Superseded |
| C17 | Camelot / tabula-py | https://github.com/camelot-dev/camelot | Y | MIT | Born-digital PDF table extraction | P | PARSE | K | Lattice tables only |
| C18 | AIN (Arabic multimodal model) | https://huggingface.co/MBZUAI | Y | ? | Arabic LMM; WER 1.23 on Misraj-DocOCR | Y | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) | Poor OCR score |
| C19 | Aya Vision (Cohere) | https://huggingface.co/CohereForAI | P | CC-BY-NC | Multilingual VLM; WER 1.41 on Misraj | Y | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) | Poor OCR, NC license |
| C20 | Gemma 3 (4B/12B) as OCR | https://huggingface.co/google | P | Gemma terms | WER 0.96–1.01 on Misraj | Y | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) | Weak OCR |
| C21 | GPT-4o-mini as OCR | https://platform.openai.com | N | Commercial | WER 1.36 on Misraj | Y | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) | Weak |
| C22 | Qari v0.1 / v0.3 variants | https://huggingface.co/NAMAA-Space | Y | per card | v0.1 high error; v0.3 trades accuracy for layouts/handwriting | Y | OCR | [arXiv](https://arxiv.org/html/2506.02295v1) | Superseded by v0.2/v0.3 choice |
| C23 | Arabic-GLM / misc HF Arabic OCR fine-tunes | https://huggingface.co/models?search=arabic%20ocr | Y | various | Many small community fine-tunes | Y | OCR | K | Unbenchmarked |
| C24 | Docling Serve | https://github.com/docling-project/docling-serve | Y | MIT | REST server wrapper for Docling | P | PARSE | K | Wrapper |
| C25 | pdf-to-markdown-gpt style scripts | https://github.com/ | Y | various | GPT-based page conversion scripts | P | OCR | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) | Ad hoc |
| C26 | Venom-bot (WhatsApp) | https://github.com/orkestral/venom | Y | Apache-2.0 | Browser-automation WhatsApp lib | Y | SERVE | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) | "Plan a migration" — stale |
| C27 | open-wa | https://github.com/open-wa/wa-automate-nodejs | P | Hippocratic/custom (K) | Browser-automation WhatsApp lib | Y | SERVE | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) | Restrictive license |
| C28 | CodeChat whatsapp-api | https://github.com/code-chat-br/whatsapp-api | Y | ? | Ancestor of Evolution API | Y | SERVE | [GitHub](https://github.com/evolution-foundation/evolution-api) | Superseded |
| C29 | d-api.cloud | https://d-api.cloud/en/evolution-api-alternative | N | Commercial | Managed Evolution-style WhatsApp API | Y | SERVE | [d-api](https://d-api.cloud/en/evolution-api-alternative) | Unofficial managed |
| C30 | whatsapp-chat-to-pdf | https://github.com/generalistprogrammer/whatsapp-chat-to-pdf | Y | ? | Export chat to readable PDF | P | INGEST | [GitHub](https://github.com/generalistprogrammer/whatsapp-chat-to-pdf) | Output for humans, not pipeline |
| C31 | AbhijeetKrishnan/whatsapp-parser | https://github.com/AbhijeetKrishnan/whatsapp-parser | Y | ? | Export .txt to CSV | P | INGEST | [GitHub](https://github.com/AbhijeetKrishnan/whatsapp-parser) | Small script |
| C32 | GitHub topic whatsapp-parser (multi-messenger scripts) | https://github.com/topics/whatsapp-parser | Y | various | Scripts for Messenger/Hangouts/WhatsApp/Telegram to DataFrames | P | INGEST | [GitHub](https://github.com/topics/whatsapp-parser) | Assorted |
| C33 | whatsapp-business-python-sdk / pywa | https://github.com/david-lev/pywa | Y | MIT (K) | Python wrapper for official Cloud API | Y | SERVE | K | Helper lib (actually useful; verify maintenance) |

## Ingestion / connectors (marginal)

| # | Name | URL | OSS | License | Description | Arabic | Step | Src | Why cached |
|---|---|---|---|---|---|---|---|---|---|
| C34 | ScrapingBee / ScraperAPI / Zyte | https://www.scrapingbee.com | N | Commercial | Scraping/unblocking APIs | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) | Generic scraping |
| C35 | Scrapfly | https://scrapfly.io | N | Commercial | Anti-bot scraping API | P | INGEST | [Tavily](https://tavily.com/blog/7-best-firecrawl-alternatives-for-ai-agents-in-2026) | Generic |
| C36 | TinyFish | https://www.tinyfish.ai | N | Commercial | Web agent/operate workflows | P | INGEST | [TinyFish](https://www.tinyfish.ai/blog/firecrawl-alternatives) | Vendor-authored claims |
| C37 | String (usestring.ai) | https://usestring.ai | N | Commercial | Hosted scraping | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) | Small vendor |
| C38 | Pipedream | https://pipedream.com | P | Commercial (components OSS) | Workflow + connect API | P | INGEST | K | Overlaps Nango/Composio |
| C39 | Carbon.ai | https://carbon.ai | N | Commercial | RAG data connectors | P | INGEST | K | Reported shutdown (2025, K) — verify |
| C40 | Ragie | https://www.ragie.ai | N | Commercial | Managed RAG ingestion + connectors | P | INGEST | K | Managed overlap |
| C41 | Vectorize.io | https://vectorize.io | N | Commercial | RAG pipelines/connectors | P | INGEST | K | Overlap |
| C42 | Singer taps (singer.io) | https://www.singer.io | Y | Apache/AGPL varies | Legacy tap/target spec | P | INGEST | K | Use via Meltano |
| C43 | Estuary Flow | https://estuary.dev | P | BSL/Commercial | Real-time CDC ELT | P | INGEST | K | Overkill for SMB |
| C44 | Hevo / Stitch | https://hevodata.com | N | Commercial | Managed ELT | P | INGEST | K | Overlap with Fivetran |
| C45 | Merge open-source MCP server | https://github.com/merge-api | Y | ? | Thin MCP over Merge Unified (single account per process) | P | INGEST | [WorkOS](https://workos.com/blog/pipes-vs-nango-composio-arcade-paragon-and-merge) | Thin wrapper |
| C46 | Apideck MCP server | https://github.com/apideck-libraries | Y | MIT (beta) | Self-hostable MCP over Apideck | P | INGEST | [Unified.to](https://unified.to/blog/top_merge_dev_alternatives_in_2026_a_guide_for_saas_and_ai_teams) | Beta |
| C47 | Paragon ActionKit MCP server | https://github.com/useparagon | Y | ? | Self-hosted MCP over ActionKit | P | INGEST | [Unified.to](https://unified.to/blog/top_merge_dev_alternatives_in_2026_a_guide_for_saas_and_ai_teams) | Wrapper |

## Cleanup / ER (research-grade or commercial MDM)

| # | Name | URL | OSS | License | Description | Arabic | Step | Src | Why cached |
|---|---|---|---|---|---|---|---|---|---|
| C48 | dblink | https://github.com/cleanzr/dblink | Y | GPL-3.0 (K) | Bayesian graphical ER on Spark | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Research |
| C49 | exchanger | https://github.com/cleanzr/exchanger | Y | ? | Bayesian ER (R/C++) | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Research |
| C50 | RecordLinkage (R) | https://cran.r-project.org/package=RecordLinkage | Y | GPL | R record linkage | P | DEDUP | [Zingg](https://www.zingg.ai/post/top-10-open-source-entity-resolution-tools-2026) | R-only |
| C51 | DeepMatcher | https://github.com/anhaidgroup/deepmatcher | Y | BSD-3 (K) | Deep learning entity matching | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Unmaintained |
| C52 | RELAIS (ISTAT) | https://www.istat.it/en/methods-and-tools/methods-and-it-tools/process/processing-tools/relais | Y | EUPL (K) | Record linkage toolkit | P | DEDUP | [Zingg](https://www.zingg.ai/post/top-10-open-source-entity-resolution-tools-2026) | Niche |
| C53 | MatchFlow | https://github.com/madmatcher/matchflow | Y | ? | Compose entity matching workflows on Spark | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | New/small |
| C54 | Delex | https://github.com/anhaidgroup/delex | Y | ? | Blocking rules on Spark | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Niche |
| C55 | DeezyMatch | https://github.com/Living-with-machines/DeezyMatch | Y | MIT (K) | Deep embedding fuzzy matching + ANN blocking | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Research |
| C56 | StarSpace | https://github.com/facebookresearch/StarSpace | Y | MIT | Similarity embedding model | P | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Archived |
| C57 | probablepeople | https://github.com/datamade/probablepeople | Y | MIT | Western name parser | N | CLEAN | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Western names only |
| C58 | python-nameparser | https://github.com/derek73/python-nameparser | Y | LGPL | Split names into parts | N | CLEAN | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Western names |
| C59 | Match Data Pro | https://matchdatapro.com | N | Commercial | Browser batch ER, Senzing-based | ? | DEDUP | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) | Small vendor |
| C60 | Quantexa | https://www.quantexa.com | N | Commercial | Decision intelligence / fraud ER | ? | DEDUP | [WinPure](https://winpure.com/best-entity-resolution-software/) | Enterprise-only |
| C61 | Informatica MDM / Reltio / IBM Match 360 / Tamr | https://www.informatica.com | N | Commercial | Enterprise MDM platforms | ? | DEDUP | [WinPure](https://winpure.com/best-entity-resolution-software/) | Enterprise-only |
| C62 | thefuzz (fuzzywuzzy) | https://github.com/seatgeek/thefuzz | Y | MIT | Fuzzy string matching | Y | DEDUP | K | Superseded by RapidFuzz |
| C63 | csvkit | https://github.com/wireservice/csvkit | Y | MIT | CSV CLI utilities | Y | CLEAN | K | Basic |
| C64 | Datasette | https://datasette.io | Y | Apache-2.0 | Explore/publish SQLite data | Y | CLEAN | K | Exploration only |
| C65 | Amazon Deequ / PyDeequ | https://github.com/awslabs/deequ | Y | Apache-2.0 | Spark data-quality checks | P | CLEAN | K | Spark-only |
| C66 | Alteryx Designer Cloud (ex-Trifacta) | https://www.alteryx.com | N | Commercial | Visual data wrangling | P | CLEAN | K | Expensive |
| C67 | Microsoft Data Formulator | https://github.com/microsoft/data-formulator | Y | MIT | AI-assisted data transformation/visualization | P | CLEAN | K | Exploratory |
| C68 | Lilac | https://github.com/lilacai/lilac | Y | Apache-2.0 | Dataset curation/dedup UI | P | CLEAN | K | Acquired by Databricks; stale |
| C69 | text-dedup / datasketch (MinHash) | https://github.com/ekzhu/datasketch | Y | MIT | Near-duplicate text detection via MinHash LSH | Y | DEDUP | K | Useful for doc-level dedup; low profile |
| C70 | Outlines / BAML | https://github.com/dottxt-ai/outlines | Y | Apache-2.0 | Constrained structured generation | Y | META | K | Overlaps Instructor |

## Chunking / KG / metadata (marginal)

| # | Name | URL | OSS | License | Description | Arabic | Step | Src | Why cached |
|---|---|---|---|---|---|---|---|---|---|
| C71 | nano-graphrag | https://github.com/gusye1234/nano-graphrag | Y | MIT | Minimal GraphRAG reimplementation | P | KG | K | Hobby-scale |
| C72 | HippoRAG 2 | https://github.com/OSU-NLP-Group/HippoRAG | Y | MIT | Memory-inspired graph RAG | P | KG | K | Research |
| C73 | KAG / OpenSPG (Ant) | https://github.com/OpenSPG/KAG | Y | Apache-2.0 | Knowledge-augmented generation framework | P | KG | K | Chinese-centric |
| C74 | R2R (SciPhi) | https://github.com/SciPhi-AI/R2R | Y | MIT | RAG server with graph extraction | P | KG, CHUNK | K | Momentum unclear |
| C75 | Kotaemon | https://github.com/Cinnamon/kotaemon | Y | Apache-2.0 | RAG UI with GraphRAG options | P | KG | K | UI app |
| C76 | FalkorDB GraphRAG SDK | https://github.com/FalkorDB/GraphRAG-SDK | Y | MIT (K) | Ontology-driven KG construction | P | KG | K | Smaller ecosystem |
| C77 | Memgraph | https://memgraph.com | P | BSL/Commercial | In-memory graph DB w/ GraphRAG | P | KG | K | DB not extraction |
| C78 | Diffbot NL API / KG | https://www.diffbot.com | N | Commercial | Entity extraction + web KG | P | KG | [Neo4j](https://neo4j.com/labs/genai-ecosystem/llm-graph-builder/) | Cost |
| C79 | Microsoft TnT-LLM (taxonomy) | https://arxiv.org/abs/2403.12173 | - | Paper | LLM-generated label taxonomy then classifier | Y (LLM) | META | K | Method, no product |
| C80 | MCP memory server (reference) | https://github.com/modelcontextprotocol/servers | Y | MIT | Simple KG memory for agents | P | KG | [ivgraph](https://ivgraph.com/journal/knowledge-graph-tools/) | Toy scale |
| C81 | spaCy | https://spacy.io | Y | MIT | NLP pipelines (no official trained Arabic pipeline; tokenizer only, K) | P | META | K | Weak Arabic |
| C82 | LangChain LLMGraphTransformer | https://python.langchain.com | Y | MIT | LLM-based graph document extraction | P | KG | [Neo4j](https://neo4j.com/labs/genai-ecosystem/llm-graph-builder/) | Used inside Neo4j builder |

## Arabic NLP / embeddings (lower-ranked or unverified)

| # | Name | URL | OSS | License | Description | Arabic | Step | Src | Why cached |
|---|---|---|---|---|---|---|---|---|---|
| C83 | Arabic-STS-Matryoshka (V1/V2) | https://huggingface.co/omarelshehy/Arabic-STS-Matryoshka | Y | per card | Arabic STS embedders (62.21 / 58.94) | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Mid-ranked |
| C84 | Arabic-Triplet-Matryoshka-V2 | https://huggingface.co/Omartificial-Intelligence-Space/Arabic-Triplet-Matryoshka-V2 | Y | Apache-2.0 | 61.99 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Mid-ranked |
| C85 | DIMI-embedding v2/v4 | https://huggingface.co/AhmedZaky1/DIMI-embedding-v2 | Y | ? | 61.48 / 60.27 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | License unclear |
| C86 | e5-base-mlqa-finetuned-arabic-for-rag | https://huggingface.co/OmarAlsaabi/e5-base-mlqa-finetuned-arabic-for-rag | Y | ? | 61.25 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Mid |
| C87 | arabic-gte-multilingual-base (RamzyBakir) | https://huggingface.co/RamzyBakir/arabic-gte-multilingual-base-200k-lora | Y | ? | 64.3 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Mid; some cc-by-nc |
| C88 | AraModernBert-Base-STS (NAMAA) | https://huggingface.co/NAMAA-Space/AraModernBert-Base-STS | Y | Apache-2.0 | 54.44 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Lower |
| C89 | Arabic-labse-Matryoshka / LaBSE | https://huggingface.co/sentence-transformers/LaBSE | Y | Apache-2.0 | Older multilingual sentence encoder | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Older |
| C90 | Arabic-MiniLM-L12-v2-all-nli-triplet | https://huggingface.co/Omartificial-Intelligence-Space/Arabic-MiniLM-L12-v2-all-nli-triplet | Y | Apache-2.0 / cc-by-nc (conflict) | Small Arabic embedder | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | License conflict in leaderboard |
| C91 | granite-embedding-278m-multilingual (IBM) | https://huggingface.co/ibm-granite/granite-embedding-278m-multilingual | Y | Apache-2.0 | 51.54 Arabic | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Low Arabic score |
| C92 | multilingual-e5-base | https://huggingface.co/intfloat/multilingual-e5-base | Y | MIT | 57.55 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Superseded by large-instruct |
| C93 | Mizan Embeddings / Mizan-Rerank v1–v3 (ALJIACHI) | https://huggingface.co/ALJIACHI/Mizan-Rerank-v1 | Y | Apache-2.0 | Arabic embed/rerank; v1 rerank 76.26; v2/v3 pending | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Pending evaluation |
| C94 | oddadmix/arabic-reranker-v1 | https://huggingface.co/oddadmix/arabic-reranker-v1 | Y | ? | 79.93 rerank | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Below bge/Namaa |
| C95 | arabertv02_reranker_2021 | https://huggingface.co/anondeb/arabertv02_reranker_2021 | Y | CC-BY-NC-4.0 | 82.28 rerank | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | NC license |
| C96 | jina-reranker-m0 | https://huggingface.co/jinaai/jina-reranker-m0 | P | CC-BY-NC-4.0 | Multimodal reranker; failed Arabic eval | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | NC + failed eval |
| C97 | microsoft/harrier-oss-v1-0.6b, perplexity pplx-embed-v1-0.6b, tencent R3-rerank-0.6b | https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard | Y | MIT / Apache-2.0 | New 2026 embedders/rerankers pending Arabic eval | ? | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Not yet scored |
| C98 | Abdelkareem zaraah / abjd embeddings | https://huggingface.co/Abdelkareem | Y | MIT/other | Tiny distilled Arabic embedders (some failed eval) | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Experimental |
| C99 | LiquidAI LFM2-ColBERT-350M | https://huggingface.co/LiquidAI/LFM2-ColBERT-350M | P | Other | Late-interaction retriever (failed Arabic eval run) | ? | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Failed eval |
| C100 | Arabic BERTs: CAMeLBERT, MARBERT, asafaya bert-base-arabic | https://huggingface.co/CAMeL-Lab | Y | Apache-2.0 / various | Base encoders for fine-tuning classifiers/NER | Y | META | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) | Not retrieval-ready |
| C101 | Qalsadi | https://github.com/linuxscout/qalsadi | Y | GPL | Arabic morphological analyzer/lemmatizer | Y | CLEAN | K | Niche |
| C102 | Shakkala / Shakkelha | https://github.com/Barqawiz/Shakkala | Y | MIT (K) | Neural diacritization | Y | CLEAN | K | Older |
| C103 | Arabic LLMs for cleanup prompts: Jais, ALLaM, Fanar, Falcon-Arabic/Falcon-H1, SILMA, Falcon-Emirati | https://annota8.ai/blog/arabic-llm-benchmark-landscape-2026.html | P | various | Arabic-capable LLMs usable for normalization/extraction prompts | Y | CLEAN, META | [annota8](https://annota8.ai/blog/arabic-llm-benchmark-landscape-2026.html); [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) | Out of core scope (LLM selection) |
| C104 | Islamic MMLU leaderboard | https://huggingface.co/spaces/islamicmmlu/leaderboard | Y | - | Islamic knowledge eval | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) | Domain-specific |
| C105 | Arabic TTS Arena / SILMA TTS benchmarks | https://huggingface.co/spaces/Navid-AI/Arabic-TTS-Arena | Y | - | TTS comparison (for voice replies on WhatsApp) | Y | SERVE, EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) | Output side, not cleanup |
| C106 | ADIDA dialect ID demo | https://camel.abudhabi.nyu.edu/adida/ | Y | - | Dialect map UI using CAMeL DID | Y | META | [LREC](https://aclanthology.org/2020.lrec-1.868.pdf) | Demo |

### Inferences
- Several cached items (pywa, datasketch MinHash, Camelot) are genuinely useful utilities; they are cached only because they are generic or low-profile, not because they are bad.

### Gaps
- Licenses and maintenance status for most K-marked cache entries were not re-verified this session.
