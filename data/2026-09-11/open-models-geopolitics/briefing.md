# Open-Source Models & AI Geopolitics — Daily Briefing
**Date:** 2026-09-11
**Query type:** GENERAL
**Sources:** WebSearch, WebFetch, BenchLM, TechNode, CNBC/Reuters, TechCrunch, Bloomberg, SCMP, CLS.cn, Tencent News, Sina News, Zhihu (titles), CSDN, Juejin (titles), Hacker News, GIGAZINE (🇯🇵), note.com (🇯🇵), Zenn (🇯🇵), Yahoo Japan (🇯🇵), Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 | — | Excluded per scope |
| X/Twitter | 0 | — | Excluded per scope |
| YouTube | 1 video | — | 🇯🇵 Japanese "breaking news" DeepSeek V4.1 |
| Hacker News | 1 story | 976 pts, 557 comments | 🌐 DeepSeek V4.1 Flash top thread |
| TikTok | 0 | — | Not searched |
| Instagram | 0 | — | Not searched |
| Bluesky | 0 | — | SOURCE HEALTH: OK; no qualifying posts found |
| Polymarket | 3 markets | ~$2.8M volume | 🌐 Chinese AI company odds; best model Sep 2026 |
| Web (global) | 58 pages | — | 🌐 via WebSearch + WebFetch; news, specs, analysis |
| Web (Japan) | 9 pages | — | 🇯🇵 GIGAZINE, note.com, NOVAIST, Zenn, Yahoo Japan (Chuo Ilbo), tek.jp, mihata.jp, aiagent-navi.com, YouTube |
| Web (China) | 14 pages | — | 🇨🇳 CLS, Tencent News (×2), 163.com, Sina, Zhihu (titles, 403 on pages), Juejin (title, JS-blocked), CSDN, Baidu Baike, LINUX DO, MeetCoding, Fudan FDDI, 21jingji, Chinatimes(TW) |

---

## Synthesized Findings

### 1. [new] DeepSeek V4.1 Flash (Sep 10): MIT Open Weights, "Causal Encoder-Decoder," 45T-Token Training 🌐🇨🇳🇯🇵

**Claim:** DeepSeek released V4.1 Flash on September 10 — MIT-licensed, native multimodal, 552B MoE with a new "Causal Encoder-Decoder" architecture trained from scratch on 45T tokens; replaces V4 Pro; HN trending at 976 pts / 557 comments.

- **Architecture:** 552B total, 8B active/input + 16B active/output (asymmetric); new Causal Encoder-Decoder (20-layer encoder → 20-layer decoder)
- **Efficiency:** KV cache 1/4 HBM, 1/8 SSD vs prior generation; FP4 compression + Compressed Sparse Attention; 890 bytes/token KV
- **Multimodal:** Native vision encoder trained alongside language model (vs V4-Flash-Vision-Exp where vision was add-on plugin)
- **Context:** 1M tokens; max output 384K tokens; Thinking + Non-thinking modes
- **Open weights:** MIT license; Hugging Face `deepseek-ai/DeepSeek-V4.1-Flash`; 48 safetensors shards; no gate
- **Pricing (Sep 10):** $0.003/M cached input, $0.15/M uncached, $0.60/M output (off-peak); peak = 2× — vs V4 Pro: −77% uncached input, −60% cached, −11% output
- **Throughput:** 420–507 tokens/second measured
- **V4 Pro retirement:** Sep 14 traffic rerouted to V4.1 Flash at V4.1 pricing
- **Performance claims:** Beats V4 Pro on all metrics; GPQA Diamond 90.9; Codeforces 3471; AutomationBench-AA top score (beats GPT-6 Astra); Artificial Analysis v4.3 score 40 (exceeds GPT-5.6 Luna)
- **HN community (976 pts):** DeepSeek's technical report praised for "juicy details" vs Anthropic's safety/welfare-focused cards; debate on Chinese AI technical transparency vs Western labs; distillation allegations contested
- **JP coverage:** GIGAZINE, note.com, NOVAIST, AIエージェントナビ, mihata.jp all published Sep 10-11; "安い！早い！" (cheap! fast!) YouTube headline
- **CN framing:** CLS "双线推进" (two-front advance: V4.1 Flash + STAR Market IPO simultaneously); Tencent News: "small-cost, big-intelligence asymmetric architecture"
- **Medium analysis:** "Should be called V5" — argued the naming downplays scope of architectural change
- **Sources:** https://deepseek.com/en/news/deepseek-v4-1-flash/ | https://cellcog.ai/blog/deepseek-v4-1-flash-release-date/ | https://news.ycombinator.com/item?id=49639090 | https://datanorth.ai/news/deepseek-releases-deepseek-v4-1-flash | https://ccleaks.com/news/deepseek-v4-1-flash-open-weights-sep-2026 | https://theroboticsmedia.com/article/deepseek-v4-1-flash-1m-context-fp4-kv-cache-cross-layer-attention-mit-open-weights-september-10-2026 | https://api-docs.deepseek.com/updates/ | https://gigazine.net/news/20260911-deepseek-v4-1-flash/ | https://note.com/cool_bee1567/n/n38286d0ef8fe | https://novaist.jp/articles/deepseek-v4-1-flash-release/ | https://aiagent-navi.com/news/deepseek-v4-1-flash-release/ | https://news.qq.com/rain/a/20260910A082TL00 | https://www.cls.cn/detail/2478606 | https://blog.csdn.net/aidoudoulong/article/details/164629225 | https://juejin.cn/post/7683375934588289075 | https://www.youtube.com/watch?v=ahBwug46Y1g

---

### 2. [new] DeepSeek Hires CITIC for Shanghai STAR Market IPO; Pre-IPO Valuation $75B 🌐🇨🇳

**Claim:** DeepSeek engaged CITIC Securities (+ three others) for a Shanghai STAR Market IPO, simultaneously with the V4.1 Flash launch; pre-IPO financing round targets ~500B yuan ($75B) valuation; filing possible end-2026, public debut 2027.

