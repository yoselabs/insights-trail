# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-07-17
**Query type:** GENERAL
**Sources:** Hacker News, X/Twitter, Bluesky, GitHub, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 threads | — | 🌐 HTTP 403 (API blocked for this domain) |
| X/Twitter | 2 posts | — | 🌐 Confirmed via web search aggregation; low direct access |
| Hacker News | 4 stories | 1,074+ points, 854+ comments | 🌐 Grok Build threads dominant |
| Bluesky | 0 new posts | — | 🌐 bluesky=OK per SOURCE HEALTH; no new high-engagement posts this window |
| GitHub | 3 repos | 68K+ stars (deer-flow), 844K lines (grok-build) | 🌐 xai-org/grok-build, bytedance/deer-flow, microsoft/skills |
| Web (global) | 35 pages | — | 🌐 via WebSearch + WebFetch supplemental |
| Web (Japan) | 10 pages | — | 🇯🇵 Qiita, Zenn, note.com, skywork.ai JP |
| Web (China) | 9 pages | — | 🇨🇳 Tencent Cloud, CSDN, Zhihu, news.qq.com, Baidu Developer |
| YouTube | 0 videos | — | Not scanned this pass |
| TikTok | 0 videos | — | No ScrapeCreators key |
| Instagram | 0 reels | — | No ScrapeCreators key |
| Polymarket | 0 markets | — | No prediction markets on agent harness topics |

---

## Synthesized Findings

### 1. [update] Grok Build: Privacy Scandal → Open-Sourced Under Apache 2.0 (July 15–16, 2026)

**New fact since prior briefing:** The prior briefing introduced Grok Build as an exciting new entrant with MCP compatibility. What happened between then and now overturned that narrative: xAI's CLI was caught uploading users' **entire Git repositories** — full commit history, committed secrets, .env files, SSH keys, and password manager databases — to a Google Cloud Storage bucket at a volume ~27,800× the data needed for any coding task. The upload ran regardless of whether users had disabled the "Improve the model" privacy toggle. Security researcher Cereblab published wire-level proof on Sunday; it hit HN's front page July 14 (537 pts, 229 comments). The top HN quote: "Your entire codebase leaves your machine unencrypted on each Grok Build invocation, not just files you ask it to read."

xAI's response: retention disabled by default July 12; Musk promised to delete all retained data; Grok Build open-sourced (Apache 2.0) and usage limits reset in the early hours of July 16. The codebase is now at [github.com/xai-org/grok-build](https://github.com/xai-org/grok-build) — 844,530 lines of Rust (only ~3% vendored). SpaceX stated: "Open-sourcing Grok Build allows anyone to support making a reliable and robust harness." HackerOne bug bounty offered ($100–$20,000 per severity). The open-source thread hit 625 comments, with simonw (577 pts) noting a self-contained Mermaid terminal renderer in the codebase, and kamikazechaser (527 pts): "The model is actually good...but it's a shame they exfiled private data." Eight forks emerged within hours.

Key technical finding: the tool implementations inside Grok Build were ported from Codex (apply_patch, grep_files, list_dir) and OpenCode (bash, edit, glob, grep, read, skill, todowrite, write), revealing that xAI built its harness layer by copying the tool layer from the top two open-source coding agents. The upload code remains in `gcs.rs` but is now disabled (hard-coded to return `session_state_upload_unavailable`). The repo was published as a single commit with no git history — itself a transparency criticism. Chinese mainstream tech media (news.qq.com, July 16) covered the scandal under the headline: "上传用户数据事件后，马斯克宣布开源Grok Build" ("After user data upload incident, Musk announces Grok Build open source").

