# AI Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-07-31
**Query type:** GENERAL
**Sources:** Hacker News, YouTube, Web (global), Web (Japan 🇯🇵), Web (China 🇨🇳), GitHub Trending

> **Run note:** The `/last30days` skill was unavailable for this run. This briefing is assembled from manual WebSearch + WebFetch across all platforms. Reddit, X/Twitter, TikTok, Instagram, Bluesky signal absent; HN and Web coverage is strong.

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not fetched (skill unavailable) |
| X/Twitter | — | — | Not fetched (skill unavailable) |
| YouTube | 2 videos | — | 🌐 Hermes+Grok walkthrough; OpenClaw skills |
| Hacker News | 6 stories | ~50 pts each | 🌐 Statewright, Pu.sh, Agent-QA, Forge, Reasonix, harness-importance |
| TikTok | — | — | Not fetched |
| Instagram | — | — | Not fetched |
| Bluesky | 0 posts | — | 🦋 Search returned no on-topic July 2026 posts; Bluesky=OK per SOURCE HEALTH |
| Web (global) | 62 pages | — | 🌐 via WebSearch + WebFetch; GitHub, blogs, changelogs |
| Web (Japan) | 12 pages | — | 🇯🇵 Qiita ×4, Zenn ×4, GIGAZINE ×1, Publickey ×1, note ×1, Hatena ×1 |
| Web (China) | 8 pages | — | 🇨🇳 Tencent Cloud ×2, Juejin ×2, CSDN ×1, Zhihu ×1, Pedaily ×1, tinyash ×1 |

---

## Synthesized Findings

### 1. [update] MCP 2026-07-28 Final Specification Ships — Stateless Core, Extensions Framework, 950+ Servers

