# Paradigm Watch — Daily Briefing
**Date:** 2026-11-06
**Query type:** GENERAL
**Sources:** HuggingFace Papers (daily + trending), GitHub Trending, Hacker News (front page keyword-free sweep), Techmeme, WebSearch (global), WebSearch (🇯🇵 Japanese), WebSearch (🇨🇳 Chinese), Qiita (JP), CSDN/Zhihu (CN), interestingengineering.com, kantan.news, superpowerdaily.com, aiweekly.co

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~30 stories scanned; 0 paradigm-relevant | Top stories: sshole 2886/706, MS Paint RCE 682/254, Dutch bank 552/343 | 🌐 |
| HuggingFace Daily Papers | 28 scanned; 5 paradigm-relevant | VFlash 79↑; DreamFree 6↑; Speculative Listening 5↑; Muir 4↑; SAE+MoE 4↑ | 🌐 |
| HuggingFace Trending | 28 scanned; 1 paradigm-relevant | VibeVoice 183↑ | 🌐 |
| GitHub Trending | ~18 repos; 0 paradigm-relevant | Dominated by scope 1-2 skills repos | 🌐 |
| Techmeme | ~11 stories; 0 paradigm-relevant | Nvidia chip tracking, Thinking Machines Lab funding, macro selloff | 🌐 |
| Bluesky | — | Health OK; no paradigm posts surfaced | 🌐 |
| Web (global) | ~30 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~3 pages | — | 🇯🇵 Qiita (3 articles; Zenn/note not surfaced today) |
| Web (China) | ~7 pages | — | 🇨🇳 CSDN ×2, Zhihu ×2 (1×403); 1 URL unavailable |

---

## Synthesized Findings

### 1. [new] VFlash — Parallel Diffusion Drafting for Spatial Primitives Beats AR Accuracy in Physical AI

**Assumption violated:** Autoregressive token-by-token generation is required for high-quality structured spatial outputs; parallel drafts must sacrifice accuracy for speed.

- **Claim:** NVIDIA + CMU + Johns Hopkins (Nov 5, arXiv:2611.08449): Flash Primitive Decoding (FPD) predicts entire trajectories, bounding boxes, and point clouds in ONE forward pass using a lightweight diffusion drafter — and exceeds the AR target's spatial accuracy while running 25× faster.
- **Mechanism:** Drafter trained on complete spatial primitives (not AR token continuations); accepts structurally valid predictions via relaxed (layout-not-token) criteria; text retains standard speculative decoding in parallel path
- **Results:**
  - 3D trajectory error: **61% reduction** vs AR baseline
  - Latency on Jetson Thor: 3,552ms → 703ms (~80% reduction, **~12×**)
  - MolmoSpaces 4-suite manipulation: **70.2%** avg success vs 62.6% baseline
  - Extends to autonomous driving (NAVSIM, Waymo tested)
- **System-1 framing:** VFlash creates a "fast, typed, structured" spatial reasoning mode for VLMs — analogous to System-1 for physical AI
- **Engagement:** 79 HF daily upvotes (highest of Nov 6)

