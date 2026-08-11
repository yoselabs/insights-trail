# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-11
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 5 threads | 350+ pts, 200+ comments | Show HN: Ante (135 pts), Building Advanced Harness (127 pts), Agent in 9 Lines (noted), containerization Ask HN |
| X/Twitter | — | — | Not accessed |
| Reddit | — | — | Not accessed |
| YouTube | — | — | Not accessed |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 SOURCE HEALTH bluesky=OK; no on-topic posts found |
| Polymarket | 0 markets | — | No agent harness markets found |
| Web (global) | ~55 pages | — | 🌐 WebSearch + WebFetch; 13 search queries |
| Web (Japan) | ~17 pages | — | 🇯🇵 DDG HTML + WebSearch (Qiita, Zenn, gihyo.jp, gamebusiness.jp, aws.amazon.com/jp) |
| Web (China) | ~20 pages | — | 🇨🇳 DDG HTML + WebSearch (Juejin, Zhihu, CSDN, Sina Finance, Sohu, SegmentFault, Tencent Cloud) |

---

## Synthesized Findings

### 1. [new] Agent Plugins 1.0: Multi-Vendor Open Standard — Anthropic Conspicuously Absent 🌐🇯🇵🇨🇳

**Claim:** Aug 6 — OpenAI, Amazon, Microsoft, Cursor/Anysphere, Vercel, GitHub, and Google (Core Maintainer) launched Agent Plugins 1.0: a packaging standard for Agent Skills + MCP servers. Anthropic — which authored the SKILL.md spec the standard builds on — is not in the coalition and Claude Code is not a launch client.

**Evidence:**
- **Format:** `plugin.json` at root + `skills/` dir + `mcp.json` — one directory, works across ChatGPT, Codex, Cursor, GitHub Copilot, Kiro, VS Code without rewriting
- **Steering committee:** Amazon, Cursor, Microsoft, OpenAI, Vercel; governance via Linux Foundation's AAIF
- **Anthropic's layout** differs: `.claude-plugin/plugin.json` (hidden path); uses `claude.md` not `agents.md`; richer features (custom subagents, hooks, LSP servers) kept out of shared spec
- **Compatibility:** Agent Plugins work with Claude Code via compatibility layers, but authors need dual layouts for full coverage
- **Technical assessment (devclass.com):** "Anthropic, which authored the underlying Agent Skills specification, is absent" — "The absence suggests Anthropic is betting on richer, platform-specific capabilities over the coalition's portable-but-minimal approach"
- **Governance:** spec at agent-plugins.org; AWS toolkit: github.com/awslabs/agent-plugins
- 🇯🇵 **JP:** gihyo.jp full coverage; gamebusiness.jp (Publickey):「ただしClaude Codeを提供しているAnthropicは沈黙しています」("Anthropic, which provides Claude Code, remains silent") — finance.biggo.jp: "industry avoids standards debate, prioritizes implementation"
- 🇨🇳 **CN:** Sina Finance mobile headline: 「六巨头定AI插件新标准！撞脸Claude，Anthropic没上桌」("Six tech giants set new AI plugin standard! Looks like Claude, but Anthropic wasn't at the table"); xzhibot.com: 「Anthropic 缺席」("Anthropic absent") framing dominant

**Sources:** https://thenextweb.com/news/openai-agent-plugins-open-standard-skills-mcp · https://www.devclass.com/devops/2026/08/08/ai-titans-to-tidy-agent-frontier-with-plugin-prescription/5285044 · https://agenticskills.io/learn/what-are-agent-plugins · https://alphasignal.ai/news/openai-microsoft-and-cursor-unite-behind-agent-plugins-to-end-fragmented-ai · https://github.com/awslabs/agent-plugins · https://gihyo.jp/article/2026/08/agent-plugins · https://www.gamebusiness.jp/article/2026/08/11/27666.html · https://aws.amazon.com/jp/blogs/news/aws-supports-agent-plugins-an-open-standard-for-portable-agent-extensions/ · https://finance.sina.cn/stock/jdts/2026-08-07/detail-inimnrap3178266.d.html · https://xzhibot.com/3331.html · https://segmentfault.com/a/1190000048142096 · https://developer.cloud.tencent.com/article/2723596 · https://qiita.com/picnic/items/936c7b6ceeda4449a6b1 · https://zenn.dev/aws_japan/articles/agent-plugins-1-0-deep-dive · https://weel.co.jp/media/tech/agent-plugins · https://www.digitalapplied.com/blog/agent-plugins-1-0-open-standard-portable-ai-skills

---

### 2. [new] Cloudflare OS + Kitesurf: Infrastructure Layer for the Agentic Web 🌐🇯🇵🇨🇳

**Claim:** Aug 5-7 — Cloudflare shipped two agent infrastructure primitives: Cloudflare OS (open-source enterprise agent workspace, Apache 2.0) and Kitesurf (agent-first browser in Rust, running in V8 isolates, 3-7x less CPU/memory than Chromium).

