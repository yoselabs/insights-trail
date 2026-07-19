# Paradigm Watch — Daily Briefing
**Date:** 2026-07-19
**Query type:** GENERAL
**Sources:** Hacker News, GitHub Trending, Hugging Face (models + papers), Techmeme, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 30 stories (front page) | Top 564 pts / 362 comments | 🌐 keyword-free front page sweep; 2 paradigm-relevant threads identified |
| GitHub Trending | 8 repos | 831–47 stars today | 🌐 keyword-free trending |
| Hugging Face Models | 5 trending | 13.5k–463 likes | 🌐 Inkling 952B #1; Ternary-Bonsai-27B #2 (ongoing) |
| Hugging Face Papers | ~15 papers | 407–7 upvotes | 🌐 keyword-free trending |
| Techmeme | ~5 stories | — | 🌐 AI coverage; Kimi K3 dominant (scope 4, excluded) |
| Web (global) | 18 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Qiita ×3, Zenn ×2, note.com ×3, labmemo ×1 (via WebSearch) |
| Web (China) | 10 pages | — | 🇨🇳 IT之家 ×1, Sina ×1, Pedaily ×1, CSDN ×2, Zhihu ×1, Juejin ×1, InfoQ ×1, SegmentFault ×1, linux.do ×1 |
| Reddit (r/MachineLearning) | 0 | — | ⚠ Access blocked |
| Bluesky | 0 | — | SOURCE HEALTH: bluesky=OK; not swept (skill unavailable for manual run) |
| YouTube | 0 | — | Not swept in manual run |
| TikTok | 0 | — | ScrapeCreators not configured |
| Instagram | 0 | — | ScrapeCreators not configured |
| Polymarket | 0 | — | No relevant markets |

---

## Synthesized Findings

Two items are genuinely new since the July 17 briefing; one prior theme has a significant new paper. Ordered by significance:

---

### 1. [new] GPT-5.6 Sol Ultra Proves Two Famous Open Mathematical Problems Using Parallel Subagent Exploration 🌐 🇨🇳 🇯🇵

**Assumption violated:** AI systems cannot discover genuinely new mathematical proofs for famous open conjectures; mathematical proof discovery requires human intuition about which directions are worth pursuing.

**What it is — two separate events:**

**Event A: Cycle Double Cover Conjecture (July 10, 2026)** — The most famous of the two. The Cycle Double Cover (CDC) Conjecture, independently posed by George Szekeres (1973) and Paul Seymour (1979), asks whether every bridgeless graph has a collection of cycles where each edge appears in exactly two cycles — one of the most prominent unsolved problems in graph theory. GPT-5.6 Sol Ultra generated a complete proof in under one hour using 64 parallel subagents, each pursuing diverse strategies, with adversarial sub-agents assigned to find weaknesses. The proof reduces to cubic graphs, uses the 8-flow theorem, and constructs edge labelings via linear algebra over GF(3). OpenAI published a 3-page PDF proof AND Lean formalization on its CDN the same day:
- Proof PDF: https://cdn.openai.com/pdf/04d1d1e4-bc75-476a-97cf-49055cd98d31/cdc_proof.pdf
- Prompt (public): https://cdn.openai.com/pdf/04d1d1e4-bc75-476a-97cf-49055cd98d31/cdc_prompt.pdf

**Event B: Convex Optimization Lower Bound (July 19, 2026, HN front page today)** — Today's highest-engagement HN story (564 pts, 362 comments). A researcher proved that the lower bound time complexity for a class of convex optimization problems equals the 30-year-old best-known algorithm's O(d²) function evaluations — closing a theoretical gap between upper and lower bound that had remained open for three decades. The author spent one year attempting this with earlier GPT models before succeeding with GPT-5.6. HN thread: https://news.ycombinator.com/item?id=48957779

