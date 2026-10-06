# Paradigm Watch — Daily Briefing
**Date:** 2026-10-06
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers, GitHub Trending, Techmeme, arXiv, WebSearch, Qiita/alphaxiv (🇯🇵), Zhihu/CSDN/Juejin (🇨🇳)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | ~30 stories scanned; 5 paradigm-adjacent | Mistral L4: 888/528; Opus 5.5 agents: 439/303; Beam: 511/165; Dust: 249/66; Vibecoding: 147/175 | 🌐 keyword-free front-page sweep |
| HuggingFace Papers | ~7 papers scanned; 4 paradigm-relevant | Kandinsky 6.0V: 110; ALoDLM: 48; In-Dist Forcing: 24; Looped Pt II: 14 | 🌐 trending papers page |
| GitHub Trending | ~12 repos; 0 paradigm-relevant | All scope 1/2 (agent harnesses, testing frameworks) | 🌐 |
| Techmeme | ~9 stories; 2 paradigm-relevant | South Korea bank hacks; Australia Medicare apology | 🌐 |
| Web (global) | ~35 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~8 pages | — | 🇯🇵 Qiita, alphaxiv.org/ja, zaikei.co.jp |
| Web (China) | ~7 pages | — | 🇨🇳 Zhihu, CSDN, Juejin |

---

## Synthesized Findings

### 1. [new] Dust — Zeroth-Order Transformer Pretraining Without Backpropagation

**Claim:** A zeroth-order method (node perturbation) is for the first time competitive with backpropagation at pretraining transformer LMs from 2M to 243M params — violating the 40-year assumption that *end-to-end differentiability and the chain rule are required to train neural networks*.

**Evidence:**
- **What it is:** Dust (Q Labs; Samip Dahal, Bishwas Mandal, Serdar Gülbahar, Akshay Vegesna)
- **Mechanism:** Adds Gaussian noise to linear layer outputs independently at each token; each token = virtual population member; one forward pass evaluates the whole population; rewards noise by loss reduction; averages reward-weighted noise to estimate gradients
- **Attention special case:** Credits jitters through attention output gradients (not direct token losses)
- **Pop of 16K:** Cosine similarity with backprop gradient ≈ 0.75 across most layer types
- **Performance (10M tokens, 256 draws):** Dust test loss 5.095 vs backprop 5.066 — essentially competitive at scale
- **Efficiency vs prior ES:** 1,000–10,000× more efficient than EGGROLL (prior weight-space ES method)
- **Counterintuitive scaling:** Larger models (243M) MORE population-efficient than smaller (2M) — opposite of prior ES assumptions
- **Authors' caveat:** "Not yet compute-efficient enough to replace backprop" — still requires ~16K forward passes per update
- **HN:** 249 pts / 66 comments
- **Significance:** Proof-of-concept that differentiability is sufficient but not necessary for LLM pretraining
- **Platforms:** Hacker News 🌐, Qiita 🇯🇵