- **Underwriter:** CITIC Securities lead; four total underwriters (others not named)
- **Market:** Shanghai STAR Market (科创板), China's Nasdaq-equivalent
- **Valuation target:** ~500B yuan / $74–75B pre-money; prior round June 2026: $7.4B at $50B+
- **Timeline:** Filing possible end 2026; fastest public debut Q2 2027
- **Capital purpose:** Computing infrastructure, model development, talent retention; Liang Wenfeng: "IPO enables compensation structure to retain key engineers"
- **Comparative scale:** Still far below US peers (Anthropic expected $2T, OpenAI targeting $1T)
- **Data sovereignty angle (TechTimes):** China's Data Law will follow every user wherever shares trade — IPO cements PRC legal jurisdiction over DeepSeek's entire business
- **CLS framing:** "双线推进" — V4.1 Flash release + IPO prep are synchronized deliberate signaling
- **Liang commitment:** Open-source and AGI goals maintained through IPO process
- **Sources:** https://finance.yahoo.com/technology/ai/articles/deepseek-taps-citic-securities-shanghai-120650036.html | https://www.datastudios.org/post/deepseek-ipo-citic-securities-shanghai-star-market-75-billion-valuation | https://www.scmp.com/tech/tech-trends/article/3366948/chinese-ai-firm-deepseek-taps-underwriters-including-citic-securities-ipo-sources | https://www.techtimes.com/articles/327106/20260909/deepseek-ipo-milestone-chinas-data-law-follows-every-api-query.htm | https://www.business-standard.com/world-news/china-s-deepseek-taps-citic-securities-for-domestic-ipo-126090901726_1.html | https://qz.com/deepseek-ipo-citic-securities-shanghai-star-market-090926 | https://en.sedaily.com/international/2026/09/09/deepseek-taps-citic-for-star-market-listing-this-year | https://www.cls.cn/detail/2478606

---

### 3. [new] Mistral Samsung-Led €3B Series D: "Third Way in AI," €21B Valuation, Semiconductor Co-Model 🌐🇯🇵

**Claim:** Mistral raised €3B in a Samsung-led Series D (Sep 8), achieving €21B valuation and the largest equity raise in European tech history; Samsung + Mistral to co-develop on-premises AI model for wafer fab operations; Macron and JP media frame it as a Korea-Europe "third axis" vs US-China AI bipolar.

- **Round:** €3B ($3.5B) Series D, announced Sep 8, 2026
- **Valuation:** €21B ($24.4B) post-money
- **Lead:** Samsung Electronics (new investor), signed at Korea-France Paris summit Sep 8
- **Co-leads:** EQT-managed EU Scaleup Europe Fund; PSG Equity (existing)
- **Others:** a16z, Nvidia, Salesforce Ventures, Advent, BlackRock, Luxembourg sovereign fund
- **Record:** Largest equity fundraise ever by a European tech company
- **Samsung collaboration:** Co-develop semiconductor AI model for Samsung DS division; applications: wafer defect detection, equipment optimization, process parameter matching, production data analysis; all data stays within Samsung infrastructure (no external transfer)
- **Macron framing:** France + South Korea "building a third way in AI" — sovereign alternative to US and China
- **JP/KR framing (Yahoo Japan / Chuo Ilbo):** "韓国と欧州が「第3のAI軸」を模索" = "Korea and Europe seeking a 'third AI axis'" as US-China bipolar solidifies
- **Funds use:** Scale compute, build infrastructure, accelerate commercial growth, expand international
- **Frontier MoE:** Still no public data; day ~130+ in partner early access; this funding event ≠ model release
- **Sources:** https://techcrunch.com/2026/09/08/mistral-raises-e3b-as-sovereign-ai-becomes-big-business/ | https://www.cnbc.com/2026/09/08/mistral-ai-funding-valuation-samsung.html | https://www.bloomberg.com/news/articles/2026-09-08/mistral-ai-raises-at-21-billion-valuation-in-samsung-led-round | https://qz.com/mistral-ai-samsung-series-d-funding-valuation-090826 | https://www.itpro.com/security/samsung-backs-mistral-in-record-breaking-eur3-billion-funding-round-as-french-ai-firm-targets-sovereign-ai-gains | https://kingy.ai/news/samsung-mistral-ai-3-billion-funding-round/ | https://news.yahoo.co.jp/articles/2a944c6afad4c55e205516a78fc598fd063720bf | https://xenospectrum.com/mistral-series-d-samsung-sovereign-ai/ | https://easternherald.com/2026/09/09/mistral-ai-samsung-series-d-european-tech-record/ | https://news.qq.com/rain/a/20260910A0BH2S00

---

### 4. [new] Qwen-Drive-1.0-4B: Apache 2.0 Autonomous Driving VLM with HKUST 🌐🇨🇳

**Claim:** Alibaba's Qwen team released Qwen-Drive-1.0-4B (Sep 7), the first VLM foundation model unifying 3D perception and motion planning without modifying the VLM base, co-developed with HKUST under Apache 2.0.

- **Model:** 4B params, built on Qwen3.5-4B VLM base (base model completely unchanged — "底座一个字没改")
- **Architecture:** External BEV perception head for 3D detection + semantic occupancy + BEV map segmentation; two planning branches: behavioral cloning + RL-optimized; joint 3D perception + visual QA pretraining
- **License:** Apache 2.0 (code, weights, demo data)
- **Collaboration:** Alibaba Qwen + Huazhong University of Science and Technology (华中科技大学)
- **Technical novelty:** First to unify 3D perception + VQA pretraining + motion planning while leaving VLM base untouched
- **Geopolitical angle:** Open-source autonomous driving foundation from Chinese lab; available globally under permissive license; extends Qwen's "infrastructure default" play into autonomous vehicle AI
- **Sources:** https://technode.com/2026/09/07/qwen-drive-autonomous-driving/ | https://aiweekly.co/alerts/alibaba-ships-qwen-drive-10-4b-for-self-driving-under-apache-20 | https://huggingface.co/Qwen/Qwen-Drive-1.0-4B | https://github.com/QwenLM/Qwen-Drive-1.0 | https://arxiv.org/pdf/2609.00111 | https://pandaily.com/alibaba-qwen-drive-1-0-4b-open-source-autonomous-driving-perception-and-planning | https://meetcoding.cn/lm/qwen-drive/introduction.html

---

### 5. [update] US-China AI Safety Pre-Talks: Mid-September Talks Planned, Topics Confirmed 🌐

