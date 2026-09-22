# AI Agent Harnesses — Daily Briefing
**Date:** 2026-09-22
**Query type:** GENERAL
**Sources:** Claude Code changelog, OpenClaw changelog, Hermes GitHub releases, VS Code release notes, GitHub Blog, OpenAI Blog, AWS Blog, MarkTechPost, SiliconAngle, The New Stack, TechZine, devblogs.microsoft.com, Releasebot, Qiita, Zenn, note.com, CSDN, Zhihu, Juejin, GitHub Trending/agents-radar, Hacker News, Forkast, InfoWorld, Neowin, Decrypt, AiCybr, CCLeaks

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 2 stories | — | Rate-limited on direct fetch; referenced via search |
| Web (global) | 55+ pages | — | 🌐 WebSearch + WebFetch, keyless |
| Web (Japan) | 6 pages | — | 🇯🇵 Qiita, Zenn, note.com, ITmedia, Benjamin |
| Web (China) | 8 pages | — | 🇨🇳 Zhihu, CSDN/Agent CSDN, Juejin, Tencent Cloud, agents-radar CN |
| GitHub Trending | 1 digest | — | 🌐 agents-radar Sep 20-22 |

---

## Synthesized Findings

### 1. [new] AWS Strands Harness: open-source multi-model agent with 28% lower token cost 🌐

**Claim:** AWS released Strands Harness (Sep 21), Apache 2.0, Python + TypeScript, built on the Strands Agents SDK — ready-to-run agent with shell, file, and web tools built in; 28% fewer tokens at comparable accuracy across 6 benchmarks; 77% cheaper than Claude Code on same Fable 5 tasks (Terminal Bench 2.1).
**GitHub:** https://github.com/strands-agents/harness-sdk (7.5k stars)
**Install:** `pip install strands-agents-harness` or `npm install strands-agents-harness`
**Evidence:**
- Multi-model: Amazon Bedrock, Anthropic, OpenAI, Google, Ollama, LiteLLM — swap with no code change
- Context: offloads bulky tool results to files; caches reused request portions; session ID for long-term memory/resume
- Delegates subtasks to built-in helper agent; checklist for multi-step work
- Agent Skills + MCP server support out of box
- Deploy: local, ECS, Google Cloud Run, Cloudflare Containers, Azure Container Apps
- Note: The New Stack headlined "45% cheaper"; AWS's own benchmark doc cites 28% lower token cost — SiliconAngle and MarkTechPost numbers closer to AWS's claim
- Sources: https://siliconangle.com/2026/09/21/aws-debuts-strands-harness-an-open-source-ai-agent-that-can-be-deployed-in-any-environment/, https://www.marktechpost.com/2026/09/21/aws-strands-agents-team-releases-strands-harness/, https://thenewstack.io/aws-strands-harness-agent/

---

### 2. [new] Claude Code Projects: coordinator dispatches parallel cloud threads 🌐🇯🇵🇨🇳

**Claim:** Sep 17 beta — redesigned Projects adds coordinator that splits one goal into parallel cloud threads (each = independent cloud session on its own branch + repo copy); shared memory persists decisions/context across threads and sessions.
**Evidence:**
- User describes goal; coordinator scopes, delegates, reviews, assembles
- Shared memory: cross-thread retention, decisions, background state
- Work continues after laptop close (cloud sessions, not local)
- Beta: select Claude Pro/Max subscribers with cloud sessions; expanding over following week
- Not the same as the prior "Smart Reports" (Enterprise beta, Sep 11) — this is a deeper architectural redesign
- 🇯🇵 Qiita weekly roundup noted: "Claude Projectsのコーディネーターはコードを書かずに計画・委任・レビューを担う" ("The coordinator in Claude Projects does planning, delegation, and review without writing code")
- 🇨🇳 Juejin listed as one of Sep 2026's five key AI events
- Sources: https://www.unite.ai/anthropic-redesigns-claude-code-projects-to-coordinate-agent-threads/, https://xenospectrum.com/en/claude-code-projects-redesign/, https://www.itechpost.com/articles/237367/20260918/claude-code-projects-gets-major-relaunch-managing-parallel-ai-agents-cloud.htm

---

### 3. [new] Claude Code Mods: TypeScript function hooks for harness extension 🌐🇯🇵

**Claim:** Mods (in early access Sep 2026) — TypeScript plugins that run inside the engine process (not JSON over a process boundary), enabling deep harness customization: screen rendering, state, tool registration, security policy enforcement.
**Evidence:**
- Proposal: GitHub Issue #91870, Sep 3; name "Mods" decided Sep 9
- `register(on, options)` pattern; `$` engine interface; `next()` continuation; 5 layers (prepend/user/append/builtin/core)
- Built-in mods: `agents-md` (AGENTS.md support), `sec-default` (org policy — unpluggable by other mods), `diff` (side column uncommitted changes), `telemetry` (recording)
- Enable: `CLAUDE_CODE_ENABLE_FUNCTION_HOOKS=1 claude` (API can still change between releases)
- Community: cc-arcade (playable games inside Claude Code interface)
- 🇯🇵 Zenn @nogu (Sep 19): "「Claude Mods」はClaudeCodeのハーネスそのものをTypeScript関数フックで拡張するプラグインシステムです" ("Claude Mods is a plugin system that extends the Claude Code harness itself with TypeScript function hooks")
- Sources: https://zenn.dev/nogu66/articles/claude-code-function-hooks-claude-mods, https://blog.4sapi.com/blog/claude-mods-typescript-hooks-developer-guide, https://github.com/anthropics/claude-code/issues/91870

---

### 4. [new] GitHub Copilot runtime rewritten in Rust via agents — $120k, 14.5 weeks 🌐🇨🇳

