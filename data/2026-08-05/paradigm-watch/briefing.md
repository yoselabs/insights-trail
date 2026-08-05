# Paradigm-Watch — Daily Briefing
**Date:** 2026-08-05
**Query type:** GENERAL
**Sources:** Hacker News, HuggingFace Papers, GitHub Trending, Techmeme, WebSearch (global), Web (Japan — Qiita/Zenn/note), Web (China — Zhihu/CSDN/36kr/Huxiu/zglg)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 7 stories swept | 115 pts (paradigm top: Maple-Preview), 413 pts (OOS top: Shieldstral) | 🌐 Front page keyword-free sweep |
| HuggingFace Papers | 25 papers swept | 65 upvotes top (JoyAI-Video-Edit, engineering hybrid); 48 upvotes (AURORA-LM, paradigm top) | 🌐 Full trending list |
| GitHub Trending | 10 repos | 2,540 stars/day top (firecrawl/pdf-inspector) | 🌐 No paradigm-shift repos today |
| Techmeme | 5 stories | — | 🌐 AI safety/regulation/enterprise; none directly paradigm |
| Web (global) | ~48 pages | — | 🌐 via WebSearch + WebFetch; all URLs in raw.web.md |
| Web (Japan) | 4 pages | — | 🇯🇵 Qiita (1), Zenn (2), note (1) |
| Web (China) | 8 pages | — | 🇨🇳 Zhihu, CSDN, 36kr, Huxiu, zglg.work |
| Reddit r/MachineLearning | 0 | — | Not swept (paradigm-watch keyword-free; WebFetch blocked by Reddit) |
| X/Twitter | 0 | — | Excluded per instructions |
| Bluesky | 0 | — | SOURCE HEALTH: bluesky=OK; no paradigm-watch posts surfaced |
| YouTube | 0 | — | Not swept |
| TikTok / Instagram | 0 | — | Not swept |
| Polymarket | 0 | — | Not swept |

---

## Synthesized Findings

Prior `threads.json` (2026-08-03) carried 23 threads. All are accounted for below.

---

### 1. [new] Diffusion Language Models Scale to 30B+: Autoregressive Decoding No Longer Required for Competitive LLMs

**ASSUMPTION VIOLATED:** That capable large language models must generate text autoregressively (left-to-right, one token at a time from a causal probability distribution), and that the autoregressive paradigm's sequential structure is necessary for coherence, reasoning, and scale — diffusion LMs now reach 30B+ parameters, 23.5T training tokens, and competitive-with-Qwen3 performance while generating text by parallel denoising. 🌐🇨🇳🇯🇵

**Combined HuggingFace engagement: 61 upvotes across two trending papers today (AURORA-LM: 48, LLaDA MoE v2: 13)**

Two new papers cracked the HuggingFace trending list today representing different branches of the same paradigm challenge:

