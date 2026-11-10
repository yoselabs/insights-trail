# Open-Source & Non-US Models / AI Geopolitics — Daily Briefing
**Date:** 2026-11-10
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan), Web (China), Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Polymarket | 2 markets | ~$105K volume | 🌐 US-removes-public-access-Chinese-AI; Muse Spark 1.4 by Nov 30 |
| Web (global) | 72 pages | — | 🌐 via WebSearch, keyless |
| Web (Japan) | 9 pages | — | 🇯🇵 Qiita, Zenn, Yahoo JP, Reuters JP, Zaikei, Xenospectrum, PromptQuorum, AITeller, hungyichen |
| Web (China) | 17 pages | — | 🇨🇳 新浪科技, 腾讯新闻, 知乎, CSDN, 掘金, 凤凰网, DoNews, RFA普通话, 禁闻网, 东方日报, IC.work, 智源社区 |

---

## Synthesized Findings

### 1. [new] Nvidia Jensen Huang / Alice Huang spy scandal — $192B evaporated, legislation accelerates 🌐🇨🇳

**Claim:** Nvidia board opened independent investigation Nov 8 after Jensen Huang admitted affair with Alice Huang (Megaspeed), accused by US intelligence of being a Chinese Ministry of State Security asset and channeling advanced AI chips to China via Singapore.

**Evidence:**
- **Alice Huang / Megaspeed:** Singapore cloud company; purchased ~$4.6–5B in Nvidia chips; accused of helping China-headquartered firms access restricted chips via "Singapore washing" (remote compute in SE Asia data centers)
- **Huang admission:** email to staff Nov 8: "I was unfaithful to my wife. My actions hurt her and our children."
- **Board position:** "no reason to believe national security or NVIDIA secrets were compromised"; independent investigation underway (4–6 weeks)
- **Huang remains CEO:** 85% analyst probability he stays; 15% removal
- **Market reaction:** Nvidia -4% Monday, -6% Tuesday; ~$192B market cap erased; AMD +13%, Broadcom +10% (key-person risk sell-off, not sector-wide)
- **Congressional response:**
  - 3 Republican House committee chairs: invited Huang for closed-door briefing Nov 18
  - Senators Banks (R) + Warren (D): "It is time for Congress to take decisive action to pass key bills like the AI Overwatch Act in the NDAA"
  - FBI investigating
- **Geopolitical impact:** scandal directly cited as catalyst for AI Overwatch Act, RASA, Chip Security Act passage; Huang's advocacy for China chip sales now politically untenable
- **China MFA:** allegations "entirely groundless, speculative and intended to smear and malign China"
- **Chinese media framing (RFA 普通话):** "美国对中管制高阶芯片的漏洞在哪里？" ("Where are the loopholes in US high-end chip controls for China?") — focus on Megaspeed's $4.6B+ purchases and Singapore channel
- **Sources:** https://www.cnbc.com/2026/11/08/nvidia-jensen-huang-investigation-china-spy.html | https://www.cnbc.com/2026/11/08/jensen-huang-nvidia-china-spy-congress.html | https://www.cnbc.com/2026/11/10/nvidia-nvda-jensen-huang-affair-chinese-spy.html | https://techcrunch.com/2026/11/09/jensen-huangs-affair-with-alleged-chinese-spy-puts-nvidias-china-ambitions-under-scrutiny/ | https://www.cnn.com/2026/11/08/business/nvidia-investigation-ceo-jensen-huang | https://www.wbiw.com/2026/11/10/senators-banks-warren-statement-on-national-security-concerns-surrounding-nvidia/ | https://finance.yahoo.com/markets/stocks/articles/nvidia-falls-5-board-probes-134356169.html | https://aljazeera.com/economy/2026/11/10/nvidia-spy-scandal-fuels-debate-over-chip-exports-to-china | https://www.rfa.org/mandarin/yataibaodao/2026/11/10/nvidia-jensen-huang-alice-huang-national-security/ | https://www.orientaldaily.com.my/news/business/2026/11/10/861807

---

### 2. [new] Baidu ERNIE 5.5 Flash Base open-sourced — first Baidu weights in 16 months 🌐🇨🇳

**Claim:** Baidu released ERNIE-5.5-Flash-Base pre-training checkpoint on Hugging Face Nov 5 — a 280B/14B MoE model trained on 33.5T tokens. "Strategic reversal" for a lab that last open-sourced in June 2025.

