# Paradigm-Watch — Daily Briefing
**Date:** 2026-09-01
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers (daily + trending), GitHub Trending, Techmeme, WebSearch (global, JP, CN), Zenn, Qiita, CSDN, Zhihu

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 30 stories swept | 230 pts (ARC-AGI paradigm item); 337 pts GPU World (fiction) | 🌐 Keyword-free full sweep |
| HuggingFace Papers (daily) | 36 papers swept | 86 top (on-policy distillation); 84, 57, 55, 35 | 🌐 Sep 1 daily papers |
| HuggingFace Papers (trending) | ~27 papers | 766 (BDH-CQ #1); 445 StateM; 205 Apodex; 177 VibeVoice/MinerU2.5 | 🌐 |
| GitHub Trending | 15 repos | 3,122/day top (OpenMAIC, Scope 1 agent); 1,005/day (minimind LLM from scratch) | 🌐 0 paradigm-watch architecture items |
| Techmeme | ~9 stories | DLSS 5 official launch Sep 3 [update]; Apple leadership transition dominates | 🌐 |
| Papers With Code | → | — | 302 redirect to HF Papers trending; captured above |
| Web (global) | ~15 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~10 pages | — | 🇯🇵 Zenn, Qiita; DuckDuckGo CAPTCHA-blocked |
| Web (China) | ~10 pages | — | 🇨🇳 CSDN, Zhihu; DuckDuckGo CAPTCHA-blocked |
| Reddit r/MachineLearning | 0 | — | Blocked (consistent) |
| X/Twitter | 0 | — | Excluded per instructions |
| Bluesky | 0 | — | bluesky=OK; no paradigm-watch posts surfaced |
| YouTube / TikTok / Instagram / Polymarket | 0 | — | Not swept |

---

## Synthesized Findings

Prior threads.json (2026-08-28): 39 threads. All accounted for below. One new thread, two updates.

---

### 1. [new] ARC-AGI-1: 44% for 67 Cents via Transductive Test-Time Training — No Pretraining Required 🌐

**ASSUMPTION VIOLATED:** That competitive ARC-AGI-1 performance requires large-scale language model pretraining — a small transformer trained from scratch in 1.5 hours for $0.67 total (training + inference) now matches TRM/HRM models and beats many frontier LLMs.

**Claim:** Mithil Vakde's blog post (HN #5, 230 pts, 64 comments) demonstrates 44% on ARC-AGI-1's public eval set at $0.67 total cost using a small autoregressive transformer trained from scratch via transductive test-time learning.

**Evidence:**
- **Architecture:** Small autoregressive transformer. NOT an LLM. No pretraining on large corpora.
- **Training method:** Transductive TTT — trains on puzzle *inputs* at eval time (labels stay hidden); cross-task learning via per-task learnable embeddings
- **Key components:** 3D RoPE (handles 2D grid layout), SwiGLU, RMSNorm, NorMuon optimizer, data augmentation (color + dihedral group permutations)
- **Cost:** 1.5h training on a single RTX 5090 + inference = $0.67 total for all 400 public ARC-AGI-1 eval tasks
- **Score:** 44% — matches TRM/HRM models; beats many frontier LLMs on this benchmark
- **Leaderboard:** Author reports 10th place on Kaggle private test set
- **Controversy:** "Transduction = cheating" debate in HN thread; author rebuts: "ARC is a metalearning benchmark, each puzzle uses a different rule" and labels were never seen
- **Prior art context:** T5-ARC (OpenReview) uses similar transductive approach; pure transductive methods cap ~40%; hybrid methods reach 80-94%
- **Relationship to BDH-CQ:** Different architecture and method. BDH-CQ (recurrent latent reasoning, 150M params, $0.0007/task, 29.5%) vs Vakde (TTT transformer from scratch, 44%, $0.67 total ≈ $0.0017/task on 400 tasks). Both attack the same "expensive" assumption from different angles.

**Sources:** [HN thread (230 pts)](https://news.ycombinator.com/item?id=49519939) | [Mithil Vakde's blog](https://mvakde.github.io/blog/44-on-arc-1/) | [ARC Progress Survey arXiv](https://arxiv.org/html/2603.13372v1) | [T5-ARC OpenReview](https://openreview.net/forum?noteId=TtGONY7UKy) | [BenchLM leaderboard](https://benchlm.ai/benchmarks/arcagi1)

**Platforms:** 🌐 Hacker News (#5, 230 pts)

---

### 2. [update] DLSS 5 Official Launch: Sep 3 with NBA 2K27 🌐

**New fact:** DLSS 5 launches Thursday September 3 with NBA 2K27 as first title. Confirmed RTX 5090 at 594fps, RTX 5070 at 262fps (both at 2560×1440, 6× frame-gen + DLSS SR Quality). Engadget calls it "divisive." Official launch date settles the Aug 28 "fall 2026" estimate.

**ASSUMPTION UPDATED:** Pixel-space diffusion transformer for real-time game rendering now shipping commercially, first available Sept 3 2026.

**Evidence:**
- **Launch:** Sep 3, 2026 (Thursday) at 9pm PT; NBA 2K27 first title
- **Hardware:** RTX 50 series full feature; older hardware partial
- **Performance numbers:** RTX 5090 594fps | RTX 5070 262fps at 2560×1440 (note: includes 6× multi frame-gen + DLSS SR on Quality — native rendering lower)
- **Visual improvements reported:** Realistic hair, dramatically improved shadows, jersey-skin interaction, light visible through ears
- **Reception:** Engadget labels it "divisive"; TechRadar: "I was genuinely impressed... but one thing still worries me"; Wccftech: "pixel-accurate" hands-on positive
- **GeForce Now inclusion:** Available day-one via streaming

**Sources:** [The Verge (Techmeme headline)](https://www.theverge.com/tech/986378/nvidia-dlss-5-launch-nba-2k27) | [Tweaktown](https://www.tweaktown.com/news/113374/nvidia-confirms-dlss-5s-official-release-date-its-out-this-week-for-nba-2k27/index.html) | [Club386](https://www.club386.com/nvidia-dlss-5-release-date/) | [HotHardware](https://hothardware.com/news/nvidia-dlss-5-neural-rendering-launch-thursday) | [Engadget](https://www.engadget.com/2248399/nvidia-dlss-5-launches-nba-2k27-september-3/) | [Wccftech](https://wccftech.com/nvidia-dlss-5-nba-2k27-hands-on-pixel-accurate/) | [Aroged](https://www.aroged.com/2026/09/01/nvidia-dlss-5-announces-official-release-date-nba-2k27-will-be-the-first-supported-game/) | [Neowin](https://www.neowin.net/news/nvidias-divisive-dlss-5-launches-this-week-with-nba-2k27/) | [TechRadar](https://www.techradar.com/computing/gpu/i-played-nba-2k27-with-nvidias-dlss-5-at-gamescom-and-i-was-genuinely-impressed-with-it-but-one-thing-still-worries-me)

**Platforms:** 🌐 Techmeme | 🌐 The Verge | 🌐 Wccftech | 🌐 Engadget

---

### 3. [update] World-Model Race: Matrix-Game 3.5 Adds Physics Engine + Robot Control to Real-Time World Simulation 🌐🇨🇳

**New fact:** Matrix-Game 3.5 (Kunlun Wanwei / Skywork AI, released at WAIC/BAAI 2026 in July, HF paper arXiv 2608.29910) — 5B-param model achieving 20FPS real-time interaction at 720p on a single GPU, now HF daily papers + strong CSDN/Zhihu coverage. First open-source world model combining real-time performance + full physics simulation + native robot joint output.

**ASSUMPTION UPDATED:** Real-time interactive world simulation has expanded beyond visual fidelity to include verifiable physics and direct robot control output on consumer hardware.

**Evidence:**
- **Parameters:** 5B (DiT-based)
- **Performance:** 20FPS at 720p on single GPU; minute-level temporal scene stability
- **Patch Memory:** Decomposes frames into 3D-coordinate-tagged spatial patches (octree-indexed) for geometry-aware retrieval — "stores space, not frames"
- **Warped PRoPE:** Camera projection geometry injected into spatiotemporal RoPE — no added learnable parameters
- **Physics engine:** Native gravity, collision detection, rigid body dynamics — not post-hoc filtering
- **Robot output:** Produces joint commands directly from world predictions
- **Distillation:** Progressive real-time distillation via Perceptual Flow Matching + curriculum Self-Rollout DMD (converts bidirectional diffusion → few-step real-time generator)
- **Positioning (CN):** "国内，昆仑万维的Matrix-Game是该赛道中起步最早、系统化程度最高的力量之一" (Among CN players, Kunlun's Matrix-Game is the earliest and most systematized in this space)
- **BAAI framing:** "从 Token 到世界状态预测，多模态的下一场范式革命" (From token to world state prediction — the next multimodal paradigm revolution)
- **Open-source:** Yes — GitHub at https://github.com/Riemann-Dynamics/Matrix-Game-3.5

**Sources:** [HF Paper arXiv 2608.29910](https://huggingface.co/papers/2608.29910) | [Matrix-Game 3.5 project page](https://matrix-game-v3-5.github.io/) | [GitHub](https://github.com/Riemann-Dynamics/Matrix-Game-3.5) | [HappyRock deep dive 🌐](https://www.happyrock.cloud/blog/2026-07-23_kunlun_matrix_game_3.5_interactive_world_model_patch_memory_20fps_single_gpu_deep_dive_en/) | [CSDN 🇨🇳](https://blog.csdn.net/csdnnews/article/details/162009132) | [Zhihu 🇨🇳](https://zhuanlan.zhihu.com/p/2021611429766148365) | [AIBoss](https://www.aiboss88.com/en/news/project-matrix-game3-5)

**Platforms:** 🌐 HuggingFace Papers | 🇨🇳 CSDN | 🇨🇳 Zhihu

---

**Still true** (ongoing — no new facts today):

- **bdh-cq-recurrent-latent-reasoning**: BDH-CQ still #1 HF trending (766 upvotes); 150M, recurrent latent reasoning, 29.5% ARC-AGI-1 at $0.0007/task.
- **llm-lean-proof-automation**: Station math multi-agent; Astra 10 proofs; Claude Riemann zeta.
- **diffusion-lm-scaling-wave**: LLaDA MoE v2, Nemotron-Diffusion, ELYZA JP diffusion LM, Sander Dieleman, Self-OPD. [first seen Aug 5; last update Aug 28]
- **samsung-lpddr5x-pim**: Samsung Hot Chips 2026; 3.01× inference; edge DRAM compute.
- **rockAI-yan-native-memory**: RockAI Yan non-Transformer; training-inference sync; WAIC 2026.
- **glm53-emergent-exploit-chain**: GLM-5.3 open-weight; ExploitBench 54.4%; Cursor vulnerability.
- **modus-decoder-only-any-to-any**: EPFL MODUS + SenseNova-U1 NEO-unify MoE.
- **colibri-lumabri-consumer-moe-p2p**: FreeToken 105 HF upvotes; 284B on gaming desktop.
- **nvidia-groq3-lpx-hardware-disaggregation**: Groq 3 LPX full production; 3,400 tok/s Gemma 4 31B.
- **llm-inference-engine-exploit-escape**: Boyd Kane essay (HN 158 pts); vLLM CVE eval() exploit.
- **stop-anthropomorphizing-llm-reasoning-traces**: Kambhampati et al. ICML 2026; 250 HN pts.
- **ant-asynchronous-neural-turing-networks**: UMass Amherst ANT; no global sync clock; continuous learning.
- **cerebras-wse-onchip-sram-inference**: Cerebras WSE; GPT-5.6 Sol 750 tok/s.
- **full-bandwidth-transformer-latent-feedback**: arXiv 2608.08888; GLU hidden-state feedback; ~1.5× data efficiency.
- **needle2-simple-attention-network**: Needle2 14MB SAN; no FFN; 500+ tok/s on RPi 5.
- **lfm2-5-hybrid-conv-lm**: LFM2.5 2.6B; 220 tok/s on CPU; hybrid conv.
- **steerling-interpretable-diffusion-lm**: Steerling-8B; interpretability scales with capability.
- **taalas-msic-weights-in-silicon**: AMD/Taalas ROM silicon; 16,960 tok/s Llama 3.1 8B.
- **maple-preview-ternary-moe**: Maple-Preview ternary MoE; IMO math at 5.31GB.
- **olix-otpu-photonic-ai-inference**: Olix DX-1 photonic; $312M; H2 2027.
- **rlsvr-spyrl-self-verifiable-rewards**: RLSVR/SpyRL; verifiable RL for creative writing.
- **neoteai-tactile-native-embodied-ai**: N₀-TWAM; touch native modality; 99% vs 35%.
- **odeworld-continuous-latent-world-model**: ODEWorld; ODE integration in latent space.
- **meshy-t2-flow-matching-mesh-generation**: Meshy T2; flow-matching 3D mesh in 6s.
- **openai-astra-ten-math-proofs**: Astra 10 open math problems; Lean 4; ~$2K.
- **frontis-ma1-recursive-ml-self-improvement**: Frontis-MA1 35B; 71.21% MLE-Bench; RTX 4090.
- **orca-baai-next-state-prediction**: BAAI Orca; Next-State-Prediction; 125K hrs video.
- **phizero-physical-language-world-model**: CASIA PhiZero; discrete physical language from unlabeled video.
- **turbovla-llm-bypass-vla**: TurboVLA; V+L→A without LLM; 32Hz.
- **gemini-robotics-2-whole-body-vla**: DeepMind Gemini Robotics 2; full humanoid VLA.
- **intact-search-free-world-model**: INTACT; eliminates CEM search; 300× faster.
- **transformer-transformer-robot-codesign**: Stanford Transformer Transformer; robot body+policy co-design.
- **qwen-agentworld-language-world-model**: Qwen-AgentWorld; language model as environment simulator.
- **three-body-scattering-generative**: Three-Body Scattering; FID=1.63, single forward pass.
- **multiverse-compactifai-tensor-network**: CompactifAI; quantum tensor network 80-95% compression.
- **vibevoice-diffusion-speech**: VibeVoice 177 HF trending; next-token diffusion for speech.
- **spectral-prior-diffusion**: Spectral Alignment; fixes diffusion exposure bias across all major models.
- **jacobian-conjecture-ai-mathematics**: Claude Fable 5 Jacobian counterexample; verification ongoing.
- **kimi-k3-kda-architecture**: Kimi Delta Attention; 6.3× faster decoding.

---

## Cross-Source Patterns

### Pattern 1: Cheap Intelligence — ARC-AGI as the Canary

ARC-AGI-1 has become the paradigm-watch signal for whether expensive compute is truly necessary for intelligence. Three approaches now converge on this signal from different angles:
- **BDH-CQ** (150M params, recurrent latent, 29.5%, $0.0007/task) — efficiency through architecture
- **Vakde 67¢** (small TTT transformer from scratch, 44%, $0.67 total) — efficiency through transductive learning
- **Maple-Preview** (ternary MoE, IMO-level math at 5.31GB) — efficiency through quantization

All three violate the assumption that this class of performance requires large-scale pretraining and expensive inference. The combined signal suggests that *multiple* distinct paths to cheap intelligence now exist in parallel.

**Platforms:** 🌐 HN | 🌐 HF Papers

### Pattern 2: World Models Grow Feet — From Video to Physics to Robots

Matrix-Game 3.5 completes a progression: prior world models were video generators; Matrix-Game 3.5 adds native physics and native robot control. The world model field is no longer asking "can we simulate?" but "can the simulation directly actuate?" This pattern aligns with ODEWorld (latent ODE world model), INTACT (search-free deployment), BAAI Orca (Next-State-Prediction), and NeoteAI tactile AI — a consistent push from representation toward grounded action.

**Platforms:** 🌐 HF Papers | 🇨🇳 CSDN | 🇨🇳 Zhihu

### Pattern 3: Diffusion Everywhere — Now in Real-Time Game Rendering

DLSS 5's Sep 3 launch extends the diffusion model wave into commercial real-time rendering. The diffusion architecture family now ships across: language (LLaDA, Nemotron-Diffusion, ELYZA), speech (VibeVoice), 3D mesh (Meshy T2), and GPU-in-the-loop game rendering (DLSS 5). Pattern: the same denoising paradigm is successively colonizing output domains that were previously served by domain-specific deterministic algorithms.

**Platforms:** 🌐 Techmeme | 🌐 The Verge | 🇯🇵 Zenn (ELYZA-LLM-Diffusion)

---

## Per-Platform Tables

**Hacker News (paradigm-watch relevant):**
| User | Title | Points | Comments | Scope | URL |
|------|-------|--------|----------|-------|-----|
| evilmathkid | 44% on ARC-AGI-1 in 67 cents | 230 | 64 | **Paradigm-watch [new arc-agi-ttt]** | https://news.ycombinator.com/item?id=49519939 |
| — | GPU World | 337 | 202 | OOS (fiction/speculation project) | https://www.gpuworld.org/ |

**HuggingFace Papers (paradigm-watch relevant — daily):**
| Title | Upvotes | Scope | URL |
|-------|---------|-------|-----|
| Does On-Policy Distillation Really Distill? From Noisy Teacher to Self-Improvement | 86 | OOS but notable | https://huggingface.co/papers/2608.31046 |
| DreamX-Creator: Native Audio-Video Generation at 2K | 84 | Adjacent modus-decoder-only thread | https://huggingface.co/papers/2608.31106 |
| GenFirst: Generation Before Reconstruction | 55 | OOS but notable | https://huggingface.co/papers/2608.29335 |
| Scaling Large Reasoning Models beyond Human Supervision | 21 | OOS but notable | https://huggingface.co/papers/2608.31075 |
| Matrix-Game 3.5: Enhancing Real-Time Streaming Interactive World Models | 3 | **Paradigm-watch [update world-model-race]** | https://huggingface.co/papers/2608.29910 |
| WebWorld: The Browser as a World Model | 3 | Paradigm-watch adjacent | https://huggingface.co/papers/2608.30530 |

**HuggingFace Papers (paradigm-watch relevant — trending):**
| Title | Upvotes | Scope | URL |
|-------|---------|-------|-----|
| BDH-CQ: Recurrent Latent Reasoning (trending #1) | 766 | **Paradigm-watch [ongoing bdh-cq]** | https://huggingface.co/papers/2608.09888 |
| FreeToken: Edge-Native MoE | 105 | **Paradigm-watch [ongoing colibri]** | https://huggingface.co/papers/2608.16157 |
| VibeVoice: Next-token diffusion for speech | 177 | **Paradigm-watch [ongoing vibevoice]** | https://huggingface.co/papers/2508.19205 |
| StateM: 95.3% Terminal-Bench (trending #2) | 445 | OOS Scope 1 | https://huggingface.co/papers/2608.15089 |
| Apodex 1.1: Agentic Intelligence | 205 | OOS Scope 1 | https://huggingface.co/papers/2608.23283 |

**GitHub Trending (paradigm-watch relevant):**
| Repo | Stars | Daily | Description | URL |
|------|-------|-------|-------------|-----|
| jingyaogong/minimind | 56,851 | 1,005 | "Train a 64M-parameter LLM from scratch in just 2h!" | https://github.com/jingyaogong/minimind |

*Full 15-repo list in raw.md. Dominated by Scope 1 agent tooling.*

**Techmeme (paradigm-watch relevant):**
| Story | Source | URL |
|-------|--------|-----|
| Nvidia Launches DLSS 5 Technology | The Verge | https://www.theverge.com/tech/986378/nvidia-dlss-5-launch-nba-2k27 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Mithil Vakde's Blog | https://mvakde.github.io/blog/44-on-arc-1/ | ARC-AGI-1 44% at $0.67 total; TTT transformer from scratch |
| 🌐 | HN item 49519939 | https://news.ycombinator.com/item?id=49519939 | ARC-AGI-1 discussion; "NOT an LLM" clarification |
| 🌐 | ARC Progress Survey | https://arxiv.org/html/2603.13372v1 | Transductive cap ~40%; hybrid peaks 80-94% |
| 🌐 | T5-ARC OpenReview | https://openreview.net/forum?noteId=TtGONY7UKy | Prior transductive TTT for ARC-AGI |
| 🌐 | BenchLM Leaderboard | https://benchlm.ai/benchmarks/arcagi1 | ARC-AGI-1 scores Aug 2026 |
| 🌐 | The Verge | https://www.theverge.com/tech/986378/nvidia-dlss-5-launch-nba-2k27 | DLSS 5 official launch |
| 🌐 | Tweaktown | https://www.tweaktown.com/news/113374/nvidia-confirms-dlss-5s-official-release-date-its-out-this-week-for-nba-2k27/index.html | DLSS 5 Sep 3 date confirmed |
| 🌐 | Club386 | https://www.club386.com/nvidia-dlss-5-release-date/ | DLSS 5 Sep 3 date |
| 🌐 | HotHardware | https://hothardware.com/news/nvidia-dlss-5-neural-rendering-launch-thursday | DLSS 5 Thursday launch |
| 🌐 | Engadget | https://www.engadget.com/2248399/nvidia-dlss-5-launches-nba-2k27-september-3/ | "Divisive" framing |
| 🌐 | Wccftech | https://wccftech.com/nvidia-dlss-5-nba-2k27-hands-on-pixel-accurate/ | RTX 5090 594fps; hands-on |
| 🌐 | Aroged | https://www.aroged.com/2026/09/01/nvidia-dlss-5-announces-official-release-date-nba-2k27-will-be-the-first-supported-game/ | Official release date |
| 🌐 | Neowin | https://www.neowin.net/news/nvidias-divisive-dlss-5-launches-this-week-with-nba-2k27/ | Divisive DLSS 5 |
| 🌐 | TechRadar | https://www.techradar.com/computing/gpu/i-played-nba-2k27-with-nvidias-dlss-5-at-gamescom-and-i-was-genuinely-impressed-with-it-but-one-thing-still-worries-me | Hands-on impressed |
| 🌐 | HappyRock | https://www.happyrock.cloud/blog/2026-07-23_kunlun_matrix_game_3.5_interactive_world_model_patch_memory_20fps_single_gpu_deep_dive_en/ | Matrix-Game 3.5 deep dive; 5B/20FPS/720p specs |
| 🌐 | Matrix-Game 3.5 Project Page | https://matrix-game-v3-5.github.io/ | Project landing page |
| 🌐 | Matrix-Game 3.5 GitHub | https://github.com/Riemann-Dynamics/Matrix-Game-3.5 | Open-source repo |
| 🌐 | AIBoss | https://www.aiboss88.com/en/news/project-matrix-game3-5 | Matrix-Game 3.5 profile |
| 🌐 | Adaline Labs | https://labs.adaline.ai/p/the-ai-research-landscape-in-2026 | 7 AI breakthroughs reshaping production |
| 🇯🇵 | Zenn (ELYZA) | https://zenn.dev/elyza/articles/f9dd010e895a34 | ELYZA-LLM-Diffusion JP diffusion LM |
| 🇯🇵 | Zenn (world model survey) | https://zenn.dev/taniii_shio/articles/311b721b7d9782 | World model current state Mar 2026 |
| 🇯🇵 | Zenn (world model guide) | https://zenn.dev/headwaters/articles/d9459829107754 | Complete AI world model guide |
| 🇯🇵 | Qiita (aokikenichi) | https://qiita.com/aokikenichi/items/7023491f03e5ebf9391a | 2026 generative AI overview |
| 🇯🇵 | Qiita (ARC-AGI-3) | https://qiita.com/kai_kou/items/3c7eeaac89e85d9dece2 | ARC-AGI-3 intro; frontier models <1% |
| 🇨🇳 | CSDN News | https://blog.csdn.net/csdnnews/article/details/162009132 | Matrix-Game 3.5 BAAI announcement |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2021611429766148365 | Matrix-Game 3.0→3.5 evolution |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2036554354874962873 | World model survey May 2026 |
| 🇨🇳 | CSDN (BAAI) | https://blog.csdn.net/BAAIBeijing/article/details/161403198 | "Token to world state prediction" paradigm |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2068902612842328752 | Aug 2026 model landscape (OOS) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (blocked, consistent)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not swept)
├─ 🟢 HN: 30 stories swept │ 230 pts paradigm-watch top (ARC-AGI 67¢) │ 337 pts GPU World (fiction/OOS)
├─ 🟣 TikTok: 0 videos (not swept)
├─ 🩷 Instagram: 0 reels (not swept)
├─ 🦋 Bluesky: 0 posts │ 0 likes (bluesky=OK; no paradigm-watch posts surfaced)
├─ 📊 Polymarket: 0 markets (not swept)
├─ 🌐 Web: ~20 pages │ 🇯🇵 ~10 │ 🇨🇳 ~10
└─ 🗣️ Top voices: Mithil Vakde (ARC-AGI 67¢); Kunlun Wanwei Skywork AI (Matrix-Game 3.5)
```

---

## Out of Scope but Notable

*(Per paradigm-watch instructions: these are the items that don't fit today's [new]/[update] findings but caught attention)*

- **GenFirst: Generation Before Reconstruction** (HF 55 upvotes, arXiv 2608.29335): Prioritizes generation objective before reconstruction in latent generative model training. gFID 0.97 on ImageNet-256 (SiT+CFG). Violates: assumption that reconstruction-optimized latents are optimal for downstream generation. Authors: Guangting Zheng et al. Not high enough engagement to classify as paradigm-shift-level but architecturally interesting. [https://huggingface.co/papers/2608.29335](https://huggingface.co/papers/2608.29335)

- **"Does On-Policy Distillation Really Distill?"** (HF 86 upvotes, arXiv 2608.31046): Finds that on-policy distillation (OPD) of LLMs often degrades into self-improvement from noisy teacher signal rather than true knowledge transfer. Three failure mechanisms: local teacher noise, horizon coverage decay, myopic per-token supervision. Challenges the assumption that OPD reliably transfers teacher capability to student. Adjacent to diffusion-lm-scaling-wave's Self-OPD thread but focused on LLMs generally. [https://huggingface.co/papers/2608.31046](https://huggingface.co/papers/2608.31046)

- **Scaling Large Reasoning Models beyond Human Supervision: A Path toward Superintelligence** (HF 21 upvotes, arXiv 2608.31075): 5-level ladder (L0-L4) for progressively removing human oversight. L4 = full co-evolution of policies, rewards, and experience. Assumption violated: that direct human evaluation can scale with model capability. May fit Scope 2 (AI software factory). [https://huggingface.co/papers/2608.31075](https://huggingface.co/papers/2608.31075)

- **GPU World** (HN #15, 337 pts, 202 comments): Fiction/speculation project imagining "one GPU per person" with AI capability frozen at Sep 1, 2026. Accepting story submissions for publication on gpuworld.org, paradigm.xyz, gwern.net. Not an AI advance, but signals HN community imagining a world where current AI becomes cheap ubiquitous infrastructure — a cultural signal. [https://www.gpuworld.org/](https://www.gpuworld.org/)

- **BAAI 2026 Conference — "From Token to World State Prediction"**: BAAI's conference framing of the "next multimodal paradigm revolution" as a shift from next-token prediction to next-world-state prediction. Aligns with BAAI Orca (ongoing thread orca-baai-next-state-prediction). New framing language, not a new system. [https://blog.csdn.net/BAAIBeijing/article/details/161403198](https://blog.csdn.net/BAAIBeijing/article/details/161403198) 🇨🇳

---

## Data Gaps

- **/last30days skill:** Unavailable (consistent with all prior runs). Manual sweep conducted.
- **Reddit r/MachineLearning:** Blocked (consistent).
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (consistent). Fell back to native-language WebSearch.
- **Zhihu:** Direct page fetches return 403 (consistent). Content via search snippets only.
- **Juejin:** JS-required; not directly fetchable. Not represented today.
- **Bluesky:** bluesky=OK; no paradigm-watch posts surfaced.
- **YouTube / TikTok / Instagram / Polymarket:** Not swept.
- **Papers With Code:** 302 redirect to HF Papers; captured via HF sweep.

**Coverage estimate: ~75%.** HN full front page (30 stories), HuggingFace Daily Papers (36 papers), HuggingFace Trending (~27 papers), GitHub Trending (15 repos), Techmeme (~9 stories), global web (~20 pages), JP hubs (~10 pages via WebSearch), CN hubs (~10 pages via WebSearch). Reddit, YouTube, Bluesky, TikTok, Instagram, Polymarket absent. DuckDuckGo CAPTCHA-blocked (mitigated by WebSearch fallback). Today was relatively quiet — Tim Cook retirement dominated non-AI news; HN front page sparse on paradigm-watch AI items.

---

## Key Quotes

> "This is NOT an LLM. its a small ar transformer trained from scratch." — Mithil Vakde (author, 231-pt HN comment) on the ARC-AGI-1 44% in 67 cents result ([link](https://news.ycombinator.com/item?id=49519939)) 🌐

> "The labels were not trained on. They are hidden." — Mithil Vakde rebutting "transduction = cheating" argument ([link](https://news.ycombinator.com/item?id=49519939)) 🌐

> "国内，昆仑万维的Matrix-Game是该赛道中起步最早、系统化程度最高的力量之一" ("Among domestic players, Kunlun's Matrix-Game is the earliest and most systematized in this space") — Zhihu on Matrix-Game 3.5 ([link](https://zhuanlan.zhihu.com/p/2021611429766148365)) 🇨🇳

> "从 Token 到世界状态预测，多模态的下一场范式革命" ("From token to world state prediction — the next multimodal paradigm revolution") — BAAI 2026 Conference framing ([link](https://blog.csdn.net/BAAIBeijing/article/details/161403198)) 🇨🇳

> "Nvidia's divisive DLSS 5 launches this week with NBA 2K27" — Neowin, Sep 1 ([link](https://www.neowin.net/news/nvidias-divisive-dlss-5-launches-this-week-with-nba-2k27/)) 🌐

> "Pure transductive approaches on ARC-AGI cap around 40%, pure inductive methods reach 80%, while hybrid approaches achieve the highest peaks at 80-94%." — ARC Progress Survey arXiv 2603.13372 ([link](https://arxiv.org/html/2603.13372v1)) 🌐

> "Matrix-Game 3.5 represents a paradigm shift from 'video generators that produce pretty pictures' to 'world simulators that understand physics, support real-time interaction, and drive robots'" — HappyRock deep dive ([link](https://www.happyrock.cloud/blog/2026-07-23_kunlun_matrix_game_3.5_interactive_world_model_patch_memory_20fps_single_gpu_deep_dive_en/)) 🌐
