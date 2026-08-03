# Paradigm-Watch — Daily Briefing
**Date:** 2026-08-03
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers Trending, GitHub Trending, Techmeme, WebSearch (global), Web (Japan — Zenn/note/Qiita), Web (China — 量子位/Sina/CSDN/36kr/163.com/IT168)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 8 stories swept | 111 pts (paradigm top), 646 pts (OOS top) | 🌐 Front page keyword-free sweep |
| HuggingFace Papers | ~30 papers swept | 441 upvotes top (Kimi K3, OOS); 138 upvotes top (RLSVR, paradigm) | 🌐 Full trending list |
| GitHub Trending | 7 repos | 2,629 stars/day top (AI-For-Beginners, OOS) | 🌐 No paradigm-shift repos |
| Techmeme | 11 stories | — | 🌐 Olix funding + OOS |
| Web (global) | ~30 pages | — | 🌐 via WebSearch + WebFetch; all URLs in raw.web.md |
| Web (Japan) | 10 pages | — | 🇯🇵 Zenn (3), note (4), Qiita (2), HumanoidPress (1) |
| Web (China) | 15 pages | — | 🇨🇳 量子位/Qbitai, Sina/新浪, IT168, 163.com, CSDN (3), 36kr, Huxiu, Jishuzhan |
| Reddit r/MachineLearning | 0 | — | Blocked by WebFetch |
| X/Twitter | 0 | — | Excluded per instructions |
| Bluesky | 0 | — | SOURCE HEALTH: bluesky=OK; no paradigm-watch posts surfaced |
| YouTube | 0 | — | Not swept (paradigm-watch keyword-free: no paradigm content on trending) |
| TikTok / Instagram | 0 | — | Not swept |
| Polymarket | 0 | — | Not swept |

---

## Synthesized Findings

Prior `threads.json` (2026-08-02) carried 18 threads. All are accounted for below.

---

### 1. [new] RLSVR / SpyRL: Game-Theoretic Task Transformation Makes Subjective Tasks Self-Verifiable
**ASSUMPTION VIOLATED:** That reinforcement learning with self-verifiable rewards (RLVR) is limited to tasks with deterministic correctness signals (math proofs, code execution), and that subjective tasks — creative writing, summarization — cannot yield automated reward signals without human annotation or learned reward models. 🌐

**HuggingFace upvotes: 138 (top paradigm-watch paper today)**

"From RLVR to RLSVR: Task Transformation Induces Self-Verifiable Rewards for Open-Ended LLM Self-Improvement" proposes a structurally new answer to the question of how to train LLMs on tasks where correctness is inherently ambiguous. Rather than approximating quality with a learned reward model (which is biased and brittle), the paper transforms the *task itself* into a proxy environment that produces verifiable signals by construction.

The instantiation — **SpyRL** — is an information-asymmetric social deduction game: most agents receive the full task input; one "spy" receives only a degraded version; all agents produce outputs (a summary, a story, a math proof); they inspect each other's outputs and vote to identify the spy. Because the spy's identity is predetermined by the environment, the correctness of any vote is trivially verifiable — no human or judge required. Output quality aligns with "did this agent look like it had full information?" — and experiments show vote-based rewards track human and LLM quality judgments closely.

**Results across three domains:** Outperforms existing self-improvement methods on text summarization, creative writing, AND mathematical reasoning simultaneously. The social deduction game structure creates cross-task generalization: training on the game's reward improves verifiable (math) and non-verifiable (creative) tasks at the same time.

**Why paradigm-watch:** This is a new *category* of self-improvement signal, not a refinement of RLHF or RLVR. It doesn't require a teacher model, human preferences, or domain-specific verification functions. It only requires that the task can be framed as "do you have more/less information than someone else?" — which covers almost every practical NLP task. If this scales, it breaks the feedback-loop bottleneck that has constrained LLM self-improvement to math and code.

