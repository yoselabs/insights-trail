# AI Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-10-16
**Query type:** GENERAL
**Sources:** WebSearch (🌐 English), WebSearch (🇯🇵 Japanese), WebSearch (🇨🇳 Chinese), WebFetch (blogs/changelogs/GitHub), Hacker News

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 stories | ~10 pts combined | Show HN: Faplex, Galahad, pentest harness |
| Web (global) | 48 pages | — | 🌐 WebSearch + changelog fetches |
| Web (Japan) | 9 pages | — | 🇯🇵 Zenn, Qiita, gihyo.jp, note.com, ITmedia |
| Web (China) | 10 pages | — | 🇨🇳 Zhihu, CSDN, Juejin, Tencent Cloud, cnblogs, Sohu |

---

## Synthesized Findings

### 1. [update] Hermes Agent v0.22.0 "The Threshold Release" — largest-ever update, ~251k stars

**Claim:** Oct 14: local model one-click deployment, Gmail/Linear/Notion connectors, guided onboarding, 600-plugin catalog, codebase −34%.
**Evidence:**
- **Scale:** ~24,200 commits, 6,080 merged PRs, 2.045M code insertions since v0.21.0; 7,180 closed issues
- **Connectors:** Gmail, Linear, Notion via Nous tool gateway; one-click browser sign-in; multiple named accounts per app; Connectors page replaces MCP tab
- **Local models:** One-click llama.cpp; hardware-specific engine auto-selected (CPU/CUDA/Metal/Vulkan/ROCm); auto-rates catalog models against GPU/RAM; includes Qwen3.8 27B, Qwen3.8 Flash Next, Qwen3.6 35B-A3B, DeepSeek V4 Flash, any GGUF from HF
- **Onboarding:** Fresh install opens guided chat on free `nous/welcome` trial model (one-time per OS user) — no API key required to start
- **Architecture:** Single gateway + backend per machine for all profiles (was one-process-per-profile); SemVer stable channel; signed MSIX + Apple Silicon builds
- **Bot Screen:** Take-over UI for watching/controlling agent actions live
- v0.22.1 (Oct 15): Korean + Brazilian Portuguese packs; TeamoRouter; lightningai/openinvest plugins
- v0.22.2 (Oct 15): Gateway restart reliability; Nemotron Super 3.5 defaults
- 🌐 Sources: https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0 | https://aicoder.com/news/news-20261014-hermes-agent-v0-22-threshold-release-local-models-connectors | https://www.tao.media/nous-research-ships-hermes-agent-threshold-release-with-guided-setup-app-connectors-and-one-click-local-models/
- 🇨🇳 Coverage: https://www.sohu.com/a/1087812264_122977613 | https://developer.cloud.tencent.com/article/2715416 | https://zhuanlan.zhihu.com/p/2026622473097978502
- 🇯🇵 Coverage: https://ai-garage.jp/column/hermes-agent-updates-2026/

---

### 2. [update] Claude Code v2.1.294–301: idle compaction, AWS advisor, OTel tool_decision, hook validation

**Claim:** Oct 9–15: five releases; idle compaction, /advisor on AWS, OTel classifier attrs, hook input validation hardened.
**Evidence:**
- **v2.1.294** (Oct 9): Fix blocking stop hooks
- **v2.1.296** (Oct 9): `code` gateway key; subagent auto-compact windows; `allow_large` Read; workflow prompt/model rewriting
- **v2.1.299** (Oct 14): **Idle compaction** — 200K+ token sessions auto-compact after 54 min idle (aligns with prompt cache expiry); `CLAUDE_CODE_DISABLE_FILE_MENTIONS`; UserPromptSubmit hooks run before skill expansion; Shift-JIS encoding fix (rejects instead of auto-converting)
- **v2.1.300** (Oct 14): 88 changes; 51 bug fixes (sessions/worktrees/hangs/cloud); `/advisor` command on Claude Platform on AWS; hook `updatedInput` validated (unknown keys dropped, tool-rejected input denies call)
- **v2.1.301** (Oct 15): `classifier_verdict`, `permission_mode`, `classifier_category` attrs on OTel `tool_decision`; Vim `%` bracket jump; mod `rows` param; `CLAUDE_CODE_RETRY_WATCHDOG_MAX_USAGE_LIMIT_WAIT_MS`; binary file fixes (.parquet, .xlsm, .epub, .heic); long conversations summarized before model switch
- 🌐 Sources: https://releasebot.io/updates/anthropic/claude-code | https://dev.classmethod.jp/en/articles/20261016-cc-updates-v2-1-301/ | https://www.claudeupdates.dev/version/2.1.300
- 🇯🇵 Shift-JIS fix resonates strongly: https://note.com/fair_godwit407/n/n4465a4348330

---