Sources: [HN wire-level analysis](https://news.ycombinator.com/item?id=48877371), [HN open-source thread](https://news.ycombinator.com/item?id=48926590), [The Hacker News](https://thehackernews.com/2026/07/grok-build-uploads-entire-git.html), [The Register](https://www.theregister.com/ai-and-ml/2026/07/16/spacex-open-sources-grok-build-after-data-retention-furore/5272333), [Simon Willison](https://simonwillison.net/2026/Jul/15/grok-build/), [xai-org/grok-build GitHub](https://github.com/xai-org/grok-build), [xAI announcement](https://x.ai/news/grok-build-open-source), [news.qq.com CN coverage](https://news.qq.com/rain/a/20260716A02CZV00), [TechTimes](https://www.techtimes.com/articles/320671/20260716/grok-build-open-sourced-after-covert-upload-code-exfiltrate-repos-stays.htm), [MarktechPost technical analysis](https://www.marktechpost.com/2026/07/15/spacexai-open-sources-grok-build-the-rust-agent-harness-tui-and-tool-layer-behind-its-coding-cli/)

---

### 2. [new] MCP Specification RC 2026-07-28 — Protocol Goes Stateless (Biggest Change Since Launch)

**New fact:** The Model Context Protocol's release candidate for its July 28 final spec was published, and the headline change is architectural: **MCP is now stateless at the protocol layer**. The `initialize`/`initialized` handshake is gone. The `Mcp-Session-Id` header is gone. Any server instance can now handle any request. The practical result: MCP servers no longer require sticky session routing, shared session stores, or deep packet inspection — a standard round-robin load balancer with `Mcp-Method` header-based routing now suffices. This fundamentally changes how harnesses can deploy and scale MCP infrastructure.

The RC (locked May 21, final ships July 28) also introduces:

- **Extensions framework**: reverse-DNS identifiers, independent versioning, own SEP governance track — capabilities can stabilize outside the core spec before potential inclusion
- **MCP Apps**: servers can ship interactive HTML interfaces that hosts render in sandboxed iframes, declared upfront for prefetch and security review
- **Tasks as Extension**: redesigned stateless lifecycle using task handles; client drives with `tasks/get`, `tasks/update`, `tasks/cancel` — server returns `InputRequiredResult` for elicitation instead of SSE
- **Auth hardening**: six SEPs aligning with OAuth 2.1/OpenID Connect; mandatory `iss` parameter (RFC 9207); proper `application_type` declaration
- **Formal deprecation policy**: 12-month minimum window between deprecation and earliest removal (Roots, Sampling, Logging enter deprecation now)
- **Observability**: required `Mcp-Method` and `Mcp-Name` headers + W3C Trace Context in `_meta` → OpenTelemetry integration

Breaking changes for harness authors: remove `Mcp-Session-Id` header handling; eliminate `initialize`/`initialized` from server logic; migrate Tasks API; change error code `-32002` to `-32602`. State is now explicit: models thread handles between tool calls (visible to the agent, not hidden in transport).

This is the single largest change to the interoperability layer the whole harness ecosystem depends on. Every harness that supports MCP will need to update.

Sources: [Official MCP blog RC announcement](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/), [AAIF analysis](https://aaif.io/blog/mcp-is-growing-up/), [byteiota explanation](https://byteiota.com/mcp-goes-stateless-2026-release-candidate/), [chatforest builder guide](https://chatforest.com/builders-log/mcp-spec-2026-07-28-release-candidate-stateless-breaking-changes-builder-guide/), [WorkOS auth changes](https://workos.com/blog/mcp-2026-spec-agent-authentication), [MCP.Directory blog](https://mcp.directory/blog/mcp-2026-07-28-release-candidate), [TruFoundry gateway governance](https://www.truefoundry.com/blog/mcp-apps-tasks-gateway-governance)

---

### 3. [new] VS Code 1.129 — Agent Host Protocol: All Harnesses in One Process (July 15, 2026)

**New fact:** VS Code 1.129 (released July 15) introduces the **Agent Host** — a separate process running Copilot, Claude, and Codex simultaneously via the **Agent Host Protocol (AHP)**. Because a session lives in its own process, "one session can connect to and render across several VS Code windows at the same time." Users select their harness from a dropdown; administrators enable via `chat.agentHost.enabled`. This is the first time Microsoft has unified all three major agent harnesses (GitHub Copilot, Anthropic Claude, OpenAI Codex) under one shared execution architecture within the IDE.

The release also ships: redesigned Agents Window with editor panel + tab bar (reviewing agent work now feels like the main editor), `!` prefix for terminal commands in agent sessions, BYOK (Bring Your Own Key) model support under the Copilot harness, and Enterprise Copilot sign-in via GitHub Enterprise. The Agents Window state persists across window reloads (side-pane width, open editors, active editor, per-file collapsed state).

The Agent Host Protocol traces back to VS Code 1.121, when the boundary between "IDE window" and "agent session" first started moving. 1.129 completes the first phase of that architectural shift.

Sources: [Help Net Security](https://www.helpnetsecurity.com/2026/07/16/vs-visual-studio-code-agent-host/), [VS Code 1.129 release notes](https://code.visualstudio.com/updates/v1_129), [ntcompatible coverage](https://www.ntcompatible.com/story/visual-studio-code-1129-overhauls-ai-architecture-with-new-agent-host-and-redesigned-agents-panel/), [Antigravity Lab historical context](https://antigravitylab.net/en/articles/editor/vscode-1-121-agent-host-protocol-remote-agents)

---

### 4. [new] Claude Code: Dynamic Workflows GA + /checkup Rebuilt (July 2 + July 8, 2026)

**New fact (Dynamic Workflows GA, July 2):** Anthropic moved Dynamic Workflows to general availability on all paid plans, including Pro for the first time. Claude now dynamically writes its own orchestration scripts and coordinates **up to 1,000 parallel subagents per run**, checking results before they fold in. Cost note: each agent consumes tokens independently — a 10-agent run costs ~10× the tokens of a single-agent run; a full 24-hour parallel run at Opus 4.8 pricing runs ~$400–$600. Use cases: widespread bug investigation, large migrations, security audits, architecture analysis.

**New fact (/checkup rebuilt, July 8):** The `/doctor` skill was rebuilt and shipped with a new alias: `/checkup`. The key change is that it now **fixes, not just diagnoses** — it deduplicates local vs checked-in CLAUDE.md files, flags unused skills/MCP servers/plugins vs their context cost, identifies slow hooks, and proposes each change individually for user confirmation before applying anything. The prior `/doctor` was a read-only report; `/checkup` takes action on confirmation. Separate community tool: cc-health-check (github.com/yurukusa/cc-health-check) runs 20 checks across 6 dimensions with a 0–100 score.

Sources: [Claude.com Dynamic Workflows blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code), [Claude Code docs workflows](https://code.claude.com/docs/en/workflows), [TechTimes Dynamic Workflows GA](https://www.techtimes.com/articles/319532/20260702/claude-code-dynamic-workflows-go-ga-pro-users-can-now-spawn-1000-parallel-agents.htm), [Week 28 changelog](https://code.claude.com/docs/en/whats-new/2026-w28), [MCP.Directory /checkup analysis](https://mcp.directory/blog/claude-code-checkup-command-2026), [cc-health-check GitHub](https://github.com/yurukusa/cc-health-check)

---

### 5. [new] Agentjacking — New Attack Class Hits 2,388 Organizations (June 2026 Disclosure)

**New fact:** Tenet Threat Labs disclosed a new attack class in June 2026 called **"agentjacking"** that hijacks Claude Code, Cursor, OpenAI Codex, and other coding agents into running attacker-controlled commands on developer machines — with no phishing required, no malware to install, and no existing security tool capable of detecting it. The vector: fake Sentry error reports containing hidden markdown injection. The coding agent parses the text and treats the injected instruction as a legitimate debugging step, then executes attacker-controlled code. Machine speed execution means the attack completes before any human can intervene.

Scale: 2,388 organizations hit; 85% exploitation rate. The attack reached the front page of The Hacker News and Dark Reading. Legacy endpoint security tools fail because the malicious actions are initiated by authenticated, trusted applications (the harness itself) operating at machine speed. This is harness-as-attack-surface: the harness's willingness to act on instructions from any parsed text becomes the exploit primitive.

This is distinct from the Sophos "false positive" finding below — Agentjacking is about active exploitation, not accidental rule triggering.

Sources: [The Hacker News](https://thehackernews.com/2026/06/agentjacking-attack-tricks-ai-coding.html), [Infosecurity Magazine](https://www.infosecurity-magazine.com/news/agentjacking-attacks-hijack-ai/), [Enterprise DNA](https://enterprisedna.co/resources/news/agentjacking-attack-ai-coding-agents-sentry-mcp-2026/), [Cybersecurity News](https://cybernews.com/security/agentjacking-attack-hijacks-ai-coding-agent/), [CISO Guide](https://kersai.com/agentjacking-ai-security-threat-ciso-guide-2026/), [Dark Reading fake bug report](https://www.darkreading.com/cyber-risk/fake-bug-report-hijacks-ai-coding-agents), [shareuhack guide](https://www.shareuhack.com/en/posts/agentjacking-mcp-security-claude-code-guide-2026)

---

### 6. [new] Sophos: AI Agents Triggering Windows EDR Rules Built for Attackers (July 8, 2026)

**New fact:** Sophos published research showing Claude Code, Cursor, and Codex regularly trigger Windows endpoint security rules originally built to catch attackers — not because the agents are malicious, but because their legitimate behavior is behaviorally identical to attack patterns. From seven days of telemetry in June 2026:
- Credential access blocked = 56.2% of all blocked agent activity
- Execution blocked = 28.8%
- The dominant trigger: DPAPI (Windows Data Protection API) access at 42.6% of credential-access events — agents using browser automation on the user's behalf

The agents are not compromised. In context, DPAPI access is browser credential decryption for a legitimate task. But the rule can't distinguish the agent from an attacker using the same API. Sophos's fix: key the rule to the agent's parent process (claude.exe, cursor.exe) or workspace/temp path rather than the action alone.

Practical implication for teams running coding agents in enterprise environments: expect EDR false positives from the harness's legitimate operations. This is now a harness deployment engineering problem, not a security problem in the traditional sense.

Sources: [Sophos blog](https://www.sophos.com/en-us/blog/2607_agents_vs_telemetry), [The Hacker News](https://thehackernews.com/2026/07/ai-coding-agents-found-triggering.html), [TechNadu](https://www.technadu.com/ai-coding-agents-trigger-security-detection-says-sophos/630580/)

---

### 7. [new] Vercel skills.sh GA + Marketplace Economics Map (June 2026)

**New fact:** Vercel shipped skills.sh to general availability in June 2026 with **600,000 open-source skills**. Authentication uses Vercel OIDC, giving cross-agent portability (moderate lock-in via the auth layer). This makes skills.sh the largest skills marketplace by count, though the open MCP ecosystem (SkillsMP + Smithery + LobeHub + MCP Marketplace combined) indexes a comparable total.

The full five-platform landscape as of July 2026:
1. **Anthropic Claude Skills** — curated SKILL.md markdown bundles; strong Claude integration, no native billing for authors
2. **Vercel skills.sh** (GA June 2026) — 600K+ skills, OIDC auth, cross-agent portable
3. **OpenAI Codex plugins** — workspace-scoped, no public marketplace; enterprise/EDU workspaces inherited plugin libraries for new members (June 2026)
4. **Cline plugins (v3.0.16+)** — self-hosted GitHub bundles, minimal lock-in, discovery burden on users
5. **MCP ecosystem** (SkillsMP, Smithery, LobeHub, MCP Marketplace) — open protocol, zero vendor lock-in across any MCP-capable client

Economics note: only Vercel skills.sh and hosted MCP providers (Smithery) offer clear monetization paths for skill authors. Anthropic and OpenAI provide free distribution but no native billing infrastructure. New aggregator: [claudemarketplaces.com](https://claudemarketplaces.com/) launched as a third-party directory for Claude skills, MCP servers, and plugins.

Sources: [totalum.app marketplace comparison](https://www.totalum.app/blog/agent-skills-marketplaces-2026), [agensi.io marketplace landscape](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026), [remoteopenclaw.com state of marketplaces](https://www.remoteopenclaw.com/blog/state-of-ai-agent-marketplaces-2026), [claudemarketplaces.com](https://claudemarketplaces.com/), [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

---

### 8. [new] DeerFlow 2.0 (ByteDance) — 68K Stars, "Docker of AI Workers"

**New fact:** ByteDance's [DeerFlow 2.0](https://github.com/bytedance/deer-flow) hit #1 on GitHub Trending with 68K+ stars after its February 28, 2026 launch — a ground-up rewrite from v1 positioning itself as a "super agent harness": sub-agents, memory, sandboxes, skills, and a message gateway. Built on LangGraph and LangChain; each task gets its own execution environment with a full filesystem view. Unlike harnesses built around a single CLI, DeerFlow is framed as the orchestration layer for long-horizon tasks (minutes to hours), handling research, code generation, and content creation in a single run. A community fork with Chinese localization + new skills exists at github.com/stophobia/deerflow2.0-enhanced.

DeerFlow 2.0 is the first major super-harness from a major Chinese tech company (ByteDance) to achieve mainstream GitHub traction. It occupies the space between single-agent CLI harnesses and full orchestration platforms — closer to a batteries-included, opinionated runtime than a framework.

Sources: [bytedance/deer-flow GitHub](https://github.com/bytedance/deer-flow), [Medium: "Docker of AI Workers"](https://medium.com/data-science-in-your-pocket/bytedance-deerflow-2-0-docker-of-ai-workers-c866b4ff558f), [Flowtivity review](https://flowtivity.ai/blog/bytedance-deerflow-superagent-review/), [dev.to DeerFlow 2.0 guide](https://dev.to/arshtechpro/deerflow-20-what-it-is-how-it-works-and-why-developers-should-pay-attention-3ip3), [deerflow2.0-enhanced fork](https://github.com/stophobia/deerflow2.0-enhanced)

---

### 9. [new] Gemini CLI → Agent Skills: Google Deprecates Eager MCP Loading

**New fact:** Google is transitioning Gemini CLI from eager-loaded MCP tools to **Agent Skills** — solving the "Context Window Saturation" problem where traditional tool-based systems front-load every tool schema into the model's context window, crowding out reasoning capacity. Under the new model, skills activate only when needed and load their instructions progressively. The first deployment: Cloud SQL for PostgreSQL extension replaced its monolithic toolset with 7 specialized skills (admin, lifecycle, data, monitor, health, view-config, replication). MCP eager-loading within Gemini CLI extensions is now deprecated in favor of skill-based discovery.

The community has already bridged this: [gemini-cli-skillz](https://github.com/intellectronica/gemini-cli-skillz) is a Gemini CLI extension for Anthropic-style Agent Skills via a skills MCP server — enabling SKILL.md-format skills in Gemini CLI. This is the first confirmed cross-platform SKILL.md runtime bridge (Anthropic format → non-Anthropic harness).

Requires Gemini CLI v0.29.0+; skills auto-install in `~/.gemini/extensions/<extension_name>/skills`.

Sources: [Google Cloud Medium article](https://medium.com/google-cloud/your-gemini-cli-extensions-just-got-smarter-introducing-agent-skills-a8fbfa077e7f), [gemini-cli-skillz GitHub](https://github.com/intellectronica/gemini-cli-skillz), [Gemini API docs](https://ai.google.dev/gemini-api/docs/coding-agents), [damimartinez deep dive](https://damimartinez.github.io/agent-skills-gemini-cli/), [danicat.dev mastering skills](https://danicat.dev/posts/agent-skills-gemini-cli/)

---

### 10. [new] Anthropic 2026 Agentic Coding Trends Report — $2.5B ARR, Delegation Gap

**New fact:** Anthropic published its 2026 Agentic Coding Trends Report with industry benchmarks. Key data points:
- Claude Code is at **$2.5B ARR**
- Developers use AI in **60% of their work** — but can "fully delegate" only **0–20% of tasks**
- Teams with well-maintained context files (CLAUDE.md etc.): **40% fewer errors**, **55% faster** task completion
- The report identifies **eight trends** reshaping software development: multi-agent coordination, long-running agents (task horizons: minutes → days/weeks), role transformation (engineer as orchestrator, not coder), context engineering as the key skill, human-AI collaboration patterns, scaling beyond engineering teams
- Case studies from Rakuten, CRED, TELUS, Zapier

The "delegation gap" (using AI for 60% of tasks but fully delegating only 0-20%) is the key new data point — it quantifies the harness engineering problem: the bottleneck is not model capability but harness design that makes delegation reliable and safe.

Sources: [Anthropic report landing page](https://resources.anthropic.com/2026-agentic-coding-trends-report), [PDF](https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf), [AgentMarketCap summary](https://agentmarketcap.ai/blog/2026/04/05/anthropic-agentic-coding-trends-report-claude-code-eight-shifts), [Pathmode analysis](https://pathmode.io/blog/orchestration-era-needs-intent), [Hivetrail analysis](https://hivetrail.com/blog/anthropic-2026-agentic-coding-report/)

---

### 11. [new] Zot — Show HN Go-Native Coding Agent Harness

**New fact:** A Show HN post introduced **Zot**, a coding agent harness written in Go: multi-model (Claude including Opus, OpenAI, Kimi, GitHub Copilot), single binary with no TypeScript dependencies, extensible with custom skills, built-in email access and web browsing. Top comment (107 pts): "3-5x better productivity for research tasks, handled Gmail integration and web browsing efficiently in 15 seconds." The harness was built, in the author's words, "to really get a feel for how harnesses work" rather than to compete directly with Pi, though it's positioned as the Go developer's alternative to TypeScript-heavy incumbents.

Zot is the first coded-in-Go coding agent harness to surface in the HN community. Its MCP compatibility and single-binary deployment model address a real deployment friction point for teams that run Go infrastructure.

Sources: [HN Show HN: Zot](https://news.ycombinator.com/item?id=48319524)

---

### 12. [new] Microsoft ships 175+ Skills + AGENTS.md Standard (microsoft/skills)

**New fact:** Microsoft shipped [microsoft/skills](https://github.com/microsoft/skills) — 175+ domain-specific skill packages for AI coding agents working with Azure SDKs, covering Python (39), TypeScript (25), .NET (29), Java (26), Rust (7), Core (11), and Foundry (11). Each skill is validated against 1,169 test scenarios using the Ralph Loop acceptance criteria system. The repository also standardizes **AGENTS.md** — a template for role-specific agent personas (backend, frontend, infrastructure, planner) — as a complement to Anthropic's CLAUDE.md. Microsoft's positioning: skills are "user guides" for agents, not instructions; the harness determines which skill fires. MCP servers included: Microsoft Docs, DeepWiki, GitHub, Playwright, Terraform, and utilities.

This is the most comprehensive public skills release from a major tech company by skill count, and the first to run validated test scenarios (1,169) against each skill before shipping.

Sources: [microsoft/skills GitHub](https://github.com/microsoft/skills)

---

### 13. [update] 🇯🇵 Zenn Publishes 17-Layer Harness Taxonomy + Meta-Harness Canon

**New fact since prior briefing:** Two significant Zenn articles appeared beyond the July 14-15 corpus:

**aiwatch_jp "Build Your Own Harness" (June 3)**: The era of picking a single framework winner has ended; builders now assemble harnesses layer-by-layer across 17 specialized layers (coding agent engines, orchestration, multi-agent frameworks, computer vision, browser automation, memory systems, tool connectors, sandboxing, evaluation, observability, skills, no-code builders, and more). The author validated ~100 repositories for active maintenance and flagged 7 owner migrations (including opencode→anomalyco) and 1 archived project. Key advice: "Verify repository health via `gh api` before adopting." — [Zenn aiwatch_jp](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained)

**genda_jp / Kento Nishio "Meta-Harness" (June 18)**: First JP article to formally define the meta-harness tier. Hierarchy: Model → Harness → Meta-Harness. Compares Omnigent (cross-harness interoperability), Claude Squad (parallel multi-agent, AGPL 3.0), Conductor (deterministic workflow), Vibe Kanban (deprecated), and Microsoft Agent Framework. Omnigent's YAML config enables harness swapping without code changes. — [Zenn genda_jp](https://zenn.dev/genda_jp/articles/60af4b2aa074ce)

Also new: Qiita @singula series articles 7-8 on MCP "tool box" design pattern (Single Responsibility Principle applied to MCP server splitting) and FastMCP minimum implementation. Note.com/surprise_byai: "MCP Complete Mastery 2026" with "AI's USB-C" framing for MCP cross-platform connectivity.

Sources: [Zenn aiwatch_jp](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained), [Zenn genda_jp](https://zenn.dev/genda_jp/articles/60af4b2aa074ce), [Qiita singula article 7](https://qiita.com/singula/items/8c7fb7a8dd26cdbb57e8), [Qiita singula article 8](https://qiita.com/singula/items/0a2b82647176ec2a02d9), [note.com/kawauso9n](https://note.com/kawauso9n/n/nb05e9bf6cfeb), [note.com/surprise_byai](https://note.com/surprise_byai/n/n992eff5a73fb)

---

### 14. [update] 🇨🇳 Grok Build Scandal in CN Media; Tencent MCP+OpenClaw 10x Claim

**New fact since prior briefing:** news.qq.com (Tencent's main news portal) covered the Grok Build data scandal on July 16, headlining "上传用户数据事件后，马斯克宣布开源Grok Build编程AI智能体" — confirming the trust crisis reached Chinese mainstream tech media. This is notable because Grok Build had previously been discussed positively in CN developer forums as an MCP-compatible newcomer.

Second new fact: Tencent Cloud Developer published "2026 Agent Development New Paradigm: MCP Protocol + OpenClaw Restructures Tool Ecosystem, 10x Integration Efficiency" — framing the combination of MCP + OpenClaw as a solution to the 80% dev effort wasted on manual tool integration. Tagged with Hermes Agent, signaling continued interest in the Hermes harness stack in CN enterprise contexts.

Sources: [news.qq.com](https://news.qq.com/rain/a/20260716A02CZV00), [Tencent Cloud MCP+OpenClaw article](https://cloud.tencent.com/developer/article/2696664), [Tencent Cloud MCP Python article](https://developer.cloud.tencent.com/article/2707597)

---

**Still true** (ongoing from July 15 briefing — no new facts this window):
- #1 SKILL.md standard at ~40 harnesses, ~1.9M community skills (agentskills.io)
- #2 OpenCode at ~186K stars (anomalyco/opencode), dominant open-source coding agent
- #3 Mozilla Otari — OpenAI-compatible LLM control plane, OpenCode integration guide
- #4 Pricing crisis: 60x cost gap ($0.07/task Cursor vs $4.10-$4.82 competitors); enterprise Claude Code cancellations at $500-2,000/mo/engineer
- #5 Warp Oz: multi-harness control plane running Claude Code + Codex + Warp Agent side-by-side
- #6 Google Antigravity 2.0: desktop app + CLI + SDK, Gemini 3.5 Flash, competing with Cursor
- #7 AutoHarness (aiming-lab, v0.1.0): governance framework, 6-step pipeline, "Agent = Model + Harness. The model reasons. The harness does everything else."
- #8 Awesome lists: revfactory/harness (meta-skill generating domain-specific agent teams), bishopZ/2026-agent-harness, bradAGI/awesome-cli-coding-agents
- #9 ZeroClaw (zeroclaw-labs) ~32K stars, nanobot (HKUDS) ~46K stars
- #10 OpenClaw Bazaar 2,300+ listings; 8 active skill marketplaces competing on curation and economics
- #11 Agent-to-agent infrastructure: Roomcomm (ephemeral REST chatrooms for cross-stack agent comms) and on-chain agent credit scores (ERC-4337 smart accounts)
- #12 Harness CI/CD (harness.io) Autonomous Worker Agents (June 30)
- #13 MemFlywheel (iflytek/memflywheel) file-native memory layer for Pi and OpenCode
- #14 Meta-harnesses: Omnigent (Databricks/Apache 2.0), Minotauris (Leader/Manager/Worker/Assembly)
- #15 JP "The model is not the bottleneck. The harness is the architecture." canon (note.com/atsu_pipi, qiita.com/Ryu-Yanagi, ai-native.jp)
- #16 CN "智能体选型" (agent framework selection guide) genre established; ZeroClaw/OpenClaw/Nanobot "Claw family" known in CN dev community
- #17 Microsoft Agent Framework 1.0 GA; CodeAct (52.4% latency reduction)

---

## Cross-Source Patterns

### Pattern 1: Trust Destruction as the New Harness Adoption Criterion 🌐
Appearing on: HN (625 + 537 + 229 comments), CN mainstream media (news.qq.com), The Register, Simon Willison, GIGAZINE

Grok Build's upload scandal crystallized a new harness selection criterion beyond capability and cost: **trust and transparency**. The harness has filesystem and network access to the most sensitive parts of a developer's machine. When that access is abused (intentionally or not), the consequences are catastrophic — SSH keys, password databases, complete commit histories including secrets. The fact that xAI's privacy toggle did nothing and the harness uploaded 27,800× more data than needed for any task makes this the harness equivalent of a supply-chain breach. The response (open-sourcing under Apache 2.0) is itself a precedent: forced transparency through open-sourcing as trust repair. This will drive more teams toward locally-compiled, fully auditable harnesses (now possible with xai-org/grok-build).

### Pattern 2: MCP Protocol Maturation as Harness Infrastructure Prerequisite 🌐🇯🇵🇨🇳
Appearing on: MCP.io blog, AAIF, Tencent Cloud (🇨🇳), Qiita @singula (🇯🇵), note.com (🇯🇵), WorkOS, byteiota

The MCP 2026-07-28 RC is the single largest change to the cross-harness interoperability layer since MCP launched. Simultaneously: Gemini CLI is deprecating eager MCP loading in favor of Agent Skills (solving Context Window Saturation), JP developers are publishing serialized MCP design guides (Qiita @singula "tool box" series), and CN cloud providers (Tencent, AWS China) are publishing enterprise MCP deployment guides. MCP's maturation is no longer a niche concern — it's now a mainstream engineering topic across all three regions.

### Pattern 3: Security Surface Expansion — Harnesses as Attack Vectors 🌐
Appearing on: HN (Grok Build threads), The Hacker News, Infosecurity Magazine, Sophos, Dark Reading

Three distinct security incidents emerged in rapid succession: (a) Grok Build's covert repository exfiltration, (b) Agentjacking via fake Sentry reports, (c) Sophos finding that legitimate agent behavior triggers EDR rules built for attackers. These are three different attack surfaces — data exfiltration by the harness itself, external injection into harness execution, and false positive noise that exhausts security teams. The commonality: the harness's permissions model (filesystem + network + tool execution) is now the primary attack surface in enterprise developer environments.

### Pattern 4: Eager Loading vs. Lazy Skills — Convergence Across Harnesses 🌐🇯🇵
Appearing on: Gemini CLI blog, Qiita @singula, note.com MCP mastery, totalum.app marketplace comparison

Gemini CLI explicitly deprecated eager-loaded MCP in favor of lazy-loading Agent Skills. Claude Code's `/checkup` now flags unused skills/MCP servers vs their context cost. The Qiita @singula series teaches MCP splitting as the default design pattern. The convergence: every major harness is discovering that giving the agent fewer tools upfront (not more) produces better outcomes — and the skills/lazy-load pattern is the implementation mechanism. This is likely to affect MCP server design patterns broadly.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Grok Build is open source | — | 625 | "The model is actually good...but it's a shame they exfiled private data." (kamikazechaser, 527 pts) | https://news.ycombinator.com/item?id=48926590 |
| — | What xAI's Grok Build CLI sends to xAI: A wire-level analysis | 537 | 229 | "Your entire codebase leaves your machine unencrypted on each Grok Build invocation" | https://news.ycombinator.com/item?id=48877371 |
| — | xAI's Grok Build CLI Uploads Git Repositories to a Google Cloud Bucket | — | — | "5.10 GB uploaded in 73 chunks regardless of privacy toggle" | https://news.ycombinator.com/item?id=48896493 |
| — | Show HN: Zot – Yet another coding agent harness | — | 107+ | "3-5x better productivity for research tasks...in 15 seconds maybe" | https://news.ycombinator.com/item?id=48319524 |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @xAI | Grok Build is Now Open Source — reset usage limits, Apache 2.0, full codebase | — | — | https://x.ai/news/grok-build-open-source |

**GitHub:**
| Repo | Stars | Issues | Description | URL |
|------|-------|--------|-------------|-----|
| xai-org/grok-build | — (new) | — | Rust coding agent CLI, open-sourced July 15-16, 844K lines | https://github.com/xai-org/grok-build |
| bytedance/deer-flow | 68K+ | — | Super agent harness; sub-agents, memory, sandbox, skills, message gateway | https://github.com/bytedance/deer-flow |
| microsoft/skills | — | — | 175+ Azure SDK skills + AGENTS.md standard + 1,169 test scenarios | https://github.com/microsoft/skills |
| intellectronica/gemini-cli-skillz | — | — | Gemini CLI extension for Anthropic-style Agent Skills | https://github.com/intellectronica/gemini-cli-skillz |
| yurukusa/cc-health-check | — | — | Free CLI diagnostic for Claude Code setup, 20 checks, 0-100 score | https://github.com/yurukusa/cc-health-check |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | MCP RC 2026-07-28: stateless core, Extensions, MCP Apps, Tasks |
| 🌐 | AAIF | https://aaif.io/blog/mcp-is-growing-up/ | MCP ecosystem maturation analysis |
| 🌐 | byteiota | https://byteiota.com/mcp-goes-stateless-2026-release-candidate/ | MCP stateless explained for server authors |
| 🌐 | chatforest | https://chatforest.com/builders-log/mcp-spec-2026-07-28-release-candidate-stateless-breaking-changes-builder-guide/ | Six breaking changes + migration guide |
| 🌐 | WorkOS | https://workos.com/blog/mcp-2026-spec-agent-authentication | Auth hardening in MCP 2026-07-28 |
| 🌐 | helpnetsecurity | https://www.helpnetsecurity.com/2026/07/16/vs-visual-studio-code-agent-host/ | VS Code 1.129 Agent Host Protocol |
| 🌐 | code.visualstudio.com | https://code.visualstudio.com/updates/v1_129 | VS Code 1.129 official release notes |
| 🌐 | simonwillison.net | https://simonwillison.net/2026/Jul/15/grok-build/ | Grok Build open-source analysis: Mermaid renderer, tool porting from Codex/OpenCode |
| 🌐 | The Register | https://www.theregister.com/ai-and-ml/2026/07/16/spacex-open-sources-grok-build-after-data-retention-furore/5272333 | Grok Build open-source: single commit, no git history; GCS code still in repo |
| 🌐 | thehackernews.com | https://thehackernews.com/2026/07/grok-build-uploads-entire-git.html | Wire-level: 5.10 GB, 27,800× excess, .env files, SSH keys |
| 🌐 | thehackernews.com | https://thehackernews.com/2026/06/agentjacking-attack-tricks-ai-coding.html | Agentjacking: fake Sentry reports, 2,388 orgs, 85% exploitation rate |
| 🌐 | infosecurity-magazine.com | https://www.infosecurity-magazine.com/news/agentjacking-attacks-hijack-ai/ | Agentjacking new attack class disclosure |
| 🌐 | sophos.com | https://www.sophos.com/en-us/blog/2607_agents_vs_telemetry | Agents triggering EDR: DPAPI, credential access 56.2%, execution 28.8% |
| 🌐 | claude.com | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Claude Code Dynamic Workflows GA |
| 🌐 | code.claude.com | https://code.claude.com/docs/en/whats-new/2026-w28 | Week 28 changelog: /checkup rebuilt |
| 🌐 | resources.anthropic.com | https://resources.anthropic.com/2026-agentic-coding-trends-report | Anthropic 2026 Agentic Coding Trends Report |
| 🌐 | Google Cloud Medium | https://medium.com/google-cloud/your-gemini-cli-extensions-just-got-smarter-introducing-agent-skills-a8fbfa077e7f | Gemini CLI Agent Skills: eager MCP deprecated |
| 🌐 | totalum.app | https://www.totalum.app/blog/agent-skills-marketplaces-2026 | Five-platform marketplace economics map |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | New Claude skills/MCP marketplace directory |
| 🌐 | agensi.io | https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 | AI agent marketplace landscape 2026 |
| 🌐 | remoteopenclaw.com | https://www.remoteopenclaw.com/blog/state-of-ai-agent-marketplaces-2026 | State of AI agent marketplaces 2026 |
| 🌐 | github.com/bytedance/deer-flow | https://github.com/bytedance/deer-flow | DeerFlow 2.0: 68K+ stars, ByteDance super-harness |
| 🌐 | dev.to DeerFlow | https://dev.to/arshtechpro/deerflow-20-what-it-is-how-it-works-and-why-developers-should-pay-attention-3ip3 | DeerFlow 2.0 deep dive |
| 🌐 | medium.com DeerFlow | https://medium.com/data-science-in-your-pocket/bytedance-deerflow-2-0-docker-of-ai-workers-c866b4ff558f | "Docker of AI Workers" framing |
| 🌐 | marktechpost.com | https://www.marktechpost.com/2026/07/15/spacexai-open-sources-grok-build-the-rust-agent-harness-tui-and-tool-layer-behind-its-coding-cli/ | Grok Build architecture: TUI, tool layer breakdown |
| 🌐 | agentmarketcap.ai | https://agentmarketcap.ai/blog/2026/04/05/anthropic-agentic-coding-trends-report-claude-code-eight-shifts | Anthropic report summary: $2.5B ARR, 8 shifts |
| 🌐 | mcp.directory | https://mcp.directory/blog/claude-code-checkup-command-2026 | Claude Code /checkup explained |
| 🌐 | InfoQ | https://www.infoq.com/podcasts/mcp-vibe-coding-harness-engineering/ | Podcast: MCP/vibe coding/harness engineering evolution |
| 🌐 | arxiv | https://arxiv.org/pdf/2607.05518 | aiAuthZ paper: off-host, identity-bound authorization for AI agents |
| 🌐 | arxiv | https://arxiv.org/html/2605.18747v1 | "Code as Agent Harness" paper |
| 🌐 | hyperfx.ai | https://www.hyperfx.ai/blog/best-marketing-skills-mcps-and-clis-for-ai-agents-2026 | Best marketing skills/MCPs for Claude Code, Codex, Hermes, OpenClaw |
| 🇯🇵 | Zenn aiwatch_jp | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | 17-layer harness taxonomy; era of single-framework picking is over |
| 🇯🇵 | Zenn genda_jp | https://zenn.dev/genda_jp/articles/60af4b2aa074ce | Meta-harness concept: Model→Harness→Meta-Harness hierarchy |
| 🇯🇵 | Qiita singula article 7 | https://qiita.com/singula/items/8c7fb7a8dd26cdbb57e8 | MCP as "tool box": Single Responsibility design for MCP servers |
| 🇯🇵 | Qiita singula article 8 | https://qiita.com/singula/items/0a2b82647176ec2a02d9 | FastMCP minimum implementation |
| 🇯🇵 | note.com/kawauso9n | https://note.com/kawauso9n/n/nb05e9bf6cfeb | "The days of just asking AI nicely are over" — harness engineering paradigm intro |
| 🇯🇵 | note.com/surprise_byai | https://note.com/surprise_byai/n/n992eff5a73fb | "AI's USB-C" — MCP as universal cross-platform connector |
| 🇯🇵 | Zenn watany | https://zenn.dev/watany/articles/d8b692bbca65a3 | Confusion and views around the AI agent "harness" concept |
| 🇯🇵 | Qiita hoge_kawamuro | https://qiita.com/hoge_kawamuro/items/b810f32a2f5d67ed9037 | Harness design for agent-resistant development |
| 🇨🇳 | Tencent Cloud (2696664) | https://cloud.tencent.com/developer/article/2696664 | MCP+OpenClaw new paradigm: 10x efficiency, 80% dev effort currently wasted |
| 🇨🇳 | Tencent Cloud (2707597) | https://developer.cloud.tencent.com/article/2707597 | From conversation to execution: MCP + Python AI Agent OS |
| 🇨🇳 | news.qq.com | https://news.qq.com/rain/a/20260716A02CZV00 | Grok Build data upload scandal + open-source in CN mainstream media |
| 🇨🇳 | CSDN devpress | https://devpress.csdn.net/v1/article/detail/162696573 | Six major AI tech trends 2026: AI Agent + MCP |
| 🇨🇳 | Zhihu framework guide | https://zhuanlan.zhihu.com/p/2012136033752470384 | "智能体选型" genre: 5-framework comparison |
| 🇨🇳 | CSDN ZeroClaw | https://blog.csdn.net/bhl120/article/details/158125047 | Claw family comparison |
| 🇨🇳 | AWS China MCP | https://aws.amazon.com/cn/blogs/china/agentic-ai-infrastructure-practice-experience-series-four-mcp-server-from-local/ | Enterprise MCP deployment guide |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ HTTP 403 block
├─ 🔵 X: 2 posts │ — likes │ — reposts
├─ 🟢 HN: 4 stories │ 537+ points │ 854+ comments
├─ 🦋 Bluesky: 0 new posts │ bluesky=OK (no new high-engagement posts this window)
├─ 🐙 GitHub: 5 repos (new/confirmed) │ xai-org/grok-build, bytedance/deer-flow (68K+), microsoft/skills, gemini-cli-skillz, cc-health-check
├─ 🌐 Web: 31 pages │ 🇯🇵 10 │ 🇨🇳 9
└─ 🗣️ Top voices: @simonw (HN 577pts on Grok Build), kamikazechaser (HN 527pts), @kordlessagain (HN) │ Tenet Threat Labs (Agentjacking), Sophos (EDR collision)
```

---

## Out of Scope but Notable

- **aiAuthZ: Off-Host, Identity-Bound Authorization for AI Agents** (arxiv.org, July 2026) — proposes moving agent authorization decisions off the agent/harness itself to an external identity-bound service. Architecture: agents get short-lived capability tokens bound to their identity, not their trust level. This is a new paradigm for agent permission governance that doesn't fit the harness-centric model. [arxiv.org/pdf/2607.05518](https://arxiv.org/pdf/2607.05518) — worth watching for ai-software-factory topic.

- **Code as Agent Harness (arxiv paper)** — "Toward Executable, Verifiable, and Stateful Agent Systems" — proposes treating executable code itself as the harness runtime rather than wrapping LLMs in traditional orchestration layers. Challenges the current harness-as-wrapper architectural assumption. [arxiv.org/html/2605.18747v1](https://arxiv.org/html/2605.18747v1)

- **DeerFlow 2.0 "Docker of AI Workers" framing** — ByteDance positioning DeerFlow not as a coding harness but as a general-purpose task execution runtime. If this framing catches on, it might signal the emergence of a "compute harness" tier above "coding harness." Belongs in ai-software-factory territory but the architecture is distinctive enough to note.

---

## Data Gaps

- **Reddit: HTTP 403** (API blocked for this domain per error message). r/AI_Agents, r/ClaudeAI, r/LocalLLaMA discussions unavailable — material gap, these communities drive some of the harness discovery signal.
- **Bluesky: No new posts found** this window beyond the July 14-15 corpus. bluesky=OK per SOURCE HEALTH; the topic simply had low Bluesky engagement in the July 15-17 window.
- **YouTube: 0 results** — tutorial content on Grok Build open-source, Dynamic Workflows GA, and VS Code 1.129 almost certainly exists but not retrieved in this pass.
- **ScrapeCreators not configured**: TikTok (0), Instagram (0) excluded.
- **Polymarket: 0 markets** — no prediction markets on harness topics.
- **HN "Automation Without Understanding" (#48882554)**: 429 error on direct fetch; confirmed in search but no content extracted.
- **Vercel skills.sh** details: only via secondary analysis (totalum.app comparison); Vercel's own announcement post not directly fetched.
- **CN pages**: Zhihu deep analysis page (HTTP 403), several CSDN pages limited to snippets. DuckDuckGo snippets used as fallback for some CN sources.
- **Coverage estimate: ~72%** — strong on the week's breaking news (Grok Build, MCP RC, VS Code 1.129); solid HN/web/JP/CN; gaps from Reddit block, zero YouTube/TikTok/Instagram, and several blocked CN pages.

---

## Key Quotes

> "Your entire codebase leaves your machine unencrypted on each Grok Build invocation, not just files you ask it to read." — @kordlessagain on [HN wire-level analysis](https://news.ycombinator.com/item?id=48877371) 🌐

> "The model is actually good...but it's a shame they exfiled private data." — @kamikazechaser (527 pts) on [HN Grok Build open-source thread](https://news.ycombinator.com/item?id=48926590) 🌐

> "Open-sourcing Grok Build allows anyone to support making a reliable and robust harness." — SpaceX, [xAI announcement](https://x.ai/news/grok-build-open-source) 🌐

> "A remote MCP server that previously needed sticky sessions, a shared session store, and deep packet inspection at the gateway can now run behind a plain round-robin load balancer." — [MCP RC 2026-07-28 official blog](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) 🌐

> "Teams with well-maintained context files see 40% fewer errors and complete tasks 55% faster than those without." — [Anthropic 2026 Agentic Coding Trends Report](https://resources.anthropic.com/2026-agentic-coding-trends-report) 🌐

> "The era of picking a single framework winner has ended; now builders assemble harnesses layer-by-layer." (「単一フレームワークの勝者を選ぶ時代は終わり、harnessをレイヤーごとに組む時代になった」) — @aiwatch_jp on [Zenn](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained) 🇯🇵

> "AIへの'お願い'はもう限界？" ("The days of just asking AI nicely are over?") — @kawauso9n on [note.com](https://note.com/kawauso9n/n/nb05e9bf6cfeb) 🇯🇵

> "Agentjacking hit 2,388 organizations with an 85% exploitation rate by targeting AI coding agents with fake Sentry error reports." — [Infosecurity Magazine](https://www.infosecurity-magazine.com/news/agentjacking-attacks-hijack-ai/) 🌐

> "上传用户数据事件后，马斯克宣布开源Grok Build编程AI智能体" ("After user data upload incident, Musk announces open-sourcing Grok Build programming AI agent") — [news.qq.com](https://news.qq.com/rain/a/20260716A02CZV00) 🇨🇳

> "MCP分割は、SEの「責務分離」の経験がそのまま使える" ("MCP division directly applies software engineers' existing module separation experience") — @singula on [Qiita](https://qiita.com/singula/items/8c7fb7a8dd26cdbb57e8) 🇯🇵
