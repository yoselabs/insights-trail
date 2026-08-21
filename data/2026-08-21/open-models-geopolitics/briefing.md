# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-21
**Query type:** GENERAL
**Sources:** Web (global 🌐), Web (Japan 🇯🇵), Web (China 🇨🇳), Polymarket, Hacker News

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 65+ pages | — | 🌐 WebSearch × 15 query passes + WebFetch |
| Web (Japan) | 8 pages | — | 🇯🇵 Qiita ×2, Zenn ×2, ITMedia/Atmarkit ×3, AI革命 ×1 |
| Web (China) | 15 pages | — | 🇨🇳 Zhihu ×9, Juejin ×3, CSDN ×2, Tencent News ×1 |
| Polymarket | 2 active markets | $755.44K volume | Best Chinese AI Aug at 94.4% Alibaba; ban market at 26% |
| Hacker News | 1 thread | 165+ points | Ornith-1.5 self-improving open-weight |
| Bluesky | 0 posts | — | 🦋 Source health OK; no on-topic posts indexed |
| Reddit | — | — | Excluded per spec |
| X/Twitter | — | — | Excluded per spec |
| YouTube | 0 | — | Not retrieved in free-tool pass |

---

## Synthesized Findings

### 1. [new] dots3-note Preview (Rednote/Xiaohongshu, Aug 14): IMO 42/42 Series Now Open-Weight 🌐 🇨🇳

**Claim:** Xiaohongshu (Rednote) open-sourced the first model in its dots3 series — dots3-note Preview — on Aug 14, the same family as the model that scored 42/42 at IMO 2026; 280B MoE / 16B active, Apache 2.0, 512K context.

- **Architecture:** 280B total / 16B active MoE; 46 attention layers (13 sparse DeepSeek-style + 33 sliding-window)
- **License:** Apache 2.0; available on Hugging Face at dots-studio/dots3-note-prev
- **Context:** 512K tokens; multimodal text + vision + audio
- **TEMPO RL:** new reinforcement learning method for long-horizon agent tasks (tasks spanning tens of hours)
- **IMO context:** dots-note-3.0 scored 42/42 at IMO 2026 (July 21) using a bespoke harness branch; published checkpoint is lighter — same series, not same harness
- **BenchLM:** open-source #2 at 68.8 (Aug 21); below Qwen3.8 Max at 79 but above all other non-Qwen open weights
- **Significance:** first open-weight model from a major consumer social platform; Rednote has 300M+ users; introduces TEMPO as novel agent RL technique
- **Chinese community** 🇨🇳: Zhihu article "小红书开源dots3-note Preview：280B总参数激活16B，512K上下文的三模态长程Agent模型"; IMO achievement thread "如何评价小红书dots-note 3.0在IMO 2026获得满分金牌？"

**Sources:** https://eu.36kr.com/en/p/3938759517896072 | https://datanorth.ai/news/dots-studio-releases-dots3-note-preview | https://huggingface.co/dots-studio/dots3-note-prev | https://github.com/studio-dots-ai/dots3-note-prev | https://openrouter.ai/dots-studio/dots-3-note-preview | https://www.remio.ai/post/rednote-opens-dots3-note-preview-but-its-agent-claims-still-need-proof | https://zhuanlan.zhihu.com/p/2072687859413394969 | https://zhuanlan.zhihu.com/p/2063226861556180872 | https://www.scmp.com/tech/article/3361482/worlds-first-ai-model-earn-perfect-score-maths-olympiad-comes-chinas-rednote

---

### 2. [new] Ornith-1.5 (Aug 19-20): Self-Improving Open-Weight; Claims Rival Opus 4.8 🌐

