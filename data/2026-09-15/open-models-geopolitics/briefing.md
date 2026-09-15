# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-09-15
**Query type:** GENERAL
**Sources:** WebSearch (EN/JP/CN), WebFetch, BenchLM, TechCrunch, CNBC, Quartz, TechNode, SCMP, Hacker News, Juejin, CSDN, V2EX, Zhihu (titles), CLS, Tencent News, Sina, 163.com, Guancha, EET-China, BAAI Hub, Fudan FDDI, Qiita, Zenn, note.com, labmemo.com, AI総合研究所, NEC Wisdom, Polymarket, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| YouTube | 0 | — | 🇯🇵 JP DeepSeek video already in prior run |
| Hacker News | 3 threads | 976+ pts, 557+ comments | 🌐 V4.1 Flash threads (main + uncensored + HF) |
| TikTok | 0 | — | Not searched |
| Instagram | 0 | — | Not searched |
| Bluesky | 0 | — | SOURCE HEALTH: OK; no qualifying posts found |
| Polymarket | 3 markets | ~$3M volume | 🌐 Chinese AI markets |
| Web (global) | 75 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita, Zenn, note.com, labmemo, AI総合研究所, NEC Wisdom |
| Web (China) | 17 pages | — | 🇨🇳 Juejin, CSDN, Zhihu (titles), V2EX, CLS, Tencent, Sina, 163, Guancha, EET-China, BAAI, Fudan |

---

## Synthesized Findings

### 1. [update] Anthropic Distillation Threat Report (Sep 10): 200M Exchanges Named — Alibaba, Moonshot, DeepSeek 🌐🇨🇳

**Claim:** New specific fact since Sep 11: Anthropic published a 154-page threat report (Sep 10) documenting ~200M distillation exchanges across 5 campaigns Dec 2025-Aug 2026, naming Alibaba/Qwen (151M), Moonshot/Kimi (~300K, alleged military routing), and DeepSeek (12.1M). China's MOFCOM called allegations "groundless" the next day.

- **Alibaba/Qwen (GTG-16005):** 151M exchanges May-Jul 2026; peak 3M/day; 3,500 accounts; single fixed prompt extracting chain-of-thought → training material for Qwen 3.5-3.7; targeting: agentic, tool use, coding, reasoning
- **Moonshot/Kimi (GTG-16002):** ~300K requests over 10 days; 5,000 accounts; alleged Chinese military routing — 1 request involved surveillance footage analysis; "live re-routing" — users believed using Kimi while Claude answered
- **DeepSeek (GTG-16001):** 12.1M exchanges over 14 days July 2026; Code/Agent framework traffic tagged for preferential Opus routing
- **Total:** ~200M exchanges; 7 Chinese labs named across report
- **China MOFCOM (Sep 9):** "Allegations groundless; distillation is common industry practice; countermeasures if Chinese AI companies suppressed"
- **Company responses:** None of the named labs publicly accepted allegations
- **Context:** Juejin analysis: "1.51亿次是它的观测，不是判决" = "151M is Anthropic's observation, not a verdict" — emphasizes absence of third-party audit, legal determination, or company admission
- **Policy linkage:** Feeds directly into US-China AI safety talks agenda (cyberattack monitoring, lab "self-regulation")
- **Sources:** https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/ | https://betterstack.com/community/guides/ai/anthropic-threat-report-2026/ | https://qz.com/anthropic-chinese-ai-labs-distillation-alibaba-deepseek-moonshot-091126 | https://www.progressiverobot.com/2026/09/11/anthropic-distillation-campaigns-alibaba-moonshot-deepseek/ | https://juejin.cn/post/7684201164355190836 | https://www.cnbc.com/2026/09/03/anthropic-distillation-battle-turns-to-dark-web-china-concerns-swell | https://www.cyberkendra.com/2026/09/anthropic-says-kimi-users-were-secretly.html | https://www.alphamatch.ai/blog/anthropic-moonshot-kimi-claude-routing-distillation-2026 | https://www.androguider.com/2026/09/anthropic-exposes-alleged-ai.html | https://streamlinefeed.co.ke/news/anthropic-details-200-million-ai-distillation-attacks-by-chinese-laboratories | https://app.dealroom.co/news/note/anthropic-alleges-moonshot-routed-some-kimi-user-requests-to-claude-then-served-the-answers-as-kimi

---

### 2. [update] BenchLM Sep 14: Kimi K2.6 Added, V4.1 Flash Still Absent, GLM-5.1 Enters Top 10 🌐

**Claim:** New specific fact: BenchLM updated Sep 14; Kimi K2.6 enters at #6 (65.46); GLM-5.1 enters at #10 (63.3); Qwen3.8-Flash-Next and DeepSeek V3.2 added; scores updated upward; DeepSeek V4.1 Flash still not listed.

