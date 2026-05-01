# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-01
**Query type:** GENERAL
**Sources:** Web, YouTube, GitHub, Hacker News

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web | 100+ pages | — | Blog posts, official docs, news coverage, dev tutorials |
| YouTube | 3 videos | N/A | Tutorials on Claude Code MCP/skills stack |
| GitHub | 15+ repos | N/A | Open-source marketplaces, skill collections, lazy-load tools |
| Hacker News | 1 thread + mentions | N/A | LangAlpha Show HN; HN digest coverage |
| Reddit | — | — | No threads surfaced |
| X/Twitter | — | — | Not crawled |
| TikTok | — | — | No results |
| Bluesky | — | — | No results |
| Polymarket | — | — | No markets found |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: Anthropic Sets the Agenda, Industry Follows

Anthropic released the Agent Skills specification on **December 18, 2025**, defining a universal format for packaging procedural knowledge for AI coding agents. The format is simple: a folder containing a `SKILL.md` file with YAML frontmatter (name, description, instructions), optional supplementary files, and optional executable scripts. The progressive disclosure design means agents load the description first and pull full instructions only when relevant — keeping context lean.

The industry response was swift and striking. Within **48 hours** of the open standard release, Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI. Within **90 days**, 32 tools from competing companies — including Google's Gemini CLI, JetBrains Junie, AWS Kiro, and Block's Goose — were reading the same SKILL.md files. The result is genuine cross-agent portability: a skill written for Claude Code works in Codex CLI without modification.

Anthropic's engineering team (Barry Zhang, Keith Lazuka, Mahesh Murag) framed the vision as giving agents the equivalent of "an onboarding guide for a new hire" — domain expertise that transforms a general-purpose agent into a specialist without custom-building new agents from scratch.

**Platforms:** Web (official docs, The New Stack, AI Business, Paperclipped, Medium, Anthropic engineering blog)