**Claim:** Sep 16 — GitHub disclosed 832,378 lines of production Rust replacing the TypeScript/Node.js Copilot agent runtime; Copilot agents wrote 61% of 1.13M tool calls; total cost $120k in tokens (136.3B, 96.2% from cache); one lead developer, ~3 weeks attributed time.
**Evidence:**
- 128 PRs merged into main; 135 releases during port (avg 1.3/day — live incremental, not a big-bang cutover)
- Motivation: Copilot runtime is now an embeddable agent engine used across GitHub, Microsoft, SDKs
- By Sep 14: all known port regressions traced and fixed
- Companion: Anthropic also did a Rust migration using Claude Code (different playbook)
- 🇨🇳 linux.do: "GitHub Copilot ：我 rusted 了！" — high engagement post; Copilot self-rewriting with its own agents seen as milestone proof-of-concept for agentic software development
- HN: https://news.ycombinator.com/item?id=49735238
- Sources: https://github.blog/ai-and-ml/generative-ai/migrating-the-github-copilot-runtime-to-rust-using-copilot/, https://devclass.com/devops/2026/09/19/microsoft-agentically-ports-copilot-runtime-to-rust-for-120k/5297592, https://thenewstack.io/github-copilot-anthropic-rust-migration/

---

### 5. [new] SEP-2640 reaches final status + Microsoft "distributed skills over MCP" architecture 🌐🇯🇵🇨🇳

**Claim:** SEP-2640 (MCP Skills Extension) merged to final status Sep 13; Microsoft Agent Framework team published pattern (Sep 16) for migrating specialist A2A agents to skills distributed over MCP — "author once, serve everywhere."
**Evidence:**
- SEP-2640 defines: `skill://` URIs; `skills/list`; `skills/get`; optional `resources/directory/read`; uses MCP Resources primitive (no new primitive needed)
- WG: AAIF; co-led Nordstrom + Anthropic; Google/GitHub/AWS/Databricks/Bloomberg participants
- Reference impl: github.com/modelcontextprotocol/experimental-ext-skills
- Microsoft pattern: keep A2A when specialist needs own model/private context/independent lifecycle; migrate to Skill over MCP when it is bounded competence (procedure + typed ops)
- Enterprise value: platform team publishes to one MCP server; all agents across org pick up without redeployment
- 🇯🇵 Zenn: "MCPはツール呼び出しの標準、Skillsは再利用可能な手順の標準" ("MCP is the standard for tool calls, Skills is the standard for reusable procedures")
- 🇨🇳 framing: "MCP的技能分发轨道落地" ("MCP's skill distribution rail lands")
- Sources: https://devblogs.microsoft.com/agent-framework/from-specialist-agents-to-distributed-skills-over-mcp/, https://forkast.news/microsoft-proposes-distributed-skills-over-mcp-as-the-post-agent-architecture/, https://github.com/modelcontextprotocol/modelcontextprotocol/pull/2640, https://modelcontextprotocol.io/community/working-groups/skills-over-mcp

---

### 6. [new] OpenAI Agents API public beta: Codex harness as managed service 🌐🇨🇳

**Claim:** Sep 10 — OpenAI put the Codex harness behind a single API call (public beta): long-lived sessions, parallel subagents, context compaction, on-demand tool search; no API fee; model billed at API rates.
**Evidence:**
- Same harness behind Codex CLI and ChatGPT for Work — now API-accessible
- Context compaction: auto-compacts earlier context as sessions approach limits; no custom bookkeeping
- Tool search: loads relevant tool defs on demand (cuts token usage, protects prompt cache)
- Compute partners: Blaxel, Cloudflare, Daytona, DigitalOcean, E2B, Modal, Oracle, Runloop, Vercel + OpenAI-hosted
- Available to all API developers at launch
- Terminal-Bench 4.0 (from search results): GPT-6 Astra in Codex 58.2% vs Claude Fable 5.1 in CC 57.9% — within margin of error at #1 slot
- Sources: https://openai.com/index/introducing-the-agents-api/, https://www.marktechpost.com/2026/09/10/openai-launches-the-agents-api-in-public-beta-putting-the-codex-harness-behind-one-api-call, https://aicybr.com/blog/openai-agents-api-codex-harness-hosted-sandboxes

---

### 7. [new] VS Code 1.138: Dev Container agents + Codex cross-app sessions 🌐🇯🇵

**Claim:** Sep 16 — VS Code 1.138 lets agents run inside a project's Dev Container (aligned with project toolchain), and Codex sessions now move between ChatGPT app and VS Code without losing state; Automations on by default.
**Evidence:**
- **Dev Container agents**: project toolchain (compilers, linters, test runners) available to agent without local install; toggle via "Use Dev Container" action
- **Codex cross-app**: continue session between ChatGPT and VS Code; swap Copilot/ChatGPT subscriptions; carry desktop automation configured in ChatGPT
- **Automations**: now on by default; export/import for team sharing
- **Session management**: auto-archive on PR merge; deletion after grace period; badge notification for sessions needing attention; parallel agents without interrupting active turn
- **1.139 Insiders**: browser-addressable links for Agent Host sessions (reopen/share from any app, issue, terminal)
- Sources: https://code.visualstudio.com/updates/v1_138, https://www.bighatgroup.com/blog/vscode-whats-new-2026-09-16/, https://www.neowin.net/news/vs-code-1138-arrives-with-dev-container-agents/

---

### 8. [new] Codex CLI 0.155: voice conversations + Touch ID for MCP 🌐

**Claim:** Sep 17 — Codex 0.155.0 adds experimental `/voice` (WebRTC voice channel with live transcripts) and Touch ID biometric gate before MCP requests on Mac (Secure Enclave signing).
**Evidence:**
- `/voice` via `/experimental`; WebRTC channel; live transcript animation; mute shortcut; workspace files linked in transcript; recording activity indicators
- Touch ID: Secure Enclave signing; MCP call blocked until biometric confirmed; backs up existing approval flow
- WSL hardening in same release
- v0.155.1: reasoning summaries disabled by default for new local TUI sessions (some providers rejected the feature)
- Sources: https://ccleaks.com/news/codex-0-155-sep-2026, https://ai-tldr.dev/releases/openai-codex-cli-0-155/, https://releasebot.io/updates/openai/codex

---

### 9. [new] Cursor Projects + Self-Hosted Machines: cloud coordinator + your own infrastructure 🌐