**Evidence:**
- **Architecture:** 280B total / 14B active MoE; sparse attention; FlashMask-4 custom attention operator
- **Training:** 33.5 trillion tokens; 128K context (stretches to 1M inference)
- **Availability:** `baidu/ERNIE-5.5-Flash-Base` FP8 (~288GB) + BF16 (~573GB) on HuggingFace and ModelScope
- **License:** Baidu's own (NOT Apache/MIT); **excludes EU, UK, South Korea**; free under $50M annual revenue; >$50M requires written approval
- **Release type:** pure pre-training checkpoint — no instruct model, no post-training; developers must fine-tune; instruct version ERNIE 5.5 Flash planned but unscheduled
- **Benchmarks (Baidu self-reported):** MMLU 93.3, MMLU-Pro 78.4, HumanEval+ 82.3, MBPP+ 81.5; first in 24/30 benchmarks vs DeepSeek-V4-Flash-Base, Hy3-preview-Base, MiMo-V2.5-Base
- **BenchLM:** not yet ranked (pre-training checkpoint; no instruct version for ranking)
- **Baidu World 2026:** Nov 12 Beijing conference — expected to bring post-trained ERNIE 5.5 Flash and Apollo World (physical AI) showcase
- **Chinese media framing (新浪科技):** "16个月后重回开源" (returning to open-source after 16 months); framed as competitive response to Kimi K3.1 Pro + Tencent Hy4 open-weight wave
- **Sources:** https://www.chinatechnews.com/2026/11/06/132184-in-strategic-reversal-baidu-open-sources-280-billion-parameter-ernie-5-5-ai-model | https://the-decoder.com/baidu-releases-ernie-5-5-flash-base-with-280-billion-parameters-as-an-open-source-foundation-model/ | https://www.marktechpost.com/2026/11/05/baidu-ernie-5-5-flash-base-280b-moe/ | https://www.orcarouter.ai/blog/ernie-5-5-flash-base-open-weights-license | https://explainx.ai/blog/baidu-ernie-5-5-flash-base-280b-open-weights-moe-14b-active-1m-context-vllm-sglang-2026 | https://finance.sina.com.cn/tech/roll/2026-11-06/doc-inixuize5487379.shtml | https://juejin.cn/post/7704578494383046671

---

### 3. [update] Qwen4 benchmark leak: Flash beats Opus 5.5 — but still unreleased 🌐🇨🇳

**Claim:** Leaked GameFeel Bench scores (circulated Nov 7-8) show Qwen4-Flash at 49.9, beating Claude Opus 5.5 xHigh (47.2); Alibaba stealth-released "Qoduck" in Qoder IDE as preview. Official release still imminent but no weights/API as of Nov 10.

**New facts since Nov 6:**
- Qwen4-Flash leaked GameFeel Bench: **49.9** (vs Opus 5.5 xHigh 47.2 — first domestic Chinese model to lead Opus 5.5 in this category); Qwen4-27B 44.6
- Cost: Qwen4-Flash $0.40/task vs Opus 5.5 $2.60 — **~85% cheaper**
- Alibaba released "Qoduck" in Qoder IDE (Nov 7) — stealth, no public API, free for individuals, almost certainly Qwen4 preview
- Alibaba Nov 6 teaser poster: "北冥有鱼" (Kun — massive fish from Zhuangzi), four named variants confirmed (Max/Flash/Plus/27B)
- Qwen4 Max reportedly to remain API-only; Max tier still closed
- Chinese media: 腾讯新闻, 凤凰网, 新浪 all ran "国产AI迎来高光时刻" ("Domestic AI reaches a highlight moment") coverage

**Caveats:**
- GameFeel Bench = game-development creativity benchmark; not standard MMLU/Arena
- All figures from pre-release leaks; unendorsed by Alibaba
- Official status: "in training"; no weights/model card/price published as of Nov 10

**Sources:** https://news.qq.com/rain/a/20261108A0BQ9400 | https://aiproducthub.cn/newsflash/alibaba-qwen4-flash-gamefeel-bench-score-beats-claude-opus-5-5/ | https://tech.ifeng.com/c/8xuNurhHW1w | https://qcode.cc/en/qwen-4-release-date | https://shattered.io/qwen4-launch-alibaba-open-source-promise-doubt-470-models-2026/ | https://www.aitoollab.cn/articles/qwen4-teaser-qoduck-preview-2026/ | https://www.yottalabs.ai/post/qwen-4-release-date-what-is-known-how-to-prepare-2026

---

### 4. [update] Commerce Dept + White House: extending remote access chip restrictions 🌐

**Claim:** Commerce Dept plans to require China-headquartered firms to obtain licenses for Blackwell/H200 chips even when physically outside China (Nov 9); White House sent feedback backing AI Overwatch provision closing cloud loophole.

**New facts since Nov 6:**
- Commerce Dept (Nov 9): extending May 2026 licensing guidance — now covers remote *use* of chips by China-HQ firms, even in SE Asian/European data centers
- Cloud providers must trace corporate structures through subsidiaries to verify non-Chinese ownership
- White House feedback to Congressional staff: AI Overwatch Act should include provision ordering Commerce to close remote access loophole
- Three-bill convergence: MATCH Act + Chip Security Act + AI Overwatch Act all in Senate NDAA manager's amendment
- Nvidia spy scandal removed Huang's voice against export controls; bipartisan alignment strengthened

**Sources:** https://cryptobriefing.com/commerce-department-blocks-china-remote-nvidia-access/ | https://fourweekmba.com/ai-white-house-said-to-back-closing-nvidia-chip-remote-access/ | https://huggingnews.com/ai/white-house-weighs-in-on-legislation-to-close-cloud-loophole-for-ai-chip-bea30795 | https://huggingnews.com/us-politics/three-bipartisan-export-bills-target-chinese-cloud-access-to-ai-chips-0e675f79

---

### 5. [update] Polymarket Chinese AI model ban: 21% Yes, up from 17% 🌐

**Claim:** "US Government removes public access to major Chinese AI model in 2026" market moved to ~21% Yes (from 17% Nov 6, 15.5% Oct 28); Nvidia spy scandal cited as upward pressure.

**New facts since Nov 6:** +4pp move in 4 days; $105K total volume (~same as Nov 6); DHS ban, Nvidia scandal, Democrat Congress, and Commerce remote access extension all as cited factors

