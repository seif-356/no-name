# Business model, decisions and open issues

## Decisions made

| Item | Decision |
|---|---|
| Target | Small companies in Egypt worth up to ~$600k: traditional businesses and startups, any industry |
| Legal base | Canadian company; operations in Egypt; not Canada-only |
| Model | Standard base package (~70% of work) at fixed price + custom work (~30%) charged per need |
| Hosting | Local / in-country hosting offered |
| Own model | Not now: use existing models (API or local) |
| Status | 2 clients, different industries, paying infrastructure only |

## Target segment reality (estimates)

- ~5–30 employees, revenue roughly $100k–600k/year.
- Realistic budget for us: **~$50–300/month**, often in EGP and paid late.
- Real competitors here: ChatGPT/Claude/Gemini (~$20/user/month), free NotebookLM, Notion AI, n8n freelancers.
- Pain starts at ~15–30+ staff or high staff turnover.

## Unit economics

First clients took ~2 weeks each (learning time, not full-time days; real hours unknown).

| Scenario | Hours per client | Clients per year (solo) | Recurring revenue after 1 year at $100/month |
|---|---|---|---|
| Today (if ~80 h) | ~80 | ~20 | ~$2,000/month |
| With base-package tooling | ~25–30 | ~60 | ~$6,000/month |

At $1,000 setup and 80 hours, effective pay is ~$12.50/hour. Getting to $5,000/month at $100/month needs ~50 clients.

## Base package (fixed price) and add-on menu (fixed prices)

| Base package | Add-ons |
|---|---|
| Collect files from Drive, WhatsApp exports, Excel | Connect another system (CRM, ERP, accounting) |
| Cleanup, dedup, scanned and Arabic files | Custom structure for one department |
| Standard folder structure and tags | Customer-facing bot |
| AI assistant on web and WhatsApp | Workflow automation (per workflow) |
| 30 test questions signed off by client | Local hosting setup |
| Monthly data refresh (subscription) | Extra sources over the limit |

Set limits on the base (files, sources, users); anything above goes to the menu. For custom work, quote a fixed day rate.

## Obsidian

Use an **Obsidian-compatible Markdown vault as the storage layer**, not as the client product.

```
Client data → cleanup tooling → Markdown vault (folders, tags, links)
            → search index → AI answers → web chat + WhatsApp
```

- Strong: plain files the client owns, free, local, links and tags, works with AI tools (Claude Code, MCP, GBrain uses the same idea).
- Weak as the product: single-user desktop app, no permissions, no automatic intake, non-technical staff won't maintain it, no WhatsApp.

## Build plan

1. Intake (Drive, Excel, WhatsApp exports)
2. Cleanup (duplicates, scanned and Arabic files, clean text)
3. Structure (standard folders and tags)
4. Brain (search + answers with sources)
5. Access (web, then WhatsApp via the official Cloud API)
6. Monthly refresh

Build only what cuts time on the next client; measure each step.

## Open issues

1. No revenue for the founder's own work yet: charge the 2 current clients, even a small amount.
2. No cost data: log hours by task on client #3, then set prices.
3. "Any industry" limits repetition; the 70% figure is unproven.
4. Custom 30% has no pricing rule yet.
5. Canada incorporation: confirm tax residency with an accountant (a company run from Egypt may be taxed as Egyptian).
6. PDPL: confirm cross-border licensing with an Egyptian lawyer.

## Still needed from the founder

1. Current tech stack (language, AI model, database, hosting)
2. Client data types (PDF, scans, Excel, WhatsApp, Drive)
3. Language: Arabic, English, or both

## Verdict

Viable as a lean, profitable services business if the base package gets each client to ~25–30 hours. Weak as a venture-backed startup until narrowed to one industry or moved up to larger and Gulf clients.
