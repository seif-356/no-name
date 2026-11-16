# Agents, agent builders and workflow automation that could sit on top of a company brain (as of 15 Nov 2026)

Method: OSS star counts, licences, last-push dates and archived flags were pulled live on 15 Nov 2026 from the GitHub search API ([GitHub API](https://api.github.com/search/repositories)); licence values are GitHub's SPDX detection ('NOASSERTION' = custom licence such as n8n Sustainable Use, Dify modified Apache, Mastra/Windmill/Activepieces EE splits). Licence explanations in parentheses (e.g. 'Sustainable Use', 'Polyform Shield', 'modified Apache') and acquisition notes marked 'unverified' come from prior knowledge, not from this pass. Hosted pricing comes from 2026 comparison blogs (many written by competing vendors) and conflicts frequently; conflicts are flagged inline. 'SMB non-tech fit' is the researcher's judgement (High = a non-technical owner could set it up alone; Low = needs a developer). About 200 OSS repos and about 30 hosted products are in this file; about 400 more repos and about 80 unverified hosted names are in agents_automation_cache.md.

## 1. General autonomous agents (Manus, OpenAI agent, Claude Cowork, Genspark, Lindy, Relevance, OpenManus, OWL, Agent Zero, AutoGPT, Suna, etc.)

### Takeaway
The general-agent space consolidated in 2026. OpenAI retired Operator (Aug 2025) and then agent mode (summer 2026) in favour of 'ChatGPT Work', and it is shutting down the visual Agent Builder on 30 Nov 2026. Claude Cowork ships inside Claude subscriptions. Manus and Genspark start at about $20/mo, and their credit-based top tiers reach $200-249. On the OSS side the scale is huge: OpenClaw (394k stars) and Hermes Agent (263k) dwarf the 2025 names. Suna was rebranded as Kortix CompanyOS (20.7k), and AgentGPT, SuperAGI and Bytebot are dead.

### Cited Findings
#### Hosted general agents / AI-assistant builders
| Name | URL | OSS | License | Pricing (hosted) | Self-host | SMB non-tech fit | Description / status | Source |
|---|---|---|---|---|---|---|---|---|
| Manus | https://manus.im | No | Proprietary | Entry paid ~$20/mo for 4,000 credits; top tiers up to ~$200/mo | No | High (chat UX) but credit burn unpredictable | General autonomous agent (research, slides, sites, browser tasks) | [Source](https://gptprompts.ai/llm-pricing-2026); [aipedia](https://aipedia-en.pages.dev/compare/manus-vs-genspark); [ArtificialAnalysis](https://artificialanalysis.ai/es/agents) |
| Genspark (Super Agent) | https://www.genspark.ai | No (released OSS genspark-ai/genoffice, 12.4k stars) | Proprietary | Entry plan ~10,000 credits/mo; top end up to ~$249/mo | No | High | All-in-one super agent: slides, sheets, calls, research; also AI office suite | [aipedia](https://aipedia-en.pages.dev/compare/manus-vs-genspark); [Source](https://gptprompts.ai/llm-pricing-2026) |
| Claude Cowork (Anthropic) | https://claude.com | No | Proprietary | Included in Claude Pro ($17/mo annual, $20 monthly), Max (from $100/mo), Team (from $20/seat annual), Enterprise | No (desktop app runs locally on files) | High | Desktop agent that works on local files/apps; one source says it was folded into the Claude chat app on 16 Sep 2026 (conflicting) | [Source](https://geeks.it.com/?p=985) |
| ChatGPT Work (OpenAI) - successor of Operator / ChatGPT agent | https://chatgpt.com | No | Proprietary | Plus $20/mo; Pro from $100/mo | No | High | Operator shut down 31 Aug 2025 and folded into ChatGPT agent; agent mode retired summer 2026 and replaced by ChatGPT Work (launched 9 Jul 2026). Also 'ChatGPT Workspace Agents' referenced | [Presenc](https://presenc.ai/research/openai-operator-update-tracker-2026); [Dassi](https://www.dassi.ai/compare/chatgpt-agent/); [Source](https://geeks.it.com/?p=985); [Sim](https://www.sim.ai/comparisons/openai-agentkit) |
| OpenAI Agent Builder (AgentKit canvas) | https://platform.openai.com | No | Proprietary | API usage | No | n/a | DEAD: deprecated 3 Jun 2026, shuts down 30 Nov 2026 with Evals; Agents SDK + ChatKit remain | [OpenAI community](https://community.openai.com/t/deprecation-notice-agent-builder/1382650); [Sim](https://www.sim.ai/comparisons/openai-agentkit) |
| Lindy | https://www.lindy.ai | No | Proprietary | Conflicting: free tier 400 credits/mo; $29.99/user/mo (3,000 credits) per Viktor & Zapier; $49.99/user/mo (5,000 credits) per Dupple/Simular; Business $199.99/mo; top-ups $10/1,000 credits | No | High (most-cited for non-tech owners: inbox, meetings, CRM, phone) | No-code AI assistant/agent builder; Autopilot computer use | [Viktor](https://viktor.com/blog/gumloop-alternatives); [Zapier](https://zapier.com/blog/best-ai-agent-builder/); [Dupple](https://dupple.com/learn/best-ai-workflow-automation-tools); [Simular](https://www.simular.ai/alternatives/best-ai-agent-builders); [Gumloop](https://www.gumloop.com/blog/best-ai-workflow-automation-tools); [AY Automate](https://www.ayautomate.com/blog/best-ai-workflow-automation-platforms) |
| Relevance AI | https://relevanceai.com | No | Proprietary | CONFLICT: Carly says Enterprise-only since Jun 2026 (Free/Pro $19/Team $234 removed May 2026); other 2026 pages still show Free/Pro $19-29/Team $234-349 (TheRundown) or Team $199/Business $599 (G2) | No | Medium (moved upmarket) | AI workforce / multi-agent builder for sales & ops | [Carly](https://www.usecarly.com/blog/relevance-ai/); [TheRundown](https://www.therundown.ai/tools/relevance-ai); [G2](https://www.g2.com/products/relevance-ai/pricing) |
| Viktor | https://viktor.com | No | Proprietary | $100 for 40,000 shared workspace credits | No | High | Describe-the-job AI coworker (Slack-centric) | [Viktor](https://viktor.com/blog/gumloop-alternatives) |
| Carly | https://carlyassistant.com | No | Proprietary | Zapier-style workflows free; AI agents from $35/mo | No | High | AI assistant + workflows for SMBs | [Carly](https://www.usecarly.com/blog/relevance-ai/) |
| MindStudio | https://www.mindstudio.ai | No | Proprietary | Entry ~$20/mo | No | High | No-code AI agent builder | [MindPal](https://mindpal.space/blog/top-ai-agent-builder-platforms-business-2026-comparison-a1b2c3) |
| Google Gemini (Workspace agents) | https://gemini.google.com | No | Proprietary | Free; AI Plus $4.99/mo; AI Pro $19.99/mo | No | High for Google Workspace shops | Agent next to Workspace data | [Activepieces](https://www.activepieces.com/blog/best-ai-agent-builders) |
| Microsoft Copilot Studio / M365 Copilot | https://copilotstudio.microsoft.com | No | Proprietary | Capacity packs / PAYG via Azure / per-seat M365 Copilot (no list price quoted) | No | Medium for M365 shops | Low-code custom agent builder | [Activepieces](https://www.activepieces.com/blog/best-ai-agent-builders) |
| Asana AI Studio / AI Teammates | https://asana.com | No | Proprietary | Starter $10.99 annual/$13.49 monthly; free Personal | No | High for Asana users | Agents inside project management | [Activepieces](https://www.activepieces.com/blog/best-ai-agent-builders) |
| Devin (Cognition) | https://devin.ai | No | Proprietary | 'Pricing has changed completely' in 2026 - current numbers not captured | No | Low | Autonomous software engineer | [FelloAI](https://felloai.com/best-ai-agents/) |
| OpenHands Cloud | https://all-hands.dev | Core OSS (MIT) | MIT core | Local OSS free (BYO key); cloud pricing not captured | Yes | Low | Hosted OpenHands coding agent | [FelloAI](https://felloai.com/best-ai-agents/) |
| Simular (Agent S / Simular Pro) | https://www.simular.ai | Partly (Agent-S Apache-2.0) | Apache-2.0 (Agent-S) | not captured | Partly | Medium | Computer-use agent company; publishes builder comparisons | [Simular](https://www.simular.ai/alternatives/best-ai-agent-builders) |

#### Open-source general / personal agents and chat-agent workspaces (live GitHub data)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| openclaw | https://github.com/openclaw/openclaw | Yes | MIT | 394.5k | 2026-11-15 | Yes | Medium | Hugely popular always-on personal agent ('the lobster'); runs on any OS, connects chat apps/tools. Many derivatives (NanoClaw, NemoClaw, AionUi). |
| hermes-agent | https://github.com/NousResearch/hermes-agent | Yes | MIT | 263.4k | 2026-11-15 | Yes | Medium | Self-improving personal agent from Nous Research; desktop companion exists (fathah/hermes-desktop). |
| AutoGPT | https://github.com/Significant-Gravitas/AutoGPT | Yes | custom/other (NOASSERTION) | 188.0k | 2026-11-15 | Yes | Medium | AutoGPT Platform: visual agent builder + marketplace; Polyform Shield licence on platform dir (NOASSERTION). |
| open-webui | https://github.com/open-webui/open-webui | Yes | custom/other (NOASSERTION) | 158.7k | 2026-11-14 | Yes | Medium-High | Most popular self-hosted AI chat UI; tools, functions, pipelines, RAG; custom licence (branding clause). |
| paperclip | https://github.com/paperclipai/paperclip | Yes | MIT | 114.0k | 2026-11-15 | Yes | Medium | Open-source app to manage agents at work (task board for agent workforce). |
| lobehub | https://github.com/lobehub/lobehub | Yes | custom/other (NOASSERTION) | 85.5k | 2026-11-15 | Yes | High | LobeHub chat workspace turned 'super-agents on your team' in existing chats; strong UI for non-tech. |
| deer-flow | https://github.com/bytedance/deer-flow | Yes | MIT | 85.4k | 2026-11-14 | Yes | Low-Med | ByteDance long-horizon 'SuperAgent' harness: research, code, create. |
| anything-llm | https://github.com/Mintplex-Labs/anything-llm | Yes | MIT | 68.3k | 2026-11-13 | Yes (desktop/Docker) | High | All-in-one desktop/server AI app with agents, RAG, no-code agent flows. |
| OpenManus | https://github.com/FoundationAgents/OpenManus | Yes | MIT | 59.0k | 2026-11-02 | Yes | Low | Open-source Manus clone from MetaGPT team. |
| goose | https://github.com/aaif-goose/goose | Yes | Apache-2.0 | 56.6k | 2026-11-14 | Yes (desktop) | Medium | Goose (originally Block) extensible desktop/CLI agent, MCP-native; now under AAIF org. |
| cherry-studio | https://github.com/CherryHQ/cherry-studio | Yes | AGPL-3.0 | 53.5k | 2026-11-15 | Yes (desktop) | High | Desktop AI workspace for models + agents (AGPL). |
| nanobot | https://github.com/HKUDS/nanobot | Yes | MIT | 50.1k | 2026-11-14 | Yes | Low-Med | Lightweight open-source personal agent (HKU). |
| CowAgent | https://github.com/zhayujie/CowAgent | Yes | MIT | 47.9k | 2026-11-13 | Yes | Medium | Personal assistant / agent harness with IM channel integrations (WeChat, Feishu, etc.). |
| LibreChat | https://github.com/LibreChat-AI/LibreChat | Yes | MIT | 47.1k | 2026-11-15 | Yes | Medium | ChatGPT-style UI with agents, MCP, skills. |
| AstrBot | https://github.com/AstrBotDevs/AstrBot | Yes | AGPL-3.0 | 46.9k | 2026-11-15 | Yes | Medium | Agent assistant framework integrating many IM platforms (AGPL). |
| openhuman | https://github.com/tinyhumansai/openhuman | Yes | GPL-3.0 | 42.7k | 2026-11-15 | Yes | Low | Agent harness focused on cost-efficiency (GPL-3.0). |
| khoj | https://github.com/khoj-ai/khoj | Yes | AGPL-3.0 | 38.1k | 2026-08-02 | Yes | Medium | Self-hostable 'AI second brain' with custom agents & scheduled automations; activity slowed (last push Aug 2026). |
| QwenPaw | https://github.com/agentscope-ai/QwenPaw | Yes | Apache-2.0 | 37.8k | 2026-11-13 | Yes | Medium | Personal AI assistant, easy install, local or cloud (AgentScope/Alibaba). |
| AgentGPT | https://github.com/reworkd/AgentGPT | Yes | GPL-3.0 | 36.3k | 2025-04-29 | Yes | Low | DEAD: repo archived (last push Apr 2025). |
| AionUi | https://github.com/iOfficeAI/AionUi | Yes | Apache-2.0 | 34.3k | 2026-11-05 | Yes (desktop) | Medium | 24/7 Cowork desktop UI for OpenClaw, Hermes, Claude Code, Codex, etc. |
| nanoclaw | https://github.com/nanocoai/nanoclaw | Yes | MIT | 31.1k | 2026-11-14 | Yes | Low-Med | Containerised, lightweight OpenClaw alternative. |
| gpt-researcher | https://github.com/assafelovic/gpt-researcher | Yes | Apache-2.0 | 30.7k | 2026-11-12 | Yes | Medium | Autonomous deep-research agent; good for report generation over web + docs. |
| agenticSeek | https://github.com/Fosowl/agenticSeek | Yes | GPL-3.0 | 27.7k | 2026-10-22 | Yes | Low | Fully local Manus alternative. |
| NemoClaw | https://github.com/NVIDIA/NemoClaw | Yes | Apache-2.0 | 23.0k | 2026-11-15 | Yes | Low | NVIDIA sandbox to run Hermes/Deep Agents/OpenClaw securely. |
| babyagi | https://github.com/yoheinakajima/babyagi | Yes | none detected | 22.4k | 2026-01-31 | Yes | Low | Original task-driven agent; now an experimental self-building 'functionz' framework. Largely historical. |
| CompanyOS | https://github.com/kortix-ai/CompanyOS | Yes | custom/other (NOASSERTION) | 20.7k | 2026-11-15 | Yes | Medium | Successor to Suna (Kortix) - 'open-source operating system for your company', multiplayer AI agents. Suna repo name no longer resolves. |
| owl | https://github.com/camel-ai/owl | Yes | none detected | 20.2k | 2026-11-09 | Yes | Low | OWL multi-agent workforce on CAMEL; strong GAIA results; no SPDX licence detected. |
| deep-research | https://github.com/dzhng/deep-research | Yes | MIT | 19.9k | 2026-04-11 | Yes | Low | Minimal iterative deep-research agent. |
| agent-zero | https://github.com/agent0ai/agent-zero | Yes | custom/other (NOASSERTION) | 19.9k | 2026-11-14 | Yes (Docker) | Low-Med | Agent Zero general-purpose personal agent framework with web UI. |
| rowboat | https://github.com/rowboatlabs/rowboat | Yes | Apache-2.0 | 18.2k | 2026-11-13 | Yes | Medium | Agent team in one group chat; multi-agent builder. |
| openfang | https://github.com/RightNow-AI/openfang | Yes | Apache-2.0 | 18.2k | 2026-07-02 | Yes | Low | Open-source 'Agent Operating System'. |
| SuperAGI | https://github.com/TransformerOptimus/SuperAGI | Yes | MIT | 17.7k | 2025-01-22 | Yes | Low | DEAD-ish: last push Jan 2025. |
| leon | https://github.com/leon-ai/leon | Yes | MIT | 17.7k | 2026-11-15 | Yes | Medium | Long-running open-source personal assistant. |
| eigent | https://github.com/eigent-ai/eigent | Yes | Apache-2.0 | 15.8k | 2026-11-13 | Yes (desktop) | Medium | Open-source Cowork desktop - local alternative to Claude Cowork; built on CAMEL. |
| GenericAgent | https://github.com/lsdefine/GenericAgent | Yes | MIT | 14.4k | 2026-11-06 | Yes | Low | Self-evolving agent growing a skill tree. |
| open_deep_research | https://github.com/langchain-ai/open_deep_research | Yes | MIT | 12.7k | 2026-08-10 | Yes | Low | ARCHIVED LangChain deep research reference. |
| OpenBot | https://github.com/CopilotKit/OpenBot | Yes | MIT | 12.3k | 2026-11-15 | Yes | Medium | Open-source AI coworkers each with their own computer (browser, files). |
| Octop | https://github.com/TencentCloud/Octop | Yes | MIT | 12.0k | 2026-11-15 | Yes | Medium | Self-hosted multi-user, multi-agent assistant. |
| hive | https://github.com/aden-hive/hive | Yes | Apache-2.0 | 11.2k | 2026-11-08 | Yes | Low | Multi-agent harness for production AI. |
| XAgent | https://github.com/OpenBMB/XAgent | Yes | Apache-2.0 | 8.6k | 2026-07-31 | Yes | Low | Autonomous agent for complex tasks (research project). |
| yao | https://github.com/YaoApp/yao | Yes | custom/other (NOASSERTION) | 8.3k | 2026-11-14 | Yes | Low-Med | All agents and workspaces in one place, on every device. |
| node-DeepResearch | https://github.com/jina-ai/node-DeepResearch | Yes | Apache-2.0 | 5.2k | 2026-11-13 | Yes | Low | Jina deep-search agent. |
| MIRIX | https://github.com/Mirix-AI/MIRIX | Yes | Apache-2.0 | 3.5k | 2026-11-11 | Yes | Low | Multi-agent personal assistant tracking screen activity, memory. |
| AGiXT | https://github.com/Josh-XT/AGiXT | Yes | MIT | 3.2k | 2026-07-28 | Yes | Low | Agent automation platform; activity slowing (last push Jul 2026). |
| MiroFlow | https://github.com/MiroMindAI/MiroFlow | Yes | Apache-2.0 | 3.2k | 2026-07-06 | Yes | Low | Deep research agent framework with web UI. |
| LocalAGI | https://github.com/mudler/LocalAGI | Yes | MIT | 2.0k | 2026-11-01 | Yes | Low-Med | Self-hostable, privacy-first agent platform (LocalAI family). |

#### Coding / Devin-style agents (OSS; adaptable to back-office automation via Claude Agent SDK-style harnesses)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| opencode | https://github.com/anomalyco/opencode | Yes | MIT | 226.9k | 2026-11-15 | Yes | Low | OpenCode - most-starred open-source coding agent (formerly sst/opencode). |
| claude-code | https://github.com/anthropics/claude-code | Yes | none detected | 155.7k | 2026-11-15 | Local CLI (proprietary) | Low-Med | Claude Code - Anthropic's agentic CLI; also basis of Claude Agent SDK; usable for non-coding automation. |
| codex | https://github.com/openai/codex | Yes | Apache-2.0 | 135.3k | 2026-11-15 | Local CLI | Low | OpenAI Codex CLI coding agent. |
| orca | https://github.com/stablyai/orca | Yes | MIT | 125.1k | 2026-11-15 | Local | Low | Run a fleet of coding agents with your own subscriptions. |
| gemini-cli | https://github.com/google-gemini/gemini-cli | Yes | Apache-2.0 | 108.8k | 2026-11-15 | Local CLI | Low | Gemini CLI open-source terminal agent. |
| OpenHands | https://github.com/OpenHands/OpenHands | Yes | MIT | 93.5k | 2026-11-15 | Yes | Low | OpenHands (ex-OpenDevin) - leading open Devin alternative; also hosted cloud. |
| cline | https://github.com/cline/cline | Yes | Apache-2.0 | 71.6k | 2026-11-13 | Local | Low | Autonomous coding agent as SDK/IDE extension/CLI. |
| MetaGPT | https://github.com/FoundationAgents/MetaGPT | Yes | MIT | 71.3k | 2026-01-21 | Yes | Low | Multi-agent 'AI software company'; last push Jan 2026 (slowing). |
| aider | https://github.com/Aider-AI/aider | Yes | Apache-2.0 | 50.1k | 2026-05-22 | Local | Low | Terminal pair programmer; slowing (last push May 2026). |
| ChatDev | https://github.com/OpenBMB/ChatDev | Yes | Apache-2.0 | 34.7k | 2026-11-06 | Yes | Low | ChatDev 2.0 multi-agent software company sim. |
| qwen-code | https://github.com/QwenLM/qwen-code | Yes | Apache-2.0 | 30.4k | 2026-11-15 | Local | Low | Qwen terminal coding agent. |
| crush | https://github.com/charmbracelet/crush | Yes | custom/other (NOASSERTION) | 29.1k | 2026-11-15 | Local | Low | Charm's agentic coding TUI. |
| vibe-kanban | https://github.com/BloopAI/vibe-kanban | Yes | Apache-2.0 | 28.7k | 2026-11-12 | Local | Low | Kanban orchestrator for coding agents. |
| SWE-agent | https://github.com/SWE-agent/SWE-agent | Yes | MIT | 20.8k | 2026-11-09 | Yes | Low | Princeton/Stanford issue-fixing agent. |
| humanlayer | https://github.com/humanlayer/humanlayer | Yes | Apache-2.0 | 12.9k | 2026-11-14 | Yes | Low | Human-in-the-loop tooling / coding agent workflows. |
| open-swe | https://github.com/langchain-ai/open-swe | Yes | MIT | 11.2k | 2026-11-15 | Yes | Low | Async cloud coding agent from LangChain. |
| gptme | https://github.com/gptme/gptme | Yes | MIT | 4.5k | 2026-11-15 | Local | Low | Terminal agent with local tools. |

### Inferences
- For a small non-technical business, the realistic 'autonomous agent on top of the company brain' options are subscription agents with connectors/MCP: Claude Cowork, ChatGPT Work, Manus, Genspark, Lindy and Viktor. Among OSS options, only the polished desktop/chat apps fit: AnythingLLM, LobeHub, Cherry Studio, Eigent and Open WebUI. Raw agent repos (OpenManus, OWL, Agent Zero, AutoGPT) still need a developer.
- Vendor churn risk is high: OpenAI killed two consumer agent surfaces and one builder within about 15 months, and Relevance AI moved to enterprise-only. Anything sitting on a company brain should talk to it through open protocols (MCP/A2A) so the agent layer can be swapped.
- The OpenClaw ecosystem (OpenClaw, NanoClaw, NemoClaw, AionUi, Hermes) is the dominant 2026 OSS personal-agent pattern, and it is worth evaluating as a self-hosted 'agent employee' over a company brain.

### Gaps
- MultiOn: no 2026 status found (possibly pivoted or dormant). Listed in the cache.
- Current Devin pricing was not captured. Manus's official pricing page was not read directly, and the reported Meta acquisition of Manus was not verified in this pass.
- Lindy and Relevance AI prices conflict across sources. Check the vendor pages before budgeting.
- Open Interpreter: the repo did not resolve under openinterpreter/open-interpreter in the GitHub search (it may have been renamed or made private). Status unknown.
- AWS Strands: strands-agents/sdk-python no longer resolves. strands-agents/harness-sdk (9.2k) appears to be the successor, but this was not confirmed.

## 2. Workflow automation with AI (n8n, Make, Zapier Agents, Activepieces, Pipedream, Windmill, Node-RED, Huginn, Gumloop, Bardeen, etc.)

### Takeaway
n8n (210k stars, fair-code, cloud from EUR20/mo) is the de-facto OSS hub. Activepieces (25.5k, MIT core) is the friendliest truly-open option. Zapier (free 100 tasks; $19.99/mo; Agents from about $33/mo) remains the easiest for non-technical users but costs the most at volume. Make (from $9/mo) and Gumloop ($37/mo) sit in between.

### Cited Findings
#### Hosted
| Name | URL | OSS | License | Pricing (hosted) | Self-host | SMB non-tech fit | Description / status | Source |
|---|---|---|---|---|---|---|---|---|
| Zapier (incl. Zapier Agents, Copilot, MCP) | https://zapier.com | No | Proprietary | Free 100 tasks/mo; Professional $19.99/mo annual ($29.99 monthly) 750 tasks; Team $69 2,000 tasks. Agents: free 400 activities/mo, Pro ~$33.33/mo annual 1,500 activities | No | High (default for non-tech, 8,000-9,000+ apps) but expensive at volume (> $300/mo at ~100k ops) | Market-leading no-code automation with AI agents | [Zapier](https://zapier.com/blog/best-ai-agent-builder/); [Dupple](https://dupple.com/learn/best-ai-workflow-automation-tools); [Simular](https://www.simular.ai/alternatives/best-ai-agent-builders); [AY Automate](https://www.ayautomate.com/blog/best-ai-workflow-automation-platforms) |
| Make (ex-Integromat) | https://www.make.com | No | Proprietary | Free 1,000 credits/mo; Core $9/mo, Pro $16, Teams $29 (FelloAI/Dupple); Viktor says $12 for 10,000 credits (conflict - billing basis) | No | High-Medium (visual canvas, cheaper at volume) | Visual scenario automation + AI agents | [FelloAI](https://felloai.com/best-ai-agents/); [Dupple](https://dupple.com/learn/best-ai-workflow-automation-tools); [Viktor](https://viktor.com/blog/gumloop-alternatives) |
| n8n Cloud | https://n8n.io | Fair-code | Sustainable Use License | Starter EUR20/mo annual (2,500 executions); Pro EUR50/mo (10,000); self-host Community free | Yes | Medium (needs technical setup; per-execution billing predictable) | Hosted n8n | [Dupple](https://dupple.com/learn/best-ai-workflow-automation-tools); [Viktor](https://viktor.com/blog/gumloop-alternatives); [Zapier](https://zapier.com/blog/best-ai-agent-builder/) |
| Activepieces Cloud | https://www.activepieces.com | Yes | MIT core | Free plan; Plus $20/mo; Team $200/mo; self-host CE free | Yes | High | 746 integrations; AI agents + MCP | [Activepieces](https://www.activepieces.com/blog/best-ai-agent-builders) |
| Gumloop | https://www.gumloop.com | No | Proprietary | Pro $37/mo, 20,000 credits, unlimited seats; overage $0.005/credit; 14-day trial; 8% orchestration fee | No | High (chat-to-build) | AI-native no-code workflows; Gumloop Browser; 300+ connectors, MCP | [Dupple](https://dupple.com/learn/best-ai-workflow-automation-tools); [Simular](https://www.simular.ai/alternatives/best-ai-agent-builders); [Carly](https://www.usecarly.com/blog/relevance-ai/) |
| Bardeen | https://www.bardeen.ai | No | Proprietary | Free 100 credits/mo; Basic $10/mo; Premium $50/mo ($480/yr, 1,000 credits) | No (browser ext) | High for GTM/sales | Browser-based AI automation for go-to-market; raised ~$25.3M | [Voiceflow blog](https://www.voiceflow.com/blog/bardeen-ai) |

#### Open-source / self-hostable (live GitHub data)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| n8n | https://github.com/n8n-io/n8n | Yes | custom/other (NOASSERTION) | 210.5k | 2026-11-15 | Yes (Sustainable Use / fair-code) | Medium (High w/ templates) | Leading fair-code visual workflow automation with AI agent nodes; 400+ integrations; cloud from EUR20/mo. |
| huginn | https://github.com/huginn/huginn | Yes | MIT | 50.5k | 2026-11-09 | Yes | Low | Classic self-hosted IFTTT-like agents (Ruby). |
| conductor | https://github.com/conductor-oss/conductor | Yes | Apache-2.0 | 32.5k | 2026-11-15 | Yes | Low | Netflix-born durable agentic workflow engine (community fork). |
| kestra | https://github.com/kestra-io/kestra | Yes | Apache-2.0 | 30.2k | 2026-11-14 | Yes | Low | Declarative YAML orchestration with AI agents. |
| budibase | https://github.com/Budibase/budibase | Yes | custom/other (NOASSERTION) | 28.4k | 2026-11-12 | Yes | Medium-High | Low-code internal apps + automations + AI agents for operations. |
| awesome-n8n-templates | https://github.com/enescingoz/awesome-n8n-templates | Yes | custom/other (NOASSERTION) | 26.4k | 2026-09-12 | n/a | High | 280+ free n8n templates (Gmail, Telegram, etc.). |
| activepieces | https://github.com/activepieces/activepieces | Yes | custom/other (NOASSERTION) | 25.5k | 2026-11-14 | Yes (MIT core CE) | High | Open-source Zapier alternative; ~400 MCP servers; simplest UI of OSS options; cloud Plus $20/mo. |
| nocobase | https://github.com/nocobase/nocobase | Yes | custom/other (NOASSERTION) | 24.9k | 2026-11-15 | Yes | Medium | Extensible no-code business system builder with AI employees. |
| temporal | https://github.com/temporalio/temporal | Yes | MIT | 24.4k | 2026-11-14 | Yes | Low | Durable execution engine; backbone for agent workflows (dev-only). |
| node-red | https://github.com/node-red/node-red | Yes | Apache-2.0 | 23.8k | 2026-11-13 | Yes | Low-Med | OpenJS low-code event flows; huge node library; IoT heritage. |
| n8n-mcp | https://github.com/czlonkowski/n8n-mcp | Yes | MIT | 23.3k | 2026-11-11 | Yes | Medium | MCP server letting Claude/ChatGPT build & operate n8n workflows - key glue for 'company brain' + n8n. |
| automa | https://github.com/AutomaApp/automa | Yes | custom/other (NOASSERTION) | 21.7k | 2026-03-02 | Browser extension | Medium | Block-based browser automation extension. |
| windmill | https://github.com/windmill-labs/windmill | Yes | custom/other (NOASSERTION) | 18.6k | 2026-11-14 | Yes (AGPL core + EE) | Low-Med | Code-first workflows, scripts, apps, AI agents; very fast engine. |
| trigger.dev | https://github.com/triggerdotdev/trigger.dev | Yes | Apache-2.0 | 16.8k | 2026-11-13 | Yes | Low | Durable background jobs & AI agents in TypeScript. |
| dagster | https://github.com/dagster-io/dagster | Yes | Apache-2.0 | 16.4k | 2026-11-13 | Yes | Low | Data orchestration (dev). |
| self-hosted-ai-starter-kit | https://github.com/n8n-io/self-hosted-ai-starter-kit | Yes | Apache-2.0 | 15.4k | 2026-11-12 | Yes | Medium | Docker template: n8n + Ollama + Qdrant + Postgres. |
| automatisch | https://github.com/automatisch/automatisch | Yes | custom/other (NOASSERTION) | 14.0k | 2026-02-11 | Yes (AGPL + EE) | Medium | Open-source Zapier alternative; slowing (last push Feb 2026). |
| keep | https://github.com/keephq/keep | Yes | custom/other (NOASSERTION) | 12.5k | 2026-11-10 | Yes | Low | AIOps alert workflows. |
| pipedream | https://github.com/PipedreamHQ/pipedream | Yes | custom/other (NOASSERTION) | 11.8k | 2026-11-13 | Components OSS; platform hosted | Low-Med | Pipedream: developer integration platform (acquired by Workday 2025 per reports - unverified here). |
| st2 | https://github.com/StackStorm/st2 | Yes | Apache-2.0 | 6.6k | 2026-10-29 | Yes | Low | 'IFTTT for Ops' event-driven automation. |
| inngest | https://github.com/inngest/inngest | Yes | custom/other (NOASSERTION) | 6.0k | 2026-11-15 | Yes (SSPL-ish, delayed OSS) | Low | Durable step functions + AgentKit. |
| actionsflow | https://github.com/actionsflow/actionsflow | Yes | MIT | 3.4k | 2025-10-21 | GitHub Actions | Low | Zapier/IFTTT alternative on GitHub Actions. |

### Inferences
- The best fit for 'company brain + 30% custom workflows' at a small business is likely a hosted/self-hosted n8n or Activepieces, with the company brain exposed as an MCP server or HTTP tool. Zapier is the fallback when nobody technical is available. n8n-mcp (23k stars) lets Claude/ChatGPT build n8n workflows from natural language, which lowers the skill barrier.
- Automatisch and Huginn are alive but slow. Temporal, Trigger.dev, Inngest, Kestra and Conductor are developer infrastructure, not SMB tools.

### Gaps
- Pipedream's ownership/pricing in 2026 was not verified (it was reportedly acquired by Workday in late 2025, unverified). Prices for Relay.app, Workato, Tray.ai, Pabbly and Latenode were not captured (see cache).
- The Make price conflict ($9 vs $12 entry) is unresolved.

## 3. Visual LLM app / agent builders (Flowise, Langflow, Dify, Rivet, Sim Studio, Voiceflow, Botpress, Stack AI, Vellum, etc.)

### Takeaway
Dify (161k), Langflow (157k) and Sim (30k, Apache-2.0) are the healthy OSS visual builders. Flowise is dead: Workday acquired it in Aug 2025, development stopped 29 Jul 2026, the repo was archived 13 Aug 2026, and it carries unpatched High/Critical advisories. OpenAI's Agent Builder shuts down 30 Nov 2026. Hosted customer-facing builders (Voiceflow about $60/mo, Botpress $150/mo) target chat and voice support rather than back-office automation.

### Cited Findings
- Flowise: Workday acquisition announced Aug 2025 ([Constellation Research](https://www.constellationr.com/insights/news/workday-acquires-flowise-speed-building-ai-agents-automated-workflows)); wind-down and archive, plus six High/Critical advisories published 10 Sep 2026 for v3.1.4 and earlier with no patch; community fork Keelflow v3.2.1 released 25 Sep 2026 ([AgentMarketCap](https://agentmarketcap.ai/blog/2026/07/30/flowise-sunset-low-code-agent-builders); [VibeCoding](https://vibecoding.app/blog/flowise-review); [StackOne](https://www.stackone.com/blog/ai-agent-builder-sunset/); archive date conflicts: 13 Aug vs 10 Aug). The GitHub API confirms archived=True with last push 2026-08-13 ([GitHub API](https://api.github.com/search/repositories)).
- OpenAI Agent Builder: deprecated 3 Jun 2026; Evals read-only 31 Oct 2026; shutdown 30 Nov 2026 ([Sim](https://www.sim.ai/comparisons/openai-agentkit); [OpenAI community](https://community.openai.com/t/deprecation-notice-agent-builder/1382650)).

#### Hosted
| Name | URL | OSS | License | Pricing (hosted) | Self-host | SMB non-tech fit | Description / status | Source |
|---|---|---|---|---|---|---|---|---|
| Voiceflow | https://www.voiceflow.com | No | Proprietary | Free 100 credits, 2 agents; Pro ~$60/mo (10,000 credits); Business ~$150/mo; +$50/editor; usage $0.005/msg, $0.05/phone min | No | Medium-High (design-led) | Chat + voice customer-facing agents | [TinyCommand](https://tinycommand.com/ai-agents/botpress-vs-voiceflow); [Macha](https://www.getmacha.com/blog/voiceflow-complete-guide) |
| Botpress Cloud | https://botpress.com | Legacy OSS (MIT repo) | MIT (repo) | New workspaces since 14 May 2026: Free 25 conversations; Plus $150/mo annual (250 conv, $25 AI incl.); Team $750/mo (1,500 conv). Older: Plus $89 / Team $495 + AI Spend | No | Medium | Chat-agent builder, developer-led | [Macha](https://www.getmacha.com/blog/voiceflow-complete-guide); [TinyCommand](https://tinycommand.com/ai-agents/botpress-vs-voiceflow) |
| Vellum | https://www.vellum.ai | No | Proprietary | Free Base plan | No | Medium | Agent builder / prompt + workflow platform | [Vellum](https://www.vellum.ai/blog/best-openai-operator-alternatives) |
| TinyCommand | https://tinycommand.com | No | Proprietary | Free plan; Professional $49/mo, 50,000 credits | No | High | Agent-on-your-data builder (vendor self-description) | [TinyCommand](https://tinycommand.com/ai-agents/botpress-vs-voiceflow) |
| Macha | https://www.getmacha.com | No | Proprietary | From $299/mo for 750 tickets (~$0.40/ticket) | No | High (done-for-you) | Support agent with setup included | [Macha](https://www.getmacha.com/blog/voiceflow-complete-guide) |
| Stammer.ai | https://stammer.ai | No | Proprietary | Pro White Label $99/mo | No | Medium (agencies) | White-label AI agents | [Totalum](https://www.totalum.app/blog/white-label-ai-agent-2026) |
| Synthflow | https://synthflow.ai | No | Proprietary | Via sales | No | Medium | White-label voice agents | [Totalum](https://www.totalum.app/blog/white-label-ai-agent-2026) |
| Insighto | https://insighto.ai | No | Proprietary | Agency Starter $299/mo | No | Medium | White-label chat/voice agents | [Totalum](https://www.totalum.app/blog/white-label-ai-agent-2026) |
| CrewAI AMP (hosted) | https://crewai.com | Core OSS | MIT core | Basic free (50 workflow executions/mo) | Yes (core) | Low-Med | Hosted CrewAI with visual studio | [FelloAI](https://felloai.com/best-ai-agents/) |

#### Open-source / self-hostable (live GitHub data)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| dify | https://github.com/langgenius/dify | Yes | custom/other (NOASSERTION) | 161.2k | 2026-11-15 | Yes (modified Apache w/ multi-tenant limits) | Medium-High | Dify: visual agentic workflows, RAG, chatbots; cloud plans + self-host. |
| langflow | https://github.com/langflow-ai/langflow | Yes | MIT | 156.6k | 2026-11-15 | Yes | Medium | Visual agent/flow builder (IBM/DataStax); MCP server support. |
| ragflow | https://github.com/infiniflow/ragflow | Yes | Apache-2.0 | 94.2k | 2026-11-13 | Yes | Medium | RAG engine with agent canvas; strong 'company brain' candidate itself. |
| Flowise | https://github.com/FlowiseAI/Flowise | Yes | custom/other (NOASSERTION) | 55.6k | 2026-08-13 | Yes (fork only) | Low (risk) | DEAD: Workday acquired (Aug 2025), dev stopped 29 Jul 2026, repo archived 13 Aug 2026, unpatched CVEs. Fork: Keelflow. |
| appsmith | https://github.com/appsmithorg/appsmith | Yes | Apache-2.0 | 41.3k | 2026-11-14 | Yes | Medium | Internal tool builder with AI agents. |
| ToolJet | https://github.com/ToolJet/ToolJet | Yes | AGPL-3.0 | 41.2k | 2026-11-14 | Yes | Medium | Internal app builder + AI (AGPL). |
| sim | https://github.com/simstudioai/sim | Yes | Apache-2.0 | 30.1k | 2026-11-15 | Yes | Medium-High | Sim Studio: Figma-like canvas to build/deploy AI agent workflows; positioning as OpenAI Agent Builder replacement. |
| FastGPT | https://github.com/labring/FastGPT | Yes | custom/other (NOASSERTION) | 30.0k | 2026-11-14 | Yes | Medium | Knowledge-base + visual workflow agent platform (China-popular). |
| MaxKB | https://github.com/1Panel-dev/MaxKB | Yes | GPL-3.0 | 23.2k | 2026-11-14 | Yes | Medium | Enterprise agent/KB platform (GPL). |
| coze-studio | https://github.com/coze-dev/coze-studio | Yes | Apache-2.0 | 21.8k | 2026-07-29 | Yes | Medium | ByteDance Coze open-source agent studio (visual). |
| rasa | https://github.com/RasaHQ/rasa | Yes | Apache-2.0 | 21.4k | 2026-07-24 | Yes | Low | Conversational AI framework (open core). |
| DB-GPT | https://github.com/eosphoros-ai/DB-GPT | Yes | MIT | 20.3k | 2026-11-15 | Yes | Low | Agentic data assistant. |
| DocsGPT | https://github.com/arc53/DocsGPT | Yes | MIT | 18.4k | 2026-11-14 | Yes | Medium | Private AI platform for agents + enterprise search. |
| parlant | https://github.com/emcie-co/parlant | Yes | Apache-2.0 | 18.3k | 2026-11-14 | Yes | Low | Customer-facing chat agents with guidelines/compliance. |
| botpress | https://github.com/botpress/botpress | Yes | MIT | 15.0k | 2026-11-13 | Hosted (OSS v12 legacy) | Medium | Chat-agent builder; cloud pricing per conversation since May 2026. |
| bisheng | https://github.com/dataelement/bisheng | Yes | Apache-2.0 | 12.3k | 2026-11-14 | Yes | Low-Med | Enterprise agent platform (China). |
| promptflow | https://github.com/microsoft/promptflow | Yes | MIT | 11.3k | 2026-11-11 | Yes | Low | LLM app flow tooling (Azure). |
| AutoAgent | https://github.com/HKUDS/AutoAgent | Yes | MIT | 9.8k | 2025-10-16 | Yes | Low | Zero-code LLM agent framework (research). |
| pyspur | https://github.com/PySpur-Dev/pyspur | Yes | Apache-2.0 | 5.8k | 2026-06-29 | Yes | Low | Visual playground for agentic workflows; slowing. |
| TaskingAI | https://github.com/TaskingAI/TaskingAI | Yes | Apache-2.0 | 5.4k | 2024-12-02 | Yes | Low | DEAD-ish: last push Dec 2024. |
| agenta | https://github.com/Agenta-AI/agenta | Yes | custom/other (NOASSERTION) | 4.9k | 2026-11-13 | Yes | Low | Workspace for building agents & automations + evals. |
| rivet | https://github.com/Ironclad/rivet | Yes | MIT | 4.7k | 2026-08-26 | Desktop | Low | Visual AI programming env; low activity (last push Aug 2026). |
| open-agent-platform | https://github.com/langchain-ai/open-agent-platform | Yes | MIT | 1.9k | 2026-02-25 | Yes | Low | ARCHIVED no-code agent platform by LangChain. |

### Inferences
- For non-technical SMBs, Dify Cloud and Sim are the most approachable OSS-backed canvases. Langflow is more developer-oriented. Dify, RAGFlow, FastGPT and MaxKB combine knowledge base and agents, so they overlap with the 'company brain' layer itself.
- The Flowise and Agent Builder shutdowns suggest that pure visual LLM canvases are being squeezed by coding agents and by workflow tools adding agents.

### Gaps
- Stack AI, Dify Cloud, Sim Cloud, Langflow (DataStax/IBM) hosted pricing and Rivet's maintenance status were not captured in this pass.

## 4. Agent frameworks (CrewAI, AutoGen/AG2, LangGraph, OpenAI Agents SDK, Claude Agent SDK, Google ADK, Pydantic AI, Agno, smolagents, Mastra, Semantic Kernel, Strands, etc.)

### Takeaway
All of these are developer libraries and unsuitable for direct use by non-technical SMBs. They matter only if an implementer builds custom agents over the company brain. By stars: LangChain 149.5k, AutoGen 61.8k, CrewAI 60.9k, LangGraph 45k, Agno 43.2k, OpenAI Agents SDK (Py) 30.7k, smolagents 30.4k, Mastra 29.5k, Semantic Kernel 28.8k, Google ADK (Py) 22.2k, Pydantic AI 21.2k, Microsoft Agent Framework 14.7k, Claude Agent SDK (Py) 8.5k.

### Cited Findings
(All star, licence and date values are from [GitHub API](https://api.github.com/search/repositories), 15 Nov 2026.)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| langchain | https://github.com/langchain-ai/langchain | Yes | MIT | 149.5k | 2026-11-14 | Library | Low | LangChain - most-used LLM framework, now 'agent engineering platform'. |
| daytona | https://github.com/daytonaio/daytona | Yes | none detected | 71.3k | 2026-07-24 | Yes | Low | Sandbox infra for AI-generated code. ARCHIVED. |
| autogen | https://github.com/microsoft/autogen | Yes | CC-BY-4.0 | 61.8k | 2026-11-12 | Library | Low | AutoGen; Microsoft now steers users to Agent Framework. |
| crewAI | https://github.com/crewAIInc/crewAI | Yes | MIT | 60.9k | 2026-11-13 | Library + CrewAI AMP cloud | Low-Med | Role-based multi-agent crews; hosted Basic tier free (50 executions/mo). |
| llama_index | https://github.com/run-llama/llama_index | Yes | MIT | 52.9k | 2026-11-14 | Library | Low | LlamaIndex - now 'document processing platform', agents/workflows. |
| langgraph | https://github.com/langchain-ai/langgraph | Yes | MIT | 45.0k | 2026-11-15 | Library | Low | Stateful graph agents; LangGraph Platform for deploy. |
| agno | https://github.com/agno-agi/agno | Yes | Apache-2.0 | 43.2k | 2026-11-14 | Library + AgentOS | Low-Med | Agno (ex-Phidata) - 'self-managing agent platform'. |
| dspy | https://github.com/stanfordnlp/dspy | Yes | MIT | 39.1k | 2026-11-13 | Library | Low | Programming (not prompting) LMs; optimizers. |
| CopilotKit | https://github.com/CopilotKit/CopilotKit | Yes | MIT | 38.7k | 2026-11-14 | Library | Low | Frontend stack for agents/generative UI (AG-UI). |
| agentscope | https://github.com/agentscope-ai/agentscope | Yes | Apache-2.0 | 36.0k | 2026-11-13 | Library | Low | Alibaba AgentScope multi-agent framework. |
| deepagents | https://github.com/langchain-ai/deepagents | Yes | MIT | 31.3k | 2026-11-15 | Library | Low | Batteries-included agent harness (planning, subagents, filesystem). |
| composio | https://github.com/ComposioHQ/composio | Yes | MIT | 31.1k | 2026-11-14 | Library + cloud | Low-Med | 1000+ toolkits/auth for agents - integration layer. |
| openai-agents-python | https://github.com/openai/openai-agents-python | Yes | MIT | 30.7k | 2026-11-15 | Library | Low | OpenAI Agents SDK (Python) - survives Agent Builder shutdown. |
| smolagents | https://github.com/huggingface/smolagents | Yes | Apache-2.0 | 30.4k | 2026-11-10 | Library | Low | HF code-acting minimal agents. |
| mastra | https://github.com/mastra-ai/mastra | Yes | custom/other (NOASSERTION) | 29.5k | 2026-11-15 | Library | Low | TypeScript agent framework (Gatsby team). |
| semantic-kernel | https://github.com/microsoft/semantic-kernel | Yes | MIT | 28.8k | 2026-11-13 | Library | Low | Enterprise SDK (C#/Python/Java). |
| fastmcp | https://github.com/PrefectHQ/fastmcp | Yes | Apache-2.0 | 28.5k | 2026-11-15 | Library | Low | Pythonic MCP servers/clients. |
| ai | https://github.com/vercel/ai | Yes | custom/other (NOASSERTION) | 28.0k | 2026-11-14 | Library | Low | Vercel AI SDK (TS) incl. agents. |
| haystack | https://github.com/deepset-ai/haystack | Yes | Apache-2.0 | 27.0k | 2026-11-14 | Library | Low | Production RAG/agent orchestration. |
| A2A | https://github.com/a2aproject/A2A | Yes | Apache-2.0 | 26.5k | 2026-11-13 | Protocol | Low | Agent2Agent interoperability protocol (Linux Foundation). |
| adk-python | https://github.com/google/adk-python | Yes | Apache-2.0 | 22.2k | 2026-11-14 | Library | Low | Google Agent Development Kit (Python); also Java/JS/Go. |
| swarm | https://github.com/openai/swarm | Yes | MIT | 22.1k | 2026-04-15 | Library | Low | Educational; superseded by Agents SDK. |
| pydantic-ai | https://github.com/pydantic/pydantic-ai | Yes | MIT | 21.2k | 2026-11-15 | Library | Low | Type-safe Python agent framework. |
| langchainjs | https://github.com/langchain-ai/langchainjs | Yes | MIT | 18.3k | 2026-11-13 | Library | Low | LangChain.js. |
| camel | https://github.com/camel-ai/camel | Yes | Apache-2.0 | 18.0k | 2026-11-09 | Library | Low | CAMEL multi-agent framework (basis of OWL, Eigent). |
| pipecat | https://github.com/pipecat-ai/pipecat | Yes | BSD-2-Clause | 17.3k | 2026-11-15 | Library | Low | Voice/multimodal agent framework (Daily). |
| agents | https://github.com/livekit/agents | Yes | Apache-2.0 | 15.2k | 2026-11-15 | Library | Low | Realtime voice agent framework. |
| E2B | https://github.com/e2b-dev/E2B | Yes | Apache-2.0 | 14.9k | 2026-11-14 | Yes | Low | Secure sandboxes for agent code execution. |
| agent-framework | https://github.com/microsoft/agent-framework | Yes | MIT | 14.7k | 2026-11-14 | Library | Low | .NET/Python successor merging AutoGen + Semantic Kernel. |
| ten-framework | https://github.com/TEN-framework/ten-framework | Yes | custom/other (NOASSERTION) | 11.2k | 2026-11-14 | Library | Low | Conversational voice agent framework. |
| voltagent | https://github.com/VoltAgent/voltagent | Yes | MIT | 11.0k | 2026-11-06 | Library | Low | TS agent framework + observability platform. |
| harness-sdk | https://github.com/strands-agents/harness-sdk | Yes | Apache-2.0 | 9.2k | 2026-11-14 | Library | Low | AWS Strands Agents - repo appears renamed to harness-sdk (sdk-python no longer resolves; TS SDK archived). |
| mcp-agent | https://github.com/lastmile-ai/mcp-agent | Yes | Apache-2.0 | 8.6k | 2026-01-25 | Library | Low | MCP-native agent patterns; slowing (Jan 2026). |
| claude-agent-sdk-python | https://github.com/anthropics/claude-agent-sdk-python | Yes | MIT | 8.5k | 2026-11-14 | Library | Low | Claude Agent SDK (Python) - Claude Code harness as a library. |
| Upsonic | https://github.com/Upsonic/Upsonic | Yes | MIT | 8.0k | 2026-06-18 | Library | Low | Python autonomous agents; slowing (Jun 2026). |
| swarms | https://github.com/kyegomez/swarms | Yes | Apache-2.0 | 7.4k | 2026-11-15 | Library | Low | Enterprise multi-agent orchestration. |
| marvin | https://github.com/PrefectHQ/marvin | Yes | Apache-2.0 | 6.2k | 2026-11-01 | Library | Low | Prefect's AI library (ControlFlow merged in). |
| ag2 | https://github.com/ag2ai/ag2 | Yes | Apache-2.0 | 5.1k | 2026-11-14 | Library | Low | Community fork AG2 (ex-AutoGen) 'AgentOS'. |
| youtu-agent | https://github.com/TencentCloudADP/youtu-agent | Yes | custom/other (NOASSERTION) | 4.6k | 2026-11-09 | Library | Low | Agent framework tuned for open models. |
| ruby_llm | https://github.com/crmne/ruby_llm | Yes | MIT | 4.5k | 2026-11-15 | Library | Low | Ruby AI framework. |
| openagents | https://github.com/openagents-org/openagents | Yes | Apache-2.0 | 4.4k | 2026-11-14 | Yes | Low | Collaboration OS for AI agents (networks). |
| AdalFlow | https://github.com/SylphAI-Inc/AdalFlow | Yes | MIT | 4.2k | 2026-11-01 | Library | Low | Auto-optimising LLM apps. |
| openai-agents-js | https://github.com/openai/openai-agents-js | Yes | MIT | 4.0k | 2026-11-15 | Library | Low | OpenAI Agents SDK (TS) incl. voice agents. |
| fast-agent | https://github.com/evalstate/fast-agent | Yes | Apache-2.0 | 4.0k | 2026-11-10 | Library | Low | MCP/ACP/A2A-native agent dev. |
| beeai-framework | https://github.com/i-am-bee/beeai-framework | Yes | Apache-2.0 | 3.5k | 2026-11-13 | Library | Low | IBM BeeAI framework (Py/TS), Linux Foundation. |
| griptape | https://github.com/griptape-ai/griptape | Yes | Apache-2.0 | 2.6k | 2026-11-13 | Library | Low | Modular Python agents/workflows. |
| agentUniverse | https://github.com/agentuniverse-ai/agentUniverse | Yes | Apache-2.0 | 2.4k | 2026-10-25 | Library | Low | Ant Group multi-agent framework. |
| claude-agent-sdk-typescript | https://github.com/anthropics/claude-agent-sdk-typescript | Yes | none detected | 1.9k | 2026-11-13 | Library | Low | Claude Agent SDK (TS). |
| adk-java | https://github.com/google/adk-java | Yes | Apache-2.0 | 1.8k | 2026-11-13 | Library | Low | Google ADK Java. |
| uAgents | https://github.com/fetchai/uAgents | Yes | Apache-2.0 | 1.6k | 2026-11-12 | Library | Low | Decentralised agents (Fetch.ai). |
| adk-js | https://github.com/google/adk-js | Yes | Apache-2.0 | 1.5k | 2026-11-14 | Library | Low | Google ADK TypeScript. |
| agent-kit | https://github.com/inngest/agent-kit | Yes | Apache-2.0 | 963 | 2026-04-29 | Library | Low | TS multi-agent networks. |

### Inferences
- Microsoft is consolidating AutoGen and Semantic Kernel into Agent Framework (14.7k). AG2 (5k) continues the community fork. OpenAI Swarm is superseded by the Agents SDK. LangChain's deepagents (31k) and the Claude Agent SDK represent the 2026 'agent harness' trend.
- MCP (fastmcp, Composio) and A2A are the integration standards to bet on for the company-brain interface.

### Gaps
- AWS Strands' rename was not confirmed. The AutoGen repo licence shows CC-BY-4.0 (docs licence; code is MIT per prior knowledge).

## 5. Browser / computer-use agents (Browser Use, Skyvern, Stagehand, Playwright MCP, etc.)

### Takeaway
Browser Use (121k stars) dominates. Skyvern (23.4k, AGPL) is the most business-workflow-oriented, with a no-code builder and cloud. Stagehand (26k) and Playwright MCP (39.7k) / Chrome DevTools MCP (56k) are the developer building blocks. Nanobrowser, BrowserOS and UI-TARS desktop are the most end-user-friendly OSS options. Bytebot, LaVague and Index are dead or archived.

### Cited Findings
(All values from [GitHub API](https://api.github.com/search/repositories), 15 Nov 2026.)

| Name | URL | OSS | License | Stars (15 Nov 2026) | Last push | Self-host | SMB non-tech fit | Description / notes |
|---|---|---|---|---|---|---|---|---|
| firecrawl | https://github.com/firecrawl/firecrawl | Yes | AGPL-3.0 | 201.8k | 2026-11-15 | Yes + cloud | Low-Med | Web data for agents (scrape/crawl/search), AGPL. |
| browser-use | https://github.com/browser-use/browser-use | Yes | MIT | 121.0k | 2026-11-14 | Yes + cloud | Low (lib) / Med (cloud) | Dominant OSS browser-agent library + Browser Use Cloud. |
| crawl4ai | https://github.com/unclecode/crawl4ai | Yes | Apache-2.0 | 87.4k | 2026-11-13 | Yes | Low | LLM-friendly crawler. |
| chrome-devtools-mcp | https://github.com/ChromeDevTools/chrome-devtools-mcp | Yes | Apache-2.0 | 56.4k | 2026-11-15 | Local | Low | Chrome DevTools MCP for agents. |
| browser | https://github.com/lightpanda-io/browser | Yes | AGPL-3.0 | 42.0k | 2026-11-15 | Yes | Low | Headless browser built for AI (AGPL). |
| playwright-mcp | https://github.com/microsoft/playwright-mcp | Yes | Apache-2.0 | 39.7k | 2026-11-13 | Local | Low-Med | Official Playwright MCP server - give any agent a browser. |
| UI-TARS-desktop | https://github.com/bytedance/UI-TARS-desktop | Yes | Apache-2.0 | 39.6k | 2026-10-09 | Desktop | Medium | Multimodal desktop/browser agent stack (UI-TARS). ARCHIVED. |
| cua | https://github.com/trycua/cua | Yes | MIT | 32.4k | 2026-11-15 | Yes | Low | Computer-use 2.0 drivers, sandboxes, benchmarks. |
| OpenCLI | https://github.com/jackwener/OpenCLI | Yes | Apache-2.0 | 31.1k | 2026-11-07 | Local | Low | Turn websites into CLIs using logged-in browser. |
| page-agent | https://github.com/alibaba/page-agent | Yes | MIT | 29.7k | 2026-11-13 | Library | Low | In-page JS GUI agent. |
| stagehand | https://github.com/browserbase/stagehand | Yes | MIT | 26.1k | 2026-11-14 | Library | Low | Browserbase SDK for AI web actions/extraction. |
| agent-desktop | https://github.com/vercel-labs/agent-desktop | Yes | Apache-2.0 | 23.8k | 2026-11-15 | Local | Low | Computer-use CLI for agents. |
| skyvern | https://github.com/Skyvern-AI/skyvern | Yes | AGPL-3.0 | 23.4k | 2026-11-15 | Yes + cloud | Medium | Vision-LLM browser workflow automation; no-code workflow builder; AGPL. |
| browser-harness | https://github.com/browser-use/browser-harness | Yes | MIT | 19.1k | 2026-11-15 | Local | Low | Let Claude Code/Codex use your real logged-in Chrome. |
| maxun | https://github.com/getmaxun/maxun | Yes | AGPL-3.0 | 18.4k | 2026-11-09 | Yes | Medium | No-code web data extraction/automation (AGPL). |
| web-ui | https://github.com/browser-use/web-ui | Yes | MIT | 16.7k | 2026-09-25 | Yes | Medium | Gradio web UI for browser-use. |
| midscene | https://github.com/web-infra-dev/midscene | Yes | MIT | 15.6k | 2026-11-13 | Library | Low | Vision-driven UI automation/testing (ByteDance). |
| BrowserOS | https://github.com/browseros-ai/BrowserOS | Yes | AGPL-3.0 | 14.3k | 2026-11-15 | Desktop | Medium | Open-source agentic browser (alt to Atlas/Comet). |
| nanobrowser | https://github.com/nanobrowser/nanobrowser | Yes | Apache-2.0 | 14.3k | 2026-11-10 | Chrome ext | Medium | Open-source Operator-like Chrome extension using your logged-in browser. |
| Agent-S | https://github.com/simular-ai/Agent-S | Yes | Apache-2.0 | 13.0k | 2026-11-13 | Yes | Low | SOTA open computer-use agent. |
| robotframework | https://github.com/robotframework/robotframework | Yes | Apache-2.0 | 12.0k | 2026-11-11 | Library | Low | Generic automation/RPA framework. |
| bytebot | https://github.com/bytebot-ai/bytebot | Yes | Apache-2.0 | 11.1k | 2025-09-12 | Yes | Low | DEAD: archived Sep 2025 (self-hosted desktop agent). |
| self-operating-computer | https://github.com/OthersideAI/self-operating-computer | Yes | MIT | 10.3k | 2026-10-19 | Local | Low | Multimodal model operates a computer. |
| UFO | https://github.com/microsoft/UFO | Yes | MIT | 10.2k | 2026-10-30 | Windows | Low | UFO3 Windows desktop agent. |
| magentic-ui | https://github.com/microsoft/magentic-ui | Yes | MIT | 10.1k | 2026-09-23 | Yes | Low-Med | Human-in-the-loop browser+files agent (MagenticLite). |
| steel-browser | https://github.com/steel-dev/steel-browser | Yes | Apache-2.0 | 8.0k | 2026-11-14 | Yes | Low | Open browser API for agents. |
| LaVague | https://github.com/lavague-ai/LaVague | Yes | Apache-2.0 | 6.4k | 2025-01-21 | Yes | Low | DEAD-ish: last push Jan 2025. |
| TagUI | https://github.com/aisingapore/TagUI | Yes | Apache-2.0 | 6.3k | 2026-11-08 | Yes | Medium | Free RPA tool (AI Singapore). |
| Integuru | https://github.com/Integuru-AI/Integuru | Yes | AGPL-3.0 | 4.8k | 2026-06-24 | Yes | Low | Agent that reverse-engineers internal APIs into integrations. |
| workflow-use | https://github.com/browser-use/workflow-use | Yes | AGPL-3.0 | 4.3k | 2026-11-13 | Yes | Low-Med | 'RPA 2.0' record-and-replay workflows (AGPL). |
| browser-agent | https://github.com/magnitudedev/browser-agent | Yes | Apache-2.0 | 4.1k | 2026-02-08 | Library | Low | Vision-first browser agent; slowing (Feb 2026). |
| autoMate | https://github.com/yuruotong1/autoMate | Yes | MIT | 4.0k | 2026-09-18 | Local | Medium | Manus-like computer-use agent. |
| openrpa | https://github.com/open-rpa/openrpa | Yes | MPL-2.0 | 3.1k | 2026-11-09 | Yes | Low-Med | Open-source enterprise RPA (MPL). |
| open-computer-use | https://github.com/e2b-dev/open-computer-use | Yes | Apache-2.0 | 2.4k | 2026-10-23 | Yes | Low | Computer use with open LLMs + E2B desktop. |
| notte | https://github.com/nottelabs/notte | Yes | custom/other (NOASSERTION) | 2.1k | 2026-11-14 | Yes + cloud | Low | Cloud browser + web agent platform. |
| OpenAdapt | https://github.com/OpenAdaptAI/OpenAdapt | Yes | MIT | 1.9k | 2026-11-14 | Yes | Low-Med | Demonstration-based desktop process automation (EHRs, portals). |
| terminator | https://github.com/mediar-ai/terminator | Yes | MIT | 1.7k | 2026-06-02 | Library | Low | Playwright-for-Windows computer use. |
| HyperAgent | https://github.com/hyperbrowserai/HyperAgent | Yes | custom/other (NOASSERTION) | 1.6k | 2026-05-11 | Library | Low | AI browser automation; slowing. |
| rpaframework | https://github.com/robocorp/rpaframework | Yes | Apache-2.0 | 1.6k | 2026-11-13 | Library | Low | Python RPA libraries. |
| agentql | https://github.com/tinyfish-io/agentql | Yes | MIT | 1.5k | 2026-11-14 | Library | Low | Query language for web elements. |
| Agent-E | https://github.com/EmergenceAI/Agent-E | Yes | MIT | 1.3k | 2026-05-04 | Yes | Low | Web automation agent; low activity. |

### Inferences
- For SMB legacy-portal automation (sites with no API), Skyvern Cloud or Browser Use Cloud plus the company brain is the most viable path. Gumloop Browser, Lindy Autopilot and Zapier's Chrome extension offer hosted equivalents for non-technical users ([Simular](https://www.simular.ai/alternatives/best-ai-agent-builders)).

### Gaps
- Browser Use Cloud, Skyvern Cloud, Browserbase, Steel and Hyperbrowser pricing was not captured. The www.activepieces.com and automationatlas.io pages could not be fetched directly (blocked by the session network), so their content was read via Firecrawl or search snippets only.
