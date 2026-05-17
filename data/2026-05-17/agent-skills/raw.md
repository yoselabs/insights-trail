# Agent Skills Research — Raw Data
**Date:** 2026-05-17
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## PLATFORM: Official Documentation

### Claude Code Skills Documentation
**URL:** https://code.claude.com/docs/en/skills
**Retrieved:** 2026-05-17

**Key Facts:**
- Skills are SKILL.md files with YAML frontmatter + markdown instructions
- Claude Code skills follow the Agent Skills open standard (agentskills.io), which works across multiple AI tools
- Custom commands (.claude/commands/) merged into skills — backward compatible
- Bundled skills: /simplify, /batch, /debug, /loop, /claude-api
- Progressive disclosure: Level 1 (description metadata in system prompt always) → Level 2 (full SKILL.md on invocation) → Level 3+ (supporting files on demand)
- Frontmatter fields: name, description, when_to_use, argument-hint, arguments, disable-model-invocation, user-invocable, allowed-tools, model, effort, context, agent, hooks, paths, shell
- Dynamic context injection via `!`command`` syntax — runs before Claude sees content
- `context: fork` for isolated subagent execution
- Permission scopes: Enterprise > Personal (~/.claude/skills/) > Project (.claude/skills/) > Plugin
- skillOverrides setting for controlling visibility without editing SKILL.md
- Live change detection — file watching within current session
- Monorepo support via nested .claude/skills/ directories
- Max skill description 1,536 chars (truncated in listing), configurable via maxSkillDescriptionChars
- skillListingBudgetFraction setting (default 1% of context window for skill descriptions)
- Invoked skill content stays in context for rest of session
- Auto-compaction: re-attaches most recent invocation, first 5,000 tokens, combined 25,000 token budget across all skills
- `disableSkillShellExecution` setting for policy enforcement
- Skills can generate visual HTML output via bundled Python scripts

**Plugin System:**
- A plugin is a directory with manifest at .claude-plugin/plugin.json
- Plugins bundle skills, MCP server configs, hooks, subagents
- /plugin command for browse/install/manage with tabs: Discover, Installed, Marketplaces, Errors
- --plugin-url flag for third-party marketplace sources
- Official Anthropic marketplace at github.com/anthropics/claude-plugins-official

---

## PLATFORM: Anthropic Engineering Blog

### "Equipping agents for the real world with Agent Skills"
**URL:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
**Published:** October 16, 2025

**Key Facts:**
- Created because "as Claude's capabilities improved, we needed more composable, scalable, and portable ways to equip them with domain-specific expertise"
- Skills transform general-purpose agents into domain-specific specialists
- Progressive Disclosure Architecture: 3 levels of information delivery
- Compatible with Claude.ai, Claude Code, Claude Agent SDK, Claude Developer Platform
- Open standard published December 18, 2025

---

## PLATFORM: Official Agent Skills Standard

### agentskills.io
**URL:** https://agentskills.io/home
**URL:** https://github.com/anthropics/skills (spec at spec/agent-skills-spec.md)

**Key Facts:**
- Published December 18, 2025
- License: Apache 2.0 (code), CC-BY-4.0 (docs)
- Includes reference SDK and validation tooling
- Adoption as of March 2026: 32 tools from competing companies
  - Google Gemini CLI
  - JetBrains Junie
  - AWS Kiro
  - Block Goose
  - Sourcegraph Amp
  - Snowflake, Databricks, ByteDance, Mistral AI, Spring AI
- Within 48 hours of announcement: Microsoft VS Code and OpenAI (ChatGPT + Codex CLI) adopted it
- VS Code agent skills docs: https://code.visualstudio.com/docs/copilot/customization/agent-skills

**VentureBeat Coverage:**
- URL: https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard
- Headline: "Anthropic launches enterprise 'Agent Skills' and opens the standard, challenging OpenAI in workplace AI"

**SiliconAngle Coverage:**
- URL: https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/
- Date: December 18, 2025

---

## PLATFORM: GitHub Repositories

### anthropics/skills
**URL:** https://github.com/anthropics/skills
**Stats:** 136k stars, 16k forks, 877 watchers, 237 open issues, 614 open PRs, 34 commits on main

