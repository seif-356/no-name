# Local models and hosting for an Arabic-capable company brain (Egyptian SMB focus), as of Nov 2026

Notes on method and reliability, applying to the whole file:
- Searches were run on 2026-11-15. Sources are mostly 2026 pages: model cards, vendor blogs, leaderboards, pricing pages, comparison blogs.
- **Verification tags.** "[V]" means this session saw a source page or search excerpt that states the fact. "[K]" means only the canonical URL is given: the entry comes from background knowledge and stable project facts (repo, broad license), and the version, price and fine detail were **not** re-checked this session. Treat every [K] item as needing a check before use.
- Most Arabic benchmark numbers are the developer's own, or come from an open leaderboard that self-submitted fine-tunes can game. Treat them as a reason to test a model, not as proof.
- Weaker, older or marginal entries are in `local_models_hosting_cache.md`.

---

## Q1. Open-weight LLMs good at Arabic, and what Arabic leaderboards say

### Takeaway
As of Nov 2026, the strongest downloadable Arabic-first family is **Jais 3**: Apache 2.0, six sizes from 0.9B to 375B-A23B, 512K context, released Oct 2026, with Egyptian dialect named in its training and evaluation. Egypt's own **Karnak** (Applied Innovation Center, under MCIT) sits **#1 on the Open Arabic LLM Leaderboard (OALL v2)** at 79.29 and is built for MSA plus Egyptian colloquial. Among general multilingual models, **Gemma 4** (Apache 2.0) and **Qwen3.5/3.6/3.8** (Apache 2.0) are the best local options for small hardware. The large Chinese MoEs (DeepSeek V4.x, GLM-5.x, Kimi K3) are the best open models overall but too large for SMB self-hosting. They are cheap via API.

