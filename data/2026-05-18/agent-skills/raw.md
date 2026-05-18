# Agent Skills & Plugin Ecosystem — Raw Research Data
**Date collected:** 2026-05-18
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## OFFICIAL ANTHROPIC SOURCES

### Anthropic Engineering Blog: "Equipping agents for the real world with Agent Skills"
URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills

**What Agent Skills Are:**
Agent Skills are organized folders containing instructions, scripts, and resources that extend Claude's capabilities for specialized tasks. They function as composable, reusable packages of procedural knowledge that transform general-purpose agents into domain-specific specialists.

**How They Work — Progressive Disclosure Architecture:**
- Level 1: Metadata (name and description) loads at startup, helping Claude decide when to use a skill (~100 tokens per skill)
- Level 2: Full SKILL.md file loads when Claude determines relevance (under 5k tokens)
- Level 3+: Additional linked files and code execute only when needed (effectively unlimited)
This architecture allows skills to bundle effectively unlimited context without consuming the entire token budget at once.

**Key Features:**
- Built around a SKILL.md file starting with YAML frontmatter
- Can include supplementary files (reference guides, specific instructions) and executable code
- Code can run deterministically without loading full scripts into context
- Works across Claude.ai, Claude Code, the Agent SDK, and Claude Developer Platform

**Security Advisory:**
Install skills only from trusted sources; thoroughly audit unfamiliar skills before use, particularly examining code dependencies and external network connections.

**Future Plans:**
Anthropic plans to expand skill creation, discovery, and sharing features, and explore complementary integration with Model Context Protocol servers.

---

### Claude API Official Documentation: Agent Skills Overview
URL: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

**Pre-Built Agent Skills Available:**
- PowerPoint (pptx): Create presentations, edit slides, analyze presentation content
- Excel (xlsx): Create spreadsheets, analyze data, generate reports with charts
- Word (docx): Create documents, edit content, format text
- PDF (pdf): Generate formatted PDF documents and reports

**Open-Source Skills (from Anthropic):**
- Claude API skill: Up-to-date API reference material, SDK documentation, best practices for 8 programming languages
URL: https://github.com/anthropics/skills

**Cross-Surface Availability Limitations:**
- Custom Skills do NOT sync across surfaces (claude.ai, API, Claude Code are all separate)
- claude.ai: Individual user only (not org-wide)
- Claude API: Workspace-wide
- Claude Code: Personal (~/.claude/skills/) or project-based (.claude/skills/)

**Runtime Environment Constraints:**
- Claude API: No network access, no runtime package installation
- Claude Code: Full network access, global package installation discouraged
- claude.ai: Varying network access depending on user/admin settings

**Beta Headers Required (Claude API):**
- code-execution-2025-08-25
- skills-2025-10-02
- files-api-2025-04-14

---

### Claude Code Official Documentation: Create Plugins
URL: https://code.claude.com/docs/en/plugins

**Plugin Architecture:**
Plugins are distribution packages that can bundle:
- Skills (SKILL.md files)
- Custom agents (sub-agents)
- Hooks (hooks/hooks.json)
- MCP server configurations (.mcp.json)
- LSP server configurations (.lsp.json)
- Background monitors (monitors/monitors.json)
- Executables (bin/)
- Default settings (settings.json)

**Plugin Manifest (plugin.json):**
```json
{
  "name": "my-first-plugin",
  "description": "Plugin description",
  "version": "1.0.0",
  "author": { "name": "Your Name" }
}
```

**Standalone vs. Plugin:**
| Approach | Best for |
|---------|---------|
| Standalone (.claude/ directory) | Personal workflows, project-specific, quick experiments |
| Plugins (with .claude-plugin/plugin.json) | Sharing with teams/community, distributing via marketplace |

**Plugin Install Commands:**
- `/plugin install` — install from marketplace
- `/plugin enable` / `/plugin disable`
- `/plugin marketplace add user-or-org/repo-name`
- `/reload-plugins` — pick up changes without restarting

