# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-25
**Query type:** GENERAL
**Sources:** Web (global 🌐), Web (Japan 🇯🇵), Web (China 🇨🇳), Polymarket, Hacker News, Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 70+ pages | — | 🌐 WebSearch × 12 query passes + WebFetch |
| Web (Japan) | 11 pages | — | 🇯🇵 note.com ×1, Qiita ×2, Zenn ×1, Hatena ×1, AlphaMatch ×1, ExaWizards ×1, AI革命 ×1, others ×3 |
| Web (China) | 17 pages | — | 🇨🇳 Zhihu ×5, Juejin ×1, Tencent News ×3, CSDN ×2, Sina ×2, Beijing Daily ×2, Yahoo HK ×1, others ×1 |
| Polymarket | 2 active markets + 1 side market | $909.83K volume | Best Chinese AI Aug at 95% Alibaba; ban market 26% |
| Hacker News | 2 threads | points not retrieved (429) | China open-weights strategy; state of open-source AI |
| Bluesky | 0 posts | — | 🦋 Source health OK; no on-topic posts indexed |
| Reddit | — | — | Excluded per spec |
| X/Twitter | — | — | Excluded per spec |
| YouTube | 0 | — | Not retrieved in free-tool pass |

---

## Synthesized Findings

### 1. [new] DeepSeek-V4-Flash-Vision-Exp (Aug 21): Multimodal API, Close to Opus 4.8 on Visual Agents 🌐 🇨🇳

**Claim:** DeepSeek released V4-Flash-Vision-Exp on Aug 21 — API-only (no open weights), 284B/13B active, 1M context, vendor-claims close to Opus 4.8 on multimodal agent benchmarks.

- **Architecture:** sparse MoE, 284B total / 13B active; 1M context; up to 384K output
- **Access:** API-only; no price premium over V4-Flash; images billed at text token rate (~384 tokens/image after resize); compatible with both OpenAI and Anthropic API schemas
- **Benchmarks (vendor-reported):** text parity with V4-Flash; "significant leap" on multimodal agents; "close to Opus 4.8" on visual understanding — no independent verification yet
- **License:** API-only; experimental; not MIT; no open weights announced
- **Context:** DeepSeek adding vision to its Flash line without a weight release — continues the API-only pattern seen for their most recent capabilities; consistent with MOFCOM consultation pressure

**Sources:** https://api-docs.deepseek.com/news/news260821/ | https://explainx.ai/blog/deepseek-v4-flash-vision-exp-multimodal-agent-august-2026 | https://seekingalpha.com/news/4635820-deepseek-says-new-ai-model-v4-flash-vision-exp-comes-close-to-anthropics-opus-48 | https://openrouter.ai/deepseek/deepseek-v4-flash-vision-exp | https://emergent.sh/news/deepseek-v4-flash-vision-exp-officially

---

### 2. [new] Meta Muse Glimmer (Aug 10-11): US Open-Weight Counter to Chinese Dominance 🌐

**Claim:** Meta released Muse Glimmer (30B, Apache 2.0, distilled from Muse Spark) explicitly as a US competitive response to Chinese open-weight AI dominance; Zuckerberg called for lower US barriers on open-source AI to compete with China.

- **Size:** ~30B parameters; 4-bit quantized to <20GB; runs on consumer GPU (24-32GB VRAM)
- **License:** Apache 2.0; distilled from Meta's closed Muse Spark system
- **Capabilities:** agentic orchestration, multi-step tool use, coding, file handling, 100+ languages, image understanding; wins on reasoning and agentic orchestration; trails on computer-use and terminal tasks
- **Geopolitical framing:** Zuckerberg explicitly called for lower US barriers on open-source AI so American developers can compete with Chinese rivals; SCMP headline: "Meta to challenge China's open-weight AI dominance"
- **Also announced:** plans to open-source Muse Spark 1.2 weights
- **Context:** First major US-origin open-weight model explicitly positioned as geopolitical counter; Kyle Chan (Brookings): "Many American users and companies will prefer to build with American models if there's a good open-source version"
- **Analyst take:** Addresses compliance and reputational risks US businesses face from Chinese AI adoption