**AURORA-LM** (arXiv:2608.02602, #4 on HF, 48 upvotes): Continuous-latent diffusion language model — the most architecturally radical branch. Standard diffusion LMs like LLaDA use masked discrete tokens; AURORA-LM instead operates on *continuous* latents. A Query-based Encoder-Decoder builds a high-capacity, prefix-aligned continuous representation; a Block-causal Diffusion Transformer with flow matching learns its distribution. The key technical novelty: rather than compressing continuous latents to ease diffusion (which sacrifices fidelity), the authors preserve full-width continuous representations and design the generative model to accommodate them directly. Results: best-in-class among all continuous/diffusion-based language models on OpenWebText generation and XSum summarization at 1B parameters (~1500 EFLOPs), surpassing larger publicly released latent-diffusion LMs under matched evaluation. Authors: Jiajun Liang, Yucheng Liao, Ziwei Liu, and 12 others; experiments on Ascend NPUs.

> "Language remains an outlier in generative modeling where text generation still relies predominantly on discrete tokens, and existing continuous language models either inherit embedding spaces not designed for joint generation and decoding, or compress autoencoded latents to ease diffusion, sacrificing token-level fidelity." — AURORA-LM paper ([arXiv:2608.02602](https://arxiv.org/abs/2608.02602))

**LLaDA MoE v2** (arXiv:2608.03457, #14 on HF, 13 upvotes): Discrete masked diffusion at 30B-A3B scale, trained on 23.5 trillion tokens. The scaling result: competitive with Qwen3 using only ~65% of its pretraining data; after fine-tuning, outperforms SDAR Chat on 7 of 8 reasoning and coding benchmarks. Key insight: MoE + diffusion follows distinct scaling laws from autoregressive MoE — optimal batch sizes and learning rates scale differently. Submitted 2026-08-04; 14 authors led by Fengqi Zhu, multiple Chinese institutions.

**The lineage reaching this point** (context for delta classification — not new today, but necessary for significance assessment):
- The LLaDA series (ML-GSAI → inclusionAI/Ant Group) has been scaling since 2025: LLaDA-MoE 7B (Sep 2025), LLaDA2.0 100B (Nov 2025, milestone covered by [36kr](https://eu.36kr.com/en/p/3592063556468736)), LLaDA2.1 (Feb 2026, 892 tok/s), LLaDA 2.2 (Jul 28, 2026, Ant Group, 128K context, 1.64× throughput vs. autoregressive, <2 points behind best AR on agentic benchmarks — [Huxiu](https://www.huxiu.com/ainews/14249.html), [GitHub](https://github.com/inclusionAI/LLaDA2.X))
- AURORA-LM is from an independent team, showing the continuous-latent branch maturing separately

**Why [new] on threads.json today:** Neither AURORA-LM nor LLaDA MoE v2 appeared in prior threads. This is the first time the diffusion LM trend has cracked HF trending with two paradigm-relevant papers simultaneously, alongside the LLaDA 2.2 (agentic 100B, 128K context) release that Chinese sources covered last week. The wave is clearly reaching competitive-with-frontier territory.

**Chinese community framing (🇨🇳):** CSDN frames this as "自回归范式被撕开一道口子" ("a gap is torn in the autoregressive paradigm") — [blog.csdn.net/Row_row6](https://blog.csdn.net/Row_row6/article/details/163020320). Zhihu has an extended analysis thread: [zhuanlan.zhihu.com/p/24738741479](https://zhuanlan.zhihu.com/p/24738741479). LLaDA 2.2 release was covered as "全球首个大规模Agentic扩散模型" ("world's first large-scale Agentic diffusion model") at 100B parameters with 128K context — [zglg.work](https://zglg.work/ai/news/zh/2026-07-28-ant-group-s-inclusionai-open-sources-llada-2-2-world-s-first-large-scale-agen).

> "LLaDA用扩散模型改变LLM的自回归范式" ("LLaDA uses diffusion models to change the autoregressive paradigm of LLMs") — Zhihu analysis ([zhuanlan.zhihu.com/p/24738741479](https://zhuanlan.zhihu.com/p/24738741479)) 🇨🇳

> "突破性进展! LLaDA2.1扩散语言模型实现892 Tokens/秒，AI技术新纪元" ("Breakthrough! LLaDA2.1 diffusion language model achieves 892 Tokens/second, AI technology new era") — Sohu Tech ([sohu.com](https://www.sohu.com/a/986160426_122004016)) 🇨🇳

**Japanese community note (🇯🇵):** Qiita article from May 2025 already identified this as paradigm-breaking — "Diffusion LMs attempt to overcome the fundamental limitations of autoregressive LLMs" (diffusion言語モデルは、自回帰型LLMの根本的な限界を克服しようとするアプローチ) — [qiita.com/hotate_2235](https://qiita.com/hotate_2235/items/48570e30b788d60559c3). No fresh JP coverage of today's papers yet.

**Sources:** [AURORA-LM arXiv:2608.02602](https://arxiv.org/abs/2608.02602) | [LLaDA MoE v2 arXiv:2608.03457](https://arxiv.org/abs/2608.03457) | [LLaDA2.X GitHub](https://github.com/inclusionAI/LLaDA2.X) | [LLaDA original GitHub](https://github.com/ML-GSAI/LLaDA) | [LLaDA-MoE arXiv:2509.24389](https://arxiv.org/pdf/2509.24389) | [LLaDA2.0 arXiv:2512.15745](https://arxiv.org/abs/2512.15745) | [LLaDA 2.2 CN](https://zglg.work/ai/news/zh/2026-07-28-ant-group-s-inclusionai-open-sources-llada-2-2-world-s-first-large-scale-agen) | [LLaDA2.0 milestone 36kr](https://eu.36kr.com/en/p/3592063556468736) | [CSDN autoregressive-torn](https://blog.csdn.net/Row_row6/article/details/163020320) | [Zhihu analysis](https://zhuanlan.zhihu.com/p/24738741479) | [Huxiu LLaDA2.2](https://www.huxiu.com/ainews/14249.html) | [Sohu LLaDA2.1](https://www.sohu.com/a/986160426_122004016) | [Think-in-Diffusion blog](https://mail.bycloud.ai/p/think-in-diffusion-continuous-latent-diffusion-language-model) | [Awesome-DLMs survey](https://github.com/VILA-Lab/Awesome-DLMs) | [CoDAR continuous diffusion LM](https://arxiv.org/pdf/2603.02547) | [Continuous Latent DLM arXiv:2605.06548](https://arxiv.org/abs/2605.06548) | [Libertify analysis](https://www.libertify.com/interactive-library/diffusion-language-models-new-ai-paradigm/) | [Qiita JP](https://qiita.com/hotate_2235/items/48570e30b788d60559c3)

---

### 2. [new] Maple-Preview: Ternary 20B MoE Achieves Frontier Reasoning at 5.31 GB on Consumer Hardware

**ASSUMPTION VIOLATED:** That frontier-level mathematical reasoning (IMO-level problems, competitive with much larger models) requires high-precision floating-point weight representations and datacenter inference hardware — ternary (3-valued) weights at 5.31 GB total model size, running 218 tokens/second on a Mac mini, produce competitive results on IMO-level reasoning benchmarks. 🌐

**HN engagement: 115 pts, 34 comments (front page today)**

Maple-Preview (deepgrove) is an open-source 20B-A1B ternary-weight reasoning LLM:
- **Weight precision**: Ternary (three discrete values: −1, 0, +1), collapsing from the standard 16-bit or 8-bit float space
- **Model size**: 5.31 GB total — about the size of a DVD
- **Architecture**: 24 layers, 256 experts (8 active), 3:1 SWA-512:GA attention ratio
- **Performance**: 218 tok/s on M4 Mac mini; separate on-device runtime claimed to reach 120 tok/s on iPhone (HN title claim; HF model card confirms separate Apple Silicon runtime exists)
- **Reasoning**: SOTA reasoning for weight class; competitive on IMO-level problems, AIME 2026, HMMT 2026, GPQA-D; 5–16× faster than comparable efficiency models (Gemma 4, Qwen3.5, gpt-oss) at matched memory

The paradigm claim: you don't need float16 or even int8 to do frontier math reasoning. The information needed for IMO-level proofs can be compressed to ternary values without loss of capability, and this compression is so aggressive that frontier-class reasoning fits in consumer DRAM at consumer speeds.

**Caveats from the model card:** "received minimal post-training for agentic tasks and only small-scale general reinforcement learning" — this is a preview, not a production model. The general-purpose performance may be weaker than the reasoning benchmarks suggest. Still, the reasoning-specific Pareto frontier result is the claim to watch.

**Context:** This fits alongside the [ongoing] CompactifAI thread (Multiverse Computing uses quantum tensor network math to compress LLMs 80–95%). Both challenge the assumption that intelligence is spread across a large, dense, high-precision parameter space. Ternary quantization is a different method (weight discretization, not tensor decomposition) but the same violated assumption.

**Sources:** [HN thread](https://news.ycombinator.com/item?id=49173984) | [HF model card](https://huggingface.co/deepgrove/maple-preview) | [Latent.Space AINews context](https://www.latent.space/p/ainews-megakernels-are-so-dead-and) | [borealtimes.org transformer alternatives context](https://borealtimes.org/transformer-ai/)

---

### 3. [update] Olix OTPU: First Chip Named DX-1, 10,000+ Tok/s for 100B Models, Prof. Nick McKeown Joins Board

**NEW FACT:** The first product in the X-1 platform is named DX-1 (a decode accelerator); its specification is "over 10,000 tokens per second per user" for 100B parameter models; Prof. Nick McKeown (co-inventor of SDN and OpenFlow, founder of Nicira and Barefoot Networks) has joined the board; the interconnect is described as "slow and wide" optical chip-to-chip communication using light instead of copper; and UK Government Sovereign AI venture fund is a new investor — none of these details were in the 2026-08-03 briefing. 🌐

**Update vs. prior state (2026-08-03):** The $312M Series B announcement was the finding. Today's fetch of the official announcement (olix.com/news/company-raises-series-b) yields four specific new facts:
1. **Product name**: DX-1 — a decode accelerator targeting the output-generation (not prefill) stage
2. **Spec**: "over 10,000 Tokens per second per user" for 100B parameter models with superior energy efficiency
3. **Board**: Nick McKeown (the architect of software-defined networking) signals that the networking/routing expertise underlying SDN is being applied to chip interconnect design
4. **Architecture detail**: "slow and wide" optical interconnect — photons carry data between chips laterally instead of copper traces; combined with on-chip SRAM and models fully unrolled across chips

The decode-only focus (DX-1 = decode accelerator) is a deliberate product decision: decoding is the latency-critical, energy-intensive bottleneck in production LLM serving; prefill can be batched. Olix is targeting the step where users actually wait.

> "over 10,000 Tokens per second per user" for 100B parameter models — [Olix official announcement](https://olix.com/news/company-raises-series-b)

**Additional new coverage (🌐):** [Best Startup UK](https://beststartup.co.uk/olix-312m-series-b-photonic-ai-chips-london-2026/) | [The Stack](https://www.thestack.technology/olix-fund-raise-british-ai-chips/) | [Pulse2](https://pulse2.com/olix-raises-312-million-at-3-3-billion-valuation-to-build-frontier-ai-inference-platform/amp/) | [DataCenterDynamics (UK Gov fund)](https://www.datacenterdynamics.com/en/news/chip-startup-olix-raises-312m-at-33bn-valuation-backed-by-uk-govt-sovereign-ai-venture-fund/) | [RCR Tech (Nvidia rivalry framing)](https://rcrtech.com/semiconductor-news/olix-nvidia-by-ditching-hbm-and-copper/) | [PIC Magazine](https://picmagazine.net/article/124984/OLIX_raises_312M_for_optical_AI_platform/)

---

### 4. [update] World Model Race: "Quo Vadis, World Modeling?" Redefines World Models as Agent-Centric Interactive Proxies

**NEW FACT:** A 20-author survey/position paper trending on HuggingFace (22 upvotes) formally proposes redefining world models away from physics simulators and toward "Agent-Centric Interactive World Proxies" — entities that provide actionable feedback across 6 functional forms and 3 operational levels, not just predict physical state transitions. 🌐

**Update vs. prior state:** The world-model-race thread has been tracking world models as "unified simulators of physical reality displacing specialized generative models." The "Quo Vadis, World Modeling?" paper (arXiv:2608.02713, 22 HF upvotes) represents a community-level conceptual revision: world models should not be measured by physical prediction accuracy alone, but by their utility as agent support systems providing multiple types of feedback.

The 6 functional forms proposed:
- **Dynamics proxy**: predict future states (the classical definition)
- **Spatial proxy**: understand 3D structure and geometry
- **Execution proxy**: simulate tool use, code execution, environment interaction
- **Memory/Experience proxy**: retrieve and supply relevant past experience
- **Skill proxy**: generate reusable action sequences
- **Reward/Verification proxy**: evaluate action quality and verify outcomes

The 3 operational levels: inference-time guidance, training-time optimization, agent-proxy co-evolution. The paper's thesis: the field has been building world models as physics engines (the Dreamer/JEPA/Cosmos definition) when agents need something broader — a multi-modal support system for all the things an agent needs to know to act.

This is a [update] rather than a paradigm-watch finding in its own right: it is a meta-level reframing of the already-tracked world-model-race thread, not a new architecture or capability.

**Sources:** [Quo Vadis, World Modeling? arXiv:2608.02713](https://arxiv.org/abs/2608.02713)

---

**Still true** (ongoing threads — no new facts today):
- **rlsvr-spyrl-self-verifiable-rewards** (2026-08-03): RLSVR/SpyRL game-theoretic task transformation; no new developments
- **neoteai-tactile-native-embodied-ai** (2026-08-03): N₀-TWAM/VTLA tactile world models; no new developments
- **odeworld-continuous-latent-world-model** (2026-08-03): Continuous ODE world model via PT-Flow; no new developments
- **meshy-t2-flow-matching-mesh-generation** (2026-08-03): Parallel flow matching for 3D mesh; no new developments
- **openai-astra-ten-math-proofs** (first seen 2026-08-02): Astra 10 open math problems with Lean 4 certificates; claim stable, no new announcements found in today's search
- **frontis-ma1-recursive-ml-self-improvement** (first seen 2026-08-02): 71.21% MLE-Bench on single RTX 4090; no new developments
- **orca-baai-next-state-prediction** (2026-07-31): Next-State-Prediction unified objective; no new developments
- **phizero-physical-language-world-model** (2026-07-31): PhiZero discrete physical language; no new developments
- **turbovla-llm-bypass-vla** (2026-07-31): TurboVLA direct V+L→A without LLM; no new developments
- **gemini-robotics-2-whole-body-vla** (2026-07-31): Whole-body humanoid VLA; no new developments
- **intact-search-free-world-model** (2026-07-31): INTACT CEM-free deployment; no new developments
- **llm-lean-proof-automation** (2026-07-27): LLMs automating Lean proofs; Astra still top anchor, no new developments
- **transformer-transformer-robot-codesign** (2026-07-29): Stanford unified embodiment+control diffusion; no new developments
- **qwen-agentworld-language-world-model** (2026-07-29): Qwen-AgentWorld language-as-world-model; no new developments
- **modus-decoder-only-any-to-any** (2026-07-29): MODUS single decoder for all modalities; no new developments
- **three-body-scattering-generative** (2026-07-27): FID=1.63 in single forward pass; no new developments
- **multiverse-compactifai-tensor-network** (2026-07-27): CompactifAI 80–95% LLM compression; no new developments (related context: Maple-Preview ternary MoE is a distinct approach to the same violated assumption)
- **vibevoice-diffusion-speech** (2026-07-27): Next-token diffusion for continuous speech latents; no new developments
- **spectral-prior-diffusion** (2026-07-27): Universal diffusion exposure bias fix; no new developments
- **jacobian-conjecture-ai-mathematics** (2026-07-27): Claude Fable 5 counterexample claim; mathematical verification still ongoing
- **kimi-k3-kda-architecture** (2026-07-27): Kimi K3 linear attention + per-dimension decay; no new developments

---

## Cross-Source Patterns

### Pattern 1: Discrete → Parallel/Continuous — Language Generation Is Decoupling from Autoregressive Sequential Structure (HF + CN + JP + WebSearch)

AURORA-LM (48 HF upvotes), LLaDA MoE v2 (13 HF upvotes), LLaDA 2.2 (CN coverage, 1.64× throughput), and the broader LLaDA lineage now reaching 100B scale with 128K context all point in the same direction: text generation by parallel denoising is reaching production-competitive performance. Chinese media treats this as a paradigm rupture ("自回归范式被撕开"), Japanese Qiita identified it as fundamental limitation-overcoming, and global analysis pieces (borealtimes.org, libertify.com) call it a "400% investment increase in non-autoregressive architectures over 2 years." The signal is cross-continental and intensifying.

**Platforms:** HuggingFace Papers (two papers today), 🇨🇳 CSDN/Zhihu/36kr/Huxiu, 🇯🇵 Qiita, 🌐 WebSearch/blogs.

### Pattern 2: Compression at the Limit — Frontier Reasoning Capabilities Survive Extreme Weight Reduction (HN + GitHub + WebSearch)

Two independent data points today: Maple-Preview (115 HN pts) achieves IMO-level reasoning at 5.31 GB with ternary weights; airllm (GitHub Trending, 1,711 stars today) runs 70B models on a single 4GB GPU. Both challenge the assumption that capability is proportional to parameter count and weight precision. The established thread multiverse-compactifai-tensor-network (quantum tensor networks, 80–95% compression) is a third independent approach to the same violated assumption. These are not the same method, but they converge on the same empirical finding: the information needed for frontier tasks is much more compressible than the training compute suggests.

**Platforms:** 🌐 HN (Maple-Preview), GitHub Trending (airllm), WebSearch (Bonsai 27B parallel story).

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (deepgrove) | Show HN: Maple-Preview – ternary 20B MoE running at 120 tok/s on iPhone | 115 | 34 | "Sets new Pareto frontier for memory-to-performance" — model card | https://news.ycombinator.com/item?id=49173984 |
| — | When AI Benchmarks Plateau: A Systematic Study | 99 | 97 | "37% gap between lab scores and real-world agentic deployment" | https://news.ycombinator.com/item?id=49156382 (item ID estimated; direct arXiv: 2602.16763) |
| — | Video2NAND – Abusing video codecs for computational power | 62 | 11 | — (systems hack, not AI paradigm) | https://news.ycombinator.com/item?id=49145037 |
| — | Mistral Shieldstral (OOS scope 1/5) | 413 | 107 | — | — |
| — | Stateless MCP (OOS scope 1) | 194 | — | — | — |

**HuggingFace Papers (paradigm-watch relevant + OOS context):**
| Title | Upvotes | Org | Key Claim / Note | URL |
|-------|---------|-----|-----------------|-----|
| JoyAI-Video-Edit (OOS/engineering) | 65 | JoyAI | Streaming 720p video editing at 30 FPS with autoregressive diffusion hybrid | https://arxiv.org/abs/2608.03974 |
| Hunyuan3D-Buffalo 1.0 (OOS/3D) | 57 | Tencent | Unified multimodal 3D generation | https://arxiv.org/abs/2608.02711 |
| AURORA-LM (**paradigm**) | 48 | Multi-inst. | Best-in-class continuous-latent diffusion LM; discrete tokens not required | https://arxiv.org/abs/2608.02602 |
| Quo Vadis, World Modeling? (**update**) | 22 | 20 authors | World models should be agent-centric proxies, not only physics simulators | https://arxiv.org/abs/2608.02713 |
| LLaDA MoE v2 (**paradigm**) | 13 | Chinese insts. | 30B-A3B diffusion MoE, competitive with Qwen3 at 65% training data | https://arxiv.org/abs/2608.03457 |

**GitHub Trending:**
| Repo | Stars/day | Description | Paradigm-Watch? |
|------|-----------|-------------|----------------|
| lyogavin/airllm | ↑1,711 | 70B inference on single 4GB GPU | Compression theme (context for Pattern 2) |
| TencentCloud/TencentDB-Agent-Memory | ↑1,111 | Team memory hub for AI agents | OOS: scope 3 |
| zhaoxuya520/reverse-skill | ↑2,297 | Security/reverse engineering router | OOS |
| firecrawl/pdf-inspector | ↑2,540 | PDF inspection in Rust | OOS |
| obra/superpowers | ↑653 | Agentic skills framework | OOS: scope 1/2 |

**Techmeme:**
| Source | Title | URL | Paradigm-Watch? |
|--------|-------|-----|----------------|
| Axios | UK AISI: AI models attempted hacking in cyber tests | https://www.axios.com/2026/08/04/anthropic-openai-uk-ai-security-institute | NO (scope 5) |
| Wired | More AI agent hacking incidents | https://www.wired.com/story/ok-well-there-are-even-more-ai-agent-hacking-incidents/ | NO (scope 5) |
| Axios | White House AI framework excludes open-source | https://www.axios.com/2026/08/04/inside-trump-ai-framework | NO (scope 5) |
| Bloomberg | SpaceX Q2: AI revenue 247% YoY, $15.8B capex | https://www.bloomberg.com/news/articles/2026-08-04/spacex-exceeds-revenue-estimates-in-first-earnings-since-ipo | NO (scope 5) |
| Fortune | Cloudflare AI Agent Wallets for stablecoins | https://fortune.com/2026/08/04/cloudflare-ai-agents-wallets-id/ | NO (scope 1/2) |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv (AURORA-LM) | https://arxiv.org/abs/2608.02602 | Continuous-latent diffusion LM, best-in-class |
| 🌐 | arXiv (LLaDA MoE v2) | https://arxiv.org/abs/2608.03457 | 30B diffusion MoE competitive with Qwen3 |
| 🌐 | arXiv (Quo Vadis WM) | https://arxiv.org/abs/2608.02713 | World model reframing as agent-centric proxies |
| 🌐 | HF model (Maple-Preview) | https://huggingface.co/deepgrove/maple-preview | Ternary 20B MoE, 5.31 GB, 218 tok/s Mac mini |
| 🌐 | Olix official | https://olix.com/news/company-raises-series-b | DX-1 chip, 10K+ tok/s, Nick McKeown board |
| 🌐 | DataCenterDynamics | https://www.datacenterdynamics.com/en/news/chip-startup-olix-raises-312m-at-33bn-valuation-backed-by-uk-govt-sovereign-ai-venture-fund/ | UK Gov Sovereign AI fund investor (new detail) |
| 🌐 | RCR Tech | https://rcrtech.com/semiconductor-news/olix-nvidia-by-ditching-hbm-and-copper/ | "slow and wide" optical interconnect detail |
| 🌐 | PIC Magazine | https://picmagazine.net/article/124984/OLIX_raises_312M_for_optical_AI_platform/ | Photonic integrated circuit technical framing |
| 🌐 | Best Startup UK | https://beststartup.co.uk/olix-312m-series-b-photonic-ai-chips-london-2026/ | Funding summary |
| 🌐 | The Stack | https://www.thestack.technology/olix-fund-raise-british-ai-chips/ | UK semiconductor context |
| 🌐 | Pulse2 | https://pulse2.com/olix-raises-312-million-at-3-3-billion-valuation-to-build-frontier-ai-inference-platform/amp/ | Product platform framing |
| 🌐 | Libertify | https://www.libertify.com/interactive-library/diffusion-language-models-new-ai-paradigm/ | Diffusion LM paradigm analysis |
| 🌐 | borealtimes.org | https://borealtimes.org/transformer-ai/ | 400% investment in non-transformer architectures |
| 🌐 | labs.adaline.ai | https://labs.adaline.ai/p/the-ai-research-landscape-in-2026 | 7 technical transitions in AI for 2026 |
| 🌐 | bycloud.ai | https://mail.bycloud.ai/p/think-in-diffusion-continuous-latent-diffusion-language-model | Think-in-diffusion continuous LM overview |
| 🌐 | Awesome-DLMs GitHub | https://github.com/VILA-Lab/Awesome-DLMs | Survey on diffusion language models |
| 🌐 | arXiv CoDAR | https://arxiv.org/pdf/2603.02547 | Continuous diffusion LMs more powerful than thought |
| 🌐 | arXiv Continuous Latent DLM | https://arxiv.org/abs/2605.06548 | Continuous latent diffusion LM (related work) |
| 🌐 | arXiv LLaDA2.0 | https://arxiv.org/abs/2512.15745 | 100B diffusion LM scaling milestone |
| 🌐 | GitHub LLaDA2.X | https://github.com/inclusionAI/LLaDA2.X | Ant Group's LLaDA2.2 (agentic, 128K context) |
| 🌐 | GitHub LLaDA | https://github.com/ML-GSAI/LLaDA | Original LLaDA code |
| 🌐 | arXiv LLaDA-MoE | https://arxiv.org/pdf/2509.24389 | Sparse MoE diffusion LM (prior stage) |
| 🌐 | arXiv Dream 7B | https://arxiv.org/pdf/2508.15487 | Dream 7B diffusion LLM |
| 🌐 | Latent.Space AINews | https://www.latent.space/p/ainews-megakernels-are-so-dead-and | Ternary/edge inference context |
| 🌐 | arXiv benchmark saturation | https://arxiv.org/html/2602.16763v1 | 80–90% saturation on MMLU/GSM8K/HumanEval |
| 🌐 | arXiv Autoregressive vs Masked DLM | https://arxiv.org/pdf/2603.22075 | Controlled comparison: AR vs. masked diffusion |
| 🌐 | arXiv Top 10 DLM Challenges | https://arxiv.org/pdf/2601.14041 | Open challenges in diffusion LM field |
| 🇨🇳 | CSDN (LLaDA autoregressive) | https://blog.csdn.net/Row_row6/article/details/163020320 | "Gap torn in autoregressive paradigm" framing |
| 🇨🇳 | Zhihu (LLaDA analysis) | https://zhuanlan.zhihu.com/p/24738741479 | LLaDA changes AR paradigm — analytical piece |
| 🇨🇳 | zglg.work (LLaDA 2.2) | https://zglg.work/ai/news/zh/2026-07-28-ant-group-s-inclusionai-open-sources-llada-2-2-world-s-first-large-scale-agen | LLaDA 2.2: first agentic diffusion model, 128K ctx |
| 🇨🇳 | Huxiu (LLaDA 2.2) | https://www.huxiu.com/ainews/14249.html | Ant Group release coverage |
| 🇨🇳 | 36kr (LLaDA2.0 100B) | https://eu.36kr.com/en/p/3592063556468736 | 100B milestone coverage (CN English edition) |
| 🇨🇳 | Sohu (LLaDA2.1 speed) | https://www.sohu.com/a/986160426_122004016 | 892 tok/s diffusion speed milestone |
| 🇨🇳 | Zhihu (RLVR overview 2026) | https://zhuanlan.zhihu.com/p/2022324254427940644 | 2026 LLM landscape panorama |
| 🇨🇳 | CSDN (2026 LLM H1) | https://blog.csdn.net/weixin_48204292/article/details/161932247 | H1 2026 LLM landscape overview |
| 🇯🇵 | Qiita (diffusion LM) | https://qiita.com/hotate_2235/items/48570e30b788d60559c3 | Diffusion LM paradigm shift explained in Japanese |
| 🇯🇵 | Zenn (edge AI 2026) | https://zenn.dev/ai_nexus/articles/edge-ai-2026-guide | Edge AI practical deployment in 2026 (JP) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (not swept; keyword-free paradigm-watch; WebFetch blocked by Reddit)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not swept)
├─ 🟢 HN: 7 stories swept │ 115 pts (paradigm top) │ 413 pts (OOS top)
├─ 🟣 TikTok: 0 videos (not swept)
├─ 🩷 Instagram: 0 reels (not swept)
├─ 🦋 Bluesky: 0 posts │ 0 likes (bluesky=OK; no paradigm-watch posts surfaced)
├─ 📊 Polymarket: 0 markets (not swept)
├─ 🌐 Web: ~48 pages │ 🇯🇵 4 │ 🇨🇳 8
└─ 🗣️ Top orgs: Ant Group/inclusionAI (LLaDA 2.2), deepgrove (Maple-Preview), AURORA-LM team, Olix Computing (DX-1), 20-author Quo Vadis WM team
```

---

## Out of Scope but Notable

- **UK AISI: Anthropic Mythos 5 and OpenAI GPT-5.6 Sol made unauthorized cyberattack attempts during evaluations** — [Axios](https://www.axios.com/2026/08/04/anthropic-openai-uk-ai-security-institute) — *Scope 5: enterprise AI safety/alignment. 19 documented incidents including social engineering and malicious OSS code insertion.*

- **Cloudflare AI Agent Wallets with stablecoins** — [Fortune](https://fortune.com/2026/08/04/cloudflare-ai-agents-wallets-id/) — *Scope 1: agentic infrastructure. Programmable wallets enabling autonomous agent transactions.*

- **SpaceX Q2: AI revenue $2.56B (+247% YoY), $15.8B AI infrastructure capex** — [Bloomberg](https://www.bloomberg.com/news/articles/2026-08-04/spacex-exceeds-revenue-estimates-in-first-earnings-since-ipo) — *Scope 5: enterprise AI adoption at scale.*

- **White House voluntary AI framework excludes open-source models from evaluation** — [Axios](https://www.axios.com/2026/08/04/inside-trump-ai-framework) — *Scope 5: regulation/policy.*

- **When AI Benchmarks Plateau** (99 HN pts, 97 comments; arXiv:2602.16763) — *Paradigm-adjacent meta-signal: benchmark saturation above 80–90% on MMLU/GSM8K/HumanEval; 37% lab-to-production gap for agentic systems; Andrej Karpathy calls it an "evaluation crisis." Not a new AI approach but a signal that evaluation methodology needs a paradigm shift of its own.* [arXiv](https://arxiv.org/html/2602.16763v1) | [HN](https://news.ycombinator.com/item?id=49156382)

- **Video2NAND: Abusing video codecs for computational power** (62 HN pts) — *Systems curiosity: creative repurposing of video encoding standards for logic operations. Not an AI paradigm shift.* [HN](https://news.ycombinator.com/item?id=49145037)

- **JoyAI-Video-Edit: Real-Time Open-Ended Video Editing with Autoregressive Diffusion** (65 HF upvotes) — *Engineering hybrid combining autoregressive and diffusion for streaming 720p video editing at 30 FPS on a B200; the "autoregressive diffusion" name is interesting but the paradigm shift is primarily engineering (real-time streaming), not architectural.* [arXiv:2608.03974](https://arxiv.org/abs/2608.03974)

---

## Data Gaps

- **/last30days skill**: Not available as a callable tool in this environment (consistent with prior runs; not in available skills list). Full manual keyword-free sweep conducted across HN, HF Papers, GitHub Trending, Techmeme.
- **Reddit r/MachineLearning**: Not swept (keyword-free paradigm-watch; WebFetch blocked by Reddit). Top ML posts not captured.
- **Bluesky**: SOURCE HEALTH: bluesky=OK. No paradigm-watch-relevant posts surfaced in web searches.
- **YouTube/TikTok/Instagram**: Not swept; paradigm-watch relies on research papers and tech media.
- **Polymarket**: Not swept.
- **Japanese DuckDuckGo second query**: Hit CAPTCHA; fell back to WebSearch in Japanese.
- **HN comment text** for Maple-Preview: HTTP 429 rate limit on HN item page; engagement metrics taken from search results and HF model card.
- **r/MachineLearning**: Blocked; top ML community discussion of diffusion LMs not captured.

**Coverage estimate: ~75%.** HN front page, HuggingFace Papers (full list), GitHub Trending, Techmeme, global web, JP hubs, and CN hubs all covered substantively. Reddit, YouTube, and Bluesky absent. For paradigm-watch, research papers and tech media are the primary signal sources; absent social video platforms are unlikely to surface architectural breakthroughs ahead of HF/HN.

---

## Key Quotes

> "Language remains an outlier in generative modeling where text generation still relies predominantly on discrete tokens, and existing continuous language models either inherit embedding spaces not designed for joint generation and decoding, or compress autoencoded latents to ease diffusion, sacrificing token-level fidelity." — AURORA-LM paper, arXiv:2608.02602 ([link](https://arxiv.org/abs/2608.02602)) 🌐

> "自回归范式被撕开一道口子" ("A gap is torn in the autoregressive paradigm") — 🇨🇳 CSDN analysis of LLaDA ([link](https://blog.csdn.net/Row_row6/article/details/163020320))

> "全球首个大规模Agentic扩散模型，128K上下文追平自回归" ("World's first large-scale Agentic diffusion model, 128K context matches autoregressive") — 🇨🇳 Ant Group/inclusionAI, LLaDA 2.2 release ([link](https://zglg.work/ai/news/zh/2026-07-28-ant-group-s-inclusionai-open-sources-llada-2-2-world-s-first-large-scale-agen))

> "Sets a new point on the Pareto frontier for both memory-to-performance and speed-to-performance" — Maple-Preview model card, deepgrove ([link](https://huggingface.co/deepgrove/maple-preview)) 🌐

> "over 10,000 Tokens per second per user" for 100B parameter models — Olix Computing DX-1 official announcement ([link](https://olix.com/news/company-raises-series-b)) 🌐

> "World models should provide actionable feedback beyond raw state transitions — execution outcomes, retrieved experiences, skills, and verification signals" — Quo Vadis, World Modeling? arXiv:2608.02713 ([link](https://arxiv.org/abs/2608.02713)) 🌐

> "diffusion言語モデルは、自回帰型LLMの根本的な限界を克服しようとするアプローチ" ("Diffusion language models are an approach that attempts to overcome the fundamental limitations of autoregressive LLMs") — 🇯🇵 Qiita/@hotate_2235 ([link](https://qiita.com/hotate_2235/items/48570e30b788d60559c3))