**Official Anthropic Marketplace:**
Pre-configured; submission forms at:
- Claude.ai: https://claude.ai/settings/plugins/submit
- Console: https://platform.claude.com/plugins/submit

**Testing:**
```bash
claude --plugin-dir ./my-plugin
claude --plugin-dir ./my-plugin.zip
claude --plugin-url https://example.com/my-plugin.zip
```

---

### Claude Agent SDK Blog Post
URL: https://claude.com/blog/building-agents-with-the-claude-agent-sdk

**What the Agent SDK Is:**
The Claude Agent SDK (formerly Claude Code SDK) is a collection of developer tools for building autonomous agents powered by Claude. It enables agents to operate with computer access—writing files, running commands, and iterating on work.

**Core Agent Loop:**
1. Gather context (file systems, semantic search, subagents, conversation compaction)
2. Take action (tools, bash scripts, code generation, MCP integrations)
3. Verify work (rule-based feedback, visual feedback, LLM judges)
4. Iterate (refining outputs based on evaluation results)

**Key Capabilities:**
- MCP: Standardized integrations with external services (Slack, GitHub, Asana) handling authentication automatically
- Subagents: Enable parallel task execution and isolated context management
- Agentic search: Claude uses bash commands to intelligently load context from folder structures

**Primary Use Cases:**
- Finance agents, personal assistants, customer support agents, deep research agents

**Docs:** https://docs.claude.com/en/api/agent-sdk/overview

---

## HACKER NEWS

### "Claude Skills" (816 points, 427 comments)
URL: https://news.ycombinator.com/item?id=45607117

**Pro-Skills Perspectives:**
- Simon Willison: Skills are "maybe a bigger deal than MCP," emphasizing their role in dynamic context assembly
- Skills enable context-efficient instruction delivery, only loading when needed—solving token wastage problems
- "dynamic context assembling with stuff crossing user boundaries" enables organizational skill-sharing
- "an interesting shift in thinking how to work with these tools"

**Skeptical Perspectives:**
- Critics argued Skills are "just prompt engineering" or "a design pattern"
- "you're getting hyped over a framework to append text to your prompt"
- Multiple users questioned overlap with existing tools (MCP prompts, AGENTS.md, Cursor Rules)
- "do we lose some deterministic behavior of MCP plumbing"

**Technical Observations:**
- Context Management: Skills solve real problems around context window limitations for large projects
- Skills vs Projects: Skills function as reusable, toggleable instruction sets within larger projects
- Network Access Limitations: Claude.ai environment restricts external API access beyond PyPI/NPM

---

### "Customize Claude Code with plugins" (48 points)
URL: https://news.ycombinator.com/item?id=45530150

**Plugin System Launch (Claude Code v2.0.12):**
- Features: plugin management including installation, enabling/disabling, marketplace integration
- `/plugin validate` and `/doctor` diagnostics added

**Community Responses:**
- Developer built claudecodemarketplace.com, stating "distribution is going to be key"
- Plugin maintainers shouldn't have to build their own marketplaces
- GitHub-based marketplace collections emerged immediately
- Security developer highlighted creating a "secret scanner hook" marketplace

**Technical Issue Noted:**
SSH authentication errors when using the shorthand "anthropics/claude-code"; fix: use full HTTPS URL.

---

### "Skills Manager – manage AI agent skills across Claude, Cursor, Copilot" (3 points, 9 comments)
URL: https://news.ycombinator.com/item?id=47423910

**The Problem Being Solved:**
Fragmentation across agents: skills stored in different locations and formats across Claude, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Goose, Codex.

**Key Discussion:**
- "the same instruction produces very different results depending on the agent"
- Claude handles multi-step rules effectively; Copilot tends to disregard anything beyond initial instructions
- Most coding agents support `~/.agents/skills` as standard path; Claude Code diverges
- "We need a unified skill marketplace for different agents."
- Skills Manager tool available free + open source: https://sm.idoevergreen.me