### 3. [update] OpenClaw 2026.10.x — Gemini 4 Argon default, restart-safe replies, Gateway SQLite rewrite

**Claim:** Oct 13–15: Gemini 4 Argon as default Gemini model; restart-safe reply resumption; faster Gateway (less SQLite).
**Evidence:**
- **2026.10.10-beta.1** (Oct 15): Gemini 4 Argon new default (+ Gemini 3.8 Flash kept); Nemotron 3.5 Super VL; xAI Imagine Image 2.0; Meta Muse Wonder via Muse Code; retired models removed from pickers; **faster Gateway** (less SQLite + main-thread work); **restart-safe replies** resume after Gateway restart; cloud session management with env recipes; local Gateway in desktop apps
- **2026.9.33** (Oct 15, Extended Stable): Work survives Gateway restarts; pnpm 12/npm/Windows compat; Meta Muse Wonder + MiniMax M3.1
- **2026.10.5-beta.3** (Oct 13): Claude CLI sessions call OpenClaw tools by MCP names; plugin SDK restored; Windows/macOS/pnpm12 update reliability
- **2026.10.5-beta.4** (Oct 15): ChatGPT models on Codex runtime
- **2026.10.2** (stable): Cleaner upgrades; stronger secret redaction; steadier prompt caching
- SQLite WAL P0 OOM: not resolved in these releases (still open)
- 🌐 Sources: https://releasebot.io/updates/openclaw | https://openclawlaunch.com/changelog | https://www.bighatgroup.com/blog/openclaw-weekly-2026-10-12/
- 🇨🇳 Coverage: https://cloud.tencent.com/developer/article/2658963

---

### 4. [update] VS Code 1.141 / 1.141.1 — unified Copilot harness, cross-platform sandboxing GA, critical 9.6 RCE patch

**Claim:** Oct 7: unified Copilot harness + session grid + cross-platform sandboxing GA; Oct 13: CVE-2026-102238 (9.6 RCE) emergency patch.
**Evidence:**
- **1.141 agent features:** Unified Copilot harness (all Copilot products on single AHP); 2D Session Grid; MXC-powered sandboxing (Win/macOS/Linux, GA); Codex Chat Handoff (continue ChatGPT/Codex CLI in VS Code); Worktree Cleanup; Background Shell Tracking; External session continuity; New Session Composer (experimental); MCP Server Discovery (preview)
- **1.141.1** (Oct 13): CVE-2026-102238 — Critical 9.6 path traversal RCE (crafted workspace file → arbitrary code); affects all VS Code 1.0.0–1.141.0; CVE-2026-102229 — remote webview path bypass (reads files outside roots over SSH/dev container)
- 🌐 Sources: https://code.visualstudio.com/updates/v1_141 | https://www.ntcompatible.com/story/visual-studio-code-11411-security-update-closes-critical-96-rce | https://visualstudiomagazine.com/articles/2026/10/13/vs-code-1-141-brings-copilot-codex-sessions-together-tightens-ai-agent-security.aspx

---

### 5. [update] GitHub Copilot — computer use preview, sandboxing GA, dynamic workflows, Skills install links

**Claim:** Oct 1–15: computer use public preview; sandboxing GA; dynamic workflows; Skills install from GitHub links.
**Evidence:**
- **Computer use** (public preview, Oct 1): reads OS accessibility tree + screenshots; clicks/types/keys/scrolls/drags; CLI + app (macOS/Windows)
- **Local sandboxing GA** (Oct 7): file/network/credential restriction via MXC; no extra cost; `allowBypass: false` for managed enforcement
- **Dynamic workflows** (Oct 1, public preview): code-defined multi-step orchestration; sequential/parallel; pause checkpoints; subagent cross-checks
- **v1.0.99-1** (Oct 15): `--trust-folder` flag; install verified Skills + plugins from GitHub install links
- **New models:** Claude Haiku 5.5 (GA); Gemini 4 Argon
- 🌐 Sources: https://github.blog/changelog/2026-10-01-dynamic-workflows-in-copilot-cli-and-the-copilot-app/ | https://github.blog/changelog/2026-10-07-local-sandboxing-for-github-copilot-now-generally-available/ | https://aicoder.com/news/news-20261002-github-copilot-computer-use-public-preview

---

### 6. [update] Antigravity v2.23.x / CLI v1.3.6 — permissions in message box, Opus/Sonnet 5.5 via ADC