**Sources:** https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model | https://www.cnbc.com/2026/08/10/meta-muse-glimmer-open-weight-ai.html | https://www.marktechpost.com/2026/08/10/meta-ai-releases-muse-glimmer/ | https://www.scmp.com/tech/big-tech/article/3363638/meta-challenge-chinas-open-weight-ai-dominance-amid-us-regulatory-fears | https://siliconangle.com/2026/08/10/meta-releases-open-source-muse-glimmer-model-30b-parameters/ | https://theaiinsider.tech/2026/08/11/meta-releases-open-weight-muse-glimmer-model-to-power-local-ai-agents-on-consumer-devices/ | https://pureai.com/articles/2026/08/19/meta-returns-to-open-weight-ai-with-muse-glimmer.aspx | https://www.infoq.com/news/2026/08/meta-muse-glimmer/

---

### 3. [update] BenchLM Aug 25: Qwen3.8-27B Jumps to #2 at 72.5; Kimi K3 at 80.3 🌐

**New fact:** Qwen3.8-27B is now separately ranked #2 on the open-source leaderboard at 72.5 (up from below the top tier as a distinct entry; closes the gap to Qwen3.8 Max by less than 10 points). MiniMax M3 rises to #4 at 68.5. Kimi K3 Chinese models #1 at 80.3 (↑ from 80.2). MiMo-V2.5-Pro at 69.1 (↑ from 68.9).

**Open-source top-10 (Aug 25):**

| Rank | Model | Org | Score (Aug 25) | vs Aug 21 |
|------|-------|-----|----------------|-----------|
| 1 | Qwen3.8 Max | Alibaba | 79 | unchanged |
| 2 | Qwen3.8-27B | Alibaba | **72.5** | **new entry** |
| 3 | dots3-note Preview | Dots Studio | 68.8 | unchanged |
| 4 | MiniMax M3 | MiniMax | 68.5 | ↑ from 68.3 |
| 5 | Ornith-1.5-397B | Ornith AI | 68.4 | ↓ from 68.5 |
| 6 | Hy3 | Tencent | 67.9 | unchanged |
| 7 | GLM-5.1 | Z.AI | 66.9 | new position |
| 8 | Inkling | Thinking Machines Lab | 66.8 | ↓ from 67.0 |
| 9 | GLM-5 | Z.AI | 65.5 | — |
| 10 | Inkling-Small | Thinking Machines Lab | 63.6 | ↓ from 65.5 |

**Chinese models top-8 (Aug 25):** Kimi K3 80.3 | Qwen3.8 Max 79.0 | Qwen3.8-27B 72.5 | Qwen3.7 Max 71.5 | MiMo-V2.5-Pro 69.1 | MiniMax M3 68.5 | Hy3 67.9 | GLM-5.1 66.9

**Note:** GLM-5.3 still absent (open weights not yet released).

**Sources:** https://benchlm.ai/best/open-source | https://benchlm.ai/best/chinese-models

---

### 4. [update] Polymarket Aug 25: Alibaba 95%, Z.ai Surges to 3.6%, Volume $909.83K 🌐

**New fact:** Z.ai jumped from 0.9% to 3.6% (the largest non-Alibaba shift) while Alibaba rose from 94.4% to 95%; total volume grew $154K in 4 days to $909.83K.

| Company | Probability (Aug 25) | Volume | vs Aug 21 |
|---------|----------------------|--------|-----------|
| Alibaba | **95%** | $212.2K | ↑ from 94.4% |
| Z.ai | **3.6%** | $127.62K | ↑ from 0.9% |
| Moonshot | 1.1% | $68.94K | ↑ from 1.0% |
| Bytedance | 0.6% | $55.7K | — |
| Baidu | 0.4% | $88.9K | — |
| Xiaomi | 0.4% | $46.05K | unchanged |
| MiniMax | 0.4% | $74.77K | — |
| Tencent | 0.4% | $42.95K | — |
| DeepSeek | **0.2%** | $143.21K | ↓ from 0.4% |

Market resolves Aug 31 on arena.ai. US removes Chinese AI model market: 26% Yes — stable.

**Sources:** https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | https://www.lines.com/prediction-markets/world/second-best-chinese-ai-company-end-of-august-20260717141100971

---

### 5. [update] Chinese Open-Source Models: 41% of Global Downloads, Surpassing US 🌐 🇨🇳

**New fact:** HuggingFace Spring 2026 report (reported Aug 22 by Tencent News): Chinese self-developed open-source models reached 41% of global downloads — surpassing the US for the first time. Top 6 most-called open-source models globally are all Chinese. Cumulative downloads exceeded 10 billion.