**Evidence — Cloudflare OS (Aug 5):**
- Open-source AI "operating system" for org-internal agents; first deployed at Cloudflare itself (May 2026)
- **Components:** (1) Agent Workspace (browser UI, isolated runtime, org context); (2) Gatekeepers (Workers mediating external tool access, zero-default capability grants, observation logs); (3) App Platform (full-stack via Dynamic Workers + Durable Object Facets + SQLite)
- **Security:** agents start with zero access; capabilities explicitly granted; data flow observation prevents unauthorized sharing; model-agnostic via AI Gateway
- **MCP integration:** built-in; deploy into own Cloudflare account
- **HN engagement:** 659 pts, 331 comments (Aug 5)
- **Repos:** github.com/cloudflare/cloudflare-os · github.com/cloudflare/cloudflare-os-starter
- 🇨🇳 AGIDaily: 「一次对 SaaS 架构的根本性挑战」("a fundamental challenge to SaaS architecture"); Juejin deep analysis: 「Cloudflare 把 Agent 平台捐了出来」("Cloudflare donates the agent platform")

**Evidence — Cloudflare Kitesurf (Aug 7):**
- Agent-first browser, no Chromium; built in Rust + WebAssembly; CDP-compatible
- **Architecture:** Engine (CDP + session state) + PageScript (isolated Dynamic Workers per page; Blitz HTML, Stylo CSS) + PageRenderer (WASM pixel gen)
- **Performance vs Chromium:**
  - Screenshots: 3.1x less CPU, 4.7x less memory
  - HTML extraction: 3.8x less CPU, 7.0x less memory
  - Wall time 1.7-1.8x slower (software render vs JIT)
- **Passes 215,000+ Web Platform Tests**; renders Wikipedia, HN, Cloudflare Blog
- **Supported:** screenshots, HTML extraction, PDF gen, DOM inspection, basic JS/WASM, CSS
- **Not supported:** video, WebGL, bot challenges, persistent authenticated sessions
- **Free beta** in Browser Run; Puppeteer/Playwright/Playwright compatible; playground at kitesurf.cloudflare.app
- **HN:** 214 pts, 61 comments
- 🇯🇵 alphamatch.ai: 「AI エージェント専用の革命的ブラウザ」("a revolutionary browser exclusively for AI agents"); zenn.dev/yusukebe: 「AIエージェントはCloudflareに賭けろ」("Bet on Cloudflare for AI agents")

**Sources:** https://blog.cloudflare.com/cloudflare-os/ · https://github.com/cloudflare/cloudflare-os · https://siliconangle.com/2026/08/05/cloudflare-launches-cloudflare-os-open-source-ai-agentic-workspace-enterprise/ · https://www.cloudflare.com/press/press-releases/2026/cloudflare-os-is-the-first-ai-workspace-built-around-how-companies-actually-work/ · https://blog.cloudflare.com/kitesurf/ · https://techcrunch.com/2026/08/07/cloudflare-launches-kitesurf-a-browser-built-for-ai-agents/ · https://developers.cloudflare.com/changelog/post/2026-08-06-kitesurf/ · https://www.marktechpost.com/2026/08/06/cloudflare-introduces-kitesurf-an-agent-first-web-browser-that-runs-entirely-in-v8-isolates-on-cloudflare-workers/ · https://thenextweb.com/news/cloudflare-kitesurf-browser-ai-agents-workers · https://agidaily.cc/articles/cloudflare-os-open-source-agent-platform · https://juejin.cn/post/7671662832451059750 · https://www.alphamatch.ai/ja/blog/cloudflare-kitesurf-agent-browser-2026 · https://zenn.dev/yusukebe/articles/ccb1f953e48ee1

---

### 3. [new] Ante (AntigmaLabs): 15MB Single-Binary Agent Harness, 82.7% Terminal-Bench 2.1 🌐

**Claim:** Aug 11 Show HN (135 pts, 80 comments) — Ante is a ~15MB single Rust binary, zero deps, offline-capable coding agent harness claiming 82.7% Terminal-Bench 2.1 with DeepSeek V4 Flash 0731 ("for every model we run, no other harness scores higher with that model") and 7-9x lower resource use than Claude Code.

**Evidence:**
- **Binary:** ~15MB, zero runtime dependencies; macOS + Linux; alpha since March 2026
- **Offline:** `/offline-mode` installs bundled llama.cpp; no API keys, no internet; Metal/CUDA/Vulkan/CPU auto-detect
- **12+ LLM providers:** Anthropic, OpenAI, Google, xAI, OpenRouter, local models
- **Terminal-Bench 2.1 (official leaderboard):** 82.7% with DeepSeek V4 Flash 0731 (89 tasks, 5 trials each, 368/445)
- **Resource efficiency claims (20 parallel tasks vs Claude Code):** ~7x lower peak memory, ~9x lower avg CPU, ~5x less disk I/O
- **Philosophy:** "We care about the harness, not the model or the prompts"
- **GitHub:** https://github.com/AntigmaLabs/ante · Website: https://ante.run/ · Company: https://antigma.ai/