### Cited Findings: leaderboards
- **OALL v2 (Hugging Face, `OALL/Open-Arabic-LLM-Leaderboard`)**. Top 10: #1 Applied-Innovation-Center/Karnak 79.29 avg (AlGhafa 79.01, ArabicMMLU 79.13, EXAMS 63.31, MadinahQA 88.16, AraTrust 88.34, ALRAGE 79.03, ArbMMLU-HT 78.04). #2 D2IL-Arabic-Qwen2.5-72B-Instruct-v0.1 75.86. #9 meta-llama/Llama-3.3-70B-Instruct 74.47. #10 Applied-Innovation-Center/AIC-1 73.89. The rest of the top 12 are mostly Qwen2.5-72B fine-tunes. [V] — [OALL Space](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard); mirrored with result-file dates (Karnak result dated 2026-02-15) at [benchmarklist.com](https://benchmarklist.com/benchmarks/open_arabic_llm_leaderboard/)
- OALL is dominated by community Qwen2.5-72B fine-tunes, and its benchmark set is mostly multiple choice. Newer families (Jais 3, Gemma 4, Qwen3.5+) do not appear in the top rows seen this session. [V, inference from the table] — [OALL Space](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard)
- An early-2026 summary said Falcon-H1 Arabic tops the OALL (7B 71.47%, 34B 75.36%). This conflicts with the live OALL table above, where Karnak scores 79.29. The likely explanation is that the TII figure is vendor-reported or comes from an older snapshot. [V] — [annota8.ai](https://annota8.ai/blog/arabic-llm-benchmark-landscape-2026.html); contradicted by [OALL Space](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard)
- **SILMA Arabic Broad Leaderboard (ABL)**. API models lead: gemini-3.5-flash 9.25/10, gpt-6-astra-pro 9.2, z-ai/glm-5 9.06. The best open-weight entry seen is **inception42/Jais-3-32B** at 8.99 benchmark and 9.75 MMLU score, ahead of qwen3.5-27b at 8.74. ABL also reports speed and a contamination score. [V] — [silma.ai/arabic-llm-leaderboard](https://silma.ai/arabic-llm-leaderboard)
- BALSAM: no 2026 results were retrieved this session. See Gaps.

### Cited Findings: Arabic-first open-weight models (main candidates)

| # | Model | URL | License | Size / ctx | Arabic notes | Hardware (vendor/est.) |
|---|---|---|---|---|---|---|
| 1 | **Jais-3-0.9B** | [HF inception42](https://huggingface.co/inception42) | Apache 2.0 | 0.9B, 128K | Arabic avg 68.5 vs Qwen3.5-2B 50.9 (vendor table) | 1 GPU, 2.2 GB BF16 [V] |
| 2 | **Jais-3-3.7B** | [HF inception42](https://huggingface.co/inception42) | Apache 2.0 | 3.7B, 512K | 78.1 vs Qwen3.5-4B 65.4, Gemma 4 E2B 64.5 | 10.1 GB BF16 [V] |
| 3 | **Jais-3-7B** | [HF card](https://huggingface.co/inception42/Jais-3-7B) | Apache 2.0 | 7B, 512K | 79.4 vs Gemma 4 12B 76.9, Qwen3.5-9B 70.9, ALLaM 7B 58.3 | 18 GB BF16; reference recipe on 1 H100 [V] |
| 4 | **Jais-3-32B** | [HF inception42](https://huggingface.co/inception42/Jais-3-32B) | Apache 2.0 | 32B dense, 512K | 83.1 vs Gemma 4 31B 82.6, Muse Glimmer 30B 80.5, Qwen3.8-27B 77.4; best open model on SILMA ABL | ~70 GB BF16 (1 H200). Q4 GGUF est. ~20 GB, so it fits on an RTX 5090 [V; Q4 is an estimate] |
| 5 | **Jais-3-MoVA-36B-A4B** | [HF inception42](https://huggingface.co/inception42) | Apache 2.0 | 36B MoE / 4B active, 512K | 82.5 | ~75 GB BF16. Low active params make it fast on unified-memory machines (inference) [V] |
| 6 | **Jais-3-375B-A23B** | [HF card](https://huggingface.co/inception42/Jais-3-375B-A23B) | Apache 2.0 | 375B MoE / 23B active | 84.0 vs Qwen3.5-397B 82.0, Nemotron 3 Ultra 81.2. Behind closed GPT-5.6 Sol 88.2 and Gemini 3.8 Flash 89.1 | 758 GB BF16; 8×H200 or 16×H100 [V] |
| — | Jais 3 family notes | [IFM blog](https://ifm.ai/blog/jais3/) | | | Built on K2 Horizon. Agentic/tool use. Names **Egyptian** and Emirati dialects, Arabizi, poetry and Islamic Q&A in training/eval. FP8, GGUF and MLX builds published. Cards recommend high reasoning effort and ≥32K output tokens, which adds latency. Launch date: blog metadata says 2026-10-12, TecnoStack says 15 Oct (corrected) | [V] [IFM](https://ifm.ai/blog/jais3/), [TecnoStack](https://tecnostack.com/en/blog/arabic-llm-comparison-falcon-allam-jais-fanar) |
| 7 | **Jais-2-70B-Chat** | [HF card](https://huggingface.co/inception42/Jais-2-70B-Chat) | Apache 2.0 (contact form before download) | 70B, 8K ctx | Released Dec 9, 2025 by Inception/Cerebras/MBZUAI; "richest Arabic-first dataset" | ~40 GB Q4 (est.) [V] [PRNewswire](https://www.prnewswire.com/ae/news-releases/inception-cerebras-and-mbzuai-release-jais-2--the-next-generation-of-the-worlds-leading-arabic-open-weight-llm-302636745.html), [arXiv 2608.13580](https://arxiv.org/abs/2608.13580) |
| 8 | **Jais-2-8B-Chat** | [HF card](https://huggingface.co/inception42/Jais-2-8B-Chat) | Apache 2.0 | 8B, 8K | MSA + dialects | ~5–6 GB Q4 (est.) [V] |
| 9 | **Karnak (Karnak-40B-v1.0)** — Egypt | [HF](https://huggingface.co/Applied-Innovation-Center/Karnak-40B-v1.0) | Free version on HF. License not captured: check the card | 40B "depth-extended Arabic–English"; vLLM example uses max_model_len 20000 | **#1 OALL v2 (79.29)**. MCIT says it understands and generates MSA **and Egyptian colloquial** "with high accuracy". Karnak Chat pilot launched Aug 23, 2026 | vLLM BF16 ~80 GB+. Q4 est. ~24 GB [V] [AIC news](https://www.aic.gov.eg/news/43/) |
| 10 | **Karnak-Th-41B-v1.0** (thinking variant) | [HF](https://huggingface.co/Applied-Innovation-Center/Karnak-Th-41B-v1.0) | not captured | 41B | Recent AIC upload (reasoning variant, inferred from name) | as above [V: existence only] |
| 11 | **AIC-1** — Egypt | [HF](https://huggingface.co/Applied-Innovation-Center/AIC-1) | not captured | not captured | OALL v2 #10, 73.89 | [V] |
| 12 | **Fanar-2-27B-Instruct** (QCRI, Qatar) | [HF](https://huggingface.co/QCRI/Fanar-2-27B-Instruct) | Apache 2.0 (Gemma 3 upstream: legal check advised) | 27B, 32,768 ctx; continued pretraining of Gemma-3-27B on 120B tokens | Names Gulf, Levantine and **Egyptian**. OALL-v2 69.40, ArabicMMLU 74.67 (PromptQuorum). Jais 3's own vendor table gives it only 48.9 Arabic avg (conflict). Stack includes speech, TTS, poetry, image and moderation models | Q4_K_M ~16–17 GB [V] [PromptQuorum](https://www.promptquorum.com/local-llms/best-arabic-local-llms-2026), [Fanar 2.0 notes](https://www.fanar.qa/en/2-0-release-notes) |
| 13 | **ALLaM-7B-Instruct-preview** (SDAIA/HUMAIN) | [HF](https://huggingface.co/humain-ai/ALLaM-7B-Instruct-preview) | Apache 2.0 per card (TecnoStack, SILMA). PromptQuorum calls it research/non-commercial: **conflict, check the card** | 7B, **4,096 ctx** | Beat Fanar slightly on StanceEval-2026 (0.726 vs 0.715). Jais 3 table: 58.3 | ~5 GB Q4 [V] [ACL 2026](https://aclanthology.org/2026.arabicnlp-sharedtasks.80.pdf) |
| 14 | **Falcon-H1-Arabic 3B / 7B / 34B** (TII) | [TII blog](https://huggingface.co/blog/tiiuae/falcon-h1-arabic) | **Unclear.** TecnoStack (21 Oct 2026) found no weights or named license. PromptQuorum says Falcon LLM License, commercial OK | Hybrid Mamba-Transformer; up to 256K ctx (128K for 3B) | Vendor-reported OALL 7B 71.47%, 34B 75.36%. Training covers Gulf, **Egyptian**, Levantine and Maghrebi | 7B Q4 ~5 GB. Treat as not yet self-hostable until weights are confirmed [V] |

### Cited Findings: general multilingual open-weight models with good Arabic (main candidates)

| # | Model | URL | License | Params (total/active), ctx | Arabic notes | VRAM / hardware |
|---|---|---|---|---|---|---|
| 15 | **Gemma 4 E2B** | [Gemma 4 card](https://ai.google.dev/gemma/docs/core/model_card_4) | Apache 2.0 | ~2B eff., 128K | Jais 3 table: 64.5 Arabic avg | phone/laptop class [V] |
| 16 | **Gemma 4 E4B** | same | Apache 2.0 | ~4B eff., 128K | 71.5 Arabic avg (Jais table) | <8 GB [V] |
| 17 | **Gemma 4 12B** | [HF](https://huggingface.co/google/gemma-4-12B-it) | Apache 2.0 | 12B, 256K, native audio | 76.9 Arabic avg (Jais table). MMLU-Pro 77.2, GPQA 78.8 | 6 GB INT4 / 24 GB FP16 [V] [Onyx](https://onyx.app/self-hosted-llm-leaderboard) |
| 18 | **Gemma 4 26B-A4B** | [HF](https://huggingface.co/google/gemma-4-26B-A4B-it) | Apache 2.0 | 26B MoE / 4B, 256K | No Arabic score seen | ~15 GB Q4 (est.) [V] |
| 19 | **Gemma 4 31B** | [HF](https://huggingface.co/google/gemma-4-31B-it) | Apache 2.0 | 31B dense, 256K | **82.6 Arabic avg, 87.2 Arabic language & culture**. Beats Jais 3 32B on culture (Jais vendor table) | 16 GB INT4 / 62 GB FP16; RTX 5090 or 24 GB card at Q4 [V] |
| 20 | **Qwen3.5-0.8B / 2B / 4B** | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | 201 languages | 2B: 50.9, 4B: 65.4 Arabic avg (Jais table) | tiny [V] |
| 21 | **Qwen3.5-9B** | [HF](https://huggingface.co/Qwen/Qwen3.5-9B) | Apache 2.0 | 9B, 128K | 70.9 Arabic avg; GPQA 81.7 | ~6 GB Q4 [V] [xigh list](https://github.com/xigh/open-weight-models) |
| 22 | **Qwen3.5-27B** | [HF](https://huggingface.co/Qwen/Qwen3.5-27B) | Apache 2.0 | 27B, 128K | SILMA ABL 8.74/10 | ~17 GB Q4 [V] |
| 23 | **Qwen3.5-35B-A3B** | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | 35B/3B, 262K | — | ~20 GB Q4. Fast on Mac/Strix Halo [V] [BenchLM](https://benchlm.ai/best/open-source) |
| 24 | **Qwen3.5-122B-A10B** | [HF](https://huggingface.co/Qwen/Qwen3.5-122B-A10B) | Apache 2.0 | 122B/10B, 256K, multimodal | — | ~70 GB Q4 (128 GB box) [V] |
| 25 | **Qwen3.5-397B-A17B** | [HF](https://huggingface.co/Qwen/Qwen3.5-397B-A17B) | Apache 2.0 | 397B/17B, 262K (1M YaRN) | 82.0 Arabic avg (Jais table) | multi-GPU server [V] |
| 26 | **Qwen3.6-27B / Qwen3.6-35B-A3B** | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | 27B 131K; 35B/3B | Used as a local workhorse in a 2026 router test | 1 high-memory GPU [V] [Morph](https://www.morphllm.com/best-open-source-llm), [Folkman](https://tylerfolkman.substack.com/p/i-tested-6-ai-models-across-3-providers) |
| 27 | **Qwen3.8-27B** | [HF](https://huggingface.co/Qwen/Qwen3.8-27B) | Apache 2.0 | 27B dense hybrid (Gated DeltaNet), native VLM, 262K (1M) | 77.4 Arabic avg (Jais table), but best on Arabic GAIA v2 (55.8). GPQA 89.2. Released Aug 5, 2026 | ~17 GB Q4; RTX 5090. OpenRouter $0.15/$1.88 per M [V] |
| 28 | **Qwen3.8-Flash-Next** | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 (assumed with the family; check) | 125B + 51B n-gram, ~6B active | 81.4 Arabic avg (Jais table) | needs 128 GB (Mac Studio M5 Max / DGX Spark) [V] [AI Engineer](https://theaiengineer.substack.com/p/mac-studio-vs-dgx-spark-vs-rtx-5090) |
| 29 | **Meta Muse Glimmer 30B** | [HF](https://huggingface.co/meta-models/Muse-Glimmer-30B) | Apache 2.0 | 29.6B dense, 131K | 80.5 Arabic avg (Jais table); SWE-bench V 76.0 | ~18 GB Q4 [V] |
| 30 | **Meta Muse Spark Open** | [BenchLM](https://benchlm.ai/models/muse-spark-open) | Muse Model License | 816B/42B, 1M, multimodal | ABL lists closed muse-spark-1.1 API at 9.2 | data-center [V] |
| 31 | **Llama 3.3 70B Instruct** | [HF](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct) | Llama Community | 70B, 128K | **OALL v2 #9 (74.47)**: highest non-fine-tuned base on OALL | ~40 GB Q4; 2×24 GB or 48 GB card [V] |
| 32 | **Llama 4 Scout / Maverick** | [Meta blog](https://ai.meta.com/blog/llama-4-multimodal-intelligence/) | Llama 4 Community | 109B/17B; 400B/17B | — | Scout ~60 GB Q4 [V] |
| 33 | **gpt-oss-20b** | [HF](https://huggingface.co/openai/gpt-oss-20b) | Apache 2.0 | 21B/3.6B, 128K | No Arabic score seen | fits 16 GB [V] |
| 34 | **gpt-oss-120b** | [HF](https://huggingface.co/openai/gpt-oss-120b) | Apache 2.0 | 117B/5.1B, 128K | — | 62 GB INT4; 1×80 GB or 128 GB box [V] |
| 35 | **DeepSeek-V4.1-Flash** | [OpenRouter](https://openrouter.ai/deepseek/deepseek-v4.1-flash-1017) | MIT | 552B, 8B/16B active, 1M | ABL lists deepseek-v4.1-flash at 9.14 (#8 overall) | 276 GB INT4. API **$0.038 in / $0.50 out per M** [V] |
| 36 | **DeepSeek-V4-Flash** | [HF](https://huggingface.co/deepseek-ai) | MIT | 284B/13B, 1M | — | 142 GB INT4. 39 tok/s on Mac Studio M5 Max (Lucebox) [V] [shattered.io](https://shattered.io/dgx-spark-vs-mac-studio-ryzen-ai-halo-local-ai-2026/) |
| 37 | **DeepSeek-V4-Pro** | [HF](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro) | MIT | 1.6T/49B, 1M | — | 800 GB INT4 [V] |
| 38 | **GLM-5.3** (Z.ai) | [BenchLM](https://benchlm.ai/models/glm-5-3) | Custom GLM-5.3 license | 753B/40B, 1M | ABL lists glm-5 at 9.06 | 376 GB INT4; 512 GB Mac Ultra [V] |
| 39 | **GLM-5.3-Flash** | [HF](https://huggingface.co/zai-org/GLM-5.3-Flash) | MIT | 320B/18B, 1M, multimodal | — | 161 GB INT4; 256 GB Mac M5 Ultra ($9,499) [V] |
| 40 | **GLM-4.7-Flash** | [HF](https://huggingface.co/zai-org/GLM-4.7-Flash) | MIT | 30B/3B, 200K | — | ~18 GB Q4 [V] |
| 41 | **Kimi K3 / K3.1 Pro** (Moonshot) | [HF](https://huggingface.co/moonshotai/Kimi-K3) | Custom Kimi licenses | 2.8T/104B, 1M | Top open model on several indices; out of SMB self-host reach | API K3.1 Pro $2/$10 per M [V] [BenchLM OpenRouter](https://benchlm.ai/hosts/openrouter) |
| 42 | **MiniMax M3** | [HF](https://huggingface.co/MiniMaxAI/MiniMax-M3) | MiniMax Community | 428B/23B, 1M | 78.7 Arabic avg (Jais table). Base of HUMAIN's Arabic humain-m3 | server [V] |
| 43 | **Mistral Small 4** | [HF](https://huggingface.co/mistralai/Mistral-Small-4-128K) | Apache 2.0 | 119B/6.5B, 256K, multimodal | — | ~65 GB Q4; 128 GB box [V] |
| 44 | **Mistral Medium 3.5 128B** | [HF](https://huggingface.co/mistralai/Mistral-Medium-3.5-128B) | Modified MIT (revenue cap) | 128B dense | — | [V] |
| 45 | **Cohere Command A+** | [Onyx table](https://onyx.app/self-hosted-llm-leaderboard) | Apache 2.0 (per Onyx; verify) | 218B, 128K | The Cohere Command family historically lists Arabic as a supported language [K] | 109 GB INT4 [V for size and license] |
| 46 | **NVIDIA Nemotron 3 Ultra** | [Morph](https://www.morphllm.com/best-open-source-llm) | OpenMDW | 550B/55B | 81.2 Arabic avg (Jais table) | server [V] |
| 47 | **Nemotron 3.5 Super-VL 120B-A12B** | [HF](https://huggingface.co/nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A12B-BF16) | OpenMDW-1.1 | 120B/12B, 1M | — | 128 GB box at Q4 [V] |
| 48 | **Tencent Hunyuan Hy4 Preview** | [geotoolbox](https://geotoolbox.ai/blog/best-open-source-llms) | Apache 2.0 | 770B/49B, 1M | — | server [V] |
| 49 | **Xiaomi MiMo-V2.6-Pro / Flash** | [BenchLM](https://benchlm.ai/models/mimo-v2-6-flash) | MIT | 1.02T/42B | Topped AA Index v4.3.2 among open models (46.3) | server [V] |
| 50 | **StepFun Step-3.5-Flash** | [HF](https://huggingface.co/stepfun-ai/Step-3.5-Flash) | Apache 2.0 | 196B/11B, 262K | — | ~110 GB Q4 [V] |
| 51 | **Ant Ling-2.6-flash / Ling 3.1 Flash** | [HF](https://huggingface.co/inclusionAI/Ling-2.6-flash) | MIT | 104B/7.4B | Ling 3.1 Flash API $0.045/$0.14 per M | 128 GB box [V] |
| 52 | **Aleph Alpha Kolibri-1** | [HF](https://huggingface.co/Aleph-Alpha/Kolibri-1-BF16) | Apache 2.0 | 78B/3.46B, 262K | — | ~45 GB Q4 [V] |
| 53 | **Reflection Beam** | [Morph](https://www.morphllm.com/best-open-source-llm) | Apache 2.0 | 501B/23B | — | server [V] |

### Inferences
- **Best local picks for an Egyptian SMB (Nov 2026):**
  - (a) **Jais-3-7B or 3.7B** for a single 24–32 GB GPU or a Mac. Arabic-first, Apache 2.0, Egyptian dialect in training.
  - (b) **Gemma 4 31B / 12B** as the multilingual alternative, Apache 2.0, strong Arabic culture scores.
  - (c) **Jais-3-32B or Karnak-40B** at Q4 on an RTX 5090 or a 48 GB card for best quality.
  - (d) **Qwen3.8-27B** when tool use and agents matter (best Arabic GAIA in its class).
  - Karnak is the only model that is both Egyptian-government-built and Egyptian-dialect-targeted. That may matter for public-sector clients, but check its license first.
- The vendor tables conflict. Jais 3's table puts Fanar 2 at 48.9 while PromptQuorum cites 69.40 on OALL. Each vendor's own harness favors its model, so SMBs should run a small Egyptian-Arabic eval set themselves.

### Gaps
- BALSAM leaderboard 2026 standings: not retrieved.
- Karnak and AIC-1 license terms and parameter counts for AIC-1: not captured.
- Falcon-H1-Arabic weight availability as of Nov 2026: last confirmed absent on 21 Oct 2026.
- No independent Egyptian-dialect benchmark (for example, an Egyptian subset of an Arabic eval) was found covering Jais 3, Gemma 4 and Karnak together.
- AceGPT, SILMA-9B, Noon and Command R7B-Arabic were not re-verified. They are in the cache file as legacy.

---

## Q2. Embedding and reranking models with Arabic support

### Takeaway
For self-hosted Arabic RAG, **Qwen3-Embedding (0.6B/4B/8B, Apache 2.0)** paired with **Qwen3-Reranker**, or **BGE-M3 (MIT)** paired with **bge-reranker-v2-m3**, are the default choices. One 2026 blog reports Qwen3 at 64.2 on Arabic versus Cohere v4 at 59.7 and OpenAI v3 at 54.3. Arabic-specific options (GATE-AraBERT, Arabic Matryoshka models, ARA-Reranker, Swan) are small and cheap, and worth testing on Egyptian-dialect queries.

### Cited Findings

| # | Model | URL | License | Size / dims / ctx | Arabic notes | Hardware |
|---|---|---|---|---|---|---|
| 54 | **Qwen3-Embedding-8B** | [HF](https://huggingface.co/Qwen/Qwen3-Embedding-8B) | Apache 2.0 | 8B; 32–4,096 dims (Matryoshka); 32K ctx | Vendor-reported 70.58 on MTEB multilingual (June 2025, #1 then). Blog per-language table: Arabic 64.2 vs Gemini 61.5, Cohere v4 59.7, OpenAI v3 54.3 | ~16 GB FP16; ~5 GB Q4 [V] [rework](https://resources.rework.com/tools/ai-data-infra/best-embedding-models-2026), [ailog](https://app.ailog.fr/en/blog/news/embedding-models-2026) |
| 55 | **Qwen3-Embedding-4B** | [HF](https://huggingface.co/Qwen/Qwen3-Embedding-4B) | Apache 2.0 | 4B, up to 2,560 dims | middle size | ~8 GB FP16 [K for details] |
| 56 | **Qwen3-Embedding-0.6B** | [HF](https://huggingface.co/Qwen/Qwen3-Embedding-0.6B) | Apache 2.0 | 0.6B | MMTEB 64.33 vs BGE-M3 59.56 (+8%) | CPU-feasible [V] [Medium](https://medium.com/@mrAryanKumar/comparative-analysis-of-qwen-3-and-bge-m3-embedding-models-for-multilingual-information-retrieval-72c0e6895413) |
| 57 | **Qwen3-Reranker-0.6B / 4B / 8B** | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | 0.6–8B | multilingual reranker paired with Qwen3-Embedding | [K] |
| 58 | **BAAI BGE-M3** | [HF](https://huggingface.co/BAAI/bge-m3) | MIT | 568M; 1,024 dims; 8,192 ctx | 100+ languages. Dense + sparse + ColBERT hybrid in one model. MTEB ~63.2 | CPU or small GPU [V] |
| 59 | **BAAI bge-reranker-v2-m3** | [HF](https://huggingface.co/BAAI/bge-reranker-v2-m3) | Apache 2.0 | ~568M | multilingual cross-encoder, commonly paired with BGE-M3 | [K] |
| 60 | **intfloat multilingual-e5-large / -instruct** | [HF](https://huggingface.co/intfloat/multilingual-e5-large-instruct) | MIT | 560M; 1,024 dims; **512 ctx** | 94 languages. Short context is the main limitation | [V] [rework](https://resources.rework.com/tools/ai-data-infra/best-embedding-models-2026) |
| 61 | **Alibaba gte-multilingual-base / gte-multilingual-reranker-base** | [HF](https://huggingface.co/Alibaba-NLP/gte-multilingual-base) | Apache 2.0 | 305M, 8K | 70+ languages incl. Arabic | [K] |
| 62 | **Jina embeddings v3** | [HF](https://huggingface.co/jinaai/jina-embeddings-v3) | CC-BY-NC-4.0 (commercial requires license) | 570M, 8K, Matryoshka | multilingual incl. Arabic | [K] |
| 63 | **Jina embeddings v4** | [HF](https://huggingface.co/jinaai/jina-embeddings-v4) | non-commercial / Qwen-research-derived | 3.8B, multimodal (text+image docs) | multilingual; useful for scanned Arabic PDFs | [K] |
| 64 | **Jina reranker v2 multilingual / m0** | [HF](https://huggingface.co/jinaai/jina-reranker-v2-base-multilingual) | CC-BY-NC | 278M | multilingual | [K] |
| 65 | **Nomic embed-text-v2-moe** | [HF](https://huggingface.co/nomic-ai/nomic-embed-text-v2-moe) | Apache 2.0 | MoE ~475M | ~100 languages | [V] [SurrealDB](https://surrealdb.com/blog/embedding-models-comparison) |
| 66 | **Snowflake arctic-embed-l-v2.0** | [HF](https://huggingface.co/Snowflake/snowflake-arctic-embed-l-v2.0) | Apache 2.0 | 568M, 8K | multilingual retrieval | [K] |
| 67 | **Google EmbeddingGemma-300m** | [HF](https://huggingface.co/google/embeddinggemma-300m) | Gemma terms | 300M | 100+ languages, on-device | [K] |
| 68 | **GATE-AraBERT-v1** (Omartificial) | [HF](https://huggingface.co/Omartificial-Intelligence-Space/GATE-AraBert-v1) | check card | AraBERT-base size | Arabic-specific embedding for RAG | CPU [V] [HF blog](https://huggingface.co/blog/Omartificial-Intelligence-Space/building-arabic-rag-pipeline-step-by-step) |
| 69 | **ARA-Reranker-V1** (Omartificial) | [HF](https://huggingface.co/Omartificial-Intelligence-Space/ARA-Reranker-V1) | check card | small cross-encoder | Arabic reranker; LangChain example | CPU [V] |
| 70 | **Arabic Matryoshka embedding collection** (Omartificial) | [HF collections](https://huggingface.co/Omartificial-Intelligence-Space/collections) | check card | various | Arabic Matryoshka models for efficient retrieval | CPU [V] |
| 71 | **Swan (Small / Large) + ArabicMTEB** | [arXiv](https://arxiv.org/html/2411.01192v2) | check release | small and large | Dialect-aware Arabic-centric embeddings. ArabicMTEB is the Arabic-specific benchmark to consult | [V] |
| 72 | **Cohere embed v4 / rerank** (API, not open) | [cohere.com](https://cohere.com/pricing) | proprietary | — | Arabic 59.7 in the blog table | API [V: score only] |
| 73 | **Voyage 4 / Gemini Embedding 2 / OpenAI text-embedding-3-small** (API) | [ayautomate](https://www.ayautomate.com/blog/best-embedding-models) | proprietary | — | Voyage 4 and Gemini Embedding 2 "lead on accuracy". text-embedding-3-small costs **$0.02 per 1M tokens** | API [V] |

### Inferences
- Embedding a whole SMB corpus (for example 10M tokens) costs only cents through APIs. The main reason to self-host embeddings is **data residency**, not cost. BGE-M3 or Qwen3-Embedding-0.6B run on CPU, which makes local embedding nearly free.
- Hybrid sparse+dense retrieval (BGE-M3) helps with Arabic spelling variants (hamza, taa marbuta, alef maqsura), which TecnoStack flags as a core Arabic test dimension. This is an inference. — [TecnoStack](https://tecnostack.com/en/blog/arabic-llm-comparison-falcon-allam-jais-fanar)

### Gaps
- Live MTEB Arabic and ArabicMTEB leaderboard numbers for Nov 2026 were not extracted. The MTEB space is dynamic. "Harrier" (74.3 multilingual MTEB v2) was mentioned without vendor details.
- No Egyptian-dialect retrieval benchmark was found.

---

## Q3. Inference and serving software

### Takeaway
For an SMB: **Ollama** or **llama.cpp** (GGUF) on a single box. **vLLM** or **SGLang** when serving multiple concurrent users on NVIDIA. **MLX / LM Studio** on Macs. **LiteLLM** as an OpenAI-compatible gateway in front of a mix of local and API models. Model cards in 2026 routinely give vLLM recipes (Karnak) and ship GGUF/MLX builds (Jais 3).

### Cited Findings

| # | Tool | URL | License | Role / notes |
|---|---|---|---|---|
| 74 | **Ollama** | [github.com/ollama/ollama](https://github.com/ollama/ollama) | MIT | One-command local runner on llama.cpp; OpenAI-compatible API. `ollama pull qwen3:8b` is cited as a standard path. [V for usage: [PromptQuorum](https://www.promptquorum.com/local-llms/best-arabic-local-llms-2026)] |
| 75 | **llama.cpp** | [github.com/ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp) | MIT | GGUF quantized inference on CPU/GPU/Metal/Vulkan; `llama-server`. Named in 2026 local guides [V: [Morph](https://www.morphllm.com/best-open-source-llm)] |
| 76 | **vLLM** | [github.com/vllm-project/vllm](https://github.com/vllm-project/vllm) | Apache 2.0 | High-throughput PagedAttention server; Karnak card gives `vllm serve` recipe [V: [Karnak card](https://huggingface.co/Applied-Innovation-Center/Karnak-40B-v1.0)] |
| 77 | **SGLang** | [github.com/sgl-project/sglang](https://github.com/sgl-project/sglang) | Apache 2.0 | Fast serving with RadixAttention; strong for MoE and agents [V mention: Morph] |
| 78 | **Hugging Face TGI** | [github.com/huggingface/text-generation-inference](https://github.com/huggingface/text-generation-inference) | Apache 2.0 | HF serving stack. Maintenance status in 2026 not verified [K] |
| 79 | **HF Text Embeddings Inference (TEI)** | [github.com/huggingface/text-embeddings-inference](https://github.com/huggingface/text-embeddings-inference) | Apache 2.0 | Serves BGE-M3, E5, GTE and rerankers [K] |
| 80 | **LM Studio** | [lmstudio.ai](https://lmstudio.ai) | Proprietary freeware (free for work use) | Desktop GUI; GGUF and MLX; local server [K] |
| 81 | **LocalAI** | [github.com/mudler/LocalAI](https://github.com/mudler/LocalAI) | MIT | OpenAI-API drop-in; multi-backend (LLM, embeddings, TTS, STT) [K] |
| 82 | **Jan** | [github.com/janhq/jan](https://github.com/janhq/jan) | Apache 2.0 (AGPL in earlier versions; check) | Offline desktop chat app [K] |
| 83 | **KoboldCpp** | [github.com/LostRuins/koboldcpp](https://github.com/LostRuins/koboldcpp) | AGPL-3.0 | Single-binary llama.cpp fork [K] |
| 84 | **NVIDIA TensorRT-LLM** | [github.com/NVIDIA/TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM) | Apache 2.0 | Maximum NVIDIA throughput; complex [K] |
| 85 | **Apple MLX / mlx-lm** | [github.com/ml-explore/mlx-lm](https://github.com/ml-explore/mlx-lm) | MIT | Mac-native inference; Jais 3 ships MLX builds [V: [TecnoStack](https://tecnostack.com/en/blog/arabic-llm-comparison-falcon-allam-jais-fanar)] |
| 86 | **Xinference** | [github.com/xorbitsai/inference](https://github.com/xorbitsai/inference) | Apache 2.0 | Serves LLMs, embeddings and rerankers behind one API [K] |
| 87 | **LiteLLM** | [github.com/BerriAI/litellm](https://github.com/BerriAI/litellm) | MIT (enterprise features separate) | OpenAI-compatible gateway/proxy; budgets, routing, fallbacks across local and API [K] |
| 88 | **Open WebUI** | [github.com/open-webui/open-webui](https://github.com/open-webui/open-webui) | Open WebUI License (BSD-3 plus branding clause) | Chat front-end with RAG for Ollama/OpenAI APIs; supports RTL [K] |
| 89 | **ExLlamaV3 + TabbyAPI** | [github.com/turboderp-org/exllamav3](https://github.com/turboderp-org/exllamav3) | MIT | Fast EXL quant inference on consumer NVIDIA [K] |
| 90 | **LMDeploy** | [github.com/InternLM/lmdeploy](https://github.com/InternLM/lmdeploy) | Apache 2.0 | TurboMind serving engine [K] |
| 91 | **KTransformers** | [github.com/kvcache-ai/ktransformers](https://github.com/kvcache-ai/ktransformers) | Apache 2.0 | CPU+GPU hybrid for giant MoEs (DeepSeek/Kimi) on one GPU + large RAM [K] |
| 92 | **Infinity (embeddings server)** | [github.com/michaelfeil/infinity](https://github.com/michaelfeil/infinity) | MIT | Fast embedding/rerank REST server [K] |
| 93 | **AMD Lemonade Server** | [github.com/lemonade-sdk/lemonade](https://github.com/lemonade-sdk/lemonade) | Apache 2.0 | Local LLM server for Ryzen AI / Strix Halo (NPU+iGPU) [K] |
| 94 | **exo** | [github.com/exo-explore/exo](https://github.com/exo-explore/exo) | Apache 2.0 (GPL earlier; check) | Cluster several Macs or PCs into one inference pool [K] |
| 95 | **llamafile** | [github.com/Mozilla-Ocho/llamafile](https://github.com/Mozilla-Ocho/llamafile) | Apache 2.0 | Single-file executable models [K] |
| 96 | **AnythingLLM** | [github.com/Mintplex-Labs/anything-llm](https://github.com/Mintplex-Labs/anything-llm) | MIT | All-in-one local RAG desktop/server (front-end over Ollama etc.) [K] |
| 97 | **NVIDIA NIM / Triton** | [developer.nvidia.com/nim](https://developer.nvidia.com/nim) | NVIDIA AI Enterprise (paid for production) | Packaged inference microservices [K] |

### Inferences
- A sensible SMB stack: Ollama or llama-server for chat, TEI or Infinity for embeddings and reranking, LiteLLM as a gateway with API fallback (DeepSeek or Qwen via OpenRouter) for overflow, and Open WebUI or AnythingLLM as the UI.

### Gaps
- Current 2026 release versions and any license changes for each tool were not re-checked this session ([K] items).

---

## Q4. Hardware and hosting options (consumer, cloud, MENA/Egypt) and Egyptian data residency

### Takeaway
A 128 GB unified-memory box costs about $4–7K: Mac Studio M5 Max, DGX Spark, or AMD Ryzen AI Halo. It can run Arabic-capable 30B dense or ~120B MoE models for a small team. Rented GPUs cost about $0.4–1.4/hr for an RTX 5090 (≈$300–1,000/month if always on). **Azure, AWS and GCP have no Egypt region.** In-country options are Huawei Cloud Cairo, Telecom Egypt, e& Egypt and local providers. Egypt's PDPL Executive Regulations (Decree 816/2025) require a **license for cross-border transfer** of personal data, with a compliance deadline of **1 Nov 2026**. That makes on-premise or in-country hosting attractive for a "company brain" that holds customer or employee data.

### Cited Findings: hardware

| # | Hardware | Price (2026) | Memory / bandwidth | Notes |
|---|---|---|---|---|
| 98 | **Mac Studio M5 Max 128GB** | **$5,399** (Oct 2026); range ~$5,100–5,400 | 128 GB unified, 614 GB/s | 174 W peak under agent load. DeepSeek V4 Flash at 39.35 tok/s (Lucebox). Entry Mac Studio from $2,499 [V] [AI Engineer](https://theaiengineer.substack.com/p/mac-studio-vs-dgx-spark-vs-rtx-5090), [shattered.io](https://shattered.io/dgx-spark-vs-mac-studio-ryzen-ai-halo-local-ai-2026/) |
| 99 | **Mac Studio M5 Ultra 256GB** | **$9,499**; M5 Ultra from $5,499; 512 GB price not confirmed | up to 512 GB | Runs GLM-5.3-Flash (256 GB) [V] |
| 100 | **NVIDIA DGX Spark 128GB** | **Conflict:** $6,950 (AI Engineer, shattered.io) vs $4,699 (vdf.ai); $3,999 at launch | 128 GB, 273 GB/s | CUDA. DeepSeek V4 Flash at 18.05 tok/s. Clustering up to 8 units. 64 GB option at $4,999 [V] [vdf.ai](https://vdf.ai/blog/dgx-spark-vs-mac-studio-vs-ryzen-ai-max-local-llm/) |
| 101 | **AMD Ryzen AI Halo (Ryzen AI Max+ 395)** | $3,999 at launch (Jul 2026) | up to 128 GB LPDDR5x-8000 | x86; Max+ PRO 495 variant raises the ceiling to 192 GB [V] |
| 102 | **Gigabyte AI TOP ATOM** | not captured | 128 GB, 273 GB/s | DGX Spark clone [V] |
| 103 | **NVIDIA RTX Spark** (Windows PCs) | not yet priced | up to 128 GB | Announced for fall 2026 [V] |
| 104 | **RTX 5090 desktop (32 GB)** | ~$11,690 for a full desktop (AI Engineer, scalped-market pricing); card draws 577 W | 32 GB, 1,792 GB/s | Fits Qwen3.8-27B or Jais-3-32B at Q4. Fastest decode per $ for ≤32 GB models [V] |
| 105 | **3× RTX 3090 (used)** | not captured | 72 GB | 124 tok/s vs DGX Spark 38.6 (IntuitionLabs). Cheap capacity [V] [shattered.io](https://shattered.io/dgx-spark-vs-mac-studio-ryzen-ai-halo-local-ai-2026/) |
| 106 | **RTX PRO 6000 Blackwell (96 GB)** | rent $0.64/hr Vast, $2.69/hr RunPod | 96 GB | Single-card 70B FP8 or 120B MoE [V] [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai) |

### Cited Findings: GPU clouds and API hosts

| # | Provider | URL | Price points (Nov 2026) |
|---|---|---|---|
| 107 | **RunPod** | [runpod.io/pricing](https://www.runpod.io/pricing) | RTX 5090 $1.39/hr secure; H100 PCIe $2.89 secure / $1.99 community; H100 SXM $4.39 / $2.69; A100 PCIe $2.09 / $1.19; H200 $5.29 / $3.59; per-second billing [V] |
| 108 | **Vast.ai** | [vast.ai](https://vast.ai) | Marketplace: RTX 5090 from $0.39–0.41/hr; L4 $0.10; A100 80GB $0.38; H100 $1.49–1.93; no SLA; unverified hosts carry interruption risk [V] [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai), [Spheron](https://www.spheron.network/blog/runpod-vs-vastai-2026/) |
| 109 | **Lambda** | [lambda.ai](https://lambda.ai) | A100 80GB $1.99–2.79/hr; H100 $3.29–3.99; 99.9% SLA [V] [PromptQuorum](https://www.promptquorum.com/local-llms/cloud-gpu-rental-comparison-2026) |
| 110 | **Hetzner GEX line** (Germany/Finland, EU) | [hetzner.com GPU](https://www.hetzner.com/dedicated-rootserver/matrix-gpu/) | Monthly dedicated: €214, €999, **€1,499 (GEX131, RTX PRO 6000 Blackwell Max-Q, Xeon Gold 5412U)**, €3,599, excl. VAT. Which GPU sits behind the €214, €999 and €3,599 tiers was not captured [V] [GEX131](https://www.hetzner.com/dedicated-rootserver/gex131/) |
| 111 | **Spheron** | [spheron.network](https://www.spheron.network/pricing/) | H100 $2.98/hr, A100 $1.48/hr (14 Nov 2026) [V] |
| 112 | **Salad** | [salad.com](https://salad.com) | RTX 4090 from $0.16/hr, RTX 5090 from $0.25/hr (consumer distributed GPUs) [V] |
| 113 | **OpenRouter** (API aggregator) | [openrouter.ai](https://openrouter.ai/pricing) | 5.5% platform fee (pay-as-you-go). 25+ free models (50 req/day; 1,000/day after $10 credit). DeepSeek V4.1 Flash $0.038/$0.50 per M; Qwen3.8-27B $0.15/$1.88; Kimi K3.1 Pro $2/$10; Ling 3.1 Flash $0.045/$0.14. `:floor` routes to the cheapest provider. **EU in-region routing exists, Egypt routing does not** [V] [OR blog](https://openrouter.ai/blog/tutorials/how-to-get-the-lowest-cost-llm-inference-on-openrouter/), [BenchLM](https://benchlm.ai/hosts/openrouter) |
| 114 | **DeepInfra** | [deepinfra.com](https://deepinfra.com) | Llama 3.3 70B $0.10 in / $0.32 out per M (cheapest of 4) [V] |
| 115 | **Novita** | [novita.ai](https://novita.ai) | Llama 3.3 70B $0.135 / $0.40 [V] |
| 116 | **Groq** | [groq.com](https://groq.com) | Llama 3.3 70B $0.59 / $0.79 (fast LPU) [V] |
| 117 | **Together AI** | [together.ai](https://together.ai) | Llama 3.3 70B $1.04 / $1.04 [V] |
| 118 | **Fireworks AI** | [fireworks.ai](https://fireworks.ai/pricing) | Serverless open models; not re-priced [K] |
| 119 | **Cerebras Inference** | [cerebras.ai](https://cerebras.ai) | Co-developer and trainer of Jais; fast inference. Not priced [V for Jais role] |
| 120 | **Inception / Jais web app and HF** | [HF collection](https://huggingface.co/collections/inceptionai/jais-2-family) | Jais available via HF download and web application [V] |
| 121 | **Fanar API** (QCRI) | [fanar.qa](https://www.fanar.qa/en/2-0-release-notes) | API on request plus web/mobile apps [V] |
| 122 | **HUMAIN Node / HUMAIN Chat** (Saudi) | [aijourn](https://aijourn.com/humain-unveils-humain-m3-a-frontier-arabic-language-model-developed-by-minimax-in-research-preview-on-humain-node/) | humain-m3 (428B MoE) in research preview. ALLaM 34B runs HUMAIN Chat (closed) [V] |

### Cited Findings: Egypt / MENA hosting and data residency

| # | Option | Source | Notes |
|---|---|---|---|
| 123 | **Microsoft Azure: no Egypt region** | [momentumx](https://momentumx.cloud/egypt-cloud-providers-2026/), [aabdc](https://www.aabdcegypt.com/blogs/post/egypt-data-centers-cloud-infrastructure) | Nearest regions: UAE, Qatar, South Africa. Saudi Arabia East due Q4 2026 [V] |
| 124 | **Huawei Cloud Cairo region** | [momentumx](https://momentumx.cloud/egypt-cloud-providers-2026/) | The hyperscaler with an Egypt region ("operating local public-cloud region") [V] |
| 125 | **Telecom Egypt Regional Data Hub (RDH/RDH2), Cairo** | [Arizton](https://www.arizton.com/market-reports/egypt-data-center-market), [aabdc](https://www.aabdcegypt.com/blogs/post/egypt-data-centers-cloud-infrastructure) | Tier III. Hosts EG-IX (with AMS-IX) and 22+ international customers. **A severe fire at a Telecom Egypt Cairo DC caused national outages**, so plan for redundancy [V] |
| 126 | **e& Egypt Mokattam Data Center** | [Arizton](https://www.arizton.com/market-reports/egypt-data-center-market) | Tier III [V] |
| 127 | **New entrants: Gulf Data Hub, Khazna Data Centers, Otech, NEOIX** | [Arizton](https://www.arizton.com/market-reports/egypt-data-center-market) | Egypt DC market [V] |
| 128 | **Egyptian local cloud providers: Arab Computers, Cloud4Rain; MENA sovereign cloud: MomentumX** | [momentumx](https://momentumx.cloud/egypt-cloud-providers-2026/) | Fit for SMB/hybrid. Source is a vendor (MomentumX), so it may be biased [V] |

### Cited Findings: Egypt PDPL (Law 151/2020) and Executive Regulations
- The Executive Regulations were issued by **MCIT Decree No. 816 of 2025** (effective/published around 1 Nov 2025). They set a tiered licensing system for processing, cross-border transfers, direct e-marketing and CCTV, plus consent, DPO and breach-reporting rules with the PDPC. — [JD Supra](https://www.jdsupra.com/legalnews/egypt-s-personal-data-protection-regime-4744548/), [Sedona Conf. translation](https://www.thesedonaconference.org/sites/default/files/meeting_paper/7.4%20Egypt%20Personal%20Data%20Protection%20Law%20-%20Executive%20Regulations.pdf)
- **Compliance deadline: 1 November 2026.** — [Lexis Middle East / Soliman, Hashish & Partners](https://www.lexismiddleeast.com/eJournal/2026-03-05_1/en)
- The law defines cross-border transfer broadly ("transfer, make available, record, store, circulate, publish, use…"). Transfer requires a **License or Permit from the Center (PDPC)**. — [Law text (ACC/MBH)](https://www.acc.com/sites/default/files/program-materials/upload/Data%20Protection%20Law%20-%20Egypt%20-%20EN%20-%20MBH.PDF)
- The regulations generally prohibit transferring, storing, sharing or processing personal data outside Egypt without a license or permit. Data-subject consent is required unless an exception applies. Adequacy-based transfers are allowed where the PDPC deems the foreign protection sufficient. Exceptions for non-adequate countries need explicit consent plus specific grounds (contract performance, legal rights, life/medical, and others). — [Ibrachy & Dermarkar](https://id.com.eg/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/)
- **Fees:** the controller/processor license is scaled by record count. It is **exempt for 1–10,000 records**, capped at **EGP 2,000,000/yr** for more than 5M records. Controller-only or processor-only licenses get 50% off. **Cross-border transfer licensing costs 50%** of the applicable controller/processor fee. Temporary permits are exempt up to 25,000 records. — [Ibrachy & Dermarkar](https://id.com.eg/overview-of-the-executive-regulations-of-the-egyptian-personal-data-protection-law/)
- Controllers and processors must use technologies that guarantee adequate protection during transfer, sharing and storage, "commensurate with the volume and nature of the data authorized for cross-border transfer". — [Sedona Conf. translation](https://www.thesedonaconference.org/sites/default/files/meeting_paper/7.4%20Egypt%20Personal%20Data%20Protection%20Law%20-%20Executive%20Regulations.pdf)

### Inferences
- Sending customer or employee personal data in prompts to a foreign API (OpenRouter, DeepSeek, US or EU clouds) counts as cross-border processing. On a plain reading of the regulations, it requires a PDPC transfer license or permit plus consent. A small business with **≤10,000 records may be fee-exempt for the base license**, but still needs the license or permit process. This is a legal inference: confirm with Egyptian counsel.
- **On-premise (a Mac Studio or Strix Halo box in the office) or in-country hosting (Huawei Cloud Cairo, Telecom Egypt, local providers) avoids the transfer question entirely.** A hybrid that routes only non-personal or anonymized queries to cheap APIs is a pragmatic middle path.
- Hetzner (EU) is cheap and GDPR-grade, but still counts as cross-border from Egypt's perspective.

### Gaps
- PDPL penalty amounts (EGP fines) and DPO thresholds were not captured this session.
- No in-country Egyptian GPU-cloud pricing (Huawei Cloud Cairo GPU instances, Telecom Egypt GPU) was found.
- Egyptian electricity tariffs and hardware import or retail prices in EGP were not retrieved.

---

## Q5. Monthly cost: local versus API for a small-business brain

### Takeaway
For typical SMB volumes (tens of millions of tokens per month), **open-model APIs cost about $10–40/month**. Local hardware amortizes to **about $110–200/month** plus power, and rented always-on GPUs cost **$300–1,100/month**. Local wins on privacy and PDPL simplicity, not on raw cost, unless usage is heavy or data must stay in Egypt.

### Cited Findings
- DeepSeek V4.1 Flash costs $0.038/M input and $0.50/M output on OpenRouter. Qwen3.8-27B costs $0.15/$1.88. OpenRouter adds a 5.5% fee. — [OpenRouter](https://openrouter.ai/deepseek/deepseek-v4.1-flash-1017), [BenchLM](https://benchlm.ai/hosts/openrouter), [OR pricing](https://openrouter.ai/pricing)
- In a 2026 field report, 2,415 agent turns across Kimi, DeepSeek and local Qwen 3.6 27B cost $76.77, against an estimated $1,272.77 if all had gone to GPT-5.5. The author's stack was OpenCode Go $10/mo, about $70 OpenRouter, and about $20/mo for local. — [Folkman](https://tylerfolkman.substack.com/p/i-tested-6-ai-models-across-3-providers)
- A Reddit user reported 136M DeepSeek tokens in a week for $2.43. This is anecdotal and likely cache-heavy. — [Reddit](https://www.reddit.com/r/hermesagent/comments/1ufjpa7/openrouter_vs_every_other_oauth_subscription/)
- Rental prices: RTX 5090 $0.41/hr (Vast) to $1.39/hr (RunPod); Hetzner GEX131 €1,499/mo. — [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai), [Hetzner](https://www.hetzner.com/dedicated-rootserver/gex131/)
- Hardware: Mac Studio M5 Max 128 GB $5,399; Ryzen AI Halo $3,999; DGX Spark $4,699–6,950. — sources in Q4

### Inferences (my calculations, not sourced figures)
- **Worked example, 20-person SMB:** about 60M input and 15M output tokens per month (RAG-heavy).
  - DeepSeek V4.1 Flash: 60×0.038 + 15×0.50 ≈ **$10/mo**.
  - Qwen3.8-27B: 60×0.15 + 15×1.88 ≈ **$37/mo** (+5.5%).
  - Embeddings via text-embedding-3-small cost pennies.
- **Local amortization over 36 months:**
  - Ryzen AI Halo $3,999 → about **$111/mo**.
  - Mac Studio M5 Max $5,399 → about **$150/mo**.
  - Power: about 174 W peak for the Mac, so roughly 40–125 kWh/mo depending on duty cycle (EGP tariff not retrieved).
- **Always-on cloud GPU:** an RTX 5090 runs 730 h × $0.41 ≈ **$300/mo** (Vast, no SLA) up to ≈ **$1,015/mo** (RunPod secure). Hetzner GEX131 costs about **€1,499/mo**.
- **Break-even:** local beats API on pure cost only above several hundred million tokens per month. The real drivers are PDPL compliance, offline resilience (see the Telecom Egypt DC fire) and Egyptian-dialect model choice (Karnak and Jais 3 are not on every API).

### Gaps
- EGP-denominated prices, Egyptian import duties on GPUs and Macs, and local electricity cost were not retrieved.
- No published case study of an Egyptian SMB running a local LLM was found.
