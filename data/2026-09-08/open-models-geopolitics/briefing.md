# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-09-08
**Query type:** GENERAL
**Sources:** WebSearch, WebFetch, BenchLM, Bloomberg, TechNode, TechTimes, Foreign Policy, Business Standard, Releasebot, Polymarket, Qiita (🇯🇵), CSDN (🇨🇳), Zhihu (🇨🇳), V2EX (🇨🇳), Guancha (🇨🇳)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| YouTube | 0 | — | Not searched |
| Hacker News | 0 | — | No qualifying threads found |
| TikTok | 0 | — | Not searched |
| Instagram | 0 | — | Not searched |
| Bluesky | 0 | — | 🦋 OK per SOURCE HEALTH; no qualifying posts found on this topic |
| Polymarket | 5 markets | ~$684K volume | 🌐 Chinese AI Co., model competition |
| Web (global) | 52 pages | — | 🌐 via WebSearch + WebFetch; news, analysis, benchmarks |
| Web (Japan) | 6 pages | — | 🇯🇵 Qiita (4), Zenn (1), labmemo (1); DuckDuckGo HTML CAPTCHA-blocked, fell back to WebSearch |
| Web (China) | 14 pages | — | 🇨🇳 Zhihu (6), Guancha (1), V2EX (1), Tencent News (1), jdon (1), 80aj (1), EET China (1), MOFCOM (1), ITBear (1); DuckDuckGo HTML CAPTCHA-blocked |

---

## Synthesized Findings

### 1. [new] DeepSeek Orders 160K Huawei Ascend 950DT — $2.56B Inference Megacluster 🌐🇨🇳
**Claim:** DeepSeek placed a ~$2.56B order for 160,000 Huawei Ascend 950DT chips for a 1 GW data center in Ulanqab, Inner Mongolia — largest known domestic AI chip cluster; inference-only use while Nvidia retained for training.
- **Order details:** 160,000 Ascend 950DT units; ¥111,000/chip (~$16,500); total ~¥17.76B (~$2.56B); Bloomberg confirmed Sep 4
- **Purpose:** Inference only (model serving); DeepSeek continues Nvidia GPUs for training — "four Huawei chips ≈ one Nvidia GPU" in compute equivalence (jdon.com)
- **Co-design:** DeepSeek + Huawei jointly designing Ascend super nodes to reduce long-text inference latency and improve throughput
- **Site:** Ulanqab (乌兰察布), Inner Mongolia; chosen for cheap electricity (0.35 yuan/kWh), cold climate, proximity to Beijing; 1 GW power target ≈ 750,000 homes
- **Timeline:** Full delivery >1 year (HBM memory shortages limit 950DT output to hundreds of thousands in 2026)
- **Data sovereignty angle (TechTimes):** All inference queries will be processed on PRC-domiciled hardware under PRC law — legal implication for any non-Chinese user of DeepSeek API
- **Parallel Nvidia procurement:** Unverified reports of parallel Blackwell procurement for same site
- **Chinese community** (Guancha, Tencent News, ITBear): "打造目前已知最大国产AI集群之一" (creating one of the largest known domestic AI clusters); reaction mostly positive; production bottleneck noted
- **Context:** DeepSeek V4 already running on Ascend 950PR (CANN not CUDA) since April 2026; ByteDance/Tencent/Alibaba also competing to order Huawei chips (Zhihu)
- **Sources:** https://technode.com/2026/09/07/deepseek-huawei-ascend-950dt-chips-inner-mongolia/ | https://www.bloomberg.com/news/articles/2026-09-04/deepseek-plans-big-huawei-ai-chip-order-to-power-new-data-center | https://www.techtimes.com/articles/326755/20260905/deepseeks-160000-chip-huawei-order-puts-prc-law-over-every-api-query.htm | https://aiweekly.co/alerts/deepseek-plans-160000-huawei-ascend-chips-for-1gw-ulanqab-site | https://www.tftc.io/deepseek-huawei-ascend-160000-chips-inner-mongolia-nvidia-sanctions | https://xenospectrum.com/en/deepseek-huawei-ascend-950dt-160k-order/ | https://www.bighatgroup.com/blog/china-ai-weekly-2026-09-06/ | https://www.jdon.com/94732-deepseek-huawei-ascend-950dt-160000-chips.html | https://www.guancha.cn/economy/2026_09_05_830131.shtml | https://news.qq.com/rain/a/20260905A0BYZ900 | https://www.itbear.com.cn/html/2026-09/1542397.html | https://zhuanlan.zhihu.com/p/2033205180116809204 | https://zhuanlan.zhihu.com/p/2031000322362041773