**Source:** https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223

---

**Still true (ongoing — no new facts today):**
- **kimi-k31-official-teaser / kimi-k3-weights-open-source:** Kimi K3.1 Pro weights remain BenchLM #1/74.6 (Nov 7 reading); Agent Arena #1 open-weight; MIT license with $20M MaaS clause — https://www.kimi.ai/blog/kimi-k3-1-pro
- **tencent-hy4-preview-apache / tencent-hy4-open-source-release:** Hy4 live (Tencent Cloud + OpenRouter); Apache 2.0 preview weights; full weights + system card still pending — https://www.technology.org/2026/11/05/tencent-hy4-open-source-model-defensive-cybersecurity-data/
- **mistral-large4-le-chonk / mistral-frontier-moe-silent:** Mistral Large 4 weights shipped Oct 29; Mistral Ecosystem Open-Weight License; TB4 41%, BenchLM #33/51.5 — https://mistral.ai/news/mistral-large-4-oss/
- **meituan-longcat-25:** 1.6T/48B on ~50K Ascend 910C; API-only; independent benchmark verification still pending — https://www.longcatai.org/news/longcat-2-5
- **opencode-sitemap-leak-unreleased-models:** Kimi K4, GLM-5.5 Flash, GLM-5.4, Muse Spark 1.4, DS V4.1 Pro, Qwen3.8 Max — all still empty namespaces — https://revesery.com/@alex/opencode-leak-points-to-six-unreleased-ai-models-muhkhhaa
- **glm-5-5-expected-august:** Still unreleased; Z.ai flagship still GLM-5.3; GLM-5.4 forecast Nov 15–Dec 23 — https://cellcog.ai/blog/glm-5-5-release-date/
- **deepseek-v4-pro-retirement-reversed / deepseek-v4-flash-vision-exp:** V4 Pro capacity shift to V4.1 Flash ongoing since Nov 5; full retirement Nov 19; V4.1 Pro still unreleased (partner eval sightings Nov 1) — https://lyceum.technology/magazine/deepseek-v4-pro-retires-move-to-v4-1-flash/
- **china-mofcom-ai-export-controls-draft-oct16:** Comment period closes Nov 15 (5 days); open-source/API still exempt; final rule will determine fate of exemptions — https://sanctionsnews.bakermckenzie.com/china-proposes-expanded-export-controls-on-ai-biopharma-and-solar-energy-technologies/
- **huawei-ascend-960-connect2026 / huawei-960dt-hbm-smuggling-crisis:** 960DT Q1 2027; HBM smuggling $4,000/unit; CXMT 20-30% yield; no new updates since Nov 3 — https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/
- **moonshot-blackwell-europe-compute:** No signed leases reported; Nvidia 51% rule still in force; RASA still advancing — https://www.cnbc.com/2026/11/05/moonshot-ai-nvidia-chips-europe-china.html
- **nvidia-51pct-non-chinese-customer-rule:** Still verbally communicated to cloud clients; new contracts only; Cloud providers scrambling to find non-Chinese clients — https://www.tomshardware.com/tech-industry/data-centers/nvidia-tells-data-center-operators-to-limit-business-from-chinese-customers-with-new-global-restrictions-report-claims
- **rasa-senate-pending-cloud-loophole:** Still in Senate Banking Committee; White House now actively backing provision; Democrat Senate makes passage more likely — https://www.congress.gov/bill/119th-congress/house-bill/2683
- **trump-diffusion-rule-remote-compute / us-midterms-2026-democrat-sweep-ai-impact:** Democrat Congress confirmed; RASA/MATCH/AI Overwatch advancing; Nvidia scandal amplifies political will — https://www.cnbc.com/2026/11/04/2026-midterm-election-results-live-updates.html
- **taiwan-trade-law-semiconductor-export-controls:** Still at draft/hearing stage (Nov 2 hearing); not voted on — https://24topnews.com/news/industry/taiwan-legislature-holds-hearing-on-expanding-advanced-semiconductor-e3b3dd89
- **double-curtain-us-china-export-controls:** US DHS ban + MOFCOM No. 48 + Nvidia 51% rule + Taiwan hearing + Commerce remote access extension + AI Overwatch = five-layer tightening cycle; Apache 2.0 weights remain outside all regimes — https://www.licentium.io/post/china-mofcom-most-announcement-48-export-control-catalogue-ai-16-october-2026
- **huawei-ascend-ecosystem-inflection / china-domestic-chip-mass-pivot:** Huawei >50% China AI accelerator market; 960DT HBM crisis is key constraint; Meituan LongCat-2.5 (50K 910C) frontier-scale confirmed — https://nexuswild.com/news/huawei-ai-chips-china-semiconductor-strategy-export-controls-2026/
- **deepseek-funding-12b-tencent-catl:** $12B round; Tencent+CATL; ~$180-200B val; 2027 STAR IPO — https://the-decoder.com/catl-and-tencent-back-deepseeks-ballooning-funding-round-as-the-ai-startup-eyes-a-2027-ipo/
- **tencent-oracle-offshore-chip-deal:** Tencent $7B/100K chips Oracle SE Asia; Commerce remote access extension + RASA would close this — https://www.theregister.com/2026/10/02/tencent_oracle_chip_lease_asia/
- **benchlm-oct16-rankings-step5-ling:** BenchLM Nov 7 — Kimi K3.1 Pro #1/74.6; Ling 3.1 Flash #3/65.3; MiMo-V2.6-Pro #15/57.2 — https://benchlm.ai/best/open-source
- **chinese-model-wave-oct-nov-2026:** Kimi K3.1 Pro ✓, Hy4 API ✓, Baidu ERNIE 5.5 base ✓; Qwen4/DS V4.1 Pro/GLM-5.5 still pending
- **open-weight-licensing-bifurcation:** Baidu adds restrictive own-license (excludes EU/UK/Korea) to the spectrum; MIT/Apache dominant Chinese labs vs Baidu/Moonshot proprietary licenses
- **xi-brics-ai-open-source-zone:** BRICS AI open-source zone ongoing; WAICO facilitation; Baidu ERNIE now also joining the global open-weight supply
- **openeurollm-european-sovereign:** No OpenEuroLLM flagship; Mistral Large 4 de facto European open frontier; EU fragility ongoing
- **sakana-fugu-ultra-jp-orchestration:** Fugu Ultra v2 routing model (Sep 11); LiveCodeBench v6 #1 at 93.2% — no new updates — https://sakana.ai/fugu/
- **jp-deepseek-japanese-cultural-benchmark:** Japanese enterprise three-layer risk framework (Qiita Oct 10) still active reference; no new Qiita/Zenn articles this week — https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6
- **eu-ai-act-august-enforcement / eu-enisa-jrc-chinese-ai-testing:** GPAI enforcement ongoing; no new ENISA updates — https://digital-strategy.ec.europa.eu/en/news/commission-starts-enforcing-ai-act-rules-and-new-transparency-requirements-2-august
- **deepseek-deepinfer-open-source / deepseek-huawei-ascend-cuda-parity:** DeepInfer dual NVIDIA/Ascend production ongoing — https://github.com/deepseek-ai/DeepInfer
- **us-china-ai-safety-talks-sep24:** Trade truce to Jan 10, 2027; no new diplomatic developments — https://www.tbsnews.net/tech/china-says-us-deepseek-ban-disregards-xi-trump-consensus-1578726
- **distillation-scale-data / anthropic-distillation-report-sep10:** No enforcement updates — https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/
- **carnegie-china-us-ai-talent:** China 40.6% global AI researcher share vs US 34.2%; no new data — https://presenc.ai/research/china-ai-talent-2026
- **meta-muse-glimmer-us-open-weight:** Muse Spark Open (Oct 15, 816B/42B) BenchLM top-10; 1.4 prediction market at 61.5% No by Nov 30 — https://www.marktechpost.com/2026/10/15/meta-muse-spark-open-816b-open-weight-model/
- **ripple-65b-ricursive-us-coding-sota / nemotron-3-ultra-us-open-weight:** Ripple-65B (Apache 2.0, TB2.1 80.52%) and Nemotron 3.5 Bolt remain Nov 4/Oct 15 US open-weight flagships — https://emergent.sh/news/ripple-65b-preview-hits-us-open-weight-coding
- **kimi-k31-pro-quota-crisis / kimi-k3-gpu-crunch-subscription-pause:** Moonshot HKEX IPO Q1 2027; ~$50B val; weights shipped — https://www.japantimes.co.jp/business/2026/10/06/moonshot-ai-ipo-plans/
- **deepseek-zhipu-self-chip-development:** DeepSeek Ascend stack open-sourced Sep 30; DeepInfer dual hardware ongoing; own inference chip in IPO disclosure — https://github.com/deepseek-ai/DeepInfer
- **alibaba-zhenwu-v900-chip:** T-Head Zhenwu V900; Q1 2027 mass production — no new updates — https://technode.com/2026/09/22/t-head-unveils-zhenwu-v900-ai-chip-in-alibabas-push-to-expand-its-ai-infrastructure-stack/
- **minimax-m31-flash-space-bunny / minimax-h1-2026-agent-dividend:** MiniMax M3.1 Flash API+weights (Oct 19+23); no new updates — https://technode.com/2026/10/23/minimax-releases-open-weights-for-428-billion-parameter-m3-1-flash-model/

