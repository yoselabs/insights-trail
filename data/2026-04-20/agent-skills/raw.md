# Agent Skills & Plugin Ecosystems — Raw Research Data
**Date:** 2026-04-20
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## WEB SEARCH RESULTS

### Query 1: "Claude Code skills plugins extensions 2026"

**Links returned:**
- https://code.claude.com/docs/en/skills — Extend Claude with skills (official docs)
- https://claudemarketplaces.com/ — Claude Code Plugins | Skills, MCP Servers & Marketplace Directory
- https://github.com/quemsah/awesome-claude-plugins — Automated collection of Claude Code plugin adoption metrics
- https://github.com/ComposioHQ/awesome-claude-plugins — A curated list of Plugins that let you extend Claude Code
- https://self.md/guides/best-claude-code-plugins/ — best claude code plugins 2026
- https://www.youtube.com/watch?v=KjEFy5wjFQg — Top 10 Claude Code Skills, Plugins & CLIs (April 2026) - YouTube
- https://composio.dev/content/top-claude-code-plugins — 10 top Claude Code plugins to consider in 2026
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 423 plugins, 2,849 skills, 177 agents for Claude Code
- https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 — Top 10 Claude Code Skills, Plugins & CLIs for 2026
- https://www.firecrawl.dev/blog/best-claude-code-plugins — Top 10 Claude Code Plugins to Try in 2026

**Key findings:**
- Claude Code plugins launched in public beta October 2025, now stable
- A plugin bundles Skills, MCP Servers, commands, hooks, or agents into one installable unit
- Skills = features Claude uses automatically when needed (e.g., Playwright for browser testing)
- Subagents = specialized AI agents (security-auditor, frontend-developer, etc.)
- MCP Servers = connect Claude to external services (Linear, GitHub, databases)
- claudemarketplaces.com is the largest directory sorted by installs and GitHub stars

---

### Query 2: "MCP servers tools marketplace 2026"

**Links returned:**
- https://mcpmarket.com/ — Discover Top MCP Servers | MCP Market
- https://www.builder.io/blog/best-mcp-servers-2026 — The Best MCP Servers for Developers in 2026
- https://lobehub.com/mcp — MCP Servers Marketplace · LobeHub
- https://www.firecrawl.dev/blog/best-mcp-servers-for-developers — 10 Best MCP Servers for Developers in 2026
- https://mcpservers.org — Awesome MCP Servers
- https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026 — The 10 Best MCP Servers for Platform Engineers
- https://www.k2view.com/blog/awesome-mcp-servers — Awesome MCP servers: Directory of the top 15
- https://mcp-marketplace.io/blog/best-mcp-servers-developers — Best MCP servers for developers | MCP Marketplace
- https://apigene.ai/blog/mcp-marketplace — MCP Marketplace Guide
- https://mcp.so — MCP Servers (20,222 servers collected)

**Key findings:**
- Dozen+ active MCP marketplace platforms competing, some tracking 8,000+ entries
- MCP released by Anthropic November 2024; OpenAI and Google DeepMind adopted early 2025
- Donated to Linux Foundation's Agentic AI Foundation (AAIF) December 2025
- mcp.so has 20,222 MCP servers collected
- Security scan of 8,000+ MCP servers: 36.7% SSRF vulnerabilities, 43% unsafe command execution, 41% zero authentication
- Glama.ai, LobeHub, MCP Marketplace, MCP.so are major hubs
- LobeHub offers MCP Toolbox for Databases (open source, enterprise database connections)

---

### Query 3: "agent skill marketplace plugin ecosystem 2026"