**Sources:** https://news.ycombinator.com/item?id=49245437 · https://github.com/AntigmaLabs/ante · https://aiweekly.co/alerts/ante-antigmas-15mb-rust-agent-hits-827-on-terminal-bench · https://antigma.ai/blog/2026/03/31/introducing-ante · https://antigma.ai/eval

---

### 4. [new] TencentDB Agent Memory v2.0: Team-Level Memory Hub (MIT, Aug 3) 🌐🇨🇳

**Claim:** Tencent Cloud open-sourced TencentDB Agent Memory v2.0 (MIT, 19.7k stars, Aug 3) — a self-hosted team-level memory hub with 4-tier L0→L3 architecture and ACL-based access control, supporting OpenClaw, Hermes, Claude Code, CodeBuddy.

**Evidence:**
- **4-tier pipeline:** L0 (raw conversations) → L1 (atoms) → L2 (scenarios) → L3 (personas)
- **4 asset types:** Chat Memory, Skills, LLM-Wiki, CodeGraph
- **ACL:** private / team / restricted / agent-targeted; per-asset ownership; private not readable even by team admins
- **CodeGraph:** indexes symbols, files, call relationships, impact paths (no vector store needed)
- **Retrieval:** L2+L3 fast bootstrap; BM25 + vector + RRF fallback to L1+L0
- **Deploy:** 3 Docker images, multi-arch (linux/amd64, linux/arm64)
- **Frameworks:** OpenClaw, Hermes, Claude Code, CodeBuddy; broader support on roadmap
- 19.7k GitHub stars; trendshift.io/repositories/29310

**Sources:** https://github.com/TencentCloud/TencentDB-Agent-Memory · https://www.marktechpost.com/2026/08/07/tencent-cloud-open-sources-tencentdb-agent-memory-v2-0/ · https://explainx.ai/blog/tencentdb-agent-memory-v2-team-hub-august-2026 · https://medium.com/@ramunarasinga/tencentdb-agent-memory-a-team-level-memory-hub-for-ai-agents-aa5712c98faa · https://dev.to/dennis_pilarinos/team-memory-hubs-for-ai-agents-what-tencentdb-agent-memory-solves-and-what-it-misses-16ja

---

### 5. [update] Claude Code v2.1.225–227: Gateway Limits, Cross-Machine SendMessage, Bug Fixes 🌐

**New facts:** v2.1.225 (Aug 7): gateway spend-limit support in usage warnings; SendMessage can now target Remote Control sessions on other machines by name; workspace trust prompts for `claude agents`. v2.1.227 (Aug 11): feature flag evaluation fix; Bash failures in GitHub Actions fixed.

**Evidence:**
- **v2.1.225 (Aug 7):** Gateway spend-limit: limit-reached message names the cap, reset time, operator message; workspace trust prompt for `claude agents` in untrusted dirs (matching `claude` behavior); SendMessage cross-machine: initiate conversations on another machine's Remote Control session by name; fix transient 401 on OAuth token refresh breaking headless sessions; MCP OAuth keychain timeout fix
- **v2.1.226 (Aug 8):** Bug fixes and reliability improvements
- **v2.1.227 (Aug 11):** Feature flag evaluation fix (expired login token dropped subscription tier → wrongly prompted Max users to enable Fable credits); fix Bash command failures in claude-code-action with `allowed_non_write_users` on GitHub-hosted runners; `/tui` rewind behavior fixed; slash-command menu: blue marks only selected row, matched chars bolded; event-loop stall reduction

**Sources:** https://code.claude.com/docs/en/changelog · https://releasebot.io/updates/anthropic/claude-code · https://dev.classmethod.jp/en/articles/20260808-cc-updates-v2-1-226/ · https://www.havoptic.com/tools/claude-code · https://claudelog.com/claude-code-changelog/

---

### 6. [update] Hoplite (YC S26): HN Engagement Grows, iMessage Trigger Added 🌐

**New facts:** HN engagement now 81 pts/70 comments (was 51 at Launch HN Aug 3). iMessage trigger added — users can now spin up cloud coding agents from phone.

**Evidence:**
- Previously: 51 HN pts at launch (Aug 3, 2026)
- Now: 81 HN pts, 70 comments
- iMessage trigger now supported alongside Slack, Linear, Sentry
- Early traction: Sentry errors → proactive PRs "when something breaks"

**Sources:** https://news.ycombinator.com/item?id=49157997 · https://hoplite.sh/ · https://www.ycombinator.com/companies/hoplite

---

**Still true** (ongoing threads, no new facts this cycle):

