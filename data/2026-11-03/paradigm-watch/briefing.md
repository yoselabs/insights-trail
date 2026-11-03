# Paradigm Watch — Daily Briefing
**Date:** 2026-11-03
**Query type:** GENERAL
**Sources:** Hacker News (front page keyword-free sweep), HuggingFace Papers (daily + trending), GitHub Trending, Techmeme, WebSearch (global), WebSearch (🇯🇵 Japanese), WebSearch (🇨🇳 Chinese), note.com, xenospectrum.com (JP), yoshishinnze.hatenablog.com, tech.ifeng.com, Sina Finance, 53AI, 163.com, bannedbook.org, VentureBeat, The Register, Latent Space

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~30 stories scanned; 3 paradigm-relevant | WSP debunking 716/166; WSP original ~1,857–2,100 pts (prior day); simonwillison 34/3 | 🌐 |
| HuggingFace Papers | 43 daily scanned; 3 paradigm-relevant | Wave Forcing 100↑; LoL 5↑; BYOD 6↑ | 🌐 |
| GitHub Trending | ~10 repos; 0 pure paradigm | Dominated scope 1/2; heretic adjacent | 🌐 |
| Techmeme | ~6 stories; 0 paradigm-relevant | Policy/enterprise | 🌐 |
| Web (global) | ~34 URLs | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~4 pages | — | 🇯🇵 note.com/npaka, xenospectrum JP, yoshishinnze hatenablog, youngju.dev |
| Web (China) | ~8 pages | — | 🇨🇳 ifeng.com ×2, Sina Finance, 53AI, 163.com, bannedbook.org, Zhihu ×2 |

---

## Synthesized Findings

### 1. [new] Weight-Space Programming — LLMs Read and Write Neural Network Weights Without Gradient Descent

**Assumption violated:** Gradient descent and symbolic optimizers (Adam, etc.) are required to modify neural network weights meaningfully; LLMs cannot natively reason about raw floating-point weight tensors.

- **Claim:** MIT CSAIL (Takehi, Teoh, Zhang, Khattab) published "Sparks of Weight-Space Programming" (Nov 2 2026, blog post): frontier LLMs like GPT-6 Astra can inspect, edit, and generate neural network weights without training infrastructure. HN original post: ~1,857–2,100 pts (day 1). Honnibal's debunking of the headline Qwen result: 716/166 on today's front page.

**Evidence — small-model experiments (not contested):**
- **Exp 1 (Read):** Identified game (Breakout/Pong/Pac-Man) from 17K–172K policy weights: **100% accuracy**
- **Exp 2 (Read):** Identified diffusion model outputs (circles/triangles/squares) from weights alone
- **Exp 3 (Read):** Determined training language + identified all copying heads from middle layers only
- **Exp 4 (Fix):** Repaired failing car control policy by editing 3.5% of weights: **0% → 100%** success
- **Exp 5 (Write):** Generated game-playing networks from scratch **beating PPO trained for 100M steps**
- **Exp 6 (Write):** 1.5M-parameter Go player **outperforms equal-sized PPO** in 50 forward passes

**Evidence — large-model experiment (contested):**
- **Exp 8 (Fix):** Qwen3.5-0.8B: MATH-500 7.9% → 48.1%; GSM8K 13.8% → 67.1%; IFEval 21.0% → 62.3%; edited only 0.016% of weights (131,072 of 800M) — found looping direction in MLP output of layers 15 + 19
- **Honnibal's critique:** This required Python code + 50 forward passes, not pure weight inspection; "Using Python tools to modify weights is simply what a human ML engineer could do"; Gemma 3 270M (no looping) barely moved (6.8% → 7.7%) — edit deleted an obstacle, did not add new capability
- **Status:** Blog post (not peer-reviewed); small-network results solid; large-model claim contested

**Broader framing:**
- **Latent Space:** "The world has gone from 0 to 1 on this very new RSI capability — which will immediately be put to use" — frames WSP as cutting autoresearch out of the RSI loop
- **VentureBeat headline:** "Like gene editing for neural networks"
- Databricks (Yuchen Jin): potential for model maintenance without fine-tuning; PauseAI (Maxime Fournes): "reckless — massively accelerates progress toward global catastrophe"

