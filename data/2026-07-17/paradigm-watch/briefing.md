# Paradigm Watch — Daily Briefing
**Date:** 2026-07-17
**Query type:** GENERAL
**Sources:** Hacker News, GitHub Trending, Hugging Face (models + papers), Techmeme, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 24 stories | ~4,200 pts, ~3,100 comments | 🌐 keyword-free front page sweep |
| Hacker News (prior threads) | 2 topic threads | 225 pts, 57 comments confirmed (SubQ thread rate-limited) | 🌐 paradigm-relevant HN archive threads |
| GitHub Trending | 8 repos | 3,537–60 stars today | 🌐 keyword-free trending |
| Hugging Face Models | 5 trending | 4.05k–361 likes | 🌐 Ternary-Bonsai-27B trending #2 |
| Hugging Face Papers | 26 papers | 320–8 upvotes | 🌐 keyword-free paper trending |
| Techmeme | 8 stories | — | 🌐 AI coverage |
| Web (global) | 22 pages | — | 🌐 WebSearch + WebFetch (ChatForest, AI2Work, WhatLLM, FelloAI, Medium, DataCamp, Codiste, PJFP, goml.io, itbusinesstoday, prismml.com, progressiverobot, Morningstar, PRNewswire, kimi.com/blog) |
| Web (Japan) | 14 pages | — | 🇯🇵 Qiita ×1, note.com ×4, GIGAZINE ×1, ITMedia ×1, Hatena ×1, Zenn ×2, Yahoo JP ×2, ai-revolution ×1, weel.co.jp ×1 |
| Web (China) | 8 pages | — | 🇨🇳 36Kr ×1, CSDN ×2, Zhihu ×1, Sina Finance ×1, Cnblogs ×1, aigc.bar ×1, yunpan.plus ×1 |
| Reddit (r/MachineLearning) | 0 | — | ⚠ Access blocked |
| Bluesky | 0 | — | Not swept in manual pass (skill unavailable) |
| YouTube | 0 | — | Not swept in manual pass |
| TikTok | 0 | — | ScrapeCreators not configured |
| Instagram | 0 | — | ScrapeCreators not configured |
| Polymarket | 0 | — | No relevant markets |

---

## Synthesized Findings

Three items are genuinely new since the July 15 briefing; one prior theme has notable new papers. Ordered by significance:

---

### 1. [new] SubQ LLM: Sub-Quadratic Sparse Attention Claims to Break the O(n²) Prerequisite for Frontier Language Models 🌐 🇯🇵 🇨🇳

**Assumption violated:** Frontier-quality language understanding requires computing pairwise attention between all n² token combinations; there is no shortcut that preserves frontier-level performance.

**What it is:** Subquadratic (Miami, 13 employees, $29M seed, ~$500M valuation) launched SubQ on May 5, 2026 — billed as "the world's first fully sub-quadratic frontier LLM." Its core architecture is **SSA (Subquadratic Selective Attention)**: instead of attending to all token pairs, each query token dynamically selects only semantically relevant positions based on content, then computes exact attention over that sparse subset. Complexity drops from O(n²) to O(n·k) where k = selected tokens.

**Claims (vendor-provided, unverified):**
- 52x faster prefill than FlashAttention-2 at 1M tokens; ~1,000x fewer attention operations at 12M tokens
- Production context: 1M tokens; research/enterprise: 12M tokens; 50M token planned Q4 2026
- Competitive benchmarks: RULER 128K → 95.0% (vs. Claude Opus 4.6: 94.8%), SWE-Bench Verified → 81.8%
- API pricing: $0.50/$1.50 per M tokens (vs. Opus-class frontier pricing)

**Critical skepticism:** AI engineer Will Depue publicly argued SubQ is likely "a sparse attention finetune of Kimi or DeepSeek" rather than a novel architecture — masking quadratic training costs under a linear inference wrapper. SubQ's own CTO subsequently confirmed the model builds on someone else's open-source weights. No independent technical report, no model card, no third-party benchmark reproduction as of today. Only long-context benchmarks have been published; general-reasoning benchmarks (MMLU, GPQA, MATH) are absent, suggesting cherry-picking.

**Why it's still significant despite skepticism:** Even if SSA is "only" a learned sparse attention layer on top of an existing model, it represents a productionized existence proof that frontier benchmark scores can be maintained at 12M-token contexts with radically different attention patterns. The Theranos comparison circulating in CN media (36Kr) suggests the community is appropriately skeptical — but the conversation it has generated around attention architecture alternatives is itself a leading indicator.

