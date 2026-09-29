# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-09-29
**Query type:** GENERAL
**Sources:** WebSearch (EN/JP/CN), WebFetch, BenchLM, TechNode, SiliconANGLE, CellCog, Juejin, CSDN, 36kr, Tencent News/QQ, 21jingji, ITHome, 17173, Zhihu, gihyo.jp, Qiita, PC Watch, GIGAZINE, innovatopia, Hacker News, OrcaRouter, Releasebot, Polymarket, EasternHerald, DataStudios, TechStackIPO, CNBC, ExportComplianceDaily, Freshfields, XenoSpectrum, TrendForce, Asia Times, TechPolicy.Press, Chatham House, Stanford HAI

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| YouTube | 0 | — | Not searched |
| Hacker News | 3 stories | N/A | 🌐 MiMo V2.6 threads; 429 on direct fetch |
| TikTok | 0 | — | Not searched |
| Instagram | 0 | — | Not searched |
| Bluesky | 0 | — | SOURCE HEALTH: OK; no qualifying posts |
| Polymarket | 1 market | $53,390 volume | 🌐 CN AI ban 16% Yes, confirmed Sep 29 3:47 PM UTC |
| Web (global) | 43 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Qiita, gihyo.jp, PC Watch, GIGAZINE, innovatopia, note.com, labmemo, ai-revolution.co.jp |
| Web (China) | 14 pages | — | 🇨🇳 Juejin, CSDN, 36kr, Tencent News, 21jingji, ITHome, 17173, Zhihu, Sina, 163 |

---

## Synthesized Findings

### 1. [new] Xiaomi MiMo-V2.6-Pro: #1 Global Open-Weight (BenchLM 74.7) — Consumer Electronics Lab Tops Frontier 🌐🇨🇳🇯🇵

**Claim:** Xiaomi released MiMo-V2.6-Pro (Sep 22, MIT, 1.02T/42B active MoE) and on Sep 28 it entered BenchLM at #1 (74.7) — dethroning Qwen3.8 Max, becoming the highest-scoring open-weight model globally. A consumer electronics company now leads the global frontier open-weight race.