- **Prior state:** ~30% global AI downloads (thread claim from July 2026)
- **41% figure:** from HuggingFace Spring 2026 report; first time China surpassed US
- **Top 6 API call volume globally:** all Chinese models
- **10 billion cumulative downloads:** Chinese open-source models, #1 globally
- **OpenRouter daily token estimate (Aug 16):** DeepSeek ~36%, Tencent ~14%, Anthropic ~10%, OpenAI ~8%, Xiaomi ~7%, others ~25%
- **China narrative:** 「从追赶者变成闭源模型的实际竞争者」— "from follower to genuine competitor against proprietary models" (Tencent News, Aug 22)

**Sources:** https://news.qq.com/rain/a/20260822A0BW8200 | https://news.qq.com/rain/a/20260715A04MGT00 | https://news.bjd.com.cn/2026/07/31/11893835.shtml | https://hk.finance.yahoo.com/news/中國開源模型超車美國-全球下載占比41-熱門前六全包-081008726.html

---

### 6. [update] GLM-5.3 Weights: 2,436 Vulnerabilities Discovered; Still Not Released 🌐 🇨🇳

**New fact:** During GLM-5.3 training, the model "unexpectedly" discovered 2,436 vulnerabilities in 269 open-source projects (1,097 high-risk or critical) — now confirmed as the primary reason for the two-week safety delay. HuggingFace zai-org still shows no GLM-5.3 repo as of Aug 22; target ~Aug 28.

- **2,436 vulnerabilities:** 269 open-source projects; 1,097 classified high-risk or critical
- **Z.ai response:** "most extensive risk review system to date" built for this release
- **API pricing:** live as of Aug 19, same as GLM-5.2
- **ZCode:** 1M users milestone reached (reported in Chinese sources)
- **HuggingFace check (Aug 22):** no GLM-5.3 repo in zai-org; latest is GLM-5.2
- **Community controversy (ongoing):** 「GLM-5.3 刚发布，社区就吵翻了：代码能力确实强了，但它真配叫「最强开源模型」吗？」("community erupted in debate") — label contested while weights withheld

**Sources:** https://fanweibin.cn/posts/2026-08-16-glm-5-3-kaiyuan-bianma-moxing-wangluo-anquan-fengxian | https://www.datalearner.com/ai-models/pretrained-models/glm-5-3 | https://www.modemguides.com/blogs/ai-news/glm-5-3-open-weights-security-findings | https://www.axios.com/2026/08/14/china-open-source-ai-glm-53 | https://www.mindstudio.ai/blog/glm-5-3-open-weights-release-timing

---

### 7. [update] Mistral: Agentic Search Released Aug 20; Frontier MoE Day ~92 🌐

**New fact:** Mistral released "Agentic Search" on Aug 20 — 3x correctness on financial filings (FinanceBench: 26.7% → 86%); reduced latency and token use. Frontier MoE is now day ~92 in partner early access (still no public benchmarks).

- **Agentic Search (Aug 20):** new retrieval layer for complex document navigation; FinanceBench 26.7% → 86% correctness
- **Frontier MoE status:** partner early access since ~June 4; day ~92 as of Aug 25; zero public benchmarks; all August releases remain auxiliary
- **Regional Inference (Aug 11):** covered in prior briefing — EU sovereign stack with GLM-5.2

**Sources:** https://releasebot.io/updates/mistral | https://mistral.ai/news/

---

**Still true** (ongoing threads — no new facts since Aug 21):

