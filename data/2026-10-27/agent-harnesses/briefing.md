# Agent Harnesses — Daily Briefing
**Date:** 2026-10-27
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 62 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Qiita, Zenn, ITmedia, PR Times, note.com, ai-agent.camp, hexabase.com |
| Web (China) | 10 pages | — | 🇨🇳 Juejin, Zhihu, CSDN, Tencent Cloud, Toutiao, 博客园 |
| GitHub trending | 16 repos | 221k–110k stars | 🌐 week of Oct 25 |
| Bluesky | 0 posts | — | SOURCE HEALTH: OK; no agent-harness posts retrieved this run |

---

## Synthesized Findings

### 1. [new] OpenCode 2.0: architectural rewrite ships (Oct 12–16)

**Claim:** OpenCode 2.0 (Oct 12–13 announcement, v2.0.32 Oct 16, 219.4k stars +5.2k/week) rebuilds around a single shared background service; terminal, web, desktop, and SDK all connect to one process.
- **Code Mode:** minimal JS interpreter — MCP servers + OpenAPI endpoints become callable functions in one round-trip script; no unrestricted FS access; individual tool permissions enforced
- **Background subagents & async shell:** concurrent work without blocking
- **@opencode/client + @opencode/sdk:** embed OpenCode into any app
- **80+ internal plugins** now core to the project; **V1 plugins break** (API contracts changed)
- **3 built-in agents:** build (full access), plan (read-only), general (subagent)
- **Star trajectory:** 219.4k (Oct 25); DeepSeek Harness leads at ~248k
- **CN context:** Chinese devs favor OpenCode for data sovereignty (local model, no cloud upload); per Artificial Analysis Oct 5: CC+Sonnet 5.5 index 68 ($14.19/task) vs OpenCode+GLM-5.3 index 54 ($4.24/task) — cost gap is driver
- **Sources:** https://aiidelist.com/blog/opencode-2-0-release-code-mode-background-agents · https://alternativeto.net/news/2026/10/opencode-2-0-officially-launches-with-background-agents-code-mode-and-a-rebuilt-api/ · https://munderdiffl.in/blog/opencode-2-0/ · https://opencode.ai/changelog · https://latenode.com/news/opencode-2-0-adds-background-subagents-and-breaks-v1-plugins

---

### 2. [new] Claude Code MCP Tasks & Elicitations: durable workflows land (Oct 19–23)

**Claim:** CC v2.1.304 (Oct 19) ships MCP Tasks + Elicitations — MCP tool calls become durable jobs and can pause to ask users questions. v2.1.305 (Oct 20) fixes regression; v2.1.310 (Oct 23) extends Monitor tool to Bedrock/Vertex/Foundry.
- **MCP Tasks:** server returns task handle (id, status, TTL, polling interval) instead of blocking; CC polls until completion delivers normal tool result
- **Elicitations:** server pauses mid-task for structured user input (confirmations, URL sign-in forms); CC renders dialog automatically, no config needed
- **Surfaces:** Terminal CLI + Agent SDK + GitHub Actions only; VS Code extension, desktop app, and Amazon Bedrock excluded
- **Protocol:** revision 2026-07-28 (stateless); calls from main conversation only, not subagents
- **v2.1.310 (Oct 23):** Monitor tool + plugin monitors on Bedrock/Vertex/Foundry; Enterprise custom roles for cloud sessions + Remote Control; blocks long-duration foreground sleep in those envs (use Monitor with until-loop or run_in_background)
- **Impact:** no more custom polling glue in every plugin; mid-task consent is now protocol-native
- **Sources:** https://forkast.news/claude-ships-mcp-tasks-and-elicitations-in-claude-code-durable-agent-workflows-narrow-launch/ · https://cellcog.ai/blog/claude-code-mcp-tasks/ · https://dev.classmethod.jp/en/articles/20261024-cc-updates-v2-1-310/ · https://alphasignal.ai/news/anthropic-lets-claude-code-run-hours-long-jobs-without-dropping-them · https://flaviocopes.com/claude-code-mcp-tasks-elicitations/ · https://www.developersdigest.tech/blog/claude-code-mcp-tasks-elicitations-long-running-tools-2026

---

### 3. [new] Claude Duet: Anthropic's proactive always-on agent app (Oct 21)

**Claim:** Anthropic launched Claude Duet (Oct 21) — a proactive agent app competing directly with Meta Muse and OpenAI Dots; waitlist-only research preview, US Pro/Max subscribers.
- **Built on:** Opus 5.5
- **Features:** morning brief from connected apps; checks apps every few hours; alerts on attention-needed items; cloud VM with own browser; approval-gated for risky actions (payments, sending messages, deletions)
- **Targets:** professionals + small business owners with high information volume
- **Available:** web + standalone iOS app; not yet Android; US only
- **Strategic:** standalone product, separate from Claude Code / CC subscription
- **Sources:** https://www.macrumors.com/2026/10/21/anthropic-claude-duet/ · https://cellcog.ai/blog/claude-duet/ · https://felloai.com/claude-duet/ · https://www.grandlinux.com/en/blogs/claude-duet.html · https://www.layer3labs.io/guides/claude-duet-explained

