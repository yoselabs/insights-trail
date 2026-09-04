# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-09-04
**Query type:** GENERAL
**Sources:** WebSearch, WebFetch, BenchLM, Releasebot, TechNode, Polymarket, Qiita (🇯🇵), Zenn (🇯🇵), CSDN (🇨🇳), Zhihu (🇨🇳), Sohu (🇨🇳), Sina Finance (🇨🇳)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 0 | — | No relevant HN threads found Sep 1-4 |
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| Bluesky | 0 | — | No qualifying posts found |
| Polymarket | 5 markets | $559K volume | 🌐 Chinese AI Co., model competition, AI bubble |
| Web (global) | 58 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Qiita (5), Zenn (1), note.com (1), GIGAZINE (1), Congaroo (1) |
| Web (China) | 14 pages | — | 🇨🇳 CSDN (3), Zhihu (2), Sina (2), Sohu (1), NBD/每经 (2), CINN (1), BAAI Hub (1), Woshipm (1), Epoch Times (1) |

---

## Synthesized Findings

### 1. [new] UAE/MBZUAI IFM K2 Horizon: Third Pole of Fully Open AI 🌐
**Claim:** MBZUAI's Institute of Foundation Models (Abu Dhabi) launched K2 Horizon on Sep 3 — six fully open models (weights + code + training data + logs) from 0.9B to 375B-A23B, all Apache 2.0; explicitly positioned as alternative to both US proprietary AND "not-as-transparent" Chinese models.
- **Size/arch:** 0.9B, 3.7B, 7B (edge/mobile), 32B (dense workstation), 36B-A4B, 375B-A23B (enterprise MoE); diffusion distillation (3× parallel token gen), Mixture of Value Attention, dynamic routing
- **Benchmarks (flagship 375B-A23B):** AI Analysis Intelligence Index 47 (vs median open-weight 29); Terminal-Bench 2.1 70.2%; SWE-Bench Pro 42.6%; GPQA Diamond 87.3%; HLE 32.0%; Toolathlon Verified 65.3%
- **Edge models:** 0.9B, 3.7B, 7B claim SOTA at their scales; 0.9B scores >48 on AIME 2026
- **Reward-hacking:** 3.37% (vs Claude 2.2%, GPT-5.6 4.1%)
- **Geopolitics:** UAE sovereign AI play; IFM offices in Silicon Valley, Paris, Abu Dhabi; Microsoft-G42 partnership history creates US scrutiny; first fully open competitor to Chinese and US models at this scale
- **Sources:** https://ifm.ai/k2/press-release/ | https://moorinsightsstrategy.com/mbzuai-ifm-launches-6-k2-horizon-frontier-models-doubles-down-on-openness-analyst-insight/ | https://www.thenationalnews.com/future/technology/2026/09/03/mbzuai-k2-horizon-ai-open-model-uae/ | https://www.middleeastainews.com/p/mbzuais-ifm-releases-worlds-largest | https://medium.com/the-geopolitical-economist/uaes-k2-think-joins-the-global-ai-arms-race-e553f510c4ee

### 2. [update] Moonshot AI Files Confidential HKEX IPO ($3B at $50B) 🇨🇳
**Claim:** Moonshot AI submitted a confidential A1 application to HKEX on Sep 3, formally starting its IPO process — targeting $3B at a $50B pre-money valuation.
- **New fact since Sep 1:** Confidential HKEX filing executed Sep 3; Deutsche Bank added as third underwriter (Goldman + CICC already known)
- **Kimi K3 ARR:** $300M (June 2026); company declined to comment
- **Pre-IPO round:** Target closing Aug 27 — no public confirmation of closure
- **Corporate restructuring:** Moonshot unwound offshore incorporation; established onshore China domicile before filing
- **Complication:** Moonshot is one of four labs named in US distillation sanctions threat; unusual to sanction a company in active IPO process
- **Sources:** https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | https://techstartups.com/2026/09/03/chinese-ai-startup-moonshot-files-for-3-billion-hong-kong-ipo-at-50-billion-valuation/ | https://qz.com/moonshot-ai-hong-kong-ipo-filing-3-billion-090326 | https://www.business-standard.com/world-news/chinese-ai-firm-moonshot-files-confidentially-for-hong-kong-ipo-126090301687_1.html | https://kr-asia.com/moonshot-ai-targets-august-27-closing-for-pre-ipo-round-ahead-of-hong-kong-filing

