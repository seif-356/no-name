# Data Ingestion, Cleanup, Parsing, OCR, Dedup and Structuring Tools (Arabic-aware) — Raw Catalogue, Nov 2026

Scope: the "data cleanup and organizing" stage that sits before an AI company brain: getting messy business data in (documents, scans, websites, SaaS apps, WhatsApp), turning it into clean text/tables, deduplicating and resolving entities, normalizing Arabic, chunking, adding metadata/taxonomy/knowledge graphs, and embedding it for retrieval.

**How to read the tables**
- **OSS** = open source (Y), partly (P = open core / open code but restricted weights or paid tier), N = proprietary/hosted.
- **Arabic**: Y = documented or benchmarked on Arabic; P = partial / via a plug-in model / generic multilingual; N = no known support; ? = unknown.
- **Step** codes: INGEST (connectors/crawl), PARSE (doc to text/markdown), OCR, CLEAN (normalize/validate), DEDUP/ER (dedup and entity resolution), CHUNK, META (metadata/taxonomy/NER), KG (knowledge graph), EMBED (embeddings/rerank), SERVE (deliver answers e.g. WhatsApp), EVAL (benchmarks).
- **Src** column: a link means a fact in that row was confirmed in a source read this session. "K" means the row comes from prior knowledge (training data to mid-2026) plus the official URL; license/feature details marked K should be re-verified before a client commitment.
- Weaker, stale, niche or duplicate entries are in `data_ingestion_cleanup_cache.md`.

---

## 1. Document parsing and OCR (general + Arabic-specific)

### Takeaway
For Arabic business documents the 2026 evidence points to three tiers: (1) Arabic-specialised compact models (Baseer, Falcon-OCR-Arabic, Qari) and Gemini-class APIs lead on Arabic text and tables; (2) Azure Document Intelligence is the strongest classic cloud OCR on Arabic character accuracy; (3) the popular open-source PDF parsers (Docling, Marker, MinerU) are excellent pipeline shells but need an Arabic-capable OCR backend for scans. Licensing (Marker/Surya weights, MinerU extra terms, PyMuPDF AGPL) is a decider for a commercial service.

### Cited Findings