---

### 4. [new] AAIF adds Agent Skills + 3 others at AGNTCon San Jose (Oct 22)

**Claim:** Agentic AI Foundation grew from 3 to 10 projects in its first year; four donations at AGNTCon + MCPCon North America (Oct 22–23, San Jose, 3,500+ attendees) include Anthropic formalizing Agent Skills as open standard.
- **Agent Skills** (Anthropic): "packaging instructions, scripts, and resources in reusable modules that load on demand across different agent platforms"; 1M public skills, 280M installs, 70+ platforms
  - Quote (David Soria Parra, Anthropic): "Without the right context, even the most intelligent agents fall short."
- **Open Responses** (OpenAI): spec for multi-provider LLM interfaces based on Responses API; "write once, deploy across providers"
  - Quote (Steve Coffey, OpenAI): "...helping developers build great products on today's language models through simple, clean, and unified interfaces."
- **OpenEnv** (Hugging Face): containerized, interoperable RL environments; trains + evaluates agents
  - Quote (Ben Burtenshaw, HF): "Reinforcement Learning environments are a fundamental part of that stack..."
- **OpenSandbox** (Alibaba): multi-language SDKs + unified APIs for secure agent execution
  - Quote (Xiaobin Xu, Alibaba): "...creating a path for more developers and organizations to help shape how sandbox environments work."
- **Also at AGNTCon:**
  - Buzz (Block): Nostr-based open workspace for humans + agents; 80k communities, 36k GitHub stars; v1.0 due mid-Nov; Bradley Axen (goose creator)
  - WebMCP (Chrome): proposed web standard (in origin trial) — websites expose tool interfaces to agents natively
  - CyberGym: observatory tracking AI-generated exploits across 1,500+ vulnerabilities
  - ~1/3 of 116 MCP conformance scenarios now test security; identity roadmap: proof-of-possession tokens, workload identity federation
- **🇯🇵 JP context (Qiita):** "Anthropicがエージェントスキルを寄贈。ChatGPT、Cursor、GitHub Copilotを含む70以上のプラットフォームが採用予定" ("Anthropic donates Agent Skills; 70+ platforms including ChatGPT, Cursor, GitHub Copilot to adopt")
- **🇨🇳 CN context:** Alibaba's OpenSandbox contribution seen as CN's contribution to open agentic standard; covered positively on CN tech hubs
- **Sources:** https://aaif.io/news/agentic-ai-foundation-announces-four-new-projects · https://www.prnewswire.com/news-releases/agentic-ai-foundation-announces-four-new-projects-agent-skills-open-responses-openenv-and-opensandbox-302916689.html · https://www.infoq.com/news/2026/10/agntcon-mcpcon-2026/ · https://www.unite.ai/agentic-ai-foundation-adds-four-projects-to-reach-10-in-first-year/ · https://block.xyz/inside/introducing-buzz-where-humans-and-agents-work-together

---

### 5. [new] Entire: ex-GitHub CEO launches agent-native Git forge (Oct 26)

**Claim:** Entire (by Thomas Dohmke, ex-GitHub CEO) launched Oct 26 — reinvents every layer of software development for teams where agents write most code: Trails replace PRs, automated review gates, distributed hosting, agent-native continuous memory.
- **Trails:** replace pull requests; review agents score every push on security, slop (quantitative AI-output-quality metric), and risk; merge waits for green scores, closed findings, human approval + passing CI
- **Performance:** pushes 89x faster than GitHub; 6x faster than Cursor Origin
- **Continuous Memory (entire-brain):** indexes structural maps + agent session logs stored in Git; carries "the why behind the what changed" across agent sessions
- **Distributed hosting:** US/EU/India/Australia with global expansion planned
- **Context:** GitHub had 257 incidents in 12 months (per TechTimes framing)
- **Sources:** https://entire.com/news/entire-launches-an-independent-git-forge-for-agent-human-collaboration · https://www.techtimes.com/articles/329530/20261027/github-had-257-incidents-12-months-entire-ships-distributed-forge-ai-agents.htm · https://thenewstack.io/entire-trails-agentic-code-review/ · https://cellcog.ai/blog/entire-git-forge-for-agents/ · https://runtimewire.com/article/entire-agent-first-git-forge-thomas-dohmke

---

### 6. [new] T3 Code v0.1.1: new harness control surface from Ping.gg (Oct 21)