### 3. [update] Qwen3.8-Max-0902 Coding Snapshot: Code Arena WebDev #1 🌐🇨🇳
**Claim:** Alibaba released a coding-focused post-training snapshot (Qwen3.8-Max-0902) on Sep 2, claiming #1 on Code Arena WebDev at 1,691 pts — 4 pts above Claude Opus 5 Max.
- **New fact:** Code Arena WebDev: Qwen3.8-Max-0902 1,691 > Claude Opus 5 Max 1,687 > Kimi K3 Max 1,674 > prev Qwen3.8-Max 1,669
- **Architecture:** Unchanged (2.4T total params, 1M context, $2/$6 per M input/output)
- **Use case:** Coding + Cowork-style agentic tasks; available on QwenCloud/API
- **Sources:** https://technode.com/2026/09/02/alibaba-upgrades-qwen38-max-with-new-0902-snapshot/ | https://www.aroged.com/2026/09/03/alibaba-launches-qwen-3-8-max-0902-model-focusing-on-programming/ | https://benchlm.ai/models/qwen3-8-max

### 4. [update] BenchLM Recalibration: Hy4 Preview and Qwen3.8 Max Scores Revised Down 🌐
**Claim:** BenchLM revised scores between Sep 1 and Sep 4; Hy4 preview dropped from 79.9 to 78.2-78.5, Qwen3.8 Max from 79.4 to 78.2-78.3; ranked universe narrowed from 228 to 106 models.
- **New fact:** 228-model board (Aug 31, including quantized variants) → 106-model curated board (Sep 4); scores recalibrated
- **Current top-3:** Hy4 preview 78.2-78.5 (#1), Qwen3.8 Max 78.2-78.3 (#2), Qwen3.8-27B 71.6 (#3)
- **#4-10:** dots3-note Preview 68.6; MiniMax M3 68.1; Hy3 67.5; Ornith-1.5 67.1; GLM-5.3 67.0; GLM-5.2 66.9; GLM-5.1 66.8
- **Chinese dominance:** 9 of top 10 positions from Chinese labs; GLM-5.3-Flash #15 at 61.8
- **Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/models/hy4-preview

### 5. [update] Huawei Domestic Chip Dominance: Ascend 950PR Milestone 🇨🇳
**Claim:** Ascend 950PR shipped 450K+ units by Q2 2026; Chinese domestic AI chip market crossed 52.3% share Q1 2026 (first majority); 950DT cloud GA confirmed August.
- **New facts since Sep 1:** Sohu confirms 450K+ Ascend 950PR units shipped; market share 52.3% domestic (Q1 2026); domestic share now market-driven, not just policy
- **950PR specs:** 112GB HBM, 1.4 TB/s bandwidth, FP8 >1 PFLOPS, 2.87× H20 single-card inference, ~1/3 cost of Nvidia equivalent
- **950DT:** Cloud GA August 2026 (confirmed); full commercial launch Q4 2026; 144GB HBM HiZQ 2.0, 4 TB/s, 2 PFLOPS FP8
- **Vendor landscape:** Huawei Ascend 37% of domestic market (70% of domestic-brand share); Cambricon and Haiguang complete "three-power oligopoly"
- **Alibaba/Tencent/ByteDance:** "Ascend + Cambricon dual vendor" Q1 2026 orders >22B RMB
- **Vice Premier Ding Xuexiang** (Jul 24): reportedly said refusing domestic chips is "betrayal" — reflecting government pressure
- **Sources:** https://www.sohu.com/a/1030450496_122410101 | https://www.esmchina.com/news/14475.html | https://www.cinn.cn/2026/05-25/GDBjZNKD.html | https://www.epochtimes.com/gb/26/7/24/n14816956.htm | https://abit.ee/en/processors/huawei-ascend-950pr-ascend-950dt-ai-chip-ai-accelerator-huawei-artificial-intelligence-china-en | https://abit.ee/en/processors/huawei-ascend-950dt-ai-chip-ai-accelerator-huawei-cloud-machine-learning-ascend-950-en

### 6. [update] Polymarket September Market: Alibaba Odds Slip to 72% 🌐
**Claim:** September's Best Chinese AI Company market updated: Alibaba 72% ($203K, was 77%); Moonshot 55% (was 52%); Z.ai 62% (was 60%).
- **New fact:** Alibaba -5pp, Moonshot +3pp, Z.ai +2pp from Sep 1 snapshot — Moonshot's HKEX filing may be boosting market confidence
- **Volume change:** Sep total volume: $315K (vs $295K combined on Sep 1)
- **Chinese best model by Dec 31:** Only 9% Yes ($232K) — market still skeptical of Chinese #1 globally
- **Best global AI model (October):** Anthropic 76% ($137K)
- **AI Bubble Burst by Dec 31:** 12% ($3M, platform's most active market)
- **Sources:** https://polymarket.com/predictions/ai-technology | https://polymarket.com/event/will-a-chinese-company-have-the-best-ai-model-by-december-31 | https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-september-20260717143435868

### 7. [update] GLM-5.3-Flash Promo: 50% Off Through Sep 9 🌐🇨🇳
**Claim:** Z.AI running 50% promo on GLM-5.3-Flash through Sep 9 ($0.045/task on AA benchmark).
- **New fact:** Promo pricing $0.045/task for ~5 days after Sep 4; standard rate unchanged post-promo
- **Source:** https://local-ai-zone.github.io/blog/September_2026_AI_Model_Updates.html

---

**Still true (ongoing from prior briefing):**
- `us-china-ai-safety-talks-sep24` — Trump-Xi Sep 24 summit: Bessent-led AI pre-talks scheduled; agenda: frontier model risks, IP; still upcoming
- `trump-diffusion-rule-remote-compute` — BIS redesigned framework committed to FY2026 (Sep 30); remote compute targeting Thailand/Singapore; still not finalized
- `tencent-hy4-preview-apache` — Hy4 preview (770B-A49B, Apache 2.0): #1 BenchLM at 78.2-78.5; Hy3 free access extended to Sep 30
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3 weights available; 744B-A40B MoE; KingBench coding 91.25%; conditional license for >$10B rev orgs
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next (125B-A6B, qwen-community-1.0); Qwen4 architecture preview; no full Qwen4 release
- `minimax-h1-2026-agent-dividend` — MiniMax ARR >$800M, H1 revenue $116.6M (+283% YoY)
- `open-weight-licensing-bifurcation` — "Enclosure turn": MIT/Apache for flash tier, conditional for frontier; GLM-5.3 + Qwen3.8-Flash-Next pattern holds
- `deepseek-v4-flash-vision-exp` — DeepSeek-V4-Flash-Vision-Exp (API-only multimodal); V5 not released, unconfirmed
- `meta-muse-glimmer-us-open-weight` — Meta Muse Glimmer (30B, Apache 2.0); Muse Spark 1.2 weights still not released; Q4 2026 expected
- `dots3-note-preview-rednote` — dots3-note Preview (280B/16B active, Apache 2.0); BenchLM #4 at 68.6
- `ornith-1-5-self-improving` — Ornith-1.5 (MIT, 397B MoE from Qwen3.5 base); BenchLM #7 at 67.1
- `qwen3-8-27b-apache-multimodal` — Qwen3.8-27B (Apache 2.0, 27B dense); BenchLM #3 at 71.6
- `mistral-glm52-eu-sovereign-hosting` — Mistral Agentic Search (Aug 20); GLM-5.2 on EU Regional Endpoints at €1.19/M
- `agents-a1-internsciense-new-entrant` — InternScience Agents-A1 (35B MoE); BenchLM #16+ range
- `deepseek-harness-v01-price-hike` — DeepSeek Harness 144K+ stars; V4-Pro peak $3.96/MTok output
- `kimi-k3-weights-open-source` — Kimi K3 (2.8T MoE, Kimi K3 License, >$20M rev must negotiate); BenchLM Chinese #1 ~80.3
- `us-moonshot-distillation-sanctions` — No enforcement; Moonshot IPO filing makes sanctions tactically harder; four labs named (Moonshot/MiniMax/Alibaba/DeepSeek)
- `openai-hf-cyberattack-glm-defense` — No new reports; GLM-5.2 forensics use case unchanged
- `deepseek-zhipu-self-chip-development` — DeepSeek inference chip (early stage); Zhipu domestic chip inference 62T tokens/day at NVIDIA parity
- `open-weights-decelerationist-accelerationist` — Palladium Mag decelerationist thesis (Aug 19); Sep 24 bilateral dimension adds co-governance layer
- `openeurollm-european-sovereign` — Published reference models; no flagship; 8B in progress; compute resource challenges
- `mistral-frontier-moe-silent` — Day ~122 in partner early access; Mistral OCR 4.1 (Aug 30) only new release; frontier MoE still silent
- `double-curtain-us-china-export-controls` — MOFCOM controls in consultation; US BIS framework by Sep 30; Ascend worldwide ban (May 2025) in effect
- `kimi-k3-eda-chip-design` — Kimi K3 designed functional chip (48h, open EDA); Synopsys/Cadence stock impact
- `minimax-m3-pro-2-7t` — MiniMax M3 Pro 2.7T unconfirmed; MiniMax M3 at BenchLM #5
- `tencent-hy3-295b` — Hy3 (295B/21B, Apache 2.0) at BenchLM #6 at 67.5; superseded by Hy4 preview
- `china-mofcom-export-controls-ai` — Tiered AI export controls still consultation; Alibaba/ByteDance/Zhipu pushing back
- `jp-deepseek-japanese-cultural-benchmark` — JP developers pragmatically adopting Chinese open-weights; Qiita @sukimaengineer "infrastructure dominance" thesis; hallucination concerns persist
- `glm-5-5-expected-august` — August target missed; window Sep-Oct 2026; no Zhipu announcement
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0, Aug 4); 54.1M training pairs
- `minimax-h3-geo-license-restriction` — H3 video (33B): US/EU/UK/Korea excluded from local deployment; Hollywood litigation ongoing
- `deepseek-autonomous-cyberattack-hermes` — Palo Alto Unit 42 "Knaithe/KnYuan": no new reports
- `industry-coalition-open-weights-letter` — 270+ signatories; Anthropic sole major US holdout; wants mandatory safety testing
- `kimi-k3-gpu-crunch-subscription-pause` (prior claim about GPU/subscription) — Moonshot IPO now the active thread; subscription pause resolved
- `nemotron-3-ultra-us-open-weight` — Nemotron 3 Ultra (550B/55B): outside top-15; Nvidia remains US open-weight leader
- `polymarket-chinese-ai-company` — Aug 31 resolved: Alibaba winner; Sep market active (see finding #6)
- `polymarket-us-chinese-model-ban` — 26% Yes; $15.1K; resolves Dec 31; Moonshot IPO adds diplomatic pressure against enactment
- `inkling-small-thinking-machines` — Inkling (276B/12B): BenchLM #11 at 66.4; Inkling-Small #13 at 63.4
- `eu-ai-act-august-enforcement` — GPAI enforcement active since Aug 2; no new enforcement actions; Chinese providers subject
- `ai-manifesto-war-pacing-frontier` — Three frameworks live; Sep 24 summit adds bilateral layer; decelerationist argument gaining traction
- `chinese-military-pla-distillation-reuters` — NUDT UAV drone targeting; no new reports Sep 1-4
- `xiaomi-mimo-frontier-entry` — MiMo-V2.5-Pro: outside top-15 BenchLM; first consumer electronics company in open-weight tier
- `distillation-scale-data` — Alibaba 28.8M exchanges largest; NSTM-4 (April 2026) classified as national security threat; no enforcement
- `databricks-enterprise-glm-migration` — GLM Coding Plan users on GLM-5.3; ZCode 1M users; Databricks/DoorDash/Cursor/Coinbase on Chinese open-weights
- `chinese-models-global-share-30pct` — 41% global HuggingFace downloads (Spring 2026); top 6 most-called open-source globally all Chinese; Chinese models 82% OpenRouter token volume (July 2026)
- `xi-waic-open-source-mandate` — Dual-track: Apache small + conditional large; China 28 Global South AI partnerships at WAIC July 17
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 superseded by GLM-5.3 API; hosted on Mistral EU endpoints; trained on Ascend 910B
- `nvidia-h200-china-trivial` — Nvidia ~8% China AI chip share; domestic share >52.3% Q1 2026 (see finding #5)
- `deepseek-chip-ascend-950dt` — Ascend 950DT cloud GA Aug 2026 (see finding #5); DeepSeek building own inference chip (early stage)

---

## Cross-Source Patterns

### Pattern 1: UAE Enters as "Third Pole" — Full Transparency vs US+CN Opacity 🌐
- **Signal:** IFM K2 Horizon explicitly rejects both US (closed proprietary) and Chinese (opaque despite open weights) models
- **Platforms:** Global web (The National UAE, Moore Insights, MBZUAI press release), Geopolitical Economist
- **Significance:** First non-US, non-Chinese actor releasing frontier-scale models with training data — creates a new legitimacy benchmark for "true openness"
- **Key quote:** IFM positions K2 Horizon as counterpoint to "closed US commercial models AND open-weight models from Chinese labs that are still not as transparent as IFM would like" — https://moorinsightsstrategy.com/mbzuai-ifm-launches-6-k2-horizon-frontier-models-doubles-down-on-openness-analyst-insight/

### Pattern 2: Chinese Open-Source as Infrastructure Layer — JP Developer Thesis Matches CN Data 🇯🇵🇨🇳
- **Signal:** Qiita @sukimaengineer (Jul 2026) independently arrived at the same framing as Chinese market data: goal is default infrastructure, not competitive destruction
- **Platforms:** Qiita (JP), CSDN, Zhihu, AlphaMatch (global), OpenRouter data
- **Data convergence:** JP: "中国のゴールはアメリカのAI企業を壊すことではなく、中国モデルを世界のデフォルトインフラにすること" / CN: Qwen 50%+ global open-model downloads, 82% OpenRouter token volume
- **Quote (JP):** "China's goal is not destroying US AI companies but making Chinese models the world's default infrastructure layer" — @sukimaengineer on Qiita (https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900)

### Pattern 3: Dual Pressure on Open-Weight Ecosystem — US and China Both Tightening 🌐
- **Signal:** US BIS framework (by Sep 30 FY2026) targeting remote compute; China MOFCOM consultation on restricting open-weight exports; creating bilateral squeeze on the global open ecosystem
- **Platforms:** Lawfare, Tom's Hardware, Mapshock, MOFCOM reporting; Chatham House warns of overreach
- **Quote:** "China's potential restrictions would do the same from the opposite direction — and the impact on the open-weight ecosystem would be far broader" — Lawfare (https://www.lawfaremedia.org/article/knives-are-out-for-open-weight-ai-models)

### Pattern 4: BenchLM Recalibration Creates "False Drop" Narrative Risk 🌐
- **Signal:** Hy4 preview score dropped 79.9→78.2; Qwen3.8 Max 79.4→78.2 — not actual model regression, BenchLM methodology/scope change
- **Platforms:** BenchLM, multiple tracker sites
- **Risk:** Downstream articles may cite "score drops" without noting recalibration; monitor for misinformed coverage

---

## Per-Platform Tables

**Polymarket:** 🌐
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company — September | Alibaba 72% | $203K | https://polymarket.com/predictions/ai-technology |
| Second-Best Chinese AI Company — September | Moonshot 55% | $82.9K | https://polymarket.com/predictions/ai-technology |
| Third-Best Chinese AI Company — September | Z.ai 62% | $29.5K | https://polymarket.com/predictions/ai-technology |
| Chinese company has best global AI model by Dec 31 | 9% Yes | $232K | https://polymarket.com/event/will-a-chinese-company-have-the-best-ai-model-by-december-31 |
| Best AI Model (October) | Anthropic 76% | $137K | https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-september-20260717143435868 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | IFM / MBZUAI (press) | https://ifm.ai/k2/press-release/ | K2 Horizon 6 fully open models Sep 3 |
| 🌐 | Moore Insights | https://moorinsightsstrategy.com/mbzuai-ifm-launches-6-k2-horizon-frontier-models-doubles-down-on-openness-analyst-insight/ | K2 Horizon geopolitical framing |
| 🌐 | The National (UAE) | https://www.thenationalnews.com/future/technology/2026/09/03/mbzuai-k2-horizon-ai-open-model-uae/ | UAE sovereign AI context |
| 🌐 | TechNode | https://technode.com/2026/09/02/alibaba-upgrades-qwen38-max-with-new-0902-snapshot/ | Qwen3.8-Max-0902 coding update |
| 🌐 | TechNode | https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | Moonshot HKEX confidential filing |
| 🌐 | Quartz | https://qz.com/moonshot-ai-hong-kong-ipo-filing-3-billion-090326 | $3B target, underwriter details |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/policy/new-us-export-controls-reportedly-target-chinese-access-to-remote-ai-servers-trump-admins-cut-down-ai-diffusion-rule-could-be-shared-with-industry-as-soon-as-september | Remote compute rule by September |
| 🌐 | Lawfare | https://www.lawfaremedia.org/article/knives-are-out-for-open-weight-ai-models | Both US+China squeezing open-weight ecosystem |
| 🌐 | CSIS | https://www.csis.org/programs/trump-xi-2026-summits | Sep 24 summit tracking |
| 🌐 | CNBC | https://www.cnbc.com/2026/07/21/us-china-ai-talks-bessent.html | Bessent-led AI pre-talks |
| 🌐 | BIS.gov | https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens | Diffusion rule rescission official |
| 🌐 | Releasebot | https://releasebot.io/updates/mistral | Mistral OCR 4.1 Aug 30; frontier MoE silent |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Current leaderboard |
| 🌐 | ValueAdd VC | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition | Huawei 50-60% China AI chip share |
| 🌐 | CFR | https://www.cfr.org/articles/chinas-ai-chip-deficit-why-huawei-cant-catch-nvidia-and-us-export-controls-should-remain | HBM bottleneck analysis |
| 🌐 | Local AI Zone | https://local-ai-zone.github.io/blog/September_2026_AI_Model_Updates.html | GLM-5.3-Flash 50% promo Sep 9 |
| 🌐 | Palladium Mag | https://www.palladiummag.com/2026/08/19/american-ai-may-not-survive-chinese-open-source | Decelerationist thesis |
| 🌐 | AlphaMatch | https://www.alphamatch.ai/blog/open-source-llm-comparison-blog-2026 | Chinese models 82% OpenRouter volume |
| 🇯🇵 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900 | China open-weight strategy: infrastructure dominance thesis |
| 🇯🇵 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | Kimi K3/Qwen3.8-Max/DeepSeek-V4-Pro deep-dive; hardware reality |
| 🇯🇵 | Qiita (daisuke-nagata) | https://qiita.com/daisuke-nagata/items/98dfec77fb193cc90093 | US-China AI gap: has it really narrowed to 2.7%? |
| 🇯🇵 | Qiita (kai_kou) | https://qiita.com/kai_kou/items/1d66ed9b16b6717053e5 | GLM-5 on Huawei chips guide |
| 🇯🇵 | Qiita (etale_cohomology) | https://qiita.com/etale_cohomology/items/61db72acde35b9fb795c | Qwen-AgentWorld; Chinese AI agent/world model frontier |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Practical Chinese AI model guide for developers (June 2026) |
| 🇯🇵 | Note.com | https://note.com/zouplans/n/na9b74156aa00 | Chinese AI adoption in Silicon Valley; status DeepSeek/Qwen/Kimi |
| 🇯🇵 | Innovatopia | https://innovatopia.jp/ai/ai-news/77013/ | DeepSeek restrictions in 12 countries; geopolitical risks |
| 🇯🇵 | GIGAZINE | https://gigazine.net/gsc_news/en/20260721-qwen3-8/ | Qwen 3.8 open release; "second only to Fable 5" |
| 🇨🇳 | CSDN | https://blog.csdn.net/csdnnews/article/details/160284776 | 2026 AI open source influence ranking; China leads globally |
| 🇨🇳 | CSDN (DeepSeek community) | https://deepseek.csdn.net/6a0ac187662f9a54cb75630b.html | Qwen3.5 (#1 LM Arena China); DeepSeek V3.2 fully on domestic chips |
| 🇨🇳 | CSDN (DeepSeek community) | https://deepseek.csdn.net/6a26115c662f9a54cb7b1d64.html | API prices down 90%; 5 Chinese models redefining development |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2009705203163752429 | Top 10 open-source 2026; 8/10 Chinese models |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2048464721083470807 | Chinese LLM ecosystem panorama 2026 |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-04-11/doc-inhuauvf9648437.shtml | Qwen downloads approaching 1 billion; US share squeezed |
| 🇨🇳 | NBD (每经) | https://www.nbd.com.cn/articles/2026-07-25/4511910.html | US-China gap: 3-5 months per Chinese researchers |
| 🇨🇳 | Sohu | https://www.sohu.com/a/1030450496_122410101 | Ascend 950PR: 450K+ shipped, 2.87× H20 |
| 🇨🇳 | ESM China | https://www.esmchina.com/news/14475.html | Nvidia 8% China share; domestic target 90% 2026 |
| 🇨🇳 | CINN | https://www.cinn.cn/2026/05-25/GDBjZNKD.html | Three domestic chip powers; market-driven (not policy) shift |
| 🇨🇳 | BAAI Hub | https://hub.baai.ac.cn/view/54415 | Brookings: US-China AI competition is multi-dimensional |
| 🇨🇳 | Sina News | https://news.sina.com.cn/c/2026-07-26/doc-inikassk8772454.shtml | China AI closing in; US tech firms feuding internally |
| 🇨🇳 | Epoch Times | https://www.epochtimes.com/gb/26/7/24/n14816956.htm | Vice Premier Ding: refusing domestic chips is "betrayal" |
| 🇨🇳 | NBD (每经) | https://www.nbd.com.cn/articles/2026-04-24/4358607.html | DeepSeek-V4 on Ascend: low latency, high throughput confirmed |
| 🇨🇳 | Zmyx Substack | https://zmyx.substack.com/p/kimi-k3ai | Open vs closed debate; US-China AI policy divergence triggered by Kimi K3 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 0 stories
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no qualifying open-models posts found)
├─ 📊 Polymarket: 5 markets │ $684K volume
├─ 🌐 Web: 58 pages │ 🇯🇵 9 │ 🇨🇳 14
└─ 🗣️ Top voices: @sukimaengineer (Qiita) │ IFM/MBZUAI │ Moonshot AI | Alibaba Qwen
```

---

## Out of Scope but Notable

- **IFM K2 Horizon diffusion distillation architecture**: The "Mixture of Value Attention" + parallel token block generation approach (3× speed) is a novel inference architecture, not just a model release. If this architecture diffuses to other labs, it could reshape inference-tier thinking across all model families. Noted here because it may belong in a "model architecture innovations" topic rather than geopolitics. — https://ifm.ai/blog/k2
- **Qwen-AgentWorld (Qiita coverage)**: Alibaba's foundational model simulating 7 agent environments with a single model, framed as a "language world model" breakthrough. Geopolitically tagged here but the underlying technique may be an agent-harnesses paradigm shift. — https://qiita.com/etale_cohomology/items/61db72acde35b9fb795c

---

## Data Gaps

- **Bluesky**: Checked; no qualifying posts on open-models/geopolitics found for Sep 1-4. Coverage_pct impact: minor (Bluesky = OK per SOURCE HEALTH but sparse on this topic).
- **HackerNews**: No significant HN threads on these specific releases detected Sep 1-4. IFM K2 Horizon / Moonshot IPO may appear later in the day.
- **DeepSeek V5**: Confirmed not released; rumors unverified. No authoritative source.
- **GLM-5.5**: Confirmed not released; window Sep-Oct 2026.
- **Mistral frontier MoE**: Day ~122 in partner early access; zero public data. Coverage gap is structural (model not yet public).
- **BenchLM recalibration**: Reason for score changes (79.9→78.2) not explained publicly; may be methodology change rather than model score change. Raw BenchLM page shows "Estimated" status for several models.
- **Moonshot pre-IPO round closure**: Aug 27 target but no public confirmation; treated as unconfirmed.
- **Approximate coverage:** 82% — strong on Sep 1-4 releases and geopolitics; gap in HN/social signal and in Mistral frontier model details.

---

## Key Quotes

> "IFM positions K2 Horizon as a counterpoint to both closed commercial models from big US providers AND open-weight models from Chinese labs that are still not as transparent as IFM would like." — Moore Insights analysis ([link](https://moorinsightsstrategy.com/mbzuai-ifm-launches-6-k2-horizon-frontier-models-doubles-down-on-openness-analyst-insight/))

> "中国のゴールはアメリカのAI企業を壊すことではなく、中国モデルを世界のデフォルトインフラにすること" ("China's goal is not destroying American AI companies but making Chinese models the world's default infrastructure") — @sukimaengineer on Qiita ([link](https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900))

> "China's potential restrictions [on open-weight exports] would do the same from the opposite direction — and the impact on the open-weight ecosystem would be far broader." — Lawfare ([link](https://www.lawfaremedia.org/article/knives-are-out-for-open-weight-ai-models))

> "丁薛祥対AI企業放狠话：拒用国产芯片就是叛徒" ("Vice Premier Ding Xuexiang to AI firms: refusing domestic chips is betrayal") — reported by Epoch Times Jul 24, 2026 ([link](https://www.epochtimes.com/gb/26/7/24/n14816956.htm))

> "The Qwen3.8-Max-0902 front-end CodeArena score rose by 22 points to 1,691, placing it first on the leaderboard." — TechNode ([link](https://technode.com/2026/09/02/alibaba-upgrades-qwen38-max-with-new-0902-snapshot/))

> "Chinese AI startup Moonshot files for $3 billion Hong Kong IPO at $50 billion valuation." — Tech Startups ([link](https://techstartups.com/2026/09/03/chinese-ai-startup-moonshot-files-for-3-billion-hong-kong-ipo-at-50-billion-valuation/))

> "国産AI芯片在中国市场占比首次突破52.3%，其中昇腾以37%的份额位居第一" ("Domestic AI chips crossed 52.3% of China's market for the first time; Ascend leads with 37%") — CINN ([link](https://www.cinn.cn/2026/05-25/GDBjZNKD.html))

> "The redesigned US framework is expected to land as an interim final rule, probably by fall 2026, probably aimed at models and access rather than chips." — Miller & Chevalier mid-year update ([link](https://www.millerchevalier.com/publication/bis-export-controls-2025-year-review-and-2026-mid-year-update))
