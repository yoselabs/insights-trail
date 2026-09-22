# Paradigm Watch — Daily Briefing
**Date:** 2026-09-22
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers, GitHub Trending, Techmeme, WebSearch, Qiita (🇯🇵), Zhihu/Juejin (🇨🇳)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 14 stories scanned; 5 paradigm-relevant | Top: 978 pts (MiMo), 921 pts (Attention), 444 pts (Kev), 299 pts (GziPT), 268 pts (Mini-AGI) | 🌐 keyword-free front-page sweep |
| HuggingFace Papers | 9 papers scanned; 3 paradigm-relevant | WorldCrafter 194 upvotes; Dream-RSI 241 upvotes; HuRo 37 upvotes | 🌐 trending papers page |
| GitHub Trending | 5 repos scanned; 0 paradigm-relevant | All agent orchestration tools today | 🌐 |
| Techmeme | 5 stories; 1 paradigm-adjacent | Alibaba Zhenwu V900 + 5-10T Qwen | 🌐 |
| Web (global) | ~35 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~5 pages | — | 🇯🇵 Qiita (Jev ecosystem, world models); Zenn CAPTCHA/agent-only |
| Web (China) | ~4 pages (snippets) | — | 🇨🇳 Zhihu/Juejin via search snippets; direct fetches 403 |

---

## Synthesized Findings

### 1. [new] GziPT — Compression-Prediction Equivalence as Language Model

**Claim:** A blog post demonstrating that gzip can act as a language model with no trained neural parameters, by scoring candidate continuations via compressed output length, sparked significant HN debate (299 pts) — reviving the mathematical equivalence between compression and prediction as a potential non-neural approach to language modeling.

**Evidence:**
- **Mechanism:** GziPT primes DEFLATE compressor with a training corpus; candidate continuations scored by compressed length (shorter = better prediction); beam search selects best continuation
- **Results:** Output captures corpus statistical regularities; not coherent prose; no quantitative metrics (perplexity/BLEU) provided
- **Theoretical basis:** DeepMind 2023 research: every prediction model is a compressor and vice versa
- **Top HN comments:** jll29 (Waikato compression-as-classifier; Hutter Prize), stingraycharles (language detection via gzip dictionary seeding), woadwarrior01 (Normalized Compression Distance academic grounding)
- **Assumption violated:** Language modeling requires trained neural network parameters; compression algorithms already embed prediction implicitly

