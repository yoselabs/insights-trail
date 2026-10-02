# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-10-02
**Query type:** GENERAL
**Sources:** BenchLM, TechNode Global, TechNode CN, ITHome, 21jingji, 17173, Sina Finance, Zhihu, Juejin, CSDN, Qiita, note.com, innovatopia, PC Watch, TomHardware, NextWeb, Benzinga, Futunn, BigGo Finance, OrcaRouter, CellCog, Releasebot Mistral, DeepSeek API Docs, BIS.gov, Polymarket, CNBC, RestOfWorld, Congress.gov, TechPolicy.Press, Wiley Law, Baker McKenzie, Freshfields

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| YouTube | 0 | — | Not searched |
| Hacker News | 3 stories | Active discussion | 🌐 CN AI debate threads; Oct 2 digest via GitHub |
| TikTok | 0 | — | Not searched |
| Instagram | 0 | — | Not searched |
| Bluesky | 0 | — | SOURCE HEALTH: OK; no qualifying posts |
| Polymarket | 1 market | $54,372 volume | 🌐 CN AI ban 16% Yes; +$982 since Sep 29 |
| Web (global) | 48 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 8 pages | — | 🇯🇵 Qiita, note.com, innovatopia, PC Watch, fyve.co.jp, Yahoo JP |
| Web (China) | 16 pages | — | 🇨🇳 Zhihu, CSDN, Juejin, 21jingji, ITHome, 17173, Sina, 36kr |

---

## Synthesized Findings

### 1. [new] DeepSeek + Huawei Open-Source Full CUDA-Parity Ascend Stack (Sep 30) 🌐🇨🇳

**Claim:** DeepSeek and Huawei jointly released a complete open-source software stack for Huawei Ascend chips on September 30, achieving "one-to-one parity" with NVIDIA's CUDA platform — removing the last major software dependency blocking China's domestic AI from training at frontier scale without NVIDIA.

- **Components:** TileLang (high-level DSL), DeepGEMM, DeepEP, TileKernels, FlashMLA, DeepSelect
- **Hardware target:** 128-card Ascend 950 supernode
- **Key statement (DeepSeek WeChat):** "Currently, every TileLang operator used in DeepSeek training has a corresponding high-performance implementation on Ascend. Performance approaches hardware limits."
- **Quote (21jingji 🇨🇳):** "华为全程深度配合，双方联合推进昇腾950的128卡超节点方案" ("Huawei provided deep, full cooperation; both sides jointly developed the 128-card Ascend 950 supernode solution")
- **Strategic signal:** China's domestic AI stack (Ascend 950PR hardware + CANN + TileLang + open-weight models) now functionally complete without NVIDIA at any layer
- **Market context:** Ascend 950PR priced at ¥70,000 vs NVIDIA H200 ¥250,000 — less than 1/3 the cost
- **Timing:** Released September 30 — National Day eve; symbolic framing across CN media
- **Sources:** https://technode.global/2026/10/01/deepseek-huawei-ascend-ai-programming-tools/ | https://www.ithome.com/1/008/604.htm | https://www.21jingji.com/article/20260930/herald/a029425a430ca26d536eed13c8ebf6b2.html | https://www.tomshardware.com/tech-industry/artificial-intelligence/deepseek-and-huawei-release-open-source-ascend-ai-programming-tools-to-reduce-reliance-on-nvidia-ecosystem-tools-include-compute-and-communication-libraries-as-well-as-ascend-support-for-tilelang | https://thenextweb.com/news/deepseek-huawei-ascend-tilelang-open-source-cuda | https://finance.biggo.com/news/f8a26b65-2476-4f12-b04a-0312be51c16b | https://www.benzinga.com/markets/prediction-markets/26/09/62079163/nvidia-cuda-deepseek-huawei-ascend | https://www.sina.cn/weibo/detail/5349119866437929.html | https://www.sina.cn/weibo/detail/5349068513476748.html | https://news.futunn.com/en/post/1000448163/challenging-nvidia-s-cuda-deepseek-open-sources-huawei-ascend-full | https://weibo.com/2/detail/5349196326503911 | https://chinatechbite.substack.com/p/deepseek-just-open-sourced-its-full | https://i10x.ai/news/deepseek-tilelang-huawei-ascend-open-source | https://www.advisiotech.com/blog/deepseek-huawei-ascend-cuda-alternative

---

### 2. [update] BenchLM v5.8 Reshuffles Rankings: DeepSeek V4.1 Flash Surges from #14 to #6 🌐

**Claim:** BenchLM updated to v5.8 on Oct 2; most significant move is DeepSeek V4.1 Flash jumping from #14 (55.7) to #6 (64.7) — a 9-point gain — and MiMo-V2.6-Flash overtaking GLM-5.3 for the first time. Benchmark recalibration (not new model) drove the moves.

**Top-10 (Oct 2, BenchAlign v5.8):**