**Claim:** Oct 12–15: permissions picker in message box; .zip/folder attachments; CLI gains Opus/Sonnet 5.5 + auto-retry.
**Evidence:**
- **App v2.23.0** (Oct 12): Permissions picker in message box for agent tool approval; full-screen media viewer (zoom/pan); .zip + folder attachments; MCP server restart + troubleshooting; subagent launch with live status; sidebar folder pinning
- **App v2.23.1** (Oct 13): Fix license picker height overflow on onboarding
- **CLI v1.3.6** (Oct 15): Claude Opus 5.5 + Sonnet 5.5 support via ADC; enhanced Auto mode sandbox egress reviews; colorized `/diff` Commit Tree; auto-retry for stalled model connections (5-min timeout)
- 🌐 Sources: https://antigravity.google/docs/changelog/ | https://releasebot.io/updates/google/antigravity

---

### 7. [update] Codex CLI v0.162 — instant_interrupt ON by default

**Claim:** Oct 8: `instant_interrupt` enabled by default for all users; GPT-5.5 retired Oct 14.
**Evidence:**
- v0.162.0: `instant_interrupt = true` for everyone (was opt-in since v0.159.0); new input preempts ongoing response or active Code Mode cell; disable with `instant_interrupt = false` under `[features]`
- v0.162.1 (Oct 9): TUI crash fix for async multi-line questions; hyperlink destinations preserved
- GPT-5.5 retired from ChatGPT + Codex as of Oct 14
- 🌐 Sources: https://releasebot.io/updates/openai/codex | https://skills-hub.ai/blog/openai-codex-cli-recent-releases-2026

---

### 8. [new] Harmony Harness (Google Cloud AI Research + CMU) — multi-objective harness self-evolution

**Claim:** Oct 10: arXiv paper proposes treating harness security and functionality as separate Pareto objectives; >10% gains over single-objective baselines.
**Evidence:**
- **Authors:** Weichen Yu, Lesly Miculicich, Bhavana Dalvi Mishra, Jiefeng Chen et al. (Google+CMU)
- **Method:** Multi-objective optimization — Pareto frontier of (security, functionality) tradeoffs; decomposition-based evolutionary search; factorized operators (separates transferable general mechanisms from env-specific adaptations); dynamic composition at inference time
- **Results:** >10 percentage points above single-objective baselines on SecRepoBench and BaxBench
- First research framing harness configuration as multi-objective rather than single-score optimization
- 🌐 Sources: https://arxiv.org/abs/2610.15150 | https://cryptobriefing.com/google-carnegie-mellon-harmony-harness-agents/

---

### 9. [new] Workday Agent Harness GA — 275+54 MCP tools; any agent gets HR/Finance context

**Claim:** Oct 13 at Workday Rising 2026: headless HR/Finance agent platform GA; 329 MCP tools; every agent runs with live organizational context.
**Evidence:**
- **Agent Harness:** Injects per-agent context (identity, role/reporting line, permissions, policies) from live Workday system — not a data copy or policy document
- **Agent-Ready Tools (MCP):** 275 read tools + 54 write/delete tools in Workday MCP catalog; any MCP-compatible agent + any model
- **Autopilot Agents:** GA alongside harness
- **Pricing:** Consumption-based Flex Credits
- **Upcoming (early 2027):** Agent Context Service (pre-reasoning context prep) + Grounded Reasoning (policy/process pre-check before agent acts)
- 🌐 Sources: https://newsroom.workday.com/2026-10-13-Workdays-Trusted-Agent-Platform-Now-Delivers-Headless-Access-to-HR-and-Finance,-Letting-Customers-Build-and-Run-Lawful-AI-Agents | https://investor.workday.com/news-and-events/press-releases/news-details/2026/Workdays-Trusted-Agent-Platform-Now-Delivers-Headless-Access-to-HR-and-Finance-Letting-Customers-Build-and-Run-Lawful-AI-Agents/default.aspx | https://www.enterprisetimes.co.uk/2026/10/16/workday-unveils-autopilot-agents-a-headless-agent-platform-and-new-decision-tools-at-rising-2026/

---

### 10. [new] Harness.io acquires Augment Code / Cosmos — end-to-end autonomous SDLC agent

**Claim:** Oct 8: Harness buys Cosmos + Auggie CLI + Code Context Engine; Cosmos → "Harness Cosmos Software Factory Agent"; GA immediately.
**Evidence:**
- **Assets acquired:** Cosmos (cloud AI coding platform), Auggie CLI, Code Context Engine, team
- **Integration:** Cosmos produces reviewed PRs → Harness existing agents (security/deploy/cost) carry into production; four Cosmos Experts: Project Builder, PR Author, Deep Reviewer, PR Fixer
- **Flow:** Idea → Cosmos PR → Harness CI/security/deploy → production; failures feed back to Cosmos with context
- 🌐 Sources: https://www.harness.io/blog/harness-acquires-augment-code-cosmos | https://siliconangle.com/2026/10/08/harness-acquires-augment-code-to-bridge-software-engineering-from-idea-to-deployment/ | https://sdtimes.com/software-factory/harness-acquires-augment-code-assets-to-advanced-autonomous-sdlc/

