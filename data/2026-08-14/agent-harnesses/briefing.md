# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-14
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Product Hunt

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Not accessed |
| YouTube | — | — | Not accessed |
| Hacker News | 5 threads | ~1,100+ pts, 600+ comments | DeepSeek Harness 678 pts, Ante 135 pts (Aug 11), Advanced Harness 127 pts, self-improvement, YC QM ongoing |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; 0 on-topic posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~55 pages | — | 🌐 WebSearch + WebFetch; 18 query passes |
| Web (Japan) | ~22 pages | — | 🇯🇵 DDG HTML + WebSearch: Gigazine, gihyo.jp, PC Watch, Qiita, Zenn, note, Hatena |
| Web (China) | ~22 pages | — | 🇨🇳 DDG HTML + WebSearch: Juejin (8+ articles), Zhihu (5+), CSDN, cnblogs, openclaw.club, tonybai.com |

---

## Synthesized Findings

### 1. [new] DeepSeek Harness v0.1: "Everything Is a Plugin" — 52k+ Stars in 24h 🌐🇯🇵🇨🇳

**Claim:** Aug 13, 2026 — DeepSeek open-sourced its internal model-benchmarking harness as DeepSeek Harness v0.1 (MIT), the year's highest-velocity harness launch: 52.9k+ GitHub stars in 24h, HN 678 pts/276 comments.

**Evidence:**
- **GitHub:** https://github.com/deepseek-ai/deepseek-harness · **Site:** https://deepseek.com/harness
- **License:** MIT · **State:** developer preview (breaking changes expected)
- **Core philosophy:** "Everything is a Plugin" — model, tools, skills, session log, agent loop, sandbox, UI all swap via Cordis plugin system without source changes
- **Cordis foundation:** TypeScript meta-framework; hot-swap at runtime (RAII-style lifecycle); originated from QQ-bot framework Koishi, community-tested for years before DeepSeek adoption
- **4 modes:**
  - Standard: full toolset (file edit, shell, web search)
  - Code/PTC (Programmatic Tool Calling): generates TypeScript SDK calls, collapses multi-op requests
  - Minimal: bash + edit only; for benchmarks
  - Creator: agent inspects and rewrites its own runtime, hot-swap plugin experimentation
- **Model-agnostic:** 30+ providers — DeepSeek, Anthropic, OpenAI, Google, Bedrock, Vertex, Azure, OpenAI-compatible
- **Traceability:** append-only session logs; all model-visible content logged; fork, replay, audit supported ("model-visible ⟺ logged")
- **Sandboxing:** Linux Landlock
- **Start:** `npx @deepseek-ai/dsh web` → http://127.0.0.1:3080; headless: `dsh --profile headless`
- **Key internal fact:** this is the framework DeepSeek used internally to benchmark V4-Flash and V4-Pro models — publicly released alongside V4-Pro-0813
- **V4-Pro-0813 (same day, out-of-scope model):** vendor-reported 87.9% Terminal-Bench 2.1, DeepSWE 12.8→62.7; NO independent verification yet (techtimes.com, dsv4pro.novcog.us.com)
- **API price increase:** peak-hour output ~350% higher; tiered pricing starts Aug 17
- **Stars:** 52.9k (OSSInsight Aug 14) / "4.6万星" per Juejin at 24h / still climbing

**HN notable comments:**
> "US models won't let you see [complete reasoning traces]" — SwellJoe (traceability competitive advantage)

> "plugin fatigue from incompatible versions and abandoned community extensions represents a known ecosystem risk" — invaliduser

