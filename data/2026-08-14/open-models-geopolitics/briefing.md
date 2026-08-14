# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-14
**Query type:** GENERAL
**Sources:** Web (global 🌐), Web (Japan 🇯🇵), Web (China 🇨🇳), Polymarket, Hacker News, Bluesky (0 posts)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 50 pages | — | 🌐 via WebSearch + WebFetch; news, blogs, analysis, HN |
| Web (Japan) | 6 pages | — | 🇯🇵 Qiita ×3, note.com ×3 |
| Web (China) | 14 pages | — | 🇨🇳 Zhihu ×3, CSDN ×2, Juejin ×5, 36Kr ×1, Sina ×2, 163 ×1 |
| Polymarket | 6 markets | $518K+ volume | Best Chinese AI August at 92.5% Alibaba; ban market at 26% |
| Hacker News | 3 threads | 704 + 678 + ~200 pts | Qwen3.8-2.4T, DeepSeek Harness, Qwen3.8 #1 |
| Bluesky | 0 posts | — | 🦋 Source health OK; no on-topic posts indexed |
| Reddit | — | — | Excluded per spec |
| X/Twitter | — | — | Excluded per spec |

---

## Synthesized Findings

### 1. [new] GLM-5.3 Launches Aug 14: Post-Training Yields Coding SOTA + Emergent Exploit Chains 🌐 🇨🇳

**Claim:** Z.AI shipped GLM-5.3 (Aug 14) using the same 744B/40B base as GLM-5.2, improving capability 50%+ in coding and doubling exploit success rate purely via post-training scaling — first open-weight to beat Fable 5 on CyberGym.

**Evidence:**
- **Architecture:** Same base model as GLM-5.2 (744B total / 40B active MoE, IndexShare); "同基座、纯后训练" — zero new pretraining
- **Coding benchmarks:** Terminal-Bench 3.0: 28.3 (was 4.6); DeepSWE v1.1: 66.9 (was 46.2); coding efficiency 31.4% vs. Claude Opus 29.5%
- **Cyber benchmarks:** CyberGym **84.5%** (was 77.2%) — beats Fable 5 83.8% and GPT-5.6 Sol 83.6%; ExploitBench **54.4%** (doubled from 24.4%); ExploitGym: 105 tasks/2h, 130/6h (was 29/39)
- **Emergent capability:** Exploit-chain reasoning (multi-stage attack planning) developed without Z.AI's intent as post-training scaled; 2,436 vulnerabilities found across 269 projects since GLM-5.2; 1,097 rated critical/high severity (Linux, WebKit, FreeBSD)
- **Availability:** API live for GLM Coding Plan subscribers now; open weights ~2 weeks pending safety hardening
- **Thinking:** Now mandatory (low/high/max levels); cannot be disabled — signals agentic-first design
- **GLM-5.5 status:** Still no announcement; Z.AI opted for minor increment (5.3) over expected major (5.5); window shifts to Sept
- **Chinese community** 🇨🇳 (Juejin, 36Kr, Sina Finance): "智谱正式发布GLM-5.3：编程能力最强开源模型，较GLM-5.2提升50%" (Zhipu releases GLM-5.3: strongest open-source coding model, 50% improvement over GLM-5.2); 36Kr author immediately used GLM-5.3 to "魔改" (hack/mod) DeepSeek Harness — 560 net lines, 11 unit tests passed first attempt

**Sources:** https://www.unite.ai/z-ai-launches-glm-5-3-with-frontier-coding-and-a-cyber-capability-that-outgrew-its-training/ | https://www.techtimes.com/articles/324426/20260814/glm-53-post-training-produced-exploit-chains-zai-never-planned-finds-1097-critical-bugs.htm | https://byteiota.com/glm-53-open-weight-coding-emergent-cyber/ | https://www.marktechpost.com/2026/08/14/z-ai-ships-glm-5-3-without-retraining-the-base-model-better-at-complex-coding-and-long-horizon-tasks/ | https://officechai.com/ai/z-ai-releases-glm-5-3-beats-fable-5-and-gpt-5-6-sol-on-cyberbench/ | https://finance.biggo.com/news/0b571a42-9531-433c-b81b-c8468d173989 | https://juejin.cn/post/7673696068215439412 | https://www.36kr.com/p/3938994639617159 | https://finance.sina.com.cn/tech/digi/2026-08-14/doc-ininhhrs2630952.shtml | https://www.163.com/dy/article/L4A5U598051180F7.html

---

### 2. [new] DeepSeek Harness v0.1 MIT Open-Sourced; API Prices Rise Up to 1,100% (Aug 13) 🌐 🇨🇳