**Categories:** Creative & Design, Development & Technical, Enterprise & Communication, Document Skills (PDF/DOCX/PPTX/XLSX)
**Languages:** Python 84.4%, HTML 12.4%, Shell 1.9%, JavaScript 1.3%
**License:** Apache 2.0 (code), source-available for Document skills

**Marketplace config:** https://github.com/anthropics/skills/blob/main/.claude-plugin/marketplace.json

---

### jeremylongshore/claude-code-plugins-plus-skills
**URL:** https://github.com/jeremylongshore/claude-code-plugins-plus-skills
**Current Stats:** 425 plugins, 2,810 skills, 200 agents
**Marketplace:** tonsofskills.com
**CLI:** ccpi (npm: @intentsolutionsio/ccpi)
**Install:** `pnpm add -g @intentsolutionsio/ccpi`
**Features:** 42 SaaS skill packs, 1,086 skills for specific platforms/services, synced daily at midnight UTC

---

### ComposioHQ/awesome-claude-plugins
**URL:** https://github.com/ComposioHQ/awesome-claude-plugins
**Description:** A curated list of Plugins that let you extend Claude Code with custom commands, agents, hooks, and MCP servers through the plugin system.

---

### alirezarezvani/claude-skills
**URL:** https://github.com/alirezarezvani/claude-skills
**Stats:** 263+ skills
**Works with:** Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents
**Categories:** Engineering, marketing, product, compliance, C-level advisory

---

### netresearch/claude-code-marketplace
**URL:** https://github.com/netresearch/claude-code-marketplace
**Description:** Curated Agent Skills collection for AI-assisted development. Open standard — agentskills.io. Portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents. By Netresearch.

---

### mukul975/Anthropic-Cybersecurity-Skills
**URL:** https://github.com/mukul975/Anthropic-Cybersecurity-Skills
**Description:** 754 structured cybersecurity skills for AI agents
**Mapped to:** MITRE ATT&CK, NIST CSF 2.0, MITRE ATLAS, D3FEND & NIST AI RMF
**Works with:** Claude Code, GitHub Copilot, Codex CLI, Cursor, Gemini CLI & 20+ platforms
**Domains:** 26 security domains

---

### agentskills/agentskills
**URL:** https://github.com/agentskills/agentskills
**Description:** Specification and documentation for Agent Skills

---

### agentic-community/mcp-gateway-registry
**URL:** https://github.com/agentic-community/mcp-gateway-registry
**Description:** Enterprise-ready MCP Gateway & Registry that centralizes AI development tools with secure OAuth authentication, dynamic tool discovery, and unified access for both autonomous AI agents and AI coding assistants.

---

## PLATFORM: Hacker News

### Thread 1: "Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills"
**URL:** https://news.ycombinator.com/item?id=46693426
**Description:** Curated marketplace filtering practical skills from 60k+ GitHub skills

---

### Thread 2: "Claude Code Skills and 380 agent skills from official dev teams and community"
**URL:** https://news.ycombinator.com/item?id=47178402
**Notes:** Skills from official developer teams and community

---

### Thread 3: "Show HN: OPC Skills – 9 AI agent skills for solopreneurs (Claude Code, Cursor)"
**URL:** https://news.ycombinator.com/item?id=46730857
**Description:** 9 skills for solopreneurs: domain hunting, product validation, logo creation, SEO optimization

---

### Thread 4: "Skills Manager – manage AI agent skills across Claude, Cursor, Copilot"
**URL:** https://news.ycombinator.com/item?id=47423910
**Points:** 3
**Comments:** 9
**Original Poster:** evergreenxx

**Key Comments:**
- **druide67:** "Claude follows multi-step rules well, Copilot tends to ignore anything beyond the first line." Real challenge isn't file syncing but ensuring same instruction works across different agents.
- **prateeksi:** Asked about conflict resolution — does the tool detect diffs when skills updated simultaneously, or last-write-win? Also asked about team-level skill sharing.
- **teekert:** Interested but noted Linux unavailability, security concerns with exposing SSH keys to agents.
- **evergreenxx (creator):** Linux support was on roadmap, later confirmed available.
- **Dshadowzh:** "Most agents support ~/.agents/skills as a standard location, except Claude Code. We need a unified skill marketplace for different agents."

---

