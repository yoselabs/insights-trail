# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-20
**Query type:** GENERAL
**Sources:** Hacker News, Web, YouTube, Polymarket, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 12 threads | est. 2,400+ points, 800+ comments | Mix of Show HN launches and discussions |
| YouTube | 1 video | est. 50K+ views | April 2026 roundup |
| Polymarket | 107 markets | $multi-M volume | AI prediction markets active |
| Web | 80+ pages | — | via WebSearch; blogs, docs, news, GitHub |

*Reddit: search returned no direct thread URLs (community discussion captured via blog aggregations). X/Twitter, TikTok, Instagram, Bluesky: no data returned.*

---

## Synthesized Findings

### 1. The Claude Code Extension Taxonomy Has Crystallized

The three-layer extension model for Claude Code stabilized in early 2026 and is now widely documented. **Skills** are SKILL.md markdown files teaching Claude procedural knowledge — lightweight (~30-50 tokens each), loaded on-demand via three-tier progressive disclosure, no external process required. **MCP Servers** are standalone processes exposing tools over the Model Context Protocol — each starts a subprocess, connects Claude to external systems (GitHub, databases, APIs), and runs with its own permission scope. **Plugins** are installable bundles packaging skills, MCP servers, slash commands, hooks, agents, LSP servers, and monitors together into a single distributable unit.

The distinction matters practically: as one DEV Community post put it, "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." The recommended default loadout is 2–3 MCP servers (GitHub, Filesystem, one domain-specific) plus custom skills for team workflow.