- **dots3-note-preview-rednote**: 280B/16B Apache 2.0; BenchLM #3 at 68.8; TEMPO RL; IMO 42/42 series; score unchanged
- **ornith-1-5-self-improving**: MIT 397B MoE; BenchLM #5 at 68.4 (score ±0.1 from estimation noise); self-improvement loop
- **mistral-glm52-eu-sovereign-hosting**: GLM-5.2 on EU Regional Endpoints; 1GW coalition; Aug 11 covered
- **agents-a1-internsciense-new-entrant**: Agents-A1 now #13 at 61.2 (estimation variance; no substantive change)
- **qwen3-8-27b-apache-multimodal**: Apache 2.0; 27B dense; 262K context; 3M+ downloads; Agentic Index 51
- **glm-5-5-expected-august**: GLM-5.5 (new base, 1T+) window still Sept–Oct; GLM-5.3 was Aug release
- **xi-waic-open-source-mandate**: Dual-track hedging pattern continuing (Apache 2.0 + revenue-share)
- **glm-5-2-benchmarks-huawei-trained**: Superseded by GLM-5.3 API; GLM-5.2 on Mistral EU at €1.19/M
- **databricks-enterprise-glm-migration**: GLM Coding Plan auto-upgraded to 5.3; ZCode 1M users; no new enterprise adoption news
- **inkling-small-thinking-machines**: BenchLM #8 at 66.8 (↓ estimation noise)
- **mistral-shieldstral-safety-classifier**: 3B Apache 2.0 safety classifier; NOT frontier MoE
- **minimax-h3-geo-license-restriction**: US/EU/UK/Korea geo-exclusions; Hollywood litigation unchanged
- **deepseek-autonomous-cyberattack-hermes**: Knaithe/KnYuan no new reports
- **industry-coalition-open-weights-letter**: 270+ signatories; all major US labs except Anthropic; unchanged
- **kimi-k3-gpu-crunch-subscription-pause**: Moonshot $50B round ongoing; no new IPO timeline since Aug 21 denial
- **polymarket-us-chinese-model-ban**: 26% Yes; stable
- **nvidia-h200-china-trivial**: Huawei 50-60% China share; Nvidia ~8%; HBM bottleneck; domestic AI company ASIC programs
- **eu-ai-act-august-enforcement**: GPAI enforcement active Aug 2; €15M or 3% fines; Chinese providers subject same enforcement; open-source exempt unless systemic risk
- **ai-manifesto-war-pacing-frontier**: Three governance frameworks live; Anthropic sole US holdout
- **chinese-military-pla-distillation-reuters**: NUDT UAV drone targeting; no new reports
- **xiaomi-mimo-frontier-entry**: MiMo-V2.5-Pro; BenchLM Chinese #5 at 69.1 (↑ from 68.9; minor estimation variance)
- **distillation-scale-data**: Alibaba 28.8M exchanges; NSTM-4; no enforcement
- **nemotron-3-ultra-us-open-weight**: Nvidia Nemotron 3 Ultra; Korea Q4 Ascend launch unchanged
- **polymarket-chinese-ai-company**: Resolved July 31 — Alibaba 100%, $1,041,459
- **kimi-k3-weights-open-source**: 2.8T custom license; DoorDash, Cursor, Databricks, Coinbase; no updates
- **us-moonshot-distillation-sanctions**: Treasury threat July 22 still unexecuted; no new developments
- **openai-hf-cyberattack-glm-defense**: No new reports
- **deepseek-zhipu-self-chip-development**: DeepSeek inference chip early stage; Zhipu also in self-chip; CUDA→CANN complete
- **open-weights-decelerationist-accelerationist**: Meta Muse Glimmer reinforces accelerationist camp; Palladium Mag's decelerationist argument gaining mainstream traction
- **openeurollm-european-sovereign**: Fall 2026 target; 8B model in progress
- **mistral-frontier-moe-silent**: Day ~92; no public benchmarks
- **double-curtain-us-china-export-controls**: MOFCOM AI controls still consultation; US BIS extraterritorial active; parallel escalation continues
- **kimi-k3-eda-chip-design**: 48h functional chip; no update
- **minimax-m3-pro-2-7t**: Q3 single-source; MiniMax unconfirmed; Q3 window has closed
- **tencent-hy3-295b**: BenchLM open-source #6 at 67.9
- **china-mofcom-export-controls-ai**: Still consultation; industry pushback strong; nothing enacted
- **china-domestic-chip-mass-pivot**: TrendForce ~90% domestic share by end-2026; Nvidia ~8%; HBM bottleneck unchanged
- **deepseek-chip-ascend-950dt**: Ascend 950DT cloud-live; V4-Flash-Vision-Exp added Aug 21 (API-only); CUDA→CANN complete
- **jp-deepseek-japanese-cultural-benchmark**: note.com/zephel01 adds practical routing guide; Japan Digital Agency Feb 2026 restriction on classified data via Chinese routes; billing variance 10x at cache tier

---

## Cross-Source Patterns

### Pattern 1: Open-Weight Geopolitics Bifurcating — US Counter-Launches While China Hedges Toward Enclosure 🌐 🇯🇵

**Platforms:** Web (global), Web (Japan), Polymarket

Two simultaneous moves: Meta Muse Glimmer (Aug 10-11, Apache 2.0) positioned as explicit US response to Chinese dominance; ExaWizards and Palladium Mag both document China's own pivot toward restricting overseas weight access. MOFCOM consultation advanced enough that Chinese industry itself is pushing back. DeepSeek-V4-Flash-Vision-Exp releasing as API-only (no weights) is consistent with this direction.