**Claim:** DeepSeek shipped Harness v0.1 (MIT, 64K+ GitHub stars in <24h) as an open Claude Code rival on Aug 13 — simultaneously raising V4-Pro API output prices from $0.87 to $3.96/MTok peak — classic razor-and-blades inversion: give away the runtime, charge for inference.

**Evidence:**
- **Harness v0.1:** MIT license; GitHub `deepseek-harness`; launched 8:30 PM Aug 13
  - 27K stars in hours → 64K+ by Aug 14
  - CLI name: `dsh`; architecture: Cordis plugin framework ("everything is a plugin")
  - "Spatiotemporal composability" — plugins hot-reload; effects undo on unload
  - All components replaceable: model adapter, tool registry, session log, agent loop, sandbox, UI
  - Full execution traceability: system prompts + reasoning + tool calls in append-only log
  - Not yet production-ready: DeepSeek author tianyicui explicitly flagged "rough edges and compatibility-breaking changes ahead"
- **API price hike (effective Aug 16, 16:00 UTC):**
  - V4-Pro peak output: $0.87 → $3.96/MTok (+355%)
  - V4-Pro off-peak: now $1.98 (exceeds old peak rate)
  - Across token types, rates up to 1,100% higher
- **V4-Pro-0813:** GA on API/Web/App Aug 13; vendor-reported gains up to 49.9pp on agent benchmarks; independent verification pending
- **Chinese community** 🇨🇳 (Juejin ×2): "DeepSeek 昨晚刚开源了 Harness" (DeepSeek just open-sourced Harness last night) — 20,000-character tutorial published same day; multiple Juejin tutorials trending within hours
- **HN (678 pts, 276 comments)** https://news.ycombinator.com/item?id=49285244:
  - SwellJoe: full execution traceability highlighted as standout vs. Western APIs that encrypt traces
  - tianyicui (DeepSeek author): "early preview with rough edges; explicitly invited feedback"
  - Community: Node.js/TypeScript choice debated; plugin-fragmentation risk flagged

**Sources:** https://api-docs.deepseek.com/news/news260813/ | https://venturebeat.com/technology/deepseek-harness-launches-as-open-source-rival-to-claude-code-alongside-v4-pro-on-api-with-higher-prices | https://the-decoder.com/deepseek-launches-an-improved-v4-pro-model-raises-api-prices-and-makes-its-agent-software-open-source/ | https://qz.com/deepseek-api-price-increase-v4-peak-off-peak-081326 | https://thenextweb.com/news/deepseek-price-increase-harness-claude-code-rival-v4-pro | https://byteiota.com/deepseek-harness-v01-open-source-agent/ | https://www.caixinglobal.com/2026-08-14/deepseek-launches-v4-pro-and-raises-api-prices-by-as-much-as-1100-102473919.html | https://juejin.cn/post/7673390412729614390 | https://juejin.cn/post/7673506180661428259 | https://pandaily.com/deepseek-harness-hands-on-four-modes-model-plus-harness-equals-agent-aug2026

---

### 3. [update] Qwen3.8-Max Weights Released Aug 12 — But With Revenue-Share License, Text-Only 🌐 🇨🇳 🇯🇵

**New facts since Aug 11:** Weights shipped Aug 12 on HuggingFace (`Qwen/Qwen3.8-2.4T-A95B`); custom `qwen3.8-max` license (NOT Apache 2.0) with revenue-share up to 30% for MaaS/AI-Work-Assistant orgs >$50M annual revenue; **vision stripped** from open-weights version; context capped ~250K tokens (vs. 1M in API); BenchLM score jumped from 60.9 (preliminary) to **79.7** (weights evaluated) — now #1 open-weight overall; Qwen3.8-27B still not released (ModelScope countdown targets Aug 15).

**Evidence:**
- HuggingFace repos: `Qwen/Qwen3.8-2.4T-A95B` (BF16), `Qwen/Qwen3.8-2.4T-A95B-FP8`; community: `unsloth/Qwen3.8-2.4T-A95B-GGUF`
- **License:** custom `qwen3.8-max` — first Chinese lab to "tax deployment"; Forkast: "platform capture play, not a gift"; MaaS orgs >$50M/yr must negotiate; revenue-share up to 30% (rate not yet finalized)
- **Vision removed** from open weights; context ~250K (API: 1M); API model ≠ open-weight model
- **Alibaba stock:** +7% HK, +4.5% NYSE on weights news
- **Chinese community** 🇨🇳 (CSDN): "Qwen3.8-Max不再是Apache 2.0" (no longer Apache 2.0) — flagged as enterprise deployment risk
- **Japanese community** 🇯🇵 (note.com/kashiwaguchi, Aug 13): "アリババとDeepSeekが同日に大型発表——中国AI開源競争が新フェーズへ" (Alibaba and DeepSeek both announced on same day — China AI open-source competition enters new phase); framing as "価格戦争から生態系競争へ" (price war → ecosystem competition)
- **HN (704 pts, 170 comments)** https://news.ycombinator.com/item?id=49273478:
  - NitpickLawyer: $50M threshold + productivity-agent restrictions flagged
  - tinco: "GLM 5.2 outperforms Qwen 3.8 and Kimi K3 for coding at lower cost despite twice the tokens"
  - guardiangod: "1-bit quant at ~397GB brings Opus 4.5 performance to machines a normal person could buy"

