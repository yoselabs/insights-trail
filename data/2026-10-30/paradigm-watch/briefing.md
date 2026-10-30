# Paradigm Watch — Daily Briefing
**Date:** 2026-10-30
**Query type:** GENERAL
**Sources:** Hacker News (front page + threads), GitHub Trending, HuggingFace Papers (daily), Techmeme, WebSearch (global), WebSearch (🇯🇵 Japanese), WebSearch (🇨🇳 Chinese), Gigazine, BigGo Finance JP, Sina Finance Tech, OSCHINA, 53AI, cnyes, note.com, Zhihu

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~30 stories scanned; 2 paradigm-relevant | Qwenputer 690/145; Nintendo 3/0 | 🌐 keyword-free front-page sweep + Oct 28-29 threads |
| HuggingFace Papers | ~20 daily scanned; 2 paradigm-relevant | IDM 234↑; JEPA 5↑ | 🌐 |
| GitHub Trending | 9 repos scanned; 0 paradigm-relevant | all scope 1/2 | 🌐 |
| Techmeme | ~5 stories; 0 paradigm-relevant | Binance hack dominated | 🌐 |
| Web (global) | ~35 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~3 pages | — | 🇯🇵 Gigazine, BigGo Finance JP, note.com (older) |
| Web (China) | ~6 pages | — | 🇨🇳 Sina Finance, OSCHINA, 53AI, cnyes, vibecafe, Zhihu |

---

## Synthesized Findings

### 1. [new] Qwenputer: RISC-V CPU Compiled Directly Into LLM Weights — No Training Required

**Assumption violated:** Neural network weights can only store statistical learned patterns from training; they cannot be programmed as deterministic computational hardware.

**Claim:** Developer Divyansh Agrawal compiled a working 32-bit RISC-V CPU directly into the weights of Qwen3.5-4B with no training involved — a compiler sets every weight. The model runs C and MicroPython programs inside its own forward passes, using its Gated DeltaNet layers as RAM. Doom E1M1 has been rendered via the compiled CPU circuit.

**Evidence:**
- **Architecture:** 11 new transformer layers inserted before Qwen's 32, all compiler-determined (no learned weights); CPU = RV32IM + Zba + bignum coprocessor
- **RAM mechanism:** Gated DeltaNet (linear RNN) layers repurposed as memory: gate=1, beta=1, one-hot keys → exact addressable row reads/writes; CPU registers, stack, program counter all stored in DeltaNet heads
- **Benchmarks (greedy, 40 problems each):**
  - DeepMind mul_big: 55.0% → **97.5%**
  - DeepMind div_big: 72.5% → **97.5%**
  - NUPA long-integer: 48.6% → **100%** (matches Python-tool-assisted Qwen)
  - ~18M consecutive instructions without error; ~230K positions validated, KL divergence 6e-4