### Thread 5: "Agent Skills: From Claude to Open Standard to Your Daily Coding Workflow"
**URL:** https://news.ycombinator.com/item?id=46779064
**Description:** Discussion of Agent Skills becoming an open standard and integration into coding workflows

---

### Thread 6: "Agent Skills"
**URL:** https://news.ycombinator.com/item?id=46871173
**Description:** General Agent Skills discussion

---

### Thread 7: "Claude Code Skills and Plugins as an Open Source Project"
**URL:** https://news.ycombinator.com/item?id=47321892
**Description:** Open source aspect of the plugin/skills ecosystem

---

### Thread 8: "Code Sandbox Tech Behind Manus and Claude Agent Skills"
**URL:** https://news.ycombinator.com/item?id=46012881
**Description:** Technical comparison of code sandbox implementations

---

### Thread 9: "Solving Agent Context Loss: A Beads and Claude Code Workflow for Large Features"
**URL:** https://news.ycombinator.com/item?id=46471286
**Description:** Workflow pattern for managing context in large Claude Code sessions

---

## PLATFORM: Reddit (aggregated from third-party sources)

**Note:** Reddit.com inaccessible to crawlers. Data sourced from morphllm.com aggregation.
**URL:** https://www.morphllm.com/claude-code-reddit

**Active Subreddits:**
- r/ClaudeCode — 4,200+ weekly contributors, most active Claude Code community
- r/ClaudeAI — all Claude products
- r/LocalLLaMA — comparison threads on local alternatives
- r/CursorAI — frequent Claude Code comparisons
- r/ChatGPT — broader AI coding tool debates
- r/Codex

**Key Discussion Themes:**
1. **MCP token costs** — Documented case: 67,000 tokens consumed from connecting four MCP servers before typing a single prompt. System prompts, tool definitions, JSON schemas, and memory files eat 30-40K tokens at session start.
2. **Cost-quality tradeoff** — Most debated topic across subreddits. MCP servers are powerful but expensive.
3. **Skills vs MCP debate** — Architecture question: Skills define the workflow and quality bar, MCP provides standardized access to external services, Tools execute individual actions.
4. **Multi-file refactoring** — Claude Code praised for capabilities
5. **Usage limits** — Complaint threads about hitting limits

---

## PLATFORM: YouTube

### Video 1: "The Ultimate Claude Code Guide | MCP, Skills & More"
**URL:** https://www.youtube.com/watch?v=uogzSxOw4LU
**Published:** April 13, 2026
**Description:** Comprehensive guide covering MCP, skills, and more in Claude Code

---

### Video 2: "How I Actually Use Claude Every Day in 2026"
**URL:** https://www.youtube.com/watch?v=EZcYjH3jAo8
**Published:** ~May 3, 2026 (2 weeks ago from May 17)
**Topics:** Claude Skills, Connectors, MCP Services

---

### Video 3: "Full Claude Code Tutorial for Non-Technical Beginners in 2026 (step-by-step)"
**URL:** https://www.youtube.com/watch?v=bqJzIWAEn40
**Published:** ~May 3, 2026

---

### Video 4: "FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step)"
**URL:** https://www.youtube.com/watch?v=qYqIhX9hTQk

---

### Video 5: "The ONLY Claude Code Tutorial You'll Ever Need in 2026"
**URL:** https://www.youtube.com/watch?v=LlFgLsffbBs

---

### Course: Claude Code 2026: Subagents, MCP, Skills and Plugins Bootcamp
**URL:** https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/
**Platform:** Udemy
**Description:** Zero to production-grade AI Agents using full Claude Code ecosystem: Subagents, MCP servers, Skills, Plugins, Hooks, Slash Commands

---

### Anthropic SkillJar: Introduction to agent skills
**URL:** https://anthropic.skilljar.com/introduction-to-agent-skills

---

## PLATFORM: Web — Key Articles & Announcements

### Claude Code May 2026 Release Notes
**URL:** https://pasqualepillitteri.it/en/news/2223/claude-code-may-2026-release-notes-radio-plugin-marketplace
**Published:** May 2026

