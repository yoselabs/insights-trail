# Paradigm Watch — Daily Briefing
**Date:** 2026-07-14
**Query type:** GENERAL
**Sources:** Hacker News, Reddit (partial), X/Twitter, GitHub, Web (global), Web (Japan), Web (China), Hugging Face Papers, Papers With Code (via HF redirect), Techmeme, Digg

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 13 stories | 394 points, 220 comments | 🌐 keyword-free top sweep |
| Reddit | 5 threads | 1,074 upvotes, 344 comments | 🌐 partial (HTTP 403 after 5 items) |
| X/Twitter | 13 posts | 236 likes, 34 reposts | 🌐 |
| GitHub | 13 items | 1 reaction, 5 comments | 🌐 daily-arxiv trackers, embodied AI repos |
| Web (global) | 16 pages | — | 🌐 WebSearch + Digg + alphaXiv + IBM Research |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita, Zenn, note, QA AI, AI Negi Lab |
| Web (China) | 9 pages | — | 🇨🇳 Zhihu, CSDN, 36Kr, suanli.cn, Tencent Cloud |
| Hugging Face Papers | 17 papers | ~500 upvotes combined | 🌐 daily + trending sweeps |
| TikTok | 0 | — | ScrapeCreators 402 (billing DOWN) |
| Instagram | 0 | — | ScrapeCreators 402 (billing DOWN) |
| YouTube | 0 | — | ScrapeCreators 402 (billing DOWN) |
| LinkedIn | 0 | — | ScrapeCreators 402 (billing DOWN) |
| Bluesky | 0 | — | OK but 0 paradigm results |
| Techmeme | 0 relevant | — | 🌐 all items fit excluded scopes |

---

## Synthesized Findings

Three genuinely novel signals emerged from the keyword-free trending sweep. Each violates a load-bearing assumption of the current AI paradigm. Ordered by breadth and volume of engagement:

### 1. World Models: The Post-LLM Bet Is Now Institutionalized 🌐 🇯🇵 🇨🇳

**Assumption violated:** Intelligence emerges from predicting text tokens; physically grounded world simulation is unnecessary for frontier AI.

This is the highest-engagement paradigm-shift signal of the current window, with coordinated billion-dollar bets, multiple major lab launches, media recognition, and active research output all converging simultaneously.