- **Variants shipped:**
  - CHIP-8 machine compiled in (classic game console; 100% on 3–20 digit arithmetic)
  - Doom E1M1 via RV32IM firmware on Qwenputer: 6,342,933 trace tokens; all matched independent reference CPU ([repo](https://github.com/Ad1tyaNarayana/qwenputer-doom))
  - NPU variant: VDOT/SMAQA neural instructions → runs a second LM (Karpathy's stories260K) as C program inside Qwen ([HF](https://huggingface.co/divagr1925/Qwenputer-npu))
- **Trade-offs:** Model doubles to 18.8GB; requires specialized inference driver; each CPU instruction = multiple token generations (ms → s per instruction); 24GB+ GPU needed
- **HN skepticism:** "claim of 'no external runtime' is dishonest given required inference driver changes"; "real innovation would be systems that *learn* to use such structures during training"; "this is fun and games" — enthusiasm tempered by pragmatism

**Sources (🌐):**
[GitHub repo](https://github.com/divagr18/qwenputer) · [Author blog](https://divagr.com/blog/qwenputer) · [HN 690pts/145c](https://news.ycombinator.com/item?id=50282838) · [HF base](https://huggingface.co/divagr1925/Qwen3.5-4B-Qwenputer) · [HF CHIP-8](https://huggingface.co/divagr1925/Qwen3.5-4B-Qwenputer-CHIP8) · [HF NPU](https://huggingface.co/divagr1925/Qwenputer-npu) · [Doom repo](https://github.com/Ad1tyaNarayana/qwenputer-doom) · [Games repo](https://github.com/Ad1tyaNarayana/qwenputer-games) · [Adafruit Oct 28](https://blog.adafruit.com/2026/10/28/qwenputer-a-risc-v-cpu-inside-a-models-weights/) · [aiweekly](https://aiweekly.co/alerts/qwenputer-compiles-a-risc-v-cpu-into-qwen35-4b-weights) · [Startup Fortune](https://startupfortune.com/a-developer-compiled-a-working-risc-v-cpu-into-a-4b-parameter-models-weights/) · [news.lavx](https://news.lavx.hu/article/qwenputer-compiles-risc-v-cpu-directly-into-qwen-3-5-weights) · [Medium explainer](https://medium.com/data-science-in-your-pocket/what-is-qwenputer-a-working-risc-v-cpu-inside-qwen3-5-febb522f000b) · [context7](https://context7.com/divagr18/qwenputer)

**JP sources (🇯🇵):**
> "「AIの中にCPUを作る」という異色の試み" ("An unusual attempt to 'build a CPU inside AI'") — Gigazine ([link](https://gigazine.net/news/20261030-qwenputer/))

[Gigazine Oct 30](https://gigazine.net/news/20261030-qwenputer/) · [BigGo Finance JP](https://finance.biggo.jp/news/87fb9728-0bd5-45a5-afcd-db7636741581)

**CN sources (🇨🇳):**
> "拿注意力层当内存——有人在 Qwen 权重里编译了一颗 RISC-V CPU" ("Using attention layers as memory — someone compiled a RISC-V CPU into Qwen weights") — OSCHINA ([link](https://www.oschina.net/news/503307/qwenputer-risc-v))

> "以前大模型做数学题，要么'猜'答案，要么调用外部Python解释器。现在这位开发者直接给模型内部装上了一台真正的计算机" ("Previously, large models either 'guessed' at math problems or called external Python interpreters. Now this developer installed an actual computer inside the model itself.") — 53AI ([link](https://www.53ai.com/news/OpenSourceLLM/2026102982934.html))

[Sina Finance Tech](https://finance.sina.com.cn/tech/digi/2026-10-30/doc-iniwysmw2326047.shtml) · [OSCHINA](https://www.oschina.net/news/503307/qwenputer-risc-v) · [53AI](https://www.53ai.com/news/OpenSourceLLM/2026102982934.html) · [cnyes TW](https://m.cnyes.com/news/id/6640772) · [vibecafe](https://vibecafe.ai/news/cmvti64pr000e08jw20nyd0wv)

**Platforms:** HN (690/145 pts), Adafruit, aiweekly, GitHub, HuggingFace, Gigazine 🇯🇵, BigGo JP 🇯🇵, Sina Finance 🇨🇳, OSCHINA 🇨🇳, 53AI 🇨🇳, cnyes 🇨🇳

---

### 2. [new] LeCun + Balestriero Prove Platonic Representation Theorem for JEPAs — 109M Model Out-Aligns 72B LLMs

**Assumption violated:** Scale (bigger models + more data) is the primary lever for better multimodal representations; this proves positive view quality, not scale, is the fundamental driver.

**Claim:** Balestriero and LeCun prove the Platonic Representation Hypothesis for JEPAs: networks trained separately on different modalities converge to the same representation up to one rotation when positive pairs are two observations of the same scene ("good views"). Next-token prediction is shown to be a JEPA with "bad views," explaining why LLMs need massive scale for multimodal alignment.

**Evidence:**
- **Theorem:** JEPAs trained on good views learn the same representation up to one rotation — separate training problems are the same problem in different coordinate systems
- **Efficiency gap:** Good views require **42× fewer training samples** than next-token prediction for equivalent alignment
- **Empirical claim:** 109M text JEPA outperforms LMs up to 72B on PRH alignment benchmarks (WIT-1024: JEPA 0.184 vs LMs 0.125–0.154)
- **Application demonstrated:** Image captioning with only frozen encoders + a single learned rotation matrix; no paired image-caption training data needed
- **Mechanism:** JEPAs are spectral embedding methods (learn eigenvectors of positive-pair kernel); SIGReg/whitening prevents collapse
- **Authors:** Randall Balestriero + Yann LeCun (galilai-group / Meta FAIR); arXiv:2610.39302; published Oct 29, 2026
- **Caveats:** Experiments use LeJEPA (uniqueness proof doesn't cover it); image encoders use crops (bad-view); no experiment meets hypotheses exactly; Recap-DataComp uses LLaVA recaptions (implicit image-text signal may inflate good-view gains). Independent replication needed.

**Sources (🌐):**
[arXiv:2610.39302](https://arxiv.org/abs/2610.39302) · [arXiv HTML](https://arxiv.org/html/2610.39302) · [HuggingFace (5↑)](https://huggingface.co/papers/2610.39302) · [Papers With Code](https://paperswithcode.co/paper/2610.39302) · [aiweekly](https://aiweekly.co/alerts/lecun-and-balestriero-prove-platonic-representation-theorem-for-jepas)

**CN background (🇨🇳):**
> "Yann LeCun 执着二十年的JEPA，这条路走通了吗？" ("The JEPA Yann LeCun Has Obsessed Over for 20 Years — Has This Path Finally Worked?") — Zhihu ([link](https://zhuanlan.zhihu.com/p/2031403464715129027))

[Zhihu 4-year JEPA review](https://zhuanlan.zhihu.com/p/1994180751378367474) · [Zhihu LeCun JEPA 20yr](https://zhuanlan.zhihu.com/p/2031403464715129027)

**JP background (🇯🇵):**
> "LLMはシンボルの世界に存在し、空間と時間の世界にはない" ("LLMs exist in the world of symbols, not in the world of space and time") — quoting LeCun, from note.com/betaitohuman ([Jun 2026 background](https://note.com/betaitohuman/n/n2234ed7de4b2))

**Platforms:** HuggingFace Papers, arXiv, aiweekly, Papers With Code, Zhihu 🇨🇳 (background), note.com 🇯🇵 (background)

---

**Still true** (ongoing, no new facts today):

- `llm-lean-proof-automation` — ETH (OpenAI+Claude independent convergence Oct 16) + Kakeya + Yang-Mills; Simons Foundation $5M review ongoing; no updates since Oct 27. [TechCrunch](https://techcrunch.com/2026/10/27/frontier-ai-labs-say-their-models-refuted-the-exponential-time-hypothesis-what-does-that-mean/)
- `worldtui-terminal-world-model` — WorldTUI 360M terminal simulator (Oct 23)
- `anthropic-formal-verification-assembly` — Claude: 239 OSS-Fuzz entry points, 180M Rocq lines, assembly-level (Oct 23)
- `fable-steganography-emergent-communication` — Fable 5.1 emergent steganography; cross-model decode 78% (Oct 23)
- `voxcpm2-tokenizer-free-tts` — VoxCPM2 tokenizer-free TTS via continuous diffusion-AR (Oct 23)
- `diffusion-lm-scaling-wave` — Mercury 3 at 1068 tok/sec, 8/12 benchmarks beat Luna/Haiku 5.5 (Oct 23)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra embodied competence gap (Oct 23)
- `world-model-race` — LaLa-World/FCP temporal shortcut; CN >20B CNY; world model race ongoing (Oct 23)
- `ncm-coarse-to-fine-parallel-generation` — NCM 10-31× speedup over diffusion LMs (Oct 23)
- `fleet-learning-collective-robots` — AgiBot fleet binary-outcome learning 97.3% (Oct 23)
- `competing-learning-hybrid-architectures` — Tsinghua NLP SSM/attention competing learning; BLD fix (Oct 23)
- `goodfire-neural-networks-clean` — Goodfire: 90% neurons single-job; polysemanticity challenged (Oct 16)
- `minions-distributed-apple-silicon-gpu` — Minions + Muse Spark 816B on 2 Mac Studios (Oct 16)
- `typesafe-jev-system-one-models` — TypeSafe Jev + OpenAI Decisions API GA (Oct 23)
- `visionhope-self-modifying-backbone` — VisionHOPE 5-memory self-modifying backbone (Oct 9)
- `sgf-plus-decoupled-gradient-flows` — SGF+ 5s train → 24h video (Oct 9)
- `dust-backprop-free-training` — Dust zeroth-order competitive with backprop (Oct 9)
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
- `frontis-ma1-recursive-ml-self-improvement` — RSI-Anything; NUS: true R1/R2 not demonstrated (Oct 23)
- `thinking-inertia-reasoning-control` — LLMs can't suppress explicit reasoning (Oct 13)
- `msar-depth-attention-residuals` — MSAR content-dependent depth attention 1.58× (Oct 13)

*(Retired this run — last_seen >30 days: `esp32s3-bitnet-distributed-cluster` last_seen 2026-09-29; `massalloc-attention-compute-allocation` last_seen 2026-09-29)*

---

## Cross-Source Patterns

**1. LLM weight space as programmable substrate — not just learned patterns (HN 🌐 × Gigazine 🇯🇵 × Sina/OSCHINA/53AI 🇨🇳)**
- Qwenputer: CPU compiled via direct weight assignment; no training
- WorldTUI (Oct 23): 360M model simulates terminal state via learned patterns
- Distinction emerging: compiler-set weights (Qwenputer) vs trained weights (WorldTUI) — both challenge the boundary between "AI model" and "software"
- CN framing: "拿注意力层当内存" (using attention as memory) — community immediately grasped the architectural novelty
- Pattern: weight space is increasingly seen as an execution medium, not just a statistical approximation

**2. Non-AR generation paradigms advancing simultaneously (HuggingFace 🌐 × arXiv 🌐)**
- JEPA theorem (Oct 29): proves good-view architecture, not scale, drives multimodal alignment
- Diffusion LMs (Mercury 3, ongoing): already at 1068 tok/sec commercial threshold
- NCM (ongoing): 10-31× speedup over diffusion LMs via hierarchical parallel generation
- Converging signal: multiple groups proving the "AR is the only scaling paradigm" assumption is false

**3. Global same-day technical community coverage of paradigm items (HN 🌐 × Gigazine 🇯🇵 × Sina/OSCHINA 🇨🇳)**
- Qwenputer covered on same day (Oct 30) by Gigazine, Sina Finance, OSCHINA, 53AI — rapid international uptake
- Framing differences: HN: "strong counter-example to LLM limitations"; JP: "異色の試み" (unusual attempt); CN: "神迹出现了" (a miracle appeared) / "拿注意力层当内存" (using attention as memory)

---

## Per-Platform Tables

**Hacker News:**
| Title | Points | Comments | Notable Quote | URL |
|-------|--------|----------|--------------|-----|
| Qwenputer: A functioning, deterministic RISC-V CPU inside Qwen3.5 | 690 | 145 | "Strong counter-example to claims about LLM limitations" | https://news.ycombinator.com/item?id=50282838 |
| A Working Nintendo in ~1GB of Qwen Weights | 3 | discuss | (CHIP-8 variant reference, low engagement) | github.com/dbreunig |
| We're releasing the weights of Mistral Large 4 | 1,643 | 426 | (Scope 4) | mistral.ai |
| We ran AI agent swarms in Minecraft and Mindustry | 372 | 152 | (Scope 1) | labs.ycombinator.com |
| Backdoor in Claude Code for VS Code (Cursor Marketplace) | 365 | 358 | (Security/Scope 1) | phorion.io |

**HuggingFace:**
| Paper | Upvotes | Institution | Status | URL |
|-------|---------|-------------|--------|-----|
| Proving and Improving the Platonic Representation Hypothesis with JEPAs | 5 | galilai-group (LeCun+Balestriero) | [new] | https://huggingface.co/papers/2610.39302 |
| L3G-World: Real-Time Infinite World Generation with Latent 3D Gaussian Memory | 34 | KAIST AI | World model thread | https://huggingface.co/papers/2610.40614 |
| Multi-Token Prediction Done Right | 7 | MIT | AR training fix | https://huggingface.co/papers/2610.38331 |
| Intrinsic Distribution Matching | 234 | inclusionAI | Diffusion distillation | https://huggingface.co/papers/2610.39633 |
| A-RSI | 145 | Xiaomi Research | Scope 3 | https://huggingface.co/papers/2610.38568 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | GitHub (divagr18) | https://github.com/divagr18/qwenputer | Qwenputer main repo, MIT |
| 🌐 | Author blog | https://divagr.com/blog/qwenputer | Full technical write-up |
| 🌐 | HuggingFace base | https://huggingface.co/divagr1925/Qwen3.5-4B-Qwenputer | Base model card |
| 🌐 | HuggingFace CHIP-8 | https://huggingface.co/divagr1925/Qwen3.5-4B-Qwenputer-CHIP8 | Game console variant |
| 🌐 | HuggingFace NPU | https://huggingface.co/divagr1925/Qwenputer-npu | Neural processing unit variant |
| 🌐 | Doom repo | https://github.com/Ad1tyaNarayana/qwenputer-doom | First Doom frame via LLM-compiled CPU |
| 🌐 | Games repo | https://github.com/Ad1tyaNarayana/qwenputer-games | CHIP-8 games + Doom audit |
| 🌐 | Adafruit | https://blog.adafruit.com/2026/10/28/qwenputer-a-risc-v-cpu-inside-a-models-weights/ | Coverage Oct 28 |
| 🌐 | aiweekly | https://aiweekly.co/alerts/qwenputer-compiles-a-risc-v-cpu-into-qwen35-4b-weights | Summary |
| 🌐 | Startup Fortune | https://startupfortune.com/a-developer-compiled-a-working-risc-v-cpu-into-a-4b-parameter-models-weights/ | Coverage |
| 🌐 | news.lavx | https://news.lavx.hu/article/qwenputer-compiles-risc-v-cpu-directly-into-qwen-3-5-weights | Coverage |
| 🌐 | Medium explainer | https://medium.com/data-science-in-your-pocket/what-is-qwenputer-a-working-risc-v-cpu-inside-qwen3-5-febb522f000b | Explainer |
| 🌐 | context7 | https://context7.com/divagr18/qwenputer | Doc mirror |
| 🌐 | arXiv JEPA | https://arxiv.org/abs/2610.39302 | LeCun+Balestriero theorem |
| 🌐 | arXiv HTML | https://arxiv.org/html/2610.39302 | JEPA HTML |
| 🌐 | Papers With Code | https://paperswithcode.co/paper/2610.39302 | JEPA entry |
| 🌐 | aiweekly JEPA | https://aiweekly.co/alerts/lecun-and-balestriero-prove-platonic-representation-theorem-for-jepas | JEPA summary |
| 🌐 | TechCrunch ETH | https://techcrunch.com/2026/10/27/frontier-ai-labs-say-their-models-refuted-the-exponential-time-hypothesis-what-does-that-mean/ | ETH ongoing |
| 🇯🇵 | Gigazine | https://gigazine.net/news/20261030-qwenputer/ | Qwenputer JP coverage Oct 30 |
| 🇯🇵 | BigGo Finance JP | https://finance.biggo.jp/news/87fb9728-0bd5-45a5-afcd-db7636741581 | Qwenputer JP |
| 🇯🇵 | note.com/betaitohuman | https://note.com/betaitohuman/n/n2234ed7de4b2 | JEPA/LeJEPA background Jun 2026 |
| 🇨🇳 | Sina Finance Tech | https://finance.sina.com.cn/tech/digi/2026-10-30/doc-iniwysmw2326047.shtml | Qwenputer CN Oct 30 |
| 🇨🇳 | OSCHINA | https://www.oschina.net/news/503307/qwenputer-risc-v | Qwenputer CN |
| 🇨🇳 | 53AI | https://www.53ai.com/news/OpenSourceLLM/2026102982934.html | Qwenputer "miracle" framing |
| 🇨🇳 | cnyes (TW) | https://m.cnyes.com/news/id/6640772 | Qwenputer Traditional Chinese |
| 🇨🇳 | vibecafe | https://vibecafe.ai/news/cmvti64pr000e08jw20nyd0wv | Qwenputer CN |
| 🇨🇳 | Zhihu JEPA history | https://zhuanlan.zhihu.com/p/1994180751378367474 | JEPA 4-year evolution CN |
| 🇨🇳 | Zhihu JEPA LeCun | https://zhuanlan.zhihu.com/p/2031403464715129027 | LeCun JEPA 20-year journey |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (persistent)
├─ 🔵 X: excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~30 stories scanned │ 2 paradigm-relevant │ Qwenputer 690/145 │ Nintendo CHIP-8 3/0
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ health OK; no paradigm posts surfaced
├─ 📊 Polymarket: 0 markets │ Polymarket suffered vendor compromise today (security incident, unrelated)
├─ 🌐 Web: ~35 pages │ 🇯🇵 3 (Gigazine, BigGo, note.com older) │ 🇨🇳 7 (Sina, OSCHINA, 53AI, cnyes, vibecafe, Zhihu ×2)
└─ 🗣️ Top voices: Divyansh Agrawal (@divagr1925) · Yann LeCun · Randall Balestriero
```

---

## Out of Scope but Notable

- **Mistral Large 4 released** (HN #1 at time of scan, 1,643 pts/426c; [mistral.ai](https://mistral.ai/news/mistral-large-4)): 1T-param MoE, 52B active, natively multimodal, weights releasing by month-end, trained on 3,800 NVIDIA Grace Blackwell GPUs in Mistral's own EU datacenters. **Scope 4** (open/non-US models). Notable paradigm edge: first frontier-scale open European model, potential regulatory-autonomy angle.

- **AI agent swarms in Minecraft and Mindustry** (HN 372 pts/152c; [labs.ycombinator.com](https://labs.ycombinator.com)): YC Labs ran multi-agent swarms in game environments. **Scope 1** (agent harnesses). Notable: game-world grounding as agent training substrate continuing to grow.

- **L3G-World: Real-Time Infinite World Generation with Latent 3D Gaussian Memory** (HF 34↑; KAIST AI; [arXiv](https://huggingface.co/papers/2610.40614)): stores VAE latent features in 3D Gaussian primitives; renders directly into DiT latent space, 349-359× faster conditioning, 9 FPS on H100. Borderline **world-model-race** thread (ongoing). Notable for memory architecture innovation — Gaussians as the persistent spatial world state.

- **Multi-Token Prediction Done Right** (HF 7↑; MIT; [arXiv:2610.38331](https://huggingface.co/papers/2610.38331)): decomposes MTP cross-entropy gradient into a useful KL self-distillation term and a harmful low-SNR residual; "soft-MTP" recovers useful signal via one-line code change, no new parameters. Borderline `sharpening-tax-post-training-coverage` / `post-training-behavioral-shadows` threads — shows the MTP training objective has a structural flaw at scale.

---

## Data Gaps

- **Reddit (r/MachineLearning):** Blocked persistent — all runs
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for JP and CN queries — **ninth consecutive run** (Oct 2, 6, 9, 13, 16, 20, 23, 27, 30). JP/CN done via WebSearch + direct WebFetch
- **Bluesky:** Health OK; no paradigm-specific posts surfaced
- **TikTok / Instagram / YouTube:** Not swept
- **Papers With Code trending:** Covered via HuggingFace route + direct search
- **last30days skill:** Unavailable in this environment; sweep conducted manually
- **Adafruit blog:** 403 Forbidden on WebFetch
- **OSCHINA article:** 403 Forbidden on WebFetch; content inferred from search extract
- **Zhihu LeCun article:** 403 Forbidden on WebFetch

**Coverage estimate:** ~82%. Strong on HN, HuggingFace Papers, GitHub Trending, Web global, CN hubs (5 sources on Qwenputer). Moderate JP (Gigazine same-day; no Qiita/Zenn today for new items). Reddit/Bluesky zero.

---

## Key Quotes

> "A computer, compiled into the weights of a language model. An exact CPU inside Qwen3.5-4B, with Gated DeltaNet state as RAM." — Divyansh Agrawal, Qwenputer GitHub README ([link](https://github.com/divagr18/qwenputer)) 🌐

> "The model's own Gated DeltaNet layers act as the RAM, so C and MicroPython run during the forward passes with no external runtime." — Qwenputer blog ([link](https://divagr.com/blog/qwenputer)) 🌐

> "This is a strong counter-example to claims about LLM limitations." — HN commenter on Qwenputer ([link](https://news.ycombinator.com/item?id=50282838)) 🌐

> "JEPAs trained on good views learn the same representation up to one rotation — separate training problems are the same problem written in different coordinate systems." — Balestriero + LeCun, arXiv:2610.39302 ([link](https://arxiv.org/abs/2610.39302)) 🌐

> "Good views require 42 times fewer training samples to reach equivalent alignment [vs next-token prediction]." — arXiv:2610.39302 ([link](https://arxiv.org/html/2610.39302)) 🌐

> "「AIの中にCPUを作る」という異色の試み" ("An unusual attempt to 'build a CPU inside AI'") — Gigazine Oct 30 ([link](https://gigazine.net/news/20261030-qwenputer/)) 🇯🇵

> "拿注意力层当内存——有人在 Qwen 权重里编译了一颗 RISC-V CPU" ("Using attention layers as memory — someone compiled a RISC-V CPU into Qwen weights") — OSCHINA ([link](https://www.oschina.net/news/503307/qwenputer-risc-v)) 🇨🇳

> "以前大模型做数学题，要么'猜'答案，要么调用外部Python解释器。现在这位开发者直接给模型内部装上了一台真正的计算机" ("Previously, large models either 'guessed' at math problems or called external Python interpreters. Now this developer installed an actual computer inside the model itself.") — 53AI ([link](https://www.53ai.com/news/OpenSourceLLM/2026102982934.html)) 🇨🇳
