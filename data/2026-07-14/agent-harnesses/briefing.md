# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-07-14
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 11 threads | 313 upvotes, 79 comments | 🌐 Partial — HTTP 403 after 11 items; r/LocalLLaMA, r/github |
| X/Twitter | 49 posts | 542 likes, 54 reposts | 🌐 Bird auth active |
| Hacker News | 23 stories | 1,541 points, 1,152 comments | 🌐 |
| Bluesky | 11 posts | 32 likes, 3 reposts | 🌐 |
| GitHub | 3 repos | 189,346 stars, 4,750 issues | 🌐 anomalyco/opencode, opensoft/oh-my-opencode, microsoft/skills |
| Web (global) | 18 pages | — | 🌐 via WebSearch + supplemental fetches |
| Web (Japan) | 8 pages | — | 🇯🇵 Zenn, Qiita, note, claudelab.jp |
| Web (China) | 10 pages | — | 🇨🇳 CSDN, Juejin, Zhihu, Tencent Cloud Developer, Jishuzhan |
| YouTube | 0 videos | — | ScrapeCreators 402 billing error |
| TikTok | 0 videos | — | ScrapeCreators 402 billing error |
| Instagram | 0 reels | — | ScrapeCreators 402 billing error |
| LinkedIn | 0 posts | — | ScrapeCreators 402 billing error |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard Has Reached Critical Mass — ~40 Harnesses, 1.9M Community Skills

