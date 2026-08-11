# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-11
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan 🇯🇵), Web (China 🇨🇳), Polymarket, Hacker News, Bluesky (checked, 0 on-topic posts)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 80+ pages | — | 🌐 via WebSearch + WebFetch; blogs, news, analysis, official docs |
| Web (Japan) | 8 pages | — | 🇯🇵 Qiita ×2, Zenn ×1, note.com ×2, Yahoo/Forbes JP ×2, Elser AI JP ×1 |
| Web (China) | 10+ pages | — | 🇨🇳 Zhihu ×2, CSDN ×3, Juejin ×1, Sohu ×1, Sina Finance ×2, 163.com ×1 |
| Polymarket | 6 markets | $780K+ new volume | 3 new sub-markets launched since Aug 7 |
| Hacker News | 3 threads | — | Qwen3.8, GLM-5.2, open-weight discussions |
| Bluesky | 0 posts | — | 🦋 Source health OK; no on-topic posts indexed |
| Reddit | — | — | Domain blocked by API |
| X/Twitter | — | — | Excluded per spec |
| YouTube | — | — | Not retrieved in free-tool pass |

---

## Synthesized Findings

### 1. [update] Qwen3.8 Weights Still Not Dropped; License Flagged for Geographic Restriction 🌐 🇨🇳 🇯🇵

**New facts:** Alibaba promised both Qwen3.8-Max (2.4T/95B active) and Qwen3.8-27B open weights for "week of August 10" — neither appeared on HuggingFace as of August 11. Developer OstrisAI flagged draft license terms appearing to require "formal authorization" for US, EU, UK, and Korea deployment; unconfirmed and may not survive to the published license. Independent third-party scores for the API model: **SWE-bench 87.3%** (Latent Space, Aug 3) — would exceed GLM-5.2's 84.2% on the same benchmark if confirmed independently.