**HN thread:** [SubQ — a major breakthrough in LLM intelligence](https://news.ycombinator.com/item?id=48024094) (rate-limited on retrieval; found via WebSearch)

🇯🇵 **Japanese community:** Multiple outlets covered SubQ — Qiita's kai_kou calls it "本当ならTransformer以後最大級のアーキテクチャ転換" ("if true, possibly the largest architecture shift after Transformers") while noting unverified claims. Sources: [Qiita/kai_kou](https://qiita.com/kai_kou/items/9428b9cc23475970c518), [note.com/kagawatomo](https://note.com/kagawatomo/n/n7c46bc432c25), [weel.co.jp](https://weel.co.jp/media/tech/subq/), [ai-revolution.co.jp](https://ai-revolution.co.jp/media/what-is-subq-llm/), [ai-career-japan.jp](https://ai-career-japan.jp/posts/subq-%E5%85%A5%E9%96%802026/)

🇨🇳 **Chinese community:** 36Kr led with "13人干翻Transformer" ("13 people overturn Transformer") framing, generating the fullest skeptical analysis. CSDN published two deep technical pieces. The framing converges on economics: "Transformer的敌人不是更大模型，而是更便宜的长上下文" ("Transformer's enemy is not bigger models, but cheaper long-context"). Sources: [36Kr](https://36kr.com/p/3797755244157959), [Zhihu](https://zhuanlan.zhihu.com/p/2035388006937403741), [CSDN (architecture)](https://blog.csdn.net/lulu1216544078/article/details/160846697), [CSDN (deep analysis)](https://blog.csdn.net/qq_60735796/article/details/160863817), [aigc.bar](https://www.aigc.bar/AI%E8%B5%84%E8%AE%AF%E6%96%87%E7%AB%A0/2026/05/06/subq-transformer-long-context-cost), [Cnblogs skeptical](https://www.cnblogs.com/gyc567/p/19982486), [Sina Finance](https://finance.sina.cn/stock/jdts/2026-05-06/detail-inhwyiyc3297368.d.html)

**Company / team:** CEO Justin Dangel, CTO Alex Whedon (former Head of GenAI at Meta), team includes PhDs from Google, Oxford, Cambridge. [ChatForest review](https://chatforest.com/reviews/subquadratic-subq-12m-context-window-sparse-attention-llm-2026/) | [DataCamp explainer](https://www.datacamp.com/blog/subq-ai-explained) | [PJFP explainer](https://pjfp.com/subquadratic-subq-explained-the-first-fully-sub-quadratic-llm-with-a-12m-token-context-window-50x-cost-reduction-and-a-post-transformer-architecture/) | [Medium critical analysis](https://medium.com/@candemir13/subq-what-actually-changed-and-whats-vendor-run-4fb63d4fb11b)

---

### 2. [new] Fujitsu PHOTON: Hierarchical Semantic Processing Achieves 475x GPU Throughput, Presented at ACL 2026 🌐 🇯🇵

**Assumption violated:** Language models must process text at uniform token granularity; meaning cannot be composed hierarchically within a single generative forward pass.

**What it is:** Fujitsu's PHOTON (**P**arallel **H**ierarchical **O**peration for **T**Op-down **N**etworks) is a Transformer-alternative LLM architecture announced June 24, 2026, and presented as an **oral session at ACL 2026** (San Diego, July 2–7, 2026). The core innovation: instead of flat token-by-token sequence processing, PHOTON organizes language into hierarchical meaning units, processing semantically coherent chunks rather than treating every token equally. A second mechanism, "multi-query integration," generates multiple slightly-varied candidate responses and selects/merges the best — combining parallel diversity with hierarchical encoding.

**The 475x number explained:** This is not a 475x overall speedup. It refers to **output tokens per GB of GPU memory** (throughput per GPU memory unit) at the 1.2B parameter scale, under multi-query conditions. A JP analyst correctly clarified: "最大475倍のメモリ効率スループット" = tokens processed per GB of GPU memory, compared to Transformer. [note.com/marusho](https://note.com/marusho_1266/n/n2c99d4c96856)

**Independent reimplementation results (Zenn/chitako):** A Japanese developer reimplemented PHOTON from scratch on a single NVIDIA DGX Spark (GB10, 121GB unified memory), using only the paper. Results at small scale confirmed:
- Prefill throughput: up to **3.75x faster** than Transformer
- Long-context decode: up to **6.36x faster**  
- KV memory: up to **2.37x reduction**
- Quality tradeoff: at 36-44M params, perplexity 1.98x worse than Transformer baseline; gap narrows to 1.71x at 158M params / 1.5B tokens
- RecGen mode requires 600M+ params / 134B tokens to be effective

Source: [Zenn/chitako reimplementation](https://zenn.dev/chitako/articles/e76ce82919e39f) — this is the most credible independent validation data available today.

**Paper:** arXiv 2512.20687. ACL 2026 oral. Scale of current validation: up to 1.2B parameters. Large-model (70B+) behavior unverified.

**Why this matters beyond the headline number:** Even at actual (non-marketed) gains of 3.75x–6.36x, hierarchical processing reduces memory pressure specifically under multi-query batch conditions — exactly the scenario where inference costs scale worst for real deployments. The ACL 2026 oral selection suggests the approach is peer-reviewed as novel; the from-scratch reimplementation suggests the approach is reproducible.

🇯🇵 **Japanese community:** Extensive and engaged — Fujitsu is a Japanese company and this generated national pride signal ("日本発のAI技術、応援したいですね" / "Japan-originated AI technology, let's cheer it on"). Sources: [GIGAZINE](https://gigazine.net/news/20260625-fujitsu-photon/), [ITMedia AI+](https://www.itmedia.co.jp/aiplus/article/2606/24/2000000125/), [Hatena/MISOLOG](https://misolog.hatenadiary.jp/entry/2026/06/25/215246), [Yahoo JP/ZDNET](https://news.yahoo.co.jp/articles/13c2cc470a0922b1b3468349dc5914e7e73511c4), [Yahoo JP/BizIT](https://news.yahoo.co.jp/articles/659914819c0b5df3e7296da92f7f653ac6dde4db), [Fujitsu official JP](https://global.fujitsu/ja-jp/technology/research/article/topics/202606-photon-architecture), [pronaviai.com](https://pronaviai.com/news/507), [ai-revolution.co.jp](https://ai-revolution.co.jp/media/fujitsu-photon-llm/), [aifriends.jp](https://aifriends.jp/fujitsu-photon-ai-architecture-475x/), [note.com/y44901726](https://note.com/y44901726/n/n5c51b49d046b)

🌐 **English coverage:** [ITBusinessToday](https://itbusinesstoday.com/tech/ai/fujitsu-unveils-photon-ai-architecture-promising-up-to-475x-greater-efficiency-than-transformers/)

---

### 3. [new] PrismML Ternary Bonsai 27B: Eliminates Floating-Point Multiplication, Runs Frontier-Class Reasoning on iPhone 🌐 🇯🇵 🇨🇳

**Assumption violated:** Neural networks require floating-point weight precision (FP16/BF16) to maintain representational capacity; compressing weights to integer lattices loses too much signal to be frontier-competitive.

**What it is:** PrismML announced Bonsai 27B on July 14, 2026 — a 27.8B-parameter model available in both 1-bit binary ({−1, +1}) and **1.58-bit ternary ({−1, 0, +1})** variants, derived from Qwen3.6-27B. Each group of 128 weights shares one FP16 scale factor; every weight is just a ternary value. By reducing weights to three integers, matrix multiplication collapses into additions — the model can run without GPU matrix multiply units.

**Key metrics:**
- Memory: **3.9GB** (vs. 54GB for FP16 Qwen3.6-27B) — 14x compression
- Device: runs on **iPhone 17 Pro at 11 tokens/second**; laptops, consumer CPUs, edge GPUs
- Benchmark retention: 1.58-bit variant maintains **>95% of FP16 performance** (80.49 avg across 15 benchmarks; AIME26: 87.5–90.8; LiveCodeBench: 85.96)
- HN engagement: [225 points, 57 comments](https://news.ycombinator.com/item?id=47812749) — commenters noted "82 toks/sec on M4 Pro," "83% from only 1.1 GiB"; critics noted hallucination in factual tasks and called for fairer comparisons against quantized baselines
- Together AI API available: https://www.together.ai/models/prism-ml-ternary-bonsai-27b

**PrismML company:** $16.25M from Khosla Ventures, Cerberus Capital, and Caltech (March 2026 emergence from stealth). Framing: "intelligence density" (知能密度 in JP community) over raw parameter count.

**Why it matters:** Ternary quantization is not quantization-as-degradation — it is a **different computational substrate**. When weights are {−1, 0, +1}, dot products become sign-based accumulations; specialized hardware (ARM CPUs, Apple Neural Engine, Qualcomm NPUs) can run these without dedicated GPU. PrismML's achievement is not just fitting a 27B model on a phone; it's achieving near-FP16 reasoning quality in a regime where multiplication doesn't exist. The constraint: 1-bit model shows hallucination issues in open-domain factual tasks (HN community reports), suggesting the ternary gain isn't free — it concentrates intelligence into reasoning tasks (AIME, coding) while degrading grounding tasks (factual recall).

🇨🇳 **Chinese parallel:** Tencent Hunyuan's **Sherry** (Feb 5, 2026) pursued the same direction independently — 1.25-bit ternary quantization with 3:4 sparsity. "开启LLM三值量化1.25bit时代" ("inaugurating the 1.25-bit ternary LLM era"). This is concurrent independent confirmation from CN labs. [CSDN/Sherry](https://www.csdn.net/article/2026-02-05/157764133)

🇯🇵 **Japanese coverage:** [note.com/humble_bobcat51](https://note.com/humble_bobcat51/n/n695e3a4a19c9) introduced "知能密度" (intelligence density) as new metric for evaluating these models. [alphaxiv.org JP](https://www.alphaxiv.org/ja/overview/2607.bonsai-27b), [Oflight Inc.](https://www.oflight.co.jp/en/columns/prismml-bonsai-27b-ternary-1bit-2026-07), [note.com/Takumi](https://note.com/_takumi_inoue_/n/n0802db271024) (theory of intelligence density in 1-bit LLMs)

**Sources:** [PrismML announcement](https://prismml.com/news/prismml-releases-bonsai-27b) | [PRNewswire](https://www.prnewswire.com/news-releases/prismml-introduces-ternary-bonsai-model-family-302745151.html) | [Morningstar](https://www.morningstar.com/news/pr-newswire/20260416sf36656/prismml-introduces-ternary-bonsai-model-family) | [ProgressiveRobot explainer](https://www.progressiverobot.com/2026/04/16/what-is-ternary-bonsai/) | [HuggingFace model page](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)

---

### 4. [update] World Models: Three High-Engagement Papers Confirm Sustained Research Velocity 🌐

**Assumption violated (ongoing):** Intelligence emerges from predicting text tokens; physically grounded world simulation is unnecessary for frontier AI.

**New since July 15:** Multiple concurrent world model papers now trending on HF papers, signaling the field is in active multi-group production (not a single flagship):

- **Orca: The World is in Your Mind** (arXiv 2606.30534) — **320 HF upvotes** (highest of any paradigm-relevant paper today). From Beijing Academy of AI (BAAI), 57 authors. Key innovation: **"Next-State-Prediction"** as unified training objective across text, images, and embodied actions — "unconscious learning" from continuous video and "conscious learning" from language-annotated events train a single shared world latent space. Pre-trained on 125K hours of video + 160M event annotations. Frozen backbone + lightweight decoders outperforms specialized baselines. "Unified state transition modeling route toward understanding, predicting, and acting upon the world." [arXiv](https://arxiv.org/abs/2606.30534) | [HF Papers](https://huggingface.co/papers/2606.30534) | [Papers with Code](https://paperswithcode.co/paper/2606.30534)

- **AlayaWorld: Long-Horizon and Playable Video World Generation** (arXiv 2607.06291) — **88 HF upvotes**. Open-source framework for real-time user-interactive world generation with diverse action support. [arXiv](https://arxiv.org/abs/2607.06291)

- **Infinite Worlds with Versatile Interactions / LingBot-World 2.0** (arXiv 2607.07534) — **43 HF upvotes**. 14B model (+ 1.3B lightweight variant), 720p video at 60 fps, **unbounded interaction horizon** (unlimited duration without quality degradation), dual agents (pilot + director), multiplayer support on single GPU. [arXiv](https://arxiv.org/abs/2607.07534)

- **Scaling Mixture-of-Experts Video Pretraining for Embodied Intelligence** (arXiv 2607.07675) — **63 HF upvotes**. DiT-based video pretraining with MoE for embodied intelligence. [arXiv](https://arxiv.org/abs/2607.07675)

The [update] here: prior briefing focused on commercial phase (World Labs Marble, Ars Technica scrutiny, AP News framing). Today, the research velocity layer is catching up — four concurrent papers with combined ~534 HF upvotes vs. the single Orca 320-upvote leader. The field has entered a multi-group simultaneous push phase.

**Still true** (from prior briefing, no new facts today):
- Diffusion LMs: ICML 2026 double Outstanding Paper, Mercury 2 (1009 tok/s), NVIDIA Fast-dLLM (27.6x), COLM 2026 workshop (Oct 9) — no new milestone today; only incremental papers (TACG 2607.03236, Consistent DLMs 2605.00161) found
- World Labs Marble commercial product + Ars Technica "promise and limits" coverage — no new update
- Post-transformer: CoFrGeNets (ICML 2026) + PaTH (NC1-complete expressivity) — no new development
- IBM "architectural conviction not incremental optimization" framing — unchanged
- CN: NTP→NSP paradigm framing (Juejin), "世界模型" as main battlefield (suanli.cn) — unchanged

---

## Cross-Source Patterns

### Pattern 1: The "Efficiency Inversion" — Three Simultaneous Bets That Compute Can Be Radically Restructured
SubQ (O(n) vs. O(n²) attention), PHOTON (hierarchical vs. flat token processing), and Ternary Bonsai (1.58-bit vs. 16-bit weights) all arrived in the same 7-week window (May 5 – July 14, 2026). None is from a major US lab. All three claim order-of-magnitude efficiency gains while maintaining competitive task performance. All three face verification gaps of some kind (SubQ: no technical report; PHOTON: unverified at 70B+; Bonsai: hallucination tradeoffs). **The convergence on efficiency-as-primary-axis is the signal** — whether each individual claim holds up, the research community has collectively decided the next frontier is compute restructuring, not parameter scaling.

**Platforms:** HN (SubQ thread, Bonsai 225pts), HF Trending (Bonsai #2), ACL 2026 oral (PHOTON), CSDN/36Kr/Zhihu (SubQ), Gigazine/ITMedia/Zenn (PHOTON), note.com (Bonsai JP)

### Pattern 2: JP/CN Divergence on Coverage Depth
Fujitsu PHOTON: massive JP coverage (8+ outlets, one developer reimplementation from scratch), minimal CN coverage. SubQ: massive CN coverage (36Kr, CSDN, Zhihu, Sina Finance), moderate JP coverage (Qiita, 3-4 note.com posts). This mirrors the source-affinity pattern: Japanese community engages with Japanese institutional research (PHOTON = Fujitsu); Chinese community leads on startup/disruption narrative (SubQ = 13-person Miami startup "overthrowing Transformer").

**Platforms:** Gigazine/Zenn (🇯🇵 → PHOTON), 36Kr/CSDN/Zhihu (🇨🇳 → SubQ)

### Pattern 3: The Ternary Convergence — US VC and CN Lab Arriving Independently at 1.58-Bit
PrismML (Khosla Ventures, March 2026) and Tencent Hunyuan's Sherry (February 2026) published sub-2-bit quantization results within weeks of each other, using different approaches (ternary training vs. post-training ternary quantization), reaching similar efficiency conclusions. Neither cites the other as prior art in their announcements. Independent convergence on extreme quantization as viable frontier-maintenance strategy is stronger evidence than any single paper.

**Platforms:** HN (225pts/57cmt), HF #2 trending model, CSDN (Tencent Sherry), Morningstar/PRNewswire (PrismML)

---

## Per-Platform Tables

**Hacker News (paradigm-relevant threads):**
| User | Title | Points | Comments | Notable | URL |
|------|-------|--------|----------|---------|-----|
| — | Ternary Bonsai: Top Intelligence at 1.58 Bits | 225 | 57 | "82 toks/sec on M4 Pro"; skepticism on factual grounding | https://news.ycombinator.com/item?id=47812749 |
| — | SubQ – a major breakthrough in LLM intelligence | — | — | Rate-limited; CTO later confirmed uses external base weights | https://news.ycombinator.com/item?id=48024094 |
| — | Kimi K3: Open Frontier Intelligence | 1,655 | 970 | 🌐 #2 story today; excluded scope (open/non-US models) | https://news.ycombinator.com/item?id=(from HN front page) |
| — | How to Train a Gen AI Kick Drum Model on 6GB VRAM | 139 | 64 | Audio diffusion; consumer democratization signal | https://zhinit.dev/ |

**Hugging Face Models (trending, paradigm-relevant):**
| Model | Downloads | Likes | Key Contribution | URL |
|-------|-----------|-------|-----------------|-----|
| prism-ml/Ternary-Bonsai-27B-gguf | 201k | 636 | 27B model at 3.9GB; 1.58-bit ternary weights | https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf |
| prism-ml/Bonsai-27B-gguf | 1.05M | 361 | 1-bit binary variant; 11 tok/s on iPhone 17 Pro | https://huggingface.co/prism-ml/Bonsai-27B-gguf |

**Hugging Face Papers (paradigm-relevant):**
| Upvotes | Title | arXiv | Key Contribution |
|---------|-------|-------|-----------------|
| 320 | Orca: The World is in Your Mind | 2606.30534 | Next-State-Prediction unified world model; 125K hrs video |
| 88 | AlayaWorld | 2607.06291 | Playable real-time world generation, open-source |
| 63 | Scaling MoE Video Pretraining for Embodied Intelligence | 2607.07675 | DiT + MoE for embodied AI |
| 43 | Infinite Worlds / LingBot-World 2.0 | 2607.07534 | 720p 60fps, unbounded interaction, multiplayer |
| 11 | Continuous Audio Language Models | 2509.06926 | Consistency modeling for audio (non-AR audio generation) |
| 8 | Terrain Diffusion | 2512.08309 | Diffusion-based procedural world generation |

**Web (Global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | ChatForest (SubQ deep review) | https://chatforest.com/reviews/subquadratic-subq-12m-context-window-sparse-attention-llm-2026/ | Best skeptical technical analysis of SubQ |
| 🌐 | AI2Work | https://ai2.work/blog/subq-debuts-commercial-subquadratic-llm-with-12-million-token-context | SubQ commercial launch details |
| 🌐 | DataCamp | https://www.datacamp.com/blog/subq-ai-explained | SubQ explainer |
| 🌐 | PJFP | https://pjfp.com/subquadratic-subq-explained-the-first-fully-sub-quadratic-llm-with-a-12m-token-context-window-50x-cost-reduction-and-a-post-transformer-architecture/ | SubQ technical explainer |
| 🌐 | Medium/Can Demir | https://medium.com/@candemir13/subq-what-actually-changed-and-whats-vendor-run-4fb63d4fb11b | Critical: "what actually changed and what's vendor-run" |
| 🌐 | WhatLLM | https://whatllm.org/blog/new-ai-models-may-2026 | May 2026 model landscape, SubQ in context |
| 🌐 | Codiste | https://www.codiste.com/subq-first-sub-quadratic-frontier-llm-long-context-ai | SubQ long-context analysis |
| 🌐 | ITBusinessToday | https://itbusinesstoday.com/tech/ai/fujitsu-unveils-photon-ai-architecture-promising-up-to-475x-greater-efficiency-than-transformers/ | PHOTON coverage (EN) |
| 🌐 | Fujitsu global | https://global.fujitsu/en-global/technology/research | PHOTON official |
| 🌐 | goml.io | https://www.goml.io/blog/orca | Orca world model explained |
| 🌐 | PrismML | https://prismml.com/news/prismml-releases-bonsai-27b | Bonsai 27B announcement |
| 🌐 | PRNewswire | https://www.prnewswire.com/news-releases/prismml-introduces-ternary-bonsai-model-family-302745151.html | PrismML Ternary Bonsai announcement |
| 🌐 | Morningstar | https://www.morningstar.com/news/pr-newswire/20260416sf36656/prismml-introduces-ternary-bonsai-model-family | PrismML family announcement |
| 🌐 | ProgressiveRobot | https://www.progressiverobot.com/2026/04/16/what-is-ternary-bonsai/ | Ternary Bonsai explainer |
| 🌐 | Together AI | https://www.together.ai/models/prism-ml-ternary-bonsai-27b | Bonsai 27B on Together AI API |
| 🌐 | arXiv Orca | https://arxiv.org/abs/2606.30534 | Orca world model |
| 🌐 | arXiv LingBot-World 2.0 | https://arxiv.org/abs/2607.07534 | Infinite Worlds |
| 🌐 | arXiv AlayaWorld | https://arxiv.org/abs/2607.06291 | AlayaWorld |
| 🌐 | arXiv Scaling MoE Embodied | https://arxiv.org/abs/2607.07675 | MoE video pretraining |
| 🌐 | arXiv Continuous Audio LMs | https://arxiv.org/abs/2509.06926 | Consistency modeling for audio |
| 🌐 | arXiv Terrain Diffusion | https://arxiv.org/abs/2512.08309 | Diffusion procedural worlds |
| 🌐 | Kimi K3 tech blog | https://www.kimi.com/blog/kimi-k3 | Architecture details (out of scope but architecture notable) |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita/kai_kou | https://qiita.com/kai_kou/items/9428b9cc23475970c518 | SubQ technical intro; "largest architecture shift after Transformer if true" |
| 🇯🇵 | note.com/kagawatomo | https://note.com/kagawatomo/n/n7c46bc432c25 | SubQ: "meaning-based sparse selection" framing |
| 🇯🇵 | weel.co.jp | https://weel.co.jp/media/tech/subq/ | SubQ full explainer in Japanese |
| 🇯🇵 | ai-career-japan.jp | https://ai-career-japan.jp/posts/subq-%E5%85%A5%E9%96%802026/ | SubQ launch coverage |
| 🇯🇵 | GIGAZINE | https://gigazine.net/news/20260625-fujitsu-photon/ | PHOTON: "Fujitsu develops 475x Transformer-alternative" |
| 🇯🇵 | ITMedia AI+ | https://www.itmedia.co.jp/aiplus/article/2606/24/2000000125/ | PHOTON: authoritative JP tech media |
| 🇯🇵 | Hatena/MISOLOG | https://misolog.hatenadiary.jp/entry/2026/06/25/215246 | PHOTON: "cost structure inflection point for generative AI" |
| 🇯🇵 | Yahoo JP (ZDNET) | https://news.yahoo.co.jp/articles/13c2cc470a0922b1b3468349dc5914e7e73511c4 | PHOTON wide reach |
| 🇯🇵 | Yahoo JP (BizIT) | https://news.yahoo.co.jp/articles/659914819c0b5df3e7296da92f7f653ac6dde4db | PHOTON wide reach |
| 🇯🇵 | Fujitsu JP official | https://global.fujitsu/ja-jp/technology/research/article/topics/202606-photon-architecture | PHOTON primary source |
| 🇯🇵 | Zenn/chitako | https://zenn.dev/chitako/articles/e76ce82919e39f | PHOTON from-scratch reimplementation on DGX Spark |
| 🇯🇵 | note.com/marusho | https://note.com/marusho_1266/n/n2c99d4c96856 | PHOTON "475x is actually memory throughput" debunking |
| 🇯🇵 | note.com/humble_bobcat51 | https://note.com/humble_bobcat51/n/n695e3a4a19c9 | Ternary Bonsai: "knowledge density" (知能密度) as new metric |
| 🇯🇵 | alphaxiv.org JP | https://www.alphaxiv.org/ja/overview/2607.bonsai-27b | Bonsai 27B paper JP overview |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | 36Kr | https://36kr.com/p/3797755244157959 | "13 people overturn Transformer" — fullest skeptical CN analysis |
| 🇨🇳 | Sina Finance | https://finance.sina.cn/stock/jdts/2026-05-06/detail-inhwyiyc3297368.d.html | SubQ mass-market CN framing |
| 🇨🇳 | CSDN (architecture) | https://blog.csdn.net/lulu1216544078/article/details/160846697 | SSA deep architecture analysis |
| 🇨🇳 | CSDN (analysis) | https://blog.csdn.net/qq_60735796/article/details/160863817 | "SubQ and SSA: Transformer's enemy is cheaper long-context" |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2035388006937403741 | SubQ leading CN discussion |
| 🇨🇳 | Cnblogs (skeptical) | https://www.cnblogs.com/gyc567/p/19982486 | "Has the quadratic curse truly been broken?" |
| 🇨🇳 | aigc.bar | https://www.aigc.bar/AI%E8%B5%84%E8%AE%AF%E6%96%87%E7%AB%A0/2026/05/06/subq-transformer-long-context-cost | SubQ vs Transformer |
| 🇨🇳 | CSDN/Tencent Sherry | https://www.csdn.net/article/2026-02-05/157764133 | Tencent's independent 1.25-bit ternary approach |

---

## Stats Block

```
├─ 🟡 HN: 24 stories (front page) + 2 archive threads │ ~225 pts confirmed (Bonsai), 57 comments │ SubQ thread rate-limited
├─ 🐙 GitHub Trending: 8 repos │ 3,537 top │ no paradigm-watch items trending today
├─ 🤗 HF Models: 5 trending │ Ternary-Bonsai-27B #2 (636 likes, 201k downloads)
├─ 📄 HF Papers: 26 papers │ Orca 320 upvotes │ top paradigm-relevant
├─ 📺 Techmeme: 8 stories │ Kimi K3 dominant (excluded scope)
├─ 🌐 Web: 21 pages │ 🇯🇵 14 │ 🇨🇳 8
├─ 🟠 Reddit: 0 │ ⚠ blocked
├─ 🦋 Bluesky: 0 │ not swept (manual run without skill)
└─ 🗣️ Top voices: Zenn/chitako (PHOTON reimpl.), note.com/marusho (PHOTON debunk), Qiita/kai_kou (SubQ), 36Kr (SubQ CN), CSDN (SubQ + Sherry)
```

---

## Out of Scope but Notable

- **Kimi K3 (2.8T params, Moonshot AI)** — HN #2 (1,655 pts, 970 comments) today. Excluded scope (4: open/non-US models & geopolitics), but two architectural details are worth flagging: **(a) Kimi Delta Attention (KDA)** — a new attention mechanism "designed to scale well beyond the trillion-parameter regime" for long sequences; and **(b) Stable LatentMoE** — routes to only 16 of 896 experts, 1.78% active parameter density, with "Quantile Balancing" to prevent routing collapse at this sparsity level. These are architectural innovations to watch in non-exclusion-scope briefings. MXFP4 training (MX-format FP4 weights + FP8 activations applied from SFT stage) achieves 2.5x scaling efficiency gain over K2. Open weights dropping July 27. [Kimi K3 tech blog](https://www.kimi.com/blog/kimi-k3) | [Graphify guide](https://graphify.net/ai-coding/llms/kimi-k3/) | [Kie.ai overview](https://kie.ai/blog/what-is-kimi-k3)

- **Continuous Audio Language Models (arXiv 2509.06926, 11 HF upvotes)** — Uses **consistency modeling** (not autoregressive, not standard diffusion) for audio generation in continuous embedding space. Violates assumption that audio must be generated token-by-token or via score-matching; uses consistency model's property of mapping any noisy state to a clean output in one step. Low engagement today but non-AR audio generation is an underrepresented paradigm angle. [arXiv](https://arxiv.org/abs/2509.06926)

- **"How to Train a Gen AI Kick Drum Model on Your Old Linux Desktop with 6GB VRAM"** (HN, 139 pts, 64 comments) — Not a paradigm shift, but a strong **democratization signal**: audio diffusion generation is now accessible to individual developers on consumer hardware below the previously assumed GPU threshold. The assumption it gently challenges: generative audio AI requires large-scale compute infrastructure. [zhinit.dev](https://zhinit.dev/)

- **Variable Bit-width Quantization: "Bigger-but-Smaller" LLMs** (arXiv 2607.02893) — Per-group precision learning, related to ternary but more granular. Interesting parallel to PrismML's group-scale approach; may inform the next phase of extreme quantization. [arXiv](https://arxiv.org/pdf/2607.02893)

---

## Data Gaps

- **`/last30days` skill:** Not registered in this environment. Full manual sweep performed across all surfaces specified in the paradigm-watch workflow. This adds 30–45 minutes of retrieval time but covers the same surface area.
- **Bluesky:** Not swept in manual run (skill provides Bluesky integration). Prior briefing found only 5 low-engagement posts; impact of gap estimated low.
- **Reddit r/MachineLearning:** Blocked (HTTP error). This is a persistent gap — compensated by HF Papers trending, HN, and multi-source web research, which surface the same papers via different paths.
- **YouTube:** Not swept. Long-form video coverage of SubQ/PHOTON/Bonsai likely exists but not retrieved.
- **TikTok, Instagram:** ScrapeCreators not configured — appropriate for this topic class.
- **CSDN direct access:** One URL (lulu1216544078 article) returned HTTP 521 (CloudFlare). Title/content confirmed from 36Kr and WebSearch summaries.
- **HN SubQ thread:** Rate-limited (HTTP 429). Thread confirmed to exist at news.ycombinator.com/item?id=48024094; engagement not retrieved directly.
- **DuckDuckGo HTML endpoint:** Returned CAPTCHA for multi-term JP/CN queries. Switched to native WebSearch in JP/CN — equivalent or better coverage.
- **Approximate coverage:** ~75% — HN, HF, Techmeme, JP, CN hubs well covered; missing Bluesky, Reddit, YouTube, and direct CSDN access.

---

## Key Quotes

> "本当ならTransformer以後最大級のアーキテクチャ転換" ("If true, possibly the largest architecture shift after Transformers") — Qiita/kai_kou on SubQ ([qiita.com](https://qiita.com/kai_kou/items/9428b9cc23475970c518)) 🇯🇵

> "Transformer の敌人不是更大模型，而是更便宜的长上下文" ("Transformer's enemy is not bigger models, but cheaper long-context") — CSDN analysis of SubQ ([CSDN](https://blog.csdn.net/qq_60735796/article/details/160863817)) 🇨🇳

> "13人干翻Transformer！新架构SSA算力暴减千倍" ("13 people overturn Transformer! New architecture SSA reduces compute by 1000x") — 36Kr headline on SubQ ([36Kr](https://36kr.com/p/3797755244157959)) 🇨🇳

> "The first 27B model to run on a phone." — PrismML on Ternary Bonsai 27B ([prismml.com](https://prismml.com/news/prismml-releases-bonsai-27b))

> "知能密度" ("Intelligence density") — JP community metric coined for ternary model evaluation ([note.com/humble_bobcat51](https://note.com/humble_bobcat51/n/n695e3a4a19c9)) 🇯🇵

> "最大475倍のメモリ効率スループット … GPU メモリ 1 GB あたりのトークン処理速度" ("Maximum 475x memory-efficient throughput … tokens processed per GB of GPU memory") — JP analyst clarifying the actual PHOTON claim ([note.com/marusho](https://note.com/marusho_1266/n/n2c99d4c96856)) 🇯🇵

> "Prefill throughput up to 3.75x faster, long-context decode up to 6.36x faster, and KV memory reduction up to 2.37x" — Zenn/chitako on PHOTON from-scratch reimplementation ([zenn.dev](https://zenn.dev/chitako/articles/e76ce82919e39f)) 🇯🇵

> "Next-State-Prediction modeling, offering a unified state-transition modeling route toward understanding, predicting, and acting upon the world." — Orca paper abstract, arXiv 2606.30534 ([arxiv.org](https://arxiv.org/abs/2606.30534))