---

## Cross-Source Patterns

**Pattern 1: Nvidia scandal as chip-control tipping point (Nov 8-10)** 🌐🇨🇳
- Jensen Huang's affair with alleged Chinese spy crystallized political will for export controls
- Huang was the primary industry voice against export tightening; that voice is now silent
- Senators Banks + Warren, 3 House Republican chairs, FBI, Nvidia board investigation — four simultaneous institutional responses
- Result: Nvidia spy scandal → AI Overwatch Act + RASA + Commerce remote access extension all advanced simultaneously
- Chinese media focused on the Singapore/Megaspeed channel, not on personal scandal
- Platforms: Web (global), Web (China); RFA 普通话 is the definitive Chinese-language analytical source here

**Pattern 2: Chinese open-weight wave complete — all 5 major labs now open** 🌐🇨🇳
- Nov 4-5 triple: Kimi K3.1 Pro (MIT/$20M), Tencent Hy4 (Apache 2.0), Baidu ERNIE 5.5 Flash Base (Baidu license/restrictive)
- Meituan (API-only, open planned), MiniMax (community license), DeepSeek (MIT), GLM-5.3 (MIT), Xiaomi MiMo (MIT), Ant Ling (MIT) — all previously open
- Baidu was the last major holdout; its Nov 5 release completes the cycle
- Pattern: Chinese labs race to establish open-weight presence for global developer mindshare ahead of potential tighter US export controls
- Licensing divergence: Baidu excludes EU/UK/Korea; Moonshot's $20M MaaS clause; others permissive
- Platforms: Web (global), Web (China), Juejin, 新浪科技