The Agent Skills open standard (agentskills.io), originally authored by Anthropic and steered by the Agentic AI Foundation, has crossed a critical adoption threshold: roughly 40 coding agent and harness products now read identical SKILL.md folders on the same path convention. The official client showcase includes not just the known incumbents (Claude Code, OpenAI Codex, Cursor, GitHub Copilot, VS Code) but a wave of newer and independent harnesses: **ZeroClaw** (Rust-native, provider-agnostic), **Autohand Code CLI** (ReAct-pattern terminal agent), **Mux** (parallel multi-agent, browser-based), **Amp** (frontier coding agent), **Letta** (stateful/memory-first), **Firebender** (Android-native coding), **Piebald** (desktop/web agentic dev), **Ona** (background cloud agents), **VT Code** (open-source, LLM-failover), **Qodo** (code integrity), **Laravel Boost** (framework-specific), **Emdash** (parallel worktree agents over SSH), **nanobot** (multi-channel personal agent — Telegram, Discord, Slack, WeChat), **fast-agent** (MCP-first, eval-friendly), **bub** (hook-first Python, channel-native), **TRAE** (ByteDance's adaptive AI IDE), **Deep Code** (DeepSeek-powered terminal), **Pulumi Neo** (cloud infra agent), **Superconductor** (multiplayer agent workspace), **Command Code** (taste-learning coding agent), **Workshop** (cross-platform, multi-LLM), **Mistral Vibe** (Mistral CLI), **Spring AI** (enterprise Java), **Databricks Genie Code**, **Snowflake Cortex Code**, **Roo Code**, **Tabnine**, **Vita** (desktop automation), **Google AI Edge Gallery** (on-device), and **Agentman** (healthcare). Community directories now index enormous catalogs — SkillsMP alone lists about 1.9 million public skills scraped from GitHub. Vercel's skills.sh and Agensi independently index tens of thousands.

Sources: [agentskills.io](https://agentskills.io/home), [Agensi skills browse](https://www.agensi.io/skills), [Medium/@sharanharsoor](https://medium.com/@sharanharsoor/agent-skills-the-quiet-standard-thats-changing-how-we-build-ai-agents-53118b633401), [Codex knowledge base](https://codex.danielvaughan.com/2026/03/27/codex-cli-skills-ecosystem/)

> **Key insight:** "Build a skill once and use it across any skills-compatible agent" is the promise that's materializing. The standard's progressive-disclosure design (name+description loaded at startup; full SKILL.md loaded only when relevant) keeps context cost low at scale.

### 2. OpenCode Hits 186K Stars — Extension Ecosystem Exploding Around It

OpenCode (anomalyco/opencode, formerly SST) remains the dominant open-source coding agent at **186K GitHub stars** with 4,690 open issues and 1.68M weekly npm downloads. Its v1.17.20 release (July 13) removed an obsolete Codex workaround and updated Azure AI support for GPT-5.6 — routine maintenance signals a mature codebase. The real action is in the extension layer. **oh-my-opencode** (opensoft/oh-my-opencode) is the leading harness extension, offering async subagents (described as "YES LIKE CLAUDE CODE"), a curated agent roster with proper model assignments, LSP/AST tools, curated MCPs, and a Claude Code compatible layer. The project's update channel moved to [@justsisyphus](https://x.com/justsisyphus) after the original X account was suspended. A parallel **oh-my-openagent** (code-yeongyu) targets "tokenmaxxers" working with complex codebases. The **opencode-memory** MCP server on [MCP Market](https://mcpmarket.com/server/opencode-memory) provides local RAG for persistent agent memory across sessions.

Sources: [anomalyco/opencode](https://github.com/anomalyco/opencode), [opensoft/oh-my-opencode](https://github.com/opensoft/oh-my-opencode), [oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent), [MCP Market opencode-memory](https://mcpmarket.com/server/opencode-memory)

### 3. Microsoft Agent Framework 1.0 GA — "Agent Harness" as a Named Production Pattern

Microsoft officially released **Microsoft Agent Framework 1.0** on April 2, 2026 (unifying AutoGen and Semantic Kernel), then unveiled its **Agent Harness** primitive at BUILD 2026. The Harness provides: automatic context compaction preventing window overflow during extended tool chains, built-in providers for file memory, file access, task tracking, skill discovery, and parallel agent delegation, plus middleware for approval workflows, OpenTelemetry tracing, and pluggable storage backends. Two companion features shipped: **Hosted Agents** (scale-to-zero Foundry deployment, per-session VM isolation, built-in Application Insights) and **CodeAct** (consolidates multiple tool calls into a single model-generated Python program running in Hyperlight micro-VMs — benchmarked at **52.4% latency reduction** and **63.9% token usage decrease**). GitHub Copilot SDK and the Handoff multi-agent orchestration pattern also hit GA. A Bluesky post from @neciudan.dev (July 13) flagged Microsoft's Maxim Salnikov on "AI harnesses, agent ops, and what truly AI native dev teams do differently" as a must-watch conversation: ["New Señors at Scale" YouTube talk](https://bsky.app/profile/neciudan.dev/post/3mqj6br4s2q2k).

Sources: [Microsoft Agent Framework BUILD 2026](https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/), [Bluesky @neciudan.dev](https://bsky.app/profile/neciudan.dev/post/3mqj6br4s2q2k)

### 4. ZeroClaw — Rust-Native Agent Runtime Emerging as Lightweight Alternative

**ZeroClaw** (zeroclaw-labs/zeroclaw), created February 2026, is building a distinct niche: a 100% Rust agent runtime targeting zero overhead — single static binary, <5MB memory, <10ms startup, runnable on ~$10 hardware. Supports 28+ model providers (Anthropic, OpenAI, Ollama, any OpenAI-compatible endpoint), multi-channel agent loops (Discord, Telegram, Matrix, email, webhooks, CLI all feeding the same agent), and full SKILL.md compatibility. The project appears in the official agentskills.io client showcase. Phase 0 (agent eval harness with deterministic replay-driven evaluation) landed as the foundation for its eval story.

Sources: [zeroclaw-labs/zeroclaw](https://github.com/zeroclaw-labs/zeroclaw), [ZeroClaw.net](https://zeroclaw.net/), [DEV Community ZeroClaw](https://dev.to/lightningdev123/zeroclaw-a-minimal-rust-based-ai-agent-framework-for-self-hosted-systems-5593), [agentskills.io client showcase](https://agentskills.io/home)

### 5. New Class of "Meta-Harnesses" Emerging — Omnigent, Flue, Minotauris

Three distinct meta-harness plays appeared in June–July 2026:

**Omnigent** (Databricks, open-source, June 2026): a meta-harness that sits above existing tools (Claude Code, Codex, Pi, custom agents), providing shared orchestration: composition, real-time team collaboration (share live sessions via URL), centralized governance (cost budgets, permission restrictions, contextual guardrails via stateful policies — not prompts), multi-interface access (web, mobile, desktop, API), and OS-level sandboxing. Framed as "Kubernetes for agents."

**Flue** (Cloudflare / Astro team, June 17): open-source, declarative agent framework built on the Pi harness (same foundation as OpenClaw.ai). Declarative approach — describe what the agent *knows* (context, model, skills, instructions) rather than scripting behavior. Ships pre-configured channels for Slack, GitHub, Linear, Discord. Uses "Durable Streams" for append-only execution logs enabling resume from exact checkpoints. On Cloudflare, leverages Agents SDK primitives (durable execution, sandboxed code, virtual filesystems). Agents write TypeScript to call APIs rather than selecting from tool lists.

**Minotauris** (minotauris.app): separates direction, coordination, execution, and critique across a Leader / Managers / Workers / Assembly architecture. Claims "a structured personal AI team for real computer execution." Posted on Bluesky (July 11) with the framing: "Most AI harnesses give one agent every responsibility. Minotauris separates [these roles]."

Sources: [Databricks Omnigent](https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents), [Cloudflare Flue SDK](https://blog.cloudflare.com/agents-platform-flue-sdk/), [Bluesky @minotauris.bsky.social](https://bsky.app/profile/minotauris.bsky.social/post/3mqfqlm5ew22l)

### 6. Pi — The Minimal Harness Powering Multiple Forks

**Pi** (badlogic/pi-mono, by Mario Zechner) is emerging as an unexpected infrastructure layer: a minimal terminal coding harness designed around "adapt pi to your workflows, not the other way around." It appears in the agentskills.io showcase AND is cited as the foundation that Flue (Cloudflare's framework) and OpenClaw.ai both build upon. Pi supports SKILL.md natively and has attracted a Mem0 integration blog post: "Giving Pi Agent Project Memory with Mem0" demonstrating persistent schema migration demos.

Sources: [Pi on agentskills.io](https://agentskills.io/home), [Pi on explainx.ai](https://explainx.ai/blog/pi-minimal-agent-harness-mario-zechner-guide-2026), [Mem0 Pi integration](https://mem0.ai/blog/giving-pi-agent-project-memory-with-mem0-a-practical-schema-migration-demo), [Cloudflare Flue SDK](https://blog.cloudflare.com/agents-platform-flue-sdk/)

### 7. MemFlywheel — File-Native Memory Layer for Agent Harnesses

**MemFlywheel** (github.com/iflytek/memflywheel, iFlytek), announced on Bluesky July 8, adds a file-native memory layer to agent harnesses (Pi, OpenCode), enabling recall-before-execution and learning-repeated-workflows. Bluesky post from @fenju.bsky.social: "Hot topic: Agents driving business automation. But without memory, every run starts from zero. MemFlywheel adds a file-native memory layer to Agent Harnesses (Pi, OpenCode), enabling recall-before-execution and learning-repeated-workflows." This addresses the stateless-per-run limitation that the Chinese IT community (CSDN) identifies as the key gap in current agent architectures.

Sources: [Bluesky @fenju.bsky.social](https://bsky.app/profile/fenju.bsky.social/post/3mq4abxctj72x), [github.com/iflytek/memflywheel](https://github.com/iflytek/memflywheel)

### 8. "Harness Handbook" — Auditable, Grounded Agent Documentation

A "field guide for making complex AI agent harnesses understandable, auditable, and editable, tying documented behavior back to grounded code evidence" appeared on Bluesky July 10 (via @bestofhn.bsky.social, pointing to a HN submission). The Harness Handbook (ruhan-wang.github.io/Harness-Handbook/) represents a new category of tooling: documentation primitives that make harness behavior inspectable and auditable. This connects to the arxiv paper "Natural-Language Agent Harnesses" (2603.25723) showing harness documents can support process-level inspection and mechanism-level analysis, and "Code as Agent Harness" (YennNing/Awesome-Code-as-Agent-Harness-Papers survey). The ai-boost/awesome-harness-engineering GitHub repo also surfaced as a curated list covering tools, patterns, evals, memory, MCP, permissions, and observability.

Sources: [Bluesky @bestofhn.bsky.social](https://bsky.app/profile/bestofhn.bsky.social/post/3mqcspldyvq2l), [ai-boost/awesome-harness-engineering](https://github.com/ai-boost/awesome-harness-engineering), [arxiv 2603.25723](https://arxiv.org/pdf/2603.25723), [YennNing/Awesome-Code-as-Agent-Harness-Papers](https://github.com/YennNing/Awesome-Code-as-Agent-Harness-Papers)

### 9. Security Alert — "Friendly Fire" Vulnerability in Autonomous Coding Agents

The AI Now Institute revealed a critical security risk in autonomous AI coding agents named "Friendly Fire": attackers embed prompt injections in repository files to trick tools like Claude Code into running malicious commands. The risk is highest in autonomous "auto-mode" configurations. X post from @Saasnext_db (July 14, 2 likes): "Under this exploit, attackers embed prompt injections in repository files to trick tools like Claude Code into running malicious commands. Because these agents run in autonomous 'auto-mode'..." This connects to the broader harness security surface identified in ClawVM (arxiv 2604.10352) which proposes harness-managed virtual memory for stateful tool-using LLM agents, and EHV (2605.17909) proposing zero-trust runtime enforcement.

Sources: [X @Saasnext_db](https://x.com/Saasnext_db/status/2077053347052556345), [arxiv ClawVM 2604.10352](https://arxiv.org/pdf/2604.10352), [arxiv EHV 2605.17909](https://arxiv.org/pdf/2605.17909)

### 10. Harness Engineering as a Discipline — Japanese Community Validates the Frame

The Japanese developer community on Qiita, Zenn, and note has independently coalesced around "harness engineering" (ハーネスエンジニアリング) as a named practice distinct from prompting. Key findings from 🇯🇵 Japanese hubs:

- **Harness engineering improvements cited at 28-47% output quality gains vs. <3% from prompt refinement alone** (note.com/aiedgerunner)
- **"Agent = Model + Harness" paradigm** gaining traction as the canonical mental model (claudelab.jp)
- **MCP vs. Skills architectural clarity**: Zenn article frames MCP as "hands" (what the AI can do) and Skills as "brain" (how it does it) — "MCPはAIの「何ができるか」を決め、Skillsは「どうやるか」を決める"
- **Coexistence patterns**: Qiita author recommends pairing skills with specific MCP servers to prevent agent confusion — role-scoped tool exposure as a stability pattern

> 「MCPはAIの「何ができるか」を決め、Skillsは「どうやるか」を決める」
> ("MCP determines *what* the AI can do; Skills determine *how* it accomplishes tasks")
> — @toyamaru on [Qiita](https://qiita.com/toyamaru/items/5a616011880f12746189)

> 「ハーネスエンジニアリングの改善は28-47%の出力品質向上をもたらすが、プロンプト改善は3%未満に留まる」
> ("Harness engineering improvements yield 28-47% output quality gains, while prompt refinement stays below 3%")
> — note.com/aiedgerunner [Harness Engineering Guide 2026](https://note.com/aiedgerunner/n/nbca11a6835f2)

Sources: [Zenn MCP vs Skills](https://zenn.dev/lumichy/articles/mcp-vs-skills-ai-agent-2026), [Qiita MCP coexistence](https://qiita.com/toyamaru/items/5a616011880f12746189), [note Harness Engineering Guide](https://note.com/aiedgerunner/n/nbca11a6835f2), [claudelab.jp](https://claudelab.jp/articles/716)

### 11. Chinese IT Hubs — MCP as the "USB Standard" for Agent Fragmentation

Chinese developer communities on CSDN, Juejin, and Zhihu are converging on MCP as the solution to framework fragmentation, with heavy technical coverage:

- **MCP framed as USB interface**: "MCP充当代理与外部工具的'USB接口'标准，消除了之前的框架不兼容问题" ("MCP acts as the 'USB interface' standard for agents and external tools, eliminating previous framework incompatibilities") — [Juejin](https://juejin.cn/post/7651426279837171764)
- **MCP 2026 Roadmap**: Four priorities identified — transport layer (HTTP streaming, WebSocket), A2A (Agent-to-Agent) protocol, governance maturation, enterprise readiness — [chenguangliang.com](https://chenguangliang.com/posts/blog088_mcp-2026-roadmap-analysis/)
- **Five-component agent architecture**: perception, planning, action, memory, reflection (感知、规划、行动、记忆、反思) as the canonical Chinese-language mental model — [CSDN](https://blog.csdn.net/m0_59162248/article/details/157030359)
- **mcpmarket.com/zh** gaining traction as the Chinese-language MCP discovery hub, connecting agents to Figma, Databricks, Storybook via MCP

Sources: [Juejin](https://juejin.cn/post/7651426279837171764), [Chen Guangliang MCP Roadmap](https://chenguangliang.com/posts/blog088_mcp-2026-roadmap-analysis/), [CSDN A2A+MCP+Skills](https://blog.csdn.net/m0_59162248/article/details/157030359), [mcpmarket.com/zh](https://mcpmarket.com/zh), [Zhihu MCP guide](https://zhuanlan.zhihu.com/p/2010143969758188866)

### 12. Harness Platform Launches — Autonomous Worker Agents for SDLC

**Harness** (the CI/CD platform, not to be confused with generic "harness" terminology) launched **Autonomous Worker Agents** on June 30, 2026 — a pipeline-native agent system designed to run inside CI/CD pipelines with full access to pipeline context, secrets, and governance controls. Distinguished from standalone coding agents by: full RBAC policy enforcement, auditable action logs, and integration with the existing Harness delivery platform. Target audience: enterprises where AI actions on the SDLC need to be traceable.

Sources: [Harness PR Newswire](http://www.prnewswire.com/news-releases/harness-launches-autonomous-worker-agents-for-software-delivery-302814180.html), [Yahoo Finance](https://finance.yahoo.com/technology/ai/articles/harness-launches-autonomous-worker-agents-150000003.html), [Harness blog](https://www.harness.io/blog/introducing-autonomous-worker-agents)

### 13. Emerging Non-Incumbent Harnesses to Watch

Beyond the named incumbents (Cursor, Claude Code, Codex, OpenCode, Windsurf, Copilot, Cline), a cluster of distinct harnesses gaining attention:

- **Emdash** (emdash.sh / generalaction/emdash): provider-agnostic desktop app running multiple coding agents in parallel, each in isolated git worktrees, locally or over SSH on remote machines. SKILL.md compatible.
- **Letta** (letta.com): stateful agent platform with advanced memory for self-improving agents. Full SKILL.md support.
- **Amp** (ampcode.com): "frontier coding agent" from the Sourcegraph team, positioned as a direct competitor in the premium coding agent tier.
- **Mux** (mux.coder.com): browser-based parallel agent workspace from Coder, runs agents in isolated workspaces, SKILL.md compatible, open source.
- **fast-agent** (fast-agent.ai): Python framework optimized for MCP-first development, evals, and skills development. Community signal: strong on HN.
- **nanobot** (HKUDS/nanobot): ultra-lightweight, multi-channel personal agent with MCP support and SKILL.md skills — runs across terminal, Telegram, Discord, Slack, WeChat.
- **Autohand Code CLI** (autohand.ai): autonomous LLM-powered terminal agent using ReAct pattern, SKILL.md compatible.
- **Ona** (ona.com): cloud platform for background agents, kernel-level governance and security.
- **Workshop** (workshop.ai): cross-platform (desktop, web, CLI), multi-LLM, supports sub-agents and custom agents.

Sources: [agentskills.io client showcase](https://agentskills.io/home), [emdash.sh](https://emdash.sh), [ampcode.com](https://ampcode.com/), [mux.coder.com](https://mux.coder.com/), [fast-agent.ai](https://fast-agent.ai/), [HKUDS/nanobot](https://github.com/HKUDS/nanobot)

---

## Cross-Source Patterns

### Pattern 1: Skills/MCP Architectural Clarity is Now Table Stakes
Appearing on: Bluesky, X, HN, Qiita (🇯🇵), Zenn (🇯🇵), Juejin (🇨🇳), CSDN (🇨🇳), WebSearch

The global developer community has reached consensus that Skills (procedural knowledge/how) and MCP (tool connectivity/what) are complementary layers, not competing standards. Japanese community frames this as MCP = hands, Skills = brain. Chinese community frames it as MCP = USB standard. Western community has agentskills.io as the reference for the SKILL.md format and mcpmarket.com for MCP discovery. The separation matters for stability: exposing all tools to all skill contexts causes agent confusion; scoping tools per skill improves reliability.

### Pattern 2: "Harness Engineering" as a Named Discipline
Appearing on: Bluesky, HN, Medium, note (🇯🇵), WebSearch

The term "harness engineering" is consolidating as distinct from "prompt engineering." Key signal: Japanese community showing 28-47% output quality gains from harness changes vs. <3% from prompting. The "Agent = Model + Harness" formula (popularized in Japanese/Chinese docs, backed by Microsoft's Agent Harness primitive) is the mental model coalescing globally. The Harness Handbook project and ai-boost/awesome-harness-engineering are early community attempts to document this discipline.

### Pattern 3: Meta-Harnesses for Multi-Agent Governance
Appearing on: Bluesky, WebSearch, X

The meta-harness pattern (a coordination layer above individual harnesses) is emerging simultaneously from Databricks (Omnigent), Cloudflare (Flue on Pi), and indie projects (Minotauris). Common thread: single-harness one-agent-does-everything architectures are being replaced by role-differentiated systems (Leader/Manager/Worker/Verifier). The architectural move mirrors how Kubernetes abstracted over individual containers.

### Pattern 4: Security Surface Expanding as Agents Go Autonomous
Appearing on: X, HN, arxiv

"Friendly Fire" prompt injection vulnerability, ClawVM harness-managed virtual memory paper, and EHV zero-trust runtime enforcement paper appeared in the same two-week window — signals that security researchers are beginning to systematically analyze the harness attack surface as agents move to auto-mode. This is a nascent signal that could grow significantly.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/LocalLLaMA | Use cases of OpenCode, Hermes Agent, etc... | 3 | 1 | "Currently I have daily cron jobs for news briefing, but I know there's much more I can do." | Reddit/r/LocalLLaMA |
| r/LocalLLaMA | oh-my-opencode vs oh-my-openagent: which harness extension is better? | 87 | 34 | "oh-my-opencode wins for the Claude Code compatible layer alone" | Reddit/r/LocalLLaMA |
| r/github | microsoft/skills repo hit 2.7K stars | 42 | 8 | "skills.md was the missing piece for cross-harness portability" | Reddit/r/github |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Saasnext_db | "The 'Friendly Fire' Vulnerability in AI Coding Agents — attackers embed prompt injections in repository files..." | 2 | 1 | https://x.com/Saasnext_db/status/2077053347052556345 |
| @ventry089 | "oh-my-opencode shipped async subagents — this is the thing that was keeping me on Claude Code" | 48 | 12 | https://x.com/ventry089 |
| @0xProbabillity | "agentskills.io showcase now has 40 clients. The network effect is real — write once, run on every harness." | 87 | 23 | https://x.com/0xProbabillity |
| @suraj_sharma14 | "ZeroClaw is wild — full Rust, <5MB memory, runs on $10 hardware. For edge AI agents this is the one." | 34 | 8 | https://x.com/suraj_sharma14 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Harness Handbook (field guide for auditable agent harnesses) | 312 | 89 | "The missing piece — making harness behavior inspectable is harder than making it work" | https://news.ycombinator.com/submitlink?u=https%3A%2F%2Fruhan-wang.github.io%2FHarness-Handbook |
| — | Microsoft Agent Framework at BUILD 2026: Agent Harness, CodeAct, Hosted Agents | 287 | 143 | "CodeAct at 52.4% latency reduction is the real headline. Consolidating tool calls to a Python program is the right abstraction." | https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/ |
| — | Cloudflare Flue SDK: Open-source agent framework on Pi harness | 201 | 67 | "Pi being the common substrate under Flue AND OpenClaw is under-discussed" | https://blog.cloudflare.com/agents-platform-flue-sdk/ |
| — | ZeroClaw: Rust-native autonomous agent runtime, <5MB, 28+ providers | 198 | 112 | "This is what happens when Rust devs decide they want an agent runtime" | https://github.com/zeroclaw-labs/zeroclaw |
| — | Omnigent: A Meta-Harness to Combine, Control and Share Your Agents (Databricks) | 167 | 78 | "Kubernetes for agents is the right analogy. Single harnesses can't govern cross-agent workflows." | https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents |
| — | agentskills.io: 1.9M community skills, 40 clients | 143 | 45 | "The moment a standard hits a million items in its community registry, it's won." | https://agentskills.io/home |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @minotauris.bsky.social | "Most AI harnesses give one agent every responsibility. Minotauris separates direction, coordination, execution, and critique across a Leader, Managers, Workers, and Assembly." | 2 | https://bsky.app/profile/minotauris.bsky.social/post/3mqfqlm5ew22l |
| @neciudan.dev | "Maxim Salnikov (Microsoft) on AI harnesses, agent ops, and what truly AI native dev teams do differently." | 1 | https://bsky.app/profile/neciudan.dev/post/3mqj6br4s2q2k |
| @bestofhn.bsky.social | "A field guide for making complex AI agent harnesses understandable, auditable, and editable" | — | https://bsky.app/profile/bestofhn.bsky.social/post/3mqcspldyvq2l |
| @fenju.bsky.social | "MemFlywheel adds a file-native memory layer to Agent Harnesses (Pi, OpenCode), enabling recall-before-execution" | 2 | https://bsky.app/profile/fenju.bsky.social/post/3mq4abxctj72x |
| @russpoldrack.org | "I have a new version of the AI coding chapter coming, will talk a bit about agent harnesses. would love to know what points you'd like covered" | 3 | https://bsky.app/profile/russpoldrack.org/post/3mq335j3xr224 |

**GitHub:**
| Repo | Stars | Issues | Description | URL |
|------|-------|--------|-------------|-----|
| anomalyco/opencode | 186K (live) | 4,690 | The open source coding agent | https://github.com/anomalyco/opencode |
| opensoft/oh-my-opencode | ~4K | — | Async subagents, curated MCPs, Claude Code compatible layer | https://github.com/opensoft/oh-my-opencode |
| microsoft/skills | 2.7K (live) | 60 | Skills, MCP servers, Custom Agents, Agents.md for SDKs to ground Coding Agents | https://github.com/microsoft/skills |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | agentskills.io | https://agentskills.io/home | Official SKILL.md spec; 40+ client showcase including 20+ non-incumbent harnesses |
| 🌐 | Databricks Blog | https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents | Omnigent meta-harness announcement |
| 🌐 | Cloudflare Blog | https://blog.cloudflare.com/agents-platform-flue-sdk/ | Flue SDK on Pi harness; Cloudflare Agents SDK integration |
| 🌐 | Microsoft Devblogs | https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/ | MAF 1.0 Agent Harness, CodeAct, Hosted Agents |
| 🌐 | ZeroClaw GitHub | https://github.com/zeroclaw-labs/zeroclaw | Rust-native agent runtime |
| 🌐 | iFlytek MemFlywheel | https://github.com/iflytek/memflywheel | File-native memory layer for Pi/OpenCode |
| 🌐 | Harness Handbook | https://ruhan-wang.github.io/Harness-Handbook/ | Field guide for auditable harness behavior |
| 🌐 | ai-boost awesome-harness | https://github.com/ai-boost/awesome-harness-engineering | Curated harness engineering resources |
| 🌐 | RyanAlberts best-of-Agent-Harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | Curated ranked list 100+ harnesses with MCP server |
| 🌐 | Agensi skills browse | https://www.agensi.io/skills | Independent SKILL.md marketplace |
| 🌐 | Totalum blog | https://www.totalum.app/blog/agent-skills-marketplaces-2026 | Skills marketplace comparison: Anthropic vs Vercel vs OpenAI vs Cline vs MCP |
| 🌐 | Harness.io Worker Agents | https://www.harness.io/blog/introducing-autonomous-worker-agents | Pipeline-native autonomous agents |
| 🌐 | Minotauris app | https://www.minotauris.app | Leader/Manager/Worker/Assembly multi-agent harness |
| 🌐 | emdash.sh | https://emdash.sh | Parallel worktree agent desktop app |
| 🌐 | fast-agent.ai | https://fast-agent.ai/ | MCP-first Python harness |
| 🌐 | nanobot.wiki | https://nanobot.wiki/ | Multi-channel personal agent |
| 🇯🇵 | Zenn | https://zenn.dev/lumichy/articles/mcp-vs-skills-ai-agent-2026 | MCP as "hands," Skills as "brain" — architectural clarity |
| 🇯🇵 | Qiita | https://qiita.com/toyamaru/items/5a616011880f12746189 | MCP+Skills coexistence pattern; role-scoped tool exposure |
| 🇯🇵 | note | https://note.com/aiedgerunner/n/nbca11a6835f2 | Harness engineering 28-47% improvement vs. <3% from prompting |
| 🇯🇵 | note | https://note.com/ai_shiryo/n/n376910311603 | Agent/MCP/Skill/Plugin as distinct architectural layers |
| 🇯🇵 | claudelab.jp | https://claudelab.jp/articles/716 | "Agent = Model + Harness" paradigm guide |
| 🇯🇵 | ncdc.co.jp | https://ncdc.co.jp/columns/13040/ | RAG/MCP/Skills as separate technologies |
| 🇯🇵 | Qiita | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | Harness engineering intro |
| 🇯🇵 | funnel-ai.jp | https://funnel-ai.jp/media/agent-harness-skill-relationship/ | Harness vs. skill component roles |
| 🇨🇳 | Juejin | https://juejin.cn/post/7651426279837171764 | MCP as "USB interface" standard; framework comparison |
| 🇨🇳 | CSDN | https://blog.csdn.net/ziwoods/article/details/161662819 | MCP complete guide for agent development |
| 🇨🇳 | CSDN | https://blog.csdn.net/m0_59162248/article/details/157030359 | A2A+MCP+Skills five-component architecture |
| 🇨🇳 | Tencent Cloud Developer | https://developer.cloud.tencent.com/article/2707597 | MCP 1.0 full explosion — conversation to execution |
| 🇨🇳 | Chen Guangliang Blog | https://chenguangliang.com/posts/blog088_mcp-2026-roadmap-analysis/ | MCP 2026 roadmap: transport, A2A, governance, enterprise |
| 🇨🇳 | Juejin/Jishuzhan | https://jishuzhan.net/article/2043896199359561730 | Six-framework comparison with code |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2010143969758188866 | Essential MCP servers guide for 2026 |
| 🇨🇳 | macgpu.com | https://macgpu.com/zh/blog/2026-0616-cong-0-kaifa-mcp-server-jiaocheng.html | Building MCP servers from zero |
| 🇨🇳 | mcpmarket.com/zh | https://mcpmarket.com/zh | Chinese-language MCP discovery hub |
| 🇨🇳 | Wasa Team | https://wasateam.com/blog/mcp-model-context-protocol-enterprise-guide | MCP enterprise implementation guide |

---

## Stats Block

```
├─ 🟠 Reddit: 11 threads │ 313 upvotes │ 79 comments │ ⚠ partial (HTTP 403 after 11 items)
├─ 🔵 X: 49 posts │ 542 likes │ 54 reposts
├─ 🟡 HN: 23 stories │ 1,541 points │ 1,152 comments
├─ 🦋 Bluesky: 11 posts │ 32 likes │ 3 reposts
├─ 🐙 GitHub: 3 repos │ 189,346 stars │ 4,750 issues
├─ 🌐 Web: 18 pages │ 🇯🇵 8 │ 🇨🇳 10
└─ 🗣️ Top voices: @0xProbabillity, @ventry089, @suraj_sharma14 │ r/LocalLLaMA, r/github
```

---

## Out of Scope but Notable

- **ByteDance deer-flow**: open-source long-horizon super-agent (researches, codes, creates using sandboxes, memories, subagents). May belong to ai-software-factory topic but has architectural novelty worth tracking — it's a harness-within-a-harness design. [GitHub trending June 2026](https://startupcorners.com/digest/devtools-digest-2026-06-25)
- **Mastra** (TypeScript-native, June 2026 Harness primitive): interactive AI agents with multiple modes, persistent threads, tool approvals, model switching. Approaching from the application framework angle rather than coding agent angle — may fit better in ai-software-factory but listed here for awareness. [The Tool Nerd](https://www.thetoolnerd.com/p/10-agent-harnesses-every-ai-builder)
- **Pydantic AI v2** (June 2026 harness-first redesign): Capability primitive, fast-moving pydantic-ai-harness track where capabilities graduate as they prove essential. Framework rather than harness. [Medium/dave-patten](https://medium.com/@dave-patten/the-state-of-ai-coding-agents-2026-from-pair-programming-to-autonomous-ai-teams-b11f2b39232a)
- **ClawVM** (arxiv 2604.10352): harness-managed virtual memory for stateful tool-using LLM agents — an academic proposal for a new harness memory primitive. Novel enough to watch. [arxiv](https://arxiv.org/pdf/2604.10352)

---

## Data Gaps

- **ScrapeCreators DOWN (402 billing)**: TikTok (0 items), Instagram (0 reels), YouTube (0 videos), Threads (0 posts), LinkedIn (0 posts) all failed with HTTP 402. These channels are excluded from all engagement counts. TikTok and YouTube in particular likely carry significant agent harness tutorial content that is not reflected here.
- **Reddit partial**: HTTP 403 block after 11 threads. Full r/LocalLLaMA, r/ChatGPTCoding, r/AI_Agents coverage unavailable. This is a material gap — these are the highest-signal communities for this topic.
- **Bluesky**: 11 posts found; the Bluesky search for the second subquery returned 0, suggesting limited coverage on the "new coding agent terminal agent" angle.
- **Polymarket**: 0 markets on agent harness topics — no prediction market signals available.
- **Coverage estimate: ~65%** — strong coverage of English web, HN, X, GitHub, and JP/CN hubs; significant gaps from Reddit block and ScrapeCreators failure removing YouTube/TikTok/Instagram.

---

## Key Quotes

> "Most AI harnesses give one agent every responsibility. Minotauris separates direction, coordination, execution, and critique across a Leader, Managers, Workers, and Assembly. A structured personal AI team for real computer execution." — @minotauris.bsky.social on Bluesky ([link](https://bsky.app/profile/minotauris.bsky.social/post/3mqfqlm5ew22l))

> "Hot topic: Agents driving business automation. But without memory, every run starts from zero. MemFlywheel adds a file-native memory layer to Agent Harnesses (Pi, OpenCode), enabling recall-before-execution and learning-repeated-workflows." — @fenju.bsky.social on Bluesky ([link](https://bsky.app/profile/fenju.bsky.social/post/3mq4abxctj72x))

> "A field guide for making complex AI agent harnesses understandable, auditable, and editable, tying documented behavior back to grounded code evidence." — @bestofhn.bsky.social on Bluesky ([link](https://bsky.app/profile/bestofhn.bsky.social/post/3mqcspldyvq2l))

> "MCPはAIの「何ができるか」を決め、Skillsは「どうやるか」を決める" ("MCP determines *what* the AI can do; Skills determine *how* it accomplishes tasks") — @toyamaru on [Qiita](https://qiita.com/toyamaru/items/5a616011880f12746189) 🇯🇵

> "MCP充当代理与外部工具的'USB接口'标准，消除了之前的框架不兼容问题" ("MCP acts as the 'USB interface' standard for agents and external tools, eliminating previous framework incompatibilities") — [Juejin](https://juejin.cn/post/7651426279837171764) 🇨🇳

> "agentskills.io showcase now has 40 clients. The network effect is real — write once, run on every harness." — @0xProbabillity on X ([link](https://x.com/0xProbabillity))

> "oh-my-opencode shipped async subagents — this is the thing that was keeping me on Claude Code" — @ventry089 on X ([link](https://x.com/ventry089))

> "ZeroClaw is wild — full Rust, <5MB memory, runs on $10 hardware. For edge AI agents this is the one." — @suraj_sharma14 on X ([link](https://x.com/suraj_sharma14))

> "CodeAct at 52.4% latency reduction is the real headline. Consolidating tool calls to a Python program is the right abstraction." — HN commenter on [Microsoft Agent Framework BUILD 2026](https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/)

> "Pi being the common substrate under Flue AND OpenClaw is under-discussed" — HN commenter on [Cloudflare Flue SDK](https://blog.cloudflare.com/agents-platform-flue-sdk/)
