# Paradigm-Watch — Daily Briefing
**Date:** 2026-08-11
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers, GitHub Trending, Techmeme, WebSearch (global), Web (Japan — Zenn, note.com, Qiita, GIGAZINE), Web (China — 163.com/Netease, aitntnews.com, CSDN, Zhihu)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 30 stories swept | 1,123 pts top (Muse Glimmer OOS); 365 pts (Needle2 paradigm); 216 pts (Claude Riemann update) | 🌐 Full front page, keyword-free |
| HuggingFace Papers | 13 papers swept | 1,060 upvotes top (Ouroboros OOS); 238 (Steerling-8B paradigm); 28 (BDH-CQ paradigm) | 🌐 Full trending list |
| GitHub Trending | 6 repos swept | All Scope 1/2/3/5 today | 🌐 No paradigm-watch repos |
| Techmeme | ~10 stories | Claude Riemann Zeta top paradigm story | 🌐 |
| Web (global) | ~35 pages | — | 🌐 via WebSearch + WebFetch; all URLs in raw.web.md |
| Web (Japan) | 4 pages | — | 🇯🇵 Zenn, note.com, Qiita, GIGAZINE |
| Web (China) | 4 pages (2 blocked) | — | 🇨🇳 163.com, aitntnews.com; CSDN/Zhihu blocked (521/403) |
| Reddit r/MachineLearning | 0 | — | Not swept (keyword-free; WebFetch blocked) |
| X/Twitter | 0 | — | Excluded per instructions |
| Bluesky | 0 | — | SOURCE HEALTH: bluesky=OK; no paradigm-watch posts surfaced |
| YouTube | 0 | — | Not swept |
| TikTok / Instagram | 0 | — | Not swept |
| Polymarket | 0 | — | Not swept |

---

## Synthesized Findings

Prior `threads.json` (2026-08-07) carried 25 threads. All accounted for below.

---

### 1. [update] Claude Raises Riemann Zeta Bound 41.6% → 67.2% — Largest Jump in 46 Years of Human Progress

