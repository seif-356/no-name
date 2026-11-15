# Local models and hosting: CACHE (weaker, older, marginal or unverified entries), Nov 2026

This file companions `local_models_hosting.md` and keeps entries that are outdated, superseded, too large or too small for an SMB, legally unclear, closed, or not verified this session, so nothing is lost.

**Verification tags.** "[V]" means a source page or search excerpt seen this session states the fact. "[K]" means the entry comes from background knowledge and gives only the canonical URL; its details were **not** re-checked in Nov 2026.

## Legacy and marginal Arabic-first or Arabic-tuned LLMs

### Takeaway
Most earlier Arabic models (Jais 1/30B, AceGPT, Noon, SILMA-9B, Fanar-1-9B, Falcon Arabic 7B) are superseded by Jais 3, Fanar 2, Karnak and Gemma 4. They are still usable as fallbacks or for low-resource experiments. Many OALL top-10 entries are anonymous community Qwen2.5-72B fine-tunes, so their production fitness is unknown.

### Cited Findings

| # | Model | URL | License | Size | Why cached / notes |
|---|---|---|---|---|---|
| C1 | Jais-30b-chat-v3 (Inception) | [HF](https://huggingface.co/inceptionai/jais-30b-v3) | Apache 2.0 | 30B; 126B Arabic + 251B English + 50B code tokens | PromptQuorum still ranks it #1 Arabic local model, but Jais 2 and 3 supersede it. ~18–20 GB Q4 [V] [PromptQuorum](https://www.promptquorum.com/local-llms/best-arabic-local-llms-2026) |
| C2 | Jais-13b-chat | [HF](https://huggingface.co/inceptionai/jais-13b-chat) | Apache 2.0 | 13B | Jais 30B beats it in 96% of human evaluations [V] |
| C3 | Jais family "jais-family-*" / "jais-adapted-*" (590M–70B, 2024) | [HF inceptionai](https://huggingface.co/inceptionai) | Apache 2.0 | 0.6–70B | 2024 generation [K] |
| C4 | Falcon Arabic 7B (TII, May 2025) | [TII news](https://www.tii.ae/news/middle-easts-leading-ai-powerhouse-tii-launches-two-new-ai-models-falcon-arabic-first-arabic) | TII Falcon License | 7B (Falcon 3 base) | Superseded by Falcon-H1-Arabic [V] [TecnoStack](https://tecnostack.com/en/blog/arabic-llm-comparison-falcon-allam-jais-fanar), [HF blog](https://huggingface.co/blog/tiiuae/falcon-arabic) |
| C5 | Falcon-H1 7B / 34B / 1.5B Deep / 3B (base family) | [HF tiiuae](https://huggingface.co/tiiuae) | Falcon LLM License | 1.5–34B | Weak on Arabic in the Jais 3 table (7B 52.0, 34B 62.6, 1.5B Deep 41.6, 3B 44.6) [V] [IFM](https://ifm.ai/blog/jais3/) |
| C6 | Falcon 40B (2023) | [HF](https://huggingface.co/tiiuae/falcon-40b) | Apache 2.0 | 40B | Old; mentioned on Reddit for Arabic [V] [Reddit](https://www.reddit.com/r/LocalLLM/comments/1htbjii/best_arabic_model/) |
| C7 | Fanar-1-9B-Instruct (QCRI) | [HF](https://huggingface.co/QCRI/Fanar-1-9B-Instruct) | check | 9B | Legacy; behind Falcon-H1-Arabic 7B on OALL per TII [V] |
| C8 | ALLaM 34B (HUMAIN Chat) | [arXiv 2508.17378](https://arxiv.org/abs/2508.17378) | Closed (enterprise via HUMAIN) | 34B | No public weights [V] |
| C9 | ALLaM-2-7B-Instruct on Azure AI | [PromptQuorum](https://www.promptquorum.com/local-llms/best-arabic-local-llms-2026) | Azure terms | 7B | Hosted since Sep 2024 [V] |
| C10 | humain-m3 (HUMAIN + MiniMax) | [aijourn](https://aijourn.com/humain-unveils-humain-m3-a-frontier-arabic-language-model-developed-by-minimax-in-research-preview-on-humain-node/) | MiniMax Community License (weights *promised*) | 428B MoE, 1T+ Arabic tokens | Preview only, no weights as of 21 Oct 2026 [V] |
| C11 | Hala 1.2B | [IFM table](https://ifm.ai/blog/jais3/) | check | 1.2B | Arabic avg 36.2 (Jais table) [V] |
| C12 | Cohere Tiny Aya Global | [IFM table](https://ifm.ai/blog/jais3/) | check (CC-BY-NC likely) | small | Arabic avg 47.3 (Jais table) [V: score] |
| C13 | IBM Granite 4.0 3B (Ar) | [IFM table](https://ifm.ai/blog/jais3/) | Apache 2.0 [K] | 3B | Arabic avg 47.9 (Jais table) [V: score] |
| C14 | D2IL-Arabic-Qwen2.5-72B-Instruct v0.1 / v0.2 | [OALL](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard) | Qwen license | 72B | OALL #2/#3 (75.86 / 75.85) [V] |
| C15 | Lina-Z/qwen_arabic_ft; Lina-Z/arabic_llm_test | [OALL mirror](https://benchmarklist.com/benchmarks/open_arabic_llm_leaderboard/) | unknown | 72B | 75.59 / 74.84; anonymous fine-tunes [V] |
| C16 | rombodawg/Rombos-LLM-V2.5-Qwen-72b | same | Qwen | 72B | 75.59 [V] |
| C17 | Sakalti/Ultiima-72B | same | unknown | 72B merge | 75.51 [V] |
| C18 | tunny/Arabic_Qwen2.5_72B_instruct_finetune_0.1 | same | unknown | 72B | 75.49 [V] |
| C19 | AbdulmalekDS/qwen72b-ar-lora | same | unknown | 72B LoRA | 75.49; AraTrust 91.4 [V] |
| C20 | MaziyarPanahi/calme-2.1 / 2.2-qwen2.5-72b | [OALL](https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard) | Qwen | 72B | 73.1 / 72.72 [V] |
| C21 | Qwen2.5-72B-Instruct (base of most OALL leaders) | [HF](https://huggingface.co/Qwen/Qwen2.5-72B-Instruct) | Qwen license | 72B | 2024 generation [K] |
| C22 | AceGPT (FreedomIntelligence / CUHK-SZ) v1/v2, 7B–70B | [HF](https://huggingface.co/FreedomIntelligence) | Llama-based | 7–70B | Legacy Arabic Llama 2 adaptation [K] |
| C23 | SILMA-9B-Instruct v1.0 (SILMA AI) | [HF](https://huggingface.co/silma-ai/SILMA-9B-Instruct-v1.0) | Gemma terms | 9B (Gemma 2) | Legacy; SILMA also runs ABL leaderboard and an Arabic model list [K] [SILMA list](https://silma.ai/arabic-large-language-models) |
| C24 | SILMA Kashif (RAG-focused Arabic) | [HF silma-ai](https://huggingface.co/silma-ai) | check | 2B | RAG-tuned small model [K] |
| C25 | Noon (Naseej, Saudi) | [HF](https://huggingface.co/Naseej/noon-7b) | check | 7B (BLOOM) | 2023, legacy [K] |
| C26 | Command R7B Arabic (Cohere) | [HF](https://huggingface.co/CohereForAI/c4ai-command-r7b-arabic-02-2025) | CC-BY-NC | 7B | Arabic-specialized, non-commercial weights [K] |
| C27 | Command R / R+ (Cohere) | [HF](https://huggingface.co/CohereForAI) | CC-BY-NC | 35B / 104B | Arabic among supported languages; NC license [K] |
| C28 | Command A (Cohere, 111B) | [HF](https://huggingface.co/CohereForAI/c4ai-command-a-03-2025) | CC-BY-NC | 111B | Superseded by Command A+ [K] |
| C29 | Aya Expanse 8B / 32B (Cohere For AI) | [HF](https://huggingface.co/CohereForAI/aya-expanse-32b) | CC-BY-NC | 8/32B | 23 languages incl. Arabic [K] |
| C30 | Aya Vision 8B/32B | [HF](https://huggingface.co/CohereForAI) | CC-BY-NC | — | Multimodal multilingual [K] |
| C31 | Llama 3.2 1B / 3B Instruct | [HF](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct) | Llama 3.2 Community | 1–3B | Listed in SILMA's Arabic list; weak Arabic [V] [HF blog](https://huggingface.co/blog/silma-ai/arabic-llm-models-list) |
| C32 | Llama 3.1 8B / 70B / 405B | [HF](https://huggingface.co/meta-llama) | Llama 3.1 Community | — | Superseded [K] |
| C33 | AraGPT2 / AraT5 / AraBERT (aubmindlab) | [HF](https://huggingface.co/aubmindlab) | various | small | Pre-LLM Arabic NLP; AraBERT useful as an encoder [K] |
| C34 | CAMeLBERT (NYU Abu Dhabi) | [HF](https://huggingface.co/CAMeL-Lab) | MIT/Apache | 110M | Dialect-aware encoders, incl. Egyptian [K] |
| C35 | MARBERT / AraELECTRA (UBC) | [HF](https://huggingface.co/UBC-NLP) | check | small | Dialectal Arabic encoders [K] |
| C36 | Mistral Saba (24B, Arabic/South Asian) | [mistral.ai](https://mistral.ai/news/mistral-saba) | API / license-on-request | 24B | Arabic-focused; weights not openly downloadable [K] |
| C37 | Qwen3-8B | [HF](https://huggingface.co/Qwen/Qwen3-8B) | Apache 2.0 | 8B | PromptQuorum's #3 for consumer Arabic; Qwen3-235B HELM Arabic 0.786; superseded by Qwen3.5 [V] |
| C38 | Qwen3-235B-A22B / 30B-A3B / 32B / 14B / 4B | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | — | Previous gen [K; 235B HELM score V] |
| C39 | QwQ-32B | [HF](https://huggingface.co/Qwen/QwQ-32B) | Apache 2.0 | 32B | Reasoning, older [V] [xigh](https://github.com/xigh/open-weight-models) |
| C40 | Qwen3-Coder-480B / Qwen3-Coder-Next | [HF Qwen](https://huggingface.co/Qwen) | Apache 2.0 | 480B/35B | Coding, not Arabic-focused [V] |
| C41 | Qwen3.7 Max (API) | [BenchLM](https://benchlm.ai/hosts/openrouter) | closed | — | $1.48/$4.42 per M [V] |

## Superseded or too-large general open-weight LLMs

| # | Model | URL | License | Size / ctx | Notes |
|---|---|---|---|---|---|
| C42 | Gemma 3 27B | [HF](https://huggingface.co/google/gemma-3-27b-it) | Gemma License | 27B, 128K | 14 GB INT4; replaced by Gemma 4; Fanar 2 base [V] [Onyx](https://onyx.app/self-hosted-llm-leaderboard) |
| C43 | Gemma 3 12B | [HF](https://huggingface.co/google/gemma-3-12b-it) | Gemma License | 12B | 8 GB INT4 [V] |
| C44 | Gemma 3n / Gemma 3 4B / 1B | [HF](https://huggingface.co/google) | Gemma | small | [K] |
| C45 | DeepSeek-R1 | [HF](https://huggingface.co/deepseek-ai/DeepSeek-R1) | MIT | 671B/37B, 128K | 351 GB INT4; replaced by V4-Pro [V] |
| C46 | DeepSeek-V3.2 / V3.1 / V3-0324 | [HF](https://huggingface.co/deepseek-ai) | MIT | 685B | Previous gen [V] |
| C47 | DS-R1-Distill-Llama-70B | [HF](https://huggingface.co/deepseek-ai) | MIT | 70B | 36 GB INT4 [V] |
| C48 | DS-R1-Distill-Qwen-32B / 14B | [HF](https://huggingface.co/deepseek-ai) | MIT | 32B/14B | 17 GB / 8 GB INT4 [V] |
| C49 | GLM-5.2 | [HF](https://huggingface.co/zai-org/GLM-5.2) | MIT | 753B, 1M | NIST CAISI: similar to GPT-5.2 [V] [Morph](https://www.morphllm.com/best-open-source-llm) |
| C50 | GLM-5.1 / GLM-5 | [BenchLM](https://benchlm.ai/models/glm-5) | MIT | — | Superseded [V] |
| C51 | GLM-4.7 / GLM-4.6 | [HF zai-org](https://huggingface.co/zai-org) | MIT | 355B/32B | [V] |
| C52 | GLM-4.5-Air | [HF](https://huggingface.co/zai-org/GLM-4.5) | MIT | 106B/12B | Fits 64–128 GB at Q4 [V] |
| C53 | Kimi K2.6 / K2.5 / K2 Thinking / K2 | [HF moonshotai](https://huggingface.co/moonshotai) | Modified MIT | 1T/32B | Kimi K2.6 cheap via API for agents [V] |
| C54 | Kimi K2.7 Code | [Kimi platform](https://platform.kimi.ai/docs/pricing/chat) | Modified MIT | 1T, 262K | Coding fork [V] |
| C55 | MiniMax M2 / M2.7 / M3.1 Flash | [HF MiniMaxAI](https://huggingface.co/MiniMaxAI) | MiniMax license | — | [V] |
| C56 | Mistral Large 3 / Mistral Large 4 | [BenchLM](https://benchlm.ai/models/mistral-large-4) | Apache 2.0 (L3, per Context Studios) | — | Large 4 has 1M ctx [V] |
| C57 | Mistral Small 3.1 / 3.2 (24B) | [HF](https://huggingface.co/mistralai) | Apache 2.0 | 24B | Superseded by Small 4 [V] |
| C58 | Devstral-2-123B | [Onyx](https://onyx.app/self-hosted-llm-leaderboard) | Modified MIT | 123B | Coding [V] |
| C59 | Magistral (Mistral reasoning) | [HF](https://huggingface.co/mistralai) | Apache 2.0 | 24B | Merged into Medium 3.5 [V] |
| C60 | Llama 4 Behemoth / Llama 3.3 405B | [Meta](https://ai.meta.com) | — | — | Not practical [K] |
| C61 | Microsoft Phi-4 / Phi-4-mini / Phi-4-multimodal | [HF](https://huggingface.co/microsoft/phi-4) | MIT | 14B / 3.8B | Weak Arabic historically [K; listed on Onyx V] |
| C62 | NVIDIA Nemotron 3 Super 120B-A12B | [NVIDIA build](https://build.nvidia.com) | OpenMDW | 120B/12B | On OpenRouter free list [V] |
| C63 | Nemotron 3.5 Bolt 74B-A9B | [HF nvidia](https://huggingface.co/nvidia) | OpenMDW | 74B/9B | [V] |
| C64 | Nemotron Ultra 253B (older) | [Onyx](https://onyx.app/self-hosted-llm-leaderboard) | NVIDIA Open | 253B | [V] |
| C65 | Hermes 4-70B (Nous) | [HF](https://huggingface.co/NousResearch/Hermes-4-70B) | Llama Community | 70B | [V] |
| C66 | InternVL3-78B | [HF](https://huggingface.co/OpenGVLab/InternVL3-78B) | Apache 2.0 | 78B VLM | Could OCR Arabic docs; unverified [V] |
| C67 | Krafton Raon-1-mini-preview | [HF](https://huggingface.co/KRAFTON/Raon-1-mini-preview) | Apache 2.0 (gated) | 28.8B/4.3B | [V] |
| C68 | Tencent Hunyuan Hy3 | [Onyx](https://onyx.app/self-hosted-llm-leaderboard) | — | — | [V] |
| C69 | StepFun Step 5 Preview (API) | [BenchLM](https://benchlm.ai/hosts/openrouter) | — | — | $1.00/$2.70 [V] |
| C70 | Thinking Machines Inkling / Inkling-Small / Inkling 2 Small | [BenchLM](https://benchlm.ai/models/inkling-small) | open weight | — | Inkling 2 Small free on OpenRouter [V] |
| C71 | Arcee, Dots Studio, Ornith AI, InternScience, Prism ML, SparkLLM, LiquidAI open models | [BenchLM](https://benchlm.ai/best/open-source) | various | — | Names only, from the 94-model ranking [V] |
| C72 | OLMo / Pythia (fully open source) | [Context Studios](https://www.contextstudios.ai/guides/best-open-weight-llms-2026) | Apache 2.0 | — | Research-grade [V] |
| C73 | Qwen3 VL 235B | [geotoolbox](https://geotoolbox.ai/blog/best-open-source-llms) | Apache 2.0 | 235B | [V] |

## Marginal embeddings and rerankers

| # | Model | URL | License | Notes |
|---|---|---|---|---|
| C74 | gte-Qwen2-7B-instruct | [HF](https://huggingface.co/Alibaba-NLP/gte-Qwen2-7B-instruct) | Apache 2.0 | Superseded by Qwen3-Embedding [K] |
| C75 | LaBSE (Google) | [HF](https://huggingface.co/sentence-transformers/LaBSE) | Apache 2.0 | Bitext mining; older [K] |
| C76 | paraphrase-multilingual-mpnet-base-v2 / MiniLM-L12-v2 | [HF](https://huggingface.co/sentence-transformers) | Apache 2.0 | Tiny, weak retrieval [K] |
| C77 | SILMA embedding matryoshka v0.1 | [HF silma-ai](https://huggingface.co/silma-ai) | check | Arabic sentence embeddings [K] |
| C78 | ARM-V1 (Omartificial Arabic reranker) | [YouTube](https://www.youtube.com/watch?v=uIzaA-BEE9Q) | check | Mentioned as an Arabic reranker [V: mention] |
| C79 | OmarAI multimodal 2048-dim Arabic embedding | [omarai.me](https://www.omarai.me/embeddings) | check | Text/image/video shared space [V: snippet] |
| C80 | mxbai-embed-large / mxbai-rerank (Mixedbread) | [HF](https://huggingface.co/mixedbread-ai) | Apache 2.0 | Mostly English [K] |
| C81 | Nomic embed-text v1.5 | [HF](https://huggingface.co/nomic-ai) | Apache 2.0 | English [K] |
| C82 | "Harrier" (74.3 multilingual MTEB v2) | [ayautomate](https://www.ayautomate.com/blog/best-embedding-models) | unknown | Vendor and details not captured [V: mention] |
| C83 | Cohere embed-multilingual-v3 / rerank-multilingual-v3 | [cohere.com](https://cohere.com) | API | Older Cohere generation [K] |
| C84 | ColBERT / Jina-ColBERT-v2 multilingual | [HF](https://huggingface.co/jinaai/jina-colbert-v2) | CC-BY-NC | Late-interaction [K] |

## Marginal inference and serving tools

| # | Tool | URL | License | Notes |
|---|---|---|---|---|
| C85 | text-generation-webui (oobabooga) | [GitHub](https://github.com/oobabooga/text-generation-webui) | AGPL-3.0 | Hobbyist UI [K] |
| C86 | GPT4All (Nomic) | [GitHub](https://github.com/nomic-ai/gpt4all) | MIT | Desktop; slower updates [K] |
| C87 | MLC-LLM | [GitHub](https://github.com/mlc-ai/mlc-llm) | Apache 2.0 | WebGPU / mobile [K] |
| C88 | Aphrodite Engine | [GitHub](https://github.com/aphrodite-engine/aphrodite-engine) | AGPL-3.0 | vLLM fork [K] |
| C89 | ik_llama.cpp | [GitHub](https://github.com/ikawrakow/ik_llama.cpp) | MIT | Faster CPU/MoE quant fork [K] |
| C90 | ExLlamaV2 | [GitHub](https://github.com/turboderp-org/exllamav2) | MIT | Superseded by V3 [K] |
| C91 | OpenVINO GenAI (Intel) | [GitHub](https://github.com/openvinotoolkit/openvino.genai) | Apache 2.0 | Intel CPU/iGPU/Arc [K] |
| C92 | ONNX Runtime GenAI | [GitHub](https://github.com/microsoft/onnxruntime-genai) | MIT | Windows/DirectML [K] |
| C93 | Llama Stack (Meta) | [GitHub](https://github.com/meta-llama/llama-stack) | MIT | Framework [K] |
| C94 | BentoML / OpenLLM | [GitHub](https://github.com/bentoml/OpenLLM) | Apache 2.0 | Packaging [K] |
| C95 | Ray Serve | [docs](https://docs.ray.io/en/latest/serve/) | Apache 2.0 | Overkill for SMB [K] |
| C96 | llm-d / vLLM production-stack | [GitHub](https://github.com/llm-d/llm-d) | Apache 2.0 | Kubernetes-scale [K] |
| C97 | Petals | [GitHub](https://github.com/bigscience-workshop/petals) | MIT | P2P inference, stale [K] |
| C98 | RamaLama (Red Hat) | [GitHub](https://github.com/containers/ramalama) | MIT | Container-native runner [K] |
| C99 | Docker Model Runner | [docs](https://docs.docker.com/ai/model-runner/) | Docker terms | llama.cpp in Docker Desktop [K] |
| C100 | Msty | [msty.app](https://msty.app) | Proprietary freemium | Desktop chat [K] |
| C101 | Portkey / Helicone / OpenRouter-style gateways | [portkey.ai](https://portkey.ai) | Mixed | LiteLLM alternatives [K] |
| C102 | NVIDIA Dynamo | [GitHub](https://github.com/ai-dynamo/dynamo) | Apache 2.0 | Data-center disaggregated serving [K] |

## Marginal hardware and hosting

| # | Option | URL | Notes |
|---|---|---|---|
| C103 | RTX 4090 (24 GB) | [PromptQuorum](https://www.promptquorum.com/local-llms/cloud-gpu-rental-comparison-2026) | Rent $0.34–0.69/hr RunPod, $0.08–0.59 Vast; used-market purchase price not retrieved [V] |
| C104 | RTX 4060 8GB / RTX 3060 12GB | [PromptQuorum](https://www.promptquorum.com/local-llms/best-arabic-local-llms-2026) | Enough for Falcon-H1-Arabic 7B / 7–8B models at Q4 (~5 GB) [V] |
| C105 | NVIDIA L4 (24 GB) cloud | [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai) | $0.10/hr Vast, $0.69 RunPod [V] |
| C106 | L40 / L40S / A40 / A6000 / RTX 6000 Ada (48 GB) | [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai) | $0.36–1.09/hr [V] |
| C107 | H100 NVL / H200 / B200 / B300 | [gpus.io](https://gpus.io/en/providers/compare/runpod-vs-vast-ai) | $1.60–9.94/hr; overkill for SMB [V] |
| C108 | Hetzner GEX130 (RTX 6000 Ada 48 GB, 2024) | [Reddit](https://www.reddit.com/r/hetzner/comments/1fo6igi/new_gpu_server_gex130/), [HN](https://news.ycombinator.com/item?id=41646163) | ~$940/mo in 2024 vs RunPod $670; likely superseded by GEX131 [V] |
| C109 | Framework Desktop / GMKtec EVO-X2 / other Strix Halo mini PCs | [frame.work](https://frame.work/desktop) | 128 GB Ryzen AI Max+ 395 boxes; 2026 prices not retrieved [K] |
| C110 | Intel Arc Pro B60 / B50 | [intel.com](https://www.intel.com) | Cheap 24 GB cards; software maturity uncertain [K] |
| C111 | AMD Radeon AI PRO R9700 (32 GB) | [amd.com](https://www.amd.com) | ROCm; unverified [K] |
| C112 | Modal / Replicate / Baseten | [modal.com](https://modal.com) | Serverless GPU; pricing not retrieved [K] |
| C113 | SambaNova / Hyperbolic / Nebius / Chutes | [nebius.com](https://nebius.com) | Open-model inference APIs; not priced [K] |
| C114 | Scaleway / OVHcloud GPU (EU) | [scaleway.com](https://www.scaleway.com) | EU alternatives to Hetzner [K] |
| C115 | AWS Bedrock / Google Vertex / Azure AI Foundry | [aws.amazon.com/bedrock](https://aws.amazon.com/bedrock) | Host open models; no Egypt region (Azure confirmed) [V for Azure] |
| C116 | Oracle Cloud (Jeddah/Riyadh), G42/Core42 cloud (UAE) | [core42.ai](https://www.core42.ai) | Gulf sovereign clouds; still cross-border for Egypt [K] |
| C117 | Paperspace (DigitalOcean) GPU droplets | [digitalocean.com](https://www.digitalocean.com) | [K] |
| C118 | OpenCode Go ($10/mo bundle) | [Folkman](https://tylerfolkman.substack.com/p/i-tested-6-ai-models-across-3-providers) | Access to Kimi, Qwen, DeepSeek, GLM; ~"$60 usage value" [V] |

### Inferences
- Nothing in this cache beats the main-file picks for an Egyptian SMB in Nov 2026. The useful fallbacks are C1 (Jais 30B) if Jais 3 tooling breaks, C37 (Qwen3-8B, very well supported in Ollama), and C104 (8–12 GB GPUs) for a sub-$500 pilot.

### Gaps
- All [K] items need license and version re-checks before use.
- AceGPT, Noon, SILMA-9B and Command R7B Arabic scores on current leaderboards were not retrieved.
