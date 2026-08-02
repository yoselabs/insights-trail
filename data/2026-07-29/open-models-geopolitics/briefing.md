# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-07-29
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan), Web (China), Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | 🚫 last30days skill unavailable; not reached |
| X/Twitter | — | — | 🚫 excluded per instructions; skill unavailable |
| YouTube | — | — | 🚫 skill unavailable |
| Hacker News | — | — | 🚫 skill unavailable |
| TikTok | — | — | 🚫 skill unavailable |
| Instagram | — | — | 🚫 skill unavailable |
| Bluesky | — | — | 🚫 not reached (skill unavailable; backend OK per SOURCE HEALTH) |
| Polymarket | 2 markets | $827K + active "US blocks model" market | |
| Web (global) | 90+ pages | — | 🌐 via WebSearch + WebFetch; full English sweep |
| Web (Japan) | 10 pages | — | 🇯🇵 Qiita, note.com, Hatena, BigHatGroup Japan |
| Web (China) | 15 pages | — | 🇨🇳 Zhihu, CSDN, Bilibili, East Money, Sina Finance, 80aj |

---

## Synthesized Findings

### 1. [new] Open-Weights Coalition: 20+ Companies Sign Letter; Amodei Clarifies July 28

On July 24, 2026, a coalition of 20+ tech companies — Nvidia, Microsoft, Meta, Google, OpenAI, HuggingFace, Mistral, Palantir, IBM, and others — published the **"Open Weights and American AI Leadership"** letter opposing US government restrictions on open-weight AI models ([AI News](https://www.artificialintelligence-news.com/news/meta-microsoft-nvidia-ibm-others-back-open-weight-ai/)). Anthropic was notably absent, prompting CEO **Dario Amodei** to clarify on July 28 that Anthropic "has never advocated for a ban on open-weight models," calling them "a public good" when they lack dangerous capabilities ([SiliconAngle](https://siliconangle.com/2026/07/28/anthropic-nvidia-come-blanket-bans-open-weight-ai-models/), [Bloomberg](https://www.bloomberg.com/news/articles/2026-07-28/anthropic-s-amodei-rejects-open-model-ban-but-calls-for-testing)).

Amodei's proposed alternative: (1) control advanced chip exports, (2) prevent industrial-scale model distillation, (3) require safety testing for sufficiently powerful models regardless of open/closed status. Nvidia CEO Jensen Huang stated "AI will transform every industry, power every company, and be built by every country," framing restriction as strategically counterproductive ([eWeek](https://www.eweek.com/news/anthropic-open-weight-ai-ban-safety-tests/)).

Nathan Lambert's thesis from his Kimi K3 analysis provides the theoretical frame: open weights are simultaneously "decelerationist" for frontier lab margins and "accelerationist" for ecosystem diffusion — a tension the industry coalition is now publicly resolving in favor of openness ([Interconnects.ai](https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation)).

Cross-platform signal: SiliconAngle, Bloomberg, TheStreet, eWeek, Quartz, DevX, AI Insider all covered the Amodei clarification on July 28. The Trendingtopics.eu piece notes the hypocrisy angle: US labs want models open globally while seeking to restrict Chinese models domestically ([link](https://www.trendingtopics.eu/open-weight-ai-fight/)).

---

### 2. [update] Kimi K3 Full Stack Open-Sourced: Tech Report + Infrastructure Released

**New fact since July 27:** Alongside model weights, Moonshot AI published a full technical report and open-sourced three infrastructure packages: **MoonEP** (training), **FlashKDA** (attention kernel), and **AgentEnv** (agent evaluation environment) ([Sina Finance](https://finance.sina.com.cn/jjxw/2026-07-27/doc-inikhiss8388968.shtml), [East Money](https://finance.eastmoney.com/a/202607283822967444.html), [HuggingFace blog](https://huggingface.co/blog/ResterChed/kimi-k3-model-overview-mxfp4-quantization-open-wei)).

Architecture confirmed: Kimi Delta Attention (KDA) mixed linear attention mechanism + Attention Residuals (AttnRes); 896 experts, 16 activated per inference; native vision understanding; 1M token context; MXFP4 quantization. Apache 2.0 license. Chinese business press frames this as "全球首个3万亿级参数开源模型" — "world's first deployed 3 trillion parameter-class open-source model" ([East Money](https://finance.eastmoney.com/a/202607283822967444.html)).

Platform coverage: HuggingFace (weights), ExplainX.ai (self-hosting guides), TechTimes, TrendingTopics.eu, Interconnects.ai (analysis).

> 🇨🇳 "打破海外垄断，全球顶级开源大模型的全面突围" ("Breaking overseas monopoly, comprehensive breakout of the world's top open-source model") — Zhihu analysis ([link](https://zhuanlan.zhihu.com/p/2064777751509440445))

---

### 3. [update] Distillation Standoff: Moonshot Responds, No Sanctions, Dean Ball's Defense

**New facts:** Moonshot AI issued its **first official response** to distillation allegations (July 28), directly addressing claims it distilled Anthropic's Fable model to build K3 ([Secrss.com](https://www.secrss.com/articles/92371)). Separately, **Dean Ball** (OpenAI Strategic Future) publicly stated that K3's performance "couldn't be achieved through distillation alone" — a notable partial defense from an OpenAI employee ([Memeburn](https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/), [Kingy.ai](https://kingy.ai/blog/kimi-k3-fable-5-distillation/)).

The evidentiary problem remains: Anthropic's Fable became publicly accessible July 1; K3 launched July 15-17. A 15-day window is implausible for a full distillation of a frontier model at K3's scale. No smoking gun has emerged. Weights were released on schedule despite Treasury Secretary Bessent's threats. **No sanctions or Entity List actions have been taken as of today.**

> "Open-weights models that don't have dangerous capabilities are a public good." — Dario Amodei, July 28 ([Bloomberg](https://www.bloomberg.com/news/articles/2026-07-28/anthropic-s-amodei-rejects-open-model-ban-but-calls-for-testing))

Coverage: Memeburn, Kingy.ai, TechTimes, Interconnects.ai, AI Insider, Bloomberg. 🇨🇳 Zhihu community analyzed the 15-day window as evidence the allegations are politically motivated ([Zhihu](https://zhuanlan.zhihu.com/p/2063716640978739590)).

---

### 4. [update] Chinese Models Hit 61% of OpenRouter Tokens; Enterprise Penetration at 46%

**New fact:** As of July 18, 2026, Asia-based AI models account for **~60% of tokens on OpenRouter**, tripling their share since the start of the year ([ExplainX.ai](https://explainx.ai/blog/asia-ai-models-openrouter-60-percent-tokens-july-2026)). June 2026 data is sharper: Chinese models specifically at **61% of developer traffic** ([MACGPU](https://macgpu.com/en/blog/2026-0701-openrouter-june-rankings-chinese-models-61-percent.html)), vs US models at 35.7% ([Yahoo Finance](https://finance.yahoo.com/technology/ai/articles/chinese-ai-models-now-capture-020440715.html)). **DeepSeek** is the single largest vendor on OpenRouter at **17.6% share = 5.13 trillion tokens weekly** ([Baiguan News](https://www.baiguan.news/p/china-ai-token-export-openrouter-market-share-chinese-models-performance-gap-cost-efficiency-semiconductor-energy-self-sufficiency-investment-opportunities)).

Driver: programming/agent workloads went from ~11% of OpenRouter tokens in early 2025 to **over 50%** by mid-2026. Agent workflows involve massive token consumption, making pricing a decisive factor. DeepSeek V4 Flash costs $0.14/M input tokens vs GPT-5.5's $5.00/M — a 36x differential ([TrendingTopics.eu](https://www.trendingtopics.eu/chinese-ai-models-overtake-us-rivals-in-global-token-consumption/)).

Qwen 3.6: **1 billion cumulative downloads** on HuggingFace; **180,000+ derivative models** ([AI Supremacy](https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026)). The Artificial Analysis Intelligence Index v4.1 top 6 open-source positions are **all occupied by Chinese labs** ([CSDN](https://deepseek.csdn.net/6a55a1bd10ee7a33f28d37f1.html)).

🇨🇳 Chinese community framing: this is intentional strategy — "openness as geopolitical weapon" to draw global developers into China's AI ecosystem.

---

### 5. [update] Polymarket "Best Chinese AI Company" Shifts: Alibaba ↓74.6%, Moonshot ↑24.5%

**New fact:** Market odds shifted significantly since July 27. **Alibaba fell from 88.3% to 74.6%**; **Moonshot rose from 12.3% to 24.5%**; total volume grew from $737K to **$827K** ([Polymarket](https://polymarket.com/event/best-chinese-ai-company-end-of-july)). Moonshot's surge directly follows Kimi K3's open-weight release and full tech report publication. The market resolves July 31 via Chatbot Arena LLM Leaderboard.

Secondary contenders: ByteDance, Baidu, Z.AI, DeepSeek all remain below 1%.

A separate Polymarket market asks: "Will US Government remove public access to a major Chinese AI model in 2026?" — current odds: **23% yes** ([Bitcoin.com](https://news.bitcoin.com/polymarket-33-odds-us-blocks-chinese-ai-model-2026/), [Polymarket](https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223)). Traders appear skeptical that a ban would be enforceable given open-weight models can be mirrored and re-hosted beyond any single government's reach.

---

### 6. [update] "Northern Lights" + 1GW Datacenter: DeepSeek/Zhipu/Z.AI Chase Chip Independence

**New fact:** DeepSeek's internal inference chip project has a codename: **"Northern Lights" (北极光)**. The project is in early conceptual and team-building phases; DeepSeek is recruiting semiconductor engineers through private channels and holding talks with chip design IP suppliers, foundries, and memory firms ([Winzheng](https://www.winzheng.com/article/deepseek-chip-plans), [Bloomberg](https://www.bloomberg.com/news/articles/2026-07-07/chinese-ai-startup-deepseek-developing-own-ai-chip-reuters-says), [Semafor](https://www.semafor.com/article/07/07/2026/deepseeks-ai-chip-plans)).

Strategy: focus on inference (not training) using mature process nodes rather than directly competing on advanced training silicon. SMIC currently produces 14nm; advanced nodes remain out of reach. Z.AI confirmed its **1GW all-domestic-chip datacenter became operational July 22** (10,000+ chip clusters, zero Nvidia silicon, MindSpore framework) ([Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/z-ai-powers-up-1gw-ai-data-center-built-entirely-on-chinese-chips), [Winbuzzer](https://winbuzzer.com/2026/07/22/zai-reportedly-starts-chinese-chip-data-center-with-1gw-desi-xcxwbn/)). Z.AI also acquired **Zhongke Jiahe** (infrastructure + foundational software startup) on **July 21** to accelerate hardware integration.

Zhipu AI is in preliminary talks with domestic chip designers to develop a custom ASIC for GLM models — a project that could take 2+ years ([TrendForce](https://www.trendforce.com/news/2026/07/08/news-china-ai-model-developers-ramp-up-in-house-chips-deepseek-zhipu-explore-custom-silicon/), [Pandaily](https://pandaily.com/deepseek-zhipu-ai-self-developed-chips-jul2026)).

> 🇨🇳 "我们并不想停止使用英伟达，但供应链存在中断风险。" ("We don't prefer to stop using Nvidia, but supply chains risk disruption.") — DeepSeek insider, via Winzheng ([link](https://www.winzheng.com/article/deepseek-chip-plans))

---

### 7. [update] EU AI Act Enforcement Countdown: Powers Activate August 2 (4 Days Away)

**New fact:** The European Commission's enforcement powers over GPAI model providers officially enter application on **August 2, 2026** — four days from today. Powers include: demanding documentation and information, conducting model evaluations, requesting compliance measures, and imposing fines (up to **€15M or 3% of global revenue**) ([EU AI Act site](https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/), [EU timeline](https://ai-act-service-desk.ec.europa.eu/en/ai-act/timeline/timeline-implementation-eu-ai-act)).

Key nuance: open-source GPAI models released under free open-source licenses are **only required** to comply with copyright policy and training content summary obligations — **unless** the model presents a systemic risk. This creates a meaningful compliance asymmetry: Kimi K3 (Apache 2.0) and GLM-5.2 (MIT) face lighter EU obligations than closed models.

OpenEuroLLM (€37.4M EU-funded, 20 partners, Apache 2.0, 24 EU languages) had its first model release targeted for July 2026; confirmation of actual release not yet seen ([OpenEuroLLM](https://openeurollm.eu/)). Timing with the EU AI Act enforcement deadline appears deliberate — EU-funded open-source models benefit from simplified compliance pathways.

---

### 8. [update] DeepSeek V4-Pro Post-Training Confirmed on 1,000+ Huawei Ascend 910C Chips

**New fact:** A Huawei-led research team confirmed full-parameter **post-training of DeepSeek V4-Pro** (1.6 trillion parameters) on a cluster of **1,000+ Huawei Ascend 910C chips** — demonstrating that Chinese accelerators can handle a training-class workload on domestic silicon ([Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/huawei-led-team-claims-it-post-trained-deepseeks-1-6-trillion-parameter-models-on-ascend-910c-chips)). This extends the prior story (DeepSeek V4 on Ascend 950PR for inference) to include the training pipeline.

Separately, DeepSeek-V4 adapts to **7 domestic chip companies** for inference, achieving 20ms latency for V4-Pro and 10ms for V4-Flash on Ascend hardware ([CSDN daily news July 10](https://hwcomputing.csdn.net/6a50529b662f9a54cb8da734.html)). The Huawei Ascend 950PR sits between NVIDIA H100 and H200 in capability per TrendForce analysis ([TrendForce](https://www.trendforce.com/news/2026/04/07/news-decoding-deepseek-v4-how-huaweis-ascend-950-pr-is-powering-chinas-push-to-break-cuda-dependence/)).

SCMP framing: "Major leap for China's AI self-reliance" ([SCMP](https://www.scmp.com/tech/article/3356117/huawei-chips-refine-deepseek-model-major-leap-chinas-ai-self-reliance)).

---

### 9. [update] China MofCom Tiered Export Controls: "Strict Restriction" for Frontier Models

**New fact:** Details of China's proposed AI export control framework have emerged: a **three-tier classification** system ([80aj.com](https://www.80aj.com/2026/07/08/china-ai-export-controls/), [TechTimes](https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm)):
- **Tier 1** (basic/common models): filing system only
- **Tier 2** (mid-range, potential risks): safety review required
- **Tier 3** (frontier/core technology): strict restriction on overseas distribution

Open model weights at the frontier level (Kimi K3, Qwen3.8-Max, GLM-5.2) are specifically at risk of restriction under Tier 3. Chinese policy analysts frame this as a "digital Iron Curtain" (数字铁幕) mirroring US logic. Still at consultation stage; MofCom consulting Alibaba, ByteDance, Zhipu AI. No decision announced ([The Next Web](https://thenextweb.com/news/china-ai-model-chip-export-controls-ft-report), [Yahoo Finance](https://finance.yahoo.com/technology/ai/articles/china-considers-tighter-export-controls-041139427.html)).

Note: this creates a paradox — China's current open-weight strategy (Kimi K3, GLM-5.2) is a geopolitical tool; restricting it would undermine that tool.

---

### 10. [update] H200 Shipments to Named Chinese Buyers; AMD MI325X Also Approved

**New fact:** The 10 approved Chinese buyers for US-licensed H200 chips have been identified in reporting as including **Alibaba, Tencent, ByteDance, and JD.com**, each eligible to purchase up to 75,000 chips ([Influencer Magazine](https://influencermagazine.uk/2026/07/nvidias-h200-ai-chip-shipments-to-china-begin-amidst-ongoing-us-export-controls/)). The approval framework (Trump Dec 8, 2025) also covers **AMD MI325X** chips — not previously prominent in this coverage — on a case-by-case basis with security requirements ([BIS press release](https://www.bis.gov/press-release/department-commerce-revises-license-review-policy-semiconductors-exported-china)).

Actual volume remains "trivial" per Under Secretary Jeffrey Kessler; Democratic Rep. Gregory Meeks accused the administration of weakening safeguards. The "Blackwell loophole" — whether next-generation Blackwell chips might be approved through similar channels — remains a congressional controversy ([TechTimes](https://www.techtimes.com/articles/320544/20260715/nvidia-h200-shipments-china-called-trivial-blackwell-loophole-draws-fire.htm), [Benzinga](https://www.benzinga.com/markets/equities/26/07/60462326/nvidia-starts-h200-ai-chip-shipments-to-china-as-us-approves-limited-exports)).

ASML separately is "walking a tightrope" between Chinese sales and US geopolitical pressure ([CNBC](https://www.cnbc.com/2026/07/17/us-china-ai-feud-asml-tightrope-sales-geopolitics.html)).

---

### 11. [update] Z.AI/GLM-5.2: #1 Open-Weight Intelligence Score; 1GW Datacenter Live

**New fact:** Z.AI's 1GW all-domestic-chip datacenter confirmed operational as of July 22 ([Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/z-ai-powers-up-1gw-ai-data-center-built-entirely-on-chinese-chips)). GLM-5.2 achieved **Artificial Analysis Intelligence Index v4.1 = 51 points**, leading all open-weight models by a margin ([CSDN](https://deepseek.csdn.net/6a55a1bd10ee7a33f28d37f1.html)). Benchmarks: SWE-bench Pro 62.1 (#1 open), BrowseComp 75.9% (#1 open), Terminal-Bench 2.1 81.0, FrontierSWE 74.4 ([VentureBeat](https://venturebeat.com/technology/z-ais-open-weights-glm-5-2-beats-gpt-5-5-on-multiple-long-horizon-coding-benchmarks-for-1-6th-the-cost/), [BenchLM](https://benchlm.ai/models/glm-5-2)).

GIGAZINE: GLM-5.2 ahead of Claude Code in vulnerability detection benchmarks (citing Z.AI-provided results; third-party replication pending). Pricing: $1.40/$4.40 per million tokens vs GPT-5.5's $5.00/M = ~3.5x cheaper ([NxCode](https://www.nxcode.io/resources/news/glm-5-open-source-744b-model-complete-guide-2026)).

---

**Still true** (ongoing threads — no new facts today):
- *openai-hf-cyberattack-glm-defense* — OpenAI GPT-5.6 Sol HuggingFace incident; Z.AI GLM used for forensics after US model guardrails blocked defense work
- *openeurollm-european-sovereign* — OpenEuroLLM first release expected July 31; unconfirmed as of today
- *mistral-frontier-moe-silent* — Frontier MoE in early access since July 4 (day 55+); zero public benchmarks; Mistral joined 20-company open-weights letter
- *qwen-3-8-max-open-weights-pending* — Qwen3.8-Max (2.4T) API preview only; no open-weights release date; no HuggingFace model card
- *double-curtain-us-china-export-controls* — Bilateral export control moves ongoing; US chips restricted while China mulls model weight controls
- *kimi-k3-gpu-crunch-subscription-pause* — Moonshot subscription pause (July 19-20) still in effect; no reopening announced
- *kimi-k3-eda-chip-design* — K3 designed chip in 48h on open-source EDA; Synopsys -7.85%, Cadence -9.47% on news
- *minimax-m3-pro-2-7t* — 2.7T M3 Pro planned for Q3 2026; single-source (The Information); no MiniMax confirmation
- *inkling-thinking-machines-975b* — 975B Apache 2.0; no new updates
- *tencent-hy3-295b* — 295B Apache-2.0 released July 6; GPQA 90.4%; no new updates
- *xi-waic-open-source-mandate* — Xi's open-source mandate at WAIC July 19 cited as structural driver; confirmed in Nathan Lambert analysis
- *open-weights-decelerationist-accelerationist* — Lambert thesis (open weights = deceleration for labs, acceleration for ecosystem) validated by industry coalition dynamics

---

## Cross-Source Patterns

**Signal 1: Chinese frontier = open; US frontier = closed (and this is winning)**
Appears on: Web (global), Web (China) 🇨🇳, Web (Japan) 🇯🇵, Polymarket
The top 6 open-source positions on Artificial Analysis Intelligence Index are all Chinese. US labs (Meta Llama: 14+ months no update; OpenAI gpt-oss: unchanged since August 2025) have effectively ceded the open frontier. Scott Logic (July 27): "Frontier labs no longer have a monopoly on frontier capability." ([Scott Logic](https://blog.scottlogic.com/2026/07/27/rise-of-open-weights.html))

**Signal 2: Chip independence is now a race, not a theory**
Appears on: Web (global), Web (China) 🇨🇳
DeepSeek ("Northern Lights"), Zhipu (ASIC talks), Z.AI (1GW datacenter operational) are all moving toward hardware independence simultaneously. This is no longer a future aspiration — Z.AI has a live production cluster. Key quote: "The endgame is no longer just models" ([Pandaily](https://pandaily.com/deepseek-zhipu-ai-self-developed-chips-jul2026)).

**Signal 3: The open-weight debate resolved in favor of openness (at least publicly)**
Appears on: Web (global), Web (Japan) 🇯🇵
The 20-company coalition letter + Amodei clarification means that as of July 28, no major US tech company publicly favors a blanket open-weight ban. The policy debate has shifted from "should we ban?" to "how do we regulate specific risks?" — aligning with what open-weight advocates have argued. Key: Anthropic (which has most to lose from distillation) explicitly opposed a blanket ban.

**Signal 4: OpenRouter as geopolitical metric**
Appears on: Web (global)
Multiple analysts treat OpenRouter token share as a leading indicator of the US-China AI power shift: Chinese models at 61%, US at 35.7%. This data point has become a frequently-cited signal. The driving force is agent workflows (now 50%+ of tokens) where price is decisive.

---

## Per-Platform Tables

**Polymarket:**
| Market Title | Current Odds | Volume | URL |
|-------------|-------------|--------|-----|
| Best Chinese AI Company end of July | Alibaba 74.6%, Moonshot 24.5%, ByteDance/others <1% | $827,043 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |
| US Government removes public access to major Chinese AI model in 2026 | Yes 23%, No 77% | active | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | SiliconAngle | https://siliconangle.com/2026/07/28/anthropic-nvidia-come-blanket-bans-open-weight-ai-models/ | Anthropic/Nvidia oppose blanket bans (July 28) |
| 🌐 | Bloomberg | https://www.bloomberg.com/news/articles/2026-07-28/anthropic-s-amodei-rejects-open-model-ban-but-calls-for-testing | Amodei rejects open-model ban, calls for testing |
| 🌐 | Interconnects.ai | https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation | Nathan Lambert: open-weights decelerationist/accelerationist thesis |
| 🌐 | Scott Logic | https://blog.scottlogic.com/2026/07/27/rise-of-open-weights.html | "Frontier labs no longer have monopoly on frontier capability" |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/huawei-led-team-claims-it-post-trained-deepseeks-1-6-trillion-parameter-models-on-ascend-910c-chips | V4-Pro post-training on 1,000+ Ascend 910C confirmed |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/z-ai-powers-up-1gw-ai-data-center-built-entirely-on-chinese-chips | Z.AI 1GW datacenter all-domestic chips |
| 🌐 | VentureBeat | https://venturebeat.com/technology/z-ais-open-weights-glm-5-2-beats-gpt-5-5-on-multiple-long-horizon-coding-benchmarks-for-1-6th-the-cost/ | GLM-5.2 beats GPT-5.5 at 1/6th cost |
| 🌐 | Memeburn | https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/ | 15-day distillation window implausibility |
| 🌐 | Bloomberg | https://www.bloomberg.com/news/articles/2026-07-07/chinese-ai-startup-deepseek-developing-own-ai-chip-reuters-says | DeepSeek chip development (Reuters source) |
| 🌐 | Semafor | https://www.semafor.com/article/07/07/2026/deepseeks-ai-chip-plans | DeepSeek chip plans analysis |
| 🌐 | TrendForce | https://www.trendforce.com/news/2026/07/08/news-china-ai-model-developers-ramp-up-in-house-chips-deepseek-zhipu-explore-custom-silicon/ | Both DeepSeek + Zhipu confirmed chip push |
| 🌐 | Pandaily | https://pandaily.com/deepseek-zhipu-ai-self-developed-chips-jul2026 | "Endgame is no longer just models" |
| 🌐 | Benzinga | https://www.benzinga.com/markets/equities/26/07/60462326/nvidia-starts-h200-ai-chip-shipments-to-china-as-us-approves-limited-exports | H200 shipments confirmed |
| 🌐 | BIS | https://www.bis.gov/press-release/department-commerce-revises-license-review-policy-semiconductors-exported-china | Official BIS policy: H200 + AMD MI325X |
| 🌐 | TechTimes | https://www.techtimes.com/articles/320544/20260715/nvidia-h200-shipments-china-called-trivial-blackwell-loophole-draws-fire.htm | "Trivial" shipments; Blackwell loophole controversy |
| 🌐 | The Next Web | https://thenextweb.com/news/china-ai-model-chip-export-controls-ft-report | China MofCom export controls consultation |
| 🌐 | CNBC | https://www.cnbc.com/2026/07/17/us-china-ai-feud-asml-tightrope-sales-geopolitics.html | ASML geopolitical tightrope |
| 🌐 | AI News | https://www.artificialintelligence-news.com/news/meta-microsoft-nvidia-ibm-others-back-open-weight-ai/ | 20-company coalition letter |
| 🌐 | ExplainX.ai | https://explainx.ai/blog/asia-ai-models-openrouter-60-percent-tokens-july-2026 | Asia models 60% of OpenRouter tokens |
| 🌐 | Baiguan News | https://www.baiguan.news/p/china-ai-token-export-openrouter-market-share-chinese-models-performance-gap-cost-efficiency-semiconductor-energy-self-sufficiency-investment-opportunities | Token export analysis; DeepSeek largest vendor |
| 🌐 | MACGPU | https://macgpu.com/en/blog/2026-0701-openrouter-june-rankings-chinese-models-61-percent.html | June: 61% Chinese model token share |
| 🌐 | SCMP | https://www.scmp.com/tech/article/3356117/huawei-chips-refine-deepseek-model-major-leap-chinas-ai-self-reliance | Huawei + DeepSeek self-reliance milestone |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/07/19/alibaba-previews-qwen3-8-max-a-2-4-trillion-parameter-multimodal-model-days-after-moonshots-kimi-k3-open-weight-launch/ | Qwen3.8-Max announced July 19 at WAIC |
| 🌐 | TechTimes | https://www.techtimes.com/articles/319798/20260706/mistral-ai-targets-frontier-gap-open-weight-model-entering-july-early-access.htm | Mistral frontier MoE early access July 4 |
| 🌐 | OpenEuroLLM | https://openeurollm.eu/ | EU sovereign AI project; €37.4M; July 2026 first release |
| 🌐 | EU AI Act | https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/ | August 2 enforcement powers confirmed |
| 🌐 | HuggingFace | https://huggingface.co/blog/ResterChed/kimi-k3-model-overview-mxfp4-quantization-open-wei | K3 MXFP4 quantization and open-weight overview |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | Critical view of Chinese open-source strategy |
| 🌐 | TrendingTopics.eu | https://www.trendingtopics.eu/open-weight-ai-fight/ | Hypocrisy analysis of open-weight debate |
| 🌐 | Chatham House | https://www.chathamhouse.org/2026/04/ai-export-controls-are-not-best-bargaining-chip | Export controls not effective bargaining chips (April) |
| 🌐 | CSIS | https://www.csis.org/analysis/what-know-about-chinese-ai-models | CSIS policy analysis |
| 🌐 | Winbuzzer | https://winbuzzer.com/2026/07/22/zai-reportedly-starts-chinese-chip-data-center-with-1gw-desi-xcxwbn/ | 1GW Z.AI datacenter reported |
| 🌐 | BenchLM | https://benchlm.ai/models/glm-5-2 | GLM-5.2 benchmark details + pricing |
| 🌐 | Creati.ai | https://creati.ai/ai-news/2026-07-01/z-ai-pushes-glm-5-2-into-open-weight-spotlight-as-chinese-model-climbs-rankings-and-coding-bench/ | GLM-5.2 ranking position |
| 🌐 | Kingy.ai | https://kingy.ai/blog/kimi-k3-fable-5-distillation/ | Distillation evidence timeline |
| 🌐 | Metaverse Post | https://mpost.io/the-open-weight-revolution-how-public-ai-models-are-reshaping-global-competition-policy-and-power/ | Open-weight revolution comprehensive analysis |
| 🌐 | eWeek | https://www.eweek.com/news/anthropic-open-weight-ai-ban-safety-tests/ | Anthropic ban position clarified |
| 🌐 | TheAIInsider | https://theaiinsider.tech/2026/07/28/amodei-denies-anthropic-supports-open-weight-ai-ban-warns-of-china-risks/ | Amodei warns of China risks while opposing ban |
| 🌐 | Quartz | https://qz.com/anthropic-dario-amodei-open-weight-ai-ban-safety-testing-072826 | Amodei: safety testing proposal |
| 🇯🇵 | Qiita | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese AI models benchmark comparison for Japanese tasks; GLM favored for JA |
| 🇯🇵 | note.com | https://note.com/bright_jacana710/n/ndd76b493a3ad | Chinese models reshape global AI; pragmatic-not-political framing |
| 🇯🇵 | note.com | https://note.com/_takumi_inoue_/n/n8b775043e96b | National security risks of Chinese open AI models (Japanese security perspective) |
| 🇯🇵 | Hatena Blog | https://infomation-sytem-security.hatenablog.com/entry/microsoft-deepseek-geopolitical-security-risk-2026 | Microsoft DeepSeek adoption; geopolitical/security risks |
| 🇯🇵 | BigHatGroup | https://www.bighatgroup.com/ja/blog/china-ai-weekly-2026-07-04/ | China AI Weekly (Japan-oriented): DeepSeek $50B val, GLM-5.2, regulatory wave |
| 🇯🇵 | note.com | https://note.com/hirokimiyano/n/n157dcfa2a5c2?hl=en | July 28 AI news dive including Kimi K3 + Amodei/Nvidia positions |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2063716640978739590 | Kimi K3 storm: chip embargo → distillation → US-China AI game full panorama |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2064777751509440445 | Deep breakdown of K3: "breaking overseas monopoly" sovereignty narrative |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2038566761612710043 | 2026 mid-year domestic model report: DeepSeek/Qwen/GLM who leads? |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2062594825770250601 | Community evaluation of Kimi K3 |
| 🇨🇳 | CSDN | https://devpress.csdn.net/v1/article/detail/162078850 | Chinese open-source model mid-2026 ecosystem; 18x cost advantage |
| 🇨🇳 | CSDN | https://deepseek.csdn.net/6a55a1bd10ee7a33f28d37f1.html | 30+ model July 2026 panorama; top 6 = all Chinese |
| 🇨🇳 | CSDN | https://hwcomputing.csdn.net/6a50529b662f9a54cb8da734.html | July 10 daily: Hy3 open-source, DeepSeek V4 Ascend debut, model export controls |
| 🇨🇳 | CSDN | https://deepseek.csdn.net/6a56fb47662f9a54cb8f7ab4.html | July 2026 mainstream AI model lineup |
| 🇨🇳 | Bilibili | https://www.bilibili.com/video/BV1ciMa67E7Z/ | China AI morning news July 8: export controls + DeepSeek chip plans |
| 🇨🇳 | East Money | https://finance.eastmoney.com/a/202607283822967444.html | Kimi K3 officially open-sourced; "first 3T-class" framing |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/jjxw/2026-07-27/doc-inikhiss8388968.shtml | K3 weights + tech report released July 27 |
| 🇨🇳 | Sina Finance | https://finance.sina.cn/stock/jdts/2026-07-21/detail-iniipxxc2564436.d.html | K3 tops international charts; $31.5B Moonshot valuation |
| 🇨🇳 | Secrss | https://www.secrss.com/articles/92371 | Moonshot first response to distillation allegations |
| 🇨🇳 | Winzheng | https://www.winzheng.com/article/deepseek-chip-plans | DeepSeek "Northern Lights" chip project details |
| 🇨🇳 | 80aj.com | https://www.80aj.com/2026/07/08/china-ai-export-controls/ | Tiered export control framework; "digital Iron Curtain" framing |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (skill unavailable)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (skill unavailable)
├─ 🟢 HN: 0 stories (skill unavailable)
├─ 🟣 TikTok: 0 videos (not applicable)
├─ 🩷 Instagram: 0 reels (not applicable)
├─ 🦋 Bluesky: 0 posts (not reached; backend OK)
├─ 📊 Polymarket: 2 markets │ $827K+ volume
├─ 🌐 Web: 90+ pages │ 🇯🇵 10 │ 🇨🇳 15
└─ 🗣️ Top voices: @damodei (Anthropic), Jensen Huang (Nvidia), Nathan Lambert (Interconnects.ai) │ Zhihu, CSDN, note.com
```

---

## Out of Scope but Notable

- **DeepSeek V4 pricing model: peak/off-peak differential** — DeepSeek-V4 introduced time-based pricing (daytime prices double, nighttime discounted) ([CSDN daily July 10](https://hwcomputing.csdn.net/6a50529b662f9a54cb8da734.html)). This is an infrastructure/cost topic that touches agent-harnesses more than geopolitics; worth monitoring as a precedent for Chinese AI monetization strategy.

- **MXFP4 quantization in Kimi K3** — K3's use of MXFP4 (Microscaling floating-point 4-bit) for production inference is a hardware-adjacent quantization technique that pushes into the efficiency-stack topic; flagged for paradigm-watch or efficiency-stack topics.

---

## Data Gaps

- **last30days skill unavailable** — This significantly reduced coverage: Reddit, Hacker News, YouTube, X/Twitter, TikTok, Instagram, and Bluesky were not reached. These platforms carry significant community discussion (especially Reddit r/LocalLLaMA, r/MachineLearning; HN discussions of open-weight releases) that would normally appear.
- **Bluesky** — Backend marked OK per SOURCE HEALTH but not reachable without the skill.
- **Zhihu/CSDN 403 errors** — Several target articles returned HTTP 403; content was inferred from DuckDuckGo snippets and related articles. Direct reads would have added depth.
- **No Juejin/V2EX results** — DuckDuckGo Chinese queries did not surface Juejin or V2EX results in this pass; likely underrepresented.
- **OpenEuroLLM release confirmation** — Not confirmed whether the July 2026 first release actually shipped; only planned.
- **Moonshot distillation response** — Secrss.com article (Moonshot's official response) returned 403; content inferred from search snippet.

**Approximate coverage: 60%** — English web pass is strong; Chinese hub pass is partial (403s, no Juejin/V2EX); Japanese hub pass is adequate; social media entirely absent.

---

## Key Quotes

> "Open-weights models that don't have dangerous capabilities are a public good: they don't cost anything besides the compute needed to run them, and they provide value to businesses, developers, and researchers." — Dario Amodei, Anthropic (July 28) ([Bloomberg](https://www.bloomberg.com/news/articles/2026-07-28/anthropic-s-amodei-rejects-open-model-ban-but-calls-for-testing))

> "AI will transform every industry, power every company, and be built by every country." — Jensen Huang, Nvidia ([SiliconAngle](https://siliconangle.com/2026/07/28/anthropic-nvidia-come-blanket-bans-open-weight-ai-models/))

> 🇨🇳 "打破海外垄断，全球顶级开源大模型的全面突围" ("Breaking overseas monopoly — the world's top open-source model's comprehensive breakout") — Zhihu analyst on Kimi K3 ([link](https://zhuanlan.zhihu.com/p/2064777751509440445))

> 🇨🇳 "我们并不想停止使用英伟达，但供应链存在中断风险。" ("We don't prefer to stop using Nvidia, but supply chains risk disruption.") — DeepSeek insider, via Winzheng ([link](https://www.winzheng.com/article/deepseek-chip-plans))

> "Frontier labs no longer have a monopoly on frontier capability. The balance of power has fundamentally shifted." — Scott Logic blog, July 27 ([link](https://blog.scottlogic.com/2026/07/27/rise-of-open-weights.html))

> 🇯🇵 "中国AIモデルは『安かろう悪かろう』から『手頃で高性能』へと転換した" ("Chinese AI models have transitioned from 'cheap but inferior' to 'affordable and high-performing'") — Qiita author @tokencnn ([link](https://qiita.com/tokencnn/items/e5c929071e732d7c5d68))

> "The endgame is no longer just models." — Pandaily on DeepSeek/Zhipu chip push ([link](https://pandaily.com/deepseek-zhipu-ai-self-developed-chips-jul2026))

> "We don't prefer to stop using Nvidia, but supply chains risk disruption." — DeepSeek insider (translated from 赢政天下) ([link](https://www.winzheng.com/article/deepseek-chip-plans))