---

### 11. [new] Corbenic AI / Galahad — 50M-token memory layer, 2.8–4.3× faster than recompute

**Claim:** Oct 1 public beta; Oct 10 arXiv paper; byte-exact KV cache restore to encrypted NVMe; 8.8–12.3× less GPU energy; 98/100 accuracy over 50M tokens (31B model).
**Evidence:**
- **galahad-kv:** Writes LLM KV state (~16K-token blocks) to encrypted local NVMe; restores byte-exact with zero recompute and constant GPU memory
- **Performance:** 2.8–4.3× faster restore; 8.8–12.3× less GPU energy vs recompute; tested on 50M-token corpus
- **Accuracy:** 12B model: 82/100 facts planted millions of tokens earlier; 31B model: 98/100; zero hallucinations
- **Agent tools:** Blaise (retrieval), Taliesin (memory); agent connectors, replay, fault finder, branching, inspector, rewind
- **Pricing:** Free non-commercial (1 GPU, 12 months); commercial pilots on request
- 🌐 Sources: https://github.com/corbenicai/galahad | https://arxiv.org/abs/2610.10845v1 | https://www.storagenewsletter.com/2026/10/07/corbenic-ai-launches-galahad-the-gpu-never-reads-the-same-text-twice-again/

---

### 12. [new] morluto/REA — MCP server for reverse engineering; ~190k stars, trending #1 in October

**Claim:** REA arms AI agents with native binary inspection (Ghidra/IDA/Hopper/ASAR/APK); ~190k stars; trending #1 in Oct 2026 (+271.9k monthly).
**Evidence:**
- MCP server + CLI; `npx rea-agents setup`; package `rea-agents` on npm
- **Supported tools:** Ghidra (NSA decompiler), Hopper, IDA Pro, ASAR (Electron), Android APK, .NET assemblies, headless browser scenario captures
- Created April 14, 2026; trending Oct 7 spike (+2,956 daily stars); now ~190k total stars
- 🌐 Sources: https://hoangyell.com/rea-explained/ | https://gittested.com/reviews/morluto-rea/ | https://gittrend.io/monthly/2026-10

---

### 13. [new] vercel-labs/skills — Universal agent skills package manager for 79+ agents; 34.6k stars

**Claim:** `npx skills` detects installed agents and installs SKILL.md files to correct paths across 79+ coding agents; 34,667 stars trending October 2026.
**Evidence:**
- Detects Claude Code, Cursor, Antigravity, Codex, Pi Mono + 74 more agents; installs to agent-specific paths
- `.agents/skills/` canonical dir; atomic symlinks for non-standard agents; `skills-lock.json` for determinism
- Resolves from GitHub/GitLab/Azure DevOps/local paths/direct downloads
- Builds on Vercel skill packs ecosystem (skills.sh, launched Aug 2026)
- 🌐 Sources: https://github.com/vercel-labs/skills | https://hoangyell.com/vercel-skills-explained/ | https://www.coddykit.com/pages/blog-detail?id=5129978

---

### 14. [new] lexmount/moli — Rust headless browser for AI agents; CDP+WebDriver BiDi on single kernel

**Claim:** Moli is a standalone Rust browser kernel (not Chromium wrapper) serving DOM/Markdown extraction, CDP, WebDriver from one process; 17.9k stars.
**Evidence:**
- V8 JS engine, html5ever HTML parser, Servo Stylo CSS; own networking/cookies/storage
- No layout/paint by default (answers from DOM state); `--layout` mode for geometry/screenshots on demand
- Single endpoint for CDP + WebDriver Classic + WebDriver BiDi
- `moli serve` starts automation server; `npx rea-agents` uses it for captures
- Latest update Oct 16, 2026; v1.1.16 returns 10 JS-rendered page quotes in 0.62s
- 🌐 Sources: https://ai-tldr.dev/tools/moli/ | https://trendshift.io/repositories/128243 | https://hysenlabs.com/projects/lexmount-moli

---

### 15. [update] Cloudflare serves SEP-2640 skills via MCP — first major production vendor

**Claim:** Oct 10: Cloudflare API MCP server now distributes Wrangler/Workers/Durable Objects skills via the SEP-2640 Skills over MCP extension.
**Evidence:**
- Skills: Wrangler, Durable Objects, Agents SDK, Workers best practices
- Discovery: `skills/list`; access: `skill://<name>/<path>`; endpoint: `https://mcp.cloudflare.com/mcp`
- First major vendor to ship a SEP-2640-compliant production server (spec finalized Sep 13)
- 🌐 Sources: https://developers.cloudflare.com/changelog/post/2026-10-10-cloudflare-mcp-skills/ | https://github.com/cloudflare/mcp/pull/272

---

