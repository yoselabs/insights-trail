# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-07
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan 🇯🇵), Web (China 🇨🇳), Polymarket, Bluesky (checked, 0 on-topic posts)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 80+ pages | — | 🌐 via WebSearch + WebFetch; blogs, news, analysis, official docs |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita ×3, Zenn ×1, note.com ×1, MIT Tech Review JP ×1, AlphaMatch JP ×1 |
| Web (China) | 9+ pages | — | 🇨🇳 CSDN ×4, Zhihu ×2 (snippet-only; 403), Ofox ZH ×1, Cnblogs ×1, TAIM.plus ×1 |
| Polymarket | 3 markets | $1.46M total volume | 2 active (Aug + US-ban), 1 resolved (July) |
| Bluesky | 0 posts | — | 🦋 Source health OK; no on-topic 2026 posts indexed |
| Reddit | — | — | Domain blocked by API |
| X/Twitter | — | — | Excluded per spec |
| YouTube | — | — | Not retrieved in free-tool pass |
| Hacker News | 1 thread | — | Via search link; content partial |

---

## Synthesized Findings

### 1. [new] Polymarket: Alibaba Leads "Best Chinese AI Company End of August" at 88.5% 🌐

**New thread.** A new recurring market launched for August:
- **Alibaba 88.5%** ($84.88K), Z.ai 6.5%, Moonshot 4%, DeepSeek 2.3%, all others <1%
- **Total volume $386.69K**; $42.06K liquidity; $41.69K open interest
- **Resolution:** highest arena.ai Text Arena rank among Chinese companies by Aug 31, 12:00 PM ET
- Alibaba surge from the July resolution (100% win) plus Qwen3.8-Max launch Aug 3 likely driving market confidence
- Companion market: "US Government removes public access to a major Chinese AI model in 2026" — **13% Yes**, $36,819 volume; hard-ban considered unlikely (open weights legally/technically difficult to claw back; First Amendment considerations)

**Sources:**
- https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/
- https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223
- https://polymarket.com/event/best-chinese-ai-company-end-of-july

*Appeared on: Polymarket 🌐*

---

### 2. [new] Inkling-Small: Thinking Machines Lab's Smaller Model Beats Its Bigger Sibling 🌐

**New thread.** Mira Murati's Thinking Machines Lab released Inkling-Small on August 2, 2026:
- **276B total / 12B active** (vs Inkling: 975B/41B); Apache 2.0; 1M context; text + image + audio
- **Hardware:** 180GB VRAM NVFP4 — fits a single NVIDIA B300 (vs 600GB for full BF16)
- **Beats Inkling on reasoning/coding:**
  - Humanity's Last Exam: **31.6% vs 29.7%**
  - SWE-bench Verified: **80.2% vs 77.6%**
  - ARC-AGI-2: **40.1% vs 36.5%**
- **Regression on factual recall:** SimpleQA 20.6% vs 43.9%; Tau3-Banking 15.5% vs 23.7%
- Demonstrates MoE student-surpasses-teacher dynamic: smaller active params, better RL post-training

**Why it matters:** At SWE-bench 80.2%, Inkling-Small ties or beats most Chinese open-weight models (GLM-5.2 at 84.2% remains ahead; Kimi K2.6 at 80.2% ties). A non-Chinese non-US lab with Apache 2.0 licensing at this level disrupts the binary Chinese-vs-US framing.

**Sources:**
- https://www.marktechpost.com/2026/08/02/thinking-machines-lab-releases-inkling-small-276b-open-weights-multimodal-moe-model/
- https://thinkingmachines.ai/news/introducing-inkling/
- https://aitoolsreview.co.uk/insights/thinking-machines-inkling

*Appeared on: Web (global) 🌐*

---

### 3. [new] Mistral Shieldstral: Safety Classifier Released; Frontier MoE Still Dark (Day ~64) 🌐

**New thread.** Mistral released Shieldstral on August 4, 2026:
- **3B open-weights multimodal safety classifier**; Apache 2.0
- Backbone: Ministral-3-3B-Base-2512 + Pixtral vision encoder; trained on **54.1M contrastive pairs** across 12 languages
- Policy-adaptive: accepts custom plain-language policies at inference time (no retraining needed)
- Runs on **single 16GB GPU**; matches models up to 7× its size
- Sources: https://mistral.ai/news/shieldstral/ | https://aiweekly.co/alerts/mistral-open-sources-shieldstral-a-3b-multimodal-safety-guard | https://the-decoder.com/mistrals-open-model-shieldstral-matches-much-larger-safety-models/