**Links returned:**
- https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ — Agent Skills, Plugins and Marketplace: The Complete Guide
- https://skillsmp.com — Agent Skills Marketplace - Claude, Codex & ChatGPT Skills | SkillsMP
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — Agent Skills Marketplace: Skills.sh Guide (2026)
- https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ — Extend your coding agent with .NET Skills
- https://learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace — Plugin Marketplace in Azure SRE Agent
- https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents — Top 5 Agent Skill Marketplaces
- https://agentskillexchange.com/ — Marketplace Home - Agent Skill Exchange
- https://github.com/vercel-labs/skills — The open agent skills tool - npx skills
- https://deepwiki.com/microsoft/agent-skills/4-plugins — Plugins | microsoft/agent-skills
- https://github.com/VoltAgent/awesome-agent-skills — 1000+ agent skills compatible with Claude Code, Codex, Gemini CLI, Cursor, and more

**Key findings:**
- SKILL.md open standard published by Anthropic December 2025, adopted by OpenAI
- Skills.sh (Vercel) launched January 20, 2026 — official directory and leaderboard for agent skill packages
- Skills.sh reached 20,000 installs within six hours of launch
- Skills.sh tracks 90,000+ skills, supports 19 AI agents
- SkillsMP: 425,000+ skills, largest discovery platform by raw numbers (500,000+ aggregated from GitHub)
- SkillHub: ~7,000 curated skills, AI-evaluated on practicality, clarity, automation, quality, impact
- npx skills add <package> is the install command
- Ecosystem fragmented: multiple competing directories with SkillsMP biggest by raw numbers
- Still in preview with VS Code settings scope restrictions and dev container issues

---

### Query 4: "Claude Code plugin system SKILL.md specification agent tools registry April 2026"

**Links returned:**
- https://code.claude.com/docs/en/plugins-reference — Plugins reference - Claude Code Docs
- https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview — Agent Skills - Claude API Docs
- https://github.com/alirezarezvani/claude-skills — 232+ Claude Code skills & agent plugins
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 423 plugins, 2,849 skills, 177 agents
- https://claude-plugins.dev/skills — Discover Agent Skills
- https://platform.claude.com/docs/en/agent-sdk/skills — Agent Skills in the SDK
- https://claude-plugins.dev/ — Claude Code Plugins & Agent Skills - Community Registry with CLI
- https://www.producttalk.org/how-to-use-claude-code-features/ — How to Use Claude Code: A Guide to Slash Commands, Agents, Skills, and Plug-ins
- https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/ — Claude Agent Skills: A First Principles Deep Dive
- https://github.com/anthropics/skills — Public repository for Agent Skills (120k stars, 14k forks)

**Key findings:**
- SKILL.md = markdown file with YAML frontmatter (config) + markdown content (instructions)
- Plugin components: skills, agents, hooks, MCP servers, LSP servers, monitors
- Plugin agents in agents/ directory: name, description, model, effort, maxTurns, tools, disallowedTools, skills, memory, background, isolation frontmatter fields
- anthropics/skills repo: 120k stars, 14k forks as of April 16, 2026
- Source-available (not fully open source) but shared as reference for complex production skills
- Featured plugins week of April 17: token-optimizer, executive-assistant-skills, skill-creator, cursor-pack, crypto-portfolio-tracker
- claude-plugins.dev: Community registry with CLI

---

### Query 5: site:news.ycombinator.com MCP servers Claude Code agent skills

**Links returned:**
- https://news.ycombinator.com/item?id=46422134 — Show HN: Agent37 – Monetize your Claude skills with shareable links
- https://news.ycombinator.com/item?id=45619537 — Claude Skills are awesome, maybe a bigger deal than MCP
- https://news.ycombinator.com/item?id=46983879 — Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks)
- https://news.ycombinator.com/item?id=45607117 — Claude Skills
- https://news.ycombinator.com/item?id=43410866 — Hacking Your Own AI Coding Assistant with Claude Pro and MCP
- https://news.ycombinator.com/item?id=46692865 — Agent Skills – Open Trusted Catalog of AI Agent Skills: Claude, OpenAI, Vercel, GH
- https://news.ycombinator.com/item?id=44347116 — Which MCP servers are Claude Code must-adds for coding
- https://news.ycombinator.com/item?id=44061614 — Trading with Claude, and writing your own MCP server
- https://news.ycombinator.com/item?id=46396930 — CLAUDE.md, Skills, Agents, MCP, slash commands discussion
- https://news.ycombinator.com/item?id=45766686 — Claude Skills vs. MCP: Complementary Philosophies for AI Customization