---

### "Claude Code Skills and Plugins as an Open Source Project"
URL: https://news.ycombinator.com/item?id=47321892

---

### "Ask HN: Best option for hosted agent in 2026?" (3 points, 2 comments)
URL: https://news.ycombinator.com/item?id=46917293

**Platforms Mentioned:**
- Claude Agent SDK (recommended as current state-of-the-art)
- OpenClaw agents (capable but requires security management)
- Open Hands (openhands.dev)
- LangGraph and OpenAI Agents SDK (alternative with model flexibility)

**Key Advice:**
Separate "superagent" into distinct specialist agents; improves focus and effectiveness.

---

### "Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills"
URL: https://news.ycombinator.com/item?id=46693426

---

### "A Claude Code and Codex Skill for Deliberate Skill Development"
URL: https://news.ycombinator.com/item?id=48130679

---

### "Show HN: Real-time dashboard for Claude Code agent teams"
URL: https://news.ycombinator.com/item?id=47602986

---

### "How I use every Claude Code feature"
URL: https://news.ycombinator.com/item?id=45786738

---

### "Superwhisper now integrates with Claude Code"
URL: https://news.ycombinator.com/item?id=47936169

---

## GITHUB REPOSITORIES

### awesome-claude-code
URL: https://github.com/hesreallyhim/awesome-claude-code
- Stars: 44.1k | Forks: 3.8k | Watchers: 300
- Description: Curated list of awesome skills, hooks, slash-commands, agent orchestrators, applications, and plugins for Claude Code
- Status: Undergoing reorganization (previous structure "was no longer fit for purpose")
- 310 open issues, 1,157 total commits
- Emphasizes "high quality, skills, security, and originality"

### antigravity-awesome-skills
URL: https://github.com/sickn33/antigravity-awesome-skills
- Stars: 37.9k | Forks: 6.2k
- Skills: 1,460+ agentic skills
- Version: V11.3.0
- License: MIT (code), CC BY 4.0 (documentation)
- Supported Agents: Claude Code, Cursor, Codex CLI, Gemini CLI, Antigravity, Kiro, OpenCode, GitHub Copilot, AdaL CLI
- Install: `npx antigravity-awesome-skills`
- Contributors: 200+ individual contributors
- Partners: Anthropic, OpenAI, Google, Vercel Labs, Supabase, Microsoft, Hugging Face
- Universal Starter Skills: brainstorming, TDD, debugging, linting, security auditing, frontend design, API design, pull request creation

### claude-code-plugins-plus-skills
URL: https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- 425 plugins, 2,810 skills, 200 agents for Claude Code
- Open-source marketplace at tonsofskills.com with ccpi CLI package manager

### VoltAgent awesome-agent-skills
URL: https://github.com/VoltAgent/awesome-agent-skills
- 1,000+ agent skills from official dev teams and community
- Compatible with Claude Code, Codex, Gemini CLI, Cursor, and more

### awesome-claude-plugins (ComposioHQ)
URL: https://github.com/ComposioHQ/awesome-claude-plugins
- Description: Curated list of plugins extending Claude Code with custom commands, agents, hooks, and MCP servers

### awesome-claude-code-toolkit (rohitg00)
URL: https://github.com/rohitg00/awesome-claude-code-toolkit
- 135 agents, 35 curated skills (+400,000 via SkillKit), 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, 26 companion apps, 52 ecosystem entries

### alirezarezvani/claude-skills
URL: https://github.com/alirezarezvani/claude-skills
- 263+ Claude Code skills for engineering, marketing, product, compliance, C-level advisory

### agent-startup-kit (Blink-h)
URL: https://github.com/Blink-h/agent-startup-kit
- Reusable AI coding workflows for Claude Code and VS Code