**Claim:** Cursor launched Projects beta (Sep 10) — coordinator agent dispatches parallel subagents across months-long workloads, reacts to Slack/schedules/PRs; Self-Hosted Machines expansion (Sep 2) lets teams run cloud agents on own infra with dynamic pools and autoscaling.
**Evidence:**
- **Projects**: coordinator doesn't write code — plans, delegates, reviews, assembles; months-long context; rolling out to all users
- **Self-Hosted Machines**: AWS Lambda, Coder, Cloudflare, Daytona, Modal, Namespace, Vercel, E2B; computer use on Linux + Mac; hibernation for cost control
- Sources: https://cursor.com/changelog, https://www.getreadyforagents.com/news/cursor-projects-self-hosted-machines/, https://aicybr.com/blog/cursor-self-hosted-machines-cloud-agents, https://pondero.ai/news/2026-09-11-cursor-projects/

---

### 10. [new] Reinventing.AI open-source AI Employee packages: 59 routines across 11 harnesses 🌐

**Claim:** Sep 19 — 8 MIT-licensed AI Employee packages (github.com/markfulton/ai-employees); each package = scheduled routines for one business role; run on user's own machine across Claude Code, OpenClaw, Hermes, OpenCode, Grok Bot, Codex, Antigravity, Muse, Pi, Cline, Qwen Code + DeepSeek.
**Evidence:**
- 59 scheduled business routines total
- No cloud required; no membership; commercial use included
- Coincides with Agent Ops Club launch (paid membership, Masterclass, Product Pass with resale license)
- Distinct from SKILL.md skill repos — these are role-based daily-driver harness extensions
- Sources: https://github.com/markfulton/ai-employees, https://www.einpresswire.com/article/941970685/reinventing-ai-releases-eight-open-source-ai-employees-on-github-under-mit-license

---

### 11. [new] BuilderIO/agent-native: shared action model for humans and agents 🌐

**Claim:** agent-native (github.com/BuilderIO/agent-native, TypeScript, trending Sep 22 +607 stars) — open-source framework where every UI action is an agent tool and vice versa; shared SQL database; MCP-compatible for Claude Code/Codex/Cursor/other clients.
**Evidence:**
- "Agent-UI parity": UI and agents operate the same codebase; shared state via versioned polling
- MCP-compatible: any MCP client can operate an agent-native app
- Framing: "agent-native app" as next architecture paradigm after SPA/SSR/PWA
- Sources: https://github.com/BuilderIO/agent-native, https://www.builder.io/blog/agent-native-architecture

---

### 12. [new] Beam CLI: open-source harness observer (AGPL-3.0) 🌐

**Claim:** Beam CLI (github.com/whyashthakker/beam-cli, AGPL-3.0, Sep 2026) — local-first monitor that sits alongside any harness, scanning hook payloads for risky shell commands, credential exposure, and destructive operations; explicitly never blocks, only observes and flags.
**Evidence:**
- Supports: claude-code, cursor, codex, copilot-cli, best-effort Gemini
- Also offline-scans SKILL.md or MCP configs for known malicious patterns
- Positioned as complement to harnesses, not replacement; part of emerging runtime-security-as-sidecar category
- See also: Apollo Research Watcher Live (93% recall, blocks), AIR Security ($50M firewall) — Beam is the lightweight OSS alternative
- Sources: https://github.com/whyashthakker/beam-cli, https://blog.dailydoseofds.com/p/your-agent-harness-needs-runtime

---

### 13. [update] Claude Code v2.1.270–278: AGENTS.md, skill syncing, send-now key 🌐🇯🇵🇨🇳

**Claim:** NEW FACTS — v2.1.277 (Sep 18): AGENTS.md directly readable as CLAUDE.md fallback (4 modes via /config); v2.1.275: skills/plugins from claude.ai now sync to terminal sessions; send-now key (ctrl+enter); `claude plugin eval` for skill testing; v2.1.278: auto mode defaults to server-side classifier (no overhead charge); Claude Code Mods early access.
**Evidence:**
- AGENTS.md: default `claude-md-or-agents-md`; configure via `/config` → Project instructions
- Not available on Bedrock/Vertex/Foundry at launch
- Skill syncing: cloud skills push to terminal; opt-out with `syncClaudeAiSkills: false`
- Gateway 400-error regression (v2.1.275 → fixed v2.1.276) within hours of shipping
- 🇯🇵 Qiita aicoding-guide (Sep 20 weekly): "v2.1.277がAGENTS.mdの直接読み込みに対応" / 🇨🇳 CSDN noted "Claude Code终于支持AGENTS.md"
- Sources: https://releasebot.io/updates/anthropic/claude-code, https://code.claude.com/docs/en/whats-new, https://qiita.com/aicoding-guide/items/8ab9d3885652fdbc138a, https://qiita.com/TakanobuSano/items/c3868ff0430b314ffbcf

---

### 14. [update] OpenClaw v2026.9.5 + Trail of Bits audit: 24 vulns, 0 critical 🌐🇨🇳

