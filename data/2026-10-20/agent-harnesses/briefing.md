# AI Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-10-20
**Query type:** GENERAL
**Sources:** Reddit (partial), X/Twitter, Hacker News, Bluesky, GitHub, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 14 threads | 7,913 upvotes, 1,326 comments | ⚠ partial after 14 items (HTTP 403) |
| X/Twitter | 15 posts | 98 likes, 23 reposts | 🌐 |
| Hacker News | 24 stories | 623 points, 438 comments | 🌐 |
| Bluesky | 12 posts | 13 likes, 1 repost | 🌐 |
| GitHub | 13 items | 15 reactions, 103 comments | 🌐 |
| Web (global) | 48 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 12 pages | — | 🇯🇵 Zenn, Qiita, note.com, Hatena |
| Web (China) | 14 pages | — | 🇨🇳 Zhihu (403 blocked), CSDN, AI Agent Radar, trendshift |

---

## Synthesized Findings

### 1. [new] Google Harness² — recursive harness self-improvement without touching model weights

**Claim:** Google Research + Northwestern University released Harness² (arXiv Oct 9, 2026; Apache 2.0) — a framework that recursively optimizes an agent's 8-file harness (system prompt, guardrails, memory, skills, tool guidance, scripts, subagents, middleware) while leaving model weights frozen.
**Evidence:**
- **Mechanism:** "Propose–Probe–Compose" cycle: generate harness edits → probe on tasks → compose successful changes using execution deltas rather than ground-truth labels. Cross-task lessons captured in a library.
- **Benchmarks:** +11.5 pts WorkBuddy-Bench, +4.5 pts JobBench, +11.8 pts Harvey Legal Benchmark (partial pass rate).
- **Caveats:** arXiv v1 (unreviewed); documents 9 regressions; assumes unrestricted network access and disabled sandboxing.
- **JP signal:** Qiita article within days of release; Harness² framed as "AIエージェントが仕事の仕組みを育てる" (AI agents cultivating their own work systems). [https://qiita.com/sin-aiagent/items/54ee8f8d95009f9cbb03]
- **Sources:** [rits.shanghai.nyu.edu](https://rits.shanghai.nyu.edu/ai/google-open-sources-harness2-for-self-improving-ai-agents/), [startupfortune.com](https://startupfortune.com/google-open-sources-harness2-letting-ai-agents-rewrite-their-own-playbook/), [github.com/google-research/harness2](https://github.com/google-research/harness2), [ntorres.dev](https://ntorres.dev/blog/harness2-google-recursive-agent-harness), [techjacksolutions.com](https://techjacksolutions.com/ai-brief/google-research-open-sources-harness-recursive-agent/)

---

### 2. [new] Reason Network — P2P cross-machine cross-harness agent coordination

**Claim:** Reason Machines released Reason Network (Oct 16, 2026; free, open-source Rust engine) — P2P layer enabling agents on separate machines to see each other's status and exchange tasks in real time.
**Evidence:**
- **Scope:** Claude Code, Codex, Cursor, Gemini CLI, Copilot CLI, Grok CLI, opencode, Pi, DeepSeek Harness, Reason — all appear in the same workspace dashboard.
- **Capability:** Any agent can message any other agent on any machine (MacBook, Mac Studio, Mac mini). Shows who, which repo/branch, busy/idle, what it's doing.
- **Architecture:** Rust execution engine, MCP-based coordination protocol.
- **JP uptake:** note.com hands-on review published Oct 18, within 48 hours of release. "複数のPCを単一のワークスペースに配置し、任意のPCの任意のエージェントにメッセージを送信できます" ("You can place multiple PCs in a single workspace and send messages to any agent on any PC"). [https://note.com/masa_wunder/n/n36fbdb8460c5]
- **Sources:** [reasonmachines.com/network](https://reasonmachines.com/network), [github.com/reason-machines/reason-network](https://github.com/reason-machines/reason-network), [eyerys.com](https://www.eyerys.com/articles/news/how-reason-machines-uses-reason-network-enable-peer-peer-agent-coordination-software)

---

### 3. [new] Reticle — runtime perception layer for agent self-verification

**Claim:** Reticle (Show HN Oct 20, 11pts/6cmt; reticlehq/reticle) gives coding agents machine-native runtime perception of web/desktop apps — agents drive real running flows and read what actually happened before declaring work done.
**Evidence:**
- **Mechanism:** Dev-only SDK inside running app. Agent reads network calls, store, console, routes, DOM. Returns pass/fail/couldn't-tell with file:line to fix.
- **DX:** No test syntax; plain-English assertions ("what should be true").
- Frames verification as the missing layer: "AI agents can generate code, but still struggle to understand what they build."
- **Sources:** [github.com/reticlehq/reticle](https://github.com/reticlehq/reticle), [promptzone.com](https://www.promptzone.com/quinn_kovac/reticle-ai-agents-that-verify-their-own-code-4d50), HN: [news.ycombinator.com](https://news.ycombinator.com/item?id=49978401)

---

### 4. [new] Hy Memory 2.0 (Tencent Hunyuan) — first CN-native dual-system agent memory

**Claim:** Tencent Hunyuan released Hy Memory 2.0 (Oct 15-17, Apache 2.0, 590+ stars Oct 18) — first framework to explicitly separate working memory from code memory, plus Hy-Memory-30B-A3B open-weight memory writer model.
**Evidence:**
- **Separation:** Chat memory + working memory + coding memory as distinct pipelines, not a single chat log.
- **Model:** Hy-Memory-30B-A3B (30B params, 3B active); performs memory write step — reads conversation/coding trace, decides what goes in persistent store. Benchmark: 55.49% vs Claude Opus 3's 54.62%.
- **MemHub:** Desktop app syncs agent history across 10 tools (Claude Code, Cursor, Codex, OpenCode included).
- **CN coverage:** Widely covered as "业界首个明确区分 working memory 和 code memory 的框架" (first in industry to explicitly separate working and code memory). [https://kucoin.com/news/flash/tencent-hunyuan-launches-open-source-hy-memory-2-0-framework]
- **Sources:** [github.com/Tencent-Hunyuan/Hy-Memory](https://github.com/Tencent-Hunyuan/Hy-Memory), [letsdatascience.com](https://letsdatascience.com/news/tencent-open-sources-hy-memory-20-stack-f1fcc6c1), [ibl.ai](https://ibl.ai/blog/tencent-hy-memory-30b-open-weight-memory-policy), [trendshift.io](https://trendshift.io/repositories/307744)

---

### 5. [new] OpenCode Console breach — API key credential theft + distillation attacks

**Claim:** Oct 16-17: attacker breached OpenCode's legacy Console system, exposing OpenAI, Anthropic, and Google API keys for ~1.4% of Console users; keys immediately used for distillation attacks.
**Evidence:**
- **Impact:** Some users hit with $1,700+ unauthorized charges overnight. Keys used for large-scale automated queries (distillation attack).
- **Scope:** Keys stored in Console's optional hosted workspace feature (team API key sharing).
- **Response:** OpenCode, Anthropic, OpenAI, Google collaborated on key revocation. OpenCode v1.19.1 discontinued session sharing.
- Bluesky security digest from @willvelida.com (Oct 20) also lists: CERT-In advisory on rogue agents, Langflow MCP CVE-2026-105740 (CVSS 9.9) exploited. [https://bsky.app/profile/willvelida.com/post/3mycaqnyqas2x]
- **Sources:** [thehackernews.com](https://thehackernews.com/2026/10/opencode-console-breach-may-have.html), [bleepingcomputer.com](https://www.bleepingcomputer.com/news/security/opencode-hack-exposes-api-keys-amid-ai-distillation-attacks/), [rescana.com](https://www.rescana.com/post/opencode-console-breach-exposes-openai-anthropic-and-google-api-keys-in-credential-theft-and-distillation-attack-october), [shattered.io](https://shattered.io/opencode-console-breach-api-keys-2026/)

---

### 6. [new] Aoki infostealer expands to target coding agent credential files

**Claim:** New Aoki infostealer variant (Symantec report, Oct 2026) specifically targets config/credential files of coding agent harnesses: .claude.json, Claude desktop cookies, Codex config.toml/.env, GitHub Copilot tokens, Cursor, Gemini, JetBrains AI, Kiro, AWS credentials.
**Evidence:**
- Targets the entire credential surface of the agent ecosystem in one sweep.
- Parallel to OpenCode breach: attacker ran 51 Claude Code agents against stolen API keys (dev.to report).
- Langflow CVE-2026-105740 (CVSS 9.9): authenticated non-admin can register MCP server with stdio transport, command executes in shell without validation. Versions before 1.9.0 affected.
- **Sources:** [gbhackers.com](https://gbhackers.com/aoki-infostealer-targets-ai/), [scworld.com](https://www.scworld.com/brief/new-infostealer-targets-ai-coding-assistant-credentials/), [dev.to/humanbound_ai](https://dev.to/humanbound_ai/an-attacker-ran-51-claude-code-agents-langflow-is-being-probed-and-headers-now-carry-prompt-1jp7), [dev.to/gabrielanhaia](https://dev.to/gabrielanhaia/an-infostealer-now-grabs-claudejson-and-codexs-configtoml-check-what-yours-hold-196n), [cyberpress.org](https://cyberpress.org/aoki-targets-ai-credentials/)

---

### 7. [update] Claude Code v2.1.302 + Claude Design EOL Dec 14

**Claim:** CC v2.1.302 (Oct 16) changes two claude -p defaults: fork subagents now on by default; permission mode changes. Standalone Claude Design closes December 14, 2026.
**Evidence:**
- Fork subagents default + permission mode changes affect headless -p usage.
- Claude Design closure: /design-sync and /design-login warn; chats/comments deleted after Dec 14; public links cease.
- CLAUDE_CODE_AUTO_MODE_MODEL added for client-side auto mode classifier.
- Idle compaction row added to /config.
- **Sources:** [dev.classmethod.jp](https://dev.classmethod.jp/en/articles/20261017-cc-updates-v2-1-302/), [dev.to/gabrielanhaia](https://dev.to/gabrielanhaia/claude-code-21302-flips-two-claude-p-defaults-permission-mode-and-fork-subagents-2k48), [gradually.ai](https://www.gradually.ai/en/changelogs/claude-code/)

---

### 8. [update] Hermes v0.22.0 "Threshold" + v0.22.1 patch

**Claim:** Hermes v0.22.0 (Oct 11) + v0.22.1 (Oct 14): native Hermes Desktop (Electron, macOS/Linux/Windows); guided local model setup (llama.cpp auto-managed); 4 new inference providers.
**Evidence:**
- New first-launch setup chat: name, accent color, layout preference, app connections, plugin install, tour.
- Local model support: engine installs/maintains llama.cpp, rates models against GPU/RAM, picks optimal build.
- New providers: GMI Cloud, Azure AI Foundry, MiniMax OAuth, Tencent Tokenhub. LM Studio to first-class.
- **Sources:** [gradually.ai/changelogs/hermes-agent](https://www.gradually.ai/en/changelogs/hermes-agent/), [releasebot.io/updates/nousresearch/hermes-agent](https://releasebot.io/updates/nousresearch/hermes-agent)

---

### 9. [update] OpenClaw October releases — Gemini 4 Argon default, Gateway stability

**Claim:** OpenClaw Oct 2026 releases: Gemini 4 Argon becomes default Gemini model; Gateway SQLite stability fixes (SIGBUS crash loop prevention); interrupted turns preserved across restarts.
**Evidence:**
- SQLite WAL SIGBUS crash loop (live file + hard-linked file overlap) fixed.
- Interrupted turns (ACP follow-up replies) preserved when new messages arrive.
- Nemotron 3.5 Super VL and xAI Imagine Image 2.0 added. Retired models removed from pickers.
- **Sources:** [gradually.ai/changelogs/openclaw](https://www.gradually.ai/en/changelogs/openclaw/), [docs.openclaw.ai/releases/2026.10.1](https://docs.openclaw.ai/releases/2026.10.1)

---

### 10. [new] Dexto (truffle-ai) — YAML-defined agent harness with MCP-first design

**Claim:** Dexto (truffle-ai/dexto) is a general-purpose agent harness where agents are defined in version-controlled YAML; CLI + SDKs; built-in orchestration for state, tools, sessions, error recovery.
**Evidence:**
- "Building an agent shouldn't mean rebuilding its runtime from scratch" — @DanKornas on X (12 likes, Oct 20). [https://x.com/DanKornas/status/2112340267671904464]
- Oct 2026 PRs: JSON/JSONL output (PR #946), packaged agent runtime (PR #956), standalone MCP setup (PR #964), MCP SDK v1 compatibility (PR #966).
- YAML-defined agents; changes reload automatically. Model/tool swap without code changes.
- **Sources:** [github.com/truffle-ai/dexto](https://github.com/truffle-ai/dexto), [x.com/DanKornas](https://x.com/DanKornas/status/2112340267671904464)

---

### 11. [update] AIDLC-workflows v2.11.0/2.11.1 — cross-harness adaptive workflow steering

**Claim:** AWS Labs aidlc-workflows v2.11.1 (Oct 20): 33-stage AI-DLC workflow model now runs in Claude Code, Kiro, Codex CLI, Cursor, opencode, and GitHub Copilot from the same codebase.
**Evidence:**
- HN 28pts/22cmt (Oct 15) for "Aidlc: Adaptive workflow steering rules for AI coding agents." [https://github.com/awslabs/aidlc-workflows]
- 5,300+ stars. Native aidlc CLI. Releases almost daily. Enterprise workflow routing and governance policies.
- Described as "harness-neutral core" for SDLC workflow automation.
- **Sources:** [getreadyforagents.com](https://www.getreadyforagents.com/news/aws-labs-aidlc-workflow-steering/), [aitoolly.com](https://aitoolly.com/ai-news/article/2026-05-10-aws-labs-introduces-ai-dlc-new-adaptive-workflow-guidance-rules-for-ai-programming-agents), [orchestrator.dev](https://orchestrator.dev/blog/2026-10-03-ai-dlc-in-practice/), [ngjoo.com](https://www.ngjoo.com/en/trending/projects/aidlc-workflows/)

---

### 12. [new] Skills Hub v1.0.0 — desktop app for cross-harness skill management

**Claim:** Skills Hub v1.0.0 (Oct 11, 2026) is a cross-platform desktop app: "Install once, sync everywhere" for SKILL.md files across 48 coding tools.
**Evidence:**
- Supports Claude Code, Codex, Cursor, OpenCode, Antigravity + 43 more tools.
- Features: collection discovery, website installation, batch updates, global/project scope, scheduled Git/local-source sync.
- Multiple GitHub repos (qufei1993/skills-hub, agentskills-vn/skills-hub, skillhub-club/skillhub-desktop) show fragmented but active ecosystem.
- **Sources:** [skills-hub.dev](https://skills-hub.dev/), [github.com/qufei1993/skills-hub](https://github.com/qufei1993/skills-hub), [github.com/agentskills-vn/skills-hub](https://github.com/agentskills-vn/skills-hub)

---

### 13. [update] Omnigent (Databricks) v0.18.0 — meta-harness GA momentum

**Claim:** Omnigent (omnigent-ai/omnigent) v0.18.0 (Oct 13): 10,817 stars/1,753 forks; YAML agent definitions portable across Claude Code, Codex, Cursor, Pi; stateful policies intercept tool calls at server/agent/session levels.
**Evidence:**
- Apache 2.0, created Jun 2026. 40+ releases since. Active daily.
- HighTalk Bluesky post (Oct 18) frames cross-harness governance as unsolved: "which permissions, records and review boundaries carry over?" and points to Omnigent. [https://bsky.app/profile/hightalk-me.bsky.social/post/3my6nksqfvv27]
- Credential proxying: agent never sees raw API token.
- **Sources:** [medium.com/@kanerika](https://medium.com/@kanerika/databricks-omnigent-the-meta-harness-for-enterprise-ai-agent-governance-812cddbd1587), [github.com/omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent), [marktechpost.com](https://www.marktechpost.com/2026/06/13/databricks-open-sources-omnigent-a-meta-harness-that-composes-governs-and-shares-ai-agents-across-claude-code-codex-and-pi/)

---

### 14. [new] Reason Agent 1.1 — harness-first coding agent beating Codex

**Claim:** Reason Agent 1.1 (Reason Machines): Coding Agent Index 65.1 vs Codex CLI 62.5 on GPT-6 Astra; 23% fewer input tokens; 15% fewer output tokens; 15-22% lower cost. Proof that harness design matters more than model.
**Evidence:**
- "It's not the AI. It's the harness. Think of it like this: The AI model is the smart worker. The harness is the manager that hands it the right files." — @JulianGoldieSEO on X. [https://x.com/JulianGoldieSEO/status/2112476953852985746]
- Compared on same GPT-6 Astra model — isolates harness contribution.
- **Sources:** [reasonmachines.com/blog](https://reasonmachines.com/blog/introducing-reason-agent-1-1), [morphllm.com](https://www.morphllm.com/ai-coding-agent)

---

### 15. [update] Extension economy: cursor/plugins (11.8k), anthropics/claude-plugins-official (39k), Tons of Skills MCP (2,900+)

**Claim:** Three new ecosystem signals: cursor/plugins (11,804 stars) with 75 official plugins; anthropics/claude-plugins-official (39k stars) formalizing Anthropic's extension ecosystem; Tons of Skills MCP aggregating 2,900+ skills and 434 plugins.
**Evidence:**
- cursor/plugins: MCP server interfaces for enterprise stacks (CRM, finance, productivity, marketing, dev platforms). [https://github.com/cursor/plugins]
- anthropics/claude-plugins-official: "launch signals that the Claude Code extension ecosystem is being formalized, making plugin discovery and packaging a first-class developer surface." [https://github.com/anthropics/claude-plugins-official — note: URL inferred from search descriptions]
- Tons of Skills MCP (mcpworld.com): 2,900+ skills, 434 plugins. [https://www.mcpworld.com/en/detail/83ae279b9103c1b8c60c2cc447d3729c]
- Alongside prior: agentskill.sh 200k+ skills, Claude marketplace 4,554+ skills, vercel-labs/skills CLI.
- **Sources:** [coddykit.com Oct trends](https://www.coddykit.com/pages/blog-detail?id=5129988), [skillgild.dev](https://skillgild.dev/learn/best-ai-agent-skill-marketplaces), [skills-hub.dev](https://skills-hub.dev/)

---

### 16. [update] LeanREA — 8KB skill replaces 207-tool MCP server

**Claim:** LeanREA (aicodeking/leanrea, Oct 17, 460+ stars): single 8KB skill file replaces morluto/REA's 207-tool MCP server; reports 38% less wall time, 35% lower cost, 56% fewer turns, 60% fewer tokens.
**Evidence:**
- REA 6.6.0 (Oct 18) adds Kuna static analysis, extends Ghidra to Windows ARM PE and m68k. LeanREA is the lean-path alternative.
- Demonstrates skill-vs-MCP tradeoff debate: skill file can beat large MCP server on efficiency when task domain is constrained.
- **Sources:** [github.com/aicodeking/leanrea](https://github.com/aicodeking/leanrea), [munderdiffl.in Oct 18](https://munderdiffl.in/blog/agent-tools-today-2026-10-18/)

---

### 17. [update] AI coding agent productivity research: "more code, but not more software"

**Claim:** Ars Technica / HN study (Oct 12, 364pts/313cmt): AI coding agents generate more code but productivity gains are "absorbed" by human review bottleneck.
**Evidence:**
- Anthropic internal report (r/ClaudeAI, Oct 20): "80% of elapsed time in Claude sessions is agents waiting for human input." Median employee spends 20% more time in meetings. Employees 1+ year are 50% more likely to switch tasks while agent runs.
- Memory usage study (oyren.ai): 6 harnesses measured across 33 Linux sessions; idle CLI harnesses only ~200-300 MB. [https://oyren.ai/blog/ai-coding-agent-memory-usage]
- @reksas13.bsky.social (Oct 14): "11 coding-agent harnesses, ~4M lines of source: none imports an agent framework, none retrieves code with embeddings. They grep." [https://bsky.app/profile/reksas13.bsky.social/post/3mxsq32fqo62i]
- **Sources:** [arstechnica.com](https://arstechnica.com/ai/2026/10/ai-coding-agents-generate-more-code-but-not-more-software/), [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1xag7e5/anthropics_internal_report_80_of_claude_session/)

---

**Still true** (ongoing threads, no new facts this cycle):
- `hermes-agent-self-improving` — v0.22.0 patch v0.22.1 (Oct 14) minor; no major capability shift
- `openclaw-gateway-harness` — Gemini 4 Argon default + SQLite fix (covered in §9)
- `vscode-1138-agent-host-protocol` — no new VS Code release this window
- `github-copilot-skills-mcp-ga` — dynamic workflows (Oct 1) + v1.0.98 Gemini 4 Argon support; covered in raw
- `codex-cli-0155-voice-touchid` — no new Codex CLI release this window
- `devin-desktop-windsurf-rebrand` — no new Devin releases found
- `skills-security-prompt-injection-36pct` — Aoki infostealer (§6) + Langflow CVE (§5) extend this
- `deepseek-harness-team` — active in CN ecosystem (CSDN guides); no new version
- `extension-economy-explosion` — updated: cursor/plugins 11.8k, claude-plugins-official 39k, Tons of Skills 2,900+ (§15)
- `sep-2640-mcp-skills-final` — Skills Hub v1.0.0 as discovery layer; no new SEP-2640 spec events
- `vercel-labs-skills-universal-cli` — ongoing; no new release
- `claude-code-doctor-skill-hygiene` — v2.1.302 covered in §7
- `anthropic-managed-agents-mcp-tunnels` — v2.1.302 covered in §7
- `harness-context-tax-problem` — LeanREA 60% token reduction (§16) adds new data point
- `mcp-security-nsa-supply-chain` — Aoki + Langflow CVE (§6) + OpenCode breach (§5) extend
- `gitspawn-class-vulnerability` — no new patches reported
- `harness-engineering-paradigm` (JP) — Zenn/Qiita active with harness-first articles
- `environment-architect-new-role` (JP) — note.com, Qiita coverage active
- `self-harness-auto-optimization` — Harness² (§1) is the major update; ahe-automated-harness-evolution updated
- `harmony-harness-google-cmu` — Harness² (§1) is a separate but related Google Research release
- `obra-superpowers-skills` — 300,249 stars (trending Oct 2026)
- `layered-oss-stack-over-single-framework` — Omnigent v0.18.0 (§13) + Hy Memory (§4) extend stack
- `workday-agent-harness-ga` — no new developments
- `harness-io-acquires-cosmos` — no new developments
- All other ongoing threads (corbenic, morluto/REA, cmux, OpenHuman, nanoMuse, etc.) — no new data this window

---

## Cross-Source Patterns

### Pattern 1: Harness-as-product moment — new harnesses launching weekly
- **Signal:** Dexto, Reason Network, Reason Agent 1.1, Reticle, Skills Hub, LeanREA, Sphinx all launched or reached notable milestones in the last 5 days.
- **Platforms:** HN, X, Bluesky, Web, munderdiffl.in daily digest
- **Quote:** "Building an agent shouldn't mean rebuilding its runtime from scratch." — @DanKornas, X ([link](https://x.com/DanKornas/status/2112340267671904464))
- **Quote:** "It's not the AI. It's the harness." — @JulianGoldieSEO, X ([link](https://x.com/JulianGoldieSEO/status/2112476953852985746))

### Pattern 2: Credential theft converging on harness ecosystem surface
- **Signal:** OpenCode Console breach (Oct 16-17) + Aoki infostealer (targets harness config files) + Langflow MCP CVE (CVSS 9.9) + CERT-In rogue agents advisory — all within one week.
- **Platforms:** Bluesky security digest, thehackernews.com, bleepingcomputer.com, dev.to, gbhackers.com, scworld.com
- **Quote:** "Last week in Agent Security! CERT-In issues advisory of rouge agents at play, Langflow MCP exploited, Aoki infostealer targeting AI coding agent credentials, and OpenCode Console breach exposes LLM API keys" — @willvelida.com, Bluesky ([link](https://bsky.app/profile/willvelida.com/post/3mycaqnyqas2x))

### Pattern 3: Human-in-the-loop is the bottleneck, not the harness
- **Signal:** HN study (364pts) shows gains absorbed by review; Anthropic internal report shows 80% wait time; @reksas13.bsky.social finds harnesses grep instead of embed.
- **Platforms:** HN, Reddit/ClaudeAI, Bluesky, arstechnica.com
- **Quote:** "Getting the new team to understand why and how the AI is set up the way it is, is challenging. There is very little standardisation in the way that AI is used." — @pdj.bsky.social ([link](https://bsky.app/profile/pdj.bsky.social/post/3mxyw7fsx722b))

### Pattern 4: JP/CN: harness engineering as discipline
- **Signal:** "2025: year of agents, 2026: year of harnesses" — JP community meme. CN: 12-module harness deep-dives. Both tracking Harness² and Reason Network within days of release.
- **Platforms:** Zenn, Qiita, note.com, Zhihu, CSDN
- **JP quote:** "2025年はエージェントの年、2026年はハーネスの年" (2025 was the year of agents, 2026 is the year of harnesses) — Qiita/Zenn consensus

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @DanKornas | "Building an agent shouldn't mean rebuilding its runtime from scratch. Dexto is an agent harness for builders..." | 12 | 2 | [link](https://x.com/DanKornas/status/2112340267671904464) |
| @thisdudelikesAI | "Claude Code finally has a SERIOUS competitor. It's called OpenCode..." | 31 | 11 | [link](https://x.com/thisdudelikesAI/status/2112479647468572950) |
| @JulianGoldieSEO | "Reason Agent 1.1 is a free coding agent that beat Codex... It's not the AI. It's the harness." | 2 | 0 | [link](https://x.com/JulianGoldieSEO/status/2112476953852985746) |
| @thomaswight | "5 free GitHub repos I'm saving for my AI agents: OpenCode, Superpowers, anthropics/skills, Langfuse, Learn Harness Engineering" | 8 | 0 | [link](https://x.com/thomaswight/status/2112280309798674876) |
| @s16a__ | "We keep confusing foundation models, LLMs, AI agents and agent harnesses as if they are interchangeable. They are not." | 4 | 0 | [link](https://x.com/s16a__/status/2112291688999956963) |
| @regunivers | "Introducing reuF2F: 244 open math problems... a minimal coding agent for Lean, so every model is compared under the same harness." | 20 | 8 | [link](https://x.com/regunivers/status/2112345448925073682) |
| @velusgautam | "Think of it as a safety harness for Claude, Cursor, Codex, Gemini CLI, and Hermes. Agentic Leash." | 0 | 1 | [link](https://x.com/velusgautam/status/2112551401629126754) |
| @smratitiwa86867 | "What if your AI coding agent didn't forget everything when you closed the terminal?... Meet Prime Agent" | 0 | 2 | [link](https://x.com/smratitiwa86867/status/2112411304162160968) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | AI coding agents generate more code, but not more software | 364 | 313 | "gains absorbed by human review bottleneck" | [link](https://news.ycombinator.com/item?id=arstechnica) |
| — | Aidlc: Adaptive workflow steering rules for AI coding agents | 28 | 22 | cross-harness 33-stage workflow | [link](https://github.com/awslabs/aidlc-workflows) |
| — | Show HN: Make AI coding agents verify its own work | 11 | 6 | Reticle; runtime perception | [link](https://github.com/reticlehq/reticle) |
| — | Show HN: Weatherdeck – read-only status board for AI coding agent lanes | 9 | — | multi-agent lane monitoring | [link](https://github.com/Moshik21/weatherdeck) |
| — | Best-of-Agent-Harnesses – Ranked list of 167 AI agent harnesses | 7 | — | 167 harnesses tracked | [link](https://github.com/ryanalberts/best-of-agent-harnesses) |
| — | Robium – Physical AI harness for coding agents | 5 | — | physical agent harness | [link](https://github.com/robium-ai/robium) |
| — | Unofficial Android app for Multica, AI coding agent task board | 3 | — | mobile agent management | [link](https://github.com/1270011/multica-android-unofficial) |
| — | Using fzf with AI coding agents | 3 | — | CLI integration pattern | [link](https://junegunn.github.io/fzf/tips/using-fzf-with-ai-agents/) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @willvelida.com | "Last week in Agent Security! CERT-In advisory, Langflow MCP exploited, Aoki infostealer, OpenCode Console breach" | 2 | [link](https://bsky.app/profile/willvelida.com/post/3mycaqnyqas2x) |
| @oyrenai.bsky.social | "How much RAM does each AI coding agent actually use? 6 harnesses, 33 sessions: idle CLI ~200-300 MB" | 2 | [link](https://bsky.app/profile/oyrenai.bsky.social/post/3my6dmjthf224) |
| @reksas13.bsky.social | "11 coding-agent harnesses, ~4M lines of source: none imports an agent framework, none retrieves code with embeddings. They grep." | 2 | [link](https://bsky.app/profile/reksas13.bsky.social/post/3mxsq32fqo62i) |
| @hightalk-me.bsky.social | "Changing coding-agent harnesses raises a governance question: which permissions, records and review boundaries carry over?" | 1 | [link](https://bsky.app/profile/hightalk-me.bsky.social/post/3my6nksqfvv27) |
| @brethof.ai | "Open Interpreter: Apache-2.0 Rust terminal coding agent (Codex fork). /harness swaps between Claude Code, Kimi, Qwen, DeepSeek..." | 1 | [link](https://bsky.app/profile/brethof.ai/post/3my5rctc4dh2p) |
| @pdj.bsky.social | "Getting the new team to understand why and how the AI is set up the way it is, is challenging. Very little standardisation." | 1 | [link](https://bsky.app/profile/pdj.bsky.social/post/3mxyw7fsx722b) |

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | Anthropic's internal report: 80% of Claude session time is agents waiting on humans | 1 | 1 | "80% elapsed time is agents waiting for human input" | [link](https://www.reddit.com/r/ClaudeAI/comments/1xag7e5/) |
| r/ClaudeAI | Matt Pocock's Claude Code habits: 5 takeaways about the human, not the AI agent | 1 | 1 | "Get grilled before you build. /grill-me only works if you actually answer." | [link](https://www.reddit.com/r/ClaudeAI/comments/1xat7xn/) |
| r/programming | AI coding agents generate more code, but not more software | 364 | 313 | gains absorbed by review bottleneck | [link](https://www.reddit.com/r/programming/comments/1x32log/) |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | munderdiffl.in | [Oct 19](https://munderdiffl.in/blog/agent-tools-today-2026-10-19/) | Sphinx (Git hook), orchestrator-skill, CC v2.1.302 |
| 🌐 | munderdiffl.in | [Oct 18](https://munderdiffl.in/blog/agent-tools-today-2026-10-18/) | LeanREA, Hy Memory, REA 6.6.0, Orca v1.4.229 |
| 🌐 | munderdiffl.in | [Oct 17](https://munderdiffl.in/blog/agent-tools-today-2026-10-17/) | Reason Network launch, Cline v3.0.73, agentplay |
| 🌐 | munderdiffl.in | [Oct 16](https://munderdiffl.in/blog/agent-tools-today-2026-10-16/) | Muse Spark Open, AI-DLC v2.11.0, Agents SDK v0.24.0 |
| 🌐 | thehackernews.com | [link](https://thehackernews.com/2026/10/opencode-console-breach-may-have.html) | OpenCode breach — API key exposure |
| 🌐 | bleepingcomputer.com | [link](https://www.bleepingcomputer.com/news/security/opencode-hack-exposes-api-keys-amid-ai-distillation-attacks/) | OpenCode distillation attack details |
| 🌐 | gbhackers.com | [link](https://gbhackers.com/aoki-infostealer-targets-ai/) | Aoki infostealer targets .claude.json, Codex config |
| 🌐 | rits.shanghai.nyu.edu | [link](https://rits.shanghai.nyu.edu/ai/google-open-sources-harness2-for-self-improving-ai-agents/) | Google Harness² release |
| 🌐 | reasonmachines.com | [link](https://reasonmachines.com/network) | Reason Network P2P spec |
| 🌐 | reasonmachines.com | [link](https://reasonmachines.com/blog/introducing-reason-agent-1-1) | Reason Agent 1.1 beat Codex |
| 🌐 | github.com/truffle-ai/dexto | [link](https://github.com/truffle-ai/dexto) | Dexto YAML harness |
| 🌐 | github.com/google-research/harness2 | [link](https://github.com/google-research/harness2) | Harness² code |
| 🌐 | github.com/reticlehq/reticle | [link](https://github.com/reticlehq/reticle) | Reticle self-verification |
| 🌐 | github.com/Tencent-Hunyuan/Hy-Memory | [link](https://github.com/Tencent-Hunyuan/Hy-Memory) | Hy Memory 2.0 |
| 🌐 | github.com/omnigent-ai/omnigent | [link](https://github.com/omnigent-ai/omnigent) | Omnigent meta-harness v0.18.0 |
| 🌐 | github.com/awslabs/aidlc-workflows | [link](https://github.com/awslabs/aidlc-workflows) | AIDLC adaptive workflows |
| 🌐 | github.com/qufei1993/skills-hub | [link](https://github.com/qufei1993/skills-hub) | Skills Hub v1.0.0 |
| 🌐 | skillgild.dev | [link](https://skillgild.dev/learn/best-ai-agent-skill-marketplaces) | Skill marketplace comparison |
| 🌐 | mcpworld.com | [link](https://www.mcpworld.com/en/detail/83ae279b9103c1b8c60c2cc447d3729c) | Tons of Skills MCP: 2,900+ skills |
| 🌐 | arstechnica.com | [link](https://arstechnica.com/ai/2026/10/ai-coding-agents-generate-more-code-but-not-more-software/) | Productivity study: review bottleneck |
| 🌐 | coddykit.com | [link](https://www.coddykit.com/pages/blog-detail?id=5129985) | GitHub trending: obra/superpowers 300k, ECC 280k |
| 🌐 | coddykit.com | [link](https://www.coddykit.com/pages/blog-detail?id=5129988) | Agent-to-agent economy: CLI-Anything 52k, claude-plugins 39k |
| 🌐 | dev.classmethod.jp | [link](https://dev.classmethod.jp/en/articles/20261017-cc-updates-v2-1-302/) | CC v2.1.302 fork subagents default |
| 🌐 | gradually.ai | [link](https://www.gradually.ai/en/changelogs/hermes-agent/) | Hermes v0.22.0 changelog |
| 🌐 | github.com/ryanalberts/best-of-agent-harnesses | [link](https://github.com/ryanalberts/best-of-agent-harnesses) | 167 harnesses tracked weekly |
| 🇯🇵 | zenn.dev/aiwatch_jp | [link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained) | 17-layer OSS harness catalog, Sept 2026 |
| 🇯🇵 | zenn.dev/tokium_dev | [link](https://zenn.dev/tokium_dev/articles/843968b5474998) | Skill-first harness development |
| 🇯🇵 | zenn.dev/aws_japan | [link](https://zenn.dev/aws_japan/articles/skills-over-mcp) | SEP-2640 design analysis |
| 🇯🇵 | qiita.com/YushiYamamoto | [link](https://qiita.com/YushiYamamoto/items/4ae5f574b042f1e837bc) | Agent skill/MCP security checklist |
| 🇯🇵 | qiita.com/toyamaru | [link](https://qiita.com/toyamaru/items/5a616011880f12746189) | MCP vs Skills distinction |
| 🇯🇵 | qiita.com/sin-aiagent | [link](https://qiita.com/sin-aiagent/items/54ee8f8d95009f9cbb03) | Google Harness² analysis |
| 🇯🇵 | note.com/masa_wunder | [link](https://note.com/masa_wunder/n/n36fbdb8460c5) | Reason Network hands-on |
| 🇯🇵 | note.com/kazu_t | [link](https://note.com/kazu_t/n/ne997eb7a20c0) | Reason Network architecture |
| 🇯🇵 | hexabase.com | [link](https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026) | 50→10 team via harness engineering |
| 🇯🇵 | ai-agent.camp | [link](https://ai-agent.camp/ja/blog/seo-jp-harness-engineering-ai-agent-guide) | Harness engineering intro (JP) |
| 🇨🇳 | github.com/apiiskan/ai-agent-radar | [link](https://github.com/apiiskan/ai-agent-radar/issues/103) | CN daily digest, 291 projects tracked |
| 🇨🇳 | blog.csdn.net | [link](https://blog.csdn.net/ziwoods/article/details/161662819) | MCP complete guide (CN) |
| 🇨🇳 | blog.csdn.net | [link](https://blog.csdn.net/weixin_42625070/article/details/165804789) | DeepSeek Harness + MCP guide |
| 🇨🇳 | github.com/Tencent-Hunyuan/Hy-Memory | [link](https://github.com/Tencent-Hunyuan/Hy-Memory) | Hy Memory 2.0 |
| 🇨🇳 | kucoin.com | [link](https://www.kucoin.com/news/flash/tencent-hunyuan-launches-open-source-hy-memory-2-0-framework-claims-superior-performance-over-opus-5) | Hy Memory 2.0 CN media coverage |
| 🇨🇳 | letsdatascience.com | [link](https://letsdatascience.com/news/tencent-open-sources-hy-memory-20-stack-f1fcc6c1) | Hy Memory 2.0 analysis |

---

## Stats Block

```
├─ 🟠 Reddit: 14 threads │ 7,913 upvotes │ 1,326 comments │ ⚠ partial (403)
├─ 🔵 X: 15 posts │ 98 likes │ 23 reposts
├─ 🟢 HN: 24 stories │ 623 points │ 438 comments
├─ 🦋 Bluesky: 12 posts │ 13 likes │ 1 repost
├─ 🐙 GitHub: 13 items │ 15 reactions │ 103 comments
├─ 🌐 Web: 48 pages │ 🇯🇵 12 │ 🇨🇳 14
└─ 🗣️ Top voices: @DanKornas, @oyrenai.bsky.social, @willvelida.com │ r/ClaudeAI, r/programming
```

---

## Out of Scope but Notable

- **Sphinx** (git hook that quizzes devs on diff content before push to protected branches, MIT, Oct 14, 110+ stars): Fits agent harness scope tangentially as a safety control layer, but the quiz-developer-not-agent paradigm is novel. [https://sphinx-six-theta.vercel.app/]
- **Antithesis for Agents** (time-travel debugger for agents, "rewinds a bug's history down to the nanosecond"): Belongs more to testing/observability than harness design, but the time-travel concept could reshape how harnesses handle agent error recovery. [https://antithesis.com/blog/2026/time-traveling-agents/]
- **agentplay** — session replay visualization for multiple agent platforms (mentioned Oct 17); could belong to observability topic.

---

## Data Gaps

- **Reddit:** Partial (HTTP 403 after 14 items); r/LocalLLaMA, r/AI_Agents, r/ChatGPTCoding, r/MachineLearning, r/singularity all returned 0 items via dedicated lane. Real discussion volume likely 3-5x higher than captured.
- **YouTube:** No YouTube data (yt-dlp not installed). Tutorial/review content on new harnesses not captured.
- **TikTok/Instagram:** Not available (ScrapeCreators not configured).
- **Zhihu:** HTTP 403 on all Zhihu article fetches; CN harness engineering content proxied via search snippets only.
- **Polymarket:** 0 on-topic markets found.
- **Bluesky:** Keyword search returned 0 items; fallback to handle-specific searches found 12 posts.
- **Coverage estimate:** ~72%. Strong on English web/HN/X/security incidents; moderate on Reddit; limited on video/CN-native/TikTok.