**Key findings:**
- Skills = filesystem-based system with progressive disclosure (three-tier loading to avoid context bloat)
- Skills can orchestrate multiple MCP servers
- Agent Skills spec requires kebab-case names but Claude Code silently ignores incorrectly named skills
- Deprecated MCP transport types show no warnings
- Agent37: monetize Claude skills with shareable links
- Agnix: lint tool for AI agent configs (Claude.md, skills, MCP, hooks)
- Aggregation effort: pulling skills from Anthropic, OpenAI, GitHub, Vercel into one JSON catalog
- Thread: "Claude Skills are awesome, maybe a bigger deal than MCP" — significant community discussion

---

### Query 6: "Show HN" agent skills Claude MCP plugin April 2026

**Links returned:**
- https://news.ycombinator.com/item?id=46869575 — Show HN: Federal Election Commission Claude Code Plugin and Agent Skill and MCP
- https://news.ycombinator.com/item?id=47602986 — Show HN: Real-time dashboard for Claude Code agent teams
- https://news.ycombinator.com/item?id=46398957 — Show HN: An AI collaboration playbook (AGENTS.md and code map and template)
- https://news.ycombinator.com/item?id=46422134 — Show HN: Agent37 – Monetize your Claude skills with shareable links
- https://www.claudepluginhub.com/plugins/caobach369-last30days — Claudepluginhub - last30days plugin
- https://mcpmarket.com/tools/skills/hacker-news-explorer — Hacker News Explorer Claude Code Skill
- https://news.ycombinator.com/item?id=46426624 — Show HN: Stop Claude Code from forgetting everything
- https://news.ycombinator.com/item?id=47766370 — Show HN: LangAlpha – what if Claude Code was built for Wall Street?
- https://news.ycombinator.com/item?id=45642911 — Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP
- https://news.ycombinator.com/item?id=46388882 — Show HN: A Claude Code plugin that catch destructive Git and filesystem commands

**Key findings:**
- Active Show HN community for Claude Code plugins/skills
- Real-time dashboard: switching to background hooks and removing unnecessary plugins significantly improved Claude performance
- Agent37: challenge of monetizing Claude skills — charge through shareable links instead of requiring manual setup
- LangAlpha: auto-generates typed Python modules from MCP schemas at workspace init (financial use case)
- "Stop Claude Code from forgetting everything" — shared memory layer skill for persistent memory across sessions
- Playwright Skill specifically designed to use less context than playwright-MCP alternative
- FEC plugin: government/civic data use case for skills

---

### Query 7: skills.sh Vercel agent skills marketplace launch January 2026

**Links returned:**
- https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem — Introducing skills, the open agent skills ecosystem
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — Agent Skills Marketplace: Skills.sh Guide (2026)
- https://www.infoq.com/news/2026/02/vercel-agent-skills/ — Vercel Introduces Skills.sh, an Open Ecosystem for Agent Commands - InfoQ
- https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ — Securing the Agent Skill Ecosystem: How Snyk and Vercel Are Locking Down the New Software Supply Chain
- https://www.toolworthy.ai/tool/skills-sh — Skills.sh Review (2026): The Open Agent Skills Directory
- https://www.termdock.com/en/blog/agent-skills-guide — Agent Skills Guide 2026: Build, Share & Secure
- https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026 — Agent Skills Are the New npm: AI Package Manager Marketplace 2026
- https://earezki.com/ai-news/2026-02-04-vercel-introduces-skillssh-an-open-ecosystem-for-agent-commands/ — Vercel Releases Skills.sh for Standardized Agent Commands
- https://vercel.com/docs/agent-resources/skills — Agent Skills
- https://reading.sh/vercel-just-launched-skills-sh-and-it-already-has-20k-installs-c07e6da7e29e?gi=f4f8a5d90ae7 — Vercel just launched skills.sh, and it already has 20K installs

