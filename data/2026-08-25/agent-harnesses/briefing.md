# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-25
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Releasebot, Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Not accessed |
| YouTube | 1 URL | — | 🌐 Copilot Studio Aug 2026 (URL logged) |
| Hacker News | 3 threads | ~273 pts, comments | Show HN: Huzzah; OneCLI (ongoing); HarnessRouter (ongoing) |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | ~6 posts | — | 🦋 bluesky=OK; no on-topic Aug 25 posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~90 pages | — | 🌐 WebSearch + WebFetch; 18+ query passes |
| Web (Japan) | ~14 pages | — | 🇯🇵 Qiita (5), Zenn (4), gihyo.jp, Innovatopia, codezine, GMO Developers, Acsim, every.tv |
| Web (China) | ~12 pages | — | 🇨🇳 Zhihu (5), CSDN (2), Juejin (4), Aliyun, Tencent Cloud, cnblogs, GitHub CN-originated |

---

## Synthesized Findings

### 1. [update] Claude Code v2.1.238–245: /design, modelPicker, Keyless Sign-In, zstd Binary 🌐

**New facts since Aug 21:** Six releases in five days (v2.1.238–245). Major additions: /design research preview, keybindingFlavor="readline", loops breakdown in /usage, modelPicker customization, keyless sign-in via Anthropic Console, startup binary compressed 75 MB (was 340 MB), MCP auto-reconnect. Critical bug fixes: glibc 2.44 startup crash (Arch/Fedora), MCP v2 stream reopen loop, 100% CPU idle sessions on Linux with sandboxing.

**Evidence:**
- **v2.1.238 (Aug 20):** keybindingFlavor="readline" (Bash-style Ctrl+W); Remote Control HTTP 403 tolerance (3 min); cross-session messaging on Windows; /claude-api upgrade Python 0.x→1.x migration; plugin marketplace headersHelper support
- **v2.1.239 (Aug 21):** /cost + status line + --max-budget-usd now includes 1.1× US-inference premium for data-residency workspaces; fullscreen renderer on Bedrock/Vertex/Foundry; Alpine/musl: native image paste, clipboard, audio add-ons
- **v2.1.241 (Aug 23):** MCP v2 stream reopen bug fixed; notification hooks fixed for Claude Desktop/VS Code; Linux CPU 100% idle bug fixed; bundled skill aliases "Unknown command" fixed
- **v2.1.243 (Aug 25):** loops breakdown in /usage per-loop metrics; modelPicker setting; keyless Anthropic Console sign-in; startup time improved via zstd-compressed binary (75 MB vs 340 MB); MCP reconnect after drops; /resume loads more sessions while scrolling
- **v2.1.245 (Aug 25):** glibc 2.44 startup crash fix (Arch Linux, CachyOS, Fedora Rawhide)
- **Earlier (v2.1.232–237, confirmed Aug 17–20):** /design research preview (ideas/screenshots → editable artboards); auto-resume on usage limit reset; plain-language allow/deny rules; @-mention to delegate between open sessions; Claude Workbench discontinued Aug 17 → console.anthropic.com