**Key items:**
- Plugin marketplace became first-class system starting with v2.1.108
- Architecture mirrors VS Code extensions with expanded capabilities (slash commands, hooks, sub-agents, skills)
- Official Anthropic marketplace hosted at anthropics/claude-plugins-official on GitHub
- --plugin-url flag for third-party plugin sources
- New /radio command for lo-fi streaming
- Opus 4.7: 1 million token context window (from 200k), effort levels (low/medium/high/xhigh/Auto)
- New commands: /loop, /ultrareview, /focus, /recap, /release-notes
- Git worktrees integration with worktree.baseRef config
- MCP OAuth token race condition patches
- Access tiers for computer-use: read, click, full permissions

---

### "Best AI Agent Skills Marketplaces in 2026" Comparison
**URL:** https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026

**Marketplace Comparison Table:**
| Marketplace | Size | Curation | Security | Pricing | Notable |
|------------|------|----------|----------|---------|---------|
| Skills.sh | ~2,000 skills | Community submissions | None | Free | Vercel-backed, npx skills add |
| SkillsMP | 800,000+ skills | GitHub scraped (2+ stars) | None | Free | Largest catalog, requires dev auditing |
| LobeHub | 169,000+ skills | Scraped aggregation | None | Free | Ecosystem-focused, polished UI |
| ClaudeSkills.info | 658 skills | Community + official Anthropic | None | Free | Beginner-friendly |
| MCP Market | ~500 skills | Submission-based | None | Free | Best for MCP server integration |
| Anthropic Official | ~20 skills | Manual verification by Anthropic | Internal audit | Free | Bundled with Claude Code |
| GitHub Plugin Marketplaces | 2,500+ registries | Per-owner variable | None | Free | Quality ranges from excellent to abandoned |
| Agensi | 200+ skills | Manual + automated | 8-point scan | One-time purchase or free | 80/20 creator split |

**Key Stat:** "6.3 issues per skill on average" across platforms, "prompt injection in 36% of skills tested"
**Key Quote:** "The catalog size that actually matters is how many skills work well enough that other developers use them repeatedly."

---

### Agent Skills Open Standard — Adoption Details
**URL:** https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/

**Timeline:**
- October 16, 2025: Anthropic publishes Agent Skills
- December 18, 2025: Open standard released (agentskills.io), Apache 2.0 + CC-BY-4.0
- Within 48 hours: Microsoft VS Code + OpenAI (ChatGPT + Codex CLI) adopt it
- January 20, 2026: Vercel launches skills.sh marketplace
- March 2026: 32 adopters including Google, JetBrains, AWS, Block, Sourcegraph, Snowflake, Databricks, ByteDance, Mistral AI, Spring AI
- By Q2 2026: anthropics/skills repo hits 100K+ stars (now 136K)
- Vercel skills.sh: 89,753 skills listed

---

### MCP Security Vulnerabilities

**Source 1:** OX Security — "The Mother of All AI Supply Chains"
**URL:** https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/

**Source 2:** The Hacker News — "Anthropic MCP Design Vulnerability Enables RCE, Threatening AI Supply Chain"
**URL:** https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html

**Source 3:** OX Security — "MCP Supply Chain Advisory: RCE Vulnerabilities Across the AI Ecosystem"
**URL:** https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/

**Source 4:** Tom's Hardware — "Anthropic's Model Context Protocol includes a critical remote code execution vulnerability"
**URL:** https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed

**Key Facts:**
- Architectural RCE vulnerability in Anthropic's MCP design
- Affects: 150M+ downloads, 7,000+ publicly accessible servers, up to 200,000 vulnerable instances
- Affected IDEs: Cursor, VS Code, Windsurf, Claude Code, Gemini-CLI
- Windsurf (CVE-2026-30615): zero user interaction required for exploitation
- Microsoft MCP Server Vulnerability: CVE-2026-26118
- Attack types: Prompt injection, Tool poisoning, Supply chain attacks (fake/compromised tools in registries)
- Languages affected: Python, TypeScript, Java, Rust SDKs
- Anthropic response: Declined to modify protocol architecture, citing behavior as "expected"
- Some vendors issued patches; shortcoming remains in Anthropic's reference implementation

---

### MCP Ecosystem Scale in 2026

**Source:** MCP Servers Directory
**URL:** https://aiagentslist.com/mcp-servers
**Stats:** 593+ MCP servers indexed

**Source:** Smithery
**Description:** Closest equivalent to Docker Hub in MCP ecosystem
**Stats:** 7,000+ available servers