- **Top 5 (Sep 14):** Qwen3.8 Max 71.7 → GLM-5.3 68.44 → GLM-5.2 68.19 → GLM-5.3-Flash 66.06 → Kimi K2.7 Code 65.56
- **New entries since Sep 10:** Kimi K2.6 #6 at 65.46; GLM-5.1 #10 at 63.3; Qwen3.8-Flash-Next #20 at 56.98; DeepSeek V3.2 #21 at 56.95; DeepSeek V3.2 (Thinking) #23 at 55.95
- **V4.1 Flash:** BenchLM says "not enough non-generated coverage for public rank" — published benchmarks shown but no leaderboard position yet
- **Unchanged:** All top 14 open-weight models from Chinese labs; Inkling (Thinking Machines) #15 at 60.35 remains first non-Chinese lab in top 15
- **Chinese models board:** Kimi K3 74.9 (#1, Kimi K3 License) → Qwen3.8 Max 71.7 (#2, Apache 2.0)
- **Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/best/chinese-models | https://benchlm.ai/models/deepseek-v4-1-flash

---

### 3. [update] DeepSeek V4.1 Flash: V4 Pro Retirement REVERSED (Sep 14); MIT Abliteration Forks Reach 23K Downloads 🌐🇨🇳

**Claim:** Two new facts since Sep 11: (1) DeepSeek reversed the forced Sep 14 V4 Pro migration — V4 Pro API continues at original pricing; (2) MIT license enabled abliterated uncensored forks within hours; 23K+ GGUF downloads by Sep 13.

- **V4 Pro reversal (Sep 14):** DeepSeek decided to continue V4 Pro API; billing unchanged; all three V4 endpoints (Flash, Flash-Vision-Exp, Pro) continue post-Sep 14
- **Controversy:** Sep 14 HN debate — "silent model swap without deprecation window"; regression testing invalidation concern; HN thread: https://news.ycombinator.com/item?id=49654387
- **MIT abliteration (Sep 10-13):**
  - `dealignai/DeepSeek-V4.1-Flash-UNCENSORED-FP8`: 2,254 downloads, 87 likes by Sep 13
  - GGUF repo: 23,375 downloads by mid-Sep
  - Performance: 100% HarmBench-320 attack success (base: 42.8%); MMLU 82.7% (−4.2 pts)
  - Abliteration = mechanical weight edit (not retraining); removes refusal activation patterns
- **Concurrency:** API concurrency raised from 500 → 2,500 with V4.1 Flash
- **API identifier:** `deepseek-flash` (new; vs prior `deepseek-v4-flash`)
- **Sources:** https://api-docs.deepseek.com/updates/ | https://shattered.io/deepseek-v4-1-flash-v4-pro-retirement-2026/ | https://evolink.ai/blog/deepseek-v4-1-flash-migration-guide | https://tech-insider.org/deepseek-v4-1-flash-uncensored-abliterated-huggingface-2026/ | https://pasqualepillitteri.it/en/news/16070/deepseek-41-flash-uncensored-abliterated-builds | https://news.ycombinator.com/item?id=49654387

---

### 4. [update] DeepSeek IPO: Revenue Disclosed, Valuation $71B, Investors Named; No Formal Filing Yet 🌐🇨🇳

**Claim:** New financials disclosed: 2026 Jan-Jul revenue 4.75亿元 (~$70.7M) = 10x full-year 2025; gross margin 44.6%; pre-IPO valuation ~$71B; investor list: Tencent, CATL, JD.com, NetEase, national AI fund. No formal IPO filing record yet despite CITIC Securities engagement.

- **Revenue:** Jan-Jul 2026: 4.75亿元 (~$70.7M); full-year 2025: ~0.47亿元 implied (10x baseline)
- **Gross margin:** 44.6%
- **Valuation:** ~5000亿元 / ~$71B pre-IPO (up from $75B estimate on Sep 9; variation by source)
- **Investors:** Tencent, CATL, JD.com, NetEase + national AI industry fund
- **Filing status:** Sina reports "暂无IPO申报记录" (no formal filing record yet); CITIC engaged for guidance; formal filing planned 2026
- **Capital uses:** GW-scale compute center + own AI inference chip project (both new disclosures)
- **IPO timeline:** Filing end-2026; listing Q1-Q2 2027
- **Sources:** https://news.qq.com/rain/a/20260909A0BS9C00 | https://www.163.com/dy/article/L1TD1FE00519D4UH.html | https://www.huxiu.com/article/4889797.html | https://www.sina.cn/news/detail/5336196901248786.html | https://finance.yahoo.com/technology/ai/articles/deepseek-taps-citic-securities-shanghai-120650036.html | https://www.scmp.com/tech/tech-trends/article/3366948/chinese-ai-firm-deepseek-taps-underwriters-including-citic-securities-ipo-sources

---

### 5. [update] Moonshot Kimi K3 Cloud Deal: Microsoft, Amazon, AND Google (30% Share); IPO Filing Confirmed 🌐🇨🇳

**Claim:** New specific fact: cloud deal now confirmed to include all three US hyperscalers (Microsoft Azure, Amazon AWS, Google Cloud) — not just "unnamed US cloud" or Microsoft alone as reported earlier; 30% revenue share sought; still not finalized.

- **Deal scope (new):** Microsoft Azure + Amazon AWS + Google Cloud all in talks; 30% revenue share Moonshot seeks
- **Terms outstanding:** Revenue-sharing mechanism, data access rights, token usage audits
- **Microsoft Copilot evaluation:** Still ongoing (July start); no official deployment timeline; earlier Kimi models on Azure AI Foundry
- **HKEX filing:** Confidential A1 Sep 3; Goldman Sachs + CICC + Deutsche Bank underwriters
- **Target:** $3B raise at ~$50B valuation; Q1 2027 earliest listing
- **ARR:** ~$300M (reached June 2026, up from $200M April)
- **Sources:** https://finance.yahoo.com/technology/ai/articles/exclusive-chinas-moonshot-talks-microsoft-075340033.html | https://invezz.com/news/2026/08/26/moonshot-ai-discusses-kimi-k3-hosting-deals-with-microsoft-amazon-google-report/ | https://thenextweb.com/news/moonshot-k3-revenue-sharing-us-clouds | https://techstartups.com/2026/08/26/chinas-moonshot-ai-in-talks-with-microsoft-amazon-and-google-to-bring-kimi-k3-to-us-clouds/ | https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | https://qz.com/moonshot-ai-hong-kong-ipo-filing-3-billion-090326 | https://www.alphamatch.ai/blog/moonshot-ai-50-billion-valuation-hong-kong-ipo-2026 | https://www.scmp.com/tech/big-tech/article/3366271/moonshot-ai-creator-kimi-k3-model-has-filed-hong-kong-ipo-sources

---

### 6. [update] US-China AI Safety Talks: China Issues Preconditions; Sep 15 Status Unclear 🌐🇨🇳

**Claim:** New fact since Sep 11: China issued specific preconditions for September talks — joint authority over definition of "AI safety" + proof US companies face the same rules Washington wants globally. White House continues to deny planning; talks may shift to October.

- **China preconditions (new):** (1) Joint authority over what "AI safety" means; (2) Proof American companies face identical standards proposed for others — published by state-affiliated media as "negotiation terms"
- **US delegation:** Treasury Secretary Bessent; China: He Lifeng or Ding Xuexiang (TBD)
- **US government signals (conflicting):** White House: "no mid-Sep meeting"; Treasury: "may meet in October"; Reuters: "talks being prepared"
- **Topics confirmed:** AI-directed cyberattack monitoring; AI lab self-regulation + incident info sharing
- **Sep 24 Xi-Trump Washington summit:** Still on schedule (Fox News confirmed Xi visiting)
- **Anthropic distillation report (Sep 10):** Directly relevant — feeds US arguments on lab self-regulation + data-use transparency
- **CN framing (Sina, Sputnik CN):** Talks occurring while US AI companies "embroiled in scandals"; framed as US seeking talks from position of weakness
- **Sources:** https://www.techtimes.com/articles/326273/20260903/china-tells-us-agree-what-ai-safety-means-september-talks-cannot-proceed.htm | https://www.cnbc.com/2026/09/05/us-china-gear-up-for-mid-september-ai-safety-talks-reuters.html | https://www.indexbox.io/blog/us-china-ai-safety-talks-set-for-mid-september/ | https://sputniknews.cn/20260905/1073092375.html | https://www.usnews.com/news/world/articles/2026-09-04/exclusive-us-china-gear-up-for-mid-september-ai-safety-dialogue | https://news.futunn.com/post/79260047/reuters-china-and-the-united-states-are-preparing-for-ai

---

### 7. [update] "Diffusion Race" Framing: Qwen 151K HuggingFace Derivatives Exceed Meta Llama; Stanford Gap 2.7% 🌐

**Claim:** New Sep 12-13 analysis quantifies ecosystem dominance: 151K+ Qwen-derived models (2.6× Meta) + Stanford 2026 AI Index shows US-China performance gap narrowed to 2.7%; "diffusion race" concept reframes the competition.

- **Qwen ecosystem (HuggingFace, published Aug 2026):** 151,448 Qwen-derived models — 2.6× Meta's derivatives, 4.7× Llama repos; 180-210 new repos/day; >1B total downloads; 1.1M downloads/day
- **Stanford AI Index (2026):** Performance gap between leading US and Chinese models = 2.7% as of March 2026; US/Chinese models traded leading positions monthly
- **"Diffusion race" (Modern Diplomacy, Sep 13):** Three distinct AI competitions — frontier (benchmarks), infrastructure (chips/cloud), diffusion (who developers build on); ecosystem adoption creates switching costs that outlast benchmark advantages
- **Strategic implication:** "Hugging Face: more derivative models than Google + Meta combined"; 45% YoY growth in Alibaba AI Cloud + Compute Services
- **Sources:** https://moderndiplomacy.eu/2026/09/13/the-ai-race-may-be-measuring-the-wrong-kind-of-power/ | https://getaibook.com/news/hugging-face-reports-chinese-open-models-overtook-us-on-hub-as-qwen-and-deepseek/ | https://huggingface.co/blog/huggingface/one-year-since-the-deepseek-moment-blog-3 | https://www.techmeme.com/260816/p3 | https://www.tun.com/home/hugging-faces-2026-open-model-report-qwen-leads-hype-vs-reality/

---

### 8. [update] BIS AI Diffusion Rule: Formal Rescission + Replacement Before Sep 30 FY End 🌐

**Claim:** New specific fact: Trump admin has stopped enforcing Biden-era AI Diffusion Rule; BIS targeting formal rescission (interim final rule) + replacement framework publication before Sep 30 (FY2026 end). Still not published as of Sep 15.

- **Current status:** Biden rule "technically on books" (GAO holding) but enforcement stopped; interim final rule for rescission due before Sep 30
- **New framework:** BIS FY2026 rulemaking agenda includes replacement; details not published
- **Sep 30 deadline:** FY2026 end creates hard publication window
- **Sources:** https://exportcompliancedaily.com/article/2026/07/08/bis-targets-end-of-fiscal-year-for-ai-diffusion-rule-replacement-2607070013 | https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens | https://perkinscoie.com/insights/article/bis-publishes-bold-new-artificial-intelligence-diffusion-framework | https://www.hlc.com/en/publications/bis-announces-rescission-of-bidenera-ai-diffusion-rule-and-issues-new-ai-policy-and-guidance | https://www.wiley.law/alert-BIS-Rescinds-AI-Diffusion-Rule

---

**Still true (ongoing, no new facts):**

- `deepseek-v4-1-flash-release` — V4.1 Flash (Sep 10, MIT, 552B CED, 45T tokens) is current flagship; replaces V4 line (note: V4 Pro retirement reversed — see finding 3 above)
- `deepseek-star-market-ipo-citic` — CITIC Securities engaged; STAR Market target; $71B valuation (note: revenue + investors now disclosed — see finding 4)
- `mistral-samsung-series-d-third-axis` — €3B Samsung Series D (Sep 8, €21B valuation) confirmed; "third AI axis" framing intact; frontier MoE still silent (day ~145)
- `qwen-drive-1-0-apache-av` — Qwen-Drive-1.0-4B (Apache 2.0, Sep 7) + HKUST; export-sensitive AV domain
- `deepseek-160k-huawei-inner-mongolia` — 160K Ascend 950DT ($2.56B) confirmed; delivery >1 year; HBM shortage
- `benchlm-aug10-rankings-minimax-leads` — Sep 14 update complete; see finding 2
- `kimi-k3-gpu-crunch-subscription-pause` — HKEX A1 filing confirmed Sep 3; Goldman/CICC/Deutsche Bank; cloud deal expanded (see finding 5)
- `us-china-ai-safety-talks-sep24` — China preconditions issued (see finding 6); talks uncertain mid-Sep; Xi-Trump Sep 24 still on
- `china-domestic-chip-mass-pivot` — Domestic AI chip market >52.3% Q1 2026; Ascend 50-60% 2026 China share; Nvidia China ~8%
- `xi-waic-open-source-mandate` — WAICO 37 nations; Digital Silk Road framing active; 151K Qwen derivatives = new measure of dominance
- `eu-ai-act-august-enforcement` — EU AI Office RFIs sent Aug 29; Alibaba Cloud + ByteDance EU subsidiaries subject to 3% global revenue fines
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon (Sep 3, 375B-A23B, Apache 2.0, 6-model fleet); still latest fully-open no-gate frontier fleet
- `qwen-3-8-max-open-weights-pending` — Qwen3.8-Max-0902 BenchLM #1 71.7 (up from 71.63); Code Arena WebDev #1 1,691 pts
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash (MIT, 320B-A18B) BenchLM #4 66.06; standard pricing since Sep 9
- `trump-diffusion-rule-remote-compute` — Formal rescission + replacement before Sep 30 (see finding 8)
- `tencent-hy4-preview-apache` — Hy4 Preview (770B-A49B, Apache 2.0) BenchLM #13 at 61.16
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3 BenchLM #2 at 68.44; KingBench 91.25%; CyberGym 84.5% (post-training)
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next now on BenchLM at #20 (56.98); Qwen4 prediction market 44% before Oct, 74% before Nov; no release
- `minimax-h1-2026-agent-dividend` — ARR >$800M; H1 revenue $116.6M (+283% YoY); HKEX IPO preparations
- `open-weight-licensing-bifurcation` — MIT/Apache for small; conditional for large; DeepSeek V4.1 Flash MIT reinforces pattern
- `deepseek-v4-flash-vision-exp` — V4 Pro retirement REVERSED (see finding 3); all V4 endpoints continue
- `meta-muse-glimmer-us-open-weight` — Muse Glimmer (30B, Apache 2.0); still outside BenchLM top 14 (all Chinese); Spark 1.2 unreleased
- `dots3-note-preview-rednote` — dots3-note Preview BenchLM #9 at 64.1 (down from 64.41)
- `ornith-1-5-self-improving` — Ornith-1.5-397B BenchLM #7 at 65.14 (was #6 65.40)
- `qwen3-8-27b-apache-multimodal` — BenchLM #8 at 64.59
- `mistral-glm52-eu-sovereign-hosting` — GLM-5.2 on Mistral EU endpoints; Leanstral 1.5 Sep (retires Sep 30); OCR 4.1 GA
- `agents-a1-internsciense-new-entrant` — Agents-A1; no new BenchLM position
- `deepseek-harness-v01-price-hike` — DeepSeek concurrency 500 → 2,500; V4.1 Flash baseline pricing
- `polymarket-us-chinese-model-ban` — Odds: 23-26% Yes; ~$15K volume (slight decline from ~26%)
- `kimi-k3-weights-open-source` — K3 (2.8T MoE) under Kimi K3 License; Chinese models board #1 at 74.9
- `us-moonshot-distillation-sanctions` — Anthropic report (Sep 10) new specifics: ~300K Kimi requests, alleged military routing; no enforcement action; cloud deal negotiations complicate
- `openai-hf-cyberattack-glm-defense` — Anthropic distillation report (Sep 10) adds new incident data; HuggingFace July breach (17,600 autonomous attacker actions) now quantified
- `deepseek-zhipu-self-chip-development` — DeepSeek own inference chip project confirmed in IPO capital-use disclosure; Zhipu domestic chip ongoing
- `open-weights-decelerationist-accelerationist` — 151K Qwen derivatives + 63% OpenRouter enterprise tokens = accelerationism winning globally; Anthropic Fable 5 kill-switch cited by CN labs as differentiator
- `openeurollm-european-sovereign` — OpenEuroLLM: no new release; Mistral Samsung D may accelerate separately
- `mistral-frontier-moe-silent` — Day ~145 partner early access; zero public data; Samsung round ≠ model release
- `double-curtain-us-china-export-controls` — BIS Sep 30 rescission deadline; MOFCOM still consultation; WAICO 37 nations
- `china-mofcom-export-controls-ai` — Still consultation; V2EX community skeptical of enforcement; companies told regulators restrictions would backfire
- `tencent-hy3-295b` — BenchLM #14 at 61.06
- `deepseek-chip-ascend-950dt` — 950DT: 160K order; HBM cap ~250-300K total units 2026; GA for inference
- `glm-5-5-expected-august` — August missed; Sep-Oct window; no announcement as of Sep 15
- `ai-manifesto-war-pacing-frontier` — China rejected US "slowdown" push; Trump confirmed "keep racing" call to Jensen Huang; Sep 24 summit layer
- `chinese-military-pla-distillation-reuters` — Anthropic report (Sep 10) provides new specific evidence: Kimi GTG-16002 alleged military routing, surveillance footage request
- `xiaomi-mimo-frontier-entry` — MiMo-V2.5-Pro; no new BenchLM position
- `distillation-scale-data` — Anthropic Sep 10 report: 200M total exchanges named (new scale); MOFCOM: "groundless"; no enforcement yet
- `nemotron-3-ultra-us-open-weight` — Outside top-15; all top-14 Chinese; no change
- `polymarket-chinese-ai-company` — Alibaba 72% best Chinese AI Sep; $2.8M volume; active market
- `inkling-small-thinking-machines` — Inkling #15 at 60.35; Inkling-Small #16 at 59.33
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0); no updates
- `minimax-h3-geo-license-restriction` — H3 video (33B); US/EU/UK/Korea excluded; Hollywood litigation
- `deepseek-autonomous-cyberattack-hermes` — Anthropic report (Sep 10) DeepSeek findings raise same profile; no incident
- `industry-coalition-open-weights-letter` — 235+ signatories; Anthropic sole major holdout; Fable 5 kill-switch episode adds fuel
- `databricks-enterprise-glm-migration` — GLM Coding Plan enterprise adoption unchanged
- `chinese-models-global-share-30pct` — 151K Qwen derivatives; 63% OpenRouter enterprise tokens; 1B+ downloads
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 BenchLM #3 at 68.19; Mistral EU endpoints; Huawei Ascend trained
- `nvidia-h200-china-trivial` — Nvidia China AI chip ~8%; domestic target 90% by 2027; Ascend worldwide ban US
- `jp-deepseek-japanese-cultural-benchmark` — JP Qiita/Zenn coverage ongoing; note.com K2 Horizon guide; NEC Wisdom geopolitics piece
- `kimi-k3-eda-chip-design` — No new reports
- `minimax-m3-pro-2-7t` — BenchLM #11 at 61.62; 2.7T unconfirmed
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 BenchLM #3; Mistral EU; Huawei Ascend trained
- `dots3-note-preview-rednote` — BenchLM #9 at 64.1