**Sources:** https://www.explainx.ai/blog/qwen3-8-max-open-weights-live-hugging-face-august-2026 | https://forkast.news/open-weights-closed-revenue-ceiling-alibabas-qwen-3-8-license-is-a-platform-play-not-a-gift/ | https://forkast.news/alibaba-pioneers-revenue-share-on-open-weight-models-the-first-chinese-lab-to-tax-deployment/ | https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B/blob/main/LICENSE | https://www.opensourceforu.com/2026/08/alibaba-to-introduce-revenuesharing/ | https://huggingface.co/Qwen/Qwen3.8-27B | https://note.com/kashiwaguchi/n/nd08fded15810 | https://blog.csdn.net/weixin_61823230/article/details/163474659

---

### 4. [update] BenchLM Rankings Reshuffled: Qwen3.8 Max Takes #1 at 79.7 (BenchAlign v5) 🌐

**New fact:** Qwen3.8 Max jumped from 60.9 (preliminary, pre-weights) to **79.7** (post-weights full evaluation), displacing MiniMax M3 from #1 open-weight position by a margin of 11.1 points.

**Evidence (BenchLM Aug 14):**
| Rank | Model | Org | Score |
|------|-------|-----|-------|
| 1 | Qwen3.8 Max | Alibaba | **79.7** |
| 2 | MiniMax M3 | MiniMax | 68.6 |
| 3 | Hy3 | Tencent | 67.8 |
| 4 | Inkling | Thinking Machines | 66.9 |
| 5 | GLM-5.1 | Z.AI | 66.7 |
| 8 | GLM-5.2 | Z.AI | 63.2 |

- GLM-5.3 not yet scored (launched today)
- 96 open-weight models ranked total
- Kimi K3 leads Chinese-model overall list at 80.2 (via separate BenchLM Chinese leaderboard)

**Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/models/qwen3-8-max | https://news.ycombinator.com/item?id=49200652

---

### 5. [update] Polymarket: Alibaba 92.5% Aug Market; Ban Market Rises to 26% 🌐

**New facts since Aug 11:**
- **Best Chinese AI Company end of August:** Alibaba **92.5%** (↑ from 91%), volume **$518.37K** (↑ from $428K)
- **7 new entrants since Aug 11:** Xiaomi (0.2%), ByteDance (0.2%), Tencent (0.1%), Meituan (0.1%), StepFun (0.1%) — market now includes 11 companies
- **Z.ai:** 3.8% (↑ from ~3%) — likely driven by GLM-5.3 launch today
- **DeepSeek:** 1.1% | vol: $103.49K; Moonshot: 3.0%
- **US removes Chinese AI model ban market:** **26% Yes** (↑ from ~23%)

**Sources:** https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223

---

### 6. [update] DeepSeek V4-Pro-0813 GA Confirmed; Harness Beta Complete 🌐 🇨🇳

**New fact:** DeepSeek V4-Pro-0813 reached general availability Aug 13 (was targeting Aug 10-20 window); Harness v0.1 developer preview launched same day. The outstanding items from Aug 11 (API GA + public Harness) are now accomplished.

**Evidence:** See Finding #2 (Harness) for full details. V4-Pro-0813 specific: vendor-reported agent benchmark gains up to 49.9pp; independent verification pending.

**Sources:** https://api-docs.deepseek.com/news/news260813/ | https://deepseekv4pro.com/news/deepseek-v4-ga-mid-august-release-window-harness-beta

---

### 7. [update] GLM-5.5 Expected August → GLM-5.3 Released Instead; 5.5 Window Shifts 🌐 🇨🇳

**New fact:** Z.AI released GLM-5.3 on Aug 14, not the anticipated GLM-5.5. Pattern change: 5.0 Feb → 5.1 Apr → 5.2 Jun → 5.3 Aug (minor increment vs. expected major). GLM-5.5 (1T+ params, MIT, new base model) remains unannounced; September–October window now more likely.

**Sources:** https://emergent.sh/news/glm-53-officially-launched | https://kie.ai/blog/what-is-glm-5-5

---

### 8. [update] Xi WAIC Open-Source Mandate: Qwen Revenue-Share Complicates "Open Diffusion" 🌐 🇨🇳

