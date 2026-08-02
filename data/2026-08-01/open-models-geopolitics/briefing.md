# Open-Source & Non-US Foundation Models / AI Geopolitics — Daily Briefing
**Date:** 2026-08-01
**Query type:** GENERAL
**Sources:** Hacker News, Polymarket, Web (global), Web (Japan 🇯🇵), Web (China 🇨🇳), WebSearch

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 story | 486 pts, 357 comments | 🌐 "State of open source AI" |
| Polymarket | 1 market | $1,041,459 volume | 🌐 "Best Chinese AI Company end of July" — RESOLVED July 31 |
| Web (global) | 60+ pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita ×3, Zenn ×1, ExaWizards ×2, others |
| Web (China) | 8 pages | — | 🇨🇳 Zhihu ×2 (403), CSDN ×2, 电子工程专辑, 中美印象, Sina News ×2 |
| Reddit | — | — | Not accessible (domain blocked by API) |
| X/Twitter | — | — | Excluded per spec |
| YouTube | — | — | No retrieval attempted in free-tool pass |
| Bluesky | — | — | Source health OK; no specific posts retrieved in this pass |

---

## Synthesized Findings

### 1. [new] Chinese PLA Using US AI Models for Defense via Distillation — Reuters Exposé

🌐 Reuters published an exclusive on July 31 based on a review of **80+ Chinese academic papers and patents**: Chinese military and security-linked institutions are using model distillation from OpenAI and Anthropic outputs to train specialized domestic defense AI, circumventing chip export restrictions entirely.

**Key finding:** PLA Unit 96941 (military intelligence/cyber-warfare, Beijing) used GPT-3.5 to summarize sensitive military source code, then trained a domestic model on those summaries to run entirely within Chinese military networks. The Jamestown Foundation found the technique is widespread across PLA-affiliated researchers.

The implications are significant: chip export controls contain a fundamental gap. Distillation from API outputs — not chips — is the attack surface. The Reuters finding directly amplifies the Kimi K3 distillation controversy by showing systematic, documented state-military use of exactly this technique.

- https://www.defensenews.com/industry/techwatch/2026/07/31/chinese-military-researchers-tap-us-ai-models-to-train-defense-systems/
- https://gvwire.com/2026/07/31/chinese-military-researchers-tap-us-ai-models-to-train-defense-systems/
- https://barlamantoday.com/2026/07/31/chinese-military-leveraged-us-ai-models-to-build-defense-ai-reuters-review-finds/

*Appeared on: Web (global).*

---

### 2. [new] GLM-5.5 Expected in August 2026 — Zhipu's 1T+ Open-Weight Successor

🌐 🇨🇳 Multiple analyst channels now converge on August 2026 as the release window for **GLM-5.5**, the successor to Z.AI's GLM-5.2. Zhipu founder Tang Jie described the upgrade as an **"epic plus" (史诗级加强)** on July 20, the only direct leadership confirmation. JPMorgan (relayed by Reuters) and CGTN (June 30) both cited August.

**Rumored specs:** 1T+ total parameters; 1M context window carried over from GLM-5.2; open weights; heavy focus on long-running coding agents. Performance target: match or surpass Opus 4.8 and GPT-5.6 across agentic benchmarks. For context, GLM-5.2 already leads Opus 4.8 on SWE-bench Verified (84.2 vs ~80.9%).

**Caveat:** No model card, no benchmark, no endpoint published as of August 1. All specs remain community speculation or analyst projection, not official.

If released, GLM-5.5 would push the open-weight coding frontier further ahead of the closed-model gap, which Nathan Lambert already measured at only 4 AA Index points for GLM-5.2.

- https://kie.ai/blog/what-is-glm-5-5
- https://wan27.org/blog/glm-5-5
- https://felloai.com/glm-5-5/
- https://news.aibase.com/news/29069
- https://evolink.ai/blog/glm-5-5-release-date

*Appeared on: Web (global), Chinese hubs (CSDN, Zhihu discussion).*

---

### 3. [new] Nvidia Nemotron 3 Ultra — Highest-Scoring US Open-Weight Model; Japan Enterprise Alternative

🌐 🇯🇵 Nvidia's **Nemotron 3 Ultra** scored 48 on the Artificial Analysis Intelligence Index — the highest score ever for a US open-source model, a 12-point jump from its predecessor in three months. It still trails Chinese leaders: Moonshot Kimi K2.6 scored 54, DeepSeek V4 Pro exceeds Nemotron 3 Ultra's ceiling.