**Claim:** T3 Code v0.1.1 (Oct 21; v0.1.0 stable Oct 15) is a free MIT-licensed "agent harness control surface" from Ping.gg — mobile/web/Electron desktop apps for multi-harness orchestration with delegate_task cross-provider routing.
- **Supported harnesses:** Codex, Claude Code, Cursor, Grok Build, OpenCode, Antigravity, Pi, Muse Code (beta), ACP Registry agents
- **delegate_task:** hand task from one agent (e.g. Claude planning) to another on any provider/model (e.g. Codex implementing); returns result
- **Mobile:** iOS + Android apps; web + Electron desktop
- **Orchestrator V2:** stable since Oct 15; React Compiler optimizations
- **Sources:** https://github.com/pingdotgg/t3code/releases/tag/v0.1.1 · https://daily.dev/posts/t3-code-is-an-agent-harness-control-surface--0pfyh8muc · https://skyflo.ai/compare/t3-code

---

### 7. [new] Agent Relay: open-source agent-to-agent communication layer (Oct 23)

**Claim:** Agent Relay (Khaliq Gant + Will Washburn, YC-backed, Apache-2.0, ~1k stars) launched Oct 23 — agents on different machines/providers share channels, search each other's sessions, and hand off work directly.
- **Core problem solved:** "Today every handoff runs through people: your agent, you, your teammate, their agent. With Agent Relay the agents talk directly."
- **Example:** frontend agent asks backend agent what an endpoint returns, instead of routing through a human
- **Architecture:** free cloud tier + self-hostable relay
- **Context:** Coder integrated Agent Relay with CC Sep 15; SpaceXAI was launch partner Sep 4
- **Sources:** https://agentrelay.com/ · https://www.ibtimes.com/agent-relay-building-missing-communication-layer-ai-agents-3808082 · https://www.ycombinator.com/companies/agent-relay · https://www.globenewswire.com/news-release/2026/09/15/3362210/0/en/coder-brings-claude-code-to-agent-relay-unlocking-agentic-development-for-the-world-s-most-regulated-enterprises.html

---

### 8. [new] cccskills: Japanese-language skills marketplace with execution scoring (Oct 27)

**Claim:** cccskills (launched Oct 27, Japan) — Agent Skills marketplace with 100k+ skills, execution scoring (real with/without test), safety A/B/C ratings; MCP server for agents to self-discover skills.
- **Execution score:** agents with and without skill solve same task; results scored blindly by AI on quality, speed, token usage, stability (0–100)
- **Safety ratings:** checks external data transmission, command execution, file deletion, credential access
- **As of Oct 26:** 100k+ skills; 5,821 rated; 3,394 safety-A; 152 safety-C
- **MCP:** `claude mcp add --transport http cccskills https://cccskills.com/mcp`; search_skills + get_skill
- **Languages:** JP/EN/ZH/KO results
- **Pricing:** free 50/day; ¥15k/year (5k/month); ¥45k/year (25k/month)
- **🇯🇵 Source:** https://prtimes.jp/main/html/rd/p/000000085.000041726.html · https://cccskills.com/

---

### 9. [new] OpenVLHarness: training-free visual agent harness (arXiv:2610.26860, Oct 19)

**Claim:** OpenVLHarness (UCLA NLP, Oct 19, arXiv:2610.26860) — training-free visual agent harness adding 9 tool capabilities + multimodal persistent memory to any tool-calling backbone. +9.7–12.6 points across 22 benchmarks.
- **9 capabilities:** visual grounding, OCR, depth, camera trajectory, zoom, text search, image search, webpage visits, Python coding agent
- **Multimodal memory:** images, boxes, masks, depth maps, web refs stay addressable for whole question
- **Training-free:** works with frozen backbone weights via native tool calling
- **22 benchmarks × 4 domains × 7 backbones:** +9.7–12.6 average points over same models without tools
- **Sources:** https://github.com/uclanlp/OpenVLHarness · https://arxiv.org/html/2610.26860 · https://huggingface.co/papers/2610.26860

---

### 10. [new] Agent Bill of Materials (ABOM/AIBOM): governance layer emerging

**Claim:** Multiple independent teams released Agent BOM tooling this week — open specs and scanners for inventorying AI agent components (model, memory, skills, sandbox, router) in CycloneDX-compatible formats.
- **WasmAgent/agentbom:** open spec for agent inventories (tools, permission scopes, model deps, compliance, capability assertions) — verifiable document
- **Aj7Ay/agent-harness-aibom (PyPI: agent-harness-aibom):** CycloneDX 1.6 AIBOM generator for Hermes/OpenClaw; scans runtime binary, models, skills, MCP servers, hooks, secrets surface
- **cisco-ai-defense/aibom:** scans codebases, container images, cloud envs; supports Python/JS/TS/Java/Go/Rust/Ruby/C#
- **CycloneDX/specification issue #895:** formal proposal for "Agent Bill of Materials" extension
- **Five layers defined:** Model (reasoning engine), Memory (persistent context), Skills (capability packages), Sandbox (isolated execution), Router (model selection/failover)
- **Sources:** https://github.com/WasmAgent/agentbom · https://github.com/Aj7Ay/agent-harness-aibom · https://pypi.org/project/agent-harness-aibom/ · https://github.com/cisco-ai-defense/aibom · https://dev.to/max_quimby/the-agent-bill-of-materials-is-on-github-right-now-2c9j · https://agentconn.com/blog/agent-bill-of-materials-github-trending-2026/