**Claim:** Ornith AI released Ornith-1.5 on Aug 19-20 — MIT, 397B MoE derived from Qwen3.5 base, with a closed self-improvement training loop; claims Terminal-Bench 86.1 (vs Claude Opus 4.8's 85.0); BenchLM open-source #3 at 68.5.

- **Sizes:** 397B MoE (flagship), 35B MoE, 9B dense
- **License:** MIT across all sizes
- **Base:** derives from Qwen3.5-397B via post-training (not from-scratch pretraining)
- **Self-improvement loop:** three stages — task generation (model proposes capability-gap tasks), scaffold generation (builds task-specific harness), solution rollout (GRPO backprop across all three)
- **Benchmarks (self-reported):** 397B: Terminal-Bench 2.1: 86.1 (vs Opus 4.8: 85.0), DeepSWE: 56.0; 35B: Terminal-Bench: 74.8
- **Benchmark caveat:** numbers are across five vendor runs; one independent community test: 35B trailed Qwen3.8-27B on DeepSWE (22.0 vs 42.2) — significant gap with vendor claims
- **HN:** top story Aug 20, 165+ pts, 58+ comments (https://news.ycombinator.com/item?id=49362401)
- **Deployment:** 8× H200 141GB for 397B; 9B runs on consumer devices including iOS/Android
- **Organization:** Ornith AI; attributed to researcher Jiwei Li (unconfirmed)
- **Note:** non-Chinese open-weight lab; new category of self-improvement architecture

**Sources:** https://news.ycombinator.com/item?id=49362401 | https://datanorth.ai/news/ornith-releases-ornith-1-5 | https://explainx.ai/blog/ornith-1-5-self-improving-open-weight-model-august-2026 | https://saascity.io/blog/ornith-1-5-self-improving-open-source-llm-2026 | https://huggingface.co/ornith-ai/Ornith-1.5-397B | https://startupfortune.com/ornith-15-is-a-free-open-source-model-that-claims-to-rival-claude-opus-48/

---

### 3. [update] BenchLM Aug 21: Qwen3.8 Max Eases to 79; dots3-note and Ornith Enter Top-3 Open-Weight 🌐

**New fact:** BenchLM open-source leaderboard (Aug 21): Qwen3.8 Max scores 79 (down from 79.9 on Aug 17); dots3-note Preview debuts at #2 (68.8) and Ornith-1.5-397B at #3 (68.5) — both new entrants; MiniMax M3 slides to #4 (68.3). Kimi K3 now #1 Chinese model (proprietary) at 80.2 — above Qwen3.8 Max.

| Rank | Model | Org | Score (Aug 21) | vs Aug 17 |
|------|-------|-----|----------------|-----------|
| 1 | Qwen3.8 Max | Alibaba | **79** | ↓ from 79.9 |
| 2 | dots3-note Preview | Dots Studio/Rednote | **68.8** | **new** |
| 3 | Ornith-1.5-397B | Ornith AI | **68.5** | **new** |
| 4 | MiniMax M3 | MiniMax | 68.3 | ↓ from 68.7 |
| 5 | Hy3 | Tencent | 67.9 | ↓ from 68.0 |

Chinese models (proprietary + open): Kimi K3 at 80.2 is Chinese #1 (above Qwen3.8 Max). GLM-5.3 still not scored (open weights pending ~Aug 28).

**Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/best/chinese-models | https://benchlm.ai/models/kimi-k3

---

### 4. [update] China's Domestic AI Chip Share Approaching 90% (Tencent News, Aug 19) 🇨🇳 🌐

**New fact:** TrendForce forecast (reported Aug 19): domestic AI chip solutions to capture ~90% of China's high-end market in 2026; Nvidia down to ~8% China share (from 66% in 2024, 40% in 2025). HBM bottleneck limits Huawei production to <300K chips/year despite die capacity >1M.

- **Nvidia trajectory:** 66% (2024) → 40% (2025) → ~8% (2026)
- **Huawei Ascend:** 81.2M units shipped in 2025 (leading domestic); 75M 950PR units planned for 2026
- **HBM constraint:** Huawei's foundry SMIC can produce >1M die/year but domestic HBM caps shippable output at <300K without foreign HBM stockpiles
- **AI companies building own chips:** Alibaba, Baidu, Tencent all in self-developed ASIC programs (Tencent News, July 21)
- Sina: domestic substitution rate rose 10% (2021) → 40-41% (2025); long-range target 70-86% by 2030
- Tencent headline: "大逆转！国产AI芯片份额逼近90%：英伟达AMD仅剩一成，还有个难题" — "one remaining problem" = HBM

**Sources:** https://news.qq.com/rain/a/20260819A068AV00 | https://k.sina.cn/article_7880068204_1d5b04c6c06801aogo.html | https://www.sina.cn/news/detail/5324989188541573.html | https://news.qq.com/rain/a/20260721A030HS00 | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition

---

### 5. [update] Moonshot Denies August IPO Filing; $50B Round Still Underway 🌐

**New fact:** Moonshot AI officially called the August IPO filing report "inaccurate." The Standard (HK) reported this denial after International Financing Review claimed Moonshot would file "as early as August." No alternative timeline given.

- **What changed:** August-filing timeline rejected; year-end or Q1 2027 window remains open
- **Unchanged:** $50B pre-money valuation target; ARR $300M (June); HK IPO intent still present
- **Context:** Kimi K3 BenchLM Chinese #1 at 80.2 supports Moonshot's premium narrative
- **Prior:** prior briefing (Aug 18) reported fund transfer deadline Aug 27 and Sept 30 filing target — the denial contradicts the Sept 30 filing claim if August is already denied

**Sources:** https://www.thestandard.com.hk/finance/article/338896/Moonshot-AI-denies-plans-to-file-Hong-Kong-IPO-in-August | https://www.scmp.com/tech/big-tech/article/3363026/chinas-moonshot-ai-aims-us50b-round-year-end-hong-kong-ipo-targeted-sources | https://technode.com/2026/07/22/moonshot-ai-reportedly-plans-final-pre-ipo-round-at-50-billion-valuation/ | https://finance.yahoo.com/technology/ai/articles/moonshot-ai-eyes-50-billion-151346997.html

---

### 6. [update] Polymarket Aug 21: Alibaba 94.4% (↓), Volume $755.44K (↑), Xiaomi New Entry 🌐

**New fact:** Alibaba odds down to **94.4%** (from 96.4% Aug 18); market volume up to **$755.44K** (from $610.89K); Xiaomi newly appears at 0.6%; Z.ai dropped to 0.9%, DeepSeek to 0.4%.

| Company | Probability (Aug 21) | Volume | Shift vs. Aug 18 |
|---------|----------------------|--------|-----------------|
| Alibaba | 94.4% | $160.66K | ↓ from 96.4% |
| Moonshot | 1.0% | $55.59K | ↓ from 1.3% |
| Z.ai | 0.9% | $104.91K | ↓ from 2.0% |
| Tencent | 0.6% | $33.46K | new |
| Xiaomi | 0.6% | $35.33K | new |
| Baidu | 0.5% | $77.78K | new |
| MiniMax | 0.4% | $65.98K | new |
| DeepSeek | 0.4% | $130.22K | ↓ from 0.6% |
| Bytedance | 0.2% | $43.03K | new |

Resolves Aug 31 on arena.ai leaderboard. US removes Chinese AI model market: 26% Yes — unchanged.

**Sources:** https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223

---

### 7. [update] DeepSeek Harness: 144K Stars, 1,080 Plugins (Aug 21) 🌐 🇨🇳

**New fact:** Stars grew from 141K (Aug 17) to **144K+** (Aug 21); forks 14.7K+; plugin count to 1,080+ in main storefront; Oh-My-DSH community directory now 1,521 repos / 301,295 combined ecosystem stars.

- Peak pricing (effective Aug 16) stands: $3.96/MTok output at peak hours; off-peak $1.98/MTok
- Community plugin growth remains sustained; no major plugin ecosystem fragmentation reported

**Sources:** https://github.com/deepseek-ai/deepseek-harness | https://ai-engineering-trend.medium.com/community-built-plugin-store-for-deepseek-hits-1-080-plugins-on-github-25c7c7977e53 | https://github.com/Dominic789654/awesome-deepseek-harness | https://www.ghacks.net/2026/08/17/deepseek-releases-v4-pro-with-higher-benchmarks-open-source-tooling-and-upcoming-price-increases/

---

**Still true** (ongoing threads — no new facts since Aug 18):

- **qwen3-8-27b-apache-multimodal**: Apache 2.0; 27B dense multimodal; 262K context; 3M+ downloads; Agentic Index 51; overthinking default remains issue
- **mistral-glm52-eu-sovereign-hosting**: GLM-5.2 on EU Regional Endpoints; 1GW coalition; Priority Tier 99.5% SLA
- **agents-a1-internsciense-new-entrant**: InternScience Agents-A1 35B MoE; BenchLM #10 at 60.8
- **glm-5-3-post-training-emergent-cyber**: API live for Coding Plan; open weights still pending ~Aug 28; CyberGym 84.5%, ExploitBench 54.4%; Greg Brockman: "likely to significantly accelerate the threat landscape"; community controversy over "open-source" label when weights not yet released
- **polymarket-us-chinese-model-ban**: 26% Yes; $15.1K volume; unchanged
- **qwen-3-8-max-open-weights-pending**: Qwen3.8-Max BenchLM #1 open-weight at 79 (slightly eased)
- **deepseek-chip-ascend-950dt**: Ascend 950DT cloud-live August; full commercial Q4 2026; DeepSeek inference chip early stage; CUDA→CANN complete
- **glm-5-5-expected-august**: GLM-5.5 window shifts to Sept–Oct; GLM-5.3 was Aug release
- **xi-waic-open-source-mandate**: Dual-track (Apache 2.0 27B + Max revenue-share) confirms private-sector hedging; dots3-note Apache 2.0 extends the pattern
- **glm-5-2-benchmarks-huawei-trained**: Superseded by GLM-5.3; remains on Mistral EU platform at €1.19/M
- **databricks-enterprise-glm-migration**: GLM Coding Plan auto-upgraded to 5.3; no new enterprise adoption news
- **inkling-small-thinking-machines**: BenchLM #7 at 65.5; Qwen3.8 Max #1 overall
- **mistral-shieldstral-safety-classifier**: 3B Apache 2.0 safety classifier; NOT frontier MoE
- **minimax-h3-geo-license-restriction**: US/EU/UK/Korea geo-exclusions stand; Hollywood litigation unchanged
- **deepseek-autonomous-cyberattack-hermes**: Knaithe/KnYuan no new reports
- **industry-coalition-open-weights-letter**: 270+ signatories; all major US labs except Anthropic
- **kimi-k3-weights-open-source**: 2.8T custom license; DoorDash, Cursor, Databricks, Coinbase
- **us-moonshot-distillation-sanctions**: Treasury threat July 22 still unexecuted
- **openai-hf-cyberattack-glm-defense**: No new reports
- **deepseek-zhipu-self-chip-development**: DeepSeek inference chip early stage; CUDA→CANN complete
- **open-weights-decelerationist-accelerationist**: OpenAI/Google joined open-weights letter; accelerationist camp stronger
- **openeurollm-european-sovereign**: Fall 2026 target; 8B model in progress
- **mistral-frontier-moe-silent**: Day ~88 in partner early access; no public benchmarks
- **double-curtain-us-china-export-controls**: MOFCOM AI controls still consultation; US BIS extraterritorial active; MOFCOM sanctioned US firms Aug 6 (not AI-specific)
- **kimi-k3-eda-chip-design**: 48h functional chip; Synopsys/Cadence impact; no update
- **minimax-m3-pro-2-7t**: Q3 single-source; MiniMax unconfirmed; Q3 window closing
- **tencent-hy3-295b**: BenchLM open-source #5 at 67.9 (↓ from 68.0)
- **china-mofcom-export-controls-ai**: Still consultation; no regulation enacted
- **chinese-models-global-share-30pct**: ~30% global downloads; ~61% OpenRouter token volume; dots3-note and Ornith now join the global top-5 open-weight
- **ai-manifesto-war-pacing-frontier**: Three governance frameworks live; Anthropic sole holdout on open-weights letter
- **chinese-military-pla-distillation-reuters**: NUDT UAV drone targeting; no new reports
- **xiaomi-mimo-frontier-entry**: MiMo-V2.5-Pro; BenchLM Chinese #4 at 68.9
- **distillation-scale-data**: Alibaba 28.8M exchanges; NSTM-4; no enforcement
- **nemotron-3-ultra-us-open-weight**: Nvidia Nemotron 3 Ultra; Korea Q4 Ascend launch on track
- **polymarket-chinese-ai-company**: Resolved July 31 — Alibaba 100%, $1,041,459
- **eu-ai-act-august-enforcement**: GPAI enforcement active since Aug 2; open-source exempt from most requirements unless systemic risk; all Chinese providers subject
- **jp-deepseek-japanese-cultural-benchmark**: Japanese enterprise guidance on Chinese model adoption (Zenn/kent_kamome updated practical guide)

---

## Cross-Source Patterns

### Pattern 1: August 2026 = "疯狂八月" — Chinese Labs Dense-Release Cycle Accelerating 🌐 🇨🇳

**Platforms:** Zhihu, Juejin, CSDN, Web (global)

Chinese community coined "疯狂八月" (crazy August) for the density of Aug 1-21 releases: Qwen3.8-Max (Aug 3), Qwen3.8-27B (Aug 14), GLM-5.2 Turbo (Aug 17), GLM-5.3 (Aug 14), DeepSeek-V4-Pro GA (Aug 13), dots3-note Preview (Aug 14). Non-Chinese labs responded: Ornith-1.5 (Aug 19-20). This matches the Juejin "triple-leap" framing (三重跃迁): parameter efficiency → ultra-long context → autonomous agents.

> "三重跃迁：参数效率 + 超长上下文 + 自主智能体" (Triple leap: parameter efficiency + ultra-long context + autonomous agents) — Juejin ([link](https://juejin.cn/post/7669935311557083163)) 🇨🇳

---

### Pattern 2: Open-Source Authenticity Dispute — Weights Held, "Open-Source" Label Contested 🌐 🇨🇳

**Platforms:** Zhihu, AIWeekly, BenchLM, ExplainX

GLM-5.3 released Aug 14 without weights (API only); Z.ai calls it open-source and it appears on BenchLM "pending" status. Chinese community erupted: "GLM-5.3 刚发布，社区就吵翻了：代码能力确实强了，但它真配叫「最强开源模型」吗？" — questioning whether the label applies before weights ship. AIWeekly: "Z.ai ships GLM-5.3, holds open weights for cyber safety review." OpenAI's Greg Brockman added external pressure: "likely to significantly accelerate the threat landscape." This pattern of release-without-weights for safety review may become standard for cyber-capable models.

---

### Pattern 3: Consumer Tech Platforms Entering Frontier AI Openweight Space 🌐 🇨🇳

**Platforms:** Web (global), Zhihu, 36Kr

Xiaohongshu/Rednote (300M+ users, consumer social platform) releasing dots3-note Preview (Apache 2.0, BenchLM #2 open-weight) represents a new category of frontier-AI entrant. Unlike Alibaba, DeepSeek, or Z.ai, Rednote's core business is consumer content, not enterprise cloud. This extends to Xiaomi (MiMo-V2.5-Pro, BenchLM Chinese #4). Consumer electronics and social platforms building frontier open-weight models — not just cloud labs — is a signal that the frontier is commoditizing.

---

### Pattern 4: China Domestic Chip Market Share Forecast Jumps — 52% → 90% 🌐 🇨🇳 🇯🇵

**Platforms:** Tencent News, Sina News, CFR, CSIS, ValueAddVC

Tencent News (Aug 19): "大逆转！国产AI芯片份额逼近90%" — a sharp jump from the 52% figure in prior briefings. TrendForce is now projecting 90% domestic share by end-2026, with Nvidia at ~8%. The bottleneck is now named clearly: HBM production (<300K chips/year limit) rather than die capacity. Japan coverage (Zenn/kent_kamome): notes GLM-5 was trained on 100K Huawei Ascend chips, confirming the domestic hardware pathway at scale.

---

## Per-Platform Tables

### Polymarket 📊
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of August | Alibaba 94.4%, Moonshot 1.0%, Z.ai 0.9%, Xiaomi 0.6%, Tencent 0.6%, DeepSeek 0.4% | $755.44K | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ |
| US Gov removes public access to Chinese AI model 2026 | Yes 26% | $15.1K | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Best Chinese AI Company end of July [RESOLVED] | Alibaba 100% | $1,041,459 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |

### Hacker News 🟢
| Thread | Points | Comments | Notable Quote | URL |
|--------|--------|----------|---------------|-----|
| Ornith-1.5: From Self-Scaffolding to Self-Improvement | 165+ | 58+ | Self-improving open-weight; "competitive with Claude Opus 4.8" | https://news.ycombinator.com/item?id=49362401 |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | 36Kr (EN) | https://eu.36kr.com/en/p/3938759517896072 | dots3-note Preview: same series as IMO 42/42 |
| 🌐 | DataNorth AI | https://datanorth.ai/news/dots-studio-releases-dots3-note-preview | dots3-note Preview release |
| 🌐 | Remio | https://www.remio.ai/post/rednote-opens-dots3-note-preview-but-its-agent-claims-still-need-proof | dots3-note: agent claims skeptical analysis |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/dots-note-3-0-leak | IMO 42/42 context |
| 🌐 | HuggingFace | https://huggingface.co/dots-studio/dots3-note-prev | Model card (Apache 2.0) |
| 🌐 | GitHub | https://github.com/studio-dots-ai/dots3-note-prev | Code repo |
| 🌐 | SCMP | https://www.scmp.com/tech/article/3361482/worlds-first-ai-model-earn-perfect-score-maths-olympiad-comes-chinas-rednote | IMO perfect score coverage |
| 🌐 | DataNorth AI | https://datanorth.ai/news/ornith-releases-ornith-1-5 | Ornith-1.5 release |
| 🌐 | ExplainX | https://explainx.ai/blog/ornith-1-5-self-improving-open-weight-model-august-2026 | Technical analysis |
| 🌐 | SaaSCity | https://saascity.io/blog/ornith-1-5-self-improving-open-source-llm-2026 | Self-improvement loop detail |
| 🌐 | HuggingFace | https://huggingface.co/ornith-ai/Ornith-1.5-397B | Model card (MIT) |
| 🌐 | StartupFortune | https://startupfortune.com/ornith-15-is-a-free-open-source-model-that-claims-to-rival-claude-opus-48/ | Benchmark claims |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Aug 21 open-source ranking |
| 🌐 | BenchLM | https://benchlm.ai/best/chinese-models | Aug 21 Chinese models ranking |
| 🌐 | BenchLM | https://benchlm.ai/models/kimi-k3 | Kimi K3 #5 overall (80.16) |
| 🌐 | The Standard HK | https://www.thestandard.com.hk/finance/article/338896/Moonshot-AI-denies-plans-to-file-Hong-Kong-IPO-in-August | Moonshot IPO denial |
| 🌐 | SCMP | https://www.scmp.com/tech/big-tech/article/3363026/chinas-moonshot-ai-aims-us50b-round-year-end-hong-kong-ipo-targeted-sources | Moonshot $50B round |
| 🌐 | TechNode | https://technode.com/2026/07/22/moonshot-ai-reportedly-plans-final-pre-ipo-round-at-50-billion-valuation/ | Moonshot pre-IPO round |
| 🌐 | ValueAddVC | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition | Export controls → Huawei 50-60% market |
| 🌐 | CFR | https://www.cfr.org/articles/chinas-ai-chip-deficit-why-huawei-cant-catch-nvidia-and-us-export-controls-should-remain | Performance gap analysis |
| 🌐 | CSIS | https://www.csis.org/analysis/deepseek-huawei-export-controls-and-future-us-china-ai-race | US-China AI race analysis |
| 🌐 | AIWeekly | https://aiweekly.co/alerts/zai-ships-glm-53-holds-open-weights-for-cyber-safety-review | GLM-5.3 weights held |
| 🌐 | TheNewStack | https://thenewstack.io/openai-open-weight-glm-5-3/ | Brockman: "accelerate threat landscape" |
| 🌐 | ExplainX | https://www.explainx.ai/blog/glm-5-3-launch-cyber-defense-benchmarks-august-2026 | GLM-5.3 cyber benchmarks |
| 🌐 | AirReleaseTracker | https://aireleasetracker.com/model/zai/glm-5.3 | GLM-5.3 weights still pending (Aug 21) |
| 🌐 | GitHub | https://github.com/deepseek-ai/deepseek-harness | 144K stars, 14.7K forks (Aug 21) |
| 🌐 | Medium | https://ai-engineering-trend.medium.com/community-built-plugin-store-for-deepseek-hits-1-080-plugins-on-github-25c7c7977e53 | 1,080 plugins milestone |
| 🌐 | GitHub | https://github.com/Dominic789654/awesome-deepseek-harness | Oh-My-DSH: 301,295 ecosystem stars |
| 🌐 | TechTimes | https://www.techtimes.com/articles/324764/20260817/deepseek-v4-api-prices-quadruple-peak-what-developers-pay-starting-now.htm | V4 peak pricing impact |
| 🌐 | gHacks | https://www.ghacks.net/2026/08/17/deepseek-releases-v4-pro-with-higher-benchmarks-open-source-tooling-and-upcoming-price-increases/ | V4-Pro and Harness summary |
| 🌐 | Taylor Wessing | https://www.taylorwessing.com/en/insights-and-events/insights/2026/08/gpai-obligations-under-the-eu-ai-act | EU AI Act GPAI enforcement Aug 2 |
| 🌐 | Beam.ai | https://beam.ai/agentic-insights/eu-ai-act-enforcement-august-2-2026-gpai-fines | 3% / €15M fines |
| 🌐 | TrendingTopics EU | https://www.trendingtopics.eu/china-weighs-export-controls-on-ai-models-including-open-weight-llms/ | MOFCOM AI weight controls |
| 🌐 | TechTimes | https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm | Download-while-you-can |
| 🌐 | Arnold & Porter | https://www.arnoldporter.com/en/perspectives/advisories/2026/07/china-imposes-export-control-and-government-procurement-restrictions-on-designated-us-companies | MOFCOM US firm sanctions July 2026 |
| 🌐 | BytesEU | https://www.byteseu.com/2254410/ | Geopolitics shifting to deployment control |
| 🌐 | Atlantic Council | https://www.atlanticcouncil.org/dispatches/eight-ways-ai-will-shape-geopolitics-in-2026/ | 8 ways AI shapes geopolitics 2026 |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita (mhamadajp) | https://qiita.com/mhamadajp/items/9e77c8c5d0485cf8d291 | AI 2027 geopolitics comparison; 35% nation AI lock-in predicted |
| 🇯🇵 | ITMedia Aiplus | https://www.itmedia.co.jp/aiplus/article/2508/29/1250829008/ | China AI law: foreign model exclusion as industrial policy |
| 🇯🇵 | Atmarkit/ITMedia | https://atmarkit.itmedia.co.jp/ait/articles/2607/24/news054.html | Kimi K3 controversy reveals AI supply-chain risk |
| 🇯🇵 | Atmarkit/ITMedia | https://atmarkit.itmedia.co.jp/ait/articles/2607/30/news018.html | Kimi K3 99% cost reduction; technology and risk |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/6c1a37ee6e9bcb7ba9d8 | Game theory: China's frontier model nationalization |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/b821f60198fbab0b9900 | China open-weight strategy goals |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Practical Chinese model guide for Japanese developers |
| 🇯🇵 | Zenn (upgradetech) | https://zenn.dev/upgradetech/articles/c129ae0ecd3cd7 | Kimi K3 overview |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese AI 2026 enterprise guide |
| 🇯🇵 | AlphaMatch JP | https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026 | Chinese models redefining AI hegemony |
| 🇯🇵 | AI革命 | https://ai-revolution.co.jp/media/chinese-ai-models-dominance/ | Chinese models 60%+ of OpenRouter; Japan enterprise impact |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2072687859413394969 | dots3-note Preview: "280B总参数激活16B" |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2063226861556180872 | Community evaluation: dots-note 3.0 IMO 42/42 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071644430679938817 | GLM-5.3 controversy: "community erupted" on open-source label |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071635090388555096 | GLM-5.3 technical evaluation |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071624366392186798 | GLM Coding Plan fully live on GLM-5.3 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071592445759042630 | GLM-5.3 official launch thread |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071641273178514485 | GLM-5.3 #1 open-source coding (claim) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071707711306216661 | "大模型的疯狂八月" (crazy August of LLMs) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071688740536374553 | DeepSeek-V4-Pro vs GLM-5.3 vs Kimi K3 comparison |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/670574382 | DataLearner tracker Aug 20 update |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2038566761612710043 | Chinese LLM mid-year report 2026 |
| 🇨🇳 | Juejin | https://juejin.cn/post/7673522589588783158 | GLM-5.3 technical review |
| 🇨🇳 | Juejin | https://juejin.cn/post/7673696068215439412 | GLM Coding Plan live on 5.3 |
| 🇨🇳 | Juejin | https://juejin.cn/post/7669935311557083163 | August 2026 "triple-leap" |
| 🇨🇳 | CSDN | https://blog.csdn.net/aidoudoulong/article/details/163755988 | GLM-5.3: base unchanged, post-training only |
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260819A068AV00 | Domestic chip share approaching 90% (Aug 19) |
| 🇨🇳 | Sina News | https://k.sina.cn/article_7880068204_1d5b04c6c06801aogo.html | Domestic chip share exceeds 52%; export controls forcing self-sufficiency |
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260721A030HS00 | AI companies collectively developing own chips |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2061506070917406934 | "Kimi K3, global open-source #1!" |

---

## Stats Block

```
├─ 🟠 Reddit: excluded per spec
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 1 thread │ 165+ points │ 58+ comments
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts │ source health OK; no on-topic posts indexed
├─ 📊 Polymarket: 2 active markets + 1 resolved │ $755.44K + $15.1K volume
├─ 🌐 Web: 65+ pages │ 🇯🇵 11 │ 🇨🇳 19
└─ 🗣️ Top voices: Ornith AI team (HN), Rednote/Dots Studio editorial, Tencent News tech desk (chip data), Z.ai editorial, Zhihu/sukimaengineer (JP analysis)
```

---

## Out of Scope but Notable

- **Mojo open-source** (Modular, Aug 20): front-page HN story, 400+ pts — Mojo programming language went fully open-source. Fits `developer-tools` or `infra` topic, not this one; notable because it signals a week of broader open-source momentum beyond just models.
  URL: https://www.modular.com/blog/mojo-open-source

- **Ornith-1.5's self-improvement loop (training-time data flywheel)**: the GRPO backprop across task-generation → scaffold → rollout is a potentially new paradigm in open-weight model development — not model capabilities, but the training method. If reproducible, it decouples open-weight progress from dataset curation. Belongs in a `training-methods` or `paradigm-watch` topic. See: https://explainx.ai/blog/ornith-1-5-self-improving-open-weight-model-august-2026

- **Gartner prediction (via Qiita/mhamadajp)**: 35% of nations will be locked into region-specific AI platforms by 2027. This is an enterprise-AI or geopolitics-governance claim worth tracking separately. URL: https://qiita.com/mhamadajp/items/9e77c8c5d0485cf8d291

---

## Data Gaps

- **DuckDuckGo HTML endpoints**: Both JP and ZH query endpoints returned CAPTCHA (same as Aug 18 run); switched to native-language WebSearch — comparable coverage quality
- **GLM-5.3 open weights**: Still not released as of Aug 21 (target ~Aug 28); all benchmarks remain vendor-reported
- **Mistral frontier MoE**: Still in partner early access, day ~88; zero public benchmarks — ongoing silence gap
- **Polymarket ban market**: 26% Yes at $15.1K volume — thin market
- **Bluesky**: Health OK; 0 posts indexed on topic
- **YouTube**: Not retrieved in free-tool pass
- **Trivium China (MOFCOM Aug 6 article)**: 403 blocked — specific US firms sanctioned unknown
- **dots3-note AccessNewsWire press release**: 403 blocked — supplemented via 36Kr and HuggingFace
- **BenchLM GLM-5.3 score**: Pending open weights; not in current rankings
- **DeepSeek Harness production adoption case studies**: Still absent despite 144K stars
- **Estimated coverage:** ~83% — strong on new model releases (dots3-note, Ornith-1.5), chip market data update, Moonshot IPO denial; gaps from YouTube, Reddit, X, GLM-5.3 weights status.

---

## Key Quotes

> "GLM-5.3 刚发布，社区就吵翻了：代码能力确实强了，但它真配叫「最强开源模型」吗？" ("Community erupted in debate: coding ability is indeed stronger, but does it deserve to be called 'the strongest open-source model'?") — Zhihu on GLM-5.3 open-source label controversy ([link](https://zhuanlan.zhihu.com/p/2071644430679938817)) 🇨🇳

> "大逆转！国产AI芯片份额逼近90%：英伟达AMD仅剩一成，还有个难题" ("The Big Reversal! Domestic AI chip share approaches 90%: Nvidia and AMD left with only 10%, and there's still one problem") — Tencent News Aug 19 ([link](https://news.qq.com/rain/a/20260819A068AV00)) 🇨🇳

> "大模型的疯狂八月" ("The Crazy August of Large Models") — Zhihu framing of August 2026 Chinese AI release density ([link](https://zhuanlan.zhihu.com/p/2071707711306216661)) 🇨🇳

> GLM-5.3 is likely to "significantly accelerate the threat landscape" — OpenAI's Greg Brockman on GLM-5.3's ExploitBench capabilities ([link](https://thenewstack.io/openai-open-weight-glm-5-3/)) 🌐

> "三重跃迁：参数效率 + 超長上下文 + 自主智能体" ("Triple leap: parameter efficiency + ultra-long context + autonomous agents") — Juejin on August 2026 Chinese AI milestone ([link](https://juejin.cn/post/7669935311557083163)) 🇨🇳

> "意外と知らない中国AI事情 外資モデル締め出す法制度と、存在感示す中華LLMたち" ("Surprisingly little-known: China's AI scene — how laws shut out foreign models, and how Chinese LLMs are asserting presence") — ITMedia Aiplus headline ([link](https://www.itmedia.co.jp/aiplus/article/2508/29/1250829008/)) 🇯🇵

> "Ornith-1.5: From Self-Scaffolding to Self-Improvement" — Ornith AI team at HN top spot Aug 20: closed self-improvement loop closes training-time data flywheel ([link](https://news.ycombinator.com/item?id=49362401)) 🌐

> "The report is inaccurate" — Moonshot AI denying plans to file Hong Kong IPO in August ([link](https://www.thestandard.com.hk/finance/article/338896/Moonshot-AI-denies-plans-to-file-Hong-Kong-IPO-in-August)) 🌐