**Source:** MCPBundles
**URL:** https://www.mcpbundles.com/blog/best-mcp-servers
**Stats:** 10,000+ tools across 700+ providers for production SaaS integrations

**Key MCP Servers (as of 2026):**
- GitHub, Vercel, Stripe, Notion, Linear
- Tavily (real-time web search)
- Atlassian (46+ tools across Jira, Confluence, Compass, Jira Service Management)
- PostgreSQL, Figma, Docker, Kubernetes, Slack

**MCP Governance:**
- Donated to Linux Foundation's Agentic AI Foundation in December 2025
- Natively supported by Anthropic, OpenAI, Google, Microsoft

---

### AWS Agent Registry
**URL:** https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/
**Announced:** April 2026
**Status:** Preview
**Description:** Private, governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources within organizations
**Platform:** Amazon Bedrock AgentCore

---

### Kong MCP Registry
**URL:** https://konghq.com/products/mcp-registry
**Description:** Register, discover, and govern MCP servers and tools so AI agents connect only to trusted, approved resources
**Blog post:** https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery

---

### Official MCP Registry
**URL:** https://registry.modelcontextprotocol.io/
**Description:** Open-source catalog with live REST API for search and discovery

---

### Enterprise Skills Deployment

**Source:** Anthropic Support
**URL:** https://support.claude.com/en/articles/13119606-provision-and-manage-skills-for-your-organization
**Key Facts:**
- Organization-wide skill management available to Team and Enterprise plans
- Skills uploaded through organization settings automatically available to all users
- Managed settings cannot be overridden by user or project settings
- SOC 2 Type II compliance, SSO, role-based permissions
- Anthropic opened Claude Cowork to third-party platforms in April 2026
- Typical enterprise rollout: 4-6 weeks from pilot to org-wide availability

---

### Skills vs MCP Architecture Debate

**Source:** Ravikanth Chaganti blog
**URL:** https://ravichaganti.com/blog/agent-skills-vs-model-context-protocol-how-do-you-choose/

**Key Points:**
- Anthropic produced two standards (MCP and Agent Skills) that "seem to be competing"
- Heated debate on social media, HN, developer blogs
- Current consensus: both coexist, complement each other
- MCP = runtime tool access (external services, APIs)
- Skills = workflow/expertise packaging (how to do things)
- Architecture: Skills (workflow + quality bar) → MCP (standardized external access) → Tools (individual actions)

**Source:** DEV.to article
**URL:** https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k

---

### Polymarket / Prediction Market Integration

**Source:** MCP.Directory
**URL:** https://mcp.directory/skills/polymarket-agent
**Description:** Polymarket Agent Skill — Prediction Market Analyst and AI trading assistant

**Source:** MCP.Directory
**URL:** https://mcp.directory/skills/polymarket-trader
**Description:** polymarket-trader agent skill

**Source:** MCPMarket
**URL:** https://mcpmarket.com/server/polymarket-4
**Description:** Polymarket AI Agent API with 29 tools for real-time data from Kalshi and Polymarket, 9,706+ active contracts

**Source:** Graph Polymarket MCP
**URL:** https://glama.ai/mcp/servers/@PaulieB14/graph-polymarket-mcp
**Tools:** 20 tools for querying market data, trader P&L, positions, orderbook trades, open interest

**Source:** Conare Marketplace
**URL:** https://conare.ai/marketplace/mcp/graph-polymarket
**Description:** Graph Polymarket MCP Server

**ClawHub:** 13,700+ skills for AI trading automation (prediction markets)

---

### Additional Notable Sources

**Discover plugins docs:**
**URL:** https://code.claude.com/docs/en/discover-plugins

**Claude Skills complete guide:**
**URL:** https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026

**Claude Code Skills vs MCP complete guide:**
**URL:** https://www.morphllm.com/claude-code-skills-mcp-plugins

**Best Claude Code Skills 2026:**
**URL:** https://www.firecrawl.dev/blog/best-claude-code-skills

**Agent Skills explained simply (Medium):**
**URL:** https://medium.com/@tahirbalarabe2/ai-agent-skills-explained-simply-4010f6d9db92

**Deep Dive SKILL.md (Medium):**
**URL:** https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996

