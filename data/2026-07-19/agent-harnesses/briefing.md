# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-07-19
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 threads | — | 🌐 HTTP 403 (API blocked) — ongoing gap |
| X/Twitter | 0 posts | — | 🌐 Not scanned this pass |
| YouTube | 0 videos | — | 🌐 Not scanned this pass |
| Hacker News | 1 story | 5 pts, 1 comment | 🌐 AMA2; July 18-19 front page returned HTTP 429 |
| TikTok | 0 videos | — | No ScrapeCreators key |
| Instagram | 0 reels | — | No ScrapeCreators key |
| Bluesky | 0 posts | — | 🌐 bluesky=OK per SOURCE HEALTH; no new high-engagement posts this window |
| Polymarket | 0 markets | — | No prediction markets on harness topics |
| GitHub | 5 repos | 15.7K–36.6K stars | 🌐 stablyai/orca, can1357/oh-my-pi, wshobson/agents, agentclientprotocol/agent-client-protocol, cursor/plugins |
| Web (global) | 38 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 12 pages | — | 🇯🇵 Qiita, Zenn, note.com, hexabase.com |
| Web (China) | 11 pages | — | 🇨🇳 Tencent news/cloud, CSDN, Juejin, Zhihu, cnblogs, aieii.com |

---

## Synthesized Findings

### 1. [new] Orca (stablyai/orca) — ADE for Parallel Agent Fleets Ships v1.4.146 TODAY

Y Combinator-backed Stably AI released **Orca v1.4.146 today** (July 19, 2026), the most significant parallel-agent IDE not covered in prior briefings. Orca is an **Agent Development Environment (ADE)** built around the premise that "10x developers in 2026 are running 3–5 coding agents simultaneously" — and the workflow has stabilized: spin off a worktree, send Claude Code at it; spin off another, send Codex; spin off a third, send Cursor; compare three diffs, cherry-pick the best parts, merge. Orca makes this fleet-management frictionless.

**Key architecture:**
- Parallel git worktrees with isolated per-agent environments
- Mobile companion (iOS + Android) — monitor and control agent fleets from a phone
- Design Mode: click UI elements to send HTML/CSS/screenshots directly into agent prompts
- SSH remote worktrees: run agents on remote machines with full file editing
- Native GitHub + Linear integration for PR/issue surfacing
- WebGL-rendered terminals with infinite splits and persistent scrollback
- Orca CLI: script agent-to-IDE workflows

**Scale claim:** Developer completing 30–50 AI-assisted tasks/day vs 5–10 with single-agent workflows (July 2026 Orca Discord community benchmarks)

**Supported agents:** Claude Code, Codex, Grok, Cursor CLI, GitHub Copilot, OpenCode, Pi, Devin, Goose, Cline, and 30+ more

**Stars:** ~15,700 (MIT license)