**Key findings:**
- skills.sh launched January 20, 2026 by Vercel
- Goal: separate agent reasoning from execution — give agents defined, auditable instructions
- 20,000 installs within 6 hours of launch
- 90,000+ skills tracked, 19 agents supported
- Stripe and other major companies shipped official skills shortly after launch
- Snyk partnership for security scanning of skills ecosystem
- Framing: "Agent Skills Are the New npm" — skills as the package manager paradigm for AI agents
- install: npx skills add <package>

---

### Query 8: MCP Tool Search lazy loading Claude Code context window April 2026

**Links returned:**
- https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search — Claude Code MCP Tool Search: Save 95% Context
- https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc — Claude Code Finally Gets Lazy Loading for MCP Tools
- https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide — What is MCP Tool Search?
- https://github.com/openai/codex/issues/9266 — Add mcp search tool, lazy mcp load issue (OpenAI Codex)
- https://github.com/microsoft/vscode/issues/288310 — Implement MCP Tool Search (Lazy Loading) from Anthropic's Claude Code (VS Code)
- https://github.com/anthropics/claude-code/issues/7336 — Feature Request: Lazy Loading for MCP Servers and Tools (95% context reduction)
- https://github.com/anthropics/claude-code/issues/11364 — Lazy-load MCP tool definitions to reduce context usage
- https://venturebeat.com/orchestration/claude-code-just-got-updated-with-one-of-the-most-requested-user-features — VentureBeat coverage
- https://github.com/anthropics/claude-code/issues/20421 — Feature Request: Dynamic/Lazy MCP Server Loading
- https://forbiddentrust.com/codex/mcp-tool-search-context-fix — MCP Tool Search: How Claude Code Fixed Context Window Bloat

**Key findings:**
- MCP Tool Search = lazy loading system that fetches tool details on-demand vs. at session start
- Activates automatically when MCP tool descriptions would use >10% of context window
- Traditional 50+ MCP tool setup: ~77K tokens before any work; with Tool Search: ~8.7K tokens
- 95% reduction in initial context consumption
- Shipped in Claude Code 2.1.7
- Now enabled by default for all users (no opt-in required)
- Microsoft VS Code and OpenAI Codex are implementing similar approaches
- Highly requested feature since late 2025

---

### Query 9: "agent skills" "MCP" security vulnerabilities supply chain 2026

**Links returned:**
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — AI Agent Security Risks 2026: MCP, OpenClaw & Supply Chain
- https://www.practical-devsecops.com/mcp-security-vulnerabilities/ — MCP Security Vulnerabilities: How to Prevent Prompt Injection and Tool Poisoning
- https://skillrisk.org/ — SkillRisk - Free AI Agent Skill Security Scanner
- https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/ — 'By Design' Flaw in MCP Could Enable Widespread AI Supply Chain Attacks (SecurityWeek)
- https://www.futuriom.com/articles/news/key-trends-from-rsac-agentic-ai-mcp-and-supply-chain-risks/2026/03 — Key Trends From RSAC: Agentic AI, MCP, and Supply-chain Risks
- https://arxiv.org/html/2604.02837v1 — Towards Secure Agent Skills: Architecture, Threat Taxonomy, and Security Analysis
- https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ — MCP Security Vulnerabilities: Complete Guide
- https://gentic.news/article/mcp-security-crisis-43-of-servers — MCP Security Crisis: 43% of Servers Vulnerable, 341 Malicious Skills Found
- https://arxiv.org/pdf/2601.10338 — Agent Skills in the Wild: An Empirical Study of Security
- https://developers.redhat.com/articles/2026/03/10/agent-skills-explore-security-threats-and-controls — Agent Skills: Explore security threats and controls (Red Hat)