**Arabic OCR benchmark evidence**
- On Misraj-DocOCR (400 expert-checked Arabic pages, Apache-2.0 dataset on HF), lowest WER: Baseer 0.25, Gemini 2.5 Pro 0.37, Azure AI Document Intelligence 0.44, Dots.ocr 0.50, Nanonets 0.71, Qari 0.76, Qwen2.5-VL-32B 0.76, GPT-5 0.86; Baseer best table TEDS (66) vs Gemini 52, GPT-5 48, Azure 42. Azure has the lowest CER (0.27). Benchmark and Baseer both built by Misraj (disclosed conflict of interest). — [Misraj blog, Nov 15 2026](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026)
- Baseer = Qwen2.5-VL-3B-Instruct fine-tuned on 500k Arabic image-text pairs; deployable cloud, on-prem or sovereign (KSA); SaaS at baseerocr.com. On corrected KITAB-Bench (small, ~30 samples) Dots.ocr has best text scores and Nanonets beats Baseer on WER. — [Misraj blog](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026)
- Falcon-OCR-Arabic (TII, 270M params, Oct 6 2026): 81.9% text accuracy on an 11,974-sample, 15-category Arabic benchmark, #2 of 17 behind Gemini 3.5 Flash (84.3%); highest table TEDS (59.95%); #1 on official documents, admin forms, receipts and invoices; best dedicated OCR competitor (Chandra OCR 2) scored 61.7%. Weights NOT yet downloadable as of community comments (Oct–Nov 2026); base Falcon-OCR is Apache-2.0; playground at ocr.arabic.aidrc.tii.ae had reported errors. — [HF blog](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic)
- Qari-OCR: fine-tuned Qwen2-VL-2B for Arabic; v0.2 claimed open-source SOTA and beat Mistral OCR on its test set; v0.3 adds handwriting; models and datasets open. — [arXiv 2506.02295](https://arxiv.org/html/2506.02295v1); [HF collection](https://huggingface.co/collections/NAMAA-Space/qari-ocr-a-high-accuracy-model-for-arabic-optical-character)
- A community comment on HF's open-OCR blog reports olmOCR gave the best results on one user's Arabic corpus (anecdotal). — [HF blog](https://huggingface.co/blog/ocr-open-models)
- A HF forum thread names "Arabic-English-handwritten-OCR-v3" as the strongest practical starting point for handwritten Arabic forms (anecdotal). — [HF forum](https://discuss.huggingface.co/t/arabic-handwritten-vlm/180583)
- olmOCR-Bench: Chandra OCR 2 85.8 (Datalab self-reported), olmOCR 2 82.4 (Ai2). — [Docsumo](https://www.docsumo.com/blog/best-ocr-models); Mistral OCR 3 = 78 and Mistral OCR 2 = 72 on olmOCR-Bench per an aggregator marked "unverified" — [CodeSOTA](https://www.codesota.com/ocr)
- Datalab's olmOCR-Bench run: Marker 76.0, MinerU pipeline 72.7, Docling 50.3 (competitor-published). — [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers)

**Parser licensing / versions**
- Docling: MIT top to bottom, v2.111 mid-2026, broadest input coverage, pluggable OCR (Tesseract, RapidOCR), DoclingDocument JSON + native chunkers. — [Medium, A. Mangal](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1); [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers)
- Marker: model weights under modified OpenRAIL-M free only under a revenue/funding threshold — $5M per [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) and [file2markdown](https://www.file2markdown.ai/blog/marker-vs-mineru) vs ~$2M per [Medium](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1). Code license conflict: Apache-2.0 per LlamaIndex/file2markdown (marker-pdf v2.0.0) vs GPL-3.0 per Medium — likely relicensed; verify on repo.
- MinerU: v4.0 (4.0.12 on PyPI Oct 11 2026), ~81k stars, CPU by default (ONNX + llama.cpp VLM), four tiers (flash/basic/standard/advanced), outputs Markdown/HTML/LaTeX/DOCX/EPUB/JSON; "MinerU Open Source License" = Apache-2.0 + additional terms with a usage threshold; 109 languages, strong on CJK; "Arabic" leadership claim in Medium is unbenchmarked. — [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers); [file2markdown](https://www.file2markdown.ai/blog/marker-vs-mineru); [Medium](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1)
- PyMuPDF is AGPL (commercial license from Artifex); PyMuPDF4LLM gives Markdown/JSON without GPU. — [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers)

### Catalogue — document parsers / converters

| # | Name | URL | OSS | License | One-line description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 1 | Docling (IBM / LF AI) | https://github.com/docling-project/docling | Y | MIT | PDF/Office/HTML/audio to lossless DoclingDocument JSON/Markdown; layout + TableFormer; native chunkers | P (via OCR backend: Tesseract/EasyOCR/RapidOCR) | PARSE, OCR, CHUNK | [Medium](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1) |
| 2 | Granite-Docling / SmolDocling | https://huggingface.co/ibm-granite/granite-docling-258M | Y | Apache-2.0 (K) | Small VLM that emits DocTags for Docling's VLM pipeline | ? | PARSE, OCR | K |
| 3 | Marker (Datalab) | https://github.com/datalab-to/marker | P | Code Apache-2.0 or GPL-3.0 (conflict) + OpenRAIL-M weights w/ revenue cap | Fast PDF/Office/EPUB/image to Markdown/JSON/HTML/chunks; optional LLM pass | P (Surya, 90+ langs) | PARSE, OCR | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) |
| 4 | Surya / Surya OCR 2 (Datalab) | https://github.com/datalab-to/surya | P | GPL-3.0 code + restricted weights (K) | OCR, layout, reading order, table recognition, 90+ languages | Y (listed language; Arabic benchmark: weak vs Falcon) | OCR | [HF Falcon blog](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 5 | Chandra OCR 2 (Datalab) | https://www.datalab.to | P | Restricted weights (K) | Datalab's VLM OCR; 85.8 olmOCR-Bench (self-reported) | P (61.7% on Falcon Arabic bench, best dedicated non-Falcon) | OCR | [Docsumo](https://www.docsumo.com/blog/best-ocr-models); [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 6 | Datalab API / platform | https://www.datalab.to | N | Commercial | Hosted Marker/Chandra; runs OmniParseBench | P | PARSE, OCR | [Datalab](https://www.datalab.to/benchmarks) |
| 7 | MinerU (OpenDataLab) | https://github.com/opendatalab/MinerU | P | Apache-2.0 + extra terms ("MinerU Open Source License") | Local-first doc parsing platform, 4 tiers, doc library with citation locators, 9 output renderers | P (109 langs) | PARSE, OCR | [file2markdown](https://www.file2markdown.ai/blog/marker-vs-mineru) |
| 8 | MinerU2.5 / 2.5-Pro VLM | https://huggingface.co/opendatalab | P | As above | 1.2B VLM behind MinerU's accurate tier; tops OmniDocBench cohort | P | OCR | [Medium](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1) |
| 9 | Unstructured (OSS library) | https://github.com/Unstructured-IO/unstructured | Y | Apache-2.0 (K) | Partition 25+ file types into typed elements; chunk_by_title; Tesseract/Paddle OCR | P (OCR lang packs) | PARSE, CHUNK | K |
| 10 | Unstructured Platform | https://unstructured.io | N | Commercial | Hosted ETL: connectors, VLM partitioning, enrichment, embeddings | P | INGEST, PARSE | K |
| 11 | LlamaParse (LlamaIndex) | https://www.llamaindex.ai/llamaparse | N | Commercial | Agentic parser; vendor ranks it #1 for hard docs | P (multilingual) | PARSE, OCR | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) |
| 12 | Reducto | https://reducto.ai | N | Commercial | Enterprise doc parsing/extraction API with layout + VLM | ? | PARSE, OCR | K |
| 13 | Mistral OCR (2503 / OCR 2 / OCR 3) | https://mistral.ai/news/mistral-ocr/ | N | Commercial API | PDF/image OCR to interleaved text+images; Arabic showcased | Y (showcased; Qari v0.2 beat it on Qari test set) | OCR | [Mistral](https://mistral.ai/news/mistral-ocr/); [arXiv](https://arxiv.org/html/2506.02295v1) |
| 14 | Azure AI Document Intelligence | https://azure.microsoft.com/products/ai-services/ai-document-intelligence | N | Commercial | Read/layout/prebuilt invoice-receipt-ID models | Y (lowest CER 0.27 on Misraj-DocOCR) | OCR, PARSE | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 15 | Google Document AI | https://cloud.google.com/document-ai | N | Commercial | OCR, form/layout parser, custom extractors | Y (K: 200+ langs incl. Arabic) | OCR, PARSE | K |
| 16 | Gemini 2.5 Pro / 3.5 Flash (as OCR) | https://ai.google.dev | N | Commercial | General VLM; top Arabic text accuracy in both 2025–26 Arabic benchmarks | Y (#1 Falcon bench 84.3%; #2 WER Misraj) | OCR | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic); [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 17 | AWS Textract | https://aws.amazon.com/textract/ | N | Commercial | OCR, forms, tables, queries, expense/ID analysis | N (K: Arabic not in supported list as of mid-2026; verify) | OCR, PARSE | K |
| 18 | Nougat (Meta) | https://github.com/facebookresearch/nougat | P | MIT code, CC-BY-NC weights (K) | Academic PDF to Markdown/LaTeX | N | OCR | K |
| 19 | olmOCR / olmOCR 2 (Ai2) | https://github.com/allenai/olmocr | Y | Apache-2.0 (K) | VLM PDF linearizer; 82.4 olmOCR-Bench | P (anecdotally best on one Arabic corpus) | OCR | [Docsumo](https://www.docsumo.com/blog/best-ocr-models); [HF](https://huggingface.co/blog/ocr-open-models) |
| 20 | olmOCR-qari fine-tune | https://github.com/ma7dev/olmOCR-qari | Y | ? | Recipe to fine-tune olmOCR on QariOCR Arabic dataset | Y | OCR | [GitHub](https://github.com/ma7dev/olmOCR-qari) |
| 21 | GOT-OCR 2.0 | https://github.com/Ucas-HaoranWei/GOT-OCR2.0 | Y | Apache-2.0 (K) | Unified end-to-end OCR-2.0 model (text, tables, formulas, charts) | P | OCR | K |
| 22 | PaddleOCR / PP-OCRv5 | https://github.com/PaddlePaddle/PaddleOCR | Y | Apache-2.0 | Classic OCR toolkit with Arabic recognition models; 80+ langs | Y (Arabic rec model, K) | OCR | K |
| 23 | PaddleOCR-VL (1.5/1.6) | https://github.com/PaddlePaddle/PaddleOCR | Y | Apache-2.0 | 0.9B doc VLM that beats much larger VLMs on OmniDocBench | P (in Falcon Arabic comparison) | OCR, PARSE | [Roboflow](https://roboflow.com/blog/best-open-source-ocr-models); [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 24 | Tesseract 5 + `ara` traineddata | https://github.com/tesseract-ocr/tesseract | Y | Apache-2.0 | Classic LSTM OCR; Arabic `ara` and script/Arabic models in tessdata_best | Y (printed; weak on low-quality scans) | OCR | K |
| 25 | EasyOCR | https://github.com/JaidedAI/EasyOCR | Y | Apache-2.0 | 80+ language OCR incl. Arabic, PyTorch | Y | OCR | K |
| 26 | RapidOCR | https://github.com/RapidAI/RapidOCR | Y | Apache-2.0 | ONNX port of PaddleOCR, CPU-fast; Docling backend | P | OCR | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) |
| 27 | Qari-OCR (NAMAA) | https://huggingface.co/collections/NAMAA-Space/qari-ocr-a-high-accuracy-model-for-arabic-optical-character | Y | Open (license per model card; K Apache-2.0) | Qwen2-VL-2B fine-tuned for Arabic incl. tashkeel and handwriting (v0.3) | Y | OCR | [arXiv](https://arxiv.org/html/2506.02295v1) |
| 28 | Baseer (Misraj) | https://misraj.ai/en/products/baseer-ocr | N | Commercial (SaaS, on-prem, sovereign) | 3B Arabic doc OCR; best WER and TEDS on Misraj-DocOCR | Y | OCR, PARSE | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 29 | Falcon-OCR-Arabic (TII) | https://ocr.arabic.aidrc.tii.ae/ | P (weights unreleased) | Base Falcon-OCR Apache-2.0; Arabic weights TBD | 270M early-fusion OCR; #1 on Arabic forms/receipts/invoices | Y | OCR | [HF blog](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 30 | Falcon-OCR (base) | https://huggingface.co/tiiuae/Falcon-OCR | Y | Apache-2.0 | 270M English doc OCR (80.3 olmOCR, 88.64 OmniDocBench) | P (55.4% on Arabic bench) | OCR | [HF blog](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 31 | dots.ocr (rednote) | https://huggingface.co/rednote-hilab/dots.ocr | Y | MIT (K) | Multilingual layout+OCR VLM; best text on corrected KITAB-Bench | Y (WER 0.50 Misraj; 0.39 KITAB) | OCR, PARSE | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 32 | Nanonets-OCR-s / OCR2 | https://huggingface.co/nanonets | Y | Apache-2.0 (K) | Doc-to-markdown VLM with tables, checkboxes, signatures | Y (WER 0.71 Misraj) | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 33 | DeepSeek-OCR | https://huggingface.co/deepseek-ai/DeepSeek-OCR | Y | MIT (K) | Optical-compression doc OCR VLM | P (in Falcon Arabic comparison) | OCR | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 34 | GLM-OCR (Zhipu) | https://huggingface.co/zai-org | Y | ? (K MIT) | 0.9B doc OCR beating 235B VLMs on OmniDocBench | P | OCR | [Roboflow](https://roboflow.com/blog/best-open-source-ocr-models) |
| 35 | Ovis OCR 2 | https://huggingface.co/AIDC-AI | Y | ? | Dedicated OCR VLM in Falcon Arabic comparison | P | OCR | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 36 | Qwen2.5-VL / Qwen3-VL family | https://huggingface.co/Qwen | Y | Apache-2.0 / Qwen license (K) | General VLMs; base of Baseer & Qari; Qwen2.5-VL-32B WER 0.76 on Arabic | P | OCR | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 37 | Dolphin (ByteDance) | https://github.com/bytedance/Dolphin | Y | MIT | Two-stage analyze-then-parse doc VLM | ? | PARSE, OCR | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) |
| 38 | MarkItDown (Microsoft) | https://github.com/microsoft/markitdown | Y | MIT | Lightweight any-file to Markdown (Office, PDF text layer, HTML); optional Azure DI | P (text layer only) | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) |
| 39 | PyMuPDF / PyMuPDF4LLM (Artifex) | https://pymupdf.readthedocs.io/en/latest/pymupdf4llm/ | P | AGPL-3.0 / commercial | Fastest text-layer extraction; Markdown/JSON with bboxes | P (RTL text layer; no OCR without Tesseract) | PARSE | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) |
| 40 | pdfplumber | https://github.com/jsvine/pdfplumber | Y | MIT | Precise char/table extraction from born-digital PDFs | P (Arabic shaping/RTL issues common) | PARSE | [LlamaIndex](https://www.llamaindex.ai/insights/best-ai-pdf-parsers) |
| 41 | Apache Tika | https://tika.apache.org | Y | Apache-2.0 | 1,000+ format text/metadata extraction server; Tesseract OCR hook | P | PARSE, META | K |
| 42 | Pandoc | https://pandoc.org | Y | GPL-2.0+ | Universal document converter (DOCX/HTML/MD/LaTeX); RTL aware | Y (RTL) | PARSE | [jimmysong](https://jimmysong.io/blog/pdf-to-markdown-open-source-deep-dive/) |
| 43 | pdf-craft (oomol) | https://github.com/oomol-lab/pdf-craft | Y | ? (K AGPL) | Scanned book PDF to Markdown/EPUB using DeepSeek OCR | ? | OCR | [themenonlab](https://themenonlab.blog/blog/best-open-source-pdf-to-markdown-tools-2026) |
| 44 | Kreuzberg | https://github.com/kreuzberg-dev/kreuzberg | Y | MIT (K) | Polyglot doc-intelligence lib (Rust core), 50+ formats, OCR backends | P | PARSE, OCR | K |
| 45 | OpenDataLoader PDF | https://github.com/opendataloader-project/opendataloader-pdf | Y | MPL-2.0 (K) | PDF to Markdown/JSON for RAG; runs opendataloader-bench | ? | PARSE | [Nutrient](https://www.nutrient.io/blog/docling-alternatives/) |
| 46 | Nutrient (PSPDFKit) AI Document Processing | https://www.nutrient.io | N | Commercial | PDF SDK + extraction; publishes parser benchmarks | ? | PARSE | [Nutrient](https://www.nutrient.io/blog/docling-alternatives/) |
| 47 | Zerox (OmniAI) | https://github.com/getomni-ai/zerox | Y | MIT | PDF to images to VLM markdown; bring-your-own model | P (model dependent) | OCR | K |
| 48 | Unstract | https://github.com/Zipstack/unstract | P | AGPL-3.0 core + cloud | No-code LLM document extraction pipelines (LLMWhisperer parser) | P | PARSE, META | K |
| 49 | RAGFlow DeepDoc | https://github.com/infiniflow/ragflow | Y | Apache-2.0 | RAG engine with "deep document understanding" parser and templates | P | PARSE, CHUNK | K |
| 50 | ABBYY FineReader / Vantage | https://www.abbyy.com | N | Commercial | Veteran OCR/IDP suite with Arabic recognition | Y (K) | OCR, PARSE | K |
| 51 | Kraken + eScriptorium | https://github.com/mittagessen/kraken | Y | Apache-2.0 | Trainable OCR/HTR for RTL and historical scripts incl. Arabic | Y | OCR | K |
| 52 | Arabic-English-handwritten-OCR-v3 | https://discuss.huggingface.co/t/arabic-handwritten-vlm/180583 | Y | per model card | Community HF VLM for handwritten Arabic/English forms | Y | OCR | [HF forum](https://discuss.huggingface.co/t/arabic-handwritten-vlm/180583) |
| 53 | Arabic OCR Models Demo (oddadmix) | https://huggingface.co/spaces/oddadmix/Arabic-OCR-Models-Demos | Y | - | HF Space comparing two Arabic-first OCR models | Y | OCR, EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 54 | Docsumo | https://www.docsumo.com | N | Commercial | IDP for invoices/bank statements; publishes OCR model guide | ? | PARSE, OCR | [Docsumo](https://www.docsumo.com/blog/best-ocr-models) |
| 55 | Nanonets IDP platform | https://nanonets.com | N | Commercial | Hosted IDP workflows on top of Nanonets OCR | Y (model) | PARSE | K |
| 56 | file2markdown | https://www.file2markdown.ai | N | Commercial | Hosted any-file to Markdown + MCP server | ? | PARSE | [file2markdown](https://www.file2markdown.ai/blog/marker-vs-mineru) |
| 57 | Claude / GPT (as OCR) | https://www.anthropic.com | N | Commercial | Frontier VLMs; Claude Opus 5.5 79.2% Arabic text acc., GPT Astra 75.0% on Falcon bench; GPT-5 WER 0.86 on Misraj | Y | OCR | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic); [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |

### Catalogue — OCR / parsing benchmarks (for vendor selection)

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 58 | Misraj-DocOCR | https://huggingface.co/datasets/Misraj/Misraj-DocOCR | Y | Apache-2.0 | 400-page expert-verified Arabic doc OCR benchmark (WER/CER/TEDS/MARS) | Y | EVAL | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 59 | KITAB-Bench (+ Misraj-corrected) | https://github.com/mbzuai-oryx/KITAB-Bench | Y | ? | Arabic OCR & doc understanding benchmark (MBZUAI); reference errors found by Misraj | Y | EVAL | [Misraj](https://misraj.ai/en/blogs/best-arabic-ocr-models-2026) |
| 60 | OmniDocBench | https://github.com/opendatalab/OmniDocBench | Y | ? | Full-page doc parsing benchmark; Falcon integrated its Arabic set into it | P | EVAL | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) |
| 61 | olmOCR-Bench | https://github.com/allenai/olmocr | Y | Apache-2.0 | Unit-test style PDF OCR benchmark | N | EVAL | [Docsumo](https://www.docsumo.com/blog/best-ocr-models) |
| 62 | opendataloader-bench | https://www.nutrient.io/blog/pdf-extraction-benchmark-opendataloader-bench/ | Y | ? | Reading order / table TEDS benchmark (Docling 0.93 TEDS) | N | EVAL | [Nutrient](https://www.nutrient.io/blog/docling-alternatives/) |
| 63 | AIMultiple OCR benchmark (DeltOCR) | https://aimultiple.com/ocr-accuracy | - | - | Third-party OCR accuracy comparison incl. Mistral OCR 2/3 (Jul 2026) | ? | EVAL | [AIMultiple](https://aimultiple.com/ocr-accuracy) |

### Inferences
- For a Gulf/Arabic SMB pipeline, a pragmatic default is: born-digital PDFs/Office → Docling (MIT); scans/photos of Arabic forms, receipts, invoices → Gemini Flash-class API or Azure DI now, with Baseer (on-prem) or Falcon-OCR-Arabic (once weights ship) as sovereign options; Qari/dots.ocr as free self-hosted fallbacks.
- English-centric leaderboards (olmOCR-Bench, OmniDocBench English) do not predict Arabic performance: Chandra OCR 2 tops olmOCR-Bench but scores ~62% on the Arabic benchmark vs ~82% for Falcon-OCR-Arabic.
- Normalisation before scoring (tables to HTML, stripping tags) matters; reuse Misraj's method for internal acceptance tests.

### Gaps
- No independent (non-vendor) Arabic benchmark covering Baseer, Falcon-OCR-Arabic, Mistral OCR 3, Azure and Google together was found; each benchmark is authored by a model vendor.
- AWS Textract Arabic support status in Nov 2026 not verified this session.
- Marker code license (Apache vs GPL) conflicts between sources.
- Falcon-OCR-Arabic release date/license unknown.

---

## 2. Web and SaaS ingestion / connectors

### Takeaway
Two layers: web crawlers that turn sites into LLM-ready Markdown (Firecrawl, Crawl4AI, Jina Reader, Crawlee, Spider) and SaaS connector platforms (ELT tools like Airbyte/dlt/Meltano for bulk sync; unified APIs like Merge/Unified.to/Nango/Paragon; agent tool layers like Composio/Arcade). For a company-brain service, a sync-capable layer (Nango, Paragon Managed Sync, Merge, Airbyte, dlt) suits ingestion; pass-through/MCP layers suit live agent actions.

### Cited Findings
- Free/OSS crawler stars (Sep 24 2026): Crawl4AI Apache-2.0 84,189; Crawlee Apache-2.0 25,884 (+Python 9,548); Jina Reader Apache-2.0 12,038; Spider (Rust) MIT 2,737; Firecrawl AGPL-3.0 184,038 (self-host lacks Fire-engine); Scrapy BSD-3; ScrapeGraphAI MIT. — [usestring](https://usestring.ai/comparisons/firecrawl-alternatives)
- Firecrawl has an AGPL-3.0 open-source version plus hosted API; Crawl4AI is the usual self-hosted alternative; Tavily positions itself for search/discovery. — [Tavily](https://tavily.com/blog/7-best-firecrawl-alternatives-for-ai-agents-in-2026)
- Unified API landscape (Oct 2026): Unified.to 2,162 integrations / 38 categories, pass-through, hosted MCP, from $750/mo; Apideck 200+; Truto 800+ (from $999/connector/yr); Paragon 124 integrations, sync+workflow; Nango 1,000+ APIs, code-first, free tier; Merge 233 integrations (sync-and-store) plus Agent Handler (MCP); Kombo HR-only. (Vendor-authored.) — [Unified.to](https://unified.to/blog/top_merge_dev_alternatives_in_2026_a_guide_for_saas_and_ai_teams)
- Nango is open source, self-hostable (Enterprise), with coding-agent skill for building integrations. — [Nango](https://nango.dev/blog/4-most-popular-merge-dev-alternatives/)
- WorkOS frames Nango/Paragon as integration runtimes, Composio/Arcade as agent tool runtimes, Merge as both; Nango self-hosted free edition; Composio 1,000+ integrations. — [WorkOS](https://workos.com/blog/pipes-vs-nango-composio-arcade-paragon-and-merge)
- Paragon's own matrix: Unified.to MCP 20,000+ tools with PII stripping; Composio 500+ tools, no data syncs for ingestion. — [Paragon](https://www.useparagon.com/blog/integrations-for-ai-agents)
- Other named alternatives: CData Connect AI, Arcade.dev, Zapier MCP — [CData](https://www.cdata.com/blog/paragon-alternatives-embedded-integrations); Knit, StackOne — [Knit](https://getknit.dev/blog/best-unified-api-platforms-2026-a-guide-to-scaling-saas-integrations/), [Unified.to](https://unified.to/blog/best_unified_api_platforms_of_2026)
- Cognee ships 30+ data-source connectors (PDF, Slack, Notion, Drive). — [Cognee](https://www.cognee.ai/cognee-review-2026-graphrag-knowledge-graphs-and-agent-memory)

### Catalogue

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 64 | Firecrawl | https://github.com/firecrawl/firecrawl | P | AGPL-3.0 + hosted | Crawl/scrape/map/extract websites to Markdown/JSON; MCP | P (UTF-8 text) | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 65 | Crawl4AI | https://github.com/unclecode/crawl4ai | Y | Apache-2.0 | Async Playwright crawler with Markdown + CSS/XPath/LLM extraction | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 66 | Jina Reader | https://github.com/jina-ai/reader | Y | Apache-2.0 | `r.jina.ai/<url>` URL-to-Markdown; `s.jina.ai` search | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 67 | Crawlee (JS + Python) | https://github.com/apify/crawlee | Y | Apache-2.0 | Crawling/browser automation library with proxy rotation | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 68 | Scrapy | https://scrapy.org | Y | BSD-3 | Mature Python spider framework | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 69 | ScrapeGraphAI | https://github.com/ScrapeGraphAI/Scrapegraph-ai | Y | MIT | LLM graph-based scraping pipelines | P | INGEST | [usestring](https://usestring.ai/comparisons/firecrawl-alternatives) |
| 70 | Spider (spider-rs / spider.cloud) | https://github.com/spider-rs/spider | P | MIT + hosted | Rust high-speed crawler; hosted API | P | INGEST | [Spider](https://spider.cloud/blog/best-web-scraping-apis-for-ai-2026/) |
| 71 | Apify | https://apify.com | N (Crawlee OSS) | Commercial | Actor marketplace for scrapers (Google Maps, social, etc.) | P | INGEST | [digitalapplied](https://www.digitalapplied.com/blog/ai-web-scraping-tools-firecrawl-guide-2025) |
| 72 | Tavily | https://tavily.com | N | Commercial | Search/extract/crawl API for agents | P | INGEST | [Tavily](https://tavily.com/blog/7-best-firecrawl-alternatives-for-ai-agents-in-2026) |
| 73 | Bright Data | https://brightdata.com | N | Commercial | Proxies/unblocker/scraping datasets | P | INGEST | [Tavily](https://tavily.com/blog/7-best-firecrawl-alternatives-for-ai-agents-in-2026) |
| 74 | Airbyte | https://github.com/airbytehq/airbyte | P | ELv2 platform / MIT connectors (K) | ELT with 600+ connectors; PyAirbyte; file/unstructured sources | P | INGEST | K |
| 75 | dlt (dltHub) | https://github.com/dlt-hub/dlt | Y | Apache-2.0 | Python-first ELT library; REST API source; schema inference | P | INGEST, CLEAN | K |
| 76 | Meltano / Singer | https://github.com/meltano/meltano | Y | MIT | Singer-tap based ELT orchestration (now part of Matatika, K) | P | INGEST | K |
| 77 | Fivetran | https://www.fivetran.com | N | Commercial | Managed ELT, 700+ connectors | P | INGEST | K |
| 78 | Nango | https://github.com/NangoHQ/nango | P | Open source (ELv2 parts, K) | Code-first integrations: OAuth, syncs, webhooks, MCP; 1,000+ APIs | P | INGEST | [Nango](https://nango.dev/blog/4-most-popular-merge-dev-alternatives/) |
| 79 | Merge (Unified + Agent Handler) | https://www.merge.dev | N | Commercial | Normalized HRIS/ATS/CRM/accounting/ticketing/file-storage API + agent tools | P | INGEST | [Unified.to](https://unified.to/blog/top_merge_dev_alternatives_in_2026_a_guide_for_saas_and_ai_teams) |
| 80 | Unified.to | https://unified.to | N | Commercial | Pass-through unified API, 2,162 integrations, hosted MCP, DB sync | P | INGEST | [Unified.to](https://unified.to/blog/top_merge_dev_alternatives_in_2026_a_guide_for_saas_and_ai_teams) |
| 81 | Paragon | https://www.useparagon.com | N | Commercial | Embedded iPaaS: Managed Sync, ActionKit, Workflows | P | INGEST | [Paragon](https://www.useparagon.com/blog/integrations-for-ai-agents) |
| 82 | Composio | https://composio.dev | P | SDK open / platform commercial (K) | Agent tool calling + auth across ~1,000–1,600 toolkits | P | INGEST, SERVE | [WorkOS](https://workos.com/blog/pipes-vs-nango-composio-arcade-paragon-and-merge) |
| 83 | Arcade.dev | https://www.arcade.dev | N | Commercial | MCP runtime for production agents | P | INGEST | [WorkOS](https://workos.com/blog/pipes-vs-nango-composio-arcade-paragon-and-merge) |
| 84 | WorkOS Pipes | https://workos.com | N | Commercial | Managed OAuth/connection layer for SaaS apps | P | INGEST | [WorkOS](https://workos.com/blog/pipes-vs-nango-composio-arcade-paragon-and-merge) |
| 85 | Apideck | https://www.apideck.com | N | Commercial | Pass-through unified API + Vault UI | P | INGEST | [Unified.to](https://unified.to/blog/best_unified_api_platforms_of_2026) |
| 86 | Truto | https://truto.one | N | Commercial | Pass-through unified API w/ JSONata mapping | P | INGEST | [Truto](https://truto.one/blog/best-alternative-to-paragon-embedded-ipaas-for-ai-agent-integrations/) |
| 87 | Kombo | https://www.kombo.dev | N | Commercial | HR/ATS/payroll unified API | P | INGEST | [Nango](https://nango.dev/blog/4-most-popular-merge-dev-alternatives/) |
| 88 | Knit | https://getknit.dev | N | Commercial | Zero-storage unified API + MCP servers | P | INGEST | [Knit](https://getknit.dev/blog/best-unified-api-platforms-2026-a-guide-to-scaling-saas-integrations/) |
| 89 | StackOne | https://www.stackone.com | N | Commercial | Provider-native actions for agents | P | INGEST | [Unified.to](https://unified.to/blog/best_unified_api_platforms_of_2026) |
| 90 | CData Connect AI | https://www.cdata.com | N | Commercial | Hosted MCP/SQL access to 300+ sources | P | INGEST | [CData](https://www.cdata.com/blog/paragon-alternatives-embedded-integrations) |
| 91 | Zapier MCP | https://zapier.com/mcp | N | Commercial | Expose Zapier's 8,000-app actions to agents | P | INGEST | [CData](https://www.cdata.com/blog/paragon-alternatives-embedded-integrations) |
| 92 | n8n | https://github.com/n8n-io/n8n | P | Sustainable Use License | Self-hostable workflow automation with AI nodes; popular with WhatsApp bots | P | INGEST, SERVE | K |
| 93 | Activepieces | https://github.com/activepieces/activepieces | Y | MIT (core) | OSS Zapier alternative with MCP pieces | P | INGEST | K |
| 94 | Airweave | https://github.com/airweave-ai/airweave | Y | MIT (K) | Syncs SaaS apps into searchable vector/graph store for agents | P | INGEST, EMBED | K |
| 95 | Onyx (ex-Danswer) connectors | https://github.com/onyx-dot-app/onyx | P | MIT CE / EE commercial | Enterprise search with 40+ connectors (Drive, Slack, Confluence) | P | INGEST | K |
| 96 | LlamaHub / LlamaIndex readers | https://llamahub.ai | Y | MIT | Hundreds of data loaders | P | INGEST | K |
| 97 | LangChain document loaders | https://python.langchain.com | Y | MIT | Hundreds of loaders (Drive, Notion, WhatsApp chat loader exists, K) | P | INGEST | K |

### Inferences
- Firecrawl's AGPL matters only if the service modifies and offers it as a network service; Crawl4AI (Apache-2.0) is the permissive self-host choice.
- For SMB clients in the Gulf, common sources are Google Drive/OneDrive, Excel, WhatsApp, Zoho/Odoo, and local ERPs; check Odoo/Zoho coverage in Nango/Unified.to/Airbyte before choosing.

### Gaps
- Odoo, Zoho, Foodics, Qoyod, Daftra (popular in MENA) connector coverage not verified per platform.
- Exact current Airbyte and Nango licenses not re-verified this session.

---

## 3. WhatsApp data: ingesting chats and serving answers

### Takeaway
Use the official WhatsApp Business Cloud API (or a BSP) for production serving; unofficial Baileys/whatsapp-web.js-based servers (Evolution API, WAHA) are cheap and integrate easily with n8n/Chatwoot/Dify but carry ban and ToS risk. For historical chat ingestion, exported `.txt/.zip` chats are parsed with whatstk (Python), whatsapp-chat-parser (Node) or WhatsR (R, with anonymisation).

### Cited Findings
- Two architectures: browser automation (whatsapp-web.js, Venom, open-wa, WPPConnect) vs protocol implementation (Baileys; Evolution API, WAHA, WaSphere built on it). Baileys is MIT but depends on libsignal (GPLv3) — isolate behind a process boundary. Venom users advised to migrate. WAHA has free core + paid tier and can switch engines. — [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/)
- Evolution API supports Baileys mode and the official WhatsApp Cloud API, with integrations to Typebot, Chatwoot, Dify, OpenAI, RabbitMQ, Kafka, SQS, S3/MinIO. — [GitHub](https://github.com/evolution-foundation/evolution-api)
- Baileys mode operates outside WhatsApp business ToS and can get numbers banned; Cloud API costs money but is sanctioned. — [oncloudapi](https://oncloudapi.com/blogs/evolution-api-vs-whatsapp-cloud-api-ban-risk-business-safety); [runxbuild](https://www.runxbuild.com/blog/evolution-api/)
- Baileys connects over WebSocket, no browser. — [baileys.wiki](https://baileys.wiki/)
- Chat export parsers: whatstk (pandas DataFrame from .txt or iOS .zip, CSV CLI) — [GitHub](https://github.com/lucasrodes/whatstk); Pustur/whatsapp-chat-parser (Node) — [GitHub](https://github.com/Pustur/whatsapp-chat-parser); mazen160/whatsapp-chat-parser (Python) — [GitHub](https://github.com/mazen160/whatsapp-chat-parser); WhatsR (R, parse + anonymize) — [WhatsR](https://gesiscss.github.io/WhatsR/); whatsapp-chat-to-pdf — [GitHub](https://github.com/generalistprogrammer/whatsapp-chat-to-pdf); AbhijeetKrishnan/whatsapp-parser to CSV — [GitHub](https://github.com/AbhijeetKrishnan/whatsapp-parser)

### Catalogue

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 98 | WhatsApp Business Cloud API (Meta) | https://developers.facebook.com/docs/whatsapp/cloud-api | N | Meta terms, per-conversation/message pricing | Official API for sending/receiving business messages, templates, media, webhooks | Y | SERVE, INGEST (live) | [oncloudapi](https://oncloudapi.com/blogs/evolution-api-vs-whatsapp-cloud-api-ban-risk-business-safety) |
| 99 | Evolution API | https://github.com/evolution-foundation/evolution-api | Y | Apache-2.0 (K) | Self-hosted REST WhatsApp server (Baileys or Cloud API) w/ Chatwoot/Typebot/Dify/n8n | Y | SERVE, INGEST | [GitHub](https://github.com/evolution-foundation/evolution-api) |
| 100 | WAHA (WhatsApp HTTP API) | https://waha.devlike.pro | P | Apache-2.0 core + WAHA Plus paid (K) | HTTP API over swappable engines (WEBJS, NOWEB/Baileys, GOWS) | Y | SERVE, INGEST | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) |
| 101 | Baileys (WhiskeySockets) | https://github.com/WhiskeySockets/Baileys | Y | MIT (+ GPLv3 libsignal dep) | TypeScript WhatsApp multi-device protocol library | Y | SERVE, INGEST | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) |
| 102 | whatsapp-web.js | https://github.com/pedroslopez/whatsapp-web.js | Y | Apache-2.0 | Puppeteer-driven WhatsApp Web client library | Y | SERVE, INGEST | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) |
| 103 | WPPConnect | https://github.com/wppconnect-team/wppconnect | Y | LGPL-3.0 (K) | Browser-automation WhatsApp library + server | Y | SERVE | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) |
| 104 | WaSphere | https://wasphere.com | Y | MIT | Baileys-based WhatsApp server (smaller community) | Y | SERVE | [WaSphere](https://wasphere.com/blog/open-source-whatsapp-api-landscape-2026/) |
| 105 | whatsmeow | https://github.com/tulir/whatsmeow | Y | MPL-2.0 (K) | Go WhatsApp multi-device library (used by WAHA GOWS, mautrix bridge) | Y | SERVE, INGEST | K |
| 106 | Chatwoot | https://github.com/chatwoot/chatwoot | P | MIT core + EE | Open-source omnichannel inbox incl. WhatsApp; agent handoff | Y (RTL UI) | SERVE | [GitHub](https://github.com/evolution-foundation/evolution-api) |
| 107 | Typebot | https://github.com/baptisteArno/typebot.io | P | FSL/AGPL (K) | Chatbot builder that plugs into Evolution API | Y | SERVE | [GitHub](https://github.com/evolution-foundation/evolution-api) |
| 108 | Dify | https://github.com/langgenius/dify | P | Dify OSS license (Apache-based w/ conditions) | LLM app/RAG platform; Evolution API integration | Y | SERVE, CHUNK | [GitHub](https://github.com/evolution-foundation/evolution-api) |
| 109 | Twilio WhatsApp | https://www.twilio.com/whatsapp | N | Commercial BSP | Official WhatsApp via Twilio APIs | Y | SERVE | K |
| 110 | 360dialog | https://www.360dialog.com | N | Commercial BSP | Low-markup official WhatsApp API BSP | Y | SERVE | K |
| 111 | Unifonic | https://www.unifonic.com | N | Commercial BSP (KSA) | MENA CPaaS with WhatsApp, Arabic-first | Y | SERVE | K |
| 112 | Infobip / Gupshup / Wati / Respond.io | https://www.infobip.com | N | Commercial | Other official BSPs / WhatsApp inboxes widely used in MENA | Y | SERVE | K |
| 113 | whatstk | https://github.com/lucasrodes/whatstk | Y | GPL-3.0 (K) | Parse WhatsApp exports (.txt / iOS .zip) into pandas; CSV CLI | P (UTF-8; date-format detection) | INGEST, CLEAN | [GitHub](https://github.com/lucasrodes/whatstk) |
| 114 | whatsapp-chat-parser (Pustur, Node) | https://github.com/Pustur/whatsapp-chat-parser | Y | MIT (K) | Parse exported chat strings into message objects | P | INGEST | [GitHub](https://github.com/Pustur/whatsapp-chat-parser) |
| 115 | whatsapp-chat-parser (mazen160, Python) | https://github.com/mazen160/whatsapp-chat-parser | Y | ? | Python parser returning author/message/timestamp | P | INGEST | [GitHub](https://github.com/mazen160/whatsapp-chat-parser) |
| 116 | WhatsR (GESIS) | https://gesiscss.github.io/WhatsR/ | Y | GPL (K) | R package: parse, anonymize, visualize exports | P | INGEST, CLEAN | [WhatsR](https://gesiscss.github.io/WhatsR/) |
| 117 | chat-miner | https://github.com/joweich/chat-miner | Y | MIT (K) | Parse WhatsApp/Telegram/Signal/Messenger exports to DataFrames | P | INGEST | K |
| 118 | LangChain WhatsAppChatLoader | https://python.langchain.com | Y | MIT | Loader for exported WhatsApp chats into Documents | P | INGEST | K |
| 119 | OpenAI Whisper / faster-whisper | https://github.com/SYSTRAN/faster-whisper | Y | MIT | Transcribe WhatsApp voice notes (Arabic incl. dialects, variable quality) | Y | INGEST | K |
| 120 | Falcon ASR (TII) | https://huggingface.co/blog/tiiuae/falcon-asr | ? | ? | TII ASR released Oct 7 2026 (Arabic focus likely) | Y? | INGEST | [HF](https://huggingface.co/blog/tiiuae/falcon-ocr-arabic) (listed) |
| 121 | Open Universal Arabic ASR Leaderboard | https://huggingface.co/spaces/elmresearchcenter/open_universal_arabic_asr_leaderboard | Y | - | Multi-dialect Arabic ASR leaderboard to pick a voice-note transcriber | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |

### Inferences
- Arabic WhatsApp exports include RTL marks (U+200E/U+200F), Arabic-Indic digits and locale-specific date formats; parser regexes need testing on Arabic-locale phones (inferred; not tested this session).
- Voice notes are a large share of Gulf WhatsApp business traffic (common observation, not sourced); an ASR step belongs in the ingestion pipeline.

### Gaps
- No source found comparing parser robustness on Arabic-locale exports.
- Current Meta pricing per region (KSA/UAE/Egypt) not fetched.

---

## 4. Spreadsheet/Excel cleanup, validation and entity resolution

### Takeaway
Open-source ER splits into probabilistic linkers (Splink, fastLink), active-learning tools (Zingg, dedupe) and research toolkits (recordlinkage, PyJedAI). Splink (MIT, DuckDB locally) is the common default; Zingg is AGPL. OpenRefine remains the best human-in-the-loop cleanup UI. Arabic names need transliteration/normalization before matching (CAMeL Tools, PyArabic).

### Cited Findings
- Zingg's list of top OSS ER tools: Zingg, Splink, dedupe, Python Record Linkage Toolkit, PyJedAI, FastLink, dblink, R RecordLinkage, DeepMatcher, RELAIS (Zingg is vendor). Zingg 0.7.0 released Aug 10 2026; Zingg+Neo4j ER-graph guide. — [Zingg](https://www.zingg.ai/post/top-10-open-source-entity-resolution-tools-2026)
- Splink: MIT, Splink 4, DuckDB/SQLite bundled, Spark/Athena/Postgres optional. — [Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/)
- Zingg: open source AGPL with enterprise edition. — [WinPure](https://winpure.com/best-entity-resolution-software/)
- Awesome-ER list adds exchanger, MatchFlow, Delex, DeezyMatch, StarSpace, cleanco, libpostal, PyJanitor, probablepeople, python-nameparser; commercial Senzing, Match Data Pro. — [Awesome-Entity-Resolution](https://github.com/OlivierBinette/Awesome-Entity-Resolution)
- Commercial ER: Senzing, Informatica, Reltio, IBM Match 360, Quantexa, AWS Entity Resolution, Tamr, Tilores, DataLadder, WinPure, MatchLogic. — [WinPure](https://winpure.com/best-entity-resolution-software/); [DataLadder](https://dataladder.com/best-entity-resolution-software/); [MatchLogic](https://matchlogic.io/resources/best-entity-resolution-software)

### Catalogue

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 122 | Splink | https://github.com/moj-analytical-services/splink | Y | MIT | Probabilistic (Fellegi-Sunter) record linkage on DuckDB/Spark/Athena/Postgres | P (string-agnostic; needs Arabic normalization) | DEDUP/ER | [Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/) |
| 123 | Zingg | https://github.com/zinggAI/zingg | P | AGPL-3.0 + enterprise | Spark ML active-learning ER; Databricks/Fabric/Snowflake | P | DEDUP/ER | [WinPure](https://winpure.com/best-entity-resolution-software/) |
| 124 | dedupe (dedupe.io) | https://github.com/dedupeio/dedupe | Y | MIT | Python active-learning fuzzy matching/dedup | P | DEDUP/ER | [Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/) |
| 125 | csvdedupe | https://github.com/dedupeio/csvdedupe | Y | MIT | CLI wrapper of dedupe for CSV files | P | DEDUP/ER | K |
| 126 | Python Record Linkage Toolkit | https://github.com/J535D165/recordlinkage | Y | BSD-3 | Prototyping toolkit: indexing, comparison, classification | P | DEDUP/ER | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 127 | PyJedAI | https://github.com/AI-team-UoA/pyJedAI | Y | Apache-2.0 | SOTA ER blocking/matching/clustering incl. embeddings | P | DEDUP/ER | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 128 | fastLink (R) | https://github.com/kosukeimai/fastLink | Y | GPL-3.0 (K) | Fast Fellegi-Sunter on a laptop | P | DEDUP/ER | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 129 | Senzing | https://senzing.com | N | Commercial (free tier) | Embeddable real-time ER engine for people/orgs | P | DEDUP/ER | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 130 | AWS Entity Resolution | https://aws.amazon.com/entity-resolution/ | N | Commercial | Managed rule/ML matching on AWS | P | DEDUP/ER | [WinPure](https://winpure.com/best-entity-resolution-software/) |
| 131 | Tilores | https://tilores.io | N | Commercial | Real-time identity resolution service | P | DEDUP/ER | [Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/) |
| 132 | WinPure | https://winpure.com | N | Commercial | No-code data cleansing & matching desktop/server | ? | CLEAN, DEDUP | [WinPure](https://winpure.com/best-entity-resolution-software/) |
| 133 | DataLadder DataMatch Enterprise | https://dataladder.com | N | Commercial | No-code fuzzy matching/dedup | ? | DEDUP | [DataLadder](https://dataladder.com/best-entity-resolution-software/) |
| 134 | MatchLogic | https://matchlogic.io | N | Commercial | On-prem ER for regulated orgs | ? | DEDUP | [MatchLogic](https://matchlogic.io/resources/best-entity-resolution-software) |
| 135 | OpenRefine | https://openrefine.org | Y | BSD-3 | Desktop/web tool to explore, cluster (fuzzy key collision), transform and reconcile messy tables | Y (Unicode; clustering works but Arabic-specific normalization manual) | CLEAN, DEDUP | K |
| 136 | Great Expectations (GX Core) | https://github.com/great-expectations/great_expectations | Y | Apache-2.0 | Declarative data validation "expectations" + data docs | P | CLEAN | K |
| 137 | Cleanlab | https://github.com/cleanlab/cleanlab | Y | AGPL-3.0 (K) | Find label errors, outliers, near-duplicates in datasets | P | CLEAN, DEDUP | K |
| 138 | pandas | https://pandas.pydata.org | Y | BSD-3 | Core DataFrame cleaning (read_excel, dedup, normalize) | Y | CLEAN | K |
| 139 | Polars | https://pola.rs | Y | MIT | Fast DataFrame engine for large CSV/Excel cleanup | Y | CLEAN | K |
| 140 | DuckDB | https://duckdb.org | Y | MIT | In-process SQL over CSV/Excel/Parquet; Splink backend | Y | CLEAN | [Tilores](https://tilores.io/content/best-open-source-entity-resolution-and-record-linkage-libraries-splink-zingg-dedupe-and-when-to-move-beyond-them/) |
| 141 | pyjanitor | https://pyjanitor-devs.github.io/pyjanitor/ | Y | MIT | Chainable pandas cleaning verbs | P | CLEAN | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 142 | Pandera | https://github.com/unionai-oss/pandera | Y | MIT | DataFrame schema validation | P | CLEAN | K |
| 143 | Soda Core | https://github.com/sodadata/soda-core | Y | Apache-2.0 | Data quality checks in YAML/SQL | P | CLEAN | K |
| 144 | ydata-profiling | https://github.com/ydataai/ydata-profiling | Y | MIT | One-line profiling report for tables (missing, dupes, types) | P | CLEAN | K |
| 145 | RapidFuzz | https://github.com/rapidfuzz/RapidFuzz | Y | MIT | Fast fuzzy string matching (Levenshtein, token ratios) | Y (Unicode) | DEDUP | K |
| 146 | libpostal | https://github.com/openvenues/libpostal | Y | MIT | Multinational address parsing/normalization | P (K: trained incl. Arabic-script addresses) | CLEAN | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 147 | cleanco | https://github.com/psolin/cleanco | Y | MIT | Strip legal suffixes from company names | N (Latin suffixes; extend for "ذ.م.م", "ش.م.ع") | CLEAN | [Awesome-ER](https://github.com/OlivierBinette/Awesome-Entity-Resolution) |
| 148 | Microsoft Data Wrangler (VS Code) | https://github.com/microsoft/vscode-data-wrangler | P | Free extension | GUI pandas cleaning that generates code | P | CLEAN | K |
| 149 | PandasAI | https://github.com/sinaptik-ai/pandas-ai | P | MIT core + EE | Natural-language querying/cleaning of DataFrames | P | CLEAN | K |
| 150 | Instructor | https://github.com/567-labs/instructor | Y | MIT | Pydantic-validated structured LLM extraction (normalize messy rows into schema) | Y (LLM-dependent) | CLEAN, META | K |
| 151 | LangExtract (Google) | https://github.com/google/langextract | Y | Apache-2.0 | LLM extraction with source grounding to spans | Y (LLM-dependent) | META | K |
| 152 | openpyxl / python-calamine | https://openpyxl.readthedocs.io | Y | MIT | Read messy Excel incl. merged cells, multiple header rows | Y | PARSE, CLEAN | K |

### Inferences
- Arabic-name ER pipeline: normalize (alef variants أ/إ/آ→ا, ta marbuta ة→ه, alef maqsura ى→ي, remove tatweel/diacritics with CAMeL/PyArabic) + transliteration key (e.g. Buckwalter via CAMeL) as an extra blocking/comparison column, then Splink/dedupe.
- AGPL tools (Zingg, Cleanlab, PyMuPDF) are fine for internal processing but need review if embedded into a distributed product.

### Gaps
- No Arabic-specific ER benchmark or Arabic name-matching library comparison was found this session.

---

## 5. Chunking, metadata, taxonomy and knowledge-graph extraction

### Takeaway
Chonkie, LangChain/LlamaIndex splitters and Docling's structure-aware chunkers cover chunking; late chunking (Jina) and Anthropic-style contextual retrieval are the high-value upgrades. For structuring into a "brain", Microsoft GraphRAG (MIT), LightRAG (MIT), Graphiti (Apache, temporal), Neo4j LLM Graph Builder (Apache) and Cognee (open source, 30+ connectors) are the main OSS options.

### Cited Findings
- Chonkie benchmarks: semantic chunking ~0.33 MB/s vs ~4.82 MB/s token-based (~14x slower); start with recursive 512-token splits; Contextual Retrieval reportedly cut top-20 failures up to 67% with reranking. — [digitalapplied](https://www.digitalapplied.com/blog/rag-chunking-strategies-2026-retrieval-quality-playbook)
- Late chunking improved nDCG@10 by 3.63% relative over naive chunking across 3 models / 4 BEIR datasets; needs whole doc in context (~8K). — [Splunk](https://www.splunk.com/en_us/blog/artificial-intelligence/chunking-techniques.html)
- LangChain SemanticChunker example. — [Firecrawl blog](https://www.firecrawl.dev/blog/best-chunking-strategies-rag)
- Neo4j LLM KG Builder: Apache-2.0, v0.8.7 July 2026, Docker Compose; GraphRAG MIT v3.3.0 (Oct 8 2026); LightRAG MIT v1.5.7 (Sep 2 2026), EMNLP 2025, stores in Neo4j/Postgres/Mongo/OpenSearch; Graphiti Apache-2.0 temporal KG. — [ivgraph](https://ivgraph.com/journal/knowledge-graph-tools/)
- Neo4j builder supports OpenAI, Gemini, Llama3, Diffbot, Claude, Qwen; lexical graph + entity graph; GraphRAG/vector/Text2Cypher. — [Neo4j](https://neo4j.com/labs/genai-ecosystem/llm-graph-builder/)
- Cognee: open-source memory control plane, ECL pipeline, 30+ connectors (vendor). — [Cognee](https://www.cognee.ai/cognee-review-2026-graphrag-knowledge-graphs-and-agent-memory); FastGraphRAG also named — [Cognee](https://www.cognee.ai/vector-databases-vs-knowledge-graph-frameworks-for-ai-memory)
- MinerU 4.0 includes a local doc library with page/block citation locators. — [file2markdown](https://www.file2markdown.ai/blog/marker-vs-mineru)

### Catalogue

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 153 | Chonkie | https://github.com/chonkie-inc/chonkie | Y | MIT | Lightweight fast chunking lib (token, sentence, recursive, semantic, late, neural, code) | P (tokenizer-dependent) | CHUNK | [digitalapplied](https://www.digitalapplied.com/blog/rag-chunking-strategies-2026-retrieval-quality-playbook) |
| 154 | LangChain text splitters (Recursive, SemanticChunker) | https://python.langchain.com | Y | MIT | Standard recursive/semantic splitters | P | CHUNK | [Firecrawl blog](https://www.firecrawl.dev/blog/best-chunking-strategies-rag) |
| 155 | LlamaIndex node parsers | https://docs.llamaindex.ai | Y | MIT | Sentence/semantic/hierarchical/markdown node parsers | P | CHUNK | K |
| 156 | Docling HybridChunker / HierarchicalChunker | https://github.com/docling-project/docling | Y | MIT | Structure + token aware chunking on DoclingDocument | P | CHUNK | [Medium](https://adityamangal98.medium.com/docling-vs-marker-vs-mineru-the-ultimate-open-source-pdf-parser-benchmark-2026-which-is-best-a36ecbb6c6b1) |
| 157 | semchunk | https://github.com/isaacus-dev/semchunk | Y | MIT | Fast semantic-boundary recursive chunker | P | CHUNK | K |
| 158 | Late chunking (Jina method) | https://arxiv.org/abs/2409.04701 | Y | Paper | Embed whole doc then pool per chunk | P (needs long-context multilingual embedder) | CHUNK, EMBED | [Splunk](https://www.splunk.com/en_us/blog/artificial-intelligence/chunking-techniques.html) |
| 159 | Anthropic Contextual Retrieval (technique) | https://www.anthropic.com/news/contextual-retrieval | - | Technique | LLM-written context prefix per chunk + BM25 + rerank | Y (LLM-dependent) | CHUNK, META | [digitalapplied](https://www.digitalapplied.com/blog/rag-chunking-strategies-2026-retrieval-quality-playbook) |
| 160 | Microsoft GraphRAG | https://github.com/microsoft/graphrag | Y | MIT | Entity/relation extraction, Leiden communities, hierarchical summaries | P (prompt tuning for Arabic) | KG | [ivgraph](https://ivgraph.com/journal/knowledge-graph-tools/) |
| 161 | LightRAG (HKUDS) | https://github.com/HKUDS/LightRAG | Y | MIT | Graph-index RAG with server + web UI | P | KG | [ivgraph](https://ivgraph.com/journal/knowledge-graph-tools/) |
| 162 | Graphiti (Zep) | https://github.com/getzep/graphiti | Y | Apache-2.0 | Temporal knowledge graph for agent memory (validity intervals) | P | KG | [typegraph](https://typegraph.ai/blog/best-open-source-graph-rag-tools) |
| 163 | Neo4j LLM Knowledge Graph Builder | https://github.com/neo4j-labs/llm-graph-builder | Y | Apache-2.0 | Upload PDFs/URLs/S3, build lexical + entity graph, chat via GraphRAG | P | KG | [Neo4j](https://neo4j.com/labs/genai-ecosystem/llm-graph-builder/) |
| 164 | Neo4j GraphRAG Python | https://github.com/neo4j/neo4j-graphrag-python | Y | Apache-2.0 (K) | Official KG-construction + retrievers package | P | KG | K |
| 165 | Cognee | https://github.com/topoteretes/cognee | Y | Apache-2.0 (K) | ECL pipeline: classify, chunk, LLM entity extraction, graph + vectors | P | KG, INGEST | [Cognee](https://www.cognee.ai/cognee-review-2026-graphrag-knowledge-graphs-and-agent-memory) |
| 166 | Fast GraphRAG (Circlemind) | https://github.com/circlemind-ai/fast-graphrag | Y | MIT (K) | Cheaper PageRank-based GraphRAG | P | KG | [Cognee](https://www.cognee.ai/vector-databases-vs-knowledge-graph-frameworks-for-ai-memory) |
| 167 | Zingg + Neo4j ER graph pattern | https://www.zingg.ai/post/building-an-entity-resolved-knowledge-graph-zingg-and-neo4j-together | - | Guide | Resolve entities first, then load one node per entity | P | DEDUP, KG | [Zingg](https://www.zingg.ai/post/top-10-open-source-entity-resolution-tools-2026) |
| 168 | GLiNER / GLiNER-multi | https://github.com/urchade/GLiNER | Y | Apache-2.0 | Zero-shot NER for arbitrary entity types (multilingual variants) | P | META | K |
| 169 | BERTopic | https://github.com/MaartenGr/BERTopic | Y | MIT | Topic modeling / taxonomy discovery with any embedding model (works with Arabic embedders) | Y (via embedder) | META | K |
| 170 | KeyBERT | https://github.com/MaartenGr/KeyBERT | Y | MIT | Keyword/tag extraction with embeddings | P | META | K |
| 171 | Microsoft Presidio | https://github.com/microsoft/presidio | Y | MIT | PII detection/anonymization (extend recognizers for Arabic) | P | CLEAN, META | K |
| 172 | LlamaIndex PropertyGraphIndex / metadata extractors | https://docs.llamaindex.ai | Y | MIT | LLM metadata (title, QA, keywords) + property graph extraction | P | META, KG | K |
| 173 | RAGFlow | https://github.com/infiniflow/ragflow | Y | Apache-2.0 | Template chunking, GraphRAG, knowledge base UI | P | CHUNK, KG | K |
| 174 | Haystack | https://github.com/deepset-ai/haystack | Y | Apache-2.0 | Pipeline framework: converters, cleaners, splitters | P | CLEAN, CHUNK | K |
| 175 | txtai | https://github.com/neuml/txtai | Y | Apache-2.0 | All-in-one embeddings DB + pipelines + graph | P | CHUNK, EMBED, KG | K |

### Inferences
- For Arabic content, graph-extraction prompts should be written/validated in Arabic and entity names canonicalized (normalization + ER) before graph loading, otherwise duplicate nodes for spelling variants multiply.

### Gaps
- No published evaluation of GraphRAG/LightRAG/Graphiti on Arabic corpora found.
- LLM-based taxonomy builders (e.g. Microsoft TnT-LLM) not researched in depth this session.

---

## 6. Arabic NLP: normalization, morphology, dialects, embeddings, rerankers

### Takeaway
CAMeL Tools (NYU Abu Dhabi) is the most complete open Arabic preprocessing toolkit (normalization, dediacritization, transliteration, morphology, 25-city dialect ID, NER, sentiment). For retrieval, the Arabic RAG leaderboard (Navid-AI) currently ranks jina-embeddings-v4, EmbeddingGemma-300m, Snowflake arctic-embed-l-v2.0, jina-v3 and an Arabic-English BGE-M3 fine-tune at the top; BAAI bge-reranker-v2-m3 and NAMAA's Arabic rerankers lead reranking. Watch licenses (jina v3/v4 are non-commercial per leaderboard metadata).

### Cited Findings
- CAMeL Tools: pre-processing (Buckwalter transliteration, letter variant normalization, tatweel removal), morphological analysis/disambiguation, dialect ID across 25 city dialects + MSA (67.9% on ~7-word sentences, 90% on 16-word), NER, sentiment. — [LREC 2020 paper](https://aclanthology.org/2020.lrec-1.868.pdf)
- CAMeL-Lab codafication: dialectal text normalization exploiting dialect ID. — [GitHub](https://github.com/CAMeL-Lab/codafication)
- PyArabic: normalization, tokenization, diacritics removal, number conversion, transliteration. — [JOSS](https://www.theoj.org/joss-papers/joss.04886/10.21105.joss.04886.pdf); [ResearchGate](https://www.researchgate.net/publication/370057456_PyArabic_A_Python_package_for_Arabic_text)
- Farasa is a fast Arabic segmenter cited alongside CAMeL. — [LREC 2020](https://aclanthology.org/2020.lrec-1.868.pdf)
- Arabic RAG leaderboard retrieval top: jina-embeddings-v4 75.51; embeddinggemma-300m (QAT q8) 75.37; Snowflake arctic-embed-l-v2.0 75.35; embeddinggemma-300m 75.10; jina-embeddings-v3 74.08; sayed0am/arabic-english-bge-m3 73.29; nomic-embed-text-v2-moe 69.63; Qwen3-Embedding-0.6B 68.90; omarelshehy/Arabic-Retrieval-v1.0 67.66; Muffakir_Embedding_V2 67.55; multilingual-e5-large-instruct 66.28. Reranking top: BAAI/bge-reranker-v2-m3 87.44; NAMAA-Space/Namaa-ARA-Reranker-V1 85.82; Alibaba gte-multilingual-reranker-base 85.03; NAMAA GATE-Reranker-V1 83.96. jina-embeddings-v3 and jina-reranker-m0 listed as cc-by-nc-4.0. Pending: Mizan embeddings/rerankers, microsoft/harrier-oss-v1-0.6b, perplexity pplx-embed-v1-0.6b, tencent R3-rerank. — [Navid-AI leaderboard](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard)
- GATE-Reranker: compact Arabic cross-encoder (OSACT 2026). — [ACL Anthology](https://aclanthology.org/2026.osact-1.5.pdf)
- Swan embedding family + ArabicMTEB benchmark (dialect-aware). — [arXiv](https://arxiv.org/html/2411.01192v2)
- Qwen3-Embedding still called best OSS embedder for most teams as of Oct 27 2026 (Apache-2.0, 32K). — [Maximem](https://www.maximem.ai/blog/best-embedding-models-2026)
- Arabic leaderboards: OALL v2, Arabic LLM Broad Leaderboard (ABL), Inception Arabic-Leaderboards, Islamic MMLU, Arabic RAG leaderboard, MTEB STS17 ar-ar. — [SILMA arabic-ai-ecosystem](https://github.com/SILMA-AI/arabic-ai-ecosystem)

### Catalogue — Arabic text processing

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 176 | CAMeL Tools | https://github.com/CAMeL-Lab/camel_tools | Y | MIT (K) | Arabic normalization, dediac, transliteration, morphology, dialect ID, NER, sentiment | Y | CLEAN, META | [LREC](https://aclanthology.org/2020.lrec-1.868.pdf) |
| 177 | CAMeL codafication | https://github.com/CAMeL-Lab/codafication | Y | ? | Dialectal Arabic text normalization to CODA | Y | CLEAN | [GitHub](https://github.com/CAMeL-Lab/codafication) |
| 178 | Farasa (QCRI) | https://farasa.qcri.org | P | Free for research; commercial license (K) | Segmenter, POS, NER, diacritizer, lemmatizer (API + Java) | Y | CLEAN, META | [LREC](https://aclanthology.org/2020.lrec-1.868.pdf) |
| 179 | PyArabic | https://github.com/linuxscout/pyarabic | Y | GPL-3.0 (K) | Normalization, tokenization, diacritics removal, number-to-words | Y | CLEAN | [JOSS](https://www.theoj.org/joss-papers/joss.04886/10.21105.joss.04886.pdf) |
| 180 | Tashaphyne | https://github.com/linuxscout/tashaphyne | Y | GPL (K) | Light Arabic stemmer/segmenter | Y | CLEAN | K |
| 181 | Mishkal | https://github.com/linuxscout/mishkal | Y | GPL (K) | Rule-based Arabic diacritizer | Y | CLEAN | K |
| 182 | Maha | https://github.com/TRoboto/Maha | Y | BSD-3 (K) | Arabic text cleaning/normalization library (keep/remove char classes, numbers) | Y | CLEAN | K |
| 183 | AraBERT preprocessor | https://github.com/aub-mind/arabert | Y | custom/MIT-ish (K) | ArabertPreprocessor: Farasa segmentation + normalization; AraBERT models | Y | CLEAN, EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 184 | Stanza (Arabic pipeline) | https://stanfordnlp.github.io/stanza/ | Y | Apache-2.0 | Tokenize, POS, lemma, dependency parse, NER for Arabic | Y | META | K |
| 185 | MADAMIRA | https://camel.abudhabi.nyu.edu/madamira/ | P | Research license | Morphological analysis + disambiguation (predecessor to CAMeL) | Y | META | K |
| 186 | Arabic auto-tashkeel demo / CATT | https://huggingface.co/spaces/MohamedRashad/arabic-auto-tashkeel | Y | ? | Neural diacritization models | Y | CLEAN | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 187 | python-bidi + arabic-reshaper | https://github.com/mpcabd/python-arabic-reshaper | Y | MIT | Fix Arabic shaping/RTL in rendered/extracted text and PDFs | Y | CLEAN | K |
| 188 | ftfy | https://github.com/rspeer/python-ftfy | Y | Apache-2.0 | Fix mojibake/encoding errors (common in Arabic CSV exports from Windows-1256) | Y | CLEAN | K |
| 189 | charset-normalizer / chardet | https://github.com/jawah/charset_normalizer | Y | MIT | Detect encodings (cp1256, UTF-8) before parsing | Y | CLEAN | K |
| 190 | Unicode NFKC (unicodedata) | https://docs.python.org/3/library/unicodedata.html | Y | PSF | Fold Arabic presentation forms (U+FB50–FEFF) to base letters | Y | CLEAN | K |

### Catalogue — Arabic-capable embeddings and rerankers

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 191 | jina-embeddings-v4 | https://huggingface.co/jinaai/jina-embeddings-v4 | P | Non-commercial (K, Qwen-based; verify) | #1 Arabic RAG retrieval (75.51), 32K ctx, multimodal | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 192 | EmbeddingGemma-300m (Google) | https://huggingface.co/google/embeddinggemma-300m | P | Gemma terms | 300M on-device embedder; #2–#5 Arabic retrieval | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 193 | Snowflake arctic-embed-l-v2.0 | https://huggingface.co/Snowflake/snowflake-arctic-embed-l-v2.0 | Y | Apache-2.0 | Multilingual 8K embedder, 75.35 Arabic retrieval | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 194 | jina-embeddings-v3 | https://huggingface.co/jinaai/jina-embeddings-v3 | P | CC-BY-NC-4.0 | 74.08 Arabic retrieval | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 195 | BGE-M3 (BAAI) | https://huggingface.co/BAAI/bge-m3 | Y | MIT | Dense+sparse+multi-vector multilingual embedder, 8K | Y | EMBED | K |
| 196 | arabic-english-bge-m3 (sayed0am) | https://huggingface.co/sayed0am/arabic-english-bge-m3 | Y | per card | BGE-M3 vocab-pruned/tuned for Ar-En; 73.29, best web-search subset (84.21) | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 197 | Qwen3-Embedding (0.6B/4B/8B) | https://huggingface.co/Qwen/Qwen3-Embedding-0.6B | Y | Apache-2.0 | Top general OSS embedder; 0.6B scores 68.90 Arabic | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard); [Maximem](https://www.maximem.ai/blog/best-embedding-models-2026) |
| 198 | nomic-embed-text-v2-moe | https://huggingface.co/nomic-ai/nomic-embed-text-v2-moe | Y | Apache-2.0 (K) | Multilingual MoE embedder; 69.63 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 199 | multilingual-e5-large-instruct | https://huggingface.co/intfloat/multilingual-e5-large-instruct | Y | MIT | Widely used multilingual baseline; 66.28 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 200 | Arabic-Retrieval-v1.0 (omarelshehy) | https://huggingface.co/omarelshehy/Arabic-Retrieval-v1.0 | Y | per card | Arabic-specific retriever; 67.66 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 201 | Muffakir_Embedding_V2 | https://huggingface.co/mohamed2811/Muffakir_Embedding_V2 | Y | per card | Arabic embedder, 8K; 67.55 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 202 | gte-multilingual-base (Alibaba) | https://huggingface.co/Alibaba-NLP/gte-multilingual-base | Y | Apache-2.0 | Compact 8K multilingual; 63.79 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 203 | AraGemma-Embedding-300m | https://huggingface.co/Omartificial-Intelligence-Space/AraGemma-Embedding-300m | Y | Apache-2.0 | Arabic-tuned EmbeddingGemma; 63.95 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 204 | GATE-AraBert-v1 | https://huggingface.co/Omartificial-Intelligence-Space/GATE-AraBert-v1 | Y | Open | Arabic STS/retrieval embedder; 59.12 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 205 | SILMA embedding (sts / matryoshka v0.1) | https://huggingface.co/silma-ai/silma-embeddding-sts-v0.1 | Y | per card | Arabic STS embedders; 61.1 / 56.77 | Y | EMBED | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 206 | Swan (Swan-Small / Swan-Large) | https://arxiv.org/html/2411.01192v2 | Y | per card | Arabic-centric dialect-aware embedders + ArabicMTEB | Y | EMBED, EVAL | [arXiv](https://arxiv.org/html/2411.01192v2) |
| 207 | BAAI bge-reranker-v2-m3 | https://huggingface.co/BAAI/bge-reranker-v2-m3 | Y | Apache-2.0 | #1 Arabic reranker (87.44) | Y | EMBED (rerank) | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 208 | Namaa-ARA-Reranker-V1 | https://huggingface.co/NAMAA-Space/Namaa-ARA-Reranker-V1 | Y | Apache-2.0 | Arabic reranker (85.82) | Y | EMBED (rerank) | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 209 | gte-multilingual-reranker-base | https://huggingface.co/Alibaba-NLP/gte-multilingual-reranker-base | Y | Apache-2.0 | Compact multilingual reranker (85.03) | Y | EMBED (rerank) | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 210 | GATE-Reranker-V1 (NAMAA) | https://huggingface.co/NAMAA-Space/GATE-Reranker-V1 | Y | Apache-2.0 | 135M Arabic cross-encoder (83.96); OSACT 2026 paper | Y | EMBED (rerank) | [ACL](https://aclanthology.org/2026.osact-1.5.pdf) |
| 211 | Qwen3-Reranker-0.6B | https://huggingface.co/Qwen/Qwen3-Reranker-0.6B | Y | Apache-2.0 | Multilingual reranker (evaluated on Arabic leaderboard) | Y | EMBED (rerank) | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 212 | Cohere Embed v4 / Rerank 3.5 | https://cohere.com | N | Commercial | Multilingual hosted embed/rerank (Arabic supported, K) | Y | EMBED | K |
| 213 | OpenAI text-embedding-3-large / Gemini Embedding | https://platform.openai.com | N | Commercial | Hosted multilingual embedders | Y | EMBED | K |

### Catalogue — Arabic leaderboards/benchmarks

| # | Name | URL | OSS | License | Description | Arabic | Step | Src |
|---|---|---|---|---|---|---|---|---|
| 214 | Arabic RAG / AIR Leaderboard (Navid-AI) | https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard | Y | - | Arabic retrieval + reranking leaderboard | Y | EVAL | [Navid-AI](https://huggingface.co/spaces/Navid-AI/The-Arabic-IR-Leaderboard) |
| 215 | Open Arabic LLM Leaderboard v2 (OALL) | https://huggingface.co/spaces/OALL/Open-Arabic-LLM-Leaderboard | Y | - | Pick an Arabic LLM for extraction/cleanup prompts | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 216 | Arabic LLM Broad Leaderboard (SILMA) | https://huggingface.co/spaces/silma-ai/Arabic-LLM-Broad-Leaderboard | Y | - | 22-skill Arabic LLM evaluation | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 217 | Inception Arabic-Leaderboards | https://huggingface.co/spaces/inceptionai/Arabic-Leaderboards | Y | - | IFEval, QA, orthography/grammar, reasoning, safety | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 218 | MTEB leaderboard (STS17 ar-ar, Arabic tasks) | https://huggingface.co/spaces/mteb/leaderboard | Y | - | General embedding benchmark incl. Arabic tasks | Y | EVAL | [SILMA list](https://github.com/SILMA-AI/arabic-ai-ecosystem) |
| 219 | SILMA arabic-ai-ecosystem (awesome list) | https://github.com/SILMA-AI/arabic-ai-ecosystem | Y | MIT | Curated index of Arabic leaderboards, OCR, tashkeel, TTS/ASR | Y | EVAL | [GitHub](https://github.com/SILMA-AI/arabic-ai-ecosystem) |

### Inferences
- Safe commercial default for Arabic retrieval: Snowflake arctic-embed-l-v2.0 (Apache-2.0) or BGE-M3 (MIT) + bge-reranker-v2-m3 (Apache-2.0); avoid jina v3/v4 unless a commercial license is bought.
- Normalization should be applied consistently at index and query time (same CAMeL/PyArabic settings); over-normalizing (e.g. ة→ه) can hurt embedders trained on raw text — test both.

### Gaps
- No public benchmark of Arabic normalization impact on modern embedders was found.
- License of several community Arabic embedders (Muffakir, Arabic-Retrieval) not verified.
- Swan model availability/licence not confirmed.