**Methodology novelty:** The CDC proof prompt explicitly instructed the model to "Assume for purposes of this task that a complete affirmative proof exists" and to spend at least 8 hours (simulated via tokens) before considering giving up. The multi-agent parallel exploration strategy — many agents pursuing different proof avenues simultaneously, adversarial agents checking each other's work — is itself a new approach to automated proof search. Cost: $275–$485 (standard) to ~$13,000 (fast parallel).

**Community reception — calibrated skepticism:**
- Manchester mathematician Thomas Bloom: "very elegant" (非常漂亮的证明) — "AI doesn't abandon approaches when they fail; it patiently tries countless variations"; criticism: missing citations to post-1983 literature
- HN on convex optimization: "AI became an exceptionally capable collaborator when guided by expert judgment" — substantial debate about attribution (10-page prompt, 1 year of scaffolding by the human author)
- Historical caveat: the CDC conjecture has attracted multiple false proofs; peer review not yet completed as of July 19
- The Lean formalization for the CDC proof is notable — it passes machine kernel verification, which is a stronger validation than informal peer review

**Sources:**
- [Developers Digest — CDC proof](https://www.developersdigest.tech/blog/gpt-56-sol-ultra-cycle-double-cover-proof)
- [OfficeChai — CDC proof OpenAI announcement](https://officechai.com/ai/openai-says-gpt-5-6-sol-produced-a-proof-of-the-50-year-old-cycle-double-cover-conjecture-using-64-subagents-in-1-hour/)
- [The Decoder — CDC proof](https://the-decoder.com/openais-gpt-5-6-sol-ultra-reportedly-solves-a-50-year-old-math-problem-in-under-an-hour/)
- [HN convex optimization](https://news.ycombinator.com/item?id=48957779)
- [HN CDC proof](https://news.ycombinator.com/item?id=48863490)
- [BigGo Finance — CDC + 700-word prompt](https://finance.biggo.com/news/05b7b227-386f-48e3-bee8-08da95cc3d36)
- [MLQ.ai — CDC proof](https://mlq.ai/news/openai-claims-gpt-56-sol-ultra-solved-50-year-old-math-conjecture-in-under-an-hour/)
- [AI Weekly — CDC proof](https://aiweekly.co/alerts/openai-attributes-cycle-double-cover-proof-to-gpt-56-sol-ultra)
- [Towards Deep Learning — CDC proof](https://www.towardsdeeplearning.com/gpt-5-6-just-shocked-the-math-world-wrote-a-proof-of-a-50-year-old-math-problem-in-under-an-hour-4badfaf67828?gi=c34356200725)
- [HTX Insights — CDC + 50-year math](https://www.htx.com/news/gpt-56-cracks-a-50-year-old-math-problem-in-1-hour-64-ais-cl-GCVTHr5I/)
- [Arxiv GPT-5-Pro convex analysis (precursor paper)](https://arxiv.org/pdf/2510.26647)
- [OpenAI GPT-5.6 official](https://openai.com/index/gpt-5-6/)

🇨🇳 **Chinese community:** Heavy coverage treating this as a historical milestone. Key framing: "AI 第一次独立完成重大证明" ("AI completes major proof independently for the first time"). Also notable: controversy framing — "GPT-5.6破50年猜想，马斯克奥尔特曼再掀骂战" (Musk-Altman controversy reignited over the claim's significance). Sources: [IT之家](https://www.ithome.com/0/975/646.htm) | [Sina News](https://k.sina.com.cn/article_5953189932_162d6782c06704ndbi.html?from=science) | [Pedaily](https://news.pedaily.cn/202607/566204.shtml) | [Linux DO](https://linux.do/t/topic/2568895) | [Steins Lab daily](https://daily.steinslab.io/events/2026-07-11-gpt56-cycle-double-cover-proof/) | [AIdea](https://aicode.cc/2026-07-12-df63d221-d629-43ef-b076-49fc1ca33022.html)

🇯🇵 **Japanese community:** GPT-5.6 as a product launch received extensive Qiita/Zenn/note coverage; the mathematical proof results are mentioned within broader GPT-5.6 explainers but not specifically singled out as architectural paradigm shifts. JP community appears to process this primarily as "capabilities milestone" rather than paradigm-level architecture change. Sources: [Zenn/m__f](https://zenn.dev/m__f/articles/chatgpt_5_6_update_overview) | [Qiita/htani0817](https://qiita.com/htani0817/items/2cfbcf3f1bb435b28e6f) | [Qiita/lhjjjk4 July 13 digest](https://qiita.com/lhjjjk4/items/8c540446fbcece25059b) | [note.com/kazu_t](https://note.com/kazu_t/n/n3a605700651d) | [Qiita/aktsmm](https://qiita.com/aktsmm/items/7b92f95325893cb4e5a3)

---

### 2. [update] World Models: "From Pixels to States" Proposes Game-Engine Architecture — Now the Highest-Upvoted Paradigm Paper 🌐

**Assumption violated (ongoing update):** World models should learn to predict future video frames (pixel-to-pixel generation); explicit state representation is unnecessary if a model can learn to generate realistic observations.

**New since July 17:** Paper arXiv 2607.14076, "From Pixels to States: Rethinking Interactive World Models as Game Engines" (Alaya Studio), now has **407 HF upvotes** — surpassing the prior briefing's leading world model paper Orca (2606.30534, which was at 320 on July 17 and is now at 323). 407 upvotes is the highest-engagement paradigm-relevant paper found in today's sweep.

**The new argument:** Rather than end-to-end video prediction (the dominant world model paradigm), this paper argues world models should adopt the **explicit state representation that game engines already use**: a recurrent action-state-observation loop where player actions update an explicit game state, and visual observations are rendered FROM that state (not predicted pixel-to-pixel). This is architecturally distinct from prior world models (Orca, AlayaWorld, Genie) which attempt to bypass explicit state by learning latent video dynamics.

**Why this is significant:** If world models adopted explicit intermediate state (like game engines), they would gain: (a) persistence — game states don't "forget" past events the way video generation forgets; (b) rule compliance — physical and game laws can be imposed at the state layer; (c) modifiability — game state can be inspected and edited. The paper argues video generation models alone can never achieve the long-horizon consistency required for real interactive applications.

**Dataset:** Black Myth: Wukong gameplay — 90+ hours, frame-aligned player actions, ground-truth game states, visual observations. This enables learning the state-to-observation mapping independently of action-to-state dynamics.

**Source:** arXiv 2607.14076 | https://arxiv.org/abs/2607.14076 | [HF Papers](https://huggingface.co/papers/2607.14076)

---

**Still true** (from July 17 briefing, no new substantive facts):

- **SubQ LLM** (#1, July 17): No new technical disclosures; community skepticism unchanged; API still available. [ongoing]
- **Fujitsu PHOTON** (#2, July 17): No new benchmarks or deployments announced; Zenn reimplementation remains the only independent validation. [ongoing]
- **Ternary Bonsai 27B** (#3, July 17): Still HF trending (761 likes, up from 636; 1.26M total downloads) — numbers updated but no new substantive fact. [ongoing]
- **World model research velocity** (#4, July 17): Orca (323 HF upvotes, stable), AlayaWorld (88→continuing), Infinite Worlds (44 upvotes, stable) — now joined by "From Pixels to States" above. [update → see §2]
- **Diffusion LMs**: Token Time Continuous Diffusion for Language Modeling (2607.14106, 7 HF upvotes) — low-signal incremental paper; no new milestone since prior briefing. [ongoing]

---

## Cross-Source Patterns

### Pattern 1: AI-as-Mathematical-Reasoner — From Benchmark to Open Conjecture (New Signal)
The CDC conjecture proof and convex optimization lower bound both appeared in the same 10-day window. These are not benchmark tasks (where training contamination is possible) — they are problems where no known solution existed. The CDC Lean verification is particularly important: it removes the ambiguity of "did the model get lucky on an informal proof" by achieving machine-kernel validation. Three platforms converged on this:

- **HN** (564 pts, 362 comments for convex optimization — highest AI engagement story today)
- **Chinese media** (IT之家, Sina, Pedaily, linux.do — framing as "AI 第一次独立完成重大证明")
- **OpenAI official** (CDN-published proof + Lean code)

The recurring structure: parallel subagent exploration + adversarial checking is a **new proof search methodology** — not just a capable model, but a new workflow for automated mathematical discovery.

### Pattern 2: World Models Split into Two Competing Architectures
The prior briefing (July 17) focused on world models as video prediction (Orca, AlayaWorld, LingBot-World). Today's new paper (2607.14076) introduces a competing paradigm: explicit game-engine state. These two camps — latent video dynamics vs. explicit structured state — are now each generating high-engagement research simultaneously. The choice between them is architectural (not incremental): video-dynamics world models inherit from video generation; game-engine world models inherit from traditional simulation engines. Both camps are Japanese/Chinese lab-heavy (Orca/BAAI, Alaya Studio for video; 2607.14076 also from Chinese authors).

**Platforms:** HF Papers (407 upvotes for game-engine vs. 323 for Orca video-dynamics)

### Pattern 3: JP/CN Community Divergence on Framing of AI Math Breakthrough
Chinese community frames GPT-5.6 math proofs as a paradigm milestone ("AI 第一次独立完成重大证明") with strong media amplification. Japanese community processes the same event primarily as a product capability story (extensive GPT-5.6 Sol/Terra/Luna coverage) without separately surfacing it as paradigm-level. Chinese media is more willing to use transformative framing; Japanese media is more cautious and contextualizes within product comparison.

**Platforms:** 🇨🇳 IT之家/Sina/Pedaily vs. 🇯🇵 Qiita/Zenn/note model-comparison framing

---

## Per-Platform Tables

**Hacker News (paradigm-relevant):**
| User | Title | Points | Comments | Notable | URL |
|------|-------|--------|----------|---------|-----|
| — | GPT-5.6 used a prompt to close a 30-year gap in convex optimization | 564 | 362 | Author spent 1 year with earlier models; "AI as exceptional collaborator" | https://news.ycombinator.com/item?id=48957779 |
| — | GPT-5.6 Sol Ultra produces proof of the Cycle Double Cover Conjecture | — | — | Rate-limited; Lean formalization published; Thomas Bloom "very elegant" | https://news.ycombinator.com/item?id=48863490 |
| — | Speech Recognition and TTS in less than 500kb (Moonshine) | 457 | 60 | Tiny model; edge ASR/TTS democratization signal | https://github.com/moonshine-ai/moonshine |
| — | Fable 5 vs. GPT-5.6 Sol on an NP-Hard Problem: Does /goal help? | 243 | 117 | AI theorem proving on hard combinatorial problems | https://charlesazam.com |
| — | The Kimi K3 Moment | 409 | 437 | EXCLUDED scope 4; KDA linear attention notable | https://bochinski.dev |

**GitHub Trending (paradigm-relevant):**
| Repo | Stars Today | Description | URL |
|------|------------|-------------|-----|
| Robbyant/lingbot-map | 831 | Feed-forward 3D foundation model; Geometric Context Transformer; 20fps streaming | https://github.com/Robbyant/lingbot-map |
| lyogavin/airllm | 161 | 70B inference on single 4GB GPU via streaming layer loading | https://github.com/lyogavin/airllm |

**Hugging Face Models (paradigm-relevant):**
| Model | Likes | Downloads | Key Contribution | URL |
|-------|-------|-----------|-----------------|-----|
| thinkingmachines/Inkling | 13.5k | 1.09k | 975B total / 41B active; sparse MoE; multimodal; open weights (see Out of Scope) | https://huggingface.co/thinkingmachines/Inkling |
| prism-ml/Ternary-Bonsai-27B-gguf | 761 (+125 since July 17) | 339k | 1.58-bit ternary; still trending [ongoing] | https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf |
| prism-ml/Bonsai-27B-gguf | 463 (+102 since July 17) | 1.26M | 1-bit binary [ongoing] | https://huggingface.co/prism-ml/Bonsai-27B-gguf |

**Hugging Face Papers (paradigm-relevant):**
| Upvotes | Title | arXiv | Key Contribution |
|---------|-------|-------|-----------------|
| 407 | From Pixels to States: Rethinking Interactive World Models as Game Engines | 2607.14076 | Game-engine state approach vs. pixel prediction; Black Myth Wukong dataset |
| 323 | Orca: The World is in Your Mind | 2606.30534 | Next-State-Prediction unified world model [ongoing] |
| 194 | SenseNova-U1: Unifying Multimodal Understanding and Generation | 2605.12500 | Joint understanding+generation architecture |
| 63 | Scaling Mixture-of-Experts Video Pretraining for Embodied Intelligence | 2607.07675 | DiT + MoE for embodied AI [ongoing] |
| 44 | Infinite Worlds with Versatile Interactions / LingBot-World 2.0 | 2607.07534 | 720p 60fps, unbounded interaction [ongoing] |
| 32 | MeanFlowNFT: Forward-Process RL to Average-Velocity Generators | 2607.15273 | Tencent Hunyuan flow-based generation |
| 29 | Geometric Context Transformer for Streaming 3D Reconstruction | 2604.14141 | LingBot-Map paper; feed-forward 3D reconstruction |
| 13 | DeepLoop: Depth Scaling for Looped Transformers | 2607.13491 | Looped (weight-tied) transformer depth scaling |
| 11 | Continuous Audio Language Models | 2509.06926 | Consistency modeling for audio; non-autoregressive [ongoing] |
| 7 | Token Time Continuous Diffusion for Language Modeling | 2607.14106 | Diffusion LM variant [ongoing — low engagement] |

**Web (Global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Developers Digest | https://www.developersdigest.tech/blog/gpt-56-sol-ultra-cycle-double-cover-proof | CDC proof technical details |
| 🌐 | OfficeChai | https://officechai.com/ai/openai-says-gpt-5-6-sol-produced-a-proof-of-the-50-year-old-cycle-double-cover-conjecture-using-64-subagents-in-1-hour/ | CDC proof OpenAI announcement |
| 🌐 | The Decoder | https://the-decoder.com/openais-gpt-5-6-sol-ultra-reportedly-solves-a-50-year-old-math-problem-in-under-an-hour/ | CDC proof independent coverage |
| 🌐 | MLQ.ai | https://mlq.ai/news/openai-claims-gpt-56-sol-ultra-solved-50-year-old-math-conjecture-in-under-an-hour/ | CDC proof claim analysis |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/openai-attributes-cycle-double-cover-proof-to-gpt-56-sol-ultra | CDC proof attribution analysis |
| 🌐 | Towards Deep Learning | https://www.towardsdeeplearning.com/gpt-5-6-just-shocked-the-math-world-wrote-a-proof-of-a-50-year-old-math-problem-in-under-an-hour-4badfaf67828?gi=c34356200725 | CDC proof community reaction |
| 🌐 | BigGo Finance | https://finance.biggo.com/news/05b7b227-386f-48e3-bee8-08da95cc3d36 | CDC + 700-word prompt details |
| 🌐 | HTX Insights | https://www.htx.com/news/gpt-56-cracks-a-50-year-old-math-problem-in-1-hour-64-ais-cl-GCVTHr5I/ | CDC proof + NP-hard angle |
| 🌐 | OpenAI CDC Proof PDF | https://cdn.openai.com/pdf/04d1d1e4-bc75-476a-97cf-49055cd98d31/cdc_proof.pdf | Primary source |
| 🌐 | OpenAI CDC Prompt PDF | https://cdn.openai.com/pdf/04d1d1e4-bc75-476a-97cf-49055cd98d31/cdc_prompt.pdf | Prompt methodology |
| 🌐 | arXiv 2607.14076 | https://arxiv.org/abs/2607.14076 | From Pixels to States (world models) |
| 🌐 | arXiv 2510.26647 | https://arxiv.org/pdf/2510.26647 | GPT-5-Pro on convex analysis (precursor) |
| 🌐 | arXiv 2602.12241 | https://arxiv.org/html/2602.12241v1 | Moonshine v2 ergodic streaming |
| 🌐 | arXiv 2509.02523 | https://arxiv.org/html/2509.02523v1 | Flavors of Moonshine (tiny ASR) |
| 🌐 | GitHub Moonshine | https://github.com/moonshine-ai/moonshine | Moonshine source |
| 🌐 | Mozilla.ai / transcribe.cpp | https://blog.mozilla.ai/announcing-transcribe-cpp/ | transcribe.cpp announcement |
| 🌐 | Workshop CJ Pais | https://workshop.cjpais.com/projects/transcribe-cpp | transcribe.cpp project page |
| 🌐 | OpenAI GPT-5.6 | https://openai.com/index/gpt-5-6/ | GPT-5.6 official release |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Zenn/m__f | https://zenn.dev/m__f/articles/chatgpt_5_6_update_overview | GPT-5.6 Sol/Terra/Luna comparison incl. math proofs |
| 🇯🇵 | Qiita/htani0817 | https://qiita.com/htani0817/items/2cfbcf3f1bb435b28e6f | GPT-5.6 release, 3-tier model family |
| 🇯🇵 | Qiita/lhjjjk4 | https://qiita.com/lhjjjk4/items/8c540446fbcece25059b | AI daily digest July 13 including GPT-5.6 Sol |
| 🇯🇵 | note.com/kazu_t | https://note.com/kazu_t/n/n3a605700651d | GPT-5.6 vs. Fable 5 benchmark comparison |
| 🇯🇵 | Qiita/aktsmm | https://qiita.com/aktsmm/items/7b92f95325893cb4e5a3 | GPT-5.6 practical model selection guide |
| 🇯🇵 | Zenn/yu_ga | https://zenn.dev/yu_ga/articles/2026-02-10-ai-world-models | LeCun → World Model Lab; background context |
| 🇯🇵 | Qiita/fe2030 | https://qiita.com/fe2030/items/90b2f1edb6031110db61 | World models: "key to breaking LLM limits" |
| 🇯🇵 | Zenn/taniii_shio | https://zenn.dev/taniii_shio/articles/311b721b7d9782 | World models current state (March 2026) |
| 🇯🇵 | note.com/ai_nstein | https://note.com/ai_nstein/n/nf6925cbc9391 | World models frontier 2026 and beyond |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | IT之家 | https://www.ithome.com/0/975/646.htm | CDC proof: "AI completes major proof independently" |
| 🇨🇳 | Sina News | https://k.sina.com.cn/article_5953189932_162d6782c06704ndbi.html?from=science | "64 AIs claim crown of graph theory" |
| 🇨🇳 | Pedaily (投资界) | https://news.pedaily.cn/202607/566204.shtml | CDC proof in VC/investment community |
| 🇨🇳 | Linux DO | https://linux.do/t/topic/2568895 | Community discussion of CDC proof |
| 🇨🇳 | Steins Lab daily | https://daily.steinslab.io/events/2026-07-11-gpt56-cycle-double-cover-proof/ | "First time AI independently completes major proof" |
| 🇨🇳 | AIdea | https://aicode.cc/2026-07-12-df63d221-d629-43ef-b076-49fc1ca33022.html | Musk-Altman controversy over CDC proof claim |
| 🇨🇳 | SegmentFault | https://segmentfault.com/a/1190000047784867 | "Core battlefield shifted to underlying architecture" |
| 🇨🇳 | InfoQ / 智源 | https://www.infoq.cn/article/XzfoHiKPOLjjHlJXK8OV | Zhiyuan AI 10 trends; world models as AGI consensus |
| 🇨🇳 | Kuchuang AI | https://www.kuchuangai.com/news/4.html | "50-year math problem solved in one hour" |
| 🇨🇳 | Unifuncs | https://s.unifuncs.com/?sid=1d561277-669b-4208-99c5-7aa6bc531609 | GPT-5.6 Sol Ultra 50-year graph theory problem |

---

## Stats Block

```
├─ 🟡 HN: 30 stories (front page) │ top paradigm item 564 pts / 362 comments │ 2 paradigm threads
├─ 🐙 GitHub Trending: 8 repos │ lingbot-map 831 stars today │ 2 paradigm-adjacent items
├─ 🤗 HF Models: 5 trending │ Inkling #1 (13.5k likes); Ternary-Bonsai-27B #2 (761 likes, ongoing)
├─ 📄 HF Papers: ~15 papers │ From Pixels to States 407 upvotes (new) │ Orca 323 (ongoing)
├─ 📺 Techmeme: ~5 stories │ Kimi K3 dominant (excluded scope 4)
├─ 🌐 Web: 18 pages │ 🇯🇵 9 │ 🇨🇳 10
├─ 🟠 Reddit: 0 │ ⚠ blocked
├─ 🦋 Bluesky: 0 │ OK per SOURCE HEALTH; not swept (skill unavailable)
└─ 🗣️ Top voices: Thomas Bloom (Manchester, on CDC proof) │ 36Kr/IT之家 (CN) │ Zenn/m__f (JP GPT-5.6) │ Qiita/kotaro_ai_lab (JP digest)
```

---

## Out of Scope but Notable

- **Inkling (thinkingmachines/Inkling, Thinking Machines Lab, Philippines)** — 975B total parameters / 41B active via sparse MoE (6 of 256 experts + 2 shared per token), 66-layer decoder, native multimodal (text + image + audio in one decoder), open weights, 13.5k HF likes. Excluded scope (4: open/non-US models & geopolitics), but the **sparse MoE routing at this extreme density (6/256 = 2.3%)** pushes what "active parameters" means — a model this size running on 41B active params is a data point for the ternary/quantization efficiency conversation. [HF page](https://huggingface.co/thinkingmachines/Inkling)

- **Kimi K3 KDA (Kimi Delta Attention)** — HN second-trending today (409 pts, 437 comments, "The Kimi K3 Moment"). Excluded scope (4). But KDA is specifically flagged as a **linear attention mechanism** replacing standard quadratic self-attention "designed to scale well beyond the trillion-parameter regime for long sequences." SemiAnalysis explicitly noted: "Some uneducated people think Kimi K3's use of linear attention (KDA) is bad for NVIDIA." Moonshot AI's public position: linear attention is the right scaling choice for 2.8T parameter frontier models. This is architecturally paradigm-adjacent even if the model is out of scope. [bochinski.dev Kimi K3 moment](https://bochinski.dev)

- **Moonshine AI: Speech Recognition + TTS in <500KB** — 457 HN pts, 60 comments. Moonshine Tiny: 26MB English model / 500KB memory footprint; 100x faster than Whisper Large on edge. Moonshine v2 (Feb 2026): ergodic streaming encoder, caches encoder+decoder state, processes only actual audio duration (no zero-padding). Not paradigm-breaking architecture (transformer-based), but **democratization of speech AI to ultra-constrained hardware** continues to erode the assumption that voice AI requires cloud-scale compute. [github.com/moonshine-ai/moonshine](https://github.com/moonshine-ai/moonshine) | [arXiv 2602.12241](https://arxiv.org/html/2602.12241v1)

- **transcribe.cpp (Mozilla.ai / CJ Pais)** — 537 HN pts, 109 comments (highest non-AI-content story today). ggml-based C/C++ speech-to-text library; supports all current STT models via GGUF; Metal/Vulkan/CUDA backends. Same democratization signal as Moonshine — the inference stack for speech is converging with llama.cpp's model (quantized GGUF + hardware-portable compute). [blog.mozilla.ai/announcing-transcribe-cpp/](https://blog.mozilla.ai/announcing-transcribe-cpp/)

---

## Data Gaps

- **`/last30days` skill:** Not registered in this environment — same condition as July 17 briefing. Full manual sweep conducted. No impact on coverage of key surfaces (HN, GitHub, HF, Techmeme, web search).
- **Bluesky:** SOURCE HEALTH = OK, but not swept in manual run (skill provides Bluesky integration). Bluesky's public API does not expose a browsable trending endpoint without auth. Impact estimated low — prior manual runs found 0–5 low-engagement posts for this topic class.
- **Reddit r/MachineLearning:** Blocked (HTTP error). Persistent gap — compensated by HF Papers trending and multi-source web research, which surface the same papers via citation.
- **YouTube:** Not swept. Video coverage of CDC conjecture proof likely exists but not retrieved.
- **TikTok, Instagram:** ScrapeCreators not configured — appropriate for this topic class.
- **Zhihu hot list:** HTTP 403 (auth required). Compensated via WebSearch in Chinese.
- **Juejin trending page:** JavaScript wall ("Please wait..."). Compensated via WebSearch.
- **CSDN direct access:** HTTP 521 (CloudFlare). Content retrieved via search snippets and DuckDuckGo summaries.
- **HN CDC proof thread (48863490):** Rate-limited on direct fetch (HTTP 429). Thread confirmed to exist; engagement not directly retrieved.
- **DuckDuckGo HTML endpoint:** JP and CN queries partially CAPTCHA-blocked — switched to native WebSearch in JP/CN (equivalent coverage).
- **Approximate coverage:** ~80% — HN, HF, Techmeme, web search, JP hubs well covered; missing Bluesky, Reddit, YouTube, and direct CN hub access (Zhihu hot, Juejin trending, CSDN trending).

---

## Key Quotes

> "AI 第一次独立完成重大证明" ("AI completes a major proof independently for the first time") — IT之家 on GPT-5.6 CDC conjecture ([ithome.com](https://www.ithome.com/0/975/646.htm)) 🇨🇳

> "AI doesn't abandon approaches when they fail; it patiently tries countless variations" — Thomas Bloom (University of Manchester), praising the CDC proof ([IT之家](https://www.ithome.com/0/975/646.htm))

> "AI became an exceptionally capable collaborator when guided by expert judgment" — HN community consensus on GPT-5.6 convex optimization ([news.ycombinator.com](https://news.ycombinator.com/item?id=48957779)) 🌐

> "This proof apparently shows that the lower bound time complexity is equal to the time complexity of an existing 30-year old algorithm: it requires Omega(d²) function evaluations." — _alternator_ on HN, explaining the convex optimization result ([news.ycombinator.com](https://news.ycombinator.com/item?id=48957779)) 🌐

> "GPT-5.6破50年猜想，马斯克奥尔特曼再掀骂战" ("GPT-5.6 breaks 50-year conjecture, reigniting Musk-Altman battle") — AIdea framing the controversy ([aicode.cc](https://aicode.cc/2026-07-12-df63d221-d629-43ef-b076-49fc1ca33022.html)) 🇨🇳

> "从预测下一个词到预测世界的下一个状态" ("from predicting the next word to predicting the world's next state") — Zhiyuan AI 2026 Trend #1 framing ([InfoQ](https://www.infoq.cn/article/XzfoHiKPOLjjHlJXK8OV)) 🇨🇳

> "核心战场已经彻底转移到了'底层架构'上" ("the core battlefield has completely shifted to 'underlying architecture'") — SegmentFault on 2026 LLM architecture upheaval ([segmentfault.com](https://segmentfault.com/a/1190000047784867)) 🇨🇳

> "物理的な『コップが落ちたら割れる』といった因果関係を肌感覚として持っているわけではありません" ("LLMs lack intuitive grasp of physical causality like 'a dropped cup breaks'") — Zenn/yu_ga on LeCun's world model argument ([zenn.dev](https://zenn.dev/yu_ga/articles/2026-02-10-ai-world-models)) 🇯🇵