**Independent replication:**
- Simon Willison (HN #3, 34/3): replicated weight-reading with Qwen 3.8 27B locally — Pac-Man 72%, Pong 75%, Breakout 88%, failed Freeway
- openwsp/openwsp GitHub (2 stars): building open tooling for weight-level read/edit/version (1/50 passes complete, compute-limited)
- HN #25 (14/4): Edward Benson's "Embedding boolean circuits in a neural network" — companion conceptual piece (no empirical work)

**Sources (🌐):**
[Original post](https://rikiyat.github.io/blog/weight-space-programming/) · [Honnibal debunking](https://honnibal.dev/blog/astra-read-write-misleading) · [simonwillison](https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/) · [openwsp GitHub](https://github.com/openwsp/openwsp) · [Papers With Code](https://paperswithcode.co/paper/131739) · [VentureBeat](https://venturebeat.com/technology/like-gene-editing-for-neural-networks-mit-researchers-used-gpt-6-astra-to-edit-qwens-open-weights-directly-boosting-math-performance) · [The Register](https://www.theregister.com/ai-and-ml/2026/11/03/forget-retraining-ai-can-now-tweak-another-ais-weights/5307105) · [Latent Space](https://latent.space/p/ainews-llms-can-read-write-neural-network-weights-weight-space-programming-cuts-autoresearch-out-of/) · [Turing Post FOD#174](https://turingpost.com/p/what-is-weight-space-programming-and-why-it-suddenly-blew-up-the-internet) · [AI TLDR](https://ai-tldr.dev/releases/mit-csail-weight-space-programming/) · [alphaxiv](https://www.alphaxiv.org/abs/2611.weight-space-programming) · [aipolix](https://aipolix.com/en-us/news/mit-csail-weight-space-programming-gpt-6-astra-edits-neural-network-weights) · [analyticsindiamag](https://analyticsindiamag.com/ai-news/mit-researchers-show-llms-can-read-and-edit-neural-network-weights-without-retraining) · [startuphub.ai](https://www.startuphub.ai/ai-news/ai-research/2026/llms-can-now-read-and-rewrite-weights-directly) · [envisioning](https://www.envisioning.com/vocab/weight-space-programming) · [byteiota](https://byteiota.com/weight-space-programming-gpt-6-astra-patches-qwen/) · [explainx.ai](https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026) · [emergent.sh](https://emergent.sh/news/gpt-6-astra-edits-neural-weights-directly-no) · [pasqualepillitteri](https://pasqualepillitteri.it/en/news/29721/gpt-6-astra-qwen-weights-weight-space-programming) · [que.com](https://que.com/ai-edits-neural-network-weights-directly-without-gradients/) · [cctest.ai](https://cctest.ai/en/articles/astra-reads-and-writes-neural-weights-to-improve-qwen) · [Startup Fortune](https://startupfortune.com/mit-researchers-show-gpt-6-astra-can-rewrite-another-ais-brain-without-training-it/) · [dev.to](https://dev.to/trillioniar_s_14a3c313e14/a-model-that-rewrites-weights-by-hand-and-stolen-keys-that-cost-1-million-2cma) · [daily.dev](https://daily.dev/posts/astra-can-read-and-write-weights-to-improve-qwen-swdnk0yoe) · [OpenAI Community](https://community.openai.com/t/weight-space-programming-or-how-to-write-llm-weights-directly-using-an-llm/1412375) · [edwardbenson conceptual](https://edwardbenson.com/2026/10/embedding-boolean-circuits-in-a-neural-network)

**JP sources (🇯🇵):**
> "重みだけでゲームAIの種類を特定" ("Can identify game AI type from weights alone") — note.com/npaka ([link](https://note.com/npaka/n/n270373a5a637))

> "AIが別のAIの「脳」を直接書き換える時代へ：MITがニューラルネットワークの重みを読み解き、修正する技術を実証" ("Towards an era where AI directly rewrites another AI's 'brain': MIT demonstrates technology to read and modify neural network weights") — xenospectrum.com JP ([link](https://xenospectrum.com/sparks-of-weight-space-programming-mit-csail/))

[note.com/npaka](https://note.com/npaka/n/n270373a5a637) · [xenospectrum JP](https://xenospectrum.com/sparks-of-weight-space-programming-mit-csail/) · [xenospectrum EN](https://xenospectrum.com/en/sparks-of-weight-space-programming-mit-csail/)

**CN sources (🇨🇳):**
> "从AI帮助人类训练模型，到AI开始直接参与模型权重的优化" ("From AI helping humans train models, to AI directly participating in the optimization of model weights") — tech.ifeng.com ([link](https://tech.ifeng.com/c/8xkLCZBA6iD))

> "突破！GPT-6 Astra竟直接改Qwen权重，性能飙升500%" ("Breakthrough! GPT-6 Astra directly modifies Qwen weights, performance soars 500%") — 53AI ([link](https://www.53ai.com/news/LargeLanguageModel/2026110327814.html))

> "先进AI模型已具备直接读写神经网络权重的能力，能精准修改权重来提升模型能力" ("Advanced AI models have acquired the ability to directly read and write neural network weights, precisely modifying weights to enhance model capabilities") — bannedbook.org ([link](https://www.bannedbook.org/bnews/itnews/20261103/2376765.html))

[ifeng ×1](https://tech.ifeng.com/c/8xkiI6dDBu3) · [ifeng ×2](https://tech.ifeng.com/c/8xkLCZBA6iD) · [Sina Finance](https://finance.sina.com.cn/tech/roll/2026-11-03/doc-inixkzym8904144.shtml) · [53AI](https://www.53ai.com/news/LargeLanguageModel/2026110327814.html) · [163.com](https://www.163.com/dy/article/LAQ77G630511B8LM.html) · [bannedbook.org](https://www.bannedbook.org/bnews/itnews/20261103/2376765.html) · [freeblueplanet](https://www.freeblueplanet.com/t/topic/14879)

**Platforms:** HN (716/166 debunking + ~1,857–2,100 original), HuggingFace, GitHub, VentureBeat, The Register, Latent Space, Turing Post, note.com 🇯🇵, xenospectrum 🇯🇵, ifeng ×2 🇨🇳, Sina Finance 🇨🇳, 53AI 🇨🇳, 163.com 🇨🇳, bannedbook.org 🇨🇳

---

### 2. [new] Library of Layers (LoL) — Transformers Whose Layers Self-Order at Runtime

**Assumption violated:** Transformer layers must be applied in a fixed, predetermined sequential order; layer ordering is a static architectural decision.

- **Claim:** arXiv:2611.03526 (Rahmani et al., Nov 2 2026): a small trained router dynamically selects which layer to apply next from a global library of transformer blocks, adapting the computation graph per input.

**Evidence:**
- **Library size hyperparameter:** small library → layer reuse (depth-recurrent regime); large library → sparse activation (MoE regime) — single knob unifies three existing efficiency paradigms
- **Interpretable routing:** distinct layer-ordering strategies per task (Sudoku vs maze), language, safety content; safety probes detectable in routing decisions
- **Benchmarks:** Competitive with dense/recurrent/MoE baselines on text pretraining
- **Authors:** Abdellah Rahmani, Sean McLeish, Ang Li, Sanae Lotfi, Pascal Frossard, Micah Goldblum
- **HF upvotes:** 5 (low engagement — very fresh)

**Sources (🌐):**
[arXiv:2611.03526](https://arxiv.org/abs/2611.03526) · [arXiv HTML](https://arxiv.org/html/2611.03526) · [HuggingFace](https://huggingface.co/papers/2611.03526) · [Papers With Code](https://paperswithcode.co/paper/2611.03526)

---

**Still true** (ongoing, no new facts today):

- `qwenputer-compiled-cpu-in-weights` — RISC-V CPU compiler-programmed into Qwen3.5-4B weights; Doom E1M1 via CPU; HN 690/145 (Oct 22–30). Note: simonwillison.net headline "Qwen 3.8 27B on my laptop can interpret model weights, too" references qwenputer context but is testing WSP replication, not qwenputer itself.
- `jepa-platonic-representation-theorem` — LeCun+Balestriero prove JEPAs with good views converge to same representation; 109M JEPA out-aligns 72B LLMs (Oct 29)
- `llm-lean-proof-automation` — ETH false + Kakeya proofs (OpenAI+Claude independent convergence); $5M Simons review ongoing
- `worldtui-terminal-world-model` — WorldTUI 360M terminal world model; vim/tmux/snake simulated (Oct 21)
- `anthropic-formal-verification-assembly` — Claude: 239 OSS-Fuzz entry points, 180M Rocq lines, assembly-level (Oct 22)
- `fable-steganography-emergent-communication` — Fable 5.1 emergent steganography; cross-model 78% (Oct 21)
- `voxcpm2-tokenizer-free-tts` — VoxCPM2 tokenizer-free TTS via continuous diffusion-AR, 48kHz, 30 languages (Oct 23)
- `diffusion-lm-scaling-wave` — Mercury 3 at 1068 tok/sec (Oct 19); CN: DiffuSpace Clover-35B-A3B-Preview claimed 5-10× AR speed (Oct 28 CSDN; could not fetch details)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra embodied competence gap; simulation vs real-world gap persists
- `world-model-race` — LaLa-World/FCP/CN govt >20B CNY designation; world model race ongoing
- `ncm-coarse-to-fine-parallel-generation` — NCM 10-31× speedup over diffusion LMs (Oct 20)
- `fleet-learning-collective-robots` — AgiBot fleet binary-outcome learning 97.3% (Oct 20)
- `competing-learning-hybrid-architectures` — Tsinghua NLP SSM/attention competing learning; BLD fix (Oct 20)
- `goodfire-neural-networks-clean` — Goodfire: 90% neurons single-job; polysemanticity challenged (Oct 15)
- `minions-distributed-apple-silicon-gpu` — Minions + Muse Spark 816B on 2 Mac Studios (Oct 16)
- `typesafe-jev-system-one-models` — TypeSafe Jev + OpenAI Decisions API GA (Oct 23)
- `visionhope-self-modifying-backbone` — VisionHOPE 5-memory self-modifying backbone (Oct 9)
- `sgf-plus-decoupled-gradient-flows` — SGF+ 5s train → 24h video (Oct 9)
- `dust-backprop-free-training` — Dust zeroth-order competitive with backprop; 2M–243M params (Oct 9)
- `vals-ai-agent-materials-discovery` — 90 Claude agents DFT → spintronics candidates (Oct 9)
- `kandinsky-6-video-joint-audio` — Sber CrossDiT video+audio one-pass (Oct 9)
- `rogue-agents-collusion-dsewiki` — S. Korea bank hacks; ECHOTRIBBLE; CEO liability (Oct 20)
- `smelt-moe-looped-transformers` — SMELT/TaH2/ALoDLM looped transformers (Oct 6)
- `hc-dlm-hierarchical-continuous-diffusion` — HC-DLM continuous latent + discrete scaffold (Oct 6)
- `sharpening-tax-post-training-coverage` — Meta RL post-training narrows pass@K (Oct 6)
- `world-observer-persistent-actor-observer` — KAIST actor+observer; Observer Sink (Oct 6)
- `onestreamer-proactive-video-text-memory` — OneStreamer proactive caption memory (Oct 6)
- `post-training-behavioral-shadows` — ATD +5.34pp; Sharpening Tax (Oct 2)
- `yue2-ar-nar-music-unification` — YuE2 AR-NAR MoT; beats Suno v5/v6 (last seen Oct 27)
- `frontis-ma1-recursive-ml-self-improvement` — RSI-Anything; NUS: true R1/R2 not demonstrated (Oct 23). Connection: WSP (today's [new]) represents a new RSI modality not tracked by this thread's existing claims.
- `thinking-inertia-reasoning-control` — LLMs can't suppress explicit reasoning (Oct 13)
- `msar-depth-attention-residuals` — MSAR content-dependent depth attention 1.58× (Oct 13)

---

## Cross-Source Patterns

**1. Weight-space as programmable substrate — theme crystallizing (HN 🌐 × JP 🇯🇵 × CN 🇨🇳)**
- Qwenputer (Oct 22, still ongoing): CPU *compiled into* weights — deterministic programming without training
- WSP (Nov 2, today [new]): LLM *reasoning about* weights — interpretive editing without gradients
- simonwillison replication (today): Qwen 3.8 27B locally validates weight-reading capability
- Framing convergence: EN "like gene editing for neural networks"; JP "AIが別のAIの「脳」を直接書き換える"; CN "从AI帮助人类训练模型，到AI开始直接参与模型权重的优化"
- Both Qwenputer and WSP challenge: "weights are statistical artifacts, not substrate for computation or programming"

**2. High controversy as signal — WSP is significant precisely because it's contested (HN 🌐)**
- Original post: ~1,857–2,100 pts → Debunking: 716/166 → Both large (aggregate >2,500 pts + 300+ comments)
- Pattern: paradigm-threatening claims generate both belief and counter-evidence, both of which are high-signal
- Small-network WSP results (game ID: 100%, RL policy fix: 0%→100%) remain uncontested

**3. Diffusion generation paradigm expanding across modalities (HF 🌐 × CN 🇨🇳)**
- Wave Forcing (100↑ HF, today): video diffusion at 7.07× throughput via concurrent denoising
- BYOD (6↑ HF, today): LoRA-only AR→diffusion conversion — low-cost entry to diffusion paradigm
- DiffuSpace Clover-35B (CN CSDN Oct 28): 5-10× AR speed for agentic coding dLLM
- CN Zhihu framing: "扩散语言模型正在挑战GPT式生成范式" ("dLLMs are challenging the GPT-style generation paradigm")

---

## Per-Platform Tables

**Hacker News:**
| Title | Points | Comments | Notable Quote | URL |
|-------|--------|----------|--------------|-----|
| Sparks of Weight-Space Programming (original, Nov 2) | ~1,857–2,100 | — | "Frontier LLMs are surprisingly good at natively reading and writing neural network weights" | https://rikiyat.github.io/blog/weight-space-programming/ |
| The 'Astra can read and write weights' post is misleading (Honnibal, Nov 3) | 716 | 166 | "Every experiment involving a real language model uses Python" | https://honnibal.dev/blog/astra-read-write-misleading |
| Qwen 3.8 27B on my laptop can interpret model weights, too (simonwillison) | 34 | 3 | Pac-Man 72%, Pong 75%, Breakout 88% — locally | https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/ |
| Embedding boolean circuits in a neural network (edwardbenson) | 14 | 4 | Conceptual framework only; no empirical tests | https://edwardbenson.com/2026/10/embedding-boolean-circuits-in-a-neural-network |
| Mac at Any Scale | 152 | 68 | (Infrastructure/distributed compute, scope 5 edge) | https://namespace.so/blog/mac-at-any-scale |

**HuggingFace:**
| Paper | ↑ | arXiv | Institution | Paradigm relevance |
|-------|---|-------|-------------|-------------------|
| Wave Forcing: Speed-of-Light Streaming Video Generation | 100 | 2611.00859 | SJTU-DENG-Lab | Concurrent denoising pipeline innovation |
| BYOD: Build Your Own DLM | 6 | 2610.41574 | UMC Utrecht | AR→Diffusion LM conversion via LoRA |
| Library of Layers (LoL): Adaptively Ordering Transformer Layers | 5 | 2611.03526 | Rahmani et al. | Dynamic layer ordering at runtime |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | MIT CSAIL original post | https://rikiyat.github.io/blog/weight-space-programming/ | Primary research: 8 experiments, small + large model |
| 🌐 | Honnibal debunking | https://honnibal.dev/blog/astra-read-write-misleading | Critique: Python required; Gemma control failed; Qwen baseline pathological |
| 🌐 | simonwillison.net | https://simonwillison.net/2026/Nov/3/qwen-can-interpret-model-weights/ | Independent weight-reading replication on Qwen 3.8 27B |
| 🌐 | openwsp/openwsp | https://github.com/openwsp/openwsp | Independent replication tooling (2 stars) |
| 🌐 | Papers With Code (WSP) | https://paperswithcode.co/paper/131739 | WSP entry |
| 🌐 | VentureBeat | https://venturebeat.com/technology/like-gene-editing-for-neural-networks-mit-researchers-used-gpt-6-astra-to-edit-qwens-open-weights-directly-boosting-math-performance | "Like gene editing for neural networks"; Databricks + PauseAI quotes |
| 🌐 | The Register | https://www.theregister.com/ai-and-ml/2026/11/03/forget-retraining-ai-can-now-tweak-another-ais-weights/5307105 | "Forget retraining" framing |
| 🌐 | Latent Space | https://latent.space/p/ainews-llms-can-read-write-neural-network-weights-weight-space-programming-cuts-autoresearch-out-of/ | RSI connection: "cuts autoresearch out of the RSI loop" |
| 🌐 | Turing Post FOD#174 | https://turingpost.com/p/what-is-weight-space-programming-and-why-it-suddenly-blew-up-the-internet | Full explainer: why it blew up the internet |
| 🌐 | AI TLDR | https://ai-tldr.dev/releases/mit-csail-weight-space-programming/ | Summary |
| 🌐 | alphaxiv | https://www.alphaxiv.org/abs/2611.weight-space-programming | alphaxiv entry |
| 🌐 | aipolix | https://aipolix.com/en-us/news/mit-csail-weight-space-programming-gpt-6-astra-edits-neural-network-weights | Coverage |
| 🌐 | analyticsindiamag | https://analyticsindiamag.com/ai-news/mit-researchers-show-llms-can-read-and-edit-neural-network-weights-without-retraining | Coverage |
| 🌐 | startuphub.ai | https://www.startuphub.ai/ai-news/ai-research/2026/llms-can-now-read-and-rewrite-weights-directly | Coverage |
| 🌐 | Turing Post | https://turingpost.com/p/what-is-weight-space-programming-and-why-it-suddenly-blew-up-the-internet | Explainer |
| 🌐 | envisioning.com | https://www.envisioning.com/vocab/weight-space-programming | Vocab entry |
| 🌐 | byteiota | https://byteiota.com/weight-space-programming-gpt-6-astra-patches-qwen/ | Coverage |
| 🌐 | explainx.ai | https://explainx.ai/blog/weight-space-programming-gpt-6-astra-edits-qwen3-5-0-8b-weights-math-7-9-to-48-1-mit-csail-2026 | Coverage |
| 🌐 | emergent.sh | https://emergent.sh/news/gpt-6-astra-edits-neural-weights-directly-no | Coverage |
| 🌐 | pasqualepillitteri | https://pasqualepillitteri.it/en/news/29721/gpt-6-astra-qwen-weights-weight-space-programming | Coverage |
| 🌐 | que.com | https://que.com/ai-edits-neural-network-weights-directly-without-gradients/ | Coverage |
| 🌐 | cctest.ai | https://cctest.ai/en/articles/astra-reads-and-writes-neural-weights-to-improve-qwen | Coverage |
| 🌐 | Startup Fortune | https://startupfortune.com/mit-researchers-show-gpt-6-astra-can-rewrite-another-ais-brain-without-training-it/ | Coverage |
| 🌐 | dev.to | https://dev.to/trillioniar_s_14a3c313e14/a-model-that-rewrites-weights-by-hand-and-stolen-keys-that-cost-1-million-2cma | Coverage |
| 🌐 | daily.dev | https://daily.dev/posts/astra-can-read-and-write-weights-to-improve-qwen-swdnk0yoe | Coverage |
| 🌐 | OpenAI Community | https://community.openai.com/t/weight-space-programming-or-how-to-write-llm-weights-directly-using-an-llm/1412375 | Discussion |
| 🌐 | edwardbenson.com | https://edwardbenson.com/2026/10/embedding-boolean-circuits-in-a-neural-network | Conceptual companion piece (no empirical work) |
| 🌐 | arXiv:2611.03526 | https://arxiv.org/abs/2611.03526 | Library of Layers |
| 🌐 | arXiv:2611.00859 | https://arxiv.org/abs/2611.00859 | Wave Forcing |
| 🌐 | arXiv:2610.41574 | https://arxiv.org/abs/2610.41574 | BYOD |
| 🌐 | HuggingFace LoL | https://huggingface.co/papers/2611.03526 | LoL entry |
| 🌐 | chinabizinsider | https://chinabizinsider.com/beyond-token-prediction-the-2026-pivot-to-world-models-and-the-industrial-shakeout-of-embodied-ai/ | World model context |
| 🇯🇵 | note.com/npaka | https://note.com/npaka/n/n270373a5a637 | WSP overview in Japanese, Nov 2-3 |
| 🇯🇵 | xenospectrum JP | https://xenospectrum.com/sparks-of-weight-space-programming-mit-csail/ | WSP JP coverage |
| 🇯🇵 | yoshishinnze hatenablog | https://yoshishinnze.hatenablog.com/entry/2026/10/01/043000 | Non-transformer architecture landscape 2026 (Oct background) |
| 🇨🇳 | ifeng.com ×1 | https://tech.ifeng.com/c/8xkiI6dDBu3 | WSP: 0.016% → 6× math score |
| 🇨🇳 | ifeng.com ×2 | https://tech.ifeng.com/c/8xkLCZBA6iD | WSP full technical summary |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-11-03/doc-inixkzym8904144.shtml | WSP CN Nov 3 |
| 🇨🇳 | 53AI | https://www.53ai.com/news/LargeLanguageModel/2026110327814.html | "500% performance soar" framing |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/LAQ77G630511B8LM.html | WSP CN |
| 🇨🇳 | bannedbook.org | https://www.bannedbook.org/bnews/itnews/20261103/2376765.html | "Advanced AI models acquired weight read/write ability" |
| 🇨🇳 | freeblueplanet | https://www.freeblueplanet.com/t/topic/14879 | WSP CN discussion |
| 🇨🇳 | Zhihu DiffuSpace | https://zhuanlan.zhihu.com/p/2075953348130370376 | DiffuSpace interview: "dLLMs challenging GPT-style generation" |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (persistent)
├─ 🔵 X: excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~30 stories scanned │ 4 paradigm-relevant │ WSP original ~1,857–2,100/— │ Honnibal debunking 716/166 │ simonwillison 34/3 │ edwardbenson 14/4
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ health OK; no paradigm posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~34 pages │ 🇯🇵 4 (note.com/npaka, xenospectrum JP, yoshishinnze hatenablog, youngju.dev) │ 🇨🇳 8 (ifeng ×2, Sina, 53AI, 163, bannedbook, freeblueplanet, Zhihu DiffuSpace)
└─ 🗣️ Top voices: Rikiya Takehi (@rikiyat) · Honnibal (@honnibal) · Simon Willison (@simonwillison)
```

---

## Out of Scope but Notable

- **Wave Forcing** (arXiv:2611.00859, SJTU-DENG-Lab, 100↑ HF): 1F1C pipeline runs concurrent multi-step denoising across GPU replicas for video; 7.07× single-GPU throughput, 134.8 FPS on 8×H200. **Scope: diffusion-lm-scaling-wave thread adjacent** (but video, not language). Engineering innovation, not fundamental architectural paradigm; assumption challenged: serial chunk denoising is required.

- **BYOD: Build Your Own DLM** (arXiv:2610.41574, UMC Utrecht, 6↑ HF): LoRA-only (4.1–5.8% params) converts AR models (Gemma 2, Llama 3.1, Qwen2.5, Ministral 8B) to diffusion LMs without pretraining. Perplexity gap remains (8.3–11.1 vs 2.2–3.0). **Scope: diffusion-lm-scaling-wave thread** — reduces pretraining barrier to diffusion LM adoption; significant perplexity cost.

- **DiffuSpace Clover-35B-A3B-Preview** (CN, CSDN Oct 28): Chinese dLLM startup claiming 5-10× speed vs same-size AR on agentic tasks. URL: https://www.csdn.net/article/2026-10-28/169361157 (HTTP 521, could not fetch). **Scope: diffusion-lm-scaling-wave thread** — potential update (CN diffusion LM commercial scaling), but details unconfirmed.

---

## Data Gaps

- **Reddit (r/MachineLearning):** Blocked persistent — all runs
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked — **10th consecutive run** (Oct 2, 6, 9, 13, 16, 20, 23, 27, 30, Nov 3). JP/CN done via WebSearch + WebFetch
- **DiffuSpace CSDN article** (Oct 28): HTTP 521 — could not fetch; content estimated from search extract only
- **Bluesky:** Health OK; no paradigm-relevant posts surfaced
- **TikTok / Instagram / YouTube:** Not swept
- **Papers With Code trending:** Accessed via HuggingFace route (redirect to HF papers/trending)
- **last30days skill:** Not available in this environment; sweep conducted manually

**Coverage estimate:** ~84%. Strong on HN (both WSP and its debunking), HuggingFace Papers, Web global (WSP covered by 20+ sources), CN hubs (7 sources on WSP). Moderate JP (note.com/npaka + xenospectrum same-day, but no Qiita/Zenn surfaced). Reddit/Bluesky zero. Wave Forcing and LoL covered via HF.

---

## Key Quotes

> "We think neural network weights will soon be natively optimized by LLMs that deliberately reason about the weights." — Rikiya Takehi, MIT CSAIL, WSP original post ([link](https://rikiyat.github.io/blog/weight-space-programming/)) 🌐

> "Every experiment involving a real language model uses Python. Using Python tools to modify weights is simply what a human ML engineer could do." — Matthew Honnibal, debunking post ([link](https://honnibal.dev/blog/astra-read-write-misleading)) 🌐

> "The world has now gone from 0 to 1 on this very new RSI capability — which will immediately be put to use." — Latent Space on WSP ([link](https://latent.space/p/ainews-llms-can-read-write-neural-network-weights-weight-space-programming-cuts-autoresearch-out-of/)) 🌐

> "Like gene editing for neural networks." — VentureBeat headline ([link](https://venturebeat.com/technology/like-gene-editing-for-neural-networks-mit-researchers-used-gpt-6-astra-to-edit-qwens-open-weights-directly-boosting-math-performance)) 🌐

> "重みだけでゲームAIの種類を特定" ("Can identify game AI type from weights alone") — note.com/npaka ([link](https://note.com/npaka/n/n270373a5a637)) 🇯🇵

> "AIが別のAIの「脳」を直接書き換える時代へ" ("Towards an era where AI directly rewrites another AI's 'brain'") — xenospectrum.com JP ([link](https://xenospectrum.com/sparks-of-weight-space-programming-mit-csail/)) 🇯🇵

> "从AI帮助人类训练模型，到AI开始直接参与模型权重的优化" ("From AI helping humans train models, to AI directly participating in the optimization of model weights") — tech.ifeng.com ([link](https://tech.ifeng.com/c/8xkLCZBA6iD)) 🇨🇳

> "突破！GPT-6 Astra竟直接改Qwen权重，性能飙升500%" ("Breakthrough! GPT-6 Astra directly modifies Qwen weights, performance soars 500%") — 53AI ([link](https://www.53ai.com/news/LargeLanguageModel/2026110327814.html)) 🇨🇳

> "Transformer代替の議論は『Transformerを倒す』物語ではなく" ("The Transformer replacement discussion isn't about defeating it, but combining both strengths") — yoshishinnze.hatenablog.com ([link](https://yoshishinnze.hatenablog.com/entry/2026/10/01/043000)) 🇯🇵
