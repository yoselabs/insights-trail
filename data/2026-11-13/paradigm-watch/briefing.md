# Paradigm Watch — Daily Briefing
**Date:** 2026-11-13
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Daily Papers, HuggingFace Trending, GitHub Trending, Techmeme, WebSearch (global), WebSearch (🇯🇵 Japanese), WebSearch (🇨🇳 Chinese), Zenn, note.com, Qiita, qiaomu.ai, BuildApp News

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~22 stories scanned; 1 paradigm-relevant | AI/Gödel: 74 pts/6 comments | 🌐 |
| HuggingFace Daily Papers | ~29 scanned; 5 paradigm-relevant | BirdDreams 45↑; PhysLoop 41↑; G-STAR 40↑; Duo 34↑; WICL 56↑ (trending) | 🌐 |
| HuggingFace Trending | ~20 scanned; 3 ongoing | LingBot-Touch 102↑; VibeVoice 186↑; FreeToken 111↑ | 🌐 |
| GitHub Trending | ~6 repos; 0 paradigm-relevant | Dominated by scope 1-2 agent tooling | 🌐 |
| Techmeme | ~20 stories; 0 paradigm-relevant | Jensen Huang/Nvidia scandal; Anthropic IPO | 🌐 |
| Bluesky | — | Health OK; no paradigm posts surfaced | 🌐 |
| Web (global) | ~38 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~7 pages | — | 🇯🇵 Qiita ×2, Zenn ×1, note ×1, BuildApp News ×1, AlphaXiv ×1 |
| Web (China) | ~6 pages | — | 🇨🇳 qiaomu.ai ×3, Sohu ×1, Juejin ×1, Huxiu ×1 |

---

## Synthesized Findings

### 1. [update] AI-Driven Formal Reasoning Extends to Historical Mathematical Archives — Gödel's Notebooks

**New fact since prior briefing:** Claude analyzed 1,009 pages of Gödel's unpublished 1940s notebooks, surfacing 663 theorems/proof ideas; ~400 verified with Coq as stated, ~200 needed repairs, ~50 were false. First systematic AI-driven mathematical archaeology of a deceased mathematician's unpublished archive.

**Assumption violated:** Mathematical archaeology from handwritten historical archives requires specialized human logicians; AI cannot navigate obsolete shorthand or reconstruct incomplete proof sketches.

- **Researcher:** Jan von Plato, University of Helsinki (project since 2017)
- **Source material:** 16 workbooks, 1,009 pages in Gabelsberger shorthand (obsolete when Gödel wrote it, 1940s)
- **Method:** Von Plato supplied Claude with his own transcriptions + 6 scholarly books on Gödel; Claude produced 650-page analysis in days
- **Results:** 663 theorems/proof ideas → ~400 verified with Coq as stated, ~200 required repairs, ~50 false
- **Epistemological caveat:** Mathematical validity ≠ historical authorship. Joel David Hamkins: "how much is Claude and how much is Gödel is a job for the historians"
- **Connection to prior thread:** Extends `llm-lean-proof-automation` (AlphaProof Code, Fable 5.2) — AI formal reasoning now reaching not just current deployed code but century-scale historical mathematical archives