Key sources: [claudemarketplaces.com](https://claudemarketplaces.com/) · [alexop.dev full-stack guide](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [morphllm complete guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [devtoolpicks comparison](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) · [skiln decision guide](https://skiln.co/blog/claude-code-plugins-vs-skills-vs-mcp-decision-guide) · [official skills docs](https://code.claude.com/docs/en/skills) · [official plugins reference](https://code.claude.com/docs/en/plugins-reference) · [producttalk guide](https://www.producttalk.org/how-to-use-claude-code-features/) · [turbodocx roundup](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers)

Discussed on: Hacker News ([Claude Skills vs. MCP: Complementary Philosophies](https://news.ycombinator.com/item?id=45766686)), Web

---

### 2. Marketplace Explosion: Competing Directories, Fragmented Discovery

The agent skills marketplace landscape exploded in early 2026 with no clear winner. Key platforms:

- **[claudemarketplaces.com](https://claudemarketplaces.com/)** — community-curated directory with ratings and install counts; 150+ skills as of March 2026; sorted by installs and GitHub stars
- **[claude-plugins.dev](https://claude-plugins.dev/)** — community registry with CLI; separate [skills browsing](https://claude-plugins.dev/skills)
- **[skills.sh](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem)** (Vercel) — launched January 20, 2026; reached 20,000 installs within 6 hours; tracks 90,000+ skills across 19 AI agents (Claude Code, Cursor, Codex, GitHub Copilot, Windsurf, Gemini, and more); install: `npx skills add <package>`
- **[SkillsMP](https://skillsmp.com)** — 425,000+ skills (500,000+ aggregated from GitHub); largest by raw numbers; built around the open SKILL.md standard
- **[tonsofskills.com](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)** — open-source marketplace via the **ccpi** CLI (`pnpm add -g @intentsolutionsio/ccpi`); 423 plugins, 2,849 skills, 177 agents; includes SaaS packs for fly.io, granola, clickup, lucidchart
- **[agentskillexchange.com](https://agentskillexchange.com/)** — Agent Skill Exchange marketplace
- **[SkillHub](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)** — ~7,000 curated skills, AI-evaluated on practicality, clarity, automation, quality, impact
- **[mcp.so](https://mcp.so)** — 20,222 MCP servers collected
- **[mcpmarket.com](https://mcpmarket.com/)** — focused MCP server directory including the [Hacker News Explorer Skill](https://mcpmarket.com/tools/skills/hacker-news-explorer)
- **[mcpservers.org](https://mcpservers.org)** — Awesome MCP Servers
- **[LobeHub MCP](https://lobehub.com/mcp)** — MCP Toolbox for Databases (enterprise focus)
- **[apigene.ai marketplace guide](https://apigene.ai/blog/mcp-marketplace)**
- **[mcp-marketplace.io](https://mcp-marketplace.io/blog/best-mcp-servers-developers)** — includes security scores for server credential handling

GitHub Awesome Lists are also massive discovery vectors: [awesome-mcp-servers](https://mcpservers.org) (84K+ stars), [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-plugins) (52K+ stars), [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) (1,000+), [anthropics/skills](https://github.com/anthropics/skills) (120K stars, 14K forks — April 16, 2026).

One community effort — [K-Dense-AI/claude-skills-mcp](https://github.com/K-Dense-AI/claude-skills-mcp) — created a dedicated MCP server for searching Claude Agent Skills with vector search, solving the meta-problem of discovering skills via Claude itself.

Framing: "Agent Skills Are the New npm" ([buildmvpfast](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)) — the package manager paradigm applied to AI agent capabilities.

Discussed on: Web, Hacker News ([Agent Skills – Open Trusted Catalog](https://news.ycombinator.com/item?id=46692865))

---

### 3. The SKILL.md Open Standard and Cross-Agent Compatibility

Anthropic published the **Agent Skills specification** as an open standard in December 2025. The spec lives at [anthropics/skills/spec/agent-skills-spec.md](https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md). OpenAI adopted the same SKILL.md format for Codex CLI and ChatGPT shortly after, creating a cross-agent compatibility layer.

As of March 2026, the same skill files work across Claude Code, Cursor, Gemini CLI, Codex CLI, and Antigravity IDE. Skills.sh explicitly supports 19 agents. The SKILL.md format: YAML frontmatter (config: name, description, triggers, permissions) + markdown content (instructions to Claude).

Anthropic's official skills repo ([anthropics/skills](https://github.com/anthropics/skills/tree/main)) is source-available (not fully open source) and serves as the canonical reference. It includes a meta-skill: [skill-creator](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md) — a skill for creating skills. The [claude-api skill](https://github.com/anthropics/skills/blob/main/skills/claude-api/SKILL.md) covers managed agents environments.

Third-party collections: [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (232+ skills), [agentskills/agentskills](https://github.com/agentskills/agentskills) (spec and docs), [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) (1,000+ curated).

Hacker News thread "Claude Skills are awesome, maybe a bigger deal than MCP" ([HN #45619537](https://news.ycombinator.com/item?id=45619537)) sparked wide discussion. Original HN "Claude Skills" thread: [HN #45607117](https://news.ycombinator.com/item?id=45607117).

Platform docs: [Agent Skills overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Agent Skills in the SDK](https://platform.claude.com/docs/en/agent-sdk/skills) · [Vercel Agent Skills docs](https://vercel.com/docs/agent-resources/skills) · [Microsoft Azure SRE Agent plugin marketplace](https://learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace) · [.NET Skills blog](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/)

Discussed on: Hacker News, Web

---

### 4. MCP Protocol Governance: Linux Foundation and AAIF

The biggest structural news in the MCP ecosystem came December 9, 2025: Anthropic donated MCP to the **Agentic AI Foundation (AAIF)**, a directed fund under the Linux Foundation. This event is widely cited across April 2026 content as the moment MCP went from "Anthropic's protocol" to "the universal interface."

- Co-founding organizations: Anthropic, Block (goose), OpenAI (AGENTS.md)
- Platinum members: AWS, Anthropic, Block, Bloomberg, Cloudflare, Google, Microsoft, OpenAI
- Founding projects: MCP, goose (Block), AGENTS.md (OpenAI)
- MCP stats at time of donation: 97M+ monthly SDK downloads, 10,000+ active servers

Projects maintain full autonomy over technical direction; AAIF governs budget, membership, and strategic investments.

Sources: [MCP blog announcement](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) · [Linux Foundation press](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation) · [Anthropic announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) · [AAIF site](https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/) · [The New Stack](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/) · [OpenAI announcement](https://openai.com/index/agentic-ai-foundation/) · [GitHub Blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/) · [TechCrunch](https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/) · [PR Newswire](https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md-302636897.html) · [InfoQ](https://www.infoq.com/news/2025/12/agentic-ai-foundation/)

In April 2026, **OAuth 2.1 authorization** (with incremental scope consent) was added to the MCP spec — a significant security improvement.

Discussed on: Web broadly

---

### 5. MCP Tool Search: Solving Context Window Bloat

One of the most discussed April 2026 developments: Claude Code shipped **MCP Tool Search** (lazy loading for MCP tools) in version 2.1.7. Previously, loading 50+ MCP tools consumed ~77K tokens before any conversation started. MCP Tool Search reduces this to ~8.7K tokens — a **95% reduction**.

How it works: Claude Code builds a lightweight index of tool names and descriptions at startup. Full tool schemas fetch on-demand only when Claude determines a tool is needed for the current request. Loaded tools stay available for the session.

Triggers automatically when MCP tool descriptions would exceed 10% of context window. Enabled by default — no opt-in.

VentureBeat coverage: [Claude Code just got updated with one of the most-requested user features](https://venturebeat.com/orchestration/claude-code-just-got-updated-with-one-of-the-most-requested-user-features)

GitHub feature request threads that preceded the fix: [anthropics/claude-code #7336](https://github.com/anthropics/claude-code/issues/7336) · [#11364](https://github.com/anthropics/claude-code/issues/11364) · [#20421](https://github.com/anthropics/claude-code/issues/20421)

Microsoft VS Code is implementing the same approach: [vscode #288310](https://github.com/microsoft/vscode/issues/288310). OpenAI Codex has an open issue: [codex #9266](https://github.com/openai/codex/issues/9266).

Guides: [claudefa.st MCP Tool Search](https://claudefa.st/blog/tools/mcp-tools/mcp-tool-search) · [JP Caparas Medium](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc) · [atcyrus context pollution guide](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) · [forbiddentrust analysis](https://forbiddentrust.com/codex/mcp-tool-search-context-fix)

Discussed on: Web, Hacker News

---

### 6. Security Crisis: Supply Chain Attacks and Vulnerable Servers

Security is the most alarming theme in the ecosystem as of April 2026. Key findings from multiple research efforts:

**MCP server vulnerabilities (scan of 8,000+ servers):**
- 36.7% vulnerable to SSRF
- 43% unsafe command execution paths
- 41% of official registry servers had zero authentication
- Trend Micro: 492 servers with zero client authentication and zero traffic encryption

**Agent skill vulnerabilities (scan of 42,447 skills):**
- 26.1% contained at least one security vulnerability
- 14 distinct patterns: prompt injection, data exfiltration, privilege escalation, supply chain risks

**Critical incidents:**
- **January 2026 supply chain attack:** coordinated campaign compromised 1,184 skills in a major community marketplace (~1 in 5 packages), delivering credential-theft payload. Publishing barrier: only a one-week-old GitHub account required; no code signing, security review, or sandboxing.
- **CVE-2025-59536 (CVSS 8.7):** Check Point Research (February 25, 2026) disclosed two configuration injection flaws in Claude Code. Hook injection via malicious `.claude/settings.json` → RCE when developer opens project.
- **MCP "by design" flaw:** Unsanitized commands can execute silently → full system compromise.

**Security tooling emerging:**
- [SkillRisk.org](https://skillrisk.org/) — free AI agent skill security scanner
- Snyk + Vercel partnership: [securing the agent skill ecosystem](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/)
- RSAC 2026 highlight: MCP and supply chain risks were top conference concerns: [Futuriom RSAC coverage](https://www.futuriom.com/articles/news/key-trends-from-rsac-agentic-ai-mcp-and-supply-chain-risks/2026/03)

**Academic research:**
- arXiv 2604.02837v1 (April 2026): [Towards Secure Agent Skills: Architecture, Threat Taxonomy, and Security Analysis](https://arxiv.org/html/2604.02837v1)
- arXiv 2601.10338 (January 2026): [Agent Skills in the Wild: An Empirical Study of Security](https://arxiv.org/pdf/2601.10338)

Additional coverage: [SecurityWeek MCP design flaw](https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/) · [Practical DevSecOps guide](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) · [blog.cyberdesserts.com](https://blog.cyberdesserts.com/ai-agent-security-risks/) · [aembit guide](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) · [gentic.news crisis coverage](https://gentic.news/article/mcp-security-crisis-43-of-servers) · [Red Hat developer article](https://developers.redhat.com/articles/2026/03/10/agent-skills-explore-security-threats-and-controls)

Discussed on: Web, Hacker News ([AGENTS.md and code map discussion](https://news.ycombinator.com/item?id=46398957))

---

### 7. Notable Show HN Launches and Hacker News Community Activity

The Hacker News community has been a primary launchpad for agent skill tooling in 2026:

- **[Agent37](https://news.ycombinator.com/item?id=46422134)** — Monetize Claude skills via shareable links; addresses the problem that skills require manual setup by end users
- **[Agnix](https://news.ycombinator.com/item?id=46983879)** — Linter for AI agent configs (Claude.md, skills, MCP, hooks); catches kebab-case naming violations, deprecated transport types
- **[FEC Claude Code Plugin](https://news.ycombinator.com/item?id=46869575)** — Federal Election Commission data as Claude plugin + skill + MCP server
- **[Real-time dashboard for Claude Code agent teams](https://news.ycombinator.com/item?id=47602986)** — Key finding: removing unnecessary plugins significantly improved Claude performance
- **[Playwright Skill](https://news.ycombinator.com/item?id=45642911)** — Specifically less context than playwright-MCP alternative (demonstrates skills vs MCP efficiency tradeoff)
- **[Stop Claude Code from forgetting everything](https://news.ycombinator.com/item?id=46426624)** — Shared memory layer skill creating persistent database across sessions
- **[LangAlpha](https://news.ycombinator.com/item?id=47766370)** — "Claude Code built for Wall Street"; auto-generates typed Python modules from MCP schemas at workspace init
- **[Destructive command catcher plugin](https://news.ycombinator.com/item?id=46388882)** — Catches destructive Git and filesystem commands
- **[AGENTS.md playbook](https://news.ycombinator.com/item?id=46398957)** — AI collaboration playbook template
- **[Hacking with Claude Pro and MCP](https://news.ycombinator.com/item?id=43410866)** — Earlier tutorial that drove MCP awareness
- **[MCP must-adds for coding](https://news.ycombinator.com/item?id=44347116)** — Community recommendations thread
- **[Trading with Claude and writing your own MCP server](https://news.ycombinator.com/item?id=44061614)** — Polymarket/trading use case

Also: [claudepluginhub.com](https://www.claudepluginhub.com/plugins/caobach369-last30days) lists plugins including last30days; [mcpmarket.com skills](https://mcpmarket.com/tools/skills/hacker-news-explorer) includes HN Explorer skill.

---

### 8. Top MCP Servers in 2026

Most-cited must-have MCP servers across a dozen blog roundups:

1. **GitHub MCP** — direct repo access, issue/PR management, autonomous contributor capability
2. **Filesystem MCP** — foundational; configurable access boundaries
3. **[Exa MCP](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers)** — most-used AI-native search server in 2026 by large margin
4. **Notion MCP** — knowledge base; exposes pages, databases, blocks as tools
5. **Taskade MCP** — workspace memory + agent intelligence; described as "strongest production option in 2026"
6. **PostgreSQL / SQLite MCP** — database connectivity
7. **Reddit MCP** — browse posts, search, analyze users; no API keys ([karanb192/reddit-mcp-buddy](https://github.com/karanb192/reddit-mcp-buddy)); also available via [LobeHub](https://lobehub.com/mcp/enescinar-reddit-mcp), [Composio](https://composio.dev/toolkits/reddit/framework/claude-code), [ClaudeLog](https://claudelog.com/claude-code-mcps/reddit-mcp/)
8. **YouTube MCP** — search, transcripts, channel browsing ([JCodesMore/youtube-mcp](https://github.com/JCodesMore/youtube-mcp)); also via [Composio](https://composio.dev/toolkits/youtube/framework/claude-code)
9. **Polymarket MCP** — prediction market data and trading ([Polymarket/agents](https://github.com/Polymarket/agents)); [AI Engineer's Guide](https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560)

Blog roundups: [claudefa.st 50+](https://claudefa.st/blog/tools/mcp-extensions/best-addons) · [builder.io best 2026](https://www.builder.io/blog/best-mcp-servers-2026) · [firecrawl dev top 10](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) · [stackgen platform engineers](https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026) · [k2view top 15](https://www.k2view.com/blog/awesome-mcp-servers) · [bannerbear top 8](https://www.bannerbear.com/blog/8-best-mcp-servers-for-claude-code-developers-in-2026/) · [taskade top 15](https://www.taskade.com/blog/mcp-servers) · [toolradar](https://toolradar.com/blog/best-mcp-servers-claude-code) · [evomap top 15](https://evomap.ai/blog/best-mcp-servers-for-claude-code-2026) · [houtini desktop](https://houtini.com/the-best-mcps-for-claude-desktop/) · [emergingai top 32](https://emergingai.substack.com/p/top-32-mcp-servers-to-make-claude) · [truefoundry](https://www.truefoundry.com/blog/best-mcp-servers-for-claude-code) · [roobia medium](https://roobia.medium.com/the-10-must-have-mcp-servers-for-claude-code-2025-developer-edition-43dc3c15c887) · [thesys.dev](https://www.thesys.dev/blogs/best-mcp-servers)

---

### 9. AI Agents on Polymarket and Prediction Markets

Polymarket has become a live laboratory for agent skill monetization and financial autonomy:

- 107 live AI prediction markets as of April 19, 2026 ([Polymarket AI](https://polymarket.com/ai) · [tech markets](https://polymarket.com/tech) · [predictions](https://polymarket.com/predictions/ai))
- Most active market: "Which company has the best AI model end of April?" — Anthropic at 93% odds
- 30%+ of Polymarket wallets already use AI agents (LayerHub analytics)
- Olas/Polystrat agent: 4,200+ trades within one month, up to 376% returns on individual trades
- CoinDesk (March 15, 2026): ["AI agents are quietly rewriting prediction market trading"](https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading)
- Tutorial: [Building AI Agents for Polymarket](https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/)
- Analysis: [CLIs as Agent-Native Interfaces: Polymarket CLI, GitHub CLI, and MCP](https://blockchain.news/ainews/clis-as-agent-native-interfaces-2026-analysis-on-polymarket-cli-github-cli-and-mcp-for-ai-automation)
- Python app example: [Polymarket Intelligence App via Agentic Coding](https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477?gi=f4f8a5d90ae7)
- [AI Agent Marketplaces 2026: Discovery and Distribution](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

---

### 10. Community Resources and Developer Education

Deep-dive technical content is abundant:

- [leehanchung.github.io: Claude Agent Skills First Principles Deep Dive](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/) — three-tier loading mechanism explained
- [kjetilfuras.com: Write Claude Code Agent Skills That Actually Work](https://kjetilfuras.com/claude-code-agent-skills/)
- [explainx.ai: What are agent skills? Complete guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide)
- [virtualuncle.com: Skills.sh Guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)
- [termdock.com: Agent Skills Guide 2026: Build, Share & Secure](https://www.termdock.com/en/blog/agent-skills-guide)
- [chris-ayers.com: Agent Skills, Plugins and Marketplace: The Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)
- [ado.im: The Claude Customization Stack: MCP vs Skills vs Plugins](https://www.ado.im/posts/claude-customization-stack-mcp-skills-plugins/)
- [scriptbyai.com: The Ultimate Claude Code Resource List (2026 Edition)](https://www.scriptbyai.com/claude-code-resource-list/)
- [releasebot.io: Claude Code Release Notes April 2026](https://releasebot.io/updates/anthropic/claude-code)
- Medium community: [Jonathan Fulton: "Agent Skills: The Cheat Codes for Claude Code" (April 2026)](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) · [unicodeveloper: 10 Must-Have Skills (March 2026)](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) · [Mohit Aggarwal: 10 Claude Plugins You Actually Need (April 2026)](https://medium.com/@mohit15856/10-claude-plugins-you-actually-need-in-2026-with-full-setup-guides-136f7d879c37)
- DEV Community: [raxxostudios best plugins guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) · [williamwangai skills vs MCP](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k)
- [self.md guides](https://self.md/guides/best-claude-code-plugins/) · [composio top plugins](https://composio.dev/content/top-claude-code-plugins) · [firecrawl top 10 plugins](https://www.firecrawl.dev/blog/best-claude-code-plugins)
- [mejba.me top 10 skills CLIs](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) · [popularaitools roundup](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026)
- [InfoQ: Vercel Skills.sh launch](https://www.infoq.com/news/2026/02/vercel-agent-skills/) · [toolworthy.ai skills.sh review](https://www.toolworthy.ai/tool/skills-sh)
- [brightcoding.dev: Claude Code Plugins Plus 270+ tools](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development)
- Video toolkit: [wilwaldon/Claude-Code-Video-Toolkit](https://github.com/wilwaldon/Claude-Code-Video-Toolkit)

---

## Cross-Source Patterns

**Pattern 1: Skills vs MCP Is the Defining Architecture Question of 2026**
Appearing on: Web (dozens of blog posts), Hacker News (multiple threads)
The debate about when to use skills vs MCP vs plugins is the most-discussed topic in the ecosystem. Nearly every developer blog published in March–April 2026 addresses this taxonomy. Consensus: use MCP for external connectivity, skills for procedural knowledge, plugins for team-wide distribution.
> "Claude Code ships with multiple ways to extend its capabilities. MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." — [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/)

**Pattern 2: Security Is the Ecosystem's Achilles Heel**
Appearing on: Web (SecurityWeek, Red Hat, arXiv, Practical DevSecOps), Hacker News
Multiple independent scans converge on alarming numbers: 36.7% SSRF in MCP servers, 26.1% vulnerability rate in skills, and a real-world supply chain attack compromising ~20% of one marketplace's catalog. The community is reacting with tooling (SkillRisk.org, Snyk+Vercel) but the governance gap remains.
> "The barrier to publishing was a GitHub account one week old—no code signing, security review, or default sandbox." — [blog.cyberdesserts.com](https://blog.cyberdesserts.com/ai-agent-security-risks/)

**Pattern 3: Context Window Bloat Was a Blocker; MCP Tool Search Is the Fix**
Appearing on: Web (VentureBeat, claudefa.st, multiple guides), GitHub issues
Claude Code 2.1.7's MCP Tool Search is widely covered as a watershed fix. The 95% context reduction unlocked running many MCP servers simultaneously, which was previously impractical.
> "95% reduction in initial context consumption for users with multiple MCP servers." — [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

**Pattern 4: SKILL.md Is Becoming the Universal Agent Extension Format**
Appearing on: Web, Hacker News
The same SKILL.md files now work across 19+ agents. Skills.sh and SkillsMP both aggregate across Claude, Codex, Cursor, Gemini, and more. This cross-agent portability is driving rapid ecosystem growth.
> "It tracks actual install counts across 90,000+ skills and supports 19 different AI agents." — [reading.sh](https://reading.sh/vercel-just-launched-skills-sh-and-it-already-has-20k-installs-c07e6da7e29e?gi=f4f8a5d90ae7)

**Pattern 5: AI Agents Are Taking Over Polymarket**
Appearing on: Polymarket, Web (CoinDesk, blockchain.news)
30%+ of Polymarket wallets use AI agents. The Polymarket MCP server is a live production integration with real money. CoinDesk covered this as a quiet revolution in trading.
> "More than 30% of wallets on Polymarket are already using AI agents." — [CoinDesk](https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Agent37 – Monetize your Claude skills | est. 300+ | est. 80+ | "addresses monetization without requiring users to manually configure Claude Code" | [HN #46422134](https://news.ycombinator.com/item?id=46422134) |
| — | Claude Skills are awesome, maybe a bigger deal than MCP | est. 500+ | est. 150+ | "three-tier loading mechanism to avoid context window bloat" | [HN #45619537](https://news.ycombinator.com/item?id=45619537) |
| — | Agnix – lint your AI agent configs | est. 200+ | est. 60+ | "catches kebab-case naming violations, deprecated transport types" | [HN #46983879](https://news.ycombinator.com/item?id=46983879) |
| — | Claude Skills | est. 400+ | est. 120+ | Original discussion thread | [HN #45607117](https://news.ycombinator.com/item?id=45607117) |
| — | Agent Skills – Open Trusted Catalog | est. 250+ | est. 70+ | "aggregates from Anthropic, OpenAI, GitHub, Vercel into one JSON catalog" | [HN #46692865](https://news.ycombinator.com/item?id=46692865) |
| — | Which MCP servers are Claude Code must-adds | est. 350+ | est. 100+ | Community recommendation thread | [HN #44347116](https://news.ycombinator.com/item?id=44347116) |
| — | Trading with Claude, writing your own MCP server | est. 280+ | est. 80+ | Financial/trading use case | [HN #44061614](https://news.ycombinator.com/item?id=44061614) |
| — | Claude Skills vs. MCP: Complementary Philosophies | est. 320+ | est. 90+ | "Skills can orchestrate multiple MCP servers" | [HN #45766686](https://news.ycombinator.com/item?id=45766686) |
| — | FEC Claude Code Plugin and Agent Skill and MCP | est. 150+ | est. 40+ | Government/civic data use case | [HN #46869575](https://news.ycombinator.com/item?id=46869575) |
| — | Real-time dashboard for Claude Code agent teams | est. 200+ | est. 60+ | "removing unnecessary plugins improved Claude performance" | [HN #47602986](https://news.ycombinator.com/item?id=47602986) |
| — | Playwright Skill – Less context than playwright-MCP | est. 180+ | est. 50+ | Demonstrates skill vs MCP efficiency tradeoff | [HN #45642911](https://news.ycombinator.com/item?id=45642911) |
| — | LangAlpha – Claude Code for Wall Street | est. 250+ | est. 70+ | "auto-generates typed Python modules from MCP schemas" | [HN #47766370](https://news.ycombinator.com/item?id=47766370) |
| — | Stop Claude Code from forgetting everything | est. 220+ | est. 65+ | Persistent memory across sessions | [HN #46426624](https://news.ycombinator.com/item?id=46426624) |
| — | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | est. 300+ | est. 90+ | Early MCP awareness driver | [HN #43410866](https://news.ycombinator.com/item?id=43410866) |
| — | A plugin that catches destructive Git/filesystem commands | est. 160+ | est. 45+ | Safety-oriented plugin | [HN #46388882](https://news.ycombinator.com/item?id=46388882) |
| — | AGENTS.md and code map discussion | est. 140+ | est. 40+ | CLAUDE.md, Skills, Agents, MCP overview | [HN #46396930](https://news.ycombinator.com/item?id=46396930) |
| — | AGENTS.md collaboration playbook | est. 170+ | est. 50+ | AI collaboration template | [HN #46398957](https://news.ycombinator.com/item?id=46398957) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | est. 50K+ | est. 2K+ | Unknown | [youtube.com/watch?v=KjEFy5wjFQg](https://www.youtube.com/watch?v=KjEFy5wjFQg) |
| Novamira | A Free Powerful WordPress MCP (Claude Code + Novamira) | est. 20K+ | est. 800+ | Unknown | [youtube.com/watch?v=vSgw2cJ8lIE](https://www.youtube.com/watch?v=vSgw2cJ8lIE) |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Which company has the best AI model end of April? | Anthropic 93% | est. $500K+ | [polymarket.com/ai](https://polymarket.com/ai) |
| (107 total AI markets active April 19, 2026) | various | est. $multi-M | [polymarket.com/predictions/ai](https://polymarket.com/predictions/ai) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs | [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills) | Official skills documentation |
| Claude Code Docs | [code.claude.com/docs/en/plugins-reference](https://code.claude.com/docs/en/plugins-reference) | Official plugins reference |
| Claude Platform Docs | [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | Agent Skills API overview |
| Claude Platform Docs | [platform.claude.com/docs/en/agent-sdk/skills](https://platform.claude.com/docs/en/agent-sdk/skills) | Agent Skills in SDK |
| Anthropic GitHub | [github.com/anthropics/skills](https://github.com/anthropics/skills) | Official skills repo (120K stars) |
| Anthropic GitHub | [github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md](https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md) | The SKILL.md open standard spec |
| Anthropic Blog | [anthropic.com/news/donating-the-model-context-protocol…](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | MCP donation to AAIF |
| MCP Blog | [blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) | MCP → AAIF announcement |
| Linux Foundation | [linuxfoundation.org/press/…](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation) | AAIF formation press release |
| AAIF | [aaif.io/press/…](https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/) | AAIF official site |
| OpenAI | [openai.com/index/agentic-ai-foundation/](https://openai.com/index/agentic-ai-foundation/) | OpenAI AAIF announcement |
| GitHub Blog | [github.blog/open-source/maintainers/mcp-joins-the-linux-foundation…](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/) | Developer impact analysis |
| TechCrunch | [techcrunch.com/2025/12/09/openai-anthropic-and-block-join…](https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/) | News coverage |
| VentureBeat | [venturebeat.com/orchestration/claude-code-just-got-updated…](https://venturebeat.com/orchestration/claude-code-just-got-updated-with-one-of-the-most-requested-user-features) | MCP Tool Search coverage |
| SecurityWeek | [securityweek.com/by-design-flaw-in-mcp…](https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/) | MCP design flaw disclosure |
| Red Hat Developer | [developers.redhat.com/articles/2026/03/10/agent-skills-explore-security-threats](https://developers.redhat.com/articles/2026/03/10/agent-skills-explore-security-threats-and-controls) | Security threats and controls |
| arXiv | [arxiv.org/html/2604.02837v1](https://arxiv.org/html/2604.02837v1) | Formal security taxonomy (April 2026) |
| arXiv | [arxiv.org/pdf/2601.10338](https://arxiv.org/pdf/2601.10338) | Empirical security study (January 2026) |
| Vercel | [vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | Skills.sh launch announcement |
| InfoQ | [infoq.com/news/2026/02/vercel-agent-skills/](https://www.infoq.com/news/2026/02/vercel-agent-skills/) | Vercel skills.sh coverage |
| Reading.sh | [reading.sh/vercel-just-launched-skills-sh…](https://reading.sh/vercel-just-launched-skills-sh-and-it-already-has-20k-installs-c07e6da7e29e?gi=f4f8a5d90ae7) | 20K installs in 6 hours |
| Snyk | [snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) | Snyk+Vercel security partnership |
| Futuriom | [futuriom.com/articles/news/key-trends-from-rsac…/2026/03](https://www.futuriom.com/articles/news/key-trends-from-rsac-agentic-ai-mcp-and-supply-chain-risks/2026/03) | RSAC 2026 summary |
| SkillRisk | [skillrisk.org](https://skillrisk.org/) | Free skill security scanner |
| CoinDesk | [coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting…](https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading) | Agent trading on Polymarket |
| claudemarketplaces.com | [claudemarketplaces.com](https://claudemarketplaces.com/) | Largest curated plugin directory |
| claude-plugins.dev | [claude-plugins.dev](https://claude-plugins.dev/) | Community registry with CLI |
| claudefa.st | [claudefa.st/blog/tools/mcp-extensions/mcp-tool-search](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) | MCP Tool Search 95% context guide |
| claudefa.st | [claudefa.st/blog/tools/mcp-extensions/best-addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers |
| mcp.so | [mcp.so](https://mcp.so) | 20,222 MCP servers |
| mcpmarket.com | [mcpmarket.com](https://mcpmarket.com/) | MCP server directory |
| SkillsMP | [skillsmp.com](https://skillsmp.com) | 425K+ skills marketplace |
| tonsofskills.com | [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 423 plugins / 2,849 skills |
| Agent Skill Exchange | [agentskillexchange.com](https://agentskillexchange.com/) | Alternative marketplace |
| VoltAgent | [github.com/VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ curated skills |
| Vercel Labs | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) | npx skills CLI tool |
| Composio | [github.com/ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) | Curated plugin list |
| quemsah | [github.com/quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) | Automated adoption metrics |
| alirezarezvani | [github.com/alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) | 232+ cross-agent skills |
| agentskills org | [github.com/agentskills/agentskills](https://github.com/agentskills/agentskills) | Spec and documentation |
| K-Dense-AI | [github.com/K-Dense-AI/claude-skills-mcp](https://github.com/K-Dense-AI/claude-skills-mcp) | MCP server for searching skills |
| JCodesMore | [github.com/JCodesMore/youtube-mcp](https://github.com/JCodesMore/youtube-mcp) | YouTube MCP plugin |
| wilwaldon | [github.com/wilwaldon/Claude-Code-Video-Toolkit](https://github.com/wilwaldon/Claude-Code-Video-Toolkit) | Video production skills+MCP |
| karanb192 | [github.com/karanb192/reddit-mcp-buddy](https://github.com/karanb192/reddit-mcp-buddy) | Clean Reddit MCP server |
| Polymarket | [github.com/Polymarket/agents](https://github.com/Polymarket/agents) | AI agents for Polymarket |
| leehanchung | [leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/) | Deep dive: three-tier loading |
| alexop.dev | [alexop.dev/posts/understanding-claude-code-full-stack/](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Full stack architecture guide |
| morphllm | [morphllm.com/claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Complete guide 2026 |
| DEV Community | [dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best plugins guide |
| DEV Community | [dev.to/williamwangai/claude-code-skills-vs-mcp-servers…](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Skills vs MCP comparison |
| Medium (Fulton) | [medium.com/jonathans-musings/agent-skills-the-cheat-codes…](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | "Cheat Codes" framing (April 2026) |
| Medium (unicodeveloper) | [medium.com/@unicodeveloper/10-must-have-skills…](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 must-have skills (March 2026) |
| Medium (Aggarwal) | [medium.com/@mohit15856/10-claude-plugins-you-actually-need…](https://medium.com/@mohit15856/10-claude-plugins-you-actually-need-in-2026-with-full-setup-guides-136f7d879c37) | 10 Claude plugins (April 2026) |
| buildmvpfast | [buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) | "Agent Skills Are the New npm" |
| InfoQ | [infoq.com/news/2025/12/agentic-ai-foundation/](https://www.infoq.com/news/2025/12/agentic-ai-foundation/) | AAIF formation coverage |
| The New Stack | [thenewstack.io/anthropic-donates-the-mcp-protocol…](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/) | MCP donation coverage |
| PR Newswire | [prnewswire.com/news-releases/linux-foundation-announces…](https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md-302636897.html) | Official press release |
| Practical DevSecOps | [practical-devsecops.com/mcp-security-vulnerabilities/](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | MCP security guide |
| aembit | [aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) | Ultimate MCP security guide |
| gentic.news | [gentic.news/article/mcp-security-crisis-43-of-servers](https://gentic.news/article/mcp-security-crisis-43-of-servers) | MCP security crisis coverage |
| cyberdesserts | [blog.cyberdesserts.com/ai-agent-security-risks/](https://blog.cyberdesserts.com/ai-agent-security-risks/) | AI agent security risks 2026 |
| JP Caparas | [jpcaparas.medium.com/claude-code-finally-gets-lazy-loading…](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc) | Lazy loading explainer |
| atcyrus | [atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) | Context pollution guide |
| forbiddentrust | [forbiddentrust.com/codex/mcp-tool-search-context-fix](https://forbiddentrust.com/codex/mcp-tool-search-context-fix) | MCP Tool Search analysis |
| Bannerbear | [bannerbear.com/blog/8-best-mcp-servers-for-claude-code-developers-in-2026/](https://www.bannerbear.com/blog/8-best-mcp-servers-for-claude-code-developers-in-2026/) | Top 8 MCP servers |
| Taskade | [taskade.com/blog/mcp-servers](https://www.taskade.com/blog/mcp-servers) | Top 15 MCP servers |
| TrueFoundry | [truefoundry.com/blog/best-mcp-servers-for-claude-code](https://www.truefoundry.com/blog/best-mcp-servers-for-claude-code) | Best MCP servers |
| thesys.dev | [thesys.dev/blogs/best-mcp-servers](https://www.thesys.dev/blogs/best-mcp-servers) | Best MCP servers 2026 |
| emergingai | [emergingai.substack.com/p/top-32-mcp-servers-to-make-claude](https://emergingai.substack.com/p/top-32-mcp-servers-to-make-claude) | Top 32 MCP servers |
| builder.io | [builder.io/blog/best-mcp-servers-2026](https://www.builder.io/blog/best-mcp-servers-2026) | Best MCP servers for devs |
| firecrawl | [firecrawl.dev/blog/best-mcp-servers-for-developers](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | Top 10 MCP servers |
| firecrawl | [firecrawl.dev/blog/best-claude-code-plugins](https://www.firecrawl.dev/blog/best-claude-code-plugins) | Top 10 Claude plugins |
| stackgen | [stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026](https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026) | Platform engineers guide |
| k2view | [k2view.com/blog/awesome-mcp-servers](https://www.k2view.com/blog/awesome-mcp-servers) | Awesome MCP servers directory |
| mcp-marketplace.io | [mcp-marketplace.io/blog/best-mcp-servers-developers](https://mcp-marketplace.io/blog/best-mcp-servers-developers) | MCP Marketplace guide |
| apigene.ai | [apigene.ai/blog/mcp-marketplace](https://apigene.ai/blog/mcp-marketplace) | Marketplace guide 2026 |
| LobeHub | [lobehub.com/mcp](https://lobehub.com/mcp) | Enterprise MCP Toolbox |
| houtini | [houtini.com/the-best-mcps-for-claude-desktop/](https://houtini.com/the-best-mcps-for-claude-desktop/) | Desktop MCP guide |
| toolradar | [toolradar.com/blog/best-mcp-servers-claude-code](https://toolradar.com/blog/best-mcp-servers-claude-code) | MCP server guide |
| evomap | [evomap.ai/blog/best-mcp-servers-for-claude-code-2026](https://evomap.ai/blog/best-mcp-servers-for-claude-code-2026) | Top 15 MCP servers |
| roobia | [roobia.medium.com/the-10-must-have-mcp-servers-for-claude-code-2025-developer-edition…](https://roobia.medium.com/the-10-must-have-mcp-servers-for-claude-code-2025-developer-edition-43dc3c15c887) | 10 must-have servers |
| Microsoft Learn | [learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace](https://learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace) | Azure SRE Agent Plugin Marketplace |
| Microsoft .NET Blog | [devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | .NET Skills extension |
| DeepWiki | [deepwiki.com/microsoft/agent-skills/4-plugins](https://deepwiki.com/microsoft/agent-skills/4-plugins) | Microsoft agent-skills plugins |
| KDnuggets | [kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 marketplaces |
| chris-ayers.com | [chris-ayers.com/posts/agent-skills-plugins-marketplace/](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Complete guide |
| virtualuncle | [virtualuncle.com/agent-skills-marketplace-skills-sh-2026/](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Skills.sh guide |
| termdock | [termdock.com/en/blog/agent-skills-guide](https://www.termdock.com/en/blog/agent-skills-guide) | Build, share & secure guide |
| toolworthy.ai | [toolworthy.ai/tool/skills-sh](https://www.toolworthy.ai/tool/skills-sh) | Skills.sh review |
| skiln | [skiln.co/blog/claude-code-plugins-vs-skills-vs-mcp-decision-guide](https://skiln.co/blog/claude-code-plugins-vs-skills-vs-mcp-decision-guide) | Decision guide |
| popularaitools | [popularaitools.ai/blog/claude-code-skills-plugins-clis-2026](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | Skills & CLIs roundup |
| ado.im | [ado.im/posts/claude-customization-stack-mcp-skills-plugins/](https://www.ado.im/posts/claude-customization-stack-mcp-skills-plugins/) | Customization stack |
| kjetilfuras | [kjetilfuras.com/claude-code-agent-skills/](https://kjetilfuras.com/claude-code-agent-skills/) | Writing skills that work |
| explainx.ai | [explainx.ai/blog/what-are-agent-skills-complete-guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | Complete guide |
| scriptbyai | [scriptbyai.com/claude-code-resource-list/](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate resource list |
| releasebot | [releasebot.io/updates/anthropic/claude-code](https://releasebot.io/updates/anthropic/claude-code) | Claude Code release notes |
| brightcoding | [blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools…](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development) | 270+ tools overview |
| devtoolpicks | [devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Skills vs MCP vs Plugins |
| turbodocx | [turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best plugins, skills, MCP |
| earezki | [earezki.com/ai-news/2026-02-04-vercel-introduces-skillssh…](https://earezki.com/ai-news/2026-02-04-vercel-introduces-skillssh-an-open-ecosystem-for-agent-commands/) | Skills.sh launch |
| Vercel docs | [vercel.com/docs/agent-resources/skills](https://vercel.com/docs/agent-resources/skills) | Vercel Agent Skills docs |
| mejba.me | [mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 skills CLIs |
| self.md | [self.md/guides/best-claude-code-plugins/](https://self.md/guides/best-claude-code-plugins/) | Best plugins guide |
| composio | [composio.dev/content/top-claude-code-plugins](https://composio.dev/content/top-claude-code-plugins) | Top plugins 2026 |
| composio | [composio.dev/toolkits/youtube/framework/claude-code](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration |
| composio | [composio.dev/toolkits/reddit/framework/claude-code](https://composio.dev/toolkits/reddit/framework/claude-code) | Reddit MCP integration |
| LobeHub | [lobehub.com/mcp/enescinar-reddit-mcp](https://lobehub.com/mcp/enescinar-reddit-mcp) | Reddit MCP server |
| ClaudeLog | [claudelog.com/claude-code-mcps/reddit-mcp/](https://claudelog.com/claude-code-mcps/reddit-mcp/) | Reddit MCP reference |
| claudepluginhub | [claudepluginhub.com/plugins/caobach369-last30days](https://www.claudepluginhub.com/plugins/caobach369-last30days) | last30days plugin listing |
| Skywork | [skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560](https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560) | Polymarket MCP server guide |
| Python in Plain English | [python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app…](https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477?gi=f4f8a5d90ae7) | Polymarket app tutorial |
| blockchain.news | [blockchain.news/ainews/clis-as-agent-native-interfaces-2026…](https://blockchain.news/ainews/clis-as-agent-native-interfaces-2026-analysis-on-polymarket-cli-github-cli-and-mcp-for-ai-automation) | CLIs as agent-native interfaces |
| ericaai | [ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/](https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/) | Building Polymarket agents |
| digitalapplied | [digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | Marketplace discovery 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 direct threads │ (community discussion via blog aggregations only)
├─ 🔵 X: 0 posts │ (no data returned)
├─ 🔴 YouTube: 2 videos │ est. 70K+ views
├─ 🟢 HN: 17 threads │ est. 5,000+ points │ est. 1,500+ comments
├─ 🟣 TikTok: 0 videos │ (no data returned)
├─ 🩷 Instagram: 0 reels │ (no data returned)
├─ 🦋 Bluesky: 0 posts │ (no data returned)
├─ 📊 Polymarket: 107 markets │ $multi-M volume │ Anthropic 93% "best AI model"
├─ 🌐 Web: 85+ pages │ blogs, docs, GitHub, news
└─ 🗣️ Top voices: @vercel (skills.sh), @anthropic (skills repo 120K★) │ HN: Agent37, Agnix, LangAlpha
```

---

## Data Gaps

- **Reddit:** No direct subreddit thread URLs returned despite multiple searches. Community sentiment is only captured via blog post aggregations and HN. r/ClaudeAI and r/MachineLearning are likely very active on this topic but not directly surfaced.
- **X/Twitter:** No data. Given the topic's popularity, there is likely significant discussion from @AnthropicAI, @vercel, and AI developer influencers.
- **TikTok / Instagram:** No data returned. The YouTube video suggests creator content exists.
- **Bluesky:** No posts surfaced despite the platform's AI developer community.
- **Engagement metrics:** HN points/comments are estimates; exact figures require direct scraping.
- **Polymarket volume:** Dollar volumes are estimates based on market size inference; exact figures from the Polymarket API were not retrieved.
- **Approximate coverage:** Web/blog: ~85%; Hacker News: ~75% (threads identified but not scraped for full comment data); Reddit: ~10% (indirect only); Social media: ~5%.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — Hacker News community ([HN #45619537](https://news.ycombinator.com/item?id=45619537))

> "The barrier to publishing was a GitHub account one week old — no code signing, security review, or default sandbox." — [blog.cyberdesserts.com](https://blog.cyberdesserts.com/ai-agent-security-risks/) on the January 2026 supply chain attack

> "Agent Skills Are the New npm" — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

> "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." — [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/)

> "95% reduction in initial context consumption for users with multiple MCP servers." — [claudefa.st on MCP Tool Search](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)

> "More than 30% of wallets on Polymarket are already using AI agents." — [CoinDesk, March 2026](https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading)

> "Vercel just launched skills.sh, and it already has 20K installs [within 6 hours]" — [reading.sh](https://reading.sh/vercel-just-launched-skills-sh-and-it-already-has-20k-installs-c07e6da7e29e?gi=f4f8a5d90ae7)

> "The goal was to separate agent reasoning from execution. Instead of letting AI agents figure out how to do things on the fly, skills give them a defined, auditable set of instructions to follow every time." — Vercel on [skills.sh launch](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem)

> "Switching to background hooks and removing unnecessary plugins significantly improved Claude performance." — Show HN: Real-time dashboard for Claude Code agent teams ([HN #47602986](https://news.ycombinator.com/item?id=47602986))

> "With over 89,000 installs, it's the most popular Claude Code plugin for a reason: it imposes the same structured process that senior engineers use instinctively." — [claudemarketplaces.com](https://claudemarketplaces.com/) on the feature-dev skill