**Pattern 3: Five-layer chip access tightening converges in one week** 🌐
- US DHS ban (Oct 20, ongoing)
- China MOFCOM No. 48 (comment closes Nov 15)
- Nvidia 51% non-Chinese customer rule (Nov 4, ongoing)
- Commerce Dept remote access extension (Nov 9, new)
- White House backing AI Overwatch cloud-loophole provision (Nov 9, new)
- Nvidia spy scandal accelerates Congressional votes
- Each layer plugs a loophole exploited by previous layer: physical ban → SE Asia offshore → remote access → cloud loophole → wholesale sanctions
- Net result: Apache 2.0 open weights remain the one regime-exempt pathway for Chinese AI globally

---

## Per-Platform Tables

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US Government removes public access to major Chinese AI model in 2026? | ~21% Yes / ~79% No | ~$105K | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Will Muse Spark 1.4 release by Nov 30? | 38.5% Yes / 61.5% No | — | https://www.lines.com/prediction-markets/tech/ai/next-muse-spark-model-1pt4-released-onptptpt |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | CNBC | https://www.cnbc.com/2026/11/08/nvidia-jensen-huang-investigation-china-spy.html | Nvidia board investigation primary |
| 🌐 | CNBC | https://www.cnbc.com/2026/11/08/jensen-huang-nvidia-china-spy-congress.html | Bipartisan congressional scrutiny |
| 🌐 | CNBC | https://www.cnbc.com/2026/11/10/nvidia-nvda-jensen-huang-affair-chinese-spy.html | Nvidia stock continues falling |
| 🌐 | TechCrunch | https://techcrunch.com/2026/11/09/jensen-huangs-affair-with-alleged-chinese-spy-puts-nvidias-china-ambitions-under-scrutiny/ | China ambitions under scrutiny |
| 🌐 | CNN | https://www.cnn.com/2026/11/08/business/nvidia-investigation-ceo-jensen-huang | CEO admits affair; investigation launched |
| 🌐 | CNN | https://www.cnn.com/2026/11/10/china/nvidia-china-spy-scandal-hnk-intl | Full scandal summary |
| 🌐 | Al Jazeera | https://aljazeera.com/economy/2026/11/10/nvidia-spy-scandal-fuels-debate-over-chip-exports-to-china | Chip export debate analysis |
| 🌐 | Bloomberg | https://www.bloomberg.com/news/articles/2026-11-08/nvidia-board-to-probe-spying-case-after-ceo-jensen-huang-admits-infidelity | Board probe announcement |
| 🌐 | Yahoo Finance | https://finance.yahoo.com/markets/stocks/articles/nvidia-falls-5-board-probes-134356169.html | Stock -5%; AMD +13% |
| 🌐 | WBIW | https://www.wbiw.com/2026/11/10/senators-banks-warren-statement-on-national-security-concerns-surrounding-nvidia/ | Banks-Warren AI Overwatch call |
| 🌐 | NPR | https://www.npr.org/2026/11/08/nx-s1-6034036/nvidia-launches-investigation-into-ceos-alleged-relationship-with-chinese-spy | Neutral reporting |
| 🌐 | Fortune | https://fortune.com/2026/11/09/jensen-huang-nvidia-china-affair-alice-huang-suspected-chinese-spy/ | Huang's prior China-service statements |
| 🌐 | The Star (MY) | https://www.thestar.com.my/news/world/2026/11/10/nvidia-spy-allegations-likely-to-spur-laws-totighten-china039s-access-to-ai-chips | Laws tightening assessment |
| 🌐 | ChinaTechNews | https://www.chinatechnews.com/2026/11/06/132184-in-strategic-reversal-baidu-open-sources-280-billion-parameter-ernie-5-5-ai-model | Baidu ERNIE 5.5 "strategic reversal" |
| 🌐 | The Decoder | https://the-decoder.com/baidu-releases-ernie-5-5-flash-base-with-280-billion-parameters-as-an-open-source-foundation-model/ | Baidu ERNIE 5.5 technical specs |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/11/05/baidu-ernie-5-5-flash-base-280b-moe/ | Official announcement coverage |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/ernie-5-5-flash-base-open-weights-license | ERNIE 5.5 license exclusions detail |
| 🌐 | ExplainX | https://explainx.ai/blog/baidu-ernie-5-5-flash-base-280b-open-weights-moe-14b-active-1m-context-vllm-sglang-2026 | Full ERNIE 5.5 technical breakdown |
| 🌐 | StartupFortune | https://startupfortune.com/baidu-open-sources-ernie-55-flash-base-in-a-race-to-cheap-inference/ | Cheap inference framing |
| 🌐 | FourWeekMBA | https://fourweekmba.com/ai-baidu-opens-ernie-5-5-flash-weights-free-up-to-50m-revenue/ | License terms analysis |
| 🌐 | Pebblous | https://blog.pebblous.ai/blog/baidu-ernie-5-5-license-korea-excluded/en/ | Korea exclusion detail |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/commerce-department-blocks-china-remote-nvidia-access/ | Commerce remote access extension |
| 🌐 | FourWeekMBA | https://fourweekmba.com/ai-white-house-said-to-back-closing-nvidia-chip-remote-access/ | White House AI Overwatch backing |
| 🌐 | HuggingNews | https://huggingnews.com/ai/white-house-weighs-in-on-legislation-to-close-cloud-loophole-for-ai-chip-bea30795 | Cloud loophole legislation details |
| 🌐 | HuggingNews | https://huggingnews.com/us-politics/three-bipartisan-export-bills-target-chinese-cloud-access-to-ai-chips-0e675f79 | Three-bill export control convergence |
| 🌐 | 1049 The Wolf | https://www.1049thewolf.com/2026/11/09/nvidia-spy-allegations-likely-to-spur-laws-to-tighten-chinas-access-to-ai-chips/ | Scandal-to-legislation causal link |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Live leaderboard Nov 7: Kimi #1/74.6 |
| 🌐 | BenchLM blog | https://benchlm.ai/blog/posts/llm-news-november-7-2026 | Nov 7 LLM news roundup |
| 🌐 | QCode | https://qcode.cc/en/qwen-4-release-date | Qwen4 live tracker |
| 🌐 | Shattered.io | https://shattered.io/qwen4-launch-alibaba-open-source-promise-doubt-470-models-2026/ | Alibaba open-source promise doubts |
| 🌐 | FelloAI | https://felloai.com/qwen-4/ | Qwen4 release date tracker |
| 🌐 | AI Tool Lab | https://www.aitoollab.cn/articles/qwen4-teaser-qoduck-preview-2026/ | Qoduck Qoder IDE stealth preview |
| 🌐 | RITS NYU Shanghai | https://rits.shanghai.nyu.edu/ai/qwen-restates-its-open-weight-promise-max-tier-still-closed/ | Max tier staying closed |
| 🌐 | Lyceum | https://lyceum.technology/magazine/deepseek-v4-pro-retires-move-to-v4-1-flash/ | DeepSeek V4 Pro retirement guide |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/deepseek-v4-1-pro-leak | V4.1 Pro partner eval sightings |
| 🌐 | Lines.com | https://www.lines.com/prediction-markets/tech/ai/next-muse-spark-model-1pt4-released-onptptpt | Muse Spark 1.4 prediction market |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/10/15/meta-muse-spark-open-816b-open-weight-model/ | Meta Muse Spark Open (Oct 15) |
| 🌐 | Foreign Affairs Forum | https://www.faf.ae/home/2026/11/10/the-trillion-dollar-bet-capital-chips-and-kilowatts-in-the-new-geography-of-ai-power | "Trillion-Dollar Bet" macro analysis Nov 10 |
| 🌐 | Malaysia Mail | https://www.malaymail.com/news/money/2026/11/10/how-china-gets-the-nvidia-chips-it-needs-to-develop-ai-despite-us-bans/242726 | Chip access loopholes, SE Asia angle |
| 🌐 | China Money Network | https://www.chinamoneynetwork.com/2026/11/10/chinas-ai-ambitions-test-us-curbs-on-nvidia-chips | $1.04T surplus; IC exports +137.1% |
| 🌐 | Baidu (Owler) | https://www.owler.com/reports/baidu--inc./baidu-world-2026-set-for-november-12-in-beijing-un/1791790935974 | Baidu World 2026: Nov 12 Beijing |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/baidu-unveils-apollo-world-model/ | Baidu Apollo World physical AI |
| 🌐 | GlobeNewswire | https://www.globenewswire.com/news-release/2026/11/10/3399162/0/en/zhihe-ai-launches-agent-3-5-local-edition-and-open-sources-70-legal-ai-skills-at-ciie-2026.html | Zhihe AI Agent 3.5 at CIIE 2026 (Nov 10) |
| 🌐 | Baker McKenzie | https://sanctionsnews.bakermckenzie.com/china-proposes-expanded-export-controls-on-ai-biopharma-and-solar-energy-technologies/ | MOFCOM No. 48 authoritative legal analysis |
| 🌐 | The Diplomat | https://thediplomat.com/2026/10/china-wants-its-ai-to-go-global-on-its-own-terms/ | China global AI strategy framing |
| 🌐 | Cellcog | https://cellcog.ai/blog/china-ai-export-controls/ | China AI export controls detail |
| 🌐 | ByteIota | https://byteiota.com/chinas-ai-export-controls-what-deepseek-and-qwen-users-must-know/ | MOFCOM practical user guide |
| 🌐 | Congress.gov | https://www.congress.gov/bill/119th-congress/house-bill/2683 | RASA (H.R. 2683) legislative status |
| 🌐 | Freshfields | https://www.freshfields.com/en/our-thinking/blogs/a-fresh-take/remote-access-or-remote-possibility-rasa-and-the-future-of-cloud-export-controls-102nfbw | RASA legal analysis |
| 🌐 | 24TopNews | https://24topnews.com/news/industry/taiwan-legislature-holds-hearing-on-expanding-advanced-semiconductor-e3b3dd89 | Taiwan semiconductor export controls |
| 🌐 | TrendForce | https://www.trendforce.com/news/2026/11/03/news-china-reportedly-obtains-smuggled-hbm-via-server-packages-huawei-960dt-faces-domestic-hbm-shortage/ | Huawei 960DT HBM smuggling |
| 🇯🇵 | Qiita | https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6 | Chinese open-weight risk survey; enterprise three-layer framework |
| 🇯🇵 | Zenn | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Chinese AI models practical guide for developers |
| 🇯🇵 | Yahoo Japan (CNET JP) | https://news.yahoo.co.jp/articles/f1eafbdd9fa1ab6e4fb0d490e1e8aa8d72500dd0 | China AI export controls Japanese coverage |
| 🇯🇵 | Reuters JP / docomo | https://topics.smt.docomo.ne.jp/article/reuters/world/reuters-20261016114 | MOFCOM 40 technologies export controls |
| 🇯🇵 | Zaikei | https://www.zaikei.co.jp/article/20261020/874182.html | Immediate registration requirement detail |
| 🇯🇵 | Xenospectrum JP | https://xenospectrum.com/china-tech-export-controls-transfer-boundaries/ | API vs weight export distinction |
| 🇯🇵 | PromptQuorum JP | https://www.promptquorum.com/ja/prompt-engineering/geopolitics-and-ai | AI geopolitics US/EU/China analysis (Japanese) |
| 🇯🇵 | AI Teller JP | https://aiteller.jp/blog/ai-kisei-chugoku | Chinese AI regulation overview (Japanese) |
| 🇯🇵 | HungYiChen JP | https://www.hungyichen.com/ja/insights/deepseek-open-source-ai-geopolitics | DeepSeek geopolitics: democratization vs tool (Japanese) |
| 🇨🇳 | 新浪科技 | https://finance.sina.com.cn/tech/roll/2026-11-06/doc-inixuize5487379.shtml | Baidu ERNIE 5.5 open-source coverage |
| 🇨🇳 | 腾讯新闻 | https://news.qq.com/rain/a/20261108A0BQ9400 | Qwen4 Flash benchmark leak; "高光时刻" |
| 🇨🇳 | AI Product Hub | https://aiproducthub.cn/newsflash/alibaba-qwen4-flash-gamefeel-bench-score-beats-claude-opus-5-5/ | Qwen4 Flash 49.9 vs Opus 5.5 47.2 |
| 🇨🇳 | 凤凰网 | https://tech.ifeng.com/c/8xuNurhHW1w | "Qwen4疑似偷跑！" (leaked benchmark) |
| 🇨🇳 | DoNews | https://www.donews.com/news/detail/1/6769732.html | Qwen4 GameFeel Bench coverage |
| 🇨🇳 | 搜狐 | https://www.sohu.com/a/1099598996_121850782 | "极高性价比展现强劲竞争力" (high cost-performance) |
| 🇨🇳 | RFA 普通话 | https://www.rfa.org/mandarin/yataibaodao/2026/11/10/nvidia-jensen-huang-alice-huang-national-security/ | Jensen Huang / 黄乐 investigation analytical report |
| 🇨🇳 | 禁闻网 | https://www.bannedbook.org/bnews/taiwannews/20261110/2379381.html | 英伟达CEO间谍门 Chinese diaspora coverage |
| 🇨🇳 | 东方日报 | https://www.orientaldaily.com.my/news/business/2026/11/10/861807 | Nvidia "7700亿蒸发" market cap loss framing |
| 🇨🇳 | 知乎 | https://zhuanlan.zhihu.com/p/14903006525 | Global AI model release timeline (community) |
| 🇨🇳 | 知乎 | https://zhuanlan.zhihu.com/p/670574382 | Model tracker Nov 6 update |
| 🇨🇳 | 新浪科技 | https://finance.sina.com.cn/tech/roll/2026-11-06/doc-inixvfew8852067.shtml | Qwen4 "北冥有鱼" teaser; 11月发布 |
| 🇨🇳 | 新浪 (Baidu World) | https://finance.sina.com.cn/tech/roll/2026-11-10/doc-iniyfzhy9252567.shtml | Baidu World 2026 Nov 12 preview |
| 🇨🇳 | 掘金 | https://juejin.cn/post/7704578494383046671 | AI日报 Nov 6: Baidu ERNIE 5.5 coverage |
| 🇨🇳 | CSDN | https://blog.csdn.net/m0_60821938/article/details/164328570 | 2026 domestic AI model landscape |
| 🇨🇳 | CSDN | https://hwcomputing.csdn.net/69fdcf72ec97137c96d97aa0.html | Open-source model + domestic chips combo |
| 🇨🇳 | 腾讯新闻 | https://news.qq.com/rain/a/20261002A047VQ | DeepSeek Ascend open-source stack |
| 🇨🇳 | IC.work | https://www.ic.work/article/china-tightens-export-controls-on-open-weight-models-and-23 | MOFCOM No. 48 semiconductor industry analysis |
| 🇨🇳 | BAAI Hub | https://hub.baai.ac.cn/view/37213 | US proposed open-source model export restrictions |

