# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-10-23
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan), Web (China), Hacker News, Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit 🌐 | 0 | — | Not queried |
| X/Twitter 🌐 | 0 | — | Not queried |
| YouTube 🌐 | 0 | — | Not queried |
| Hacker News 🌐 | 2 threads | high | DeepInfer (Oct 20); MiniMax M3.1 Flash weights (Oct 23) |
| Bluesky 🌐 | 0 | — | bsky=OK; no content extracted |
| TikTok 🌐 | 0 | — | Not queried |
| Instagram 🌐 | 0 | — | Not queried |
| Polymarket 🌐 | 1 market | $90,846+ vol | 18-19% Yes; slight uptick from 17% Oct 20 |
| Web (global) 🌐 | 80+ pages | — | via WebSearch + WebFetch; excludes Reddit/X/Twitter |
| Web (Japan) 🇯🇵 | 12 pages | — | WebSearch: gizmodo.jp, itmedia.co.jp, mynavi.jp, crystal-method.com, ai.cbagames.jp, gadget-otaku.com, chaitechjp.substack (403), bloomberg.com/jp, ai-souken.com, singularitysociety.org, labmemo.com, xenospectrum.com |
| Web (China) 🇨🇳 | 24 pages | — | WebSearch: Juejin (3), CSDN (1), Guancha, China.com, Sohu, Sina Finance (3), 21Jingji (2), Zhihu (2), VOA Chinese, Bannedbook (2), Huxiu, Guangming, Qiniu, Tencent Cloud, fcgvisa, linux.do, stdaily |

---

## Synthesized Findings

