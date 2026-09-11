# Paradigm-Watch — Daily Briefing
**Date:** 2026-09-11
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Daily Papers, HuggingFace Trending, GitHub Trending, Techmeme, WebSearch (global, JP, CN), note.com, Zenn, Qiita, Zhihu, Sohu, Tencent News, iThome, CSDN

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 30 stories swept | 840 pts (OpenAI math); 512 pts (Raschka/SMELT); 430 pts (SWE-2) | 🌐 Keyword-free best/48h sweep |
| HuggingFace Daily Papers | 19 papers | 126 (NCP-ArchPreview #1); 99 (SenseNova-U1.5) | 🌐 Sep 11 daily papers |
| HuggingFace Trending | 26 papers | 779 (BDH-CQ #1); 207 (AuK); 84 (PWM) | 🌐 |
| GitHub Trending | 16 repos | +3,642 (gods-eye-view); +3,440 (i-have-adhd) | 🌐 0 paradigm-watch items (5th consecutive) |
| Papers With Code | → | — | 302 redirect to HF Papers; captured above |
| Techmeme | ~6 stories | Anthropic threat intel #1 | 🌐 |
| Web (global) | ~35 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~6 pages | — | 🇯🇵 note.com, Zenn, Qiita (DuckDuckGo CAPTCHA-blocked; fell back to WebSearch) |
| Web (China) | ~8 pages | — | 🇨🇳 Zhihu, Sohu, Tencent News, iThome, jdon.com (DuckDuckGo CAPTCHA-blocked; fell back to WebSearch) |
| Reddit r/MachineLearning | 0 | — | Blocked (consistent) |
| X/Twitter | 0 | — | Excluded per instructions |
| Bluesky | 0 | — | bluesky=OK; no paradigm-watch posts surfaced |
| YouTube / TikTok / Instagram / Polymarket | 0 | — | Not swept |

---

## Synthesized Findings

Prior threads.json: 41 threads (2026-09-08). 2 new threads today. 4 updates to existing threads. 35 prior threads ongoing.

---

### 1. [new] NCP-ArchPreview: Concept-Level Supervision Halves LLM Training Token Cost 🌐🇯🇵

**ASSUMPTION VIOLATED:** Next-token prediction is the necessary and sufficient training objective for LLMs; introducing multi-granularity concept supervision adds architectural complexity without efficiency gains.

**Claim:** NCP-ArchPreview (arXiv 2609.10715, Sep 11, 126 HF daily upvotes) scales "Next Concept Prediction" (NCP) to 8.9B parameters on 5.73T tokens — the largest latent-space LM to date — achieving OLMo-3-7B's final pretraining loss using only **51.3% of training tokens**.

**Evidence:**
- **Method:** Product-quantized concept vocabulary built from model hidden states; dedicated Concept Module predicts future concepts which then guide token generation; NTP and NCP trained jointly end-to-end
- **Efficiency:** 51.3% of training tokens → same pretraining loss; outperforms OLMo-3-7B by 2.45 pts macro-average; +5.99 pts GSM8K
- **Speculative decoding:** +4.17% mean accepted length improvement (concepts as draft signal)
- **Domain adaptation:** 17M-parameter VQ module enables lightweight domain adaptation (vs full fine-tune)
- **Lineage:** ConceptLM (arXiv 2602.08984, Feb 2026) demonstrated at 70M–1.5B; NCP-ArchPreview is the 8.9B/5.73T scale-up
- **JP framing (note.com, Feb 2026):** NCP described as "mesoscale parameters" (中間スケールパラメータ) between token and sentence level; resonates with LeCun's JEPA; "adding concept-level prediction tasks different from token prediction greatly improves data efficiency"
- **Related:** Zenn/galirage article explicitly frames concept-level models (Meta LCM + NCP) as "the next paradigm after LLMs":「トークンよりも大きな"概念"単位での予測がLLMの次のパラダイムになる可能性」("Predictions at a 'concept' unit larger than tokens may become the next paradigm for LLMs")

**Sources:** [arXiv 2609.10715](https://arxiv.org/abs/2609.10715) | [HuggingFace](https://huggingface.co/papers/2609.10715) | [ConceptLM original (Feb 2026)](https://arxiv.org/abs/2602.08984) | [Conceptual-Level Planning analysis](https://aiwithmike.substack.com/p/conceptual-level-planning-in-latent) | [NCP arxiviq analysis](https://arxiviq.substack.com/p/next-concept-prediction-in-discrete) | [Bilingual NCP analysis](https://alanhou.org/blog/arxiv-next-concept-prediction/) | [JP note.com review 🇯🇵](https://note.com/jack4manastalk/n/nbc26a9f74400) | [Zenn LCM connection 🇯🇵](https://zenn.dev/galirage/articles/meta-large-concept-model-lcm)

**Platforms:** 🌐 HuggingFace Daily Papers (#1, 126 upvotes) | 🇯🇵 note.com (concept established Feb 2026), Zenn (framed as LLM successor paradigm)

---

### 2. [new] SMELT: MoE Looped Transformers Save 6.8–18% Training FLOPs Under Compute-Budget Matching 🌐

**ASSUMPTION VIOLATED:** Increasing model depth requires proportionally increasing parameters; weight sharing across layers fundamentally limits model expressivity at scale.

**Claim:** SMELT (arXiv 2609.01343, Tsinghua/ByteDance Seed/TokenWave.AI) loops the middle half of MoE Transformer layers twice while **exactly matching** per-token FLOPs, total non-embedding parameters, and KV cache — achieving 6.8–18.0% training FLOPs savings at the compute-optimal frontier. Scaled to 54B non-embedding parameters with separate Chinchilla-style scaling laws.

**Evidence:**
- **Architecture:** Sparse MoE Transformer, middle layers Loop Twice; loop count increases with compute budget
- **Budget-matched:** matches baseline on all 3 budgets (FLOPs, params, KV cache); controls for confounds that invalidated prior looped transformer comparisons
- **Training FLOPs saved:** 6.8–18.0% at compute-optimal frontier
- **Downstream advantage:** Largest on Code; grows with sample length and in-context examples — beyond what validation loss predicts
- **Mechanistic insight:** Second loop visit reduces "attention sink" and redirects mass to content-relevant tokens — suggests looping acts as a refinement step, not just capacity addition
- **Connection to GPT-6 Astra:** Raschka article (HN 512 pts) discusses SMELT in context of Astra's probable looped/recurrent depth architecture; Pachocki quote: "depth of computation graph within factor of 2 of GPT-4"
- **Quote (Raschka):** "Looping improves reasoning on multi-step problems without adding parameters, but doesn't increase knowledge storage capacity."

**Sources:** [arXiv 2609.01343](https://arxiv.org/abs/2609.01343) | [HuggingFace](https://huggingface.co/papers/2609.01343) | [alphaXiv](https://www.alphaxiv.org/abs/2609.01343) | [HTML full paper](https://arxiv.org/html/2609.01343v1) | [Sebastian Raschka analysis (HN 512 pts)](https://magazine.sebastianraschka.com/p/gpt-6-astra-looped-transformers-and)

**Platforms:** 🌐 HN (#5 best, 512 pts, via Raschka article) | 🌐 HuggingFace Papers (unlisted in trending; surfaced via HN)

---

### 3. [update] OpenAI Claims Navier-Stokes Millennium Prize Solution: 10K Agents, 88 Hours, ~$Millions — Clay Institute Rejects 🌐🇨🇳

**NEW FACT:** OpenAI used ~10,000 parallel AI agents over 88 hours with a model "significantly more capable than GPT-6 Astra" to produce a Lean 4-verified Navier-Stokes singularity proof. Cost ~$millions (1,000× prior $2K math experiments). Clay Institute has not accepted. Attribution controversy with Buckmaster/Alpöge.

**Prior thread (`llm-lean-proof-automation`):** AI mathematical reasoning reaching frontier benchmarks; Astra 10 math proofs at ~$2K; Claude Riemann zeta.

**Evidence:**
- **Model used:** Internal model not publicly released; "significantly more capable than GPT-6 Astra" — not the same as GPT-6 Astra used in prior math runs
- **Method:** ~10,000 parallel AI agents; 88 hours total; agents converged on proof that 3D Navier-Stokes equations can develop singularity in finite time ("blowup"); Lean 4 formal verification completed
- **Cost:** ~$millions; Mark Chen (CRO): "in the ballpark of millions" — 1,000× the ~$2K prior Astra math experiments
- **Clay Institute status:** Has NOT accepted proof; the proof relies on a "forcing" that most mathematicians exclude from Navier-Stokes formulation; verification ongoing
- **Attribution controversy:**
  - Tristan Buckmaster (NYU) + Levent Alpöge (Anthropic) worked same problem ~1 year using Claude and Codex
  - Their breakthrough: Aug 15, 2026
  - OpenAI announcement: Sep 5, 2026 (12 hours after Buckmaster's concurrent announcement)
  - Buckmaster alleges OpenAI "cannot rule out" de-identified usage data helped train the model
  - Buckmaster alleges researcher was pressured: "why would you want to destroy your career"
  - OpenAI: offered concurrent release + attribution; Buckmaster rejected
- **CN framing (Sohu/QQ News):** "AI数学革命引爆全球署名风暴" — "AI math revolution ignites global authorship controversy"; strong emphasis on 10,000 parallel agents as demonstration of new AI-math methodology
- **CN framing (Zhihu):** Active community debate on whether AI can "really do" mathematics or merely assembles human insights
- **Quote (Fortune / Buckmaster):** "Why would you want to destroy your career?" — alleged threat from OpenAI to researcher challenging authorship

**Sources:** [OpenAI primary](https://openai.com/index/navier-stokes-solution/) | [Simon Willison summary](https://simonwillison.net/2026/Sep/8/on-navier-stokes/) | [Axios (attribution)](https://www.axios.com/2026/09/08/openai-math-solution-navier-stokes-credit) | [MIT Tech Review](https://www.technologyreview.com/2026/09/08/1143747/what-openais-latest-controversy-tells-us-about-the-future-of-math/) | [Quanta Magazine](https://www.quantamagazine.org/ai-has-solved-one-of-maths-1-million-millennium-prize-problems-20260908/) | [Fortune](https://fortune.com/2026/09/08/openai-says-it-cracked-navier-stokes-math-grand-challenge-buckmaster-accusation-cheating-intimidation-tao-lament/) | [Scientific American](https://www.scientificamerican.com/article/openai-claims-blockbuster-math-breakthrough-amid-swirl-of-controversy/) | [Clay rejects claim](https://www.implicator.ai/clay-institute-navier-stokes-openai-proof-claim/) | [XenoSpectrum](https://xenospectrum.com/en/openai-navier-stokes-singularity-clay-dispute/) | [AAAS Science](https://www.science.org/content/article/how-ai-math-breakthrough-ignited-controversy) | [kingy.ai dispute](https://kingy.ai/blog/navier-stokes-ai-proof-claims-dispute/) | [Sohu CN 🇨🇳](https://www.sohu.com/a/1073603434_122066679) | [Tencent News CN 🇨🇳](https://news.qq.com/rain/a/20260909A0C53O00) | [iThome TW 🇨🇳](https://www.ithome.com.tw/news/178803) | [Zhihu CN 🇨🇳](https://zhuanlan.zhihu.com/p/2080862488376120192) | [jdon.com CN 🇨🇳](https://www.jdon.com/94801-navier-stokes-ai-proof-controversy-2026.html) | [CN-SEC CN 🇨🇳](https://cn-sec.com/archives/5424287.html)

**Platforms:** 🌐 HN (#3 best, 840 pts); 🌐 Techmeme (adjacent, Sep 8); 🌐 Axios, MIT TR, Quanta, Fortune, Scientific American; 🇨🇳 Sohu, Tencent News, iThome, Zhihu, jdon.com, gm7.org

---

### 4. [update] SenseNova-U1.5: Spatially-Coupled Decoder + 4K Native Resolution Extends Encoder/VAE-Free Unified Multimodal 🌐

**NEW FACT:** V1.5 introduces spatially-coupled decoder (convolutions + Pixel Shuffle replacing patch-wise MLPs) and 4K native resolution; 8B-MoT architecture confirmed; multi-expert on-policy distillation with 4 specialized RL experts.

**Prior thread (`modus-decoder-only-any-to-any`):** Unified understanding+generation paradigm; EPFL MODUS + SenseNova-U1 NEO-unify treating understanding/generation as synergistic views of one process.

**Evidence:**
- **U1.5 architecture:** 8B Mixture-of-Transformers (MoT); encoder-free + VAE-free; spatially-coupled decoder for coherent pixel reconstruction at high resolution; 4K native resolution support
- **Multi-expert post-training:** Four specialized RL experts (aesthetics, text rendering, infographics, editing) → consolidated via on-policy distillation
- **New capabilities:** Leading bilingual text rendering (CVTG-2K 0.948); VBVR-Pro-Bench reasoning-via-generation leadership; ImgEdit 4.59 / GEdit-Bench leading open-source
- **Source commitment:** Plans to open-source training code (SFT, RL, on-policy distillation)
- **99 HF daily upvotes** (Sep 11)

**Sources:** [arXiv 2609.11929](https://arxiv.org/abs/2609.11929) | [HuggingFace](https://huggingface.co/papers/2609.11929)

**Platforms:** 🌐 HuggingFace Daily Papers (#2, 99 upvotes)

---

### 5. [update] Programmable World Model: Explicit Verifiable State Decoupled from Generative Rendering 🌐

**NEW FACT:** PWM (Alaya Lab, arXiv 2609.10540, Sep 9) achieves 94% count accuracy and 98% state accuracy by separating executable world state from visual generation — versus 40.75%/8% for baseline video world models.

**Prior thread (`world-model-race`):** World models expanding from video/appearance to physics+3D: Matrix-Game 3.5, Puffin-World, WorldSculpt composing worlds from grounded video.

**Evidence:**
- **Core decoupling:** Agent → NL instructions → executable programs (entity states + transition rules) → lightweight engine maintains explicit persistent world state → state-augmented 3D OBBs guide video generation
- **Key principle:** "State is executable and verifiable, while appearance remains generative"
- **Results (CombatStateBench):** Count Accuracy 94% vs 40.75% (LingBot-World-V2), 32% (YUME); State Accuracy 98% vs 8% (LingBot-World-V2), 58% (YUME)
- **Supports:** Off-screen entity tracking; non-visual attributes; coherent long-horizon generation; unseen visual styles
- **84 HF trending upvotes**

**Sources:** [arXiv 2609.10540](https://arxiv.org/abs/2609.10540) | [HuggingFace](https://huggingface.co/papers/2609.10540) | [Project page](https://alaya-lab.github.io/pwm/) | [Code](https://github.com/AlayaLab/pwm)

**Platforms:** 🌐 HuggingFace Trending (84 upvotes)

---

### 6. [update] Anthropic Threat Intelligence: Autonomous Zero-Day Discovery at Dozen/Month Scale; Attackers' Cost Curves Invert 🌐

**NEW FACT:** Anthropic report (Techmeme #1) documents GTG-10007 (attributed: Chinese group) producing "a dozen zero-day findings in a single month" via autonomous vulnerability research (50 orgs targeted); GTG-50014 mass-downloaded 1.8M APKs. Confirms "sophisticated attacks no longer require sophisticated attackers" as empirical fact across multiple state-level and criminal actors.

**Prior thread (`weworm-ai-cyberweapon-compression`):** WeWorm compressed zero-click cross-platform worm from months to ~9 days (AI-assisted, Sep 8).

**Evidence:**
- **GTG-10007 (Chinese group):** Dozen zero-days in single month, autonomous; 50 orgs targeted
- **GTG-20006 (Russian espionage):** 300K+ national identity records; malware auto-rebuilds and redeploys when detected
- **GTG-50014 (ShinyHunters):** 1.8M Android APKs mass-downloaded; credential harvesting; breaches in hours
- **Influence ops:** 70+ fabricated news websites; 1,000+ fake social media accounts per campaign; content laundered through outlet chains
- **Economic inversion:** AI compresses attackers' cost while defenders must continuously update; operators can "close the loop faster than defenders can develop" new detections
- **Individual actor:** One person built complete doxxing platform with "ingestion pipelines" and "containerized deployment" previously requiring teams
- **AI credentials as targets:** Stolen API keys become attack resources ("living off the land" applied to AI)

**Sources:** [Anthropic Threat Intelligence Report](https://www.anthropic.com/threat-intelligence-report-september-2026) | [Techmeme](https://www.techmeme.com)

**Platforms:** 🌐 Techmeme (#1 story today) | 🌐 Anthropic primary

---

**Still true** (ongoing — no new facts today for 35 prior threads):

- **weathernext3-fgn-raw-satellite**: WeatherNext 3 FGN; 5km/hourly; 60% CRPS; bypasses 6h data assimilation. No updates Sep 11.
- **uno-diffusion-ar-speedup**: Uno 8B; 3× AR speedup; "lossless" AR+diffusion hybrid.
- **gpt6-astra-arc-agi3-saturation**: GPT-6 Astra; ARC-AGI-3 99.9%; AI-supervised training Stargate. (Note: today's Navier-Stokes used a still-unreleased model beyond Astra.)
- **rogue-agents-collusion-dsewiki**: OpenAI agents DSEWiki 18K posts; HF breach 1,200 agents.
- **arc-agi-1-transductive-ttt-67cents**: Mithil Vakde TTT; 44% ARC-AGI-1 at $0.67.
- **dlss5-neural-rendering**: DLSS 5 NBA 2K27; pixel-space diffusion transformer in gaming.
- **samsung-lpddr5x-pim**: LPDDR5X-PIM; 3.01× inference; 614 GB/s; memory as compute substrate.
- **rockAI-yan-native-memory**: RockAI Yan non-Transformer; training-inference sync; WAIC 2026.
- **glm53-emergent-exploit-chain**: GLM-5.3 ExploitBench → Astra 100%; zero-day discovery.
- **bdh-cq-recurrent-latent-reasoning**: BDH-CQ 779 HF trending; recurrent latent reasoning; $0.0007/task.
- **colibri-lumabri-consumer-moe-p2p**: FreeToken 109 HF trending; 284B on gaming desktop.
- **diffusion-lm-scaling-wave**: VibeVoice 178 HF trending; LLaDA/Nemotron diffusion LM lineage.
- **nvidia-groq3-lpx-hardware-disaggregation**: Groq 3 LPX; disaggregated prefill/decode; 3,400 tok/s.
- **llm-inference-engine-exploit-escape**: Boyd Kane; vLLM CVE eval(); model → arbitrary code execution.
- **stop-anthropomorphizing-llm-reasoning-traces**: Kambhampati ICML 2026; tokens not reasoning traces.
- **ant-asynchronous-neural-turing-networks**: UMass ANT; no global sync clock; continuous learning.
- **cerebras-wse-onchip-sram-inference**: Cerebras WSE; 1,500 tok/s Qwen 3.8 27B.
- **full-bandwidth-transformer-latent-feedback**: arXiv 2608.08888; GLU hidden-state feedback; ~1.5× data efficiency.
- **needle2-simple-attention-network**: Needle2 14MB SAN; no FFN; 500+ tok/s RPi 5.
- **lfm2-5-hybrid-conv-lm**: LFM2.5 2.6B; 220 tok/s CPU; hybrid recurrent.
- **steerling-interpretable-diffusion-lm**: Steerling-8B; interpretability scales with capability.
- **taalas-msic-weights-in-silicon**: AMD/Taalas ROM silicon; 16,960 tok/s Llama 3.1 8B.
- **maple-preview-ternary-moe**: Maple-Preview ternary MoE; IMO math at 5.31 GB.
- **olix-otpu-photonic-ai-inference**: Olix DX-1 photonic; 10K+ tok/s per user; H2 2027.
- **rlsvr-spyrl-self-verifiable-rewards**: RLSVR/SpyRL; verifiable RL for creative writing.
- **neoteai-tactile-native-embodied-ai**: N₀-TWAM; touch native modality; 99% vs 35%.
- **odeworld-continuous-latent-world-model**: ODEWorld; ODE integration in latent space.
- **meshy-t2-flow-matching-mesh-generation**: Meshy T2; flow-matching 3D mesh in 6s.
- **openai-astra-ten-math-proofs**: Astra 10 math proofs; Lean 4; ~$2K. (Superseded cost-wise by today's ~$millions Navier-Stokes run; but distinct result set.)
- **frontis-ma1-recursive-ml-self-improvement**: Frontis-MA1 35B; 71.21% MLE-Bench; RTX 4090.
- **orca-baai-next-state-prediction**: BAAI Orca; Next-State-Prediction; 125K hrs video.
- **phizero-physical-language-world-model**: CASIA PhiZero; discrete physical language from unlabeled video.
- **turbovla-llm-bypass-vla**: TurboVLA; V+L→A without LLM; 32Hz at 0.2B.
- **gemini-robotics-2-whole-body-vla**: DeepMind Gemini Robotics 2; full humanoid under one policy.
- **intact-search-free-world-model**: INTACT; eliminates CEM search; 300× faster.
- **transformer-transformer-robot-codesign**: Stanford; robot body+policy via diffusion.
- **qwen-agentworld-language-world-model**: Qwen-AgentWorld; language model as environment simulator.
- **three-body-scattering-generative**: Three-Body Scattering; FID=1.63; single forward pass.
- **multiverse-compactifai-tensor-network**: CompactifAI; quantum tensor network 80-95% compression.
- **spectral-prior-diffusion**: Spectral Alignment; fixes diffusion exposure bias across all major models.
- **jacobian-conjecture-ai-mathematics**: Claude Fable 5 Jacobian counterexample; verification ongoing.
- **kimi-k3-kda-architecture**: Kimi Delta Attention; 6.3× faster decoding; 75% KV-cache reduction.

---

## Cross-Source Patterns

### Pattern 1: AI-as-Swarm for Mathematics — A New Computational Paradigm

The Navier-Stokes result (10,000 parallel AI agents, 88 hours) represents a structurally different approach from Astra's previous 10-problem math run (~$2K, sequential agent chains). This is the first public demonstration of a brute-force parallel AI swarm (4 orders of magnitude more agents) applied to an open millennium-level problem. The cost inversion (×1,000 from prior run) and Clay Institute rejection on a technical objection suggests the paradigm is: "spend compute to explore mathematical search space, then formally verify what survives."

Whether this counts as mathematical discovery or mathematical search is precisely what the attribution controversy is about.

**Platforms:** 🌐 HN (840 pts); 🌐 Axios/MIT TR/Fortune/Scientific American; 🇨🇳 Sohu, Tencent News, Zhihu

### Pattern 2: Hierarchical Training Objectives — NCP + SMELT Both Break Token-Level Atomicity

Two independent papers today challenge the assumption that training should operate at a single granularity:
- **NCP-ArchPreview:** Concept-level supervision (multi-token) + token-level → 51.3% training token savings
- **SMELT:** Layer-level iteration (second loop visit) → 6.8–18% training FLOPs savings

Both work by making the model process the same content at a different temporal/structural granularity during training. Neither requires a new base architecture — both are composable with existing Transformers and MoE.

**Platforms:** 🌐 HF Daily Papers (NCP #1); 🌐 HN (SMELT via Raschka #5)

### Pattern 3: GitHub Trending = Zero Paradigm-Watch (5th Consecutive Sweep)

All 16 GitHub Trending repos are Scopes 1-2 (agent harnesses, SDLC tooling, knowledge bases). The tooling wave has fully captured the trending surface. Consistent with prior 4 sweeps.

---

## Per-Platform Tables

**Hacker News (paradigm-watch relevant):**
| User | Title | Points | Comments | Scope | URL |
|------|-------|--------|----------|-------|-----|
| — | More questions about whether researchers can trust OpenAI with unpublished math | 840 | 784 | **[update] llm-lean-proof-automation** | https://news.ycombinator.com/item?id=49639408 |
| — | GPT-6 Astra, looped transformers, and hidden reasoning | 512 | 161 | **[new] SMELT (looped transformers)** | https://magazine.sebastianraschka.com/p/gpt-6-astra-looped-transformers-and |
| — | OpenAI might have stolen another major proof | 294 | 10 | [update] llm-lean-proof-automation | https://mathstodon.xyz/@ValerioCapraro/117244102901892965 |
| — | Cognition SWE-2 | 430 | 184 | OOS Scope 1-2 | https://cognition.com/blog/swe-2 |
| — | OpenAI Agents API | 306 | 164 | OOS Scope 1 | https://developers.openai.com/api/docs/guides/agents-api/overview |

**HuggingFace Daily Papers (paradigm-watch relevant):**
| Title | Upvotes | Scope | URL |
|-------|---------|-------|-----|
| NCP-ArchPreview: Moving towards Latent Space LMs through Next Concept Prediction | 126 | **[new] NCP** | https://huggingface.co/papers/2609.10715 |
| SenseNova-U1.5: Towards Native Unified Visual Intelligence | 99 | **[update] modus** | https://huggingface.co/papers/2609.11929 |
| SpatialBlock | 44 | OOS Scope 1 | https://huggingface.co/papers/2609.07064 |
| EvoSafeHarness | 35 | OOS Scope 1 | https://huggingface.co/papers/2609.05903 |

**HuggingFace Trending (paradigm-watch relevant):**
| Title | Upvotes | Scope | URL |
|-------|---------|-------|-----|
| BDH-CQ: Recurrent Latent Reasoning | 779 | Ongoing [bdh-cq] | https://arxiv.org/abs/2608.09888 |
| Programmable World Model | 84 | **[update] world-model-race** | https://arxiv.org/abs/2609.10540 |
| OpenWAM (World-Action Model pretraining) | 64 | Ongoing [world-model-race adjacent] | https://arxiv.org/abs/2609.07398 |
| VibeVoice | 178 | Ongoing [vibevoice] | https://arxiv.org/abs/2508.19205 |
| FreeToken | 109 | Ongoing [colibri] | https://arxiv.org/abs/2608.16157 |

**GitHub Trending:** No paradigm-watch items. All Scope 1-2.

| Repo | Stars/Day | Scope | URL |
|------|-----------|-------|-----|
| bilawalsidhu/gods-eye-view | +3,642 | Not AI (satellite viz) | https://github.com/bilawalsidhu/gods-eye-view |
| ayghri/i-have-adhd | +3,440 | Scope 1/2 | https://github.com/ayghri/i-have-adhd |
| obra/superpowers | +731 | Scope 1/2 | https://github.com/obra/superpowers |
| github/spec-kit | +985 | Scope 2 | https://github.com/github/spec-kit |
| nashsu/llm_wiki | +640 | Scope 3 | https://github.com/nashsu/llm_wiki |

**Techmeme:**
| Story | Source | URL |
|-------|--------|-----|
| Anthropic threat intelligence report | Anthropic | https://www.anthropic.com/threat-intelligence-report-september-2026 |
| Sam Altman: OpenAI open to slowing AI development | Bloomberg | https://www.bloomberg.com/news/articles/2026-09-11/openai-is-open-to-slowing-cutting-edge-ai-development |
| OpenAI asked Congress if AI slowdown would violate antitrust | Wired | https://www.wired.com/story/openai-wants-to-know-if-an-ai-industry-slowdown-would-even-be-legal/ |
| California child safety chatbot/social media laws | CalMatters | https://calmatters.org/economy/technology/2026/09/california-enacts-laws-restricting-chatbots-protecting-kids-online/ |
| Adobe Q3 earnings | Reuters | https://www.reuters.com/business/adobe-beats-third-quarter-revenue-estimates-2026-09-10/ |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv 2609.10715 | https://arxiv.org/abs/2609.10715 | NCP-ArchPreview primary |
| 🌐 | arXiv 2602.08984 | https://arxiv.org/abs/2602.08984 | ConceptLM (NCP original, Feb 2026) |
| 🌐 | aiwithmike.substack | https://aiwithmike.substack.com/p/conceptual-level-planning-in-latent | NCP planning framing |
| 🌐 | arXiv 2609.01343 | https://arxiv.org/abs/2609.01343 | SMELT primary |
| 🌐 | alphaXiv SMELT | https://www.alphaxiv.org/abs/2609.01343 | SMELT community discussion |
| 🌐 | Sebastian Raschka | https://magazine.sebastianraschka.com/p/gpt-6-astra-looped-transformers-and | SMELT analysis/HN 512 pts |
| 🌐 | OpenAI | https://openai.com/index/navier-stokes-solution/ | Navier-Stokes primary |
| 🌐 | Simon Willison | https://simonwillison.net/2026/Sep/8/on-navier-stokes/ | Technical context |
| 🌐 | Axios | https://www.axios.com/2026/09/08/openai-math-solution-navier-stokes-credit | Attribution controversy |
| 🌐 | MIT Technology Review | https://www.technologyreview.com/2026/09/08/1143747/what-openais-latest-controversy-tells-us-about-the-future-of-math/ | Future of math analysis |
| 🌐 | Quanta Magazine | https://www.quantamagazine.org/ai-has-solved-one-of-maths-1-million-millennium-prize-problems-20260908/ | Best technical explainer |
| 🌐 | Fortune | https://fortune.com/2026/09/08/openai-says-it-cracked-navier-stokes-math-grand-challenge-buckmaster-accusation-cheating-intimidation-tao-lament/ | Attribution/threats claims |
| 🌐 | Scientific American | https://www.scientificamerican.com/article/openai-claims-blockbuster-math-breakthrough-amid-swirl-of-controversy/ | Broad scientific context |
| 🌐 | Implicator.ai | https://www.implicator.ai/clay-institute-navier-stokes-openai-proof-claim/ | Clay Institute position |
| 🌐 | XenoSpectrum | https://xenospectrum.com/en/openai-navier-stokes-singularity-clay-dispute/ | Mathematician perspective |
| 🌐 | AAAS Science | https://www.science.org/content/article/how-ai-math-breakthrough-ignited-controversy | Scientific community reaction |
| 🌐 | kingy.ai | https://kingy.ai/blog/navier-stokes-ai-proof-claims-dispute/ | Dispute summary |
| 🌐 | arXiv 2609.10540 | https://arxiv.org/abs/2609.10540 | Programmable World Model primary |
| 🌐 | PWM project | https://alaya-lab.github.io/pwm/ | Demo materials |
| 🌐 | PWM code | https://github.com/AlayaLab/pwm | Open-source |
| 🌐 | Anthropic Threat Intel | https://www.anthropic.com/threat-intelligence-report-september-2026 | AI misuse; zero-day autonomy |
| 🌐 | arXiv 2609.11929 | https://arxiv.org/abs/2609.11929 | SenseNova-U1.5 primary |
| 🇯🇵 | note.com (jack4manastalk) | https://note.com/jack4manastalk/n/nbc26a9f74400 | NCP JP review (Feb 2026) |
| 🇯🇵 | Zenn (galirage) | https://zenn.dev/galirage/articles/meta-large-concept-model-lcm | LCM/NCP JP framing |
| 🇯🇵 | Zenn (taniii_shio) | https://zenn.dev/taniii_shio/articles/311b721b7d9782 | World models JP overview |
| 🇯🇵 | Zenn (mkj) | https://zenn.dev/mkj/articles/nlp_20260208 | NLP2026 frontiers incl NCP |
| 🇯🇵 | Qiita (teppei_nakano) | https://qiita.com/teppei_nakano/items/56e335a208edba2ea668 | Multimodal paradigm 2026 |
| 🇨🇳 | Sohu | https://www.sohu.com/a/1073603434_122066679 | Navier-Stokes CN; 10K agents framing |
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260909A0C53O00 | Navier-Stokes CN |
| 🇨🇳 | iThome TW | https://www.ithome.com.tw/news/178803 | Navier-Stokes TW; Lean 4 angle |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2080862488376120192 | Navier-Stokes CN community |
| 🇨🇳 | jdon.com | https://www.jdon.com/94801-navier-stokes-ai-proof-controversy-2026.html | Navier-Stokes; attribution controversy |
| 🇨🇳 | CN-SEC | https://cn-sec.com/archives/5424287.html | Navier-Stokes; verification/implications |
| 🇨🇳 | CSDN/QbitAI | https://blog.csdn.net/QbitAI/article/details/142760480 | Non-Transformer architecture coverage |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (blocked, consistent)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not swept)
├─ 🟢 HN: 30 stories swept │ 840 pts (OpenAI math) │ 512 pts (Raschka/SMELT) │ 294 pts (OpenAI proof theft claim)
├─ 🟣 TikTok: 0 videos (not swept)
├─ 🩷 Instagram: 0 reels (not swept)
├─ 🦋 Bluesky: 0 posts │ 0 likes (bluesky=OK; no paradigm-watch posts surfaced)
├─ 📊 Polymarket: 0 markets (not swept)
├─ 🌐 Web: ~35 pages │ 🇯🇵 6 │ 🇨🇳 8
└─ 🗣️ Top voices: OpenAI (Navier-Stokes); Tristan Buckmaster (attribution controversy); Sebastian Raschka (SMELT analysis); NCP-ArchPreview team (Tsinghua/ByteDance); Alaya Lab (PWM)
```

---

## Out of Scope but Notable

- **Sam Altman: OpenAI open to slowing cutting-edge AI development** (Techmeme #2, Bloomberg Sep 11): Altman told staff OpenAI considers a development slowdown; asked Congress whether industry coordination would violate antitrust. URLs: [Bloomberg](https://www.bloomberg.com/news/articles/2026-09-11/openai-is-open-to-slowing-cutting-edge-ai-development) | [Wired](https://www.wired.com/story/openai-wants-to-know-if-an-ai-industry-slowdown-would-even-be-legal/) → Scope 5 (enterprise AI / industry policy).

- **Cognition SWE-2 model** (HN 430 pts): New frontier coding agent model, "rivaling Fable 5.1 and GPT-Astra"; [Cognition blog](https://cognition.com/blog/swe-2) → Scope 1-2.

- **California child chatbot/social media safety laws** (Techmeme/CalMatters): Gov. Newsom signs bills restricting AI chatbot interactions for under-16s and banning "addictive" social media features; [CalMatters](https://calmatters.org/economy/technology/2026/09/california-enacts-laws-restricting-chatbots-protecting-kids-online/) → Scope 5 (enterprise/policy).

- **iPhone Duo / iPhone 18 Pro** (HN #1 + #7, ~1,800 combined pts): New foldable iPhone form factor; not AI architecture. URLs: [Apple iPhone Duo](https://apple.com/iphone-duo/) | [iPhone 18 Pro](https://apple.com/newsroom/2026/09/apple-debuts-iphone-18-pro)

---

## Data Gaps

- **Reddit r/MachineLearning:** Blocked (consistent with all prior runs).
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (consistent). Fell back to WebSearch in native languages.
- **Zhihu direct page fetches:** 403 (consistent). Content via search snippets only.
- **Juejin:** JS-required; not directly fetchable.
- **Bluesky:** bluesky=OK; no paradigm-watch posts surfaced.
- **YouTube / TikTok / Instagram / Polymarket:** Not swept.
- **SMELT HF paper engagement:** Not in HF trending top list; engagement via HN article (512 pts). HF paper page exists but low direct upvote count.
- **NCP-ArchPreview JP/CN hub coverage (Sep 11-specific):** Paper is from today; JP and CN hubs cover the Feb 2026 ConceptLM origin paper; today's NCP-ArchPreview scale-up not yet specific-covered on Zenn/Qiita/CSDN as of Sep 11.
- **Papers With Code:** 302 redirect to HF Papers trending; captured above.

**Coverage estimate: ~78%.** HN full best/48h (30 stories), HF Daily Papers (19 papers), HF Trending (26 papers), GitHub Trending (16 repos), Techmeme (~6 stories), global web (~35 pages), JP (~6 pages via WebSearch), CN (~8 pages via WebSearch). Reddit, YouTube, Bluesky, TikTok, Instagram, Polymarket absent. Today: 2 new paradigm-watch threads (NCP-ArchPreview, SMELT), 4 updates (Navier-Stokes, SenseNova-U1.5, PWM, Anthropic threat intel). Primary sources for all findings accessible. Navier-Stokes coverage exceptional (HN 840 pts, 10+ global outlets, 6 CN outlets).

---

## Key Quotes

> "トークンよりも大きな'概念'単位での予測がLLMの次のパラダイムになる可能性" ("Predictions at a 'concept' unit larger than tokens may become the next paradigm for LLMs") — Zenn/galirage on concept-level LMs ([link](https://zenn.dev/galirage/articles/meta-large-concept-model-lcm)) 🇯🇵

> "AI数学革命引爆全球署名风暴" ("AI math revolution ignites global authorship controversy") — Sohu on OpenAI Navier-Stokes ([link](https://www.sohu.com/a/1073603434_122066679)) 🇨🇳

> "State is executable and verifiable, while appearance remains generative." — Programmable World Model paper ([link](https://arxiv.org/abs/2609.10540)) 🌐

> "Looping improves reasoning on multi-step problems without adding parameters, but doesn't increase knowledge storage capacity." — Sebastian Raschka on SMELT ([link](https://magazine.sebastianraschka.com/p/gpt-6-astra-looped-transformers-and)) 🌐

> "Sophisticated attacks no longer require sophisticated attackers." — Anthropic Threat Intelligence Report ([link](https://www.anthropic.com/threat-intelligence-report-september-2026)) 🌐

> "Why would you want to destroy your career?" — Alleged threat to mathematician challenging OpenAI Navier-Stokes authorship (Fortune, [link](https://fortune.com/2026/09/08/openai-says-it-cracked-navier-stokes-math-grand-challenge-buckmaster-accusation-cheating-intimidation-tao-lament/)) 🌐

> "The depth of the computation graph for our present frontier models, including Astra, is within a factor of two of GPT-4." — Jakub Pachocki (OpenAI Chief Scientist), on looped transformers, via Sebastian Raschka ([link](https://magazine.sebastianraschka.com/p/gpt-6-astra-looped-transformers-and)) 🌐

> "OpenAI cannot rule out that de-identified data derived from their usage of OpenAI's products helped improve their models." — OpenAI statement on Buckmaster/Alpöge Navier-Stokes work ([link](https://www.axios.com/2026/09/08/openai-math-solution-navier-stokes-credit)) 🌐