**Key findings:**
- Scan of 42,447 skills: 26.1% contained at least one security vulnerability
- 14 distinct vulnerability patterns: prompt injection, data exfiltration, privilege escalation, supply chain risks
- CVE-2025-59536 (CVSS 8.7): two configuration injection flaws in Claude Code; Hook injection → RCE when dev opens project
- January 2026: coordinated supply chain campaign compromised 1,184 skills in major community marketplace (~1 in 5 packages), delivering credential-theft payload
- Publishing barrier: only a one-week-old GitHub account needed; no code signing, security review, or sandboxing
- MCP design flaw: unsanitized commands can execute silently → full system compromise
- Trend Micro: 492 MCP servers with zero client authentication and zero traffic encryption
- Bitsight: exposed servers with admin panels, debug endpoints, API routes accessible without credentials
- 43% of official MCP registry servers had zero authentication
- SkillRisk.org: free security scanner for agent skills
- RSAC 2026 highlight: MCP and supply chain risks were top concerns
- arXiv 2604.02837v1 (April 2026): formal security taxonomy for agent skills

---

### Query 10: ccpi CLI package manager tonsofskills.com

**Links returned:**
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — Main repo (423 plugins, 2,849 skills, 177 agents)
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md
- Multiple subdirectory links for saas-packs (fly.io, granola, clickup, lucidchart)
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/CONTRIBUTING.md
- https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development — Claude Code Plugins Plus: 270+ AI Agent Tools

**Key findings:**
- ccpi (Claude Code Plugin Index) CLI: pnpm add -g @intentsolutionsio/ccpi
- Commands: ccpi search, ccpi install, ccpi list --installed, ccpi update, ccpi validate
- tonsofskills.com = open-source marketplace
- SaaS packs available for fly.io, granola, clickup, lucidchart
- Validates against 2026 schema standard with secured tool permissions
- 423 plugins, 2,849 skills, 177 agents as of latest

---

### Query 11: anthropics/skills github agent skills open source 2026

**Links returned:**
- https://github.com/anthropics/skills/tree/main — Public repository for Agent Skills
- https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md — Agent Skills Specification
- https://skillsmp.com — SkillsMP
- https://github.com/orgs/anthropics/repositories — Anthropic org repos
- https://github.com/topics/anthropic-skills — GitHub topic
- https://github.com/agentskills/agentskills — Specification and documentation for Agent Skills
- https://github.com/anthropics/skills/blob/main/skills/claude-api/shared/managed-agents-environments.md
- https://github.com/anthropics/skills/blob/main/skills/claude-api/SKILL.md
- https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md

**Key findings:**
- anthropics/skills: 120k stars, 14k forks as of April 16, 2026
- Contains the Agent Skills Specification as open standard (December 2025)
- Covers creative to enterprise use cases; all source-available
- Includes skill-creator skill (meta-skill for creating skills)
- claude-api skills for managed agents environments

---

### Query 12: Polymarket AI agent skills MCP market predictions 2026

**Links returned:**
- https://polymarket.com/predictions/ai — AI Predictions & Real-Time Odds | Polymarket
- https://polymarket.com/tech — Technology Prediction Markets & Live Odds 2026
- https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution — AI Agent Marketplaces 2026
- https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/ — Building AI Agents for Polymarket
- https://blockchain.news/ainews/clis-as-agent-native-interfaces-2026-analysis-on-polymarket-cli-github-cli-and-mcp-for-ai-automation — CLIs as Agent-Native Interfaces: 2026 Analysis
- https://github.com/Polymarket/agents — Trade autonomously on Polymarket using AI Agents
- https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560 — AI Engineer's Guide to Polymarket MCP Server
- https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477?gi=f4f8a5d90ae7 — Built Polymarket Intelligence App with Agentic Coding
- https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading — AI agents are quietly rewriting prediction market trading (CoinDesk)
- https://polymarket.com/ai — AI Prediction Markets & Live Odds