### 16. [update] Devin Desktop v3.10.67 — enterprise custom extension marketplaces

**Claim:** Oct 12: enterprise admins now get custom extension marketplaces; large-project performance improvements.
**Evidence:**
- v3.10.67 (Oct 12): custom extension marketplace feature for enterprise admins; performance gains on large projects
- Windsurf → Devin Desktop rebrand (Jun 2, 2026); Cascade → Devin Local (Jul 1, 2026)
- 🌐 Source: https://www.havoptic.com/tools/windsurf

---

**Still true** (ongoing, no new facts this week):
- claude-haiku-5-5-subagent-economics: Haiku 5.5 ($0.10/M, 1M ctx, Oct 7) still the sub-agent economics benchmark
- openhuman-rust-harness: OpenHuman (41.7k stars, Rust, 500 agents/$10 VPS, TokenJuice 80%)
- nanomuse-cross-device-agent: nanoMuse 1.0.0 Keel cross-device agent (Android/iOS/desktop/browser)
- jotbus-e2ee-cross-agent-scratchpad: Jotbus E2EE shared scratchpad via MCP
- cmux-ghostty-agent-terminal: manaflow-ai/cmux (28.1k stars) macOS terminal on libghostty
- agency-agents-harness-library: msitarzewski/agency-agents (158.5k stars, 230+ agents for 15+ harnesses)
- trycua-computer-use-fleet: trycua/cua (29.2k stars) Computer-Use 2.0 fleet platform
- docker-agent-yaml-runtime: docker/docker-agent (4.3k stars) declarative YAML multi-agent runtime
- pinrail-human-in-loop-inbox: forgeplane/Pinrail (34 stars) local human-approval inbox
- pi-minimal-agent-harness: Pi 1.0 (111.8k stars, MIT) minimal coding agent with Codemode/Pi Durable
- offrun-multi-agent-workspace: Offrun Mac app (CC/Codex/AGY/Grok Build side-by-side)
- headlong-microharness-bash: Headlong (~10K Bash microharness, never sleeps)
- television-agent-gui-sidecar: Television (GUI sidecar for any agent harness)
- skills-security-prompt-injection-36pct: 157 malicious skills, STSS/skilltrust attestation
- extension-economy-explosion: addyosmani/agent-skills 102k; obra/superpowers 294.9k; mattpocock/skills ~277k
- sep-2640-mcp-skills-final: SEP-2640 finalized; no mainstream harness default yet (Cloudflare first production server)
- harness-context-tax-problem: Token compression ongoing (OpenHuman 80%, caveman 65%, Headroom 65–70%)
- nvidia-openshell-agent-runtime: NVIDIA OpenShell (14.3k stars, kernel-level, deny-by-default)
- weave-router-model-routing: Weave Router 2.0 (HMM routing, Astra-quality at 52% cost)
- mattpocock-skills-135k: mattpocock/skills ~277k stars
- openai-devday-2026-gpt61-dots: OpenAI Agents API GA; Dots always-on agents; $0.002/step
- cn-miit-claude-code-notice: MIIT CC security notice; CN proxy projects (shareAI-lab, KimYx0207)
- claude-sonnet-5-5: Sonnet 5.5 (Sep 28) still CC default
- salesforce-enterprise-ai-harness: Salesforce Trusted Enterprise AI Harness (FY28 rollout)
- openrig-multi-agent-harness: mvschwarz/openrig (2.2k stars) YAML RigSpec
- hindsight-standalone-memory: vectorize-io/hindsight (40.5k stars) biomimetic memory
- jauvex-voice-multi-agent: reindent/jauvex voice-first desktop harness
- google-ax-agentic-runtime: Google AX (11.2k stars) Kubernetes-native distributed agent runtime
- cursor-projects-self-hosted-machines: Cursor Projects beta; Self-Hosted Machines; Remote Control iOS
- univer-office-harness: dream-num/univer (Beijing) Office Harness for AI Agents
- addy-osmani-agent-skills: addyosmani/agent-skills 102k stars
- harness-engineering-paradigm: JP gihyo.jp Oct 2026 formalizes Agentic Coding vs Vibe Coding
- harness-internal-external-disambiguation: JP 内部/外部ハーネス distinction
- environment-architect-new-role: JP "Environment Architect" specialization solidifying
- anthropic-managed-agents-mcp-tunnels: CC managed agents + marketplace plugin install
- deepseek-harness-team: DeepSeek Harness ~248k stars; Cordis-everything-is-a-plugin
- qwen-code-alibaba: Qwen Code v0.25.0 (28k stars) durable workspace agent
- microsoft-maf-codeact: Microsoft Agent Framework v1.20.0
- cloudflare-os-kitesurf: Cloudflare OS (11.3k stars) managed cloud agent workspace
- layered-oss-stack-over-single-framework: Security (OpenShell) → distributed (AX) → harness → terminal (cmux) → memory (Hindsight) → skills (SEP-2640) — composable stack model
- hkuds-nanobot-personal-agent: HKUDS/nanobot v0.3.5 (48.6k stars)
- gitspawn-class-vulnerability: GitSpawn 8 flaws, 4 still unpatched
- mcp-security-nsa-supply-chain: NSA advisory; CHAINDROP; AIR Security $50M
- cursor-spacex-acquisition: Cursor acquired by SpaceX (Aug 14)
- microsoft-intelligent-terminal: microsoft/intelligent-terminal (2,042 stars) Windows Terminal agent fork