---

### 11. [update] Hermes v0.22.5: plugin catalog 614→763, Singularity to plugins, mcp-serve (Oct 23)

**New fact since Oct 20:** v0.22.5 (Oct 23) rolls up 81 PRs/231 commits, grows plugin catalog from 614 to 763, moves Singularity backend out of core into plugins, and adds pluggable delegation backends per session.
- **v0.22.5 (Oct 23):** 81 PRs, 231 commits
- **New plugins:** mcp-serve (Hermes as MCP server), agent-importers (Cursor support), bubblewrap (bwrap Linux), singularity, inbox, workflow-record, advanced-delegation, deadbolt
- **Pluggable delegation backends:** route subagents by model map or profile; switchable per session
- **Plugin slash commands** can present option pickers to users
- **Platform:** Electron 44 + Pillow 13 upgrades; drag-to-pin sidebar; one-click installs with tier badges; improved Windows update recovery
- **v0.22.4 (Oct 21):** removed suggestion pills; skip consent for no-dependency plugins; WhatsApp logout/re-pair fix
- **v0.22.3 (Oct 21):** minor distribution update
- **mcp-serve plugin:** Hermes can now act as an MCP server, exposing its agents and tools to other harnesses
- **Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.5 · https://freedom.tech/posts/2026-10-23-hermes-agent-0-22-5/ · https://www.gradually.ai/en/changelogs/hermes-agent/ · https://hermesatlas.com/projects/42-evey/hermes-plugins

---

### 12. [update] Claude Code auto mode: rolling out as default for Pro/Max/Team (Oct 22+)

**New fact since Oct 20:** Auto mode classifier announced as default rollout beginning Oct 22+ for Pro/Max/Team new sessions; classifier overhead no longer billed.
- **What changed:** new sessions start in auto mode instead of requiring explicit permission approval per action
- **Safety model:** automated classifier reviews actions; safe ones proceed; risky ones blocked while CC finds another route — 89% catch rate vs 13.6% human baseline
- **Cost change:** classifier overhead no longer charged on Pro/Max/Team
- **Scope:** users without custom default mode; org-managed defaults never overridden
- **Extension to web/desktop/mobile:** Claude.ai apps also rolling out auto mode default starting following week
- **Sources:** https://claude.com/resources/articles/auto-mode-default-in-claude-code · https://cellcog.ai/blog/claude-code-auto-mode/ · https://www.xda-developers.com/auto-mode-is-now-claude-codes-default-and-it-changes-how-fast-you-can-actually-build/ · https://explainx.ai/blog/claude-code-auto-mode-default-pro-max-team-august-2026

---

### 13. [update] MCP stateless at 70% of platform traffic; 4-version coexistence; Red Hat gateway

**New fact since Oct 20:** Per AGNTCon data, ~70% of platform traffic now on stateless MCP (2026-07-28 revision); 4 protocol versions coexist; Red Hat MCP gateway (Oct 16) negotiates per client.
- **July 28, 2026 revision:** initialize/initialized handshake removed; Mcp-Session-Id deprecated; each request carries protocol version, client info, capabilities independently
- **Load balancing:** standard round-robin now viable (no sticky sessions)
- **Caching:** tool + prompt lists cacheable at gateway layer
- **4 versions coexisting:** 2025-03-26, 2025-06-18, 2025-11-25, 2026-07-28
- **Red Hat MCP gateway (Oct 16):** negotiates compatibility per client across all 4 versions
- **Schema efficiency:** 75% of published servers keep schemas under 1KB
- **🇯🇵 JP source (Qiita kakusan2022):** "必須だった `initialize` / `initialized` のハンドシェイクが廃止された" ("The previously required initialize/initialized handshake was abolished") — https://qiita.com/kakusan2022/items/4673c56be9f2ff850a28
- **Sources:** https://www.infoq.com/news/2026/10/agntcon-mcpcon-2026/ · https://qiita.com/kakusan2022/items/4673c56be9f2ff850a28

---

### 14. [update] LongHorizon-Harness v0.1.8: reliability fixes + CC MCP isolation (Oct 21)

**New fact since Oct 20:** v0.1.8 (Oct 21) fixes resumed-run approval bug (HTTP 409), adds CC MCP isolation (--strict-mcp-config), and adds configurable final reply budget.
- **Fixed:** resumed run no longer inherits managed=false
- **Fixed:** CC passes --strict-mcp-config; user/project MCP registries no longer loaded implicitly
- **Fixed:** DeepSeek output ASCII-escaped JSONL (Unicode survives legacy stdout)
- **New:** configurable final reply budget (--final-response-timeout)
- **Still blocked:** native Windows (POSIX-only control-bus; use WSL2)
- **Sources:** https://github.com/AMAP-ML/LongHorizon-Harness/releases/tag/v0.1.8 · https://github.com/AMAP-ML/LongHorizon-Harness