**Key findings:**
- 107 live AI prediction markets on Polymarket as of April 19, 2026
- Most active market: "Which company has the best AI model end of April?" — Anthropic at 93%
- Olas/Polystrat agent: 4,200+ trades on Polymarket within a month, up to 376% returns on individual trades
- 30%+ of Polymarket wallets using AI agents (per LayerHub analytics)
- Polymarket MCP Server: bridge between AI agents (Claude, Cursor) and Polymarket
- Polymarket CLI (Rust): agents can query markets, place trades, pull data
- Eight marketplaces identified for AI capabilities: Claude Skills, GPT Store, MCP Hubs, HuggingFace Spaces, Replit Agent Market, LangChain Hub, Vercel Agent Gallery, Cloudflare AI Marketplace

---

### Query 13: MCP Linux Foundation Agentic AI Foundation donation

**Links returned:**
- https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ — MCP joins the Agentic AI Foundation
- https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation — Linux Foundation Announcement
- https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation — Anthropic news release
- https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/ — AAIF press release
- https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/ — The New Stack coverage
- https://openai.com/index/agentic-ai-foundation/ — OpenAI's announcement
- https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/ — GitHub Blog
- https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/ — TechCrunch coverage
- https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md-302636897.html — PR Newswire
- https://www.infoq.com/news/2025/12/agentic-ai-foundation/ — InfoQ

**Key findings:**
- Announced December 9, 2025
- AAIF (Agentic AI Foundation) = directed fund under Linux Foundation
- Co-founded by Anthropic, Block, OpenAI
- Platinum members: AWS, Anthropic, Block, Bloomberg, Cloudflare, Google, Microsoft, OpenAI
- Founding projects: MCP, goose (Block), AGENTS.md (OpenAI)
- MCP stats at donation: 97M+ monthly SDK downloads, 10,000+ active servers
- Projects maintain autonomy over technical direction; AAIF governs budget/membership/strategic investments

---

### Query 14: Reddit Claude Code best MCP servers discussion April 2026

**Links returned:**
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers — Best Claude Code Plugins, Skills & MCP Servers (2026)
- https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 — Claude Skills vs MCP Connectors vs Plugins
- https://www.morphllm.com/claude-code-skills-mcp-plugins — Claude Code Skills vs MCP vs Plugins: Complete Guide
- https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 — Best Claude Code Skills & Plugins (DEV Community)
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — 50+ Best MCP Servers for Claude Code
- https://alexop.dev/posts/understanding-claude-code-full-stack/ — Understanding Claude Code's Full Stack
- https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k — Claude Code Skills vs MCP Servers (DEV Community)
- https://medium.com/@mohit15856/10-claude-plugins-you-actually-need-in-2026-with-full-setup-guides-136f7d879c37 — 10 Claude Plugins You Actually Need (Medium)
- https://skiln.co/blog/claude-code-plugins-vs-skills-vs-mcp-decision-guide — Claude Code Plugins vs Skills vs MCP Servers: A Developer's Decision Guide
- https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026 — Popular AI Tools

**Key findings:**
- Plugin marketplace launched February 2026
- MCP Channels (push messages into Claude session) still research preview as of April 2026
- MCP Tool Search reduces context usage up to 95%; enables running all MCP servers without context limits
- Claudemarketplace.com: community-curated directory, 150+ skills as of March 2026, with ratings and install counts
- awesome-mcp-servers: 84K+ GitHub stars; awesome-claude-skills: 52K+ GitHub stars
- Typical recommendation: 2-3 MCP servers (GitHub, Filesystem, one domain-specific) + custom Skills
- Most popular plugin (89,000+ installs): feature-dev skill imposing 7-phase workflow

---

### Query 15: best MCP servers Reddit discussion April 2026