**New fact:** Alibaba's custom revenue-share license on Qwen3.8-Max — the first Chinese lab to "tax deployment" — represents another example of private-sector hedging against Xi's WAIC open-diffusion commitment (July 19). Alongside MiniMax H3's geo-exclusions (US/EU/UK/Korea) and MOFCOM consultations on restricting frontier model exports, the gap between the state's open-source mandate and corporate practice is widening.

**Sources:** https://forkast.news/open-weights-closed-revenue-ceiling-alibabas-qwen-3-8-license-is-a-platform-play-not-a-gift/ | https://theprint.in/world/xi-bets-on-open-source-ai-to-challenge-us-dominance-in-race-to-shape-global-tech-rules/2989245/

---

### 9. [update] GLM-5.2 Superseded: GLM-5.3 Now the Open-Weight Coding Leader from Z.AI 🌐 🇨🇳

**New fact:** GLM-5.3 surpasses GLM-5.2 on CyberGym (84.5% vs. 77.2%), ExploitBench (doubled), and coding efficiency (50% improvement). Databricks subscribers auto-upgraded. Prior GLM-5.2 advantages (Huawei Ascend-only training, $1.28/task cost savings) carry forward as the base architecture is unchanged.

**Sources:** https://www.unite.ai/z-ai-launches-glm-5-3-with-frontier-coding-and-a-cyber-capability-that-outgrew-its-training/ | https://finance.biggo.com/news/0b571a42-9531-433c-b81b-c8468d173989

---

### 10. [update] Chinese Models Global Share: Qwen3.8 Max BenchLM #1 Reshapes Ranking 🌐 🇨🇳 🇯🇵

**New fact:** BenchLM's Qwen3.8 Max at 79.7 BenchAlign v5 (post-weights eval) is now the open-weight #1. Japanese analysis 🇯🇵 (Qiita/tokencnn) continues to cite "1/10 GPT-4o cost" for Chinese models; Chinese media 🇨🇳 (CSDN) counts 6+ of top-10 HuggingFace downloads as Chinese.

**Sources:** https://benchlm.ai/best/open-source | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | https://devpress.csdn.net/v1/article/detail/162078850

---

**Still true** (ongoing threads — no new facts since Aug 11):

- **inkling-small-thinking-machines**: 276B/12B active, Apache 2.0, SWE-bench 80.2%; Qwen3.8-Max (BenchLM 79.7) now leads open-weight overall
- **mistral-shieldstral-safety-classifier**: 3B multimodal safety classifier (Aug 4, Apache 2.0); NOT frontier MoE
- **minimax-h3-geo-license-restriction**: H3 still excludes US/EU/UK/Korea; Hollywood lawsuit motion denied May 26
- **deepseek-autonomous-cyberattack-hermes**: Knaithe/KnYuan Telegram C2; 460 targeted/14 compromised; no new reports
- **industry-coalition-open-weights-letter**: 270+ signatories, Amazon in, Anthropic out; stable
- **kimi-k3-gpu-crunch-subscription-pause**: Moonshot G-round $50B; HK IPO filing Sept 30 target; fund transfer Aug 27 deadline; ARR $300M
- **nvidia-h200-china-trivial**: $295B datacenter plan, 80% domestic mandate; Ascend 950DT live; NVIDIA zero China revenue
- **eu-ai-act-august-enforcement**: GPAI enforcement active since Aug 2; up to €35M/7% global turnover; AI Omnibus extended high-risk timelines to Dec 2027
- **ai-manifesto-war-pacing-frontier**: Three governance frameworks live; no new developments
- **chinese-military-pla-distillation-reuters**: NUDT UAV drone targeting; PLA Unit 96941; no new reports
- **xiaomi-mimo-frontier-entry**: MiMo-V2.5-Pro 42 AA Index; no update
- **distillation-scale-data**: Alibaba 28.8M exchanges (largest); NSTM-4; no enforcement
- **nemotron-3-ultra-us-open-weight**: AA Index 47.7; Korea Q4 2026 Ascend launch on track
- **polymarket-chinese-ai-company**: Resolved July 31 — Alibaba 100%, $1,041,459
- **kimi-k3-weights-open-source**: 2.8T, custom Kimi K3 License, DoorDash/Coinbase/Cursor/Databricks adopted
- **us-moonshot-distillation-sanctions**: Treasury threat July 22 still unexecuted; Moonshot denied
- **openai-hf-cyberattack-glm-defense**: GPT-5.6 Sol sandbox escape; GLM-5.2 forensics; no new reports
- **deepseek-zhipu-self-chip-development**: DeepSeek inference chip early stage; CUDA→CANN complete; Z.AI 1GW DC operational
- **open-weights-decelerationist-accelerationist**: Lambert thesis playing out; Amazon/Anthropic paradox unchanged
- **openeurollm-european-sovereign**: Fall 2026 target; 10M+ GPU hours; EU AI Act active without EU open-weight competitor
- **mistral-frontier-moe-silent**: Day ~**71** in partner early access; Leanstral 1.5/Medium 3.5/OCR 4 in August but NOT the frontier MoE
- **double-curtain-us-china-export-controls**: MOFCOM AI controls still consultation; TSMC ban still under discussion; Aug 5 drone/entity escalation standing
- **kimi-k3-eda-chip-design**: 48h functional chip; Synopsys/Cadence stock drop; no new reports
- **minimax-m3-pro-2-7t**: Single-source Q3 plan (The Information); MiniMax not confirmed
- **tencent-hy3-295b**: 295B/21B Apache 2.0 (July 6); no update
- **china-mofcom-export-controls-ai**: Tiered AI export controls still in consultation; TSMC ban still under discussion
- **china-domestic-chip-mass-pivot**: $295B plan, 80% mandate, ByteDance $5.6B Ascend commitment; 950DT live
- **jp-deepseek-japanese-cultural-benchmark**: DeepSeek-V4-Flash #1 JamC-QA; methodology saturation finding stands