Sources: [stablyai/orca GitHub](https://github.com/stablyai/orca), [onorca.dev](https://www.onorca.dev/), [DEV Community review](https://dev.to/andrew-ooo/orca-review-the-ide-built-for-parallel-coding-agents-15df), [andrew.ooo review](https://andrew.ooo/posts/orca-stablyai-parallel-coding-agents-ide-review/), [Daily AI World](https://dailyaiworld.com/blogs/orca-parallel-coding-agent-environment-2026), [EveryDev.ai](https://www.everydev.ai/tools/orca-ide)

---

### 2. [new] Windsurf Becomes Devin Desktop — Cascade EOL July 1, ACP Now Native

**The Cascade EOL deadline has now passed.** Windsurf rebranded to **Devin Desktop** on June 2, 2026 via OTA update; Cascade's final day was July 1. As of today (July 19), Devin Local is the mandatory local agent for all Devin Desktop users.

**Devin Local vs Cascade:** Full Rust rewrite; up to 30% more token efficient; supports parallel subagents (Cascade was single-context only). Any CI pipeline or automation script that invoked Cascade must now point at Devin Local.

**The architectural pivot — "Agent Command Center":** Devin Desktop inverts the typical IDE relationship. The Kanban board of all running local and cloud agents is now the primary interface; the code editor is a secondary tab. This is the first major IDE to make agent management the primary surface rather than code editing.

**New features:**
- **Spaces:** Early feature for sharing context between agents, grouping sessions, PRs, files, and context — expected to evolve through Q3 2026
- **Agent Router:** Upcoming feature to direct tasks to the most efficient agent or model
- **ACP support:** Native support for the Agent Client Protocol (see Finding #3 below) — Codex, Claude Agent, OpenCode, and 25+ ACP-compatible agents run as first-class agents inside Devin Desktop

🇨🇳 **CN media coverage:** news.qq.com ran "Windsurf更名Devin Desktop：推出Rust本地智能体并支持多智能体协同" (Windsurf renames to Devin Desktop: launches Rust-native agent, supports multi-agent collaboration) on June 3, confirming the story reached CN mainstream tech press.

Sources: [devin.ai/blog/windsurf-is-now-devin-desktop](https://devin.ai/blog/windsurf-is-now-devin-desktop), [byteiota.com](https://byteiota.com/windsurf-is-now-devin-desktop-what-actually-changed/), [webdeveloper.com](https://webdeveloper.com/news/windsurf-devin-desktop-cascade-eol/), [digitalapplied.com](https://www.digitalapplied.com/blog/windsurf-becomes-devin-desktop-ide-migration-2026/), [The Agent Report](https://the-agent-report.com/2026/06/cognition-devin-desktop-agent-orchestration/), [aieii.com ACP CN coverage](https://aieii.com/posts/2026-06-13-windsurf-devin-desktop-acp/), [news.qq.com 🇨🇳](https://news.qq.com/rain/a/20260603A038ZC00)

---

### 3. [new] Agent Client Protocol (ACP) — The "LSP for AI Coding Agents"

The **Agent Client Protocol** is an emerging open standard (Apache 2.0, JSON-RPC 2.0) that solves the same problem for coding agents that LSP solved for language intelligence: any agent should run in any editor without custom integration work. Created by Zed in August 2025; JetBrains adopted late 2025; the ACP Agent Registry launched January 2026.

**How it works:** Local agents run as sub-processes of the code editor, communicating via JSON-RPC over stdio. Editors expose a standardized API; agents implement the protocol once. The Registry lists dozens of agents (Claude Code, Gemini CLI, Codex, GitHub Copilot, Goose, etc.) in a discoverable format.

**Current adoption (July 2026):**
- Zed (native — created the protocol)
- JetBrains IDEs (native — IntelliJ, PyCharm, GoLand, WebStorm)
- Devin Desktop (native, launched with ACP as a founding feature)
- Neovim (community plugin)
- Emacs (community plugin)
- VS Code (partial via extensions)

**Strategic significance:** ACP decouples the harness selection decision from the IDE selection decision. If ACP achieves the same adoption curve as LSP, it would commoditize IDE integrations and shift competition back to agent capability and UX. Devin Desktop shipping ACP natively is the biggest adoption signal yet — it means the IDE best positioned to benefit from proprietary lock-in chose open interoperability instead.

Sources: [zed.dev/acp](https://zed.dev/acp), [agentclientprotocol.com](https://agentclientprotocol.com/get-started/introduction), [github.com/agentclientprotocol/agent-client-protocol](https://github.com/agentclientprotocol/agent-client-protocol), [JetBrains ACP Registry blog](https://blog.jetbrains.com/ai/2026/01/acp-agent-registry/), [jetbrains.com/acp](https://www.jetbrains.com/acp/), [blog.marcnuri.com](https://blog.marcnuri.com/agent-client-protocol-acp-introduction), [lucaberton.com](https://lucaberton.com/blog/agent-client-protocol-acp-standardizing-ai-coding-agents-2026/), [danilchenko.dev](https://www.danilchenko.dev/posts/agent-client-protocol/)

---

### 4. [new] Kiro (AWS) V3 CLI Early Access — Spec-Driven Terminal + OpenAI GPT-5.6 Added

AWS's Kiro IDE (GA since March 2026, built on Code OSS, powered by Claude via Bedrock) launched an early access preview of **Kiro CLI V3** in July 2026 with four headline changes:

1. **Spec-driven development in the terminal:** The same four-phase pipeline (Requirements.md → Design.md → Tasks.md → Code) that distinguished Kiro's IDE is now available as a CLI workflow, enabling spec-driven agents in CI/CD and scripted pipelines
2. **Capability-based permissions model:** Replaces the prior flat permissions model; agents get fine-grained capability grants rather than binary allow/deny
3. **Enhanced hooks with standalone file format:** Agent hooks (automated triggers on file save, commit, new file creation) now use a dedicated standalone file format for better composability; a new **Post Task Execution** hook fires after any task completes, enabling auto-tests, linting, or external system notifications
4. **Tag-based agent configuration:** Agents can be tagged and configured in sets

**First OpenAI models in Kiro:** GPT-5.6 Sol, Terra, and Luna added — Kiro now runs models from Anthropic, OpenAI, and (previously) Google side-by-side within one IDE. Sol is positioned for the hardest spec-driven implementation and long-horizon refactors.

Sources: [releasebot.io/updates/kiro](https://releasebot.io/updates/kiro), [kiro.dev/changelog/ide/](https://kiro.dev/changelog/ide/), [developersdigest.tech](https://www.developersdigest.tech/blog/aws-kiro-developer-guide-2026), [pingax.com](https://pingax.com/kiro-aws-launch-announcement/)

---

### 5. [new] "Friendly Fire" — AI Security-Audit Agents Tricked Into Executing Their Target's Malicious Code

A proof-of-concept attack published in The Hacker News (July 2026) exposes a new harness attack surface distinct from Agentjacking (prior briefing #5): **security-auditing agents are specifically exploitable** because they run in autonomous modes with broader tool execution authority.

**Attack mechanism:** A malicious binary is disguised as the compiled build artifact of an innocuous Go source file inside a repository. The README.md instructs users to run `security.sh` as part of routine checks. When a coding agent in autonomous audit mode follows the README instructions, it executes the binary. The payload is seeded with strings from legitimate source files to defeat Claude Code's disassembly checks.

**Affected systems:**
- Claude Code auto-mode (CLI versions 2.1.116, 2.1.196, 2.1.198, 2.1.199) on Sonnet 4.6/5 or Opus 4.8
- OpenAI Codex auto-review (CLI 0.142.4) on GPT-5.5

**Why no patch:** The weakness is architectural — the agent's designed capability to read and execute code for auditing is also the attack surface. No implementation-level fix is possible; the defense is harness-level (restrict autonomous modes when auditing untrusted repositories, require human confirmation before running any script).

**Relationship to prior findings:** This is the third distinct harness security vector in consecutive briefings: (a) Grok Build covert exfiltration, (b) Agentjacking via fake Sentry reports, (c) "Friendly fire" via auditing tasks. The common thread: the harness's trust model for instructions and execution is the attack primitive, not a model vulnerability.

Source: [thehackernews.com/2026/07/friendly-fire](https://thehackernews.com/2026/07/friendly-fire-ai-agents-built-to-catch.html)

---

### 6. [new] oh-my-pi (can1357) — Hash-Anchored Terminal Agent, 17.6K Stars

**can1357/oh-my-pi** is a terminal AI coding agent in Rust (~55,000 lines) with a distinctive approach to the "model proposes bad edits" problem: **hash-anchored edits**. Instead of the model retyping the lines it wants to change (causing whitespace battles and "string not found" loops), the model points at cryptographic anchors in the file. If a file has changed since the agent last read it, the anchor diverges and the patch is rejected — preventing silent edits to stale files.

**Capabilities:**
- 32 built-in tools
- 14 LSP operations (diagnostics, definition, type_definition, implementation, references, hover, symbols, rename, code_actions, status, reload) + format-on-write + workspace diagnostics
- 28 DAP operations (debug adapter protocol)
- 40+ language providers
- Browser access, Python runtime, subagents

**Stars:** ~17,600

oh-my-pi joins the cluster of post-incumbent terminal agents competing on tool harness quality rather than model choice. Its specific innovation (hash-anchored edits) addresses the most common failure mode in autonomous multi-file editing sessions.

Sources: [github.com/can1357/oh-my-pi](https://github.com/can1357/oh-my-pi), [skillsllm.com/skill/oh-my-pi](https://skillsllm.com/skill/oh-my-pi)

---

### 7. [new] Stanford HAI Quantification: Harness Engineering Beats Prompting by 9–15x

A note.com article (June 4, 2026) by こうへい (Kohei) citing Stanford HAI validation across 12 production use cases quantifies the harness-vs-prompt gap that practitioners have argued qualitatively:

- **Prompt optimization alone:** < 3% quality improvement
- **Harness engineering (RAG + tool access + structured validation):** 28–47% quality improvement
- **LangChain TerminalBench 2.0:** Harness-only optimization without model changes moved ranking from position 30 → position 5 (scores 52.8 → 66.5, approximately 26% improvement)
- **MindStudio Analysis:** Topology selection produces 12–23% more improvement than model selection alone
- **MCP adoption:** 97 million monthly SDK downloads as of March 2026

🇯🇵 The specific article title frames this as breaking news: 「新たな定量データ（プロンプト改善3%未満 vs ハーネス改善28-47%）」 ("New quantitative data: prompt improvement <3% vs harness improvement 28-47%").

A complementary Qiita article (@cvusk, February 23, 2026) established the "fewer tools perform better" principle via Spotify Honk (only 3 tools, 1,500+ PRs merged to production), and model routing as a cost lever (per-task cost from $0.15 to $0.054 = 64% savings). These two data points together — harness engineering as the high-ROI lever, AND simpler tool harnesses as the implementation pattern — form the emerging JP canon on harness ROI.

🇯🇵 hexabase.com went further with a business case: "50人→10人のチーム。AIエージェント×ハーネス設計が破壊する、業務自動化の常識" ("50-person → 10-person team: AI Agent × harness design destroys conventional wisdom about business automation").

Sources: [note.com/aiedgerunner](https://note.com/aiedgerunner/n/nbca11a6835f2) 🇯🇵, [qiita.com/cvusk](https://qiita.com/cvusk/items/9c3e2738eede36eb206f) 🇯🇵, [hexabase.com business automation](https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026) 🇯🇵, [hexabase.com complete guide](https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps) 🇯🇵

---

### 8. [update] Cursor Plugin Marketplace — 30+ New Partners Added (Atlassian, Datadog, GitLab)

**New fact since prior briefing:** The Cursor Marketplace (launched February 17, 2026 with Cursor 2.5) expanded significantly. By March 11, 2026, over **30 new plugins** had joined from partners including **Atlassian, Datadog, GitLab, Glean, Hugging Face, monday.com, and PlanetScale** — expanding beyond the launch set of Amplitude, AWS, Figma, Linear, and Stripe.

Plugin architecture bundles: Skills + Subagents + MCP servers + Hooks + Rules into single-click installable units. Private team marketplaces are available on Teams and Enterprise plans, enabling organizations to publish internal plugins with governance controls.

The Cursor plugin repo (github.com/cursor/plugins) is the canonical registry — third-party developers can submit plugins for marketplace listing.

Sources: [cursor.com/blog/marketplace](https://cursor.com/blog/marketplace), [cursor.com/marketplace](https://cursor.com/marketplace), [cursor.com/docs/plugins](https://cursor.com/docs/plugins), [github.com/cursor/plugins](https://github.com/cursor/plugins), [adwaitx.com](https://www.adwaitx.com/cursor-marketplace-plugins/), [engincanveske.substack.com](https://engincanveske.substack.com/p/i-tried-cursors-new-plugin-marketplace)

---

### 9. [new] wshobson/agents — 36.6K-Star Cross-Harness Plugin Marketplace

**wshobson/agents** is a production-ready multi-harness plugin marketplace with **36,600 stars** (June 2026) and approximately **94 plugins, 203 agents, 175 skills, and 109 commands** — built from a single Markdown source and consumed natively by Claude Code, OpenAI Codex CLI, Cursor, OpenCode, Gemini CLI, and GitHub Copilot.

**Architecture insight:** "One source-of-truth (plugins/) for five harnesses — each harness gets idiomatic, harness-native artifacts rather than lowest-common-denominator translations." Codex and Cursor install natively from committed registries; Gemini CLI and OpenCode install via clone-and-generate.

**Quality assurance:** Plugin-eval framework with three-layer evaluation: static analysis, LLM-judge semantic evaluation, and Monte Carlo statistical reliability testing — the first community marketplace to publish an eval spec.

This is the open cross-harness counterpart to Vercel skills.sh (closed auth) and OpenClaw Bazaar (OpenClaw-specific). At 36.6K stars it has larger GitHub traction than either.

Source: [github.com/wshobson/agents](https://github.com/wshobson/agents)

---

### 10. [new] 🇯🇵 JP New Articles: Hooks Canon + Harness Engineering Intro

Two new JP articles extend the harness engineering canon since the July 17 briefing:

**Qiita @nogataka — "Harness Engineering Intro: The AI Agent Control Paradigm After CLAUDE.md"**
- Frames harness engineering as the successor skill to CLAUDE.md authoring
- Covers hooks (PreToolUse, PostToolUse, Stop) with concrete implementations: MCP server health checks, quality gate checks before tool execution
- URL: https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 🇯🇵

**Qiita @kai_kou — "Anthropic Multi-Agent Harness Intro: 3-Agent Design for Autonomous App Development"**
- First JP article to translate Anthropic's three-agent orchestration pattern into practical guidance for autonomous app development
- URL: https://qiita.com/kai_kou/items/94b00143fc895ac0271e 🇯🇵

**MCP comparison articles (Qiita @agdexai):**
- "MCP 2026 Complete Introduction" — positions MCP as transforming the AI agent development landscape since late 2024
  https://qiita.com/agdexai/items/6ba0889696a3f7e4911f 🇯🇵
- "MCP vs A2A Full Comparison 2026" — distinguishes the two protocol types now circulating in JP developer discussions
  https://qiita.com/agdexai/items/9f32b795c10b40c6bcd5 🇯🇵

**AI/LLM Timeline 2026.06 (Qiita @yokoto):**
- Annotated timeline of AI/LLM milestones through June 2026 with agent harness focus
  https://qiita.com/yokoto/items/e110fea5892c56946826 🇯🇵

Other JP sources:
- note.com/arukt — "AI's USB-C Changes Development" — MCP as universal cross-platform connector: 「MCPは、AIを『あなたの会社のGoogle DriveやSlackと直接つなぐ共通規格』として現実のものになっています」 ("MCP is now a real standard for connecting AI directly to your company's Google Drive, Slack, etc.") — https://note.com/arukt/n/n97fb3ec1d851 🇯🇵
- Zenn @renk — "Agent Harness Research" scraps thread: https://zenn.dev/renk/scraps/a6fb7cebdea333 🇯🇵
- ai-heartland.com — JP-language hub for Claude Code, MCP, AI agents, OSS security: https://ai-heartland.com/ 🇯🇵

---

### 11. [update] 🇨🇳 CN Coverage: "IDE is Becoming an Agent Manager"; 75M Developer Stat

**New facts since prior briefing:**

**Tencent News** (June 3): Covered Windsurf → Devin Desktop rebrand: "Windsurf更名Devin Desktop：推出Rust本地智能体并支持多智能体协同" — confirms the Cascade → Devin Local transition reached CN mainstream coverage. CN developers reading Tencent News now have the ACP + multi-agent pivot framing. — [news.qq.com 🇨🇳](https://news.qq.com/rain/a/20260603A038ZC00)

**aieii.com** headline captures the architectural shift: "Windsurf 谢幕，Devin Desktop 登场：IDE 正在变成 Agent 管理器" ("Windsurf exits, Devin Desktop enters: IDE is becoming an agent manager") — the sharpest one-line summary of the category-level shift. — [aieii.com 🇨🇳](https://aieii.com/posts/2026-06-13-windsurf-devin-desktop-acp/)

**CSDN developer stat** (blog.csdn.net/df2209/article/details/162903819): "全球每月至少使用一次AI编程工具的开发者已超过7500万，比2024年增长超300%" — Monthly active AI coding tool users globally has exceeded 75 million, 300%+ growth since 2024. — [CSDN 🇨🇳](https://blog.csdn.net/df2209/article/details/162903819)

**Juejin** covers Microsoft's BUILD 2026 MCP announcement: "Microsoft在2026年Build大会上宣布全面拥抱MCP协议" (Microsoft announced full embrace of MCP protocol at 2026 BUILD conference) — adds a new data point to the prior briefing's Tencent MCP+OpenClaw finding; Microsoft's public commitment to MCP is now confirmed in CN tech press. — [Juejin 🇨🇳](https://juejin.cn/post/7651426279837171764)

**CN framing of MCP:** Both "AI 的 USB-C 端口" (Juejin) and "AI的USB-C" (JP note.com) use the same metaphor independently — cross-cultural convergence on the USB-C framing for MCP interoperability.

Other CN sources: [cloud.tencent.com MCP+agent](https://cloud.tencent.com/developer/article/2701441) 🇨🇳, [developer.cloud.tencent.com](https://developer.cloud.tencent.com/article/2703450) 🇨🇳, [CSDN MCP guide](https://blog.csdn.net/ziwoods/article/details/161662819) 🇨🇳, [aws.amazon.com/cn MCP GA](https://aws.amazon.com/cn/about-aws/whats-new/2026/05/aws-mcp-server/) 🇨🇳, [cnblogs.com comparison](https://www.cnblogs.com/deali/p/19864809) 🇨🇳, [liuqi.dev MCP stateless](https://liuqi.dev/blog/mcp-2026-stateless-revolution) 🇨🇳

---

**Still true** (ongoing from July 17 briefing — no new facts this window):
- **MCP 2026-07-28 RC** — final spec ships July 28 (9 days away); stateless core, Extensions, MCP Apps, Tasks (finding #2 in prior)
- **Grok Build** — remains open-sourced at github.com/xai-org/grok-build under Apache 2.0 (finding #1 in prior)
- **VS Code 1.129 Agent Host Protocol** — Agent Host still GA, multi-harness unified execution architecture (finding #3 in prior)
- **Claude Code Dynamic Workflows GA + /checkup** — on all paid plans including Pro; /checkup still the active diagnostic skill (finding #4 in prior)
- **Agentjacking** — 2,388 organizations, 85% exploitation rate via fake Sentry reports (finding #5 in prior)
- **Sophos EDR collision** — legitimate agent behavior triggering Windows EDR rules; DPAPI 42.6% of credential-access events (finding #6 in prior)
- **Vercel skills.sh** — 600K+ open-source skills, OIDC auth (finding #7 in prior)
- **DeerFlow 2.0** (ByteDance) — 68K+ stars, super-agent harness (finding #8 in prior)
- **Gemini CLI → Agent Skills** — eager MCP deprecated; gemini-cli-skillz bridge (finding #9 in prior)
- **Anthropic 2026 Agentic Coding Trends Report** — $2.5B ARR; delegation gap (0–20% fully delegatable) (finding #10 in prior)
- **Zot** (Show HN, Go-native) — single binary coding agent (finding #11 in prior)
- **microsoft/skills** — 175+ Azure SDK skills, AGENTS.md standard (finding #12 in prior)
- **Zenn JP 17-layer taxonomy** + meta-harness canon (finding #13 in prior)
- **CN MCP+OpenClaw 10x claim** (Tencent Cloud, Hermes Agent ecosystem) (finding #14 in prior)
- **SKILL.md standard** at ~40 harnesses, ~1.9M community skills
- **OpenCode** (~186K stars, anomalyco), dominant open-source coding agent
- **Pricing crisis** — 60x cost gap ($0.07/task Cursor vs $4.10+ competitors)
- **ZeroClaw** (~32K stars), **nanobot** (~46K stars); OpenClaw Bazaar 2,300+ listings
- **aiAuthZ** — off-host, identity-bound authorization for AI agents (arxiv, July 2026)

---

## Cross-Source Patterns

### Pattern 1: IDE → Agent Command Center Pivot 🌐🇨🇳
Appearing on: devin.ai (global), byteiota, The Agent Report, aieii.com (🇨🇳), AI Navigate

The most significant architectural shift this window: **the IDE is becoming an agent manager**. Devin Desktop flips the IDE/agent relationship — the Kanban board of agent runs is the primary surface; code editing is secondary. Orca takes this further: it's not an IDE at all, just a fleet management environment for agents you run in whatever editor you prefer. The convergence point: as parallel agent workflows become the norm ("3–5 agents simultaneously" is now the community benchmark), the tool for managing that fleet is more valuable than the IDE wrapper. Cursor's parallel agents view and Kiro's Agent Hooks are smaller steps toward the same architectural endpoint.

CN framing (aieii.com): "IDE 正在变成 Agent 管理器" — "IDE is becoming an agent manager."

### Pattern 2: Open Protocol Race — ACP vs MCP as Complementary Layers 🌐
Appearing on: zed.dev, jetbrains.com, agentclientprotocol.com, blog.modelcontextprotocol.io, Devin Desktop launch

Two open protocols are now converging on the harness ecosystem: **MCP** (model-to-tool connectivity, July 28 final spec ships in 9 days) and **ACP** (editor-to-agent connectivity, built by Zed, adopted by JetBrains + Devin Desktop). These are complementary layers: ACP standardizes how editors talk to agents; MCP standardizes how agents talk to tools. Together they form a fully open stack: any editor → any agent → any tool. The USB-C metaphor that JP (note.com) and CN (Juejin) communities independently landed on for MCP applies equally to ACP.

### Pattern 3: Harness Security as a Recurring Three-Vector Problem 🌐
Appearing on: The Hacker News (global), prior Sophos and Agentjacking findings

Three distinct harness attack vectors have now emerged in consecutive briefings:
1. **Grok Build (prior):** Harness itself as data exfiltration agent
2. **Agentjacking (prior):** External injection via parsed text (fake Sentry reports) hijacking harness tool execution
3. **"Friendly fire" (this briefing):** Auditing-mode harness exploited via the legitimate code it's asked to review

Each vector exploits a different trust boundary: harness-to-network, harness-to-instruction, harness-to-code. The lack of a patch for "friendly fire" signals that harness security is a design-time problem, not a runtime patching problem — security review needs to happen at the harness permission model, not the vulnerability.

### Pattern 4: Quantification of Harness ROI Arriving 🌐🇯🇵
Appearing on: note.com/aiedgerunner (🇯🇵), qiita.com/cvusk (🇯🇵), Anthropic 2026 Trends Report (🌐), LangChain TerminalBench 2.0

The harness-vs-prompt debate has moved from qualitative to quantitative. Stanford HAI validation (12 production use cases): prompt optimization < 3% improvement; harness engineering 28–47%. LangChain TerminalBench 2.0: harness-only changes moved ranking from 30 → 5 without model changes. Spotify Honk: 3-tool harness, 1,500+ PRs merged. These data points, combined with Anthropic's 40% fewer errors / 55% faster task completion from well-maintained context files, are arriving simultaneously in the JP harness engineering canon. The field is developing evidence-based design principles.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| ejhooooon | Show HN: AMA2, messenger built for AI agent | 5 | 1 | "They don't care about an agent's context. To follow a thread, the agent has to pull the whole history every time." | https://news.ycombinator.com/item?id=48727140 |

**GitHub:**
| Repo | Stars | License | Description | URL |
|------|-------|---------|-------------|-----|
| stablyai/orca | 15,700 | MIT | ADE for parallel agent fleets; mobile companion; 30+ agents; v1.4.146 July 19 | https://github.com/stablyai/orca |
| wshobson/agents | 36,600 | — | Cross-harness plugin marketplace; 94 plugins, 203 agents, 175 skills, 109 commands | https://github.com/wshobson/agents |
| can1357/oh-my-pi | 17,600 | — | Terminal AI coding agent; hash-anchored edits, 32 tools, 14 LSP, 28 DAP ops, ~55K lines Rust | https://github.com/can1357/oh-my-pi |
| agentclientprotocol/agent-client-protocol | — | Apache 2.0 | ACP spec repo: any editor × any agent open standard | https://github.com/agentclientprotocol/agent-client-protocol |
| cursor/plugins | — | — | Cursor plugin specification and official plugins | https://github.com/cursor/plugins |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | stablyai/orca (GitHub) | https://github.com/stablyai/orca | ADE for parallel agent fleets; v1.4.146 TODAY |
| 🌐 | onorca.dev | https://www.onorca.dev/ | Orca product site: ADE for 100x builders |
| 🌐 | andrew.ooo review | https://andrew.ooo/posts/orca-stablyai-parallel-coding-agents-ide-review/ | Detailed Orca review: parallel worktrees, mobile companion |
| 🌐 | dev.to Orca review | https://dev.to/andrew-ooo/orca-review-the-ide-built-for-parallel-coding-agents-15df | Orca feature walkthrough |
| 🌐 | devin.ai blog | https://devin.ai/blog/windsurf-is-now-devin-desktop | Official Windsurf → Devin Desktop announcement |
| 🌐 | byteiota.com | https://byteiota.com/windsurf-is-now-devin-desktop-what-actually-changed/ | Devin Local: Rust rewrite, 30% token efficiency, ACP |
| 🌐 | webdeveloper.com | https://webdeveloper.com/news/windsurf-devin-desktop-cascade-eol/ | Cascade EOL July 1, Devin Local details |
| 🌐 | The Agent Report | https://the-agent-report.com/2026/06/cognition-devin-desktop-agent-orchestration/ | Agent Command Center architectural analysis |
| 🌐 | digitalapplied.com | https://www.digitalapplied.com/blog/windsurf-becomes-devin-desktop-ide-migration-2026/ | Migration guide: Cascade → Devin Local |
| 🌐 | zed.dev/acp | https://zed.dev/acp | ACP canonical spec page |
| 🌐 | agentclientprotocol.com | https://agentclientprotocol.com/get-started/introduction | ACP introduction |
| 🌐 | JetBrains ACP registry | https://blog.jetbrains.com/ai/2026/01/acp-agent-registry/ | ACP Agent Registry January 2026 launch |
| 🌐 | jetbrains.com/acp | https://www.jetbrains.com/acp/ | JetBrains ACP landing page |
| 🌐 | blog.marcnuri.com | https://blog.marcnuri.com/agent-client-protocol-acp-introduction | "LSP for AI coding agents" explainer |
| 🌐 | lucaberton.com | https://lucaberton.com/blog/agent-client-protocol-acp-standardizing-ai-coding-agents-2026/ | ACP adoption timeline |
| 🌐 | danilchenko.dev | https://www.danilchenko.dev/posts/agent-client-protocol/ | ACP technical walkthrough |
| 🌐 | releasebot.io/kiro | https://releasebot.io/updates/kiro | Kiro July 2026 release notes |
| 🌐 | kiro.dev/changelog | https://kiro.dev/changelog/ide/ | Kiro IDE changelog |
| 🌐 | developersdigest.tech/kiro | https://www.developersdigest.tech/blog/aws-kiro-developer-guide-2026 | Kiro V3 developer guide |
| 🌐 | thehackernews.com friendly-fire | https://thehackernews.com/2026/07/friendly-fire-ai-agents-built-to-catch.html | "Friendly fire" attack: security-audit agents compromised |
| 🌐 | github.com/can1357/oh-my-pi | https://github.com/can1357/oh-my-pi | oh-my-pi: hash-anchored edits, 17.6K stars |
| 🌐 | skillsllm.com/oh-my-pi | https://skillsllm.com/skill/oh-my-pi | oh-my-pi feature summary |
| 🌐 | github.com/wshobson/agents | https://github.com/wshobson/agents | 36.6K star cross-harness plugin marketplace |
| 🌐 | cursor.com/blog/marketplace | https://cursor.com/blog/marketplace | Cursor Marketplace launch |
| 🌐 | cursor.com/marketplace | https://cursor.com/marketplace | Cursor Marketplace browser |
| 🌐 | cursor.com/docs/plugins | https://cursor.com/docs/plugins | Cursor plugin documentation |
| 🌐 | adwaitx.com | https://www.adwaitx.com/cursor-marketplace-plugins/ | Cursor one-click plugin install analysis |
| 🌐 | engincanveske.substack.com | https://engincanveske.substack.com/p/i-tried-cursors-new-plugin-marketplace | First impressions of Cursor Marketplace |
| 🌐 | lushbinary.com | https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/ | Coding agents 2026 comparison |
| 🌐 | agentdepot.dev | https://agentdepot.dev/blog/cursor-windsurf-claude-code-whats-new-mid-2026 | Mid-2026 updates for major harnesses |
| 🌐 | dailyaiworld.com | https://dailyaiworld.com/blogs/orca-parallel-coding-agent-environment-2026 | Orca parallel agent environment overview |
| 🌐 | everydev.ai | https://www.everydev.ai/tools/orca-ide | Orca open-source parallel agent IDE |
| 🌐 | openllm.wavise.com | https://openllm.wavise.com/blog/orca-ade-parallel-agents | Orca ADE: run parallel agents with own subscription |
| 🌐 | aiagentstore.ai | https://aiagentstore.ai/ai-agent-news/this-week | AI Agents Week of July 16: AgentPrizm, other launches |
| 🌐 | github.com/ai-boost/awesome-harness-engineering | https://github.com/ai-boost/awesome-harness-engineering | Awesome list for AI agent harness engineering |
| 🇯🇵 | note.com/aiedgerunner | https://note.com/aiedgerunner/n/nbca11a6835f2 | Stanford HAI: prompt <3% vs harness 28-47% |
| 🇯🇵 | qiita.com/nogataka | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | Harness engineering intro: hooks (PreToolUse, PostToolUse, Stop) |
| 🇯🇵 | qiita.com/kai_kou | https://qiita.com/kai_kou/items/94b00143fc895ac0271e | Anthropic 3-agent multi-agent harness intro |
| 🇯🇵 | qiita.com/cvusk | https://qiita.com/cvusk/items/9c3e2738eede36eb206f | Fewer tools = better; Spotify Honk (3 tools, 1500+ PRs) |
| 🇯🇵 | qiita.com/agdexai (MCP intro) | https://qiita.com/agdexai/items/6ba0889696a3f7e4911f | MCP complete intro 2026 |
| 🇯🇵 | qiita.com/agdexai (MCP vs A2A) | https://qiita.com/agdexai/items/9f32b795c10b40c6bcd5 | MCP vs A2A full comparison |
| 🇯🇵 | qiita.com/yokoto | https://qiita.com/yokoto/items/e110fea5892c56946826 | AI/LLM timeline 2026.06 |
| 🇯🇵 | note.com/arukt | https://note.com/arukt/n/n97fb3ec1d851 | "AI's USB-C" — MCP as universal connector |
| 🇯🇵 | hexabase.com business | https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026 | 50-person → 10-person team via harness design |
| 🇯🇵 | hexabase.com guide | https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps | Harness engineering complete guide; 3 productivity elements |
| 🇯🇵 | ai-heartland.com | https://ai-heartland.com/ | JP hub: Claude Code, MCP, AI agents, OSS security in Japanese |
| 🇯🇵 | zenn.dev/renk | https://zenn.dev/renk/scraps/a6fb7cebdea333 | Agent harness research scraps thread |
| 🇨🇳 | news.qq.com Devin | https://news.qq.com/rain/a/20260603A038ZC00 | CN mainstream: Windsurf → Devin Desktop, Rust agent |
| 🇨🇳 | aieii.com | https://aieii.com/posts/2026-06-13-windsurf-devin-desktop-acp/ | "IDE is becoming an agent manager"; ACP coverage |
| 🇨🇳 | CSDN developer stat | https://blog.csdn.net/df2209/article/details/162903819 | 75M monthly AI coding tool users, 300%+ growth |
| 🇨🇳 | CSDN MCP guide | https://blog.csdn.net/ziwoods/article/details/161662819 | MCP protocol complete guide for AI agent development |
| 🇨🇳 | Juejin AI Agent practice | https://juejin.cn/post/7651426279837171764 | Microsoft full MCP embrace at BUILD 2026 |
| 🇨🇳 | Juejin MCP roadmap | https://juejin.cn/post/7616246892184027155 | MCP as "AI USB-C port" — 3 capabilities |
| 🇨🇳 | Tencent Cloud MCP+OpenClaw | https://cloud.tencent.com/developer/article/2696664 | MCP+OpenClaw 10x efficiency claim |
| 🇨🇳 | Tencent Cloud conversation→action | https://cloud.tencent.com/developer/article/2701441 | AI Agent engineering implementation 2026 |
| 🇨🇳 | Tencent Cloud MCP guide | https://developer.cloud.tencent.com/article/2703450 | MCP practical guide for AI agent interconnection |
| 🇨🇳 | AWS China MCP GA | https://aws.amazon.com/cn/about-aws/whats-new/2026/05/aws-mcp-server/ | AWS MCP Server GA in China region |
| 🇨🇳 | cnblogs.com comparison | https://www.cnblogs.com/deali/p/19864809 | AI tools comparison 2026; McKinsey: 46% time savings |
| 🇨🇳 | liuqi.dev MCP | https://liuqi.dev/blog/mcp-2026-stateless-revolution | MCP 2026 stateless revolution + OAuth 2.1 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ HTTP 403 block (ongoing gap)
├─ 🔵 X: 0 posts │ Not scanned this pass
├─ 🔴 YouTube: 0 videos │ Not scanned this pass
├─ 🟢 HN: 1 story │ 5 points │ 1 comment │ July 18-19 front page HTTP 429
├─ 🟣 TikTok: 0 videos │ No ScrapeCreators key
├─ 🩷 Instagram: 0 reels │ No ScrapeCreators key
├─ 🦋 Bluesky: 0 posts │ bluesky=OK (no new high-engagement posts this window)
├─ 📊 Polymarket: 0 markets │ No harness prediction markets
├─ 🐙 GitHub: 5 repos │ stablyai/orca (15.7K★), wshobson/agents (36.6K★), can1357/oh-my-pi (17.6K★), agentclientprotocol/acp, cursor/plugins
├─ 🌐 Web: 38 pages │ 🇯🇵 12 │ 🇨🇳 11
└─ 🗣️ Top voices: can1357 (oh-my-pi creator), @nogataka (Qiita hooks intro), こうへい/aiedgerunner (Stanford HAI quant data) │ stablyai (Orca ADE)
```

---

## Out of Scope but Notable

- **AgentPrizm — AgentMemory + AgentSkills REST + MCP Platform** (launched July 9, 2026): Pairs a REST API with MCP infrastructure for persistent agent memory across sessions. Could belong in agent-infrastructure or ai-software-factory rather than harness; flagging in case it signals a new "memory-as-a-service" subcategory. [aiagentstore.ai](https://aiagentstore.ai/ai-agent-news/this-week)

- **Meta Muse Spark 1.1 — OS-Level Computer Control Agent**: Meta claims Muse Spark 1.1 can operate a computer autonomously (web searches, forms, app switching). If accurate, it's a general-purpose autonomous agent that competes with the harness category from the OS layer rather than the IDE layer — a different attack vector on the space. [aiagentstore.ai](https://aiagentstore.ai/ai-agent-news/this-week)

- **ACP Registry** (January 2026): The JetBrains-hosted registry for ACP-compatible agents is an agent discovery mechanism that may displace MCP-based discovery for coding contexts. Worth watching for convergence or bifurcation with MCP.directory-style registries.

---

## Data Gaps

- **Reddit: HTTP 403** (persistent API block for this domain) — r/AI_Agents, r/ClaudeAI, r/LocalLLaMA discussions unavailable; this remains a material gap as community signal originates there
- **Hacker News July 18-19 front page: HTTP 429** — rate-limited; could not verify if any new harness stories made the front page in the last 48 hours specifically
- **YouTube: 0 results** — tutorial content on Orca, Devin Desktop, oh-my-pi almost certainly exists but not retrieved
- **Bluesky: No new posts** — bluesky=OK per SOURCE HEALTH; topic had low Bluesky engagement this window
- **ScrapeCreators not configured**: TikTok (0), Instagram (0) excluded
- **Polymarket: 0 markets** — no prediction markets on harness topics
- **Zhihu: HTTP 403** — key CN community for tool selection discussions; only snippets available via DDG; material CN gap
- **Juejin dynamic content**: Some pages returned JavaScript-only loading screen ("Please wait..."); content extracted via search snippets
- **wshobson/agents**: Star count from a June 2026 citation (36.6K); current count may differ
- **oh-my-pi**: Star count from skillsllm.com aggregate; not directly fetched from GitHub
- **Orca star discrepancy**: Two sources give different counts (15,700 vs 22,000); likely reflects rapid growth; both cited for transparency
- **last30days skill unavailable**: Conducted equivalent research manually; may have missed Reddit/YouTube/TikTok/Instagram sources that the skill would have reached
- **Coverage estimate: ~68%** — strong on web/GitHub/JP/CN; gaps from Reddit block, YouTube/TikTok/Instagram zero coverage, HN rate-limiting on July 18-19 front pages, several blocked CN pages

---

## Key Quotes

> "In 2026, most '10x developers' are running three to five coding agents at once... spin off a worktree, send Claude Code at it; spin off another, send Codex; spin off a third, send Cursor; compare three diffs, cherry-pick the best." — [Orca review, andrew.ooo](https://andrew.ooo/posts/orca-stablyai-parallel-coding-agents-ide-review/) 🌐

> "新たな定量データ（プロンプト改善3%未満 vs ハーネス改善28-47%）" ("New quantitative data: prompt improvement <3% vs harness improvement 28-47%") — @aiedgerunner on [note.com](https://note.com/aiedgerunner/n/nbca11a6835f2) 🇯🇵

> "ツールは少ないほど良い" ("Fewer tools perform better") — @cvusk on [Qiita](https://qiita.com/cvusk/items/9c3e2738eede36eb206f), citing Spotify Honk (3 tools, 1,500+ PRs) 🇯🇵

> "IDE 正在变成 Agent 管理器" ("IDE is becoming an agent manager") — [aieii.com](https://aieii.com/posts/2026-06-13-windsurf-devin-desktop-acp/) 🇨🇳

> "The weakness stems from architectural design rather than implementation flaws" — [The Hacker News](https://thehackernews.com/2026/07/friendly-fire-ai-agents-built-to-catch.html) on "Friendly fire" agent attack 🌐

> "Agent Client Protocol (ACP) is the LSP for AI coding agents: one open standard so any agent runs in any editor." — [blog.marcnuri.com](https://blog.marcnuri.com/agent-client-protocol-acp-introduction) 🌐

> "Windsurf 谢幕，Devin Desktop 登场：IDE 正在变成 Agent 管理器" ("Windsurf exits, Devin Desktop enters: IDE is becoming an agent manager") — [aieii.com](https://aieii.com/posts/2026-06-13-windsurf-devin-desktop-acp/) 🇨🇳

> "全球每月至少使用一次AI编程工具的开发者已超过7500万，比2024年增长超300%" ("Developers globally using AI coding tools at least once/month exceeds 75 million, 300%+ growth since 2024") — [CSDN](https://blog.csdn.net/df2209/article/details/162903819) 🇨🇳

> "Microsoft在2026年Build大会上宣布全面拥抱MCP协议" ("Microsoft announced full embrace of MCP protocol at the 2026 Build conference") — [Juejin](https://juejin.cn/post/7651426279837171764) 🇨🇳

> "MCPは、AIを『あなたの会社のGoogle DriveやSlackと直接つなぐ共通規格』として現実のものになっています" ("MCP is now a real standard for connecting AI directly to your company's Google Drive, Slack, etc.") — @arukt on [note.com](https://note.com/arukt/n/n97fb3ec1d851) 🇯🇵