- `meta-muse-code` — Meta Muse Code beta (Aug 5): parallel worktrees, Muse Spark 1.2, 82.9% Terminal-Bench 2.1 ($0.10/MTok contributor tier); no Aug 8-11 updates found
- `prime-agent-rlm` — Prime Agent (MIT, Aug 5): RLM harness, 95.5% ARC-AGI-3, Continual Harness CRUD; no new release
- `aq-multiplayer-harness` — AQ multiplayer coding harness; no new facts
- `qwen-code-alibaba` — Qwen Code; no new facts
- `oh-my-agent` — oh-my-agent (10+ harnesses); no new facts
- `autoharness-deepmind` — AutoHarness (DeepMind); no new facts
- `hermes-agent-self-improving` — Hermes v0.20.0 Herald Release; no Aug 8-11 updates found
- `openclaw-gateway-harness` — OpenClaw; no new facts
- `microsoft-maf-codeact` — MAF Harness GA; no new facts
- `extension-economy-explosion` — 23,600+ skills, 12,700+ MCP servers; Agent Plugins 1.0 now adds packaging layer on top
- `claude-tag-slack-agent` — Claude Tag deployed Aug 3; no new facts
- `mimo-code-xiaomi` — MiMo Code; no new facts
- `ecc-cross-harness-os` — ECC: now 238,879 stars (up from 237k); no feature changes reported
- `cursor-3-11-update` — Cursor 3.11 side chats, transcript search; no new facts
- `cursor-router-workspace-plugins` — Cursor Router (68% cheaper); no Aug 8-11 changes
- `kimi-code-moonshot` — Kimi Code; no new facts
- `runtime-yc-p26` — Runtime; no new facts
- `noclick-always-on` — NoClick; no new facts
- `nyx-offensive-testing` — Nyx (Fabraix); no new facts
- `agentguard-security-tool` — AgentGuard; no new facts
- `mcp-security-nsa-supply-chain` — Agentjacking; no new facts
- `yc-qm-multiplayer-harness` — YC QM; no new facts
- `anthropic-managed-agents-mcp-tunnels` — Claude Tag, Opus 5; no new facts (Sonnet 5 promo pricing ends Aug 31)
- `mcp-stateless-spec-2026-07-28` — MCP 2026-07-28 spec; no new facts
- `jadepuffer-agentic-security` — JADEPUFFER ransomware; no new facts
- `grok-build-xai-rust-harness` — Grok-Build Rust TUI; no new facts
- `self-harness-auto-optimization` — Self-Harness (Shanghai AI Lab); no new facts
- `openharness-hkuds` — OpenHarness; no new facts
- `vscode-1130-agent-host` — VSCode 1.130 AHP; no new facts
- `antigravity-gemini-cli-successor` — Antigravity 2.0; no new facts
- `claw-code-claude-rewrite` — Claw Code ~195k stars; no new facts
- `kiro-aws-spec-driven` — Kiro CLI v2.13.0; no new facts
- `metaharness-scaffold-generator` — MetaHarness; no new facts
- `harness-engineering-paradigm` — Agent=Model+Harness; up to 6x perf diff from harness alone; JP community still dominant on this topic
- `deerflow-superagent-harness` — DeerFlow 2.0 ByteDance; no new facts
- `omnigent-meta-harness` — Databricks Omnigent; no new facts
- `zot-go-coding-harness` — Zot Go single-binary; no new facts
- `omp-omo-pi-derivatives` — oh-my-pi + oh-my-openagent; no new facts
- `yorishiro-presence-harness` — Yorishiro macOS 3D avatar; no new facts
- `agentskills-open-standard` — SKILL.md portable across 20+ harnesses; Agent Plugins 1.0 now co-opts this format (see Finding #1)
- `letta-agent-file-format` — Letta .af format; no new facts
- `layered-oss-stack-over-single-framework` — 17+ OSS layers per task; no new facts
- `macos-harness-proving-ground` — macOS proving ground; no new facts
- `ahe-automated-harness-evolution` — arXiv AHE papers; no new facts
- `harness-internal-external-disambiguation` — Internal vs External Harness; no new facts
- `environment-architect-new-role` — JP: 環境設計者 role; still dominant JP framing
- `warp-oz-multi-harness` — Warp Oz; no new facts
- `mozilla-otari-llm-gateway` — Mozilla Otari; no new facts
- `statewright-guardrails` — Statewright state machine guardrails; no new facts
- `headroom-token-compression` — Headroom: now 65,567 stars (up from 62k)
- `pi-minimal-agent-harness` — Pi: now 85,757 stars (up from 54k in prior cycle — significant growth)
- `nvidia-skillspector-security` — SkillSpector; no new facts
- `deepseek-harness-team` — DeepSeek Harness team + Reasonix; no new facts
- `cli-anything-hkuds` — CLI-Anything; no new facts
- `forge-acp-universal-cli` — Forge ACP; no new facts
- `github-copilot-skills-mcp-ga` — Copilot skills+MCP GA; no new facts (now part of Agent Plugins ecosystem)
- `opencode-anomaly-rebrand` — OpenCode (Anomaly): v1.18.12-15 in Aug (MCP fixes, OAuth, tab nav, JSON export); steady iteration
- `cursor-spacex-acquisition` — SpaceX $60B acquisition, closing Q3 2026; no new facts
- `block-buzz-workspace` — Block Buzz Nostr ACP workspace; no new facts
- `zcode-zhipu-agent-ide` — ZCode (Z.ai); no new facts
- `devin-desktop-windsurf-rebrand` — Devin Desktop: editor context awareness added, Always Allow persists across sessions; no major feature news
- `devin-fusion-multimodel` — Devin Fusion; no new facts
- `ambiance-unix-harness` — Ambiance; no new facts
- `kore-artemis-abl` — Kore.ai Artemis ABL; no new facts
- `open-agent-passport-oap` — OAP; no new facts
- `code-as-agent-harness-paper` — arXiv:2605.18747; no new facts
- `tilde-harness-sdk` — Tilde; no new facts
- `microsoft-agent-governance-toolkit` — AGT; no new facts
- `tinyagents-rust-recursive` — TinyAgents; no new facts
- `sprocket-hardware-software-agent` — Sprocket; no new facts
- `gambit-reliable-agent-harness` — Gambit; no new facts
- `nlah-natural-language-harnesses` — NLAH; no new facts
- `skills-security-prompt-injection-36pct` — 36% prompt injection in skills; no new facts
- `copilot-studio-ga-harness-billing` — Copilot Studio billing; no new facts
- `vercel-ai-sdk-harnessagent` — Vercel AI SDK v7 HarnessAgent; no new facts

---

## Cross-Source Patterns

### Pattern 1: The SKILL.md Fork — Coalition Adopts Anthropic's Format, Excludes Anthropic 🌐🇯🇵🇨🇳
**Platforms:** thenextweb.com, devclass.com, AlphaSignal, gihyo.jp, Qiita, gamebusiness.jp, Sina Finance CN, xzhibot.com CN

Agent Plugins 1.0 builds on Anthropic's open Agent Skills spec (SKILL.md) but Anthropic is absent from the 7-company coalition and Claude Code is not a launch client. The standard is "portable but minimal" — omitting Claude Code's richer plugin capabilities (custom subagents, hooks, LSP servers). The JP and CN press both called this out explicitly as the defining story.

> "Anthropic, which authored the underlying Agent Skills specification, is absent — suggesting Anthropic is betting on richer, platform-specific capabilities over the coalition's portable-but-minimal approach." — devclass.com ([link](https://www.devclass.com/devops/2026/08/08/ai-titans-to-tidy-agent-frontier-with-plugin-prescription/5285044)) 🌐

---

### Pattern 2: Cloudflare Pivots to Agent Infrastructure Layer 🌐🇯🇵🇨🇳
**Platforms:** Cloudflare Blog, TechCrunch, SiliconAngle, Juejin, Zenn, alphamatch.ai JP

Cloudflare OS (Aug 5) + Kitesurf (Aug 7) represent a coherent infrastructure thesis: every agent needs an execution environment (Workers), a browser (Kitesurf), a memory (Agent Memory), a gateway (AI Gateway), and security (Gatekeepers). CN press framed this as "fundamental challenge to SaaS architecture."

> "Cloudflare built a browser for AI agents. It uses 7x less memory than Chromium and runs entirely on Workers." — thenextweb.com ([link](https://thenextweb.com/news/cloudflare-kitesurf-browser-ai-agents-workers)) 🌐

---

### Pattern 3: Minimal Harness Counter-Trend — Single Binary Resurgent 🌐
**Platforms:** HN Show HN (135 pts), aiweekly.co, antigma.ai

Ante (15MB Rust binary) joins Zot and Pi in a counter-trend to bloated harnesses. "We care about the harness, not the model or the prompts" — positioning where the harness architecture itself is the core product claim. Ante claims best-in-class harness efficiency per model and 82.7% Terminal-Bench 2.1 with open models. HN comments echoed the Pi/Ambiance anti-bloat sentiment.

> "We care about the harness, not the model or the prompts." — Antigma Labs / Ante ([link](https://news.ycombinator.com/item?id=49245437)) 🌐

---

### Pattern 4: CN Developer Spotlight — Anthropic's Ecosystem Position Under Scrutiny 🇨🇳
**Platforms:** Sina Finance CN mobile, xzhibot.com, Juejin

Agent Plugins 1.0 has become a flashpoint in the CN developer community: the standard "looks exactly like Claude" but Anthropic was not at the table. Combined with existing discussion about MCP/A2A/AG-UI protocol fragmentation (from prior cycle), CN community is tracking Anthropic's ecosystem influence vs market competitors.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| AntigmaLabs | Show HN: Ante, a coding agent in a single binary that runs offline | 135 | 80 | "We care about the harness, not the model or the prompts" | https://news.ycombinator.com/item?id=49245437 |
| — | Building an Advanced Agentic Harness | 127 | 43 | "smol minimalist system benchmarks cheaper+faster than orchestrated frameworks" | https://news.ycombinator.com/item?id=49182946 |
| — | Show HN: Agent in 9 Lines Python | ~noted | — | Agent with tool calling, no kitchen-sink deps | https://news.ycombinator.com/item?id=49006862 |
| — | Ask HN: AI Agent and harness containerization/security recommendations | — | active | sandboxing discussion for agents running local+network commands | https://news.ycombinator.com/item?id=48899674 |
| tosh | qm – Multiplayer agent harness for work | 665 | 161 | AQ dev: "validating for the market direction" | https://news.ycombinator.com/item?id=49126604 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | The Next Web | https://thenextweb.com/news/openai-agent-plugins-open-standard-skills-mcp | Agent Plugins 1.0 overview, coalition |
| 🌐 | DevClass | https://www.devclass.com/devops/2026/08/08/ai-titans-to-tidy-agent-frontier-with-plugin-prescription/5285044 | Anthropic's absence analysis |
| 🌐 | AlphaSignal | https://alphasignal.ai/news/openai-microsoft-and-cursor-unite-behind-agent-plugins-to-end-fragmented-ai | Fragmentation problem solved |
| 🌐 | AgenticSkills | https://agenticskills.io/learn/what-are-agent-plugins | Complete standard guide |
| 🌐 | AWS GitHub | https://github.com/awslabs/agent-plugins | Official plugin toolkit |
| 🌐 | Cloudflare Blog | https://blog.cloudflare.com/cloudflare-os/ | Cloudflare OS official |
| 🌐 | Cloudflare Blog | https://blog.cloudflare.com/kitesurf/ | Kitesurf architecture details |
| 🌐 | TechCrunch | https://techcrunch.com/2026/08/07/cloudflare-launches-kitesurf-a-browser-built-for-ai-agents/ | Kitesurf launch |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/08/05/cloudflare-launches-cloudflare-os-open-source-ai-agentic-workspace-enterprise/ | Cloudflare OS enterprise angle |
| 🌐 | Cloudflare Dev | https://developers.cloudflare.com/changelog/post/2026-08-06-kitesurf/ | Official changelog |
| 🌐 | GitHub cloudflare-os | https://github.com/cloudflare/cloudflare-os | Open-source code |
| 🌐 | Phoronix | https://www.phoronix.com/news/Cloudflare-OS | Open-source coverage |
| 🌐 | The Next Web | https://thenextweb.com/news/cloudflare-kitesurf-browser-ai-agents-workers | 7x memory reduction |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/06/cloudflare-introduces-kitesurf-an-agent-first-web-browser-that-runs-entirely-in-v8-isolates-on-cloudflare-workers/ | V8 isolates detail |
| 🌐 | HN: Ante | https://news.ycombinator.com/item?id=49245437 | 135 pts Show HN |
| 🌐 | GitHub: AntigmaLabs/ante | https://github.com/AntigmaLabs/ante | Ante source |
| 🌐 | AI Weekly | https://aiweekly.co/alerts/ante-antigmas-15mb-rust-agent-hits-827-on-terminal-bench | 82.7% Terminal-Bench |
| 🌐 | antigma.ai | https://antigma.ai/blog/2026/03/31/introducing-ante | Ante intro |
| 🌐 | GitHub: TencentDB | https://github.com/TencentCloud/TencentDB-Agent-Memory | TencentDB v2.0 |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/07/tencent-cloud-open-sources-tencentdb-agent-memory-v2-0/ | v2.0 launch |
| 🌐 | Medium (ramu) | https://medium.com/@ramunarasinga/tencentdb-agent-memory-a-team-level-memory-hub-for-ai-agents-aa5712c98faa | Team memory explainer |
| 🌐 | DEV.to | https://dev.to/dennis_pilarinos/team-memory-hubs-for-ai-agents-what-tencentdb-agent-memory-solves-and-what-it-misses-16ja | What it misses analysis |
| 🌐 | Classmethod JP | https://dev.classmethod.jp/en/articles/20260808-cc-updates-v2-1-226/ | CC v2.1.225-226 details |
| 🌐 | Havoptic | https://www.havoptic.com/tools/claude-code | CC v2.1.227 summary |
| 🌐 | Hoplite | https://hoplite.sh/ | Cloud agent deploy |
| 🌐 | HN: Hoplite | https://news.ycombinator.com/item?id=49157997 | 81 pts |
| 🌐 | GitHub: farion1231/cc-switch | https://github.com/farion1231/cc-switch | 93k+ star desktop switcher |
| 🌐 | Builder Radar | https://buttondown.com/Builder-Radar/archive/builder-radar-week-of-august-9-2026/ | Aug 9 week trending |
| 🌐 | ExplainX | https://explainx.ai/blog/agent-plugins-openai-standard-aws-cursor-github-vscode-2026 | Agent Plugins guide |
| 🌐 | kingy.ai | https://kingy.ai/blog/openai-agent-plugins-open-standard/ | Standard explainer |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/agent-plugins-1-0-open-standard-portable-ai-skills | What 1.0 fixes |
| 🌐 | eesel AI | https://www.eesel.ai/blog/agent-plugins | Agent Plugins overview |
| 🌐 | n8n Lab | https://n8nlab.io/news/agent-plugins-universal-standard-ai-components | Universal standard |
| 🌐 | Decrypt | https://decrypt.co/374997/cloudflare-os-inside-open-source-ai-agent-platform | Inside Cloudflare OS |
| 🌐 | digitaltrends | https://www.digitaltrends.com/computing/cloudflares-new-browser-kitesurf-is-designed-for-ai-agents-to-browse-the-internet/ | Kitesurf consumer angle |
| 🌐 | Releasebot | https://releasebot.io/updates/anthropic/claude-code | CC release tracker |
| 🌐 | Explainx Ante | https://explainx.ai/blog/tencentdb-agent-memory-v2-team-hub-august-2026 | TencentDB explainer |
| 🌐 | aiweekly.co | https://aiweekly.co/alerts/cloudflare-launches-kitesurf-a-rust-browser-built-for-ai-agents | Kitesurf Rust browser |
| 🌐 | ante.run | https://ante.run/ | Ante product site |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/08/agent-plugins | JP: Agent Plugins official |
| 🇯🇵 | gamebusiness.jp | https://www.gamebusiness.jp/article/2026/08/11/27666.html | JP: Anthropic silent |
| 🇯🇵 | AWS JP blog | https://aws.amazon.com/jp/blogs/news/aws-supports-agent-plugins-an-open-standard-for-portable-agent-extensions/ | JP: AWS official |
| 🇯🇵 | finance.biggo.jp | https://finance.biggo.jp/news/287756f7-b7bb-4921-8ed7-85c509161fa6 | JP: industry pragmatic framing |
| 🇯🇵 | weel.co.jp | https://weel.co.jp/media/tech/agent-plugins | JP: Agent Plugins guide |
| 🇯🇵 | Qiita (picnic) | https://qiita.com/picnic/items/936c7b6ceeda4449a6b1 | JP: Agent Plugins 1.0 explainer |
| 🇯🇵 | Zenn (aws_japan) | https://zenn.dev/aws_japan/articles/agent-plugins-1-0-deep-dive | JP: What it standardized vs not |
| 🇯🇵 | alphamatch.ai | https://www.alphamatch.ai/ja/blog/cloudflare-kitesurf-agent-browser-2026 | JP: Kitesurf |
| 🇯🇵 | Zenn (yusukebe) | https://zenn.dev/yusukebe/articles/ccb1f953e48ee1 | JP: "Bet on Cloudflare for AI agents" |
| 🇯🇵 | Qiita (Ryu-Yanagi) | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | JP: Harness Engineering guide |
| 🇯🇵 | note.com | https://note.com/fond_fennel4377/n/n531cb4eb88ca | JP: Harness engineering |
| 🇨🇳 | Sina Finance CN | https://finance.sina.cn/stock/jdts/2026-08-07/detail-inimnrap3178266.d.html | CN: Anthropic not at table |
| 🇨🇳 | xzhibot.com | https://xzhibot.com/3331.html | CN: Anthropic absent framing |
| 🇨🇳 | Juejin | https://juejin.cn/post/7671662832451059750 | CN: Cloudflare OS deep analysis |
| 🇨🇳 | Sohu | https://www.sohu.com/a/1059633862_114838 | CN: Cloudflare OS |
| 🇨🇳 | AGIDaily | https://agidaily.cc/articles/cloudflare-os-open-source-agent-platform | CN: SaaS architecture challenge |
| 🇨🇳 | SegmentFault | https://segmentfault.com/a/1190000048142096 | CN: Agent Plugins cross-client |
| 🇨🇳 | Tencent Cloud Dev | https://developer.cloud.tencent.com/article/2723596 | CN: Agent Plugins explainer |
| 🇨🇳 | Juejin/技术栈 | https://jishuzhan.net/article/2086991808977846273 | CN: Agent Plugins + MCP hands-on |
| 🇨🇳 | jiazhuangai.com | https://www.jiazhuangai.com/articles/-agent-plugins-10ai-agent- | CN: 5 vendors unified format |
| 🇨🇳 | coodoor.com | https://www.coodoor.com/2026/08/cloudflareai-agentcloudflare-os.html | CN: Cloudflare OS surprise |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2014376030144579565 | CN: 2026 AI Agent deep review |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2003203520984264788 | CN: Coding Agent panorama report |
| 🇨🇳 | CSDN | https://blog.csdn.net/u012725843/article/details/156166502 | CN: 8 tools new era |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 5 threads │ ~350+ points │ ~200+ comments
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: 0 on-topic posts (searched, none found; bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 ~17 │ 🇨🇳 ~20
└─ 🗣️ Top voices: AntigmaLabs (Ante Show HN), devclass.com (Anthropic analysis), gihyo.jp 🇯🇵, gamebusiness.jp 🇯🇵, Sina Finance CN 🇨🇳
```

---

## Out of Scope but Notable

- **cc-switch (farion1231, 93k+ stars):** Cross-platform desktop All-in-One Tauri 2 app managing 8 coding agents (Claude Code, Codex, OpenCode, OpenClaw, Gemini CLI, Grok Build, Hermes, Claude Desktop). Not a harness per se; a harness manager. Borderline in-scope. ([link](https://github.com/farion1231/cc-switch))
- **MemPalace (58,243 stars):** "Best-benchmarked open-source AI memory system" (April 2026); not agent-harness-specific but trending alongside harness tooling. ([link](https://github.com/MemPalace/mempalace))
- **Graphify-Labs/graphify (104,429 stars):** Turns codebases, SQL schemas, PDFs into queryable knowledge graphs via AST parsing; no vector store. Positioned as harness-compatible context provider but not itself a harness. ([link](https://github.com/Graphify-Labs/graphify))
- **Kilo Code/Kilo Marketplace:** VS Code AI coding extension (Cline/Roo Code fork, $8M seed, 1.5M users); Kilo Marketplace curates Skills/MCP/Modes for Kilo ecosystem following SKILL.md spec. Agent Plugins 1.0 compatible. Likely fits `extension-economy-explosion` thread. ([link](https://github.com/Kilo-Org/kilo-marketplace) · [link](https://kilo.ai/))

---

## Data Gaps

- **last30days skill unavailable:** not in skill registry for this run — social platform data (Reddit, X, TikTok, Instagram, Bluesky, YouTube, Polymarket) not collected via skill
- **Bluesky:** SOURCE HEALTH bluesky=OK; searched but found 0 on-topic posts
- **Reddit/X/YouTube/TikTok/Instagram:** Not accessed — social signal gap for Agent Plugins 1.0 reactions
- **Ante star count:** Not retrieved (GitHub rate limited on HN fetch); HN points/comments confirmed
- **Cloudflare OS HN link:** HN ID not found separately; counts from press coverage (659 pts confirmed)
- **Agent Plugins — no primary reason from Anthropic:** No official Anthropic statement on absence found; analysis from devclass.com is the best available
- **Approximate coverage:** 72% — HN and English web comprehensive; JP/CN passes captured Agent Plugins 1.0 and Cloudflare OS reaction well; social platforms entirely absent

---

## Key Quotes

> "Anthropic, which authored the underlying Agent Skills specification, is absent — suggesting Anthropic is betting on richer, platform-specific capabilities over the coalition's portable-but-minimal approach." — devclass.com ([link](https://www.devclass.com/devops/2026/08/08/ai-titans-to-tidy-agent-frontier-with-plugin-prescription/5285044)) 🌐

> "We care about the harness, not the model or the prompts." — AntigmaLabs / Ante Show HN ([link](https://news.ycombinator.com/item?id=49245437)) 🌐

> "Cloudflare built a browser for AI agents. It uses 7x less memory than Chromium and runs entirely on Workers." — The Next Web ([link](https://thenextweb.com/news/cloudflare-kitesurf-browser-ai-agents-workers)) 🌐

> 🇯🇵「ただしClaude Codeを提供しているAnthropicは沈黙しています」
> ("However, Anthropic, which provides Claude Code, remains silent") — gamebusiness.jp / Publickey ([link](https://www.gamebusiness.jp/article/2026/08/11/27666.html)) 🇯🇵

> 🇨🇳「六巨头定AI插件新标准！撞脸Claude，Anthropic没上桌」
> ("Six tech giants set new AI plugin standard! Looks like Claude but Anthropic wasn't at the table") — Sina Finance Mobile ([link](https://finance.sina.cn/stock/jdts/2026-08-07/detail-inimnrap3178266.d.html)) 🇨🇳

> 🇨🇳「一次对 SaaS 架构的根本性挑战」
> ("A fundamental challenge to SaaS architecture") — AGIDaily on Cloudflare OS ([link](https://agidaily.cc/articles/cloudflare-os-open-source-agent-platform)) 🇨🇳

> 🇯🇵「AIエージェントはCloudflareに賭けろ」
> ("Bet on Cloudflare for AI agents") — zenn.dev/yusukebe ([link](https://zenn.dev/yusukebe/articles/ccb1f953e48ee1)) 🇯🇵

> "The Ante harness hits 82.7% on Terminal-Bench 2.1 with DeepSeek V4 Flash 0731 — for every model we run, no other harness scores higher with that model." — antigma.ai ([link](https://antigma.ai/eval)) 🌐