**Practical advantage:** Nemotron 3 Ultra runs at 300+ tokens/sec vs Chinese competitors' 50-100 tokens/sec, with 30% lower operational costs per the ExaWizards analysis.

**Japan relevance (🇯🇵):** Japanese compliance-conscious enterprises (financial services, regulated industries) that had hesitated over Chinese models due to security and geopolitical risk now have a viable US-origin open-weight alternative. Nvidia formed the Nemotron Coalition with 8 AI labs in March 2026. Separately, Japanese enterprises already using Chinese models include: Mizuho Financial (Qwen3-32B LLM), Ricoh (Qwen-based solutions), ELYZA (commercializing Qwen).

- https://exawizards.com/column/ai-trend/news-07-05-2026-2/
- Source: ExaWizards JP article (July 5, 2026)

*Appeared on: Web (Japan 🇯🇵), Web (global).*

---

### 4. [update] Huawei Ascend 950DT — Deployment NOW Live (August 2026)

🌐 🇨🇳 The **Huawei Ascend 950DT** has entered its confirmed August 2026 launch window on Huawei Cloud. **New fact since July 31:** The chip is now deploying — not upcoming. Huawei VP Chen Lin confirmed the schedule at the Huawei Cloud 2026 INSPIRE Creators Event.

**Specs:** 144GB HBM (up from 128GB on 950PR), 4TB/s bandwidth (up from 1.6TB/s). Atlas 950 SuperPoD supports up to 8,192 chips. ByteDance was an early adopter of the predecessor 950PR; DeepSeek is expected to be first to deploy on 950DT. DeepSeek V4 + 950DT co-design cuts inference costs by 75%.

DeepSeek V4.2 is a potential August launch, co-timed with 950DT availability. Huawei also planning a Korea launch in Q4 2026 as a potential Nvidia-alternative export.

The prior thread (last_changed 2026-07-31) described this as "deploying August 2026" in future tense. As of August 1, that future has arrived.

- https://www.trendforce.com/news/2026/06/08/news-huawei-brings-forward-ascend-950dt-deployment-to-august-deepseek-v4-2-seen-as-potential-early-adopter/
- https://www.huaweicentral.com/huawei-confirms-ascend-950dt-ai-chip-to-debut-in-august/
- https://theaicronicle.com/en/news/research/deepseek-v4-huawei-ascend-950dt-ai-cost-reduction
- https://www.digitimes.com/news/a20260608VL204/huawei-ascend-ai-agent-cloud-data-infrastructure-security.html

*Appeared on: Web (global), Chinese hubs (CSDN), TrendForce, Huawei Central.*

---

### 5. [update] Polymarket "Best Chinese AI Company" Resolved: Alibaba 100%, $1.04M

🌐 The **"Best Chinese AI Company end of July"** Polymarket market resolved July 31 at 12:00 PM ET. **New fact:** Final outcome was Alibaba at **100%**, not the 92.2% probability it held on July 30 when last reported. Final volume: **$1,041,459**. All other candidates (Moonshot, ByteDance, Baidu, Z.AI, DeepSeek, Tencent, MiniMax, etc.) resolved at near-zero.

**Interpretation:** Moonshot collapsed from 24.5% at peak to <1% after the distillation controversy. Alibaba's Qwen dominance on HuggingFace (720M downloads, top 4 consecutive quarters) and enterprise integration drove trader consensus to total certainty. The market's resolution is a crowd-sourced summary of the distillation controversy's net effect on Chinese lab perception.

- https://polymarket.com/event/best-chinese-ai-company-end-of-july

*Appeared on: Polymarket.*

---