### claude-multi-agent-architecture (mnzralee)
URL: https://github.com/mnzralee/claude-multi-agent-architecture
- Production-ready template: 185 specialized AI agents, 16 multi-agent workflow orchestrators, 153 agent skills, 100 commands organized into 80 focused plugins

### Polymarket Skills Repos
- https://github.com/atompilot/polymarket-skill — Claude Code skill for Polymarket API (Polygon integration)
- https://github.com/mjunaidca/polymarket-skills — Composable skills for prediction market trading, paper-trading-first, security-audited
- https://github.com/harish-garg/Claude-Plugin-Marketplace-for-Polymarket — Suite of modular plugins for Polymarket platform

---

## SKILL MARKETPLACES

### SkillsMP (skillsmp.com)
URL: https://skillsmp.com/
- Total skills: 1,419,713+ (from GitHub repos, min 2-star quality filter)
- Compatible: Claude Code, OpenAI Codex CLI, ChatGPT
- Categories: Tools (340,854), Business (249,376), Development (202,543), Testing & Security (146,642), Data & AI (133,453), DevOps (114,069), Documentation (97,418), Content & Media (87,176), Research (51,212)
- Features: AI-powered semantic search, REST API (free), MCP server support
- Pricing: Completely free, community-driven
- "Skills are model-invoked—Claude automatically decides when to use them based on context"

### ClaudeMarketplaces.com
URL: https://claudemarketplaces.com/
- 6,700+ skills, 2,500+ marketplaces aggregated, 840+ MCP servers catalogued
- Skills Directory: https://claudemarketplaces.com/skills

### Tonsofskills.com
URL: https://tonsofskills.com/
- Curated by Jeremy Longshore
- 427 plugins, updated 2026-05-07
- Every submission reviewed; notable entries get homepage feature and Hall of Fame listing
- Active development; new plugins added weekly

### Agensi Marketplace
URL: https://www.agensi.io/
- Revenue split: 80/20 favoring creators
- Security scanning for dangerous commands and obfuscated code
- Verified marketplace for community plugins

### Skills.sh (Vercel)
- Launched: January 20, 2026
- Skills indexed: 89,753

### LobeHub Skills
- Skills indexed: 169,739

### MCP Market
URL: https://mcpmarket.com/
- MCP server directory with tools and skills sections
- Includes Polymarket skill listings

### AI Agents List MCP Directory
URL: https://aiagentslist.com/mcp-servers
- 593+ MCP servers catalogued

---

## MCP ECOSYSTEM STATISTICS

Source: https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol
Source: https://effloow.com/articles/mcp-ecosystem-growth-100-million-installs-2026
Source: https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/

**Growth Metrics:**
- Public MCP server registry: Q1 2025: 1,200 servers → April 2026: 9,400+ servers (7.8x YoY, +18% MoM in Q1 2026)
- SDK downloads: 97-110 million per month (David Soria Parra, MCP co-creator)
- Enterprise AI teams (50+ practitioners) with MCP in production: 78% (up from 31% a year prior)
- 300+ MCP clients across editors, chat apps, enterprise platforms
- 80% of top servers offer remote deployment options

**Clients Supporting MCP:**
Claude (native), ChatGPT (April 2025), Google Gemini API and Vertex AI (March 2026), Cursor, Windsurf, Zed, JetBrains AI Assistant, Vercel AI SDK, OpenAI Agents SDK

---

## SKILL.MD OPEN STANDARD ADOPTION

Source: https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
Source: https://www.agensi.io/learn/agent-skills-open-standard

**Timeline:**
- September 22, 2025: anthropics/skills repository created
- October 2025: Skills appear in Claude Code
- December 12, 2025: Evidence of OpenAI building undisclosed support
- December 18, 2025: Official open standard announcement (Anthropic)
- Within 48 hours: Microsoft (VS Code) and OpenAI (ChatGPT, Codex CLI) integrated support
- January 20, 2026: Vercel launched skills.sh marketplace
- February 5, 2026: AWS Kiro IDE shipped support
- March 2026: 32 total adopters confirmed