**Claude Code CLI Complete Guide:**
**URL:** https://blakecrosley.com/guides/claude-code

**MCP Roadmap 2026 (The New Stack):**
**URL:** https://thenewstack.io/model-context-protocol-roadmap-2026/

**MCP Predictions 2026 (DEV Community):**
**URL:** https://dev.to/blackgirlbytes/my-predictions-for-mcp-and-ai-assisted-coding-in-2026-16bm

**MCP Security Guide:**
**URL:** https://www.practical-devsecops.com/mcp-security-guide/

**TrueFoundry MCP Registries comparison:**
**URL:** https://www.truefoundry.com/blog/best-mcp-registries

**InfoWorld enterprise MCP registry:**
**URL:** https://www.infoworld.com/article/4145014/how-to-build-an-enterprise-grade-mcp-registry.html

**Composio YouTube MCP:**
**URL:** https://composio.dev/toolkits/youtube/framework/claude-code

**AI Agents for Prediction Markets:**
**URL:** https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi

**Claude Code Plugin Deep Dive (blog):**
**URL:** https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/

**BrightCoding — Claude Skills Marketplace:**
**URL:** https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers

**DEV.to — Best Claude Code Skills 2026:**
**URL:** https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4

**ScrimBA — Best Claude Code tutorials 2026:**
**URL:** https://scrimba.com/articles/best-claude-code-tutorials-and-courses-in-2026/

**LiteLLM Claude Code Plugin Marketplace:**
**URL:** https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace

**Nimbalyst — Claude Code Plugins Guide:**
**URL:** https://nimbalyst.com/blog/claude-code-plugins-guide/

**ScriptByAI — Ultimate Claude Code Resource List:**
**URL:** https://www.scriptbyai.com/claude-code-resource-list/

**Mejba.me — Top 10 Claude Code Skills, Plugins & CLIs 2026:**
**URL:** https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026

**Agensi — Claude Code Plugins vs Skills:**
**URL:** https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained

**Agensi — Plugin Marketplace Guide:**
**URL:** https://www.agensi.io/learn/claude-code-plugin-marketplace-guide

**ClaudeMarketplaces directory:**
**URL:** https://claudemarketplaces.com/

**Skywork — Skills Marketplace Guide:**
**URL:** https://skywork.ai/blog/ai-bot/claude-code-skills-marketplace-ultimate-guide/

**AgentSkill.club — Free Skills Library:**
**URL:** https://www.agentskill.club/

**SkillsMP:**
**URL:** https://skillsmp.com/

**LobeHub Skills:**
**URL:** https://lobehub.com/skills

**ClaudeSkills.info:**
**URL:** https://claudeskills.info/skills/

**Agent-skills.cc (Curated):**
**URL:** https://agent-skills.cc/

**ClaudePluginHub:**
**URL:** https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills

**AitMpl — Claude Code Plugins collection:**
**URL:** https://www.aitmpl.com/plugins/

**Toloka — Best MCP servers for AI agents:**
**URL:** https://toloka.ai/blog/best-mcp-servers-for-ai-agents/

**MCP Market directory:**
**URL:** https://mcpmarket.com/

**Analytics Vidhya — Top 10 MCP Servers 2026:**
**URL:** https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/

**K2View — Awesome MCP servers:**
**URL:** https://www.k2view.com/blog/awesome-mcp-servers

**Firecrawl — Best MCP Servers for Developers:**
**URL:** https://www.firecrawl.dev/blog/best-mcp-servers-for-developers

**MCPBundles — Best MCP Servers:**
**URL:** https://www.mcpbundles.com/blog/best-mcp-servers

**ByteBridge — MCP Gateways 2026:**
**URL:** https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a

**GetKnit — Future of MCP:**
**URL:** https://www.getknit.dev/blog/the-future-of-mcp-roadmap-enhancements-and-whats-next

**RuhAI — AI Agent Protocols 2026:**
**URL:** https://www.ruh.ai/blogs/ai-agent-protocols-2026-complete-guide

**Red Hat — Building effective AI agents with MCP:**
**URL:** https://developers.redhat.com/articles/2026/01/08/building-effective-ai-agents-mcp

**Wikipedia — Model Context Protocol:**
**URL:** https://en.wikipedia.org/wiki/Model_Context_Protocol