**Claim:** NEW FACTS — v2026.9.5 (Sep 19, 4,179 PRs from 503 contributors); Trail of Bits security audit complete (via OpenAI's Patch the Planet initiative): 24 confirmed vulns (0 Critical, 2 High, 16 Medium, 6 Low); atomic updates (rollback to last working config if update fails); Linux AppImage + Debian packages.
**Evidence:**
- Audit scope: permission handling, identity checks, skill manifest handling
- Atomic updates: existing gateway stays running while update prepares; rollback on failure
- Linux companion: AppImage + Debian from v2026.9.5 source
- Sep 21 commits: safer skill pin + manifest byte-exact cleanup; gateway transcript artifact performance
- 🇨🇳 note: CN community tracks OC + Hermes + CC as "三大核心技术栈" ("three core tech stacks")
- Sources: https://releasebot.io/updates/openclaw, https://releases.sh/openclaw

---

### 15. [update] Hermes v0.21.4 (Sep 21): skills auto-load, 12 new plugins, JSONL output 🌐

**Claim:** NEW FACTS — v0.21.4 (Sep 21, ~1,800 PRs): `skills.auto_load` pins skills into every new session; `--format stream-json` for structured JSONL output; 12 new community plugins including Tailscale, SSH, Shodan, Terminal, RSS; Desktop font picker + one-click local engine updates; v0.21.3 (Sep 14) stability fixes.
**Evidence:**
- Host-wide gateway singleton lock (no duplicate Desktop instances)
- `session_search` now supports after/before bounds with OR-relaxed recall retry
- `hermes sessions set-journal-mode` new command
- MCP: configurable discovery concurrency (`mcp.discovery_concurrency`)
- Video: LTX 2.5 and Kling O3
- v0.21.3 (Sep 14): refresh token coalescing fix (sessions no longer expire on refresh bursts)
- Sources: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.21, https://releasebot.io/updates/nousresearch/hermes-agent, https://www.gradually.ai/en/changelogs/hermes-agent/

---

### 16. [update] Extension economy: SEP-2640 final; MCP Registry 33,766 servers; distributed skills migration 🌐🇯🇵🇨🇳

**Claim:** NEW FACTS — SEP-2640 merged final Sep 13 (skills/list, skills/get, skill:// URIs over MCP Resources); MCP Registry now 33,766 latest-version servers (Sep 20); Microsoft architectural post (Sep 16) formalizes migration from specialist agents to skills over MCP.
**Evidence:**
- claudemarketplaces.com: still 23,600+ skills / 12,800+ MCP servers (tracking unchanged)
- MCP Registry 33,766 (this is latest-version server count; prior Glama 71k+ was total registrations)
- Skills distribution rail: `skill://` URI scheme; skills/list + skills/get via MCP Resources (no new primitive)
- Trend: "packaged knowledge that once shipped as MCP server migrating to Agent Skills" — rule of thumb: MCP for live tool calls, Skills for reusable knowledge
- 🇯🇵 Zenn: "MCPはツール呼び出しの標準、Skillsは再利用可能な手順の標準"
- 🇨🇳: Skills over MCP = "一次编写，随处服务" ("author once, serve everywhere")
- Sources: https://modelcontextprotocol.io/community/working-groups/skills-over-mcp, https://github.com/modelcontextprotocol/modelcontextprotocol/pull/2640, https://devblogs.microsoft.com/agent-framework/from-specialist-agents-to-distributed-skills-over-mcp/, https://mcpmarket.com/

---

### 17. [update] DeepSeek Harness CVE-2026-82533: npm publication gap clarified 🌐🇨🇳

**Claim:** NEW FACT — the actual first published npm release containing the fix is 0.1.2-alpha.2, not 0.1.2-alpha.1 (never published to npm); 3-day gap between GitHub fix and npm publication. Stars now ~232k (+8.5k/7 days).
**Evidence:**
- OX Research disclosed Aug 24; DeepSeek pushed GitHub fix Aug 27; OX retested Aug 30
- Anyone who upgraded to 0.1.2-alpha.1 via GitHub got the fix; npm users needed to wait for alpha.2
- CVSS 9.4; agent can reach local control API and set `danger-full-access` mode (one shell command)
- 🇨🇳: highest-coverage security story from a CN-origin project; CN community noted npm gap as systemic risk
- Sources: https://aicybr.com/blog/deepseek-harness-cve-2026-82533-sandbox-escape, https://www.ox.security/blog/cve-2026-82533-deepseek-harness-ai-agent-sandbox-escape/

---

**Still true** (ongoing threads, no new facts Sep 12-22):
- **meta-muse-code**: Muse Code GA (Aug 31) remains latest; no new Sep 12-22 releases
- **colibri-lumabri-moe-inference**: colibri (26,699 stars Sep 3); lumabri; no new updates found
- **omarchy-herdr-agentic-linux**: Omarchy 4 Quattro; Herdr (Rust, ~29k stars); no new updates
- **agensi-skill-marketplace**: Agensi 70/30 revenue split; 8-point security checklist; ongoing
- **kilo-code-anaconda**: Anaconda acquisition; Kilo Marketplace; ongoing
- **harness-io-agent-ready-scm**: Harness.io security agents (Zero-Day Agent, AI SAST, etc.); Agent DLC ongoing; Code Repository + AI Code Review (Aug 27) now tracking here
- **extension-economy-explosion**: see finding #16 for updates
- **addy-osmani-agent-skills**: O'Reilly book (Aug 2026); 89.6k+ stars; ongoing
- **orca-ade-parallel-fleet**: stablyai/orca (74k stars, Sep 21 +5.9k/7 days); ongoing
- **ponytail-laziest-dev-skill**: 121,552 stars; ongoing
- **trueforge-open-source-harness**: TrueFoundry TrueForge; ongoing
- **aws-kiro-crew-open-source**: Kiro Crew (Aug 4); AgentCore prebuilt skills; ongoing
- **hiddenlayer-agent-harness-security**: runtime security for agent tool calls; ongoing
- **longhorizon-harness-amap**: AMAP-ML/LongHorizon-Harness; ongoing
- **caspian-talk-to-human-tool**: Caspian SDK; ongoing
- **kubell-whitelist-harness-tools**: allowlist-approach CLI tools; ongoing
- **block-berd-desktop-workspace**: Block Berd (Apache 2.0, v0.6.2); ongoing
- **loopx-long-horizon-control-plane**: LoopX v0.4.x; ongoing
- **cloudflare-computer-agent-runtime**: @cloudflare/computer (MIT); ongoing
- **cursor-google-workspace-plugins**: three official plugins (Gmail/Drive/Calendar); ongoing
- **huzzah-pseudocode-editor**: Huzzah (.hz persistent pseudocode); ongoing
- **paperclip-multi-agent-company-os**: Paperclip (79.3k stars); ongoing
- **onecli-yc-s26-credential-gateway**: OneCLI (Apache-2.0, 2.5k+ stars); ongoing
- **harnessrouter-uhp-open-standard**: HarnessRouter (UHP, Apache-2.0); ongoing
- **codex-open-platform-harness**: Codex CLI + open platform; see finding #6 for Agents API update
- **flue-2-react-hooks-harness**: Flue 2.0 (July 31); ongoing
- **hax-c-minimalist-agent**: Hax (C, terminal-native); ongoing
- **copilot-autofix-dual-ai-security**: Copilot Autofix Snowflake script injection; ongoing
- **bullet-yc-s26-coding-agent**: Bullet (YC S26, 95.8% SWE-bench); ongoing
- **book-to-skill-pdf-to-skill**: Leutenegger/book-to-skill (12k+ stars); ongoing
- **cursor-origin-code-hosting**: Cursor Origin (Aug 17 beta); ongoing
- **deepseek-harness-v01**: same as finding #17
- **prime-agent-rlm**: Prime Agent (PrimeIntellect, 95.5% ARC-AGI-3); ongoing
- **aq-multiplayer-harness**: AQ (aq.dev) multiplayer harness; ongoing
- **qwen-code-alibaba**: Qwen Code / qwen-audio-agent; ongoing
- **oh-my-agent**: oh-my-agent (first-fluke); ongoing
- **autoharness-deepmind**: Google DeepMind AutoHarness (arXiv:2603.03329); ongoing
- **hoplite-yc-s26-cloud-deploy**: Hoplite (YC S26); ongoing
- **vercel-ai-sdk-harnessagent**: Vercel AI SDK v7 HarnessAgent; ongoing
- **microsoft-agent-governance-toolkit**: MIT, 9500+ tests; ongoing
- **tinyagents-rust-recursive**: TinyAgents (Rust, GPL-3.0); ongoing
- **sprocket-hardware-software-agent**: Sprocket (hardware + software); ongoing
- **gambit-reliable-agent-harness**: Gambit (91 HN pts); ongoing
- **nlah-natural-language-harnesses**: NLAH (OSWorld 47.2%); ongoing (🇯🇵 tracking)
- **skills-security-prompt-injection-36pct**: Watcher Live 93% recall; AIR $50M; CHAINDROP; GitSpawn — see finding #12 (Beam) for new OSS monitoring option
- **claude-tag-slack-agent**: Claude Tag (ambient Slack agent); ongoing
- **mimo-code-xiaomi**: MiMo Code (Xiaomi, 12.6k stars); ongoing
- **ecc-cross-harness-os**: ECC (262,949 stars); ongoing
- **kimi-code-moonshot**: Kimi Code; ongoing
- **runtime-yc-p26**: Runtime (YC P26, Docker Compose snapshots); ongoing
- **noclick-always-on**: NoClick always-on infrastructure; ongoing
- **nyx-offensive-testing**: Nyx (Fabraix, 10,000+ attack strategies); ongoing
- **agentguard-security-tool**: AgentGuard (PreToolUse hook); ongoing
- **mcp-security-nsa-supply-chain**: GitSpawn + CHAINDROP + CVE-2026-82533 + AIR + Watcher; no new patches reported Sep 12-22
- **yc-qm-multiplayer-harness**: YC QM (1.9k+ stars); ongoing
- **jadepuffer-agentic-security**: JADEPUFFER/SingGuard-NSFA; ongoing
- **grok-build-xai-rust-harness**: Grok-Build (26,391 stars); ongoing
- **self-harness-auto-optimization**: Self-Harness (arXiv); ongoing
- **openharness-hkuds**: HKUDS/OpenHarness; ongoing
- **antigravity-gemini-cli-successor**: Google Antigravity 2.0; ongoing
- **claw-code-claude-rewrite**: Claw Code (~195k stars); ongoing
- **metaharness-scaffold-generator**: ruvnet/agent-harness-generator; ongoing
- **harness-engineering-paradigm**: VS Code 1.138 Dev Container agents (finding #7); SEP-2640 final (finding #5); distributed skills (finding #5)
- **deerflow-superagent-harness**: DeerFlow 2.0 (ByteDance, 77.9k stars); ongoing
- **omnigent-meta-harness**: Databricks Omnigent; ongoing
- **zot-go-coding-harness**: Zot (299 stars); ongoing
- **omp-omo-pi-derivatives**: oh-my-pi / oh-my-openagent; ongoing
- **yorishiro-presence-harness**: Yorishiro (58 stars); ongoing
- **agentskills-open-standard**: SEP-2640 final (finding #5); MCP Registry 33,766
- **letta-agent-file-format**: Letta Agent File (.af, 1.2k stars); ongoing
- **layered-oss-stack-over-single-framework**: VS Code 1.138 confirming bifurcation; ongoing
- **macos-harness-proving-ground**: VS Code 1.138 Voice Mode still experimental; ongoing
- **ahe-automated-harness-evolution**: HarnessX (arXiv:2606.14249); ongoing
- **harness-internal-external-disambiguation**: 🇯🇵 Zenn ongoing
- **environment-architect-new-role**: 🇯🇵 community; nogataka 7-layer framework; ongoing
- **warp-oz-multi-harness**: Warp Oz; ongoing
- **mozilla-otari-llm-gateway**: Mozilla Otari; ongoing
- **statewright-guardrails**: Statewright (Rust, 373 stars); ongoing
- **headroom-token-compression**: Headroom (65-66k stars); ongoing
- **pi-minimal-agent-harness**: Pi (85,757 stars); ongoing
- **nvidia-skillspector-security**: NVIDIA SkillSpector; ongoing
- **deepseek-harness-team**: see finding #17
- **cli-anything-hkuds**: HKUDS CLI-Anything (46.4k stars); ongoing
- **forge-acp-universal-cli**: Forge (ACP, 15+ agents); ongoing
- **github-copilot-skills-mcp-ga**: Copilot Rust rewrite (finding #4); Codex CLI 0.155 (finding #8)
- **block-buzz-workspace**: Block Buzz (Nostr-based); ongoing
- **zcode-zhihu-agent-ide**: ZCode (Z.ai); ongoing
- **devin-desktop-windsurf-rebrand**: Devin Desktop now at v3.10.27 (Sep 15); $48B valuation, ~$900M run-rate revenue; ongoing
- **devin-fusion-multimodel**: Devin Fusion; ongoing
- **ambiance-unix-harness**: Ambiance; ongoing
- **kore-artemis-abl**: Kore.ai Artemis; ongoing
- **open-agent-passport-oap**: OAP (arXiv); ongoing
- **code-as-agent-harness-paper**: arXiv:2605.18747; ongoing
- **tilde-harness-sdk**: Tilde (trytilde.ai); ongoing
- **microsoft-maf-codeact**: Microsoft MAF Harness GA; ongoing
- **kiro-aws-spec-driven**: Kiro; ongoing
- **cursor-spacex-acquisition**: SpaceX acquisition closed; Origin code hosting; ongoing
- **munder-difflin-office-of-clones**: Munder Difflin (303 HN pts); ongoing
- **aura-mezmo-sre-harness**: AURA (315 stars); ongoing
- **jetstream-clearance-zero-trust**: JetStream Clearance ($34M seed); ongoing
- **tenable-cyberagents-exchange-inspector**: Tenable CyberAgents Exchange; ongoing
- **vscode-1136-agent-merge**: Superseded by 1.137 (Sep 9) then 1.138 (Sep 16)
- **sonar-vortex-inside-loop**: Sonar Vortex (SemSitter, 36% token reduction); ongoing
- **devspace-minimal-mcp-harness**: DevSpace (3.5k stars); ongoing
- **skills-over-mcp-wg-sep2640**: SEP-2640 final (finding #5) — major update
- **accuknox-agentz-enterprise**: AccuKnox AgentZ; ongoing
- **harness-context-tax-problem**: ongoing
- **gstack-virtual-engineering-team**: gstack (132k stars); ongoing
- **graphify-codebase-knowledge-graph**: Graphify-Labs (115.4k stars, YC S26); ongoing
- **atlas-source-control-agents**: atlas (3.3k stars); ongoing
- **nodeterm-canvas-terminal-manager**: nodeterm (1.8k stars); ongoing
- **paseo-multi-provider-orchestration**: Paseo (16k stars); ongoing
- **openchamber-ade-opencode**: OpenChamber (~190 HN pts); ongoing
- **magnitude-local-inference-server**: magnitude (3.3k stars); ongoing
- **opencode-v2-rewrite**: Sep 2026 stability updates; Azure CLI sign-in; Bedrock improvements; ongoing
- **gpt6-astra-provider-adapter-harness**: 62.7% vs 99.9% on ARC-AGI-3; ongoing
- **context-mode-tool-output-compression**: context-mode (98% tool output reduction); ongoing
- **openclaude-community-agent**: openclaude (32.7k stars); ongoing
- **ruflo-meta-harness-swarm**: ruflo (ruvnet); ongoing
- **vscode-1137-agent-host-protocol**: see finding #7 for 1.138 follow-up
- **air-security-agent-firewall**: AIR Security ($50M); ongoing
- **gitspawn-class-vulnerability**: 4/8 unpatched Sep 1; no new patches Sep 12-22
- **watcher-apolloresearch-monitoring**: Watcher Live (93% recall); ongoing
- **harness-enterprise-governance-gap**: Harness.io report (n=700, 7/8 incidents); ongoing
- **claude-managed-agents-auto-permission**: auto mode server-side classifier (see finding #13, v2.1.278)
- **harnessx-composable-foundry**: HarnessX (arXiv:2606.14249); ongoing
- **tencentdb-agent-memory**: TencentDB Agent Memory v2.0; ongoing
- **penguinharness-self-improving**: PenguinHarness; ongoing
- **cloudflare-os-kitesurf**: Cloudflare OS + Kitesurf; ongoing
- **ante-antigma-single-binary**: Ante (~135 HN pts); ongoing
- **ante-antigma-single-binary**: ongoing

---

## Cross-Source Patterns

**1. Every major harness shipped coordinator/parallel-agent features simultaneously**
- Claude Code Projects (Sep 17): coordinator dispatches parallel cloud threads
- Cursor Projects beta (Sep 10): coordinator dispatches parallel subagents
- OpenAI Agents API (Sep 10): multi-agent subagent decomposition
- OpenClaw v2026.9.5 (Sep 19): Swarm sub-agent orchestration on by default (launched Sep 5 in 2026.9.2)
- Platforms: VS Code 1.138 session management, HN, global news

**2. AGENTS.md as multi-harness convergence standard**
- Claude Code v2.1.277 now reads AGENTS.md (fallback mode)
- Codex CLI: native AGENTS.md; Claude reading it removes last cross-tool friction
- JP community: recognized as the "shared project instructions" moment
- CN community: "Claude Code终于支持AGENTS.md" across CSDN and Zhihu
- Platforms: Qiita weekly roundup, InfoWorld, explainx.ai

**3. Open-source incumbents (DeepSeek, OpenClaw) adding formal security audits**
- OpenClaw: Trail of Bits audit complete (0 Critical, 2 High); first major OSS harness to publish a third-party audit
- DeepSeek: CVE-2026-82533 npm gap disclosure post-mortem
- Beam CLI: new AGPL-3.0 observer positioned for community-level security monitoring
- Platforms: global news, CN community (DeepSeek home project), global security press

**4. "Harness as runtime infrastructure" crystallized by Rust rewrites**
- GitHub Copilot rewrote 832k lines of production Rust using its own agents ($120k, 14.5 weeks)
- Framing: Copilot runtime is now an "embeddable agent engine used across GitHub, Microsoft, SDKs"
- Both Copilot (TypeScript→Rust) and Anthropic (Claude Code's own Rust components) used agents for large rewrites
- Platforms: GitHub Blog, The New Stack, devclass, linux.do (🇨🇳)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via search) | Empirical Study of Harness Design for Coding Agents | — | — | "ReAct-loop vs plan-and-execute: same model, very different results depending on stateful vs stateless harness design" | https://news.ycombinator.com/item?id=49753878 |
| (via search) | Migrating the GitHub Copilot runtime to Rust, using Copilot | — | high | "Copilot writing most of its own runtime migration is a proof-of-concept moment" | https://news.ycombinator.com/item?id=49735238 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | SiliconAngle | https://siliconangle.com/2026/09/21/aws-debuts-strands-harness-an-open-source-ai-agent-that-can-be-deployed-in-any-environment/ | AWS Strands Harness launch; 28% token cost reduction |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/09/21/aws-strands-agents-team-releases-strands-harness/ | 6-benchmark comparison; 77% cheaper on Fable 5 |
| 🌐 | The New Stack | https://thenewstack.io/aws-strands-harness-agent/ | "45% cheaper" headline; critical context around harness tax |
| 🌐 | GitHub Blog | https://github.blog/ai-and-ml/generative-ai/migrating-the-github-copilot-runtime-to-rust-using-copilot/ | Copilot Rust rewrite; 832k lines; $120k; 14.5 weeks |
| 🌐 | devclass | https://www.devclass.com/devops/2026/09/19/microsoft-agentically-ports-copilot-runtime-to-rust-for-120k/5297592 | Cost breakdown |
| 🌐 | The New Stack (Rust) | https://thenewstack.io/github-copilot-anthropic-rust-migration/ | GitHub vs Anthropic Rust migration playbook comparison |
| 🌐 | Unite.AI | https://www.unite.ai/anthropic-redesigns-claude-code-projects-to-coordinate-agent-threads/ | Claude Code Projects redesign details |
| 🌐 | XenoSpectrum | https://xenospectrum.com/en/claude-code-projects-redesign/ | Parallel thread architecture |
| 🌐 | InfoWorld | https://www.infoworld.com/article/4224410/claude-code-now-also-accepts-instructions-in-openais-agents-md-format.html | AGENTS.md cross-harness framing |
| 🌐 | Neowin | https://www.neowin.net/news/vs-code-1138-arrives-with-dev-container-agents/ | VS Code 1.138 Dev Container agents |
| 🌐 | OpenAI | https://openai.com/index/introducing-the-agents-api/ | Agents API launch |
| 🌐 | Forkast | https://forkast.news/microsoft-proposes-distributed-skills-over-mcp-as-the-post-agent-architecture/ | Microsoft distributed skills architecture |
| 🌐 | MS Agent Framework blog | https://devblogs.microsoft.com/agent-framework/from-specialist-agents-to-distributed-skills-over-mcp/ | Full A2A → distributed skills migration guide |
| 🌐 | AAIF | https://aaif.io/blog/skills-over-mcp | SEP-2640 final; WG status |
| 🌐 | MCP PR #2640 | https://github.com/modelcontextprotocol/modelcontextprotocol/pull/2640 | Official SEP-2640 merge |
| 🌐 | AiCybr | https://aicybr.com/blog/deepseek-harness-cve-2026-82533-sandbox-escape | CVE-2026-82533; fixed version clarification |
| 🌐 | OX Security | https://www.ox.security/blog/cve-2026-82533-deepseek-harness-ai-agent-sandbox-escape/ | Disclosure timeline |
| 🌐 | CCLeaks | https://ccleaks.com/news/codex-0-155-sep-2026 | Codex 0.155 voice + Touch ID |
| 🌐 | OpenAI (Agents API) | https://www.marktechpost.com/2026/09/10/openai-launches-the-agents-api-in-public-beta-putting-the-codex-harness-behind-one-api-call/ | Sandbox compute partners |
| 🌐 | AgentsReady | https://www.getreadyforagents.com/news/cursor-projects-self-hosted-machines/ | Cursor Projects + Self-Hosted Machines combined |
| 🌐 | AiCybr (Cursor) | https://aicybr.com/blog/cursor-self-hosted-machines-cloud-agents | Self-Hosted Machines infra details |
| 🌐 | Builder.io Blog | https://www.builder.io/blog/agent-native-architecture | agent-native architecture paradigm |
| 🌐 | GitHub (agent-native) | https://github.com/BuilderIO/agent-native | +607 stars Sep 22 |
| 🌐 | einpresswire | https://www.einpresswire.com/article/941970685/reinventing-ai-releases-eight-open-source-ai-employees-on-github-under-mit-license | AI Employee packages launch |
| 🌐 | GitHub (ai-employees) | https://github.com/markfulton/ai-employees | 8 roles, 59 routines, 11 harnesses |
| 🌐 | GitHub (beam-cli) | https://github.com/whyashthakker/beam-cli | AGPL-3.0; harness observer |
| 🌐 | Daily Dose of DS | https://blog.dailydoseofds.com/p/your-agent-harness-needs-runtime | Runtime security category framing |
| 🌐 | Releasebot (OC) | https://releasebot.io/updates/openclaw | v2026.9.5 + audit |
| 🌐 | Hermes v0.21.4 release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.21 | 1,800 PRs; skills auto_load |
| 🌐 | Releasebot (CC) | https://releasebot.io/updates/anthropic/claude-code | v2.1.270–278 |
| 🌐 | VS Code 1.138 | https://code.visualstudio.com/updates/v1_138 | Dev Container agents; Codex cross-app |
| 🌐 | BigHatGroup | https://www.bighatgroup.com/blog/vscode-whats-new-2026-09-16/ | 1.138 summary |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | 23,600+ skills / 12,800+ MCP |
| 🌐 | mcpmarket.com | https://mcpmarket.com/ | 33,766 latest-version servers |
| 🌐 | Harness.io Code Repo press | https://www.harness.io/press-and-news/harness-launches-code-repository-with-ai-code-review | Agent-ready code hosting |
| 🌐 | devops.com (Harness) | https://devops.com/harness-unfurls-source-code-repository-alternative-to-github/ | "alternative to GitHub" framing |
| 🌐 | Strandsagents.com docs | https://strandsagents.com/docs/user-guide/harness/quickstart/ | Official Strands Harness quickstart |
| 🇯🇵 | Qiita (aicoding-guide) | https://qiita.com/aicoding-guide/items/8ab9d3885652fdbc138a | Sep 20 weekly CC/Codex/Gemini roundup |
| 🇯🇵 | Qiita (TakanobuSano) | https://qiita.com/TakanobuSano/items/c3868ff0430b314ffbcf | AGENTS.md modes; JP multi-harness analysis |
| 🇯🇵 | Zenn (nogu) | https://zenn.dev/nogu66/articles/claude-code-function-hooks-claude-mods | Claude Mods deep dive; TypeScript hooks |
| 🇯🇵 | Qiita (nogataka) | https://qiita.com/nogataka/items/24db436c1123ab3d4cb2 | 7-layer harness framework for large codebases |
| 🇯🇵 | Benjamin.co.jp | https://benjamin.co.jp/blog/technologies/strands-agents-handson/ | AWS Strands hands-on (JP) |
| 🇯🇵 | ITmedia AIplus | https://www.itmedia.co.jp/aiplus/article/2608/10/2000000487/ | Agent Plugins 1.0 standard; Claude not yet supported |
| 🇨🇳 | CSDN (gitcode) | https://gitcode.csdn.net/69e7e55554b52172bc6b572f.html | "三大核心技术栈" analysis |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2043266397380272701 | CN terminal agent comparison |
| 🇨🇳 | CSDN zero-CLI tutorial | https://agent.csdn.net/6a699923662f9a54cb95abc6.html | Beginner install guide |
| 🇨🇳 | Juejin | https://juejin.cn/post/7680994387312623654 | Sep 2026 CN AI hotspots |
| 🇨🇳 | agents-radar Sep 22 | https://github.com/howe12/agents-radar/issues/557 | CN trending repos including Hermes, ECC, nanobot |
| 🇨🇳 | linux.do | https://linux.do/t/topic/2918727 | "GitHub Copilot ：我 rusted 了！" community reaction |
| 🇨🇳 | QQ news | https://news.qq.com/rain/a/20260901A06K6600 | openJiuwen/WorkSwarm CN-native ecosystem |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per research rules)
├─ 🔵 X/Twitter: 0 posts (excluded per research rules)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 2 stories (rate-limited; no point/comment counts)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no harness-specific posts found in free search)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 6 │ 🇨🇳 8
└─ 🗣️ Top voices: @nogu (Zenn), @nogataka (Qiita), @aicoding-guide (Qiita), @TakanobuSano (Qiita), Tommaso Stocchi (MS Agent Framework)
```

---

## Out of Scope but Notable

- **trycua/cua** (trending Sep 22, +609 stars): "Computer-Use 2.0" — cross-OS open-source infrastructure with standardized benchmarks; positioned as infrastructure layer, not a coding harness per se; may fit `ai-software-factory` or `open-models-geopolitics` depending on scope — flagging as potential paradigm-watch item (computer use going infrastructure-grade)
- **Microsoft/agent-lightning** (18,427 stars): RL training framework specifically for agent harnesses; sits at intersection of model training + harness engineering — may deserve own tracking if RL-based harness optimization becomes a distinct category
- **Sidetrade SAFE** (Sep 10): enterprise "Sovereign Agentic Framework" (proprietary data lake, ISO 27001, private data centers for CFO/Order-to-Cash) — signals emerging enterprise-sovereign agent harness category distinct from dev-tools ecosystem; could fit `ai-software-factory` if that topic covers vertical enterprise agents
- **openJiuwen/WorkSwarm** (CN): CN-native coding agent hitting SOTA on multiple benchmarks and landing in CN enterprise harness; separate ecosystem from CC/OC/Hermes — may merit dedicated tracking if CN-native agent ecosystem diverges further

---

## Data Gaps

- **Reddit:** Excluded per research protocol (reddit.com blocked domains)
- **X/Twitter:** Excluded per research protocol
- **Bluesky:** Starter packs list found; no individual posts retrievable without authenticated client; 0 posts logged
- **YouTube:** Not searched; no video-specific data
- **TikTok/Instagram:** Not searched
- **Polymarket:** No harness-specific prediction markets found
- **HN direct fetch:** Rate-limited (HTTP 429 on two attempts); HN data from search results only — point/comment counts unavailable
- **DuckDuckGo HTML endpoint:** Served CAPTCHA for both JP and CN queries; switched to WebSearch for JP/CN passes
- **/last30days skill:** Unavailable (unknown skill error); replaced with direct WebSearch + WebFetch multi-platform sweep
- **Cursor changelog direct fetch:** Not fetched directly; data from search results
- **Coverage estimate:** ~75% — comprehensive on core harness updates (CC, OC, Hermes, VSCode, Codex, Cursor) and major news (AWS Strands, Copilot Rust, SEP-2640, Agents API); gaps in Reddit/X/Bluesky/YouTube and long-tail HN discussions

---

## Key Quotes

> "Claude Code now reads AGENTS.md files and supports 'mods,' a plugin system for customizing the coding harness itself." — MindStudio (https://www.mindstudio.ai/blog/claude-code-mods-agents-md)

> "Copilot's own agents handled 61% of the 1.13 million tool calls the project required." — GitHub Blog (https://github.blog/ai-and-ml/generative-ai/migrating-the-github-copilot-runtime-to-rust-using-copilot/)

> "When a specialist is a bounded competence — a procedure plus typed operations — it becomes a skill over MCP. Keep A2A when the agent needs its own model, private context, or independent lifecycle." — Tommaso Stocchi, Microsoft Agent Framework (https://devblogs.microsoft.com/agent-framework/from-specialist-agents-to-distributed-skills-over-mcp/)

> "「Claude Mods」はClaudeCodeのハーネスそのものをTypeScript関数フックで拡張するプラグインシステムです" ("Claude Mods is a plugin system that extends the Claude Code harness itself with TypeScript function hooks") — @nogu on Zenn (https://zenn.dev/nogu66/articles/claude-code-function-hooks-claude-mods)

> "OpenClaw是万能执行者，Hermes是智能大脑，Claude Code是专业编码搭档——三者不是选择题，是组合拳" ("OpenClaw is the versatile executor, Hermes is the intelligent brain, Claude Code is the professional coding partner — not a multiple choice, a combination") — gitcode.csdn.net (https://gitcode.csdn.net/69e7e55554b52172bc6b572f.html)

> "The work consumed approximately 136.3 billion tokens and cost about $120,000 in model usage, including 130.6 billion cached input tokens." — devclass on Copilot Rust migration (https://www.devclass.com/devops/2026/09/19/microsoft-agentically-ports-copilot-runtime-to-rust-for-120k/5297592)

> "SEP-2640 is Final, merged on September 13, 2026." — MCP extensions track (https://github.com/modelcontextprotocol/modelcontextprotocol/pull/2640)

> "Strands Harness cost 77% less than Claude Code on the same tasks, while achieving a higher overall score on the Terminal Bench 2.1 benchmark." — MarkTechPost (https://www.marktechpost.com/2026/09/21/aws-strands-agents-team-releases-strands-harness/)