**Sources (🌐):**
[Guardian](https://www.theguardian.com/science/2026/nov/13/kurt-godel-notebooks-ai-helps-unlock-hidden-discoveries-man-who-transformed-maths) · [superpowerdaily](https://superpowerdaily.com/posts/claude-surfaced-663-theorems-and-proof-ideas-in-g-del-s-notebooks-researcher-says) · [mezha.net](https://mezha.net/eng/news/mezha-5bfca8e96e5185cfd3400769_claude_helps_uncover/)
**JP (🇯🇵):** [Qiita/picnic (Fermat context)](https://qiita.com/picnic/items/b2a6ccfa366ff7fe29ba)
**Platforms:** HN (74 pts/6 comments), Guardian, global news

---

### 2. [new] G-STAR — 32-64× Compression for Discrete Autoregressive Image Generation (20× Speedup)

**Assumption violated:** Extreme spatial compression in discrete autoregressive image generation inevitably degrades representation quality; the compression-quality tradeoff is a fundamental constraint, not an addressable design choice.

- **Team:** DAGroup-PKU (Peking University / various), arXiv:2611.13004, Nov 8
- **Core principle:** Group size of product-quantized tokenizer should scale **quadratically** with per-axis spatial compression factor under fixed nominal information budget → "spatial-group co-scaling" preserves representation capacity at extreme compression
- **Semi-autoregressive decoder:** Models within-group dependencies efficiently; enables parallel computation within groups + lightweight causal modeling across groups
- **Numbers:**
  - 32× and effective **64× compression**
  - **20× speedup** over prior discrete AR image generation models
  - 1024×1024 generation in **2.5 seconds** on single NVIDIA H200
  - Competitive across 5 text-to-image benchmarks (GenEval, DPG-Bench, PRISM, LongText-Bench, Qwen-Image-Bench)
- **CN framing (🇨🇳):** "G-STAR不仅仅是调整压缩比，而是提出了一条协调这种权衡的基本原理" / "G-STAR does not merely adjust compression ratios but proposes a fundamental principle for coordinating the tradeoff" — qiaomu.ai
- **Code:** https://github.com/DAGroup-PKU/G-STAR

**Sources (🌐):**
[arXiv:2611.13004](https://arxiv.org/abs/2611.13004) · [GitHub](https://github.com/DAGroup-PKU/G-STAR) · [Papers With Code](https://paperswithcode.co/paper/2611.13004) · [ArXivSignals](https://arxivsignals.io/papers/2611.13004)
**CN (🇨🇳):** [qiaomu.ai rewrite](https://rss.qiaomu.ai/articles/g-star-%E9%9D%A2%E5%90%91%E6%B7%B1%E5%BA%A6%E5%8E%8B%E7%BC%A9%E8%87%AA%E5%9B%9E%E5%BD%92%E7%94%9F%E6%88%90%E7%9A%84%E7%BB%84%E7%BC%A9%E6%94%BE-token-%E5%AE%B9%E9%87%8F--2b60154bd0ce)
**Platforms:** HuggingFace (40↑), qiaomu.ai (CN)

---

### 3. [new] WICL / RoboScript — Frozen Robot Policy Outperforms Trained Baselines via Simulation Context

**Assumption violated:** Robots require large training datasets and weight updates to achieve high manipulation success; a frozen foundation model cannot match task-trained policies on dexterous manipulation.

- **Team:** ArcheOne-AI, arXiv:2611.12885, Nov 11
- **Paradigm:** World In-Context Learning (WICL) — frozen foundation model learns from 1 demonstration by rehearsing in simulation; writes learned knowledge as "Task Memory" to context, not to weights
- **Key insight:** "What an agent learns in context is semantic, recording task steps and object roles rather than visual appearance" → enables cross-visual-distribution transfer
- **Numbers:**
  - **83.4% mean success** across all 50 RoboTwin 2.0 tasks (clean + randomized settings)
  - **+20 percentage points** above strongest trained action policy
  - **1 demonstration per task, 0 gradient updates**
- **Transfer:** Cross-embodiment to physical dual-arm robot; generalizes across visual distributions via reflection
- **Independent caveat (aiweekly.co):** "If independently verified, [this] could challenge the conventional wisdom that teams need large data-collection infrastructure" — no physical hardware success rates disclosed
- **Code:** https://github.com/ArcheOne-AI/RoboScript

**Sources (🌐):**
[arXiv:2611.12885](https://arxiv.org/abs/2611.12885) · [GitHub/RoboScript](https://github.com/ArcheOne-AI/RoboScript) · [aiweekly.co](https://aiweekly.co/alerts/roboscript-hits-834-on-robotwin-20-from-one-demo-per-task) · [hyper.ai](https://hyper.ai/en/papers/2611.12885) · [tokenpost](https://www.tokenpost.com/news/technology/55069) · [ArXivSignals](https://arxivsignals.io/papers/2611.12885)
**Platforms:** HuggingFace (56↑ trending)

---

### 4. [update] World-Model Race — Duo (Cognition-as-World) + BirdDreams (Joint BEV+Perspective) Both Drop Nov 10-11

**New facts since prior briefing:** (a) Duo v1 (Ant Group inclusionAI, arXiv:2611.15131, Nov 11): Reciprocal World Model treating cognition as intrinsic to the world, not an external controller; 153 GB open weights released; full-duplex audio-video-text interaction. (b) BirdDreams (arXiv:2611.14815, Nov 10, HF 45↑): first driving world model that jointly generates perspective + BEV video; eliminates need for pre-specified scene layout inputs.

**Assumption violated (Duo):** World models simulate physical reality with reasoning as an external module; cognition and world modeling are necessarily separate components.
**Assumption violated (BirdDreams):** Driving world models require pre-specified future vehicle trajectories or HD maps as conditioning inputs; layout cannot be generated jointly with ego video.

#### Duo: Reciprocal World Model
- **Framework:** RWM treats intelligence AND physical reality as equally fundamental; cognition intrinsic to the world model
- **Two modules:** Intent (Qwen3VL-based, decides when/what to say) + Realization (MiniMax H3-based, generates video+audio)
- **Weights:** 153 GB open weights across 4 HF repositories (released Nov 12 by Ant Group inclusionAI)
- **Latency:** 330-650ms (8-GPU tensor parallelism); 708ms chunk cycle (17 video frames @ 24fps + audio)
- **Territorial restriction:** License excludes US, UK, EU, South Korea (inherited from MiniMax H3)
- **CN framing (🇨🇳):** "让模型一边持续看和听，一边实时回应你，也就是真正的全双工交互" / "enabling the model to continuously perceive while responding in real time — genuine full-duplex interaction"

#### BirdDreams: Joint Perspective+BEV Driving World Model
- **Architecture:** Two coupled video diffusion-transformer branches (perspective + BEV) with joint attention throughout denoising
- **BEV format:** Roads and vehicles as simple shapes at fixed metric scale; reduced occlusion
- **Key elimination:** No future vehicle trajectories, HD maps, or vehicle-state inputs required
- **Results:** Outperforms prior driving world models on PhysicalAI-AV + nuScenes ego trajectory following; more plausible ego motion without ego-action conditioning; superior surrounding-vehicle behavior in human evaluation
- **CN framing (🇨🇳):** "把场景布局变成预测未来的一部分，而不是预设输入" / "makes scene layout part of the predicted future, not a preset input"

**Sources — Duo (🌐):**
[arXiv:2611.15131](https://arxiv.org/abs/2611.15131) · [HuggingFace](https://huggingface.co/papers/2611.15131) · [orcarouter.ai](https://www.orcarouter.ai/blog/duo-1-0-causal-base-quiet-weights-release) · [paperswithcode](https://paperswithcode.co/paper/2611.15131) · [interconnects.ai](https://www.interconnects.ai/p/inside-a-chinese-frontier-lab-inclusion) · [scmp.com](https://www.scmp.com/tech/big-tech/article/3341842/ant-groups-open-source-push-aims-move-robots-lab-demos-real-world-work)
**CN (🇨🇳):** [qiaomu.ai Duo](https://rss.qiaomu.ai/articles/duo-%E9%9D%A2%E5%90%91%E5%85%A8%E5%8F%8C%E5%B7%A5%E4%BA%A4%E4%BA%92%E7%9A%84%E4%BA%92%E6%83%A0%E4%B8%96%E7%95%8C%E6%A8%A1%E5%9E%8B--9997292c8a19)

**Sources — BirdDreams (🌐):**
[arXiv:2611.14815](https://arxiv.org/abs/2611.14815) · [HuggingFace](https://huggingface.co/papers/2611.14815) · [paperswithcode](https://paperswithcode.co/paper/2611.14815)
**CN (🇨🇳):** [qiaomu.ai BirdDreams](https://rss.qiaomu.ai/articles/birddreams-%E8%81%94%E5%90%91%E8%A7%86%E8%A7%92%E4%B8%8E-bev-%E8%A7%86%E9%A2%91%E7%94%9F%E6%88%90-%E6%9E%84%E5%BB%BA%E5%8F%AF%E4%BF%A1%E5%8F%AF%E5%93%8D%E5%BA%94%E7%9A%84%E9%A9%BE%E9%A9%B6%E4%B8%96%E7%95%8C%E6%A8%A1%E5%9E%8B--9a1af963defb)
**Platforms:** HuggingFace (Duo 34↑, BirdDreams 45↑), Qiaomu.ai (CN)

---

### 5. [update] RSI Surface Diversification — PhysLoop Applies LLM-Guided RSI to Video Generation Physics Quality

**New fact since prior briefing:** PhysLoop (arXiv:2611.16748, Nov 12, HF 41↑) applies recursive self-improvement logic to video generation: LLMs constrain/guide → generation → selection → LLM correction cycle; distills physical knowledge into physically consistent training videos with limited human intervention.

- **New RSI surface:** Video generation physics quality — previously RSI surfaces covered model weights (WSP), training infrastructure config (InfraRSI), architecture (NAS), reasoning (R1/R2). PhysLoop adds synthetic data quality as a new RSI layer.
- **Dataset released:** 100K videos across diverse indoor/outdoor scenes
- **Evaluation:** PhysLoop-Gen + PhysLoop-Repair benchmarks; external Physics-IQ Verified benchmark
- **RSI claim:** "marks a key milestone toward recursive self-improvement in video generation models with limited human intervention"

**Sources (🌐):**
[arXiv:2611.16748](https://arxiv.org/abs/2611.16748) · [HuggingFace](https://huggingface.co/papers/2611.16748) · [paperswithcode](https://paperswithcode.co/paper/2611.16748)
**Platforms:** HuggingFace (41↑)

---

**Still true** (ongoing, no new facts today):

- `vflash-parallel-spatial-primitive-decoding` — NVIDIA VFlash: parallel diffusion drafter for spatial primitives beats AR accuracy at 25×; 61% 3D error reduction (Nov 5-6)
- `muir-linear-attention-asymmetric-gating` — Google Muir: 1M-token recall at 25MB state vs 2.1TB KV cache; 2.7× faster at 32K (Nov 5)
- `speculative-listening-idle-speech-drafting` — Speculative Listening: 95.3% idle → draft speech during silence; 73% latency reduction (Nov 2026)
- `weight-space-programming-mit-csail` — MIT CSAIL: frontier LLMs read/write NN weights without gradients; Honnibal debunking ongoing (Nov 3)
- `library-of-layers-adaptive-ordering` — LoL: router orders transformer blocks dynamically at runtime (Nov 2)
- `qwenputer-compiled-cpu-in-weights` — RISC-V CPU + Doom compiled into Qwen3.5-4B weights; HN 690/145 (Oct 22)
- `jepa-platonic-representation-theorem` — LeCun+Balestriero: JEPAs with good views learn same representation; 109M JEPA out-aligns 72B LMs (Oct 29)
- `worldtui-terminal-world-model` — WorldTUI 360M: simulates terminal (vim/tmux/snake) without running commands (Oct 21)
- `anthropic-formal-verification-assembly` — Claude+Theorem Labs: 239 OSS-Fuzz entry points, 180M Rocq lines at RISC-V assembly level (Oct 22)
- `fable-steganography-emergent-communication` — Fable 5.1: emergent steganography in SVG via height-as-alphabet; 78% cross-model decode (Oct 21)
- `voxcpm2-tokenizer-free-tts` — VoxCPM2: continuous diffusion-AR bypasses discrete TTS tokenization; 30 languages (Oct 23)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra: embodied competence threshold crossed in simulation; real-world gap persists (Oct 23)
- `ncm-coarse-to-fine-parallel-generation` — NCM: 10-31× speedup over diffusion LMs; no noise process needed (Oct 20)
- `fleet-learning-collective-robots` — AgiBot fleet: binary outcome learning → 97.3% success, no expert demos (Oct 20)
- `competing-learning-hybrid-architectures` — Tsinghua: SSM/attention competing learning; BLD fix restores division of labor (Oct 20)
- `goodfire-neural-networks-clean` — Goodfire: 90% neurons single-job; polysemanticity paradigm challenged (Oct 15)
- `minions-distributed-apple-silicon-gpu` — FreeToken 111↑ still trending; 753B at 14.9 tok/s on single workstation GPU (ongoing)
- `typesafe-jev-system-one-models` — TypeSafe Jev + OpenAI Decisions API GA; SO-Arena benchmarking paper (71 HF↑ today) is scope 2/5
- `rogue-agents-collusion-dsewiki` — S. Korea bank hacks; ECHOTRIBBLE autonomous cyber (Oct 20)
- `diffusion-lm-scaling-wave` — VibeVoice 186↑ still trending; FewStepRL (Tencent, Nov 5)
- `yue2-ar-nar-music-unification` — YuE2 AR-NAR MoT; beats Suno v5/v6 (last seen Oct 27)
- `lingbot-touch-tactile-foundation-model` — LingBot-Touch now 102 HF↑ (up from 92 on Nov 10; no new facts)
- `sage-taiyi-metacognitive-science` — Sage-Taiyi 54.0 vs AI Scientist-v2 47.9; carbonylation trace→84% (Nov 9)
- `energy-tweedie-score-energy-bridge` — Energy-Tweedie NeurIPS 2026: extends Tweedie's formula to arbitrary Gibbs distributions (Nov 7)

---

## Cross-Source Patterns

**1. World models as default frame for physical AI — global consensus (🌐 HF × 🇨🇳 Zhihu/CSDN/Huxiu × 🇯🇵 Zenn/note)**
- BirdDreams + Duo (HF): two new world model variants on same day
- CN: "2026, 世界模型×具身智能" (world model × embodied intelligence) as consensus direction; "AGI year for robotics"; NSP (Next-State Prediction) replacing next-token prediction
- JP: Three-stage AI evolution (Perception → Generative → World Model AI); "LLM + world model" as coexisting paradigms requiring strategic task allocation
- Pattern: World model framing has completed its shift from research curiosity to industry consensus across all three regions

**2. Context-over-weights as alternative learning paradigm (🌐 HF)**
- WICL/RoboScript: frozen policy via simulation-context beats trained baselines
- Earlier threads: Weight Space Programming (frontier LLM edits NN weights without gradients), Library of Layers (dynamic block routing at runtime)
- Pattern: Multiple independent lines of work converging on the idea that model weights need not be the primary site of learning/computation — context, routing, and external state are increasingly doing the work weights did before

**3. RSI stack growing layer by layer (🌐 HF)**
- InfraRSI (Nov 8): RSI applied to training infrastructure config
- PhysLoop (Nov 12): RSI applied to synthetic video physics quality
- Prior layers: model weights (WSP), architecture (NAS/AutoML), reasoning (R1/R2)
- Pattern: RSI is becoming a general optimization strategy applied bottom-up through every layer of the AI stack

---

## Per-Platform Tables

**Hacker News:**

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (various) | AI unlocks Gödel's notebooks | 74 | 6 | "how much is Claude and how much is Gödel is a job for the historians" — Hamkins | https://www.theguardian.com/science/2026/nov/13/kurt-godel-notebooks-ai-helps-unlock-hidden-discoveries-man-who-transformed-maths |
| (various) | Jensen Huang resigns (not paradigm) | 3,949 | 3,360 | Dominant story, all scope 4 | https://apnews.com/article/nvidia-megaspeed-china-singapore-huang-5403f152a601cf82ce939f1d24fffa0f |

**HuggingFace Daily Papers (paradigm-relevant):**

| Paper | ↑ | arXiv | Assumption Violated |
|-------|---|-------|---------------------|
| BirdDreams: Joint Perspective+BEV Driving World Model | 45 | 2611.14815 | Scene layout must be provided as input to driving world models |
| PhysLoop: LLM Physics Awareness for Self-Improving Video Generation | 41 | 2611.16748 | Physics-consistent video requires human annotation; RSI cannot improve synthetic data quality |
| G-STAR: Group-Scaled Token Capacity for Deeply Compressed AR Generation | 40 | 2611.13004 | Extreme spatial compression in discrete AR generation degrades representation quality |
| Duo: A Reciprocal World Model for Full-Duplex Interaction | 34 | 2611.15131 | Cognition is external to world models; world models model only physical reality |
| World In-Context Learning / RoboScript | 56* | 2611.12885 | Robot policies require large training datasets and weight updates to achieve high success |

*on HF trending

**GitHub Trending (paradigm-relevant today): none** — dominated by scope 1-2 agent tooling (openai/codex-security +754, alibaba/open-code-review +206, GoogleChrome/modern-web-guidance-src +1,875).

**Techmeme (paradigm-relevant today): none** — Jensen Huang/Nvidia scandal (scope 4), Anthropic IPO (scope 5).

**Web:**

| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Guardian | https://www.theguardian.com/science/2026/nov/13/kurt-godel-notebooks-ai-helps-unlock-hidden-discoveries-man-who-transformed-maths | Gödel notebooks original story |
| 🌐 | superpowerdaily | https://superpowerdaily.com/posts/claude-surfaced-663-theorems-and-proof-ideas-in-g-del-s-notebooks-researcher-says | 663 theorems; Coq verification breakdown |
| 🌐 | mezha.net | https://mezha.net/eng/news/mezha-5bfca8e96e5185cfd3400769_claude_helps_uncover/ | Supporting Gödel coverage |
| 🌐 | arXiv:2611.13004 | https://arxiv.org/abs/2611.13004 | G-STAR paper |
| 🌐 | DAGroup-PKU/G-STAR | https://github.com/DAGroup-PKU/G-STAR | G-STAR code |
| 🌐 | paperswithcode (G-STAR) | https://paperswithcode.co/paper/2611.13004 | G-STAR benchmarks |
| 🌐 | arXiv:2611.12885 | https://arxiv.org/abs/2611.12885 | WICL paper |
| 🌐 | ArcheOne-AI/RoboScript | https://github.com/ArcheOne-AI/RoboScript | WICL code |
| 🌐 | aiweekly.co (RoboScript) | https://aiweekly.co/alerts/roboscript-hits-834-on-robotwin-20-from-one-demo-per-task | 83.4% result + independence caveat |
| 🌐 | hyper.ai (WICL) | https://hyper.ai/en/papers/2611.12885 | WICL coverage |
| 🌐 | tokenpost (WICL) | https://www.tokenpost.com/news/technology/55069 | WICL coverage |
| 🌐 | arxivsignals (WICL) | https://arxivsignals.io/papers/2611.12885 | WICL signal |
| 🌐 | arXiv:2611.15131 | https://arxiv.org/abs/2611.15131 | Duo paper |
| 🌐 | HuggingFace (Duo) | https://huggingface.co/papers/2611.15131 | Duo 34↑ |
| 🌐 | orcarouter.ai (Duo) | https://www.orcarouter.ai/blog/duo-1-0-causal-base-quiet-weights-release | 153 GB weights analysis; territorial restriction |
| 🌐 | paperswithcode (Duo) | https://paperswithcode.co/paper/2611.15131 | Duo coverage |
| 🌐 | interconnects.ai | https://www.interconnects.ai/p/inside-a-chinese-frontier-lab-inclusion | Ant Group inclusionAI strategy |
| 🌐 | scmp.com | https://www.scmp.com/tech/big-tech/article/3341842/ant-groups-open-source-push-aims-move-robots-lab-demos-real-world-work | Ant Group open-source framing |
| 🌐 | arXiv:2611.14815 | https://arxiv.org/abs/2611.14815 | BirdDreams paper |
| 🌐 | HuggingFace (BirdDreams) | https://huggingface.co/papers/2611.14815 | BirdDreams 45↑ |
| 🌐 | paperswithcode (BirdDreams) | https://paperswithcode.co/paper/2611.14815 | BirdDreams benchmarks |
| 🌐 | arXiv:2611.16748 | https://arxiv.org/abs/2611.16748 | PhysLoop paper |
| 🌐 | HuggingFace (PhysLoop) | https://huggingface.co/papers/2611.16748 | PhysLoop 41↑ |
| 🌐 | paperswithcode (PhysLoop) | https://paperswithcode.co/paper/2611.16748 | PhysLoop coverage |
| 🌐 | llm-releases.com | https://www.llm-releases.com/labs/ant-group | Ant Group releases context |
| 🌐 | haddyalchaer.com | https://haddyalchaer.com/jepa | 600 JEPA experiments (HN 6 pts; low engagement) |
| 🇯🇵 | Qiita/picnic (Fermat) | https://qiita.com/picnic/items/b2a6ccfa366ff7fe29ba | Sept 2026 Fermat context (11 days / Lean) |
| 🇯🇵 | Zenn/taniii_shio (world models) | https://zenn.dev/taniii_shio/articles/311b721b7d9782 | World models March 2026; SSM/Mamba for WM |
| 🇯🇵 | note.com/naren_bao | https://note.com/naren_bao/n/nefd15c8193ac | World Models → Physical AI; 3 stages of AI |
| 🇯🇵 | BuildApp News | https://news.build-app.jp/article/39594/ | LLM×WM coexistence; "intersection of language and physical law" |
| 🇨🇳 | qiaomu.ai (G-STAR) | https://rss.qiaomu.ai/articles/g-star-%E9%9D%A2%E5%90%91%E6%B7%B1%E5%BA%A6%E5%8E%8B%E7%BC%A9%E8%87%AA%E5%9B%9E%E5%BD%92%E7%94%9F%E6%88%90%E7%9A%84%E7%BB%84%E7%BC%A9%E6%94%BE-token-%E5%AE%B9%E9%87%8F--2b60154bd0ce | G-STAR CN framing |
| 🇨🇳 | qiaomu.ai (Duo) | https://rss.qiaomu.ai/articles/duo-%E9%9D%A2%E5%90%91%E5%85%A8%E5%8F%8C%E5%B7%A5%E4%BA%A4%E4%BA%92%E7%9A%84%E4%BA%92%E6%83%A0%E4%B8%96%E7%95%8C%E6%A8%A1%E5%9E%8B--9997292c8a19 | Duo CN framing; "conceptual shift" |
| 🇨🇳 | qiaomu.ai (BirdDreams) | https://rss.qiaomu.ai/articles/birddreams-%E8%81%94%E5%90%88%E8%A7%86%E8%A7%92%E4%B8%8E-bev-%E8%A7%86%E9%A2%91%E7%94%9F%E6%88%90-%E6%9E%84%E5%BB%BA%E5%8F%AF%E4%BF%A1%E5%8F%AF%E5%93%8D%E5%BA%94%E7%9A%84%E9%A9%BE%E9%A9%B6%E4%B8%96%E7%95%8C%E6%A8%A1%E5%9E%8B--9a1af963defb | BirdDreams CN framing |
| 🇨🇳 | Sohu | https://www.sohu.com/a/980715205_122619244 | Multi-architecture trend; CAS 瞬悉1.0 non-Transformer |
| 🇨🇳 | Juejin | https://juejin.cn/post/7628639071426576420 | NSP paradigm; embodied intelligence |
| 🇨🇳 | Huxiu | https://www.huxiu.com/article/4893452.html | World models as "AGI year for robotics" |
| 🇨🇳 | DAMO/CSDN | https://damodev.csdn.net/6a4db5d310ee7a33f288f735.html | World models + embodied intelligence 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (persistent — all runs)
├─ 🔵 X: excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~22 stories scanned │ 1 paradigm-relevant │ top paradigm: AI/Gödel 74 pts/6 comments │ dominant: Jensen Huang 3,949 pts
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ health OK; no paradigm posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~38 pages │ 🇯🇵 7 (Qiita ×2, Zenn ×1, note ×1, BuildApp ×1, AlphaXiv ×1) │ 🇨🇳 7 (qiaomu.ai ×3, Sohu ×1, Juejin ×1, Huxiu ×1, DAMO ×1)
└─ 🗣️ Top voices: Jan von Plato (U Helsinki / Gödel) | DAGroup-PKU (G-STAR) | ArcheOne-AI (WICL) | Ant Group inclusionAI (Duo) | Junyoung Seo (BirdDreams)
```

---

## Out of Scope but Notable

This IS the paradigm-watch topic — findings above are the paradigm-watch output.

Non-paradigm items seen on trending surfaces today:
- **Jensen Huang resigns** (HN 3,949/3,360, AP News): Nvidia CEO exits amid chip smuggling scandal + personal conduct allegations — scope 4 (geopolitics/open models)
- **Gemini 4 Hydrogen + Google Antigravity** (HN 483/159): Orchestrator dynamically switches Carbon/Hydrogen mid-task — scope 1-2 (agent harnesses); "Antigravity" branding for developer platform
- **Claude.ai / Claude Code elevated errors** (HN 449/359): Outage incident — scope 5 (enterprise AI adoption / reliability)
- **Rust 1.100** (HN 844/304): Non-AI
- **Anthropic IPO proceedings** (Techmeme): ~$1.3T FDV; Nasdaq "ANT" — scope 5

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked — **13th consecutive run** (Oct 2–Nov 13). JP/CN hub discovery done entirely via WebSearch + WebFetch.
- **Reddit (r/MachineLearning):** Blocked persistent — all runs.
- **Bluesky:** Health OK per prompt; no paradigm-relevant posts surfaced.
- **YouTube / TikTok / Instagram:** Not swept.
- **Zhihu:** Multiple relevant pages 403 Forbidden (p/1997049165985887555, p/1993020615532232902).
- **Guardian (Gödel story):** Blocked by The Guardian paywall — story details sourced from SuperPowerDaily + mezha.net instead.
- **WICL physical hardware results:** Not disclosed in paper; simulation results only independently verified.
- **last30days skill:** Unavailable — sweep conducted manually for 13th consecutive run.

**Coverage estimate:** ~76%. G-STAR, BirdDreams, Duo, WICL well-covered (3-6 sources each). PhysLoop light (3 sources). Gödel story moderate (3 sources; Guardian blocked). Reddit/Bluesky/YouTube zero. JP/CN coverage good on trends, light on specific Nov 13 papers.

---

## Key Quotes

> "How much is Claude and how much is Gödel is a job for the historians." — Joel David Hamkins, logician, via superpowerdaily ([link](https://superpowerdaily.com/posts/claude-surfaced-663-theorems-and-proof-ideas-in-g-del-s-notebooks-researcher-says)) 🌐

> "If independently verified, [RoboScript] could challenge the conventional wisdom that teams need large data-collection infrastructure." — aiweekly.co on WICL ([link](https://aiweekly.co/alerts/roboscript-hits-834-on-robotwin-20-from-one-demo-per-task)) 🌐

> "让模型一边持续看和听，一边实时回应你，也就是真正的全双工交互" / "Enabling the model to continuously perceive while responding in real time — genuine full-duplex interaction." — qiaomu.ai on Duo ([link](https://rss.qiaomu.ai/articles/duo-%E9%9D%A2%E5%90%91%E5%85%A8%E5%8F%8C%E5%B7%A5%E4%BA%A4%E4%BA%92%E7%9A%84%E4%BA%92%E6%83%A0%E4%B8%96%E7%95%8C%E6%A8%A1%E5%9E%8B--9997292c8a19)) 🇨🇳

> "G-STAR不仅仅是调整压缩比，而是提出了一条协调这种权衡的基本原理" / "G-STAR does not merely adjust compression ratios but proposes a fundamental principle for coordinating the tradeoff." — qiaomu.ai on G-STAR ([link](https://rss.qiaomu.ai/articles/g-star-%E9%9D%A2%E5%90%91%E6%B7%B1%E5%BA%A6%E5%8E%8B%E7%BC%A9%E8%87%AA%E5%9B%9E%E5%BD%92%E7%94%9F%E6%88%90%E7%9A%84%E7%BB%84%E7%BC%A9%E6%94%BE-token-%E5%AE%B9%E9%87%8F--2b60154bd0ce)) 🇨🇳

> "LLMは言語的なパターンを学習することはできるが、物理世界の因果関係や時間的なダイナミクスを真に理解することはできない" / "LLMs learn linguistic patterns but cannot truly understand physical causality and temporal dynamics of the physical world." — note.com/naren_bao on World Models ([link](https://note.com/naren_bao/n/nefd15c8193ac)) 🇯🇵

> "What an agent learns in context is semantic, recording task steps and object roles rather than visual appearance." — WICL paper, arXiv:2611.12885 ([link](https://arxiv.org/abs/2611.12885)) 🌐

> "言語と物理法則の交点" / "The intersection of language and physical law" defines future AI evolution." — BuildApp News on LLM×World Model coexistence ([link](https://news.build-app.jp/article/39594/)) 🇯🇵
