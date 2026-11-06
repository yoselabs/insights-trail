# Open-Source & Non-US Models / AI Geopolitics — Daily Briefing
**Date:** 2026-11-06
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan), Web (China), Hacker News, Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 stories | 901 combined points | Kimi K3.1 Pro 431pts, Ripple-65B 260pts, Tencent Hy4 210pts |
| Polymarket | 1 market | $122,467 volume | 🌐 US-removes-public-access-Chinese-AI |
| Web (global) | 68 pages | — | 🌐 via WebSearch, keyless |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita, Zenn, note, Blackford, MIT Tech Review JP, Alphamatch JP, ai-souken |
| Web (China) | 21 pages | — | 🇨🇳 Zhihu, 腾讯新闻, 新浪财经, IT之家, 163.com, 金融界, EET China, Caixin, Tencent Cloud Dev, 大纪元, LINUX DO |

---

## Synthesized Findings

### 1. [update] Kimi K3.1 Pro weights shipped — now BenchLM #1 open-weight 🌐🇨🇳

**Claim:** Weights released Nov 4-5 on HuggingFace; model jumped from API-only to new open-weight #1 on BenchLM BenchAlign v5.8 (75.1, up from K3's 69.3).

**Evidence:**
- **Repo:** moonshotai/Kimi-K3.1-Pro — public, ungated, 1.56TB BF16 (96 shards), Nov 4 16:00 UTC
- **Architecture:** 2.8T total / 104B active MoE, 896 experts (16 active), 93 layers, 1.05M context, MXFP4
- **BenchLM BenchAlign v5.8:** #1/75.1 (prev: K3 was #1/69.3)
- **Agent Arena:** #1 open-weight, #13 overall; +5.1% net improvement (17,500+ real sessions)
- **TB4:** 65.7% (above GPT-6 Astra 58.2%; 0.7pp below Claude Opus 5.5 66.4%)
- **BrowseComp:** 92.1%; **HLE-Full with tools:** 70.0%
- **License:** MIT-style with $20M MaaS clause for large operators
- **Hardware:** BF16 ≈5.6TB; INT4 ≈1.4TB — consumer deployment not feasible
- **HN:** 431 points, top of three simultaneous model releases Nov 4
- **IT之家 quote:** "2.8万亿参数Kimi K3.1 Pro开放权重，登顶Agent Arena开源模型榜" ("2.8T weights released, tops Agent Arena open-source leaderboard")
- **腾讯新闻:** "3万亿参数保持全球最大开源纪录" ("3T-class: maintains world's largest open-source record")
- Moonshot simultaneously launched Kimi Hosted Agents enterprise service
- **Sources:** https://www.kimi.ai/blog/kimi-k3-1-pro | https://www.aicoder.com/news/news-20261104-kimi-k3-1-pro-open-weights-released-hugging-face-2-8t-mxfp4-license-20m-maas-clause | https://www.ithome.com/1/022/490.htm | https://news.qq.com/rain/a/20261105A04BET00 | https://finance.sina.com.cn/stock/t/2026-11-05/doc-inixrunh9585646.shtml | https://explainx.ai/blog/kimi-k3-1-pro-open-weights-benchmarks-price-terminal-bench-nov-4-2026

---

### 2. [new] Moonshot sought 8,000-GPU Blackwell clusters in Europe to bypass US curbs 🌐🇨🇳

**Claim:** CNBC Nov 5 exclusive: Moonshot approached European neocloud operators for Nvidia Blackwell inference and training capacity throughout 2026, described as "very aggressive."