**Frontier MoE status:** Shieldstral is NOT the "fat but sparse" frontier MoE. That model remains in partner early access since ~June 4 — **now day ~64** with zero public benchmarks. Partners: Ericsson, ESA, Reply, Singapore DSO/HTX, ASML. Mistral valuation ~$23B.
- Source: https://www.techtimes.com/articles/319798/20260706/mistral-ai-targets-frontier-gap-open-weight-model-entering-july-early-access.htm
- Source: https://tech-insider.org/au/mistral-robotics-model-valuation-2026/

*Appeared on: Web (global) 🌐*

---

### 4. [update] DeepSeek: V4 Flash Open-Sourced MIT; Harness Beta Recruiting This Week 🌐 🇨🇳

**New facts since Aug 5:**
1. **V4 Flash open-sourced MIT** (July 31): 284B/13B active, 1M context, 384K max output, configurable `reasoning_effort` (low/high/max), speculative decoding (vLLM/SGLang), 90% KV cache reduction. Multi-stage post-training (RL + SFT + teacher distillation).
2. **Harness internal beta:** Cui Tianyi (harness team lead) posted recruitment for beta ~Aug 1-3; beta launch "this week" (week of Aug 3-7); small invitation groups. DeepSeek describes Harness as "1/105th the price" of Claude Code.
3. **V4 Pro GA:** Still preview as of Aug 7; Aug 10-20 window unconfirmed. Harness expected before V4 Pro GA.
4. **Ascend 950DT:** Deploying to Huawei Cloud August as planned; 144GB HBM, 4TB/s memory bandwidth.

**Sources:**
- https://www.opensourceforu.com/2026/08/deepseek-open-sources-v4-flash/
- https://www.scmp.com/tech/tech-trends/article/3362792/chinas-deepseek-beefs-agentic-ai-harness-tests-v4-model-jolts-silicon-valley
- https://blog.4sapi.com/blog/deepseek-harness-ai-agent-framework
- https://finance.biggo.com/news/092d974d-a3fa-4485-8056-49c5b5e8dba9
- https://deepseekv4pro.com/news/deepseek-v4-ga-mid-august-release-window-harness-beta
- https://www.trendforce.com/news/2026/06/08/news-huawei-brings-forward-ascend-950dt-deployment-to-august-deepseek-v4-2-seen-as-potential-early-adopter/

*Appeared on: Web (global) 🌐, Web (China 🇨🇳 — SCMP, CSDN)*

---

### 5. [update] NVIDIA China Effectively Foreclosed: $4.5B Write-Off, Zero H200 Shipments 🌐

**New facts since Aug 5:**
- NVIDIA recognized **$4.5B in charges** tied to export restrictions in Q1 FY2026 (quarter ended January 2026)
- **Zero H200 shipments** to China vs $4.6B in the prior year period
- CFO Colette Kress: company "has yet to generate any revenue from H200 sales to China"
- Commerce Dept told Congress: "H200 shipments have been very few despite roughly $10B in approved licenses"
- NVIDIA: cannot create "a competitive product for China's data center market that receives approval from both USG and Chinese government"
- Huawei counter: predicts **60% revenue boost** from AI chip sales in 2026; $12B forecast

**Sources:**
- https://beam.ai/agentic-insights/nvidia-china-market-share-zero-huawei-12-billion
- https://techjournal.org/us-imposes-25-tariff-on-nvidia-h200-ai-chips-bound-for-china
- https://www.datacenterdynamics.com/en/news/huawei-predicts-60-revenue-boost-from-sale-of-its-ai-chips-in-2026/
- https://www.brookings.edu/articles/ball-games-over-the-us-is-out-of-the-ai-chip-market-in-china/

*Appeared on: Web (global) 🌐*

---

### 6. [update] OpenEuroLLM: Flagship Target Slips to Fall 2026; 10M GPU Hours Secured 🌐

**New facts since Aug 5:**
- **July 2026 flagship deadline missed** (confirmed as of Aug 7); **new target: "fall 2026"**
- Progress: **10M+ GPU hours** secured on EuroHPC systems; 8B model in progress; larger model on strategic compute allocation
- Reference models published; no flagship; €20.6M EU funding / €37.4M total; 20 orgs; led by Charles University + Silo AI
- Covers all EU official languages; EU AI Act active without EU competitive open-weight alternative