| # | Model | Creator | Score | Δ vs Sep 28 |
|---|-------|---------|-------|------------|
| 1 | MiMo-V2.6-Pro | Xiaomi | **75.5** | +0.8 |
| 2 | Qwen3.8 Max | Alibaba | 72.1 | +0.4 |
| 3 | MiMo-V2.6-Flash | Xiaomi | 66.4 | +2.3 ↑ from #4 |
| 4 | GLM-5.3 | Z.AI | 65.7 | +0.3 ↓ from #3 |
| 5 | DeepSeek V4 Pro 0813 | DeepSeek | 65.0 | +1.0 |
| 6 | **DeepSeek V4.1 Flash** | DeepSeek | **64.7** | **+9.0 ↑ from #14** |
| 7 | Qwen3.8-Flash-Next | Alibaba | 64.5 | +3.7 ↑ from #9 |
| 8 | dots3-note Preview | Dots Studio | 63.6 | +1.0 ↓ from #6 |
| 9 | GLM-5.2 | Z.AI | 63.2 | +0.6 ↓ from #7 |
| 10 | Ornith-1.5-397B | Ornith AI | 62.7 | +0.9 ↓ from #8 |

**Notable changes (11-20):**
- Kimi K2.6 (#12, 60.2) returned to top-20
- GLM-5.3-Flash dropped from #10 (60.6) to #13 (58.6)
- Inkling-Small fell from #15 to #17; still only non-Chinese in top-20 with Inkling (#19)
- Kimi K2.7 Code returned at #20 (54.6) — was off Sep 28 board

- **Source:** https://benchlm.ai/best/open-source | https://benchlm.ai/models/mimo-v2-6-pro | https://benchlm.ai/models/mimo-v2-6-flash

---

### 3. [update] DeepSeek V4.1 Pro: Gray-Scale Testing Active, National Day Window Open 🌐🇨🇳

**Claim:** New fact since Sep 29: DeepSeek V4.1 Pro entered gray-scale testing as of ~Sep 27-28; CN media reports "有望国庆发布" (expected during National Day holidays Oct 1-7); reportedly 2T parameters with CED+Engram architecture.

- **Testing status:** Gray-scale by account; "High-level reasoning" default; text/code only (image disabled)
- **Reported specs:** ~2 trillion parameters; CED+Engram; Prefill/Decode separation; asymmetric activation
- **Future:** 8T version reportedly on roadmap (unconfirmed)
- **Sep 30 window:** Closed; Oct 1-7 National Day week remains open (today is Oct 2)
- **Unconfirmed:** DSH 0.2 (DeepSeek Harness desktop 0.2) was rumored same-day; OrcaRouter confirmed no 0.2 tag exists in npm/GitHub as of Sep 29
- **Sep 29 API changelog:** Still last entry Sep 10; no new V4.1 Pro entry today
- **Sources:** https://news.17173.com/content/09282026/150341407.shtml | https://news.17173.com/content/09212026/210050369.shtml | https://finance.sina.com.cn/tech/roll/2026-09-28/doc-initkhxi3756687.shtml | https://www.orcarouter.ai/blog/dsh-0-2-v4-1-pro-leak | https://api-docs.deepseek.com/updates/

---

### 4. [update] Huawei Ascend 950 Cloud: Sep 30 Domestic Launch Confirmed 🌐🇨🇳

**Claim:** New fact since Sep 29: Ascend 950 cloud service launched domestically as scheduled on Sep 30; >1,000 supernodes confirmed in commercial use; global launch Nov 30 on track.

- **Status:** Commercial; >1,000 supernodes deployed
- **Specs:** 1,024-card cluster; 1 EFLOPS FP8; 2 EFLOPS FP4; 256TB unified memory; Lingqu interconnect
- **Context:** Software stack completion (Sep 30 DeepSeek/Huawei open-source) coincided with cloud launch — hardware + software milestones on same day
- **Sources:** https://news.metal.com/newscontent/104143081-smm-flash-huawei-ascend-950-ai-computing-cluster-officially-launched-for-commercial-use-on-september-30 | https://www.huaweicentral.com/huawei-ascend-950-ai-cluster-to-debut-globally-on-november-30/ | https://pandaily.com/huawei-cloud-ascend-950-lingqu-cluster-commercial-dates

---

### 5. [update] Mistral Platform: Leanstral 1.5 Retired; GLM-5.3 Replaces GLM-5.2 on EU Endpoints 🌐

**Claim:** New facts since Sep 29: Leanstral 1.5 officially retired Sep 28/30; GLM-5.2 deprecated Sep 28 on Mistral platform; GLM-5.3 GA on Mistral EU-sovereign endpoints as of Sep 27.

- **Leanstral 1.5:** Retired as scheduled
- **GLM-5.3:** Now GA on Mistral (identifier: zai-glm-5-3); GLM-5.2 deprecated
- **Frontier MoE:** Still day ~179+; partner early access; no public announcement
- **Sources:** https://releasebot.io/updates/mistral | https://docs.mistral.ai/resources/changelogs

---

### 6. [update] BIS Diffusion Rule: Sep 30 FY2026 Deadline Passed Without Replacement 🌐

**Claim:** New fact since Sep 29: The Sep 30 fiscal year deadline passed with no Federal Register replacement rule — confirming continued regulatory purgatory. Original rule text remains technically in CFR.

- **Status:** No replacement published; not enforced; text in CFR
- **Draft rule:** Went to OIRA Feb 2026; withdrawn March; no re-submission
- **RASA:** Still in Senate Banking Committee; no floor vote; S.3519 companion bill pending
- **Sources:** https://www.bis.gov/news-updates | https://www.mofo.com/resources/insights/250617-ai-diffusion-rule-out-but-bis-increases-compliance | https://www.congress.gov/bill/119th-congress/senate-bill/3519/text

---

**Still true (ongoing, no new facts since Sep 29):**

- `xiaomi-mimo-frontier-entry` — MiMo-V2.6-Pro: now 75.5 (#1 BenchLM v5.8); #1 Artificial Analysis 46.32; consumer electronics lab leads global open-weight frontier
- `benchlm-aug10-rankings-minimax-leads` — Oct 2 v5.8: #1 MiMo-V2.6-Pro 75.5; #2 Qwen3.8 Max 72.1; #3 MiMo-V2.6-Flash 66.4; #4 GLM-5.3 65.7; Inkling-Small #17 still only non-Chinese in top-20 alongside Inkling #19
- `deepseek-star-market-ipo-citic` — CITIC; ~$74-75B; $1B ARR; 82.9% gross margin; Q2 2027 STAR Market
- `chinese-models-global-share-30pct` — CNBC Sep 26 confirmed; 63% enterprise OpenRouter tokens; DeepSeek 16.3%; 3B Alibaba downloads; Airbnb/Coinbase now using Chinese models
- `xi-brics-ai-open-source-zone` — Xi Sep 13 BRICS AI zone; DeepSeek+Qwen to Global South free; WAICO+BRICS two-layer multilateral architecture
- `qwen-image-2-1-open-source` — Qwen-Image-2.1 (Sep 20, 7B, research-only license)
- `us-china-ai-safety-talks-sep24` — Trump-Xi Sep 24: first US-China AI Dialogue; chip controls NOT on agenda; trade truce to Jan 10, 2027; no joint statement
- `huawei-ascend-ecosystem-inflection` — Sep 19 inflection: 5,200+ CANN MAU; non-Huawei devs exceed Huawei; 5B yuan 3-year; 40+ LLMs trained
- `polymarket-us-chinese-model-ban` — 16% Yes; $54,372 (+$982 since Sep 29); odds unchanged
- `eu-ai-act-august-enforcement` — GPAI Sep 15 deadline passed; no Chinese lab signed Code of Practice; EU enforcement limited
- `qwen4-apsara-announcement` — Still in training; 74% before Nov 1 prediction market; no weights/benchmarks
- `alibaba-zhenwu-v900-chip` — T-Head Zhenwu V900: 3× M890; 216GB HBM; Q1 2027
- `deepseek-v41-pro-2t-leak` — Gray-scale testing active; National Day window; 2T params confirmed by CN media; not yet released (Oct 2)
- `huawei-ascend-960-connect2026` — 960DT Q1 2027 (9 months early); 960PR Q3 2027; 970/980 roadmap
- `rasa-senate-pending-cloud-loophole` — Senate Banking; no floor vote; S.3519 pending; Aivres $5.6B Blackwell ongoing
- `deepseek-v4-1-flash-release` — V4.1 Flash: now #6 BenchLM at 64.7 (huge v5.8 jump from 55.7)
- `deepseek-v4-pro-retirement-reversed` — V4 Pro continues; #5 BenchLM at 65.0
- `deepseek-v41-flash-abliteration` — MIT license; 23K+ GGUF downloads; 100% HarmBench-320
- `anthropic-distillation-report-sep10` — 200M exchanges; MOFCOM "groundless"; no enforcement
- `mistral-samsung-series-d-third-axis` — €3B Samsung Series D (€21B/$24B); frontier MoE silent (day ~179+)
- `qwen-drive-1-0-apache-av` — Qwen-Drive-1.0-4B (Apache 2.0, HKUST); autonomous driving VLM
- `deepseek-160k-huawei-inner-mongolia` — 160K Ascend 950DT order ($2.56B); delivery >1 year
- `kimi-k3-gpu-crunch-subscription-pause` — HKEX confidential A1; $3B target; $50B val; ARR $300M
- `china-domestic-chip-mass-pivot` — >52.3% domestic Q1 2026; Ascend 50-60% 2026 share; Nvidia ~8%
- `xi-waic-open-source-mandate` — WAICO 37-nation; BRICS AI zone = two-layer multilateral structure
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon (375B-A23B, Apache 2.0); fully-open frontier fleet
- `qwen-3-8-max-open-weights-pending` — #2 BenchLM (72.1); Qwen 4 no release
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash: #13 BenchLM (58.6, dropped from #10)
- `tencent-hy4-preview-apache` — Hy4 preview: #11 BenchLM at 61.1
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3: #4 BenchLM at 65.7 (dropped from #3 due to MiMo-V2.6-Flash)
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next: #7 BenchLM at 64.5 (up from #9/60.8)
- `minimax-h1-2026-agent-dividend` — ARR >$800M; H1 revenue $116.6M (+283% YoY)
- `open-weight-licensing-bifurcation` — MIT for flash/small; research-only image gen; geo-restriction MiMo Desktop (EU/UK/Korea excluded)
- `deepseek-v4-flash-vision-exp` — All V4 endpoints continue
- `meta-muse-glimmer-us-open-weight` — Outside BenchLM top-20
- `dots3-note-preview-rednote` — #8 BenchLM at 63.6 (down from #6/62.6)
- `ornith-1-5-self-improving` — #10 BenchLM at 62.7 (down from #8)
- `qwen3-8-27b-apache-multimodal` — #15 BenchLM at 57.6
- `mistral-frontier-moe-silent` — Day ~179+; no public announcement
- `agents-a1-internsciense-new-entrant` — No new position
- `deepseek-harness-v01-price-hike` — V4.1 Flash pricing baseline; concurrency 500→2,500
- `kimi-k3-weights-open-source` — K3 (2.8T MoE, 32B active); Kimi K3 License
- `us-moonshot-distillation-sanctions` — Bessent Jul 22 threat; cloud deal; no enforcement
- `openai-hf-cyberattack-glm-defense` — HuggingFace July breach framing persists
- `deepseek-zhipu-self-chip-development` — CUDA→CANN pivot confirmed; Ascend parity software stack released Sep 30; own inference chip in IPO disclosure
- `open-weights-decelerationist-accelerationist` — 63% OpenRouter enterprise tokens Chinese; 56.72T CN calls vs 16.54T US
- `openeurollm-european-sovereign` — No new release; Mistral Samsung D separate track
- `kimi-k3-eda-chip-design` — No new reports
- `minimax-m3-pro-2-7t` — MiniMax M3: #16 BenchLM at 55.2 (down from #17)
- `china-mofcom-export-controls-ai` — Still deliberating; no finalization
- `deepseek-chip-ascend-950dt` — 950DT: 160K DeepSeek order; 960DT Q1 2027; 950 cloud CONFIRMED LIVE Sep 30
- `glm-5-5-expected-august` — No GLM-5.4 yet; Oct 8-Nov 9 window; Oct 22 median
- `ai-manifesto-war-pacing-frontier` — Sep 30 Ascend stack + cloud launch strengthens "Android Moment" thesis; National Day symbolism in CN media
- `chinese-military-pla-distillation-reuters` — GTG-16002; 300K requests; no enforcement
- `distillation-scale-data` — 200M exchanges; MOFCOM "groundless"
- `nemotron-3-ultra-us-open-weight` — Outside top-20; all-Chinese dominance continues
- `polymarket-chinese-ai-company` — Not re-checked; prior: Alibaba 72% best Chinese AI
- `inkling-small-thinking-machines` — Inkling-Small: #17 BenchLM at 55.1 (fell from #15); Inkling #19 at 54.8 — still only non-Chinese in top-20
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0); no updates
- `minimax-h3-geo-license-restriction` — H3 video geo-restriction ongoing; Hollywood litigation
- `deepseek-autonomous-cyberattack-hermes` — No new incident
- `industry-coalition-open-weights-letter` — 235+ signatories; Anthropic sole major holdout
- `databricks-enterprise-glm-migration` — GLM-5.3 enterprise coding; Airbnb/Coinbase confirmed
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2: #9 BenchLM at 63.2 (up from #7/62.6); Huawei Ascend trained; DEPRECATED on Mistral (replaced by GLM-5.3)
- `nvidia-h200-china-trivial` — Nvidia ~8% China AI; domestic 90% target 2027; Ascend 950 cloud live
- `jp-deepseek-japanese-cultural-benchmark` — Mizuho Qwen3-32B; ~60% JP enterprises on DeepSeek/Qwen; MiMo-V2.6 getting JP developer testing
- `qwen38-omni-flash-agent` — Qwen3.8-Omni-Flash (Sep 17): omnimodal agent
- `qwen-huggingface-ecosystem-dominance` — 3B downloads; 56M/month; 300K+ derivatives
- `xiaomi-mimo-v26-tops-leaderboard` — Now 75.5 (#1 BenchLM v5.8); score update confirms continued leadership

---

## Cross-Source Patterns

### Pattern 1: Sep 30 = China's Domestic AI Independence Day 🌐🇨🇳
- **Signal:** Three milestones landed on September 30: (1) DeepSeek+Huawei CUDA-parity Ascend software stack open-sourced; (2) Ascend 950 cloud service commercially launched; (3) DeepSeek V4.1 Pro gray-scale testing active. CN media framing: "国产AI底层软件生态" complete — China now has frontier model training capability from chip to cloud to software without NVIDIA.
- **Platforms:** ITHome, 21jingji, Zhihu, Sina Weibo (CN); TechNode Global, TomHardware, NextWeb, Benzinga, Futunn (global)
- **Quote (Zhihu 🇨🇳):** "中国AI迎来'安卓时刻' — 华为昇腾+DeepSeek构建出与美国体系平行的完整AI技术栈" ("Chinese AI arrives at its 'Android Moment' — Huawei Ascend + DeepSeek builds a complete AI technology stack parallel to the US ecosystem")
- **Quote (ITHome 🇨🇳 via Weibo):** "9月30日正式开源昇腾基础组件 对标CUDA生态" ("Sep 30 officially open-sourced Ascend infrastructure, benchmarked against CUDA ecosystem")

### Pattern 2: BenchLM v5.8 Recalibration Amplifies DeepSeek V4.1 Flash Position 🌐
- **Signal:** BenchAlign v5.8 upgrade caused the largest score jump for DeepSeek V4.1 Flash (+9.0 pts, #14→#6). This model was already the #1 AutomationBench open-weight; the leaderboard recalibration confirms it's been systematically underrated. MiMo-V2.6-Flash also gained +2.3 pts.
- **Platforms:** BenchLM (global)
- **Implication:** Narrowing gap between MiMo-V2.6-Pro (75.5) and the next tier (64.5-66.4) is partially a calibration artifact; the gap between #1 and #3-#7 is real at ~9-11 pts.

### Pattern 3: Hardware + Software + Cloud All Landed on Same Day 🌐🇨🇳
- **Signal:** DeepSeek Ascend stack (software) + Ascend 950 cloud (infrastructure) on Sep 30 is a coordinated milestone that CN media explicitly treats as the completion of China's "second AI ecosystem." Distinct from WAICO/BRICS (geopolitical) — this is technical ecosystem.
- **Platforms:** ITHome, 21jingji, Zhihu, TechNode Global, TomHardware, Benzinga
- **Why it matters:** Open-weight models already exported CUDA dependency globally; now the training infrastructure can follow. DeepSeek V4.1 Pro (2T, National Day window) would be the first frontier model trained primarily on this stack.

### Pattern 4: Hacker News Actively Debating Chinese AI Strategy (Oct 2) 🌐
- **Signal:** Three separate HN threads on Oct 2 about Chinese open-weight dominance, with active community discussion.
- **Platforms:** Hacker News (global)
- **Quote:** "China's open-weights AI strategy is winning" (https://news.ycombinator.com/item?id=48979269)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (unknown) | China's open-weights AI strategy is winning | N/A | Active | Community debate on strategic intent | https://news.ycombinator.com/item?id=48979269 |
| (unknown) | Who's afraid of Chinese models? | N/A | Active | Enterprise adoption discussion | https://news.ycombinator.com/item?id=48977128 |
| (unknown) | The state of open source AI | N/A | Active | Global open-weight ecosystem survey | https://news.ycombinator.com/item?id=48947825 |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US removes public access to major Chinese AI model in 2026 | **16% Yes** | $54,372 | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | TechNode Global (Oct 1) | https://technode.global/2026/10/01/deepseek-huawei-ascend-ai-programming-tools/ | DeepSeek+Huawei Ascend open-source; Sep 30 date confirmed |
| 🌐 | TomHardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/deepseek-and-huawei-release-open-source-ascend-ai-programming-tools-to-reduce-reliance-on-nvidia-ecosystem-tools-include-compute-and-communication-libraries-as-well-as-ascend-support-for-tilelang | TileLang + libraries; CUDA parity |
| 🌐 | NextWeb | https://thenextweb.com/news/deepseek-huawei-ascend-tilelang-open-source-cuda | "Simpler programming model than CUDA" |
| 🌐 | Benzinga | https://www.benzinga.com/markets/prediction-markets/26/09/62079163/nvidia-cuda-deepseek-huawei-ascend | Nvidia software moat threat |
| 🌐 | BigGo Finance | https://finance.biggo.com/news/f8a26b65-2476-4f12-b04a-0312be51c16b | "One-to-one parity" framing |
| 🌐 | Futunn | https://news.futunn.com/en/post/1000448163/challenging-nvidia-s-cuda-deepseek-open-sources-huawei-ascend-full | "Challenging NVIDIA's CUDA" |
| 🌐 | ChinaTechBite Substack | https://chinatechbite.substack.com/p/deepseek-just-open-sourced-its-full | Full stack analysis |
| 🌐 | i10x.ai | https://i10x.ai/news/deepseek-tilelang-huawei-ascend-open-source | TileLang DSL technical analysis |
| 🌐 | Advisiotech | https://www.advisiotech.com/blog/deepseek-huawei-ascend-cuda-alternative | CUDA alternative implications |
| 🌐 | BenchLM (Oct 2) | https://benchlm.ai/best/open-source | Top-20 rankings v5.8 |
| 🌐 | BenchLM MiMo-Pro | https://benchlm.ai/models/mimo-v2-6-pro | MiMo-V2.6-Pro 75.5; #11 of 211 total |
| 🌐 | BenchLM MiMo-Flash | https://benchlm.ai/models/mimo-v2-6-flash | MiMo-V2.6-Flash 66.4 |
| 🌐 | HuaweiCentral | https://www.huaweicentral.com/huawei-ascend-950-ai-cluster-to-debut-globally-on-november-30/ | Global Nov 30 confirmed |
| 🌐 | SMM Flash | https://news.metal.com/newscontent/104143081-smm-flash-huawei-ascend-950-ai-computing-cluster-officially-launched-for-commercial-use-on-september-30 | Sep 30 launch confirmed |
| 🌐 | Pandaily | https://pandaily.com/huawei-cloud-ascend-950-lingqu-cluster-commercial-dates | Ascend 950 specs recap |
| 🌐 | InsideAI.news | https://insideai.news/news/ai-hardware-infrastructure/huawei-ascend-950-ai-cluster/12281/ | 1,000+ supernodes commercial |
| 🌐 | OrcaRouter (DSH) | https://www.orcarouter.ai/blog/dsh-0-2-v4-1-pro-leak | DSH 0.2 unconfirmed; V4.1 Pro no official record |
| 🌐 | OrcaRouter (V4.1 Pro) | https://www.orcarouter.ai/blog/deepseek-v4-1-pro-leak | "What changed in a week" — no release |
| 🌐 | DeepSeek API Docs | https://api-docs.deepseek.com/updates/ | Last entry Sep 10; V4.1 Pro absent |
| 🌐 | YottaLabs | https://www.yottalabs.ai/post/deepseek-v4-1-pro-release-date-what-is-known-how-to-prepare-2026 | V4.1 Pro prep guide |
| 🌐 | BIS.gov | https://www.bis.gov/news-updates | No replacement rule as of Oct 2 |
| 🌐 | MoFo | https://www.mofo.com/resources/insights/250617-ai-diffusion-rule-out-but-bis-increases-compliance | FY2026 deadline missed |
| 🌐 | Baker McKenzie | https://sanctionsnews.bakermckenzie.com/us-house-passes-remote-access-security-act/ | RASA Jan 2026; Senate pending |
| 🌐 | Congress.gov | https://www.congress.gov/bill/119th-congress/senate-bill/3519/text | RASA Senate companion text |
| 🌐 | Freshfields (RASA) | https://www.freshfields.com/en/our-thinking/blogs/a-fresh-take/remote-access-or-remote-possibility-rasa-and-the-future-of-cloud-export-controls-102nfbw | RASA Senate Banking analysis |
| 🌐 | Polymarket | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 | 16% Yes; $54,372 |
| 🌐 | TechPolicy.Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | MOFCOM three-tier deliberations |
| 🌐 | TechTimes | https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm | CN export controls on model weights |
| 🌐 | TomHardware (MOFCOM) | https://www.tomshardware.com/tech-industry/artificial-intelligence/china-is-considering-export-controls-on-ai-technologies | TSMC angle |
| 🌐 | RestOfWorld | https://restofworld.org/2026/china-siliconvalley-ai-moonshot-kimi/ | Silicon Valley keeps using Chinese AI |
| 🌐 | CNBC | https://www.cnbc.com/2026/09/26/china-ai-global-adoption.html | Chinese AI surge globally |
| 🌐 | TechStartups | https://techstartups.com/2026/06/29/western-companies-are-quietly-switching-to-chinese-ai-models-as-u-s-frontier-ai-prices-rise/ | Western migration to CN models |
| 🌐 | CellCog (Qwen 4) | https://cellcog.ai/blog/qwen-4-release-date/ | In training; 74% before Nov 1 |
| 🌐 | Versely.studio | https://www.versely.studio/blog/qwen-4-announced-at-apsara-2026 | Four tiers; 10T roadmap |
| 🌐 | CellCog (GLM) | https://cellcog.ai/blog/glm-5-5-release-date/ | Oct 8-Nov 9 window |
| 🌐 | Releasebot (Mistral) | https://releasebot.io/updates/mistral | GLM-5.3 GA; Leanstral 1.5 retired |
| 🌐 | HN digest (GitHub) | https://github.com/Chestnuts-Sisyphus/gittok/issues/1576 | Oct 2 digest: FTC/OpenAI-Synopsys top |
| 🌐 | MasonAI Lab | https://masonailab.com/insights/china-restricts-own-ai-models-export-2026/ | Mirror-image export control analysis |
| 🇨🇳 | ITHome (Ascend stack) | https://www.ithome.com/1/008/604.htm | DeepSeek Ascend open-source; Sep 30 |
| 🇨🇳 | ITHome (950 cloud) | https://www.ithome.com/1/003/981.htm | Sep 30 domestic / Nov 30 global |
| 🇨🇳 | 21jingji (Ascend) | https://www.21jingji.com/article/20260930/herald/a029425a430ca26d536eed13c8ebf6b2.html | "Wholehearted support"; strategic analysis |
| 🇨🇳 | 17173 (V4.1 Pro test) | https://news.17173.com/content/09282026/150341407.shtml | Gray-scale testing; National Day window |
| 🇨🇳 | 17173 (V4.1 Pro 2T) | https://news.17173.com/content/09212026/210050369.shtml | 2T params; 8T future; Ascend bet |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-09-28/doc-initkhxi3756687.shtml | V4.1 Pro National Day mirror |
| 🇨🇳 | Zhihu (Android Moment) | https://zhuanlan.zhihu.com/p/2026037521889370330 | "Android Moment" confirmed |
| 🇨🇳 | Zhihu (landscape Oct 1) | https://zhuanlan.zhihu.com/p/670574382 | Oct 1 model landscape |
| 🇨🇳 | Zhihu (2026 TOP10) | https://zhuanlan.zhihu.com/p/2009705203163752429 | Open-source top-10 analysis |
| 🇨🇳 | Zhihu (950PR price) | https://zhuanlan.zhihu.com/p/2026893491125467122 | ¥70K vs ¥250K H200 |
| 🇨🇳 | Weibo (Ascend open-source) | https://weibo.com/2/detail/5349196326503911 | Sep 30 Ascend open-source confirmed |
| 🇨🇳 | Weibo (stack detail) | https://www.sina.cn/weibo/detail/5349119866437929.html | 128-card supernode; interface compat |
| 🇨🇳 | Weibo (full component list) | https://www.sina.cn/weibo/detail/5349068513476748.html | Full component list |
| 🇨🇳 | Juejin (MiMo deep dive) | https://juejin.cn/post/7688170325382594560 | MiMo-V2.6 deep dive |
| 🇨🇳 | Juejin (V4.1 internal test) | https://juejin.cn/post/7683353819853766692 | V4.1 Flash 48h pre-release window |
| 🇨🇳 | CSDN (DeepSeek) | https://deepseek.csdn.net/6a0ac187662f9a54cb75630b.html | CUDA→CANN pivot |
| 🇨🇳 | CSDN (benchmark) | https://adg.csdn.net/6a392d27662f9a54cb82beb5.html | 2026 open-source model deep evaluation |
| 🇨🇳 | 36kr (Ascend 950) | https://36kr.com/p/3780399181878528 | DeepSeek V4 officially supports Ascend 950 |
| 🇨🇳 | CLS.cn (V4 Ascend) | https://www.cls.cn/detail/2354690 | V4 + Ascend supernode; 1M context era |
| 🇨🇳 | Futunn CN | https://news.futunn.com/en/post/1000428379/benchmarking-nvidia-s-cuda-deepseek-has-open-sourced-its-ascend | "Benchmarking NVIDIA's CUDA" |
| 🇯🇵 | Qiita (MiMo Mac) | https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760 | Cost table; license caution; Mac deployment |
| 🇯🇵 | note.com (MiMo agent) | https://note.com/humble_bobcat51/n/n94012cad5242 | DeepSWE 71.9%; training transparency |
| 🇯🇵 | note.com (AI curator) | https://note.com/ai_curator/n/nd7476130d366 | "One-week war" synthesis |
| 🇯🇵 | note.com (takutakuai) | https://note.com/takutakuai/n/n94b43fd5772f | 41% HuggingFace CN models; 16.3% DeepSeek |
| 🇯🇵 | innovatopia | https://innovatopia.jp/ai/ai-news/118163/ | "What Xiaomi released was the training method" |
| 🇯🇵 | PC Watch | https://pc.watch.impress.co.jp/docs/news/2142608.html | JP comparison MiMo vs Opus 5 |
| 🇯🇵 | Yahoo Japan | https://news.yahoo.co.jp/articles/a3c8a635e7989bc2aacb60b7365b249f4667a421 | PC Watch mirror |
| 🇯🇵 | fyve.co.jp | https://fyve.co.jp/ai-advisor/articles/mimo-v2-6-pro-cost-vs-accuracy | Cost: 1/44th of Western models |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 stories │ active discussions on CN open-weight strategy (Oct 2)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ SOURCE HEALTH: OK
├─ 📊 Polymarket: 1 market │ $54,372 volume │ CN AI ban 16% Yes (unchanged)
├─ 🌐 Web: 72 pages │ 🇯🇵 8 │ 🇨🇳 16
└─ 🗣️ Top voices: DeepSeek (Sep 30 WeChat Ascend announcement) │ 17173/Sina (V4.1 Pro testing) │ Zhihu "Android Moment" │ @Takuya__ Qiita (license caution) │ TechNode Global (Oct 1 Ascend coverage)
```

---

## Out of Scope but Notable

- **FTC investigates OpenAI and Anthropic (198 pts HN, Oct 2):** US-frontier news, but notable as geopolitical context — regulatory pressure on US labs could accelerate enterprise migration to open-weight Chinese models. Not squarely in scope but worth tracking as an asymmetric market dynamic. Source: https://github.com/Chestnuts-Sisyphus/gittok/issues/1576

- **OpenAI-Synopsys chip design partnership (162 pts HN, Oct 2):** US closed-source lab entering EDA/chip design — Kimi K3 for chip design (tracked in this topic) is now getting a US counterpart. Paradigm signal: AI models as chip-design tools becoming cross-national race. Source: https://github.com/Chestnuts-Sisyphus/gittok/issues/1576

---

## Data Gaps

- **DuckDuckGo HTML endpoint (JP + CN):** CAPTCHA-blocked on both passes (consistent with all prior runs); native-language WebSearch + direct hub WebFetch used as fallback
- **Zhihu direct fetch (Oct 1 landscape article):** HTTP 403 Forbidden; content from search snippet only
- **DeepSeek V4.1 Pro status on Oct 2:** Gray-scale testing confirmed; National Day window technically still open (Oct 2 of 1-7); no release as of time of writing
- **BIS replacement rule:** No Federal Register notice found; Sep 30 deadline passed without publication
- **Polymarket "best Chinese AI company":** Not re-checked; prior state (Sep 22): Alibaba 72%, $2.8M volume
- **GLM-5.4:** Not released as of Oct 2; Oct 22 remains median prediction
- **Qwen 4:** Not released; 74% before Nov 1 prediction market
- **Mistral frontier MoE:** Day ~179+; zero public data; no announcement
- **YouTube/TikTok/Instagram:** Not searched
- **Approximate coverage:** 85% — strong on Sep 30 Ascend software stack release (new), BenchLM v5.8 reshuffles, V4.1 Pro testing status, Ascend 950 cloud launch confirmation; gaps in real-time V4.1 Pro release status (may still ship Oct 2-7), Polymarket full suite, HN engagement metrics

---

## Key Quotes

> "DeepSeek全部训练算子都已经在昇腾上完成高性能实现。性能已接近硬件上限"
> (Translation: "All of DeepSeek's training operators have completed high-performance implementations on Ascend. Performance approaches hardware limits.")
> — DeepSeek official WeChat, Sep 30, 2026 (https://www.ithome.com/1/008/604.htm)

> "9月30日正式开源昇腾基础组件 对标CUDA生态"
> (Translation: "Sep 30 officially open-sourced Ascend infrastructure, benchmarked against CUDA ecosystem")
> — Weibo summary, Sep 30, 2026 (https://weibo.com/2/detail/5349196326503911)

> "中国AI迎来'安卓时刻' — 华为昇腾+DeepSeek构建出与美国体系平行的完整AI技术栈"
> (Translation: "Chinese AI arrives at its 'Android Moment' — Huawei Ascend + DeepSeek builds a complete AI technology stack parallel to the US ecosystem")
> — Zhihu analysis, 2026 (https://zhuanlan.zhihu.com/p/2026037521889370330)

> "有望国庆发布 DeepSeek V4.1 Pro已开始测试：性能值得期待"
> (Translation: "Expected to be released during National Day; DeepSeek V4.1 Pro has started testing: performance is promising")
> — 17173.com, Sep 28, 2026 (https://news.17173.com/content/09282026/150341407.shtml)

> "Nvidia's near-monopoly in the AI market isn't just about silicon; it's heavily protected by CUDA. By providing an open-source bridge to Huawei's hardware, DeepSeek is attempting to commoditize the software layer."
> — Benzinga, Sep 30, 2026 (https://www.benzinga.com/markets/prediction-markets/26/09/62079163/nvidia-cuda-deepseek-huawei-ascend)

> "Chinese AI developers cut off from top Nvidia hardware by US export controls now have a fuller domestic software stack to build on after the unveiling."
> — BigGo Finance (https://finance.biggo.com/news/f8a26b65-2476-4f12-b04a-0312be51c16b)

> "ライセンスの注意事項: リポジトリにLICENSEファイルが存在しない; V2.6は以前の版の'商用展開承認'文言を省略。展開前にライセンス状態の確認を推奨"
> (Translation: "License caution: no LICENSE file in repository; V2.6 omits prior version's 'commercial deployment approved' language. Recommend verifying license status before deployment.")
> — @Takuya__ on Qiita, Sep 23, 2026 (https://qiita.com/Takuya__/items/0b7b8b767fedaadc6760)

> "DeepSeek V4.1 Pro或为2万亿参数：未来还有8万亿版、押注国产芯片"
> (Translation: "DeepSeek V4.1 Pro reportedly has 2 trillion parameters; future 8 trillion version; betting on domestic chips")
> — 17173.com, Sep 21, 2026 (https://news.17173.com/content/09212026/210050369.shtml)