**Microsoft Learn — Using MCP Tools:**
**URL:** https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools

**MACH Alliance MCP Registry:**
**URL:** https://machalliance.org/mach-alliance-mcp-registry

**MCP Servers directory:**
**URL:** https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp

**Practical DevSecOps — MCP Security Vulnerabilities:**
**URL:** https://www.practical-devsecops.com/mcp-security-vulnerabilities/

**Aembit — Ultimate Guide to MCP Security:**
**URL:** https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/

**Adversa AI — MCP Security Resources (Feb 2026):**
**URL:** https://adversa.ai/blog/top-mcp-security-resources-february-2026/

**Adversa AI — MCP Security Resources (Mar 2026):**
**URL:** https://adversa.ai/blog/top-mcp-security-resources-march-2026/

**PointGuard AI — CVE-2026-26118:**
**URL:** https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118

**CyberDesserts — AI Agent Security Risks 2026:**
**URL:** https://blog.cyberdesserts.com/ai-agent-security-risks/

**Essa Mamdani — Complete Guide to MCP 2026:**
**URL:** https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026

**Databar.ai — Best MCP Servers for Sales 2026:**
**URL:** https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026

**SparkCo — Prediction Market Agent:**
**URL:** https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi

**MCPMarket — Polymarket Development Suite:**
**URL:** https://mcpmarket.com/tools/skills/polymarket-development-suite

**The ONLY Claude Code Tutorial (YouTube):**
**URL:** https://www.youtube.com/watch?v=LlFgLsffbBs

**Claude Code Tutorial Playlist:**
**URL:** https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY

**Verdent — What Are Claude Skills:**
**URL:** https://www.verdent.ai/guides/what-are-claude-skills-guide-2026

**Strapi — What Are Agent Skills:**
**URL:** https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them

**Paperclipped — Agent Skills Open Standard Explained:**
**URL:** https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/

**ObviousWorks — Claude Skills vs MCP:**
**URL:** https://www.obviousworks.ch/en/claude-skills-vs-mcp-the-ultimate-guide-to-efficient-ki-workflows/

**Duet.so — Agent Skills 101:**
**URL:** https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills

**DevToolPicks — Claude Skills vs MCP:**
**URL:** https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026

**AIToolDiscovery — Claude Code Reddit:**
**URL:** https://www.aitooldiscovery.com/guides/claude-code-reddit

**DEV.to — Claude Code Skills Practical Guide:**
**URL:** https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p

**Nimbalyst — Claude Code Skills Guide:**
**URL:** https://nimbalyst.com/blog/claude-code-skills-guide/

**TolokAI — What is MCP:**
**URL:** https://toloka.ai/blog/what-is-model-context-protocol-mcp/

**Complete Guide to Building Skills for Claude (PDF):**
**URL:** https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf

**Claude Skills: Complete 2026 Guide:**
**URL:** https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026

**IntentSolutions CCPI (npm):**
**URL:** https://www.npmjs.com/package/@intentsolutionsio/ccpi

**NimbaLyst — Claude Code Plugins:**
**URL:** https://nimbalyst.com/blog/claude-code-plugins-guide/

**ScriptByAI — Claude Code Resource List:**
**URL:** https://www.scriptbyai.com/claude-code-resource-list/

**Agent Skills Directory (MCP Market):**
**URL:** https://mcpmarket.com/tools/skills

**LobeHub — Agent Skills Marketplace:**
**URL:** https://lobehub.com/skills

**IntuitionLabs — Claude Enterprise Guide:**
**URL:** https://intuitionlabs.ai/articles/claude-enterprise-deployment-training-guide-2026

**SystemPrompt.io — Enterprise Rollout:**
**URL:** https://systemprompt.io/guides/claude-code-organisation-rollout

**CodingNomads — Enterprise Deployment:**
**URL:** https://codingnomads.com/claude-code-enterprise-deployment-policies-settings

**Enterprise Managed Settings:**
**URL:** https://systemprompt.io/guides/enterprise-claude-code-managed-settings

**TrueFoundry — Enterprise Security:**
**URL:** https://www.truefoundry.com/blog/enterprise-security-for-claude

**UseSkills in Claude Help:**
**URL:** https://support.claude.com/en/articles/12512180-use-skills-in-claude