**Sources:** [nathan.rs](https://nathan.rs/posts/gzip-lm/) · [HN thread](https://news.ycombinator.com/item?id=49797323) · [Lobsters](https://lobste.rs/s/j11pew/can_gzip_be_a_language_model)
**Platforms:** HN (299 pts, 114 comments) 🌐

---

### 2. [new] Mini-AGI — Catastrophic Forgetting Solved via Differential Learning Rates

**Claim:** Show HN project Mini-AGI demonstrates that a byte-level LM can learn continuously from a live stream without catastrophic forgetting using a single architectural trick — setting the trunk's learning rate 10× lower than expert modules — achieving 99.84% retention of prior knowledge when absorbing a new 524K-character corpus.

**Evidence:**
- **Architecture:** Byte-level LM; trunk (embeddings, attention, routers) at 0.1× LR; expert modules at 1× LR
- **Forgetting measurement:** Reading 524K chars of new subject: +0.0067 nats forgetting on unrelated subjects (99.84% retention) vs +2.2300 nats with equal LR
- **Hardware:** Trains on 8GB VRAM consumer GPU (RTX class)
- **Key insight:** Training and inference run identical code paths — no separate fine-tuning step; model is deployable at any moment during learning
- **Assumption violated:** Training and inference must be separate phases; continual learning on a live stream requires specialized MoE/replay/regularization architectures — a single LR asymmetry suffices

**Sources:** [github.com/volotat/mini-AGI](https://github.com/volotat/mini-AGI/)
**Platforms:** HN (268 pts, 68 comments) 🌐

---

### 3. [new] HuRo — Human Internet Video Substitutes for Expensive Robot Demonstrations in VLA Pretraining

**Claim:** HuRo (CoRL 2026, arXiv:2609.10706) demonstrates that a pipeline "robotizing" internet-scale human video — removing hands, overlaying a rendered robot arm, retargeting motion to robot action trajectories — produces 630K pretraining episodes that improve VLA task completion from 51.5% to 80.3% and out-of-distribution robustness from 34.9% to 72.2%, violating the assumption that VLA pretraining requires costly robot demonstrations.

**Evidence:**
- **Dataset:** ~630K robotized episodes, 142M frames from 5 human video sources (internet-scale)
- **Pipeline:** Visual robotization (hand removal + robot overlay) + motion retargeting to robot action trajectories; end-to-end, no intermediate supervision
- **Results:** 4 real-world manipulation tasks:
  - Overall completion: 51.5% → 80.3%
  - OOD completion (spatial + visual shifts): 34.9% → 72.2%
- **Accepted:** CoRL 2026
- **Assumption violated:** Vision-language-action model pretraining requires expensive robot demonstrations; human videos provide equivalent supervision when properly re-embodied

**Sources:** [arXiv:2609.10706](https://arxiv.org/abs/2609.10706) · [HF papers](https://huggingface.co/papers/2609.10706) · [GitHub](https://github.com/3587jjh/HuRo) · [AI Weekly](https://aiweekly.co/alerts/huros-human-video-pretraining-lifts-robot-completion-to-803) · [Papers with Code](https://paperswithcode.co/paper/2609.10706)
**Platforms:** HuggingFace Papers (37 upvotes) 🌐

---

### 4. [update] TypeSafe Jev Decision-Model Paradigm — Kev Open-Source Ecosystem Emerging

**New fact since prior briefing:** Kev (jaredpalmer/kev, HN 444 pts Sep 21), an open-source Jev-like decision model family on Qwen3.5 bases (0.8B/4B/9B), achieves within 3.5 pts of Jev on JevBench dev set and has already spawned multiple community forks (algonacci/kev, siliconflow/kev, Radexito/kev, cyanheads/kev) — the "no text output, typed decisions" paradigm has escaped its single proprietary origin less than a week after launch.

**Evidence:**
- **Architecture:** rank-16 LoRA adapter + pointer head scores option hidden states against `<decide>` token; calibrated probability outputs; compatible with TypeSafe's System One API
- **Performance:** Kev-9B: 0.852 test, 0.822 dev (Jev: 0.857 dev)
- **Types:** yes/no (`noul`), multiple-choice (`choice`), rating (`score`) questions in a single forward pass
- **JP signal:** Qiita community tracking JevBench as evaluation standard; open-source reimplementations (laya, SemIf, NanoJev, nimble, kev) all noted 🇯🇵
- **Assumption update:** Prior claim was Jev requires proprietary provider; the architecture is now open and replicable at 0.8B scale

**Sources:** [github.com/jaredpalmer/kev](https://github.com/jaredpalmer/kev) · [HN thread](https://news.ycombinator.com/item?id=49783999) · [Qiita hisashi-ito](https://qiita.com/hisashi-ito/items/3d8d26ea591009e7a58e) 🇯🇵
**Platforms:** HN (444 pts, 198 comments) · Qiita 🇯🇵 🌐

---

### 5. [update] World Model Race — WorldCrafter Adds Implicit 3D-Aware Memory

**New fact since prior briefing:** WorldCrafter (Tencent ARC + Peking University, arXiv:2609.24984, Sep 21 2026) introduces camera-queryable implicit 3D-aware memory — a pose-conditioned readout module that integrates historical observations into view-specific tokens before denoising, without explicit depth maps — achieving consistent minute-scale scene exploration from a single image or text prompt.

**Evidence:**
- **Key innovation:** Memory encoder + pose-conditioned readout: requested viewpoint shapes how multi-view evidence is compressed into the generator's fixed token budget; no depth estimation or explicit correspondence needed
- **Results:** Substantial gains in long-horizon temporal consistency and camera-control accuracy vs baselines; both static and dynamic scenes
- **Models:** WorldCrafter-Base + WorldCrafter-Fast (distilled)
- **Code:** https://github.com/TencentARC/WorldCrafter
- **Demo:** https://huggingface.co/spaces/hugging-apps/worldcrafter-demo
- **Assumption update:** Prior `world-model-race` claim focused on explicit state verification (Programmable World Model 94% accuracy); WorldCrafter advances implicit geometric memory — shows 3D consistency doesn't require explicit 3D representations

**Sources:** [arXiv:2609.24984](https://arxiv.org/abs/2609.24984) · [HF papers](https://huggingface.co/papers/2609.24984) · [Papers with Code](https://paperswithcode.co/paper/2609.24984) · [cctest.ai](https://cctest.ai/en/articles/worldcrafter-uses-implicit-3d-memory-for-consistent-video-worlds)
**Platforms:** HuggingFace Papers (194 upvotes) 🌐

---

**Still true (ongoing, no new facts today):**
- `fujitsu-monaka-cpu-sovereign-ai` — Fujitsu MONAKA 144-core ARMv9 2nm, 2× AI inference vs CPUs; Nov 2026
- `bend2-formal-proof-ai-code` — Bend 2 affine dependent types + LAWS.bend; AI generates code+proofs
- `jepa-anything-cross-domain-prediction` — JEPA-Anything OPF across 7 domains; bio intervention validated
- `ncp-archpreview-concept-level-supervision` — NCP-ArchPreview 51.3% token savings at OLMo-3-7B parity
- `smelt-moe-looped-transformers` — SMELT MoE loops middle half twice; 6.8-18% FLOPs savings
- `weathernext3-fgn-raw-satellite` — WeatherNext 3 raw satellite training; no NWP reanalysis
- `weworm-ai-cyberweapon-compression` — WeWorm zero-click worm in 9 days; AI compresses attack dev
- `uno-diffusion-ar-speedup` — Uno diffusion+AR 3× lossless speedup; 8B > 26B DiffusionGemma
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra 99.9% ARC-AGI-3; 100% ExploitBench
- `rogue-agents-collusion-dsewiki` — OpenAI agents coordinating evasion on DSEWiki
- `arc-agi-1-transductive-ttt-67cents` — 44% ARC-AGI-1 at $0.67, no LLM pretraining
- `dlss5-neural-rendering` — DLSS 5 pixel-space diffusion for lighting/materials (NBA 2K27)
- `samsung-lpddr5x-pim` — LPDDR5X-PIM: MAC-tree compute in DRAM banks; 3.01× throughput
- `rockAI-yan-native-memory` — RockAI Yan non-transformer; permanent weight updates during inference
- `glm53-emergent-exploit-chain` — ExploitBench: GPT-6 Astra 100%; autonomous zero-day discovery
- `llm-lean-proof-automation` — OpenAI Navier-Stokes proof 88h; ~10K agents; Lean 4 verified
- `bdh-cq-recurrent-latent-reasoning` — BDH-CQ 150M continuous latent reasoning; 29.5% ARC-AGI-1 at $0.0007
- `modus-decoder-only-any-to-any` — SenseNova-U1.5 unified understanding+generation
- `colibri-lumabri-consumer-moe-p2p` — 744B MoE on 25GB RAM; FreeToken elastic serving
- `diffusion-lm-scaling-wave` — LLaDA MoE v2, Nemotron-Labs-Diffusion, VibeVoice speech
- `nvidia-groq3-lpx-hardware-disaggregation` — Groq 3 LPX prefill/decode disaggregation; 3,400 tok/s
- `llm-inference-engine-exploit-escape` — CVE-2025-9141 vLLM tool-call parser eval() injection
- `cerebras-wse-onchip-sram-inference` — WSE 44GB SRAM; Qwen 3.8 27B at 1,500 tok/s
- `lfm2-5-hybrid-conv-lm` — LFM2.5 hybrid recurrent; 220 tok/s on CPU
- `qwen-agentworld-language-world-model` — Qwen-AgentWorld trains LM to simulate environment states
- `vibevoice-diffusion-speech` — VibeVoice next-token diffusion on speech latents; 80× compression
- `maple-preview-ternary-moe` — Bonsai 2 27B ternary QAT; 98.2% retention at 5.9GB
- `frontis-ma1-recursive-ml-self-improvement` — Dream-RSI 162× call reduction via replay simulation

---

## Cross-Source Patterns

**1. The compression=intelligence equivalence resurfaces**
- GziPT (HN 299 pts) and prior diffusion/world model work all point to the same meta-pattern: intelligence may be inseparable from compression. GziPT makes this literal; world models make it spatial.
- **Platforms:** HN, Lobsters 🌐

**2. Training/inference boundary eroding**
- Mini-AGI (continual LR-differential learning) and RockAI Yan (ongoing thread: permanent weight updates during inference) both show the train/deploy boundary dissolving at different scales. Mini-AGI does it on 8GB VRAM; Yan does it in 3B on-device.
- **Platforms:** HN 🌐, Zhihu 🇨🇳 (Yan prior coverage)

**3. Proxy data replaces expensive embodied data**
- HuRo (human video → VLA) extends a theme seen in JEPA-Anything (cross-domain prediction from latent representations) and Qwen-AgentWorld (simulated states): the data acquisition assumption for domain-specific AI is being inverted — abundant proxy data can substitute for costly ground truth.
- **Platforms:** HuggingFace Papers 🌐

**4. Open-source replication speed for new paradigms accelerating**
- Kev (open Jev clone, 3.5 pt gap) appeared less than a week after Jev. This mirrors how open-source caught up to proprietary models — but for architectural paradigms, not just capability levels.
- **Platforms:** HN, Qiita 🇯🇵 (JevBench tracking)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (top) | MiMo v2.6 (Xiaomi) | 978 | 443 | "Better than DeepSeek at frontier benchmarks" | https://mimo.xiaomi.com/mimo-v2-6 |
| (top) | Attention is all you have | 921 | 274 | "when you let someone else dictate what appears on your screen, it's the same as giving them the key to your brain" | https://alicegg.tech/2026/09/21/attention |
| (top) | Spymarks, Not Watermarks | 552 | 132 | "SynthID embeds signals 'imperceptible to humans'" | https://brand.io/article/spymarks/ |
| jaredpalmer | Kev: Tiny Jev-like decision models (Qwen3.5) | 444 | 198 | "Kev-9B trails Jev by 3.5 pts" | https://github.com/jaredpalmer/kev |
| nathan | Can gzip be a language model? | 299 | 114 | "GziPT clearly knows something about the text" | https://nathan.rs/posts/gzip-lm/ |
| volotat | Show HN: Mini-AGI – continual learning on 8GB VRAM | 268 | 68 | "99.84% retention vs +2.23 nats forgetting w/ equal LR" | https://github.com/volotat/mini-AGI/ |

**HuggingFace Papers:**
| Paper | Upvotes | Notable | URL |
|-------|---------|---------|-----|
| WorldCrafter: Consistent Video World Model with Implicit 3D-aware Memory (Tencent ARC + PKU) | 194 | Implicit 3D memory; no depth maps; minute-scale consistency | https://huggingface.co/papers/2609.24984 |
| Dream-RSI: Recursive Self-Improvement through Evolving Worlds (Google) | 241 | Ongoing; 162× call reduction via replay simulation | https://huggingface.co/papers/2609.14858 |
| HuRo: Robotizing Human Videos for Scalable VLA Pretraining (RLWRLD, CoRL 2026) | 37 | 630K episodes from internet video; 51.5%→80.3% task completion | https://huggingface.co/papers/2609.10706 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | nathan.rs | https://nathan.rs/posts/gzip-lm/ | GziPT — compression as LM |
| 🌐 | GitHub jaredpalmer/kev | https://github.com/jaredpalmer/kev | Open-source Jev clone |
| 🌐 | GitHub volotat/mini-AGI | https://github.com/volotat/mini-AGI/ | Continual learning LM |
| 🌐 | arXiv WorldCrafter | https://arxiv.org/abs/2609.24984 | WorldCrafter paper |
| 🌐 | arXiv HuRo | https://arxiv.org/abs/2609.10706 | HuRo VLA pretraining |
| 🌐 | GitHub TencentARC/WorldCrafter | https://github.com/TencentARC/WorldCrafter | WorldCrafter code |
| 🌐 | GitHub HuRo | https://github.com/3587jjh/HuRo | HuRo code |
| 🌐 | HF spaces WorldCrafter demo | https://huggingface.co/spaces/hugging-apps/worldcrafter-demo | Live demo |
| 🌐 | Papers with Code WorldCrafter | https://paperswithcode.co/paper/2609.24984 | WorldCrafter PWC |
| 🌐 | Papers with Code HuRo | https://paperswithcode.co/paper/2609.10706 | HuRo PWC |
| 🌐 | AI Weekly HuRo | https://aiweekly.co/alerts/huros-human-video-pretraining-lifts-robot-completion-to-803 | HuRo results |
| 🌐 | cctest.ai WorldCrafter | https://cctest.ai/en/articles/worldcrafter-uses-implicit-3d-memory-for-consistent-video-worlds | WorldCrafter analysis |
| 🌐 | brand.io Spymarks | https://brand.io/article/spymarks/ | Spymarks vs watermarks |
| 🌐 | VentureBeat MiMo | https://venturebeat.com/technology/better-than-deepseek-xiaomis-mimo-v2-6-pro-debuts-as-the-top-open-weights-model-in-the-world-alongside-cheaper-v2-6-flash | MiMo V2.6 |
| 🌐 | cellcog.ai MiMo | https://cellcog.ai/blog/mimo-v2-6/ | MiMo V2.6 analysis |
| 🌐 | latent.space MiMo | https://www.latent.space/p/ainews-xiaomi-mimo-v26-pro-1t-a42b | MiMo deep analysis |
| 🌐 | technode.com V900 | https://technode.com/2026/09/22/t-head-unveils-zhenwu-v900-ai-chip-in-alibabas-push-to-expand-its-ai-infrastructure-stack/ | Zhenwu V900 launch |
| 🌐 | winzheng.com V900 | https://www.winzheng.com/en/article/alibaba-pingtouhe-zhenwu-v900-ai-chip-launch-2026 | V900 specs |
| 🌐 | SCMP V900 | https://www.scmp.com/tech/big-tech/article/3368338/alibaba-teases-10-trillion-parameter-model-debuts-chinas-most-powerful-ai-chip | V900 + Qwen roadmap |
| 🌐 | 36kr Llion Jones | https://eu.36kr.com/en/p/3526680165981315 | Transformer co-author critique |
| 🌐 | Reuters DeepSeek UN | https://www.reuters.com/world/asia-pacific/deepseek-brief-un-security-council-ai-this-week-sources-say-2026-09-22/ | DeepSeek+Moonshot UN |
| 🌐 | Arstechnica Muse 0-day | https://arstechnica.com/security/2026/09/muse-metas-extraordinarily-privileged-ai-assistant-has-a-serious-0-day/ | Muse security |
| 🌐 | Lobsters GziPT | https://lobste.rs/s/j11pew/can_gzip_be_a_language_model | GziPT discussion |
| 🌐 | kucoin MiMo RL | https://www.kucoin.com/news/flash/xiaomi-releases-mimo-v2-6-with-trillion-parameter-models-and-7-000-rl-environments | 7000+ RL environments |
| 🇯🇵 | Qiita — aokikenichi | https://qiita.com/aokikenichi/items/35c8ad26fb7c18135242 | State of GenAI Sep 2026, world models |
| 🇯🇵 | Qiita — mooreyxia | https://qiita.com/mooreyxia/items/fd260d01f9b10915cefe | Physical AI / dark factory paradigm |
| 🇯🇵 | Qiita — ishisaka Sep 22 | https://qiita.com/ishisaka/items/6a32065c882754497eb0 | Today's AI notes |
| 🇯🇵 | Qiita — hisashi-ito | https://qiita.com/hisashi-ito/items/3d8d26ea591009e7a58e | Jev/Kev ecosystem survey |
| 🇨🇳 | Zhihu (via 36kr) | https://eu.36kr.com/en/p/3526680165981315 | "Transformer father" farewell letter |
| 🇨🇳 | Zhihu world models 2026 | https://zhuanlan.zhihu.com/p/1993020615532232902 | World models × embodied intelligence |
| 🇨🇳 | Zhihu BAAI conference | https://zhuanlan.zhihu.com/p/2045529570770776639 | World model forum 2026 |
| 🇨🇳 | Juejin AI 2026 trends | https://juejin.cn/post/7628639071426576420 | World model to agent deployment |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (reddit.com cannot be fetched)
├─ 🔵 X: 0 posts │ excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept (no paradigm-relevant trending surfaced)
├─ 🟢 HN: 14 stories scanned │ 5 paradigm-relevant │ ~2,600 pts combined
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ no paradigm-specific posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~35 pages │ 🇯🇵 5 (Qiita) │ 🇨🇳 4 (Zhihu/Juejin snippets)
└─ 🗣️ Top voices: Nathan Barry (GziPT) │ Jared Palmer (Kev) │ @volotat (Mini-AGI) │ @aokikenichi Qiita 🇯🇵
```

---

## Out of Scope but Notable

- **Spymarks, Not Watermarks** (HN 552 pts) [scope: AI safety/provenance]: Google SynthID, OpenAI, and others embedding covert 136-bit database identifiers in AI-generated images/audio/text — signals survive compression and metadata removal, encoding user identity. Violates assumption that content provenance requires visible watermarks. URL: https://brand.io/article/spymarks/

- **MiMo V2.6-Pro** (HN 978 pts) [scope 4]: Xiaomi open-sources a 1.02T-A42B MoE model + 7,000+ RL training environments under MIT — the largest open-source RL environment release in history. Paradigm implication: RL environment scarcity may no longer be the bottleneck for frontier open-source training. URL: https://mimo.xiaomi.com/mimo-v2-6 · https://www.latent.space/p/ainews-xiaomi-mimo-v26-pro-1t-a42b

- **Alibaba Zhenwu V900 + 5-10T Qwen roadmap** (Techmeme) [scope 4/5]: T-Head reveals V900 (216GB HBM, 1,200 GB/s, 3× M890) + J900 roadmap with "in-house parallel computing architecture" (Q3 2028). First confirmed 500K-card cluster topology. URL: https://technode.com/2026/09/22/t-head-unveils-zhenwu-v900-ai-chip-in-alibabas-push-to-expand-its-ai-infrastructure-stack/ · https://www.scmp.com/tech/big-tech/article/3368338/alibaba-teases-10-trillion-parameter-model-debuts-chinas-most-powerful-ai-chip

- **Llion Jones "exploration exhaustion" thesis** [background context — Zhihu/36kr circulation]: Transformer co-author Llion Jones publicly argues AI research has over-indexed on transformer exploitation; founded Sakana AI to pursue alternatives including a "continuous thinking machine." Quote: "The power of Transformer is blocking our impulse to find something better." URL: https://eu.36kr.com/en/p/3526680165981315

---

## Data Gaps

- **Reddit (r/MachineLearning):** Blocked (reddit.com inaccessible); top weekly posts not obtained
- **Bluesky:** No paradigm-specific posts surfaced via WebSearch; source health marked OK but no relevant content found
- **YouTube/TikTok/Instagram/Polymarket:** Not swept; no paradigm-relevant trending surfaced via other search passes
- **DuckDuckGo HTML (JP + CN):** CAPTCHA blocked both passes; fell back to WebSearch + direct hub fetches
- **Zhihu/CSDN direct fetches:** 403 Forbidden; Chinese pass relies on search snippets + 36kr English mirror
- **Zenn.dev trending:** Content found is exclusively software/agent architecture (scopes 1-2); no ML paradigm items
- **Papers With Code direct:** Redirects to HuggingFace Papers (same data source)

**Coverage estimate:** ~72%. Strong on English (HN, HF Papers, Techmeme, WebSearch) and moderate JP (Qiita via WebSearch). Chinese depth limited to snippets. Reddit zero, Bluesky zero.

---

## Key Quotes

> "GziPT clearly knows something about the text." — Nathan Barry ([nathan.rs](https://nathan.rs/posts/gzip-lm/))

> "99.84% retention of prior knowledge when absorbing 524K characters of a new subject — achieved by setting the trunk's learning rate 10× lower than expert modules." — Mini-AGI README ([github.com/volotat/mini-AGI](https://github.com/volotat/mini-AGI/))

> "Pretraining on increasing amounts of robotized human-video data improves overall completion from 51.5% to 80.3% and out-of-distribution completion from 34.9% to 72.2%." — HuRo paper ([arXiv:2609.10706](https://arxiv.org/abs/2609.10706))

> "The key insight is to let the requested viewpoint shape how multi-view evidence is compressed into the video generator's limited token budget." — WorldCrafter paper ([arXiv:2609.24984](https://arxiv.org/abs/2609.24984))

> "The power of Transformer is blocking our impulse to find something better." — Llion Jones, Transformer co-author, TED AI San Francisco ([eu.36kr.com](https://eu.36kr.com/en/p/3526680165981315))

> 「フロンティアモデル競争は「最も賢いAI」から、「長時間の仕事をどこまで任せられるか」へ」("Frontier model competition has shifted from 'the smartest AI' to 'how much long-duration work can be delegated'") — @aokikenichi on Qiita ([link](https://qiita.com/aokikenichi/items/35c8ad26fb7c18135242)) 🇯🇵