---

## Cross-Source Patterns

**1. Enterprise harnesses going headless (Workday + Harness.io Cosmos)**
- Workday (Oct 13): 329 MCP tools, any agent gets live HR/Finance context
- Harness.io (Oct 8): acquires Cosmos → SDLC agent from idea to PR to deploy
- **Pattern:** Enterprise platforms are removing the GUI requirement; agents become first-class consumers of enterprise data and workflow APIs
- Platforms: 🌐 SiliconANGLE, SD Times, Constellation Research, Workday newsroom

**2. Harness self-evolution becoming a research field (Harmony Harness + Corbenic + prior arXiv)**
- Harmony Harness (Oct 10): multi-objective Pareto evolution of harness configuration
- Corbenic/Galahad (Oct 1/Oct 10): memory that never re-reads → harness gets perfect recall at lower compute
- Prior: arXiv:2604.25850 (observability-driven auto-evolution), arXiv:2608.08466 (hierarchical self-improvement)
- **Pattern:** From manual harness configuration toward automated/learned harness optimization
- Platforms: arXiv, Crypto Briefing, Storage Newsletter

**3. Skills distribution infrastructure solidifying (vercel-labs/skills + Cloudflare SEP-2640)**
- vercel-labs/skills (34.6k stars): first universal CLI for 79+ agents
- Cloudflare MCP Skills (Oct 10): first major vendor SEP-2640 production server
- addyosmani/agent-skills 102k, mattpocock/skills ~277k, obra/superpowers 294k
- **Pattern:** Distribution layer maturing: package manager (npx skills), vendor distribution (Cloudflare), open standard (SEP-2640). Installation solved; discovery and curation still open.
- Platforms: 🌐 CoddyKit, 🇯🇵 Zenn (Agent Plugins 1.0), 🇨🇳 Juejin, CSDN

**4. Safety/sandboxing becoming default, not optional (VS Code + Copilot GA + CC hooks)**
- VS Code 1.141: cross-platform sandboxing GA + 9.6 RCE emergency patch
- Copilot CLI: local sandboxing GA (Oct 7), MXC-powered
- CC v2.1.300: hook `updatedInput` validation hardened (unknown keys dropped)
- CC v2.1.301: OTel `classifier_verdict`/`permission_mode`/`classifier_category` for auditability
- **Pattern:** Security going from optional feature to required infrastructure; harness vendors shipping policy enforcement by default
- Platforms: 🌐 VS Magazine, ntcompatible.com, plainenglish.io, GitHub Blog

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kkrausse | Show HN: Faplex | 4 | 3 | "like `Claude agents` but all machines and harnesses" | https://github.com/kkrausse/faplex |
| corbenicai | Show HN: Galahad (memory) | 3 | 0 | 50M token KV memory, free non-commercial | https://github.com/corbenicai/galahad |
| vigiloss | Show HN: Agent harness for long-running pentests and code audits | ~5 | — | Specialized security testing harness | https://news.ycombinator.com/item?id=50034204 |