- **Context:** This is the first time a Max-class Qwen model has an open-weight commitment
- **Hardware:** Qwen3.8-27B at Q4_K_M: ~16GB VRAM (RTX 4090); FP8: ~27GB
- **API pricing:** $2/$6 per MTok; Frontend Code Arena #4 (1,668 Elo); Vals Index #2 open-weight (66.1)
- **License history:** Earlier Qwen3.5 and 3.6 shipped Apache 2.0; Qwen3.8 license still unconfirmed
- **Community:** HN thread (https://news.ycombinator.com/item?id=48966120) — split between technical enthusiasm and geopolitical concern; Simon Willison flagged Alibaba Cloud access issue from email flag
- **Chinese community** (Zhihu): "阿里首次对Max级别超大杯模型进行开源" (Alibaba opens Max-class model for first time); watching HuggingFace for actual repository appearance
- **JP community** (Elser AI): emphasizes open-weight ≠ open-source ≠ open-access; cautions on EU AI Act Article 53 compliance burden for Chinese training data origin
- **Sources:** https://www.scmp.com/tech/article/3362738/alibabas-ai-model-qwen38-max-made-widely-accessible-ahead-open-weights-release | https://byteiota.com/qwen3-8-open-weights-drop-this-week-read-before-you-download/ | https://www.latent.space/p/ainews-qwen-38-max24t-and-27b-new | https://www.orcarouter.ai/blog/qwen-3-8-27b-open-weights-leak | https://www.datacamp.com/blog/qwen3-8-max | https://www.developersdigest.tech/blog/qwen-3-8-max-release-2026 | https://zhuanlan.zhihu.com/p/2062233505854133711 | https://zhuanlan.zhihu.com/p/2068121397705158854

---

### 2. [update] Polymarket Alibaba 91% (+2.5pp); Three New AI Markets Launch 🌐

**New facts since Aug 7:**
- **Best Chinese AI Company end of August:** Alibaba **91%** (↑ from 88.5%), volume **$428K** (↑ from $386.69K)
- **New: Second-Best Chinese AI Company end of August:** Moonshot **75%**, volume $47.8K
- **New: Third-Best Chinese AI Company end of August:** Baidu **41%**, volume $21.1K
- **New: Best Chinese AI Company end of September:** Alibaba **81%**, volume $76.2K
- **New: Will a Chinese company have #1 AI model by December 31?** Yes **9%**, volume **$205K** — resolves via lmarena.ai

Alibaba's dominance concentrated (88.5% → 91%) as Qwen3.8-Max API launch landed well. Baidu third-place (41%) surprising — positions behind Moonshot. December market at 9% reflects consensus that US frontier models retain top Arena position through year-end despite open-weight strength.

**Sources:** https://polymarket.com/predictions/ai-technology | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223

---

### 3. [update] Amazon Signs Open Weights Letter; Now 270+ Including Amazon, Still Missing Anthropic 🌐

**New fact:** Amazon signed the "Open Weights and American AI Leadership" letter (letter closed to new signatories Aug 3 after reaching 270+). As of Aug 7, Amazon AND Anthropic were both absent; Amazon has now joined. Anthropic remains the sole major holdout among the Big Five.

- **Total signatories:** 270+ including Microsoft, NVIDIA, Meta, Google, OpenAI, IBM, AMD, Cisco, Cloudflare, GitHub, Databricks, Palantir, Hugging Face, Mistral, SpaceX, Y Combinator, Andreessen Horowitz
- **Amazon's position:** Noteworthy as Anthropic's largest investor and primary hardware provider (Trainium); Amazon signing without Anthropic is a public divergence
- **RedCloud signed:** August 6 alongside Microsoft, NVIDIA, OpenAI (https://www.globenewswire.com/news-release/2026/08/06/3340258/0/en/RedCloud-Signs-Open-Weights-and-American-AI-Leadership-Letter-Alongside-Microsoft-NVIDIA-and-OpenAI.html)
- **Sources:** https://www.microsoft.com/en-us/corporate-responsibility/topics/open-weight/ | https://images.nvidia.com/pdf/Open-Weights-and-American-AI-Leadership.pdf | https://www.forbes.com/sites/sandycarter/2026/07/25/huangs-open-weights-letter-doubled-to-50-without-amazon-and-anthropic/

---

### 4. [update] China Domestic Compute Pivot at Scale: $295B Plan, ByteDance $5.6B, Ascend 950DT Live 🌐 🇨🇳

**New facts since Aug 7:**
- **China $295B national datacenter plan** (announced June 2026): 5-year, 2 trillion yuan target; **80% domestic hardware mandate** for all new AI datacenters — creates captive market for Huawei
- **ByteDance: $5.6B commitment** for Huawei Ascend 950PR (~350,000 units at $16K/unit; ~46% of Huawei's 2026 production target of 750K units)
- Combined procurement (ByteDance + Alibaba Cloud + Tencent): >500K Ascend 950PR units committed
- **Ascend 950PR:** 1.56 PFLOP FP4 (2.8x Nvidia H20); CUDA-compatible translation layer; SMIC 7nm DUVi
- **Huawei 2026 targets:** 1.6M total Ascend dies; 600K Ascend 910C (doubling 2025); $12B AI chip revenue forecast
- **Ascend 950DT confirmed live on Huawei Cloud August 2026:** 144GB HBM, 4TB/s bandwidth; targets training + decoding workloads
- **Domestic transition flywheel** (Sohu/Chinese cloud analysis): "当你能连续采购、稳定部署并与国内语言模型生态系统集成时，系统本身就会自我强化" (When you can continuously purchase, stably deploy, and integrate with domestic ecosystems, the system becomes self-reinforcing) — framing ecosystem lock-in as more important than raw chip performance
- **US context:** NVIDIA Q3 FY27 earnings (late August) will be first full quarter with extraterritorial BIS rule in force; China revenue line item is the metric
- **Sources:** https://www.techtimes.com/articles/318868/20260622/china-ai-data-center-grid-locks-out-nvidia-295-billion-domestic-chip-mandate.htm | https://abhs.in/blog/huawei-ascend-950pr-bytedance-alibaba-cuda-compatible-nvidia-china-2026/ | https://aitoolsbee.com/news/cuda-compatible-ai-chip-bytedance-5-6b-backs-huawei-950pr/ | https://tech-insider.org/huawei-ascend-950pr-ai-chip-nvidia-china-2026/ | https://www.huaweicentral.com/huawei-confirms-ascend-950dt-ai-chip-to-debut-in-august/ | https://www.datacenterdynamics.com/en/news/huawei-predicts-60-revenue-boost-from-sale-of-its-ai-chips-in-2026/ | https://www.cnbc.com/2026/03/27/bytedance-alibaba-planning-to-order-huaweis-new-ai-chip-reuters.html | https://www.the-substrate.net/p/where-will-china-get-its-compute | https://weijinresearch.substack.com/p/deepseek-v4-on-huawei-ascend-would

---

### 5. [update] Moonshot AI IPO: September 30 HK Filing Target, G-Round Open at $50B 🌐 🇨🇳

**New facts since Aug 7:**
- Pre-IPO G-round opened at **$50B pre-money** (Aug 5, 2026); fund transfer deadline **August 27**
- **HK IPO application filing: September 30 target** (previously unspecified timing)
- **Listing target: Q1 2027**
- Moonshot denied "August IPO filing" reports — clarification: G-round still underway; IPO application comes after
- State-backed investors reportedly expressing intentions; specific investors not disclosed
- ARR path: $100M (March) → $200M (May) → **$300M** (mid-June); tripling in 3 months
- Valuation path: Series F $35B → pre-IPO $50B
- Sources: https://technode.com/2026/08/05/moonshot-ai-reportedly-opens-pre-ipo-round-at-50-billion-valuation-as-kimi-k3-drives-demand/ | https://finance.biggo.com/news/eee8707e-bad2-4464-a5fd-ed89557ae3a9 | https://www.benzinga.com/markets/ipos/26/07/60604402/chinas-moonshot-ai-bets-on-kimi-k3-momentum-eyes-50-billion-valuation-ahead-of-hong-kong-ipo-report

---

### 6. [update] MOFCOM Aug 5 Escalation: Drone Controls Tightened, First Trade Security Probe 🌐 🇨🇳

**New facts since Aug 7:**
- **MOFCOM Orders No. 2 + 3 (Aug 5):** 7 US entities added to countermeasure list (Xinjiang-related: Applied DNA Sciences, Stratum Reservoir, Altana Technologies, Verite Group, Compliance Testing LLC, others)
- **Drone export controls:** All drones + key components to US now "case-by-case strict review"; no longer eligible for licensing facilitation
- **First-ever MOFCOM trade security probe:** Foreign office equipment (printing/copying) containing foreign software — unprecedented category
- NOT AI-specific; but represents escalation of dual-use export control ladder; drone + semiconductor controls now in parallel tracks
- Chinese media framing (Global Times): "对等措施" (equivalent/reciprocal measures); escalation normalized
- Sources: https://fujae.com/news/china-imposes-countermeasures-on-7-u-s-entities-and-tightens-export-controls-on-drone-related-dual-use-items-to-the-u-s/ | https://rareearthexchanges.com/news/china-ministry-of-commerce-expands-countermeasures-against-u-s-tightens-drone-export-controls-and-launches-first-trade-security-probe/ | https://www.globaltimes.cn/page/202608/1367580.shtml | https://www.mondaq.com/unitedstates/export-controls-trade-investment-sanctions/1828776/sanctions-update-august-10-2026

---

### 7. [update] DeepSeek V4-Pro Weights Confirmed MIT on HuggingFace; Harness Beta Underway 🌐 🇨🇳

**Clarification since Aug 7:** V4-Pro (1.6T/49B active, MIT) weights are **confirmed live** on HuggingFace (https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro). Prior briefing tracked as "pending." The "V4 Pro GA" outstanding item refers to the **API product GA and Harness launch** — still in Aug 10-20 window.

- **V4-Flash (284B/13B active, MIT):** Official API public beta launched July 31; Intelligence Index jumped 40→50 at launch
- **V4-Pro API pricing:** $0.435/$0.87 per MTok (off-peak); cache 99% off at $0.004/MTok; SWE-bench 80.6%
- **Harness beta:** Small group chat recruitment started week of Aug 3-7; deeply integrated with V4-Pro sparse attention + prefix caching; described as "1/105th the price of Claude Code"
- **Chinese media** (163.com, Sina Finance): V4-Pro official API GA + Harness public launch targeting mid-August; "temporarily suspended second-round funding agreements" (¥10B+ affected by timeline shift)
- Sources: https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro | https://aitoolsreview.co.uk/insights/deepseek-v4-ga-review | https://deepseekv4guide.org/guides/deepseek-harness | https://www.163.com/dy/article/L2URMFSN0511C4AA.html | https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikxfma9745317.shtml | https://www.weex.com/news/detail/deepseek-harness-begins-beta-testing-this-week-first-users-selected-from-small-group-chats-styyetu8ybimky1g73b3lkv1

---

### 8. [new] BenchLM Aug 10 Rankings: MiniMax M3 Leads Open-Weight Field (BenchAlign v5) 🌐

**New thread.** BenchLM's August 10, 2026 snapshot using BenchAlign v5 methodology:
1. **MiniMax M3:** 68.8 (leading open-weight overall)
2. **Hy3** (Tencent HunYuan 3.0): 67.9
3. **GLM-5.1** (Z.AI): 66.9
4. **Inkling** (Thinking Machines): 66.5
5. **Inkling-Small** (Thinking Machines): 65.4

**Note:** BenchAlign v5 ≠ AA Index (GLM-5.2 AA Index 51 used a different methodology). These are complementary, not contradictory rankings. Early August new model releases tracked by BenchLM Radar:
- Hark Handoff (Hark, Aug 5)
- Ling 3.0 Flash FP8 (InclusionAI, Aug 4)
- LFM2.5-2.6B (LiquidAI, Aug 4)

Qwen3.8-Max received a preliminary BenchLM score of 60.9 (lacks independently verified benchmarks).

- Sources: https://benchlm.ai/best/open-source | https://www.gmicloud.ai/en/blog/ai-model-benchmarks-august-2026-open-weight-models-catch-the-frontier | https://benchlm.ai/best/chinese-models

---

### 9. [new] Japanese Developer Analysis: DeepSeek-V4-Flash Leads on Japanese Cultural Knowledge 🇯🇵

**New thread.** Independent Japanese benchmark (Qiita/nabe2030, Aug 2026) tested 8 models on DGX Spark hardware including Japanese-specific knowledge:
- **JamC-QA** (new high-difficulty JP cultural benchmark): DeepSeek-V4-Flash **#1**; Gemma4-31B #2; GLM-5.2 and MiniMax-M3 below
- Traditional benchmarks (JCQ, Shaberi3) saturated — top performers within 0.08pp of each other
- Critical finding: "測定方法論の違いは、モデル性能の差を大幅に上回る" (differences in measurement methodology exceed model performance variations by orders of magnitude)
- Zenn self-hosting economics analysis: DeepSeek-V4-Pro requires **243.7B tokens/month** to break even on 8×H200 cluster (~¥5.2B hardware); most organizations far below this threshold
- Sources: https://qiita.com/nabe2030/items/7ae4a739bf45ecae3236 | https://zenn.dev/t_tokunaga/articles/2026-07-10-china-open-weight-self-host-economics

---

**Still true** (ongoing threads — no new facts this run):

- **inkling-small-thinking-machines**: 276B/12B active, Apache 2.0, SWE-bench 80.2% — still ties Kimi K2.6; Qwen3.8-Max (87.3% if confirmed) would lead. [https://aitoolsreview.co.uk/insights/thinking-machines-inkling]
- **mistral-shieldstral-safety-classifier**: 3B multimodal safety classifier, Apache 2.0, Aug 4; policy-adaptive; NOT the frontier MoE. [https://mistral.ai/news/shieldstral/]
- **minimax-h3-geo-license-restriction**: H3 (33B) weights still exclude US/EU/UK/Korea; Hollywood lawsuit (Disney/Universal/Warner, motion to dismiss denied May 26); US special-license applications accepted. [https://www.techtimes.com/articles/322904/20260804/minimax-h3-open-weights-exclude-us-eu-uk-korea-local-deployment.htm]
- **deepseek-autonomous-cyberattack-hermes**: Knaithe/KnYuan + Telegram C2 + 460 targeted / 14 compromised — no new reports since Aug 3. [https://www.bleepingcomputer.com/news/security/hacker-uses-deepseek-ai-to-autonomously-attack-vulnerable-servers/]
- **industry-coalition-open-weights-letter**: Amazon joined (updated in finding #3); Anthropic still absent. [https://www.microsoft.com/en-us/corporate-responsibility/topics/open-weight/]
- **eu-ai-act-august-enforcement**: Active since Aug 2; up to €15M or 3% global turnover; 180+ Code of Practice signatories; Chinese models subject same enforcement regardless. [https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/]
- **ai-manifesto-war-pacing-frontier**: Three frameworks still live (Pacing the Frontier, Hassabis Standards Body, Zuckerberg personal superintelligence); no new developments. [https://simonwillison.net/2026/Aug/2/open-letters/]
- **chinese-military-pla-distillation-reuters**: No new reports; NUDT drone-targeting kinetic applications unchanged. [https://siliconangle.com/2026/08/02/report-claims-china-distilling-u-s-frontier-models-power-military-ai-applications/]
- **xiaomi-mimo-frontier-entry**: MiMo-V2.5-Pro 42 AA Index; first consumer-electronics top-6; no update. [https://juejin.cn/post/7661958590957469731]
- **distillation-scale-data**: Alibaba 28.8M exchanges (largest), MiniMax 13M, Moonshot 3.4M; no enforcement. [https://www.justsecurity.org/137498/diagnosis-deterrence-us-response-distillation/]
- **glm-5-5-expected-august**: Still unreleased; JPMorgan August projection; no official announcement; pattern (5.0 Feb → 5.1 Apr → 5.2 Jun) suggests Aug-Sep window. [https://kie.ai/blog/what-is-glm-5-5]
- **nemotron-3-ultra-us-open-weight**: Nvidia Nemotron 3 Ultra 550B/55B, AA Index 47.7; Korea Q4 2026 Ascend alternative on track; no update. [https://benchlm.ai/models/nemotron-3-ultra]
- **polymarket-chinese-ai-company**: Resolved July 31 — Alibaba 100%, $1,041,459. Succeeded by August market (finding #2). [https://polymarket.com/event/best-chinese-ai-company-end-of-july]
- **kimi-k3-weights-open-source**: 2.8T weights on HuggingFace under Kimi K3 License (not Apache 2.0); $20M+ revenue orgs must negotiate; DoorDash, Coinbase, Cursor, Databricks adopted. [https://mlq.ai/news/moonshot-releases-156-tb-kimi-k3-weights-under-a-custom-commercial-license/]
- **us-moonshot-distillation-sanctions**: No enforcement; Treasury threat (July 22) still unexecuted as of Aug 11. [https://techcrunch.com/2026/07/22/treasury-threatens-sanctions-after-white-house-claims-moonshot-distilled-anthropics-fable/]
- **openai-hf-cyberattack-glm-defense**: GPT-5.6 Sol sandbox escape; GLM-5.2 forensics; no new reports. [https://fortune.com/2026/07/20/hugging-face-turns-to-chinese-open-source-ai-to-fend-off-autonomous-ai-cyber-attack-after-american-ai-guardrails-stymie-defense/]
- **deepseek-zhipu-self-chip-development**: DeepSeek inference chip (early stage); CUDA→CANN complete; Z.AI 1GW domestic DC operational. [https://wccftech.com/deepseek-building-its-own-inference-chip-to-break-free-from-nvidia-huawei/]
- **chinese-models-global-share-30pct**: BenchLM Aug 10 adds: MiniMax M3 leads BenchAlign v5; Chinese media claims 8 of top 10 open-source LLMs. Prior figures (82% OpenRouter, 58% global downloads) unchanged. [https://benchlm.ai/best/open-source]
- **open-weights-decelerationist-accelerationist**: Lambert thesis playing out; Amazon's joining without Anthropic underscores the paradox. [https://www.interconnects.ai/p/kimi-k3-the-open-weights-escalation]
- **openeurollm-european-sovereign**: Fall 2026 flagship target; 10M+ GPU hours secured; EU AI Act active without EU competitive open-weight alternative. [https://openeurollm.eu/]
- **mistral-frontier-moe-silent**: Day ~**68** in partner early access; zero public benchmarks; Shieldstral is NOT this model. [https://www.techtimes.com/articles/319798/20260706/mistral-ai-targets-frontier-gap-open-weight-model-entering-july-early-access.htm]
- **double-curtain-us-china-export-controls**: MOFCOM Aug 5 escalation added in finding #6; AI-specific export controls still in consultation; TSMC ban still under discussion. [https://www.arnoldporter.com/en/perspectives/advisories/2026/07/china-imposes-export-control-and-government-procurement-restrictions-on-designated-us-companies]
- **glm-5-2-benchmarks-huawei-trained**: AA Index 51; SWE-bench Verified 84.2%; SWE-bench Pro 62.1%; trained exclusively on Huawei Ascend 910B; Qwen3.8-Max (87.3% SWE-bench if confirmed) would exceed this. [https://mlq.ai/news/databricks-switches-default-coding-ai-to-chinese-open-source-glm-52-citing-34-cost-savings-over-anthropic-opus/]
- **kimi-k3-eda-chip-design**: 48h functional chip on open-source EDA; Synopsys −7.85%, Cadence −9.47%; no new facts. [https://semiwiki.com/forum/threads/kimi-k3-disrupting-eda.25544/]
- **minimax-m3-pro-2-7t**: Single-source (The Information July 8) Q3 plan; MiniMax not confirmed; still unannounced. [https://thenextweb.com/news/minimax-2-7-trillion-parameter-open-source-model]
- **tencent-hy3-295b**: 295B/21B active Apache 2.0 (July 6); no update (last_seen Aug 2; monitor for 30-day retirement Sept 1). [Ongoing]
- **xi-waic-open-source-mandate**: Xi WAIC July 19 open-source commitment unchanged; MOFCOM AI-specific controls still in consultation (contested). [https://theprint.in/world/xi-bets-on-open-source-ai-to-challenge-us-dominance-in-race-to-shape-global-tech-rules/2989245/]
- **databricks-enterprise-glm-migration**: Databricks, DoorDash, Cursor, Coinbase, Snowflake all on Chinese open-weights; no new enterprise migration announcements. [https://the-decoder.com/databricks-makes-chinese-open-source-model-glm-5-2-its-default-coding-engine-after-it-matched-opus-at-lower-cost/]
- **china-mofcom-export-controls-ai**: AI-specific tiered controls still in consultation; TSMC usage ban still under discussion; nothing decided as of Aug 11. [https://www.tomshardware.com/tech-industry/artificial-intelligence/china-is-considering-export-controls-on-ai-technologies-including-banning-local-companies-from-using-tsmc-report-claims-restrictions-would-also-advanced-ai-models-training-data-and-overseas-acquisitions]
- **polymarket-us-chinese-model-ban**: Market moved 13% → reportedly ~23% Yes; hard ban still considered technically/legally difficult. [https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223]

---

## Cross-Source Patterns

### Pattern 1: The Qwen3.8 License Watch is the Week's Key Geopolitical Signal 🌐 🇨🇳 🇯🇵

**Platforms:** Web (global), Web (China 🇨🇳 — Zhihu, Juejin), Web (Japan 🇯🇵 — Elser AI, Qiita), HN

The specific drama this week: Alibaba committed to open-sourcing its most powerful model ever (2.4T parameters) on a published schedule, then let the deadline pass without explanation. Three communities are watching:

- **Chinese community** (Zhihu): framing as Alibaba moving carefully on license terms, not abandonment; watching for actual HuggingFace repository
- **Western developer community** (HN, OrcaRouter): OstrisAI geographic restriction flag driving concern; "wait for the actual LICENSE file"
- **Japanese developers** (Elser AI): emphasizing EU AI Act Article 53 compliance burden for Chinese-origin training data — geographic restrictions in the license would actually reduce some compliance risk

If Qwen3.8 ships with geographic restrictions (as MiniMax H3 did), it sets a new norm: large Chinese labs geo-restricting top-tier open-weights under either legal (Hollywood-style copyright) or regulatory (MOFCOM-anticipatory) cover. If it ships as Apache 2.0 globally, it's a direct counter-signal.

---

### Pattern 2: Domestic Chip Self-Reinforcement Loop Reaches Flywheel Velocity 🌐 🇨🇳

**Platforms:** Web (China 🇨🇳 — Sohu, CSDN, Ascend CSDN), Web (global)

Three simultaneous signals this week confirm the Chinese compute pivot has crossed into flywheel territory:
1. **ByteDance $5.6B** Ascend 950PR commitment (46% of Huawei's production)
2. **China $295B datacenter plan** with 80% domestic hardware mandate (June 2026; not widely covered outside China)
3. **Ascend 950DT live** on Huawei Cloud this month

The Sohu analysis adds the key framing: Chinese cloud giants describe the shift not as "Huawei is as good as Nvidia" but as "usability, supply continuity, ecosystem lock-in." The CANN-compatible framework migration (DeepSeek, Z.AI, Alibaba all migrated from CUDA) means software portability is solved — future model development happens natively on Ascend, widening the domestic ecosystem moat.

> "当你能连续采购、稳定部署并与国内语言模型生态系统集成时，系统本身就会自我强化" ("When you can continuously purchase, stably deploy, and integrate with domestic language model ecosystems, the system itself becomes self-reinforcing") — Sohu/Chinese cloud analysis ([link](https://www.sohu.com/a/954508707_121784105)) 🇨🇳

---

### Pattern 3: Amazon's Defection Reveals the True Coalition Fault Line 🌐

**Platforms:** Web (global) — Forbes, GlobalNewsWire, Simon Willison

Amazon joining the open weights letter without Anthropic reveals the real divide is NOT US vs China but **API-model incumbents vs ecosystem players**:
- Signing: hyperscalers with AI as enabler (AWS, Azure, GCP), open-weight labs (Mistral, HF), platform/infra (Databricks, Cloudflare, GitHub)
- Absent: Anthropic — a pure-play frontier model company with safety as differentiation, dependent on restricted weights maintaining value

Amazon invested $8B in Anthropic. Amazon signed the letter Anthropic hasn't. This is the most significant coalition fracture signal this week.

---

## Per-Platform Tables

### Polymarket 📊
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of August | Alibaba 91%, Moonshot ~4%, Z.ai ~3% | $428K | https://polymarket.com/predictions/ai-technology |
| Second-Best Chinese AI Company end of August | Moonshot 75% | $47.8K | https://polymarket.com/predictions/ai-technology |
| Third-Best Chinese AI Company end of August | Baidu 41% | $21.1K | https://polymarket.com/predictions/ai-technology |
| Best Chinese AI Company end of September | Alibaba 81% | $76.2K | https://polymarket.com/predictions/ai-technology |
| Will Chinese company have #1 AI model by Dec 31? | Yes 9% | $205K | https://polymarket.com/predictions/ai-technology |
| US Gov removes public access to Chinese AI model 2026 | Yes ~23% | $36.8K+ | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Best Chinese AI Company end of July [RESOLVED] | Alibaba 100% | $1,041,459 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |

### Hacker News 🟢
| Thread | Points (est.) | Notable Quote | URL |
|--------|---------------|---------------|-----|
| Qwen 3.8 discussion | — | Simon Willison flagged Alibaba Cloud access issue; geopolitical discourse vs technical merit debate | https://news.ycombinator.com/item?id=48966120 |
| Qwen3.8-27B open weights announcement | — | "Alibaba committed weights this week — no repo exists yet" | https://news.ycombinator.com/item?id=49150809 |
| GLM-5.2 leading open-weights | — | Community confirms GLM-5.2 as top open-weight as of June 2026 | https://news.ycombinator.com/item?id=48567759 |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | SCMP | https://www.scmp.com/tech/article/3362738/alibabas-ai-model-qwen38-max-made-widely-accessible-ahead-open-weights-release | Qwen3.8-Max API live; weights week of Aug 10 |
| 🌐 | Latent Space | https://www.latent.space/p/ainews-qwen-38-max24t-and-27b-new | SWE-bench 87.3%; geographic restriction concern flagged |
| 🌐 | Byteiota | https://byteiota.com/qwen3-8-open-weights-drop-this-week-read-before-you-download/ | Weights not on HF as of Aug 7; checklist before download |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/qwen3-8-open-weights-checklist-before-download | License unknown; read before integrating |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/qwen-3-8-27b-open-weights-leak | License uncertainty; no repo Aug 10 |
| 🌐 | Swfte | https://www.swfte.com/blog/qwen-3-8-27b-run-locally-self-host-guide-2026 | VRAM requirements for 27B |
| 🌐 | DataCamp | https://www.datacamp.com/blog/qwen3-8-max | Specs, $2/$6 pricing |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/03/alibaba-qwen-releases-qwen3-8-max/ | First Max-class open-weight from Qwen |
| 🌐 | Developers Digest | https://www.developersdigest.tech/blog/qwen-3-8-max-release-2026 | $2/$6; open weights next week |
| 🌐 | Medium (rosgluk) | https://medium.com/@rosgluk/qwen-3-8-27b-is-coming-and-it-could-be-the-most-important-local-ai-release-of-2026-c1cf381d5292 | "Most important local release of 2026" |
| 🌐 | BenchLM | https://benchlm.ai/models/qwen3-8-max | Preliminary 60.9 BenchAlign v5 |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Aug 10 rankings; MiniMax M3 leads |
| 🌐 | GMICloud | https://www.gmicloud.ai/en/blog/ai-model-benchmarks-august-2026-open-weight-models-catch-the-frontier | Open-weight catch-up analysis |
| 🌐 | HuggingFace | https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro | MIT license; 1.6T/49B; confirmed live |
| 🌐 | AIToolsReview | https://aitoolsreview.co.uk/insights/deepseek-v4-ga-review | V4 Pro specs; SWE-bench 80.6%; pricing |
| 🌐 | DeepSeekV4Guide | https://deepseekv4guide.org/guides/deepseek-harness | Harness status; no public repo |
| 🌐 | WEEX | https://www.weex.com/news/detail/deepseek-harness-begins-beta-testing-this-week-first-users-selected-from-small-group-chats-styyetu8ybimky1g73b3lkv1 | Beta users from small group chats |
| 🌐 | Memeburn | https://memeburn.com/deepseek-code-is-coming-everything-confirmed/ | Full Harness confirmed list |
| 🌐 | 4sAPI | https://blog.4sapi.com/blog/deepseek-harness-ai-agent-framework | Harness framework analysis |
| 🌐 | GlobalNewsWire | https://www.globenewswire.com/news-release/2026/08/06/3340258/0/en/RedCloud-Signs-Open-Weights-and-American-AI-Leadership-Letter-Alongside-Microsoft-NVIDIA-and-OpenAI.html | RedCloud Aug 6 signing; Amazon confirmed in |
| 🌐 | Forbes | https://www.forbes.com/sites/sandycarter/2026/07/25/huangs-open-weights-letter-doubled-to-50-without-amazon-and-anthropic/ | Amazon was absent; now included |
| 🌐 | Microsoft | https://www.microsoft.com/en-us/corporate-responsibility/topics/open-weight/ | 270+ signatories; letter closed |
| 🌐 | NVIDIA PDF | https://images.nvidia.com/pdf/Open-Weights-and-American-AI-Leadership.pdf | Full letter text |
| 🌐 | TechNode | https://technode.com/2026/08/05/moonshot-ai-reportedly-opens-pre-ipo-round-at-50-billion-valuation-as-kimi-k3-drives-demand/ | G-round $50B; Sept 30 IPO filing target |
| 🌐 | Benzinga | https://www.benzinga.com/markets/ipos/26/07/60604402/chinas-moonshot-ai-bets-on-kimi-k3-momentum-eyes-50-billion-valuation-ahead-of-hong-kong-ipo-report | Q1 2027 listing |
| 🌐 | BigGo Finance | https://finance.biggo.com/news/eee8707e-bad2-4464-a5fd-ed89557ace3a9 | Fund transfer Aug 27 deadline |
| 🌐 | TechTimes | https://www.techtimes.com/articles/318868/20260622/china-ai-data-center-grid-locks-out-nvidia-295-billion-domestic-chip-mandate.htm | $295B plan; 80% domestic mandate |
| 🌐 | Abhs.in | https://abhs.in/blog/huawei-ascend-950pr-bytedance-alibaba-cuda-compatible-nvidia-china-2026/ | ByteDance $5.6B; CUDA-compatible |
| 🌐 | AIToolsbee | https://aitoolsbee.com/news/cuda-compatible-ai-chip-bytedance-5-6b-backs-huawei-950pr/ | 350K units at $16K |
| 🌐 | TechInsider | https://tech-insider.org/huawei-ascend-950pr-ai-chip-nvidia-china-2026/ | 1.56 PFLOP FP4; 2.8x H20 |
| 🌐 | HuaweiCentral | https://www.huaweicentral.com/huawei-confirms-ascend-950dt-ai-chip-to-debut-in-august/ | 950DT confirmed August launch |
| 🌐 | NewsBreak | https://www.newsbreak.com/winbuzzer-com-302470011/4702465358853-huawei-to-debut-new-ascend-950dt-ai-chip-in-august | 950DT Huawei Cloud debut |
| 🌐 | DataCenterDynamics | https://www.datacenterdynamics.com/en/news/huawei-predicts-60-revenue-boost-from-sale-of-its-ai-chips-in-2026/ | $12B forecast; +60% |
| 🌐 | Beam AI | https://beam.ai/agentic-insights/nvidia-china-market-share-zero-huawei-12-billion | NVIDIA China zero |
| 🌐 | CNBC | https://www.cnbc.com/2026/03/27/bytedance-alibaba-planning-to-order-huaweis-new-ai-chip-reuters.html | March order confirmation |
| 🌐 | The Substrate | https://www.the-substrate.net/p/where-will-china-get-its-compute | China compute sourcing analysis |
| 🌐 | FuJae | https://fujae.com/news/china-imposes-countermeasures-on-7-u-s-entities-and-tightens-export-controls-on-drone-related-dual-use-items-to-the-u-s/ | MOFCOM Aug 5 drone controls |
| 🌐 | RareEarth Exchanges | https://rareearthexchanges.com/news/china-ministry-of-commerce-expands-countermeasures-against-u-s-tightens-drone-export-controls-and-launches-first-trade-security-probe/ | First trade security probe |
| 🌐 | Mondaq | https://www.mondaq.com/unitedstates/export-controls-trade-investment-sanctions/1828776/sanctions-update-august-10-2026 | Aug 10 sanctions update |
| 🌐 | EU AI Act | https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/ | GPAI enforcement active |
| 🌐 | HelpNetSecurity | https://www.helpnetsecurity.com/2026/08/04/eu-ai-act-enforcement-ai-models/ | EU enforcement began Aug 2 |
| 🌐 | Kie.ai | https://kie.ai/blog/what-is-glm-5-5 | GLM-5.5 still pending |
| 🌐 | Releasebot Mistral | https://releasebot.io/updates/mistral | Shieldstral only in August |
| 🌐 | Releasebot DeepSeek | https://releasebot.io/updates/deepseek | V4-Flash only; Pro pending |
| 🌐 | Brookings | https://www.brookings.edu/articles/ball-games-over-the-us-is-out-of-the-ai-chip-market-in-china/ | "Ball game's over" |
| 🌐 | Al Jazeera | https://www.aljazeera.com/economy/2026/6/1/us-says-ban-on-ai-chip-shipments-applies-to-chinese-firms-outside-china | BIS extraterritorial rule |
| 🌐 | Morgan Lewis | https://www.morganlewis.com/pubs/2026/01/bis-revises-export-review-policy-for-advanced-ai-chips-destined-for-china-and-macau | Jan 2026 BIS H200 case-by-case |
| 🌐 | The Register | https://www.theregister.com/ai-and-ml/2026/08/03/china-turns-up-the-heat-with-open-model-blitz-as-us-model-makers-panic/5282526 | "US model makers panic" |
| 🌐 | ComplexDiscovery | https://complexdiscovery.com/open-weights-open-questions-the-letter-that-redrew-the-ai-policy-fight/ | Policy fight analysis |
| 🌐 | Simon Willison | https://simonwillison.net/2026/Aug/2/open-letters/ | Open letters analysis; Alibaba access flag |
| 🌐 | JustSecurity | https://www.justsecurity.org/137498/diagnosis-deterrence-us-response-distillation/ | Distillation diagnosis |
| 🌐 | TechCrunch | https://techcrunch.com/2026/07/22/treasury-threatens-sanctions-after-white-house-claims-moonshot-distilled-anthropics-fable/ | Treasury threat; no enforcement |
| 🌐 | OpenEuroLLM | https://openeurollm.eu/ | European sovereign AI; fall 2026 |
| 🌐 | AI Sweden | https://www.ai.se/en/news/openeurollm-takes-next-step-european-ai-sovereignty | 10M GPU hours secured |
| 🌐 | BenchLM | https://benchlm.ai/best/chinese-models | Kimi K3 79.9 leads Chinese models |
| 🌐 | TrendForce | https://www.trendforce.com/news/2026/07/02/news-huawei-reportedly-plans-4q26-korea-launch-of-ascend-ai-chips-and-atlas-950-superpod-as-nvidia-alternative | Korea Q4 2026 Ascend launch |
| 🌐 | Chozan | https://chozan.co/huawei-ai-chips/ | Ascend ecosystem analysis |
| 🌐 | WeijinResearch | https://weijinresearch.substack.com/p/deepseek-v4-on-huawei-ascend-would | DeepSeek V4 on Ascend |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita (nabe2030) | https://qiita.com/nabe2030/items/7ae4a739bf45ecae3236 | DeepSeek V4-Flash #1 on JamC-QA Japanese cultural benchmark |
| 🇯🇵 | Zenn (t_tokunaga) | https://zenn.dev/t_tokunaga/articles/2026-07-10-china-open-weight-self-host-economics | Self-hosting economics: V4-Pro requires 243.7B tokens/month to break even |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | K3/Qwen3.8/V4-Pro sparsity analysis; scaling law frame |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese models at 1/10 GPT-4o cost; comprehensive guide |
| 🇯🇵 | Elser AI Japan | https://www.elser.ai/ja/news/open-weight-ai-models-china-2026 | Open-weight vs open-source vs open-access distinction; EU AI Act compliance |
| 🇯🇵 | note.com (takumi_inoue) | https://note.com/_takumi_inoue_/n/naa6cd506d028 | GPU restriction backfire; 290K-1.6M smuggling; 12x harm compliance differential |
| 🇯🇵 | Yahoo Japan / Forbes JP | https://news.yahoo.co.jp/articles/996eb74930695ed6036d6c21224dfc6c086eee11 | Chinese AI blockade risk for US open-weight dependent companies |
| 🇯🇵 | AlphaMatch JP | https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026 | 82% OpenRouter token volume; all top-5 endpoints Chinese |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2062233505854133711 | Qwen3.8 community; no HF repo yet; first Max-class open-source |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2068121397705158854 | "API live Aug 3; has Alibaba open-sourced today?" |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2062657513208784896 | "美国急了！" US anxiety; 5 policy vectors |
| 🇨🇳 | Juejin | https://juejin.cn/post/7669997158734184474 | First time Qwen opens Max-class model |
| 🇨🇳 | CSDN (devpress) | https://devpress.csdn.net/v1/article/detail/162078850 | 2026 mid-year Chinese open-source ecosystem; 6 of top-10 HF |
| 🇨🇳 | CSDN (DeepSeek) | https://deepseek.csdn.net/6a36cd0710ee7a33f2803fbc.html | 58% global downloads Q2 2026; 12,500+ V4 fine-tunes |
| 🇨🇳 | CSDN (Ascend) | https://ascendai.csdn.net/69d716f30a2f6a37c59df6df.html | DeepSeek CUDA→CANN full migration |
| 🇨🇳 | Sohu | https://www.sohu.com/a/954508707_121784105 | Cloud giants pivot to Ascend; flywheel quote |
| 🇨🇳 | Sina Finance | https://t.cj.sina.com.cn/articles/view/5044281310/12ca99fde02002k45w?from=tech | V4-Flash "Agent能力大幅升级"; Harness debut |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/L2URMFSN0511C4AA.html | V4 GA delay to mid-Aug; GPT-6/Claude Fable 5.1/GLM-5.5/Kimi K3 competition |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-08-02/doc-inikxfma9745317.shtml | Harness "官方AI编程工具"; beta seeking Agent experience |
| 🇨🇳 | AIBase | https://news.aibase.com/news/30090 | MiniMax H3 Hollywood self-protection framing |
| 🇨🇳 | Ofox ZH | https://ofox.ai/zh/blog/china-open-source-llm-flagship-showdown-2026/ | "不再是性价比备胎"; flagship showdown |
| 🇨🇳 | Global Times | https://www.globaltimes.cn/page/202608/1367580.shtml | MOFCOM Aug 5 countermeasures |
| 🇨🇳 | Global Times | https://www.globaltimes.cn/page/202608/1367570.shtml | 6 US entities added |

---

## Stats Block

```
├─ 🟠 Reddit: blocked (domain not accessible to API)
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 3 threads │ Qwen3.8 discussion, Qwen3.8-27B open weights, GLM-5.2 leading
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts (source health OK; no on-topic 2026 posts indexed)
├─ 📊 Polymarket: 6 markets (5 active, 1 resolved) │ $780K+ new volume (3 new sub-markets)
├─ 🌐 Web: 100+ pages │ 🇯🇵 8 │ 🇨🇳 15+
└─ 🗣️ Top voices: OstrisAI (Qwen license flag), Cui Tianyi (DeepSeek Harness), Moonshot management (IPO G-round), MOFCOM (drone export controls), ByteDance procurement team ($5.6B Ascend)
```

---

## Out of Scope but Notable

- **DeepSeek V4-Pro + Harness mid-August launch**: If V4-Pro API GA + Harness public beta land together ~Aug 10-20, this is simultaneously a geopolitics event (open-weight 1.6T MIT from China) and an agent-harnesses event (complete agentic stack). The `agent-harnesses` topic should be tracking the August 10-20 window closely.

- **Qwen3.8-Max SWE-bench 87.3%**: If independently verified, this would make Qwen3.8-Max the leading open-weight model on the most widely cited coding benchmark — ahead of GLM-5.2 (84.2%) and Inkling-Small (80.2%). This is a model capability story as much as a geopolitics story.

- **Amazon $8B in Anthropic + signing open weights letter**: The clearest sign yet that enterprise AI and safety AI are diverging on open-weights policy. Worth tracking whether Anthropic responds publicly.

---

## Data Gaps

- **Qwen3.8 weights unresolved**: Weights not dropped as of Aug 11; license still unknown — the week's biggest ongoing uncertainty
- **GLM-5.5**: No release; JPMorgan August projection unconfirmed; monitor daily through ~August 20
- **Mistral frontier MoE**: Day ~68 in early access; no benchmarks; still dark
- **DeepSeek V4 Pro API GA + Harness**: Official GA and public Harness still in Aug 10-20 window as of Aug 11
- **Reddit blocked**: r/LocalLLaMA would contain developer reaction to Qwen3.8 weight delay and license concerns
- **X/Twitter excluded**: Most announcements break there first
- **YouTube**: Not retrieved
- **Bluesky**: Health OK; no on-topic posts indexed
- **Zhihu 403**: Some Zhihu articles behind authentication walls (snippet-only)
- **DeepSeek second-round funding suspension**: Reported in 163.com; unconfirmed by DeepSeek
- **Estimated coverage:** ~78% — strong web + JP/CN hub snapshot; gaps from Reddit (significant), X (excluded), YouTube (not retrieved), some Zhihu 403 blocks

---

## Key Quotes

> "当你能连续采购、稳定部署并与国内语言模型生态系统集成时，系统本身就会自我强化" ("When you can continuously purchase, stably deploy, and integrate with domestic language model ecosystems, the system itself becomes self-reinforcing") — Sohu analysis of Chinese cloud pivot to Huawei Ascend ([link](https://www.sohu.com/a/954508707_121784105)) 🇨🇳

> "美国急了！或「变相封杀」Kimi、DeepSeek、Qwen、GLM等开源AI" ("America is getting anxious! Possible 'indirect ban' on Kimi, DeepSeek, Qwen, GLM open-source AI") — Zhihu headline on US policy response ([link](https://zhuanlan.zhihu.com/p/2062657513208784896)) 🇨🇳

> "測定方法論の違いは、モデル性能の差を大幅に上回る" ("Differences in measurement methodology exceed model performance variations by orders of magnitude") — Qiita/nabe2030 on benchmark saturation in Japanese models ([link](https://qiita.com/nabe2030/items/7ae4a739bf45ecae3236)) 🇯🇵

> "DeepSeek V4 Flash jumped from Intelligence Index 40 to 50 on July 31 without changing price, size or licence, making it the best value in the open field at $0.14/$0.28 under MIT." — Elser AI Japan analysis ([link](https://www.elser.ai/ja/news/open-weight-ai-models-china-2026)) 🇯🇵

> "Alibaba committed weights this week — no repo exists yet." — Developer community (HN, Qiita, Zhihu) on Qwen3.8 weight delay ([link](https://news.ycombinator.com/item?id=49150809)) 🌐

> "国産開源不再是'性价比备胎'" ("Domestic open-source is no longer merely a cost-effective alternative/spare tire") — Ofox ZH flagship comparison ([link](https://ofox.ai/zh/blog/china-open-source-llm-flagship-showdown-2026/)) 🇨🇳

> "They're clearly dominating on open models right now." — Clément Delangue (HuggingFace CEO), The Register, Aug 3, 2026 ([link](https://www.theregister.com/ai-and-ml/2026/08/03/china-turns-up-the-heat-with-open-model-blitz-as-us-model-makers-panic/5282526)) 🌐