---

## Stats Block

```
├─ 📊 Polymarket: 2 markets │ ~$105K volume
├─ 🌐 Web: 72 pages │ 🇯🇵 9 │ 🇨🇳 17
└─ 🗣️ Top voices: @n_hiraoka (Qiita) │ 腾讯新闻, 新浪科技, 知乎, RFA普通话, 掘金/CSDN
```

---

## Out of Scope but Notable

- **Zhihe AI Agent 3.5 at CIIE 2026 (Nov 10):** Legal AI vertical — 70 proprietary legal skills open-sourced at China's import expo. Not an open-weight frontier model, but represents Chinese domain-specific AI open-sourcing at CIIE 2026. URL: https://www.globenewswire.com/news-release/2026/11/10/3399162/0/en/zhihe-ai-launches-agent-3-5-local-edition-and-open-sources-70-legal-ai-skills-at-ciie-2026.html — possibly fits `enterprise-ai-signals`.

- **China IC exports +137.1% YoY (Oct 2026):** Export controls restricting chip access to China appear to have accelerated Chinese AI hardware supply-chain expansion globally (servers, power equipment, cables) even as advanced chip access is restricted. China's $1.04T trade surplus driven partly by this. Possibly fits `semiconductor-and-infrastructure` or `paradigm-watch`. URL: https://www.chinamoneynetwork.com/2026/11/10/chinas-ai-ambitions-test-us-curbs-on-nvidia-chips