**Web (global) 🌐:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | releasebot.io | https://releasebot.io/updates/anthropic/claude-code | CC v2.1.294–301 changelog |
| 🌐 | dev.classmethod.jp | https://dev.classmethod.jp/en/articles/20261016-cc-updates-v2-1-301/ | v2.1.301 deep-dive |
| 🌐 | claudeupdates.dev | https://www.claudeupdates.dev/version/2.1.300 | v2.1.300 88-change detail |
| 🌐 | NousResearch/hermes-agent | https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0 | Hermes v0.22.0 official notes |
| 🌐 | aicoder.com | https://aicoder.com/news/news-20261014-hermes-agent-v0-22-threshold-release-local-models-connectors | Hermes v0.22.0 summary |
| 🌐 | releasebot.io | https://releasebot.io/updates/openclaw | OpenClaw Oct changelog |
| 🌐 | antigravity.google | https://antigravity.google/docs/changelog/ | Antigravity App+CLI changelog |
| 🌐 | code.visualstudio.com | https://code.visualstudio.com/updates/v1_141 | VS Code 1.141 full features |
| 🌐 | ntcompatible.com | https://www.ntcompatible.com/story/visual-studio-code-11411-security-update-closes-critical-96-rce | CVE-2026-102238 analysis |
| 🌐 | github.blog | https://github.blog/changelog/2026-10-07-local-sandboxing-for-github-copilot-now-generally-available/ | Copilot sandboxing GA |
| 🌐 | github.blog | https://github.blog/changelog/2026-10-01-dynamic-workflows-in-copilot-cli-and-the-copilot-app/ | Dynamic workflows preview |
| 🌐 | releasebot.io | https://releasebot.io/updates/openai/codex | Codex CLI v0.162 |
| 🌐 | arxiv.org | https://arxiv.org/abs/2610.15150 | Harmony Harness paper |
| 🌐 | workday newsroom | https://newsroom.workday.com/2026-10-13-Workdays-Trusted-Agent-Platform-Now-Delivers-Headless-Access-to-HR-and-Finance,-Letting-Customers-Build-and-Run-Lawful-AI-Agents | Workday Agent Harness GA |
| 🌐 | harness.io | https://www.harness.io/blog/harness-acquires-augment-code-cosmos | Cosmos acquisition |
| 🌐 | arxiv.org | https://arxiv.org/abs/2610.10845v1 | Galahad 50M-token memory |
| 🌐 | github.com | https://github.com/corbenicai/galahad | Galahad repo |
| 🌐 | hoangyell.com | https://hoangyell.com/rea-explained/ | REA explainer |
| 🌐 | github.com | https://github.com/vercel-labs/skills | vercel-labs/skills |
| 🌐 | cloudflare.com | https://developers.cloudflare.com/changelog/post/2026-10-10-cloudflare-mcp-skills/ | Cloudflare SEP-2640 |
| 🌐 | gittrend.io | https://gittrend.io/monthly/2026-10 | Oct trending repos |
| 🌐 | coddykit.com | https://www.coddykit.com/pages/blog-detail?id=5129964 | 30-day GitHub trending analysis |
| 🌐 | siliconangle.com | https://siliconangle.com/2026/10/08/harness-acquires-augment-code-to-bridge-software-engineering-from-idea-to-deployment/ | Cosmos acquisition coverage |
| 🌐 | enterprisetimes.co.uk | https://www.enterprisetimes.co.uk/2026/10/16/workday-unveils-autopilot-agents-a-headless-agent-platform-and-new-decision-tools-at-rising-2026/ | Workday Rising 2026 |

**Web (Japan) 🇯🇵:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita | https://qiita.com/Takuya__/items/ff4e4ef6c157d081168c | Harness engineering: 3-layer architecture; hidden technical debt |
| 🇯🇵 | Zenn | https://zenn.dev/shintaroamaike/articles/df3ecc0ddee047 | AutoHarness skill; enforcement vs description gap |
| 🇯🇵 | Zenn | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | 100 OSS tools catalog across 17 layers |
| 🇯🇵 | Zenn | https://zenn.dev/aws_japan/articles/skills-over-mcp | SEP-2640 design explanation |
| 🇯🇵 | Zenn | https://zenn.dev/big_tanukiudon/articles/4386870c80dcbf | OpenCode vs Hermes harness comparison |
| 🇯🇵 | Zenn | https://zenn.dev/takuyanagai0213/articles/harness-engineering-intro-8months | 0→420 CLAUDE.md files in 8 months |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/10/agentic-coding-and-harness-engineering | Agentic Coding vs Vibe Coding; 内部/外部ハーネス |
| 🇯🇵 | note.com | https://note.com/fair_godwit407/n/n4465a4348330 | CC v2.1.299–301 JP same-day summary |
| 🇯🇵 | ai-garage.jp | https://ai-garage.jp/column/hermes-agent-updates-2026/ | Hermes Oct updates in Japanese |