### 1. [new] DeepSeek + MiniMax Win China Export-Control Approval for Global Use (Oct 23)
**Claim:** CCTV-affiliated Yuyuantantian account confirmed Oct 23 that DeepSeek and MiniMax were the first companies to complete registration under China's Oct 16 export-control framework, clearing both for continued open-source and overseas authorized use.
- **Source of announcement:** Yuyuantantian (玉渊谭天) — CCTV-affiliated social account; widely treated as authoritative state signal
- **What "completion" means:** Both companies "顺利履行登记手续，并完成开源和海外授权使用" (successfully completed registration and open-source/overseas authorization)
- **Policy framing (same source):** "划定边界，而非单纯限制AI技术对外出口" (establishing boundaries, not simply restricting exports); three restricted categories: data security, sensitive applications, computational infrastructure; API/SaaS/apps remain permanently outside scope
- **WAICO provision:** Export control framework explicitly facilitates AI cooperation for WAICO member nations — creates preferred-access lane for aligned nations
- **"Not a policy reversal" (Oct 23 Yuantan Tian):** "此次修订是依法依规进行的常态化工作" (routine regulatory work; China has revised the Directory many times since 2001)
- **21Jingji framing:** "DeepSeek、MiniMax出手，国产AI大模型'新战场'来了" (DeepSeek and MiniMax act; the new battlefield for Chinese AI going global has arrived)
- **Geopolitical signal:** Fastest-possible regulatory compliance by China's two most globally-deployed AI companies; demonstrates export control is a gate, not a wall
- **Sources:** [bloomberg.com](https://www.bloomberg.com/news/articles/2026-10-23/deepseek-minimax-win-approval-for-global-use-state-media-says) · [finance.sina.cn](https://finance.sina.cn/2026-10-23/detail-iniwcnvc5905718.d.html) · [finance.sina.com.cn Yuantan Tian](https://finance.sina.com.cn/jjxw/2026-10-23/doc-iniweiyu8031101.shtml) · [wtvbam.com](https://wtvbam.com/2026/10/23/chinas-deepseek-minimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says/) · [money.usnews.com](https://money.usnews.com/investing/news/articles/2026-10-23/chinas-deepseek-minimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says) · [www.thestar.com.my](https://www.thestar.com.my/tech/tech-news/2026/10/23/deepseek-minimax-win-approval-for-global-use-state-media-says) · [21jingji.com](https://www.21jingji.com/article/20261019/herald/327e351994ba49a91d29ba8fc438a987.html) · [bannedbook.org](https://www.bannedbook.org/bnews/itnews/20261023/2372850.html) · [tradersunion.com](https://tradersunion.com/news/companies/show/3938681-deepseek-minimax-china-ai-export-approval/) · [investing.com](https://investing.com/news/stock-market-news/chinas-deepseekminimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says-4968133) 🇨🇳 🌐
- **CN community:** [politics.gmw.cn](https://politics.gmw.cn/2026-10/23/content_39062802.htm) · [21jingji.com Yuantan analysis](https://www.21jingji.com/article/20261023/herald/cbeccbd50748efda57788d0dffb53af2.html) 🇨🇳
- **Platforms:** Web (China) 🇨🇳, Web (global) 🌐

---

### 2. [update] MiniMax M3.1 Flash Weights Released Today — MiniMax Community License, $20M Threshold, Together AI
**Claim:** MiniMax dropped the 428B/23B-active M3.1 Flash weights on Hugging Face Oct 23 — but under MiniMax's own community license (attribution required; $20M annual revenue threshold triggers prior written authorization), not MIT/Apache; Together AI named as production inference partner.
- **Weight specs:** 428B total / 23B active MoE; 252.4 GB (48 shards + 2.3 GB speculative-decoding drafter); 1M context; text/image/video input
- **License:** MiniMax community license — not open-source; commercial requires "Built with MiniMax M3.1-Flash" attribution; >$20M revenue needs MiniMax's prior written authorization
- **Inference partner:** Together AI (named in MiniMax announcement)
- **Distinction:** "A real open-weights release, and it is not an open-source one" — OrcaRouter analysis; vs DeepSeek V4.1 Flash MIT = full commercial freedom
- **The Decoder framing:** "MiniMax M3.1 Flash shows China's AI price race has no floor in sight"
- **BenchLM:** Chinese models list #7 at 67.1 (unchanged from Oct 19); not yet on global open-weight list (pending license review per previous entry)
- **HN:** Active thread at https://news.ycombinator.com/item?id=50154540
- **Sources:** [orcarouter.ai/minimax-weights](https://www.orcarouter.ai/blog/minimax-m3-1-flash-open-weights) · [technode.com](https://technode.com/2026/10/23/minimax-releases-open-weights-for-428-billion-parameter-m3-1-flash-model/) · [runtimewire.com](https://runtimewire.com/article/minimax-m31-flash-open-weights-together-inference) · [fourweekmba.com](https://fourweekmba.com/ai-minimax-opens-m3-1-flash-20m-products-need-its-sign-off/) · [the-decoder.com](https://the-decoder.com/minimax-m3-1-flash-shows-chinas-ai-price-race-has-no-floor-in-sight/) · [orcarouter.ai/license-compare](https://www.orcarouter.ai/blog/minimax-m3-1-flash-vs-deepseek-v4-1-flash) · [strongmocha.com](https://strongmocha.com/ai-infrastructure/minimax-m3-1-flash-a-closer-look-at-its-open-model-test-results/) 🌐
- **Platforms:** Web (global) 🌐, Hacker News 🌐

---

### 3. [new] Tencent Hy Memory 2.0 (Oct 16) — Three-Layer Apache 2.0 Agent-Memory Stack
**Claim:** Tencent Hunyuan open-sourced Hy Memory 2.0 on Oct 16 under Apache 2.0 — a three-layer release comprising a memory model (Hy-Memory-30B-A3B), a Python framework, and a local-first app (MemHub); claims to beat Claude Opus 5 on major memory benchmarks.
- **Three layers:**
  1. **Model:** Hy-Memory-30B-A3B on Hugging Face; attributed RL for long-term memory writing; 30B/3B active MoE
  2. **Framework:** hy-memory==2.0.4 Python package (chat, working, coding memory)
  3. **App:** MemHub — local-first CLI + macOS app pulling from 10 AI tools; stores on local disk
- **License:** Apache 2.0 (all three layers)
- **Benchmark claim:** "Beats Claude Opus 5 across major memory frameworks" — per KuCoin/TechFlowPost
- **GitHub:** https://github.com/Tencent-Hunyuan/Hy-Memory
- **Context:** Hy4 Pro language model still pending; Hy Memory 2.0 is separate product (agent memory layer, not base LLM)
- **Sources:** [aitamer.news](https://aitamer.news/posts/tencent-hy-memory-2-open-source-agent-memory/) · [orcarouter.ai](https://www.orcarouter.ai/blog/hy-memory-2-0-open-source-stack) · [letsdatascience.com](https://letsdatascience.com/news/tencent-open-sources-hy-memory-20-stack-f1fcc6c1) · [latenode.com](https://latenode.com/news/tencent-open-sources-hy-memory-2-0-stack) · [kucoin.com](https://www.kucoin.com/news/flash/tencent-hunyuan-launches-open-source-hy-memory-2-0-framework-claims-superior-performance-over-opus-5) · [techflowpost.com](https://www.techflowpost.com/en-US/newsletter/140244) 🌐
- **Platforms:** Web (global) 🌐

---

### 4. [new] Kimi K3.1 Official Teaser Video — First Confirmation, No Release Yet
**Claim:** On Oct 23, Moonshot's official Kimi account posted a 24-second video showing "Model: Kimi K3.1" in a Kimi Code terminal, constituting the first official acknowledgment of K3.1 — but no model card, pricing, or release date.
- **Video content:** Retro-computer terminal shows K3.1 label while the model writes a Three.js 3D scene
- **Prior signals:** kimi-k3-1 identifier found on Moonshot API (late Sep); K3.1 appeared in Kimi Code model-switching config Oct 21
- **Expected features (from config leaks):** Three reasoning levels (Low/High/Max); 1M context; native Agent mode; Swarm multi-agent collaboration
- **Status:** Teaser only; OrcaRouter: "Four signals point at a launch next week"
- **Sources:** [explainx.ai](https://explainx.ai/blog/kimi-k3-1-teaser-video-kimi-code-terminal-three-js-release-what-is-confirmed-2026) · [kucoin.com (video)](https://www.kucoin.com/news/flash/kimi-official-video-reveals-k3-1-model) · [kucoin.com (imminent)](https://www.kucoin.com/news/flash/kimi-official-video-reveals-k3-1-model-new-release-imminent) · [cellcog.ai](https://cellcog.ai/blog/kimi-k3-1-release-date/) · [orcarouter.ai (leak)](https://www.orcarouter.ai/blog/kimi-k3-1-next-week-leak) · [runtimewire.com](https://runtimewire.com/article/kimi-code-is-preparing-to-release-kimi-k3-1-as-model-appears-mid-session) · [medium.com](https://medium.com/data-science-in-your-pocket/kimi-k3-1-is-here-71936c8cd1ce) 🌐
- **Platforms:** Web (global) 🌐

---

### 5. [new] Sage-A1.5 (InternScience/Shanghai AI Lab) Enters BenchLM at #10
**Claim:** Sage-A1.5 — a 35B MoE Apache 2.0 agentic model from InternScience (Shanghai AI Lab affiliation) fine-tuning Qwen3.6 — entered BenchLM at #10 (63.0), notable for its scientific-discovery agentic orchestration design.
- **Specs:** 35B MoE (Qwen3.6-35B-A3B base); Apache 2.0; 262K context
- **Capabilities:** Agentic orchestration (parallel subagent investigation), verification mode (mid-trajectory self-review), open scientific discovery (neuroscience/electrochemistry with real feedback)
- **Paper:** https://huggingface.co/papers/2610.28578
- **HuggingFace:** https://huggingface.co/InternScience/Sage-A1.5
- **BenchLM:** #10 at 63.0 (new entry as of Oct 23 snapshot)
- **Sources:** [benchlm.ai/sage](https://benchlm.ai/models/sage-a1-5-fp8) · [huggingface.co/InternScience](https://huggingface.co/InternScience/Sage-A1.5) · [modelscope.ai](https://www.modelscope.ai/collections/InternScience/Sage-A15) 🌐
- **Platforms:** Web (global) 🌐

---

### 6. [new] Bilibili Index-Translate (Sep 30 – Oct 10) — 35B MoE, 150 Languages, Apache 2.0
**Claim:** Bilibili's Index team released Index-Translate (35B/3B active MoE, Apache 2.0) on Sep 30 covering 150 languages with free API and image translation — missed in the Oct 20 run.
- **Architecture:** MoE 35B/3B active; 262K context; based on Qwen3.5; GGUF/FP8/NVFP4 quantized builds available
- **Timeline:**
  - Sep 30: weights on HuggingFace + ModelScope (2B/9B/35B preview)
  - Oct 2: quantized builds (GGUF, FP8, NVFP4)
  - Oct 4: free public API at index-translate.bilibili.com/v1
  - Oct 10: multimodal image translation (zero external OCR dependencies)
- **License:** Apache 2.0
- **GitHub:** https://github.com/bilibili/Index-Translate
- **CN community:** Active discussion in linux.do thread https://linux.do/t/topic/2974061
- **Sources:** [pandaily.com](https://pandaily.com/bilibili-index-translate-open-source-qwen3-5-150-languages) · [techjacksolutions.com](https://techjacksolutions.com/ai-brief/bilibili-index-translate-35b-moe-150-languages-apache-2/) · [phemex.com](https://phemex.com/news/article/bilibili-opensources-indextranslate-model-supporting-150-languages-98353) · [github.com/bilibili/Index-Translate](https://github.com/bilibili/Index-Translate) 🌐
- **Platforms:** Web (global) 🌐, Web (China) 🇨🇳

---

### 7. [update] DeepInfer Viral — 15K GitHub Stars in 5 Days; "DeepSeek才是真正的OpenAI"
**Claim:** DeepInfer (released Oct 20) reached 15,000+ GitHub stars within 5 days; the phrase "DeepSeek才是真正的OpenAI" (DeepSeek is the true OpenAI) went viral across CN platforms (Guancha, China.com, Sohu, Sina, Toutiao), framing Apache 2.0 production inference as a strategic rebuke of US restrictions.
- **Performance:** Single cluster throughput 1.55 trillion tokens/day for V4.1 Flash on DeepInfer
- **GitHub stars:** 15,000+ within 5 days (per multiple CN sources including Guancha, Sohu)
- **Juejin framing:** "V4.1 Flash实现了与Astra接近的成本，而成本仅为Astra的1/15" (at 1/15 the cost of Astra)
- **Sina/Weibo analysis:** "开源论文不限制，核心资产不再'洗澡式出海'" — open-source releases escape both US and Chinese restrictions; core IP stay-in-China era begins
- **SCMP (Oct 21-22):** DHS ban "may deter US private sector firms from adopting Chinese AI models" — chilling effect beyond federal government
- **Juejin (Oct 21):** "国产AI出海的考验才刚刚开始" (Test for Chinese AI going global has just begun)
- **Sources:** [guancha.cn](https://www.guancha.cn/CaiJing/2026_10_22_905376.shtml) · [news.china.com](https://news.china.com/socialgd/10000169/20261023/49812588.html) · [m.sohu.com](https://m.sohu.com/a/1090953467_122033970/) · [post.smzdm.com](https://post.smzdm.com/p/agg5v9e3/) · [sina.cn](https://www.sina.cn/weibo/detail/5356407437656966.html) · [scmp.com](https://www.scmp.com/tech/big-tech/article/3371649/washingtons-deepseek-ban-may-deter-us-firms-adopting-chinese-ai-models-experts) · [juejin.cn/7698331749005639723](https://juejin.cn/post/7698331749005639723) · [juejin.cn/7698932135780991039](https://juejin.cn/post/7698932135780991039) · [21jingji.com/20261019](https://www.21jingji.com/article/20261019/herald/327e351994ba49a91d29ba8fc438a987.html) · [news.ycombinator.com/50163277](https://news.ycombinator.com/item?id=50163277) 🇨🇳 🌐
- **Platforms:** Web (China) 🇨🇳, Web (global) 🌐, Hacker News 🌐

---

### 8. [update] BenchLM Rankings (Oct 23) — 105 Models; Sage-A1.5 New at #10; MiMo-V2.6-Flash Visible at #7
**Claim:** BenchLM grew to 105 ranked models (from 103 Oct 20); Sage-A1.5 (InternScience) is the notable new entry at #10 (63.0); MiMo-V2.6-Flash (Xiaomi) now explicitly tracked at #7 (64.6); micro-score shifts throughout top-20; Mistral Large 4 remains Pending Day 17.
- **Top-10 (Oct 23):**
  | Rank | Model | Lab | Score | vs Oct 20 |
  |------|-------|-----|-------|-----------|
  | 1 | MiMo-V2.6-Pro | Xiaomi | 73.6 | -0.1 |
  | 2 | Qwen3.8 Max | Alibaba | 69.7 | stable |
  | 3 | Step 5 Preview | StepFun | 69.7 | +0.1 |
  | 4 | Ling 3.1 Flash | InclusionAI | 68.1 | stable |
  | 5 | GLM-5.3 | Z.AI | 68.0 | stable |
  | 6 | DeepSeek V4.1 Flash 1017 | DeepSeek | 65.7 | stable |
  | 7 | MiMo-V2.6-Flash | Xiaomi | 64.6 | ← now explicitly tracked |
  | 8 | dots3-note Preview | Dots Studio | 63.9 | -0.2 |
  | 9 | DeepSeek V4 Pro 0813 | DeepSeek | 63.2 | stable |
  | 10 | **Sage-A1.5** | InternScience | 63.0 | **NEW** |
- **Other notable:** Kimi K2.6 (Moonshot) appears at #18 (58.3); total model count 105 (was 103)
- **Mistral Large 4:** Pending Day 17 (target Oct 27)
- **Sources:** [benchlm.ai/best/open-source](https://benchlm.ai/best/open-source) · [benchlm.ai/models/sage-a1-5-fp8](https://benchlm.ai/models/sage-a1-5-fp8) · [benchlm.ai/models/mimo-v2-6-flash](https://benchlm.ai/models/mimo-v2-6-flash) · [dev.to/leaderboard-audit](https://dev.to/ward_ed_6b5e6aa8ded94a987/best-open-weight-llm-in-october-2026-auditing-two-leaderboards-row-by-row-1b64) 🌐
- **Platforms:** Web (global) 🌐

---

### 9. [update] Polymarket Chinese AI Ban — 18-19% Yes; DHS Chilling Effect Noted
**Claim:** Polymarket "US removes public access to major Chinese AI model in 2026" ticked up to ~18-19% Yes (from 17% Oct 20); SCMP analysis identifies DHS ban creating chilling effect on US private sector adoption of Chinese AI.
- **Market odds:** ~18-19% Yes (evolution: 33% Jul → 26% Aug → 23% → 17% Oct 20 → 18-19% Oct 23)
- **Why odds ticked up:** SCMP experts note the DHS ban creates reputational/legal risk for US companies deploying Chinese AI — possible path to broader restriction; still "improbable absent major escalation"
- **Market scope:** Resolves Yes only on formal action cutting off US _public_ access; DHS federal procurement ban does NOT qualify
- **Sources:** [polymarket.com](https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223) · [scmp.com](https://www.scmp.com/tech/big-tech/article/3371649/washingtons-deepseek-ban-may-deter-us-firms-adopting-chinese-ai-models-experts) · [cryptobriefing.com/polymarket](https://cryptobriefing.com/us-government-chinese-ai-model-restriction-polymarket/) · [news.bitcoin.com](https://news.bitcoin.com/polymarket-33-odds-us-blocks-chinese-ai-model-2026/) 🌐
- **Platforms:** Polymarket 🌐, Web (global) 🌐

---

### 10. [update] Mistral Large 4 — Oct 27 Target; Still Pending Day 17
**Claim:** Mistral Large 4 weights are confirmed targeting October 27 — a three-week testing period with developers, cybersecurity leaders, and government authorities — still not released as of Oct 23 (BenchLM Pending Day 17).
- **Oct 27:** TNW reports weights will be published after ~3 weeks of closed testing (including government/security stakeholders); Mistral's official commitment remains "by end of October"
- **What's new vs Oct 20:** Confirmed Oct 27 target per TNW; "three-week testing period" framing adds government/security testing context
- **Scale:** 3,800 Nvidia Grace Blackwell GPUs in Mistral's European data centers
- **Sources:** [thenextweb.com](https://thenextweb.com/news/mistral-releases-large-4-a-1-trillion-parameter-open-weight-ai-model) · [betanews.com](https://betanews.com/article/mistral-large-4-preview-open-weights/) · [letsdatascience.com](https://letsdatascience.com/blog/mistral-trillion-parameter-weights-this-month-license-blank) · [miraflow.ai](https://miraflow.ai/blog/mistral-large-4-explained-1t-open-weight-moe-benchmarks-2026) · [venturebeat.com](https://venturebeat.com/technology/mistral-debuts-large-4-le-chonk-a-1-trillion-parameter-text-output-model-with-high-benchmarks-planned-for-open-weights-release) 🌐
- **Platforms:** Web (global) 🌐

---

### 11. [update] China's Wave of 7 Models — Kimi K3.1 Teaser Issued; 6 of 7 Still Pending Full Release
**Claim:** Of the 7 major Chinese releases forecast for late Oct (Weibo community forecast from Oct 12), MiniMax M3.1 Flash weights are now fully out (2/7 considering API + weights as distinct milestones); Kimi K3.1 issued official teaser Oct 23; 6 of 7 still lack full public API/release.
- **Status Oct 23:**
  - **MiniMax M3.1 Flash:** API Oct 19 + weights Oct 23 ✓ (fully shipped)
  - **Kimi K3.1:** Teaser video Oct 23; still no release ←
  - **DeepSeek V4.1 Pro:** Unreleased; stealth endpoint still reported at ~180 tok/s
  - **GLM 5.5:** Still unreleased; Zhipu GLM-5.3 remains current
  - **Qwen 4.0 Max + 27B:** Still in training; community window Oct 22 passed without release
  - **Tencent Hy-4 Pro:** Still pending (Hy Memory 2.0 was separate release)
  - **Xiaomi MiMo V2.7 Pro:** Still pending
- **Sources:** [explainx.ai/kimi-k3-1](https://explainx.ai/blog/kimi-k3-1-teaser-video-kimi-code-terminal-three-js-release-what-is-confirmed-2026) · [cellcog.ai/glm](https://cellcog.ai/blog/glm-5-5-release-date/) · [orcarouter.ai/qwen4-vllm](https://www.orcarouter.ai/blog/qwen-4-leak-vllm-fuse-op) · [orcarouter.ai/kimi](https://www.orcarouter.ai/blog/kimi-k3-1-next-week-leak) 🌐
- **Platforms:** Web (global) 🌐

---

### 12. [update] Japan Enterprise: DHS DeepSeek Ban Creates Three-Layer Risk Framework
**Claim:** Japanese tech analysts formalized a three-layer risk framework (data sovereignty, supply chain/compliance, business continuity) following the DHS ban; consensus: self-hosted open weights + switchability design as the practical response.
- **Crystal Method (Oct 21 JP) three-layer risk:**
  1. **Data sovereignty:** "機密情報・顧客データ・個人情報を入力することのリスクは、国内ベンダーや欧米クラウドとは性質が異なる" (risks differ fundamentally from domestic/Western cloud)
  2. **Supply chain/compliance:** Japanese firms with US clients face contract renegotiation; defense/aerospace/semiconductor/finance most vulnerable
  3. **Business continuity:** "V4-Proの出力価格はオフピークでも旧プロモーション価格比で約2.3倍の水準に上昇" (pricing jumped 2.3× even at off-peak in August 2026)
- **Recommended path:** Distinguish DeepSeek model technology vs cloud service; self-hosted MIT-licensed weights mitigate data sovereignty while preserving capability
- **AI.cbagames.jp (Oct 21):** "地政学的リスクの観点から慎重な検討が求められています" (careful consideration required from geopolitical risk perspective)
- **ITmedia + MyNavi:** Major Japanese IT trade press covered DHS ban within 24 hours (Oct 20-21)
- **Sources:** [crystal-method.com](https://crystal-method.com/blog/us-bans-deepseek-japan-enterprise-risk/) · [ai.cbagames.jp](https://ai.cbagames.jp/2026/10/21/deepseek-us-federal-ban-japan/) · [itmedia.co.jp](https://www.itmedia.co.jp/news/article/2610/20/2000002405/) · [mynavi.jp](https://news.mynavi.jp/techplus/article/20261021-5167694/) · [gizmodo.jp](https://www.gizmodo.jp/article/trump-admin-bans-deepseek-from-federal-agencies/) · [gadget-otaku.com](https://gadget-otaku.com/2026/10/20/us-federal-agencies-ban-deepseek-ai/) 🇯🇵
- **Platforms:** Web (Japan) 🇯🇵

---

### 13. [update] Bruegel/Global Analysis: China's Open-Source Exemption Is Fragile for Europe
**Claim:** Bruegel (Oct 23) argues European dependence on Chinese open-weight models faces structural fragility — open-source exemptions are real today but China could stop open-sourcing future frontier models; advocates European open-weight investment (Mistral) as hedge.
- **Bruegel key point:** China is "only country besides US controlling nearly all technologies required for AI"; even if existing weights stay available, next generation may not be open
- **China Global South Project (Oct 22):** China's export controls include WAICO facilitation provision — creates tiered access; Global South countries gain preferred route through WAICO membership
- **Tech Policy Press:** "Will China crack down on open-weight models?" — concludes: existing published weights are permanently exempt; future frontier models may not be open-sourced
- **Sina/Weibo analysis (Oct 23):** "核心资产不再'洗澡式出海'" — core IP stays in China going forward; open-source as strategic tool, not obligation
- **Sources:** [bruegel.org/china-grip](https://www.bruegel.org/first-glance/what-lessons-should-europe-take-chinas-tightening-grip-its-advanced-ai) · [bruegel.org/outbound](https://www.bruegel.org/analysis/chinas-outbound-ai-strategy-starts-models-and-governance-and-ends-chips) · [chinaglobalsouth.com](https://chinaglobalsouth.com/2026/10/22/china-ai-export-controls-global-south/) · [techpolicy.press](https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/) · [sina.cn/weibo](https://www.sina.cn/weibo/detail/5356407437656966.html) 🌐 🇨🇳
- **Platforms:** Web (global) 🌐, Web (China) 🇨🇳

---

### Still true (ongoing — no new facts since Oct 20)

- `dhs-deepseek-federal-ban-oct20` — DHS ban still in force; follow-up coverage ongoing (SCMP chilling effect, CN approval news)
- `deepseek-deepinfer-open-source` — 15K+ stars in 5 days; strategic framing deepening (see Finding 7)
- `benchlm-oct16-rankings-step5-ling` — Step 5 at 69.7 (+0.1), otherwise stable; see Finding 8 for Oct 23 update
- `benchlm-aug10-rankings-minimax-leads` — see Finding 8
- `china-mofcom-ai-export-controls-draft-oct16` — Oct 16 draft still in comment window (Nov 15); DeepSeek+MiniMax completed registration (see Finding 1)
- `deepseek-v4-1-flash-release` — BenchLM #6 at 65.7; DeepInfer now adds production-grade dual hardware context
- `double-curtain-us-china-export-controls` — Continues; DeepSeek+MiniMax approval adds new data point: export control as gate not wall
- `polymarket-us-chinese-model-ban` — 18-19% (ticked up from 17%; see Finding 9)
- `minimax-h1-2026-agent-dividend` — M3.1 Flash weights now fully released; Together AI inference
- `mistral-large4-le-chonk` — Oct 27 target confirmed (government testing period); still pending (see Finding 10)
- `chinese-model-wave-oct-nov-2026` — Kimi K3.1 teaser Oct 23; 6/7 still pending (see Finding 11)
- `kimi-k3-weights-open-source` — K3.1 teaser issued Oct 23; K3.1 not released yet
- `deepseek-v41-pro-2t-leak` — Still unreleased; no new official info
- `qwen4-apsara-announcement` — Community window Oct 22 passed without release; Qwen 4 still in training
- `glm-5-5-expected-august` — Still unreleased; no date; GLM-5.3 current
- `deepseek-funding-12b-tencent-catl` — $12B round; STAR 2027; no new development
- `tencent-oracle-offshore-chip-deal` — $7B SE Asia lease; RASA in Senate NDAA; no new development
- `reflection-ai-beam-501b` — No update
- `carnegie-china-us-ai-talent` — China 40.6% vs US 34.2% researcher share; no new report
- `huawei-ascend-ecosystem-inflection` — DeepInfer Ascend support confirmed; ongoing
- `huawei-ascend-950-cloud-launch` — Commercial Sep 30; >50% market share; no new report
- `trump-diffusion-rule-remote-compute` — BIS FY2026 deadline missed; Senate NDAA pending; no update
- `mistral-glm52-eu-sovereign-hosting` — GLM-5.3 GA on Mistral EU + Amazon Bedrock; stable
- `deepseek-star-market-ipo-citic` — $12B round; STAR 2027; no new development
- `alibaba-zhenwu-v900-chip` — T-Head Zhenwu V900; Q1 2027 mass production; no update
- `huawei-ascend-960-connect2026` — 960DT Q1 2027; supply-constrained
- `deepseek-v4-pro-retirement-reversed` — V4 Pro API continues; BenchLM #9 at 63.2
- `deepseek-v41-flash-abliteration` — MIT license forks active; no new development
- `anthropic-distillation-report-sep10` — ~200M exchanges; MOFCOM "groundless"; no enforcement
- `mistral-samsung-series-d-third-axis` — Samsung-led €3B Series D; Oct 27 weights target
- `chinese-models-global-share-30pct` — Vercel: 11% → 55% enterprise token traffic Jan-Aug 2026
- `xi-brics-ai-open-source-zone` — BRICS AI open-source zone; WAICO facilitation in export controls
- `qwen-image-2-1-open-source` — No update
- `us-china-ai-safety-talks-sep24` — Trade truce to Jan 10, 2027; ongoing
- `rasa-senate-pending-cloud-loophole` — RASA + OVERWATCH + Chip Security + MATCH in Senate NDAA; no floor vote
- `deepseek-160k-huawei-inner-mongolia` — 160K Ascend order; HBM constraints
- `kimi-k3-gpu-crunch-subscription-pause` — Moonshot HKEX IPO; no new development
- `china-domestic-chip-mass-pivot` — Domestic >52.3% Q1 2026; Huawei >50%; no new data
- `xi-waic-open-source-mandate` — WAICO + BRICS; Joe Tsai; ongoing
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon 375B-A23B Apache 2.0; stable
- `qwen-3-8-max-open-weights-pending` — BenchLM #2 at 69.7; Qwen 4 still in training
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash; Ascend-trained; no change
- `tencent-hy4-preview-apache` — Hy4 Preview #14 BenchLM (61.3); Hy-4 Pro still pending
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3 #5 BenchLM (68.0); GA on Amazon Bedrock
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next #11 BenchLM (62.8)
- `open-weight-licensing-bifurcation` — MiniMax M3.1 Flash community license ($20M threshold); MIT/Apache remains norm elsewhere
- `deepseek-v4-flash-vision-exp` — V4.1 Flash 1017 ongoing; BenchLM #6 at 65.7
- `meta-muse-glimmer-us-open-weight` — Muse Spark Open #12 at 62.8
- `dots3-note-preview-rednote` — BenchLM #8 at 63.9 (-0.2)
- `ornith-1-5-self-improving` — BenchLM #13 at 62.4
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 BenchLM #15 at 60.5
- `mistral-frontier-moe-silent` — Oct 27 target; Day 17 BenchLM Pending
- `kimi-k3-eda-chip-design` — K3 EDA use; K3.1 teaser Oct 23
- `minimax-m3-pro-2-7t` — M3.1 Flash weights released; M3 at #20 (~55)
- `china-mofcom-export-controls-ai` — RESOLVED into Finding 1 (registration completed); draft still in comment window
- `deepseek-chip-ascend-950dt` — DeepInfer confirms production dual support ongoing
- `deepseek-zhipu-self-chip-development` — DeepInfer NVIDIA/Ascend dual confirmed ongoing
- `chinese-military-pla-distillation-reuters` — No enforcement; no new development
- `distillation-scale-data` — ~200M exchanges; no enforcement
- `nemotron-3-ultra-us-open-weight` — Nemotron 3.5 Bolt; BenchLM license review pending
- `polymarket-chinese-ai-company` — Alibaba 72% best Chinese AI; Moonshot 25% (not re-verified)
- `inkling-small-thinking-machines` — BenchLM range; no update
- `mistral-shieldstral-safety-classifier` — No update
- `minimax-h3-geo-license-restriction` — US/EU/UK/Korea exclusion; no update
- `deepseek-autonomous-cyberattack-hermes` — No new development
- `industry-coalition-open-weights-letter` — 235+ signatories; ongoing
- `databricks-enterprise-glm-migration` — GLM-5.3 on Bedrock; Airbnb/Coinbase; ongoing
- `nvidia-h200-china-trivial` — H200 technically allowed; near-zero China revenue
- `jp-deepseek-japanese-cultural-benchmark` — JP 3-layer risk framework formalized (see Finding 12)
- `qwen38-omni-flash-agent` — LiveCodeBench v6 #3 at 92.6%; no new benchmark
- `qwen-huggingface-ecosystem-dominance` — 3B downloads in 6 months; no new data
- `open-weights-decelerationist-accelerationist` — MiniMax M3.1 Flash weights + DeepInfer continuing open-infrastructure entrenchment
- `openeurollm-european-sovereign` — Mistral Large 4 Oct 27 target; see Finding 10
- `deepseek-160k-huawei-inner-mongolia` — Order ongoing; HBM constraints
- `us-moonshot-distillation-sanctions` — Entity List threat; K3.1 teaser Oct 23; no formal action
- `openai-hf-cyberattack-glm-defense` — No new development
- `sakana-fugu-ultra-jp-orchestration` — LiveCodeBench v6 #1; ongoing
- `tsai-open-source-europe-sovereignty` — Joe Tsai Turin; Bruegel now adds European fragility analysis
- `eu-enisa-jrc-chinese-ai-testing` — ENISA/JRC testing; no new announcement
- `eu-ai-act-august-enforcement` — EU AI Office enforcement; no new announcement
- `glm-53-amazon-bedrock-ga` — GA on Bedrock; stable
- `stepfun-step5-preview-open-weights` — BenchLM #3 at 69.7 (+0.1)
- `ant-group-ling31-flash-benchlm-top5` — BenchLM #4 at 68.1; open-source still "planned"
- `xiaomi-mimo-v26-tops-leaderboard` — BenchLM #1 at 73.6 (-0.1); MiMo-V2.6-Flash now #7 at 64.6
- `xiaomi-mimo-frontier-entry` — Still BenchLM #1 at 73.6
- `qwen3-8-27b-apache-multimodal` — BenchLM #16 at 59.6 on global list
- `us-anthropic-fable-mythos-foreign-ban` — Jun 12 US ban; ongoing precedent
- `nvidia-nemotron-bolt-fully-open` — Released Oct 15; BenchLM license review still pending
- `minimax-m31-flash-space-bunny` — Weights NOW released Oct 23 (see Finding 2)

---

## Cross-Source Patterns

### Pattern 1: Export Control Symmetry → Selective Permeability (US bans specific company; China registers and clears same companies)
- **Signal:** DHS banned DeepSeek from federal agencies (Oct 19-20). China's export controls (Oct 16) imposed registration requirement. By Oct 23, DeepSeek and MiniMax completed registration — the first two companies to navigate both sides of the curtain simultaneously. Result: restricted from US government but globally cleared by China.
- **Asymmetry:** US ban is hard (remove from systems); China registration is fast (days to complete). Open-source Apache 2.0 weights remain permanently outside both regimes.
- **SCMP chilling effect:** DHS ban may extend deterrence into US private sector without formal legal action
- **Platforms:** Web (global) 🌐, Web (China) 🇨🇳, Polymarket 🌐
- **Quote:** "DeepSeek才是真正的OpenAI" — viral phrase across CN platforms, framing Apache 2.0 production infrastructure as immune to any jurisdiction's restrictions (multiple CN sources) 🇨🇳

### Pattern 2: License Divergence Deepens — MIT/Apache vs. Commercial Thresholds
- **Signal:** MiniMax M3.1 Flash (Oct 23) introduced a MiniMax community license with $20M revenue threshold — distinct from the MIT/Apache norm for Chinese models. DeepSeek V4.1 Flash = MIT (pure commercial freedom). MiniMax M3.1 Flash = open weights but NOT open-source. The distinction is now material for enterprise deployment decisions.
- **Platforms:** Web (global) 🌐, Hacker News 🌐
- **Quote:** "A real open-weights release, and it is not an open-source one" — OrcaRouter analysis ([link](https://www.orcarouter.ai/blog/minimax-m3-1-flash-open-weights)) 🌐

### Pattern 3: JP Enterprise Converges on Self-Hosting as Risk Mitigation
- **Signal:** Japanese IT media (ITmedia, MyNavi, Crystal Method, AI.cbagames.jp) all published DHS ban impact analyses within 24-48 hours, all converging on the same recommendation: distinguish Chinese model weights (MIT-licensed, self-hostable) from Chinese cloud services (data sovereignty risk). Pricing volatility (2.3× increase) + geopolitics + US compliance risk = three-layer forcing function.
- **Platforms:** Web (Japan) 🇯🇵
- **Quote (JP/EN):** "V4-Proの出力価格はオフピークでも旧プロモーション価格比で約2.3倍の水準に上昇" ("Pricing jumped 2.3× even at off-peak rates in August 2026") — crystal-method.com ([link](https://crystal-method.com/blog/us-bans-deepseek-japan-enterprise-risk/)) 🇯🇵

### Pattern 4: China's Open-Source Exemption — Strategic Tool, Not Permanent Obligation
- **Signal:** Bruegel (Oct 23), Tech Policy Press, and Sina/Weibo analysis all note that the open-source exemption in China's export controls is real today but not structurally guaranteed. The "洗澡式出海" (laundering via overseas open-source entities) route is being closed. Future frontier models may not be open-sourced. The exemption benefits existing published weights (DeepSeek, Qwen, Kimi) permanently but creates no obligation for future releases.
- **Platforms:** Web (global) 🌐, Web (China) 🇨🇳
- **Quote (CN/EN):** "核心资产不再'洗澡式出海'" ("Core assets will no longer go abroad through laundering methods") — Sina/Weibo analysis of 2026 AI ban ([link](https://www.sina.cn/weibo/detail/5356407437656966.html)) 🇨🇳

---

## Per-Platform Tables

### Polymarket 🌐
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US removes public access to major Chinese AI model in 2026 | ~18-19% Yes | $90,846+ | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |

### Hacker News 🌐
| Story | Notes | URL |
|-------|-------|-----|
| DeepInfer: High-performance inference framework for DeepSeek models | Top of HN Oct 20; 15K+ GitHub stars in 5 days | https://news.ycombinator.com/item?id=50163277 |
| MiniMax M3.1 Flash open weights | Active Oct 23; license discussion dominant thread | https://news.ycombinator.com/item?id=50154540 |

### Web 🌐 🇯🇵 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Bloomberg | https://www.bloomberg.com/news/articles/2026-10-23/deepseek-minimax-win-approval-for-global-use-state-media-says | DeepSeek+MiniMax global approval |
| 🌐 | TechNode | https://technode.com/2026/10/23/minimax-releases-open-weights-for-428-billion-parameter-m3-1-flash-model/ | M3.1 Flash 428B weights |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/minimax-m3-1-flash-open-weights | $20M licence analysis |
| 🌐 | OrcaRouter (compare) | https://www.orcarouter.ai/blog/minimax-m3-1-flash-vs-deepseek-v4-1-flash | MiniMax vs DeepSeek license |
| 🌐 | The Decoder | https://the-decoder.com/minimax-m3-1-flash-shows-chinas-ai-price-race-has-no-floor-in-sight/ | China price race framing |
| 🌐 | FourWeekMBA | https://fourweekmba.com/ai-minimax-opens-m3-1-flash-20m-products-need-its-sign-off/ | $20M sign-off |
| 🌐 | RuntimeWire | https://runtimewire.com/article/minimax-m31-flash-open-weights-together-inference | Together AI inference |
| 🌐 | SCMP | https://www.scmp.com/tech/big-tech/article/3371649/washingtons-deepseek-ban-may-deter-us-firms-adopting-chinese-ai-models-experts | DHS chilling effect private sector |
| 🌐 | TechCrunch | https://techcrunch.com/2026/10/20/us-orders-federal-agencies-to-remove-chinas-deepseek-ai-from-their-systems/ | DHS DeepSeek ban |
| 🌐 | CNBC | https://www.cnbc.com/2026/10/20/us-deepseek-federal-agency-ban.html | DHS ban overview |
| 🌐 | Bleeping Computer | https://www.bleepingcomputer.com/news/security/dhs-bans-deepseek-products-across-us-federal-civilian-agencies/ | Security framing |
| 🌐 | CyberScoop | https://cyberscoop.com/dhs-bans-deepseek-federal-agencies/ | Federal IT ban |
| 🌐 | AI Tamer | https://aitamer.news/posts/tencent-hy-memory-2-open-source-agent-memory/ | Hy Memory 2.0 Apache 2.0 |
| 🌐 | Latenode | https://latenode.com/news/tencent-open-sources-hy-memory-2-0-stack | Three-layer stack |
| 🌐 | Pandaily | https://pandaily.com/bilibili-index-translate-open-source-qwen3-5-150-languages | Bilibili Index-Translate |
| 🌐 | TechJackSolutions | https://techjacksolutions.com/ai-brief/bilibili-index-translate-35b-moe-150-languages-apache-2/ | 35B 150 languages Apache 2.0 |
| 🌐 | ExplainX | https://explainx.ai/blog/kimi-k3-1-teaser-video-kimi-code-terminal-three-js-release-what-is-confirmed-2026 | Kimi K3.1 teaser confirmed |
| 🌐 | KuCoin | https://www.kucoin.com/news/flash/kimi-official-video-reveals-k3-1-model-new-release-imminent | K3.1 release imminent |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Oct 23 rankings 105 models |
| 🌐 | BenchLM Sage | https://benchlm.ai/models/sage-a1-5-fp8 | Sage-A1.5 model card |
| 🌐 | HuggingFace Sage | https://huggingface.co/papers/2610.28578 | Sage-A1.5 paper |
| 🌐 | GitHub Tencent | https://github.com/Tencent-Hunyuan/Hy-Memory | Hy Memory 2.0 repo |
| 🌐 | GitHub Bilibili | https://github.com/bilibili/Index-Translate | Index-Translate repo |
| 🌐 | TNW | https://thenextweb.com/news/mistral-releases-large-4-a-1-trillion-parameter-open-weight-ai-model | Mistral Large 4 vs Chinese |
| 🌐 | BetaNews | https://betanews.com/article/mistral-large-4-preview-open-weights/ | Oct 27 target |
| 🌐 | VentureBeat | https://venturebeat.com/technology/mistral-debuts-large-4-le-chonk-a-1-trillion-parameter-text-output-model-with-high-benchmarks-planned-for-open-weights-release | Le Chonk launch |
| 🌐 | Bruegel | https://www.bruegel.org/first-glance/what-lessons-should-europe-take-chinas-tightening-grip-its-advanced-ai | EU fragility analysis |
| 🌐 | China Global South | https://chinaglobalsouth.com/2026/10/22/china-ai-export-controls-global-south/ | WAICO facilitation |
| 🌐 | Tech Policy Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | Open-weight analysis |
| 🌐 | Startupfortune | https://startupfortune.com/china-opposes-us-deepseek-ban-as-it-drafts-its-own-export-controls/ | Opposes ban while drafting own |
| 🌐 | TechNode | https://technode.global/2026/10/18/china-ai-export-controls-23-technologies/ | 23 technologies |
| 🌐 | The Decoder | https://the-decoder.com/china-plans-to-tighten-export-controls-on-open-weight-models-and-23-key-ai-technologies/ | Open-weight controls |
| 🌐 | Recouprev | https://recouprev.com/article/china-ai-model-export-controls-2026-deepseek-qwen-november-deadline | Nov 15 deadline |
| 🌐 | Latin Times | https://www.latintimes.com/deepseek-kimi-k3-open-source-strategy-turning-chinese-ai-geopolitical-force-600424 | Geopolitical force |
| 🌐 | US News | https://money.usnews.com/investing/news/articles/2026-10-23/chinas-deepseek-minimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says | Approval coverage |
| 🌐 | Local AI Zone | https://local-ai-zone.github.io/blog/October_2026_AI_Model_Updates.html | October AI models tracker |
| 🌐 | Digital Applied | https://www.digitalapplied.com/blog/ai-model-releases-october-2026-tracker | Release tracker |
| 🌐 | CellCog | https://cellcog.ai/blog/glm-5-5-release-date/ | GLM 5.5 still no date |
| 🌐 | OrcaRouter Kimi | https://www.orcarouter.ai/blog/kimi-k3-1-next-week-leak | K3.1 four signals |
| 🌐 | OrcaRouter Qwen4 | https://www.orcarouter.ai/blog/qwen-4-leak-vllm-fuse-op | Qwen 4 October window |
| 🌐 | Miraflow | https://miraflow.ai/blog/mistral-large-4-explained-1t-open-weight-moe-benchmarks-2026 | Large 4 1T explained |
| 🌐 | LetsDatasScience | https://letsdatascience.com/blog/mistral-trillion-parameter-weights-this-month-license-blank | Blank license |
| 🌐 | AI News | https://www.artificialintelligence-news.com/news/mistral-ai-launches-large-4-preview-ahead-open-weight-release/ | Preview launch |
| 🌐 | DEV Community | https://dev.to/ward_ed_6b5e6aa8ded94a987/best-open-weight-llm-in-october-2026-auditing-two-leaderboards-row-by-row-1b64 | Leaderboard audit |
| 🌐 | Computingforgeeks | https://computingforgeeks.com/xiaomi-mimo-v2-6-pro-flash/ | MiMo V2.6 Pro+Flash |
| 🌐 | Vals.ai | https://www.vals.ai/models/xiaomi_mimo-v2.6-flash | MiMo-V2.6-Flash independent |
| 🌐 | TradersUnion | https://tradersunion.com/news/companies/show/3938681-deepseek-minimax-china-ai-export-approval/ | Export approval |
| 🌐 | Investing.com | https://investing.com/news/stock-market-news/chinas-deepseekminimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says-4968133 | Approval |
| 🌐 | WTVB | https://wtvbam.com/2026/10/23/chinas-deepseek-minimax-win-approval-for-ai-global-use-state-media-affiliated-entity-says/ | Approval |
| 🌐 | Cryptobriefing Polymarket | https://cryptobriefing.com/us-government-chinese-ai-model-restriction-polymarket/ | Polymarket 26% earlier |
| 🌐 | BitcoinNews Polymarket | https://news.bitcoin.com/polymarket-33-odds-us-blocks-chinese-ai-model-2026/ | Polymarket 33% evolution |
| 🌐 | Phemex | https://phemex.com/news/article/bilibili-opensources-indextranslate-model-supporting-150-languages-98353 | Index-Translate |
| 🌐 | Panews | https://panews.io/articles/01a0f2b8-887c-72f6-b3a6-d8f6fa368e66 | Index-Translate |
| 🌐 | TechFlowPost | https://www.techflowpost.com/en-US/newsletter/140244 | Hy Memory 2.0 |
| 🌐 | ModelScope | https://www.modelscope.ai/collections/InternScience/Sage-A15 | Sage-A1.5 |
| 🌐 | HuggingFace InternScience | https://huggingface.co/InternScience/Sage-A1.5 | Sage-A1.5 weights |
| 🌐 | Medium Kimi K3.1 | https://medium.com/data-science-in-your-pocket/kimi-k3-1-is-here-71936c8cd1ce | K3.1 teaser |
| 🌐 | RuntimeWire Kimi | https://runtimewire.com/article/kimi-code-is-preparing-to-release-kimi-k3-1-as-model-appears-mid-session | K3.1 mid-session |
| 🌐 | CellCog Kimi | https://cellcog.ai/blog/kimi-k3-1-release-date/ | K3.1 release date |
| 🌐 | Eesel | https://www.eesel.ai/blog/minimax-m3-1-flash-review | M3.1 Flash review |
| 🌐 | StrongMocha | https://strongmocha.com/ai-infrastructure/minimax-m3-1-flash-a-closer-look-at-its-open-model-test-results/ | M3.1 test results |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/10/20/deepseek-open-sources-deepinfer-the-inference-framework-behind-its-production-services/ | DeepInfer |
| 🌐 | CCLeaks | https://ccleaks.com/news/deepseek-deepinfer-open-source-inference-oct-2026 | DeepInfer how-to-run |
| 🌐 | HackerNews (DHS) | https://thehackernews.com/2026/10/us-orders-deepseek-removed-from-federal.html | DHS ban |
| 🌐 | Technology.org | https://www.technology.org/2026/10/20/dhs-deepseek-ban-federal-civilian-agencies-fascsa/ | DHS FASCSA |
| 🌐 | Taipei Times | https://www.taipeitimes.com/News/biz/archives/2026/10/17/2003866098 | Export controls |
| 🌐 | Arxiv | https://arxiv.org/pdf/2604.06217 | End of Foundation Model Era |
| 🇯🇵 | ITmedia NEWS | https://www.itmedia.co.jp/news/article/2610/20/2000002405/ | DHS ban JP coverage |
| 🇯🇵 | MyNavi TechPlus | https://news.mynavi.jp/techplus/article/20261021-5167694/ | DHS ban JP IT coverage |
| 🇯🇵 | Gizmodo Japan | https://www.gizmodo.jp/article/trump-admin-bans-deepseek-from-federal-agencies/ | DHS ban consumer JP |
| 🇯🇵 | Crystal Method | https://crystal-method.com/blog/us-bans-deepseek-japan-enterprise-risk/ | 3-layer Japan risk |
| 🇯🇵 | AI CBA Games | https://ai.cbagames.jp/2026/10/21/deepseek-us-federal-ban-japan/ | Japan enterprise impact |
| 🇯🇵 | Gadget Otaku | https://gadget-otaku.com/2026/10/20/us-federal-agencies-ban-deepseek-ai/ | JP consumer coverage |
| 🇯🇵 | Bloomberg JP | https://www.bloomberg.com/jp/news/articles/2026-10-21/TN7J12KJH6V500 | DeepInfer lower costs JP |
| 🇯🇵 | AI-Souken | https://www.ai-souken.com/article/chinese-ai-model-overview | Chinese AI guide JP |
| 🇯🇵 | Singularity Society | https://singularitysociety.org/articles/tech-blog/2026-10-01-deepseek-qwen-chinese-ai-reality/ | JP 3 collapsed assumptions |
| 🇯🇵 | LabMemo | https://labmemo.com/llm-llama-deepseek-qwen-mistral-gemma-2026/ | JP LLM comparison 2026 |
| 🇨🇳 | Juejin DeepInfer | https://juejin.cn/post/7698932135780991039 | 1.55T tok/day |
| 🇨🇳 | Juejin DHS ban | https://juejin.cn/post/7698331749005639723 | "test just begun" |
| 🇨🇳 | Juejin Oct 20 daily | https://juejin.cn/post/7698629823459786761 | Oct 20 AI news roundup |
| 🇨🇳 | CSDN DeepSeek | https://deepseek.csdn.net/6a26115c662f9a54cb7b1d64.html | 5 Chinese open-source models |
| 🇨🇳 | Guancha | https://www.guancha.cn/CaiJing/2026_10_22_905376.shtml | DeepSeek "true OpenAI" |
| 🇨🇳 | China.com | https://news.china.com/socialgd/10000169/20261023/49812588.html | Open-source wins global praise |
| 🇨🇳 | Sohu | https://m.sohu.com/a/1090953467_122033970/ | DeepSeek core tech open-sourced |
| 🇨🇳 | smzdm Sina/Weibo | https://www.sina.cn/weibo/detail/5356407437656966.html | AI ban: open-source not restricted |
| 🇨🇳 | Sina Finance (approval) | https://finance.sina.cn/2026-10-23/detail-iniwcnvc5905718.d.html | DeepSeek+MiniMax approval |
| 🇨🇳 | Sina Finance (Yuantan) | https://finance.sina.com.cn/jjxw/2026-10-23/doc-iniweiyu8031101.shtml | Not a policy reversal |
| 🇨🇳 | Guangming | https://politics.gmw.cn/2026-10/23/content_39062802.htm | Yuantan Tian |
| 🇨🇳 | 21Jingji (new battlefield) | https://www.21jingji.com/article/20261019/herald/327e351994ba49a91d29ba8fc438a987.html | New battlefield CN AI |
| 🇨🇳 | 21Jingji (Yuantan) | https://www.21jingji.com/article/20261023/herald/cbeccbd50748efda57788d0dffb53af2.html | Routine regulatory work |
| 🇨🇳 | VOA Chinese | https://www.voachinese.com/a/dhs-banning-chinese-ai-deepseek-from-government-agency-it-systems-20261019/8212963.html | DHS ban CN audience |
| 🇨🇳 | Bannedbook (approval) | https://www.bannedbook.org/bnews/itnews/20261023/2372850.html | DeepSeek+MiniMax completed |
| 🇨🇳 | Bannedbook (DeepInfer) | https://www.bannedbook.org/bnews/itnews/20261020/2371967.html | DeepInfer |
| 🇨🇳 | Huxiu | https://www.huxiu.com/article/4899241.html | DHS FASCSA legal analysis |
| 🇨🇳 | stdaily | https://www.stdaily.com/web/gdxw/2026-10/21/content_600125.html | State perspective on DHS ban |
| 🇨🇳 | Zhihu (model tracker) | https://zhuanlan.zhihu.com/p/670574382 | CN model landscape Oct 17 |
| 🇨🇳 | Zhihu (TOP10) | https://zhuanlan.zhihu.com/p/2009705203163752429 | 2026 open-source TOP10 |
| 🇨🇳 | Qiniu | https://news.qiniu.com/archives/1791947058402 | October models overview |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2657621 | 15-model comparison |
| 🇨🇳 | smzdm | https://post.smzdm.com/p/agg5v9e3/ | Why DeepSeek is true OpenAI |
| 🇨🇳 | Linux.do (Index-Translate) | https://linux.do/t/topic/2974061 | Bilibili Index-Translate CN |
| 🇨🇳 | fcgvisa AI观察 | https://bbs.fcgvisa.com/t/ai-10-20-deepseek/62985 | AI observation Oct 20 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 (not queried)
├─ 🔵 X: 0 (not queried)
├─ 🔴 YouTube: 0 (not queried)
├─ 🟢 HN: 2 threads │ DeepInfer (15K+ stars); MiniMax M3.1 Flash weights (license discussion)
├─ 🟣 TikTok: 0 (not queried)
├─ 🩷 Instagram: 0 (not queried)
├─ 🦋 Bluesky: 0 (bsky=OK; no content extracted)
├─ 📊 Polymarket: 1 market │ $90,846+ volume │ ~18-19% Yes
├─ 🌐 Web: 80+ pages │ 🇯🇵 12 │ 🇨🇳 24
└─ 🗣️ Top voices: CCTV-Yuyuantantian (DeepSeek+MiniMax approval) │ DeepSeek/Juejin CN (DeepInfer viral) │ MiniMax/Together AI (M3.1 Flash weights) │ Bruegel (EU analysis) │ Crystal Method JP (3-layer risk) │ Moonshot (K3.1 teaser)
```

---

## Out of Scope but Notable

- **Meta Muse Wonder (Oct 12): First Meta closed frontier model** — $4/$20 per 1M tokens; breaks Meta's open-weight-only pattern at frontier. Would fit a `frontier-labs` or `us-ai-strategy` topic. (Per local-ai-zone.github.io)
- **GPT-6.1 Astra cancelled (WSJ):** OpenAI cancelled GPT-6.1 Astra after internal safety tests — notable precedent for self-imposed safety hold on a flagship model. Fits `ai-safety` or `frontier-labs` topics. (Per local-ai-zone.github.io)
- **Claude Haiku 5.5 (Oct 7):** "75-90% cheaper than Haiku 4.5"; 1M context; $0.10/$0.50 per 1M — relevant to cost competition dynamics but excluded per EXCLUDE rule (US frontier lab product, not driving open-source or geopolitical shift directly).

---

## Key Quotes

> "DeepSeek才是真正的OpenAI" ("DeepSeek is the true OpenAI") — viral phrase across Guancha, China.com, Sohu, Sina Oct 22-23, framing Apache 2.0 production inference as a global rebuttal to US restrictions ([Guancha](https://www.guancha.cn/CaiJing/2026_10_22_905376.shtml)) 🇨🇳

> "A real open-weights release, and it is not an open-source one." — OrcaRouter on MiniMax M3.1 Flash community license ($20M threshold), distinguishing it from MIT-licensed DeepSeek ([link](https://www.orcarouter.ai/blog/minimax-m3-1-flash-open-weights)) 🌐

> "DeepSeek和MiniMax已经顺利履行登记手续，并完成开源和海外授权使用" ("DeepSeek and MiniMax have successfully completed registration procedures and finished open-source and overseas authorization") — Yuyuantantian (CCTV-affiliated), Oct 23, first official state-media confirmation of compliance ([Sina Finance](https://finance.sina.cn/2026-10-23/detail-iniwcnvc5905718.d.html)) 🇨🇳

> "核心资产不再'洗澡式出海'" ("Core assets will no longer go abroad through laundering methods") — Sina/Weibo analysis of China's 2026 AI ban: the era of routing core IP through overseas open-source entities is ending ([link](https://www.sina.cn/weibo/detail/5356407437656966.html)) 🇨🇳

> "V4-Proの出力価格はオフピークでも旧プロモーション価格比で約2.3倍の水準に上昇" ("Pricing jumped 2.3× even at off-peak rates in August 2026") — crystal-method.com, on business continuity risk for Japanese enterprises using Chinese AI cloud services ([link](https://crystal-method.com/blog/us-bans-deepseek-japan-enterprise-risk/)) 🇯🇵

> "MiniMax M3.1 Flash shows China's AI price race has no floor in sight." — The Decoder, framing the weights release as evidence of ongoing price/capability compression ([link](https://the-decoder.com/minimax-m3-1-flash-shows-chinas-ai-price-race-has-no-floor-in-sight/)) 🌐

> "国産AI出海の考験才刚刚开始" ("The test for Chinese AI going global has just begun") — Juejin, framing the DHS federal ban as the opening move of a longer competitive arc ([link](https://juejin.cn/post/7698331749005639723)) 🇨🇳

---

## Data Gaps

- **Reddit/X/Twitter/TikTok/Instagram:** Not queried; r/LocalLLaMA and X likely have significant discussion on MiniMax weights + Kimi K3.1 teaser
- **Bluesky:** bsky=OK per SOURCE HEALTH; no content extracted (login wall/topic search limitation)
- **/last30days skill:** Unavailable ("Unknown skill"); entire English social media sweep replaced by manual WebSearch + WebFetch
- **DuckDuckGo HTML (JP/CN):** CAPTCHA on both passes (consistent with all 2026 runs); compensated with native-language WebSearch
- **Zhihu direct:** HTTP 403 (consistent); key content reconstructed from search snippets
- **Juejin direct:** JavaScript-rendered pages return "Please wait..." (consistent with prior runs); content from search snippets
- **Bruegel, SCMP:** HTTP 403; key points reconstructed from search snippets
- **Chaitechjp Substack:** HTTP 403 (authentication wall); title/framing captured only
- **DeepSeek V4.1 Pro:** No new official information; stealth endpoint reports unverified
- **BenchLM Chinese models list:** Not directly refreshed today; prior data (K3 at 70.0) carried forward
- **Polymarket second market (best Chinese AI company):** Not re-verified today (last verified Sep 22: Alibaba 72%, Moonshot 25%)
- **Coverage estimate:** ~73% — strong on MiniMax weights, DeepSeek+MiniMax China approval (Oct 23 breaking), Kimi K3.1 teaser, BenchLM update, Tencent Hy Memory 2.0, Bilibili Index-Translate, JP enterprise risk analysis, Bruegel analysis; moderate on Qwen 4 status, GLM 5.5; weak on social platforms (no X/Reddit/Bluesky)