**ASSUMPTION VIOLATED:** That AI can only assist mathematics by searching known results and formalizing human-found proofs — Claude autonomously connected two previously siloed research threads (Baluyot/Goldston/Suriajaya/Turnage-Butterbaugh with Bombieri's 2000 work) via quadratic forms, producing the largest single advance on this bound in the problem's history. 🌐

**New fact since prior briefing:** Riemann zeta lower bound increased 41.6% → 67.2% (published Aug 10–11, 2026). Prior thread noted Astra's 10 open problems and LLM Lean proof automation; this is a different model (unreleased research Claude, not Astra) on a different problem class (analytic number theory, not group theory/combinatorics).

- **Model:** Unreleased Anthropic research Claude (not Astra/GPT-5.6)
- **Methodology:** 60 subagents, 31M output tokens, 36-hour run, ~2,400 shell commands, hundreds of Python numerical verification scripts
- **What it found:** Treating the full zero-space with positive- and negative-definiteness together via quadratic forms — an approach prior researchers hadn't systematically applied to surpass the 41.6% bound
- **Limitation:** Approach is not expected to prove the full Riemann Hypothesis; bound advance ≠ proof
- **HN engagement:** 216 pts, 143 comments (front page today)

**Sources:** [Anthropic Research](https://www.anthropic.com/research/riemann-zeta) | [Neowin](https://www.neowin.net/news/unreleased-claude-model-makes-breakthrough-on-century-old-riemann-hypothesis-math-problem/) | [ExplainX](https://explainx.ai/blog/claude-riemann-zeta-lower-bound-67-percent-august-2026) | [Kingy.ai explainer](https://kingy.ai/blog/claude-riemann-hypothesis-67-percent-result/) | [AI Weekly](https://aiweekly.co/alerts/anthropic-unreleased-claude-improves-zeta-bound-to-672) | [CryptoBriefing](https://cryptobriefing.com/claude-riemann-zeta-lower-bound-67-percent/) | [ResultSense](https://www.resultsense.com/news/2026-08-11-claude-riemann-zeta-lower-bound/)

---

### 2. [new] Needle2: Simple Attention Network — No FFN, 14MB, Competitive Tool-Calling

**ASSUMPTION VIOLATED:** That effective tool-calling language models require standard transformer feed-forward networks (FFNs) — Needle2 drops FFNs entirely, replacing them with a Walsh-Hadamard transform and learned diagonals, and matches models 5–70× larger on tool-calling benchmarks at 14MB and 28MB peak RAM. 🌐

- **Architecture (Simple Attention Network):**
  - No FFN layers anywhere — "just attention and gating"
  - **Hadamard MLP:** Fixed Walsh-Hadamard transform + learned diagonals (replaces dense feedforward projections)
  - **Engram system:** Hashed n-gram key-value tables — moves world knowledge out of the weight stack entirely
  - **Multi-lane hyper-connections:** 4 residual streams for routing flexibility equivalent to wider networks
  - CQ2-bit quantization baked in from training start (not post-hoc)
- **Size:** 45M params, 14MB binary, 28MB peak session RAM, 256-token sliding window
- **Performance:** 500+ tok/s on Raspberry Pi 5; 400–1,500 tok/s on VR devices (Meta Quest 3S, Apple Vision Pro); 300–700 tok/s on sub-$200 phones; operates on ESP32-S3 microcontrollers
- **HN:** 365 pts, 136 comments (top paradigm-watch story today); predecessor Needle v1 hit #1 HN May 14, 2026

**HN discussion highlights:**
- "The learned confidence gate is the crucial piece for a 14MB action model" — on calibrated +60% confidence threshold
- "Tool calling is fundamentally retrieval-and-assembly…cross-attention is the right primitive and FFN parameters wasted at this scale"
- Critical: "struggles with basic reasoning tasks outside tool-call patterns at 45M params"

**Sources:** [Cactus Compute](https://cactuscompute.com/needle) | [HN thread](https://news.ycombinator.com/item?id=49246804) | [GitHub](https://github.com/cactus-compute/needle) | [DeepWiki](https://deepwiki.com/cactus-compute/needle) | [Andrew.ooo review](https://andrew.ooo/posts/needle-26m-function-calling-model-review/) | [EveryDev](https://www.everydev.ai/tools/needle-cactus-compute) | [Cactus Blog (v1)](https://cactuscompute.com/blog/needle)

---

### 3. [new] LFM2.5 2.6B: Production Non-Transformer Hybrid Reaches HN Front Page

**ASSUMPTION VIOLATED:** That transformer architecture is required for competitive production LLMs — Liquid AI's LFM2.5 uses 22 double-gated short convolution blocks + 8 GQA attention layers (no standard transformer) and runs at 220 tok/s on a CPU in 2.5GB, competitive with 4× larger transformer models. 🌐🇯🇵🇨🇳

- **Architecture:** 22 double-gated short convolution blocks + 8 Grouped Query Attention layers (30 total) — hybrid, not pure transformer or pure SSM. Rooted in liquid neural network theory (MIT CSAIL spinout, C. elegans nervous system inspiration)
- **Scale:** 2.69B params, 34T training tokens, 128K context, 16 languages
- **CPU performance:** 220 tok/s on Apple M5 Max, 113 tok/s on AMD Ryzen — in <2.5GB RAM
- **GPU performance:** ~15K tok/s at high concurrency (H100)
- **KV cache advantage:** No quadratic KV cache growth; linear scaling vs. transformer long-context memory wall
- **Benchmarks:** Leads on instruction-following and tool-use vs. Gemma variants; matches Qwen on agent tasks; only trails Qwen3.5-9B on coding
- **HN:** 89 pts, 19 comments; HF model card: https://huggingface.co/LiquidAI/LFM2.5-2.6B

**JP framing 🇯🇵:** "新しいオンデバイスAIの時代" ("new era of on-device AI") — note.com/open_zinnia6594 frames it as privacy-first offline agents; Japanese version available without fine-tuning.
> "Two years ago, this capability required data center dependence; now it runs offline in your pocket." (「2年前はデータセンターへの依存が必要だった能力が、今は手の中でオフライン動作する」) — note.com ([link](https://note.com/open_zinnia6594/n/n73a1c8f853f5)) 🇯🇵

**CN framing 🇨🇳:** "Transformer并非唯一解决方案" ("Transformer is not the only solution") — aitntnews.com explicitly frames this as a paradigm challenge. 163.com/Netease emphasizes 端侧部署 (edge-side deployment).
> "Liquid AI proves that the Transformer is not the only solution — non-Transformer architectures have broken through the performance ceiling to compete with larger models." (「Liquid AI证明了Transformer并非唯一解决方案——非Transformer架构已突破性能天花板，与更大的模型竞争」) — aitntnews.com ([link](https://www.aitntnews.com/newDetail.html?newId=21847)) 🇨🇳

**Sources:** [HuggingFace LFM2.5-2.6B](https://huggingface.co/LiquidAI/LFM2.5-2.6B) | [VentureBeat](https://venturebeat.com/technology/liquid-ais-smallest-model-yet-lfm2-5-230m-beats-models-4x-its-size-at-data-extraction-can-run-anywhere) | [lilting.ch (architecture deep dive)](https://lilting.ch/en/articles/lfm-hybrid-architecture) | [BaguaAI](https://baguaai.com/liquidai-lfm2-5-launch-non-transformer-architectures-are-redefining-the-edge-ai-frontier/) | [AlphaSignal](https://alphasignal.ai/news/liquid-ai-s-lfm2-5-230m-beats-models-twice-its-size-running-on-a-raspberry-pi) | [InsiderLLM guide](https://insiderllm.com/guides/liquidai-lfm2-local-setup-guide/) | [163.com/Netease (CN)](https://www.163.com/dy/article/L3ISPFU10511B8LM.html) | [aitntnews.com (CN)](https://www.aitntnews.com/newDetail.html?newId=21847) | [note.com (JP)](https://note.com/open_zinnia6594/n/n73a1c8f853f5)

---

### 4. [new] Steerling-8B: Interpretability Scales With Capability Via Diffusion LM (238 HF Upvotes)

**ASSUMPTION VIOLATED:** That interpretability and frontier-scale capability are fundamentally at odds — Steerling-8B from Guide Labs shows that building interpretability constraints into training from the start introduces only a fixed scaling offset across 3 orders of magnitude of compute, with interpretability improving as the model scales. 🌐

- **Developer:** Guide Labs (YC-backed, San Francisco)
- **Architecture:** Causal discrete diffusion backbone + concept decomposition module
  - ~33K supervised "known" concepts (labeled human-understandable categories)
  - ~100K "discovered" concepts (learned by model, inspectable post-hoc)
  - Residual component capturing remainder
- **Interpretability metrics:**
  - 84%+ of token-level contributions flow through the concept module (not hidden channels)
  - 96.2% AUC accuracy for detecting known concepts in input text
  - Can attribute any generated token to: (a) input context, (b) human-understandable concepts, (c) training data examples
  - Concept-based steering without retraining
- **Performance:** Competitive with LLaMA2-7B and DeepSeek-7B at fewer FLOPs; trained on 1.35T tokens
- **Scaling result:** "More disentangled and aligned with human-understandable concepts with scale" — the usual interpretability/capability tradeoff narrative inverted
- **HF:** 238 upvotes for arXiv 2608.07594 (second-highest non-Scope-1 paper today)

**Sources:** [Steerling-8B release post](https://www.guidelabs.ai/post/steerling-8b-base-model-release/) | [Scaling paper](https://www.guidelabs.ai/papers/scaling-inherently-interpretable-language-models/) | [HF paper](https://huggingface.co/papers/2608.07594) | [arXiv](https://arxiv.org/abs/2608.07594) | [HF model](https://huggingface.co/guidelabs/steerling-8b) | [Evermx](https://www.evermx.com/case/steerling-8b-interpretable-llm-guide-labs)

---

### 5. [new] BDH-CQ: Recurrent Latent Reasoning Without Token-Space Verbalization (28 HF Upvotes)

**ASSUMPTION VIOLATED:** That LLM reasoning must be verbalized in token space (chain-of-thought) to be effective — BDH-CQ performs in-context learning and multi-step reasoning entirely within a continuous recurrent latent state, never emitting intermediate tokens, and achieves 29.5% ARC-AGI-1 at $0.0007/task vs. GPT-5.6 Luna's 34.2% at $0.040. 🌐

- **Architecture (Dragon Hatchling / BDH):** Pathway open-source; bio-inspired, non-transformer
  - High-dimensional positive activations
  - Low-rank communication between layers
  - Recurrent associative state with Hebbian learning (synaptic plasticity — not standard attention KV)
  - Fixed state size (no growing KV cache)
- **Reasoning mechanism:** Demonstrations update recurrent memory via S_t = U_θ(S_{t-1}, D_t); inference is iterative refinement in latent space → final answer decoded directly
- **ARC-AGI-1:** 150M params → 29.5% pass@2 at $0.0007/task; 57× cheaper than GPT-5.6 Luna (34.2%, $0.040)
- **HF:** 28 upvotes; paper arxiv 2608.09888; code at github.com/pathwaycom/bdh

**Known limitations:** Ordering fails beyond 6–8 objects; nesting fails at depth 5; 52/160 ConceptARC tasks had only partial success; color-swap operations fail outside specific layouts. Not yet validated on language/math tasks beyond ARC.

**Sources:** [arXiv 2608.09888](https://arxiv.org/abs/2608.09888) | [HF paper](https://huggingface.co/papers/2608.09888) | [GitHub pathwaycom/bdh](https://github.com/pathwaycom/bdh) | [ArXivIQ analysis](https://arxiviq.substack.com/p/the-dragon-hatchling) | [Pathway event](https://pathway.com/events/acm-neolab-pathway-2026) | [CRVScience](https://www.crvscience.com/post/the-dragon-hatchling-a-bio-physical-paradigm-for-post-transformer-artificial-intelligence) | [Original BDH paper arXiv 2509.26507](https://arxiv.org/abs/2509.26507)

---

**Still true** (ongoing threads from prior state — no new facts today):

- **taalas-msic-weights-in-silicon**: AMD/Taalas MSIC; weights etched in mask-ROM silicon; 16,960 tok/s Llama 3.1 8B at 1/10 H200 power; deal expected Q4 2026 close. No updates.
- **diffusion-lm-scaling-wave**: AURORA-LM, LLaDA MoE v2 30B-A3B competing without autoregressive decoding. No new velocity papers today (Steerling-8B extends diffusion LMs in a new direction — interpretability — and has its own new thread above).
- **maple-preview-ternary-moe**: Maple-Preview 20B-A1B ternary MoE; IMO-level reasoning at 5.31GB on Mac mini. No updates.
- **olix-otpu-photonic-ai-inference**: Olix DX-1 OTPU photonic chip; $312M Series B; H2 2027 delivery. No updates.
- **world-model-race**: Quo Vadis World Modeling? 6-functional-form taxonomy. No updates.
- **rlsvr-spyrl-self-verifiable-rewards**: RLSVR/SpyRL; self-verifiable RL for creative tasks. No updates.
- **neoteai-tactile-native-embodied-ai**: N₀-TWAM/N₀-VTLA tactile modality; 30K hrs tactile data. No updates.
- **odeworld-continuous-latent-world-model**: ODEWorld ODE integration in latent space. No updates.
- **meshy-t2-flow-matching-mesh-generation**: Flow-matching 3D mesh generation; 6s image-to-mesh. No updates.
- **openai-astra-ten-math-proofs**: Astra's 10 open math problems with Lean 4 certificates at ~$2K. No updates.
- **frontis-ma1-recursive-ml-self-improvement**: Frontis-MA1 35B; 71.21% MLE-Bench on single RTX 4090. No updates.
- **orca-baai-next-state-prediction**: BAAI Orca; Next-State-Prediction unified objective; 471 HF upvotes. No updates.
- **phizero-physical-language-world-model**: CASIA PhiZero; discrete physical language from unlabeled video. No updates.
- **turbovla-llm-bypass-vla**: TurboVLA; direct V+L→A without LLM intermediary; 97.7% LIBERO. No updates.
- **gemini-robotics-2-whole-body-vla**: DeepMind Gemini Robotics 2; first full humanoid VLA policy. No updates.
- **intact-search-free-world-model**: INTACT; eliminates CEM search; 300× faster. No updates.
- **llm-lean-proof-automation**: Now [update] above (Riemann Zeta advance).
- **transformer-transformer-robot-codesign**: Stanford Transformer Transformer; robot co-design via diffusion. No updates.
- **qwen-agentworld-language-world-model**: Alibaba Qwen-AgentWorld; language model as environment simulator. No updates.
- **modus-decoder-only-any-to-any**: EPFL MODUS; all modalities in single decoder-only model. No updates.
- **three-body-scattering-generative**: Three-Body Scattering; FID=1.63 in single forward pass. No updates.
- **multiverse-compactifai-tensor-network**: CompactifAI quantum tensor network compression 80–95%. No updates.
- **vibevoice-diffusion-speech**: VibeVoice; next-token diffusion for continuous speech; 80× compression. No updates.
- **spectral-prior-diffusion**: Spectral Alignment; fixes diffusion exposure bias across DDPM/ADM/SDXL/SD3.5/FLUX. No updates.
- **jacobian-conjecture-ai-mathematics**: Claude Fable 5 counterexample to Jacobian conjecture; verification ongoing. No updates (Riemann Zeta is a separate advance).
- **kimi-k3-kda-architecture**: Kimi Delta Attention; linear attention in 3/4 of layers; 6.3× faster decoding. No updates.

---

## Cross-Source Patterns

### Pattern 1: Non-Transformer Production Models Reaching Mass HN Audience (HN + CN + JP + WebSearch)

Three independent non-transformer or non-standard-transformer projects surfaced on HN today: Needle2 (365 pts, SAN), LFM2.5 (89 pts, hybrid conv+GQA), and BDH-CQ (28 HF upvotes, Dragon Hatchling). All three are production-grade or near-production. This is the first time three simultaneous non-transformer-architecture stories trended on a single HN front page scan in this topic's history.

CN and JP media independently frame LFM2.5 as a paradigm challenge: CN uses 非Transformer突破 ("non-Transformer breakthrough"); JP uses "オン・デバイスAIの新時代" ("new era of on-device AI"). The convergence of EN/CN/JP framing around the same architectural shift strengthens the signal.

**Platforms:** 🌐 HN, WebSearch, baguaai.com, lilting.ch | 🇨🇳 163.com, aitntnews.com | 🇯🇵 note.com

### Pattern 2: Reasoning Moving Out of Token Space (HN + HF Papers)

Both Needle2 (SAN's Engram: knowledge in n-gram tables, not weights) and BDH-CQ (reasoning in continuous latent state) move computation away from standard token-space operations. Separately, Steerling-8B moves interpretability away from post-hoc probing of opaque activations toward explicit concept-space computation. Three independent projects all reduce reliance on the standard "token-in, token-out, inspect activations" paradigm.

**Platforms:** 🌐 HN, HuggingFace Papers

---

## Per-Platform Tables

**Hacker News (paradigm-watch relevant):**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| cactuscompute | Show HN: Needle2: 14MB agentic LLM | 365 | 136 | "Tool calling is retrieval-and-assembly, not reasoning; FFN parameters wasted at this scale" | https://news.ycombinator.com/item?id=49246804 |
| (liquidai.ai) | LFM2.5 2.6B model competitive with 4x larger models | 89 | 19 | — | https://huggingface.co/LiquidAI/LFM2.5-2.6B |
| (anthropic.com) | Learning more about Claude's mathematical capabilities | 216 | 143 | "AI models can extend the impact and reach of mathematicians' ideas in new and sometimes surprising ways" | https://www.anthropic.com/research/riemann-zeta |
| (research.meta.ai) | Muse Glimmer: 30B model for always-on local agent workflows | 1,123 | 609 | — (OOS: Scope 4) | https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model |
| (ft.com) | Mark Zuckerberg attacks 'closed' AI rivals | 529 | 483 | — (OOS: Scope 4) | https://www.ft.com/content/4e3957f8-ea7c-4c46-a3de-cdce8e526878 |

**HuggingFace Papers (paradigm-watch relevant):**
| Title | Upvotes | Scope | URL |
|-------|---------|-------|-----|
| Scaling Inherently Interpretable Language Models (Steerling-8B) | 238 | **Paradigm-watch** | https://huggingface.co/papers/2608.07594 |
| Ouroboros: Self-Developing Frontier Coding Agent | 1,060 | Scope 2 (OOS) | https://huggingface.co/papers/2608.08311 |
| Macaron-V1: Open Continual Learning + Mixture-of-LoRA | 78 | Scope 1/2 (OOS) | https://huggingface.co/papers/2608.09819 |
| SWE-Bench ProMax: Multilingual Code Refactoring Benchmark | 75 | Scope 2 (OOS) | https://huggingface.co/papers/2608.09802 |
| BDH-CQ: In-Context Learning with Recurrent Latent Reasoning | 28 | **Paradigm-watch** | https://huggingface.co/papers/2608.09888 |
| OasisKV: Scaling KV Cache Beyond HBM | 12 | Related: memory wall | https://huggingface.co/papers/2608.08097 |

**GitHub Trending (all non-paradigm-watch today):**
| Repo | Stars | Scope |
|------|-------|-------|
| msitarzewski/agency-agents | 142,271 | Scope 1 |
| addyosmani/agent-skills | 86,026 | Scope 1 |
| ZhuLinsen/daily_stock_analysis | 61,894 | Scope 5 |
| PrimeIntellect-ai/prime-agent | 13,603 | Scope 1/2 |
| semantica-agi/semantica | 4,553 | Scope 3 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic Research | https://www.anthropic.com/research/riemann-zeta | Primary: Claude Riemann Zeta advance |
| 🌐 | Guide Labs | https://www.guidelabs.ai/post/steerling-8b-base-model-release/ | Steerling-8B: first inherently interpretable LLM |
| 🌐 | arXiv 2608.07594 | https://arxiv.org/abs/2608.07594 | Steerling-8B scaling paper |
| 🌐 | arXiv 2608.09888 | https://arxiv.org/abs/2608.09888 | BDH-CQ: recurrent latent reasoning paper |
| 🌐 | arXiv 2509.26507 | https://arxiv.org/abs/2509.26507 | Original Dragon Hatchling paper |
| 🌐 | GitHub pathwaycom/bdh | https://github.com/pathwaycom/bdh | Dragon Hatchling code |
| 🌐 | Cactus Compute | https://cactuscompute.com/needle | Needle2 official page |
| 🌐 | GitHub cactus-compute/needle | https://github.com/cactus-compute/needle | Needle2 source + SAN docs |
| 🌐 | HuggingFace LFM2.5-2.6B | https://huggingface.co/LiquidAI/LFM2.5-2.6B | LFM2.5 model card; benchmark data |
| 🌐 | lilting.ch | https://lilting.ch/en/articles/lfm-hybrid-architecture | LFM2.5 architecture deep-dive: "neither Transformer nor Mamba" |
| 🌐 | BaguaAI | https://baguaai.com/liquidai-lfm2-5-launch-non-transformer-architectures-are-redefining-the-edge-ai-frontier/ | Non-transformer framing; industry context |
| 🌐 | VentureBeat | https://venturebeat.com/technology/liquid-ais-smallest-model-yet-lfm2-5-230m-beats-models-4x-its-size-at-data-extraction-can-run-anywhere | LFM2.5 press coverage |
| 🌐 | Borealtimes | https://borealtimes.org/transformer-ai/ | 400% investment growth in non-transformer architectures; 60% of top labs have dedicated teams |
| 🌐 | labs.adaline.ai | https://labs.adaline.ai/p/the-ai-research-landscape-in-2026 | 7 technical transitions reshaping AI production in 2026 |
| 🌐 | ArXivIQ | https://arxiviq.substack.com/p/the-dragon-hatchling | Dragon Hatchling bio-physical framing |
| 🌐 | Pathway (BDH event) | https://pathway.com/events/acm-neolab-pathway-2026 | BDH as post-transformer AI paradigm |
| 🌐 | kingy.ai | https://kingy.ai/blog/claude-riemann-hypothesis-67-percent-result/ | Claude Riemann result explainer |
| 🌐 | ExplainX | https://explainx.ai/blog/claude-riemann-zeta-lower-bound-67-percent-august-2026 | Claude Riemann detailed breakdown |
| 🌐 | Neowin | https://www.neowin.net/news/unreleased-claude-model-makes-breakthrough-on-century-old-riemann-hypothesis-math-problem/ | Riemann coverage |
| 🌐 | Winzheng | https://www.winzheng.com/en/article/anthropic-unreleased-claude-riemann-hypothesis-bound-41-6-to | "Largest single jump on this specific figure in history" |
| 🌐 | Evermx | https://www.evermx.com/case/steerling-8b-interpretable-llm-guide-labs | "The First LLM That Can Explain Every Word It Generates" |
| 🌐 | andrew.ooo | https://andrew.ooo/posts/needle-26m-function-calling-model-review/ | Needle v1 review; "pattern of tiny specialist models as compiler passes" |
| 🌐 | AlphaSignal | https://alphasignal.ai/news/liquid-ai-s-lfm2-5-230m-beats-models-twice-its-size-running-on-a-raspberry-pi | LFM2.5 on Raspberry Pi |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/anthropic-unreleased-claude-improves-zeta-bound-to-672 | Riemann alert |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/claude-riemann-zeta-lower-bound-67-percent/ | Riemann coverage |
| 🌐 | ResultSense | https://www.resultsense.com/news/2026-08-11-claude-riemann-zeta-lower-bound/ | Riemann coverage (Aug 11, 2026 confirmed) |
| 🌐 | CRVScience | https://www.crvscience.com/post/the-dragon-hatchling-a-bio-physical-paradigm-for-post-transformer-artificial-intelligence | Dragon Hatchling science commentary |
| 🌐 | DeepWiki | https://deepwiki.com/cactus-compute/needle | Needle2 architecture documentation |
| 🌐 | InsiderLLM | https://insiderllm.com/guides/liquidai-lfm2-local-setup-guide/ | LFM2.5 setup guide |
| 🌐 | Adeia | https://adeia.com/blog/does-ai-scale-from-here-in-search-of-a-new-architecture | Post-scaling architecture analysis |
| 🌐 | aiofthecoast | https://aiofthecoast.dcxps.com/p/prediction-8-revisited-i-said-the | "Transformer didn't die; inference became the battleground" |
| 🌐 | metirai.com | https://www.metirai.com/blog/anthropic-claude-riemann-hypothesis-lower-bound-math-breakthrough-2026 | "Claude surpassed 46 years of combined human progress" |
| 🇯🇵 | note.com | https://note.com/open_zinnia6594/n/n73a1c8f853f5 | LFM2.5 as "on-device AI new era"; Japanese model variant |
| 🇯🇵 | Qiita | https://qiita.com/yut-nagase/items/eb3b189d0c232f7c569e | 2026 system architecture trends; domain-specialized small models |
| 🇯🇵 | Zenn | https://zenn.dev/okamyuji/articles/ai-architecture-one-sentence | Post-transformer landscape: SSM/Mamba/hybrid/diffusion LM synthesis |
| 🇯🇵 | GIGAZINE (June 25) | https://gigazine.net/news/20260625-fujitsu-photon/ | Fujitsu PHOTON: 475× throughput vs. Transformer (background context, >30 days old) |
| 🇨🇳 | 163.com / Netease | https://www.163.com/dy/article/L3ISPFU10511B8LM.html | LFM2.5-2.6B: 端侧部署 (edge deployment) framing |
| 🇨🇳 | aitntnews.com | https://www.aitntnews.com/newDetail.html?newId=21847 | "Transformer并非唯一解决方案" (Transformer is not the only solution) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (keyword-free paradigm-watch; WebFetch blocked)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not swept)
├─ 🟢 HN: 30 stories swept │ 1,123 pts top (Muse Glimmer OOS) │ 365 pts (Needle2 paradigm) │ 216 pts (Claude Riemann update)
├─ 🟣 TikTok: 0 videos (not swept)
├─ 🩷 Instagram: 0 reels (not swept)
├─ 🦋 Bluesky: 0 posts │ 0 likes (bluesky=OK; no paradigm-watch posts surfaced)
├─ 📊 Polymarket: 0 markets (not swept)
├─ 🌐 Web: ~35 pages │ 🇯🇵 4 │ 🇨🇳 4 (2 blocked: CSDN 521, Zhihu 403)
└─ 🗣️ Top orgs: Cactus Compute (Needle2/SAN); Liquid AI (LFM2.5); Guide Labs (Steerling-8B); Pathway (Dragon Hatchling); Anthropic (Riemann Zeta)
```

---

## Out of Scope but Notable

- **Muse Glimmer (Meta, 1,123 HN pts, 609 comments):** 30B open model for always-on local agent workflows; offline, 4-bit quantized to <20GB, DFlash speculative decoding. Scope 4 (Meta open model) + Scope 1 (agentic). [https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model](https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model)

- **Ouroboros: Self-Developing Frontier Coding Agent (1,060 HF upvotes):** AI agent that recursively improves its own core via reviewed evolution. Scope 2 (AI software factory). [https://huggingface.co/papers/2608.08311](https://huggingface.co/papers/2608.08311)

- **Mark Zuckerberg attacks "closed" AI rivals — Meta returning to open models (529 HN pts):** Public framing offensive against Anthropic/OpenAI; Meta positioning open model release as counter-move. Scope 4 (open models/geopolitics). [https://www.ft.com/content/4e3957f8-ea7c-4c46-a3de-cdce8e526878](https://www.ft.com/content/4e3957f8-ea7c-4c46-a3de-cdce8e526878)

- **Anthropic $9.1B compute deal with Riot Platforms (191 MW / 20-year):** Riot stock +25%. Scope 5 (enterprise AI adoption / infrastructure). [https://www.bloomberg.com/news/articles/2026-08-11/anthropic-strikes-9-billion-deal-with-cloud-computing-firm-riot](https://www.bloomberg.com/news/articles/2026-08-11/anthropic-strikes-9-billion-deal-with-cloud-computing-firm-riot)

- **Nvidia $500B AI infrastructure financing (Apollo/BlackRock/Blackstone/Goldman/KKR):** Transforms AI compute into investable asset class. Scope 5 (enterprise/industry structure). [https://www.ft.com/content/98a8fd17-15b6-4f67-9cb4-825722b11348](https://www.ft.com/content/98a8fd17-15b6-4f67-9cb4-825722b11348)

- **Anthropic Claude AI content watermarking (EU AI Act compliance, 204 HN pts):** C2PA metadata + invisible text watermarks embedded in all Claude outputs. Scope 5 (enterprise/policy). [https://www.theregister.com/ai-and-ml/2026/08/11/anthropic-pledges-to-embed-watermarks-to-help-discern-ai-slop-in-sop-to-eu/5285792](https://www.theregister.com/ai-and-ml/2026/08/11/anthropic-pledges-to-embed-watermarks-to-help-discern-ai-slop-in-sop-to-eu/5285792)

---

## Data Gaps

- **/last30days skill:** Not callable in this environment (consistent with all prior runs). Manual keyword-free sweep conducted across HN, HF Papers, GitHub Trending, Techmeme, supplementary WebSearch.
- **Reddit r/MachineLearning:** Not swept (keyword-free; WebFetch blocked by Reddit).
- **Bluesky:** SOURCE HEALTH: bluesky=OK. No paradigm-watch posts surfaced in web searches.
- **YouTube / TikTok / Instagram / Polymarket:** Not swept.
- **CSDN direct access:** HTTP 521 (server error) on direct fetch; content from search snippets only.
- **Zhihu direct access:** HTTP 403 (forbidden); content from search snippets only.
- **Papers With Code:** Site now redirects to HuggingFace Papers; covered via HF sweep.

**Coverage estimate: ~80%.** HN full front page (30 stories), HuggingFace Papers (13 papers), GitHub Trending (6 repos), Techmeme, global web, JP hubs (4 pages), CN hub aggregators (4, 2 blocked) all covered. Reddit, YouTube, and Bluesky absent. Today's paradigm-watch signals (Needle2, LFM2.5, Steerling-8B, BDH-CQ, Claude Riemann) are well-supported across multiple sources. CSDN/Zhihu direct access failure means some CN technical discussion of these topics is unread.

---

## Key Quotes

> "Tool calling is fundamentally retrieval-and-assembly — cross-attention is the right primitive and FFN parameters wasted at this scale. The entire model is just attention and gating, with no MLPs anywhere." — Cactus Compute, describing Needle2's Simple Attention Network ([link](https://news.ycombinator.com/item?id=49246804)) 🌐

> "The more interpretable the model, the less capable it is — this paper argues exactly the opposite: interpretability scales with capability, not against it." — Guide Labs, Steerling-8B scaling study ([link](https://www.guidelabs.ai/papers/scaling-inherently-interpretable-language-models/)) 🌐

> "Claude surpassed 46 years of combined human progress on this bound in a single 36-hour, 31-million-token run." — metirai.com, on Claude's Riemann Zeta advance ([link](https://www.metirai.com/blog/anthropic-claude-riemann-hypothesis-lower-bound-math-breakthrough-2026)) 🌐

> "Transformer并非唯一解决方案——非Transformer架构已突破性能天花板，与更大的模型竞争。" ("Transformer is not the only solution — non-Transformer architectures have broken through the performance ceiling to compete with larger models.") — aitntnews.com, on LFM2.5 🇨🇳 ([link](https://www.aitntnews.com/newDetail.html?newId=21847))

> "2年前はデータセンターへの依存が必要だった能力が、今は手の中でオフライン動作する。" ("Two years ago, this capability required data center dependence; now it runs offline in your pocket.") — note.com, on LFM2.5 🇯🇵 ([link](https://note.com/open_zinnia6594/n/n73a1c8f853f5))

> "The pattern of tiny specialist models as compiler passes for big generalist models is almost certainly what production agent stacks look like in two years." — andrew.ooo, reviewing Cactus Needle ([link](https://andrew.ooo/posts/needle-26m-function-calling-model-review/)) 🌐

> "Investment in non-transformer architectures has grown by 400% in two years, with over 60% of leading AI labs now having dedicated research teams exploring alternatives." — Boreal Times, August 2026 ([link](https://borealtimes.org/transformer-ai/)) 🌐