**Web (China) 🇨🇳:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2029953897662505928 | OpenClaw vs Hermes vs Harness Engineering 6-dim comparison |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2026622473097978502 | Hermes deep-dive research report |
| 🇨🇳 | CSDN | https://blog.csdn.net/ziwoods/article/details/161662819 | MCP "USB-C for agents" framing; 97M/month SDK downloads |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2658963 | Hermes/CC/OpenClaw "three-way game" |
| 🇨🇳 | Tencent Cloud | https://developer.cloud.tencent.com/article/2696664 | MCP + OpenClaw 10x integration efficiency |
| 🇨🇳 | Tencent Cloud | https://developer.cloud.tencent.com/article/2715416 | Hermes vs OpenClaw 8-dimension test |
| 🇨🇳 | Juejin | https://juejin.cn/post/7694947768088657935 | MCP as enterprise infrastructure; architect governance framework (Oct 11) |
| 🇨🇳 | Sohu | https://www.sohu.com/a/1087812264_122977613 | Hermes v0.22.0 CN coverage |
| 🇨🇳 | cnblogs | https://www.cnblogs.com/databank/p/19508724 | A2A v1.0 + MCP dual standard overview |
| 🇨🇳 | Bilibili | https://www.bilibili.com/video/BV1zRdaBcE9x/ | Hermes vs OpenClaw hands-on video |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per instructions)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 stories │ ~10 pts │ ~8 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 48 pages │ 🇯🇵 9 │ 🇨🇳 10
└─ 🗣️ Top sources: releasebot.io, dev.classmethod.jp, gittrend.io, coddykit.com | Zenn (JP), Zhihu/Tencent Cloud (CN)
```

---

## Out of Scope but Notable

- **Strata (Niko1221/Strata, +22.4k stars Oct 2026):** Local inference engine with native Qwen3.8-Flash-Next support — belongs to open-models-geopolitics but its harness MCP integration is notable for local-model agent workflows. https://github.com/Niko1221/Strata
- **Tencent HyMemory 2.0 (open-source):** Claims superior performance over Opus 5 on memory benchmarks — potentially relevant to open-models but also to agent memory infrastructure. https://www.kucoin.com/news/flash/tencent-hunyuan-launches-open-source-hy-memory-2-0-framework-claims-superior-performance-over-opus-5

---

## Data Gaps

- **Bluesky** (SOURCE HEALTH: OK): No bluesky-specific posts found in this sweep; the skill for direct Bluesky API access was not available, so only cross-referenced from other sources
- **Reddit/X/Twitter:** Excluded per topic instructions
- **HN search rate limit:** HN item https://news.ycombinator.com/item?id=50034204 returned 429; extracted via search result snippet only
- **Zhihu direct fetches:** 403 on direct Zhihu page fetches; extracted via WebSearch snippets
- **cc-switch, OpenChamber, Pi Mono updates:** No new Oct 9–16 data found; presumed ongoing
- **Cursor changelog Oct 9–16:** No specific new releases found post Oct 9 (Remote Control iOS / 7% token efficiency already captured last run)
- **Approximate coverage:** 82% — strong coverage of major harnesses and new tools; HN full post list not scraped; some niche new repos likely missed

---

## Key Quotes

> "The whole codebase was simplified with zero behavior change: source went from about 1.06M to 698K lines (−34%) and gateway/run.py shrank from 34,847 lines to 5,512." — Hermes Agent v0.22.0 release notes ([link](https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.0))

> "A fresh desktop install now opens on a guided setup chat that runs on a free trial model, so a newcomer is talking to Hermes before they own an API key." — Hermes Agent v0.22.0 announcement ([link](https://aicoder.com/news/news-20261014-hermes-agent-v0-22-threshold-release-local-models-connectors))

> "A restore was 2.8× to 4.3× faster and consumed 8.8× to 12.3× less GPU energy [vs recompute]" — Corbenic AI / arXiv:2610.10845 ([link](https://arxiv.org/abs/2610.10845v1))

> "CVE-2026-102238… lets an attacker run arbitrary code on your machine… affects every VS Code version from 1.0.0 through 1.141.0" — ntcompatible.com ([link](https://www.ntcompatible.com/story/visual-studio-code-11411-security-update-closes-critical-96-rce))

> "Instead of optimizing one blended score, [Harmony Harness] frames harness evolution as a multi-objective optimization problem, with security and functionality treated as distinct targets rather than mashed into a single number." — Crypto Briefing ([link](https://cryptobriefing.com/google-carnegie-mellon-harmony-harness-agents/))

> "Every agent deployed on Workday runs on Agent Harness, which gives each agent the context a task depends on, including who the person is, their role and reporting line, what they can see and do, and which policies and processes apply. That context comes from the system that runs HR and finance, not from a data copy or policy document." — Workday newsroom ([link](https://newsroom.workday.com/2026-10-13-Workdays-Trusted-Agent-Platform-Now-Delivers-Headless-Access-to-HR-and-Finance,-Letting-Customers-Build-and-Run-Lawful-AI-Agents))

> "ハーネスエンジニアリングにより、エンジニアの役割が「自分でコードを書く」から「AIチームをマネジメントする」へシフト" / "Harness engineering shifts the engineer's role from 'writing code yourself' to 'managing the AI team'" — gihyo.jp Oct 2026 ([link](https://gihyo.jp/article/2026/10/agentic-coding-and-harness-engineering))

> "MCP已成为'智能体USB-C接口'，从Anthropic的内部实验变成Linux Foundation下的行业标准" / "MCP has become the 'USB-C interface for agents,' evolving from Anthropic's internal experiment to an industry standard under the Linux Foundation" — CSDN ([link](https://blog.csdn.net/ziwoods/article/details/161662819))