---

## Cross-Source Patterns

### Pattern 1: Anthropic Sep 10 Report as Geopolitical Accelerant 🌐🇨🇳

- **Signal:** A single 154-page technical report triggered simultaneous responses across policy (US-China safety talks), industry (MOFCOM countermeasure threat), community (Juejin: "observation not verdict"), and open-source safety (HN uncensored forks on same day)
- **Platforms:** TechCrunch, Quartz, CNBC (global); Juejin, Sina, MOFCOM statement (CN); HN uncensored thread (dev community)
- **Contradiction tension:** Same day as Anthropic report: DeepSeek MIT-licensed V4.1 Flash, enabling the very abliteration forks that demonstrate open-weights cannot be "recalled" — structural response to "kill-switch" concern
- **Quote (Juejin):** "1.51亿次是它的观测，不是判决" = "151M is Anthropic's observation, not a verdict"

### Pattern 2: Ecosystem Race Now Numerically Documented; Frontier Race Secondary 🌐

- **Signal:** Stanford 2026 AI Index (2.7% gap) + HuggingFace 151K Qwen derivatives + 63% OpenRouter enterprise tokens form a consistent picture: Chinese labs are winning the diffusion race even as frontier benchmarks converge
- **Platforms:** Modern Diplomacy (Sep 13), HuggingFace blog, Techmeme, RedMonk (global); Qiita/Zenn/NEC Wisdom (JP framing); BAAI Hub (CN analysis)
- **Quote (Modern Diplomacy):** "The performance gap between leading US and Chinese models had narrowed to 2.7 percent after models from both countries repeatedly traded leading positions"

