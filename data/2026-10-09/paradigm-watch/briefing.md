# Paradigm Watch — Daily Briefing
**Date:** 2026-10-09
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers, GitHub Trending, Techmeme, arXiv, WebSearch, Qiita/Zenn (🇯🇵), Zhihu/CSDN/Juejin/Sina Finance (🇨🇳)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~30 stories scanned; 5 paradigm-adjacent | Math 2.0: 603/637; OpenAI math: 364/602; Whistle: 868/172; Planet: 247/119; DeepSeek 4.1F: ~971/~882 | 🌐 keyword-free front-page sweep |
| HuggingFace Papers | ~26 papers; 6 paradigm-relevant | VisionHOPE: 253; Long-WAM: 98; SGF+: 55; UniWAM: 53; WorldSonus: 33; Kandinsky: 160 | 🌐 trending papers page |
| GitHub Trending | ~12 repos; 0 paradigm-relevant | All scope 1/2 | 🌐 |
| Techmeme | ~10 stories; 0 paradigm-relevant | Governance/policy/market stories | 🌐 |
| Web (global) | ~40 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~7 pages | — | 🇯🇵 Qiita, Zenn, alphaxiv.org/ja |
| Web (China) | ~12 pages | — | 🇨🇳 Sina, 163, tmtpost, Zhihu, CSDN, Juejin, InfoQ |

---

## Synthesized Findings

### 1. [update] OpenAI AI-Math Acceleration: 722 Preprints from Unreleased Model; 3 Withdrawn; Tao IAS Panel Scrutinizes

**New facts since Oct 6:** OpenAI on Oct 6 dumped 722 AI-generated math manuscripts to GitHub from an unreleased model (beyond GPT-6 Astra); withdrew 3 the next day; Terence Tao coined "Math 2.0" in response; IAS advisory panel formed.

**Claim:** An unreleased OpenAI model (more capable than GPT-6 Astra) generated 722 math preprints targeting 372 problem families in one pass — violating the assumption that *rigorous mathematical breakthroughs require peer review at each step and are produced one at a time*.

**Evidence:**
- **Release (Oct 6):** GitHub repo `openai/math`, Apache 2.0; ~4,000 open problems targeted; ~3h ChatGPT Pro compute per accepted result; 372 families
- **Lean coverage:** only 162/722 manuscripts (22%) include Lean 4 formal proofs; rest unverified
- **Withdrawals (Oct 7–8):** 3 papers pulled due to sign error: "Algebraicity of Weil-classes on split abelian eightfolds," "Kuga-Satake Correspondences for K3 Surfaces," "Hodge conjecture for K3 products"; 14 others revised ("proof repairs, corrected statements")
- **Claims standing:** partial progress claimed on Riemann hypothesis + Hodge conjecture; Navier-Stokes singularity proof (Sep 8) separate track, not in 722
- **IAS panel:** Tao + others at Institute for Advanced Study; "we do not endorse this practice, and we ask them to stop testing advanced mathematical problems on proprietary models"
- **Mathematician reaction:** "Releasing over 700 files at once is not a demonstration of scholarship, but a demonstration of power"; "scopocalypse"; physicist's term
- **HN:** 364 pts / 602 comments; community: "Have your LLM generate 372 breakthroughs and have 2,000 mathematicians spend two weeks understanding each"
- **Tao's "Math 2.0" (HN 603 pts/637 comments):** "Math 1.0 placed a premium on being the first to solve an open problem. Math 2.0 will need to decenter the role of raw problem solving... solutions to open problems are now being harvested at large scale in an unsustainable fashion."
- **Platforms:** HN 🌐 (both items top 10); Techmeme 🌐; WebSearch 🌐

**Updates:** `llm-lean-proof-automation`