### 2. [update] BenchLM Sep 8 Recalibration: Qwen3.8 Max #1, Hy4 Drops to #13 🌐
**Claim:** BenchLM underwent another significant recalibration by Sep 8 — Hy4 preview dropped from #1 (78.2-78.5 on Sep 4) to #13 (61.04); Qwen3.8 Max now #1 at 71.62; GLM-5.3 rose to #2 at 68.36.
- **New fact since Sep 4:** Full leaderboard reshuffle; 104 curated open-weight models; Hy4 preview fell 17+ points
- **Current top-5 open-weight (Sep 8):** Qwen3.8 Max 71.62 (#1) | GLM-5.3 68.36 (#2) | GLM-5.2 68.11 (#3) | GLM-5.3-Flash 66.04 (#4) | Kimi K2.7 Code 65.51 (#5)
- **#6-15:** Kimi K2.6 65.41 | Ornith-1.5-397B 65.2 | Qwen3.8-27B 64.44 | dots3-note Preview 64.24 | GLM-5.1 63.47 | MiniMax M3 61.5 | GLM-5 61.45 | Hy4 preview 61.04 (#13) | Hy3 60.94 | Inkling 60.29
- **Chinese dominance:** All top 14 from Chinese labs; Inkling (Thinking Machines Lab) first non-Chinese model at #15
- **Calibration note:** Scores dropped across the board vs Sep 4; consistent with another methodology recalibration; BenchLM overall board has Qwen3.8 Max at #10 of 411 all models (72.43/100 on larger board)
- **Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/models/qwen3-8-max | https://benchlm.ai/models/hy4-preview

### 3. [update] Kimi K3 US Cloud Talks: 30% Revenue-Share Demand, No Deal Yet 🌐🇨🇳
**Claim:** Moonshot AI negotiating with Microsoft (Azure), Amazon (AWS), and Google (GCP) to host Kimi K3 at 30% revenue share — potential first Chinese AI/US cloud revenue-sharing pact; no finalized deal as of Sep 8.
- **New fact since Sep 4:** 30% revenue-share ask confirmed (The Next Web, Quartz); People's Daily framing: "exposing rift between Washington narrative and market reality"
- **Outstanding issues:** Revenue split; data access protocols; auditing of token usage
- **Scale request:** Revenue from K3-related services on Azure/AWS/GCP
- **Geopolitical tension:** US Treasury Bessent still has sanctions threat on table; Moonshot disputes distillation allegations
- **People's Daily Sep 1:** US cloud giants negotiating despite White House anti-Moonshot posture — market vs policy gap
- **Sources:** https://thenextweb.com/news/moonshot-k3-revenue-sharing-us-clouds | https://www.business-standard.com/world-news/moonshot-ai-in-talks-with-microsoft-amazon-google-over-k3-revenue-sharing-126082600532_1.html | https://qz.com/moonshot-ai-kimi-k3-revenue-sharing-microsoft-amazon-google-082626 | http://en.people.cn/n3/2026/0901/c90000-20494495.html | https://invezz.com/news/2026/08/26/moonshot-ai-discusses-kimi-k3-hosting-deals-with-microsoft-amazon-google-report/ | https://finance.yahoo.com/technology/ai/articles/google-microsoft-amazon-could-open-175433833.html

### 4. [update] Trump-Xi AI Pre-Talks Active; Foreign Policy Sep 8: "AI Was Elephant in Room" 🌐
**Claim:** US-China AI pre-talks proceeding ahead of Sep 24 summit; Foreign Policy Sep 8 piece confirms "AI Was the Elephant in Room" at May summit; both sides see this as highest-stakes bilateral agenda item.
- **New fact since Sep 4:** Foreign Policy Sep 8 analysis ("AI Talks: U.S. and China Can Cooperate Without a Grand Bargain") elevates AI pre-talks as primary agenda; Business Standard Sep 5 confirms "AI safety in September" discussions
- **US agenda:** Frontier model proliferation; IP protection; export controls enforcement
- **China agenda:** US restrictions on Chinese open-weight models; control of future US frontier model releases
- **SCMP:** Trump says visit "exciting"; claims US leads China in AI race
- **Structure:** Bessent-led US delegation; pre-summit AI safety talks to precede Sep 24 summit proper
- **Sources:** https://foreignpolicy.com/2026/09/08/us-china-ai-negotiations-safety-governance-trump-xi-summit/ | https://www.business-standard.com/world-news/us-china-may-discuss-ai-safety-in-september-ahead-of-trump-xi-summit-126090500304_1.html | https://www.csis.org/programs/trump-xi-2026-summits | https://www.scmp.com/news/china/diplomacy/article/3366162/trump-calls-xis-washington-visit-exciting-claims-us-leads-china-ai-race

### 5. [update] WAICO Grows to 37 Members; Lawfare Frames It as Digital Silk Road 2.0 🌐🇨🇳
**Claim:** WAICO expanded from 29 founding (Jul 16) to 37 members by late July (Iran among additions); Lawfare analysis: China's open-weight AI strategy is Huawei telecom playbook replayed — "give the weights, sell the stack, own the dependency."
- **New fact since Sep 4:** Lawfare "Open-Weight Diplomacy" piece post-Sep 4 adds "Digital Silk Road" analytical frame; WAICO member count 37 confirmed (vs. prior 29)
- **WAICO members (29 founding → 37):** Algeria, Belarus, Brazil, Cambodia, China, Congo, Cuba, Ethiopia, Indonesia, Kazakhstan, Kenya, Kyrgyzstan, Laos, Lesotho, Malaysia, Myanmar, Mozambique, Nicaragua, Oman, Pakistan, Russia, Senegal, Serbia, South Africa, Tajikistan, Uzbekistan, Venezuela, Zambia + Iran + 7 others
- **Lawfare "Digital Silk Road" framing:** "Give the weights away, sell the stack around it, own the dependency" — mirrors Huawei telecom strategy in Global South
- **Supporting data:** Huawei opened cloud regions in Egypt; pledged 150K trained in sub-Saharan Africa; 300K in Pakistan; 8 Chinese chipmakers achieved DeepSeek V4 day-0 compatibility
- **Alibaba Cloud:** Uses open-weight Qwen as "funnel into Alibaba Cloud" justifying $17B/year new infrastructure spending
- **Sources:** https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road | https://en.wikipedia.org/wiki/World_Artificial_Intelligence_Cooperation_Organization | https://thediplomat.com/2026/07/chinas-new-ai-club-the-world-artificial-intelligence-cooperation-organization/ | https://www.techtimes.com/articles/320812/20260717/china-launches-rival-ai-governance-bloc-waic-2026-opens-300-product-debuts.htm | https://aiangst.com/china/world-ai-cooperation-organization | https://www.cigionline.org/articles/will-china-keep-its-ai-models-open-source-waico-and-kimi-k3-suggest-yes-for-now/

### 6. [update] EU AI Office Sends RFIs to GPAI Providers (Aug 29); Chinese Companies Included 🌐
**Claim:** EU AI Office formally sent requests for information Aug 29 to GPAI providers across regions; Chinese providers subject given Alibaba Cloud + ByteDance EU subsidiaries (3% global turnover fine exposure).
- **New fact since Sep 4:** RFIs dispatched Aug 29 — next enforcement step after Aug 2 activation
- **Scope:** Model security, independent external evaluations, market monitoring
- **Penalties:** Up to 3% of annual global revenue for GPAI providers
- **Chinese exposure:** Alibaba Cloud and ByteDance EU subsidiaries against which fines can be collected
- **SSRN paper:** "Frontier AI Safety Laws and Chinese AI Companies: Applicability and Enforcement" — legal analysis of cross-border applicability
- **Sources:** https://tokenstead.ai/guides/eu-ai-act-first-enforcement-security-rfis | https://www.helpnetsecurity.com/2026/08/04/eu-ai-act-enforcement-ai-models/ | https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6106566 | https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/

---

**Still true (ongoing from prior briefing):**
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon (Sep 3, 375B-A23B, Apache 2.0, 6 models); UAE sovereign AI play; fully open including training data; still the latest fully-open frontier model
- `kimi-k3-gpu-crunch-subscription-pause` / `kimi-k3-weights-open-source` — Moonshot HKEX IPO still in process; Kimi K3 (2.8T, Kimi K3 License); ARR $300M; cloud deal negotiations active (see finding #3)
- `qwen-3-8-max-open-weights-pending` — Qwen3.8-Max-0902 snapshot still #1 on BenchLM; Code Arena WebDev #1 at 1,691 pts
- `china-domestic-chip-mass-pivot` — Ascend 950PR 450K+ shipped; domestic market >52.3% Q1 2026; DeepSeek 160K order confirms inference pivot (see finding #1)
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash (MIT, 320B-A18B) 50% promo through Sep 9; standard pricing resumes
- `polymarket-chinese-ai-august` — Sep markets: Alibaba 72% (-5pp), Moonshot 55% (+3pp), Z.ai 62% (+2pp); volumes ~$315K total
- `us-china-ai-safety-talks-sep24` — Summit still Sep 24; pre-talks active (see finding #4)
- `trump-diffusion-rule-remote-compute` — BIS remote compute rules by Sep 30; Nvidia customer whitelist dropping >50% Asian customers
- `tencent-hy4-preview-apache` — Hy4 preview (770B-A49B, Apache 2.0): BenchLM #13 at 61.04 (post-recalibration)
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3 weights (744B-A40B MoE); KingBench 91.25%; BenchLM #2 at 68.36 (recalibrated up from #8)
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next (125B-A6B, qwen-community-1.0); BenchLM #17 at 58.56
- `minimax-h1-2026-agent-dividend` — ARR >$800M; H1 revenue $116.6M (+283% YoY)
- `open-weight-licensing-bifurcation` — "Enclosure turn" holds: MIT/Apache small, conditional large; pattern unchanged
- `deepseek-v4-flash-vision-exp` — V4 still current; V5 leaks suggest September but unconfirmed; official models: v4-flash, v4-pro, v4-flash-vision-exp
- `meta-muse-glimmer-us-open-weight` — Muse Glimmer (30B, Apache 2.0); Spark 1.2 still not released
- `dots3-note-preview-rednote` — dots3-note Preview: BenchLM #9 at 64.24 (recalibrated)
- `ornith-1-5-self-improving` — Ornith-1.5 (MIT, 397B MoE): BenchLM #7 at 65.2
- `qwen3-8-27b-apache-multimodal` — Qwen3.8-27B (Apache 2.0): BenchLM #8 at 64.44
- `mistral-glm52-eu-sovereign-hosting` — Mistral Agentic Search; OCR 4.1 (Aug 30); GLM-5.2 on EU endpoints; EU AI Office RFIs sent Aug 29
- `agents-a1-internsciense-new-entrant` — InternScience Agents-A1; no new BenchLM position found
- `deepseek-harness-v01-price-hike` — DeepSeek Harness 144K+ stars; V4-Pro pricing unchanged
- `us-moonshot-distillation-sanctions` — No enforcement; cloud negotiations (see finding #3) highlight policy-market gap
- `openai-hf-cyberattack-glm-defense` — No new reports
- `deepseek-zhipu-self-chip-development` — DeepSeek 160K Huawei order (inference); DeepSeek own inference chip development continues separately (early stage)
- `open-weights-decelerationist-accelerationist` — RedMonk Sep 3 adds: 63% OpenRouter token share from Chinese models; accelerationist dominance confirmed empirically
- `openeurollm-european-sovereign` — First year progress: MixtureVitae dataset; no flagship; compute resource challenges persist
- `mistral-frontier-moe-silent` — Day ~126 partner early access; frontier MoE still silent
- `double-curtain-us-china-export-controls` — US BIS remote compute rules by Sep 30; MOFCOM AI controls still consultation; Lawfare "Digital Silk Road" adds third dimension (WAICO scaffolding)
- `kimi-k3-eda-chip-design` — No new reports on Kimi EDA chip design
- `minimax-m3-pro-2-7t` — MiniMax M3 at BenchLM #11 (61.5); 2.7T unconfirmed
- `tencent-hy3-295b` — Hy3 (295B/21B, Apache 2.0): BenchLM #14 at 60.94
- `china-mofcom-export-controls-ai` — Three-tier framework still consultation; MOFCOM official statement vs US sanctions accusations; V2EX debate ongoing
- `glm-5-5-expected-august` — August missed; Sep-Oct 2026 window; no Zhipu announcement
- `eu-ai-act-august-enforcement` — GPAI enforcement active; RFIs sent Aug 29 (see finding #6)
- `ai-manifesto-war-pacing-frontier` — Three frameworks live; WAICO adds fourth (Global South AI governance cluster)
- `chinese-military-pla-distillation-reuters` — No new reports
- `xiaomi-mimo-frontier-entry` — MiMo-V2.5-Pro: no new BenchLM position found
- `distillation-scale-data` — No new enforcement; US cloud negotiations with Moonshot complicate sanctions narrative
- `nemotron-3-ultra-us-open-weight` — Outside top-15; Chinese models dominant
- `polymarket-chinese-ai-company` — Sep market active; Alibaba 72% best Chinese
- `inkling-small-thinking-machines` — Inkling: BenchLM #15 at 60.29; first non-Chinese in top 15
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0, Aug 4); no new updates
- `minimax-h3-geo-license-restriction` — H3 video (33B); US/EU/UK/Korea excluded; Hollywood litigation ongoing
- `deepseek-autonomous-cyberattack-hermes` — No new reports
- `industry-coalition-open-weights-letter` — 235+ signatories (RedMonk: 235 vs prior 270+); Anthropic still sole major holdout
- `databricks-enterprise-glm-migration` — GLM Coding Plan users on GLM-5.3; enterprise adoption unchanged
- `chinese-models-global-share-30pct` — Chinese models 63% OpenRouter enterprise tokens Aug 2026 (up from prior 82% total volume figure; may be different metric); a16z: 80% VC portfolio using Chinese open-source
- `xi-waic-open-source-mandate` — WAICO now 37 members; "Digital Silk Road" framing confirmed by Lawfare
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 still on Mistral EU endpoints; superseded by GLM-5.3 API
- `nvidia-h200-china-trivial` — Nvidia China revenue H200 <1% of datacenter (down from 26.4% in 2022); remote compute whitelist dropping >50% Asian customers
- `deepseek-chip-ascend-950dt` — 950DT cluster order confirmed (see finding #1); 950DT inference-only
- `jp-deepseek-japanese-cultural-benchmark` — JP community: @TaichiEndoh (Apr) adds practical risk framework; @tokencnn (Jun) confirms GLM-5 best for Japanese tasks

---

## Cross-Source Patterns

### Pattern 1: Inference Goes Domestic — DeepSeek's Two-Tier Architecture 🌐🇨🇳
- **Signal:** DeepSeek V4 on Nvidia for training; 160K Ascend 950DT for inference — deliberate bifurcation
- **Platforms:** Bloomberg, TechNode, Guancha, Zhihu, jdon
- **Significance:** Inference moves to PRC legal jurisdiction; training remains Nvidia-dependent (export controls barrier); this split may become the template for all Chinese AI labs
- **Quote:** "DeepSeek计划在内蒙古部署至少16万张华为昇腾950DT，打造目前已知最大国产AI集群之一" — ITBear (https://www.itbear.com.cn/html/2026-09/1542397.html)

### Pattern 2: "Give the Weights, Own the Stack" — Open-Weight Diplomacy Thesis Gains Analytical Consensus 🌐
- **Signal:** Lawfare "Digital Silk Road", CIGI "for now" analysis, CSIS, RedMonk all arriving at same frame: Chinese open weights are strategic infrastructure play, not generosity
- **Platforms:** Lawfare, CIGI, CSIS, RedMonk, AI Supremacy; JP: @sukimaengineer Qiita; CN: Zhihu CSIS repost
- **Data convergence:** 63% OpenRouter enterprise tokens (Aug 2026); a16z 80% VC portfolio; Huawei cloud expanding Global South; WAICO at 37 nations
- **Quote:** "Give the weights away, sell the stack around it, own the dependency." — Lawfare (https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road)

### Pattern 3: Policy-Market Schism — US Government vs US Cloud Corporations 🌐
- **Signal:** White House/Treasury threatening sanctions on Moonshot; simultaneously Microsoft/Amazon/Google negotiating to host Kimi K3 at 30% revenue share
- **Platforms:** Quartz, The Next Web, Business Standard, People's Daily (via foreign lens)
- **People's Daily:** "Exposing rift between Washington narrative and market reality" (http://en.people.cn/n3/2026/0901/c90000-20494495.html)
- **Significance:** US cloud giants' market incentives directly contradicting stated government AI policy — deal would be first Chinese AI/US cloud revenue-sharing pact

### Pattern 4: V2EX "Great Wall" vs Lawfare "Digital Silk Road" — Two Frames, Same Data 🌐🇨🇳
- **Signal:** Chinese developers on V2EX: "the only moat for domestic models is that wall" (forced domestic use, skeptical of genuine advantage); Lawfare/Western analysts: "it's infrastructure capture" (strategic dominance)
- **Platforms:** V2EX (CN), Lawfare (global), RedMonk (global)
- **Insight:** Same open-weight strategy read as defensive (CN view: "we need the wall to survive") and offensive (Western view: "wall is the delivery mechanism for dependency") simultaneously — neither is wrong

---

## Per-Platform Tables

**Polymarket:** 🌐
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company — September | Alibaba 72% | $203K | https://polymarket.com/predictions/ai-technology |
| Second-Best Chinese AI Company — September | Moonshot 55% | $82.9K | https://polymarket.com/predictions/ai-technology |
| Third-Best Chinese AI Company — September | Z.ai 62% | $29.5K | https://polymarket.com/predictions/ai-technology |
| Chinese company has best global AI model by Dec 31 | 9% Yes | $232K | https://polymarket.com/event/will-a-chinese-company-have-the-best-ai-model-by-december-31 |
| US Government removes public access to major Chinese AI model in 2026 | ~26% Yes | $15.1K | https://polymarket.com/predictions/ai-technology |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Bloomberg (Sep 4) | https://www.bloomberg.com/news/articles/2026-09-04/deepseek-plans-big-huawei-ai-chip-order-to-power-new-data-center | DeepSeek 160K Ascend 950DT order; original report |
| 🌐 | TechNode (Sep 7) | https://technode.com/2026/09/07/deepseek-huawei-ascend-950dt-chips-inner-mongolia/ | Inference-only; co-design with Huawei |
| 🌐 | TechTimes (Sep 5) | https://www.techtimes.com/articles/326755/20260905/deepseeks-160000-chip-huawei-order-puts-prc-law-over-every-api-query.htm | PRC law/data sovereignty angle |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/deepseek-plans-160000-huawei-ascend-chips-for-1gw-ulanqab-site | 1GW power scale |
| 🌐 | TFTC | https://www.tftc.io/deepseek-huawei-ascend-160000-chips-inner-mongolia-nvidia-sanctions | Nvidia sanctions context |
| 🌐 | Xenospectrum | https://xenospectrum.com/en/deepseek-huawei-ascend-950dt-160k-order/ | Technical specs breakdown |
| 🌐 | Big Hat Group (Sep 6) | https://www.bighatgroup.com/blog/china-ai-weekly-2026-09-06/ | China AI Weekly digest |
| 🌐 | Foreign Policy (Sep 8) | https://foreignpolicy.com/2026/09/08/us-china-ai-negotiations-safety-governance-trump-xi-summit/ | US-China AI talks; "elephant in room" |
| 🌐 | Business Standard (Sep 5) | https://www.business-standard.com/world-news/us-china-may-discuss-ai-safety-in-september-ahead-of-trump-xi-summit-126090500304_1.html | AI safety pre-talks Sep 2026 |
| 🌐 | SCMP | https://www.scmp.com/news/china/diplomacy/article/3366162/trump-calls-xis-washington-visit-exciting-claims-us-leads-china-ai-race | Trump framing: US leads AI race |
| 🌐 | CSIS | https://www.csis.org/programs/trump-xi-2026-summits | Summit tracker |
| 🌐 | Quartz | https://qz.com/moonshot-ai-kimi-k3-revenue-sharing-microsoft-amazon-google-082626 | Kimi K3 30% revenue share |
| 🌐 | The Next Web | https://thenextweb.com/news/moonshot-k3-revenue-sharing-us-clouds | Cloud deal details |
| 🌐 | Business Standard (Aug 26) | https://www.business-standard.com/world-news/moonshot-ai-in-talks-with-microsoft-amazon-google-over-k3-revenue-sharing-126082600532_1.html | Microsoft/Amazon/Google Kimi K3 talks |
| 🌐 | Lawfare | https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road | "Digital Silk Road" open-weight framing |
| 🌐 | CIGI | https://www.cigionline.org/articles/will-china-keep-its-ai-models-open-source-waico-and-kimi-k3-suggest-yes-for-now/ | China open-weight trajectory |
| 🌐 | The Diplomat (Jul) | https://thediplomat.com/2026/07/chinas-new-ai-club-the-world-artificial-intelligence-cooperation-organization/ | WAICO analysis |
| 🌐 | Wikipedia | https://en.wikipedia.org/wiki/World_Artificial_Intelligence_Cooperation_Organization | WAICO full member list 37 |
| 🌐 | RedMonk (Sep 3) | https://redmonk.com/sogrady/2026/09/03/open-weight-models/ | 63% OpenRouter enterprise tokens Chinese models |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | $8B National AI Fund; a16z 80% figure |
| 🌐 | Value Add VC | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition | Huawei 50-60% China chip market |
| 🌐 | CFR | https://www.cfr.org/articles/chinas-ai-chip-deficit-why-huawei-cant-catch-nvidia-and-us-export-controls-should-remain | Huawei 5× gap; 17× by 2027 |
| 🌐 | Semiconductors Insight | https://semiconductorsinsight.com/us-china-chip-export-controls-h200-2026/ | Remote compute controls; customer whitelist |
| 🌐 | Chatham House | https://www.chathamhouse.org/2026/04/ai-export-controls-are-not-best-bargaining-chip | Export controls accelerating domestic dev |
| 🌐 | Geopolitical Monitor | https://www.geopoliticalmonitor.com/us-export-controls-and-chinas-good-enough-ai-stack/ | China "good enough" sovereign AI stack |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Current open-weight leaderboard Sep 8 |
| 🌐 | BenchLM | https://benchlm.ai/models/qwen3-8-max | Qwen3.8 Max model page |
| 🌐 | BenchLM | https://benchlm.ai/models/hy4-preview | Hy4 preview model page |
| 🌐 | Tech-ish | https://tech-ish.com/2026/09/04/deepseek-turns-to-huawei-for-160000-ai-chips-as-nvidia-stays-locked-out-of-china/ | Nvidia locked-out angle |
| 🌐 | tokenstead.ai | https://tokenstead.ai/guides/eu-ai-act-first-enforcement-security-rfis | EU AI Office RFIs Aug 29 |
| 🌐 | Help Net Security | https://www.helpnetsecurity.com/2026/08/04/eu-ai-act-enforcement-ai-models/ | EU AI Act enforcement Aug 2 start |
| 🌐 | SSRN | https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6106566 | Chinese AI companies and EU AI Act |
| 🌐 | People's Daily (Sep 1) | http://en.people.cn/n3/2026/0901/c90000-20494495.html | PRC official: US cloud/China AI market reality gap |
| 🌐 | OpenEuroLLM | https://openeurollm.eu/blog/first-year-progress-and-next-steps | First year progress; MixtureVitae dataset |
| 🌐 | Releasebot | https://releasebot.io/updates/mistral | Mistral: no new frontier model Sep 2026 |
| 🌐 | GLM 5.5 app | https://glm5.app/glm-5-5 | GLM-5.5: still unreleased; Sep-Oct window |
| 🌐 | deepseek.ai blog | https://deepseek.ai/blog/deepseek-v5-release-date-rumors | DeepSeek V5: no official announcement |
| 🌐 | Modern Diplomacy | https://moderndiplomacy.eu/2026/05/25/huawei-unveils-major-chip-design-breakthrough-as-china-pushes-past-us-sanctions/ | Huawei chip design advances |
| 🌐 | AI Angst | https://aiangst.com/china/world-ai-cooperation-organization | WAICO: US not a member |
| 🌐 | Quartz | https://qz.com/us-china-ai-talks-trump-bessent-september-072126 | Bessent-led talks |
| 🌐 | hidekazu-konishi.com | https://hidekazu-konishi.com/entry/open_weights_llm_release_history_and_timeline.html | Open-weight release history timeline |
| 🌐 | TechPolicy.Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | MOFCOM analysis |
| 🌐 | 80aj | https://www.80aj.com/2026/07/08/china-ai-export-controls/ | Tiered AI export controls proposal detail |
| 🌐 | Mason AI Lab | https://masonailab.com/insights/china-restricts-own-ai-models-export-2026/ | Taiwan Chinese: "mirror reversal of chip war" |
| 🌐 | EET China | https://www.eet-china.com/news/202607247090.html | China AI export control consideration |
| 🌐 | MOFCOM | https://www.mofcom.gov.cn/syxwfb/art/2026/art_7f1622463a7c48ef9fad600ce0ef702f.html | MOFCOM official US sanctions statement |
| 🇯🇵 | Qiita (@TaichiEndoh, Apr 2026) | https://qiita.com/TaichiEndoh/items/1a5c829e8568a16ea834 | Geopolitical risk framework for engineers adopting Chinese AI |
| 🇯🇵 | Qiita (@tokencnn, Jun 2026) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese AI models 2026 comparison; GLM-5 best for Japanese tasks |
| 🇯🇵 | Qiita (@etale_cohomology, Jun 2026) | https://qiita.com/etale_cohomology/items/5043330f12d891d5c27e | China Physical AI + World Models stack; US-China 2.7% Elo gap |
| 🇯🇵 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900 | China open-weight infrastructure dominance thesis |
| 🇯🇵 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | Kimi K3 / Qwen3.8-Max / DeepSeek V4-Pro deep-dive |
| 🇯🇵 | labmemo.com | https://labmemo.com/llm-llama-deepseek-qwen-mistral-gemma-2026/ | Japanese LLM comparison 2026 |
| 🇨🇳 | Guancha (Sep 5) | https://www.guancha.cn/economy/2026_09_05_830131.shtml | DeepSeek 160K Huawei; Chinese public reaction |
| 🇨🇳 | ITBear (Sep 2026) | https://www.itbear.com.cn/html/2026-09/1542397.html | Inner Mongolia cluster details |
| 🇨🇳 | jdon.com | https://www.jdon.com/94732-deepseek-huawei-ascend-950dt-160000-chips.html | 4 Huawei = 1 Nvidia; inference pivot |
| 🇨🇳 | Tencent News (Sep 5) | https://news.qq.com/rain/a/20260905A0BYZ900 | DeepSeek 160K order coverage |
| 🇨🇳 | Coder Liang | https://coderliang.com/posts/2148bf4e-af6c-49e5-8477-d82ceecea697 | Inner Mongolia 160K chip cluster |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2024565159583031612 | DeepSeek V4 abandoning CUDA → CANN |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2031000322362041773 | DeepSeek V4 on Ascend super nodes |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2033205180116809204 | ByteDance/Tencent/Alibaba ordering Huawei chips |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2032454554143412892 | DeepSeek V4: domestic chip ecosystem inflection |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2031114969861899858 | Cambricon day-0 DeepSeek V4 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2048464721083470807 | Chinese AI ecosystem panorama 2026 |
| 🇨🇳 | V2EX | https://www.v2ex.com/t/1225707 | Community debate: export controls "only moat is the wall" |
| 🇨🇳 | 80aj (Jul 8) | https://www.80aj.com/2026/07/08/china-ai-export-controls/ | Three-tier export control framework |
| 🇨🇳 | MOFCOM | https://www.mofcom.gov.cn/syxwfb/art/2026/art_7f1622463a7c48ef9fad600ce0ef702f.html | Official: US accusations are sovereign interference |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 0 stories
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (SOURCE HEALTH: OK; no qualifying open-models posts found)
├─ 📊 Polymarket: 5 markets │ ~$563K volume
├─ 🌐 Web: 52 pages │ 🇯🇵 6 │ 🇨🇳 14
└─ 🗣️ Top voices: @sukimaengineer (Qiita) │ Bloomberg │ TechNode │ Foreign Policy │ Lawfare
```

---

## Out of Scope but Notable

- **DeepSeek two-tier inference architecture (training vs inference split):** If DeepSeek's deliberate choice to keep Nvidia for training while pivoting to Huawei for inference becomes a design pattern, it defines a new "hybrid sovereign AI" infrastructure template: performance on training, legal/political compliance on serving. This is an architectural governance decision masquerading as a chip order and may be more significant than any single model release. — https://technode.com/2026/09/07/deepseek-huawei-ascend-950dt-chips-inner-mongolia/ — Belongs partly to a "China AI infrastructure" topic but the inference sovereignty angle is genuinely new.
- **WAICO as multilateral AI governance bloc (Global South):** At 37 nations, WAICO is no longer just diplomatic signaling — it's a parallel multilateral track to the G7/GPAI framework. If it develops enforcement or standards-setting capacity, it changes the geopolitical architecture of AI governance permanently. This belongs partly in a "global AI governance" topic but intersects deeply with open-weight diplomacy here. — https://en.wikipedia.org/wiki/World_Artificial_Intelligence_Cooperation_Organization

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN passes; fell back to WebSearch with language-specific queries. Some hub coverage (Zenn, note.com, Juejin, Aliyun Developer) may be underrepresented as a result.
- **Bluesky:** SOURCE HEALTH = OK but no qualifying open-models/geopolitics posts found Sep 5-8. This topic consistently produces little Bluesky signal.
- **HackerNews:** No significant HN threads on DeepSeek chip order or WAICO found Sep 5-8.
- **DeepSeek V5:** Confirmed no release; September leaks remain unverified.
- **GLM-5.5:** Confirmed no release; Sep-Oct window.
- **Mistral frontier MoE:** Day ~126 partner early access; zero public data.
- **Moonshot HKEX A1 filing:** Confidential; no public prospectus data available.
- **BenchLM recalibration Sep 8:** Hy4 preview went from #1 (78.2) to #13 (61.04) — methodology explanation not publicly disclosed; treating as recalibration, not model regression.
- **Approximate coverage:** 82% — strong on chip/infrastructure, geopolitics, BenchLM; gap in social/video signal and CN community commentary more granular than search result excerpts.

---

## Key Quotes

> "DeepSeek计划在内蒙古部署至少16万张华为昇腾950DT，打造目前已知最大国产AI集群之一" ("DeepSeek plans to deploy at least 160,000 Huawei Ascend 950DT in Inner Mongolia, creating one of the largest known domestic AI clusters") — ITBear ([link](https://www.itbear.com.cn/html/2026-09/1542397.html))

> "Give the weights away, sell the stack around it, own the dependency." — Lawfare, "Open-Weight Diplomacy: How China's AI Models Are Rerunning the Digital Silk Road" ([link](https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road))

> "Exposing rift between Washington narrative and market reality: experts" — People's Daily Online on US cloud giants negotiating Kimi K3 hosting despite White House anti-Moonshot stance ([link](http://en.people.cn/n3/2026/0901/c90000-20494495.html))

> "国内大模型的唯一护城河就是那道墙" ("The only moat for domestic large models is that [Great] wall") — V2EX user on China AI model export controls debate ([link](https://www.v2ex.com/t/1225707))

> "AI was the Elephant in the Room at the Trump-Xi Summit" — Foreign Policy, Sep 8, 2026 ([link](https://foreignpolicy.com/2026/09/08/us-china-ai-negotiations-safety-governance-trump-xi-summit/))

> "Chinese-origin AI models face stricter security reviews due to data sovereignty concerns" (「中国発のAIモデルは、データ主権の懸念でセキュリティレビューが厳しい」) — @TaichiEndoh on Qiita ([link](https://qiita.com/TaichiEndoh/items/1a5c829e8568a16ea834))

> "美国限制高端算力（GPU）出口中国，中国开始限制高端智能（模型权重）出海，AI技术正式成为国家战略资产" ("US restricts GPU exports; China restricts model weight exports; AI technology officially becomes national strategic asset") — 80aj.com ([link](https://www.80aj.com/2026/07/08/china-ai-export-controls/))

> "中国のゴールはアメリカのAI企業を壊すことではなく、中国モデルを世界のデフォルトインフラにすること" ("China's goal is not destroying American AI companies but making Chinese models the world's default infrastructure") — @sukimaengineer on Qiita ([link](https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900))
