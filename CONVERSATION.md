# Full conversation log: AI company brain project

Context file for any person or AI agent joining the project. It records, in order, what the founder asked, what the analysis found, what was decided, and what was built. Founder messages are quoted as written (spelling kept). Assistant answers are condensed; the full detail lives in the files linked from [README.md](README.md).

**Project:** a done-for-you "AI company brain" for small Egyptian businesses: clean and organize a company's messy data, then connect an AI that answers from it (web chat + WhatsApp), optionally hosted locally.
**Founder preferences:** challenge every idea, be brutally honest, be precise, don't talk too much, do exactly what is asked.
**Dates:** 15–25 Nov 2026.

---

## 1. Market search, SWOT, red vs blue ocean

> "i want you to search the whole internet companies that make ai services for other mid cat companies the serveses that i am talking about is ai brain for the company as to collect and organize the whole company data so the what ever the ai is connected know to answer from the companys data search : instgram facebook x threads linkedin tiktok and google ... in need a swat analyses and to know is it blue ocain or red be brutel use grill-me skill"

**Answer (→ [analysis/01-market-and-swot.md](analysis/01-market-and-swot.md))**
- Verdict: **red ocean, getting redder.** "Company brain" was named a category by Y Combinator's Summer 2026 Request for Startups (April 2026).
- Players: suite giants (Microsoft Copilot, Gemini Enterprise, ChatGPT Enterprise, Claude Enterprise), funded specialists (Glean ~$300M ARR, Dust, Guru, Sana, Notion AI), the 2026 wave (Hyper, Sentra, Coworker, Lore), free/infra (GBrain, AWS Bedrock KB), agencies (Growy, Wobble, Propexo, many n8n freelancers).
- Social media: mostly agency owners and course sellers; X/Threads/TikTok not indexable.
- The grill-me skill was not available in the session, so the grilling was done directly.
- Six hard questions asked (why not Copilot's built-in connector, product vs service, which country/industry, who pays, messy data, defensibility).

## 2. Founder's answers, round 1

> "1. we work with them every step till there data turns from messy not readble to somthing with archticture and could be reachable with a click of a hand ... they dont need any expert on there side
> 2. we sell what the other company need . at the beging we will start with small ai brain development till we reach the companyes on model if they needed it ... we are targeting the nontechnical companies that dont want to lose to the race of ai integration
> 3. mostly egypt at the begning with a vesion to expand to canada
> 4. i am already working for multible companies that pays me but i want this insted of being just a freelance work i want to turn it to startup
> 5. we work till every thing it suited
> 6. this we will work on with you"

**Answer**
- Real differentiator is data cleanup + management, not AI. It's a consultancy until something repeats; charge cleanup separately.
- "Sell what they need" = freelancing. Custom models are a red flag: retrieval (RAG) over clean data beats training a model.
- Egypt: real edge (Arabic, Egyptian dialect, scanned docs, WhatsApp) but EGP, price-sensitive. PDPL (Law 151/2020) matters. Gulf is the better expansion than Canada.
- Unlimited scope at fixed price ruins margins.
- Local competitors found: Loop Wise, WideBot, DXwand, 103 AI consultancies in Egypt.

## 3. Founder's answers, round 2 + request for competitor research

> "for 2 i meant till we as me make my own model to help them / for 3 we can offer local hosting for there data brain / for the canada thing i have an a method to open a company there as my main branch ... / for 4 am still building and they are 2 and they paying for the infrastructure right now / no they donot share same industry / the same thing is the data cleanup and organizing / ... right now i want a full research on our compatitores and what companies do they serve and the net profit of each one and the company price for both also the service they offer"

**Answer (→ [analysis/02-competitors.md](analysis/02-competitors.md))**
- Own model: not at 2 clients (WideBot raised $3M to build one). Local hosting: decide who pays for hardware. Canada: check tax residency with an accountant.
- 2 clients paying only infrastructure = no revenue for the founder's work; the repeatable asset is data cleanup.
- Competitor table: Glean ($7.2B valuation, $300M ARR), Notion (~$11B, reportedly profitable), Sana (bought by Workday $1.1B), Coveo (net loss $28.9M), Elastic (net loss $68M/9 months), Dust, Guru, Onyx, Coworker, Sentra, Hyper; MENA: DXwand ($5M+ ARR), WideBot, Gaia, Arabic.ai, Loop Wise.
- Net profit is almost never public.

## 4. Client size and value

> "can you tell me the average rang of each company they serve" → "price range of the companies they serve" → "not there profit i want the customer company price in market ex company x worth 100k ..."

**Answer:** tables of each competitor's client size, client company value (e.g. Glean clients $500M–$500B+) and what clients pay. Founder's band (mid-size Egyptian) is ~$1M–$40M and unserved by funded players.

## 5. Target changed to small companies

> "the market i see is not this market i want to work with startup companies that there worth doesnot exceed the 600k dollor in egypt as an example could be higher or lower but i work with samll companies"

**Answer**
- ~5–30 staff, budget ~$50–300/month. Real rivals: ChatGPT/Claude/Gemini (~$20/user), NotebookLM (free), Notion AI, n8n freelancers.
- Pain starts at ~15–30+ staff. Tight economics: $5k/month needs ~50 clients at $100.
- Where it can work: one industry, WhatsApp interface, fixed package.

## 6. Focus questions

> "1. both if a comany needs 2. what ever the indestry 3. about a 2 weeks me alone working"

**Answer:** 2 weeks ≈ 80 h → ~$12.50/h at $1,000 setup, ~20 clients/year, ~$2k/month recurring after a year. "Any industry" keeps it at 80 h. Need 10–15 h per client via one industry, fixed package, cleanup tooling.

## 7. The 70/30 model

> "we will work on a genral bais and charge for the extra work so we fill about 70% of the work as a rebeated thing then we make the other 30% wih extra fee if needed"

**Answer:** workable, but (1) 70% is unproven, measure it; (2) the repeatable part is what cheap tools already do, so put WhatsApp, Arabic/scans, local hosting and monthly refresh into the base; (3) replace "extra fee if needed" with a fixed-price add-on menu. Target ~25–30 h per client → ~60 clients/year.

> "we will build the 70% so the pricing is ready the other 30% will be charged diffrently depending on what the company need the 80 hour thing this is becase i am new to this not case i work every day"

**Answer:** pricing needs a cost floor, so log hours by task on client #3. Use a fixed day rate for custom work. Build only what cuts time on the next client. Build order: intake → cleanup → structure → brain → web/WhatsApp → monthly refresh. Asked for stack, data types, language (still unanswered).

## 8. Summary requested

> "i want a clear view of what we ended up with"

**Answer (→ [analysis/03-business-model-and-decisions.md](analysis/03-business-model-and-decisions.md))**: idea, market, decisions, strengths, unresolved weaknesses, rules, build plan, verdict: viable as a lean services business, weak as a venture-backed startup unless narrowed.

## 9. Deep research on tools

> "brain storm and deepsearch all the ai assitance and tools and search engines like mimch and so on that could be used or build one alike i want a full reseach also search reels and repos for all new skills and tools that helps i want as many resorces as possible not less than 10k"

Clarified: "mimch" = all of Meilisearch, Mem, Perplexity-style engines, Manus. 10k declared unrealistic; founder chose "max raw list, drop the weaker but cache them in a file".

8 research tracks: answer/search engines, company-brain products, open-source RAG repos, data cleanup/OCR/Arabic, agents/automation, skills/MCP/dev tools, reels/creators, local models/hosting. Each wrote a main file and a `_cache` file (→ [research_notes/](research_notes/Company%20brain%20tools%20and%20repos/)). Report: [reports/Company brain tools and repos.md](reports/Company%20brain%20tools%20and%20repos.md). ~4,500 unique links, ~2,950 GitHub repos.

Key findings:
- **Egypt PDPL** Executive Regulations (Decree 816/2025), compliance deadline 1 Nov 2026: cross-border transfer of personal data needs a licence → local/in-country hosting is a selling point (confirm with a lawyer). No Azure/AWS/GCP region in Egypt; Huawei Cloud Cairo, Telecom Egypt, e& exist.
- **Arabic models:** Jais 3 (Apache 2.0, Egyptian dialect), Karnak (Egypt's AIC, #1 Open Arabic LLM Leaderboard, licence unconfirmed).
- **Cost:** API ~$10–37/month vs local hardware ~$110–150/month for a 20-person firm; local wins on compliance, not price.
- **Arabic OCR:** Gemini, Azure Document Intelligence, Baseer; free: Qari-OCR, dots.ocr. English leaders can drop to ~62% on Arabic.
- **Licences:** Docling, Crawl4AI safe; Firecrawl, PyMuPDF, Zingg AGPL; Marker revenue-capped.
- **WhatsApp:** use the official Cloud API; Baileys-based (Evolution API, WAHA) risks bans.
- **Gaps / opportunities:** no Arabic-first internal company brain in MENA; no Arabic NLP/OCR MCP server; no Arabic "company brain" content on social media.
- Correction: Growy, Lore and Gaia exist (one research track missed them).

Starter stack: Docling + MarkItDown → Arabic OCR → CAMeL Tools + Splink → Obsidian-compatible Markdown vault + Postgres → Meilisearch hybrid search → BGE-M3/arctic-embed + bge-reranker → Jais 3 via Ollama/vLLM → AnythingLLM web chat + official WhatsApp Cloud API → office box or in-Egypt hosting.

## 10. Obsidian

> "why not using obsedian brain ?"

**Answer:** use an Obsidian-compatible Markdown vault as the **storage layer** (client-owned plain files, free, local, works with AI tools; GBrain uses the same idea), not as the client product (single-user, no permissions, no intake, no WhatsApp, staff won't maintain it). Pipeline: data → cleanup → vault → search → AI → web + WhatsApp.

## 11. Repo housekeeping

- "add this person to the github": collaborator invites can't be done with the available tools; founder to invite via Settings → Collaborators.
- "remove the skills": meant the `grill-me` / `grilling` agent skills on branch `claude/brave-fermat-rwfd00` (the repo's default branch). The skills research was mistakenly removed, then restored.
- "merge it into main": `main` created with all research, no agent skills.
- "add it to the main everything we did": README + 3 analysis files added.
- This file added; other branches deleted.

---

## Open items (as of 25 Nov 2026)

1. Founder still to give: current tech stack, client data types, language (Arabic/English/both).
2. Charge the 2 current clients for the founder's work.
3. Log hours by task on client #3; then set base price and add-on prices.
4. Confirm PDPL implications with an Egyptian lawyer; Canada tax residency with an accountant.
5. Next build step: intake + cleanup tooling (steps 1–2 of the build plan).
