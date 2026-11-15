# Company brain products — CACHE (weaker, stale, marginal, unverified or adjacent entries, as of 15 Nov 2026)

Companion to `company_brain_products.md`. Nothing here was dropped; entries are here because they are (a) enterprise-only or adjacent rather than "connect data, AI answers", (b) acquired/sunset/deprecated, (c) named by the user but not verifiable this session, (d) agencies/services rather than products, (e) open-source repos/infrastructure rather than hosted products, or (f) only known from training data with low confidence.

Legend: **V** = confirmed this session from linked source; **TD** = from model training knowledge (cutoff mid-2026), NOT re-verified; **UNVERIFIED** = name supplied in the brief, could not be matched to a product.

## Which weaker / marginal entries should be retained for completeness?

### Takeaway
~95 additional entries. Highest-value items to re-check later: the four user-named 2026 "company brain" startups that could not be verified (Agently, Growy, Cerenovus, Savant), "Lore" and "Gaia"; status of Mendable, Tettra-like small wikis; and MENA vendors from MAGNiTT/Wamda not yet queried.

### Cited Findings

#### A. User-named but UNVERIFIED this session
| # | Name | Best-guess URL | Note | Ver. |
|---|---|---|---|---|
| C1 | Agently | unknown | Named in brief as 2026 company-brain vendor; no source found in this session's searches | UNVERIFIED |
| C2 | Growy | unknown | Named in brief; not found in company-brain comparisons ([MultiplierAI](https://multiplierai.ai/resources/company-brain-software), [Sentra](https://www.sentra.app/articles/best-company-brain-platforms), [Sento](https://www.sentohq.com/posts/best-company-brain-tools-2026)) | UNVERIFIED |
| C3 | Cerenovus | unknown | Named in brief; not found | UNVERIFIED |
| C4 | Savant | unknown | Named in brief; several unrelated "Savant" companies exist (e.g., Savant Labs analytics automation, TD) | UNVERIFIED |
| C5 | Lore | unknown | Named in brief as AI knowledge base; no current product found (search returned unrelated Marc Lore results) | UNVERIFIED |
| C6 | Gaia (MENA) | unknown | Named in brief as MENA/Arabic vendor; not identified | UNVERIFIED |
| C7 | Klikflo domain | klikflo.com? | Product verified by name ([MultiplierAI](https://multiplierai.ai/resources/company-brain-software)) but domain not confirmed | V (name) |

#### B. Acquired / sunset / deprecated / rebranded
| # | Name | URL | Status note | Ver. / Source |
|---|---|---|---|---|
| C8 | Rewind (Limitless) | https://www.limitless.ai | Rewind sunset after Meta acquired Limitless; Pendant sales ended 5 Dec 2025 | V — [limitless.ai](https://www.limitless.ai/) |
| C9 | Elastic Workplace Search / App Search | https://www.elastic.co | Deprecated in Elastic 9.0; not available to new customers; 8.x support end conflicts: 15 Jan 2027 vs 15 Jul 2027 | V — [Sentra](https://www.sentra.app/articles/glean-alternatives); [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| C10 | Elastic (Elasticsearch, Serverless search) | https://www.elastic.co/pricing/serverless-search | Build-your-own search; serverless from $0.09/VCU/hr; self-managed free | V — [Sentra](https://www.sentra.app/articles/glean-alternatives) |
| C11 | Amazon Q Business (legacy name) | https://aws.amazon.com/q/business/pricing/ | Evolved into AWS Quick; legacy pricing page still shows index pricing (e.g., Enterprise Index $190 example) | V — [AWS](https://aws.amazon.com/q/business/pricing/) |
| C12 | Google Agentspace (legacy name) | https://cloud.google.com/gemini-enterprise | Renamed Gemini Enterprise | V — [CData](https://www.cdata.com/blog/glean-alternatives-enterprise-ai) |
| C13 | Drift (Salesloft) | https://www.salesloft.com/platform/drift | Conversational marketing bot; contact for pricing; Drift acquired by Salesloft 2024, Salesloft merged with Clari 2025 (TD) | V (listing) — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/); corporate history TD |
| C14 | Mendable | https://www.mendable.ai | Docs chatbot; team's focus moved to Firecrawl; product believed wound down (TD) | TD |
| C15 | Sana Labs standalone | https://sanalabs.com | Now part of Workday (closed 4 Nov 2025) | V — [Workday](https://newsroom.workday.com/2025-11-04-Workday-Completes-Acquisition-of-Sana) |
| C16 | Moveworks standalone | https://www.moveworks.com | Now part of ServiceNow | V — [Moveworks](https://community.moveworks.com/announcements-updates-102/moveworks-servicenow-2927) |
| C17 | Bee (wearable) | https://www.bee.computer | Acquired by Amazon 2025 (TD) | TD |
| C18 | Qatalog | https://qatalog.com | Pivoted away from knowledge hub (TD) | TD |
| C19 | Humane / other wearables | n/a | Not relevant; noted to avoid confusion | TD |
| C20 | Stack Overflow for Teams naming | https://stackoverflow.co | Rebranded "Stack Internal" (TD, 2025) | TD |

#### C. Enterprise-only or adjacent platforms (marginal for SMB)
| # | Name | URL | One-line | Size | Pricing | Arabic | API/MCP | Ver. |
|---|---|---|---|---|---|---|---|---|
| C21 | Kestra | https://kestra.io | OSS workflow orchestration used to build RAG/search pipelines (2,600+ plugins) | Eng teams | OSS / EE | n/a | API | V — [Kestra](https://kestra.io/resources/ai/glean-alternatives) |
| C22 | Workato (Genies / Enterprise MCP) | https://www.workato.com | iPaaS with AI agents over company apps | Ent | Custom | ? | MCP (TD) | V (listed) — [Kestra](https://kestra.io/resources/ai/glean-alternatives) |
| C23 | AlphaSense | https://www.alpha-sense.com | Market intelligence search incl. internal content | Ent | Custom | ? | API | V (listed) — [Tricky Wombat](https://www.trickywombat.ai/enterprise-search-alternatives) |
| C24 | IBM watsonx Orchestrate | https://www.ibm.com/products/watsonx-orchestrate | Enterprise agent platform with knowledge | Ent | Custom | Y (TD) | API | TD |
| C25 | Salesforce Agentforce (+ Data Cloud) | https://www.salesforce.com/agentforce/ | Agents grounded in CRM + unstructured data | Mid-Ent | Per conversation/credits (TD) | Y (TD) | API, MCP (TD) | TD |
| C26 | ServiceNow Now Assist / AI Search | https://www.servicenow.com | Enterprise service AI incl. Moveworks | Ent | Custom | Y (TD) | API | TD |
| C27 | Aisera | https://aisera.com | Agentic AI for IT/HR service desks | Ent | Custom | ? | API | TD |
| C28 | Espressive (Barista) | https://www.espressive.com | Employee-assistant for IT/HR | Ent | Custom | ? | ? | TD |
| C29 | You.com (enterprise) | https://you.com/business | Research assistant with company data | Mid-Ent | TD | ? | API | TD |
| C30 | Zoom AI Companion / Zoom Docs | https://www.zoom.com/en/products/ai-assistant/ | AI over meetings, chat, docs; connectors | SMB-Ent | Included in paid Zoom (TD) | Y (TD) | ? | TD |
| C31 | Unleash | https://www.unleash.so | AI enterprise search assistant | Mid | TD | ? | ? | TD |
| C32 | Ayraa | https://www.ayraa.io | Work AI search + recall across apps | SMB-Mid | TD | ? | ? | TD |
| C33 | Credal | https://www.credal.ai | Secure AI platform/agents with permissioned enterprise data | Mid-Ent | TD | ? | API, MCP (TD) | TD |
| C34 | Pinecone Assistant | https://www.pinecone.io/product/assistant/ | Managed RAG assistant API | Dev | Usage | n/a | API, MCP (TD) | TD |
| C35 | Ragie | https://www.ragie.ai | RAG-as-a-service with connectors | Dev | Free + usage (TD) | n/a | API, MCP (TD) | TD |
| C36 | Sierra | https://sierra.ai | Enterprise customer-experience AI agents | Ent | Outcome-based (TD) | Y (TD) | ? | TD |
| C37 | Forethought | https://forethought.ai | Support AI agents | Mid-Ent | Custom | ? | ? | TD |
| C38 | Lorikeet | https://www.lorikeetcx.ai | AI support concierge for regulated industries | Mid | Custom | ? | ? | V (named) — [Fini](https://www.usefini.com/guides/top-chatbase-alternatives) |
| C39 | Amio | https://amio.io | Conversational design + integrations | SMB-Mid | Chatbot Starter $150; AI Expert $350 | ? | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| C40 | Rasa | https://rasa.com | OSS conversational AI framework; Growth plan $35,000/yr | Mid-Ent | $35k/yr | Y (TD) | API | V — [Jotform](https://www.jotform.com/ai/agents/chatbase-alternative/) |
| C41 | Staffbase | https://staffbase.com | Employee comms intranet with AI | Ent | Custom | Y (TD) | ? | TD |
| C42 | Microsoft Loop / SharePoint Premium | https://www.microsoft.com/microsoft-loop | Collaborative pages; AI via Copilot | SMB-Ent | Bundled | Y (TD) | Graph | TD |
| C43 | Zoho WorkDrive / Zia | https://www.zoho.com/zia/ | Zoho suite AI over business data | SMB | Bundled (TD) | Y (TD: Zoho strong in MENA) | API | TD |
| C44 | Gorgias Cortex (internal) | https://www.gorgias.com | Internal company brain built by Gorgias (12,000 Markdown nodes, 10-30c/query) — reference architecture, not for sale | n/a | n/a | n/a | MCP | V — [Slite solutions](https://slite.com/learn/company-brain-solutions) |

#### D. Open-source / developer infrastructure (not hosted products, kept for reference)
| # | Name | URL | Note | Ver. |
|---|---|---|---|---|
| C45 | GBrain (Garry Tan) | https://github.com/garrytan/gbrain | Open-source personal/company brain; MIT; released 5 Apr 2026; ~23.6K stars; cited by YC RFS | V — [Colrows](https://colrows.com/blogs/yc-company-brain-rfs/); [Slite](https://slite.com/learn/company-brain) |
| C46 | Sylph | unknown | Self-hosted plain-files-in-git brain pattern | V (named) — [Slite solutions](https://slite.com/learn/company-brain-solutions) |
| C47 | Letta (ex-MemGPT) | https://www.letta.com | Open-core agent memory SDK | V (named) — [Slite solutions](https://slite.com/learn/company-brain-solutions) |
| C48 | Graphiti (Zep OSS) | https://github.com/getzep/graphiti | Temporal knowledge graph engine | V — [Sentra](https://www.sentra.app/articles/best-company-brain-platforms) |
| C49 | Karpathy "LLM wiki" gist | https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f | Concept origin for self-maintaining wiki | V — [Slite](https://slite.com/learn/company-brain) |
| C50 | Foundation Capital "context graphs" essay | https://foundationcapital.com/ideas/context-graphs-ais-trillion-dollar-opportunity | 22 Dec 2025 concept origin | V — [Slite](https://slite.com/learn/company-brain) |
| C51 | Khoj | https://khoj.dev | OSS/hosted personal AI second brain | TD |
| C52 | Screenpipe | https://screenpi.pe | OSS screen/audio capture memory | TD |
| C53 | AnythingLLM (Mintplex) | https://anythingllm.com | Desktop/self-host RAG workspace; hosted option | TD |
| C54 | Open WebUI | https://openwebui.com | Self-host chat UI with knowledge bases | TD |
| C55 | LibreChat | https://www.librechat.ai | OSS ChatGPT-style UI with RAG | TD |
| C56 | Danswer (old name of Onyx) | https://onyx.app | Renamed Onyx | TD |
| C57 | PrivateGPT / h2oGPT | https://privategpt.dev | Local doc Q&A | TD |
| C58 | Scalekit + Cognee "Build a Company Brain" hackathon | https://www.tech-week.com | Event signal, not product | V — [Tech Week](https://www.tech-week.com/calendar/sf/events/build-a-company-brain-ai-agents-with-memory-context-and-secure-access-7be293b1-dbb0-458b-90be-6ec7e32794f6) |

#### E. Second-brain / notes / meeting tools (marginal for company use)
| # | Name | URL | Note | Ver. |
|---|---|---|---|---|
| C59 | Craft | https://www.craft.do | Docs/notes app with AI | V (listed) — [Saner tags](https://www.saner.ai/tags/knowledge-management) |
| C60 | Anytype | https://anytype.io | Local-first encrypted object notes | V (listed) — [Saner tags](https://www.saner.ai/tags/knowledge-management) |
| C61 | Evernote (AI) | https://evernote.com | Legacy notes with AI search | V (listed) — [Saner tags](https://www.saner.ai/tags/knowledge-management) |
| C62 | AmpleNote | https://www.amplenote.com | Notes + tasks with AI | V (listed) — [Saner tags](https://www.saner.ai/tags/knowledge-management) |
| C63 | Google Keep (Gemini) | https://keep.google.com | Lightweight notes | V (listed) — [Saner tags](https://www.saner.ai/tags/knowledge-management) |
| C64 | Elephas | https://elephas.app | Mac AI "super brain" over personal files | V (domain) — [Elephas](https://elephas.app/resources/amazon-quick-pricing) |
| C65 | Fabric | https://fabric.so | AI workspace/self-organizing drive | TD |
| C66 | Personal.ai | https://www.personal.ai | Personal/business memory AI | TD |
| C67 | Plaud (NotePin) | https://www.plaud.ai | AI voice recorder + notes | TD |
| C68 | tl;dv | https://tldv.io | Meeting recorder with multi-meeting AI reports | TD |
| C69 | Fathom | https://fathom.video | Meeting notetaker, team edition | TD |
| C70 | Glasp | https://glasp.co | Web highlights + AI | TD |
| C71 | Readwise Reader (Ghostreader) | https://readwise.io | Reading highlights with AI chat; MCP (TD) | TD |
| C72 | Sana AI (personal assistant app) | https://sana.ai | Sana's assistant product; status post-Workday unclear | TD |
| C73 | Microsoft OneNote + Copilot | https://www.onenote.com | Notes via Copilot | TD |

#### F. SMB chatbot builders (lower confidence / marginal)
| # | Name | URL | Note | Ver. |
|---|---|---|---|---|
| C74 | Elfsight AI Chatbot | https://elfsight.com/ai-chatbot-widget/ | Website widget chatbot trained on site content; widget-level | TD |
| C75 | Chatling | https://chatling.ai | No-code website AI chatbot | TD |
| C76 | Wonderchat | https://wonderchat.io | Website chatbot on your docs | TD |
| C77 | Chatsimple | https://www.chatsimple.ai | AI sales/support chatbot | TD |
| C78 | Dante AI | https://www.dante-ai.com | Custom chatbot on your data | TD |
| C79 | Agentplace | https://agentplace.io | Mentioned by Reddit user as Chatbase alternative | V (weak) — [Reddit](https://www.reddit.com/r/ChatGPT/comments/1r1i2n5/chatbase_alternative_heres_what_i_found_after/) |
| C80 | Zapier Agents / Chatbots | https://zapier.com/agents | AI agents + chatbots with knowledge sources over 7,000+ apps | TD |
| C81 | Relevance AI | https://relevanceai.com | AI workforce builder with knowledge | TD |
| C82 | Gumloop | https://www.gumloop.com | AI workflow automation with knowledge | TD |
| C83 | n8n (cloud) AI agents | https://n8n.io | Workflow automation with RAG nodes | TD |
| C84 | Flowise / Langflow cloud | https://flowiseai.com | Low-code RAG builders | TD |
| C85 | Poe / GPTs / Gemini Gems | n/a | Consumer custom bots with file knowledge; not business-governed | TD |

#### G. MENA — agencies, services and lower-confidence vendors
| # | Name | URL | Note | Arabic | Ver. |
|---|---|---|---|---|---|
| C86 | Eshal.ai | https://eshal.ai | Arabic AI chatbot guide/vendor for global businesses | Native | V (domain) — [Eshal](https://eshal.ai/blog/arabic-ai-chatbot-guide) |
| C87 | Modeer360 | https://modeer360.com | Arabic customer-service chatbot that takes actions (orders, bookings) on WhatsApp/IG/Messenger | Native | V (self-described) — [Modeer360](https://modeer360.com/en/blog/best-arabic-ai-chatbot-customer-service) |
| C88 | Fortune Code | https://www.fortunecode.org | Gulf-dialect Arabic chatbot (service/agency) | Native | V — [Fortune Code](https://www.fortunecode.org/en/services/arabic-ai-chatbot) |
| C89 | Ting Saudi | https://www.tingsaudi.com | Enterprise Arabic chatbot guidance/vendor KSA | Native | V (domain) — [Ting](https://www.tingsaudi.com/blog/arabic-ai-chatbots-saudi-enterprises) |
| C90 | Taahadsoft | https://taahadsoft.com | Arabic chatbot answering from your KB (agency) | Native | V — [Taahadsoft](https://taahadsoft.com/en/blogs/arabic-ai-chatbot-for-customer-service) |
| C91 | Imaddhin | https://www.imaddhin.com | Arabic-first Gulf chatbot build guide (agency) | Native | V — [Imaddhin](https://www.imaddhin.com/blog/arabic-ai-chatbot-gulf) |
| C92 | Rinaztec | https://rinaztec.com | Arabic chatbot development (agency) | Native | V — [Rinaztec](https://rinaztec.com/services/arabic-ai-chatbot) |
| C93 | Jamil Global | https://www.jamilglobal.com | AI agents/chatbots for KSA, Kuwait, UAE (agency) | Native | V — [Jamil Global](https://www.jamilglobal.com/blog/why-every-enterprise-in-saudi-arabia-and-kuwait-needs-ai-agents-and-chatbots-right-now) |
| C94 | Inception (G42) / Jais Chat | https://www.inceptionai.ai | Arabic LLM Jais; enterprise apps (TD) | Native | TD |
| C95 | Core42 (G42) | https://www.core42.ai | Sovereign cloud + Compass AI for UAE (TD) | Native | TD |
| C96 | Intella | https://intella.ai | Arabic speech analytics/voice AI (TD) | Native | TD |
| C97 | Mawdoo3 AI (Salma) | https://ai.mawdoo3.com | Arabic LLM/assistant (TD; status unclear) | Native | TD |
| C98 | TII Falcon (Falcon Arabic) | https://falconllm.tii.ae | Open Arabic LLM; component not product | Native | TD |
| C99 | Verint / Genesys Arabic bots | n/a | Global CCaaS with Arabic bots; adjacent | Y | TD |
| C100 | RevenueBase UAE list | https://revenuebase.ai/companies/enterprise-chatbot-platforms/united-arab-emirates | Data source: 127 enterprise chatbot companies linked to UAE (Oct 2026) — mine for more names | n/a | V — [RevenueBase](https://revenuebase.ai/companies/enterprise-chatbot-platforms/united-arab-emirates) |

#### H. Content/comparison sources that are themselves vendors (bias flags)
- Sentra (sentra.app), Slite, Gyld, Sento, MultiplierAI, Dust, Tana, Taskade, Saner, Littlebird, BrainTube, Chatbase, HelpJet, Jotform, Elbi, Tricky Wombat, Colrows, Jinba, NeuralTrust, cognee, Kestra, CData all publish "best X" lists that rank themselves first — [examples: Sentra](https://www.sentra.app/articles/best-company-brain-platforms), [Gyld](https://gyld.ai/blog/best-company-brain-software-in-2026-9-tools-that-give-ai-real-business-context), [Jinba](https://jinba.io/blog/compare-company-brain-tools), [NeuralTrust](https://neuraltrust.ai/blog/what-is-a-company-brain).
- Colrows (colrows.com) and Jinba (jinba.io) appear to be adjacent vendors (structured-data / workflow) — product scope not verified (TD/unknown).

### Inferences
- The unverified user-named startups (Agently, Growy, Cerenovus, Savant) may be very early/stealth or regional; they did not appear in any of the six 2026 company-brain comparison pages scraped.
- Rows marked TD are the most likely to be stale on price; re-verify before any recommendation.

### Gaps
- MAGNiTT, Wamda, Product Hunt and G2/Capterra were not directly queried (tool budget); they would likely add 50+ long-tail names, especially MENA.
- No verification of Arabic support for most global SMB chatbot builders beyond training knowledge.