> "Many American users and companies will prefer to build with American models if there's a good open-source version" — Kyle Chan, Brookings (via SCMP, https://www.scmp.com/tech/big-tech/article/3363638/meta-challenge-chinas-open-weight-ai-dominance-amid-us-regulatory-fears) 🌐

---

### Pattern 2: Chinese Open-Source Download Share 41% — Ecosystem Supremacy Now a Cited Fact 🌐 🇨🇳

**Platforms:** Tencent News, Zhihu, CSDN, Juejin, Web (global)

The HuggingFace Spring 2026 report's 41% figure (Chinese downloads > US, top 6 most-called models all Chinese) is now being cited authoritatively in Chinese policy and tech media as proof of ecosystem maturity, not just capability. This crosses from "China is catching up" to "China is the ecosystem" — a rhetorical shift that accelerates domestic regulatory pressure to protect these assets.

> 「从追赶者变成闭源模型的实际竞争者」("From follower to genuine competitor against proprietary models") — Tencent News, Aug 22 (https://news.qq.com/rain/a/20260822A0BW8200) 🇨🇳

---

### Pattern 3: GLM-5.3 as Template for "Open-Weight for Cyber" Dilemma 🌐 🇨🇳

**Platforms:** Axios, fanweibin.cn, aiweekly.co, Zhihu, HN

Z.ai's discovery of 2,436 vulnerabilities during GLM-5.3 training — and subsequent weight hold — is becoming an industry template question: how do you release powerful cyber-capable models as open weights? US labs (OpenAI, Anthropic) resolved this by restricting the most powerful to closed/government-only. Chinese labs (Z.ai) are now doing staged weight releases with safety review. The distinction between "open-source" and "API-only" is becoming a contested frontier.

> GLM-5.3 is likely to "significantly accelerate the threat landscape" — OpenAI's Greg Brockman ([link](https://thenewstack.io/openai-open-weight-glm-5-3/)) 🌐

---

### Pattern 4: Palladium / AI Supremacy / Tech Policy Converging on "US Policy Response" 🌐

**Platforms:** Web (global), HN

Three August 2026 analysis pieces — Palladium Mag (Aug 19), ai-supremacy.com, TechPolicy.Press — converge on the same question: does the US need to regulate Chinese open-weight AI access to protect frontier labs' economic viability? The Palladium piece adds the sharpest claim: Anthropic's Mythos model is already effectively military-only (government and selected cybersecurity customers). The window between "open" and "restricted" is narrowing on both sides.

---

## Per-Platform Tables

### Polymarket 📊
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of August | Alibaba 95%, Z.ai 3.6%, Moonshot 1.1%, ByteDance 0.6%, Baidu 0.4%, Xiaomi 0.4%, MiniMax 0.4%, Tencent 0.4%, DeepSeek 0.2% | $909.83K | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ |
| US Gov removes public access to Chinese AI model 2026 | Yes 26% | $15.1K | https://polymarket.com/event/us-government-removes-public-access-to-a-major-chinese-ai-model-in-2026-20260703203328223 |
| Second-Best Chinese AI Company end of August | Moonshot 56.1% | — | https://www.lines.com/prediction-markets/world/second-best-chinese-ai-company-end-of-august-20260717141100971 |

### Hacker News 🟢
| Thread | Points | Comments | Notable Quote | URL |
|--------|--------|----------|---------------|-----|
| China's open-weights AI strategy is winning | N/A (429) | — | — | https://news.ycombinator.com/item?id=48979269 |
| The state of open source AI | N/A (429) | — | — | https://news.ycombinator.com/item?id=48947825 |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | DeepSeek API Docs | https://api-docs.deepseek.com/news/news260821/ | V4-Flash-Vision-Exp official launch |
| 🌐 | ExplainX | https://explainx.ai/blog/deepseek-v4-flash-vision-exp-multimodal-agent-august-2026 | Technical deep-dive; close to Opus 4.8 |
| 🌐 | Seeking Alpha | https://seekingalpha.com/news/4635820-deepseek-says-new-ai-model-v4-flash-vision-exp-comes-close-to-anthropics-opus-48 | Vendor claim coverage |
| 🌐 | OpenRouter | https://openrouter.ai/deepseek/deepseek-v4-flash-vision-exp | API pricing details |
| 🌐 | Emergent.sh | https://emergent.sh/news/deepseek-v4-flash-vision-exp-officially | Launch coverage |
| 🌐 | Meta AI Research | https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model | Muse Glimmer official launch |
| 🌐 | CNBC | https://www.cnbc.com/2026/08/10/meta-muse-glimmer-open-weight-ai.html | Meta launches Muse Glimmer |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/10/meta-ai-releases-muse-glimmer/ | Technical analysis; 30B Apache 2.0 |
| 🌐 | SCMP | https://www.scmp.com/tech/big-tech/article/3363638/meta-challenge-chinas-open-weight-ai-dominance-amid-us-regulatory-fears | Geopolitical framing |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/08/10/meta-releases-open-source-muse-glimmer-model-30b-parameters/ | 30B open-source coverage |
| 🌐 | InfoQ | https://www.infoq.com/news/2026/08/meta-muse-glimmer/ | Technical reference |
| 🌐 | Pure AI | https://pureai.com/articles/2026/08/19/meta-returns-to-open-weight-ai-with-muse-glimmer.aspx | Aug 19 follow-up |
| 🌐 | The AI Insider | https://theaiinsider.tech/2026/08/11/meta-releases-open-weight-muse-glimmer-model-to-power-local-ai-agents-on-consumer-devices/ | Local agent use cases |
| 🌐 | ArXiv | https://arxiv.org/abs/2608.23283 | Apodex 1.1 paper (Aug 24) |
| 🌐 | BenchLM | https://benchlm.ai/best/open-source | Aug 25 open-source ranking |
| 🌐 | BenchLM | https://benchlm.ai/best/chinese-models | Aug 25 Chinese models ranking |
| 🌐 | Releasebot | https://releasebot.io/updates/mistral | Mistral Aug 20 Agentic Search |
| 🌐 | Palladium Mag | https://www.palladiummag.com/2026/08/19/american-ai-may-not-survive-chinese-open-source | Policy thesis: US AI at risk |
| 🌐 | ExplainX | https://www.explainx.ai/blog/glm-5-3-launch-cyber-defense-benchmarks-august-2026 | GLM-5.3 cyber benchmarks |
| 🌐 | MindStudio | https://www.mindstudio.ai/blog/glm-5-3-open-weights-release-timing | Weights timeline analysis |
| 🌐 | ModemGuides | https://www.modemguides.com/blogs/ai-news/glm-5-3-open-weights-security-findings | Security findings + weights status |
| 🌐 | Axios | https://www.axios.com/2026/08/14/china-open-source-ai-glm-53 | "Rivals U.S. models at hacking" |
| 🌐 | DataLearner | https://www.datalearner.com/ai-models/pretrained-models/glm-5-3 | Model card; Aug 25 weight target |
| 🌐 | Interconnects | https://www.interconnects.ai/p/glm-53-how-chinese-labs-keep-stride | Nathan Lambert analysis |
| 🌐 | Fanweibin | https://fanweibin.cn/posts/2026-08-16-glm-5-3-kaiyuan-bianma-moxing-wangluo-anquan-fengxian | 2,436 vulns detail (Chinese blog) |
| 🌐 | CryptoSlate | https://cryptoslate.com/predictions/market/best-chinese-ai-company-end-of-august/ | Polymarket odds |
| 🌐 | SCMP | https://www.scmp.com/tech/tech-trends/article/3361415/kimi-k3-developer-moonshot-ai-expedites-fundraising-ahead-planned-ipo-source-says | Moonshot IPO update |
| 🌐 | Palladium Mag | https://www.palladiummag.com/2026/08/19/american-ai-may-not-survive-chinese-open-source | Policy: US AI survival threat |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | "China problem just got worse" |
| 🌐 | TechPolicy.Press | https://www.techpolicy.press/will-china-crack-down-on-open-weight-models/ | China crackdown probability |
| 🌐 | High Capacity | https://www.highcapacity.org/p/chinas-global-ai-strategy | China's global AI strategy |
| 🌐 | NextBigTeng | https://nextbigteng.substack.com/p/american-open-weight-leadership | American open-weight leadership |
| 🌐 | USCC | https://www.uscc.gov/sites/default/files/2026-03/Two_Loops--How_Chinas_Open_AI_Strategy_Reinforces_Its_Industrial_Dominance.pdf | Two loops report (March 2026) |
| 🌐 | CFR | https://www.cfr.org/articles/chinas-ai-chip-deficit-why-huawei-cant-catch-nvidia-and-us-export-controls-should-remain | Chip performance gap analysis |
| 🌐 | ValueAddVC | https://valueaddvc.com/blog/how-export-controls-on-ai-chips-are-reshaping-global-tech-competition | Huawei 50-60% China share |
| 🌐 | CSIS | https://www.csis.org/analysis/deepseek-huawei-export-controls-and-future-us-china-ai-race | US-China AI race |
| 🌐 | TrendingTopics EU | https://www.trendingtopics.eu/china-weighs-export-controls-on-ai-models-including-open-weight-llms/ | MOFCOM AI controls |
| 🌐 | Arnold & Porter | https://www.arnoldporter.com/en/perspectives/advisories/2026/07/china-imposes-export-control-and-government-procurement-restrictions-on-designated-us-companies | MOFCOM US firm sanctions |
| 🌐 | TechTimes | https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm | MOFCOM weight controls |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | ExaWizards | https://exawizards.com/column/ai-trend/news-07-08-2026/ | China's policy reversal ("囲い込み"); Mythos shock framing |
| 🇯🇵 | note.com (zephel01) | https://note.com/zephel01/n/n380d8aa4bdb8 | Practical routing/billing guide; 10x cache price variance; JP Digital Agency Feb 2026 restriction |
| 🇯🇵 | MIT Tech Review JP | https://www.technologyreview.jp/s/381701/chinas-open-source-bet/ | Chinese open-source strategy coverage |
| 🇯🇵 | Forbes Japan | https://forbesjapan.com/articles/detail/95069 | Why China has upper hand in open-source AI |
| 🇯🇵 | Qiita (kai_kou) | https://qiita.com/kai_kou/items/1d66ed9b16b6717053e5 | GLM-5 on Huawei chips introduction |
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | 2026 Chinese AI model comparison guide |
| 🇯🇵 | AI革命 | https://ai-revolution.co.jp/media/chinese-ai-models-dominance/ | OpenRouter Chinese models >60%; JP enterprise impact |
| 🇯🇵 | Hatena Blog | https://tt-ai.hatenablog.com/entry/2026/08/13/000000_3 | Qwen3.8-27B JP coverage |
| 🇯🇵 | PC Watch | https://pc.watch.impress.co.jp/docs/news/2132435.html | Qwen3.8-27B release (Aug 14 weights) |
| 🇯🇵 | AlphaMatch JP | https://www.alphamatch.ai/ja/blog/open-source-llm-comparison-blog-2026 | Chinese models redefining AI hegemony |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | Practical Chinese AI guide for JP devs |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260822A0BW8200 | 41% global download share (Aug 22); top 6 all Chinese |
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260715A04MGT00 | 41% milestone original Tencent report |
| 🇨🇳 | Beijing Daily | https://news.bjd.com.cn/2026/07/31/11893835.shtml | 10B+ cumulative downloads #1 globally |
| 🇨🇳 | Beijing Daily | https://news.bjd.com.cn/2026/07/31/11894380.shtml | Top 6 API call volume all Chinese |
| 🇨🇳 | Yahoo Finance HK | https://hk.finance.yahoo.com/news/中國開源模型超車美國-全球下載占比41-熱門前六全包-081008726.html | Chinese open-source surpasses US |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/670574382 | DataLearner tracker Aug 21 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071707711306216661 | 「大模型的疯狂八月」 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071592445759042630 | GLM-5.3 official launch thread |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071644430679938817 | GLM-5.3 open-source label controversy |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2073319660544602286 | Daily AI briefing Aug 19 (403 on fetch) |
| 🇨🇳 | Juejin | https://juejin.cn/post/7669935311557083163 | August 2026 "triple-leap" |
| 🇨🇳 | CSDN | https://deepseek.csdn.net/6a55a1bd10ee7a33f28d37f1.html | Open-source model survey July 2026; GLM-5.2 led at 51 pts |
| 🇨🇳 | CSDN | https://adg.csdn.net/6a392d27662f9a54cb82beb5.html | Deep evaluation 2026 open-source models |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/stock/t/2026-07-08/doc-inihaxzw7997184.shtml | DeepSeek chip project (one year old) |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-07-08/doc-inihaawh8031397.shtml | DeepSeek chip strategy to reduce Nvidia dependence |
| 🇨🇳 | Winzheng | https://www.winzheng.com/article/deepseek-chip-plans | DeepSeek chip plan vs US export controls |
| 🇨🇳 | Fanweibin | https://fanweibin.cn/posts/2026-08-16-glm-5-3-kaiyuan-bianma-moxing-wangluo-anquan-fengxian | GLM-5.3: 2,436 vulns caused weight delay |

---

## Stats Block

```
├─ 🟠 Reddit: excluded per spec
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 2 threads │ points not retrieved (429 rate limit)
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts │ source health OK; no on-topic posts indexed
├─ 📊 Polymarket: 2 active markets + 1 side market │ $909.83K + $15.1K volume
├─ 🌐 Web: 70+ pages │ 🇯🇵 11 │ 🇨🇳 17
└─ 🗣️ Top voices: Palladium Mag (decelerationist analysis), Tencent News tech desk (41% download share), ExaWizards JP (Mythos shock framing), Zuckerberg/Meta (open-weight counter-launch), Z.ai/Zhipu (GLM-5.3 safety review template)
```

---

## Out of Scope but Notable

- **Apodex 1.1** (Aug 24, arXiv 2608.23283): new agentic model paper from Apodex AI; 35B Mini locally deployable; Apache 2.0 prior open-weight versions fine-tuned from Qwen3.5; complex professional work focus. Not clearly Chinese or European lab — fits `agent-harnesses` or `agentic-ai` topic better than this one. Worth tracking: https://arxiv.org/abs/2608.23283

- **Mistral Agentic Search** (Aug 20): 3x FinanceBench correctness improvement; relevant to `enterprise-ai` or `retrieval-augmented-generation` topics. Not a model release, but a retrieval layer — fits this topic only as auxiliary Mistral news. https://releasebot.io/updates/mistral

- **"Digital AI communism" framing**: Dean Ball (OpenAI) quote in SCMP/ai-supremacy coverage — "one probable outcome of an open-weight-model-dominant world is full AI communism." Novel political-economy framing for what open weights mean at scale. Could anchor a `governance-paradigm` thread.

---

## Data Gaps

- **DuckDuckGo HTML endpoint**: both JP and ZH queries returned CAPTCHA; switched to native-language WebSearch — comparable quality coverage
- **HN thread engagement**: 429 Too Many Requests on both HN threads (points/comments not retrieved)
- **Zhihu daily briefing Aug 19**: 403 Forbidden on direct fetch
- **GLM-5.3 open weights**: Not released as of Aug 22 check; target Aug 25-28 per DataLearner; not confirmed
- **Mistral frontier MoE**: Day ~92 partner early access; still zero public benchmarks
- **Bluesky**: Health OK; 0 posts indexed on topic
- **YouTube**: Not retrieved in free-tool pass
- **DeepSeek Harness stars**: Not re-fetched in this pass (144K+ as of Aug 21 remains last known)
- **Polymarket ban market**: 26% Yes at $15.1K volume; thin market, low confidence
- **MiniMax M3 Pro 2.7T**: Q3 window has now closed; unconfirmed (single-source, MiniMax never confirmed)
- **Estimated coverage:** ~82% — strong on new model releases (DeepSeek Vision, Meta Muse Glimmer), download share update, Polymarket, GLM-5.3 vulnerability detail; gaps from YouTube, Reddit, X, HN engagement numbers

---

## Key Quotes

> "Many American users and companies will prefer to build with American models if there's a good open-source version." — Kyle Chan (Brookings Institution), via SCMP on Meta Muse Glimmer ([link](https://www.scmp.com/tech/big-tech/article/3363638/meta-challenge-chinas-open-weight-ai-dominance-amid-us-regulatory-fears)) 🌐

> 「从追赶者变成闭源模型的实际竞争者」("From follower to genuine competitor against proprietary models") — Tencent News, Aug 22 on Chinese AI download share surpassing US ([link](https://news.qq.com/rain/a/20260822A0BW8200)) 🇨🇳

> 「世界を席巻した中国のAIオープンモデルが一転、囲い込みへ」("China's AI open models that swept the world now turning to enclosure") — ExaWizards AI Trend column ([link](https://exawizards.com/column/ai-trend/news-07-08-2026/)) 🇯🇵

> GLM-5.3 is likely to "significantly accelerate the threat landscape" — OpenAI's Greg Brockman on GLM-5.3's ExploitBench capabilities ([link](https://thenewstack.io/openai-open-weight-glm-5-3/)) 🌐

> 「GLM-5.3 发布：编程能力暴涨 50%，却因"意外挖出"上千个高危漏洞而推迟开源权重」("GLM-5.3 launch: coding surged 50%, but weight release delayed due to 'unexpectedly' uncovering thousands of high-risk vulnerabilities") — fanweibin.cn ([link](https://fanweibin.cn/posts/2026-08-16-glm-5-3-kaiyuan-bianma-moxing-wangluo-anquan-fengxian)) 🇨🇳

> "Chinese self-developed open-source models reached 41% of global downloads, surpassing the US for the first time — this scenario would have been unimaginable two years prior." — HuggingFace Spring 2026 Report, cited by Tencent News (https://news.qq.com/rain/a/20260822A0BW8200) 🇨🇳