The structural shift: [Yann LeCun's AMI Labs](https://techcrunch.com/2026/03/09/yann-lecuns-ami-labs-raises-1-03-billion-to-build-world-models/) closed a $1.03B seed round in March 2026 - Europe's largest ever seed - to build JEPA-based world models. JEPA (Joint Embedding Predictive Architecture) learns abstract representations of physical reality in latent space rather than predicting next text tokens, an architectural bet directly opposed to the LLM paradigm. In parallel, [Google DeepMind launched Genie 3](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/) on January 29, 2026 - real-time interactive 3D world generation at 24fps/720p from text prompts - and [NVIDIA launched Cosmos 3](https://nvidianews.nvidia.com/news/nvidia-launches-cosmos-3-the-open-frontier-foundation-model-for-physical-ai) in June 2026, an open frontier foundation model for physical AI using a "mixture-of-transformers" architecture trained on 20 trillion tokens including nearly a billion images and 400 million videos. [World Labs](https://fortune.com/2026/05/20/physical-ai-world-models-research-nvidia-google-fei-fei-li-yann-lecun/) (Fei-Fei Li) holds a $5B valuation and $1B funding.

[MIT Technology Review](https://www.technologyreview.com/2026/04/21/1135650/world-models-ai-artificial-intelligence/) named world models one of its 10 most important AI technologies of 2026 in April, and [Fortune](https://fortune.com/2026/05/20/physical-ai-world-models-research-nvidia-google-fei-fei-li-yann-lecun/) dedicated a feature to why "the AI field's biggest names are betting billions" on this direction. [NextBigFuture](https://www.nextbigfuture.com/2026/04/2026-is-breakthrough-year-for-reliable-ai-world-models-and-continual-learning-prototypes.html) called 2026 the breakthrough year for reliable world models.

On the research side, Hugging Face trending papers (past week) show concentrated world model activity: [AlayaWorld: Long-Horizon Playable Video World Generation](https://arxiv.org/abs/2607.06291) leads with 86 upvotes, [Scaling Mixture-of-Experts Video Pretraining for Embodied Intelligence](https://arxiv.org/abs/2607.07675) at 62 upvotes, [Infinite Worlds with Versatile Interactions](https://arxiv.org/abs/2607.07534) at 38 upvotes, and [Multiplayer Interactive World Models with Representation Autoencoders](https://arxiv.org/abs/2607.05352) at 24 upvotes. [Xiaomi-Robotics-U0](https://arxiv.org/abs/2607.11643) is framed explicitly as "Unified Embodied Synthesis with World Foundation Model."

🇨🇳 Chinese coverage is extensive and notably framing-forward. [suanli.cn](https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/) articulates the paradigm shift cleanly: "LLMs answer 'what is the world like' - observers reporting language patterns. World models answer 'if I do this, how will the world change' - participants predicting consequences." ("大语言模型回答'世界是什么样的'，而世界模型回答'如果我这样做，世界会怎么变化'") [36Kr](https://www.36kr.com/p/3868221222851589) documents the Chinese competitive landscape under the headline "没有统一名字的战争" ("The war without a unified name"): Alibaba's Qwen-AgentWorld (native language world model, 35B and 397B MoE variants), Daoxiao Robot's Kairos World Model 3.0 leading embodied video generation benchmarks. The [Chinese Academy of Sciences 2026 world model survey](https://zhuanlan.zhihu.com/p/1997422676625600733) treats balancing "expert precision and generalist generalization" as the central unsolved research question. [Zhihu](https://zhuanlan.zhihu.com/p/2036554354874962873) has a comprehensive "浅调研" (shallow survey) from May 2026 that synthesizes the global landscape for a Chinese technical audience.

🇯🇵 Japanese coverage confirms the global trend from a research literacy angle, with [QA AI](https://qaai.jp/question_detail/12161) noting OECD.AI 2026 energy scoring now evaluates environmental impact alongside accuracy - giving SSMs and alternative architectures a structural scoring advantage.

---

### 2. Diffusion Language Models: ICLR 2026 Marks the Field's Arrival 🌐 🇨🇳

**Assumption violated:** Text generation must be autoregressive (sequential left-to-right next-token prediction); parallel denoising cannot match this quality at scale.

Discrete diffusion language models (dLLMs) have moved from "interesting alternative" to "ICLR-published science" in the last 30 days. The conference materialized what had been theoretical: ICLR 2026 published ["Scaling Behavior of Discrete Diffusion Language Models"](https://openreview.net/pdf?id=GDYaNzxt9T) as a conference paper, presented ["Diffusion LLMs Can Do Faster-Than-AR Inference via Discrete Diffusion Forcing"](https://openreview.net/forum?id=t5uLZSRjhF), and featured the blog-track poster ["dLLM - Rethinking Generation Beyond Autoregressive Models"](https://iclr.cc/virtual/2026/poster/10012127). A dedicated [ICLR 2026 workshop](https://iclr.cc/virtual/2026/10021653) on Discrete Diffusion Language Models featured Volodymyr Kuleshov on mechanisms that are "not constrained to generate data sequentially."

The key findings: FS-DFM achieves perplexity parity with a 1,024-step baseline in just 8 sampling steps (128x faster). [ELF: Embedded Language Flows](https://www.alphaxiv.org/abs/2605.10938) (arXiv:2605.10938, 369 interactions on alphaXiv) demonstrates that continuous DLMs - operating on vector embeddings rather than discrete tokens - scale competitively with discrete diffusion for language, challenging the assumption that text generation requires token-level discretization. ["Continuous Diffusion Scales Competitively with Discrete Diffusion for Language"](https://arxiv.org/pdf/2605.18530) (arXiv:2605.18530) extends this result.

On Hacker News, ["The Geometry of Noise: Why Diffusion Models Don't Need Noise Conditioning"](https://intuitivepapers.ai/geometry-of-noise/) (6pts, 2026-06-23) and ["InfiniteDiffusion: A new approach to infinite generation with diffusion models"](https://twitter.com/xandurglar/status/2070179038417821777) (3pts, 2026-06-25) show the practitioner community actively tracking this space, even if engagement is modest at this stage.

The broader argument is architectural: dLLMs enable "flexible infilling" and "long-term planning" that strict left-to-right decoding cannot, because the model can attend bidirectionally during generation. Current limitation acknowledged: dLLM inference remains slower than AR for most settings due to bidirectional attention cost - but the Faster-Than-AR paper directly addresses this.

🇨🇳 [鲸林向海](https://www.itsolotime.com/archives/20771) ("扩散语言模型：从架构挑战到推理优化的深度探索") tracks this as a serious paradigm challenge, noting that the performance gap with autoregressive models - long cited as fatal to dLLMs - is narrowing rapidly. [Zhihu/Raschka 2026 predictions](https://zhuanlan.zhihu.com/p/1994793614048507255) frame it as "Transformer dominance continues, but diffusion models quietly rise" - the "quietly" being the tell of an underestimated transition.

---

### 3. Post-Transformer Architecture Shift Gets Institutional Signal 🌐 🇯🇵

**Assumption violated:** The multi-head attention mechanism paired with feed-forward networks is the irreplaceable computational substrate for frontier AI; no alternative can match it at scale.

Two institutional signals in the past two weeks make this more than a research curiosity:

[IBM Research](https://research.ibm.com/blog/cofrgenets-replace-the-bones-of-transformer-based-models) published "CoFrGeNets replace the 'bones' of transformer-based models" on July 9, 2026. CoFrGeNets (Continuous Frame Geometry Networks) use differential geometry to replace multi-head attention and feed-forward networks - the core computational "bones" - with operations that are structurally motivated rather than empirically assembled. IBM framing it as replacing "bones" (not "improving performance") signals architectural conviction, not incremental optimization.

[Digg](https://digg.com/tech/5aea7u04) ran "AI Labs Shift Focus From Model Size To Post-Transformer Architectures" on July 2 (6,700 interactions), Rohan Paul's aggregation confirming multiple labs moving research investment away from scale-via-transformers and toward architectural diversity. [arXiv:2506.01963](https://arxiv.org/html/2506.01963v1) ("Breaking Quadratic Barriers: A Non-Attention LLM for Ultra-Long Context Horizons") addresses the fundamental quadratic cost of attention via state space kernels, hierarchical convolutions, and retrieval-based memory.

NVIDIA's Cosmos 3 is itself a post-pure-transformer design: its "mixture-of-transformers" architecture pairs a reasoning transformer with an expert generation transformer, suggesting even the labs most invested in transformers are hybridizing away from the uniform architecture.

🇯🇵 The Zenn book ["Beyond Transformers - The Rise of Next-Generation Architectures"](https://zenn.dev/sue738/books/llm-research-2025/viewer/chapter04) (chapter 4 of a dedicated ML research book) shows Japanese ML community engaged enough to produce structured book-length treatment of SSMs, Mamba, MoE, and Ring Attention as serious alternatives. [AI Negi Lab](https://ai.negi-lab.com/posts/2026-02-17-289cffdd/) notes architectures "prioritizing biological efficiency" as the competing direction, echoing the energy-efficiency framing prominent in OECD.AI 2026 scoring.

---

### 4. SteerAF: Inference-Time Steering as an Alternative to Retraining 🌐

**Assumption violated:** To change what a trained model produces (e.g., to explore alternative protein conformations), you must retrain or fine-tune; inference-time optimization is insufficient.

With 57 likes from [@BiologyAIDaily](https://x.com/BiologyAIDaily/status/2068350722161479861) (2026-06-20), [SteerAF](https://x.com/BiologyAIDaily/status/2068350722161479861) introduces inference-time optimization that steers AlphaFold2 away from training-biased default conformations by optimizing the input MSA (multiple sequence alignment) features - not the network weights. The distogram cross-entropy loss guides the MSA toward states the model can already predict but doesn't default to. This is a narrow but conceptually important finding: the model already "knows" alternative conformations implicitly; the training distribution biases suppress them. Inference-time steering recovers them without any weight update.

The generalization: if training-biased distributions systematically suppress valid outputs, inference-time input optimization may be broadly applicable beyond protein structure - a tool that separates "what the model has capacity to produce" from "what training makes it likely to produce."

This item has lower engagement than the top three and is domain-specific (computational biology), but the architectural concept - steering via input rather than weights - is paradigm-adjacent for the broader "inference-time compute" conversation.

---

## Cross-Source Patterns

### Pattern 1: World Model = LLM alternative, not extension
The clearest cross-source signal is that world models are being positioned as an *architectural successor* to LLMs, not a bolt-on capability. This framing appears consistently across: suanli.cn (observer vs. participant framing), AMI Labs (JEPA vs. next-token prediction), MIT Technology Review (top-10 list), 36Kr (competitive race framing), Fortune (bets "against" LLMs), and the HF paper cluster. The pattern is that organizations are treating this as a zero-sum architectural bet, not a complementary capability - the same framing that attended deep learning vs. SVMs in 2012-2014.

**Platforms:** Web global, Web China, Hugging Face Papers, Fortune, MIT Technology Review

### Pattern 2: Diffusion for text gains credibility precisely as LLM scaling plateaus
The timing of dLLM momentum at ICLR 2026 correlates with the "post-scaling" narrative visible in HN and Techmeme commentary (IBM Q2 miss, Hassabis AI governance framing). When the dominant paradigm shows diminishing returns, alternatives gain serious attention. dLLMs benefit from image diffusion's demonstrated success while attacking the specific weaknesses of AR - sequential generation, no long-range planning, inability to fill from both ends.

**Platforms:** ICLR 2026 (OpenReview), alphaXiv, HN, Zhihu/CN blogs

### Pattern 3: Post-transformer is a label, not yet a unified alternative
IBM, Digg/Rohan Paul, and the Zenn chapter all use "post-transformer" as a category, but the actual candidates diverge: SSMs (Mamba), differential geometry networks (CoFrGeNets), non-attention state-space hybrids, and ring attention are very different approaches. This is the "pre-paradigm" phase where many candidates compete without a clear leader - analogous to pre-2017 deep learning architecture diversity before transformers unified the field.

**Platforms:** Web global (IBM, Digg), Web Japan (Zenn), arXiv

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable | URL |
|------|-------|--------|----------|---------|-----|
| LorenDB | InfiniteDiffusion: A new approach to infinite generation with diffusion models | 3 | 1 | Diffusion paradigm signal | https://twitter.com/xandurglar/status/2070179038417821777 |
| skzv | The Geometry of Noise: Why Diffusion Models Don't Need Noise Conditioning | 6 | 0 | Diffusion theory | https://intuitivepapers.ai/geometry-of-noise/ |
| botfriendsarent | We need tech news sources which exclude AI | 141 | 81 | Social signal (excluded scope) | https://news.ycombinator.com/item?id=48713041 |
| sollawen | AI coding is a nightmare | 64 | 53 | SDLC (excluded scope) | https://news.ycombinator.com/item?id=48770319 |
| NotASithLord | Show HN: peerd – AI agent harness in browser | 75 | 23 | Agent (excluded scope) | https://github.com/NotASithLord/peerd |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @BiologyAIDaily | SteerAF: Distogram-based Steering of AlphaFold2 toward Alternative Conformations | 57 | 7 | https://x.com/BiologyAIDaily/status/2068350722161479861 |
| @NuttyCLD | An Investor's Handbook II - AI Power (1) | 69 | 12 | https://x.com/NuttyCLD/status/2074547604340551888 |
| @burny_tech | Current state and future of "recursive AI self-improvement" research | 12 | 3 | https://x.com/burny_tech/status/2073013937235243192 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | IBM Research | https://research.ibm.com/blog/cofrgenets-replace-the-bones-of-transformer-based-models | CoFrGeNets as geometric replacement for transformer attention+FFN |
| 🌐 | Digg (Rohan Paul) | https://digg.com/tech/5aea7u04 | "AI Labs Shift Focus From Model Size To Post-Transformer Architectures" (6.7K interactions) |
| 🌐 | alphaXiv | https://www.alphaxiv.org/abs/2605.10938 | ELF: Embedded Language Flows — continuous DLMs competitive with discrete |
| 🌐 | MIT Technology Review | https://www.technologyreview.com/2026/04/21/1135650/world-models-ai-artificial-intelligence/ | World models: 10 Things That Matter in AI Right Now |
| 🌐 | Fortune | https://fortune.com/2026/05/20/physical-ai-world-models-research-nvidia-google-fei-fei-li-yann-lecun/ | Why AI's biggest names are betting billions on world models |
| 🌐 | TechCrunch | https://techcrunch.com/2026/03/09/yann-lecuns-ami-labs-raises-1-03-billion-to-build-world-models/ | AMI Labs $1.03B seed for JEPA world models |
| 🌐 | Google DeepMind | https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/ | Genie 3 — real-time interactive 3D world generation |
| 🌐 | NVIDIA Newsroom | https://nvidianews.nvidia.com/news/nvidia-launches-cosmos-3-the-open-frontier-foundation-model-for-physical-ai | Cosmos 3 open physical AI foundation model |
| 🌐 | NextBigFuture | https://www.nextbigfuture.com/2026/04/2026-is-breakthrough-year-for-reliable-ai-world-models-and-continual-learning-prototypes.html | 2026 as breakthrough year for reliable world models |
| 🌐 | arXiv | https://arxiv.org/html/2506.01963v1 | Breaking Quadratic Barriers: Non-Attention LLM for ultra-long context |
| 🌐 | OpenReview (ICLR) | https://openreview.net/pdf?id=GDYaNzxt9T | Scaling Behavior of Discrete Diffusion LMs (published ICLR 2026) |
| 🌐 | OpenReview (ICLR) | https://openreview.net/forum?id=t5uLZSRjhF | Diffusion LLMs Faster-Than-AR via Discrete Diffusion Forcing |
| 🌐 | ICLR 2026 | https://iclr.cc/virtual/2026/poster/10012127 | dLLM - Rethinking Generation Beyond Autoregressive Models (poster) |
| 🌐 | ICLR 2026 | https://iclr.cc/virtual/2026/10021653 | Discrete Diffusion Language Models workshop |
| 🇯🇵 | Zenn | https://zenn.dev/sue738/books/llm-research-2025/viewer/chapter04 | "Beyond Transformers — Rise of Next-Gen Architectures" book chapter (SSMs, Mamba, Ring Attention) |
| 🇯🇵 | AI Negi Lab | https://ai.negi-lab.com/posts/2026-02-17-289cffdd/ | Non-transformer architectures prioritizing biological efficiency |
| 🇯🇵 | QA AI | https://qaai.jp/question_detail/12161 | OECD.AI 2026 energy scoring giving SSMs structural advantage |
| 🇯🇵 | Qiita | https://qiita.com/teppei_nakano/items/56e335a208edba2ea668 | Omni-modal AI and MoE developments 2026 |
| 🇨🇳 | suanli.cn | https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/ | "LLMs are observers; world models are participants predicting consequences" |
| 🇨🇳 | 36Kr | https://www.36kr.com/p/3868221222851589 | Chinese tech giants' world model landscape (Alibaba, Kairos) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2036554354874962873 | World model 浅调研 (May 2026 survey) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1997422676625600733 | CAS 2026 world model survey |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1994793614048507255 | Raschka 2026: "Transformer dominance continues, but diffusion models quietly rise" |
| 🇨🇳 | CSDN | https://blog.csdn.net/2403_88718395/article/details/157357090 | World models as core connection for AGI path |
| 🇨🇳 | 鲸林向海 | https://www.itsolotime.com/archives/20771 | Diffusion language models: architecture challenges to inference optimization |

**Hugging Face Papers (trending, week of 2026-07-14):**
| Title | Upvotes | ArXiv | Paradigm relevance |
|-------|---------|-------|-------------------|
| AlayaWorld: Long-Horizon Playable Video World Generation | 86 | 2607.06291 | World model architecture for long-horizon interactive generation |
| Scaling MoE Video Pretraining for Embodied Intelligence | 62 | 2607.07675 | DiT + MoE for embodied AI video |
| Infinite Worlds with Versatile Interactions | 38 | 2607.07534 | Causal pretraining for unbounded interaction horizons |
| Multiplayer Interactive World Models (Representation Autoencoders) | 24 | 2607.05352 | Stable long-horizon rollouts in physics-based environments |
| Continuous Audio Language Models (VAE + consistency) | 11 | 2509.06926 | Avoids lossy discrete audio tokenization |
| LATO.2: Factorized 3D Mesh Generation with Vertex and Topology Flow | 2 | 2607.10623 | Flow-based 3D generation |
| Xiaomi-Robotics-U0: Embodied Synthesis with World Foundation Model | 2 | 2607.11643 | Embodied world foundation model |

---

## Stats Block

```
├─ 🟠 Reddit: 5 threads │ 1,074 upvotes │ 344 comments │ ⚠ partial (HTTP 403 after 5)
├─ 🔵 X: 13 posts │ 236 likes │ 34 reposts
├─ 🟡 HN: 13 stories │ 394 points │ 220 comments
├─ 🐙 GitHub: 13 items │ 1 reaction │ 5 comments
├─ 🌐 Web: 16 pages │ 🇯🇵 7 │ 🇨🇳 9
└─ 🗣️ Top voices: @BiologyAIDaily, @NuttyCLD │ r/LocalLLaMA, r/homelab │ Zhihu, 36Kr, MIT Tech Review
```

---

## Out of Scope but Notable

- **GLM-5.2: frontier-level MIT-licensed model wins r/LocalLLaMA** (1,065pts, 284cmt): [Reddit thread](https://www.reddit.com/r/LocalLLaMA/comments/1u8ai2a/glm52_is_a_win_for_local_ai/) — 753B model with distillation potential for 8B/70B. Clearly belongs to open/non-US models topic (#4).

- **Recursive AI self-improvement: "In how strong form is it real?"** [@burny_tech on X](https://x.com/burny_tech/status/2073013937235243192), 12 likes - an underexplored meta-question about AI-building-AI that sits near the paradigm-watch boundary but is too low-engagement to surface as a confirmed item.

- **Neuromorphic computing speculation** ([r/investing](https://www.reddit.com/r/investing/comments/1ulo0yx/intel_ai_neuromorphic_computing_and_you/), 24cmt): Intel neuromorphic computing framed as a 15-20 year play. Signal is too speculative and low-engagement for this briefing.

- **SteerAF inference-time protein steering** ([X/@BiologyAIDaily](https://x.com/BiologyAIDaily/status/2068350722161479861), 57 likes): Covered above as Item 4. Domain-specific but conceptually interesting for inference-time-compute paradigm.

---

## Data Gaps

- **ScrapeCreators=DOWN (402 billing)**: TikTok, Instagram, YouTube, LinkedIn, Threads all returned HTTP 402. This is a known billing issue per SOURCE HEALTH. The paradigm-watch topic is less affected than consumer topics since paradigm-shift research is primarily discussed in text/papers/blogs, not short-form video.
- **Reddit partial**: HTTP 403 blocked after 5 items. r/MachineLearning direct WebFetch also returned 403. This is significant since r/MachineLearning is the primary Reddit community for paradigm-shift discussion. Workaround: used HF Papers trending as a proxy for ML community signal.
- **Techmeme**: All current stories fit excluded scopes (AI governance, business/earnings, product launches). No fundamental research breakthrough on the homepage today.
- **GitHub Trending**: Dominated by agent/assistant repositories today (excluded scopes). No pure architecture research in trending.
- **Bluesky**: Returned 0 results - likely keyword mismatch, not platform absence.
- **Approximate coverage:** ~72% - missing Reddit r/MachineLearning community signal and all short-form video; compensated by HF Papers sweep, multi-source web research, and JP/CN hub coverage.

---

## Key Quotes

> "LLMs answer 'what is the world like' - observers reporting language patterns. World models answer 'if I do this, how will the world change' - participants predicting consequences." — [suanli.cn](https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/) (🇨🇳, Apr 2026)

> "Transformer dominance continues, but diffusion models quietly rise." ("Transformer主导地位持续，但扩散模型悄然崛起") — [Zhihu/Raschka 2026 predictions](https://zhuanlan.zhihu.com/p/1994793614048507255) (🇨🇳)

> "AI Labs Shift Focus From Model Size To Post-Transformer Architectures" — [Digg/Rohan Paul](https://digg.com/tech/5aea7u04) (🌐, 6,700 interactions, Jul 2, 2026)

> "Diffusion large language models offer parallel token generation and flexible infilling instead of strict left-to-right decoding." — [ICLR 2026 dLLM poster abstract](https://iclr.cc/virtual/2026/poster/10012127) (🌐, Suhas Pai & Xiaojun Ren)

> "The algorithms are not constrained to generate data sequentially, offering potential benefits in long-term planning, controllable generation, and sampling speed." — [ICLR 2026 Discrete Diffusion workshop](https://iclr.cc/virtual/2026/10021653) (🌐, Volodymyr Kuleshov)

> "CoFrGeNets replace the 'bones' of transformer-based models." — [IBM Research blog](https://research.ibm.com/blog/cofrgenets-replace-the-bones-of-transformer-based-models) (🌐, Jul 9, 2026)

> "2026年AI圈最被低估的暗流：世界模型，正在悄悄变成主战场" ("2026's most underestimated undercurrent: world models quietly becoming the main battlefield") — [suanli.cn](https://suanli.cn/blog/2026/4/f3ajwt98piw50ekhivhckq86noe/) (🇨🇳)

> "SteerAF steers predictions away from the default (training-biased) conformation toward alternative states by exploiting multi-peak signals already present in AF2 distograms." — [@BiologyAIDaily](https://x.com/BiologyAIDaily/status/2068350722161479861) (🌐, 57 likes)