- **Norway grid saturation:** Foreign Affairs Forum notes Norway pausing new data-center connections (26,000 MW applications, triple existing capacity) — energy becoming binding AI constraint before chips in some regions. Possibly fits `paradigm-watch` (energy-not-compute as the actual bottleneck). URL: https://www.faf.ae/home/2026/11/10/the-trillion-dollar-bet-capital-chips-and-kilowatts-in-the-new-geography-of-ai-power

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked (error 90d2) for all Chinese and Japanese queries — same failure mode as Nov 6 run. Fell back to WebSearch with native-language queries; Chinese hub coverage still achieved via 新浪/腾讯/知乎/CSDN/掘金 through WebSearch.
- **Bluesky:** SOURCE HEALTH OK but no Bluesky search performed; gap in open-source AI discourse on that platform.
- **Reddit / X/Twitter:** Excluded per instructions.
- **YouTube:** Not searched.
- **Hacker News:** Not searched this run; last run found K3.1 Pro/Hy4/Ripple-65B at 901 combined points; Nvidia scandal likely trending on HN by now.
- **Zhihu direct fetch:** HTTP 403 on direct Zhihu article fetches; content obtained via WebSearch and third-party summaries.
- **Juejin:** Page returned "Please wait…" loading state on direct fetch.
- **Baidu World 2026 (Nov 12):** Conference in 2 days — may bring post-trained ERNIE 5.5 Flash and new Baidu model announcements; this briefing does not capture that event.
- **GLM-5.4/5.5 and DS V4.1 Pro:** Both confirmed unreleased as of today; monitoring only.
- **Nvidia investigation timing:** Board investigation 4-6 weeks; Congressional testimony hearings begin Nov 18. Situation developing rapidly and briefing is a snapshot as of Nov 10.
- **Coverage estimate:** ~78% — strong model release, geopolitics, and hardware coverage; gaps in social media (Bluesky, HN, X), some Chinese hub direct-fetch failures, and Baidu World event not yet covered.