Key sources: [Anthropic Engineering: Equipping Agents for the Real World](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [Agent Skills Open Standard Interoperability Guide](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) · [The New Stack: Anthropic's Next Bid to Define AI Standards](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) · [AI Business: Anthropic Launches Skills Open Standard](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) · [OpenAI Codex Skills docs](https://developers.openai.com/codex/skills) · [anthropics/skills GitHub repo](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md) · [Medium: Unveiling Agent Skill](https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71)

---

### 2. Marketplace Fragmentation: A Cambrian Explosion of Skill Directories

In the four months since SKILL.md dropped, the skill marketplace landscape has exploded — and fragmented. Multiple competing directories have emerged, each tracking slightly different numbers and targeting slightly different audiences:

- **skills.sh (Vercel)** — Launched January 20, 2026. The most prominent open directory and leaderboard. 90,000+ skills indexed, 19 AI agent platforms supported, real-time install telemetry. Top skill: `find-skills` by Vercel Labs with 579,000+ installs. CLI: `npx skills add <owner>/<repo>`. Positioned as infrastructure-neutral.
- **SkillsMP** — 425,000+ skills, largest raw catalog count, built on the open SKILL.md standard.
- **LobeHub** — 169,739 skills indexed, fast-growing, polished UI, cross-platform (Claude, Codex, ChatGPT).
- **ClaudeSkills.info** — 658+ free skills including official Anthropic-produced skills (PDF, DOCX, XLSX workflows, frontend design, MCP builder).
- **tonsofskills.com** — Claude-specific; 2,849 skills, 423 plugins, 177 agents; ships with `ccpi` CLI (`pnpm add -g @intentsolutionsio/ccpi`); MIT-licensed, updated daily by GitHub Actions.
- **claudemarketplaces.com** — 150+ skills as of March 2026, curated list.
- **AgentSkillExchange** — Another emerging marketplace.

The aggregate numbers suggest 4,200+ skills and 770+ MCP servers across the ecosystem as of April 2026. The proliferation is generating some fatigue: community guides consistently recommend limiting active plugins to 2-3 maximum to avoid context window degradation.

**Platforms:** Web, GitHub

Key sources: [skills.sh](https://skills.sh/) · [Vercel Changelog: Introducing skills](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [InfoQ: Vercel Agent Skills](https://www.infoq.com/news/2026/02/vercel-agent-skills/) · [SkillsMP](https://skillsmp.com/) · [LobeHub Skills](https://lobehub.com/skills) · [tonsofskills.com GitHub repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [AgentSkillExchange](https://agentskillexchange.com/) · [Best AI Agent Skills Marketplaces 2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) · [KDnuggets: Top 5 Agent Skill Marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) · [Brightcoding: Claude Skills Marketplace](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers) · [VirtualUncle: Skills.sh Guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) · [Toolworthy: skills.sh Review](https://www.toolworthy.ai/tool/skills-sh) · [Vercel Labs/skills GitHub](https://github.com/vercel-labs/skills) · [Tessl Registry: find-skills](https://tessl.io/registry/skills/github/vercel-labs/skills/find-skills) · [ClaudeMarketplaces.com](https://claudemarketplaces.com/)

---

### 3. The Three-Layer Stack: Skills vs. MCP vs. Plugins — A Maturing Taxonomy

The community has converged on a clear (if contested) taxonomy for Claude Code's extension systems:

- **Skills** = procedural knowledge (30-50 tokens each). Markdown instruction files. Teach Claude *how* to behave. Stored globally in `~/.claude/skills/` or project-locally in `.claude/skills/`. Load lazily.
- **MCP Servers** = integration plumbing. Give Claude access to external tools, databases, APIs, and live data it couldn't otherwise reach. The N-agents-to-M-services problem solved once.
- **Plugins** = bundles. Package skills + slash commands + subagents + MCP configurations + hooks into a single installable unit. "If Skills are individual recipe cards and MCP is the kitchen plumbing, a Plugin is the full kitchen, stocked and ready to cook."

The persistent confusion: newcomers conflate all three. Multiple blog posts and video tutorials in April 2026 are explicitly titled to address this (morphllm.com, devtoolpicks.com, agensi.io, geeky-gadgets.com, alexop.dev). The recommended practical stack: 2-3 MCP servers (GitHub, Filesystem, one domain-specific) + a few custom skills; plugins at most 2-3 active.

**Platforms:** Web, YouTube

Key sources: [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [Claude Skills vs MCP Connectors vs Plugins](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) · [Plugins vs Skills Explained](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [Geeky Gadgets: Claude Code MCP vs Skills vs Hooks](https://www.geeky-gadgets.com/claude-code-mcp-plugins-explained/) · [Alexop.dev: Understanding Claude Code's Full Stack](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [DEV Community: Skills vs MCP Servers 2026](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) · [Best Claude Code Skills & Plugins Guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) · [Redwerk: 7 Best Claude Code Plugins](https://redwerk.com/blog/best-claude-code-plugins/) · [TurboDocx: Best Skills Plugins MCP](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) · [The Ultimate Claude Code Guide — YouTube](https://www.youtube.com/watch?v=uogzSxOw4LU) · [Claude Plugins & Skills Tutorial — Ansh Mehra YouTube](https://www.youtube.com/watch?v=6EFOT6hjvAU) · [Claude Code Skills & Agents: Slash Commands](https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865) · [Mejba.me: Top 10 Skills Plugins CLIs 2026](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) · [Raxxo: Best Skills Plugins 2026](https://raxxo.shop/blogs/lab/best-claude-code-skills-plugins-2026-guide) · [Smart Webtech: Claude Code Workflows Best Practices](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/) · [Claude Code Survival Guide LinkedIn](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) · [Chris Ayers: Agent Skills Plugins Marketplace](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)

---

### 4. MCP Tool Search: Lazy Loading Breaks the Context Ceiling

A critical infrastructure problem emerged as users piled on more MCP servers: tool definitions eat the context window. A server with 50 tools could consume 50K+ tokens before a single line of code was written.

Anthropic shipped **MCP Tool Search** on **January 14, 2026**. The mechanism: if MCP tool descriptions would exceed 10K tokens (>10% of context), Claude Code automatically defers tools with `defer_loading: true`, injects a lightweight Tool Search tool instead, and loads 3-5 relevant tools (~3K tokens) per query on demand. Result: up to **95% context reduction** in high-server-count setups; Anthropic cites 85% in official materials. Now enabled by default.

The community response was significant. Open-source alternatives appeared (voicetreelab/lazy-mcp, PeterCha90/mcp-lazy-load). OpenAI filed a parallel feature request for Codex (Issue #9266). Amp/Sourcegraph documented their own lazy-load approach combining MCP with skills.

**Platforms:** Web, GitHub

Key sources: [Claude Code MCP Tool Search: Save 95% Context](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) · [What is MCP Tool Search? — atcyrus.com](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) · [Efficient MCP Tool Loading — ampcode.com](https://ampcode.com/news/lazy-load-mcp-with-skills) · [Lazy Load MCP server — mcpmarket.com](https://mcpmarket.com/server/lazy-load) · [MCP, Skills, and Agents — cra.mr](https://cra.mr/mcp-skills-and-agents/) · [GitHub voicetreelab/lazy-mcp](https://github.com/voicetreelab/lazy-mcp) · [GitHub PeterCha90/mcp-lazy-load](https://github.com/PeterCha90/mcp-lazy-load) · [OpenAI Codex Issue #9266](https://github.com/openai/codex/issues/9266)

---

### 5. MCP Dev Summit 2026: Skills Are Not the MCP Killer

The **MCP Dev Summit North America** (April 2-3, 2026, New York City) drew 1,200 attendees, 17 keynotes, and 95+ sessions under the banner of the Agentic AI Foundation (AAIF). The headline technical debate: would Anthropic's Agent Skills specification displace MCP?

Pedro Rodrigues from Supabase delivered the most-cited session of the summit: **"Skills Are Not the MCP Killer."** His argument: the framing is wrong. MCP and Skills solve different problems. MCP solves the integration problem (connecting N agents to M external services). Skills solve the context saturation problem (guiding agents without bloating context windows). His analogy: "MCP is the pilot, skills are the co-pilot."

He demonstrated the stakes with a live security incident: an MCP-only agent, asked to build a PostgreSQL view, accidentally bypassed Row-Level Security and exposed all teams' data. Adding a skill that directed the agent to read security documentation first fixed the issue. The lesson: capability alone (MCP) without behavioral guidance (skills) is a liability.

Separately, a **"Skills Over MCP Interest Group"** held office hours on April 14, 2026, documenting architectural decisions in GitHub Discussion #2585. Key outcomes: host discovery via `index.json` at startup; multi-file skills ship as archives; Mintlify quietly shipped `.well-known` URI skill hosting exposing skills as MCP resources — an unexpected integration point.

**Platforms:** Web, GitHub

Key sources: [Skills Aren't the MCP Killer — obot.ai](https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/) · [MCP Dev Summit North America — Linux Foundation](https://events.linuxfoundation.org/mcp-dev-summit-north-america/) · [AAIF MCP Summit Coverage — InfoQ](https://www.infoq.com/news/2026/04/aaif-mcp-summit/) · [MCP Dev Summit: Standardizing AI Agents — SD Times](https://sdtimes.com/ai/mcp-dev-summit-standardizing-ai-agents-starting-with-mcp/) · [AAIF Sets A Clear Direction — Futurum](https://futurumgroup.com/insights/mcp-dev-summit-2026-aaif-sets-a-clear-direction-with-disciplined-guardrails/) · [Skills Over MCP Office Hours Notes — GitHub Discussion #2585](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585) · [LF: AAIF MCP Dev Summit Schedule](https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule) · [AAIF Schedule Announcement](https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/) · [Yahoo Finance: AAIF MCP Dev Summit](https://finance.yahoo.com/news/agentic-ai-foundation-unveils-mcp-140000965.html) · [Wikipedia: Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol)

---

### 6. Claude Managed Agents: Production-Grade Agent Infrastructure

On **April 8, 2026**, Anthropic launched **Claude Managed Agents** (currently in beta) — a suite of composable APIs for building and deploying cloud-hosted agents at scale. The pitch: stop building the agent harness yourself. Managed Agents provides the full runtime: sandboxed code execution, checkpointing, credential management, scoped permissions, and end-to-end tracing, with built-in prompt caching and compaction.

Pricing is usage-only: **$0.08/session-hour** + standard token costs. No flat monthly fee, no per-agent license. All endpoints require the `managed-agents-2026-04-01` beta header. Multi-agent coordination and self-evaluation remain in "research preview."

InfoWorld called it "execution and control for AI agent workflows." The developer community response was measured: the "Honest Pros and Cons" Medium post (unicodeveloper) noted the $0.08/hr runtime cost adds up quickly for always-on agents, and the beta restrictions limit production use cases. Still, the direction is clear: Anthropic wants to own the full agent stack, from skills to runtime.

**Platforms:** Web

Key sources: [Claude Managed Agents Blog Post](https://claude.com/blog/claude-managed-agents) · [Claude Managed Agents API Docs](https://platform.claude.com/docs/en/managed-agents/overview) · [InfoWorld: Anthropic Rolls Out Claude Managed Agents](https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html) · [Help Net Security: Claude Managed Agents](https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/) · [DevOps.com: Claude Introduces Agent Skills for Custom Workflows](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) · [Verdent: What Is Claude Managed Agents](https://www.verdent.ai/guides/what-is-claude-managed-agents) · [Verdent: Pricing Guide](https://www.verdent.ai/guides/claude-managed-agents-pricing) · [ClaudeAI.dev: What Just Launched](https://claudeai.dev/blog/claude-managed-agents-what-just-launched/) · [Toolworthy: Review](https://www.toolworthy.ai/tool/claude-managed-agents) · [Findskill.ai: Explained](https://findskill.ai/blog/claude-managed-agents-explained/) · [Medium @unicodeveloper: Honest Pros and Cons](https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14)

---

### 7. Desktop Extensions (.dxt → .mcpb): One-Click MCP Installation

Desktop Extensions — `.dxt` files (now transitioning to `.mcpb` / MCP Bundle format) — solve MCP server installation friction. Rather than editing JSON configs and managing runtimes, users download a file and double-click it. Claude Desktop handles everything.

The format is spiritually similar to Chrome extensions (`.crx`) or VS Code extensions (`.vsix`). Anthropic maintains the `anthropics/dxt` GitHub repository defining the spec; the format has since been adopted by the `modelcontextprotocol/mcpb` project. Two community collections have emerged: `milisp/awesome-claude-dxt` and `samihalawa/awesome-claude-dxt` (500+ extensions). Socket Security launched `Socket MCP` for Claude Desktop as a security-scanning extension.

Format evolution note: `.mcpb` is now recommended for new extensions; `.dxt` is legacy but still supported.

**Platforms:** Web, GitHub

Key sources: [Anthropic Engineering: Desktop Extensions](https://www.anthropic.com/engineering/desktop-extensions) · [anthropics/dxt GitHub](https://github.com/anthropics/dxt) · [modelcontextprotocol/mcpb GitHub](https://github.com/modelcontextprotocol/mcpb) · [mcp.so/dxt](https://mcp.so/dxt) · [desktopextensions.com](https://www.desktopextensions.com/) · [awesome-claude-dxt (milisp)](https://github.com/milisp/awesome-claude-dxt) · [awesome-claude-dxt (samihalawa)](https://github.com/samihalawa/awesome-claude-dxt) · [Socket MCP for Claude Desktop](https://socket.dev/blog/introducing-socket-mcp-for-claude-desktop) · [Glama: Getting Started with DXT](https://glama.ai/blog/2025-07-11-getting-started-with-mcp-desktop-extensions-dxt-in-claude-desktop)

---

### 8. Real-World MCP Applications: APIs, Security, and Live Catalogs

Several notable production MCP implementations shipped in April 2026:

**Kestra MCP** (April 30, 2026): A remote HTTP MCP server at `https://api.kestra.io/v1/mcp` exposing Kestra's entire plugin registry and Blueprint catalog as 13 read-only tools — zero auth required, always current, framework-agnostic. Connect with `claude mcp add --transport http kestra https://api.kestra.io/v1/mcp`. Works with Codex CLI, Gemini CLI, and OpenCode equally.

**Cloudflare Code Mode**: A dense-encoding approach giving agents an entire API in 1,000 tokens via MCP — solving the "I have a large API, how do I not burn context explaining it" problem.

**CVE MCP Server**: Turns Claude into a security analyst with 27 tools across 21 APIs covering vulnerability research.

**Meta Ads CLI + MCP**: Run Facebook ad campaigns directly from Claude (YouTube tutorial, April 29, 2026).

The common thread: MCP is becoming the default integration layer for any service that wants agent-accessible documentation or APIs, replacing one-off custom tools.

**Platforms:** Web, GitHub, YouTube

Key sources: [Kestra MCP Blog](https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints) · [Kestra plugin-ai GitHub](https://github.com/kestra-io/plugin-ai) · [Kestra AI Tools Docs](https://kestra.io/docs/ai-tools) · [Kestra AI Agents](https://kestra.io/docs/ai-tools/ai-agents) · [Kestra MCP Python server](https://github.com/kestra-io/mcp-server-python) · [Kestra 1.0](https://kestra.io/1-0) · [Cloudflare Code Mode MCP](https://blog.cloudflare.com/code-mode-mcp/) · [CVE MCP Server](https://cybersecuritynews.com/cve-mcp-server-and-claude/) · [Meta Ads CLI + MCP YouTube](https://www.youtube.com/watch?v=mcT9f3JjYho) · [Best MCP Servers for Web Developers](https://www.deployhq.com/blog/best-mcp-servers-for-web-developers) · [50+ Best MCP Servers for Claude Code](https://claudefa.st/blog/tools/mcp-extensions/best-addons) · [MCP Servers List 2026 — TokenMix](https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory) · [5 MCP servers every Claude Code user should know](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1)

---

### 9. Agent Teams, Subagents, and the Multi-Agent Frontier

Claude Code's agent model has matured beyond single-agent workflows:

- **Subagents**: Each runs in its own context window with a custom system prompt, specific tool access, and independent permissions. Claude delegates tasks matching a subagent's description automatically.
- **Agent Teams** (research preview): Multiple agents working in parallel on shared codebases, coordinating autonomously.
- **Multi-agent orchestration**: Open-source projects like `wshobson/agents` and `FlorianBruniaux/claude-code-ultimate-guide` document orchestration patterns.

Community emphasis is shifting from "what can this agent do?" to "how do I verify what it did?" Hacker News coverage highlights verification as the emerging bottleneck for production multi-agent systems.

**Platforms:** Web, GitHub, Hacker News

Key sources: [Claude Code Docs: Create Custom Subagents](https://code.claude.com/docs/en/sub-agents) · [Claude API Docs: Agent Skills Overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Claude Code Docs: MCP](https://code.claude.com/docs/en/mcp) · [wshobson/agents GitHub](https://github.com/wshobson/agents) · [claude-code-ultimate-guide: agent-teams.md](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md) · [Udemy: Claude Code 2026 Bootcamp](https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/) · [What HN Gets Right About AI Coding Agents](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) · [January 2026: AI Agents Take Over — codewithandrea](https://codewithandrea.com/newsletter/january-2026/) · [chatprd: Claude AI Workflows](https://www.chatprd.ai/how-i-ai/workflows/tool/claude) · [HN: LangAlpha Show HN](https://news.ycombinator.com/item?id=47766370) · [Microsoft .NET Blog: Extend Coding Agent with .NET Skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) · [Deepwiki: microsoft/agent-skills Plugins](https://deepwiki.com/microsoft/agent-skills/4-plugins) · [quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins)

---

## Cross-Source Patterns

### Pattern 1: Skills and MCP Are Complementary, Not Competing

**Platforms:** Web, GitHub, Conference coverage (MCP Dev Summit)

The most consistent signal across all sources: the "Skills vs. MCP" framing is a false dichotomy. Every serious practitioner and conference talk in April 2026 arrived at the same conclusion — MCP handles connectivity, skills handle behavior. The live security demo (RLS bypass) at MCP Dev Summit gave this abstract point a concrete weight.

> "MCP is the pilot, skills are the co-pilot." — Pedro Rodrigues, Supabase, MCP Dev Summit 2026 ([obot.ai](https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/))

> "Agents are very lazy to go beyond their training data, and they need a push to search the web or find the right information." — Pedro Rodrigues ([GitHub Discussion #2585](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585))

---

### Pattern 2: Context Window Management Is Now the Primary Engineering Problem

**Platforms:** Web, GitHub (multiple repos)

Every major tooling release in Q1-Q2 2026 touches context management: MCP Tool Search (January), lazy-loading MCP skills (Amp), the `defer_loading` directive, multiple open-source lazy-load proxies. The OpenAI Codex team filed a feature request for the same capability. This is a platform-wide pressure, not Claude-specific.

> "MCP Tool Search is Claude Code's new lazy loading system for MCP servers that loads a lightweight search index and fetches tool details on-demand." — [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

---

### Pattern 3: SKILL.md Portability Accelerating Cross-Tool Adoption

**Platforms:** Web, GitHub, Official docs (Anthropic, OpenAI, Microsoft)

The same SKILL.md files work across 32 tools in less than 5 months. This portability is generating real pull: teams can standardize on SKILL.md and let each developer pick their preferred agent. The skills marketplace numbers (425K+ on SkillsMP, 169K+ on LobeHub, 90K+ tracked on skills.sh) reflect this multiplier effect.

---

### Pattern 4: Production Agents Need More Than Skills — Runtime Infrastructure Matters

**Platforms:** Web (InfoWorld, Help Net Security, Medium)

Claude Managed Agents (April 8, 2026) and the community discussion around it reflect a maturing concern: skills tell Claude what to do, but production agents need checkpointing, credential management, scoped permissions, and observability. The beta launch and $0.08/hr pricing model are being watched closely.

---

## Per-Platform Tables

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | [equipping-agents-for-the-real-world-with-agent-skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Official SKILL.md spec origin, design rationale |
| Anthropic Engineering | [desktop-extensions](https://www.anthropic.com/engineering/desktop-extensions) | One-click MCP install format (.dxt) |
| Anthropic Blog | [claude-managed-agents](https://claude.com/blog/claude-managed-agents) | Managed Agents launch post |
| Claude Code Docs | [mcp](https://code.claude.com/docs/en/mcp) | Official MCP integration guide |
| Claude Code Docs | [sub-agents](https://code.claude.com/docs/en/sub-agents) | Official subagent guide |
| Claude API Docs | [agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | Official Agent Skills API reference |
| Claude API Docs | [managed-agents/overview](https://platform.claude.com/docs/en/managed-agents/overview) | Managed Agents API reference |
| Claude Release Notes | [release-notes/overview](https://platform.claude.com/docs/en/release-notes/overview) | Platform changelog |
| Claude Support | [local-mcp-servers](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop) | MCP Desktop setup guide |
| ModelContextProtocol.io | [connect-local-servers](https://modelcontextprotocol.io/docs/develop/connect-local-servers) | Official MCP docs |
| Vercel Changelog | [introducing-skills](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh launch |
| Vercel Docs | [agent-resources/skills](https://vercel.com/docs/agent-resources/skills) | Vercel skills docs |
| Kestra Blog | [kestra-mcp-plugins-blueprints](https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints) | Live MCP plugin catalog (April 30, 2026) |
| Kestra Docs | [ai-tools/ai-agents](https://kestra.io/docs/ai-tools/ai-agents) | Kestra AI agent setup |
| Obot.ai | [skills-arent-the-mcp-killer](https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/) | MCP Dev Summit recap, skills vs. MCP |
| InfoQ | [vercel-agent-skills](https://www.infoq.com/news/2026/02/vercel-agent-skills/) | Vercel skills.sh coverage |
| InfoQ | [aaif-mcp-summit](https://www.infoq.com/news/2026/04/aaif-mcp-summit/) | MCP Dev Summit coverage |
| The New Stack | [agent-skills-anthropics-next-bid](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Industry analysis on SKILL.md standard |
| AI Business | [anthropic-launches-skills-open-standard](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) | News coverage of standard launch |
| InfoWorld | [anthropic-rolls-out-claude-managed-agents](https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html) | Managed Agents news coverage |
| Help Net Security | [claude-managed-agents](https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/) | Security-angle Managed Agents coverage |
| DevOps.com | [claude-introduces-agent-skills](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) | Agent Skills for DevOps workflows |
| Cloudflare Blog | [code-mode-mcp](https://blog.cloudflare.com/code-mode-mcp/) | API-in-1000-tokens approach |
| Cyber Security News | [cve-mcp-server-and-claude](https://cybersecuritynews.com/cve-mcp-server-and-claude/) | CVE MCP 27 tools across 21 APIs |
| MorphLLM | [claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Definitive comparison guide |
| Alexop.dev | [understanding-claude-code-full-stack](https://alexop.dev/posts/understanding-claude-code-full-stack/) | MCP + Skills + Subagents + Hooks explained |
| claudefa.st | [mcp-tool-search](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) | MCP lazy loading deep-dive |
| claudefa.st | [best-addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers list |
| Paperclipped | [agent-skills-open-standard-interoperability](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) | Cross-tool adoption data (32 tools in 90 days) |
| Linux Foundation Events | [mcp-dev-summit-north-america](https://events.linuxfoundation.org/mcp-dev-summit-north-america/) | Summit details |
| Futurum | [mcp-dev-summit-2026-aaif](https://futurumgroup.com/insights/mcp-dev-summit-2026-aaif-sets-a-clear-direction-with-disciplined-guardrails/) | AAIF direction and guardrails analysis |
| SD Times | [mcp-dev-summit](https://sdtimes.com/ai/mcp-dev-summit-standardizing-ai-agents-starting-with-mcp/) | Summit overview |
| Linux Foundation Press | [aaif-mcp-summit-schedule](https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule) | Official schedule release |
| OpenAI Developers | [codex/skills](https://developers.openai.com/codex/skills) | OpenAI SKILL.md adoption |
| Microsoft .NET Blog | [dotnet-skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | Microsoft .NET agent skills |
| Brightcoding | [claude-skills-marketplace](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers) | Marketplace overview (April 26, 2026) |
| Agensi.io | [best-ai-agent-skills-marketplaces-2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Marketplace comparison |
| KDnuggets | [top-5-agent-skill-marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 marketplace ranking |
| cra.mr | [mcp-skills-and-agents](https://cra.mr/mcp-skills-and-agents/) | MCP + Skills + Agents analysis |
| ampcode.com | [lazy-load-mcp-with-skills](https://ampcode.com/news/lazy-load-mcp-with-skills) | Amp lazy loading approach |
| atcyrus.com | [mcp-tool-search-guide](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) | Context pollution guide |
| Verdent | [claude-managed-agents](https://www.verdent.ai/guides/what-is-claude-managed-agents) | Developer guide to Managed Agents |
| Verdent | [claude-managed-agents-pricing](https://www.verdent.ai/guides/claude-managed-agents-pricing) | Pricing breakdown |
| Findskill.ai | [claude-managed-agents-explained](https://findskill.ai/blog/claude-managed-agents-explained/) | $0.08/hr Managed Agents explainer |
| ClaudeAI.dev | [managed-agents-launch](https://claudeai.dev/blog/claude-managed-agents-what-just-launched/) | Launch coverage |
| Toolworthy | [claude-managed-agents](https://www.toolworthy.ai/tool/claude-managed-agents) | Review and setup guide |
| Medium @unicodeveloper | [managed-agents-honest-review](https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14) | Honest pros/cons |
| Medium @lmpo | [unveiling-agent-skill](https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71) | Standard analysis |
| Wikipedia | [Model Context Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) | Background reference |
| DEV Community | [skills-vs-mcp-servers](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Developer community guide |
| DEV Community | [skills-plugins-guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best skills and plugins guide |
| DEV Community | [slash-commands-skills](https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865) | Custom slash commands tutorial |
| Smart Webtech | [workflows-best-practices](https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/) | Workflows best practices |
| DevToolPicks | [skills-vs-mcp-vs-plugins](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Comparison guide |
| Geeky Gadgets | [mcp-skills-hooks-guide](https://www.geeky-gadgets.com/claude-code-mcp-plugins-explained/) | MCP vs Skills vs Hooks explained |
| Agensi.io | [plugins-vs-skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Plugins vs Skills |
| Agensi.io | [agent-skills-open-standard](https://www.agensi.io/learn/agent-skills-open-standard) | Open standard explainer |
| Redwerk | [best-claude-code-plugins](https://redwerk.com/blog/best-claude-code-plugins/) | 7 best plugins guide |
| TurboDocx | [skills-plugins-mcp](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Skills/plugins/MCP roundup |
| Mejba.me | [top-10-skills-plugins-clis](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 list |
| Raxxo | [best-skills-plugins](https://raxxo.shop/blogs/lab/best-claude-code-skills-plugins-2026-guide) | Best skills and plugins |
| Claude Marketplaces | [claudemarketplaces.com](https://claudemarketplaces.com/) | Claude-specific marketplace directory |
| SkillsMP | [skillsmp.com](https://skillsmp.com/) | 425,000+ skills marketplace |
| LobeHub | [lobehub.com/skills](https://lobehub.com/skills) | 169,739 skills cross-platform |
| AgentSkills.io | [agentskills.io](https://agentskills.io/home) | Agent skills overview hub |
| AgentSkillExchange | [agentskillexchange.com](https://agentskillexchange.com/) | Emerging marketplace |
| VirtualUncle | [skills-sh-guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | skills.sh guide |
| Toolworthy | [skills-sh-review](https://www.toolworthy.ai/tool/skills-sh) | skills.sh review |
| skills.sh | [find-skills page](https://skills.sh/vercel-labs/skills/find-skills) | Top skill listing |
| Tessl | [find-skills registry](https://tessl.io/registry/skills/github/vercel-labs/skills/find-skills) | Registry entry |
| Developers Digest | [hn-ai-coding-agents](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | HN trends on AI agents |
| Code With Andrea | [january-2026-newsletter](https://codewithandrea.com/newsletter/january-2026/) | AI agents January 2026 roundup |
| LinkedIn | [claude-code-survival-guide](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) | Survival guide article |
| mcp.so | [dxt](https://mcp.so/dxt) | DXT directory |
| desktopextensions.com | [desktopextensions.com](https://www.desktopextensions.com/) | DXT resource site |
| Socket.dev | [socket-mcp-desktop](https://socket.dev/blog/introducing-socket-mcp-for-claude-desktop) | Socket MCP security extension |
| Glama | [getting-started-dxt](https://glama.ai/blog/2025-07-11-getting-started-with-mcp-desktop-extensions-dxt-in-claude-desktop) | DXT getting started guide |
| MCPMarket | [lazy-load-server](https://mcpmarket.com/server/lazy-load) | Lazy-load MCP server listing |
| MCPPlayground | [setup-mcp-claude-desktop](https://mcpplaygroundonline.com/blog/how-to-setup-mcp-claude-desktop) | Claude Desktop MCP setup |
| ToolRadar | [claude-desktop-mcp-setup](https://toolradar.com/blog/claude-desktop-mcp-server-setup) | MCP server setup guide |
| TokenMix | [mcp-servers-list-2026](https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory) | 70+ production MCP servers |
| DeployHQ | [best-mcp-servers-web-dev](https://www.deployhq.com/blog/best-mcp-servers-for-web-developers) | Best MCP for web developers |
| SystemPrompt.io | [claude-code-mcp-extensions](https://systemprompt.io/guides/claude-code-mcp-servers-extensions) | MCP servers guide |
| claudefa.st | [cursor-mcp-setup](https://claudefa.st/blog/tools/mcp-extensions/cursor-mcp-setup) | Cursor MCP setup |
| Chris Ayers | [agent-skills-plugins-marketplace](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Complete guide |
| ChatPRD | [claude-ai-workflows](https://www.chatprd.ai/how-i-ai/workflows/tool/claude) | Claude workflows how-to |
| Udemy | [claude-code-bootcamp](https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/) | 2026 bootcamp course |
| Yahoo Finance | [aaif-mcp-summit-news](https://finance.yahoo.com/news/agentic-ai-foundation-unveils-mcp-140000965.html) | Summit news |
| Kestra | [plugin-ai/tool](https://kestra.io/plugins/plugin-ai/tool) | Plugin AI tool reference |
| Kestra | [1-0 launch](https://kestra.io/1-0) | Kestra 1.0 announcement |
| Kestra | [ai-tools](https://kestra.io/docs/ai-tools) | AI tools overview |
| Kestra | [ssemcpclient](https://kestra.io/plugins/plugin-ai/tool/io.kestra.plugin.ai.tool.ssemcpclient) | SSE MCP client plugin |
| Kestra | [aiagent plugin](https://kestra.io/plugins/plugin-ai/agent/io.kestra.plugin.ai.agent.aiagent) | AI agent plugin |
| LinkedIn (svpino) | [mcp-agents-post](https://www.linkedin.com/posts/svpino_how-to-use-mcp-servers-from-a-custom-ai-agent-activity-7313596149448265732-FR59) | Custom AI agent + MCP |
| Composio | [youtube-framework-claude](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration |
| GitHub Gist | [5-mcp-servers](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) | 5 essential MCP servers |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Unknown | The Ultimate Claude Code Guide \| MCP, Skills & More | N/A | N/A | No | [youtube.com](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| Ansh Mehra | Claude Plugins & Skills Tutorial (All Updates Combined) | N/A | N/A | No | [youtube.com](https://www.youtube.com/watch?v=6EFOT6hjvAU) |
| Unknown | Meta Ads CLI + MCP: Complete Setup Guide | N/A | N/A | No | [youtube.com](https://www.youtube.com/watch?v=mcT9f3JjYho) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| N/A | Show HN: LangAlpha – what if Claude Code was built for Wall Street? | N/A | N/A | Claude Code adapted for financial/trading workflows | [news.ycombinator.com](https://news.ycombinator.com/item?id=47766370) |

**GitHub:**
| Repo | Description | URL |
|------|-------------|-----|
| jeremylongshore/claude-code-plugins-plus-skills | 423 plugins, 2,849 skills, 177 agents; tonsofskills.com + ccpi CLI | [GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) |
| vercel-labs/skills | npx skills CLI; powers skills.sh | [GitHub](https://github.com/vercel-labs/skills) |
| anthropics/skills | Official Anthropic skills repo with SKILL.md spec | [GitHub](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md) |
| anthropics/dxt | Desktop Extensions (.dxt) spec | [GitHub](https://github.com/anthropics/dxt) |
| modelcontextprotocol/mcpb | MCP Bundle (.mcpb) successor to .dxt | [GitHub](https://github.com/modelcontextprotocol/mcpb) |
| modelcontextprotocol/modelcontextprotocol | Discussion #2585: Skills Over MCP Office Hours | [GitHub](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585) |
| wshobson/agents | Multi-agent orchestration for Claude Code | [GitHub](https://github.com/wshobson/agents) |
| FlorianBruniaux/claude-code-ultimate-guide | Agent teams workflow documentation | [GitHub](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md) |
| milisp/awesome-claude-dxt | Awesome Claude Desktop Extensions collection | [GitHub](https://github.com/milisp/awesome-claude-dxt) |
| samihalawa/awesome-claude-dxt | 500+ extensions collection | [GitHub](https://github.com/samihalawa/awesome-claude-dxt) |
| voicetreelab/lazy-mcp | MCP proxy with lazy loading support | [GitHub](https://github.com/voicetreelab/lazy-mcp) |
| PeterCha90/mcp-lazy-load | MCP lazy load tools | [GitHub](https://github.com/PeterCha90/mcp-lazy-load) |
| openai/codex Issue #9266 | Feature request: lazy MCP loading for Codex | [GitHub](https://github.com/openai/codex/issues/9266) |
| kestra-io/plugin-ai | Kestra AI plugin suite | [GitHub](https://github.com/kestra-io/plugin-ai) |
| kestra-io/mcp-server-python | Kestra Python MCP server | [GitHub](https://github.com/kestra-io/mcp-server-python) |
| quemsah/awesome-claude-plugins | Claude plugin adoption metrics | [GitHub](https://github.com/quemsah/awesome-claude-plugins) |
| JCodesMore/youtube-mcp | YouTube research plugin for Claude Code | [GitHub](https://github.com/JCodesMore/youtube-mcp) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ — │ —  (not surfaced)
├─ 🔵 X: 0 posts │ — │ —  (not crawled)
├─ 🔴 YouTube: 3 videos │ N/A views │ 0 with transcripts
├─ 🟢 HN: 1 thread │ N/A points │ N/A comments
├─ 🟣 TikTok: 0 videos │ —
├─ 🩷 Instagram: 0 reels │ —
├─ 🦋 Bluesky: 0 posts │ —
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 100+ pages
└─ 🗣️ Top voices: @AnshMehra (YouTube), Pedro Rodrigues/Supabase (MCP Dev Summit) │ r/— (no Reddit data)
```

---

## Data Gaps

- **Reddit**: No direct Reddit threads were surfaced in searches. Discussions about Claude Code skills and MCP are highly active in r/ClaudeAI, r/LocalLLM, and r/MachineLearning based on community references, but these were not retrieved.
- **X/Twitter**: Not crawled in this run. High-volume discussion expected from AI developers.
- **TikTok / Instagram / Bluesky**: No results found; likely minimal coverage on these platforms for this technical topic.
- **Polymarket**: No prediction markets on MCP/skills ecosystem found.
- **YouTube engagement metrics**: View and like counts were not retrieved; 3 videos identified but not quantified.
- **HN engagement**: Only 1 direct HN thread found (LangAlpha); many HN discussions are referenced in secondary sources but not directly retrieved.
- **Marketplace accuracy**: Skill/plugin counts vary significantly across sources (425K on SkillsMP vs. 90K on skills.sh vs. 2,849 on tonsofskills.com) — reflecting different scopes (all agents vs. CLI-tracked vs. Claude-specific).
- **Coverage estimate**: ~70% of the web signal, ~20% of social signal, ~10% of video signal.

---

## Key Quotes

> "MCP is the pilot, skills are the co-pilot." — Pedro Rodrigues, Supabase, MCP Dev Summit 2026 ([obot.ai](https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/))

> "Agents are very lazy to go beyond their training data, and they need a push to search the web or find the right information." — Pedro Rodrigues, Supabase ([GitHub Discussion #2585](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585))

> "Connect it to your AI coding agent once; from that point, the agent can discover plugins, inspect task schemas, and fetch Blueprint YAML without ever leaving the conversation." — Kestra team ([kestra.io](https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints))

> "If Skills are individual recipe cards and MCP is the kitchen plumbing, a Plugin is the full kitchen, stocked and ready to cook." — Community guide ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "Anthropic's Agent Skills spec became the universal standard for AI coding tools in under 90 days." — [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

> "Teams that figure out skills-plus-MCP early, with governance built in, will ship safer agents faster than teams treating skills as a separate track or as a replacement for MCP." — [obot.ai](https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/)

> "MCP Tool Search is Claude Code's new lazy loading system for MCP servers that loads a lightweight search index and fetches tool details on-demand when you actually need them." — [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

> "A skill written for Claude Code can be copied into Codex's skills directory and it works." — [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)