**Claim:** Reuters Sep 5 confirms mid-September US-China AI safety dialogue being prepared — first formal bilateral AI meeting under Trump; US agenda adds AI-directed cyberattack monitoring and AI lab "self-regulation" to the agenda; White House denied planning while Treasury said "may meet in October."

- **New fact:** Reuters Sep 5 revealed mid-September talks being prepared — more specific than the vague "pre-talks active" known on Sep 8
- **US delegation:** Treasury Secretary Bessent
- **China delegation:** Possibly He Lifeng (Bessent's protocol counterpart, VP) or Ding Xuexiang (#7 official); TBD
- **Topics (new detail):** (1) Cooperate on monitoring AI-directed cyberattacks; (2) AI lab self-regulation framework — US + Chinese labs "police themselves" and share AI cyber incident information
- **Ambiguity:** White House: "no planned AI-related meeting in mid-September"; US Treasury: "may meet in October"; Reuters: location undetermined
- **Context:** CN Sina (Sep 6): "美企频爆雷、被点名之际" = talks happening as US AI companies embroiled in scandals — OpenAI rogue agent (Germany, May 2026), HuggingFace breach (July 2026) cited
- **TW Chinatimes:** "为习川会铺路！AI密会" = "paving road for Xi-Trump summit; AI secret meeting"
- **Sep 24 summit:** Still on schedule; Fox News confirmed Xi in Washington Sep 24
- **Expected outcome:** Analysts say "handful of toothless risk management clauses" most likely; US won't compromise on export controls; China wants restrictions on US frontier models and end to Chinese open-weight model bans
- **Sources:** https://www.cnbc.com/2026/09/05/us-china-gear-up-for-mid-september-ai-safety-talks-reuters.html | https://www.japantimes.co.jp/business/2026/09/05/tech/us-china-ai-safety-talks/ | https://news.bloomberglaw.com/artificial-intelligence/us-china-plan-ai-safety-dialogue-in-mid-september-reuters-says | https://thenextweb.com/news/us-china-ai-talks-cyberattacks-trump-xi-summit-september | https://news.sina.com.cn/w/2026-09-06/doc-iniqwnku4233060.shtml | https://www.chinatimes.com/realtimenews/20260905001914-260410 | https://foreignpolicy.com/2026/09/08/us-china-ai-negotiations-safety-governance-trump-xi-summit/ | https://www.foxnews.com/politics/trump-says-chinese-president-xi-jinping-visit-us-sept-24

---

### 6. [update] Moonshot HKEX IPO: $3B Target, Goldman/CICC/Deutsche Bank, Onshore Domicile 🌐🇨🇳

**Claim:** Moonshot AI's HKEX confidential filing (Sep 3) targets $3B raise at $50B valuation, underwritten by Goldman Sachs, CICC, Deutsche Bank; required onshore China domicile conversion; Kimi K3 ARR ~$300M; cloud deal still not finalized but Microsoft began evaluating K3 for Copilot.

- **New fact since Sep 8:** $3B raise target, Goldman Sachs/CICC/Deutsche Bank named as underwriters; onshore China domicile conversion required before filing
- **Filing:** Confidential; LatePost first reported Sep 3; HKEX process
- **Raise target:** $3B; valuation ~$50B
- **Underwriters:** Goldman Sachs, CICC, Deutsche Bank
- **Structural change:** Had to unwind offshore incorporation structure → onshore China domicile
- **ARR:** ~$300M driven by Kimi K3
- **Microsoft evaluation (July, no confirmation):** Testing Kimi K3 for some Copilot inference functions; industry estimates: $600M/yr inference cost savings; earlier Kimi models already on Azure AI Foundry; no official deployment timeline
- **Cloud deal (30% revenue share):** Still no finalization as of Sep 11; outstanding: revenue split, data access, token usage auditing
- **Sources:** https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | https://qz.com/moonshot-ai-hong-kong-ipo-filing-3-billion-090326 | https://ground.news/article/moonshot-ai-eyes-hong-kong-ipo-within-six-months-as-kimi-k3-drives-300m-revenue-run-rate | https://en.sedaily.com/international/2026/09/05/moonshot-ai-files-confidentially-for-hong-kong-ipo-seeks-3 | https://technode.com/2026/07/23/microsoft-reportedly-evaluates-moonshot-ais-kimi-k3-for-copilot/

---

### 7. [update] BenchLM Sep 10: Leaderboard Stable, 103 Models 🌐

**Claim:** BenchLM updated Sep 10 with no material ranking changes from Sep 8; Qwen3.8 Max holds #1 at 71.63; 103 models listed (was 104 Sep 8); Kimi K3 leads separate Chinese models board at 74.8.

- **New fact:** Leaderboard now 103 models (was 104 Sep 8, minor churn)
- **Open-weight top-5 (Sep 10):** Qwen3.8 Max 71.63 → GLM-5.3 68.37 → GLM-5.2 68.12 → GLM-5.3-Flash 65.99 → Kimi K2.7 Code 65.49
- **New additions in leaderboard (Sep 10):** Inkling-Small #16 at 59.25; GLM-4.7 #17 at 57.71; GLM-5 (Reasoning) #18 at 57.43; Qwen3.5 397B (Reasoning) #19; DeepSeek V3.2 #20 at 56.88
- **Chinese models board (all-Chinese, open + closed):** Kimi K3 74.8 (#1, Kimi K3 License) → Qwen3.8 Max 71.6 (#2 open) → GLM-5.3 68.4 → GLM-5.2 68.1 → Qwen3.7 Max 67.1
- **Absent:** DeepSeek V4.1 Flash not yet listed (same-day Sep 10 release; leaderboard update typically takes 1-2 days)
- **Still true:** All top 14 open-weight models from Chinese labs; Inkling (Thinking Machines) remains first non-Chinese model in top 15 at 60.28
- **Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/best/chinese-models

---

**Still true (ongoing, no new facts):**

- `deepseek-160k-huawei-inner-mongolia` — 160K Ascend 950DT order ($2.56B) confirmed; delivery >1 year due to HBM shortage; inference-only; site Ulanqab Inner Mongolia
- `china-domestic-chip-mass-pivot` — Domestic AI chip market >52.3% Q1 2026; DeepSeek V4 on Ascend 950PR (CANN); ByteDance/Tencent/Alibaba competing for Huawei chips
- `xi-waic-open-source-mandate` — WAICO at 37 nations; Lawfare "Digital Silk Road" framing; 63% OpenRouter enterprise tokens from Chinese models (Aug 2026)
- `eu-ai-act-august-enforcement` — EU AI Office RFIs sent Aug 29; Alibaba Cloud + ByteDance EU subsidiaries subject to 3% global revenue fines
- `mbzuai-k2-horizon-open-fleet` — K2 Horizon (Sep 3, 375B-A23B, Apache 2.0, 6 models); UAE sovereign AI play; still latest fully-open frontier fleet
- `kimi-k3-weights-open-source` — Kimi K3 (2.8T MoE) weights: Kimi K3 License (>$20M rev must negotiate); cloud deal still unfinalized
- `us-moonshot-distillation-sanctions` — No enforcement; cloud negotiations complicate sanctions narrative
- `glm-5-3-post-training-emergent-cyber` — GLM-5.3 weights (744B-A40B); KingBench 91.25%; BenchLM #2 at 68.37
- `qwen-3-8-max-open-weights-pending` — Qwen3.8-Max-0902 still BenchLM #1; Code Arena WebDev #1 1,691 pts
- `glm-5-3-flash-ox-alpha-domestic-chip` — GLM-5.3-Flash (MIT, 320B-A18B); 50% promo through Sep 9; standard pricing resumes now
- `polymarket-chinese-ai-august` — Sep markets: Alibaba 72% best Chinese; Moonshot 25%; $2.8M volume
- `tencent-hy4-preview-apache` — Hy4 preview (770B-A49B, Apache 2.0): BenchLM #13 at 61.08
- `glm-5-5-expected-august` — August missed; Sep-Oct window; no Zhipu announcement as of Sep 11
- `deepseek-v4-flash-vision-exp` — V4-Flash and V4-Flash-Vision-Exp continue until Sep 14, then traffic migrates to V4.1 Flash; V4.1 Flash replaces the whole V4 line
- `trump-diffusion-rule-remote-compute` — BIS new framework due by Sep 30 (FY2026 end); still not published; GAO holding: AI Diffusion Rule technically still on books
- `deepseek-chip-ascend-950dt` — 950DT GA; 160K order in progress; HBM memory cap limits 2026 production to hundreds of thousands total
- `open-weight-licensing-bifurcation` — Enclosure turn holds: MIT/Apache for small/flash models; conditional for powerful models
- `open-weights-decelerationist-accelerationist` — 63% OpenRouter enterprise tokens Chinese models (Aug); a16z 80% VC portfolio using Chinese open-source
- `openeurollm-european-sovereign` — First year progress: MixtureVitae dataset; no flagship; compute challenges persist
- `mistral-frontier-moe-silent` — Day ~130 partner early access; zero public data; Samsung funding ≠ model release
- `double-curtain-us-china-export-controls` — MOFCOM controls still consultation; US BIS Sep 30 deadline; Lawfare "Digital Silk Road" + WAICO third dimension
- `china-mofcom-export-controls-ai` — Three-tier framework still consultation; no finalization Sep 8-11
- `ai-manifesto-war-pacing-frontier` — WAICO 37 nations = fourth governance bloc; Sep 24 summit adds bilateral layer
- `qwen3-8-27b-apache-multimodal` — BenchLM #8 at 64.52
- `ornith-1-5-self-improving` — BenchLM #6 at 65.40
- `dots3-note-preview-rednote` — BenchLM #9 at 64.41
- `meta-muse-glimmer-us-open-weight` — Muse Glimmer (30B, Apache 2.0); Spark 1.2 still not released
- `minimax-h1-2026-agent-dividend` — ARR >$800M; H1 revenue $116.6M (+283% YoY)
- `deepseek-harness-v01-price-hike` — DeepSeek Harness 144K+ stars; V4.1 Flash pricing supersedes prior structure
- `openai-hf-cyberattack-glm-defense` — No new reports
- `deepseek-zhipu-self-chip-development` — DeepSeek own inference chip (early stage); V4 on Ascend; Zhipu domestic chip inference ongoing
- `kimi-k3-eda-chip-design` — No new reports
- `minimax-m3-pro-2-7t` — MiniMax M3 BenchLM #11 at 61.55; 2.7T unconfirmed
- `tencent-hy3-295b` — Hy3 BenchLM #14 at 60.98
- `distillation-scale-data` — No enforcement; cloud negotiations complicate sanctions narrative
- `nemotron-3-ultra-us-open-weight` — Outside top-15; Chinese models dominant
- `inkling-small-thinking-machines` — Inkling #15 at 60.28; Inkling-Small #16 at 59.25 [new addition]
- `mistral-shieldstral-safety-classifier` — Shieldstral (3B, Apache 2.0); no updates
- `minimax-h3-geo-license-restriction` — H3 video (33B); US/EU/UK/Korea excluded; Hollywood litigation ongoing
- `deepseek-autonomous-cyberattack-hermes` — No new reports
- `industry-coalition-open-weights-letter` — 235+ signatories; Anthropic still sole major holdout
- `databricks-enterprise-glm-migration` — GLM Coding Plan on GLM-5.3; enterprise adoption unchanged
- `chinese-models-global-share-30pct` — 63% OpenRouter enterprise tokens; a16z 80%; Qwen approaching 1B downloads
- `glm-5-2-benchmarks-huawei-trained` — GLM-5.2 on Mistral EU endpoints; BenchLM #3 at 68.12
- `nvidia-h200-china-trivial` — Nvidia ~8% China AI chip share; domestic target 90% high-end; US Ascend worldwide ban in effect
- `polymarket-us-chinese-model-ban` — ~26% Yes "US removes public access to major Chinese AI model in 2026"; $15.1K volume
- `polymarket-chinese-ai-company` — Sep active: Alibaba 72%; market active; $2.8M volume
- `chinese-military-pla-distillation-reuters` — No new reports
- `xiaomi-mimo-frontier-entry` — MiMo-V2.5-Pro: no new BenchLM position
- `mistral-glm52-eu-sovereign-hosting` — GLM-5.2 on Mistral EU endpoints; Leanstral 1.5 released Sep; OCR 4.1 GA Aug 30
- `agents-a1-internsciense-new-entrant` — Agents-A1; no new BenchLM position
- `jp-deepseek-japanese-cultural-benchmark` — JP coverage expanded Sep 11: GIGAZINE, note.com, NOVAIST on V4.1 Flash; Zenn June article on practical Chinese AI (Qwen best JP language)
- `qwen3-8-flash-next-qwen4-preview` — Qwen3.8-Flash-Next architecture preview of Qwen4; no Qwen4 release yet; prediction market 44% before October, 74% before November

---

## Cross-Source Patterns

### Pattern 1: DeepSeek Executes Dual-Track Strategy — Open-Source Leadership + Public Markets 🌐🇨🇳

- **Signal:** V4.1 Flash (MIT, beats V4 Pro on all metrics) + CITIC Securities STAR Market IPO preparation announced the same week
- **Platforms:** CLS financial wire, Reuters/SCMP (IPO); HN, TechNode, CSDN, Juejin, Zhihu, GIGAZINE, note.com (V4.1 Flash)
- **Significance:** Open-source credibility (MIT, 45T tokens, full HF weights) serves as marketing asset ahead of IPO; IPO provides capital for the 160K Ascend 950DT cluster; the two moves are mutually reinforcing
- **Quote (CLS):** "DeepSeek双线推进：V4.1 Flash模型明日发布 同步筹备科创板IPO" = "DeepSeek advancing on two fronts: releasing V4.1 Flash tomorrow, simultaneously preparing STAR Market IPO" — https://www.cls.cn/detail/2478606

### Pattern 2: "Third Axis" Crystallizes — Samsung-Mistral vs US-China AI Bipolar 🌐🇯🇵

- **Signal:** Samsung (Korea) leads €3B Mistral (France/EU) round; Macron + Samsung executives both frame as "third way" vs US-China
- **Platforms:** TechCrunch, Bloomberg, CNBC (global); Yahoo Japan/Chuo Ilbo (JP framing); Tencent News (CN framing)
- **Convergence:** JP media says "third AI axis"; CN media focuses on semiconductor manufacturing AI; Western media focuses on sovereign AI demand
- **Why it matters:** Korea and EU are the two largest US ally markets with the most to lose from US-China AI bifurcation; Samsung-Mistral partnership signals that chipmakers + AI labs outside US-China are willing to pool resources for sovereignty

### Pattern 3: US-China AI Safety Talks Approach with Conflicting Signals 🌐🇨🇳

- **Signal:** Reuters confirms mid-September talks being prepared; simultaneously White House denies planning them; Treasury says "may be October"
- **Platforms:** CNBC/Reuters, Bloomberg Law, Japan Times, Sina News (CN), Chinatimes (TW)
- **CN angle (Sina):** Talks happening while US AI companies embroiled in scandals — framed as US needing talks from position of weakness, not strength
- **Key ambiguity:** Three different US government messages (White House: no; Treasury: maybe October; Reuters sources: yes mid-September); actual date undetermined as of Sep 11

### Pattern 4: Open-Source as Autonomous Driving Infrastructure — Qwen-Drive Extends "Default Infrastructure" Play 🌐🇨🇳

- **Signal:** Qwen-Drive-1.0 (Apache 2.0) is now a foundation model for autonomous vehicles; Alibaba is applying open-source-as-default strategy to a new vertical
- **Platforms:** TechNode, AI Weekly, Pandaily, MeetCoding (CN)
- **Pattern:** Same playbook as language model open-sourcing — release permissive-licensed model to become the default foundation the ecosystem builds on (training data funnel → Alibaba Cloud dependency)
- **Geopolitical significance:** Autonomous driving AI is export-control-sensitive; Apache 2.0 release sidesteps restrictions while embedding Chinese AI in global AV research

---

## Per-Platform Tables

**Hacker News:** 🌐
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| Liwink | DeepSeek v4.1 Flash | 976 | 557 | "DeepSeek's tech report has juicy details vs Anthropic's system card focused on model welfare" — top comment | https://news.ycombinator.com/item?id=49639090 |

**Polymarket:** 🌐
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company — September | Alibaba 72%, Moonshot 25% | ~$2.8M | https://polymarket.com/predictions/ai-technology |
| Chinese company has best global AI model by Dec 31 | 9% Yes | $232K | https://polymarket.com/event/will-a-chinese-company-have-the-best-ai-model-by-december-31 |
| US Government removes public access to major Chinese AI model in 2026 | ~26% Yes | $15.1K | https://polymarket.com/predictions/ai-technology |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | DeepSeek official (Sep 10) | https://deepseek.com/en/news/deepseek-v4-1-flash/ | V4.1 Flash announcement; specs; MIT weights |
| 🌐 | TechNode (Sep 9) | https://technode.com/2026/09/09/deepseek-v4-1-flash-multimodal-limited-beta/ | Beta timeline; DeepSeek framing as "not formal release" at beta stage |
| 🌐 | CellCog (Sep 10) | https://cellcog.ai/blog/deepseek-v4-1-flash-release-date/ | 552B Causal Encoder-Decoder; 20-layer arch; FP4 KV cache; formal release confirmed |
| 🌐 | CCLeaks | https://ccleaks.com/news/deepseek-v4-1-flash-open-weights-sep-2026 | HuggingFace weights confirmed; 48 safetensors; MIT |
| 🌐 | The Robotics Media | https://theroboticsmedia.com/article/deepseek-v4-1-flash-1m-context-fp4-kv-cache-cross-layer-attention-mit-open-weights-september-10-2026 | FP4, Cross-Layer Attention specs |
| 🌐 | Yotta Labs | https://www.yottalabs.ai/post/deepseek-v4-1-flash-pricing-specs-v4-pro-routing-2026 | V4 Pro routing timeline |
| 🌐 | DataNorth | https://datanorth.ai/news/deepseek-releases-deepseek-v4-1-flash | Pricing confirmed; $0.15/M uncached |
| 🌐 | DeepSeek API docs | https://api-docs.deepseek.com/updates/ | Official changelog Sep 10 entry |
| 🌐 | DEV.to (Sep 10) | https://dev.to/ryan_zhao/deepseek-v41-flash-the-native-multimodal-model-thats-breaking-speed-records-1ged | 420 tokens/sec; native multimodal |
| 🌐 | Medium (Andrew Zhu) | https://xhinker.medium.com/deepseek-v4-1-flash-it-should-be-called-v5-open-source-and-beat-opus-5-0-d73fc8656c5b | "Should be called V5" framing |
| 🌐 | CLS.cn (Sep 9) | https://www.cls.cn/detail/2478606 | "双线推进" IPO + V4.1 Flash |
| 🌐 | DataStudios (IPO) | https://www.datastudios.org/post/deepseek-ipo-citic-securities-shanghai-star-market-75-billion-valuation | $75B pre-IPO valuation target |
| 🌐 | Yahoo Finance (Reuters) | https://finance.yahoo.com/technology/ai/articles/deepseek-taps-citic-securities-shanghai-120650036.html | Reuters exclusive: CITIC Securities engaged |
| 🌐 | SCMP (IPO) | https://www.scmp.com/tech/tech-trends/article/3366948/chinese-ai-firm-deepseek-taps-underwriters-including-citic-securities-ipo-sources | SCMP confirms 4 underwriters |
| 🌐 | TechTimes (IPO) | https://www.techtimes.com/articles/327106/20260909/deepseek-ipo-milestone-chinas-data-law-follows-every-api-query.htm | China Data Law sovereignty angle |
| 🌐 | Business Standard | https://www.business-standard.com/world-news/china-s-deepseek-taps-citic-securities-for-domestic-ipo-126090901726_1.html | IPO confirmation |
| 🌐 | TechCrunch (Mistral) | https://techcrunch.com/2026/09/08/mistral-raises-e3b-as-sovereign-ai-becomes-big-business/ | €3B, sovereign AI big business |
| 🌐 | CNBC (Mistral) | https://www.cnbc.com/2026/09/08/mistral-ai-funding-valuation-samsung.html | €21B valuation; full investor list |
| 🌐 | Bloomberg (Mistral) | https://www.bloomberg.com/news/articles/2026-09-08/mistral-ai-raises-at-21-billion-valuation-in-samsung-led-round | Bloomberg confirmation |
| 🌐 | Quartz (Mistral) | https://qz.com/mistral-ai-samsung-series-d-funding-valuation-090826 | Series D details |
| 🌐 | IT Pro (Mistral) | https://www.itpro.com/security/samsung-backs-mistral-in-record-breaking-eur3-billion-funding-round-as-french-ai-firm-targets-sovereign-ai-gains | Largest European equity raise |
| 🌐 | SamMobile | https://www.sammobile.com/news/samsung-invests-mistral-ai-startup-improve-chips | Samsung to improve chips with Mistral |
| 🌐 | Eastern Herald | https://easternherald.com/2026/09/09/mistral-ai-samsung-series-d-european-tech-record/ | European tech record confirmed |
| 🌐 | Kingy AI | https://kingy.ai/news/samsung-mistral-ai-3-billion-funding-round/ | Samsung partnership details |
| 🌐 | TechNode (Qwen-Drive) | https://technode.com/2026/09/07/qwen-drive-autonomous-driving/ | Qwen-Drive-1.0-4B Apache 2.0 release |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/alibaba-ships-qwen-drive-10-4b-for-self-driving-under-apache-20 | Self-driving Apache 2.0 shipped |
| 🌐 | GitHub (Qwen-Drive) | https://github.com/QwenLM/Qwen-Drive-1.0 | Code + weights; Apache 2.0 |
| 🌐 | HuggingFace (Qwen-Drive) | https://huggingface.co/Qwen/Qwen-Drive-1.0-4B | Model weights |
| 🌐 | ArXiv | https://arxiv.org/pdf/2609.00111 | Technical report Sep 2026 |
| 🌐 | Pandaily | https://pandaily.com/alibaba-qwen-drive-1-0-4b-open-source-autonomous-driving-perception-and-planning | Specs overview |
| 🌐 | CNBC/Reuters (talks Sep 5) | https://www.cnbc.com/2026/09/05/us-china-gear-up-for-mid-september-ai-safety-talks-reuters.html | Mid-Sep AI safety talks; Bessent leads |
| 🌐 | Japan Times | https://www.japantimes.co.jp/business/2026/09/05/tech/us-china-ai-safety-talks/ | First official bilateral AI dialogue under Trump |
| 🌐 | Bloomberg Law | https://news.bloomberglaw.com/artificial-intelligence/us-china-plan-ai-safety-dialogue-in-mid-september-reuters-says | Bloomberg law confirmation |
| 🌐 | The Next Web | https://thenextweb.com/news/us-china-ai-talks-cyberattacks-trump-xi-summit-september | Cyberattack monitoring + self-regulation topics |
| 🌐 | Progressive Robot | https://www.progressiverobot.com/2026/09/07/us-china-ai-safety-talks-mid-september/ | Essential facts on US-China AI safety risk |
| 🌐 | Foreign Policy (Sep 8) | https://foreignpolicy.com/2026/09/08/us-china-ai-negotiations-safety-governance-trump-xi-summit/ | "Can cooperate without grand bargain" |
| 🌐 | Fox News | https://www.foxnews.com/politics/trump-says-chinese-president-xi-jinping-visit-us-sept-24 | Xi visit September 24 confirmed |
| 🌐 | TechNode (Moonshot IPO) | https://technode.com/2026/09/03/moonshot-ai-reportedly-submits-confidential-hong-kong-ipo-filing/ | HKEX confidential filing Sep 3 |
| 🌐 | Quartz (Moonshot IPO) | https://qz.com/moonshot-ai-hong-kong-ipo-filing-3-billion-090326 | $3B / $50B target |
| 🌐 | Ground.news | https://ground.news/article/moonshot-ai-eyes-hong-kong-ipo-within-six-months-as-kimi-k3-drives-300m-revenue-run-rate | ARR $300M; IPO within 6 months |
| 🌐 | Seoul Economic Daily | https://en.sedaily.com/international/2026/09/05/moonshot-ai-files-confidentially-for-hong-kong-ipo-seeks-3 | $3B at ~$50B target |
| 🌐 | BenchLM open-source (Sep 10) | https://benchlm.ai/best/open-source | 103 models; Qwen3.8 Max #1 71.63 |
| 🌐 | BenchLM Chinese (Sep 10) | https://benchlm.ai/best/chinese-models | Kimi K3 74.8 all-Chinese #1 |
| 🌐 | Sakana AI (OOS) | https://sakana.ai/fugu-max-release/ | Fugu Max + Ultra v2 Sep 11; multi-agent; 74.3 DeepSWE |
| 🌐 | RAND | https://www.rand.org/pubs/perspectives/PEA4686-1.html | Open Models, Soft Power, US-China spectrum |
| 🌐 | USCC Two Loops | https://www.uscc.gov/sites/default/files/2026-03/Two_Loops--How_Chinas_Open_AI_Strategy_Reinforces_Its_Industrial_Dominance.pdf | China open AI strategy reinforces industrial dominance |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | 63% OpenRouter tokens; China problem revisited |
| 🌐 | Rest of World | https://restofworld.org/2026/ai-divide-america-china-world/ | AI divide: America, China, world |
| 🌐 | One Lex Partners | https://www.onelexpartners.com/news-and-insights/us-export-controls-and-ai-a-practitioners-guide | US AI export controls 2026 guide; FY2026 deadline |
| 🌐 | WilmerHale | https://www.wilmerhale.com/en/insights/client-alerts/20250515-us-export-controls-on-ai-diffusion-officially-paused-but-new-guidance-elevates-risk-for-ai-related-exports | AI diffusion rule paused but legally on books |
| 🌐 | Releasebot Mistral | https://releasebot.io/updates/mistral | Leanstral 1.5 Sep; OCR 4.1 GA Aug 30; frontier MoE still silent |
| 🌐 | Qiita (@TaichiEndoh) | https://qiita.com/TaichiEndoh/items/1a5c829e8568a16ea834 | Risk framework for engineers adopting Chinese AI |
| 🌐 | Qiita (@tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | GLM-5 best for Japanese tasks; 2026 comparison |
| 🌐 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900 | Infrastructure dominance thesis |
| 🌐 | Qiita (@sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | Kimi K3 / Qwen3.8-Max / DeepSeek V4-Pro deep-dive |
| 🌐 | RedMonk (Sep 3) | https://redmonk.com/sogrady/2026/09/03/open-weight-models/ | 63% OpenRouter enterprise tokens from Chinese models |
| 🌐 | Lawfare | https://www.lawfaremedia.org/article/open-weight-diplomacy--how-china-s-ai-models-are-rerunning-the-digital-silk-road | "Digital Silk Road" open-weight framing |
| 🇯🇵 | GIGAZINE (Sep 11) | https://gigazine.net/news/20260911-deepseek-v4-1-flash/ | "Surpasses Claude Opus 5 and GPT-5.6 Sol" — Japanese coverage |
| 🇯🇵 | note.com KintoNavi (Sep 11) | https://note.com/cool_bee1567/n/n38286d0ef8fe | "77% cheaper than V4 Pro; V4 Pro retires Sep 14" |
| 🇯🇵 | NOVAIST (Sep 10) | https://novaist.jp/articles/deepseek-v4-1-flash-release/ | 552B MoE; API price cut |
| 🇯🇵 | AIエージェントナビ | https://aiagent-navi.com/news/deepseek-v4-1-flash-release/ | V4.1 Flash announcement; V4 Pro Sep 14 retirement |
| 🇯🇵 | mihata.jp | https://mihata.jp/column/deepseek-v4-1-flash | DeepSeek V4.1 Flash pricing + Pro cutover |
| 🇯🇵 | Yahoo Japan (Chuo Ilbo) | https://news.yahoo.co.jp/articles/2a944c6afad4c55e205516a78fc598fd063720bf | Samsung-Mistral "third AI axis" framing |
| 🇯🇵 | XenoSpectrum Japan | https://xenospectrum.com/mistral-series-d-samsung-sovereign-ai/ | "On-premises sovereign AI for semiconductor manufacturing" |
| 🇯🇵 | Zenn (kent_kamome, Jun) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Qwen leads Japanese; OpenRouter recommended; task-specific developer usage patterns |
| 🇯🇵 | YouTube JP | https://www.youtube.com/watch?v=ahBwug46Y1g | "安い！早い！GPT5.6-Solに比肩！" |
| 🇯🇵 | labmemo.com | https://labmemo.com/llm-llama-deepseek-qwen-mistral-gemma-2026/ | Open-source LLM comparison 2026 |
| 🇨🇳 | CLS Financial Wire | https://www.cls.cn/detail/2478606 | "双线推进" DeepSeek IPO + V4.1 Flash |
| 🇨🇳 | Tencent News (Sep 10, V4.1) | https://news.qq.com/rain/a/20260910A082TL00 | V4.1 Flash formal release; performance claims |
| 🇨🇳 | Tencent News (Sep 10, Samsung) | https://news.qq.com/rain/a/20260910A0BH2S00 | Samsung-Mistral semiconductor AI partnership |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/L6CGBSHV05568W0A.html | Samsung-Mistral strategic partnership |
| 🇨🇳 | Sina News (Sep 6) | https://news.sina.com.cn/w/2026-09-06/doc-iniqwnku4233060.shtml | US AI company scandals + AI safety talks context |
| 🇨🇳 | Chinatimes TW | https://www.chinatimes.com/realtimenews/20260905001914-260410 | "AI密会" framing for Xi-Trump pre-talks |
| 🇨🇳 | CSDN (beta) | https://blog.csdn.net/aidoudoulong/article/details/164629225 | V4.1 Flash beta "5-minute integration" |
| 🇨🇳 | Juejin (Sep 8) | https://juejin.cn/post/7683375934588289075 | V4.1 Flash API integration guide; 507 tokens/s max |
| 🇨🇳 | LINUX DO | https://linux.do/t/topic/2879180 | V4.1 Flash in "domestic alternatives" community |
| 🇨🇳 | Baidu Baike | https://baike.baidu.com/item/DeepSeek-V4.1/67766548 | DeepSeek V4.1 encyclopedia entry |
| 🇨🇳 | MeetCoding | https://meetcoding.cn/lm/qwen-drive/introduction.html | Qwen-Drive "base model completely unchanged" framing |
| 🇨🇳 | Fudan FDDI | https://fddi.fudan.edu.cn/f1/9c/c21253a717212/page.htm | "Closed loop from chip to model; US chip moat weakening" |
| 🇨🇳 | Zhihu (Sep 11) | https://www.zhihu.com/question/2081380378493961583 | DeepSeek V4.1 Flash evaluation (403 on page, title from search) |
| 🇨🇳 | Zhihu (Sep 11) | https://zhuanlan.zhihu.com/p/2080959870170296494 | "Textbook-style intermediate version release" analysis |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per scope)
├─ 🔵 X: 0 posts (excluded per scope)
├─ 🔴 YouTube: 1 video │ 🇯🇵 Japanese DeepSeek V4.1 Flash coverage
├─ 🟢 HN: 1 story │ 976 points │ 557 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (SOURCE HEALTH: OK; no qualifying posts)
├─ 📊 Polymarket: 3 markets │ ~$3M volume
├─ 🌐 Web: 58 pages │ 🇯🇵 9 │ 🇨🇳 14
└─ 🗣️ Top voices: Liang Wenfeng (DeepSeek) │ Macron (Mistral framing) │ Liwink @HN │ Bloomberg │ Reuters/CNBC │ CLS Financial Wire
```

---

## Out of Scope but Notable

- **Sakana AI Fugu Max + Fugu Ultra v2 (Sep 11)** — Japan-based AI lab releases multi-agent orchestration system scoring 48.3 on Chartography (vs Fable 5's 29.5) and 74.3 on DeepSWE. Not a foundation model but a router/orchestrator — raises the question of whether orchestration layers over open weights can outperform proprietary frontier models on agentic tasks at lower cost. If so, it's a new capability tier that doesn't map to existing model rankings. Belongs to agent-harness topic but the open-weight ecosystem dependency is highly relevant here. https://sakana.ai/fugu-max-release/

- **DeepSeek "should be called V5" consensus** — Multiple analysts note that V4.1 Flash's architectural scope (new Causal Encoder-Decoder trained from scratch on 45T tokens, replacing the entire V4 line) is semantically a new generation, not an incremental "flash" update. If naming convention systematically understates capability jumps from Chinese labs, benchmarking and comparative analysis are being distorted by nomenclature. https://xhinker.medium.com/deepseek-v4-1-flash-it-should-be-called-v5-open-source-and-beat-opus-5-0-d73fc8656c5b

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN passes; fell back to WebSearch with language-specific queries. Some hub coverage (Zenn Sep 11 posts, Juejin Sep 11, Aliyun Developer) underrepresented.
- **Zhihu direct pages:** 403 Forbidden on all three fetched Zhihu article URLs. Titles and excerpts obtained from search results; full text unavailable.
- **Juejin direct pages:** JavaScript-rendered "Please wait..." screen — content not fetchable.
- **Bluesky:** SOURCE HEALTH = OK; zero qualifying open-models/geopolitics posts found Sep 9-11. Consistent with prior runs — topic produces minimal Bluesky signal.
- **Mistral frontier MoE:** Day ~130 in partner early access; zero public performance data.
- **GLM-5.5:** Confirmed no release; Sep-Oct 2026 window remains.
- **DeepSeek V5:** Confirmed no formal release; V4.1 Flash is the new flagship.
- **BIS new framework:** Due Sep 30 (FY2026 end); not yet published as of Sep 11.
- **DeepSeek V4.1 Flash benchmarks:** Company claims beat V4 Pro on all metrics, beats Opus 5 and GPT-5.6 Sol on some benchmarks. No independent third-party BenchLM score yet (same-day release). Treat performance claims as preliminary until independent benchmark scores appear.
- **Approximate coverage:** 84% — strong on model releases, IPO news, geopolitics, JP/CN hub coverage; gap in Zhihu/Juejin full text, Bluesky, and live BenchLM score for V4.1 Flash.

---

## Key Quotes

> "DeepSeek双线推进：V4.1 Flash模型明日发布 同步筹备科创板IPO" ("DeepSeek advancing on two fronts: releasing V4.1 Flash tomorrow, simultaneously preparing STAR Market IPO") — CLS Financial Wire ([link](https://www.cls.cn/detail/2478606))

> "It should be called V5, open source, and beat Opus 5.0" — Andrew Zhu, Medium analysis of DeepSeek V4.1 Flash ([link](https://xhinker.medium.com/deepseek-v4-1-flash-it-should-be-called-v5-open-source-and-beat-opus-5-0-d73fc8656c5b))

> "グローバルAI競争が米中二強体制として固まりつつある状況で、韓国と欧州が「第3のAI軸」を模索する動きとしても解釈されています" ("As global AI competition solidifies into a US-China bipolar structure, this is interpreted as South Korea and Europe seeking a 'third AI axis'") — Yahoo Japan/Chuo Ilbo on Samsung-Mistral ([link](https://news.yahoo.co.jp/articles/2a944c6afad4c55e205516a78fc598fd063720bf))

> "DeepSeek's technical report has juicy details while Anthropic's system card is focused on safety and model welfare rather than technical benchmarks" — top HN comment, DeepSeek V4.1 Flash thread ([link](https://news.ycombinator.com/item?id=49639090))

> "美企频爆雷、被点名之际，中美正筹备AI安全会谈" ("While US companies are embroiled in scandals and being named, China-US is preparing AI safety talks") — Sina News Sep 6 framing ([link](https://news.sina.com.cn/w/2026-09-06/doc-iniqwnku4233060.shtml))

> "一旦有顶级模型在中国国产硬件上跑通了稳定高效的推理，美国芯片的护城河就不再牢固" ("Once a top model runs stable and efficient inference on Chinese domestic hardware, America's chip moat will no longer be solid") — Fudan University FDDI ([link](https://fddi.fudan.edu.cn/f1/9c/c21253a717212/page.htm))

> "底座一个字没改" ("Not a single word of the base model changed") — MeetCoding on Qwen-Drive-1.0 architecture ([link](https://meetcoding.cn/lm/qwen-drive/introduction.html))

> "We share with South Korea the goal of building a third way in AI" — French President Macron on Samsung-Mistral partnership ([link](https://techcrunch.com/2026/09/08/mistral-raises-e3b-as-sovereign-ai-becomes-big-business/))