---

## Key Quotes

> "It is time for Congress to take decisive action to pass key bills like the AI Overwatch Act in the NDAA that will cut off the various pathways through which China accesses advanced chips." — Senators Banks and Warren ([link](https://www.wbiw.com/2026/11/10/senators-banks-warren-statement-on-national-security-concerns-surrounding-nvidia/)) 🌐

> "If his influence is diminished by this investigation, those pushing for tighter restrictions will be in a much stronger position." — Analyst, cited by Al Jazeera on Nvidia spy scandal ([link](https://aljazeera.com/economy/2026/11/10/nvidia-spy-scandal-fuels-debate-over-chip-exports-to-china)) 🌐

> "国产AI迎来高光时刻：千问Qwen4跑分首度超越Opus 5.5，极高性价比展现强劲竞争力" ("Domestic AI reaches a highlight moment: Qwen4 benchmark scores surpass Opus 5.5 for the first time, showing strong cost-performance") — 腾讯新闻/搜狐 ([link](https://news.qq.com/rain/a/20261108A0BQ9400)) 🇨🇳

> "美国对中管制高阶芯片的漏洞在哪里？" ("Where are the loopholes in US high-end chip controls for China?") — RFA 普通话 on the Megaspeed/Singapore-washing channel ([link](https://www.rfa.org/mandarin/yataibaodao/2026/11/10/nvidia-jensen-huang-alice-huang-national-security/)) 🇨🇳

> "Strategic advantage belongs to nations commanding the entire chain — capital, manufacturing, power, security, and governance — not merely those developing the most capable models." — Foreign Affairs Forum ([link](https://www.faf.ae/home/2026/11/10/the-trillion-dollar-bet-capital-chips-and-kilowatts-in-the-new-geography-of-ai-power)) 🌐

> "16个月后重回开源" ("Returning to open-source after 16 months") — 新浪科技 on Baidu ERNIE 5.5 Flash Base release ([link](https://finance.sina.com.cn/tech/roll/2026-11-06/doc-inixuize5487379.shtml)) 🇨🇳

> "The claim that complete security auditing is possible simply because weights are public is not supported by current technology." (「公開ウェイトだから安全性を完全に監査できるという主張は、現状の技術では成立しない」) — @n_hiraoka on Qiita ([link](https://qiita.com/n_hiraoka/items/9ce3d2b6b21101b015f6)) 🇯🇵

> "I was unfaithful to my wife. My actions hurt her and our children." — Jensen Huang, Nvidia CEO, email to staff, Nov 8, 2026 ([link](https://www.cnbc.com/2026/11/08/nvidia-jensen-huang-investigation-china-spy.html)) 🌐