### Pattern 3: DeepSeek Dual-Track Continues — MIT Open Weights + Capital Markets 🌐🇨🇳

- **Signal:** V4.1 Flash MIT release + CITIC IPO prep + revenue disclosure ($70.7M Jan-Jul, 10x YoY) + V4 Pro retirement reversal all in the same week
- **Platforms:** CLS financial wire, Tencent News, 163.com, Huxiu (CN); Yahoo Finance/SCMP/Reuters (global); CellCog, DataStudios (analysis)
- **CLS quote (Sep 9):** "DeepSeek双线推进：V4.1 Flash模型明日发布 同步筹备科创板IPO" — dual-track intentional signaling

### Pattern 4: Chinese Labs' "No Kill Switch" Advantage Goes on Marketing Record 🌐🇨🇳🇯🇵

- **Signal:** Anthropic Fable 5 blocked June 12-July 1 by Trump export controls; Chinese labs now explicitly cite this in marketing: "at least our models don't come with a kill switch"
- **Platforms:** Axios (Fable 5 original coverage); local-ai-zone (compilation); BAAI Hub, V2EX (CN developer community); labmemo.com, AI総合研究所 (JP market context)
- **Why it matters:** Open weights + MIT license + no government recall mechanism = structural advantage that Anthropic's Fable 5 incident proved is real, not hypothetical