**New fact since 2026-07-29:** The specification shipped as final (not just RC) on July 28, 2026. All major SDKs (TypeScript, Python, Go, C#) updated day-of; GitHub MCP Server updated same day; 950+ servers now registered in Claude's connector directory; MCP SDK crossed **400M monthly downloads** (Chinese tech media: "月下载狂飙破4亿").

The MCP 2026-07-28 spec is the largest MCP revision since launch. Three changes are load-bearing for harness builders:

**1. Stateless core** — eliminates `initialize` handshake and `Mcp-Session-Id`. Every request is self-contained; any server instance can handle any request. "Before, running a remote MCP server meant managing session state, which limited where you could run it. Now that MCP is stateless, you can deploy on serverless and edge infrastructure." Load balancing becomes trivial; sticky sessions become unnecessary. Japanese practitioners flagged this as breaking: "MCPクライアントからのリクエストはどのMCPサーバに到着しても処理されるようになります" (MCP client requests will be processed regardless of which server they reach) — but also the key enabler for enterprise scale (Publickey: https://www.publickey1.jp/blog/26/mcp728mcpgithub_mcp.html).

**2. Extensions Framework** — reverse-DNS identifiers, separate repos, independent versioning, dedicated Extensions Track. MCP Apps (server-rendered UIs in sandboxed iframes) and Tasks (stateless lifecycle: `tasks/get`, `tasks/update`, `tasks/cancel`) are the first two official extensions.

**3. OAuth hardening** — 6 SEPs: mandatory `iss` parameter (RFC 9207), application type declaration, issuer binding, refresh token guidance. WorkOS analysis: https://workos.com/blog/mcp-2026-spec-agent-authentication

**Caching/routing support**: `ttlMs` + `cacheScope` on list results; `Mcp-Method` + `Mcp-Name` headers for load balancers without body inspection.

**Deprecations (12-month minimum)**: Roots, Sampling, Logging.

Sources: https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ · https://aaif.io/blog/mcp-is-growing-up · https://gigazine.net/news/20260729-model-context-protocol-2026-07-28/ · https://stacktr.ee/blog/mcp-2026-spec-changes

Platform signal: 🌐 global, 🇯🇵 Japan (GIGAZINE, Publickey, note, Mamezou Developer), 🇨🇳 China (Pedaily, Tencent Cloud)

---

### 2. [update] GitHub Copilot Code Review: Agent Skills + MCP Go GA (July 29) — Mainstream Arrival of SKILL.md

**New fact since 2026-07-29:** On July 29, 2026, GitHub made agent skills and MCP server connections **generally available** in Copilot code review for all Pro, Pro+, Business, and Enterprise tiers. (Public preview launched June 2.)

Teams can now drop `SKILL.md` files into `.github/skills/` to give Copilot code review repo- or org-specific context and instructions. MCP connections pull from issue trackers, documentation systems, service catalogs — all read-only. Attribution feature shows which comments were informed by which skill or MCP tool.

This is the most mainstream distribution event the SKILL.md standard has seen — every paying Copilot user now has a skills/MCP layer.

Source: https://github.blog/changelog/2026-07-29-copilot-code-review-agent-skills-and-mcp-now-generally-available/

Platform signal: 🌐 global

---

### 3. [update] Kiro CLI V3: Spec-Driven Terminal + Unified Agent Harness (July 2026)

**New fact since 2026-07-29:** Kiro shipped a full month of changes including Claude Opus 5 (July 24), OpenAI GPT-5.6 Sol/Terra/Luna (July 14), global hooks (`~/.kiro/hooks/`), and the most significant structural change: **Kiro CLI V3 early access**, described as "a unified agent harness that powers the Kiro IDE and Web, with every improvement shipping to all surfaces simultaneously."

V3 introduces spec-driven development in the terminal, a capability-based permissions model, enhanced hooks, and tag-based agent configuration. The `/upgrade-agent` command (July 22) migrates V2 custom agents to the universal format.

Other July entries: `/spec new` now starts with a guided description step (July 27); `Ask Kiro to Fix` editor context menu action for errors/warnings (July 28); introspect subagent for learning Kiro features (July 17); MCP OAuth support expansion (July 9).

Sources: https://kiro.dev/changelog/ · https://releasebot.io/updates/kiro · https://www.geekwire.com/2026/aws-targets-ai-slop-with-new-spec-check-in-kiro-coding-tool-amid-scrutiny-of-agent-reliability/ · https://builder.aws.com/content/3DlOO7A9RFAazBbwbNl2iV8WHr9/harness-engineering-with-kiro-spec-driven-development-for-the-multi-agent-era

Platform signal: 🌐 global

---

### 4. [update] Claude Code July 2026 — Nested Subagents Depth 3, /fork, Opus 5 Default, Hardened Sandbox

**New facts since 2026-07-29:** v2.1.219 (July 24-25) made **Opus 5 the default Opus model** (1M context) and enabled **nested subagents up to depth 3** (was 1). `/fork` (v2.1.212, July 17) creates background session copies — the in-session subagent it used to launch is now `/subtask`. `/code-review` now runs as background subagent (v2.1.218). `/verify` and `/code-review` are now **manual-only** — no auto-launch (v2.1.215).

Safety additions: session-wide WebSearch cap (default 200), subagent spawn cap (default 200), subagent concurrency cap (default 20), `sandbox.filesystem.disabled` and `sandbox.network.strictAllowlist` settings, Docker command permission prompts, Unicode exploit hardening in permission preview. `EndConversation` tool for abusive users.

Memory leak fixes: MCP stdio server stderr capped at 64 MB/server; LSP documents LRU-capped at 50 docs; quadratic slowdown in long sessions eliminated.

New DX: `/ultrareview` with descriptive arguments; emoji shortcode autocomplete; `CLAUDE_CODE_PROCESS_WRAPPER` for corporate launchers; live elapsed-time counter; OpenTelemetry message-level correlation attributes; auto mode on Bedrock/Vertex/Foundry without opt-in flag.

Sources: https://releasebot.io/updates/anthropic/claude-code · https://code.claude.com/docs/en/changelog · https://www.havoptic.com/tools/claude-code

Platform signal: 🌐 global

---

### 5. [update] MCP Security: NVIDIA SkillSpector — 1-in-4 Skills Has a Real Vulnerability

**New fact since 2026-07-29:** NVIDIA open-sourced **SkillSpector** (168 stars) — the first dedicated security scanner for AI agent skills. It runs a two-stage pipeline: 64 regex-based vulnerability patterns across 16 categories (Stage 1), plus optional LLM semantic analysis at ~87% precision (Stage 2).

Scale of the problem is now quantified: "Agent Skills in the Wild" (Liu et al., 2026) scanned 42,447 skills — **1 in 4 has a real vulnerability**. Snyk scanned 3,984 published skills (Feb 2026): 36.8% had at least one flaw; 13.4% critical; 76% confirmed malicious — eight still downloadable when the report shipped.

OpenClaw is collaborating with NVIDIA on agent skill security. NVIDIA also launched a Verified Agent Skills program with Skill Cards for capability governance.

Sources: https://github.com/nvidia/skillspector · https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/ · https://aiinsiders.net/article/nvidia-ships-open-source-scanner-for-agent-skill-supply · https://openclaw.ai/blog/openclaw-nvidia-skill-security · https://towardsdatascience.com/from-green-checkmark-to-real-judgment-auditing-ai-agent-skills-with-skillspector/

Platform signal: 🌐 global; 🇯🇵 Japan (via NSA/MCP security thread ongoing)

---

### 6. [update] OpenClaw July 2026 — Session Rewind/Branching, Ticketed MCP Apps, Cross-Harness Memory Imports

**New fact since 2026-07-29:** OpenClaw 2026.7.2-beta.5 (July 28) introduces session rewind and branching — users can "rewind or fork conversations from individual messages, switch transcript branches across web and native apps." Ticketed MCP Apps with bound tools and resources can now be hosted or pinned to dashboards. Memory imports from Claude Code, Codex, and Hermes now supported in Skill Workshop. MCP server connections are scoped to their requesting session (isolation improvement).

Also: durable channel delivery (Telegram, Signal, Slack recoverable across restarts), crash-recoverable SQLite snapshots, Wear OS companion, remote coding sessions (cloud workers).

Sources: https://releasebot.io/updates/openclaw · https://openclawlaunch.com/news

Platform signal: 🌐 global

---

### 7. [update] Extension Economy — Skills at Scale, MAF Skills-from-MCP, Microsoft/Vercel Convergence

**New facts since 2026-07-29:** 
- **MAF skills-from-MCP** (July 28): Microsoft Agent Framework agents can now discover and load Agent Skills directly from MCP servers on demand — no redeploy required when new skills publish.
- **GitHub Copilot code review** (July 29): SKILL.md standard reaches all paying Copilot users (see finding #2).
- **NVIDIA SkillSpector** (see finding #5): supply-chain risk quantified for the first time.
- **MCP SDK at 400M+ monthly downloads** (Chinese media).
- **microsoft/SkillOpt** trending (+275 stars July): text-space optimizer training reusable NL skills for frozen LLMs.
- **google-labs-code/stitch-skills** (+24 stars July): Google's open skills library compatible with Gemini CLI, Claude Code, Cursor.

Sources: https://devblogs.microsoft.com/agent-framework/discover-agent-skills-from-mcp-servers-in-net/ · https://www.totalum.app/blog/agent-skills-marketplaces-2026 · https://vercel.com/changelog/the-skills-sh-api-is-now-available

Platform signal: 🌐 global

---

### 8. [update] Claude Code /doctor, /ultrareview, and Hygiene Toolchain (July 2026)

**New fact since 2026-07-29:** `/ultrareview` added with descriptive arguments support. `/verify` and `/code-review` now explicitly manual-only (v2.1.215, July 19). `/doctor` confirmed as comprehensive setup checkup (dedup CLAUDE.md files, flag unused skills/MCP servers, identify slow hooks, propose fixes). Week 28 (July 6-10): built-in desktop browser, `/doctor` comprehensive upgrade, `/commit-push-pr` auto-allows configured push remote.

Sources: https://releasebot.io/updates/anthropic/claude-code · https://claudelog.com/faqs/claude-code-release-notes/

---

### 9. [new] Warp Oz: First Multi-Harness Control Plane — Cross-Harness Memory, Side-by-Side Orchestration

Warp launched major upgrades to **Oz** (May 19, 2026), positioning it as "the first multi-harness control plane for cloud agents." Core capability: run Claude Code, Codex, and Warp Agent simultaneously in a unified system with consistent governance and audit logs.

**Cross-Harness Agent Memory** (research preview): "Your agents now learn how you work — code review agents learn your team's coding style" and retain institutional knowledge across sessions, repos, and projects. This is the only system claiming true cross-harness persistent memory.

**Automatic multi-agent orchestration**: Oz spawns and coordinates parallel subagents for complex long-running projects (feature development, code migrations).

Enterprise controls: per-team billing, credit caps, granular permission, Kubernetes self-hosting.

Philosophy: "Companies shouldn't have to bet their future on a single model or harness."

Sources: https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration · https://sdtimes.com/ai/warp-updates-oz-to-help-enterprises-orchestrate-coding-agents-across-any-model-or-harness/ · https://www.warp.dev/oz · https://docs.warp.dev/agent-platform/

Platform signal: 🌐 global

---

### 10. [new] Mozilla Otari: Open-Source LLM Gateway With Built-In Agent Harnesses (July 6, 2026)

Mozilla.ai shipped **Otari** (July 6, 2026) — an open-source, OpenAI-compatible LLM gateway for operators who want provider credentials and usage data to stay in their own environment. Stars: 357.

Differentiators vs simple proxies:
- **Virtual keys**: clients receive scoped, revocable API keys (never direct provider credentials)
- **Pre-request budgets**: cost controls enforced *before* API calls execute, not reconciled afterward
- Built-in **security guardrails**: prompt injection detection at request layer
- Built-in **tools**: sandboxed code execution and web search
- **Agent Harnesses** (built-in): packaged orchestration layer for building agent-ready applications
- 40+ providers via a single OpenAI-compatible endpoint

Both standalone and hybrid mode with otari.ai. Admin dashboard for key management and analytics.

Sources: https://github.com/mozilla-ai/otari · https://blog.mozilla.ai/introducing-otari-the-open-source-llm-control-plane/ · https://gigazine.net/gsc_news/en/20260707-mozilla-ai-otari/ · https://otari.ai/

Platform signal: 🌐 global

---

### 11. [new] Statewright: Rust State Machine Guardrails for Agents (Show HN, 373 Stars)

**Show HN: "Statewright – Visual state machines that make AI agents reliable"** (HN: https://news.ycombinator.com/item?id=48108778, ~50 upvotes)

Statewright is a pure-Rust state machine evaluator that constrains which tools an AI coding agent can use in each workflow phase. Per-state tool allow-lists are enforced at the hook layer before execution — no LLM in the guardrail loop. Workflows defined in JSON with states, transitions, guards, and tool allowlists.

Research result: two local models improved from **2/10 to 10/10** on a 5-task SWE-bench subset with constraints enabled. The mechanism: preventing agents from taking shortcuts (e.g., editing during planning phase, running tests during implementation).

Integrates via MCP and hooks with Claude Code, Codex, Cursor, OpenCode, and Pi. Hard enforcement vs advisory mode available.

License: Apache 2.0 (engine + agent layer); FSL-1.1-ALv2 for MCP gateway (converts to Apache 2.0 in 2029).

Sources: https://github.com/statewright/statewright · https://statewright.ai/ · https://news.ycombinator.com/item?id=48108778

Platform signal: 🌐 global (HN)

---

### 12. [new] Headroom: Context Compression Layer — 62k Stars, 20-95% Token Reduction

**Headroom** (headroomlabs-ai/headroom, 62k stars, 229 contributors, weekly releases) compresses tool outputs, logs, files, and RAG chunks before they reach the LLM. Claims 20% fewer tokens for coding agents, 60-95% for JSON, "same answers."

Architecture: CacheAligner → ContentRouter → reversible compression. Content-type routing: SmartCrusher for JSON, AST-aware CodeCompressor for code languages, HuggingFace model for general text. Compression is reversible and local-first; originals retrievable via `headroom_retrieve`.

Available as: library, drop-in proxy (port 8787), or MCP server (compress, retrieve, stats). Repository Radar commit-release score: 100/100. Built by Netflix engineer.

Significant because the cost of tool outputs is the largest scaling challenge for long-horizon agent runs — Headroom addresses this at the infrastructure layer rather than requiring prompt changes.

Sources: https://github.com/headroomlabs-ai/headroom · https://headroomlabs.ai/ · https://repositoryradar.dev/repo/headroomlabs-ai/headroom · https://www.developersdigest.tech/blog/github-trending-headroom-2026-06-06

Platform signal: 🌐 global

---

### 13. [new] Pi: Minimal Coding Agent Harness — 54k Stars, Lazy Skills, Sub-1000-Token System Prompt

**Pi** (github.com/earendil-works/pi, 54k stars, TypeScript, MIT) from Armin Ronacher (Flask, Jinja2) and Mario Zechner is a "deliberate rebuttal to the bloated-harness era — the argument that the model is already smart enough, and the harness should get out of its way."

Core mechanism: **Lazy Skills** — only a one-line description of each skill stays in context; full instructions load on demand when the model invokes the skill. Combined with ~4 primitive tools (read, write/edit, shell, search), sessions start lean and pull detail as needed.

Sub-1,000-token system prompt contrasts sharply with incumbents (Claude Code, Cursor, Codex) which carry substantially heavier context overhead. The Pi philosophy is gaining traction as developers observe that larger harnesses don't proportionally improve outcomes on mid-complexity tasks.

oh-my-pi (14.7k stars, can1357) and oh-my-openagent (48k stars) are Pi derivatives with heavier feature sets (hash-anchored edits, LSP, DAP, 40+ providers).

Context: Google retired Gemini CLI June 18 → Antigravity. Roo Code archived May 15. Pi fills the minimal-harness niche both left.

Sources: https://github.com/earendil-works/pi · https://pi.dev/ · https://ailearningguides.com/pi-ai-coding-agent-2026-lean-cli/ · https://www.contextstudios.ai/blog/pi-agent-vs-claude-code-when-minimal-beats-maximal · https://academy.kspl.tech/blog/2026-06-05-pi-agent-deep-dive-2026

Platform signal: 🌐 global

---

### 14. [new] DeepSeek Forms Internal Harness Team — "Model + Harness = Agent" as Company Formula

DeepSeek internally formed a **Harness team** (mid-May 2026) focused on code agent products, benchmarking internally against Claude Code. Their recruitment JD explicitly states: **"Model + Harness = Agent."** This is significant: a frontier model lab publicly acknowledging that harness is the competitive frontier, not just the model.

**Reasonix** (May 25, 2026, github.com/esengine/deepseek-reasonix): DeepSeek-native terminal coding agent engineered around prefix-cache stability — "leave it running." Default behavior: prompt caching on. On 90-minute pair coding sessions, often cuts spend by 60%+.

DeepSeek V4 ships "Deep Code" — open-source terminal coding agent. Community: deepseek-ai/awesome-deepseek-agent.

Chinese tech analysis: PANews frames DeepSeek's harness focus as "domestic AI competition battlefield shifting" to the harness layer: "Everything beyond the model is harness." (https://panews.io/articles/019eede8-f90e-746d-929c-82a7c608db11)

Sources: https://github.com/esengine/deepseek-reasonix · https://winbuzzer.com/2026/05/25/reasonix-launches-deepseek-native-terminal-coding-agent-xcxwbn/ · https://www.verdent.ai/guides/deepseek-coding-plan-2026 · https://github.com/deepseek-ai/awesome-deepseek-agent

Platform signal: 🌐 global, 🇨🇳 China (PANews)

---

### 15. [new] CLI-Anything (HKUDS): Making All Software Agent-Native — 46.4k Stars, CLI-Hub

**CLI-Anything** (github.com/HKUDS/CLI-Anything, 46.4k stars) from the same lab as OpenHarness automatically generates CLIs from any source code or application, then makes them discoverable by AI agents via auto-generated SKILL.md files.

**CLI-Hub** (`pip install cli-anything-hub`): package manager for community-built CLIs — browse, search, install. Meta-skill: agents can autonomously discover CLIs from the hub registry and read each CLI's SKILL.md for task-specific guidance. Available at https://clianything.cc/

This is an infrastructure play at a different level than MCP servers: CLI-Anything wraps *any existing software* in an agent-callable interface without requiring that software to implement MCP or any other protocol.

Sources: https://github.com/HKUDS/CLI-Anything · https://clianything.cc/

Platform signal: 🌐 global

---

### 16. [new] Forge + Agent Client Protocol (ACP): Universal CLI Standard for Harness Interop

**forge-agents/forge** (github.com/forge-agents/forge, 25 stars but 4,396 commits) implements the **Agent Client Protocol (ACP)** — described as "an open standard that lets any editor work with any agent, similar to how LSP standardized language servers." Supports 15+ agents with weekly additions, unified conversation history across all, full ACP feature set (tool calls, session modes, agent plans).

A separate Rust variant, **Adulari/forge**, offers model-agnostic three-agent architecture: `forge` (implements), `sage` (researches, read-only), `muse` (plans). Benchmark-ranked cost-tier routing across 300+ models, cross-provider failover, subscription bridging. Apache 2.0. (`curl -fsSL https://forgecode.dev/cli | sh`)

ACP as an LSP-equivalent for agents is the conceptual claim to watch — if it achieves adoption comparable to LSP, it would decouple editors from agent implementations at the protocol layer.

HN Show HN: https://news.ycombinator.com/item?id=47594802

Sources: https://github.com/forge-agents/forge · https://github.com/Adulari/forge · https://medium.com/@richardhightower/forgecode-dominating-terminal-bench-2-0-harness-engineering-beat-claude-code-codex-gemini-etc-eb5df74a3fa4

Platform signal: 🌐 global (HN)

---

### 17. [new] OpenCode Rebrands to Anomaly, Hits 165k Stars with July Feature Push

**OpenCode** (formerly SST) rebranded to **Anomaly** — repo moved to github.com/anomalyco/opencode. Old `sst/opencode` Docker references break. Stars: 165k+.

July 2026 updates: connector-based auth flows, stored provider credentials, v2 API endpoints (create/fetch sessions, list questions, active location resolution), nested subagent launch fixes with configurable `subagent_depth`, OpenAI pro reasoning mode support. 75+ LLM endpoints (Anthropic, OpenAI, Google, AWS Bedrock, Azure, OpenRouter, Ollama).

Sources: https://releasebot.io/updates/sst/opencode · https://github.com/anomalyco/opencode · https://www.gradually.ai/en/changelogs/opencode/ · https://www.morphllm.com/comparisons/opencode-vs-claude-code

Platform signal: 🌐 global

---

**Still true** (no new facts since prior briefing, not re-explained):

- **jadepuffer-agentic-security** — JADEPUFFER first agentic ransomware (July 1, Sysdig); SingGuard-NSFA (Ant Group, July 14) as open-source guardrail response
- **grok-build-xai-rust-harness** — SpaceXAI Grok-Build (Rust, Apache 2.0, 23.3k stars, ACP support)
- **self-harness-auto-optimization** — Shanghai AI Lab Self-Harness (arXiv:2606.09498) +60% Terminal-Bench 2.0
- **openharness-hkuds** — HKUDS/OpenHarness (MIT, 15.1k stars, 43 tools, ohmo agent across Feishu/Slack/Telegram)
- **vscode-1130-agent-host** — VSCode 1.130 Agent Host Protocol (AHP, July 22): agent sessions decouple from window lifetime
- **antigravity-gemini-cli-successor** — Google Antigravity 2.0 (successor to Gemini CLI, retired June 18); SKILL.md portable unchanged
- **claw-code-claude-rewrite** — Claw Code (105k stars) clean-room rewrite; fastest-growing repo in GitHub history
- **metaharness-scaffold-generator** — ruvnet/agent-harness-generator (MetaHarness, 523 stars); branded npm harnesses with Darwin Mode
- **harness-engineering-paradigm** — "Agent = Model + Harness" dominant 2026 paradigm; 3% vs 47% performance gap; confirmed by DeepSeek, Qiita/Zenn
- **deerflow-superagent-harness** — ByteDance DeerFlow 2.0 (77.9k stars); TIAMAT cloud memory backend
- **hermes-agent-self-improving** — Nous Research Hermes: native desktop app, self-improving loop; Grok integration active
- **omnigent-meta-harness** — Databricks Omnigent (Apache 2.0, June 2026): compose/swap harnesses; Beta as of July 17
- **zot-go-coding-harness** — Zot (299 stars, Go, HN 107 pts); API spoofing controversy ongoing
- **omp-omo-pi-derivatives** — oh-my-pi (14.7k stars), oh-my-openagent (48k stars); Sisyphus Orchestrator
- **yorishiro-presence-harness** — Yorishiro (58 stars); macOS Presence Harness with 3D avatar, Reflex Layer
- **agentskills-open-standard** — agentskills.io SKILL.md portable across 20+ harnesses; zero modification required
- **anthropic-managed-agents-mcp-tunnels** — Managed Agents, self-hosted sandboxes, MCP Tunnels (research preview) shipping
- **letta-agent-file-format** — Letta Agent File (.af, Apache 2.0, 1.2k stars); leading serialization format for stateful agents
- **layered-oss-stack-over-single-framework** — 2026 consensus: 17+ specialized OSS layers per task; star count ≠ maintenance
- **macos-harness-proving-ground** — macOS as proving ground: Yorishiro, macOS26/Agent!, Supacode
- **ahe-automated-harness-evolution** — arXiv:2604.25850 formalizes AHE; Lilian Weng July 4 synthesis
- **harness-internal-external-disambiguation** — Internal vs External Harness distinction causing practitioner confusion
- **environment-architect-new-role** — "Environment Architect" as new engineering role; translating domain knowledge into harness specs

---

## Cross-Source Patterns

### Pattern 1: The Stateless Turn — MCP, Skills, and Infrastructure Decoupling

Appeared on: 🌐 Web (spec blog, WorkOS, AAIF), 🇯🇵 GIGAZINE/Publickey/Mamezou, 🇨🇳 Pedaily/Tencent Cloud, HN (indirectly via Forge/ACP discussions)

The MCP 2026-07-28 stateless spec, combined with Kiro CLI V3's "unified harness powering all surfaces simultaneously," and MAF's "pull skills from MCP on demand" all point to the same infrastructure direction: **harness state and skill state should be decoupled from individual sessions and deployments**. Serverless MCP + on-demand skills = harness-as-infrastructure rather than harness-as-app.

Japanese practitioners: "これにより、AWS等クラウド環境との相性が格段に良くなりました" (This dramatically improves compatibility with cloud environments like AWS) — Mamezou Developer.

Chinese practitioners: MCP-as-USB-C for AI, emphasizing interoperability as the value proposition.

### Pattern 2: Security Scaling Problem Hits Harness Extension Ecosystem

Appeared on: 🌐 Web (NVIDIA, Towards Data Science, aiinsiders.net, OpenClaw blog), prior signal from NSA MCP guidelines thread

The extension economy is large enough to be a supply-chain target. NVIDIA SkillSpector, OpenClaw/NVIDIA partnership, NVIDIA Verified Skills/Skill Cards, and the "1-in-4 skills has a real vulnerability" finding all arrived in the same week as the largest MCP spec update. The timing is deliberate: the new spec's stateless architecture and formal Extensions Track governance directly address the attack surface that results from arbitrary server/skill execution.

Quote: "Agent skills — the extensions that Claude Code, Codex CLI, Gemini CLI, and similar tools execute with implicit trust — are a new and largely unvetted attack surface." — NVIDIA SkillSpector docs

### Pattern 3: Control Plane Wars — Multi-Harness Orchestration as Differentiated Category

Appeared on: 🌐 Web (Warp, Databricks/Omnigent, htek.dev comparison, SD Times), HN

Three distinct products now explicitly compete as multi-harness orchestration layers: **Warp Oz** (first mover, cross-harness memory, enterprise), **Databricks Omnigent** (meta-harness for policy + composition), **Kore.ai Artemis** (Agent Blueprint Language + 6 orchestration patterns). All three are betting that the top of the harness stack — the control plane that governs multiple harnesses — is a distinct and durable market position.

Key: July 2026 marks the first month where multiple vendors explicitly name "multi-harness orchestration" as a product category in their marketing.

### Pattern 4: Minimal-Harness Countermovement

Appeared on: 🌐 Web (Pi, Statewright, Pu.sh/HN, sdd-riper), 🇯🇵 Qiita harness engineering guide

As the major harnesses grow heavier, a countermovement toward minimal, deterministic harnesses is gaining stars:
- **Pi**: sub-1,000-token system prompt; lazy skills; 54k stars
- **Statewright**: Rust state machine for deterministic guardrails; 373 stars; 2/10 → 10/10 improvement
- **Pu.sh**: 400-line shell harness (HN Show HN)
- **sdd-riper**: "let strong models explore while humans steer with minimal specs"

Japanese practitioners articulating the 3% (prompt) vs 47% (harness) performance gap as justification, while simultaneously noting that over-specifying harnesses adds its own failure modes.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| statewright | Show HN: Statewright – Visual state machines that make AI agents reliable | ~50 | multiple | "2 local models improved from 2/10 to 10/10 with constraints enabled" | https://news.ycombinator.com/item?id=48108778 |
| (author) | Show HN: Pu.sh – a full coding-agent harness in 400 lines of shell | N/A | many | "code of this quality does not engender confidence" (commenter on minification) | https://news.ycombinator.com/item?id=47968112 |
| (author) | Open-Source Agentic QA Harness with Memory | ~50 | several | "prevents LLMs from writing hacky tests by separating observation from execution" | https://news.ycombinator.com/item?id=48191312 |
| (author) | Show HN: Initialize an AI Harness with Forge CLI | N/A | N/A | ACP: "open standard that lets any editor work with any agent, similar to LSP" | https://news.ycombinator.com/item?id=47594802 |
| (esengine) | DeepSeek reasonix, native coding agent with prefix caching and low cost | N/A | N/A | "much more mature harness" in context of DeepSeek | https://news.ycombinator.com/item?id=48256953 |
| (author) | The importance of Agent Harness in 2026 | N/A | N/A | General harness discussion | https://news.ycombinator.com/item?id=46531173 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (OpenClaw/community) | Grok in Hermes and OpenClaw (Skills, Connectors, and More) | N/A | N/A | No | https://www.youtube.com/watch?v=KPMA7Rnx4WM |
| (Nous Research/community) | Hermes Agent desktop app walkthrough | N/A | N/A | No | https://www.youtube.com/watch?v=_LYXbI6JY5M |

**Web (global) — Key Pages:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | MCP 2026-07-28 spec: stateless core, ext-* framework, Tasks/MCP Apps, OAuth |
| 🌐 | github.blog | https://github.blog/changelog/2026-07-29-copilot-code-review-agent-skills-and-mcp-now-generally-available/ | Copilot code review: agent skills + MCP GA July 29 |
| 🌐 | kiro.dev | https://kiro.dev/changelog/ | Full July 2026 Kiro changelog: CLI V3, Opus 5, GPT-5.6, global hooks |
| 🌐 | releasebot.io | https://releasebot.io/updates/anthropic/claude-code | Claude Code July changelog: /fork, depth-3, Opus 5, 200-cap |
| 🌐 | warp.dev | https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration | Warp Oz multi-harness control plane; cross-harness memory |
| 🌐 | blog.mozilla.ai | https://blog.mozilla.ai/introducing-otari-the-open-source-llm-control-plane/ | Mozilla Otari: open-source LLM gateway with agent harnesses |
| 🌐 | github.com/statewright | https://github.com/statewright/statewright | Statewright: Rust state machine guardrails; 2/10 → 10/10 SWE-bench |
| 🌐 | github.com/headroomlabs-ai | https://github.com/headroomlabs-ai/headroom | Headroom: 62k stars; 20-95% token reduction; library+proxy+MCP |
| 🌐 | github.com/earendil-works | https://github.com/earendil-works/pi | Pi: minimal harness; 54k stars; lazy skills; sub-1000-token |
| 🌐 | developer.nvidia.com | https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/ | NVIDIA SkillSpector + Verified Skills; 1-in-4 vulnerable |
| 🌐 | github.com/HKUDS/CLI-Anything | https://github.com/HKUDS/CLI-Anything | CLI-Anything: 46.4k stars; makes any software agent-native |
| 🌐 | github.com/forge-agents | https://github.com/forge-agents/forge | Forge: ACP universal CLI; 15+ agents; LSP-for-agents claim |
| 🌐 | panews.io | https://panews.io/articles/019eede8-f90e-746d-929c-82a7c608db11 | DeepSeek "Model + Harness = Agent" formula; domestic AI shifts to harness layer |
| 🌐 | winbuzzer.com | https://winbuzzer.com/2026/05/25/reasonix-launches-deepseek-native-terminal-coding-agent-xcxwbn/ | Reasonix: DeepSeek-native terminal agent with prefix-cache optimization |
| 🌐 | sdtimes.com | https://sdtimes.com/ai/warp-updates-oz-to-help-enterprises-orchestrate-coding-agents-across-any-model-or-harness/ | Warp Oz enterprise update coverage |
| 🌐 | htek.dev | https://htek.dev/articles/all-agent-harnesses-live-comparison | Comprehensive harness comparison: includes Kore.ai Artemis, Neura, Mozilla Otari, Statewright |
| 🌐 | devblogs.microsoft.com | https://devblogs.microsoft.com/agent-framework/discover-agent-skills-from-mcp-servers-in-net/ | MAF: pull agent skills from MCP servers on demand (July 28) |
| 🌐 | releasebot.io | https://releasebot.io/updates/openclaw | OpenClaw 2026.7.2-beta.5: session rewind, MCP Apps, durable delivery |

**Web (Japan 🇯🇵) — Key Pages:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | gigazine.net | https://gigazine.net/news/20260729-model-context-protocol-2026-07-28/ | MCP 2026-07-28 largest update; stateless; breaking changes warning |
| 🇯🇵 | publickey1.jp | https://www.publickey1.jp/blog/26/mcp728mcpgithub_mcp.html | MCP July 28; GitHub MCP same-day update; stateless = load balancing |
| 🇯🇵 | qiita.com | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | Harness Engineering complete guide; Planner/Generator/Evaluator 3-agent pattern |
| 🇯🇵 | qiita.com | https://qiita.com/shatolin/items/ca1810e419fee5fd963b | Claude Code plugins/MCP/tools; Claude-Mem 20k stars; Superpowers 43k |
| 🇯🇵 | zenn.dev | https://zenn.dev/atsukish/articles/e080ae2847540d | MCP (tools) vs Agent Skills (wisdom) as complementary; hybrid strategy |
| 🇯🇵 | zenn.dev | https://zenn.dev/picnic/articles/vscode-updates | VS Code evolving as multi-agent hub: MCP Apps, agent lifecycle, session memory |
| 🇯🇵 | qiita.com | https://qiita.com/aktsmm/items/ab4c4caa0bee262f06ed | Agent Skill Ninja: VS Code extension for managing Skills |
| 🇯🇵 | qiita.com | https://qiita.com/kai_kou/items/94b00143fc895ac0271e | Anthropic multi-agent harness intro: 3-agent design (Planner/Generator/Evaluator) |
| 🇯🇵 | zenn.dev | https://zenn.dev/muramasa0228/articles/2026-06-20-mcp-zenn-pipeline | Claude Code + MCP pipeline: write article → Zenn publish → portfolio accumulation |
| 🇯🇵 | note.com | https://note.com/gtminami/n/n973c3052b93f | Why MCP was redesigned; what changes in AI tool connectivity |
| 🇯🇵 | developer.mamezou-tech.com | https://developer.mamezou-tech.com/blogs/2026/07/10/mcp-spec-2026-07-28-rc/ | MCP 2026-07-28 RC analysis: stateless → edge/serverless compatibility |
| 🇯🇵 | future-architect.github.io | https://future-architect.github.io/articles/20260622a/ | Evaluating agent skills: building assessment frameworks |

**Web (China 🇨🇳) — Key Pages:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | news.pedaily.cn | https://news.pedaily.cn/202607/566963.shtml | MCP SDK 400M+ monthly downloads; "最大规模MCP升级" |
| 🇨🇳 | cloud.tencent.com | https://cloud.tencent.com/developer/article/2653637 | MCP maturing in 2026 vs 2025 hype; enterprise adoption |
| 🇨🇳 | developer.cloud.tencent.com | https://developer.cloud.tencent.com/article/2703450 | MCP "USB-C for AI"; Tencent Cloud integration; Industrial IoT + AI agents |
| 🇨🇳 | juejin.cn | https://juejin.cn/post/7646938869472378915 | MCP + A2A + AG-UI three-protocol landscape analysis |
| 🇨🇳 | alianga.com | https://alianga.com/articles/mcp-servers | 8 Chinese MCP marketplace platforms; Alipay MCP as first payment scenario tool |
| 🇨🇳 | panews.io | https://panews.io/articles/019eede8-f90e-746d-929c-82a7c608db11 | DeepSeek harness team; "domestic AI competition battlefield shifts to harness layer" |
| 🇨🇳 | www.tinyash.com | https://www.tinyash.com/blog/safari-mcp-server-news/ | Apple Safari MCP Server (July 3); agents can read DOM/screenshots in Safari |
| 🇨🇳 | jishuzhan.net | https://jishuzhan.net/article/2066505783961022465 | AI Agent practical development: 2026 mainstream frameworks + MCP deep analysis |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (skill unavailable)
├─ 🔵 X: 0 posts (skill unavailable)
├─ 🔴 YouTube: 2 videos │ views not captured
├─ 🟢 HN: 6 stories │ ~50 pts each
├─ 🟣 TikTok: 0 (skill unavailable)
├─ 🩷 Instagram: 0 (skill unavailable)
├─ 🦋 Bluesky: 0 posts │ 0 likes (OK per source health; no on-topic posts found)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 62 pages │ 🇯🇵 12 │ 🇨🇳 8
└─ 🗣️ Top voices: statewright (HN Show HN), headroomlabs-ai, forge-agents, Armin Ronacher (Pi), mozilla-ai │ r/— (unavailable)
```

---

## Out of Scope but Notable

- **Apple Safari MCP Server (July 3, 2026)** — https://www.tinyash.com/blog/safari-mcp-server-news/ — Apple officially released a Safari MCP server allowing AI coding agents to read DOM, capture screenshots, and execute JavaScript in browser windows. Belongs to a "browser-as-tool" category distinct from agent harnesses; could belong to open-models-geopolitics (Apple AI strategy) or a dedicated MCP-ecosystem topic if one existed. Caught my eye because it's the first major consumer platform shipping first-party MCP.

- **TencentCloud/TencentDB-Agent-Memory (+318 GitHub trending July 2026)** — https://github.com/TencentCloud/TencentDB-Agent-Memory — Local long-term memory for agents with zero external API dependencies. The "local-first, zero-external-deps" pattern (also seen in Headroom) suggests growing developer preference for agent memory that doesn't phone home. May belong to a cloud/infrastructure topic, but the zero-external-deps design principle is a distinct architectural signal.

- **microsoft/SkillOpt (+275 GitHub trending)** — https://github.com/microsoft/SkillOpt — "Text-space optimizer that trains reusable natural-language skills for frozen LLM agents." If this is what it says, it's a training-time tool for skill quality improvement — potentially closer to model fine-tuning than harness engineering, but positioned as harness infrastructure. Genuinely unclear which topic this belongs to.

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram**: Not fetched — the `/last30days` skill was unavailable for this run. These platforms were not manually covered. Reddit and X are typically the highest-engagement signal sources for this topic; their absence is the single biggest gap.
- **Bluesky**: Available (SOURCE HEALTH: bluesky=OK) but manual search returned no on-topic July 2026 posts specifically about agent harnesses — zero findings. This may reflect low Bluesky penetration for this topic, or limitations of keyword-based search on the platform.
- **Polymarket**: Not searched; no agent harness prediction markets known.
- **GitHub Trending exact star counts**: Where GitHub Trending delta star counts are cited (+N), these are from the July 9 digest snapshot (startupcorners.com) and may not reflect latest state.
- **Juejin full content**: Several Juejin articles returned "Please wait..." (JS-rendered pages) — content extracted from search snippets only, not full fetches.
- **Approx coverage**: ~75% — strong Web/HN/JP/CN coverage; Reddit/X/social missing.

---

## Key Quotes

> "Any MCP request can land on any server instance." — MCP 2026-07-28 specification blog, on the stateless core ([link](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/))

> "Companies shouldn't have to bet their future on a single model or harness." — Warp, on Oz multi-harness platform ([link](https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration))

> "A deliberate rebuttal to the bloated-harness era — the argument that the model is already smart enough, and the harness should get out of its way." — Pi agent harness documentation ([link](https://ailearningguides.com/pi-ai-coding-agent-2026-lean-cli/))

> "Model + Harness = Agent." — DeepSeek internal Harness team recruitment JD, 2026 ([link](https://panews.io/articles/019eede8-f90e-746d-929c-82a7c608db11))

> "Agent skills — the extensions that Claude Code, Codex CLI, Gemini CLI, and similar tools execute with implicit trust — are a new and largely unvetted attack surface." — NVIDIA SkillSpector documentation ([link](https://docs.nvidia.com/skills/scanning-agent-skills))

> "1 in 4 skills has a real vulnerability" — from 42,447 skills analyzed in "Agent Skills in the Wild" (Liu et al., 2026) ([link](https://github.com/nvidia/skillspector))

> "ACP is an open standard that lets any editor work with any agent, similar to how LSP standardized language servers." — Forge CLI (ACP) project ([link](https://github.com/forge-agents/forge))

> "MCPクライアントからのリクエストはどのMCPサーバに到着しても処理されるようになります" ("MCP client requests will be processed regardless of which server they reach") — Publickey.jp on MCP 2026-07-28 (🇯🇵) ([link](https://www.publickey1.jp/blog/26/mcp728mcpgithub_mcp.html))

> "ハーネス設計こそが2026年のソフトウェア開発における競争優位" ("Harness design is the competitive advantage in 2026 software development") — Qiita, Ryu-Yanagi harness engineering guide (🇯🇵) ([link](https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb))

> "从'对话式AI'到'行动式AI'的范式跃迁" ("Paradigm leap from 'conversational AI' to 'action-oriented AI'") — Tencent Cloud Developer article (🇨🇳) ([link](https://developer.cloud.tencent.com/article/2703450))