> 🇯🇵 Qiita/aimakerlab: 「IDEを閉じていても動く。深夜も動く。これがClaude Codeが「インフラ」になっている理由。」 ("Claude Code runs with the IDE closed and works at night — this is why it functions as infrastructure.") — [link](https://qiita.com/aimakerlab/items/d52cc2199a07a438c78e)

**Sources:** https://releasebot.io/updates/anthropic/claude-code · https://dev.classmethod.jp/en/articles/20260822-cc-updates-v2-1-239/ · https://origami.sa/en/blog/claude-code-august-2026/ · https://github.com/anthropics/claude-code/releases · https://code.claude.com/docs/en/changelog · https://www.claudeupdates.dev/

---

### 2. [new] Block Berd: Apache 2.0 Desktop Workspace Above Agent Runtimes 🌐

**Claim:** Block (Jack Dorsey) open-sourced Berd on Aug 19 — a local-first desktop app (Apache 2.0, v0.6.2, 91 contributors) that orchestrates above Goose/Claude Code/Codex, not instead of them; stores conversation history locally; "Gloopies" visual agent identities.

**Evidence:**
- **Orchestration layer:** sits above agent runtimes; doesn't bundle its own agent loop
- **Local-first:** conversation history on user device; no cloud dependency for storage
- **Gloopies:** distinct visual identities for each configured agent
- **Persistent projects:** retain files, instructions, agent configurations across sessions
- **Platform:** free macOS/Windows/Linux builds; Apache 2.0
- **Brad Axen (Block):** "Berd provides the consistent desktop environment around those harnesses"
- **Origin:** built internally for Block employees; now open-sourced
- **Comparables:** similar orchestration intent to ECC (cross-harness OS) and Warp Oz, but Block-backed and local-first

**Sources:** https://venturebeat.com/orchestration/blocks-new-apache-2-0-agent-workspace-berd-works-across-models-and-harnesses-stores-conversation-history-locally · https://dataconomy.com/2026/08/19/block-open-sources-berd-ai-agent-desktop-app/ · https://paperclip.ing/product/extensions/

---

### 3. [update] Hermes v0.20.5 (Aug 21): Bot Mode Group Rooms + Keyless Web Search + Cron Memory 🌐

**New facts since Aug 21:** ~323 merged PRs, ~746 commits since v0.20.4. Bot Mode now supports group-room threads (named multi-bot roster). Keyless web search: 5-vendor free rotation, ring failover, works on fresh installs with zero keys. Cron jobs gained persistent memory + per-job reasoning effort. Full curation ships with v0.21.0.

**Evidence:**
- **Bot Mode group rooms:** named multi-bot roster; group-room threads; blob-face avatars; drag-and-drop PDF/file attachments; foldable conversation summaries
- **Keyless web:** 5-vendor free rotation with ring failover; web search on fresh installs with zero keys — removes API key barrier for new users
- **Cron memory:** cron jobs persist memory; per-job reasoning effort configurable
- **CLI polish:** fuzzy /model picker; Ctrl+P command palette; richer /status
- **Execution discipline:** runtime stall guards from Composio eval findings; worktree list/prune; update receipts; fleet --plan verification
- **Performance:** paint-first Bot Mode hydration; compositor spinners; React Compiler in both renderers
- **Zero-auth provider:** opencode-free zero-auth option; multi-question clarify; desktop perf
- **v0.21.0 forthcoming:** full curated notes documenting everything from v0.20.0 onward with contributor credits

**Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.19 · https://releasebot.io/updates/nousresearch/hermes-agent · https://www.marktechpost.com/2026/08/17/nous-research-hermes-bot-mode/ · https://hermes-ai.net/changelog/ · https://changelogs.info/hermes-agent/changelog/

---

### 4. [update] OpenClaw 2026.8.1-beta.3 (Aug 24): GPT-5.6 Ultra + Puppeteer CDP + SQLite Backup 🌐

**New facts since Aug 21:** beta.3 ships GPT-5.6 Ultra across OpenClaw and Codex runtime; adds Puppeteer-compatible CDP relay support; introduces compact SQLite backup/restore commands; Gateway lifecycle supervision.

**Evidence:**
- **GPT-5.6 Ultra:** Sol, Terra, Luna, and Ultra reasoning support across OpenClaw + Codex runtime
- **Puppeteer CDP:** compatible CDP relay for browser automation
- **SQLite backup:** compact backup and restore commands
- **Gateway:** lifecycle supervision, shared ingress monitors
- **Internal QA Aug 21–23:** 6 internal releases: fail-closed QA compatibility profile, beta evidence validation, legacy CLI allowlist migration

**Sources:** https://releasebot.io/updates/openclaw · https://github.com/openclaw/openclaw/releases · https://docs.nvidia.com/nemoclaw/user-guide/openclaw/release-notes/2026/8/7

---

### 5. [new] LoopX: Long-Horizon Agent Control Plane (5.1k Stars, Apache 2.0) 🌐

**Claim:** huangruiteng/loopx (Apache 2.0, v0.4.x, 5.1k stars, 443 forks) is a provider-neutral stateful control plane operating *above* agent harnesses — not a replacement — keeping durable state (goals, todos, evidence, quota) across multi-day sessions across Codex/Claude Code/Cursor and custom runtimes.

**Evidence:**
- **Core pitch:** "layer above the loop" — durable objectives, human-approval gates, todo ownership, evidence logs, quota-aware auto-wake, verifiable handoffs
- **Cross-harness:** works alongside existing harnesses; doesn't replace loops
- **Tagline:** "Keep the loop moving. Keep judgment human."
- **Long-running work:** goals/conversations/tasks/files/schedules survive across restarts, harness switches, agent handoffs — "work that began last week resumes exactly where the last bounded turn stopped"
- **Prior versions MIT; v0.4.8+ Apache 2.0**
- **Comparable pattern:** similar to Cursor's /goal but harness-agnostic and open-source

**Sources:** https://github.com/huangruiteng/loopx · https://explainx.ai/blog/loopx-agent-control-plane-loop-engineering-august-2026 · https://dev.to/arshtechpro/loopx-a-control-plane-for-ai-agents-that-have-to-keep-working-for-days-47n · https://huangruiteng.github.io/loopx/

---

### 6. [new] @cloudflare/computer: Isolates + Containers for Agent Runtimes (Aug 3, MIT) 🌐

**Claim:** Cloudflare released @cloudflare/computer (MIT, github.com/cloudflare/computer) on Aug 3 — a novel agent runtime that dynamically selects between lightweight V8 isolates (Durable Objects) and full Linux containers, so agents use "right compute primitive for the task."

**Evidence:**
- **Architecture:** harness runs in Durable Object (isolate); calls attached container on-demand as tool
- **Virtual filesystem:** SQLite-backed, populated from cloud storage/source control; agents read/write files, run shell commands, interact with git
- **All ops gated + audited + observed**
- **Scaling:** Durable Objects → infinite horizontal; containers → vertical
- **Three pluggable backends**
- **GA preview:** https://developers.cloudflare.com/changelog/post/2026-08-03-cloudflare-computer/
- **Open source (MIT):** github.com/cloudflare/computer
- **InfoQ coverage:** https://www.infoq.com/news/2026/08/cloudflare-computer-agents/
- **Relationship to prior:** separate from Cloudflare OS (Aug 5) and Flue 2.0 (already tracked); third distinct Cloudflare agent infrastructure release in August 2026

**Sources:** https://blog.cloudflare.com/cloudflare-computer/ · https://github.com/cloudflare/computer · https://developers.cloudflare.com/changelog/post/2026-08-03-cloudflare-computer/ · https://www.infoq.com/news/2026/08/cloudflare-computer-agents/ · https://explainx.ai/blog/cloudflare-computer-agent-runtime-isolates-containers-august-2026

---

### 7. [new] Cursor Google Workspace Plugins: Gmail + Drive + Calendar in the IDE (Aug 3) 🌐

**Claim:** Cursor shipped three official Google Workspace plugins on Aug 3 giving coding agents direct read/write access to Gmail, Google Drive, and Google Calendar — enabling context-free agent workflows without leaving the editor.

**Evidence:**
- **Google Drive:** search, open, download, create, organize files
- **Gmail:** search/read mail, draft/send messages, labels, thread management
- **Google Calendar:** read schedules, create/update events, find free time
- **Agent workflow:** agent can read PRD from Drive, pull relevant Gmail thread, check calendar for release window, generate RFC in Docs — without context-switching
- **Available:** Cursor Marketplace or Customize page
- **No new Cursor releases after Aug 19** (as of Aug 25)

**Sources:** https://cursor.com/changelog/google-workspace-plugins · https://explainx.ai/blog/cursor-google-workspace-plugins-gmail-drive-calendar-august-2026 · https://byteiota.com/cursor-3-google-workspace-plugins-gmail-drive-and-docs-in-your-ide/ · https://www.joinnextdev.com/blog/cursors-google-workspace-plugins-change-the-rules

---

### 8. [new] Huzzah: Pseudocode-First Editor (Show HN, ~273 pts) 🌐

**Claim:** Daniel Vaughn's Huzzah (github.com/danielvaughn/hz) proposes replacing longform English agent prompts with persistent declarative pseudocode (.hz files); generating real code alongside; source maps link intent to implementation. ~273 HN pts, 146 comments.

**Evidence:**
- **Core innovation:** prompts are pseudocode (declarative, persistent) not longform English (imperative, transient)
- **Mechanism:** .hz file → save → generates real code; source maps preserve intent alongside implementation
- **Pitch:** "less token churn, higher information density than natural-language chats; built-in developer docs that capture intent"
- **Current limit:** new codebases only; multi-file scaling unproven
- **HN reaction:** most-upvoted comment: "Programming is meditative, it is a thinking process... Agent-based development... you're just barking what you want at it" — extended debate around spec-driven reinvention
- **Positioning:** midpoint between manual coding and pure agent delegation

**Sources:** https://news.ycombinator.com/item?id=49378768 · https://github.com/danielvaughn/hz · https://www.danielvaughn.dev/posts/huzzah/ · https://techplanet.today/post/huzzah-finding-the-sweet-spot-between-ai-assisted-coding-and-manual-programming

---

### 9. [new] Addy Osmani agent-skills: 89.6k Stars, 24 Production-Grade Skills (Show HN) 🌐

**Claim:** Google Engineering Lead Addy Osmani's agent-skills (github.com/addyosmani/agent-skills, MIT, 89.6k stars) ships 24 production-grade engineering skills across the full dev lifecycle, with machine-enforced quality gates; multi-harness (Claude Code, Cursor, Codex, Copilot, Cline, Gemini CLI, 70+ agents).

**Evidence:**
- **24 skills** across Define/Plan/Build/Verify/Review/Ship phases
- **8 slash commands:** /spec, /plan, /build, /test, /review, /webperf, /code-simplify, /ship
- **4 specialist personas:** code reviewer, test engineer, security auditor, web performance auditor
- **7 reference checklists:** testing, security, performance, accessibility, observability
- **Quality gates:** verification gates, anti-rationalization tables baked in from Google engineering best practices
- **Install:** `npx skills add addyosmani/agent-skills`
- **Grill-me skill** overtook Anthropic's frontend-design as most-installed non-bundled skill (756.3K vs 742.3K installs on live leaderboard)
- **Show HN thread:** https://news.ycombinator.com/item?id=49396937 (returned 429 on direct fetch)

**Sources:** https://github.com/addyosmani/agent-skills · https://www.coddykit.com/pages/blog-detail?id=512909 · https://www.agensi.io/learn/best-frontend-skills-ai-agents-2026

---

### 10. [update] OpenCode v1.18.21–23 (Aug 21–25): Vertex REP, Unknown Finish Reason, Archive Command 🌐

**New facts since Aug 21:** Three releases (v1.18.21–23). Continues responses when model returns unknown finish reason; routes Vertex AI eu/us multi-region Gemini through REP endpoints; keeps file search results visible during next search; registers archive session command in both desktop layouts.

**Sources:** https://github.com/anomalyco/opencode/releases · https://github.com/anomalyco/opencode/releases/tag/v1.18.21 · https://releasebot.io/updates/sst/opencode

---

### 11. [update] Extension Economy: claudemarketplaces.com Adds 12,800+ MCP Servers Data Point 🌐🇨🇳

**New facts since Aug 21:** claudemarketplaces.com now reports 12,800+ MCP servers alongside 23,600+ skills and 2,700+ marketplaces. DSH plugin ecosystem holding at 2,000+ professionally reviewed plugins. CN community cn-built DSH plugin categories: long-term memory, electronic pets, browser integration, vision model injection, mini-games — organic creativity beyond official scope.

**Evidence:**
- **claudemarketplaces.com:** 23,600+ skills · 2,700+ marketplaces · **12,800+ MCP servers** (new)
- **dsh-plugin.org:** 2,000+ professionally reviewed plugins (unchanged from Aug 21)
- **Oh-My-DSH:** 1,117 curated plugins; 1,521 monitored repos; 301,295 combined stars
- **agent-skills (Addy Osmani):** 89.6k stars; grill-me skill overtook Anthropic frontend-design at 756.3K installs
- **🇨🇳 Signal:** CN community building DSH plugins Hermes/DeepSeek AI never shipped (electronic pets, vision injection, mini-games) — demonstrates open plugin ecosystems attract organic creativity beyond official scope

**Sources:** https://claudemarketplaces.com/ · https://dsh-plugin.org/ · https://github.com/addyosmani/agent-skills · https://zhuanlan.zhihu.com/p/2071956716355425552 · https://github.com/libukai/awesome-deepseek-harness

---

### 12. [new] Paperclip: MIT Multi-Agent Company OS at 79.3k Stars (v2026.817.0) 🌐

**Claim:** Paperclip (github.com/paperclipai/paperclip, MIT, 79.3k stars, 14.6k forks, @dotta) is an open-source Node.js server + React UI orchestrating AI agent teams into structured companies; v2026.817.0 shipped Aug 17; repositioned from "zero-human companies" to "manage AI agents at work."

**Evidence:**
- **Multi-agent coordination:** Claude Code, Codex, Cursor, OpenClaw, HTTP bots
- **Org chart + budgets:** roles, permissions, reporting lines, per-agent monthly budgets with automatic throttling
- **Atomic task execution:** prevents duplicate work and runaway spending
- **Governance:** approval workflows, audit logging, scheduled routines (heartbeat)
- **Skills Studio:** agent training, skill library
- **Growth:** 43,900 stars in first month; 79.3k as of this briefing
- **Tagline evolution:** "open-source orchestration for zero-human companies" → "the app people use to manage agents at work" (softened positioning)

**Sources:** https://github.com/paperclipai/paperclip · https://pub.towardsai.net/paperclip-the-open-source-operating-system-for-zero-human-companies-2c16f3f22182 · https://ossinsight.io/blog/zero-human-company-2026 · https://www.dplooy.com/blog/paperclip-ai-build-zero-human-companies-with-agents

---

**Still true** (ongoing threads, no new facts this cycle):

- `copilot-autofix-dual-ai-security` — Copilot Autofix/Snowflake/Wiz Red Agent (Aug 17); no new facts
- `bullet-yc-s26-coding-agent` — Bullet YC S26; no new facts
- `book-to-skill-pdf-to-skill` — book-to-skill 12k+ stars; no new facts
- `cursor-origin-code-hosting` — Cursor Origin; no new facts
- `cursor-spacex-acquisition` — SpaceX acquisition; no new facts
- `cursor-router-workspace-plugins` — Cursor Aug 19 (subscriptions/goal) still latest; GWS plugins covered above (Finding #7)
- `agent-plugins-1-standard` — AP1.0 GA; Anthropic still absent; no new facts
- `vscode-1130-agent-host` — VSCode 1.133; no new facts
- `anthropic-managed-agents-mcp-tunnels` — CC updates now in Finding #1
- `openclaw-gateway-harness` — now updated (Finding #4)
- `deepseek-harness-v01` — plugin ecosystem ongoing (Finding #11)
- `hermes-agent-self-improving` — now updated (Finding #3)
- `claude-code-doctor-skill-hygiene` — now updated (Finding #1)
- `kiro-aws-spec-driven` — Kiro no releases after Aug 19; no new facts
- `penguinharness-self-improving` — no new facts
- `cloudflare-os-kitesurf` — @cloudflare/computer is a new distinct product (Finding #6); OS itself no new facts
- `ante-antigma-single-binary` — Ante; no new facts
- `tencentdb-agent-memory` — no new facts
- `meta-muse-code` — no new facts
- `prime-agent-rlm` — no new facts
- `aq-multiplayer-harness` — no new facts
- `qwen-code-alibaba` — no new facts
- `oh-my-agent` — no new facts
- `autoharness-deepmind` — no new facts
- `hoplite-yc-s26-cloud-deploy` — no new facts
- `vercel-ai-sdk-harnessagent` — no new facts
- `copilot-studio-ga-harness-billing` — no new facts
- `microsoft-agent-governance-toolkit` — no new facts
- `tinyagents-rust-recursive` — no new facts
- `sprocket-hardware-software-agent` — no new facts
- `gambit-reliable-agent-harness` — no new facts
- `nlah-natural-language-harnesses` — no new facts
- `skills-security-prompt-injection-36pct` — no new facts beyond Hermes v0.20.5 stall guards
- `claude-tag-slack-agent` — no new facts
- `mimo-code-xiaomi` — no new facts
- `ecc-cross-harness-os` — no new facts
- `cursor-3-11-update` — superseded
- `kimi-code-moonshot` — no new facts
- `runtime-yc-p26` — no new facts
- `noclick-always-on` — no new facts
- `nyx-offensive-testing` — no new facts
- `agentguard-security-tool` — no new facts
- `mcp-security-nsa-supply-chain` — no new facts
- `yc-qm-multiplayer-harness` — no new facts
- `mcp-stateless-spec-2026-07-28` — 12,800+ MCP servers in claudemarketplaces (extension economy update covers this)
- `jadepuffer-agentic-security` — no new facts
- `grok-build-xai-rust-harness` — no new facts
- `self-harness-auto-optimization` — no new facts
- `openharness-hkuds` — no new facts
- `antigravity-gemini-cli-successor` — no new facts
- `claw-code-claude-rewrite` — no new facts
- `metaharness-scaffold-generator` — no new facts
- `harness-engineering-paradigm` — JP/CN communities actively generating content reinforcing this
- `deerflow-superagent-harness` — no new facts
- `omnigent-meta-harness` — no new facts
- `zot-go-coding-harness` — no new facts
- `omp-omo-pi-derivatives` — no new facts
- `yorishiro-presence-harness` — no new facts
- `agentskills-open-standard` — SKILL.md + 12,800+ MCP servers in claudemarketplaces
- `letta-agent-file-format` — no new facts
- `layered-oss-stack-over-single-framework` — 🇯🇵 Zenn/aiwatch_jp actively documenting: "The age of picking a single framework winner is over"
- `macos-harness-proving-ground` — @cloudflare/computer extends pattern via Workers
- `ahe-automated-harness-evolution` — harness engineering paradigm strengthening
- `harness-internal-external-disambiguation` — still active JP discussion (Zenn/watany)
- `environment-architect-new-role` — JP continuing content production on 環境設計者
- `warp-oz-multi-harness` — no new facts
- `mozilla-otari-llm-gateway` — no new facts
- `statewright-guardrails` — no new facts
- `headroom-token-compression` — no new facts
- `pi-minimal-agent-harness` — no new facts
- `nvidia-skillspector-security` — no new facts
- `deepseek-harness-team` — absorbed into deepseek-harness-v01
- `cli-anything-hkuds` — no new facts
- `forge-acp-universal-cli` — no new facts
- `github-copilot-skills-mcp-ga` — no new facts
- `opencode-anomaly-rebrand` — updated (Finding #10)
- `block-buzz-workspace` — Block Berd is a distinct successor-era product (Finding #2); Buzz itself no new facts
- `zcode-zhihu-agent-ide` — no new facts
- `devin-desktop-windsurf-rebrand` — no new facts
- `devin-fusion-multimodel` — no new facts
- `ambiance-unix-harness` — no new facts
- `kore-artemis-abl` — no new facts
- `open-agent-passport-oap` — no new facts
- `code-as-agent-harness-paper` — no new facts
- `tilde-harness-sdk` — no new facts
- `microsoft-maf-codeact` — no new facts
- `onecli-yc-s26-credential-gateway` — no new facts (Aug 20–21 launch; ongoing discussions)
- `harnessrouter-uhp-open-standard` — no new facts
- `codex-open-platform-harness` — no new facts
- `flue-2-react-hooks-harness` — no new facts (Cloudflare computer is a separate product; Flue itself no new facts)
- `hax-c-minimalist-agent` — no new facts

---

## Cross-Source Patterns

### Pattern 1: "Layer Above the Loop" Is Becoming a Product Category 🌐

**Platforms:** GitHub, HN, Cloudflare Blog, InfoQ

Three distinct new projects this week address long-running/multi-session agent governance as a first-class problem, not bolted-on:
- **LoopX:** OSS control plane above harnesses; durable goals+evidence+quota across sessions
- **@cloudflare/computer:** selective compute primitive (isolate vs container) per task; gated/audited
- **Paperclip:** company-OS layer above agents; org charts, budgets, approval workflows

Pattern: harness primitives (context, tools, sandbox) are now table stakes; the new competition is *governance infrastructure* — what runs above multiple harnesses to coordinate work across time and agents.

---

### Pattern 2: Cloudflare Is Building Three Distinct Agent Infrastructure Layers 🌐

**Platforms:** Cloudflare Blog, GitHub, InfoQ, Latent Space

In August 2026 alone, Cloudflare shipped three separate agent infrastructure releases:
1. **Cloudflare OS (Aug 5):** enterprise agent workspace with Gatekeepers
2. **Flue 2.0 (July 31/Aug 15 coverage):** React hooks for harness design
3. **@cloudflare/computer (Aug 3):** isolate+container agent runtime

Each targets a different layer: developer framework (Flue), enterprise workspace (CF OS), execution substrate (@computer). No single vendor had this breadth this month.

---

### Pattern 3: JP Community Settled on Harness Labor Division; CN Community Building DSH Creatively 🇯🇵🇨🇳

**Platforms:** Qiita, Zenn, Zhihu, Juejin

- **🇯🇵:** Clear practitioner consensus = Claude Code for "autonomous/batch/overnight" work; Cursor for "interactive/GUI/frontend." Workbench→Console migration actively documented.
- **🇨🇳:** DSH plugins organically covering categories DeepSeek never planned (electronic pets, mini-games, vision injection) — creativity-as-traction signal. 「养蛊模式」("parasite breeding mode") coined for Claude Code parallel multi-model generation.
- **Divergence:** JP community formalizing labor division rules; CN community exploring ecosystem edges.

---

### Pattern 4: Production Skill Packs Emerging as Second-Order Extension Economy 🌐

**Platforms:** HN, GitHub, Agensi, CoddyKit

Addy Osmani's agent-skills (89.6k stars) and the Show HN front-end skill pack both signal: the next wave of extension economy is NOT raw skills/MCP servers but curated, opinionated skill packs encoding real engineering workflows with quality gates. "Grill-me" overtaking Anthropic's frontend-design in install count shows community packs competing with official ones.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| danielvaughn | Show HN: Huzzah – a novel approach to coding with AI | ~273 | 146 | "Prompts are pseudocode, declarative, and persistent — unlike coding agents where prompts are longform, imperative, and transient" | https://news.ycombinator.com/item?id=49378768 |
| — | Show HN: Front end skill pack for AI agents, with machine-enforced quality gates | — | — | "76,000+ GitHub Stars; grill-me overtook frontend-design" | https://news.ycombinator.com/item?id=49396937 |
| guyb3 | Launch HN: OneCLI (YC S26) | 86 | 27 | (ongoing) | https://news.ycombinator.com/item?id=49363710 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @lemonodor.bsky.social | "Claude Code is the only agent I've found that's worth using" | — | https://bsky.app/profile/lemonodor.bsky.social/post/3lj4kzaqrfs2q |
| @anthropicbot.bsky.social | Anthropic updates post | — | https://bsky.app/profile/anthropicbot.bsky.social/post/3mfcq72km632j |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC v2.1.238–245 release tracker |
| 🌐 | DevelopersIO | https://dev.classmethod.jp/en/articles/20260822-cc-updates-v2-1-239/ | v2.1.238–239 features (EN) |
| 🌐 | Origami | https://origami.sa/en/blog/claude-code-august-2026/ | CC August 2026 feature overview |
| 🌐 | CC GitHub | https://github.com/anthropics/claude-code/releases | Official releases |
| 🌐 | CC Changelog | https://code.claude.com/docs/en/changelog | Official changelog |
| 🌐 | claudeupdates.dev | https://www.claudeupdates.dev/ | CC release history |
| 🌐 | VentureBeat | https://venturebeat.com/orchestration/blocks-new-apache-2-0-agent-workspace-berd-works-across-models-and-harnesses-stores-conversation-history-locally | Block Berd announcement |
| 🌐 | Dataconomy | https://dataconomy.com/2026/08/19/block-open-sources-berd-ai-agent-desktop-app/ | Block Berd open-source |
| 🌐 | Hermes Release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.19 | v0.20.5 release notes |
| 🌐 | Releasebot Hermes | https://releasebot.io/updates/nousresearch/hermes-agent | Hermes August tracker |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/17/nous-research-hermes-bot-mode/ | Hermes Bot Mode announcement |
| 🌐 | Hermes Changelog | https://hermes-ai.net/changelog/ | Official Hermes changelog |
| 🌐 | Changelogs.info | https://changelogs.info/hermes-agent/changelog/ | Hermes changelog archive |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OpenClaw August tracker |
| 🌐 | OC Releases | https://github.com/openclaw/openclaw/releases | OpenClaw releases |
| 🌐 | NVIDIA NemoClaw | https://docs.nvidia.com/nemoclaw/user-guide/openclaw/release-notes/2026/8/7 | NVIDIA NemoClaw Aug 7 |
| 🌐 | LoopX GitHub | https://github.com/huangruiteng/loopx | LoopX 5.1k stars |
| 🌐 | LoopX explainx | https://explainx.ai/blog/loopx-agent-control-plane-loop-engineering-august-2026 | LoopX control plane explainer |
| 🌐 | LoopX DEV.to | https://dev.to/arshtechpro/loopx-a-control-plane-for-ai-agents-that-have-to-keep-working-for-days-47n | LoopX 4 agents 47n |
| 🌐 | LoopX homepage | https://huangruiteng.github.io/loopx/ | LoopX homepage |
| 🌐 | CF Computer Blog | https://blog.cloudflare.com/cloudflare-computer/ | @cloudflare/computer announcement |
| 🌐 | CF Computer GitHub | https://github.com/cloudflare/computer | MIT source |
| 🌐 | CF Changelog | https://developers.cloudflare.com/changelog/post/2026-08-03-cloudflare-computer/ | Preview launch |
| 🌐 | InfoQ CF | https://www.infoq.com/news/2026/08/cloudflare-computer-agents/ | Stateful environments analysis |
| 🌐 | explainx CF | https://explainx.ai/blog/cloudflare-computer-agent-runtime-isolates-containers-august-2026 | CF computer explainer |
| 🌐 | Cursor GWS | https://cursor.com/changelog/google-workspace-plugins | Google Workspace plugins |
| 🌐 | explainx GWS | https://explainx.ai/blog/cursor-google-workspace-plugins-gmail-drive-calendar-august-2026 | GWS plugins breakdown |
| 🌐 | byteiota GWS | https://byteiota.com/cursor-3-google-workspace-plugins-gmail-drive-and-docs-in-your-ide/ | GWS plugins guide |
| 🌐 | nextdev GWS | https://www.joinnextdev.com/blog/cursors-google-workspace-plugins-change-the-rules | GWS rules analysis |
| 🌐 | HN Huzzah | https://news.ycombinator.com/item?id=49378768 | Show HN: Huzzah ~273 pts |
| 🌐 | Huzzah GitHub | https://github.com/danielvaughn/hz | Pseudocode editor |
| 🌐 | Vaughn blog | https://www.danielvaughn.dev/posts/huzzah/ | Creator explanation |
| 🌐 | TechPlanet | https://techplanet.today/post/huzzah-finding-the-sweet-spot-between-ai-assisted-coding-and-manual-programming | Huzzah analysis |
| 🌐 | agent-skills GH | https://github.com/addyosmani/agent-skills | 89.6k stars, MIT, 24 skills |
| 🌐 | CoddyKit | https://www.coddykit.com/pages/blog-detail?id=512909 | agent-skills 76k+ stars article |
| 🌐 | Agensi frontend | https://www.agensi.io/learn/best-frontend-skills-ai-agents-2026 | Best frontend skills |
| 🌐 | OpenCode releases | https://github.com/anomalyco/opencode/releases | v1.18.21–23 |
| 🌐 | OpenCode v1.18.21 | https://github.com/anomalyco/opencode/releases/tag/v1.18.21 | v1.18.21 details |
| 🌐 | Releasebot OCode | https://releasebot.io/updates/sst/opencode | OpenCode tracker |
| 🌐 | claudemarketplaces | https://claudemarketplaces.com/ | 23,600+ skills · 12,800+ MCP servers |
| 🌐 | Paperclip GitHub | https://github.com/paperclipai/paperclip | 79.3k stars, MIT |
| 🌐 | TowardsAI | https://pub.towardsai.net/paperclip-the-open-source-operating-system-for-zero-human-companies-2c16f3f22182 | Paperclip OS explainer |
| 🌐 | OSS Insight | https://ossinsight.io/blog/zero-human-company-2026 | Zero-human company wave analysis |
| 🌐 | Dplooy | https://www.dplooy.com/blog/paperclip-ai-build-zero-human-companies-with-agents | Paperclip AI guide |
| 🌐 | Builder Radar | https://buttondown.com/Builder-Radar/archive/builder-radar-week-of-august-16-2026/ | Week Aug 16 roundup |
| 🌐 | RyanAlberts | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked |
| 🌐 | explainx top10 | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Top 10 open/closed 2026 |
| 🌐 | DSH flowtivity | https://flowtivity.ai/blog/deepseek-harness-open-source-agent-explained/ | DSH 95k stars analysis |
| 🌐 | DSH OhMyDSH | https://ai-engineering-trend.medium.com/community-built-plugin-store-for-deepseek-hits-1-080-plugins-on-github-25c7c7977e53 | Community plugin store 1,080+ |
| 🌐 | DSH deepseekharness | https://deepseekharness.io/ | Official DSH site |
| 🌐 | dsh-plugin.org | https://dsh-plugin.org/ | 2,000+ reviewed plugins |
| 🌐 | mcpmarket.com | https://mcpmarket.com/ | MCP Market discovery |
| 🌐 | MCP docs skills | https://modelcontextprotocol.io/docs/2026-07-28/develop/build-with-agent-skills | Official MCP skills docs |
| 🌐 | Slack MCP plugin | https://docs.slack.dev/changelog/2026/07/31/slack-skills-plugin/ | Slack MCP and Skills Plugin |
| 🌐 | SpaceXAI skills | https://docs.x.ai/build/features/skills-plugins-marketplaces | xAI skills/plugins/marketplaces docs |
| 🌐 | winder comparison | https://winder.ai/ai-agent-harness-comparison/ | Harness comparison 2026 |
| 🌐 | awesome-harness | https://github.com/ai-boost/awesome-harness-engineering | Awesome harness engineering list |
| 🌐 | Vercel skill packs | https://www.digitalapplied.com/blog/agent-skill-packs-package-ecosystem-supply-chain-risk | Vercel skill packs analysis |
| 🇯🇵 | Qiita/aimakerlab | https://qiita.com/aimakerlab/items/d52cc2199a07a438c78e | CC vs Cursor Aug 17 Workbench end |
| 🇯🇵 | Qiita/aimakerlab | https://qiita.com/aimakerlab/items/73978089bc457f5158dd | CC vs Cursor Aug 2026 comparison |
| 🇯🇵 | Qiita/aimakerlab | https://qiita.com/aimakerlab/items/a7f4c8e60e7729c70066 | Claude Workbench → Console migration |
| 🇯🇵 | Qiita/muryodecode | https://qiita.com/muryodecode/items/27325f232b602290b8bc | CC harness engineering complete guide |
| 🇯🇵 | Qiita/saitoko | https://qiita.com/saitoko/items/a95cbb5888835be0f7fd | CC weekly update summary Aug 2 |
| 🇯🇵 | Zenn/watany | https://zenn.dev/watany/articles/d8b692bbca65a3 | Internal vs external harness confusion |
| 🇯🇵 | Zenn/ubie_dev | https://zenn.dev/ubie_dev/articles/sec-agent-harness-eng | Security agent harness engineering |
| 🇯🇵 | Zenn/aiwatch_jp | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | Layered OSS assembly 2026 |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/08/deepseek-harness-developer-preview | DSH developer preview JP analysis |
| 🇯🇵 | Innovatopia | https://innovatopia.jp/ai/ai-news/116283/ | AI coding: models → agent infra |
| 🇯🇵 | Docswell | https://www.docswell.com/s/Fujiwo/KX2QDY-2026-08-17-130347 | AI-driven dev walkthrough Aug 17 |
| 🇯🇵 | genai-ai.co.jp | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | CC harness engineering 3-subagent |
| 🇯🇵 | codezine | https://codezine.jp/article/detail/23340 | Long-running task harness design |
| 🇯🇵 | GMO Developers | https://developers.gmo.jp/technology/81389/ | Harness engineering practical |
| 🇯🇵 | Acsim | https://ai.acsim.app/articles/harness-engineering-2026 | Harness engineering autonomous design |
| 🇯🇵 | every Tech Blog | https://tech.every.tv/entry/2026/07/03/112235 | What is an agent harness? (JP explainer) |
| 🇯🇵 | Hexabase | https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps | Harness engineering complete guide |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1999804779141030200 | 2026 AI coding tools full evaluation |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2011401752482689910 | Claude Code / Cursor / Codex / CoPaw benchmarks |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2071956716355425552 | DSH plugins explode: pets/memory/games |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2072698072879125245 | Top 10 must-install DSH plugins |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2072466931421074027 | DSH "everything is a plugin" architecture |
| 🇨🇳 | CSDN | https://blog.csdn.net/2301_81024796/article/details/163823565 | 9 recommended DSH plugins |
| 🇨🇳 | CSDN | https://blog.csdn.net/2301_81024796/article/details/163746154 | DSH setup tutorial |
| 🇨🇳 | cnblogs | https://www.cnblogs.com/jzssuanfa/p/20143642 | Cursor 3 vs Claude Code deep comparison |
| 🇨🇳 | Juejin | https://juejin.cn/post/7677418026090233882 | 8 AI agent tools 2026 (cc-haha noted) |
| 🇨🇳 | Juejin | https://juejin.cn/post/7671084235286986803 | Aug 2026 AI stack recommendations |
| 🇨🇳 | Juejin | https://juejin.cn/post/7669935311557083163 | Aug model landscape affecting agents |
| 🇨🇳 | Juejin | https://juejin.cn/post/7666800237570637833 | CN enterprise agent platform landscape |
| 🇨🇳 | Aliyun | https://developer.aliyun.com/article/1755877 | DSH open-source architecture |
| 🇨🇳 | Tencent Cloud | https://developer.cloud.tencent.com/article/2726629 | DSH "everything is a plugin" |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2657589 | Claude Code vs Cursor 2026 selection |
| 🇨🇳 | libukai/GitHub | https://github.com/libukai/awesome-deepseek-harness | Awesome DSH guide CN-originated |
| 🇨🇳 | DSH discussion | https://github.com/deepseek-ai/deepseek-harness/discussions/1477 | Collaborative plugin guide |
| 🇨🇳 | runoob | https://www.runoob.com/deepseek-harness/deepseek-harness-plugins.html | DSH community plugins tutorial |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: 1 URL logged │ not transcribed
├─ 🟢 HN: 2 direct threads │ ~273+ pts │ 146+ comments │ + front-page scan
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: ~6 posts found │ bluesky=OK; no on-topic Aug 25 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~90 pages │ 🇯🇵 14 │ 🇨🇳 12
└─ 🗣️ Top voices: danielvaughn (Huzzah), Brad Axen (Block/Berd), Addy Osmani (agent-skills), huangruiteng (LoopX) │ 🇯🇵 Qiita/aimakerlab │ 🇨🇳 Zhihu/DSH plugin community
```

---

## Out of Scope but Notable

- **「养蛊模式」 (parasite breeding mode):** CN community coined this term for parallel multi-model generation in Claude Code — where multiple agents generate competing implementations and a human or orchestrator selects the best. Not a formal harness feature yet, but a usage pattern with its own name. If Anthropic formalizes it, it becomes a harness feature.

- **cc-haha:** Juejin/CN community mentions "cc-haha" (local-first desktop workspace for Claude Code with built-in skill marketplace) — unverified; could not independently confirm GitHub URL or star count. Worth watching if it surfaces on HN or English sources.

- **Paperclip repositioning:** The shift from "zero-human company" to "manage agents at work" is a significant framing signal — the zero-human company concept is moving from provocative pitch to practical messaging as regulatory scrutiny (EU AI Act Aug 2) increases.

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram:** not accessed; social signal layer absent
- **/last30days skill:** unavailable; replaced with multi-pass WebSearch + WebFetch
- **DuckDuckGo HTML endpoint:** returned CAPTCHA for all JP and CN queries (same as Aug 21 briefing); WebSearch in native language used as substitute — lower raw coverage than direct DDG browse
- **Bluesky:** bluesky=OK; no on-topic Aug 25 posts found in search results
- **HN rate-limiting (429):** two HN threads (49396937 front-end skill pack; 49383353 2-month autonomous agent) returned 429 on direct fetch; details sourced from search result snippets only
- **Coverage estimate: 77%** — HN and English web well covered; JP/CN passes captured key content via indexed search; social layer absent; estimated ~23% gap from missing social platforms + Reddit

---

## Key Quotes

> 「IDEを閉じていても動く。深夜も動く。これがClaude Codeが「インフラ」になっている理由。」 ("Claude Code runs with the IDE closed and works at night — this is why it functions as infrastructure.") — Qiita/aimakerlab ([link](https://qiita.com/aimakerlab/items/d52cc2199a07a438c78e)) 🇯🇵

> "Prompts are pseudocode, declarative, and persistent — unlike coding agents where prompts are longform, imperative, and transient." — Daniel Vaughn (Huzzah), Hacker News ([link](https://news.ycombinator.com/item?id=49378768)) 🌐

> "Berd provides the consistent desktop environment around those harnesses." — Brad Axen, Block ([link](https://venturebeat.com/orchestration/blocks-new-apache-2-0-agent-workspace-berd-works-across-models-and-harnesses-stores-conversation-history-locally)) 🌐

> "Keep the loop moving. Keep judgment human." — LoopX tagline ([link](https://huangruiteng.github.io/loopx/)) 🌐

> "Your agent needs a computer, not a container." — Cloudflare (@cloudflare/computer announcement) ([link](https://blog.cloudflare.com/cloudflare-computer/)) 🌐

> 「AIコーディング競争は「モデル」から「エージェント基盤」へ」 ("The AI coding competition shifts from 'models' to 'agent infrastructure'") — Innovatopia ([link](https://innovatopia.jp/ai/ai-news/116283/)) 🇯🇵

> 「単一フレームワークの勝者を選ぶ時代は終わり、harnessをレイヤーごとに組む時代になった」 ("The age of picking a single framework winner is over; the age of assembling harness layer by layer has begun") — Zenn/aiwatch_jp ([link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained)) 🇯🇵

> 「DeepSeek Harness插件一夜燃爆GitHub：长期记忆、电子宠物、4399小游戏全来了」 ("DSH plugins exploded overnight on GitHub: long-term memory, electronic pets, mini-games all appeared") — Zhihu ([link](https://zhuanlan.zhihu.com/p/2071956716355425552)) 🇨🇳