- **Architecture:** 1.02T total params; 42B active/token; sparse MoE (256 experts/layer, 8 activated); 1M context
- **Flash:** 309B total; 15B active; 48 layers (39 SWA + 9 full attention); MIT license
- **Omnimodal:** text, image, video, audio, 3D spatial, computer-use — natively
- **Benchmarks:**
  - BenchLM v5.7: **74.7** (#1 as of Sep 28)
  - Artificial Analysis Intelligence Index v4.3.2: **46.32** (#1 open-weight; vs GLM-5.3: 45, Kimi K3: 44)
  - DeepSWE v1.1: 71.9 (surpasses DeepSeek V4 Pro 0813)
  - AutomationBench v1.0.6: **53.1** (exceeds GPT-6 Astra 52.0)
  - Terminal Bench 4.0: 34.9 (gap vs Claude Fable 5.1 at 52.0 persists)
- **Training:** <6 days; 30 RL iterations; ~750K trajectories; **Pro: $2.62M; Flash: $850K** (total $3.47M)
- **Cost:** Pro ¥3-6/M tokens (~1/20th–1/60th comparable Western models); Flash ¥1-2/M tokens
- **Domestic chip:** Day-zero support for 5 domestic vendors (Huawei Ascend, Biren, Cambricon, Hygon, Montage)
- **Geo-restriction:** MiMo Desktop NOT available in EU, UK, Korea
- **IP release:** 7,000+ RL task environments + mini-harnesses framework (JP media: "the real value released")
- **CN reaction (36kr):** "罗福莉交出小米最强开源模型" ("Luo Fuli [Xiaomi AI chief] delivers Xiaomi's strongest open-source model")
- **JP reaction (Qiita):** License caution flagged — "no explicit LICENSE file; V2.6 omits prior version's 'commercial deployment approved' language; verify before deploying"
- **HN reaction:** Training cost transparency praised; "most comprehensive training disclosure by any Chinese lab"; "starting to wonder if frontier AI barriers are collapsing" (https://news.ycombinator.com/item?id=49812257)
- **Sources:** https://technode.com/2026/09/22/xiaomi-open-sources-mimo-v2-6-models-after-scaling-reinforcement-learning/ | https://siliconangle.com/2026/09/22/xiaomi-introduces-mimo-v2-6-series-open-source-ai-model-family/ | https://cellcog.ai/blog/mimo-v2-6/ | https://juejin.cn/post/7688170325382594560 | https://36kr.com/p/3785761705909512 | https://gihyo.jp/article/2026/09/xiaomi-mimo-v2.6 | https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760 | https://news.ycombinator.com/item?id=49792730 | https://news.ycombinator.com/item?id=49812257 | https://news.ycombinator.com/item?id=49732270 | https://aifrontierpost.com/articles/xiaomi-mimo-v26-open-source-release/ | https://www.eweek.com/news/xiaomi-mimo-v26-open-source-rl-reproduction/ | https://m.21jingji.com/article/20260924/ae90cf5fdaf2ed1648f18016d35524a4.html | https://news.qq.com/rain/a/20260922A053PP00 | https://pc.watch.impress.co.jp/docs/news/2142608.html | https://gigazine.net/gsc_news/en/20260924-mimo-v2-6-pro-flash/ | https://www.testingcatalog.com/xiaomi-open-sources-mimo-v2-6-pro-and-flash-models/

---

### 2. [update] BenchLM Sep 28 Reshuffle: MiMo Tops, V4.1 Flash Enters Top-20, K2.7 Code Falls Off 🌐

**Claim:** BenchLM updated Sep 28 with new model entries — Xiaomi MiMo-V2.6-Pro (#1 at 74.7) and MiMo-V2.6-Flash (#4 at 64.1) reshuffled the board; DeepSeek V4.1 Flash entered the top-20 (#14 at 55.7); Kimi K2.7 Code dropped entirely.

**Current top-10 (Sep 28, BenchAlign v5.7):**

| # | Model | Creator | Score |
|---|-------|---------|-------|
| 1 | MiMo-V2.6-Pro | Xiaomi | **74.7** |
| 2 | Qwen3.8 Max | Alibaba | 71.7 |
| 3 | GLM-5.3 | Z.AI | 65.4 |
| 4 | MiMo-V2.6-Flash | Xiaomi | 64.1 |
| 5 | DeepSeek V4 Pro 0813 | DeepSeek | 64.0 |
| 6 | dots3-note Preview | Dots Studio | 62.6 |
| 7 | GLM-5.2 | Z.AI | 62.6 |
| 8 | Ornith-1.5-397B | Ornith AI | 61.8 |
| 9 | Qwen3.8-Flash-Next | Alibaba | 60.8 |
| 10 | GLM-5.3-Flash | Z.AI | 60.6 |

**Key moves:**
- Xiaomi entered with TWO models in top-4 simultaneously
- Inkling-Small (#15) and Inkling (#19) remain only non-Chinese in top-20
- Kimi K2.7 Code dropped off entirely (was #19 at 50.4 Sep 25)
- GLM-5.3-Flash rose from #9 (58.0) to #10 (60.6)
- DeepSeek V4.1 Flash entered at #14 (55.7) — first time in top-20

- **Source:** https://benchlm.ai/best/open-source

---

### 3. [new] Huawei Ascend 950 Cloud: Commercial Launch TODAY (Sep 30) 🌐🇨🇳

**Claim:** Huawei's "灵衢昇腾950智算集群" cloud service launches for domestic Chinese customers today (Sep 30, 2026), with global launch Nov 30. Transition from chip hardware to commercial cloud service marks a new phase for the Ascend ecosystem.

- **Announced:** Sep 18 at Huawei Connect 2026 by CEO Zhou Yuefeng
- **Specs:** 1,024-card cluster; 1 EFLOPS FP8 / 2 EFLOPS FP4; 256TB unified global memory; 自研 Lingqu interconnect protocol
- **Performance:** Token throughput +20% vs prior generation; 40-day stable cloud training runs; fault recovery <10 min (5-level mechanism)
- **Timeline:** Sep 30 domestic (TODAY) → Nov 30 global
- **Context:** Follows Sep 19 ecosystem inflection point (5,200+ CANN MAU; non-Huawei devs exceed Huawei); 960DT to Q1 2027 (9 months early)
- **CN analyst (CITIC Securities):** China AI chip market to exceed ¥300B in 2026; Bernstein: Huawei targets ~50% domestic AI chip share
- **Sources:** https://www.ithome.com/1/003/981.htm | https://news.17173.com/content/09182026/120317504.shtml | https://news.qq.com/rain/a/20260918A04I5N00 | https://cn.technode.com/post/2026-09-18/huawei-cloud-ascend-950-commercial-service/ | https://finance.sina.com.cn/jjxw/2026-09-18/doc-inishenx0300242.shtml

---

### 4. [update] DeepSeek IPO: Valuation Steps Up to $74-75B; ~$1B ARR 🌐🇨🇳

**Claim:** New facts since Sep 25: DeepSeek's pre-IPO financing round targets ~$74-75B valuation (up from $71B July figure); annualized revenue run rate now ~$1B (more than doubled); 82.9% gross margin through July confirmed.

- **Valuation:** ~500B yuan (~$74-75B) — 48% step-up from June round ($50B+)
- **Revenue:** ~$1B ARR (annualized); gross margin 82.9% through July
- **Underwriter:** CITIC Securities (confirmed)
- **Exchange:** Shanghai STAR Market
- **Timeline:** Q2 2027 IPO target (unchanged)
- **Capital use:** IPO disclosure includes funding for own inference chip development (previously disclosed CUDA→CANN pivot)
- **Sources:** https://www.datastudios.org/post/deepseek-ipo-citic-securities-shanghai-star-market-75-billion-valuation | https://easternherald.com/2026/09/25/deepseek-revenue-billion-shanghai-ipo/ | https://www.techstackipo.com/company/deepseek | https://kraneshares.com/a-complete-guide-to-deepseeks-2026-ipo-what-it-means-for-china-etf-kstr/

---

### 5. [update] Chinese Models Global Adoption: CNBC Sep 26 + "Android Moment" Framing in CN 🌐🇨🇳

**Claim:** New facts since Sep 25: CNBC published Sep 26 citing token usage surge on OpenRouter/Vercel; US lawmakers now actively investigating; Chinese Zhihu analysts frame Huawei Ascend + DeepSeek as "China's Android Moment."

- **CNBC Sep 26:** "Chinese AI models surge in global popularity — and Washington is worried"; lower prices + strong agentic coding performance driving adoption
- **Congressional scrutiny:** US lawmakers investigating growing use of Chinese AI in American developer stacks
- **DeepSeek OpenRouter share:** 16.3% token volume — exceeds Google, Anthropic, OpenAI (per note.com analysis)
- **OpenRouter enterprise:** 63% enterprise tokens from Chinese models (ongoing)
- **CN framing:** 中国AI迎来"安卓时刻" — "Ascend + DeepSeek builds complete AI stack parallel to US ecosystem" (Zhihu)
- **MOFCOM:** Still deliberating overseas access restrictions on advanced Chinese models (no finalization)
- **Sources:** https://www.cnbc.com/2026/09/26/china-ai-global-adoption.html | https://note.com/takutakuai/n/n94b43fd5772f | https://zhuanlan.zhihu.com/p/2026037521889370330 | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/

---

**Still true (ongoing, no new facts since Sep 25):**

- `xi-brics-ai-open-source-zone` — Xi Sep 13 BRICS AI open-source zone (5-component, DeepSeek+Qwen to Global South free); WAICO+BRICS two-layer architecture
- `qwen-image-2-1-open-source` — Qwen-Image-2.1 (Sep 20, 7B, research-only license, unified gen+edit)
- `us-china-ai-safety-talks-sep24` — Trump-Xi Sep 24: first US-China AI Dialogue; chip controls NOT on agenda; trade truce to Jan 10, 2027; no joint statement
- `huawei-ascend-ecosystem-inflection` — Sep 19 inflection point: 5,200+ CANN MAU; non-Huawei devs exceed Huawei; PyTorch supported; 5B yuan 3-year commitment
- `polymarket-us-chinese-model-ban` — 16% Yes; $53,390; confirmed Sep 29 3:47 PM UTC (unchanged from Sep 25)
- `eu-ai-act-august-enforcement` — GPAI Sep 15 deadline passed; no Chinese lab signed Code of Practice; EU enforcement capacity limited
- `trump-diffusion-rule-remote-compute` — BIS Sep 30 deadline TODAY; no Federal Register rule as of Sep 29; inter-agency coordination failures; RASA Senate Banking Committee
- `qwen4-apsara-announcement` — Qwen 4 "in training"; no weights/benchmarks/price; four tiers (Max/Plus/Flash/27B)
- `alibaba-zhenwu-v900-chip` — T-Head Zhenwu V900: 3× M890; 216GB HBM; Q1 2027
- `deepseek-v41-pro-2t-leak` — Still unreleased Sep 29; no entry in API changelog Sep 25-29; speculative window closed
- `huawei-ascend-960-connect2026` — 960DT Q1 2027; 960PR Q3 2027; Atlas 960E SuperPoD 4096 cards 8 EFLOPS; 970/980 roadmap 2028/2029
- `rasa-senate-pending-cloud-loophole` — RASA Senate Banking Committee; no floor vote; Aivres $5.6B Blackwell confirmed; SE Asia loophole ongoing
- `deepseek-v4-1-flash-release` — V4.1 Flash (Sep 10, MIT, 552B MoE); now #14 BenchLM at 55.7
- `deepseek-v4-pro-retirement-reversed` — V4 Pro API continues; now #5 BenchLM at 64.0
- `deepseek-v41-flash-abliteration` — MIT license; 23K+ GGUF downloads; 100% HarmBench-320
- `deepseek-star-market-ipo-citic` — CITIC; $74-75B; $1B ARR; STAR Market Q2 2027 (see finding 4)
- `anthropic-distillation-report-sep10` — 200M exchanges; MOFCOM "groundless"; no enforcement
- `mistral-samsung-series-d-third-axis` — €3B Samsung Series D (€21B); frontier MoE silent; Leanstral 1.5 retiring Sep 30
- `qwen-drive-1-0-apache-av` — Qwen-Drive-1.0-4B (Apache 2.0, HKUST); autonomous driving VLM
- `deepseek-160k-huawei-inner-mongolia` — 160K Ascend 950DT order ($2.56B); delivery >1 year
- `kimi-k3-gpu-crunch-subscription-pause` — HKEX A1 confidential filing; $3B target; $50B; ARR $300M; Q1 2027
- `china-domestic-chip-mass-pivot` — >52.3% domestic Q1 2026; Ascend 50-60% share; Nvidia ~8%
- `xi-waic-open-source-mandate` — WAICO 37-nation (Jul 17 Shanghai) + BRICS AI zone = two-layer multilateral AI structure
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon (375B-A23B, Apache 2.0); still fully-open frontier fleet
- `qwen-3-8-max-open-weights-pending` — Now #2 BenchLM (71.7) — dethroned by MiMo-V2.6-Pro Sep 28
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash: #10 BenchLM (60.6, rose from #9/58.0); Huawei Ascend trained
- `tencent-hy4-preview-apache` — Hy4 preview: #11 BenchLM at 60.3
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3: #3 BenchLM at 65.4
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next: #9 BenchLM at 60.8 (Qwen4 architecture preview)
- `minimax-h1-2026-agent-dividend` — ARR >$800M; H1 revenue $116.6M (+283% YoY)
- `open-weight-licensing-bifurcation` — MIT for small/flash; research-only for image gen (Qwen-Image-2.1); geo-restriction in MiMo Desktop (EU/UK/Korea excluded)
- `deepseek-v4-flash-vision-exp` — All V4 endpoints continue; V4 Pro continues
- `meta-muse-glimmer-us-open-weight` — Outside BenchLM top-20 (all Chinese except Inkling-Small #15, Inkling #19)
- `dots3-note-preview-rednote` — dots3-note Preview: #6 BenchLM at 62.6
- `ornith-1-5-self-improving` — Ornith-1.5-397B: #8 BenchLM at 61.8
- `qwen3-8-27b-apache-multimodal` — Qwen3.8-27B: #16 BenchLM at 55.3
- `mistral-glm52-eu-sovereign-hosting` — GLM-5.2 on EU-sovereign Mistral endpoints; Leanstral 1.5 retiring Sep 30
- `agents-a1-internsciense-new-entrant` — No new position
- `deepseek-harness-v01-price-hike` — V4.1 Flash pricing baseline; concurrency 500→2,500
- `kimi-k3-weights-open-source` — K3 (2.8T MoE, 32B active); Kimi K3 License
- `us-moonshot-distillation-sanctions` — Bessent Jul 22 threat; cloud deal; no enforcement
- `openai-hf-cyberattack-glm-defense` — HuggingFace July breach framing persists
- `deepseek-zhipu-self-chip-development` — CUDA→CANN pivot confirmed; own inference chip in IPO disclosure; Ascend 950 primary training target
- `open-weights-decelerationist-accelerationist` — 63% OpenRouter enterprise tokens Chinese models; 56.72T CN model calls vs 16.54T US
- `openeurollm-european-sovereign` — No new release; Mistral Samsung D separate track
- `mistral-frontier-moe-silent` — Day ~176+ partner early access; zero public data; Leanstral 1.5 retiring Sep 30
- `double-curtain-us-china-export-controls` — BIS Sep 30 deadline TODAY; RASA Senate; chip controls NOT on AI dialogue (Trump-Xi summit)
- `kimi-k3-eda-chip-design` — No new reports
- `minimax-m3-pro-2-7t` — MiniMax M3: #17 BenchLM at 54.8
- `china-mofcom-export-controls-ai` — Still deliberating; no finalization; CNBC Sep 26 confirms ongoing
- `deepseek-chip-ascend-950dt` — 950DT: GA inference; 160K DeepSeek order; 960DT Q1 2027; ecosystem inflection Sep 19; 950 cloud TODAY
- `glm-5-5-expected-august` — GLM-5.4 Oct 8–Nov 9 window per CellCog; no Oct release found
- `ai-manifesto-war-pacing-frontier` — Summit Sep 24 "whoever wins AI wins" (Trump); BRICS AI zone Sep 13; Xi at two-layer multilateral architecture
- `chinese-military-pla-distillation-reuters` — GTG-16002; 300K requests; no enforcement
- `distillation-scale-data` — 200M exchanges; MOFCOM "groundless"; stands
- `nemotron-3-ultra-us-open-weight` — Outside top-20; all-Chinese dominance (top-19 Chinese, only Inkling-Small #15, Inkling #19 non-Chinese)
- `polymarket-chinese-ai-company` — Not re-checked; prior: Alibaba 72% best Chinese AI
- `inkling-small-thinking-machines` — Inkling-Small: #15 BenchLM at 55.7; Inkling #19 at 54.2
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0); no updates
- `minimax-h3-geo-license-restriction` — H3 video geo-restriction (US/EU/UK/Korea excluded); Hollywood litigation
- `deepseek-autonomous-cyberattack-hermes` — No new incident
- `industry-coalition-open-weights-letter` — 235+ signatories; Anthropic sole major holdout
- `databricks-enterprise-glm-migration` — GLM-5.3 enterprise coding; no change
- `chinese-models-global-share-30pct` — CNBC Sep 26 confirms surge; 63% OpenRouter enterprise tokens; 3B Alibaba downloads; 56M Qwen3.8/month
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2: #7 BenchLM at 62.6; Huawei Ascend trained; on Mistral EU endpoints
- `nvidia-h200-china-trivial` — Nvidia ~8% China AI; domestic 90% target 2027; Ascend 950 cloud commercial Sep 30
- `jp-deepseek-japanese-cultural-benchmark` — Mizuho Qwen3-32B; Lion LLM; ~60% JP enterprises on DeepSeek/Qwen (Nikkei)
- `qwen38-omni-flash-agent` — Qwen3.8-Omni-Flash (Sep 17): omnimodal agent
- `qwen-huggingface-ecosystem-dominance` — 3B total downloads; 56M/month; 300K+ derivatives; Perplexity/Airbnb/Pinterest/Reuters deploying

---

## Cross-Source Patterns

### Pattern 1: Consumer Electronics Lab Now Leads Global Open-Weight Frontier 🌐🇨🇳🇯🇵
- **Signal:** Xiaomi MiMo-V2.6-Pro (#1 BenchLM 74.7, AA 46.32) was built by a consumer electronics company — not an AI lab — for $2.62M in <6 days. HN community: "Are frontier AI barriers collapsing?"
- **Platforms:** BenchLM (global); TechNode, 36kr, Juejin, Tencent News (CN); Qiita, gihyo.jp, PC Watch, GIGAZINE (JP); SiliconANGLE, eWeek (EN); Hacker News
- **Key quote (CN, Juejin 🇨🇳):** "六天不到，两百六十多万美元，登顶全球开源榜——这是新的'斩杀线'" ("Less than six days, $2.62 million, topped the global open-source chart — this is the new 'kill line'")
- **Key quote (JP, Qiita 🇯🇵):** "コスト比較: Pro $0.13/タスク vs Claude Fable 5.1 $7.63/タスク — 59倍の差" ("Cost comparison: Pro $0.13/task vs Claude Fable 5.1 $7.63/task — 59× difference")

### Pattern 2: Huawei Stack Transition — From Chips to Cloud 🌐🇨🇳
- **Signal:** Huawei Ascend 950 cloud service launches domestically Sep 30 (TODAY), completing the hardware-to-service transition: 950DT chip (GA) → ecosystem inflection Sep 19 → MoE frontier models trained on Ascend → commercial cloud service Sep 30
- **Platforms:** ITHome, 17173, Tencent News, Sina, 163 (CN); TrendForce, XenoSpectrum (global)
- **CN framing (Zhihu 🇨🇳):** "中国AI迎来'安卓时刻' — 华为昇腾+DeepSeek构建出与美国体系平行的完整AI技术栈" ("China's AI arrives at its 'Android Moment' — Huawei Ascend + DeepSeek builds complete AI stack parallel to US ecosystem")

### Pattern 3: Global Adoption Pressure + Washington Scrutiny Escalate Together 🌐
- **Signal:** CNBC Sep 26 ("Chinese AI models surge globally — Washington worried") + HN community debating if "Xiaomi's $2.62M frontier model" undermines the premise of export controls — adoption and scrutiny are accelerating simultaneously
- **Platforms:** CNBC (global); note.com (JP); Zhihu (CN); HN (global); TechPolicy.Press
- **Key tension:** Open-weight models (MIT license) can be mirrored globally, making any ban technically unenforceable — Polymarket traders confirm this at 16% Yes probability

### Pattern 4: BIS Rule Deadline Without Outcome 🌐
- **Signal:** Sep 30 (TODAY) is BIS's fiscal year end target for AI Diffusion replacement rule — no Federal Register notice found as of Sep 29. Ongoing regulatory purgatory persists.
- **Platforms:** ExportComplianceDaily, Freshfields, Asia Times
- **Key quote:** "Regulatory purgatory — announced rescinded, not enforced, not removed, not replaced"

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (unknown) | MiMo v2.6 | N/A (429 on fetch) | Active | "Starting to wonder if frontier AI barriers are collapsing" | https://news.ycombinator.com/item?id=49792730 |
| (unknown) | Seeing how cheaply Xiaomi trained Mimo 2.6... | N/A | Active | "Are we watching the end of the moat?" | https://news.ycombinator.com/item?id=49812257 |
| (unknown) | Xiaomi Mimo 2.6 live post-training dashboard | N/A | Active | "Most comprehensive training disclosure by any Chinese lab" | https://news.ycombinator.com/item?id=49732270 |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US removes public access to major Chinese AI model in 2026 | **16% Yes** | $53,390 | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | BenchLM (Sep 28) | https://benchlm.ai/best/open-source | MiMo-V2.6-Pro #1 at 74.7; full top-20 |
| 🌐 | TechNode (Sep 22) | https://technode.com/2026/09/22/xiaomi-open-sources-mimo-v2-6-models-after-scaling-reinforcement-learning/ | MiMo-V2.6 release; spec details |
| 🌐 | SiliconANGLE (Sep 22) | https://siliconangle.com/2026/09/22/xiaomi-introduces-mimo-v2-6-series-open-source-ai-model-family/ | MIT license; RL stack; UltraSpeed |
| 🌐 | CellCog | https://cellcog.ai/blog/mimo-v2-6/ | AA Index 46.32; top-5 comparison |
| 🌐 | eWeek | https://www.eweek.com/news/xiaomi-mimo-v26-open-source-rl-reproduction/ | 9B Qwen3.5-based distillation |
| 🌐 | AI Frontier Post | https://aifrontierpost.com/articles/xiaomi-mimo-v26-open-source-release/ | Training cost breakdown; RL environments |
| 🌐 | TestingCatalog | https://www.testingcatalog.com/xiaomi-open-sources-mimo-v2-6-pro-and-flash-models/ | API pricing |
| 🌐 | HN: MiMo v2.6 | https://news.ycombinator.com/item?id=49792730 | Community response; Sep 22 post |
| 🌐 | HN: Training cost | https://news.ycombinator.com/item?id=49812257 | Barrier-collapse debate |
| 🌐 | HN: Dashboard | https://news.ycombinator.com/item?id=49732270 | Xiaomi training transparency |
| 🌐 | EasternHerald (Sep 25) | https://easternherald.com/2026/09/25/deepseek-revenue-billion-shanghai-ipo/ | DeepSeek $1B ARR; $74-75B IPO |
| 🌐 | DataStudios | https://www.datastudios.org/post/deepseek-ipo-citic-securities-shanghai-star-market-75-billion-valuation | $74-75B valuation details |
| 🌐 | TechStackIPO | https://www.techstackipo.com/company/deepseek | $115B speculative ceiling |
| 🌐 | Releasebot DeepSeek | https://releasebot.io/updates/deepseek | Sep 10 last entry; V4.1 Pro unreleased |
| 🌐 | DeepSeek API | https://api-docs.deepseek.com/updates/ | V4.1 Pro still unreleased Sep 29 |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/deepseek-v4-1-pro-leak | Sep 28-30 window closing without release |
| 🌐 | CNBC (Sep 26) | https://www.cnbc.com/2026/09/26/china-ai-global-adoption.html | Chinese AI surge globally; WA scrutiny |
| 🌐 | ExportComplianceDly | https://exportcompliancedaily.com/article/2026/07/08/bis-targets-end-of-fiscal-year-for-ai-diffusion-rule-replacement-2607070013 | BIS Sep 30 deadline |
| 🌐 | Polymarket (Sep 29) | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 | 16% Yes; $53,390 |
| 🌐 | TrendForce (Sep 17) | https://www.trendforce.com/news/2026/09/17/news-huawei-speeds-up-ai-chip-roadmap-reportedly-pulls-ascend-960dt-forward-three-quarters-to-1q27/ | 960DT pulled 9 months forward |
| 🌐 | XenoSpectrum | https://xenospectrum.com/en/huawei-ascend-960dt-superpod-roadmap/ | Full 960 roadmap |
| 🌐 | Asia Times (Sep) | https://asiatimes.com/2026/09/nvidia-chip-export-loophole-clouds-us-china-ai-summit-talks/ | Cloud loophole summit context |
| 🌐 | TechPolicy.Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | MOFCOM deliberations on outbound restriction |
| 🌐 | Releasebot Qwen | https://releasebot.io/updates/qwen | Qwen 4 training; Image-2.1; Omni-Flash |
| 🌐 | Releasebot Mistral | https://releasebot.io/updates/mistral | Leanstral 1.5 retiring Sep 30; EU sovereign |
| 🌐 | HAI Stanford | https://hai.stanford.edu/assets/files/hai-digichina-issue-brief-beyond-deepseek-chinas-diverse-open-weight-ai-ecosystem-policy-implications.pdf | Policy analysis: China's diverse open-weight ecosystem |
| 🌐 | Chatham House | https://www.chathamhouse.org/2026/04/ai-export-controls-are-not-best-bargaining-chip | Export controls strategic costs |
| 🌐 | KraneShares | https://kraneshares.com/a-complete-guide-to-deepseeks-2026-ipo-what-it-means-for-china-etf-kstr/ | DeepSeek IPO China ETF implications |
| 🇨🇳 | Juejin (Sep 22) | https://juejin.cn/post/7688170325382594560 | MiMo-V2.6 deep dive; domestic chip day-zero |
| 🇨🇳 | 36kr (Sep 22) | https://36kr.com/p/3785761705909512 | MiMo: surpasses DeepSeek V4; Luo Fuli |
| 🇨🇳 | Tencent News (Sep 22) | https://news.qq.com/rain/a/20260922A053PP00 | MiMo #1 domestic + global |
| 🇨🇳 | 21jingji (Sep 24) | https://m.21jingji.com/article/20260924/ae90cf5fdaf2ed1648f18016d35524a4.html | $3.47M total training cost |
| 🇨🇳 | ITHome (Ascend 950) | https://www.ithome.com/1/003/981.htm | Sep 30 domestic commercial launch |
| 🇨🇳 | ITHome (inflection) | https://www.ithome.com/1/004/441.htm | Ecosystem inflection point |
| 🇨🇳 | 17173 (Ascend 950) | https://news.17173.com/content/09182026/120317504.shtml | Sep 30 / Nov 30 timeline |
| 🇨🇳 | TechNode CN | https://cn.technode.com/post/2026-09-18/huawei-cloud-ascend-950-commercial-service/ | Ascend 950 cloud service |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/jjxw/2026-09-18/doc-inishenx0300242.shtml | Huawei Cloud enterprise AI |
| 🇨🇳 | Zhihu (landscape) | https://zhuanlan.zhihu.com/p/670574382 | Model landscape Sep 23 |
| 🇨🇳 | Zhihu (Android) | https://zhuanlan.zhihu.com/p/2026037521889370330 | "China's Android Moment" analysis |
| 🇨🇳 | Zhihu (chip market) | https://zhuanlan.zhihu.com/p/2033821357394366898 | Ascend 950PR mass production; chip revenue |
| 🇨🇳 | Zhihu (chip report) | https://zhuanlan.zhihu.com/p/2035819335441236955 | AI chip 5-year outlook |
| 🇨🇳 | CSDN (MiMo) | https://blog.csdn.net/weixin_69359007/article/details/166364612 | MiMo-V2.6 deep dive; "kill line" |
| 🇨🇳 | CSDN (DeepSeek) | https://deepseek.csdn.net/6a0ac187662f9a54cb75630b.html | CANN pivot; cost cut |
| 🇯🇵 | Qiita (Sep 23) | https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760 | MiMo on Mac; license nuance; cost table |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/09/xiaomi-mimo-v2.6 | JP coverage; domestic chip; geo-restriction |
| 🇯🇵 | PC Watch | https://pc.watch.impress.co.jp/docs/news/2142608.html | JP comparison with Opus 5 |
| 🇯🇵 | GIGAZINE (Sep 24) | https://gigazine.net/gsc_news/en/20260924-mimo-v2-6-pro-flash/ | Sep 24; GPT-5.6 Sol comparison |
| 🇯🇵 | innovatopia | https://innovatopia.jp/ai/ai-news/118163/ | "Training method as IP" framing |
| 🇯🇵 | note.com (AI curator) | https://note.com/ai_curator/n/nd7476130d366 | Chinese AI "one-week war" context |
| 🇯🇵 | note.com (takutakuai) | https://note.com/takutakuai/n/n94b43fd5772f | 41% HuggingFace Chinese models |
| 🇯🇵 | labmemo (JP) | https://labmemo.com/deepseek-v41-flash-release-deepseek-flash-native-multimodal-2026/ | DeepSeek V4.1 Flash JP coverage |
| 🇯🇵 | ai-revolution.co.jp | https://ai-revolution.co.jp/media/what-is-deepseek-v4-1/ | DeepSeek V4.1 JP security/pricing guide |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 stories │ 429 on direct fetch │ active community discussion on MiMo-V2.6
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ SOURCE HEALTH: OK
├─ 📊 Polymarket: 1 market │ $53,390 volume │ CN AI ban 16% Yes (Sep 29 3:47 PM UTC)
├─ 🌐 Web: 66 pages │ 🇯🇵 9 │ 🇨🇳 14
└─ 🗣️ Top voices: Xiaomi Luo Fuli (MiMo-V2.6 launch) │ Huawei Zhou Yuefeng (Ascend 950 cloud Sep 30) │ CNBC (CN AI surge, Sep 26) │ Zhihu "Android Moment" thesis │ Qiita Takuya__ (MiMo license caution)
```

---

## Out of Scope but Notable

- **MiMo Desktop geo-restriction (EU/UK/Korea excluded):** Xiaomi's MiMo Desktop app (Windows + Apple Silicon) is NOT available in EU, UK, or Korea. Open weights are MIT-licensed but the app/service layer has territory exclusions — a new micro-pattern of open-weight + closed-distribution emerging across Chinese labs (cf. MiniMax H3 geo-exclusions). Not squarely in geopolitics scope but worth tracking as a soft-power distribution lever.

- **Juejin (掘金) confirms "day-zero" Huawei Ascend adaptation for MiMo-V2.6:** Xiaomi's new #1 model natively supports 5 domestic chip vendors from launch. This is the clearest example yet of Chinese open-weight model development being chip-ecosystem-agnostic from the start — a capability US open-weight models do NOT yet offer equivalently (Meta Llama still primarily Nvidia-dependent). Potential paradigm signal for future model releases.

---

## Data Gaps

- **DuckDuckGo HTML (JP + CN):** CAPTCHA-blocked on both passes (consistent with all prior runs); native-language WebSearch + direct hub fetches used as fallback
- **Zhihu direct page fetches:** HTTP 403 Forbidden on direct article fetch; content from search snippets only
- **Hacker News:** HTTP 429 (rate limited) on direct fetch of MiMo threads; points/comments counts unavailable; community discussion confirmed via search snippets
- **CNBC Sep 26 article:** HTTP 403; content reconstructed from search snippet + prior secondary references
- **CSDN MiMo article:** HTTP 521 on direct fetch; content from search snippets
- **Eastern Herald Sep 25 article:** HTTP 403; content from search snippet
- **BIS Sep 30 rule:** No Federal Register entry found as of Sep 29; deadline is TODAY — may publish same-day; treat as uncertain
- **Bluesky:** SOURCE HEALTH = OK; zero qualifying posts Sep 25-29
- **Polymarket "best Chinese AI company":** Not re-checked; prior state Sep 22: Alibaba 72%; $2.8M volume
- **DeepSeek V4.1 Pro:** Confirmed unreleased as of Sep 29; speculative Sep 28-30 window passed without release
- **Mistral frontier MoE:** Day ~176+ partner early access; zero public data
- **GLM-5.4:** Not released; CellCog Oct 8-Nov 9 window unchanged
- **YouTube/TikTok/Instagram:** Not searched
- **Approximate coverage:** 83% — strong on MiMo-V2.6 launch, BenchLM Sep 28, Ascend 950 cloud, DeepSeek IPO update, CNBC adoption story; gaps in Zhihu direct content, HN engagement metrics, BIS rule same-day publication, Polymarket full suite

---

## Key Quotes

> "2026年9月22日凌晨，小米正式发布 MiMo-V2.6-Pro，以46.32分登顶全球开源模型榜首，超越Kimi K3（44分）和GLM-5.3（45分）"
> (Translation: "In the early hours of September 22, 2026, Xiaomi officially released MiMo-V2.6-Pro, topping the global open-source model rankings at 46.32 points, surpassing Kimi K3 [44] and GLM-5.3 [45]")
> — Juejin, Sep 22, 2026 (https://juejin.cn/post/7688170325382594560)

> "Seeing how cheaply Xiaomi was able to train Mimo 2.6 I am starting to wonder if [frontier AI barriers are collapsing]"
> — Hacker News (https://news.ycombinator.com/item?id=49812257)

> "灵衢昇腾950智算集群云服务将于9月30日面向国内市场商用，11月30日面向全球市场商用"
> (Translation: "The Lingqu Ascend 950 AI Cluster Cloud Service will launch domestically on September 30, globally on November 30")
> — Huawei Cloud CEO Zhou Yuefeng at Huawei Connect 2026 (https://www.ithome.com/1/003/981.htm)

> "中国AI迎来'安卓时刻' — 华为昇腾+DeepSeek构建出与美国体系平行的完整AI技术栈"
> (Translation: "Chinese AI arrives at its 'Android Moment' — Huawei Ascend + DeepSeek builds a complete AI technology stack parallel to the US ecosystem")
> — Zhihu analysis, Sep 2026 (https://zhuanlan.zhihu.com/p/2026037521889370330)

> "ライセンスの注意事項: リポジトリにLICENSEファイルが存在しない; V2.6は以前の版の'商用展開承認'文言を省略。展開前にライセンス状態の確認を推奨"
> (Translation: "License caution: no LICENSE file in repository; V2.6 omits prior version's 'commercial deployment approved' language. Recommend verifying license status before deployment")
> — @Takuya__ on Qiita, Sep 23, 2026 (https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760)

> "DeepSeek has more than doubled its annualized revenue run rate to approximately $1 billion"
> — Eastern Herald, Sep 25, 2026 (https://easternherald.com/2026/09/25/deepseek-revenue-billion-shanghai-ipo/)

> "Chinese AI models surge in global popularity — and Washington is worried"
> — CNBC headline, Sep 26, 2026 (https://www.cnbc.com/2026/09/26/china-ai-global-adoption.html)

> "コスト比較: Pro $0.13/タスク vs Claude Fable 5.1 $7.63/タスク — 59倍の差"
> (Translation: "Cost comparison: Pro $0.13/task vs Claude Fable 5.1 $7.63/task — 59× difference")
> — @Takuya__ on Qiita, Sep 23, 2026 (https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760)