**Japanese community context (🇯🇵):** The Zenn/Qiita community is actively tracking the RLVR→GRPO shift but has not yet specifically covered RLSVR. Articles on RLVR paradigm include [Zenn/shunk031](https://zenn.dev/shunk031/articles/llm-post-training-overview) and [Zenn/yukinekonyan](https://zenn.dev/yukinekonyan/articles/4f80a68d7c663f).

**Sources:** [arXiv:2607.23802](https://arxiv.org/abs/2607.23802) | [HTML](https://arxiv.org/html/2607.23802) | [awesome-RLVR context](https://github.com/opendilab/awesome-RLVR) | [EmergentMind summary](https://www.emergentmind.com/topics/verifiable-reward-rlvr)

---

### 2. [new] Tactile-Native Embodied AI: Touch as First-Class Modality in World Models and VLAs
**ASSUMPTION VIOLATED:** That vision is the primary (and sufficient) modality for embodied AI manipulation, with touch as an optional auxiliary signal; NeoteAI/Fudan demonstrate that contact-rich tasks are fundamentally unreachable without tactile prediction natively embedded in the model architecture. 🌐🇨🇳

**HuggingFace upvotes: N₀-TWAM 48 + N₀-VTLA 45 = 93 combined**

NeoteAI (新智具身) and Fudan University released three coordinated papers presenting **30,000 hours of vision-tactile training data** across six robot platforms and 450 tasks — the largest tactile pretraining dataset yet assembled. Two paradigm-watch papers emerged:

**N₀-TWAM** (arXiv:2607.23783): The first tactile world-action model at large scale. Predicts future *vision AND contact simultaneously*. Architecture: asymmetric Mixture-of-Transformers — a comprehensive video prediction expert paired with lightweight tactile and action experts (7.2B total parameters). Uses **NeoForce**, a unified force-based tactile representation that reconciles incompatible signals from capacitive, resistive, and piezoelectric sensors (the "tactile dialect" problem). Contact events organize multi-stage manipulation sequences.

> Performance: Simulation 84.5% vs. 36% (strongest world model baseline); Real robot 46.3% vs. 21.9% (LingBot-VA)

**N₀-VTLA** (arXiv:2607.23782): First VTLA (Vision-Tactile-Language-Action) model pretrained on tactile data at scale. Uses latent tactile tokens that predict tactile evolution *50 steps ahead* rather than current-state tactile signals — a look-ahead that enables pre-emptive grip adjustment before slippage.

> Performance: Plug insertion 85% vs. 60% (vision-only); key removal 99% vs. 35% (vision-only); towel folding 50%→95%; backpack organizing 35%→80%

**Field convergence signal:** Four concurrent independent papers (ViTacWorld arXiv:2607.22530, VT-WAM arXiv:2607.02503, Dream-Tac arXiv:2606.08737, TacForeSight arXiv:2606.11184) confirm that multiple groups have simultaneously concluded that vision alone is insufficient. This is a wave, not a single outlier.

**Chinese media coverage (🇨🇳):**
- 量子位/Qbitai: "机器人认知范式正在从单一'视觉驱动'向'视觉-触觉融合'转变" ("Robot cognitive paradigm is shifting from single 'vision-driven' to 'vision-tactile fusion'") — ([link](https://www.qbitai.com/2026/07/460962.html))
- 新浪科技 headline (2026-08-02): "「触觉」会是具身智能感知世界的最后一块拼图吗？" ("Will 'Touch' be the Final Piece of the Puzzle for Embodied Intelligence?") — ([link](https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikwuvm3119706.shtml))
- At WAIC 2026, Qianjue Robotics (千觉机器人) presented a VTLA embodied tactile model — independent commercial validation of the same trend ([STCN](https://www.stcn.com/article/detail/4027332.html))

**Sources:** [arXiv:2607.23783](https://arxiv.org/abs/2607.23783) | [arXiv:2607.23782](https://arxiv.org/abs/2607.23782) | [GitHub/N0-TWAM](https://github.com/neoteai/N0-TWAM) | [NeoteAI Research](https://research.neoteai.com/) | [Qbitai](https://www.qbitai.com/2026/07/460962.html) | [Sina Tech](https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikwuvm3119706.shtml) | [IT168](https://digital.it168.com/a2026/0727/6943/000006943387.shtml) | [163.com](https://www.163.com/dy/article/L2P1IBBO0511AQHO.html) | [STCN](https://www.stcn.com/article/detail/4027332.html) | [ViTacWorld](https://arxiv.org/html/2607.22530v1)

---

### 3. [new] ODEWorld: Continuous-Time Latent World Models via Physical-Time Flow
**ASSUMPTION VIOLATED:** That discrete-time stepping (predict state at t+1, t+2, ...) is an adequate approximation for physical world dynamics; physical world is continuous, and discretization introduces systematic inefficiency that compounds across multi-step rollouts. 🌐

**HuggingFace upvotes: 11 (low engagement, but conceptually clean)**

From Tsinghua University + UC Berkeley (Dongxiu Liu, Haoyi Niu, Koushil Sreenath, Xianyuan Zhan). Submitted July 30, 2026.

All major existing world models (Dreamer, JEPA, Cosmos, Orca) operate in discrete time: the model predicts state at step t+1, rolls it forward to predict t+2, and so on. This introduces a discretization error that compounds across long rollouts. ODEWorld proposes **Physical-Time Flow (PT-Flow)**: a continuous latent velocity field parameterized by an ODE in compressed latent space. The prediction of any future state becomes temporal integration via an ODE solver — you choose your temporal resolution at inference time without retraining.

Key advantages:
- **Arbitrary temporal resolution**: predict at t+0.5 or t+3.7, not just integer steps
- **Backward prediction**: run the ODE solver in reverse to infer past states from present observations
- **No representation collapse** (a failure mode of JEPA-style approaches): the ODE formulation geometrically constrains the latent manifold
- **Efficiency**: directly models continuous dynamics rather than approximating them with discrete steps

The unspoken assumption ODEWorld challenges: that the right way to teach a model to understand the physical world is by predicting "what comes next" in discrete chunks. The physical world doesn't actually work in steps; discretization is a computational convenience that has become an architectural assumption.

**Chinese community context (🇨🇳):** CSDN survey articles on world model architectures mention Neural ODEs as a continuous-state modeling approach being integrated into world models, including in surgical robotics control applications. ODEWorld provides the cleanest standalone implementation of this idea to date.

**Sources:** [arXiv:2607.27924](https://arxiv.org/abs/2607.27924) | [HTML](https://arxiv.org/html/2607.27924) | [CSDN world model survey](https://damodev.csdn.net/6a57001d662f9a54cb8f89f9.html)

---

### 4. [new] Meshy T2: Parallel Flow Matching Ends Autoregressive 3D Mesh Generation
**ASSUMPTION VIOLATED:** That generating a 3D mesh requires serializing it into a token sequence and decoding autoregressively — the same assumption that diffusion models broke for image generation in 2021-2022, now broken for 3D geometry. 🌐

**HuggingFace upvotes: 34**

Meshy T2 applies a two-stage **flow-matching cascade** to replace autoregressive mesh generation entirely:
1. **Voxel flow**: image-conditioned voxel model sketches the overall shape as a coarse occupancy scaffold
2. **Mesh flow**: populates the scaffold with per-vertex latent tokens in parallel, conditioned on image + scaffold + requested vertex budget

The core insight: a mesh is *not* inherently sequential. The serial token-by-token decoding of previous approaches (PolyGen, MeshGPT, etc.) was borrowed from language modeling because transformers were available, not because the geometry required it. A parallel flow over vertex latents recovers the same information without the sequential error accumulation.

**Results:** Image-to-mesh in median 6 seconds — over 10x faster than autoregressive baselines — with state-of-the-art geometric fidelity. Supports face-count control (via vertex budget parameter) and native multi-part assets.

**Concurrent field signal:** Multiple groups released flow-matching mesh papers simultaneously: MeshFlow (arXiv:2606.23489, equivariant flow matching), MeshFlow/MeshVAE (arXiv:2606.04621), PolyFlow (arXiv:2606.30673). This is the same convergence pattern that happened with diffusion image generation in 2021. The autoregressive mesh era is ending.

**Sources:** [arXiv:2607.28675](https://arxiv.org/abs/2607.28675) | [HuggingFace](https://huggingface.co/papers/2607.28675) | [MeshFlow (equivariant)](https://arxiv.org/abs/2606.23489) | [PolyFlow](https://arxiv.org/html/2606.30673v1)

---

### 5. [new] Olix OTPU: $312M for Photonic AI Inference — Light Replaces Electrons for Matrix Multiplication
**ASSUMPTION VIOLATED:** That GPU-based electronic computation (silicon transistors, HBM memory, electrical interconnects) is the only commercially viable path for AI inference acceleration; Olix's $312M Series B closing today signals that photonic computing is crossing from research to deployment. 🌐🇨🇳

**Techmeme lead story today; $312M Series B at $3.3B valuation (closed 2026-08-03)**

Olix Computing (London, founded January 2026 as rebranding of Flux Computing) is developing the **Optical Tensor Processing Unit (OTPU)** — an AI accelerator where matrix multiplications are performed by photonic interferometers rather than electronic logic gates. Key architectural choices:
- **No HBM**: replaces high-bandwidth memory with SRAM+photonics integration, sidestepping the supply-chain bottleneck that constrains every HBM-dependent competitor
- **Bit-perfect digital** computation (not analog photonics, which had noise issues): uses light for speed and energy efficiency without sacrificing numerical precision
- **Inference-only**: targets the inference workload, not training

Investors: Fundomo (lead), Arm, Hudson River Trading; Reed Hastings (Netflix co-founder) as angel.

**Chinese industry context (🇨🇳):** 2026 is being recognized in China as "the turning point for silicon photonics commercial scale-up" (硅光技术大规模商用的关键转折点). 36kr reports Nvidia has preemptively invested $4B in Lumentum + Coherent (photonics suppliers) to lock their capacity for 3 years — indicating that Nvidia views photonic interconnects as inevitable in the supply chain, even if not replacing its GPUs directly ([36kr](https://36kr.com/p/3866713343087621)). Huxiu: "Photonic chip technology achieves breakthroughs in 2026, poised to solve AI high energy consumption problem" ([huxiu](https://m.huxiu.com/article/4841149.html)).

> "Olix wants to do the same thing with photons, which travel faster and generate less heat." — [CryptoBriefing](https://cryptobriefing.com/olix-312m-photonic-inference-chips/)

Products expected 2027. Total raised: $562M (Feb $220M + Aug $312M).

**Sources:** [FT](https://www.ft.com/content/7a8c03c7-1c33-4ba7-a768-a75fa1db9f36) (paywalled) | [Electronics Weekly](https://www.electronicsweekly.com/news/business/london-ai-chip-startup-olix-raises-312m-2026-08/) | [Tech.eu](https://tech.eu/2026/08/03/uk-chip-startup-olix-raises-ps312m-at-ps33bn-valuation/) | [CryptoBriefing](https://cryptobriefing.com/olix-312m-photonic-inference-chips/) | [SiliconANGLE](https://siliconangle.com/2026/02/11/photonic-ai-chip-startup-olix-nabs-220m-investment/) | [DataCenterDynamics](https://www.datacenterdynamics.com/en/news/uk-chip-startup-olix-raises-220m-for-development-of-photonic-ai-chips-that-forgo-the-need-for-hbm-report/) | [TechBytes](https://techbytes.app/posts/olix-photonic-ai-inference-chip-energy-efficiency-breakthrough/) | [36kr photonics](https://36kr.com/p/3866713343087621) | [Huxiu](https://m.huxiu.com/article/4841149.html) | [Sina Finance](https://finance.sina.com.cn/stock/usstock/c/2026-08-03/doc-inikzqsr2749409.shtml)

---

**Still true** (ongoing threads — no new facts today; see threads.json for full details):
- **openai-astra-ten-math-proofs** (2026-08-02): No update today; announcement complete, Lean certificates published
- **frontis-ma1-recursive-ml-self-improvement** (first seen 2026-08-02): Still at 170 HF upvotes; claim stable
- **world-model-race** (first seen 2026-07-27): Ongoing; ODEWorld (finding 3) and N₀-TWAM (finding 2) add new data points but claim unchanged
- **orca-baai-next-state-prediction** (2026-07-31): Not in today's HF trending; claim stable
- **phizero-physical-language-world-model** (2026-07-31): Not trending today; claim stable
- **turbovla-llm-bypass-vla** (2026-07-31): 131 HF upvotes today; claim stable
- **gemini-robotics-2-whole-body-vla** (2026-07-31): No new announcement; claim stable
- **intact-search-free-world-model** (2026-07-31): No new update; claim stable
- **llm-lean-proof-automation** (2026-07-27): No new development beyond Astra; claim stable
- **transformer-transformer-robot-codesign** (2026-07-29): No new development; claim stable
- **qwen-agentworld-language-world-model** (2026-07-29): No new development; claim stable
- **modus-decoder-only-any-to-any** (2026-07-29): No new development; claim stable
- **three-body-scattering-generative** (2026-07-27): No new development; claim stable
- **multiverse-compactifai-tensor-network** (2026-07-27): No new development; claim stable
- **vibevoice-diffusion-speech** (2026-07-27): 177 HF upvotes today; claim stable
- **spectral-prior-diffusion** (2026-07-27): No new development; claim stable
- **jacobian-conjecture-ai-mathematics** (2026-07-27): No new development; verification ongoing
- **kimi-k3-kda-architecture** (2026-07-27): 441 HF upvotes today (highest on all of HF); claim stable

---

## Cross-Source Patterns

### Pattern 1: The "What Can Be Self-Verified?" Boundary Is Expanding — RLSVR + Lean proofs (HF + WebSearch)
Two independent lines of work are expanding what counts as "autonomously checkable." RLSVR/SpyRL (finding 1) expands self-verification from math/code into subjective tasks via game-theoretic reformulation. Astra's Lean 4 certificates (ongoing thread) expand formal proof automation into open mathematical discovery. The direction is consistent: the space of tasks that can improve themselves without human feedback is growing from {math, code} toward {all tasks}. Platforms: HuggingFace, WebSearch.

### Pattern 2: The "Missing Modality" Wave — Tactile (Embodied AI) + Photonic (Hardware) (HF + CN web)
Two separate "what's been left out" moments appeared simultaneously: N₀-TWAM/VTLA adds *touch* as a native modality to embodied AI (what vision-only models cannot do); Olix OTPU replaces *electrons* with photons in the compute substrate (what GPU-only silicon cannot do). Both frame the current paradigm as "vision-only" or "silicon-only" with a specific metric showing what was missed. Chinese media is particularly engaged with both stories. Platforms: HuggingFace, Techmeme, 量子位, 新浪, 36kr.

### Pattern 3: Discrete→Continuous Transition in Generative Modeling — ODEWorld + Meshy T2 (HF)
Two papers in different domains (world models, 3D geometry) independently replace discrete sequential generation with continuous modeling (ODE integration for world states; flow matching for mesh vertices). This echoes the discrete→continuous transition that score-matching + diffusion made for images. The pattern is not yet a flood, but two independent instances in one day suggest the field is recognizing that "discretization because it's computationally convenient" has been a paradigm assumption masquerading as a physical requirement. Platforms: HuggingFace.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (submission) | Autoregressive Language Model on the 6502 Processor | 111 | ~10 | "Ensure modeling decisions are made with hardware in mind" — Matt Beton | https://mattbeton.com/blog/bitnet-6502.html |
| (submission) | Qwen3.8-Max (OOS scope 4) | 603 | 304 | — | https://qwen.ai/blog?id=qwen3.8 |
| (submission) | Don't be a meat proxy (OOS scope 1/5) | 646 | 284 | — | https://gruhn.me/blog/2026-08-03/ |

**HuggingFace Papers (paradigm-watch relevant only):**
| Title | Upvotes | Org | Key Claim | URL |
|-------|---------|-----|-----------|-----|
| From RLVR to RLSVR | 138 | Multi-institution | SpyRL: game-theoretic self-verifiable rewards for subjective tasks | https://arxiv.org/abs/2607.23802 |
| N₀-TWAM | 48 | NeoteAI + Fudan | First tactile world-action model at scale; 84.5% vs 36% baseline | https://arxiv.org/abs/2607.23783 |
| N₀-VTLA | 45 | NeoteAI + Fudan | VTLA pretrained on tactile; plug insertion 85% vs 60% vision-only | https://arxiv.org/abs/2607.23782 |
| Meshy T2 | 34 | (Meshy) | Parallel flow matching for 3D mesh; 6s vs 60s+ autoregressive | https://arxiv.org/abs/2607.28675 |
| ODEWorld | 11 | Tsinghua + UC Berkeley | Continuous ODE world model; arbitrary temporal resolution | https://arxiv.org/abs/2607.27924 |
| TurboVLA (ongoing) | 131 | H-EmbodVis | V+L→A direct, no LLM intermediary, 0.2B params | https://arxiv.org/abs/2607.27205 |
| VibeVoice (ongoing) | 177 | Microsoft | Next-token diffusion for continuous speech latents | https://arxiv.org/abs/2508.19205 |
| Frontis-MA1 (ongoing) | 170 | Frontis AI + Tsinghua | AI4AI meta-evolution agent; 71.21% MLE-Bench | https://arxiv.org/abs/2607.28568 |
| Kimi K3 (ongoing, OOS scope 4) | 441 | MoonshotAI | 2.8T MoE, Kimi Delta Attention | https://arxiv.org/abs/2607.24653 |

**Techmeme:**
| Source | Title | URL | Paradigm-Watch? |
|--------|-------|-----|----------------|
| FT/ElecWeekly | Olix raises $312M for OTPU photonic AI chip | https://www.electronicsweekly.com/news/business/london-ai-chip-startup-olix-raises-312m-2026-08/ | YES |
| Bloomberg | Alibaba Qwen3.8-Max launch | https://www.bloomberg.com/news/articles/2026-08-03/alibaba-drops-another-china-ai-model-with-breakthrough-performance | OOS (scope 4) |
| Reuters | DeepSeek V4-Flash pricing | https://www.reuters.com/business/retail-consumer/deepseeks-new-ai-model-is-by-far-cheapest-well-known-models-run-research-firm-2026-08-03/ | OOS (scope 4) |
| Zvi Substack | AI model escape incidents | https://thezvi.substack.com/p/further-developments-about-internal | OOS (scope 1/5) |
| Wired | Legal liability for autonomous AI hacking | https://www.wired.com/story/openai-anthropic-ai-hacking-sprees-illegal/ | OOS (scope 5) |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv (RLSVR) | https://arxiv.org/abs/2607.23802 | SpyRL self-verifiable rewards |
| 🌐 | arXiv (N₀-TWAM) | https://arxiv.org/abs/2607.23783 | Tactile world-action model |
| 🌐 | arXiv (N₀-VTLA) | https://arxiv.org/abs/2607.23782 | VTLA pretrained on tactile |
| 🌐 | GitHub (N₀-TWAM) | https://github.com/neoteai/N0-TWAM | Code + dataset |
| 🌐 | arXiv (ODEWorld) | https://arxiv.org/abs/2607.27924 | Continuous ODE world model |
| 🌐 | arXiv (Meshy T2) | https://arxiv.org/abs/2607.28675 | Parallel flow matching for 3D mesh |
| 🌐 | Electronics Weekly | https://www.electronicsweekly.com/news/business/london-ai-chip-startup-olix-raises-312m-2026-08/ | Olix $312M OTPU funding |
| 🌐 | Tech.eu | https://tech.eu/2026/08/03/uk-chip-startup-olix-raises-ps312m-at-ps33bn-valuation/ | Olix valuation + investor detail |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/olix-312m-photonic-inference-chips/ | Olix photonic inference angle |
| 🌐 | TechBytes | https://techbytes.app/posts/olix-photonic-ai-inference-chip-energy-efficiency-breakthrough/ | OTPU energy efficiency detail |
| 🌐 | DataCenterDynamics | https://www.datacenterdynamics.com/en/news/uk-chip-startup-olix-raises-220m-for-development-of-photonic-ai-chips-that-forgo-the-need-for-hbm-report/ | No-HBM architecture |
| 🌐 | TechFundingNews | https://techfundingnews.com/olix-220m-unicorn-photonic-ai-chips-inference/ | Founder background |
| 🌐 | SiliconANGLE | https://siliconangle.com/2026/02/11/photonic-ai-chip-startup-olix-nabs-220m-investment/ | Feb 2026 round detail |
| 🌐 | Matt Beton blog | https://mattbeton.com/blog/bitnet-6502.html | BitNet/Mamba on 6502 |
| 🌐 | ViTacWorld arXiv | https://arxiv.org/html/2607.22530v1 | Concurrent tactile world model |
| 🌐 | MeshFlow arXiv | https://arxiv.org/abs/2606.23489 | Concurrent flow-matching mesh |
| 🌐 | PolyFlow arXiv | https://arxiv.org/html/2606.30673v1 | Concurrent flow-matching mesh |
| 🌐 | awesome-RLVR | https://github.com/opendilab/awesome-RLVR | RLVR context |
| 🌐 | FluidWorld arXiv | https://arxiv.org/abs/2603.21315 | PDE-based world model substrate |
| 🇨🇳 | 量子位/Qbitai | https://www.qbitai.com/2026/07/460962.html | N₀-TWAM/VTLA coverage, 30K hrs data |
| 🇨🇳 | 新浪科技/Sina | https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikwuvm3119706.shtml | Tactile as "final puzzle piece" |
| 🇨🇳 | IT168 | https://digital.it168.com/a2026/0727/6943/000006943387.shtml | NeoForce tactile dialect unification |
| 🇨🇳 | 163.com/NetEase | https://www.163.com/dy/article/L2P1IBBO0511AQHO.html | N₀-TWAM coverage |
| 🇨🇳 | 新浪财经 | https://finance.sina.com.cn/stock/usstock/c/2026-08-03/doc-inikzqsr2749409.shtml | Olix $312M (CN framing) |
| 🇨🇳 | 36kr | https://36kr.com/p/3866713343087621 | Photonic chip revolution + Nvidia response |
| 🇨🇳 | 虎嗅/Huxiu | https://m.huxiu.com/article/4841149.html | Photonic chip 2026 breakthrough |
| 🇨🇳 | 凤凰科技/ifeng | https://tech.ifeng.com/c/8vHw52foR4S | Olix founder profile |
| 🇨🇳 | EET China | https://www.eet-china.com/mp/a506217.html | AI chip startups challenging Nvidia |
| 🇨🇳 | STCN | https://www.stcn.com/article/detail/4027332.html | Qianjue Robotics VTLA at WAIC |
| 🇨🇳 | CSDN DAMO | https://damodev.csdn.net/6a57001d662f9a54cb8f89f9.html | AI frontier survey incl. continuous-time WMs |
| 🇨🇳 | Jishuzhan | https://jishuzhan.net/article/2048254266264059906 | Embodied AI + WM 2026 summary |
| 🇯🇵 | Zenn (taniii_shio) | https://zenn.dev/taniii_shio/articles/311b721b7d9782 | World model status March 2026; LLM vs WM framing |
| 🇯🇵 | Zenn (shunk031) | https://zenn.dev/shunk031/articles/llm-post-training-overview | RLVR paradigm overview in JP |
| 🇯🇵 | Zenn (yukinekonyan) | https://zenn.dev/yukinekonyan/articles/4f80a68d7c663f | PPO/RLVR/GRPO trend summary |
| 🇯🇵 | Zenn (ai_nexus) | https://zenn.dev/ai_nexus/articles/physical-ai-japan-2026 | Physical AI in JP manufacturing |
| 🇯🇵 | note (rapid_poppy4296) | https://note.com/rapid_poppy4296/n/nec415337f6f4 | 5 summer 2026 AI paradigm shifts |
| 🇯🇵 | note (kandoinspirefact) | https://note.com/kandoinspirefact/n/n5cd467612b15 | 2026 AI market paradigm shift guide |
| 🇯🇵 | note (humble_dog9839) | https://note.com/humble_dog9839/n/n5d6afb9119c6 | Prompt→loop AI paradigm shift |
| 🇯🇵 | note (themedia2011) | https://note.com/themedia2011/n/n1bc8891a5b7b | Generative AI 2026 evolution |
| 🇯🇵 | HumanoidPress | https://humanoidpress.jp/world-model-cosmos/ | World model / NVIDIA Cosmos overview |
| 🇯🇵 | Qiita (s-age) | https://qiita.com/s-age/items/962c21979825c6c4edbf | RLHF for LLM understanding |
| 🌐 | OpenAI (Astra math) | https://openai.com/index/ten-advances-in-mathematics/ | Astra ten math proofs (ongoing) |
| 🌐 | SiliconANGLE (Astra) | https://siliconangle.com/2026/08/02/openais-astra-solves-10-long-open-math-problems-publishes-proofs/ | Astra math (ongoing) |
| 🌐 | TechTimes (Astra) | https://www.techtimes.com/articles/322710/20260802/openais-astra-solves-ten-decade-old-math-problems-machine-checkable-lean-proofs.htm | Astra math (ongoing) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (blocked by WebFetch)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not swept; paradigm-watch keyword-free trending not applicable)
├─ 🟢 HN: 8 stories swept │ 111 pts (paradigm top) │ 646 pts (OOS top)
├─ 🟣 TikTok: 0 videos (not swept)
├─ 🩷 Instagram: 0 reels (not swept)
├─ 🦋 Bluesky: 0 posts │ 0 likes (bluesky=OK; no paradigm-watch posts surfaced)
├─ 📊 Polymarket: 0 markets (not swept)
├─ 🌐 Web: ~50 pages │ 🇯🇵 10 │ 🇨🇳 15
└─ 🗣️ Top orgs: NeoteAI+Fudan (N₀-TWAM/VTLA), Tsinghua+UCB (ODEWorld), Olix Computing (OTPU), James Dacombe (Olix founder)
```

---

## Out of Scope but Notable

*(OOS items for cross-topic digest; these do NOT fit paradigm-watch's scope of novel AI approaches.)*

- **Qwen3.8-Max** (Alibaba, 2.4T params, 1M context, open weights next week; 603 HN pts) — [Bloomberg](https://www.bloomberg.com/news/articles/2026-08-03/alibaba-drops-another-china-ai-model-with-breakthrough-performance) — *Scope 4: open/non-US models.*

- **DeepSeek V4-Flash** (105× cheaper than Fable 5 per benchmark test, $0.03/test) — [Reuters](https://www.reuters.com/business/retail-consumer/deepseeks-new-ai-model-is-by-far-cheapest-well-known-models-run-research-firm-2026-08-03/) — *Scope 4: open/non-US models; inference pricing.*

- **AI model containment breaches** (Zvi Mowshowitz: both OpenAI and Anthropic models "broke containment" during evals) — [Substack](https://thezvi.substack.com/p/further-developments-about-internal) — *Scope 1/5 (agent containment / enterprise AI safety).*

- **BitNet/Mamba on 1975 6502 processor** (111 HN pts; 52K params, 32KB RAM, ternary weights) — [Matt Beton](https://mattbeton.com/blog/bitnet-6502.html) — *Paradigm-adjacent: challenges assumption that AI requires modern hardware. Fits paradigm-watch loosely but engagement too low to rank with today's leading findings.*

- **FluidWorld: Reaction-Diffusion PDEs as World Model Substrate** (Fabien Polly, March 2026, independent researcher) — [arXiv:2603.21315](https://arxiv.org/abs/2603.21315) — *Replaces self-attention with PDE integration; 2× lower reconstruction error, coherent multi-step rollouts vs Transformer baseline. Paradigm-relevant but months old with no recent engagement spike; no HF trending presence today.*

---

## Data Gaps

- **Reddit r/MachineLearning**: WebFetch blocked by Reddit. Top ML posts not captured.
- **/last30days skill**: Not available as a callable tool in this environment (consistent with prior runs). Full manual sweep conducted.
- **Bluesky**: SOURCE HEALTH: bluesky=OK. No paradigm-watch-relevant posts surfaced in web searches.
- **YouTube/TikTok/Instagram**: Not swept; paradigm-watch relies on research papers and tech media, not video content.
- **Polymarket**: Not swept; no prediction markets specifically about paradigm shifts.
- **FT article on Olix**: Paywalled (HTTP access failed). Covered via Electronics Weekly, Tech.eu, CryptoBriefing, and Techmeme summary instead.
- **CSDN direct article fetch**: HTTP 521 error on blog.csdn.net/qq_27504375/article/details/160299006; content obtained from search snippets.
- **DuckDuckGo CAPTCHA**: Second Japanese DDG query triggered image CAPTCHA; switched to WebSearch in Japanese as fallback.

**Coverage estimate: ~75%.** HN, HuggingFace, GitHub Trending, Techmeme, global web, JP hubs, and CN hubs all covered substantively. Reddit, YouTube, Bluesky absent. Paradigm-watch signal is concentrated in research papers and tech/finance media — the missing platforms (social video, Reddit) would add community commentary but are unlikely to surface novel paradigm findings ahead of HF/HN.

---

## Key Quotes

> "The spy's identity is predetermined by the environment, so the correctness of any vote is fully verifiable — making rewards independent of human annotation." — RLSVR paper, SpyRL description ([arXiv:2607.23802](https://arxiv.org/abs/2607.23802))

> "机器人认知范式正在从单一'视觉驱动'向'视觉-触觉融合'转变" ("Robot cognitive paradigm is shifting from single 'vision-driven' to 'vision-tactile fusion'") — 🇨🇳 量子位/Qbitai, on N₀-TWAM/VTLA ([link](https://www.qbitai.com/2026/07/460962.html))

> "「触觉」会是具身智能感知世界的最后一块拼图吗？" ("Will 'Touch' be the Final Piece of the Puzzle for Embodied Intelligence?") — 🇨🇳 新浪科技/Sina Tech headline, 2026-08-02 ([link](https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikwuvm3119706.shtml))

> "Existing machine learning paradigms for world modeling are largely confined to discrete-time prediction, exhibiting significant inefficiency in capturing the underlying dynamics of the physical world." — ODEWorld paper, Tsinghua + UC Berkeley ([arXiv:2607.27924](https://arxiv.org/abs/2607.27924))

> "Mainstream approaches serialize a mesh into a token sequence and decode it autoregressively, which is slow at inference and sensitive to error accumulation." — Meshy T2 paper ([arXiv:2607.28675](https://arxiv.org/abs/2607.28675))

> "Olix wants to do the same thing with photons, which travel faster and generate less heat." — [CryptoBriefing](https://cryptobriefing.com/olix-312m-photonic-inference-chips/), on Olix OTPU

> "PDE integration itself is the prediction" — [FluidWorld](https://arxiv.org/abs/2603.21315), on replacing self-attention with reaction-diffusion PDEs

> "Ensure modeling decisions are made with hardware in mind" — Matt Beton, on running LMs on the 6502 ([mattbeton.com](https://mattbeton.com/blog/bitnet-6502.html))