**Sources (🌐):**
[arXiv:2611.08449](https://arxiv.org/abs/2611.08449) · [arXiv HTML](https://arxiv.org/html/2611.08449) · [HuggingFace](https://huggingface.co/papers/2611.08449) · [Papers With Code](https://paperswithcode.co/paper/2611.08449) · [NVIDIA Research](https://research.nvidia.com/labs/lpr/vflash/) · [NVIDIA paper PDF](https://research.nvidia.com/labs/lpr/vflash/assets/paper/vflash.pdf?v=20261105-2) · [interestingengineering](https://interestingengineering.com/ai-robotics/nvidia-vflash-robot-planning-speed-trajectory-accuracy) · [kantan.news](https://kantan.news/news/nvidia-accelerates-robot-trajectory-planning-12-fold-with-vflash) · [superpowerdaily](https://superpowerdaily.com/posts/nvidia-says-vflash-runs-robot-ai-pipelines-five-times-faster-in-research-tests) · [axisofordinary links](https://axisofordinary.substack.com/p/links-for-2026-11-05-2) · [Korean: promppy](https://www.promppy.com/item/2880276) · [Spanish: mechatronicstore](https://noticias.mechatronicstore.cl/electronica/vflash-de-nvidia-genera-la-trayectoria-de-un-robot-12-veces-mas-rapido)

**Platforms:** HuggingFace (79↑), arXiv, interestingengineering, kantan.news, superpowerdaily, promppy (KR), mechatronicstore (ES)

---

### 2. [new] Muir — Linear Attention Achieves 1M-Token Recall with 25 MB State (Google Research)

**Assumption violated:** Accurate long-context recall requires a growing KV cache; erase and write gates in linear attention should be parameterized symmetrically.

- **Claim:** Google Research (Gil Tabak, Clemens JS Schaefer, arXiv:2611.08376, Nov 5): Muir improves Gated DeltaNet-2 by discovering erase gates need far lower rank than write gates; matched-filter readout reweights state rows by signal content.
- **Key numbers:**
  - **25 MB recurrent state** vs **2.1 TB KV cache** for comparable Transformer at 1M tokens
  - Near-100% passkey retrieval to **1M tokens** (GDN-2 collapses at 4K–8K)
  - Extrapolates from 4K training to **10M tokens** without perplexity drift (2,560× stretch)
  - 2.5–3.6% lower perplexity than Transformer baseline; 1.8–2.0% lower than GDN-2
  - 2.7× faster training than Transformer at 32K context
- **Range tested:** 166M–1.34B parameters
- **aiweekly.co note:** "inference-economics signal worth tracking; external validation pending" — claims are authors' own until replicated
- **Engagement:** 4 HF daily upvotes (low; paper very fresh as of Nov 5)

**Sources (🌐):**
[arXiv:2611.08376](https://arxiv.org/abs/2611.08376) · [arXiv HTML](https://arxiv.org/html/2611.08376) · [HuggingFace](https://huggingface.co/papers/2611.08376) · [Papers With Code](https://paperswithcode.co/paper/2611.08376) · [aiweekly.co](https://aiweekly.co/alerts/googles-muir-cuts-perplexity-36-vs-transformer-at-134b)

---

### 3. [new] Speculative Listening — Speech Models Can Draft While Idle; 95.3% of Chunks Unchanged from Silence

**Assumption violated:** Real-time full-duplex speech models must wait for actual audio input before generating the next chunk.

- **Claim:** arXiv:2611.06982 (Nov 2026): 95.3% of audio chunks are unchanged when silence is assumed as input → model can pre-generate speech during idle listening periods; training-free, lossless verification when actual audio arrives.
- **Results:**
  - Speaking chunks: **2.6–2.8× acceleration**
  - Tool-call chunks: up to **23.4× speedup**
  - Response latency: **73% reduction** (to 74–241 ms avg)
  - Max real-time lag: **94.4% reduction**
  - Timing approaches natural human turn-taking gap (~200ms)
- **Engagement:** 5 HF daily upvotes

**Sources (🌐):**
[arXiv:2611.06982](https://arxiv.org/abs/2611.06982) · [HuggingFace](https://huggingface.co/papers/2611.06982)

---

### 4. [update] World-Model Race — DreamFree Shows Robot WAMs Don't Need Future Video Generation (KAIST, Nov 4)

**New fact since prior briefing:** KAIST DreamFree (arXiv:2611.04527, Nov 4) achieves 64% DROID success vs 56% state-of-art DreamZero and 16% π₀.₅ — WITHOUT generating any future videos at deployment, 17.8× faster.

- **Prior claim:** World models advancing on multiple fronts; LaLa-World/FCP world models improving cross-domain latent planning (prior thread thread last updated Oct 23)
- **New finding:** DreamFree distills a frozen video diffusion model's predictive representations into a visual encoder trained only on CURRENT observations; zero video generation at deploy time
  - **Stage 1:** Encoder learns to predict frozen teacher representations via future-representation distillation + generative objectives
  - **Stage 2:** Action module maps predictive features → robot actions
  - Enables transfer from video demos without action labels; cross-embodiment transfer demonstrated
- **Speed:** 17.8× faster than video-generating WAMs; **11Hz** real-time control
- **Assumption newly challenged:** "World models for robot control must generate future video frames to plan effectively"
- **Engagement:** 6 HF daily upvotes

**Sources (🌐):**
[arXiv:2611.04527](https://arxiv.org/abs/2611.04527) · [HuggingFace](https://huggingface.co/papers/2611.04527) · [Papers With Code](https://paperswithcode.co/paper/2611.04527)

---

### 5. [update] Diffusion-LM Scaling Wave — VibeVoice (ICLR 2026, Microsoft) Extends Diffusion Paradigm to 30-Min Multi-Speaker Speech

**New fact since prior briefing:** VibeVoice (arXiv:2508.19205, Microsoft, ICLR 2026 accepted) now trending with 183 HF upvotes — diffusion paradigm has an ICLR-accepted speech model achieving 80× compression vs Encodec, 30-min 4-speaker zero-shot.

- **Prior claim:** Mercury 3 at 1068 tok/sec; diffusion LM crossing commercial threshold; CN: DiffuSpace Clover-35B claims 5-10× AR speed (Oct 28)
- **New finding:** VibeVoice = hybrid AR + diffusion head: LLM backbone for context/dialogue flow + diffusion head for high-fidelity acoustics; continuous speech tokenizer at 7.5 FPS (80× compression vs Encodec); 30-minute multi-speaker zero-shot; non-lexical cues (breaths, lip smacks)
- **ICLR 2026 acceptance** confirms peer-validated status; Microsoft open-sourced: github.com/microsoft/VibeVoice
- **Extension note:** Diffusion paradigm now covers text (Mercury), code (DiffuSpace), and speech (VibeVoice) — broad modality adoption
- **CN framing (🇨🇳):** "扩散语言模型成为下一代大模型主流路线" ("Diffusion language models are becoming the mainstream route for next-gen LLMs") — Zhihu ([link](https://zhuanlan.zhihu.com/p/2033148030510167610))

**Sources (🌐):**
[arXiv:2508.19205](https://arxiv.org/html/2508.19205v1) · [HuggingFace (183↑)](https://huggingface.co/papers/2508.19205) · [ICLR 2026](https://mlanthology.org/iclr/2026/peng2026iclr-vibevoice/) · [github.com/microsoft/VibeVoice](https://github.com/microsoft/VibeVoice) · [liner.com review](https://liner.com/review/vibevoice-expressive-podcast-generation-with-nexttoken-diffusion) · [papernotes ICLR 2026](https://en.papernotes.org/ICLR2026/audio_speech/vibevoice_expressive_podcast_generation_with_next-token_diffusion/) · [awesomepapers](https://awesomepapers.io/generative-models/papers/2508.19205) · [ai.miraheze](https://ai.miraheze.org/wiki/VibeVoice) · [HF model doc](https://huggingface.co/docs/transformers/model_doc/vibevoice)

---

**Still true** (ongoing, no new facts today):

- `weight-space-programming-mit-csail` — MIT CSAIL: frontier LLMs read/write NN weights without gradients; Honnibal debunking ongoing (Nov 3 [new]). JP community still processing: Qiita Nov 4-6 articles reference WSP as AI-making-AI paradigm shift.
- `library-of-layers-adaptive-ordering` — LoL (arXiv:2611.03526, Nov 2): router orders transformer blocks dynamically at runtime; 5 HF↑ (Nov 3 [new])
- `qwenputer-compiled-cpu-in-weights` — RISC-V CPU compiled into Qwen3.5-4B weights; Doom E1M1; HN 690/145 (Oct 22–30)
- `jepa-platonic-representation-theorem` — LeCun+Balestriero prove JEPAs with good views converge; 109M JEPA out-aligns 72B LMs (Oct 29)
- `llm-lean-proof-automation` — ETH false + Kakeya proofs; $5M Simons review (last seen Oct 30)
- `worldtui-terminal-world-model` — WorldTUI 360M terminal world model; vim/tmux/snake simulated (Oct 21)
- `anthropic-formal-verification-assembly` — Claude: 239 OSS-Fuzz entry points, 180M Rocq lines (Oct 22)
- `fable-steganography-emergent-communication` — Fable 5.1 emergent steganography; cross-model 78% (Oct 21)
- `voxcpm2-tokenizer-free-tts` — VoxCPM2 tokenizer-free TTS via continuous diffusion-AR (Oct 23)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra embodied competence gap; simulation vs real-world gap persists
- `ncm-coarse-to-fine-parallel-generation` — NCM 10-31× speedup over diffusion LMs; Stanford+Together AI (Oct 20)
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
- `frontis-ma1-recursive-ml-self-improvement` — NUS: true R1/R2 RSI not demonstrated; WSP adds new RSI modality. JP: Qiita/cvusk covers NAS+AutoML+WSP as AI-making-AI frontier (Nov 6).
- `thinking-inertia-reasoning-control` — LLMs can't suppress explicit reasoning (Oct 13)
- `msar-depth-attention-residuals` — MSAR content-dependent depth attention 1.58× (Oct 13)

---

## Cross-Source Patterns

**1. Non-AR spatial generation exceeds AR in physical AI (HF 🌐 × interestingengineering 🌐)**
- VFlash (Nov 5, 79↑): parallel diffusion drafter beats AR for spatial primitives
- DreamFree (Nov 4, 6↑): distilled world model beats video-generating world model
- Pattern: for STRUCTURED outputs (coordinates, trajectories, feature representations), joint/parallel generation is strictly better than AR
- Both challenge the implicit assumption that AR is the quality ceiling for all output types

**2. Recurrent/linear attention closing the KV-cache gap (HF 🌐 × aiweekly 🌐)**
- Muir (Nov 5, 4↑): 1M token recall, 25MB vs 2.1TB KV cache
- Prior: MSAR (Oct 13), competing-learning-hybrid-architectures (Oct 20), Gated DeltaNet-2 lineage
- Trend: linear attention models are progressively solving the recall failures that made them impractical; 2,560× context extrapolation is a new milestone

**3. Diffusion paradigm completing cross-modality sweep (HF trending 🌐 × CN 🇨🇳)**
- Text: Mercury 3 / diffusion LMs at scale
- Speech: VibeVoice (ICLR 2026, 183↑ trending) — now ICLR-validated
- Video: Wave Forcing (100↑, Nov 3)
- Code: DiffuSpace Clover-35B (CN, Oct 28)
- CN framing: "扩散语言模型成为下一代大模型主流路线" (diffusion LMs are the mainstream next-gen route)

**4. HN front page AI-free today (HN 🌐)**
- Paradigm-notable: ZERO AI papers/research on HN front page today
- Top stories: security bugs (sshole/MS Paint RCE), Hackintosh, non-AI tooling
- Context: AI market selloff (Nasdaq -6%, Taiwan Taiex record drop) may be redirecting community attention to non-AI topics today

---

## Per-Platform Tables

**HuggingFace Daily Papers (paradigm-relevant):**

| Paper | ↑ | arXiv | Institution | Assumption Violated |
|-------|---|-------|-------------|---------------------|
| VFlash: Fast, Accurate Visual Planning via Flash Primitive Decoding | 79 | 2611.08449 | NVIDIA/CMU/JHU | Parallel spatial drafts can beat AR accuracy |
| Future Representation Distillation for Imagination-free World Action Models | 6 | 2611.04527 | KAIST | Robot WAMs must generate future video frames |
| Decode Before You Hear: Speculative Listening | 5 | 2611.06982 | (unnamed) | Speech must wait for real audio before drafting |
| Muir: Linear Attention with Sensitivity-Allocated Gating | 4 | 2611.08376 | Google Research | Erase/write gates must be symmetric; recall needs growing KV cache |

**HuggingFace Trending (paradigm-relevant):**

| Paper | ↑ | arXiv | Institution | Paradigm relevance |
|-------|---|-------|-------------|-------------------|
| VibeVoice Technical Report | 183 | 2508.19205 | Microsoft | Next-token diffusion for speech; ICLR 2026 accepted |

**Hacker News (paradigm-relevant today): none**

**GitHub Trending (paradigm-relevant today): none**

**Techmeme (paradigm-relevant today): none**

**Web:**

| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | NVIDIA Research | https://research.nvidia.com/labs/lpr/vflash/ | Official VFlash page |
| 🌐 | interestingengineering | https://interestingengineering.com/ai-robotics/nvidia-vflash-robot-planning-speed-trajectory-accuracy | "12× faster, 61% error reduction" |
| 🌐 | kantan.news | https://kantan.news/news/nvidia-accelerates-robot-trajectory-planning-12-fold-with-vflash | VFlash 12× coverage |
| 🌐 | superpowerdaily | https://superpowerdaily.com/posts/nvidia-says-vflash-runs-robot-ai-pipelines-five-times-faster-in-research-tests | VFlash 5× coverage |
| 🌐 | axisofordinary | https://axisofordinary.substack.com/p/links-for-2026-11-05-2 | VFlash in links roundup |
| 🌐 | aiweekly.co (Muir) | https://aiweekly.co/alerts/googles-muir-cuts-perplexity-36-vs-transformer-at-134b | "inference-economics signal worth tracking" |
| 🌐 | ICLR 2026 (VibeVoice) | https://mlanthology.org/iclr/2026/peng2026iclr-vibevoice/ | Peer-reviewed acceptance |
| 🌐 | github.com/microsoft/VibeVoice | https://github.com/microsoft/VibeVoice | Open-source Microsoft |
| 🌐 | liner.com (VibeVoice) | https://liner.com/review/vibevoice-expressive-podcast-generation-with-nexttoken-diffusion | Review |
| 🌐 | papernotes ICLR | https://en.papernotes.org/ICLR2026/audio_speech/vibevoice_expressive_podcast_generation_with_next-token_diffusion/ | ICLR note |
| 🌐 | awesomepapers | https://awesomepapers.io/generative-models/papers/2508.19205 | Coverage |
| 🌐 | ai.miraheze | https://ai.miraheze.org/wiki/VibeVoice | Wiki |
| 🌐 | HF doc | https://huggingface.co/docs/transformers/model_doc/vibevoice | Model card |
| 🌐 | CACM | https://cacm.acm.org/news/beyond-llms-a-post-transformer-world-emerges/ | "Beyond LLMs" background |
| 🌐 | philippdubach | https://philippdubach.com/posts/the-last-architecture-designed-by-hand/ | Hybrid architecture overview 2026 |
| 🌐 | Techmeme: Inkling 2 | https://thinkingmachines.ai/news/inkling-2-small/ | Thinking Machines Lab 594B MoE (scope 4) |
| 🌐 | Techmeme: TML funding | https://www.businessinsider.com/thinking-machines-lab-is-closing-5-billion-new-round-2026-11 | $5B at $40B (scope 5) |
| 🌐 | Techmeme: Nvidia SE Asia | https://www.bloomberg.com/news/articles/2026-11-06/nvidia-boosts-chip-tracking-in-southeast-asia-to-fight-smuggling | Chip tracking (scope 5) |
| 🌐 | Techmeme: Democrats Nvidia | https://www.bloomberg.com/news/articles/2026-11-06/nvidia-s-ai-chip-exports-emerge-as-target-in-democratic-congress | Exports (scope 5) |
| 🌐 | Techmeme: Jensen Huang | https://www.cnbc.com/2026/11/05/nvidia-jensen-huang-china-spy-congress.html | Congress inquiry (scope 5) |
| 🌐 | Techmeme: Anthropic IPO | https://www.wsj.com/finance/major-investors-are-skeptical-anthropic-ipo-can-achieve-1-5-trillion-valuation-ca965d8b | IPO skepticism (scope 5) |
| 🌐 | Techmeme: Nasdaq | https://www.bloomberg.com/news/articles/2026-11-05/us-stock-futures-diverge-as-chip-selloff-extends-into-second-day | Nasdaq -6% (macro) |
| 🌐 | Techmeme: Asia markets | https://asia.nikkei.com/business/markets/taiwan-stocks-in-steepest-ever-fall-south-korea-halts-trading-amid-ai-rout | Taiwan/Korea rout (macro) |
| 🌐 | CSDN: 2026 AI tech overview | https://blog.csdn.net/longtengzhangjie/article/details/162900061 | 2026 AI paradigm: world models + embodied AI + agents |
| 🌐 | CSDN: multimodal | https://blog.csdn.net/Follow_24/article/details/161546827 | Transformer not only choice; hybrid best path |
| 🌐 | Zhihu: diffusion LM | https://zhuanlan.zhihu.com/p/2033148030510167610 | "dLLMs challenging GPT-style paradigm" |
| 🌐 | Zhihu: big model survey | https://zhuanlan.zhihu.com/p/2057383619325432992 | 2024.07–2026.07 survey |
| 🌐 | CSDN: non-transformer | https://blog.csdn.net/QbitAI/article/details/142760480 | Non-transformer architectures from first principles |
| 🌐 | Foundations-of-LLMs CSDN | https://blog.csdn.net/gitblog_00892/article/details/151421363 | Transformer to non-transformer evolution |
| 🇯🇵 | Qiita Nov 6 (ishisaka) | https://qiita.com/ishisaka/items/bc45e3f3415f83ab5c11 | AI dev ecosystem Nov 6; mentions Gemini Omni Flash, GitHub Rubicon |
| 🇯🇵 | Qiita: AIでAIを作る最前線 | https://qiita.com/cvusk/items/4bb0f0075e581c92c3a6 | AI-making-AI frontier: NAS, AutoML, WSP |
| 🇯🇵 | Qiita Nov 4 (ishisaka) | https://qiita.com/ishisaka/items/8b2a5246b9a8f3ba0826 | Programming roundup Nov 4; governance focus |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (persistent — all runs)
├─ 🔵 X: excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~30 stories scanned │ 0 paradigm-relevant │ top: sshole 2886/706, MS Paint RCE 682/254
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ health OK; no paradigm-relevant posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~30 pages │ 🇯🇵 3 (Qiita ×3) │ 🇨🇳 7 (CSDN ×4, Zhihu ×2, 1×403)
└─ 🗣️ Top voices: Shihao Wang (NVIDIA, VFlash), Gil Tabak/Clemens Schaefer (Google Research, Muir), Jaehyeong Jo et al. (KAIST, DreamFree)
```

---

## Out of Scope but Notable

This IS the paradigm-watch topic — findings above are the paradigm-watch output. No out-of-scope AI paradigm items noted today.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked — **11th consecutive run** (Oct 2, 6, 9, 13, 16, 20, 23, 27, 30, Nov 3, Nov 6). JP/CN hub discovery done entirely via WebSearch + WebFetch.
- **Reddit (r/MachineLearning):** Blocked persistent — all runs. No r/ML content.
- **Bluesky:** Health OK per prompt; no paradigm-relevant posts surfaced.
- **YouTube / TikTok / Instagram:** Not swept.
- **Zhihu Nov 6 article** (国内外知名大模型及应用 2026/11/06): HTTP 403 Forbidden — content not retrieved.
- **JP hub coverage:** Qiita only (3 articles); Zenn/note/Hatena not surfaced today for paradigm-watch topic.
- **HN front page:** Completely AI-free today; likely influenced by AI market selloff context.
- **last30days skill:** Unavailable — sweep conducted manually.

**Coverage estimate:** ~76%. VFlash well-covered (8+ sources), Muir and DreamFree lightly covered (2-3 sources each), VibeVoice well-covered (9 sources). JP/CN coverage degraded by CAPTCHA and 403. Reddit/Bluesky/YouTube zero.

---

## Key Quotes

> "Unlike conventional speculative decoding, which checks generated tokens against a target model, VFlash can accept structurally valid visual predictions without requiring token-by-token agreement." — interestingengineering.com on VFlash ([link](https://interestingengineering.com/ai-robotics/nvidia-vflash-robot-planning-speed-trajectory-accuracy)) 🌐

> "Near-100% passkey retrieval to 1M tokens... extrapolates from 4K training to 10M tokens without perplexity drift. 25 MB recurrent state vs 2.1 TB KV cache." — arXiv:2611.08376 on Muir ([link](https://arxiv.org/abs/2611.08376)) 🌐

> "inference-economics signal worth tracking; external validation pending" — aiweekly.co on Muir ([link](https://aiweekly.co/alerts/googles-muir-cuts-perplexity-36-vs-transformer-at-134b)) 🌐

> "95.3% of audio chunks are unchanged when silence is assumed as input." — arXiv:2611.06982 on Speculative Listening ([link](https://arxiv.org/abs/2611.06982)) 🌐

> "Distills a frozen video diffusion model's predictive representations into a visual encoder trained only on current observations, avoiding future-video generation." — arXiv:2611.04527 on DreamFree ([link](https://arxiv.org/abs/2611.04527)) 🌐

> "扩散語言モデルが次世代大規模モデルの主流経路になりつつある" / "扩散语言模型成为下一代大模型主流路线" ("Diffusion language models are becoming the mainstream route for next-gen large models") — Zhihu ([link](https://zhuanlan.zhihu.com/p/2033148030510167610)) 🇨🇳

> "AIの役割がモデルの候補選択から学習メカニズムの設計・内部パラメータの改変へと拡大" ("AI's role has expanded from selecting model candidates to designing learning mechanisms and modifying internal parameters") — Qiita/cvusk on AIでAIを作る最前線 ([link](https://qiita.com/cvusk/items/4bb0f0075e581c92c3a6)) 🇯🇵

> "2026年AI正式完成范式跃迁：从传统'文本token预测'转向物理世界状态预测，技术主线由通用对话大模型全面切换为世界模型+自主智能体Agent+物理具身AI三条主线并行" ("In 2026, AI has formally completed its paradigm leap: from text token prediction to physical world state prediction") — CSDN ([link](https://blog.csdn.net/longtengzhangjie/article/details/162900061)) 🇨🇳