**Tools Supporting SKILL.md (as of March 2026):**
Anthropic (Claude Code), OpenAI (Codex CLI, ChatGPT), Microsoft (VS Code, GitHub Copilot), Google (Gemini CLI), JetBrains (Junie), AWS (Kiro), Block (Goose), Sourcegraph (Amp), Snowflake, Databricks, ByteDance (TRAE), Mistral AI (total: 32)

**Simon Willison Quote:**
The specification is "quite heavily under-specified," particularly regarding metadata fields and the experimental `allowed-tools` mechanism.

**Market Growth:**
Monthly search volume for agent skills terms: 21,000 → 400,000+ (19x growth in 2 years)

---

## SECURITY VULNERABILITIES & CONCERNS

### The Register: "Bug hunter tracks down three massive MCP flaws"
URL: https://www.theregister.com/security/2026/05/13/bug-hunter-tracks-down-three-serious-mcp-database-flaws-one-left-unpatched/5238916

**CVE-2025-66335 — Apache Doris MCP SQL Injection:**
- exec_query fails to validate db_name before constructing SQL queries
- Allows injection of malicious SQL statements
- Status: Patched in December

**Apache Pinot MCP — Authentication Bypass:**
- Uses HTTP without authentication
- Enables unauthenticated remote attackers to execute queries
- Status: StarTree added OAuth option; Apache opened security issue

**Alibaba RDS MCP — Information Disclosure:**
- No authentication before RAG tool invocation
- Allows exfiltration of table names, schema definitions, sensitive metadata
- Status: UNPATCHED — Alibaba declined to fix, claiming "not applicable"

**Notable Quote:**
"There is missing or faulty security validation between the MCP server and its back end...these security gaps will become high-value targets for attackers." — Tomer Peled, Akamai security analyst

### Broader MCP Security Landscape
Sources:
- https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/
- https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/
- https://www.practical-devsecops.com/mcp-security-vulnerabilities/
- https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/
- https://live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed-what-you-need-to-know-now/ba-p/1227143
- https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118

**Key Stats:**
- 30+ CVEs filed in Jan-Feb 2026 targeting MCP infrastructure
- Only 8.5% of MCP servers use OAuth; rest rely on static API keys or no auth
- 9 of 11 MCP registries successfully "poisoned" with malicious trial balloon
- Microsoft CVE-2026-26118: MCP server vulnerability enabling AI tool hijacking
- Major threat vectors: prompt injection, tool poisoning, version drift/supply chain attacks

---

## YOUTUBE VIDEOS

### "The Ultimate Claude Code Guide | MCP, Skills & More"
URL: https://www.youtube.com/watch?v=uogzSxOw4LU
- Posted: April 2026
- Covers: MCP configuration, Skills setup, Nimbalyst integration

### "Máster Claude Code 2026: Agentes IA, MCP, Skills y Comandos"
URL: https://www.youtube.com/watch?v=roPfcQHdUtY
- Posted: ~1 month ago (Spanish-language)
- Covers: AI agents, MCP, Skills, Claude Code commands

### "How I Actually Use Claude Every Day in 2026"
URL: https://www.youtube.com/watch?v=EZcYjH3jAo8
- Posted: 2 weeks ago
- Covers: Claude Skills, Connectors, MCP Services

### "Full Claude Code Tutorial for Non-Technical Beginners in 2026 (step-by-step)"
URL: https://www.youtube.com/watch?v=bqJzIWAEn40
- Posted: 3 weeks ago
- Covers: Full Claude Code setup for beginners

---

## POLYMARKET

Source: https://polymarket.com/predictions/claude