**Evidence:**
- Sought clusters of 8,000+ Blackwell GPUs from European data centers
- Both inference AND training applications discussed
- Follows White House-confirmed Moonshot access via Thailand (K3 training, revealed July 2026)
- No signed leases reported
- **Nvidia:** told cloud clients globally ≥51% of Blackwell GPU services must go to non-Chinese customers (verbally communicated, new contracts only, Nov 4)
- **RASA (Remote Access Security Act):** passed House Jan 2026; pending Senate; would explicitly close cloud-compute loophole
- **Democrat Congress** (see Finding #5) now expected to advance RASA faster
- Moonshot, Nvidia, White House, DOC all declined to comment
- **Chinese media framing:** "绕过美国限制" ("bypassing US restrictions") — LINUX DO developer community notes broader precedent concern
- **Sources:** https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html | https://dealroom.co/news/170092-moonshot-sought-8-000-gpu-blackwell-clusters-in-europe-to-skirt-us-chip-curbs/ | https://www.unite.ai/moonshot-ai-discussed-european-blackwell-leases-amid-u-s-chip-curbs/ | https://linux.do/t/topic/3131427 | https://247wallst.com/investing/2026/11/04/nvidia-is-telling-cloud-clients-to-sell-at-least-51-to-non-chinese-customers/

---

### 3. [new] Huawei 960DT faces HBM crisis — smugglers strip Korean memory from server packages 🌐🇨🇳

**Claim:** Huawei's Q1 2027 Ascend 960DT is exposing a critical Samsung/SK Hynix HBM dependency; smuggling networks exploiting server-package loophole; Ascend 950DT prices surging.

**Evidence:**
- **Smuggling method:** package HBM with low-end server CPUs (export controls assess compute by CPU not memory); separate on arrival (melt solder to strip HBM stacks); high damage risk
- **Price:** HBM3E street price ≈$4,000/unit (10x+ normal); Ascend 950DT price raised to RMB 250,000 (~$37,000) ≈ Nvidia B200 price at ~50% performance
- Huawei told clients to source HBM3E themselves for 960DT installations
- **Domestic shortage:** CXMT 20-30% yield vs SK Hynix ~70% HBM3E; Fujian Jinhua below tech parity
- Cambricon, MetaX, Iluvatar CoreX all raised chip prices 20-30%
- **BIS guidance:** use of Huawei Ascend chips violates US export controls (pre-existing)
- **Chinese developer framing (Tencent Cloud):** "华为昇腾910C是中国AI产业唯一的选择" ("Ascend 910C is the only choice for China's AI industry")
- **Sources:** https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/ | https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt | https://en.sedaily.com/international/2026/11/03/smugglers-melt-solder-to-strip-korean-hbm-for-huawei | https://aiweekly.co/alerts/huawei-tells-clients-ascend-960dt-runs-on-samsung-sk-hynix-hbm | https://cloud.tencent.com/developer/article/2697481

---

### 4. [new] Tencent Hy4 and Ripple-65B: simultaneous Nov 4 open-weight triple release 🌐

**Claim:** Three open-weight models hit Hacker News front page simultaneously Nov 4: Kimi K3.1 Pro (#1), Ripple-65B (#2), Tencent Hy4 (#3) — each with cybersecurity filtering documentation.

**Tencent Hy4:**
- 770B/49B active MoE, 1M+ context, native vision + computer use (first in Hunyuan line)
- Apache 2.0 weights on HuggingFace (Hy4 preview); API live on Tencent Cloud + OpenRouter (50% discount through Dec 31)
- Full open weights date: unconfirmed ("will publish a system card when it does")
- Cybersecurity: filtered to defensive data only; Tencent admits "notable gap remains" with top proprietary models
- BenchLM BenchAlign v5.8: #10/61.5
- HN: 210 points; comment: "very thorough and therefore verrrrry slow" (data analytics user)
- **Sources:** https://www.technology.org/2026/11/05/tencent-hy4-open-source-model-defensive-cybersecurity-data/ | https://shattered.io/tencent-hy4-770b-parameters-apache-2-0-open-source-model-2026/ | https://madrobot.blog/2026/11/04/tencent-hy4-release-computer-use-open-weight/

**Ripple-65B Preview (Ricursive Intelligence):**
- 65B dense Transformer, Apache 2.0, Nov 4; co-founders Anna Goldie + Azalia Mirhoseini (chip-design AI lab, Palo Alto)
- 12T training tokens, 1M context; trained for $32M (~1/10 prior SOTA cost)
- **Terminal-Bench 2.1:** 80.52% — top self-reported US open-weight coding SOTA (beats Beam 501B at TB4)
- 1.4M rollouts vs 100M+ for Beam; Apache 2.0 on HuggingFace, Together AI, GMI Cloud, OpenRouter
- HN: 260 points
- **Sources:** https://www.marktechpost.com/2026/11/04/ricursive-ripple-65b-preview-open-weight-model/ | https://emergent.sh/news/ripple-65b-preview-hits-us-open-weight-coding | https://dataconomy.com/2026/11/06/ricursive-launches-ripple-65b-preview-claiming-us-open/

---

### 5. [update] Democrats sweep US Congress — chip export controls set to tighten 🌐🇨🇳

**Claim:** Democrats won House (258+ seats) and Senate (54 seats) on Nov 3; AI/data centers was defining voter issue; RASA/MATCH/AI OVERWATCH bills now have stronger political cover.

**Evidence:**
- 56% of voters cited AI and data centers as "crucial or major factor" in their vote
- ~24 local data-center restriction measures passed across 10 states
- Post-election Democrat calls: "national data center moratorium now"
- Goldman Sachs: states now leaning to restrict data centers = ~45% of planned US capacity
- Nasdaq dropped 5.52% on results (金融界, Nov 6)
- **NDAA implications:** MATCH Act + Chip Security Act + AI OVERWATCH still in Senate NDAA manager's amendment; conference reconciliation still needed; Democrat majority expected to push tighter controls
- **RASA:** passed House; now likelier to pass Senate given Democrat control + Moonshot Europe story (same news cycle)
- **Chinese financial media framing (163.com):** "AI产业将迎来哪些变数？" ("What uncertainties does AI industry face?")
- **Sources:** https://www.cnbc.com/2026/11/04/2026-midterm-election-results-live-updates.html | https://time.com/article/2026/11/04/midterm-elections-results-ai-industry-data-centers/ | https://www.cnbc.com/2026/11/05/democrats-data-center-restrictions-midterms.html | https://abhs.in/blog/us-midterms-2026-democrats-sweep-house-senate-ai-export-controls-iran-tech-impact | https://renstocks.substack.com/p/democrats-take-congress-what-happens | https://finance.jrj.com.cn/2026/11/06115159037418.shtml | https://www.163.com/dy/article/LB0FCBKG05119734.html

---

### 6. [new] Taiwan joins the chip-control tightening — Trade Law amendment hearing Nov 2 🌐🇨🇳

**Claim:** Taiwan legislature held Nov 2 public hearing on Trade Law amendment expanding semiconductor export controls to mainland China, tripling maximum prison term.

**Evidence:**
- Proposed new Art. 13-2: adds specific ICs, wafer materials, components, manufacturing equipment to controlled list
- Maximum penalty raised: 10 years prison + NT$5-10M fine (up from 5 years + NT$3M)
- Third-party transshipment explicitly covered with same penalties + forfeiture
- **Driver:** Taiwan-US ART agreement (Feb 2026) requires alignment with US export controls
- Background context: US chip smuggling via Taiwan as reported by BIS
- **Status:** draft; not yet voted on; definitions of "effectively controlled by mainland" still undefined
- Effectively: US + China + Taiwan simultaneously tightening semiconductor access to mainland
- **Sources:** https://www.eet-china.com/news/202611054470.html | https://24topnews.com/news/industry/taiwan-legislature-holds-hearing-on-expanding-advanced-semiconductor-e3b3dd89 | https://companies.caixin.com/2026-11-04/102500933.html

---

### 7. [new] Atria Dawn Preview: Shanghai AI Lab's 744B MIT agent model tops research leaderboards 🌐🇨🇳

**Claim:** Shanghai AI Lab's InternLM Atria Dawn Preview (Sep 11, 744B MIT) leads BenchLM's specialized agent and research leaderboards at 92.5-93.9, though benchmarks are self-reported.

**Evidence:**
- 744B MoE (built on GLM-5.2 foundation), MIT license, 256K context (1M via YarN)
- BenchLM agent leaderboard: 92.5; BenchLM research leaderboard: 93.9
- Self-reported task scores: BrowseComp 92.5, CyberGym 86.5, MLE-bench Lite 86.2, SWE-bench Pro 59.6, DeepSearchQA 96.0
- No independent verifier (Artificial Analysis etc.) has published third-party scores
- Available: HuggingFace (internlm org), ModelScope, API (global + China regions)
- **Sources:** https://techjacksolutions.com/ai-brief/shanghai-ai-lab-atria-dawn-preview-open-weight-agentic-model/ | https://www.orcarouter.ai/blog/atria-dawn-preview-quiet-release | https://pandaily.com/shanghai-ai-lab-atria-dawn-preview-744b-moe-agent | https://hokai.io/hub/models/atria-dawn-preview

---

### 8. [update] DeepSeek V4 Pro capacity shift to V4.1 Flash happening today (Nov 5) 🌐

**Claim:** V4 Pro capacity migrating to V4.1 Flash starting Nov 5 (today); full retirement Nov 19; V4.1 Pro still unreleased with no date.

**Evidence:**
- Nov 5: GPUs serving V4 Pro shifted to V4.1 Flash — V4 Pro may be slower
- Nov 19: V4 Pro retired; DeepSeek will NOT auto-forward requests to another model
- V4.1 Flash: MIT, 552B MoE, BenchLM BenchAlign v5.8 #4/65.4; 75% cheaper input, 62.5% cheaper output
- V4.1 Pro: DeepSeek named it in Sep 10 announcement but no date/size/benchmark/license confirmed as of Nov 1
- **Sources:** https://lyceum.technology/magazine/deepseek-v4-pro-retires-move-to-v4-1-flash/ | https://api-docs.deepseek.com/news/news260910/ | https://deepseek.ai/blog/deepseek-v41-flash-generally-available | https://qcode.cc/en/deepseek-v4-1-pro-status-tracker

---

### 9. [update] Qwen 4: CTO "next week" window (Nov 2-8) missed — now likely Nov 18 🌐

**Claim:** Qwen 4 release window teased by Alibaba CTO at Apsara Amsterdam (Oct 29) has passed; prediction markets now price Nov 18 as most likely; "currently in training" still the only official statement.

**Evidence:**
- Alibaba CTO said "Qwen4 next week" at Apsara Oct 29; week of Nov 2-8 passed without release (Nov 5 update)
- Official status: "currently in training" — no model card, download, API, or price
- Teased lineup: Qwen 4 Max/Flash/Plus/27B
- Prediction markets: ~93% by December; most likely Nov 18
- Code leaks still pointing to qwen4-omni-120b-think, qwen4-coder-plus, qwen4.5-max
- **Sources:** https://qcode.cc/en/qwen-4-release-date | https://felloai.com/qwen-4/ | https://www.orcarouter.ai/blog/qwen-4-leak-vllm-fuse-op

---

### 10. [update] BenchLM open-weight leaderboard reshuffle: Kimi K3.1 Pro dethrones MiMo 🌐

**Claim:** BenchLM BenchAlign v5.8 updated Nov 6: Kimi K3.1 Pro jumps to #1/75.1; Xiaomi MiMo-V2.6-Pro dropped from composite #1/73.6 to #15/57.3 on this sub-benchmark.

**Evidence (top 20 BenchAlign v5.8, Nov 6):**
- #1 Kimi K3.1 Pro 75.1 | #2 Kimi K3 69.5 | #3 Ling 3.1 Flash (InclusionAI) 65.5
- #4 DeepSeek V4.1 Flash 1017 65.4 | #5 Qwen3.8 Max 64.9 | #6 dots3-note Preview 64.3
- #7 Sage-A1.5 (InternScience) 63.1 | #8 DeepSeek V4 Pro 0813 62.7 | #9 Ornith-1.5-397B 62.5
- #10 Hy4 preview (Tencent) 61.5 | #11 GLM-5.3 (Z.AI) 61.3 | #12 GLM-5.2 60.2
- #15 MiMo-V2.6-Pro (Xiaomi) 57.3 (was composite #1/73.6 — substantial BenchAlign score gap reflects sub-benchmark evolution)
- **Source:** https://benchlm.ai/best/open-source

---

### 11. [update] China MOFCOM export control comment period ends Nov 15 — 9 days away 🌐🇨🇳

**Claim:** MOFCOM Announcement No. 48 comment period (Oct 16 – Nov 15) closing; final rule will determine whether open-source exemption remains intact and whether top-10 registration requirement expands.

**Evidence:**
- 23 AI technologies in draft (40 total across sectors); mandatory registration effective Oct 16
- Key exemptions: already-public open-source weights; API/SaaS; academic papers
- Registration required: >2T params OR >10^26 FLOPs OR global top-10 rank
- DeepSeek + MiniMax already registered (Oct 22-23); open-source use authorized for both
- **Strategic dynamic:** open-source exemption functions as "passport" through both US and Chinese regimes
- Comments to: jinxianmulu@mofcom.gov.cn; deadline Nov 15
- **Sources:** https://www.licentium.io/post/china-mofcom-most-announcement-48-export-control-catalogue-ai-16-october-2026 | https://sanctionsnews.bakermckenzie.com/china-proposes-expanded-export-controls-on-ai-biopharma-and-solar-energy-technologies/ | https://thediplomat.com/2026/10/china-wants-its-ai-to-go-global-on-its-own-terms/ | https://labs.cloudsecurityalliance.org/research/csa-research-note-china-ai-export-controls-announcement-48-2/

---

**Still true (ongoing — no new facts today):**
- **mistral-large4-le-chonk**: Weights shipped Oct 29 (confirmed); 1T/52B MoE, TB4 41%, BenchLM #33/51.5, Mistral Ecosystem Open-Weight License — https://techcrunch.com/2026/10/29/mistral-releases-weights-for-its-trillion-parameter-ai-model-targeting-cybersecurity/
- **meituan-longcat-25**: 1.6T/48B on ~50K Ascend 910C; API-only; open weights planned; independent benchmark verification still pending — https://www.techtimes.com/articles/329925/20261103/meituan-releases-longcat-25-chinese-chips-benchmark-claims-await-independent-tests.htm
- **opencode-sitemap-leak-unreleased-models**: Kimi K4, GLM-5.5 Flash, GLM-5.4, Muse Spark 1.4, DS V4.1 Pro, Qwen3.8 Max — all still empty namespaces — https://revesery.com/@alex/opencode-leak-points-to-six-unreleased-ai-models-muhkhhaa
- **glm-5-5-expected-august**: Still unreleased; leaked post-training traces (community, Nov 1); expected November; next version may be GLM-5.4 — https://cellcog.ai/blog/glm-5-5-release-date/ | https://felloai.com/glm-5-5/
- **polymarket-us-chinese-model-ban**: 17% Yes / 83% No (slight uptick from 15.5% Oct 28); $122,467 volume; DHS federal ban didn't resolve market — https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223
- **huawei-ascend-960-connect2026**: 960DT Q1 2027; 2 FP8 PFLOPS, 288GB HiZQ, 9.6TB/s; 960PR Q3 2027; now known HBM dependency on Samsung/SK Hynix — https://wccftech.com/huawei-ascend-960dt-960pr-2027-970-2028980-2028-superpods-ai/
- **kimi-k3-gpu-crunch-subscription-pause** / **kimi-k31-pro-quota-crisis**: Q1 2027 HKEX IPO; ~$50B valuation; weights shipped; IPO track continues — https://www.japantimes.co.jp/business/2026/10/06/moonshot-ai-ipo-plans/
- **double-curtain-us-china-export-controls**: DHS DeepSeek ban + China MOFCOM registration ongoing; Nvidia 51% rule adds new dimension — https://www.winzheng.com/en/article/china-ai-export-controls-23-technologies-deepseek-minimax-op
- **china-domestic-chip-mass-pivot**: Huawei >50% China AI accelerator market; Meituan 50K Ascend 910C confirmed frontier-scale; HBM crisis threatens 960DT timeline
- **xi-brics-ai-open-source-zone**: BRICS AI open-source zone; WAICO facilitation; DeepSeek+Qwen to Global South — https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road
- **deepseek-v4-1-flash-release**: BenchLM #4/65.4; MIT; V4 Pro capacity shift to V4.1 Flash starting Nov 5
- **benchlm-aug10-rankings-minimax-leads**: Updated — Kimi K3.1 Pro now #1/75.1
- **xiaomi-mimo-frontier-entry** / **xiaomi-mimo-v26-tops-leaderboard**: MiMo-V2.6-Pro dropped to BenchAlign #15/57.3; V2.7 Pro still pending
- **chinese-model-wave-oct-nov-2026**: K3.1 Pro ✓, Hy4 API ✓; Qwen 4/DS V4.1 Pro/GLM-5.5/Muse Spark still pending
- **dhs-deepseek-federal-ban-oct20**: DHS ban still in force; Polymarket 17% Yes
- **deepseek-deepinfer-open-source**: DeepInfer production dual NVIDIA/Ascend support ongoing
- **jp-deepseek-japanese-cultural-benchmark**: Japanese enterprise three-layer risk framework confirmed by Qiita deep-dive (Oct 10)
- **distillation-scale-data** / **anthropic-distillation-report-sep10**: No new enforcement as of Nov 6
- **us-china-ai-safety-talks-sep24**: Trade truce to Jan 10, 2027; DHS ban still cited by China as violating Xi-Trump consensus
- **openeurollm-european-sovereign**: Mistral Large 4 weights de facto European open frontier; EU fragility on Chinese open-weight dependency ongoing — https://www.bruegel.org/first-glance/tough-choices-ahead-us-pushes-global-artificial-intelligence-divide
- **eu-ai-act-august-enforcement**: GPAI enforcement ongoing; no Chinese company signed GPAI Code of Practice
- **tsai-open-source-europe-sovereignty**: Alibaba Joe Tsai open-source-as-sovereignty framing; Bruegel EU fragility analysis ongoing
- **tencent-oracle-offshore-chip-deal**: Tencent $7B/100K chips Oracle SE Asia; RASA (now likelier with Democrat Senate) would close this loop
- **deepseek-funding-12b-tencent-catl**: $12B round; implied val ~$180-200B; 2027 STAR IPO

---

## Cross-Source Patterns

**Pattern 1: Triple lock-tightening on chip access (Nov 2-6)**
- US (DHS ban Oct 20 + Nvidia 51% rule Nov 4 + RASA advancing)
- China (MOFCOM Announcement 48, comment closes Nov 15)
- Taiwan (Trade Law amendment hearing Nov 2)
- Platforms: Web (global), Web (China); Chinese media: "对中生意再添变数" ("another uncertainty for China business")

**Pattern 2: Cybersecurity capability pruning as open-weight precondition**
- Kimi K3.1 Pro: cybersecurity data removed from mid-training+RL; documented in model card; exploit benchmark 81% (filtered) vs 90.5% (unfiltered)
- Tencent Hy4: filtered to defensive cybersecurity only; system card promised at open-weight release
- HN discussion: both models noted for the pruning; community noted the new norm
- Platforms: Web (global), HN, Web (China)

**Pattern 3: European and offshore compute as the contested frontier**
- Moonshot/Europe Blackwell lease discussions (CNBC Nov 5)
- Nvidia 51% non-Chinese customer rule (Nov 4) responds to same dynamic
- RASA (Remote Access Security Act) explicitly targets this loophole
- Democrat Congress makes RASA more likely; same week as Moonshot CNBC story
- Platforms: Web (global), Web (China)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (various) | Kimi K3.1 Pro Weights Released | 431 | — | "Kimi K3.1 Pro and Hy4 both trimmed their offensive security abilities" | https://www.kimi.ai/blog/kimi-k3-1-pro |
| (various) | Ripple-65B Preview (Ricursive) | 260 | — | "80.5 on TB2.1 with 1.4M rollouts vs 100M+ for Beam" | https://www.marktechpost.com/2026/11/04/ricursive-ripple-65b-preview-open-weight-model/ |
| (various) | Tencent Hy4 Open Weight | 210 | — | "very thorough and therefore verrrrry slow" (data analytics) | https://www.technology.org/2026/11/05/tencent-hy4-open-source-model-defensive-cybersecurity-data/ |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US Government removes public access to a major Chinese AI model in 2026? | 17% Yes / 83% No | $122,467 | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | CNBC | https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html | Moonshot European Blackwell compute — primary source |
| 🌐 | TrendForce | https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/ | HBM smuggling method and Huawei 960DT supply crisis |
| 🌐 | Seoul Economic Daily | https://en.sedaily.com/international/2026/11/03/smugglers-melt-solder-to-strip-korean-hbm-for-huawei | Melt-solder HBM stripping technique detail |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/huawei-tells-clients-ascend-960dt-runs-on-samsung-sk-hynix-hbm | Huawei 960DT Samsung/SK Hynix disclosure |
| 🌐 | The Next Web | https://thenextweb.com/news/huawei-hbm-smuggling-samsung-sk-hynix-ascend-960dt | HBM smuggling policy context |
| 🌐 | Tom's Hardware | https://tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims | Nvidia 51% non-Chinese customer rule |
| 🌐 | 247 Wall St | https://247wallst.com/investing/2026/11/04/nvidia-is-telling-cloud-clients-to-sell-at-least-51-to-non-chinese-customers/ | Nvidia rule confirmation |
| 🌐 | CNN | https://www.cnn.com/2026/11/05/politics/live-news/midterm-election-congress | US midterm results |
| 🌐 | TIME | https://time.com/article/2026/11/04/midterm-elections-results-ai-industry-data-centers/ | AI as voter issue — 56% cited it |
| 🌐 | CNBC | https://www.cnbc.com/2026/11/05/democrats-data-center-restrictions-midterms.html | Democrat data center moratorium calls |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Live open-weight leaderboard — Kimi K3.1 Pro #1/75.1 |
| 🌐 | BenchLM | https://benchlm.ai/best/research | Atria Dawn Preview tops research at 93.9 |
| 🌐 | Kimi | https://www.kimi.ai/blog/kimi-k3-1-pro | Official K3.1 Pro tech blog |
| 🌐 | TechCrunch | https://techcrunch.com/2026/10/29/mistral-releases-weights-for-its-trillion-parameter-ai-model-targeting-cybersecurity/ | Mistral Large 4 weights (Oct 29, confirmed) |
| 🌐 | Mistral | https://mistral.ai/news/mistral-large-4-oss/ | Mistral Large 4 OSS page |
| 🌐 | Licentium | https://www.licentium.io/post/china-mofcom-most-announcement-48-export-control-catalogue-ai-16-october-2026 | China MOFCOM Announcement 48 primary analysis |
| 🌐 | The Diplomat | https://thediplomat.com/2026/10/china-wants-its-ai-to-go-global-on-its-own-terms/ | China AI export strategy analysis |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/11/04/ricursive-ripple-65b-preview-open-weight-model/ | Ripple-65B announcement |
| 🌐 | Emergent | https://emergent.sh/news/ripple-65b-preview-hits-us-open-weight-coding | Ripple-65B TB2.1 score |
| 🌐 | Technology.org | https://www.technology.org/2026/11/05/tencent-hy4-open-source-model-defensive-cybersecurity-data/ | Tencent Hy4 cybersecurity filtering detail |
| 🌐 | Shattered.io | https://shattered.io/tencent-hy4-770b-parameters-apache-2-0-open-source-model-2026/ | Hy4 specs and Apache 2.0 confirmation |
| 🌐 | LongCat AI | https://www.longcatai.org/news/longcat-2-5 | Meituan LongCat-2.5 official page |
| 🌐 | TechJack | https://techjacksolutions.com/ai-brief/shanghai-ai-lab-atria-dawn-preview-open-weight-agentic-model/ | Atria Dawn Preview announcement |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/atria-dawn-preview-quiet-release | Atria Dawn Preview analysis |
| 🌐 | CSIS | https://www.csis.org/analysis/chinas-open-weight-challenge-us-ai-leadership | China Open-Weight Challenge analysis |
| 🌐 | Bruegel | https://www.bruegel.org/first-glance/tough-choices-ahead-us-pushes-global-artificial-intelligence-divide | US-China AI divide — EU perspective |
| 🌐 | 24TopNews | https://24topnews.com/news/industry/taiwan-legislature-holds-hearing-on-expanding-advanced-semiconductor-e3b3dd89 | Taiwan semiconductor export control hearing |
| 🌐 | EET China | https://www.eet-china.com/news/202611054470.html | Taiwan Trade Law amendment details (Chinese) |
| 🌐 | Deal Room | https://dealroom.co/news/170092-moonshot-sought-8-000-gpu-blackwell-clusters-in-europe-to-skirt-us-chip-curbs/ | Moonshot 8,000 Blackwell GPU detail |
| 🌐 | Unite.AI | https://www.unite.ai/moonshot-ai-discussed-european-blackwell-leases-amid-u-s-chip-curbs/ | Moonshot Europe compute summary |
| 🌐 | Cellcog | https://cellcog.ai/blog/glm-5-5-release-date/ | GLM-5.5 status tracker |
| 🌐 | FelloAI | https://felloai.com/glm-5-5/ | GLM-5.5 November release window |
| 🌐 | QCode | https://qcode.cc/en/qwen-4-release-date | Qwen 4 live tracker |
| 🌐 | Lyceum | https://lyceum.technology/magazine/deepseek-v4-pro-retires-move-to-v4-1-flash/ | DeepSeek V4 Pro retirement guide |
| 🇯🇵 | Qiita | https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6 | Chinese open-weight model risk survey (n_hiraoka, Oct 10) |
| 🇯🇵 | Blackford | https://blackford.co.jp/columns/0322-chinese-llm-enterprise-usage-regulatory-risk-2026-oct | Enterprise Chinese LLM regulatory risk framework |
| 🇯🇵 | MIT Tech Review JP | https://www.technologyreview.jp/s/378017/whats-next-for-chinese-open-source-ai/ | Chinese open models dominate global developer usage |
| 🇯🇵 | Alphamatch AI JP | https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026 | Open-source LLM revolution 2026 — Japanese analysis |
| 🇯🇵 | Exawizards | https://exawizards.com/column/ai-trend/news-07-05-2026-2/ | US open-source AI catching up with China |
| 🇯🇵 | Zenn | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Chinese AI models practical guide for developers |
| 🇯🇵 | hungyichen | https://www.hungyichen.com/ja/insights/deepseek-open-source-ai-geopolitics | DeepSeek geopolitics — democratization vs strategic tool |
| 🇨🇳 | IT之家 | https://www.ithome.com/1/022/490.htm | Kimi K3.1 Pro Agent Arena #1 coverage |
| 🇨🇳 | 腾讯新闻 | https://news.qq.com/rain/a/20261105A04BET00 | Kimi K3.1 Pro weights — 3T record maintained |
| 🇨🇳 | 新浪财经 | https://finance.sina.com.cn/stock/t/2026-11-05/doc-inixrunh9585646.shtml | Kimi K3.1 Pro Agent Arena leaderboard coverage |
| 🇨🇳 | 知乎 | https://zhuanlan.zhihu.com/p/2097141377679283273 | Kimi K3.1 Pro community analysis |
| 🇨🇳 | 知乎 | https://zhuanlan.zhihu.com/p/2097265556500104562 | K3.1 Pro exceeds GPT-6 on TB4 — community benchmark |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/LB093O5G0514R9P4.html | K3.1 Pro weights + Hosted Agents launch |
| 🇨🇳 | 大纪元 | https://www.epochtimes.com/gb/26/11/5/n14883823.htm | Moonshot Europe Nvidia chips — Chinese report |
| 🇨🇳 | LINUX DO | https://linux.do/t/topic/3131427 | Moonshot European Blackwell compute — dev community |
| 🇨🇳 | 腾讯云开发者 | https://cloud.tencent.com/developer/article/2697481 | Ascend 910C "only choice" — Chinese dev community |
| 🇨🇳 | 新浪财经 | https://finance.sina.com.cn/stock/usstock/c/2026-11-06/doc-inixttce5171077.shtml | Democrat data center moratorium calls — Chinese media |
| 🇨🇳 | 金融界 | https://finance.jrj.com.cn/2026/11/06115159037418.shtml | Nasdaq -5.52% on Democrat wins + AI regulation fear |
| 🇨🇳 | 爱集微 | https://news.cnyes.com/news/id/6651657 | Democrat Congress: Nvidia CEO to face chip export hearings |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/LB0FCBKG05119734.html | Midterms: AI industry uncertainty analysis |
| 🇨🇳 | EET China | https://www.eet-china.com/news/202611054470.html | Taiwan semiconductor export controls expansion |
| 🇨🇳 | 财新 | https://companies.caixin.com/2026-11-04/102500933.html | Taiwan semiconductor export controls (Caixin) |

---

## Stats Block

```
├─ 🟢 HN: 3 stories │ 901 combined points
├─ 📊 Polymarket: 1 market │ $122,467 volume
├─ 🌐 Web: 68 pages │ 🇯🇵 7 │ 🇨🇳 21
└─ 🗣️ Top voices: @n_hiraoka (Qiita), @kent_kamome (Zenn) │ IT之家, 腾讯新闻, 知乎, 金融界, LINUX DO
```

---

## Out of Scope but Notable

- **Ricursive Intelligence chip-design angle**: Ripple-65B's lab (Goldie + Mirhoseini) is a chip-design AI startup, not a pure LLM lab. Training a frontier coding model for $32M as a side-product of chip-design research suggests cross-domain resource efficiency gains that may generalize. Possibly fits `paradigm-watch` (chip-design AI collaterally producing competitive LLMs at 1/10 cost).

- **Democrat Congress "data center moratorium" call**: Not an AI model geopolitics finding, but the demand for a nationwide data center moratorium post-midterms represents a potential structural shift in US AI infrastructure capacity that would indirectly benefit non-US model training (if US training capacity contracts). Possibly fits `enterprise-ai-signals` or a new policy topic.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for all three Japanese and Chinese language queries (error code 90d2). Fell back to WebSearch with native-language queries — substantial Chinese hub coverage still achieved via direct WebSearch and IT之家/知乎/腾讯新闻 fetches.
- **Bluesky:** No data — this run did not access Bluesky (not in failed sources; SOURCE HEALTH: bluesky=OK but not searched). Coverage gap on open-source AI discourse there.
- **Reddit:** Excluded per instructions (reddit.com blocked).
- **X/Twitter:** Excluded per instructions.
- **YouTube:** Not searched.
- **ScrapeCreators (Instagram/TikTok/LinkedIn):** Not accessed; likely minimal relevance for this topic.
- **Zhihu direct fetch:** HTTP 403 on direct fetch of two Zhihu articles; content obtained via WebSearch summaries instead.
- **Blackford.co.jp:** HTTP 403 on direct fetch.
- **bannedbook.org:** HTTP 403 on direct fetch.
- **EET China:** Fetch timeout; content obtained via WebSearch.
- **Polymarket:** Only one relevant market found; "Best Chinese AI Company end of October" market already resolved; no live market on that question.
- **BenchLM composite rank for Kimi K3.1 Pro:** Agent Arena #1 among open-weight, BenchAlign v5.8 #1/75.1 confirmed; composite (all-task) rank not explicitly extracted.
- **Coverage estimate:** ~78% — strong model release, geopolitics, and hardware coverage; gaps in social media (Bluesky, Twitter) and some Chinese hub direct-fetch failures.

---

## Key Quotes

> "2.8万亿参数Kimi K3.1 Pro开放权重，登顶Agent Arena开源模型榜" ("2.8T weights released, tops Agent Arena open-source leaderboard") — IT之家 ([link](https://www.ithome.com/1/022/490.htm)) 🇨🇳

> "Dangers that persist even when running open-weight models locally have been demonstrated by multiple independent studies" (「オープンウェイトのモデルをローカル実行しても消えない危険が、複数の独立した研究によって実証されている」) — @n_hiraoka on Qiita ([link](https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6)) 🇯🇵

> "America cannot win the AI race unless America's AI infrastructure wins worldwide" — Nvidia statement on Moonshot European compute ([link](https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html)) 🌐

> "华为昇腾910C不是最好的AI芯片，但它是中国AI产业唯一的选择——然后呢" ("Huawei Ascend 910C is not the best AI chip, but it's the only choice for China's AI industry — what next?") — Tencent Cloud developer community ([link](https://cloud.tencent.com/developer/article/2697481)) 🇨🇳

> "Kimi K3.1 Pro and Hy4 both trimmed their offensive security abilities" — Hacker News commenter on Nov 4 open-weight triple release ([link](https://madrobot.blog/2026/11/04/tencent-hy4-release-computer-use-open-weight/)) 🌐

> "The claim that complete security auditing is possible simply because weights are public is not supported by current technology" (「公開ウェイトだから安全性を完全に監査できるという主張は、現状の技術では成立しない」) — @n_hiraoka on Qiita ([link](https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6)) 🇯🇵

> "56% of voters said that AI and data centers were a 'crucial or major factor' in their vote for Congress" — NBC exit poll, cited in TIME ([link](https://time.com/article/2026/11/04/midterm-elections-results-ai-industry-data-centers/)) 🌐

> "民主党拿下参众两院多数引发AI数据中心监管担忧，纳指跌5.52%" ("Democrats win both chambers: AI data-center regulation fears push Nasdaq down 5.52%") — 金融界 ([link](https://finance.jrj.com.cn/2026/11/06115159037418.shtml)) 🇨🇳