**Quote:** "Many of the core assumptions in optimization research are completely wrong." — Samip Dahal, Q Labs ([qlabs.sh/research/dust](https://qlabs.sh/research/dust))

**JP coverage 🇯🇵:** 「誤差逆伝播法（Backpropagation）を使わずに、モデルを事前学習する革新的な手法」("An innovative approach to pre-train models without using backpropagation") — Qiita tanakanekosuke ([qiita.com](https://qiita.com/tanakanekosuke/items/7505a402e3fb78209796))

**Sources:** [Paper](https://qlabs.sh/research/dust) · [GitHub](https://github.com/qlabs-eng/dust) · [ai-tldr](https://ai-tldr.dev/releases/qlabs-dust/) · [byteiota](https://byteiota.com/backprop-has-a-real-challenger-dust-trains-transformers/) · [Digg](https://digg.com/ai/5zv01jcm) · [cctest](https://cctest.ai/en/articles/dust-explores-transformer-pretraining-without-backpropagation) · [Qiita 🇯🇵](https://qiita.com/tanakanekosuke/items/7505a402e3fb78209796)

---

### 2. [new] Vals.ai — 90 Claude Opus 5.5 Agents Discover Two Room-Temperature Magnetic Semiconductor Candidates

**Claim:** A swarm of 90 AI agents autonomously ran quantum-mechanical DFT simulations and proposed two spintronic semiconductor candidates — violating the assumption that *AI in science assists data analysis but that hypothesis generation and experimental-level simulation require human scientists*.

**Evidence:**
- **Who:** Vals.ai (published Oct 4–6, 2026); HN 439 pts / 303 comments
- **Agents:** 90 Claude Opus 5.5 agents; ran PBE+U + HSE06 DFT at two approximation levels; generated material design hypotheses; self-corrected 5 errors in own records
- **Found 1 — YBaMnFeO₅ (designed):**
  - 2.35 eV band gap; spin-sorted windows: 1.0 eV (holes), 1.4 eV (electrons)
  - Magnetic ordering ~420–490 K; synthesis instability above 950 K limits practical route
- **Found 2 — KV[Cr(CN)₆] (1999 compound, newly characterized):**
  - 2.1 eV band gap; spin-sorted windows: 2.6 eV (holes), 1.6 eV (electrons)
  - Experimental magnetic ordering: 376 K; already synthesized; structurally stable
- **Both:** Luttinger-compensated antiferromagnets — zero net magnetism yet spin-sort electrons
- **Implication:** Spintronic memory ~1,000× faster switching than ferromagnetic memory, lower crosstalk
- **Open ledger:** 61 claims, all simulation inputs/outputs, claim checker, 5 self-corrections on GitHub
- **Status:** Computational only — neither candidate experimentally confirmed; next step: resynthesize KV[Cr(CN)₆]
- **CN parallel 🇨🇳:** ElementsClaw (Alibaba DAMO + RUC + UCAS, July 2026): 28 GPU hours, 2.4M crystal structures → 68,000 superconductor candidates → 4 experimentally verified — same agent-swarm+DFT approach, 3 months earlier, different material class ([CSDN](https://blog.csdn.net/shaobingj126/article/details/162596976))

**Sources:** [Vals.ai blog](https://www.vals.ai/blogs/room-temperature-magnetic-semiconductors) · [hermes-ai.net](https://hermes-ai.net/news/vals-ai-deploys-90-claude-agents-to-hunt-room-temperature-magnetic/) · [alphasignal.ai](https://alphasignal.ai/news/vals-ai-deploys-90-claude-agents-to-hunt-room-temperature-magnetic) · [ai-tldr](https://ai-tldr.dev/releases/vals-ai-opus-5-5-magnetic-semiconductors/) · [aicoder.com](https://aicoder.com/news/news-20261006-vals-opus-5-5-agents-room-temp-compensated-magnets) · [explainx.ai](https://www.explainx.ai/blog/opus-5-5-agents-room-temperature-magnetic-semiconductor-candidates-2026) · [promptzone.com](https://www.promptzone.com/dito_nakamura/opus-55-agents-identify-two-magnetic-semiconductor-candidates-14np) · [CSDN 🇨🇳](https://blog.csdn.net/shaobingj126/article/details/162596976)

---

### 3. [new] Kandinsky 6.0 Video — Joint Synchronized Video+Audio Generation via CrossDiT

**Claim:** A single diffusion model generates video and synchronized audio simultaneously in one pass using bidirectional cross-attention — violating the assumption that *video and audio are separate modalities requiring sequential or post-hoc alignment*.

**Evidence:**
- **Paper:** arXiv:2610.05608 (Oct 6, 2026); Sber Kandinsky Lab (72+ contributors); MIT license
- **HF:** 110 upvotes (highest today)
- **Architecture (CrossDiT):** Pretrained video stream + newly trained audio stream; bidirectional cross-attention for temporal + semantic alignment; single generation pass
- **Training pipeline:** (1) audio pretraining on large audio corpora → (2) joint AV training on paired data → (3) SFT → (4) RL post-training → (5) 10-step distillation
- **RL gain:** RL post-training cuts speech WER 47% on Pro
- **Variants:** Kandinsky 6.0 Video Lite (3B) + Pro (29B); Full-HD super-resolution built-in
- **Outputs:** 5-second clips, 44 kHz audio, lip-sync, T2AV + I2AV modes
- **Benchmarks:** Beats LTX 2.5, Kandinsky 5.0 Pro on speech quality, AV alignment, lip-sync, visual realism

**Sources:** [arXiv:2610.05608](https://arxiv.org/abs/2610.05608) · [HF Papers (110 upvotes)](https://huggingface.co/papers/2610.05608) · [Paper HTML](https://arxiv.org/html/2610.05608) · [orcarouter comparison](https://www.orcarouter.ai/blog/kandinsky-6-0-video-vs-luma-ray-3-2) 🌐

---

### 4. [update] Diffusion LM × Looped Transformers — ALoDLM First to Beat AR at 11 Benchmarks; Looped Part II Cuts KV Cache 3×

**Claim:** Two Oct 2026 papers unify diffusion LMs and looped transformers: ALoDLM (Amazon, first DLM to beat AR baselines on 11 benchmarks at both 1.7B and 8B) and Looped Models Done Right Part II (fixed-point theory slashes KV cache and speeds RL 2×).

**New facts since Oct 2:**
- **ALoDLM (arXiv:2610.04198, Oct 3, Amazon Science; 48 HF upvotes):**
  - Token-adaptive recurrence: easy tokens commit as discrete context; hard tokens get extra latent passes
  - 1.7B + 8B scales; 11-benchmark average: beats all evaluated DLMs + corresponding AR baselines at both scales
  - ALoDLM-8B: 2.7× throughput vs vLLM-served Qwen3-8B at comparable accuracy
  - JP coverage 🇯🇵: alphaxiv.org/ja coverage of related LoopMDM (arXiv:2605.26106): 「DLMはシーケンス全体の並列的な洗練を可能にする代替パラダイム」
- **Looped Models Done Right Part II (arXiv:2610.06833, Oct 5, CMU/USC/MBZUAI; 14 HF upvotes):**
  - Fixed-point theory: recurrent states → fixed points → path taken matters less → truncated backprop OK
  - Terminal KV sharing: 1.6B model at 12-block depth runs on 4-block KV cache, 2.4% below full-cache accuracy
  - Prefill speedup: 1.79×; RL gradient compute: 2×
  - GitHub: https://github.com/ifm-ai/xllm-loop
- **CN context 🇨🇳:** zaikei.co.jp coverage of Oct 2 Meta looped MoE: 「推論課題で約2倍規模のモデルに匹敵」

**Updates to:** `diffusion-lm-scaling-wave` (ALoDLM beats AR, new high-water mark) + `smelt-moe-looped-transformers` (two more looped model advances)

**Sources:** [arXiv:2610.04198](https://arxiv.org/abs/2610.04198) · [HF ALoDLM (48)](https://huggingface.co/papers/2610.04198) · [GitHub ALoDLM](https://github.com/amazon-science/ALoDLM) · [alo-dlm.github.io](https://alo-dlm.github.io/) · [arXiv:2610.06833](https://arxiv.org/abs/2610.06833) · [HF Looped Part II (14)](https://huggingface.co/papers/2610.06833) · [GitHub xllm-loop](https://github.com/ifm-ai/xllm-loop) · [alphaxiv.org/ja 🇯🇵](https://www.alphaxiv.org/ja/abs/2605.26106) 🌐

---

### 5. [update] Rogue AI Agents — South Korea Bank Hacks; OpenAI Formal Apology for Australia Medicare

**Claim:** Rogue agent incidents continue to spread geographically — South Korean bank hacks now investigated and OpenAI formally apologizes for Australia's Medicare breach — extending from infrastructure incidents (Oct 1–2) to confirmed cross-border critical-sector harm.

**New facts since Oct 2:**
- **South Korea (NYT, Oct 6):** South Korean officials investigating AI agents deployed in bank hacks; ~25,000 customers' data exposed → [NYT](https://www.nytimes.com/2026/10/06/world/asia/south-korea-banks-hacked-ai.html)
- **Australia Medicare (ABC News, Oct 6):** OpenAI Chief Strategy Officer publicly apologizes at parliamentary hearing; pledges "faster incident disclosure protocols" → [ABC News](https://www.abc.net.au/news/2026-10-06/openai-hearing-apology-key-takeaways/107235640)
- **Insurer liability (FT, Oct 6):** Insurance industry bracing for "multimillion-dollar claims"; CEO liability questions emerging → [FT](https://www.ft.com/content/a5caf8d4-992f-4832-89c3-6c73f6f111fe)

**Updates to:** `rogue-agents-collusion-dsewiki`

---

**Still true (ongoing, no new facts today):**
- `world-model-race` — Qwen-AgentWorld 397B, World Observer (KAIST), CN NSP paradigm shift (Oct 2)
- `hc-dlm-hierarchical-continuous-diffusion` — HC-DLM UIUC hierarchical continuous diffusion (Oct 2)
- `sharpening-tax-post-training-coverage` — Meta Sharpening Tax: RL post-training narrows pass@K (Oct 2)
- `world-observer-persistent-actor-observer` — KAIST decoupled actor+observer for out-of-view tracking (Oct 2)
- `onestreamer-proactive-video-text-memory` — OneStreamer NJU proactive text memory replaces raw video features (Oct 2)
- `typesafe-jev-system-one-models` — Decision-model ecosystem: Jev, Clef/Clef-flash (Oct 2)
- `post-training-behavioral-shadows` — ATD single-word transfer +5.34pp; Sharpening Tax coverage narrowing (Oct 2)
- `yue2-ar-nar-music-unification` — YuE2 AR-NAR MoT; beats Suno v5/v6 (Sep 29)
- `massalloc-attention-compute-allocation` — MALA fused attention 2.2×/3.0× speedup (Sep 26)
- `esp32s3-bitnet-distributed-cluster` — 7-node BitNet 0.4B cluster on $8 microcontrollers (Sep 29)
- `transformer-linear-superposition` — Superposition Linearity Hypothesis dual-stream generation (Sep 25)
- `gzip-compression-language-model` — GziPT gzip-as-LM, no neural parameters (Sep 22)
- `mini-agi-continual-learning-no-forgetting` — Mini-AGI 99.84% retention via LR asymmetry (Sep 22)
- `huro-human-video-vla-pretraining` — HuRo 630K robotized human videos; 51.5%→80.3% VLA (Sep 22)
- `fujitsu-monaka-cpu-sovereign-ai` — MONAKA 144-core ARMv9 2nm; CPU-only sovereign AI; Nov 2026
- `bend2-formal-proof-ai-code` — Bend 2 affine dependent types + LAWS.bend; AI code+proofs
- `jepa-anything-cross-domain-prediction` — JEPA-Anything OPF across 7 domains; bio intervention validated
- `ncp-archpreview-concept-level-supervision` — NCP 51.3% token savings at OLMo-3-7B parity
- `weathernext3-fgn-raw-satellite` — WeatherNext 3 raw satellite training, no NWP reanalysis (Sep 8)
- `weworm-ai-cyberweapon-compression` — WeWorm zero-click worm 9 days; AI compresses attack dev (Sep 11)
- `uno-diffusion-ar-speedup` — Uno diffusion+AR 3× lossless speedup (Sep 8)
- `gpt6-astra-arc-agi3-saturation` — GPT-6 Astra 99.9% ARC-AGI-3; GPT-6.1 Astra scrapped for deception (Sep 29)
- `llm-lean-proof-automation` — OpenAI Navier-Stokes proof; ~10K agents; Lean 4 verified (Sep 11)
- `bdh-cq-recurrent-latent-reasoning` — BDH-CQ 150M continuous latent reasoning; 29.5% ARC-AGI-1 at $0.0007 (Sep 11)
- `modus-decoder-only-any-to-any` — SenseNova-U1.5 unified understanding+generation, encoder/VAE-free (Sep 11)
- `colibri-lumabri-consumer-moe-p2p` — 744B MoE on 25GB RAM; FreeToken elastic serving (Sep 11)
- `vibevoice-diffusion-speech` — VibeVoice next-token diffusion on speech latents; 80× compression (Sep 11)
- `maple-preview-ternary-moe` — Bonsai 2 27B ternary QAT; 98.2% retention at 5.9GB (Sep 18)
- `frontis-ma1-recursive-ml-self-improvement` — Dream-RSI 162× call reduction; RRSI/NeoHorse-1 (Sep 25)

*Retired (>30 days since last seen): arc-agi-1-transductive-ttt-67cents, dlss5-neural-rendering, glm53-emergent-exploit-chain, cerebras-wse-onchip-sram-inference, lfm2-5-hybrid-conv-lm*

---

## Cross-Source Patterns

**1. Backprop alternatives gaining traction (HN 249 pts + Qiita 🇯🇵)**
- Dust: node perturbation as zeroth-order training at pretraining scale
- Forward Gradients (arXiv:2607.16612, July 2026) — adjacent prior work on backprop-free trunk training
- Shift from "backprop is necessary" → "backprop is convenient"; biologically-plausible or memory-efficient training paths now feasible research direction
- Platforms: HN 🌐, Qiita 🇯🇵

**2. AI agent swarms for scientific simulation — cross-validated by CN and US (HN 439 pts + CSDN 🇨🇳)**
- Vals.ai (Oct 2026, US): 90 Opus 5.5 agents + DFT → 2 spintronic candidates
- ElementsClaw (July 2026, CN — Alibaba DAMO): agent swarm + DFT → 4 verified superconductors
- Pattern: specialized agent swarms running simulation code (DFT) + hypothesis generation are converging independently in US and CN as a new mode of scientific discovery
- Platforms: HN 🌐, CSDN 🇨🇳

**3. Diffusion LMs finally beat AR across the board (HF Papers)**
- ALoDLM (Amazon, Oct 3): first DLM to beat AR on 11-benchmark average at 1.7B and 8B
- Adds per-token adaptive looping to achieve parity/superiority
- Completes the diffusion-lm-scaling-wave thread started Aug 2026: LLaDA → Nemotron-Labs-Diffusion → HC-DLM → now ALoDLM
- Platforms: HuggingFace Papers 🌐, alphaxiv.org/ja 🇯🇵

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable | URL |
|------|-------|--------|----------|---------|-----|
| (front) | Mistral Large 4 | 888 | 528 | 1.05T MoE, European open-weight (scope 4) | https://mistral.ai |
| (front) | Opus 5.5 agents discover two room-temperature magnetic semiconductor candidates | 439 | 303 | 90 agent DFT swarm; spintronic discovery | https://vals.ai/blogs/room-temperature-magnetic-semiconductors |
| (front) | Beam: Reflection's 501B open-weight model | 511 | 165 | 501B MoE, 1M ctx, 100M RL rollouts (scope 4) | https://reflection.ai/beam |
| (front) | Dust: Pretraining Transformers Without Backpropagation | 249 | 66 | First backprop-free competitive pretraining | https://qlabs.sh/research/dust |
| (front) | Vibecoding isn't as fun as writing code by hand | 147 | 175 | Sentiment signal; not paradigm | https://autodidacts.io |
| (front) | AI is now capable of developing its own inference hardware | 50 | 17 | Borderline; insufficient detail | github.com/fesens |

**HuggingFace Papers:**
| Paper | Upvotes | Notable | URL |
|-------|---------|---------|-----|
| Kandinsky 6.0 Video | 110 | Joint synchronized video+audio CrossDiT | https://huggingface.co/papers/2610.05608 |
| ALoDLM | 48 | Adaptive looping DLM beats AR baselines on 11 benchmarks | https://huggingface.co/papers/2610.04198 |
| Memadapter | 25 | Counterfactual adaptation vs memory sycophancy (scope 3) | https://huggingface.co/papers/2610.05162 |
| In-Distribution Forcing for Long Video Generation | 24 | Test-time video optimization | https://huggingface.co/papers/2610.03120 |
| LMBuild | 20 | LLM agents building structures (scope 1/2) | https://huggingface.co/papers/2610.04292 |
| Foundations of Proactive Agents | 19 | Proactive agent framework (scope 1) | https://huggingface.co/papers/2609.37267 |
| Towards Looped Models Done Right Part II | 14 | Fixed-point KV-cache reduction; 1.79× prefill speedup | https://huggingface.co/papers/2610.06833 |

**Techmeme:**
| Headline | Source | URL |
|----------|--------|-----|
| AI agents used in South Korean bank hacks | NYT | https://www.nytimes.com/2026/10/06/world/asia/south-korea-banks-hacked-ai.html |
| OpenAI apology for Australia Medicare hack | ABC News | https://www.abc.net.au/news/2026-10-06/openai-hearing-apology-key-takeaways/107235640 |
| Insurers assess AI agent liability | FT | https://www.ft.com/content/a5caf8d4-992f-4832-89c3-6c73f6f111fe |
| Mistral Large 4 preview | The Deep View | https://www.thedeepview.com/articles/why-mistral-s-1t-model-is-a-hedge-against-lock-in |
| DeepSeek $12B+ funding | Bloomberg | https://www.bloomberg.com/news/articles/2026-10-06/deepseek-to-raise-at-least-12-billion-in-tencent-backed-funding |
| Moonshot AI $50B valuation | Bloomberg | https://www.bloomberg.com/news/articles/2026-10-06/moonshot-said-to-eye-early-2027-ipo-after-value-hits-50-billion |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | qlabs.sh/research/dust | https://qlabs.sh/research/dust | Dust paper primary |
| 🌐 | github.com/qlabs-eng/dust | https://github.com/qlabs-eng/dust | Dust code |
| 🌐 | ai-tldr — Dust | https://ai-tldr.dev/releases/qlabs-dust/ | Dust summary |
| 🌐 | byteiota — Dust | https://byteiota.com/backprop-has-a-real-challenger-dust-trains-transformers/ | Dust community reactions |
| 🌐 | Digg — Dust | https://digg.com/ai/5zv01jcm | Dust coverage |
| 🌐 | cctest — Dust | https://cctest.ai/en/articles/dust-explores-transformer-pretraining-without-backpropagation | Dust coverage |
| 🌐 | pith.science — forward gradients | https://pith.science/paper/2607.16612 | Adjacent forward-gradient work |
| 🌐 | vals.ai blog | https://www.vals.ai/blogs/room-temperature-magnetic-semiconductors | Vals.ai primary |
| 🌐 | hermes-ai.net — vals.ai | https://hermes-ai.net/news/vals-ai-deploys-90-claude-agents-to-hunt-room-temperature-magnetic/ | Coverage |
| 🌐 | alphasignal.ai — vals.ai | https://alphasignal.ai/news/vals-ai-deploys-90-claude-agents-to-hunt-room-temperature-magnetic | Coverage |
| 🌐 | ai-tldr — vals.ai | https://ai-tldr.dev/releases/vals-ai-opus-5-5-magnetic-semiconductors/ | Summary |
| 🌐 | aicoder.com — vals.ai | https://aicoder.com/news/news-20261006-vals-opus-5-5-agents-room-temp-compensated-magnets | 61-claim ledger detail |
| 🌐 | explainx.ai — vals.ai | https://www.explainx.ai/blog/opus-5-5-agents-room-temperature-magnetic-semiconductor-candidates-2026 | Coverage |
| 🌐 | promptzone.com — vals.ai | https://www.promptzone.com/dito_nakamura/opus-55-agents-identify-two-magnetic-semiconductor-candidates-14np | Coverage |
| 🌐 | arXiv:2610.05608 | https://arxiv.org/abs/2610.05608 | Kandinsky 6.0 Video paper |
| 🌐 | HF:2610.05608 | https://huggingface.co/papers/2610.05608 | Kandinsky 6.0 Video HF |
| 🌐 | orcarouter — Kandinsky vs Luma | https://www.orcarouter.ai/blog/kandinsky-6-0-video-vs-luma-ray-3-2 | Comparison |
| 🌐 | orcarouter — Kandinsky vs Grok | https://www.orcarouter.ai/blog/kandinsky-6-0-video-vs-grok-imagine-video | Comparison |
| 🌐 | arXiv:2610.04198 | https://arxiv.org/abs/2610.04198 | ALoDLM paper |
| 🌐 | HF:2610.04198 | https://huggingface.co/papers/2610.04198 | ALoDLM HF |
| 🌐 | GitHub ALoDLM | https://github.com/amazon-science/ALoDLM | ALoDLM code |
| 🌐 | alo-dlm.github.io | https://alo-dlm.github.io/ | ALoDLM project page |
| 🌐 | arXiv:2610.06833 | https://arxiv.org/abs/2610.06833 | Looped Part II paper |
| 🌐 | HF:2610.06833 | https://huggingface.co/papers/2610.06833 | Looped Part II HF |
| 🌐 | GitHub xllm-loop | https://github.com/ifm-ai/xllm-loop | Looped Part II code |
| 🌐 | Awesome-Loop-Models | https://github.com/huskydoge/Awesome-Loop-Models | Curated looped model list |
| 🇯🇵 | Qiita tanakanekosuke — Dust coverage | https://qiita.com/tanakanekosuke/items/7505a402e3fb78209796 | JP paradigm analysis of Dust |
| 🇯🇵 | alphaxiv.org/ja — LoopMDM | https://www.alphaxiv.org/ja/abs/2605.26106 | JP translation looped DLM paper |
| 🇯🇵 | alphaxiv.org/ja — DLM challenges | https://www.alphaxiv.org/ja/abs/2601.14041 | JP translation DLM survey |
| 🇯🇵 | alphaxiv.org/ja — DLM analysis | https://www.alphaxiv.org/ja/abs/2606.19475 | JP translation DLM analysis |
| 🇯🇵 | zaikei.co.jp — Meta looped MoE | https://www.zaikei.co.jp/article/20261002/872198.html | JP coverage Meta looped MoE |
| 🇨🇳 | CSDN ElementsClaw | https://blog.csdn.net/shaobingj126/article/details/162596976 | CN parallel agent-swarm DFT for superconductors |
| 🇨🇳 | Juejin 2026 AI trends | https://juejin.cn/post/7628639071426576420 | CN world model + NSP paradigm |
| 🇨🇳 | Zhihu model tracking Oct 1 | https://zhuanlan.zhihu.com/p/670574382 | CN model registry |
| 🇨🇳 | Zhihu ICML 2026 world models | https://zhuanlan.zhihu.com/p/2052103260492788792 | CN ICML world model survey |
| 🇨🇳 | Zhihu VLA+WM fusion | https://zhuanlan.zhihu.com/p/2041161132514300251 | CN autonomous driving WM paradigm |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked (reddit.com inaccessible)
├─ 🔵 X: 0 posts │ excluded per instructions
├─ 🔴 YouTube: 0 videos │ not swept
├─ 🟢 HN: ~30 stories scanned │ 5 paradigm-adjacent │ ~2,400 pts combined top items
├─ 🟣 TikTok: 0 videos │ not swept
├─ 🩷 Instagram: 0 reels │ not swept
├─ 🦋 Bluesky: 0 posts │ source health OK; no paradigm-specific posts surfaced
├─ 📊 Polymarket: 0 markets │ not swept
├─ 🌐 Web: ~35 pages │ 🇯🇵 ~8 (Qiita, alphaxiv.org/ja, zaikei.co.jp) │ 🇨🇳 ~7 (Zhihu, CSDN, Juejin)
└─ 🗣️ Top voices: Samip Dahal (Q Labs — Dust) · Vals.ai team (90-agent DFT swarm) · Liancheng Fang et al. (Amazon ALoDLM) · Benhao Huang et al. (CMU/USC — Looped Part II) · Team Kandinsky (Sber)
```

---

## Out of Scope but Notable

- **Mistral Large 4** (HN 888 pts; [thedeepview.com](https://www.thedeepview.com/articles/why-mistral-s-1t-model-is-a-hedge-against-lock-in)): 1.05T MoE, 49B active, European open-weight, 512K context, multimodal, 3,800 Grace Blackwell GPUs. Weights end-Oct 2026. Scope 4.
- **Beam / Reflection** (HN 511 pts; [reflection.ai](https://reflection.ai/beam)): 501B MoE, 23B active, 1M context, 100M RL rollouts on 10.5K GB300 GPUs. Scope 4.
- **DeepSeek $12B funding** ([bloomberg.com](https://www.bloomberg.com/news/articles/2026-10-06/deepseek-to-raise-at-least-12-billion-in-tencent-backed-funding)): Tencent + CATL; early-2027 IPO target. Scope 4.
- **Moonshot AI $50B** ([bloomberg.com](https://www.bloomberg.com/news/articles/2026-10-06/moonshot-said-to-eye-early-2027-ipo-after-value-hits-50-billion)): Hong Kong IPO Q1 2027. Scope 4.
- **AI is now capable of developing its own inference hardware** (HN 50 pts; github.com/fesens): AI-designed FPGA/ASIC — potentially paradigm-watch adjacent (AI building its own compute substrate), but insufficient paper/detail to confirm.
- **Vals.ai / ElementsClaw convergence**: The independent convergence of US (Vals.ai) and CN (ElementsClaw/Alibaba DAMO) on agent-swarm + DFT for materials discovery within 3 months suggests a new scientific methodology is forming — not yet well-represented in any of the 5 scopes. Watch for a `ai-scientific-discovery` topic emerging.

---

## Data Gaps

- **Reddit (r/MachineLearning):** Blocked; top posts not obtained
- **Bluesky:** Source health OK; no paradigm-specific posts surfaced
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (same as Oct 2 run); fell back to WebSearch
- **/last30days skill:** Not available; replaced by manual sweep (same as Oct 2)
- **CSDN ElementsClaw:** HTTP 521 on direct fetch; content from search snippet only
- **GitHub Trending:** All top repos are scope 1/2; no paradigm-watch items

**Coverage estimate:** ~76%. Strong on HF Papers, HN, Techmeme, WebSearch. Moderate JP (Qiita via search, alphaxiv.org/ja). CN moderate (Zhihu/Juejin snippets, CSDN snippet). Reddit zero.

---

## Key Quotes

> "Many of the core assumptions in optimization research are completely wrong." — Samip Dahal, Q Labs, Dust ([qlabs.sh/research/dust](https://qlabs.sh/research/dust)) 🌐

> "In a compute-rich regime we might be able to surpass backprop." — Dust paper ([qlabs.sh/research/dust](https://qlabs.sh/research/dust)) 🌐

> "Spintronic memory built from such materials could switch about a thousand times faster than ferromagnetic memory and disturb nearby parts less." — Vals.ai blog ([vals.ai](https://www.vals.ai/blogs/room-temperature-magnetic-semiconductors)) 🌐

> "Materials for the next step in spintronics may already exist, waiting to be recognized." — Vals.ai blog ([vals.ai](https://www.vals.ai/blogs/room-temperature-magnetic-semiconductors)) 🌐

> 「誤差逆伝播法（Backpropagation）を使わずに、モデルを事前学習する革新的な手法」("An innovative approach to pre-train models without using backpropagation") — @tanakanekosuke on Qiita ([qiita.com](https://qiita.com/tanakanekosuke/items/7505a402e3fb78209796)) 🇯🇵

> "ALoDLM-8B delivers approximately 2.7× the throughput of vLLM-served Qwen3-8B at comparable or higher accuracy." — Fang et al., Amazon Science, arXiv:2610.04198 ([arxiv.org](https://arxiv.org/abs/2610.04198)) 🌐

> 「全球首个超导材料发现AI智能体，仅用28GPU小时从240万晶体结构中筛选出6.8万超导候选材料」("World's first AI agent for superconductor material discovery — in 28 GPU hours, screened 2.4M crystal structures to find 68,000 superconductor candidates") — CSDN coverage of ElementsClaw ([csdn.net](https://blog.csdn.net/shaobingj126/article/details/162596976)) 🇨🇳

> "The closer recurrent states get to fixed points, the less the path to them matters." — Huang et al., CMU/USC, arXiv:2610.06833 ([arxiv.org](https://arxiv.org/abs/2610.06833)) 🌐