**Active Claude-Related Markets ($1.1M+ aggregate volume):**
- "Claude Mythos released by…?" — 20% odds, $375K volume
- "Claude score on Humanity's Last Exam by June 30?" — 20% odds (45%+ threshold), $283K volume
- "Anthropic Claude score on FrontierMath Benchmark by June 30?" — 54% odds (50%+ threshold), $62.9K volume
- "Will Claude go down on __ days in May?" — 45% odds (9-11 range), $33.9K volume
- "Anthropic valued higher than OpenAI in 2026?" — 90% odds, $81.4K volume
- "Will Anthropic make a deal with the Pentagon by June 30?" — 23% odds, $132K volume
- "Trump orders federal review of AI model releases by May 31?" — 17% odds, $66.2K volume

Note: Markets focus on Claude model performance/releases; no direct agent skills/plugin markets found.

---

## KEY BLOG POSTS & ANALYSIS

### Personal Setup: "My Claude Code Setup After 4 Months of Daily Use"
URL: https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/

**MCP Servers in Active Use:**
1. Coolify MCP — deployment management, service restarts, database management
2. Telegram MCP — message reading, replies, channel management for 24/7 automation
3. Codex MCP — dual-model review with OpenAI for independent validation

**Custom Skills Built:**
- ton-analyst: Dune SQL queries for blockchain analysis
- ton-profiler: Wallet connection investigation, relationship graph building
- crosspost: Content distribution across Telegram, Ghost blog, social media in 3 languages

**Workflow:**
Voice notes → transcription → agent handles SQL, formatting, charts, reports
Time savings: Hours of analytical work → ~20 minutes review
Cost: $100/month Claude Max plan

---

### SKILL.md vs CLAUDE.md vs AGENTS.md Comparison
URL: https://www.termdock.com/blog/skill-md-vs-claude-md-vs-agents-md

---

### DEV.to: "Best Claude Code Skills & Plugins (2026 Guide)"
URL: https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4

**Top Skills by Category:**
Development & Learning: Git Dojo (5 EUR), Code Review, Test Writer, Commit Helper
Productivity: Napkin (documentation), Project Bootstrap
Design & Frontend: Component Builder, Design System Auditor, Accessibility Checker (WCAG)
Content: Brand Voice, Content Pipeline, Localization, SEO Audit

**Key Statistics:**
- Most Claude Code users operate without customization ("vanilla")
- Paid skills typically cost 5-15 EUR
- Recommended skill size: under 2,000 tokens for optimal performance
- 10 skills at 2,000 tokens each = ~5% of context window
- Custom skills > generic ones (project-specific configurations provide greater ROI)

---

### KDNuggets: "Top 5 Agent Skill Marketplaces"
URL: https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents

**Eight marketplaces that matter:**
Claude Skills, GPT Store, MCP Hubs, Hugging Face Spaces, Replit Agent Market, LangChain Hub, Vercel Agent Gallery, Cloudflare AI Marketplace

---

### Chris Ayers: "Agent Skills, Plugins and Marketplace: The Complete Guide"
URL: https://chris-ayers.com/posts/agent-skills-plugins-marketplace/

**Key Distinction:**
- Skills follow an open standard (agentskills.io) shared across 20+ AI coding agents
- 20+ AI coding agents supporting SKILL.md = sufficient installed base to sustain marketplace economy
- "Every major computing platform eventually gets a marketplace. PCs got software stores. Smartphones got the App Store and Google Play. Browsers got extension stores. AI agents are getting skills marketplaces."

---

### MCP Security State — March 2026
URL: https://nimblebrain.ai/blog/state-of-mcp-security-2026/

---

### Analytics Vidhya: "Top 10 MCP Servers for AI Builders in 2026"
URL: https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/

**Top MCP Servers:**
GitHub, Vercel, Stripe, Notion, Linear, Tavily (real-time web search), Playwright (browser automation), PostgreSQL, Figma

---

### MCP Dev Summit North America 2026
URL: https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/