**JP reaction 🇯🇵:**
> "DeepSeekがClaude Code対抗を無償公開" ("DeepSeek releases Claude Code rival for free") — aifriends.jp ([link](https://aifriends.jp/deepseek-harness-v01-open-source/))
> 「Agent版のVS Code」framing on Zenn ([link](https://zenn.dev/hjpotter1/articles/4f44fcacede3b6))

**CN reaction 🇨🇳:**
> 「Agent时代的安卓」("Android for the Agent era") — community framing for open-ecosystem positioning ([link](https://openclaw.club/archives/deepseek-harness-official-release))
> 「没有丝毫宣传地发布…但GitHub却爆了」("Released without any fanfare…yet GitHub exploded") — CSDN ([link](https://blog.csdn.net/GreenHands495/article/details/163758358))

**Community ecosystem day 1:** CLI tools, visual toolkits, 20,000-char install tutorials (Juejin), Windows/Linux/macOS guides all emerged within hours.

**Sources:** https://thenewstack.io/deepseek-harness-open-source-plugins/ · https://venturebeat.com/technology/deepseek-harness-launches-as-open-source-rival-to-claude-code-alongside-v4-pro-on-api-with-higher-prices · https://alphasignal.ai/news/deepseek-harness-opens-the-agent-framework-it-used-to-benchmark-its-own-models · https://github.com/deepseek-ai/deepseek-harness · https://deepseek.com/harness · https://news.ycombinator.com/item?id=49285244 · https://byteiota.com/deepseek-harness-v01-open-source-agent/ · https://cryptobriefing.com/deepseek-harness-open-source-developer-preview/ · https://pandaily.com/deepseek-harness-hands-on-four-modes-model-plus-harness-equals-agent-aug2026 · https://the-decoder.com/deepseek-launches-an-improved-v4-pro-model-raises-api-prices-and-makes-its-agent-software-open-source/ · https://www.techtimes.com/articles/324241/20260813/deepseek-v4-pro-0813-goes-ga-benchmark-claims-await-independent-proof.htm · https://dsv4pro.novcog.us.com/

---

### 2. [new] PenguinHarness: Self-Improving Agent Harness from LlamaFactory Team 🌐

**Claim:** LlamaFactory creator Yaowei Zheng ships PenguinHarness (MIT) — closed-loop self-improving harness where agents build, evaluate, and optimize other agents; $0.02/RAG-app on benchmark; 66 Product Hunt upvotes.

**Evidence:**
- **GitHub:** https://github.com/Prism-Shadow/penguin-harness · **Site:** https://penguin.ooo/
- **Product Hunt:** https://www.producthunt.com/products/penguinharness — 66 upvotes, launched ~Jul 22-23, 2026
- **Team:** Yaowei Zheng (LlamaFactory), PrismShadow AI Team, Fable 5
- **Core loop:** agents build → agents evaluate (automatic data generation + multi-agent scoring) → retain successful mods → iterate
- **1,000+ models** via AI-native SDK; reusable Skills; tool + context management
- **Benchmark:** complex data-analysis task — PenguinHarness + DeepSeek = highest accuracy at ~1/70 the cost of Claude Code + Opus
- **Concern raised on PH:** evaluation bias in self-improving systems (no external grader)
- **CLI + Web UI:** zero-code entry point; local-first, self-hostable

**Sources:** https://www.producthunt.com/products/penguinharness · https://github.com/Prism-Shadow/penguin-harness · https://penguin.ooo/ · https://explainx.ai/blog/self-harness-agents-improve-themselves-arxiv-2026

---

### 3. [update] Claude Code v2.1.232: Subagent Forking Default + @Cross-Session Mentions 🌐

**New facts since Aug 11:** v2.1.232 (Aug 14) — subagent forking on by default; cross-session `@` mentions; GitLab marketplace; Fable 5 advisor return; 12 security fixes. Auto mode default for Pro/Max/Team starts today.

**Evidence:**
- **v2.1.231 (Aug 13):** MCP OAuth redirect-URI fix for servers with pre-registered clients (e.g. Slack); 30s MCP hang fixed
- **v2.1.232 (Aug 14) — 50 changes (6 new features, 12 security, 17 fixes, 12 improvements, 2 perf, 1 breaking):**
  - **Subagent forking default:** `subagent_type: 'fork'` inherits full conversation + prompt cache; non-teammate agents now background by default in interactive sessions → eliminates context re-entry and cache misses
  - **Cross-session @mentions:** type `@<session-name>` to reach another running Claude session via SendMessage (available since v2.1.224 but now surfaced in TUI)
  - **GitLab plugin support:** marketplace expanded to GitLab including nested subgroups; `gitlab.com` URLs work like GitHub equivalents
  - **Fable 5 advisor return:** orgs with Fable access regain `/advisor` option
  - **Security:** PowerShell variable overwrite fix; Git Bash symlink path bypass fix; nested repo trust now requires individual confirmation; Linux sandbox protected-path hardening; GitLab token masking
  - **Breaking:** project-level `sandbox.ripgrep` overrides removed — migrate to user-level/managed/CLI
- **Auto mode default (Aug 14):** Pro, Max, and Team plans — all new sessions use auto mode; replaces permission prompts with background safety checks

**Sources:** https://code.claude.com/docs/en/changelog · https://dev.classmethod.jp/en/articles/20260814-cc-updates-v2-1-232/ · https://www.claudeupdates.dev/version/2.1.232 · https://xenospectrum.com/en/claude-code-cross-session-messaging/ · https://code.claude.com/docs/en/whats-new · https://startdebugging.net/2026/08/subtask-vs-fork-vs-background-agent-in-claude-code/

---

### 4. [update] Kiro Crew (AWS, Aug 4): 24/7 Autonomous Coding Workspace 🌐

**New fact since Aug 11:** Kiro Crew launched Aug 4 — persistent, self-evolving, multi-agent workspace that runs 24/7; also Kiro v2.17.0 adds cloud sessions.

**Evidence — Kiro Crew:**
- **What:** autonomous coding workspace on top of Kiro IDE; agents work offline or online
- **Multi-agent:** specialist sub-agents; tasks fan out across complex projects
- **Persistent memory:** agents adapt to preferences, pass lessons between sessions; visible memory with developer control
- **Scheduled work:** heartbeat monitoring for recurring jobs
- **Chat:** Slack, Telegram, Discord, WeCom
- **Self-evolving:** designed to learn from corrections; visible memory so developers control persistence
- **Config:** reads .kiro files; integrates OpenClaw and Hermes tools
- **Platform:** macOS direct download/GitHub; Linux + Windows setup docs

**Evidence — Kiro CLI v2.17.0 / IDE v1.0.293 (Aug 11):**
- **Cloud sessions:** `--cloud` flag; run in managed sandbox, disconnect while agent keeps working, resume from any machine
- **IDE:** Cloud Sessions in Agent Focus Mode (preview); sessions rail collapsible icon-only view; attention cards; back/forward navigation
- Always Allow restored for forgotten commands

**Sources:** https://siliconangle.com/2026/08/04/aws-launches-kiro-crew-autonomous-agentic-orchestrator-24-7-code-development/ · https://aws.amazon.com/blogs/aws/aws-weekly-roundup-aws-heroes-summit-web-search-on-amazon-bedrock-dogwood-kiro-crew-and-more-august-10-2026/ · https://kiro.dev/changelog/ · https://releasebot.io/updates/kiro

---

### 5. [update] Hermes Agent v0.20.1 (Aug 13): Patch Rolling Up 1,444 Commits 🌐

**New fact since Aug 11:** v0.20.1 (Aug 13) tagged with 1,444 commits / 656 PRs since v0.20.0 (Aug 3); stabilizes Docker images and hosted deployments.

**Evidence:**
- 2,172 files changed, +233,872 / −75,244 lines since v0.20.0
- ~481 issues closed
- Full curated release notes defer to v0.21.0
- Docker images, hosted deployments, "latest" tag now all on v0.20.1

**Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.13 · https://releasebot.io/updates/nousresearch/hermes-agent · https://hermesatlas.com/guide/

---

### 6. [update] Cursor: Cloud Builds (3× Faster), iOS Beta, AIUC-1 Certification 🌐

**New facts since Aug 11:** Cloud Agents 3× faster startup via pre-built environments (Aug 13); iOS public beta (all paid plans); AIUC-1 agent security certification.

**Evidence:**
- **Cloud Builds (Aug 13):** environments prepared hourly in background at no cost; 3× faster agent startup (Faire: "large repos now start in seconds"); agent continues from last successful build on failure; new Builds dashboard tab; all environments default to builds from Aug 17
- **Cursor iOS:** always-on agents, Remote Control, live notifications, mobile review; available all paid plans
- **AIUC-1 certification (Aug 13):** agent intelligence unit compatibility for agent security/reliability
- **Cursor Start India:** ₹649/mo (new market access)
- **Grok 4.6 added** to Cursor Router (Aug 12)

**Sources:** https://cursor.com/changelog · https://releasebot.io/updates/cursor

---

### 7. [update] Extension Economy: Skills Marketplace 244 New Skills (Aug 13) 🌐

**New fact since Aug 11:** Aug 13 — Skills Marketplace: 12 publishers added 244 skills; 3.5M+ total installs milestone.

**Evidence:**
- DeepSeek Harness day-1 ecosystem: community plugins tag `dsh-plugin` on GitHub; CLI tools and visual toolkits emerged within hours of launch
- Kilo Marketplace (ongoing): Modes renamed → Agents in 2026 rebuild; 500+ LLMs, MCP marketplace, BYOK
- claudemarketplaces.com (ongoing): 23,600+ skills, 12,700+ MCP servers

**Sources:** https://www.agensi.io/learn/skills-marketplace-ai-agents · https://github.com/Kilo-Org/kilo-marketplace · https://claudemarketplaces.com/

---

### 8. [update] OpenClaw 2026.8.1-beta.1 + OpenCode v1.18.18 (Aug 13) 🌐

**New facts since Aug 11:** OpenClaw hardening beta + GPT-5.6 support; OpenCode Kimi provider bug fix.

**Evidence — OpenClaw 2026.8.1-beta.1:**
- Hardening: safer browser/network boundaries, more resilient agent/provider runs
- GPT-5.6 model family support
- Extended-stable channel: 2026.6.33 (backports from 2026.6.11)
- Stable: v2026.7.1-2 (Aug 4)

**Evidence — OpenCode v1.18.18 (Aug 13):**
- Bug fix: Kimi system prompt selection for official Moonshot/Kimi providers
- Bug fix: xhigh reasoning effort for xAI models

**Sources:** https://github.com/openclaw/openclaw/releases · https://releasebot.io/updates/openclaw · https://github.com/anomalyco/opencode/releases

---

**Still true** (ongoing threads, no new facts this cycle):

- `agent-plugins-1-standard` — Agent Plugins 1.0 (Aug 6): 7-company coalition, Anthropic absent; continued adoption
- `cloudflare-os-kitesurf` — Cloudflare OS + Kitesurf; no new facts
- `ante-antigma-single-binary` — Ante 15MB Rust binary (Show HN Aug 11, 135 pts); source pushed Aug 10; no new release
- `tencentdb-agent-memory` — TencentDB Agent Memory v2.0; no new facts
- `meta-muse-code` — Meta Muse Code beta; no new facts
- `prime-agent-rlm` — Prime Agent (MIT); no new facts
- `aq-multiplayer-harness` — AQ; no new facts
- `qwen-code-alibaba` — Qwen Code; no new facts
- `oh-my-agent` — oh-my-agent; no new facts
- `autoharness-deepmind` — AutoHarness; no new facts
- `hoplite-yc-s26-cloud-deploy` — Hoplite; no new facts
- `vercel-ai-sdk-harnessagent` — Vercel AI SDK v7 HarnessAgent; no new facts
- `cursor-router-workspace-plugins` — Cursor Router; Grok 4.6 added Aug 12 (minor update)
- `copilot-studio-ga-harness-billing` — Copilot Studio; no new facts
- `microsoft-agent-governance-toolkit` — AGT; no new facts
- `tinyagents-rust-recursive` — TinyAgents; no new facts
- `sprocket-hardware-software-agent` — Sprocket; no new facts
- `gambit-reliable-agent-harness` — Gambit; no new facts
- `nlah-natural-language-harnesses` — NLAH; no new facts
- `skills-security-prompt-injection-36pct` — 36% prompt injection; no new facts
- `claude-tag-slack-agent` — Claude Tag; no new facts
- `mimo-code-xiaomi` — MiMo Code; no new facts
- `ecc-cross-harness-os` — ECC; no new facts
- `cursor-3-11-update` — Cursor 3.11; superseded by Builds update above
- `kimi-code-moonshot` — Kimi Code; no new facts (OpenCode Kimi fix indirectly related)
- `runtime-yc-p26` — Runtime; no new facts
- `noclick-always-on` — NoClick; no new facts
- `nyx-offensive-testing` — Nyx; no new facts
- `agentguard-security-tool` — AgentGuard; no new facts
- `mcp-security-nsa-supply-chain` — Agentjacking; no new facts
- `yc-qm-multiplayer-harness` — YC QM; no new facts
- `anthropic-managed-agents-mcp-tunnels` — Sonnet 5 promo pricing ends Aug 31 → Sept 1 price increase; no other new facts
- `mcp-stateless-spec-2026-07-28` — MCP 2026-07-28 spec; no new facts
- `jadepuffer-agentic-security` — JADEPUFFER ransomware; no new facts
- `grok-build-xai-rust-harness` — Grok-Build; no new facts
- `self-harness-auto-optimization` — Self-Harness; no new facts
- `openharness-hkuds` — OpenHarness; no new facts
- `vscode-1130-agent-host` — VSCode 1.130 AHP; no new facts
- `antigravity-gemini-cli-successor` — Antigravity 2.0; no new facts
- `claw-code-claude-rewrite` — Claw Code ~195k stars; no new facts
- `kiro-aws-spec-driven` — see Finding #4 above (Kiro Crew + v2.17.0)
- `metaharness-scaffold-generator` — MetaHarness; no new facts
- `harness-engineering-paradigm` — Agent=Model+Harness still dominant 2026 paradigm; DeepSeek launch reinforces
- `deerflow-superagent-harness` — DeerFlow 2.0; no new facts
- `omnigent-meta-harness` — Omnigent; no new facts
- `zot-go-coding-harness` — Zot; no new facts
- `omp-omo-pi-derivatives` — oh-my-pi + oh-my-openagent; no new facts
- `yorishiro-presence-harness` — Yorishiro; no new facts
- `agentskills-open-standard` — SKILL.md; Agent Plugins 1.0 ongoing
- `letta-agent-file-format` — Letta .af; no new facts
- `layered-oss-stack-over-single-framework` — 17+ OSS layers; no new facts
- `macos-harness-proving-ground` — macOS; no new facts
- `ahe-automated-harness-evolution` — AHE papers; no new facts
- `harness-internal-external-disambiguation` — Internal vs External Harness; no new facts
- `environment-architect-new-role` — 環境設計者; JP community continues articulating this role
- `warp-oz-multi-harness` — Warp Oz; no new facts
- `mozilla-otari-llm-gateway` — Mozilla Otari; no new facts
- `statewright-guardrails` — Statewright; no new facts
- `headroom-token-compression` — Headroom; no new facts
- `pi-minimal-agent-harness` — Pi; no new facts
- `nvidia-skillspector-security` — SkillSpector; no new facts
- `deepseek-harness-team` — DeepSeek Harness team now public (see Finding #1)
- `cli-anything-hkuds` — CLI-Anything; no new facts
- `forge-acp-universal-cli` — Forge ACP; no new facts
- `github-copilot-skills-mcp-ga` — Copilot skills+MCP GA; no new facts
- `opencode-anomaly-rebrand` — see Finding #8 above (v1.18.18 bug fixes)
- `cursor-spacex-acquisition` — SpaceX $60B acquisition closing Q3 2026; no new facts
- `block-buzz-workspace` — Block Buzz; no new facts
- `zcode-zhihu-agent-ide` — ZCode; no new facts
- `devin-desktop-windsurf-rebrand` — Devin Desktop; no new facts
- `devin-fusion-multimodel` — Devin Fusion; no new facts
- `ambiance-unix-harness` — Ambiance; no new facts
- `kore-artemis-abl` — Kore.ai Artemis; no new facts
- `open-agent-passport-oap` — OAP; no new facts
- `code-as-agent-harness-paper` — arXiv:2605.18747; no new facts
- `tilde-harness-sdk` — Tilde; no new facts
- `microsoft-maf-codeact` — MAF Harness GA; no new facts
- `claude-code-doctor-skill-hygiene` — see Finding #3 above

---

## Cross-Source Patterns

### Pattern 1: The Modular-Everything Counter-Bid — DeepSeek's "Harness Android" Moment 🌐🇯🇵🇨🇳
**Platforms:** The New Stack, VentureBeat, AlphaSignal, HN (678 pts), Juejin (8+ articles), Zhihu, CSDN, gihyo.jp, Gigazine, Zenn, note

DeepSeek's "Everything is a Plugin" principle (via Cordis) is the sharpest competitive counter to the monolithic incumbents (Claude Code, Codex, Kiro). The CN community immediately framed it as "Agent时代的安卓" — an open platform play against closed products. JP community converged on "Agent版のVS Code" framing. The harness-as-platform pattern (where models are just plugins) has been theorized (Self-Harness paper, MetaHarness, Ante, Ambiance) but DeepSeek is the first major lab to ship it as a product.

> "DeepSeek opens the agent framework it used to benchmark its own models." — AlphaSignal ([link](https://alphasignal.ai/news/deepseek-harness-opens-the-agent-framework-it-used-to-benchmark-its-own-models)) 🌐

---

### Pattern 2: Competition Shifts from Model → Harness Execution Layer 🌐🇯🇵🇨🇳
**Platforms:** VentureBeat, The Decoder, HN, Juejin, Zhihu, Qiita (Ryu-Yanagi)

Same benchmark tool DeepSeek used internally to prove V4-Flash/V4-Pro capabilities is now public. This means the community can reproduce evaluation conditions — and potentially prove that the harness (not the model) explains much of the performance gap. Combined with Ante's 82.7% TB2.1 claim ("for every model we run, no other harness scores higher with that model") and the harness-engineering paradigm thread, the field is converging on harness architecture as the primary competitive variable.

---

### Pattern 3: 24/7 Autonomous Coding Infra Emerges as Standard Offering 🌐
**Platforms:** SiliconAngle, AWS Blog, Cursor changelog, Kiro changelog

Within one week: Kiro Crew (Aug 4), Cursor Cloud Builds (Aug 13), and the ongoing Hoplite/Runtime/NoClick cluster all ship persistent-background-agent infrastructure. The pattern: agents run offline/online, disconnect and resume from any machine, pre-warm environments. The "always-on coding agent" is becoming table stakes.

---

### Pattern 4: DeepSeek Harness Dominates JP/CN Coverage as "Claude Code Rival" 🇯🇵🇨🇳
**Platforms:** Gigazine, gihyo.jp, PC Watch (JP); Juejin, Zhihu, CSDN, openclaw.club, tonybai.com (CN)

Within hours of launch, JP and CN developer communities produced: multiple hands-on install guides, deep architecture analyses, and strategic commentary. Both framed DeepSeek Harness primarily as a Claude Code/Codex competitor — the "open-source free rival." CN community is the more technically detailed, producing 20k-character tutorials on day 1. JP community picked up on the "Agent版のVS Code" framing and the "すべてがプラグイン" (everything is a plugin) philosophy.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| deepseek-ai | DeepSeek Harness developer preview | 678 | 276 | "US models won't let you see [complete reasoning traces]" — SwellJoe | https://news.ycombinator.com/item?id=49285244 |
| AntigmaLabs | Show HN: Ante, a coding agent in a single binary that runs offline | 135 | 80 | "We care about the harness, not the model or the prompts" | https://news.ycombinator.com/item?id=49245437 |
| — | Building an Advanced Agentic Harness | 127 | 43 | "smol minimalist system benchmarks cheaper+faster than orchestrated frameworks" | https://news.ycombinator.com/item?id=49182946 |
| — | Harness engineering for self-improvement | — | — | Self-harness optimization discussion | https://news.ycombinator.com/item?id=49164896 |
| tosh | qm – Multiplayer agent harness for work | 665 | 161 | YC QM ongoing community (prior cycle) | https://news.ycombinator.com/item?id=49126604 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | The New Stack | https://thenewstack.io/deepseek-harness-open-source-plugins/ | DeepSeek Harness launch coverage (Frederic Lardinois) |
| 🌐 | VentureBeat | https://venturebeat.com/technology/deepseek-harness-launches-as-open-source-rival-to-claude-code-alongside-v4-pro-on-api-with-higher-prices | DeepSeek Harness vs Claude Code; V4-Pro price increase |
| 🌐 | AlphaSignal | https://alphasignal.ai/news/deepseek-harness-opens-the-agent-framework-it-used-to-benchmark-its-own-models | Internal benchmarking harness angle |
| 🌐 | GitHub (DeepSeek) | https://github.com/deepseek-ai/deepseek-harness | 52.9k+ stars; MIT; "Everything is a Plugin" |
| 🌐 | deepseek.com | https://deepseek.com/harness | Official harness page |
| 🌐 | The Decoder | https://the-decoder.com/deepseek-launches-an-improved-v4-pro-model-raises-api-prices-and-makes-its-agent-software-open-source/ | V4-Pro + Harness + price hike bundle |
| 🌐 | ByteIota | https://byteiota.com/deepseek-harness-v01-open-source-agent/ | Plugin-by-plugin walkthrough |
| 🌐 | ExplainX | https://explainx.ai/blog/deepseek-harness-v0-1-plugin-first-agent-stack-august-2026 | Technical guide |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/deepseek-harness-open-source-developer-preview/ | MIT preview coverage |
| 🌐 | X-CMD | https://www.x-cmd.com/install/deepseek-harness/ | Component-swap without forking |
| 🌐 | Pandaily | https://pandaily.com/deepseek-harness-hands-on-four-modes-model-plus-harness-equals-agent-aug2026 | Hands-on four modes |
| 🌐 | TechTimes | https://www.techtimes.com/articles/324241/20260813/deepseek-v4-pro-0813-goes-ga-benchmark-claims-await-independent-proof.htm | Benchmark independence caveat |
| 🌐 | DSV4Pro | https://dsv4pro.novcog.us.com/ | What shipped vs what's unverified |
| 🌐 | PenguinHarness PH | https://www.producthunt.com/products/penguinharness | Self-improving harness; 66 upvotes |
| 🌐 | GitHub (PenguinHarness) | https://github.com/Prism-Shadow/penguin-harness | MIT; LlamaFactory team |
| 🌐 | penguin.ooo | https://penguin.ooo/ | Official product site |
| 🌐 | Classmethod | https://dev.classmethod.jp/en/articles/20260814-cc-updates-v2-1-232/ | CC v2.1.232 detailed breakdown |
| 🌐 | ClaudeUpdates | https://www.claudeupdates.dev/version/2.1.232 | 50 changes list |
| 🌐 | XenoSpectrum | https://xenospectrum.com/en/claude-code-cross-session-messaging/ | @cross-session messaging deep-dive |
| 🌐 | StartDebugging | https://startdebugging.net/2026/08/subtask-vs-fork-vs-background-agent-in-claude-code/ | Fork vs subtask guide |
| 🌐 | Claude What's New | https://code.claude.com/docs/en/whats-new | Week 32 digest; auto mode default Aug 14 |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/08/04/aws-launches-kiro-crew-autonomous-agentic-orchestrator-24-7-code-development/ | Kiro Crew launch |
| 🌐 | AWS Blog | https://aws.amazon.com/blogs/aws/aws-weekly-roundup-aws-heroes-summit-web-search-on-amazon-bedrock-dogwood-kiro-crew-and-more-august-10-2026/ | AWS weekly with Kiro Crew highlight |
| 🌐 | Kiro changelog | https://kiro.dev/changelog/ | v2.17.0 CLI; IDE v1.0.293 |
| 🌐 | Hermes release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.13 | v0.20.1 patch |
| 🌐 | Hermes Atlas | https://hermesatlas.com/guide/ | v0.20.1 guide |
| 🌐 | Cursor changelog | https://cursor.com/changelog | Cloud Builds; iOS; AIUC-1 |
| 🌐 | OSSInsight | https://ossinsight.io/trending/ai | DeepSeek Harness 52.9k stars trending |
| 🌐 | Agensi Skills | https://www.agensi.io/learn/skills-marketplace-ai-agents | 244 new skills Aug 13 |
| 🌐 | Kilo Marketplace | https://github.com/Kilo-Org/kilo-marketplace | Modes→Agents; 500+ LLMs |
| 🌐 | Claude Marketplaces | https://claudemarketplaces.com/ | 23,600+ skills; 12,700+ MCP servers |
| 🌐 | OpenClaw releases | https://github.com/openclaw/openclaw/releases | 2026.8.1-beta.1 |
| 🌐 | OpenCode releases | https://github.com/anomalyco/opencode/releases | v1.18.18 |
| 🌐 | The Agent Report | https://the-agent-report.com/2026/08/hermes-agent-v020-herald-release-august-2026/ | Hermes v0.20.0 context |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/ante-antigmas-15mb-rust-agent-hits-827-on-terminal-bench | Ante 82.7% TB2.1 |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | Marketplace distribution landscape |
| 🌐 | Vercel blog | https://vercel.com/blog/introducing-agent-plugins | Agent Plugins intro (ongoing) |
| 🌐 | ai-boost GitHub | https://github.com/ai-boost/awesome-harness-engineering | Harness engineering awesome list |
| 🌐 | RyanAlberts | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked |
| 🇯🇵 | Gigazine | https://gigazine.net/news/20260814-deepseek-harness-v0-1/ | JP: DeepSeek Harness v0.1 全覧 |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/08/deepseek-harness-developer-preview | JP: Developer preview詳細 |
| 🇯🇵 | PC Watch | https://pc.watch.impress.co.jp/docs/news/2132785.html | JP: すべてがプラグイン |
| 🇯🇵 | Zenn (hjpotter1) | https://zenn.dev/hjpotter1/articles/4f44fcacede3b6 | JP: DeepSeek Harness手動実体験 |
| 🇯🇵 | Zenn (vector_tech) | https://zenn.dev/vector_tech_lab/articles/agent-harness-design | JP: 組織安全設計 |
| 🇯🇵 | Qiita (Ryu-Yanagi) | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | JP: ハーネスエンジニアリング完全ガイド |
| 🇯🇵 | note (masa_cloud) | https://note.com/masa_cloud/n/n2f9450f72e90 | JP: DeepSeek Harness完全ガイド |
| 🇯🇵 | aifriends.jp | https://aifriends.jp/deepseek-harness-v01-open-source/ | JP: Claude Code対抗無償公開 |
| 🇯🇵 | AIgent Lab | https://aigentlab.tech/articles/deepseek-harness-closed-beta-launch-2026/ | JP: クローズドβ712件 |
| 🇯🇵 | labmemo.com | https://labmemo.com/deepseek-harness-cordis-plugin-architecture-agent-runtime-2026/ | JP: Cordisプラグイン解説 |
| 🇯🇵 | livedoor news | https://news.livedoor.com/topics/detail/32066482/ | JP: v0.1公開報道 |
| 🇯🇵 | asi.tokyo | https://asi.tokyo/2026/08/14/deepseekが独自のハーネスを投入！/ | JP: 独自ハーネス投入 |
| 🇯🇵 | Zenn (kirilab) | https://zenn.dev/kirilab/articles/ai-agent-engineering-overview | JP: 3つのエンジニアリング整理 |
| 🇯🇵 | leadeas.co.jp | https://leadeas.co.jp/blog/harness-engineering-ai-agents-2026 | JP: Agent=Model+Harness新設計規律 |
| 🇨🇳 | Juejin (tutorial) | https://juejin.cn/post/7673390412729614390 | CN: 2万字DeepSeek Harness保姆教程 |
| 🇨🇳 | Juejin (Cordis) | https://juejin.cn/post/7673436957741236239 | CN: Cordis选型原因（来自Koishi） |
| 🇨🇳 | Juejin (arch) | https://juejin.cn/post/7673390412729155638 | CN: 架构研究与上手指南 |
| 🇨🇳 | Juejin (plugin) | https://juejin.cn/post/7673506180662755363 | CN: 一切皆插件解读 |
| 🇨🇳 | Juejin (dsh-TUI) | https://juejin.cn/post/7673679501595213834 | CN: dsh-TUI变体 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071365150741881632 | CN: 黑鲸来啦——国产版Codex |
| 🇨🇳 | Zhihu Q&A | https://www.zhihu.com/question/2071507868952662321 | CN: 有什么亮点？ |
| 🇨🇳 | Zhihu (survey) | https://zhuanlan.zhihu.com/p/2045588090547447756 | CN: 最新综述讲透DeepSeek Harness |
| 🇨🇳 | CSDN | https://blog.csdn.net/GreenHands495/article/details/163758358 | CN: 开源解读 |
| 🇨🇳 | openclaw.club | https://openclaw.club/archives/deepseek-harness-official-release | CN: 安卓时刻 |
| 🇨🇳 | uuaihub | https://www.uuaihub.com/blog/deepseek-harness-agent-framework | CN: 4.6万星深度解析 |
| 🇨🇳 | cnblogs | https://www.cnblogs.com/sing1ee/p/22455466 | CN: 完全指南 |
| 🇨🇳 | Tony Bai | https://tonybai.com/2026/08/14/deepseek-harness-everything-is-a-plugin/ | CN: 深度解读 |
| 🇨🇳 | aitoolly | https://aitoolly.com/zh/ai-news/article/2026-08-14-deepseek-launches-harness-developer-preview | CN: 预览版深度解析 |
| 🇨🇳 | jdon.com | https://www.jdon.com/93962-deepseek-harness-developer-preview.html | CN: 思维链全公开 |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 5 threads │ ~1,100+ pts │ ~600+ comments
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: 0 posts │ 0 on-topic (bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 ~22 │ 🇨🇳 ~22
└─ 🗣️ Top voices: deepseek-ai (HN 678 pts), AntigmaLabs (HN 135 pts), Ryu-Yanagi Qiita 🇯🇵, tonybai.com 🇨🇳
```

---

## Out of Scope but Notable

- **DeepSeek-V4-Pro-0813 benchmarks:** vendor-reported 87.9% Terminal-Bench 2.1, DeepSWE 62.7 (+390% from preview) — no independent verification. Out-of-scope (foundation model), but the harness–model performance coupling means watchers of this topic need to know. Sources: https://dsv4pro.novcog.us.com/ · https://www.techtimes.com/articles/324241/20260813/deepseek-v4-pro-0813-goes-ga-benchmark-claims-await-independent-proof.htm

- **Harness engineering research context:** OSSInsight reports that swapping harness alone moved same model from 23% to 52% pass@1 on GLM-5.2 and from 15% to 36% on Gemma 4 26B — more than many model upgrades. Belongs to `harness-engineering-paradigm` thread but as standalone data point this is striking. Source: https://ossinsight.io/trending/ai

---

## Data Gaps

- **Reddit, X/Twitter, YouTube, TikTok, Instagram:** not accessed — entire social signal layer absent. DeepSeek Harness launch likely generated significant volume on these platforms (especially X and Reddit).
- **/last30days skill:** unavailable in this run — social platform data (Reddit, X, TikTok, Instagram, YouTube, Polymarket, Bluesky) not collected via the skill. WebSearch + WebFetch substituted for English, JP, CN web passes.
- **Bluesky:** SOURCE HEALTH bluesky=OK; 0 on-topic posts found
- **V4-Pro benchmark independence:** all DeepSeek-V4-Pro-0813 performance numbers are vendor-reported; no independent third-party reproduction as of Aug 14
- **PenguinHarness star count:** not retrieved; Product Hunt upvotes (66) are the only engagement signal
- **DeepSeek Harness non-English community:** Zenn hands-on article references (Zenn author linked to HN), suggesting JP developers are running it already, but only one Zenn article retrieved (rate-limited)
- **Coverage estimate: 75%** — HN and English web comprehensive; JP and CN passes captured DeepSeek Harness extensively; social layer (Reddit, X, TikTok, Instagram, YouTube) fully absent; Bluesky found nothing

---

## Key Quotes

> "DeepSeek opens the agent framework it used to benchmark its own models." — AlphaSignal ([link](https://alphasignal.ai/news/deepseek-harness-opens-the-agent-framework-it-used-to-benchmark-its-own-models)) 🌐

> "US models won't let you see [complete reasoning traces]" — SwellJoe on HN DeepSeek Harness thread ([link](https://news.ycombinator.com/item?id=49285244)) 🌐

> 🇨🇳「Agent时代的安卓」("Android for the Agent era") — CN community framing for DeepSeek Harness open-ecosystem positioning ([link](https://openclaw.club/archives/deepseek-harness-official-release)) 🇨🇳

> 🇨🇳「没有丝毫宣传地发布…但GitHub却爆了」("Released without any fanfare — no blog post, no social media, yet GitHub exploded") — CSDN ([link](https://blog.csdn.net/GreenHands495/article/details/163758358)) 🇨🇳

> 🇯🇵「DeepSeekがClaude Code対抗を無償公開」("DeepSeek releases Claude Code rival for free") — aifriends.jp ([link](https://aifriends.jp/deepseek-harness-v01-open-source/)) 🇯🇵

> "plugin fatigue from incompatible versions and abandoned community extensions represents a known ecosystem risk that requires strong governance" — invaliduser on HN ([link](https://news.ycombinator.com/item?id=49285244)) 🌐

> "Subagents with `subagent_type: 'fork'` inherit the full conversation and prompt cache." — Claude Code v2.1.232 changelog ([link](https://dev.classmethod.jp/en/articles/20260814-cc-updates-v2-1-232/)) 🌐

> "Cordis implements 'destructor propagation' similar to C++ RAII, allowing components to clean up resources when disabled." — lxdlam on HN ([link](https://news.ycombinator.com/item?id=49285244)) 🌐