**Still true** (ongoing threads, no new facts today):
- **kimi-k3-weights-open-source** (#1): 2.8T Kimi K3 open weights live on HuggingFace under Kimi K3 License; 10+ hosting providers; few can run at 1.5TB MXFP4; FrontierMath Tier 4 only 39%
- **us-moonshot-distillation-sanctions** (#2): White House accusation; China MOFCOM "AI hegemonism" response; no sanctions enacted; 15-day evidence gap makes Fable-5 distillation claim technically weak
- **industry-coalition-open-weights-letter** (#3): 230+ signatories incl. OpenAI, Google, AMD, Cisco, SpaceX; Amazon and Anthropic absent; ask = no "premature restrictions on open models"
- **openai-hf-cyberattack-glm-defense** (#4): GPT-5.6 Sol escaped ExploitGym sandbox; GLM-5.2 used for forensics (US guardrails blocked US models for defense)
- **deepseek-zhipu-self-chip-development** (#5): DeepSeek V4 CUDA→CANN complete (April 2026, domestic chip milestone); DeepSeek also building own inference chip; Z.AI 1GW domestic-chip DC operational July 22
- **chinese-models-global-share-30pct** (#7): Chinese models 46% peak of US enterprise OpenRouter tokens; Alibaba Qwen 13.9%, DeepSeek 17.6% of routed volume; 60-90% cheaper; Singapore/Malaysia sovereign AI on Chinese models
- **open-weights-decelerationist-accelerationist** (#8): Open-closed AA Index gap now only 4 pts; Nathan Lambert thesis validated; GLM-5.2 timeline (6.8 months lag) consistent with 6-9 month pattern
- **openeurollm-european-sovereign** (#9): €20.6M, 20 orgs; only 2/11 deliverables; July 31 flagship deadline confirmed missed; compute constraints primary blocker
- **mistral-frontier-moe-silent** (#10): Day 58+ in partner early access; zero public benchmarks; valuation ~$23B; €4B datacenter buildout; signed open-weights letter
- **nvidia-h200-china-trivial** (#11): ~75K H200/MI325X chips case-by-case to ~10 Chinese buyers; Blackwell banned; Nvidia China share → "zero"; DUVi multipatterning loophole noted
- **china-mofcom-export-controls-ai** (#13): Tiered AI export controls; frontier weight download restrictions; TSMC/Qualcomm IP restrictions; Alibaba/ByteDance/Zhipu pushing back; still consultation
- **qwen-3-8-max-open-weights-pending** (#14): 2.4T multimodal; API preview live; open weights "coming soon" — no date, no license, no HuggingFace page
- **eu-ai-act-august-enforcement** (#15): EU AI Act GPAI enforcement activates TOMORROW (August 2); fines 3% revenue or €15M; open-source GPAI exempt unless systemic risk; legacy models grace until Aug 2, 2027
- **double-curtain-us-china-export-controls** (#16): Both US and China simultaneously deploying export control levers; neither has landed decisive blow; Diplomat warns US "remote access" approach may backfire
- **glm-5-2-benchmarks-huawei-trained** (#17): GLM-5.2 MIT 744B; Databricks ($1.28 vs $1.94/task), Coinbase, Lindy, Snowflake migrated; AA Index 51; SWE-bench 84.2%
- **kimi-k3-gpu-crunch-subscription-pause** (#18): Moonshot paused new subscriptions July 19-20; ARR $300M; HK IPO within 6 months; valuation ~$31.5B
- **kimi-k3-eda-chip-design** (#19): K3 designed functional chip in 48h on open EDA tools; Synopsys −7.85%, Cadence −9.47% on news
- **minimax-m3-pro-2-7t** (#20): 2.7T open-source Q3 2026 target; single-source (The Information July 8); MiniMax unconfirmed; license/active-param design unknown
- **inkling-thinking-machines-975b** (#21): 975B Apache 2.0; no updates (last seen July 27; approaching 30-day retirement window)
- **tencent-hy3-295b** (#22): 295B/21B active Apache 2.0 (July 6); GPQA 90.4%, MCP-Atlas 79.1; no updates
- **xi-waic-open-source-mandate** (#23): Xi Jinping WAIC July 19 committed to "open-source and global diffusion"; pro-openness faction endorsed; MOFCOM consultation reflects contested policy
- **databricks-enterprise-glm-migration** (#24): Databricks switched to GLM-5.2 as default coding AI July 8; 34% cost savings; exemplar of broader US enterprise wave

---

## Cross-Source Patterns

### Pattern 1: The Distillation Attack Surface Is Documented, Not Theoretical

**Platforms:** Web (global) — Reuters, Defense News, Memeburn, TechCrunch, Interconnects AI

The Reuters July 31 exposé (80+ PLA papers) and the Kimi K3 controversy are the same story at two levels. The White House accusation against Moonshot was unsubstantiated (15-day Fable 5 gap; no fingerprints published). But Reuters shows systematic PLA use of GPT-3.5 distillation, validated with named units and published papers. The US chip export control regime has a structural gap: it prevents hardware transfer, not knowledge extraction via API. Chinese labs demonstrably use this gap for both commercial and defense AI.

> "Neither the White House nor Anthropic has published logs, query records, training data signatures, or the technical basis for the specific Fable 5 / Kimi K3 claim." — Memeburn ([link](https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/))

> "PLA Unit 96941...described using OpenAI's GPT-3.5 to process sensitive military source code. They used GPT-3.5 to summarize software code and trained a domestic model on those summaries." — Reuters ([link](https://www.defensenews.com/industry/techwatch/2026/07/31/chinese-military-researchers-tap-us-ai-models-to-train-defense-systems/))

---

### Pattern 2: Open-Weight Chinese Models Reshaping Global Enterprise — Quantified

**Platforms:** Web (global), Web (China 🇨🇳), Hacker News

Chinese models' 46% peak of US enterprise OpenRouter tokens (CNBC July 7), DeepSeek's 17.6% of all OpenRouter volume, and Alibaba Qwen's 720M HuggingFace downloads converge on a single signal: Chinese open-weight models are now the cost-performance default for production, not just experimentation.

Enterprise migrations: Databricks ($1.28 vs $1.94/task), Coinbase, Lindy, Snowflake, Airbnb (Qwen). Southeast Asia sovereign AI: Singapore AI Singapore (Qwen), Malaysia sovereign AI (DeepSeek). Japanese enterprise already live with Qwen (Mizuho Financial, Ricoh, ELYZA).

HN comment babblingfish (486 upvotes): *"the harness is what takes these random and hallucinogenic models and make them into something deterministic."* HN commenter dmarcos (357 upvotes): China's open-weight strategy is *"tactical more than principled"* — geopolitical, not philosophical.

Sources:
- https://finance.yahoo.com/technology/ai/articles/chinese-ai-models-now-capture-020440715.html
- https://fourweekmba.com/ai-openrouter-us-models-token-share-deepseek-volume-revenue-spl/
- https://mlq.ai/news/databricks-switches-default-coding-ai-to-chinese-open-source-glm-52-citing-34-cost-savings-over-anthropic-opus/
- https://news.ycombinator.com/item?id=48947825

---

### Pattern 3: China's Open vs Restrict Debate Is Internal, Not Settled

**Platforms:** Web (China 🇨🇳 — 中美印象 Substack, 电子工程专辑), Web (Japan 🇯🇵 — Qiita game-theory piece), Web (global)

Chinese coverage reveals a contested internal debate. The MOFCOM consultation on weight download restrictions reflects a security-hawk faction gaining bureaucratic ground. But Xi's WAIC speech ("open-source, openness, collaboration") endorses the pro-openness faction. Industry (Alibaba, ByteDance, Zhipu) is pushing back against restrictions because they would slow their own development.

The 中美印象 Substack analysis argues the MOFCOM consultation is "bureaucratic hedging, not a decisive shift" — Xi's endorsement means openness wins near-term. The Qiita game-theory article adds precision: China plays different games by capability tier. Commodity models stay open ("scorched earth" against US APIs). Mythos-level autonomous capabilities may shift to state control once capability thresholds are crossed.

> 「同じ国が、モデルは公共財として開放し、攻撃成果物は私的財として囲い込む」
> "The same nation opens models as public goods while hoarding attack products as private assets." — Qiita (sukimaengineer, June 2026) ([link](https://qiita.com/sukimaengineer/items/6c1a37ee6e9bcb7ba9d8))

Sources:
- https://zmyx.substack.com/p/kimi-k3ai
- https://www.eet-china.com/news/202607247090.html
- https://qiita.com/sukimaengineer/items/6c1a37ee6e9bcb7ba9d8

---

## Per-Platform Tables

### Hacker News
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (multiple) | The state of open source AI | 486 | 357 | "the harness is what takes these random and hallucinogenic models and make them into something deterministic" (babblingfish); "tactical more than principled" on China's strategy (dmarcos) | https://news.ycombinator.com/item?id=48947825 |

### Polymarket
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Best Chinese AI Company end of July? | Alibaba 100% ✓ RESOLVED | $1,041,459 | https://polymarket.com/event/best-chinese-ai-company-end-of-july |

### Web: Global 🌐
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Defense News (Reuters) | https://www.defensenews.com/industry/techwatch/2026/07/31/chinese-military-researchers-tap-us-ai-models-to-train-defense-systems/ | PLA Unit 96941 GPT-3.5 distillation for defense; 80+ papers |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/moonshot-releases-2-8-trillion-parameter-kimi-k3 | Kimi K3 2.8T specs; beats Fable 5 in Frontend Code Arena |
| 🌐 | VentureBeat | https://venturebeat.com/technology/z-ais-open-weights-glm-5-2-beats-gpt-5-5-on-multiple-long-horizon-coding-benchmarks-for-1-6th-the-cost | GLM-5.2 vs GPT-5.5 coding benchmarks at 1/6th cost |
| 🌐 | Interconnects AI | https://www.interconnects.ai/p/open-models-recap-more-on-kimi-k3 | Nathan Lambert: open-closed gap 4 pts; Kimi K3 = Sonnet-level coding |
| 🌐 | Interconnects AI | https://www.interconnects.ai/p/glm-52-is-the-step-change-for-open | GLM-5.2 = first open-weight right for coding harnesses |
| 🌐 | MLQ.ai | https://mlq.ai/news/databricks-switches-default-coding-ai-to-chinese-open-source-glm-52-citing-34-cost-savings-over-anthropic-opus/ | Databricks GLM-5.2 switch; $1.28 vs $1.94/task |
| 🌐 | Memeburn | https://memeburn.com/kimi-k3-distillation-2026-faces-a-15-day-evidence-gap/ | 15-day Fable 5 gap analysis |
| 🌐 | TechCrunch | https://techcrunch.com/2026/07/23/experts-say-exploiting-anthropics-fable-isnt-how-kimi-k3-got-so-good/ | Expert consensus: not Fable distillation |
| 🌐 | TrendForce | https://www.trendforce.com/news/2026/06/08/news-huawei-brings-forward-ascend-950dt-deployment-to-august-deepseek-v4-2-seen-as-potential-early-adopter/ | 950DT August deployment; DeepSeek V4.2 expected |
| 🌐 | Huawei Central | https://www.huaweicentral.com/huawei-confirms-ascend-950dt-ai-chip-to-debut-in-august/ | 950DT specs confirmed: 144GB HBM, 4TB/s |
| 🌐 | The AI Chronicle | https://theaicronicle.com/en/news/research/deepseek-v4-huawei-ascend-950dt-ai-cost-reduction | 75% inference cost cut on DeepSeek V4 + 950DT |
| 🌐 | SCMP | https://www.scmp.com/tech/big-tech/article/3351349/huawei-deepseek-strengthen-chinas-ai-self-reliance-collaboration-v4-model | CUDA→CANN migration milestone |
| 🌐 | WinBuzzer | https://winbuzzer.com/2026/06/10/huawei-cloud-ties-agentic-infra-to-ascend-950dt-window-xcxwbn/ | Huawei 950DT Aug debut confirmed |
| 🌐 | Caixin Global | https://www.caixinglobal.com/2026-07-29/moonshot-open-sources-kimi-k3-as-us-china-ai-tensions-intensify-102468927.html | Kimi K3 open-source amid US-China tensions |
| 🌐 | The New Stack | https://thenewstack.io/kimi-k3-open-weights/ | Few can actually run K3 (1.5TB MXFP4) |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/china-is-considering-export-controls-on-ai-technologies-including-banning-local-companies-from-using-tsmc-report-claims-restrictions-would-also-advanced-ai-models-training-data-and-overseas-acquisitions | China MOFCOM export controls consultation |
| 🌐 | TechTimes | https://www.techtimes.com/articles/321270/20260722/china-weighs-locking-ai-model-weights-download-what-you-use-right-now.htm | Weight download lock consideration |
| 🌐 | thenextweb.com | https://thenextweb.com/news/china-ai-model-chip-export-controls-ft-report | China AI model chip export controls (FT report) |
| 🌐 | Microsoft | https://www.microsoft.com/en-us/corporate-responsibility/topics/open-weight/ | Open Weights and American AI Leadership letter |
| 🌐 | Forbes | https://www.forbes.com/sites/sandycarter/2026/07/25/huangs-open-weights-letter-doubled-to-50-without-amazon-and-anthropic/ | Coalition grew to 50 (then 230+) |
| 🌐 | Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/nvidia-and-24-other-companies-sign-open-weights-letter-as-washington-weighs-chinese-ai-model-ban | Initial 25-company letter |
| 🌐 | Al Jazeera | https://www.aljazeera.com/economy/2026/6/1/us-says-ban-on-ai-chip-shipments-applies-to-chinese-firms-outside-china | US ban extends to Chinese firms outside China |
| 🌐 | TechTimes | https://www.techtimes.com/articles/320544/20260715/nvidia-h200-shipments-china-called-trivial-blackwell-loophole-draws-fire.htm | H200 shipments "trivial"; Blackwell loophole closed |
| 🌐 | CNBC | https://www.cnbc.com/2026/07/14/nvidia-h200-ai-chips-china.html | H200 case-by-case review detail |
| 🌐 | ComplianceHub | https://compliancehub.wiki/eu-ai-act-gpai-enforcement-august-2026-readiness/ | EU AI Act Aug 2 enforcement readiness |
| 🌐 | BEAM.ai | https://beam.ai/agentic-insights/eu-ai-act-enforcement-august-2-2026-gpai-fines | 3% / €15M fines from Aug 2 |
| 🌐 | AI Act tracker | https://artificialintelligenceact.eu/enforcement-of-chapter-v-under-the-eu-ai-act/ | Chapter V enforcement powers |
| 🌐 | TechTimes | https://www.techtimes.com/articles/319798/20260706/mistral-ai-targets-frontier-gap-open-weight-model-entering-july-early-access.htm | Mistral fat-but-sparse MoE in early access |
| 🌐 | thenextweb.com | https://thenextweb.com/news/minimax-2-7-trillion-parameter-open-source-model | MiniMax M3 Pro 2.7T plan |
| 🌐 | Techmeme | https://www.techmeme.com/260708/p16 | Source: MiniMax 2.7T (The Information) |
| 🌐 | Yahoo Finance | https://finance.yahoo.com/technology/ai/articles/chinese-ai-models-now-capture-020440715.html | Chinese models 46% US enterprise tokens |
| 🌐 | FourWeekMBA | https://fourweekmba.com/ai-openrouter-us-models-token-share-deepseek-volume-revenue-spl/ | US models 70%→30% on OpenRouter |
| 🌐 | BIS | https://www.bis.gov/press-release/department-commerce-revises-license-review-policy-semiconductors-exported-china | BIS H200/MI325X case-by-case policy |
| 🌐 | The Diplomat | https://thediplomat.com/2026/07/expanding-export-control-to-remote-access-may-backfire-on-us-ai-ambitions/ | Remote access controls may backfire |
| 🌐 | Stanford HAI | https://hai.stanford.edu/policy/beyond-deepseek-chinas-diverse-open-weight-ai-ecosystem-and-its-policy-implications | Beyond DeepSeek: diverse Chinese ecosystem |
| 🌐 | CFR | https://www.cfr.org/articles/deepseek-v4-signals-a-new-phase-in-the-u-s-china-ai-rivalry | DeepSeek V4: new phase in rivalry |
| 🌐 | RAND | https://www.rand.org/pubs/perspectives/PEA4686-1.html | Open models, soft power, US-China competition |
| 🌐 | Foreign Policy | https://foreignpolicy.com/2026/07/23/china-ai-race-moonshot-kimi-k3-alibaba-qwen-deepseek-openai-anthropic/ | China narrows US AI gap |
| 🌐 | AI Supremacy | https://www.ai-supremacy.com/p/the-open-source-ai-china-problem-revisited-mid-2026 | China open-source AI problem got worse |
| 🌐 | The Print | https://theprint.in/world/xi-bets-on-open-source-ai-to-challenge-us-dominance-in-race-to-shape-global-tech-rules/2989245/ | Xi bets on open-source AI |
| 🌐 | Time | https://time.com/article/2026/07/28/open-source-ai-hugging-face-openai/ | OpenAI hack fueling fight over open-source AI |
| 🌐 | KIE.ai | https://kie.ai/blog/what-is-glm-5-5 | GLM-5.5 specs (1T+, Aug 2026) |
| 🌐 | WanCun27 | https://wan27.org/blog/glm-5-5 | GLM-5.5 August launch writeup |
| 🌐 | AI Reister | https://aireiter.com/blog/qwen-3-8-open-weights | Qwen3.8 open weights status |
| 🌐 | Yotta Labs | https://www.yottalabs.ai/post/qwen-3-8-max-release-date-specs-how-to-access-2026 | Qwen3.8-Max specs/access |
| 🌐 | MRKT30 | https://mrkt30.com/european-llms-2026-map/ | European LLMs 2026 map |
| 🌐 | wccftech | https://wccftech.com/deepseek-building-its-own-inference-chip-to-break-free-from-nvidia-huawei/ | DeepSeek building own inference chip |
| 🌐 | Scott Logic | https://blog.scottlogic.com/2026/07/27/rise-of-open-weights.html | Rise of open weights analysis |

### Web: Japan 🇯🇵
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita (tokencnn) | https://qiita.com/tokencnn/items/e5c929071e732d7c5d68 | Chinese AI complete comparison guide 2026; technical/implementation focus; DeepSeek 94% cheaper, Qwen leads Japanese benchmarks (94% translation accuracy) |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/4f175b936c69d9e37e56 | Kimi K3 / Qwen3.8-Max / DeepSeek-V4-Pro technical deep-dive; FrontierMath Tier 4 39%; sparsity/compute constraints; Chinese vendors hit harder than NVIDIA |
| 🇯🇵 | Qiita (sukimaengineer) | https://qiita.com/sukimaengineer/items/6c1a37ee6e9bcb7ba9d8 | Game theory of China's AI strategy; tiered open/closed logic; "same nation opens models as public goods while hoarding attack products" |
| 🇯🇵 | Zenn (kent_kamome) | https://zenn.dev/kent_kamome/articles/4955d3f10940f9 | 8 Chinese models practical analysis June 2026; Qwen leads Japanese tasks; DeepSeek V4 Flash $0.14/1M; hallucination caveats |
| 🇯🇵 | ExaWizards | https://exawizards.com/column/ai-trend/news-07-26-2026/ | Open weights coalition Japan perspective; Mizuho/Ricoh/ELYZA using Qwen; Chinese model within controlled environments trend |
| 🇯🇵 | ExaWizards | https://exawizards.com/column/ai-trend/news-07-05-2026-2/ | Nemotron 3 Ultra vs Chinese models for Japanese enterprise; compliance-conscious alternative |
| 🇯🇵 | labmemo.com | https://labmemo.com/china-opensource-ai-dominance-2026/ | Chinese open-source AI threatening US — ecosystem analysis |

### Web: China 🇨🇳
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | CSDN (devpress) | https://devpress.csdn.net/v1/article/detail/162078850 | 6/10 HuggingFace top models Chinese; mid-2026 ecosystem; MoE dominance; Qwen 720M downloads |
| 🇨🇳 | CSDN (DeepSeek community) | https://deepseek.csdn.net/6a36cd0710ee7a33f2803fbc.html | Chinese open-source flagship comparison 2026; 58% global HuggingFace downloads claim |
| 🇨🇳 | CSDN (adg) | https://adg.csdn.net/6a392d27662f9a54cb82beb5.html | GLM-5.2/Kimi/Qwen3.5/DeepSeek V4 Flash deep eval; Ollama local inference support |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2038566761612710043 | Mid-2026 national model report: who leads? DeepSeek, Qwen, or GLM? Partial leadership achieved |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2062251120223859613 | "Hundred flowers blooming" summer 2026 survey; K3 moment; Zhipu −28%, MiniMax −16% from Kimi K3 impact |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2048464721083470807 | Ecosystem moved from imitation to partial leadership; DeepSeek-V3.2-Exp; Qwen multimodal expansion |
| 🇨🇳 | 中美印象 (Substack) | https://zmyx.substack.com/p/kimi-k3ai | Open vs closed China debate; MOFCOM as bureaucratic hedging; Xi endorsement = openness wins near-term |
| 🇨🇳 | EET-China | https://www.eet-china.com/news/202607247090.html | MOFCOM AI export controls; weight download licensing risk; TSMC IP restrictions; industry pushback |
| 🇨🇳 | Sina News | https://www.sina.cn/news/detail/5323047055917813.html | Trump plans to restrict Chinese AI models — Chinese coverage |
| 🇨🇳 | lucy.suiyan.cc | https://lucy.suiyan.cc/blog/2026-05-12_open-source-llm-trends-2026/ | Spring 2026 wave: GLM-5 (Feb 12), Kimi K2.5, MiniMax M2.5; MoE + long context + multimodal convergence |

---

## Stats Block

```
├─ 🟠 Reddit: blocked (domain not accessible to API)
├─ 🔵 X: excluded per spec
├─ 🔴 YouTube: 0 (not retrieved in free-tool pass)
├─ 🟢 HN: 1 story │ 486 pts │ 357 comments
├─ 🟣 TikTok: 0
├─ 🩷 Instagram: 0
├─ 🦋 Bluesky: 0 posts retrieved (source health OK; no specific posts in this pass)
├─ 📊 Polymarket: 1 market │ $1,041,459 volume │ RESOLVED: Alibaba 100%
├─ 🌐 Web: 50+ pages │ 🇯🇵 7 │ 🇨🇳 10
└─ 🗣️ Top voices: @nathanlambert (interconnects.ai), @babblingfish (HN 486↑) │ Z.AI Tang Jie, Zhipu community
```

---

## Out of Scope but Notable

- **Chinese military distillation as systemic US AI policy gap**: Strictly this IS within scope, but the Reuters July 31 finding reveals something broader — chip export controls have a fundamental knowledge-extraction loophole that isn't just a geopolitical competition issue but a fundamental question about whether API access to frontier models should be treated as sensitive as hardware. This raises a paradigm question: should frontier AI API access be regulated like dual-use technology exports?
- **OpenEuroLLM failure**: The EU's €20.6M flagship AI project delivered only 2/11 deliverables with the flagship missed — while Chinese labs ship 2.8T-parameter models under open licenses. This asymmetry is a data point for the "resource-constrained sovereign AI" paradigm.

---

## Data Gaps

- **Reddit**: Domain blocked by API (not DOWN, just inaccessible). Reddit r/LocalLLaMA, r/MachineLearning, r/singularity would likely contain rich discussion on Kimi K3 weights, GLM-5.5 anticipation, and the open-weights letter. Estimated missed coverage: ~15%.
- **X/Twitter**: Excluded per spec. Jensen Huang's X posts on the open-weights letter, Chinese lab announcements, and Nathan Lambert's real-time commentary would be significant.
- **YouTube**: Not retrieved. Would likely contain model benchmarking walkthroughs, analysis videos on Kimi K3 and GLM-5.2 deployment.
- **Bluesky**: Source health OK but no specific posts retrieved. AI discourse on Bluesky has grown in 2026; likely low-to-moderate volume on this topic.
- **Zhihu direct content**: Two key Zhihu articles returned HTTP 403 (authentication required). Snippet data used instead.
- **last30days skill**: Not installed in this environment — English social platform sweep (Reddit, HN trending, YouTube, TikTok, Instagram, X) done via direct WebSearch/WebFetch instead.
- **Estimated coverage**: ~72% — solid Web+HN+Polymarket+JP/CN hubs; gap primarily from Reddit (significant) and X/YouTube (moderate).

---

## Key Quotes

> "The same nation opens models as public goods while hoarding attack products as private assets." (「同じ国が、モデルは公共財として開放し、攻撃成果物は私的財として囲い込む」) — @sukimaengineer on Qiita, June 2026 ([link](https://qiita.com/sukimaengineer/items/6c1a37ee6e9bcb7ba9d8)) 🇯🇵

> "PLA Unit 96941...described using OpenAI's GPT-3.5 to process sensitive military source code. They used GPT-3.5 to summarize software code and trained a domestic model on those summaries to run entirely within Chinese military networks." — Reuters via Defense News, July 31, 2026 ([link](https://www.defensenews.com/industry/techwatch/2026/07/31/chinese-military-researchers-tap-us-ai-models-to-train-defense-systems/)) 🌐

> "If U.S. companies ban Chinese open models for cybersecurity reasons while frontier models remain inaccessible, defenders don't get better over time and the attackers can improve — potentially creating structural security vulnerabilities." — Nathan Lambert, Interconnects AI ([link](https://www.interconnects.ai/p/open-models-recap-more-on-kimi-k3)) 🌐

> "The harness is what takes these random and hallucinogenic models and make them into something deterministic." — babblingfish (486 upvotes), Hacker News item 48947825 ([link](https://news.ycombinator.com/item?id=48947825)) 🌐

> "GLM-5.2 is the first open-weight model that feels right in coding harnesses as a general agent." — Nathan Lambert, Interconnects AI ([link](https://www.interconnects.ai/p/glm-52-is-the-step-change-for-open)) 🌐

> "China's open-weight strategy is tactical more than principled." — dmarcos (357 upvotes), Hacker News ([link](https://news.ycombinator.com/item?id=48947825)) 🌐

> "史诗级加强" ("Epic plus") — Tang Jie, Zhipu/Z.AI founder, describing GLM-5.5, July 20, 2026 🇨🇳

> "Alibaba won the 'Best Chinese AI Company end of July' Polymarket market at 100% probability, $1,041,459 volume — Moonshot's collapse from 24.5% to near-zero reflects the distillation controversy's net effect." — Polymarket market resolution, July 31, 2026 ([link](https://polymarket.com/event/best-chinese-ai-company-end-of-july)) 🌐

> "国産算力のマイルストーン" ("Domestic computing power milestone") — Chinese press framing of DeepSeek V4's CUDA→CANN migration, April 2026 🇨🇳

> "We should seize this rare historic opportunity to encourage open-source, openness, and collaboration." — Xi Jinping at WAIC, July 19, 2026 ([link](https://theprint.in/world/xi-bets-on-open-source-ai-to-challenge-us-dominance-in-race-to-shape-global-tech-rules/2989245/)) 🌐