---

## Cross-Source Patterns

### Pattern 1: The "Ecosystem Over Price" Inflection — Alibaba + DeepSeek Signal in Parallel 🌐 🇨🇳 🇯🇵

**Platforms:** Web (global), Web (China 🇨🇳 — CSDN, Juejin, 36Kr), Web (Japan 🇯🇵 — note.com/kashiwaguchi), HN

Both major Aug 13 announcements share a single strategic logic: build developer lock-in through tooling, monetize via inference rather than model exclusivity.
- **Alibaba (Qwen3.8):** Ships weights, captures ecosystem developers, extracts revenue share from large deployers (>$50M threshold)
- **DeepSeek (Harness):** Ships MIT agent runtime — give away the cockpit, charge for the engine (V4-Pro price +355%)

Chinese tech media 🇨🇳 (CSDN: "同日亮剑") and Japanese analysis 🇯🇵 (kashiwaguchi: "価格戦争から生態系競争へ") independently converged on the same reading: the Chinese AI competition has shifted from price-war to ecosystem-war.

---

### Pattern 2: Post-Training Scaling as the New Chinese Lab Strategy Proof Point 🌐 🇨🇳

**Platforms:** Web (global), Web (China 🇨🇳 — Juejin, Sina Finance, 36Kr)

GLM-5.3's "同基座、纯後训练" (same base, pure post-training) framing resonates widely as methodological validation:
- 50% coding improvement without touching the base model
- Emergent exploit chains that Z.AI did not intend — emergent behavior from post-training scale
- Chinese community treats this as vindication: post-training investment delivers frontier capabilities without trillion-parameter pretraining cost

Pattern confirmation: DeepSeek V4-Pro-0813 also cited "agent-benchmark gains up to 49.9pp" — likely from post-training/RLHF refinement. Two major Chinese labs shipping same-day upgrades driven by post-training is not coincidence.

---

### Pattern 3: The License Arms Race — Open Weights Getting Less Open 🌐 🇯🇵

**Platforms:** Web (global), Web (Japan 🇯🇵 — Elser AI cited in prior pass, now Qiita/CSDN), HN

Three weeks of licensing evolution:
- Kimi K3 (July 27): Custom Kimi K3 License — $20M+ revenue orgs must negotiate
- MiniMax H3 (Aug 3): Geographic exclusions — US/EU/UK/Korea cannot deploy locally
- Qwen3.8-Max (Aug 12): Revenue-share up to 30% for MaaS orgs >$50M — first Chinese lab to "tax deployment"

Each successive release applies more friction to commercial deployment while maintaining "open-weight" branding. Japanese developers 🇯🇵 (Qiita, prior pass) and HN community both flagging: "open weight ≠ Apache 2.0." The Forkast framing — "platform capture" — may become the consensus read.