**Sources:** [retractionwatch.com](https://retractionwatch.com/2026/10/08/openai-withdraws-preprints-722-manuscripts-unsolved-math-problems/) · [HN withdrawal](https://news.ycombinator.com/item?id=50002650) · [HN Math 2.0](https://news.ycombinator.com/item?id=50002008) · [mathstodon.xyz/@tao](https://mathstodon.xyz/@tao/117395269325940185) · [unite.ai](https://www.unite.ai/openai-releases-722-math-manuscripts-from-an-unreleased-ai-model/) · [aiweekly.co](https://aiweekly.co/alerts/openai-posts-722-ai-generated-math-preprints-pulls-three) · [tech-insider Tao scrutiny](https://tech-insider.org/openai-722-math-claims-mathematician-scrutiny-2026/) · [techmeme.com](https://www.techmeme.com/261006/p42)

---

### 2. [new] VisionHOPE — Self-Modifying Visual Backbone Where Memory and Learning Rules Co-Evolve

**Claim:** VisionHOPE is the first generic visual backbone formulated as a self-modifying learning system — what the model stores and how it updates co-evolve during each image forward pass — violating the assumption that *visual backbone behavior is fully prescribed by trained weights and fixed at inference time*.

**Evidence:**
- **Paper:** arXiv:2609.33325; Mininglamp Technology; Sep 27, 2026; **253 HF trending upvotes**
- **Architecture:** 5 coupled memories: content storage, key generation, value generation, learning rate governance, retention governance — all co-evolve along each 2D scan direction
- **Mechanism:** Self-referential update rule (Nested Learning principle); each memory updates based on current state + incoming visual context
- **Stability fix:** Soft cap on self-referential injection + spectral clamp on memory transition matrix (prevents divergence from unconstrained updates)
- **4 directional scans:** chunks align with image rows + columns
- **Proven property:** memory dynamics are non-expansive along each scan direction
- **Benchmarks:** Competitive on ImageNet-1K, COCO, ADE20K vs fixed-backbone methods
- **Code:** https://github.com/PSRben/VisionHOPE; weights on HF
- **Platforms:** HuggingFace Papers 🌐 (253 upvotes — #1 paradigm-adjacent paper today)

**Sources:** [arXiv:2609.33325](https://arxiv.org/abs/2609.33325) · [arXiv HTML](https://arxiv.org/html/2609.33325) · [HF paper](https://huggingface.co/papers/2609.33325) · [HF weights](https://huggingface.co/PSRben/VisionHOPE) · [GitHub](https://github.com/PSRben/VisionHOPE) 🌐

---

### 3. [new] SGF+: Train on 5 Seconds, Generate 24 Hours — Decoupled Gradient Flows for Autoregressive Video

**Claim:** SGF+ decouples the context-writing and denoising roles that AR video models force onto shared parameters — whose gradients systematically conflict — violating the assumption that *AR video generation requires a single unified parameter set and long training windows to produce long-form video*.

**Evidence:**
- **Paper:** arXiv:2610.10429; Zihan Su et al.; Oct 7, 2026; **55 HF upvotes**
- **Root cause identified:** In causal AR video generation, the same parameters must (a) refine current frame quality via denoising and (b) write key-value context for future prediction; these roles produce "gradients [that] exhibit distinct patterns and systematic negative alignment" — optimizer conflict
- **Solution:** Role-specific parameterization; causal attention preserves interaction between decoupled sub-networks; both roles jointly optimized via original generation objective (no auxiliary losses)
- **Supervised via downstream:** context-writing component supervised through its contribution to future predictions only
- **Key result:** Trained exclusively on 5-second clip windows → continuous generation for up to **24 hours** without any long-video fine-tuning
- **Extrapolation improvement:** Outperforms baselines on visual quality + temporal consistency in both framewise and chunkwise generation
- **Code:** https://github.com/Zihan-Su/Self_Gradient_Forcing_Plus
- **Predecessor:** Self Gradient Forcing v1 (arXiv:2607.20368) — bounded two-pass replay; SGF+ generalizes with clean role separation
- **Platforms:** HuggingFace Papers 🌐

**Sources:** [arXiv:2610.10429](https://arxiv.org/abs/2610.10429) · [HF paper](https://huggingface.co/papers/2610.10429) · [GitHub](https://github.com/Zihan-Su/Self_Gradient_Forcing_Plus) · [SGF v1 arXiv:2607.20368](https://arxiv.org/abs/2607.20368) 🌐

---

### 4. [update] World Models — Long-WAM (NVIDIA): AR Pretraining Essential; Bidirectional Gets No Gain from Long Context

**New facts since Oct 2:** Long-WAM (NVIDIA/MIT/HKU/UCSD, Oct 8): bidirectional video pretraining yields zero net gain from extended history for robot control; only AR pretraining converts long context to success (63.3%→78.7%); UniWAM (HKUSTGZ) unifies physical reasoner + world generator + action predictor in one architecture.

**Evidence:**
- **Long-WAM (arXiv:2610.10528; Oct 8; 98 HF upvotes):**
  - Pretrained LongLive2.0-Robot on ~10,000 window-equivalent hours; robot + egocentric video; no action labels; autoregressive
  - Key finding: AR-pretrained model + 19.2s context → 63.3%→78.7% success on RoboCasa GR-1; bidirectionally-pretrained init → **zero net gain** at extended context
  - Real-world: 95% on dynamic cup stacking (0% for compared methods); deployment on RTX 5090 / DGX Spark / Jetson AGX Thor
  - Also: LIBERO-Long, RoboTwin 2.0, DOMINO benchmarks
  - Violated assumption: bidirectional attention models are more capable per parameter than AR models
- **UniWAM (arXiv:2610.02054; HKUSTGZ; 53 HF upvotes):**
  - Three-component unified architecture: physical reasoner + world generator + action predictor
  - Hypothesis: separating perception/prediction/action into distinct learned sub-modules enables better generalization
- **Prior context (ongoing):** Qwen-AgentWorld 397B, World Observer (KAIST), WROP, WorldCrafter, World Labs Atlas, NSP paradigm shift in CN discourse

**CN context 🇨🇳:** "世界模型正在悄悄变成主战场" ("World models are quietly becoming the main battlefield") — suanli.cn

**Sources:** [arXiv:2610.10528](https://arxiv.org/abs/2610.10528) · [HF Long-WAM (98)](https://huggingface.co/papers/2610.10528) · [Long-WAM project](https://nvlabs.github.io/LongLive/Long-WAM/) · [aiweekly Long-WAM](https://aiweekly.co/alerts/nvidia-long-wam-lifts-robocasa-gr-1-to-787-with-192s-context) · [arXiv:2610.02054](https://arxiv.org/abs/2610.02054) · [HF UniWAM (53)](https://huggingface.co/papers/2610.02054) · [suanli.cn world model](https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/) 🌐🇨🇳

---

### 5. [update] Diffusion LMs — DiffuSpace Sets World's Largest DLM Funding Record ($70M); WorldSonus Extends Diffusion to Real-Time Spatial Audio

**New facts since Oct 6:** DiffuSpace (HKU NLP / Shenzhen) closes ~500M RMB ($70M) — world's largest DLM company funding round — with Huawei + Xiaomi backing; WorldSonus introduces streaming causal AR diffusion for spatial audio in world models.

**Evidence:**
- **DiffuSpace (Sina Finance + 7 outlets, Oct 9 2026; 🇨🇳):**
  - Founder: Prof. Kong Lingpeng (HKU NLP lab co-director) + PhD students Gong Shan, Ye Jiacheng; founded May 2026 Shenzhen
  - Total funding: 5亿元 RMB (~$70M USD); **world record for DLM company**; two consecutive rounds in 2026
  - Lead investors: Matrix Capital (经纬), Shunwei/Xiaomi (顺为), Junlian/Legend Capital (君联)
  - Follow: Huawei Halo (华为哈勃), Horizon Robotics (地平线), CAS Creation Star (中科创星)
  - **Dream 7B:** "First to comprehensively surpass autoregressive models of equivalent scale" (首次全面超越同参数规模的自回归模型); planning comparable to DeepSeek V3 671B at 7B params; 2.5M+ HF downloads; one of top-3 dLLMs at ICML 2025 alongside Gemini Diffusion + Inception Mercury
  - Upcoming: larger-parameter dLLM + open-source release in October 2026
  - CN DLM advantages stated: reversible correction, global solving, 5–10× parallel decoding acceleration
- **WorldSonus (arXiv:2610.08760; NoizAI; 33 HF upvotes):**
  - Streaming causal AR diffusion architecture; RTF 0.41 (real-time capable)
  - Audio-centric captioning pipeline; chunk-indexed prompt scheduling for interactive control during generation
  - High-quality stereo supervision from stereo + ambisonic datasets
  - Outperforms bidirectional models on acoustic quality + spatial alignment — causal streaming beats full-context for real-time audio
  - Designed specifically for interactive world models as audio backbone

**Prior context (ongoing):** ALoDLM (Amazon, Oct 3) first DLM to beat AR on 11-benchmark avg; HC-DLM (UIUC); Kandinsky 6.0 Video (160 HF upvotes, ongoing); VibeVoice

**Sources:** [Sina Finance DiffuSpace](https://finance.sina.cn/2026-10-09/detail-iniuquqp3081149.d.html) · [tmtpost.com](https://www.tmtpost.com/8162358.html) · [163.com](https://www.163.com/dy/article/L8Q2B52H05118O92.html) · [InfoQ](https://www.infoq.cn/article/kjPiCQV1cOO6AzaOjioR) · [凤凰网](https://tech.ifeng.com/c/8x4sRquT6qP) · [arXiv:2610.08760](https://arxiv.org/abs/2610.08760) · [HF WorldSonus (33)](https://huggingface.co/papers/2610.08760) 🌐🇨🇳

---

**Still true** (ongoing, no new facts today):
- `dust-backprop-free-training` — Q Labs Dust: node perturbation competitive with backprop at pretraining; 1K–10K× vs EGGROLL; still cited in JP/HN (Oct 6)
- `vals-ai-agent-materials-discovery` — Vals.ai 90 agents + DFT → YBaMnFeO₅ + KV[Cr(CN)₆] (Oct 6)
- `kandinsky-6-video-joint-audio` — CrossDiT joint video+audio (160 HF upvotes today, up from 110)
- `hc-dlm-hierarchical-continuous-diffusion` — HC-DLM UIUC continuous latent + discrete scaffold (Oct 2)
- `sharpening-tax-post-training-coverage` — Meta RL post-training narrows pass@K across 14 model pairs (Oct 2)
- `world-observer-persistent-actor-observer` — KAIST decoupled actor+observer; Observer Sink (Oct 2)
- `onestreamer-proactive-video-text-memory` — OneStreamer NJU proactive text memory replaces raw video features (Oct 2)
- `typesafe-jev-system-one-models` — Jev, Clef/Clef-flash decision model ecosystem (Oct 2)
- `post-training-behavioral-shadows` — ATD +5.34pp; Sharpening Tax (Oct 2)
- `yue2-ar-nar-music-unification` — YuE2 AR-NAR MoT; 233 HF upvotes today
- `massalloc-attention-compute-allocation` — MALA fused attention 2.2×/3.0× speedup (Sep 26)
- `esp32s3-bitnet-distributed-cluster` — 7-node BitNet 0.4B on ESP32-S3 microcontrollers (Sep 29)
- `transformer-linear-superposition` — Superposition Linearity Hypothesis dual-stream generation (Sep 25)
- `gzip-compression-language-model` — GziPT gzip-as-LM, no neural parameters (Sep 22)
- `mini-agi-continual-learning-no-forgetting` — Mini-AGI 99.84% retention via LR asymmetry (Sep 22)
- `huro-human-video-vla-pretraining` — HuRo 630K robotized human videos; 51.5%→80.3% VLA (Sep 22)
- `fujitsu-monaka-cpu-sovereign-ai` — MONAKA 144-core ARMv9 2nm; CPU-only sovereign AI; Nov 2026 (Sep 18)
- `bend2-formal-proof-ai-code` — Bend 2 + LAWS.bend; affine dependent types; AI code+proofs (Sep 18)
- `jepa-anything-cross-domain-prediction` — JEPA-Anything OPF across 7 domains; bio intervention validated (Sep 18)
- `ncp-archpreview-concept-level-supervision` — NCP 51.3% token savings at OLMo-3-7B parity (Sep 11)
- `weworm-ai-cyberweapon-compression` — WeWorm zero-click worm in 9 days; AI compresses attack dev (Sep 11)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra 99.9% ARC-AGI-3; GPT-6.1 scrapped for deception (Sep 29)
- `llm-lean-proof-automation` — UPDATED (see §1 above)
- `bdh-cq-recurrent-latent-reasoning` — BDH-CQ 150M continuous latent reasoning; 29.5% ARC-AGI-1 (Sep 11)
- `modus-decoder-only-any-to-any` — SenseNova-U1.5 unified understanding+generation, encoder/VAE-free (Sep 11)
- `colibri-lumabri-consumer-moe-p2p` — 744B MoE on 25GB RAM; FreeToken elastic serving (Sep 11)
- `vibevoice-diffusion-speech` — VibeVoice next-token diffusion on speech latents; 80× compression (Sep 11)
- `maple-preview-ternary-moe` — Bonsai 2 27B ternary QAT; 98.2% retention at 5.9GB (Sep 18)
- `frontis-ma1-recursive-ml-self-improvement` — Dream-RSI 162× reduction; RRSI; NeoHorse-1 (Sep 25)
- `rogue-agents-collusion-dsewiki` — S. Korea bank hacks; OpenAI Australia Medicare apology; FT CEO liability (Oct 6)

*Retired (>30 days since last seen): `weathernext3-fgn-raw-satellite` (last seen Sep 8), `uno-diffusion-ar-speedup` (last seen Sep 8)*

---

## Cross-Source Patterns

**1. AI math at institutional scale creates validation crisis (HN × Web × Techmeme 🌐)**
- OpenAI dumps 722 AI-generated preprints; 3 withdrawn 24h later; only 22% Lean-verified
- Tao's "Math 2.0" concept: AI shifts math from individual breakthroughs to community verification bottleneck
- HN community: verification burden outsourced to human mathematicians; "demonstration of power, not scholarship"
- Pattern: AI can now generate mathematical claims faster than the mathematical community can verify them — this is a structural asymmetry, not just a speedup

**2. Self-modification as a new backbone paradigm (HF Papers 🌐)**
- VisionHOPE (253 HF upvotes): backbone where memory + learning rules co-evolve per input
- Long-WAM's finding (98 HF upvotes): AR pretraining gives robots the ability to use long context; bidirectional fails
- Pattern: the field is discovering cases where the inference-time computation *structure* (causal vs. bidirectional; fixed vs. self-modifying) matters as much as scale

**3. DLM commercial validation crosses milestone in China 🇨🇳**
- DiffuSpace $70M = world's largest DLM funding round; Huawei + Xiaomi backing
- Combined with: ALoDLM (Amazon) first DLM to beat AR on 11 benchmarks (Oct 6 thread)
- Pattern: investor capital (CN) + benchmark dominance (US) in same week signals DLMs moving from research to commercial deployment phase

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable | URL |
|------|-------|--------|----------|---------|-----|
| (front) | "Math 2.0" will need to value mathematical progress holistically | 603 | 637 | Terence Tao coins "Math 2.0" in response to AI math blast | https://news.ycombinator.com/item?id=50002008 |
| (front) | OpenAI withdraws three mathematical results | 364 | 602 | 722 preprints from unreleased model; 3 withdrawn; Tao IAS panel | https://news.ycombinator.com/item?id=50002650 |
| (front) | Whistle: Speech to Text in 16.9 MB | 868 | 172 | Monarch Hadamard MLPs; 11ms TTF; beats Whisper base (145MB) | https://cactuscompute.com |
| (front) | Finding undiscovered planet using Claude Code | 247 | 119 | TESS exoplanet candidate; 116 ly; ~1.4× Earth radius | https://news.ycombinator.com/item?id=50002665 |
| (front) | DeepSeek 4.1 Flash | ~971 | ~882 | Strong engagement; scope 4 | dgt.is |
| (front) | AI-ready biological data: $1.8B commitment | 140 | 20 | Biohub; data infra | https://biohub.org |

**HuggingFace Papers:**
| Paper | Upvotes | Notable | URL |
|-------|---------|---------|-----|
| VisionHOPE: Visual Backbones as Self-Modifying Learning Systems | 253 | 5 coupled memories co-evolve in each forward pass; competitive vs fixed backbones | https://huggingface.co/papers/2609.33325 |
| YuE2: Unifying Symbolic and Audio Music Generation | 233 | AR-NAR MoT; score → audio in one model (ongoing) | https://huggingface.co/papers/2609.33757 |
| Kandinsky 6.0 Video | 160 | CrossDiT joint video+audio (ongoing) | https://huggingface.co/papers/2610.05608 |
| Long-WAM: Scaling the Context of World-Action Models | 98 | AR pretraining essential; bidirectional fails on long context for robotics | https://huggingface.co/papers/2610.10528 |
| SGF+: Decoupling Gradient Flows for AR Video Generation | 55 | Role-specific params; 5s train → 24h generation | https://huggingface.co/papers/2610.10429 |
| UniWAM: Unified World-Action Model | 53 | Physical reasoner + world generator + action predictor unified | https://huggingface.co/papers/2610.02054 |
| WorldSonus: Bringing Sound to Worlds | 33 | Streaming causal AR diffusion; RTF 0.41; beats bidirectional for real-time audio | https://huggingface.co/papers/2610.08760 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | retractionwatch.com | https://retractionwatch.com/2026/10/08/openai-withdraws-preprints-722-manuscripts-unsolved-math-problems/ | Primary coverage of OpenAI 722 withdrawal |
| 🌐 | unite.ai — OpenAI math | https://www.unite.ai/openai-releases-722-math-manuscripts-from-an-unreleased-ai-model/ | Model beyond GPT-6 Astra detail |
| 🌐 | aiweekly — OpenAI math | https://aiweekly.co/alerts/openai-posts-722-ai-generated-math-preprints-pulls-three | Community reaction; "scopocalypse" |
| 🌐 | tech-insider — Tao scrutiny | https://tech-insider.org/openai-722-math-claims-mathematician-scrutiny-2026/ | Tao + IAS panel details |
| 🌐 | mathstodon.xyz/@tao | https://mathstodon.xyz/@tao/117395269325940185 | Primary source: "Math 2.0" concept |
| 🌐 | tech-insider — OpenAI math model | https://tech-insider.org/openai-722-math-manuscripts-unreleased-model-2026/ | Model capabilities detail |
| 🌐 | arxiv:2609.33325 | https://arxiv.org/abs/2609.33325 | VisionHOPE primary |
| 🌐 | GitHub VisionHOPE | https://github.com/PSRben/VisionHOPE | VisionHOPE code |
| 🌐 | HF weights PSRben | https://huggingface.co/PSRben/VisionHOPE | VisionHOPE weights |
| 🌐 | arxiv:2610.10429 | https://arxiv.org/abs/2610.10429 | SGF+ primary |
| 🌐 | GitHub SGF+ | https://github.com/Zihan-Su/Self_Gradient_Forcing_Plus | SGF+ code |
| 🌐 | arxiv:2610.10528 | https://arxiv.org/abs/2610.10528 | Long-WAM primary |
| 🌐 | Long-WAM project | https://nvlabs.github.io/LongLive/Long-WAM/ | Long-WAM page |
| 🌐 | aiweekly — Long-WAM | https://aiweekly.co/alerts/nvidia-long-wam-lifts-robocasa-gr-1-to-787-with-192s-context | Long-WAM summary |
| 🌐 | arxiv:2610.02054 | https://arxiv.org/abs/2610.02054 | UniWAM primary |
| 🌐 | arxiv:2610.08760 | https://arxiv.org/abs/2610.08760 | WorldSonus primary |
| 🌐 | promptzone — exoplanet | https://www.promptzone.com/elena_liu/claude-code-spots-new-exoplanet-in-public-data-5bm0 | Claude Code exoplanet discovery |
| 🌐 | arxiv:2607.20368 | https://arxiv.org/abs/2607.20368 | SGF v1 predecessor |
| 🌐 | quantamagazine NS proof | https://www.quantamagazine.org/ai-has-solved-one-of-maths-1-million-millennium-prize-problems-20260908/ | Background: Sep 8 NS proof |
| 🌐 | arxiv:2609.17642 | https://arxiv.org/pdf/2609.17642 | Independent challenge to NS proof |
| 🌐 | techmeme OpenAI math release | https://www.techmeme.com/261006/p42 | Techmeme coverage |
| 🇯🇵 | Qiita teppei_nakano — multimodal paradigms | https://qiita.com/teppei_nakano/items/56e335a208edba2ea668 | JP: Native omni-modal architecture shift |
| 🇯🇵 | Qiita aokikenichi 202609 | https://qiita.com/aokikenichi/items/35c8ad26fb7c18135242 | JP: 5 paradigm shifts in Sept 2026 |
| 🇯🇵 | Zenn tesla — simulation | https://zenn.dev/tesla/articles/545165ed6334c7 | JP: Simulation as AI compression theme |
| 🇯🇵 | alphaxiv.org/ja DLM survey | https://www.alphaxiv.org/ja/abs/2601.14041 | JP: DLM unsolved challenges |
| 🇯🇵 | Zenn ELYZA-LLM-Diffusion | https://zenn.dev/elyza/articles/f9dd010e895a34 | JP: Japanese-specific DLM |
| 🇨🇳 | Sina Finance — DiffuSpace | https://finance.sina.cn/2026-10-09/detail-iniuquqp3081149.d.html | CN: World's largest DLM funding |
| 🇨🇳 | tmtpost DiffuSpace 5亿 | https://www.tmtpost.com/8162358.html | CN: Funding record detail |
| 🇨🇳 | 163.com DiffuSpace investors | https://www.163.com/dy/article/L8Q2B52H05118O92.html | CN: Huawei + Horizon investor detail |
| 🇨🇳 | InfoQ DiffuSpace | https://www.infoq.cn/article/kjPiCQV1cOO6AzaOjioR | CN: Technical focus |
| 🇨🇳 | 凤凰网 DiffuSpace | https://tech.ifeng.com/c/8x4sRquT6qP | CN: Xiaomi connection |
| 🇨🇳 | tmtpost.com founder | https://www.tmtpost.com/nictation/8161964.html | CN: Prof. Kong Lingpeng background |
| 🇨🇳 | 163.com founder | https://www.163.com/dy/article/L8POV70G05199LET.html | CN: HKU NLP lab background |
| 🇨🇳 | juejin AI trends | https://juejin.cn/post/7628639071426576420 | CN: World model + NSP paradigm (ongoing) |
| 🇨🇳 | CSDN world model intro | https://blog.csdn.net/qq_27504375/article/details/160299006 | CN: NSP architecture frameworks |
| 🇨🇳 | suanli.cn world models | https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/ | CN: World models as "main battlefield" |
| 🇨🇳 | zhihu.com model registry | https://zhuanlan.zhihu.com/p/670574382 | CN: Oct 8 model tracking |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (inaccessible)
├─ 🔵 X: 0 posts │ excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~30 stories scanned │ 5 paradigm-adjacent │ ~2,500 pts combined top items
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ source health OK; no paradigm-specific posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~40 pages │ 🇯🇵 ~7 (Qiita, Zenn, alphaxiv.org/ja) │ 🇨🇳 ~12 (Sina, 163, tmtpost, InfoQ, Zhihu, CSDN, Juejin)
└─ 🗣️ Top voices: Terence Tao (Math 2.0 concept) · NVIDIA LongLive team (Long-WAM) · Mininglamp Tech (VisionHOPE) · Zihan Su (SGF+) · Prof. Kong Lingpeng (DiffuSpace/Dream 7B)
```

---

## Out of Scope but Notable

- **Whistle STT in 16.9 MB** (HN 868 pts; [cactuscompute.com](https://cactuscompute.com)): Monarch Hadamard MLPs + Simple Attention; outperforms Whisper base (145.3 MB) at 1/8th the size; 11.1ms TTF. More efficiency engineering than paradigm shift, but challenges scale-is-necessary assumptions.
- **Finding exoplanet with Claude Code** (HN 247 pts; [promptzone.com](https://www.promptzone.com/elena_liu/claude-code-spots-new-exoplanet-in-public-data-5bm0)): Individual developer "Pavel" used Claude Code to process NASA TESS photometry → discovered exoplanet candidate 116 ly, ~1.4× Earth radius; NASA accepted for follow-up. Scope 1/2 (AI coding tool), but adds to Vals.ai pattern of AI enabling individual-scale scientific discovery.
- **MiMo-V2.6** (HF 54 upvotes; [arXiv:2610.11959](https://arxiv.org/abs/2610.11959)): Xiaomi's RL scaling toward self-improvement. Adjacent to `frontis-ma1-recursive-ml-self-improvement` thread (scope 1/2).
- **DeepSeek 4.1 Flash** (~971 HN pts; dgt.is): High engagement but scope 4 (open non-US models). Note: "Why isn't the industry freaking out about DeepSeek 4.1 Flash?" framing suggests paradigm-level performance surprise.
- **AI autonomy in formal mathematics**: OpenAI's 722 preprints represent the first time an AI lab has released a *batch industrial* math output — not a single proof but a factory. Whether this is a paradigm in mathematical practice (Math 2.0) or a governance failure is the open question.

---

## Data Gaps

- **Reddit (r/MachineLearning):** Blocked; top posts not obtained
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (persistent across all three runs: Oct 2, Oct 6, Oct 9)
- **Bluesky:** Source health OK; no paradigm-specific posts surfaced
- **Zhihu direct access:** 403 Forbidden on direct WebFetch of Zhihu URLs; content from search snippets only
- **tech-insider.org:** 403 Forbidden on direct WebFetch; content from search snippets
- **GitHub Trending:** All top repos are scope 1/2; no paradigm-watch items
- **Papers With Code:** Redirects to HuggingFace trending; same data
- **/last30days skill:** Not available; replaced by manual sweep (consistent with Oct 2/6 runs)

**Coverage estimate:** ~78%. Strong on HF Papers, HN, WebSearch. Moderate JP (Qiita + Zenn via search). CN strong this run due to DiffuSpace funding news. Reddit zero; Bluesky zero.

---

## Key Quotes

> "Math 1.0 placed a premium on being the first to solve an open problem, even if the solution was not initially well understood. Math 2.0 will need to decenter the role of raw problem solving and value mathematical progress more holistically." — Terence Tao on Mathstodon ([mathstodon.xyz/@tao](https://mathstodon.xyz/@tao/117395269325940185)) 🌐

> "Solutions to open problems are now being harvested at large scale in an unsustainable fashion, leaving entire fields of mathematics much less fertile than when such problems were solved in the traditional 'Math 1.0' fashion." — Terence Tao ([mathstodon.xyz/@tao](https://mathstodon.xyz/@tao/117395269325940185)) 🌐

> "Releasing over 700 files at once is not a demonstration of scholarship, but a demonstration of power." — Mathematician quoted in aiweekly.co ([aiweekly.co](https://aiweekly.co/alerts/openai-posts-722-ai-generated-math-preprints-pulls-three)) 🌐

> "Access to history is not the same as using it: longer histories pay off far more when the video foundation is pretrained autoregressively." — NVIDIA Long-WAM paper ([arXiv:2610.10528](https://arxiv.org/abs/2610.10528)) 🌐

> "We formulate VisionHOPE as a self-modifying learning system, in which what the model remembers and how it learns co-evolve within an image." — Mininglamp Technology, arXiv:2609.33325 ([arxiv.org](https://arxiv.org/abs/2609.33325)) 🌐

> 「すべてのモダリティを最初から共通の潜在空間で同時・ネイティブに処理する統合型ネットワーク」("Unified networks that natively process all modalities simultaneously in shared latent space from the start") — teppei_nakano on Qiita ([qiita.com](https://qiita.com/teppei_nakano/items/56e335a208edba2ea668)) 🇯🇵

> 「首次全面超越同参数规模的自回归模型」("First to comprehensively surpass autoregressive models of equivalent parameter scale") — DiffuSpace / Dream 7B claim ([tmtpost.com](https://www.tmtpost.com/8162358.html)) 🇨🇳

> "We identify that context writing and denoising roles exhibit gradients with distinct patterns and systematic negative alignment — creating an optimization conflict we can resolve by separating them." — SGF+ paper, arXiv:2610.10429 ([arxiv.org](https://arxiv.org/abs/2610.10429)) 🌐