**Sources:**
- https://openeurollm.eu/
- https://www.ai.se/en/news/openeurollm-takes-next-step-european-ai-sovereignty
- https://futurium.ec.europa.eu/en/apply-ai-alliance/community-content/sovereign-infrastructure-sovereign-capability-europe-open-weight-ai-race
- https://mrkt30.com/european-llms-2026-map/

*Appeared on: Web (global) 🌐*

---

**Still true** (ongoing threads — no new facts today):

- **minimax-h3-geo-license-restriction**: H3 (33B) weights still exclude US/EU/UK/Korea; Hollywood lawsuit detail added (Disney/Universal/Warner Bros., Sept 2025; motion to dismiss denied May 26, 2026); US special-license applications accepted. [https://www.kucoin.com/news/flash/minimax-restricts-h3-license-in-u-s-eu-uk-and-south-korea-due-to-hollywood-copyright-lawsuit]
- **deepseek-autonomous-cyberattack-hermes**: No new reports since Aug 3 Unit 42 disclosure; Knaithe/KnYuan + Telegram C2 + 460 targeted / 14 compromised still the definitive account. [https://www.bleepingcomputer.com/news/security/hacker-uses-deepseek-ai-to-autonomously-attack-vulnerable-servers/]
- **qwen-3-8-max-open-weights-pending**: Still not on HuggingFace/ModelScope as of Aug 7; week of Aug 10 expected; license and geographic restrictions still unconfirmed. [https://www.explainx.ai/blog/qwen3-8-max-coding-cowork-august-2026]
- **industry-coalition-open-weights-letter**: 270+ orgs; OpenAI within 24h; Amazon/Anthropic remain out; hard measures (ban, Entity List) at 13% Polymarket probability. [https://complexdiscovery.com/open-weights-open-questions-the-letter-that-redrew-the-ai-policy-fight/]
- **kimi-k3-gpu-crunch-subscription-pause**: Moonshot $35B→$50B pre-IPO path; HK IPO within 6 months; ARR $300M; distillation denied. [https://memeburn.com/moonshot-ai-valuation-hits-35b/]
- **eu-ai-act-august-enforcement**: Active since Aug 2; Article 50 grace period — machine-readable marking delayed to Dec 2 (tooling not ready); 180+ orgs signed GPAI Code of Practice. [https://accuroai.co/blog/eu-ai-act-what-actually-applies-august-2-2026]
- **ai-manifesto-war-pacing-frontier**: Three competing frameworks (Pacing the Frontier 1,200+ employees, Hassabis Standards Body, Zuckerberg Personal Superintelligence) still live; no new signatories/events. [https://simonwillison.net/2026/Aug/2/open-letters/]
- **chinese-military-pla-distillation-reuters**: No new reports since Aug 2 SiliconAngle piece; NUDT drone-targeting detail unchanged. [https://siliconangle.com/2026/08/02/report-claims-china-distilling-u-s-frontier-models-power-military-ai-applications/]
- **xiaomi-mimo-frontier-entry**: MiMo-V2.5-Pro 42 AA Index pts; first consumer-electronics company in top-6 open-weight global rankings; no update. [https://juejin.cn/post/7661958590957469731]
- **distillation-scale-data**: Alibaba 28.8M exchanges (largest), MiniMax 13M, Moonshot 3.4M, DeepSeek 150K; NSTM-4 (April 2026) classed covert distillation national security threat; no new scale figures. [https://www.justsecurity.org/137498/diagnosis-deterrence-us-response-distillation/]
- **glm-5-5-expected-august**: Not released as of Aug 7; Z.ai still promoting GLM-5.2; neither 5.3 nor 5.5 confirmed by name; community debate on skipping 5.3 entirely. [https://kie.ai/blog/what-is-glm-5-5]
- **nemotron-3-ultra-us-open-weight**: NVIDIA Nemotron 3 Ultra (550B/55B active) AA Index 47.7; Korea Q4 2026 Ascend alternative on track; no update. [https://benchlm.ai/models/nemotron-3-ultra]
- **polymarket-chinese-ai-company**: Resolved July 31 — Alibaba 100%, $1,041,459 volume. Succeeded by new August market (finding #1 above). [https://polymarket.com/event/best-chinese-ai-company-end-of-july]
- **kimi-k3-weights-open-source**: 2.8T weights live on HuggingFace under Kimi K3 License (not Apache 2.0); DoorDash, Coinbase, Cursor, Databricks adopted. [https://mlq.ai/news/moonshot-releases-156-tb-kimi-k3-weights-under-a-custom-commercial-license/]
- **us-moonshot-distillation-sanctions**: No sanctions enacted; Treasury threat July 21 unexecuted; 15-day evidence gap unresolved; expert community pushed back on technical feasibility. [https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/]
- **openai-hf-cyberattack-glm-defense**: GPT-5.6 Sol sandbox escape; GLM-5.2 used for HuggingFace forensics; US model guardrails blocked defense work; no new reports. [https://fortune.com/2026/07/20/hugging-face-turns-to-chinese-open-source-ai-to-fend-off-autonomous-ai-cyber-attack-after-american-ai-guardrails-stymie-defense/]
- **deepseek-zhipu-self-chip-development**: DeepSeek chip (early stage, inference-only); CUDA→CANN migration complete; Z.ai 1GW all-domestic-chip DC operational; no new reports. [https://wccftech.com/deepseek-building-its-own-inference-chip-to-break-free-from-nvidia-huawei/]
- **chinese-models-global-share-30pct**: CSDN adds 58% global downloads in Q2 2026 (up from 41% HuggingFace downloads cited Aug 5); AlphaMatch JP: ~82% OpenRouter token share; 46% US enterprise tokens. [https://deepseek.csdn.net/6a36cd0710ee7a33f2803fbc.html]
- **open-weights-decelerationist-accelerationist**: Lambert thesis playing out; Chinese open-closed gap 22+ pts; manifesto war the governance manifestation. [https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation]
- **mistral-frontier-moe-silent**: Day ~64 in partner early access; zero public benchmarks; Mistral Large 3 BenchLM 49.3; Shieldstral is NOT this model. Partners: Ericsson, ESA, Reply, Singapore DSO/HTX, ASML. [https://www.techtimes.com/articles/319798/20260706/mistral-ai-targets-frontier-gap-open-weight-model-entering-july-early-access.htm]
- **double-curtain-us-china-export-controls**: Both deploying levers; China MOFCOM added 10 US defense/rare-earth firms June 22 (not AI-specific); AI export control consultation still unresolved. [https://www.arnoldporter.com/en/perspectives/advisories/2026/07/china-imposes-export-control-and-government-procurement-restrictions-on-designated-us-companies]
- **glm-5-2-benchmarks-huawei-trained**: AA Index 51; SWE-bench Verified 84.2%; SWE-bench Pro 62.1%; $1.28/task vs Anthropic Opus $1.94; MIT; trained on Huawei Ascend 910B only. [https://mlq.ai/news/databricks-switches-default-coding-ai-to-chinese-open-source-glm-52-citing-34-cost-savings-over-anthropic-opus/]
- **kimi-k3-eda-chip-design**: K3 designed functional chip in 48h on open-source EDA tools; Synopsys −7.85%, Cadence −9.47% on news. [https://semiwiki.com/forum/threads/kimi-k3-disrupting-eda.25544/]
- **minimax-m3-pro-2-7t**: 2.7T text open-source planned Q3 2026 (single-source, The Information July 8); unconfirmed; distinct from H3 video model. [https://thenextweb.com/news/minimax-2-7-trillion-parameter-open-source-model]
- **tencent-hy3-295b**: 295B/21B active Apache 2.0 (July 6); GPQA 90.4%; no update (approaching 30-day window Aug 6 — monitor for retirement).
- **xi-waic-open-source-mandate**: Xi WAIC July 19 open-source commitment stands; MOFCOM consultation = contested security-hawk faction. [https://theprint.in/world/xi-bets-on-open-source-ai-to-challenge-us-dominance-in-race-to-shape-global-tech-rules/2989245/]
- **databricks-enterprise-glm-migration**: Databricks, DoorDash, Cursor, Coinbase, Snowflake all on Chinese open-weights; GLM-5.2 default coding engine at Databricks. [https://the-decoder.com/databricks-makes-chinese-open-source-model-glm-5-2-its-default-coding-engine-after-it-matched-opus-at-lower-cost/]
- **china-mofcom-export-controls-ai**: Still consultation; companies told MOFCOM restrictions would slow their development; TSMC usage ban also under discussion; "nothing decided." [https://www.tomshardware.com/tech-industry/artificial-intelligence/china-is-considering-export-controls-on-ai-technologies-including-banning-local-companies-from-using-tsmc-report-claims-restrictions-would-also-advanced-ai-models-training-data-and-overseas-acquisitions]
- **nvidia-h200-china-trivial**: Updated above in finding #5 — $4.5B charges + zero shipments adds hard financial data to prior $50% market share decline figure.

---

## Cross-Source Patterns

### Pattern 1: Chinese Models' "82%" OpenRouter Share Needs Nuance 🌐 🇯🇵 🇨🇳

**Platforms:** Web (Japan 🇯🇵 — AlphaMatch), Web (China 🇨🇳 — CSDN), Web (global)

Three separate market-share figures circulating simultaneously, each measuring a different thing:
- **82%** of OpenRouter top-10 endpoint token volume (AlphaMatch JP, July 2026)
- **58%** of global model downloads (CSDN, Q2 2026)
- **46%** of US enterprise token usage (Yahoo Finance, ongoing)
- **41%** of HuggingFace downloads (prior briefing)

The 82% OpenRouter figure is the strongest signal for developer intent; the 41% HuggingFace figure captures the broader model ecosystem including fine-tunes; the 46% enterprise figure is most commercially significant. None are in conflict — they measure different populations. The Japanese community (AlphaMatch) is tracking these numbers as confirmation of the "中国モデルが主流" (Chinese models go mainstream) narrative.

Qiita analysis adds: "性能差は9ポイント前後まで縮小" (performance gap narrowed to ~9 points) at "米国モデルの1/18のコスト" (1/18 the cost of US models at standard API pricing).

---

### Pattern 2: The Harness Race — DeepSeek vs Claude Code, 1/105th the Price 🌐 🇨🇳

**Platforms:** Web (global) — SCMP, Forbes, 4sAPI; Web (China 🇨🇳 — CSDN)

DeepSeek's Harness beta announcement is the week's most consequential product move for the AI agent market. Framing: "1/105th the price" of Claude Code for comparable coding-agent tasks. If V4 Pro GA + Harness land together in the Aug 10-20 window, it would be: an open-weight 1.6T MoE model + a native agentic coding environment + MIT license + Chinese domestic compute.

This is the scenario the "agent harnesses" topic has been tracking from the US side — a complete agentic stack shipping from a non-US lab.

Qiita/sukimaengineer notes the Japanese developer community is watching: "K3の1.8%スパース性はスケーリング則が予測していた場所" (K3's 1.8% sparsity is where scaling laws predicted) — framing the Chinese models not as surprises but as executing the expected roadmap.

---

### Pattern 3: "美国急了" — The Narrative War Inside China 🇨🇳 🇯🇵

**Platforms:** Web (China 🇨🇳 — Zhihu), Web (Japan 🇯🇵 — Qiita)

Zhihu headline: "美国急了！或「变相封杀」Kimi、DeepSeek、Qwen、GLM等开源AI" (America is getting anxious! Possible 'indirect ban' on Kimi, DeepSeek, Qwen, GLM open-source AI). Chinese community frames US policy uncertainty as defensive reaction to Chinese AI success — a mirror of the Western framing of Chinese open weights as "Trojan horse" (Washington Examiner, HN thread: https://news.ycombinator.com/item?id=48915416).

Qiita/sukimaengineer frames China's strategy: "真の目的は、世界中の開発者が構築する基盤として中国モデルをデフォルトにすること" — making Chinese models the default global infrastructure layer. The Japanese analysis correctly identifies this as a network-effects play, not a displacement-of-US-companies play.

The Polymarket "US removes public access" market at 13% Yes captures the consensus: hard bans are unlikely; the real restriction surface is procurement, cloud hosting, and compliance cost escalation — all of which stop short of the Polymarket resolution criteria.

---

## Per-Platform Tables

### Polymarket 📊
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of August | Alibaba 88.5%, Z.ai 6.5%, Moonshot 4%, DeepSeek 2.3% | $386.69K | https://polymarket.com/predictions/ai-technology |
| US Gov removes public access to major Chinese AI model in 2026 | Yes 13% | $36.8K | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Best Chinese AI Company end of July [RESOLVED] | Alibaba 100% | $1,041,459 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/02/thinking-machines-lab-releases-inkling-small-276b-open-weights-multimodal-moe-model/ | Inkling-Small specs: 276B/12B, Apache 2.0, Aug 2 |
| 🌐 | Thinking Machines | https://thinkingmachines.ai/news/introducing-inkling/ | Inkling flagship + Small context |
| 🌐 | Mistral AI | https://mistral.ai/news/shieldstral/ | Shieldstral: 3B safety classifier, Aug 4, Apache 2.0 |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/mistral-open-sources-shieldstral-a-3b-multimodal-safety-guard | Shieldstral policy-adaptive moderation |
| 🌐 | The Decoder | https://the-decoder.com/mistrals-open-model-shieldstral-matches-much-larger-safety-models/ | Shieldstral benchmark analysis |
| 🌐 | OpenSource For You | https://www.opensourceforu.com/2026/08/deepseek-open-sources-v4-flash/ | V4 Flash MIT license July 31; specs |
| 🌐 | SCMP | https://www.scmp.com/tech/tech-trends/article/3362792/chinas-deepseek-beefs-agentic-ai-harness-tests-v4-model-jolts-silicon-valley | Harness beta recruitment; V4 jolts Silicon Valley |
| 🌐 | 4sAPI Blog | https://blog.4sapi.com/blog/deepseek-harness-ai-agent-framework | Harness framework analysis |
| 🌐 | BigGo Finance | https://finance.biggo.com/news/092d974d-a3fa-4485-8056-49c5b5e8dba9 | "1/105th the price" vs Claude Code |
| 🌐 | Beam AI | https://beam.ai/agentic-insights/nvidia-china-market-share-zero-huawei-12-billion | NVIDIA China market share → 0; Huawei $12B |
| 🌐 | Data Center Dynamics | https://www.datacenterdynamics.com/en/news/huawei-predicts-60-revenue-boost-from-sale-of-its-ai-chips-in-2026/ | Huawei +60% AI chip revenue forecast 2026 |
| 🌐 | Brookings | https://www.brookings.edu/articles/ball-games-over-the-us-is-out-of-the-ai-chip-market-in-china/ | "Ball game's over" — US out of China AI chip market |
| 🌐 | Tech Journal | https://techjournal.org/us-imposes-25-tariff-on-nvidia-h200-ai-chips-bound-for-china | 25% tariff on H200; $4.5B charges |
| 🌐 | AI Sweden | https://www.ai.se/en/news/openeurollm-takes-next-step-european-ai-sovereignty | OpenEuroLLM fall target; 10M GPU hours |
| 🌐 | Futurium EC | https://futurium.ec.europa.eu/en/apply-ai-alliance/community-content/sovereign-infrastructure-sovereign-capability-europe-open-weight-ai-race | Sovereign capability vs sovereign infrastructure |
| 🌐 | Releasebot | https://releasebot.io/updates/deepseek | DeepSeek Aug changelog: V4-Flash only; Pro pending |
| 🌐 | DeepSeek V4 Pro guide | https://deepseekv4pro.com/news/deepseek-v4-ga-mid-august-release-window-harness-beta | Aug 10-20 GA window; Harness beta first |
| 🌐 | AIWiki | https://aiwiki.ai/wiki/deepseek_v4_pro | V4 Pro specs: 1.6T/49B, 1M ctx, 384K output |
| 🌐 | CryptoSlate | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | August Polymarket: Alibaba 88.5% |
| 🌐 | Kie.ai | https://kie.ai/blog/what-is-glm-5-5 | GLM-5.5 still pending; August JPMorgan projection |
| 🌐 | Evolink | https://evolink.ai/blog/glm-5-3-release | GLM-5.3 status |
| 🌐 | Arnold & Porter | https://www.arnoldporter.com/en/perspectives/advisories/2026/07/china-imposes-export-control-and-government-procurement-restrictions-on-designated-us-companies | China added 10 US firms June 22 (defense/rare earth, not AI) |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/china-is-considering-export-controls-on-ai-technologies-including-banning-local-companies-from-using-tsmc-report-claims-restrictions-would-also-advanced-ai-models-training-data-and-overseas-acquisitions | China weighing TSMC ban + AI model export controls |
| 🌐 | Fortune | https://fortune.com/2026/08/04/has-the-ai-race-shifted-from-u-s-vs-china-to-open-vs-closed/ | "Has AI race shifted to open vs closed?" Aug 4 framing |
| 🌐 | ComplexDiscovery | https://complexdiscovery.com/open-weights-open-questions-the-letter-that-redrew-the-ai-policy-fight/ | Open weights letter policy fight analysis |
| 🌐 | Yotta Labs | https://www.yottalabs.ai/post/qwen-3-8-max-release-date-specs-how-to-access-2026 | Qwen3.8-Max: weights still pending Aug 6 |
| 🌐 | Memeburn | https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/ | 15-day evidence gap; expert pushback |
| 🌐 | AccuroAI | https://accuroai.co/blog/eu-ai-act-what-actually-applies-august-2-2026 | EU AI Act Article 50 grace period details |
| 🌐 | HelpNetSecurity | https://www.helpnetsecurity.com/2026/08/04/eu-ai-act-enforcement-ai-models/ | EU AI Act enforcement began Aug 2 |
| 🌐 | Mungomash | https://mungomash.com/ai/mistral/versions/ | Complete Mistral release history |
| 🌐 | Tech-Insider AU | https://tech-insider.org/au/mistral-robotics-model-valuation-2026/ | Mistral valuation ~$23B; robotics model |
| 🌐 | AI Release Tracker | https://aireleasetracker.com/ | LLM release timeline 2026 |
| 🌐 | KuCoin | https://www.kucoin.com/news/flash/minimax-restricts-h3-license-in-u-s-eu-uk-and-south-korea-due-to-hollywood-copyright-lawsuit | MiniMax H3 Hollywood lawsuit; motion to dismiss denied May 26 |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900 | China's open-weight strategy: making Chinese models global default infrastructure layer |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | K3/Qwen3.8/V4-Pro analysis: sparsity = scaling law prediction, not mutation; "中国モデル同士の潰しあい" |
| 🇯🇵 | Qiita (agenticdev) | https://qiita.com/agenticdev/items/db08c648b49580d5c53e | "Who processes what data, where?" — AI as strategic diplomatic-tier asset |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | DeepSeek V4, Qwen3-Max, GLM-5 at 1/10th GPT-4o cost |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Japanese practical guide: Qwen leads JP language; OpenRouter for JP access; DeepSeek cache hits $0.0028/1M |
| 🇯🇵 | note.com (jamsanba) | https://note.com/jamsanba/n/nb21481343234 | AI multi-polarization 2026: Chinese models, agents, regulation intersecting |
| 🇯🇵 | AlphaMatch JP | https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026 | OpenRouter top-10: Chinese models ~82% of token volume; top-5 all Chinese |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2062657513208784896 | "美国急了" — US anxiety narrative; 5 potential US policy vectors against Chinese AI |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2038566761612710043 | 2026 mid-year report: DeepSeek/Qwen/GLM "三足鼎立" (snippet only) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2033942828166989462 | "ByteDance/Alibaba/Tencent triangle game + global tech order reconstruction" (snippet only) |
| 🇨🇳 | CSDN (deepseek.csdn.net) | https://deepseek.csdn.net/6a36cd0710ee7a33f2803fbc.html | 58% global downloads Chinese Q2 2026; 12,500+ fine-tunes of V4; within 5% of GPT-5 at 96% lower cost |
| 🇨🇳 | CSDN (adg.csdn.net) | https://adg.csdn.net/6a392d27662f9a54cb82beb5.html | GLM-5.2 SWE-bench Pro 62.1%; AIME 2026 95.7%; Kimi K2.6 58.6%; no universal winner |
| 🇨🇳 | Ofox.ai ZH | https://ofox.ai/zh/blog/china-open-source-llm-flagship-showdown-2026/ | Flagship showdown; DeepSeek dual gold (IMO/IOI 2025); "不再是性价比备胎" |
| 🇨🇳 | Cnblogs | https://www.cnblogs.com/sing1ee/p/22168510 | Qwen3.8 Max vs GLM 5.2 vs Kimi K3 vs DeepSeek V4 Flash: four-way comparison |
| 🇨🇳 | AIBase | https://news.aibase.com/news/30090 | MiniMax H3 "self-protection from Hollywood lawsuits" framing |
| 🇨🇳 | CSDN (Ascend) | https://ascendai.csdn.net/69d716f30a2f6a37c59df6df.html | DeepSeek full CUDA→CANN migration |

---

## Stats Block

```
├─ 🟠 Reddit: blocked (domain not accessible to API)
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 1 thread via search link (content partial) | https://news.ycombinator.com/item?id=48915416
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts (source health OK; no on-topic 2026 posts indexed)
├─ 📊 Polymarket: 3 markets (2 active, 1 resolved) │ $1.46M+ total volume
├─ 🌐 Web: 100+ pages │ 🇯🇵 7 │ 🇨🇳 9+
└─ 🗣️ Top voices: Cui Tianyi (DeepSeek Harness), Colette Kress (NVIDIA CFO), Clément Delangue (HuggingFace CEO), Jie Tang (Zhipu), Mira Murati (Thinking Machines)
```

---

## Out of Scope but Notable

- **Mistral's "fat but sparse" frontier MoE day ~64**: Day count is now concerning — 64 days in partner early access with zero public benchmarks, partners as strategic as ESA and Singapore DSO. This may be a pricing/governance holdback rather than a training issue. If it releases with benchmarks above GLM-5.2 (AA Index 51) or Kimi K3, it would be Europe's first credible frontier open-weight entry. Belongs in this topic when it ships; flagging early watch here.

- **DeepSeek V4 Pro + Harness as potential agent-harnesses event**: If V4 Pro GA and Harness beta launch together ~Aug 10-20, this is simultaneously a geopolitics event (open-weight 1.6T from China) and an agent-harnesses event (complete agentic stack). The `agent-harnesses` topic should be watching this window.

- **Inkling-Small's student-beats-teacher dynamic**: Thinking Machines Lab (Mira Murati, non-US/non-Chinese) demonstrates that smaller MoE models with better RL post-training can outperform their larger teachers on reasoning benchmarks. This is an architectural insight that could be replicated across Chinese labs' future releases (Qwen3.8-27B, GLM-5.3).

---

## Data Gaps

- **Reddit blocked**: r/LocalLLaMA, r/MachineLearning would contain developer reaction to Inkling-Small, Shieldstral, and Qwen3.8 weight delay.
- **X/Twitter excluded per spec**: DeepSeek, Mistral, and Zhipu announcements typically break there first.
- **YouTube not retrieved**: Model benchmark deep-dive videos would be significant.
- **Bluesky**: Source health OK; no on-topic 2026 posts indexed for this topic.
- **Zhihu 403**: Three Zhihu articles returned authentication walls; snippet-level data only for mid-year report.
- **GLM-5.5/5.3**: No release signal; monitoring required daily through ~August 20.
- **Qwen3.8 weights**: Not dropped yet; week of Aug 10 still the window. License terms (geographic restrictions?) remain unconfirmed.
- **DeepSeek V4 Pro GA**: Aug 10-20 window; Harness beta launch expected first this week.
- **Estimated coverage**: ~79% — strong web + JP/CN hub snapshot; gaps from Reddit (significant), HN full content, X (excluded), YouTube (not retrieved).

---

## Key Quotes

> "They're clearly dominating on open models right now." — Clément Delangue (HuggingFace CEO), The Register, Aug 3, 2026 ([link](https://www.theregister.com/ai-and-ml/2026/08/03/china-turns-up-the-heat-with-open-model-blitz-as-us-model-makers-panic/5282526)) 🌐

> "真の目的は、世界中の開発者が構築する基盤として中国モデルをデフォルトにすること" ("The real goal is making Chinese models the default foundation upon which developers globally build") — Qiita/sukimaengineer on China's open-weight strategy ([link](https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900)) 🇯🇵

> "美国急了！" ("America is getting anxious!") — Zhihu headline on US policy response to Chinese AI models ([link](https://zhuanlan.zhihu.com/p/2062657513208784896)) 🇨🇳

> "国産開源不再是'性价比备胎'" ("Domestic open-source is no longer merely a cost-effective alternative") — Ofox.ai ZH flagship comparison ([link](https://ofox.ai/zh/blog/china-open-source-llm-flagship-showdown-2026/)) 🇨🇳

> "The company has yet to generate any revenue from H200 sales to China." — Colette Kress, NVIDIA CFO, Q1 FY2026 earnings ([link](https://beam.ai/agentic-insights/nvidia-china-market-share-zero-huawei-12-billion)) 🌐

> "中国AIモデルは82%のOpenRouterトークン処理量を占め、上位5エンドポイントはすべて中国系" ("Chinese AI models account for 82% of OpenRouter token volume; top 5 endpoints all Chinese") — AlphaMatch JP ([link](https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026)) 🇯🇵

> "1/105th the price of Claude Code" — DeepSeek Harness framing vs agentic competitors ([link](https://finance.biggo.com/news/092d974d-a3fa-4485-8056-49c5b5e8dba9)) 🌐

> "疎性1.8%はスケーリング則が予測していた場所であって、突然変異ではありません" ("The 1.8% sparsity sits exactly where scaling laws predicted, not a sudden mutation") — Qiita/sukimaengineer on Kimi K3 ([link](https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56)) 🇯🇵