---

### Still true (ongoing threads, no new facts this week)

- **google-harness2-recursive** — Harness² (Oct 9, Google Research/Northwestern, Apache 2.0) still arXiv lead; no new activity
- **reason-network-multi-pc-p2p** — Reason Network P2P agent coordination (Oct 16); no new release
- **reticle-agent-self-verify** — reticlehq/reticle runtime perception SDK; no new release
- **hy-memory-tencent-dual-system** — Tencent Hy Memory 2.0 (590+ stars); no new release
- **opencode-console-breach** — Oct 16-17 breach; keys revoked; v1.19.1 discontinued session sharing
- **aoki-infostealer-coding-agent-creds** — Symantec Oct 2026; ongoing threat
- **langflow-mcp-cve-stdio** — CVE-2026-105740 CVSS 9.9; no new patch
- **leanrea-8kb-skill-replacement** — 8KB SKILL.md vs 207-tool MCP; efficiency benchmark stands
- **skills-hub-v1-desktop-app** — Skills Hub v1.0.0 cross-platform desktop; no new version
- **anthropics-claude-plugins-official** — 39k stars; ongoing
- **cursor-plugins-marketplace-official** — 11,804 stars, 75+ plugins; ongoing
- **reason-agent-1-1-beats-codex** — 65.1 vs 62.5 CAI; no new benchmarks
- **dexto-yaml-agent-harness** — YAML agent harness; ongoing
- **aidlc-workflows-v211-aws** — v2.11.1 (Oct 20); ongoing
- **omnigent-meta-harness** — Databricks Omnigent v0.18.0 (Oct 13); ongoing
- **morluto-rea-reverse-engineering-mcp** — REA 6.6.0; ongoing
- **skills-over-mcp-wg-sep2640** — SEP-2640 Final; Cloudflare MCP production; ongoing
- **harness-context-tax-problem** — LeanREA 60% token reduction standing; CC idle compaction; ongoing
- **mcp-security-nsa-supply-chain** — Aoki infostealer + Langflow CVE + OpenCode breach stack ongoing
- **agentskills-open-standard** — Agent Skills donated to AAIF (see finding #4) — status upgraded above
- **obra-superpowers-skills** — 305k stars (+3.4k/week); ongoing
- **self-harness-auto-optimization** / **ahe-automated-harness-evolution** — Harness²; no new papers
- **harness-engineering-paradigm** — JP community; ongoing
- **extension-economy-explosion** — addyosmani/agent-skills 110k+ stars (+2.3k/week); obra/superpowers 305k; cccskills launched (see #8)
- **sep-2640-mcp-skills-final** — AAIF Agent Skills donation (see #4) further solidifies; ongoing
- **vscode-1138-agent-host-protocol** — VS Code 1.141.1; no new release
- **github-copilot-skills-mcp-ga** — Copilot v1.0.99; ongoing
- **codex-cli-0155-voice-touchid** — v0.162.1; ongoing
- **devin-desktop-windsurf-rebrand** — Devin Desktop v3.10.67; ongoing
- **antigravity-gemini-cli-successor** — v2.23.0/CLI v1.3.6; ongoing
- **harmony-harness-google-cmu** — arXiv:2610.15150; ongoing
- **workday-agent-harness-ga** — GA Oct 13; ongoing
- **harness-io-acquires-cosmos** — Harness.io/Cosmos; ongoing
- **corbenic-galahad-memory** — KV cache persistence; ongoing
- **vercel-labs-skills-universal-cli** — 34,667 stars; ongoing
- **lexmount-moli-rust-browser** — 17.9k stars; ongoing
- **cloudflare-sep2640-production-server** — Cloudflare MCP skills; ongoing
- All remaining ~80 ongoing threads from prior state carry forward unchanged

---

## Cross-Source Patterns

**Pattern 1: "Agent stack formalization week"**
- AAIF adding Agent Skills + OpenSandbox + Open Responses + OpenEnv lands the same week as Claude Duet, MCP Tasks, and OpenCode 2.0 — the foundational protocol, sandbox, model-interface, and capability layers all got formal standards simultaneously.
- Platforms: Global web (InfoQ, PR Newswire), 🇯🇵 Qiita, 🇨🇳 Toutiao/Juejin
- Key quote: "Without the right context, even the most intelligent agents fall short." — David Soria Parra, Anthropic (https://aaif.io/news/agentic-ai-foundation-announces-four-new-projects)

**Pattern 2: Agent harness infrastructure going proactive and persistent**
- Claude Duet (always-on, morning briefs), OpenCode 2.0 (background service), MCP Tasks (durable jobs), Entire (continuous memory), Agent Relay (agent-to-agent channels) — five independent projects all move in the same direction: agents should run continuously, not in one-shot sessions.
- Platforms: Global web, 🇯🇵 Qiita/note
- Key quote: "Anthropic Lets Claude Code Run Hours-Long Jobs Without Dropping Them" — alphasignal.ai headline (https://alphasignal.ai/news/anthropic-lets-claude-code-run-hours-long-jobs-without-dropping-them)

**Pattern 3: Agent BOM / governance layer emerging as category**
- Independently: Cisco (aibom), WasmAgent (agentbom), Aj7Ay (agent-harness-aibom), CycloneDX proposal — four teams building inventory/compliance tooling for agent harnesses.
- Platforms: Global web (GitHub, DEV, PyPI)
- Quote: "teams hand-rolling these layers are accumulating architectural debt that compounds daily" — agentconn.com (https://agentconn.com/blog/agent-bill-of-materials-github-trending-2026/)

**Pattern 4: Git infrastructure rebuilt for agent-speed write traffic**
- Entire (89x faster pushes, Trails, distributed hosting) signals that existing Git infrastructure (GitHub) wasn't designed for machine-speed code commits; agent era may require infrastructure fork.
- Platforms: Global web (The New Stack, TechTimes, Analytics India Magazine)

**Pattern 5: Skills marketplaces differentiating on trust signals (🌐 + 🇯🇵)**
- cccskills (JP) adds execution scoring + A/B/C safety ratings; agentskillexchange requires real upstream project per skill; SkillExchange adds marketplace comparisons — quality signals replacing star counts as selection criteria
- Platforms: 🇯🇵 PR Times, global web
- Quote: "実行スコア" (execution score) — cccskills (https://prtimes.jp/main/html/rd/p/000000085.000041726.html)

---

## Per-Platform Tables

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Forkast | https://forkast.news/claude-ships-mcp-tasks-and-elicitations-in-claude-code-durable-agent-workflows-narrow-launch/ | MCP Tasks & Elicitations full explainer |
| 🌐 | dev.classmethod.jp | https://dev.classmethod.jp/en/articles/20261024-cc-updates-v2-1-310/ | CC v2.1.304/305/310 changelog |
| 🌐 | entire.com | https://entire.com/news/entire-launches-an-independent-git-forge-for-agent-human-collaboration | Entire official announcement |
| 🌐 | aaif.io | https://aaif.io/news/agentic-ai-foundation-announces-four-new-projects | AAIF 4 new projects |
| 🌐 | InfoQ | https://www.infoq.com/news/2026/10/agntcon-mcpcon-2026/ | AGNTCon full coverage |
| 🌐 | MacRumors | https://www.macrumors.com/2026/10/21/anthropic-claude-duet/ | Claude Duet launch |
| 🌐 | aiidelist | https://aiidelist.com/blog/opencode-2-0-release-code-mode-background-agents | OpenCode 2.0 explainer |
| 🌐 | alternativeto | https://alternativeto.net/news/2026/10/opencode-2-0-officially-launches-with-background-agents-code-mode-and-a-rebuilt-api/ | OpenCode 2.0 official launch |
| 🌐 | startupcorners | https://startupcorners-app-production.up.railway.app/digest/devtools-digest-2026-10-21 | GitHub Trending Oct 21 digest |
| 🌐 | coddykit | https://www.coddykit.com/pages/blog-detail?id=5129998 | GitHub Trending Oct 2026 |
| 🌐 | ibtimes | https://www.ibtimes.com/agent-relay-building-missing-communication-layer-ai-agents-3808082 | Agent Relay |
| 🌐 | agentrelay.com | https://agentrelay.com/ | Agent Relay official |
| 🌐 | YC | https://www.ycombinator.com/companies/agent-relay | Agent Relay YC page |
| 🌐 | Coder blog | https://coder.com/blog/introducing-agent-relay-cloud-hosted-agents-self-hosted-execution | Agent Relay + Coder |
| 🌐 | arXiv | https://arxiv.org/html/2610.26860 | OpenVLHarness paper |
| 🌐 | GitHub uclanlp | https://github.com/uclanlp/OpenVLHarness | OpenVLHarness repo |
| 🌐 | HuggingFace | https://huggingface.co/papers/2610.26860 | OpenVLHarness HF page |
| 🌐 | GitHub AMAP-ML | https://github.com/AMAP-ML/LongHorizon-Harness/releases/tag/v0.1.8 | LH-Harness v0.1.8 |
| 🌐 | freedom.tech | https://freedom.tech/posts/2026-10-23-hermes-agent-0-22-5/ | Hermes v0.22.5 |
| 🌐 | NousResearch releases | https://github.com/NousResearch/hermes-agent/releases/tag/v0.22.5 | Hermes releases |
| 🌐 | gradually.ai | https://www.gradually.ai/en/changelogs/hermes-agent/ | Hermes changelog |
| 🌐 | GitHub pingdotgg | https://github.com/pingdotgg/t3code/releases/tag/v0.1.1 | T3 Code v0.1.1 |
| 🌐 | daily.dev | https://daily.dev/posts/t3-code-is-an-agent-harness-control-surface--0pfyh8muc | T3 Code overview |
| 🌐 | claude.com | https://claude.com/resources/articles/auto-mode-default-in-claude-code | Auto mode official |
| 🌐 | alphasignal | https://alphasignal.ai/news/anthropic-lets-claude-code-run-hours-long-jobs-without-dropping-them | CC hours-long jobs |
| 🌐 | block.xyz | https://block.xyz/inside/introducing-buzz-where-humans-and-agents-work-together | Block Buzz |
| 🌐 | PR Newswire | https://www.prnewswire.com/news-releases/agentic-ai-foundation-announces-four-new-projects-agent-skills-open-responses-openenv-and-opensandbox-302916689.html | AAIF official PR |
| 🌐 | GitHub WasmAgent | https://github.com/WasmAgent/agentbom | AgentBOM spec |
| 🌐 | GitHub Aj7Ay | https://github.com/Aj7Ay/agent-harness-aibom | AIBOM generator |
| 🌐 | GitHub cisco | https://github.com/cisco-ai-defense/aibom | Cisco AI BOM |
| 🌐 | PyPI | https://pypi.org/project/agent-harness-aibom/ | AIBOM package |
| 🌐 | DEV agentconn | https://agentconn.com/blog/agent-bill-of-materials-github-trending-2026/ | ABOM trending article |
| 🌐 | DEV max_quimby | https://dev.to/max_quimby/the-agent-bill-of-materials-is-on-github-right-now-2c9j | ABOM explainer |
| 🌐 | best-of digest | https://github.com/RyanAlberts/best-of-Agent-Harnesses/releases/tag/digest-2026-10-25 | Star movers week Oct 25 |
| 🌐 | TechTimes | https://www.techtimes.com/articles/329530/20261027/github-had-257-incidents-12-months-entire-ships-distributed-forge-ai-agents.htm | Entire + GitHub context |
| 🌐 | The New Stack | https://thenewstack.io/entire-trails-agentic-code-review/ | Entire Trails |
| 🌐 | cellcog Claude Duet | https://cellcog.ai/blog/claude-duet/ | Claude Duet explainer |
| 🌐 | felloai | https://felloai.com/claude-duet/ | Duet pricing/access |
| 🌐 | GlobeNewswire | https://www.globenewswire.com/news-release/2026/09/15/3362210/0/en/coder-brings-claude-code-to-agent-relay-unlocking-agentic-development-for-the-world-s-most-regulated-enterprises.html | Coder + CC + Agent Relay |
| 🌐 | cccskills.com | https://cccskills.com/ | cccskills platform |
| 🌐 | agentskillexchange | https://github.com/agentskillexchange/skills | Skills catalog |
| 🌐 | hermesatlas | https://hermesatlas.com/projects/42-evey/hermes-plugins | Hermes plugin catalog |
| 🌐 | xda-developers | https://www.xda-developers.com/auto-mode-is-now-claude-codes-default-and-it-changes-how-fast-you-can-actually-build/ | Auto mode rollout |
| 🇯🇵 | Qiita kakusan2022 | https://qiita.com/kakusan2022/items/4673c56be9f2ff850a28 | MCP stateless + AAIF JP coverage |
| 🇯🇵 | Qiita hathibei7 | https://qiita.com/hathibei7/items/a398c118c40bd92d6956 | Oct 24 AI cloud roundup |
| 🇯🇵 | PR Times | https://prtimes.jp/main/html/rd/p/000000085.000041726.html | cccskills launch JP |
| 🇯🇵 | Zenn aiwatch_jp | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | 17-layer OSS catalog |
| 🇯🇵 | Zenn tokium_dev | https://zenn.dev/tokium_dev/articles/843968b5474998 | Skill-first harness methodology |
| 🇯🇵 | Zenn tkszenn | https://zenn.dev/tkszenn/articles/cafc72cd8d1754 | Cursor harness engineering |
| 🇯🇵 | ai-agent.camp | https://ai-agent.camp/ja/blog/seo-jp-harness-engineering-ai-agent-guide | 内部/外部 harness guide |
| 🇯🇵 | hexabase.com | https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026 | 50→10 team case study |
| 🇯🇵 | note.com | https://note.com/noted_gerbil9067/n/n34922dbe801c | Claude auto mode JP coverage |
| 🇯🇵 | ITmedia | https://www.itmedia.co.jp/aiplus/article/2608/10/2000000487/ | Skills+MCP standard Aug coverage |
| 🇨🇳 | Juejin | https://juejin.cn/post/7694947768088657935 | MCP-as-USB-C architecture |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1999804779141030200 | 2026 AI coding tools panoramic review |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2011954028528038812 | 2026 complete guide to AI tools |
| 🇨🇳 | CSDN oscar999 | https://blog.csdn.net/oscar999/article/details/160346041 | CC vs OpenCode comparison |
| 🇨🇳 | CSDN weixin | https://blog.csdn.net/weixin_50937681/article/details/161960735 | 4-CLI tool 30-day test |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2634560 | CC + OpenCode selection guide |
| 🇨🇳 | Zhihu OpenHarness | https://zhuanlan.zhihu.com/p/2023728026781796003 | HKUDS OpenHarness coverage |
| 🇨🇳 | Toutiao | https://www.toutiao.com/article/7610595807275893263/ | CC 1-year anniversary; AAIF stack |
| 🇨🇳 | 博客园 itech | https://www.cnblogs.com/itech/p/19918589 | OpenCode as CC substitute CN |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded from scope)
├─ 🔵 X: 0 posts (excluded from scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 0 stories directly captured
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (SOURCE HEALTH: OK; no agent-harness posts this run)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 62 pages │ 🇯🇵 9 │ 🇨🇳 10
└─ 🗣️ Top voices: @DavidSoriaParra (Anthropic), Thomas Dohmke (Entire), Khaliq Gant + Will Washburn (Agent Relay), Brad Axen (Buzz/Block)
```

---

## Out of Scope but Notable

- **Claude API version 2026-10-21** (Oct 22): Anthropic released the first official API version since 2023, enabling more frequent breaking-change handling. Relevant to api-sdks topic, not harnesses. https://qiita.com/hathibei7/items/a398c118c40bd92d6956
- **ChatGPT Team Tasks** (Oct 21): OpenAI's Dots-adjacent feature automating routine engineering work (weekly status summaries, team review + adjustment of future tasks). Competes with Claude Duet/Dots in proactive-agent space. https://qiita.com/hathibei7/items/a398c118c40bd92d6956
- **WebMCP (Chrome)**: Proposed web standard in origin trial at AGNTCon — websites expose tool interfaces directly to AI agents without any MCP server setup. If it ships, it collapses the distinction between "website" and "MCP server." https://www.infoq.com/news/2026/10/agntcon-mcpcon-2026/

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** returned CAPTCHA for both JP and ZH queries; fell back to native-language WebSearch + direct WebFetch on top results — coverage achieved but hub discovery was less exhaustive than ideal
- **Bluesky:** SOURCE HEALTH OK; no agent-harness posts retrieved this run (low-signal day for this topic on BSky)
- **Reddit / X / Twitter:** excluded from scope per instructions
- **Zhihu direct fetch:** HTTP 403 on https://zhuanlan.zhihu.com/p/1999804779141030200 — content inferred from search summaries
- **CSDN article 163539691:** HTTP 521 — content not retrieved
- **Hacker News:** no explicit HN thread found for this week's agent-harness launches (Entire / Agent Relay / T3 Code not spotted as active HN threads during this run — may have appeared but not surfaced in search results)
- **OpenCode 2.0 The New Stack:** page returned no article content (only newsletter form)
- **Approximate coverage:** 82% — all major English sources covered; JP/ZH had CAPTCHA limitation but WebSearch fallback recovered most content; no YouTube/TikTok/Reddit/social data

---

## Key Quotes

> "Without the right context, even the most intelligent agents fall short." — David Soria Parra, Anthropic, on Agent Skills donation to AAIF ([link](https://aaif.io/news/agentic-ai-foundation-announces-four-new-projects))

> "Anthropic Lets Claude Code Run Hours-Long Jobs Without Dropping Them" — alphasignal.ai ([link](https://alphasignal.ai/news/anthropic-lets-claude-code-run-hours-long-jobs-without-dropping-them))

> "Today every handoff runs through people: your agent, you, your teammate, their agent. With Agent Relay the agents talk directly, and you both stay on the work." — Agent Relay ([link](https://agentrelay.com/))

> "必須だった `initialize` / `initialized` のハンドシェイクが廃止された" ("The previously required initialize/initialized handshake was abolished") — Qiita kakusan2022 on MCP stateless revision ([link](https://qiita.com/kakusan2022/items/4673c56be9f2ff850a28))

> "Claude Code 発布一周年：2026年Agentic AI底層基礎設施與標準化" ("Claude Code one-year anniversary: Agentic AI underlying infrastructure and standardization in 2026") — Toutiao headline ([link](https://www.toutiao.com/article/7610595807275893263/))

> "Trails replace the pull request: review agents score every push on evals such as security, slop and risk, and a merge waits until the scores are green and the findings are closed." — Entire ([link](https://entire.com/news/entire-launches-an-independent-git-forge-for-agent-human-collaboration))

> "teams hand-rolling these layers are accumulating architectural debt that compounds daily" — AgentConn Blog on ABOM ([link](https://agentconn.com/blog/agent-bill-of-materials-github-trending-2026/))

> "AI エージェントが自分で「使えるスキル」を選ぶ" ("AI agents select 'usable skills' themselves") — cccskills PR Times launch announcement ([link](https://prtimes.jp/main/html/rd/p/000000085.000041726.html))