---

## Per-Platform Tables

**Hacker News:** 🌐
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| Liwink | DeepSeek v4.1 Flash | 976 | 557 | "DeepSeek's tech report has juicy details vs Anthropic's system card focused on model welfare" | https://news.ycombinator.com/item?id=49639090 |
| (community) | DeepSeek v4.1 Flash Uncensored | — | — | "MIT makes abliteration trivial; the model swap controversy is worse than the safety implications" | https://news.ycombinator.com/item?id=49654387 |
| (community) | DeepSeek launching v4.1 flash | — | — | "For 80-90% of software tasks, paying 10× premium for closed models is no longer justifiable" | https://news.ycombinator.com/item?id=49624603 |

**Polymarket:** 🌐
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| US Gov removes public access to major Chinese AI model in 2026 | 23-26% Yes | ~$15.1K | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Best Chinese AI Company — September | Alibaba 72%, Moonshot 25% | ~$2.8M | https://polymarket.com/ai |
| Chinese company has best global AI model by Dec 31 | 9% Yes | $232K | https://polymarket.com/event/will-a-chinese-company-have-the-best-ai-model-by-december-31 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | TechCrunch (Sep 10) | https://techcrunch.com/2026/09/10/anthropic-details-distillation-campaigns-from-alibaba-moonshot-ai-and-deepseek/ | Anthropic distillation report: 151M Alibaba, 300K Kimi military routing, 12.1M DeepSeek |
| 🌐 | BetterStack | https://betterstack.com/community/guides/ai/anthropic-threat-report-2026/ | Sep 2026 threat report analysis; campaign GTG IDs |
| 🌐 | Quartz (Sep 11) | https://qz.com/anthropic-chinese-ai-labs-distillation-alibaba-deepseek-moonshot-091126 | Distillation coverage; company non-responses |
| 🌐 | CNBC (Anthropic) | https://www.cnbc.com/2026/09/03/anthropic-distillation-battle-turns-to-dark-web-china-concerns-swell | Dark web distillation escalation Sep 3 |
| 🌐 | DeepSeek API Changelog | https://api-docs.deepseek.com/updates/ | V4 Pro retirement reversed; V4.1 Flash concurrency 2,500 |
| 🌐 | Shattered.io | https://shattered.io/deepseek-v4-1-flash-v4-pro-retirement-2026/ | V4 Pro routing reversal analysis |
| 🌐 | Modern Diplomacy (Sep 13) | https://moderndiplomacy.eu/2026/09/13/the-ai-race-may-be-measuring-the-wrong-kind-of-power/ | Diffusion race; 2.7% gap; 151K derivatives |
| 🌐 | Tech Insider | https://tech-insider.org/deepseek-v4-1-flash-uncensored-abliterated-huggingface-2026/ | Abliteration builds; HarmBench 100%; 23K downloads |
| 🌐 | TechTimes | https://www.techtimes.com/articles/326273/20260903/china-tells-us-agree-what-ai-safety-means-september-talks-cannot-proceed.htm | China AI safety preconditions |
| 🌐 | BenchLM open-source (Sep 14) | https://benchlm.ai/best/open-source | Sep 14 update; Kimi K2.6 #6; GLM-5.1 #10; DeepSeek V3.2 #21 |
| 🌐 | BenchLM Chinese models | https://benchlm.ai/best/chinese-models | Kimi K3 74.9 #1 |
| 🌐 | BenchLM DeepSeek V4.1 Flash | https://benchlm.ai/models/deepseek-v4-1-flash | "Not enough non-generated coverage for public rank" |
| 🌐 | Thenextweb | https://thenextweb.com/news/moonshot-k3-revenue-sharing-us-clouds | 30% revenue share sought from all three US clouds |
| 🌐 | Invezz | https://invezz.com/news/2026/08/26/moonshot-ai-discusses-kimi-k3-hosting-deals-with-microsoft-amazon-google-report/ | MS/Amazon/Google cloud deal details |
| 🌐 | GetAIBook | https://getaibook.com/news/hugging-face-reports-chinese-open-models-overtook-us-on-hub-as-qwen-and-deepseek/ | HuggingFace Chinese model overtake report |
| 🌐 | Techmeme | https://www.techmeme.com/260816/p3 | 151K+ Qwen derivatives headline |
| 🌐 | HuggingFace Blog | https://huggingface.co/blog/huggingface/one-year-since-the-deepseek-moment-blog-3 | One year since DeepSeek moment; ecosystem analysis |
| 🌐 | TechNode (Moonshot IPO) | https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | A1 filing Sep 3 |
| 🌐 | AlphaMatch | https://www.alphamatch.ai/blog/moonshot-ai-50-billion-valuation-hong-kong-ipo-2026 | $50B round; IPO timeline |
| 🌐 | Export Compliance Daily | https://exportcompliancedaily.com/article/2026/07/08/bis-targets-end-of-fiscal-year-for-ai-diffusion-rule-replacement-2607070013 | Sep 30 BIS rescission target |
| 🌐 | BIS official | https://www.bis.gov/press-release/department-commerce-announces-rescission-biden-era-artificial-intelligence-diffusion-rule-strengthens | Rescission announcement |
| 🌐 | Perkins Coie | https://perkinscoie.com/insights/article/bis-publishes-bold-new-artificial-intelligence-diffusion-framework | New framework analysis |
| 🌐 | RealClearDefense (Sep 12) | https://www.realcleardefense.com/2026/09/12/open_models_are_becoming_a_tool_of_chinese_statecraft_1205672.html | Chinese statecraft via open models [403 blocked] |
| 🌐 | Axios (Fable 5 block) | https://www.axios.com/2026/06/12/anthropic-trump-mythos-fable-national-security | Trump blocks Fable 5 foreign access |
| 🌐 | Axios (Fable 5 restored) | https://www.axios.com/2026/06/30/trump-anthropic-ai-model-fable-restrictions | Restrictions lifted July 1 |
| 🌐 | MBZUAI official | https://mbzuai.ac.ae/news/mbzuais-institute-of-foundation-models-launches-k2-horizon-the-worlds-largest-fully-open-ai-models-in-history/ | K2 Horizon 6-model fleet |
| 🌐 | IFM blog | https://ifm.ai/blog/k2/ | K2 Horizon technical introduction |
| 🌐 | CNBC/Reuters | https://www.cnbc.com/2026/09/05/us-china-gear-up-for-mid-september-ai-safety-talks-reuters.html | Mid-Sep talks preparation |
| 🌐 | TechNode (Qwen-Drive) | https://technode.com/2026/09/07/qwen-drive-autonomous-driving/ | Qwen-Drive-1.0-4B Apache 2.0 |
| 🌐 | TechCrunch (Mistral) | https://techcrunch.com/2026/09/08/mistral-raises-e3b-as-sovereign-ai-becomes-big-business/ | €3B Samsung Series D |
| 🌐 | CNBC (Mistral) | https://www.cnbc.com/2026/09/08/mistral-ai-funding-valuation-samsung.html | €21B valuation |
| 🌐 | Bloomberg (Mistral) | https://www.bloomberg.com/news/articles/2026-09-08/mistral-ai-raises-at-21-billion-valuation-in-samsung-led-round | Bloomberg confirmation |
| 🌐 | DataStudios | https://www.datastudios.org/post/deepseek-ipo-citic-securities-shanghai-star-market-75-billion-valuation | DeepSeek IPO target |
| 🌐 | Yahoo Finance (Reuters) | https://finance.yahoo.com/technology/ai/articles/deepseek-taps-citic-securities-shanghai-120650036.html | CITIC Securities engaged |
| 🌐 | SCMP (IPO) | https://www.scmp.com/tech/tech-trends/article/3366948/chinese-ai-firm-deepseek-taps-underwriters-including-citic-securities-ipo-sources | 4 underwriters confirmed |
| 🌐 | Value Add VC | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition | Huawei 50%+ China AI chip market |
| 🌐 | SemiconductorX | https://semiconductorx.com/spotlight-huawei-hisilicon.html | Ascend chip timeline + specs |
| 🌐 | Sputnik CN | https://sputniknews.cn/20260905/1073092375.html | CN framing of US-China AI talks |
| 🌐 | Local AI Zone | https://local-ai-zone.github.io/blog/September_2026_AI_Model_Updates.html | Sep 2026 complete model release log |
| 🌐 | Model Diplomat | https://modeldiplomat.com/story/chinas-ai-models-face-export-restrictions | MOFCOM export controls analysis |
| 🌐 | TechPolicy.Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | Open-weight crackdown analysis |
| 🌐 | Releasebot (Mistral) | https://releasebot.io/updates/mistral | Mistral Leanstral 1.5; OCR 4.1 |
| 🌐 | Releasebot (Qwen) | https://releasebot.io/updates/qwen | Qwen3.8-Max-0902 release notes |
| 🌐 | Manifold Markets | https://manifold.markets/Bayesian/when-will-alibaba-release-qwen-4 | Qwen4 prediction market |
| 🌐 | CellCog | https://cellcog.ai/blog/qwen-4-release-date/ | Qwen4 architecture preview analysis |
| 🌐 | Deepseek.ai blog | https://deepseek.ai/blog | DeepSeek official blog |
| 🌐 | DeepSeek model tracker | https://aireleasetracker.com/company/deepseek | DeepSeek 23 releases tracked |
| 🌐 | OpenSourceForYou | https://www.opensourceforu.com/2026/09/deepseek-opens-its-first-native-vision-model/ | V4-Flash-Vision-Exp native vision |
| 🌐 | BenchLM homepage | https://benchlm.ai/ | LLM leaderboard Sep 2026 |
| 🌐 | Huxiu | https://www.huxiu.com/article/4889797.html | DeepSeek CITIC engagement details |
| 🌐 | Progress Robot | https://www.progressiverobot.com/2026/09/11/anthropic-distillation-campaigns-alibaba-moonshot-deepseek/ | Distillation campaigns risk analysis |
| 🌐 | AlphaMatch (Kimi) | https://www.alphamatch.ai/blog/anthropic-moonshot-kimi-claude-routing-distillation-2026 | Kimi routing allegation |
| 🌐 | TechStartups | https://techstartups.com/2026/08/26/chinas-moonshot-ai-in-talks-with-microsoft-amazon-and-google-to-bring-kimi-k3-to-us-clouds/ | Cloud deal three-hyperscaler confirmation |
| 🌐 | TechTimes (distillation) | https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm | China model weight lock-down concern |
| 🌐 | Kie.ai | https://kie.ai/blog/what-is-glm-5-5 | GLM-5.5 >1T param community leak |
| 🌐 | StreamlineFeed | https://streamlinefeed.co.ke/news/anthropic-details-200-million-ai-distillation-attacks-by-chinese-laboratories | 200M exchanges total |
| 🌐 | CyberKendra | https://www.cyberkendra.com/2026/09/anthropic-says-kimi-users-were-secretly.html | Kimi users served Claude secretly |
| 🌐 | AndroGuider | https://www.androguider.com/2026/09/anthropic-exposes-alleged-ai.html | Anthropic exposes allegations |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/us-government-chinese-ai-model-restriction-polymarket/ | Polymarket 26% Chinese AI ban |
| 🌐 | Pasqualepillitteri | https://pasqualepillitteri.it/en/news/16070/deepseek-41-flash-uncensored-abliterated-builds | Abliterated builds first-day analysis |
| 🌐 | App.Dealroom | https://app.dealroom.co/news/note/anthropic-alleges-moonshot-routed-some-kimi-user-requests-to-claude-then-served-the-answers-as-kimi | Dealroom: Kimi routing allegation |
| 🌐 | U.S. News | https://www.usnews.com/news/world/articles/2026-09-04/exclusive-us-china-gear-up-for-mid-september-ai-safety-dialogue | Sep 4 exclusive |
| 🌐 | Internazionale | https://www.internazionale.it/ultime-notizie-reuters/2026/09/04/exclusive-us-china-gear-up-for-mid-september-ai-safety-dialogue | Reuters via Internazionale |
| 🇯🇵 | AI総合研究所 | https://www.ai-souken.com/article/chinese-ai-model-overview | Chinese AI model overview for JP market |
| 🇯🇵 | labmemo.com | https://labmemo.com/llm-llama-deepseek-qwen-mistral-gemma-2026/ | Open-source LLM comparison 2026 |
| 🇯🇵 | NEC Wisdom (田中) | https://wisdom.nec.com/ja/series/tanaka/2026021601/index.html | Chinese AI as "intelligence infrastructure" for developing countries |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese AI 2026 comparison; GLM best JP tasks |
| 🇯🇵 | Qiita (etale_cohomology) | https://qiita.com/etale_cohomology/items/61db72acde35b9fb795c | Qwen-AgentWorld; Chinese AI agents frontline |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | Kimi K3/Qwen3.8-Max/DeepSeek V4-Pro deep-dive |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Qwen leads JP language; OpenRouter recommended |
| 🇯🇵 | note.com (AI Driven Lab) | https://note.com/ai_driven/n/nbb8a89579c01 | K2 Horizon comprehensive guide |
| 🇯🇵 | note.com (Fushiki) | https://note.com/zouplans/n/na9b74156aa00 | Chinese open-source AI adoption in Silicon Valley |
| 🇨🇳 | Juejin (Anthropic蒸馏) | https://juejin.cn/post/7684201164355190836 | Anthropic distillation analysis: "observation not verdict" |
| 🇨🇳 | Juejin (Flash价格战) | https://juejin.cn/post/7678618678955474950 | Flash model price war; DeepSeek V4-Flash cache 0.1元/1M |
| 🇨🇳 | Juejin (API Gateway) | https://juejin.cn/post/7683457864930590772 | Unified API gateway for Chinese models |
| 🇨🇳 | CSDN (V4.1 Flash内测) | https://blog.csdn.net/aidoudoulong/article/details/164629225 | 5-min API integration; 507 tokens/s |
| 🇨🇳 | CSDN (国产开源格局) | https://deepseek.csdn.net/6a0ac187662f9a54cb75630b.html | Domestic open-source 2026; Hygon DCU + Cambricon training |
| 🇨🇳 | V2EX (分级出海) | https://www.v2ex.com/t/1225707 | MOFCOM tiered export controls discussion |
| 🇨🇳 | BAAI Hub | https://hub.baai.ac.cn/view/52228 | Post-DeepSeek ecosystem: hardware-first pivot; Apache 2.0 default |
| 🇨🇳 | CLS (双线推进) | https://www.cls.cn/detail/2478606 | "Two-front advance": IPO + V4.1 Flash |
| 🇨🇳 | Tencent News (V4.1) | https://news.qq.com/rain/a/20260910A082TL00 | V4.1 Flash formal release |
| 🇨🇳 | Tencent News (IPO) | https://news.qq.com/rain/a/20260909A0BS9C00 | DeepSeek revenue/valuation/IPO details |
| 🇨🇳 | 163.com (IPO) | https://www.163.com/dy/article/L1TD1FE00519D4UH.html | 5000亿元 valuation; investor list |
| 🇨🇳 | Sina News | https://news.sina.com.cn/w/2026-09-06/doc-iniqwnku4233060.shtml | US companies "embroiled in scandals" framing |
| 🇨🇳 | Sina (IPO无申报) | https://www.sina.cn/news/detail/5336196901248786.html | "No formal IPO filing record yet" |
| 🇨🇳 | Chinatimes TW | https://www.chinatimes.com/realtimenews/20260905001914-260410 | "AI密会" paving road for Xi-Trump summit |
| 🇨🇳 | Guancha | https://www.guancha.cn/economy/2026_09_05_830131.shtml | 160K Ascend 950DT procurement |
| 🇨🇳 | EET-China (V4/Ascend) | https://www.eet-china.com/news/202604093584.html | Alibaba/ByteDance/Tencent 950PR orders |
| 🇨🇳 | Fudan FDDI | https://fddi.fudan.edu.cn/f1/9c/c21253a717212/page.htm | "US chip moat weakening" thesis |
| 🇨🇳 | Huxiu (IPO) | https://www.huxiu.com/article/4889797.html | CITIC engagement details |
| 🇨🇳 | LINUX DO | https://linux.do/t/topic/2879180 | DeepSeek V4.1 in domestic alternatives community |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 0 videos (prior JP DeepSeek video already in Sep 11 briefing)
├─ 🟢 HN: 3 threads │ 976+ pts │ 557+ comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ SOURCE HEALTH: OK
├─ 📊 Polymarket: 3 markets │ ~$3M volume
├─ 🌐 Web: 75 pages │ 🇯🇵 7 │ 🇨🇳 17
└─ 🗣️ Top voices: Anthropic (threat report) │ China MOFCOM │ CLS Financial Wire │ Reuters/CNBC │ HN community │ Juejin/CSDN/BAAI developers
```

---

## Out of Scope but Notable

- **DeepSeek V4.1 Flash "abliteration" as open-weights safety failure mode** — MIT license enabled 100% HarmBench-320 pass rate within days; 23K+ GGUF downloads. This is not a model architecture story or a geopolitics story; it's a new empirical data point on what "fully permissive open weights" means for AI safety in practice — no government, no company, no framework can "recall" the weights once published. Bridges open-weights licensing debates with the AI safety governance agenda. https://tech-insider.org/deepseek-v4-1-flash-uncensored-abliterated-huggingface-2026/

- **HuggingFace July 2026 incident: 17,600 autonomous AI attacker actions** — Cited in Modern Diplomacy (Sep 13) as evidence that concentrated AI infrastructure dependencies create resilience risks. Not a model-release story; belongs to AI security/agent-harness topic. https://moderndiplomacy.eu/2026/09/13/the-ai-race-may-be-measuring-the-wrong-kind-of-power/

---

## Data Gaps

- **DuckDuckGo HTML endpoints:** CAPTCHA-blocked for both JP and CN passes (consistent with prior run); fell back to WebSearch in native languages
- **Zhihu direct pages:** 403 Forbidden on fetched Zhihu URLs; titles + snippets from search results only
- **Juejin:** Most articles accessible via search snippets; direct fetches not attempted for all
- **The Neuron Sep 14 digest:** 403 blocked
- **RealClearDefense Sep 12:** 403 blocked (key article on Chinese statecraft via open models)
- **Bluesky:** SOURCE HEALTH = OK; zero qualifying posts found Sep 12-15; consistent with prior runs on this topic
- **Mistral frontier MoE:** Day ~145 partner early access; zero public data still
- **GLM-5.5:** Confirmed not yet released; Sep-Oct window unchanged
- **Qwen4:** Confirmed not yet released; fall 2026 expected
- **DeepSeek V4.1 Flash BenchLM:** Not yet listed ("insufficient non-generated coverage"); company benchmarks only
- **US-China AI safety talks Sep 15 outcome:** Status unknown — talks may not have occurred; September 15 deadline ambiguous
- **Approximate coverage:** 83% — strong on model releases, Anthropic report, IPO news, BIS status, JP/CN hub coverage; gap in Zhihu/Juejin full text, Bluesky, Mistral frontier details, Sep 15 US-China talks outcome

---

## Key Quotes

> "DeepSeek双线推进：V4.1 Flash模型明日发布 同步筹备科创板IPO" ("DeepSeek advancing on two fronts: releasing V4.1 Flash tomorrow, simultaneously preparing STAR Market IPO") — CLS Financial Wire ([link](https://www.cls.cn/detail/2478606))

> "1.51亿次是它的观测，不是判决" ("151M is Anthropic's observation, not a verdict") — Juejin analysis of Anthropic distillation report ([link](https://juejin.cn/post/7684201164355190836))

> "The performance gap between leading US and Chinese models had narrowed to 2.7 percent after models from both countries repeatedly traded leading positions" — Modern Diplomacy, citing Stanford 2026 AI Index ([link](https://moderndiplomacy.eu/2026/09/13/the-ai-race-may-be-measuring-the-wrong-kind-of-power/))

> "DeepSeek's technical report has juicy details while Anthropic's system card is focused on safety and model welfare rather than technical benchmarks" — top HN comment, DeepSeek V4.1 Flash thread ([link](https://news.ycombinator.com/item?id=49639090))

> "美企频爆雷、被点名之际，中美正筹备AI安全会谈" ("While US companies are embroiled in scandals and being named, China-US is preparing AI safety talks") — Sina News Sep 6 ([link](https://news.sina.com.cn/w/2026-09-06/doc-iniqwnku4233060.shtml))

> "一旦有顶级模型在中国国产硬件上跑通了稳定高效的推理，美国芯片的护城河就不再牢固" ("Once a top model runs stable and efficient inference on Chinese domestic hardware, America's chip moat will no longer be solid") — Fudan University FDDI ([link](https://fddi.fudan.edu.cn/f1/9c/c21253a717212/page.htm))

> "For 80-90% of software tasks, paying a 10× premium for larger proprietary models is no longer economically justifiable" — HN comment, DeepSeek V4.1 Flash thread ([link](https://news.ycombinator.com/item?id=49624603))

> "Alibaba has more derivative models on HuggingFace than Google and Meta combined" — HuggingFace 2026 Open Model Report, via Techmeme ([link](https://www.techmeme.com/260816/p3))