**Links returned:**
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — 50+ Best MCP Servers
- https://www.bannerbear.com/blog/8-best-mcp-servers-for-claude-code-developers-in-2026/ — 8 Best MCP Servers (Bannerbear)
- https://www.taskade.com/blog/mcp-servers — 15 Best MCP Servers for AI Developers 2026
- https://toolradar.com/blog/best-mcp-servers-claude-code — Best MCP Servers for Claude Code
- https://evomap.ai/blog/best-mcp-servers-for-claude-code-2026 — Best Claude Code MCP Servers: Top 15
- https://houtini.com/the-best-mcps-for-claude-desktop/ — Best MCP Servers for Claude Desktop
- https://emergingai.substack.com/p/top-32-mcp-servers-to-make-claude — Top 32 MCP Servers to Make Claude Super Powerful
- https://www.truefoundry.com/blog/best-mcp-servers-for-claude-code — Best MCP Servers for Claude Code
- https://roobia.medium.com/the-10-must-have-mcp-servers-for-claude-code-2025-developer-edition-43dc3c15c887 — 10 Must-Have MCP Servers
- https://www.thesys.dev/blogs/best-mcp-servers — Best MCP Servers for Claude in 2026

**Key findings:**
- GitHub MCP: direct repo access, issue/PR management, autonomous contributor capability
- Filesystem MCP: foundational; configurable access boundaries
- Exa MCP: most-used search server in 2026 by large margin (AI-native search)
- Notion MCP: knowledge base integration; exposes pages, databases, blocks
- Taskade MCP: strongest production option; workspace memory + agent intelligence
- PostgreSQL MCP, SQLite MCP: database connectivity
- OAuth 2.1 authorization added to MCP spec in April 2026 (incremental scope consent)
- Recommendation: limit to 5-6 active servers (each starts a subprocess; more = sluggish)
- 5-server setup with 58 tools: ~55,000 tokens before conversation starts; Anthropic Tool Search reduces by 85%

---

### Additional URLs collected

**DEV Community / Medium / Blogs:**
- https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k
- https://alexop.dev/posts/understanding-claude-code-full-stack/
- https://www.ado.im/posts/claude-customization-stack-mcp-skills-plugins/
- https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d — "Agent Skills: The Cheat Codes for Claude Code" (April 2026)
- https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 — "10 Must-Have Skills for Claude" (March 2026)
- https://explainx.ai/blog/what-are-agent-skills-complete-guide
- https://kjetilfuras.com/claude-code-agent-skills/
- https://www.scriptbyai.com/claude-code-resource-list/ — The Ultimate Claude Code Resource List (2026 Edition)

**GitHub repos:**
- https://github.com/K-Dense-AI/claude-skills-mcp — MCP server for searching/retrieving Claude Agent Skills using vector search
- https://github.com/JCodesMore/youtube-mcp — Claude Code plugin for YouTube research
- https://github.com/wilwaldon/Claude-Code-Video-Toolkit — Skills, MCP servers for video production
- https://github.com/karanb192/reddit-mcp-buddy — Clean Reddit MCP server (no API keys required)
- https://github.com/agentskills/agentskills — Specification and documentation for Agent Skills

**Release tracking:**
- https://releasebot.io/updates/anthropic/claude-code — Claude Code by Anthropic - Release Notes - April 2026 Latest Updates

**Security:**
- https://arxiv.org/html/2604.02837v1 — Towards Secure Agent Skills (April 2026 preprint)
- https://arxiv.org/pdf/2601.10338 — Agent Skills in the Wild: Empirical Study (January 2026)
- https://skillrisk.org/ — SkillRisk free scanner

---

## SUMMARY STATISTICS

- **Web pages:** 80+ unique URLs collected
- **Hacker News threads:** 12+ identified
- **YouTube:** 1 confirmed video (April 2026)
- **Polymarket:** 107 live AI markets; Anthropic at 93% odds "best AI model end of April"
- **GitHub repos:** 10+ major repos identified
- **Key dates:** MCP donated to AAIF Dec 9 2025; Skills.sh launched Jan 20 2026; Plugin marketplace launched Feb 2026; MCP OAuth 2.1 added April 2026; MCP Tool Search shipped Claude Code 2.1.7