**MCP is Now Enterprise Infrastructure**
Key Enterprise Adoption Stats:
- 78% of enterprise AI teams have MCP in production (up from 31% a year prior)
- 110M+ SDK downloads/month (David Soria Parra)

---

### Marketplace Comparisons
URL: https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison
URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
URL: https://authority.md/guides/best-places-to-buy-claude-skills

**Summary:**
- For scale: SkillsMP
- For curated engineering workflows: SkillHub or awesome-claude on GitHub
- For aggregation: ClaudeMarketplaces.com
- For curated/reviewed: tonsofskills.com
- Most marketplaces lack quality ranking (biggest gap across the category)

---

## ADDITIONAL WEB SOURCES (SUPPLEMENTARY)

- https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work — How marketplaces work (developer guide)
- https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026 — Marketplace comparison
- https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ — New plugin ecosystem analysis
- https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained — Skills and plugins explained
- https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution — Discovery & distribution
- https://www.morphllm.com/claude-code-plugins — Plugins overview
- https://www.morphllm.com/claude-code-plugins-vs-skills — Plugins vs skills comparison
- https://blakecrosley.com/guides/claude-code — Complete CLI guide with Hooks, MCP, Skills
- https://nimbalyst.com/blog/claude-code-plugins-guide/ — 2026 plugins guide
- https://nimbalyst.com/blog/best-claude-code-mcp-servers/ — Best MCP servers ranked
- https://composio.dev/content/top-claude-code-plugins — Top plugins from Composio
- https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know — MCP vulnerability guide
- https://www.scriptbyai.com/claude-code-resource-list/ — Ultimate resource list 2026
- https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 — Top 10 skills/plugins/CLIs
- https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026 — Complete skills guide
- https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 — Must-have skills
- https://medium.com/mcp-server/the-rise-of-mcp-protocol-adoption-in-2026-and-emerging-monetization-models-cb03438e985c — MCP monetization
- https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a — MCP gateways
- https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools — Microsoft MCP tools docs
- https://deepwiki.com/microsoft/agent-skills/4-plugins — Microsoft agent skills plugins
- https://www.firecrawl.dev/blog/best-claude-code-skills — Best Claude Code skills
- https://www.firecrawl.dev/blog/best-mcp-servers-for-developers — Best MCP for devs
- https://mcpbundles.com/blog/best-mcp-servers — Best MCP servers updated April 2026
- https://toloka.ai/blog/best-mcp-servers-for-ai-agents/ — Best MCP for agents
- https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 — MCP for sales
- https://www.k2view.com/blog/awesome-mcp-servers — Awesome MCP directory
- https://codeless.co/best-claude-mcp-servers/ — Best Claude MCP servers
- https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/ — MCP ecosystem overview
- https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1 — 5 MCP servers every Claude Code user should know
- https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ — SkillsMP marketplace guide
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — Skills.sh guide
- https://claude-plugins.dev/ — Claude Code Plugins & Agent Skills community registry with CLI
- https://claudeskills.info/skills/ — Claude Skills Directory (free)
- https://www.agentskills.in/marketplace/@Jamie-BitFlight/claude-plugins-reference-2026 — Plugin reference
- https://findskill.ai/blog/claude-cowork-guide/ — Claude Cowork guide
- https://docs.chainstack.com/docs/polygon-creating-a-polymarket-trading-openclaw-skill — Polymarket OpenClaw skill
- https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf — Anthropic PDF guide
- https://www.udemy.com/course/claude-course-prompt-skills-mcp-claude-code-cowork-etc/ — Udemy course
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — AI agent security risks 2026
- https://docs.anthropic.com/en/docs/claude-code/sub-agents — Official subagents docs
- https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md — Agent teams workflow guide
- https://github.com/wshobson/agents — Intelligent automation and multi-agent orchestration
- https://github.com/catlog22/Claude-Code-Workflow — JSON-driven multi-agent cadence-team framework