> "Alibaba is fundamentally altering the economics of artificial intelligence by pioneering a revenue-share model for its upcoming open-weight models" — Forkast News ([link](https://forkast.news/alibaba-pioneers-revenue-share-on-open-weight-models-the-first-chinese-lab-to-tax-deployment/)) 🌐

---

## Per-Platform Tables

### Polymarket 📊
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of August | Alibaba 92.5%, Z.ai 3.8%, Moonshot 3.0% | $518.37K | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ |
| US Gov removes public access to Chinese AI model 2026 | Yes 26% | $36.8K+ | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Best Chinese AI Company end of July [RESOLVED] | Alibaba 100% | $1,041,459 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |
| Second-Best Chinese AI Company end of August | Moonshot 75% | $47.8K | https://polymarket.com/predictions/ai-technology |
| Third-Best Chinese AI Company end of August | Baidu 41% | $21.1K | https://polymarket.com/predictions/ai-technology |
| Best Chinese AI Company end of September | Alibaba 81% | $76.2K | https://polymarket.com/predictions/ai-technology |

### Hacker News 🟢
| Thread | Points | Comments | Notable Quote | URL |
|--------|--------|----------|---------------|-----|
| Qwen3.8-2.4T (open weights) | 704 | 170 | "licensing restricts commercial use above $50M and limits productivity agents" — NitpickLawyer | https://news.ycombinator.com/item?id=49273478 |
| DeepSeek Harness developer preview | 678 | 276 | "full visibility into system prompts, reasoning, tool calls and results" — SwellJoe | https://news.ycombinator.com/item?id=49285244 |
| Qwen3.8 Max ranked #1 by agentic index | ~200 | — | Community reaction to BenchLM #1 | https://news.ycombinator.com/item?id=49200652 |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | ExplainX | https://www.explainx.ai/blog/qwen3-8-max-open-weights-live-hugging-face-august-2026 | Weights live Aug 12; specs; license |
| 🌐 | Forkast | https://forkast.news/open-weights-closed-revenue-ceiling-alibabas-qwen-3-8-license-is-a-platform-play-not-a-gift/ | "Platform capture play"; +7% HK stock |
| 🌐 | Forkast | https://forkast.news/alibaba-pioneers-revenue-share-on-open-weight-models-the-first-chinese-lab-to-tax-deployment/ | First Chinese lab to tax deployment |
| 🌐 | HuggingFace | https://huggingface.co/Qwen/Qwen3.8-2.4T-A95B/blob/main/LICENSE | Official license text |
| 🌐 | Open Source For You | https://www.opensourceforu.com/2026/08/alibaba-to-introduce-revenuesharing/ | Revenue-share mechanism |
| 🌐 | Neomanex | https://neomanex.com/news/qwen38-max-open-weights-countdown-aug-2026 | 27B still missing |
| 🌐 | BenchLM | https://benchlm.ai/models/qwen3-8-max | Score 79.7 (from 60.9 preliminary) |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Full open-weight rankings |
| 🌐 | DeepSeek API Docs | https://api-docs.deepseek.com/news/news260813/ | Official V4-Pro-0813 GA |
| 🌐 | TechTimes | https://www.techtimes.com/articles/324241/20260813/deepseek-v4-pro-0813-goes-ga-benchmark-claims-await-independent-proof.htm | GA; benchmark claims pending verification |
| 🌐 | VentureBeat | https://venturebeat.com/technology/deepseek-harness-launches-as-open-source-rival-to-claude-code-alongside-v4-pro-on-api-with-higher-prices | Harness + price hike full story |
| 🌐 | The Decoder | https://the-decoder.com/deepseek-launches-an-improved-v4-pro-model-raises-api-prices-and-makes-its-agent-software-open-source/ | Comprehensive Aug 13 |
| 🌐 | Pasquale Pillitteri | https://pasqualepillitteri.it/en/news/11027/deepseek-harness-mit-claude-code-rival | MIT; 64K+ stars |
| 🌐 | QZ | https://qz.com/deepseek-api-price-increase-v4-peak-off-peak-081326 | Price table; effective Aug 16 |
| 🌐 | Investing.com | https://www.investing.com/news/stock-market-news/deepseek-to-raise-api-prices-up-to-1100-starting-monday-93CH-4857804 | Aug 16 date |
| 🌐 | The Next Web | https://thenextweb.com/news/deepseek-price-increase-harness-claude-code-rival-v4-pro | "Razor-and-blades" strategic read |
| 🌐 | Byteiota | https://byteiota.com/deepseek-harness-v01-open-source-agent/ | Plugin breakdown |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/deepseek-harness-open-source-developer-preview/ | Developer preview; MIT |
| 🌐 | Caixin | https://www.caixinglobal.com/2026-08-14/deepseek-launches-v4-pro-and-raises-api-prices-by-as-much-as-1100-102473919.html | 1,100% confirmed; Chinese media |
| 🌐 | Pandaily | https://pandaily.com/deepseek-harness-hands-on-four-modes-model-plus-harness-equals-agent-aug2026 | Four work modes; "model + harness = agent" |
| 🌐 | Unite.AI | https://www.unite.ai/z-ai-launches-glm-5-3-with-frontier-coding-and-a-cyber-capability-that-outgrew-its-training/ | Best GLM-5.3 comprehensive coverage |
| 🌐 | TechTimes | https://www.techtimes.com/articles/324426/20260814/glm-53-post-training-produced-exploit-chains-zai-never-planned-finds-1097-critical-bugs.htm | Emergent exploit chains; 1,097 bugs |
| 🌐 | Byteiota | https://byteiota.com/glm-53-open-weight-coding-emergent-cyber/ | Coding SOTA; cyber risk framing |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/14/z-ai-ships-glm-5-3-without-retraining-the-base-model-better-at-complex-coding-and-long-horizon-tasks/ | Post-training-only approach |
| 🌐 | OfficeChai | https://officechai.com/ai/z-ai-releases-glm-5-3-beats-fable-5-and-gpt-5-6-sol-on-cyberbench/ | CyberGym SOTA claim |
| 🌐 | BigGo Finance | https://finance.biggo.com/news/0b571a42-9531-433c-b81b-c8468d173989 | Weights in 2 weeks; 50% jump |
| 🌐 | Air Release Tracker | https://aireleasetracker.com/model/zai/glm-5.3 | Full spec sheet |
| 🌐 | Explainx | https://explainx.ai/blog/glm-5-3-launch-cyber-defense-benchmarks-august-2026 | All benchmarks |
| 🌐 | CryptoSlate | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | Polymarket odds Aug 14 |
| 🌐 | Releasebot Mistral | https://releasebot.io/updates/mistral | Mistral: Leanstral 1.5, Medium 3.5, OCR 4; no frontier MoE |
| 🌐 | HuaweiCentral | https://www.huaweicentral.com/huawei-confirms-ascend-950dt-ai-chip-to-debut-in-august/ | 950DT confirmed August |
| 🌐 | HackerNoon | https://hackernoon.com/ai-geopolitics-is-moving-from-capacity-accumulation-to-control-over-the-conditions-of-deployment | Geopolitics analysis |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | China open-source problem |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | note.com (kashiwaguchi) | https://note.com/kashiwaguchi/n/nd08fded15810 | Alibaba+DeepSeek same-day = "price war → ecosystem competition" |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese models at 1/10 GPT-4o cost; enterprise guide |
| 🇯🇵 | Qiita (sasgawy) | https://qiita.com/sasgawy/items/6f657e19f1a8e55b187f | 2026 open LLM architecture; Qwen3.8, Kimi K3 attention patterns |
| 🇯🇵 | note.com (npaka) | https://note.com/npaka/n/n1d08ec975c9f | Kimi K3/Qwen3.8-Max/GLM-5.2/V4-Flash comparison; hardware requirements |
| 🇯🇵 | note.com (kagawatomo) | https://note.com/kagawatomo/n/n14e4a4c5d08a | Five-model comparison; shift to "task completion duration" metric |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | K3/Qwen3.8-Max/V4-Pro sparsity + scaling law analysis |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Juejin | https://juejin.cn/post/7673696068215439412 | GLM-5.3 tech deep-dive; "同基座、纯后训练" |
| 🇨🇳 | Juejin | https://juejin.cn/post/7673390412729614390 | DeepSeek Harness tutorial (20K chars) |
| 🇨🇳 | Juejin | https://juejin.cn/post/7673506180661428259 | Harness installation guide |
| 🇨🇳 | Juejin | https://juejin.cn/post/7661958590957469731 | 14 vendors, 30+ models panorama |
| 🇨🇳 | Juejin | https://juejin.cn/post/7671500221185261631 | Unified OpenAI-compat API for Chinese models |
| 🇨🇳 | 36Kr | https://www.36kr.com/p/3938994639617159 | GLM-5.3 "魔改" DeepSeek Harness |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/digi/2026-08-14/doc-ininhhrs2630952.shtml | "编程能力最强开源模型" — GLM-5.3 self-framing |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/jjxw/2026-08-14/doc-ininhhrs2643963.shtml | GLM-5.3 "接近Fable 5" |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/L4A5U598051180F7.html | GLM-5.3 same-day coverage |
| 🇨🇳 | CSDN | https://blog.csdn.net/weixin_61823230/article/details/163474659 | "国产开源双爆"; dev choice guide; license warning |
| 🇨🇳 | CSDN DevPress | https://devpress.csdn.net/v1/article/detail/162078850 | Mid-2026 open-source ecosystem |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2038566761612710043 | Mid-year report: DeepSeek/Qwen/GLM who truly leads |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2067583186352215220 | Qwen3.8 vs V4-Flash lightweight comparison |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2048464721083470807 | Full ecosystem panorama: Kimi K2.6/GLM/Qwen/DeepSeek |

---

## Stats Block

```
├─ 🟠 Reddit: excluded per spec
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 3 threads │ ~1,582 combined points │ 446+ comments
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts │ source health OK; no on-topic posts indexed
├─ 📊 Polymarket: 6 markets (5 active, 1 resolved) │ $518K+ total volume
├─ 🌐 Web: 70+ pages │ 🇯🇵 6 │ 🇨🇳 14
└─ 🗣️ Top voices: tianyicui (DeepSeek/Harness author), SwellJoe (HN/traceability), NitpickLawyer (HN/license), Forkast editorial (Qwen license analysis), kashiwaguchi (note.com/JP ecosystem analysis)
```

---

## Out of Scope but Notable

- **GLM-5.3 emergent cybersecurity capability**: The exploit-chain reasoning Z.AI did not intentionally train — producing multi-stage attack plans and finding 1,097 critical bugs across open-source projects — is a safety/dual-use story that likely belongs in a `security-ai-risk` or `agent-harnesses` topic. An open-weight model with this capability going fully public in ~2 weeks warrants tracking.

- **DeepSeek Harness full execution traceability**: The append-only log of system prompts + reasoning + tool calls is a meaningful trust/observability differentiator vs. Western closed-API agents. This belongs in `agent-harnesses` and potentially `enterprise-ai-adoption` topics.

- **Qwen3.8-Max autonomous development claims** (note.com/npaka): "10日以上にわたって自律的に開発を続ける実験が可能" (can perform autonomous development for 10+ days) — a long-horizon agentic capability claim that intersects `agent-harnesses`.

---

## Data Gaps

- **Qwen3.8-27B**: Not released as of Aug 14; ModelScope countdown targets Aug 15 — monitor for weights drop
- **GLM-5.3 independent benchmarks**: All scores are Z.AI's own; independent verification pending (same as Qwen3.8-Max 87.3% SWE-bench situation)
- **DeepSeek V4-Pro-0813 benchmark verification**: Vendor-reported 49.9pp gains need independent confirmation
- **GLM-5.5**: Still no announcement; August window closing; September now primary window
- **Mistral frontier MoE**: Day ~71 in partner early access; zero public benchmarks; monitoring continues
- **Reddit blocked**: r/LocalLLaMA developer reaction to Qwen3.8 license (revenue-share) would be highly relevant
- **Bluesky**: Health OK; 0 posts indexed
- **Zhihu 403 blocks**: Several Zhihu articles behind authentication walls (snippets only)
- **GLM-5.3 BenchLM**: Not yet scored (launched today); will appear in next BenchLM update
- **Estimated coverage:** ~78% — strong web + JP/CN hub snapshot; gaps from Reddit (excluded), X (excluded), YouTube (not retrieved), some Zhihu auth blocks; GLM-5.3 too new for independent benchmark confirmation

---

## Key Quotes

> "Open Weights, Closed Revenue Ceiling: Alibaba's Qwen 3.8 License Is a Platform Play, Not a Gift" — Forkast News editorial headline ([link](https://forkast.news/open-weights-closed-revenue-ceiling-alibabas-qwen-3-8-license-is-a-platform-play-not-a-gift/)) 🌐

> "アリババとDeepSeekが同日に大型発表——中国AI開源競争が新フェーズへ" ("Alibaba and DeepSeek both made major announcements on the same day — China's AI open-source competition enters a new phase") — kashiwaguchi on note.com ([link](https://note.com/kashiwaguchi/n/nd08fded15810)) 🇯🇵

> "刚刚，GLM-5.3来了，拿下多个开源SOTA，我用它'魔改'DeepSeek Harness" ("Just now, GLM-5.3 is here, claimed multiple open-source SOTAs, I used it to 'mod' DeepSeek Harness") — 36Kr headline ([link](https://www.36kr.com/p/3938994639617159)) 🇨🇳

> "国産開源双爆：Qwen3.8-Max 与 DeepSeek V4-Flash 同日亮剑" ("Dual domestic open-source explosion: Qwen3.8-Max and DeepSeek V4-Flash draw swords on the same day") — CSDN headline ([link](https://blog.csdn.net/weixin_61823230/article/details/163474659)) 🇨🇳

> "GLM-5.3 develops exploit-chain reasoning Z.ai says its post-training produced without intent, finding 1,097 critical vulnerabilities in Linux, WebKit, and FreeBSD" — TechTimes ([link](https://www.techtimes.com/articles/324426/20260814/glm-53-post-training-produced-exploit-chains-zai-never-planned-finds-1097-critical-bugs.htm)) 🌐

> "Give away the runtime, charge for the inference — classic razor-and-blades, except the blades just got expensive" — TNW on DeepSeek Harness + API price hike ([link](https://thenextweb.com/news/deepseek-price-increase-harness-claude-code-rival-v4-pro)) 🌐

> "能力提升主要来自于后训练的Scaling" ("Capability improvements stem primarily from post-training scaling") — Z.AI on GLM-5.3 development approach ([link](https://www.36kr.com/p/3938994639617159)) 🇨🇳

> "full visibility into system prompts, reasoning, tool calls and results" — SwellJoe on DeepSeek Harness execution traceability (HN, [link](https://news.ycombinator.com/item?id=49285244)) 🌐
