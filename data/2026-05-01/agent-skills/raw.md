# Agent Skills — Raw Research Data
**Date:** 2026-05-01
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## Pipeline Notes
- Primary pipeline: WebSearch across multiple queries
- Platforms attempted: Web, YouTube, GitHub, Hacker News
- Platforms with no results: Reddit (no direct threads surfaced), X/Twitter (blocked), TikTok, Instagram, Bluesky, Polymarket
- Supplementary: WebFetch on key URLs

---

## SEARCH BATCH 1: Claude Code Skills, Plugins, MCP Servers

### Query: "Claude Code skills plugins MCP servers 2026"

**Results:**
- "50+ Best MCP Servers for Claude Code in 2026" — https://claudefa.st/blog/tools/mcp-extensions/best-addons
- "Claude Code Skills vs MCP vs Plugins: Complete Guide 2026" — https://www.morphllm.com/claude-code-skills-mcp-plugins
- "Connect Claude Code to tools via MCP - Claude Code Docs" — https://code.claude.com/docs/en/mcp
- "Best Claude Code Plugins, Skills & MCP Servers (2026) | TurboDocx" — https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers
- "Best Claude Code Skills & Plugins (2026 Guide) - DEV Community" — https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4
- "Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks Explained | alexop.dev" — https://alexop.dev/posts/understanding-claude-code-full-stack/
- "Claude Code Plugins | Skills, MCP Servers & Marketplace Directory" — https://claudemarketplaces.com/
- "7 Best Claude Code Plugins Every Developer Should Install in 2026 | Redwerk" — https://redwerk.com/blog/best-claude-code-plugins/
- "GitHub - jeremylongshore/claude-code-plugins-plus-skills: 423 plugins, 2,849 skills, 177 agents" — https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- "Claude Code Skills vs MCP Servers — What to Use, How to Install, and the Best Ones in 2026 - DEV Community" — https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k

**Key Findings:**
- Three main extension systems: Skills (markdown instruction files, 30-50 tokens each, loaded on-demand), Plugins (bundles of slash commands, subagents, MCP configs, hooks, skills), MCP Servers (tool/database/API integrations via Model Context Protocol)
- As of April 2026: 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces
- Over 150 skills on claudemarketplace.com as of March 2026
- MCP Tool Search enables lazy loading, reducing context usage by up to 95%
- Recommended stack: 2-3 MCP servers + a few custom skills; max 2-3 active plugins to avoid context degradation

---

## SEARCH BATCH 2: Agent Skill Marketplaces

### Query: "agent skill marketplace plugin ecosystem 2026"

**Results:**
- "Agent Skills, Plugins and Marketplace: The Complete Guide" — https://chris-ayers.com/posts/agent-skills-plugins-marketplace/
- "Claude Skills Marketplace: The Essential Plugin Hub for Developers" — https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers
- "Agent Skills Marketplace | Claude, Codex & ChatGPT Skills · LobeHub" — https://lobehub.com/skills
- "The Best AI Agent Skills Marketplaces in 2026 — Honest Comparison" — https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- "Agent Skills Marketplace - Claude, Codex & ChatGPT Skills | SkillsMP" — https://skillsmp.com/
- "Top 5 Agent Skill Marketplaces for Building Powerful AI Agents - KDnuggets" — https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
- "Agent Skills Marketplace: Skills.sh Guide (2026)" — https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/
- "Extend your coding agent with .NET Skills - .NET Blog" — https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/
- "Marketplace Home - Agent Skill Marketplace" — https://agentskillexchange.com/
- "Plugins | microsoft/agent-skills | DeepWiki" — https://deepwiki.com/microsoft/agent-skills/4-plugins

**Key Findings:**
- MAJOR PLATFORMS:
  - SkillsMP: 425,000+ skills, open SKILL.md standard
  - skills.sh (Vercel): launched January 20, 2026; directory + leaderboard; 90,000+ skills; 19 agent platforms; top skill "find-skills" by Vercel Labs with 579,000+ installs
  - LobeHub: 169,739 skills indexed, fast-growing
  - ClaudeSkills.info: 658+ free skills, including official Anthropic skills (PDF, DOCX, XLSX, frontend design, MCP builder)
  - tonsofskills.com: 2,849 skills, 423 plugins, 177 agents, ccpi CLI package manager
- MCP-based access: connect to marketplace MCP server once, load skills on demand, no manual updates
- SKILL.md open standard originally published by Anthropic in December 2025, later adopted by OpenAI

---

## SEARCH BATCH 3: MCP Server Registry, Claude Extensions

### Query: "MCP server tools registry Claude extensions April 2026"

**Results:**
- "Getting Started with Local MCP Servers on Claude Desktop" — https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop
- "Install and Configure MCP Servers in Claude Code (2026)" — https://systemprompt.io/guides/claude-code-mcp-servers-extensions
- "How to Set Up MCP in Claude Desktop (Complete 2026 Guide)" — https://mcpplaygroundonline.com/blog/how-to-setup-mcp-claude-desktop
- "Kestra MCP: A Live Plugin and Blueprint Catalog for AI Coding Agents" — https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints
- "50+ Best MCP Servers for Claude Code in 2026" — https://claudefa.st/blog/tools/mcp-extensions/best-addons
- "Connect to local MCP servers - Model Context Protocol" — https://modelcontextprotocol.io/docs/develop/connect-local-servers
- "MCP Servers List 2026: Complete Directory of 70+ Production Servers" — https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory
- "Connect Claude Code to tools via MCP - Claude Code Docs" — https://code.claude.com/docs/en/mcp
- "How to Set Up MCP Servers in Claude Desktop (2026 Guide)" — https://toolradar.com/blog/claude-desktop-mcp-server-setup
- "Cursor MCP Servers: Complete Setup Guide for 2026" — https://claudefa.st/blog/tools/mcp-extensions/cursor-mcp-setup

**Key Findings:**
- 500+ community servers in modelcontextprotocol/servers registry; ~70 matter most for real workflows
- Official transport as of April 2026: Streamable HTTP (MCP protocol 2025-11-25)
- Desktop Extensions (.dxt / now .mcpb): one-click install for local MCP servers
- Claude Desktop settings has Anthropic-reviewed extension directory
- `claude mcp` command handles all MCP server management in Claude Code
- MCP Tool Search: lazy loading reduces context by up to 95%; auto-enabled when tools > 10% context

---

## SEARCH BATCH 4: Custom Workflows, Reusable Agent Capabilities

### Query: "Claude Code custom workflows reusable agent capabilities 2026"

**Results:**
- "Create custom subagents - Claude Code Docs" — https://code.claude.com/docs/en/sub-agents
- "Agent Skills - Claude API Docs" — https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- "Claude Code 2026: Subagents, MCP, Skills and Plugins Bootcamp" — https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/
- "Claude Introduces Agent Skills for Custom AI Workflows - DevOps.com" — https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/
- "Claude Code: Workflows and Best Practices 2026" — https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/
- "Claude Code Skills & Agents: Build Custom Slash Commands for Real Work - DEV Community" — https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865
- "GitHub - wshobson/agents: Intelligent automation and multi-agent orchestration for Claude Code" — https://github.com/wshobson/agents
- "Claude Managed Agents bring execution and control to AI agent workflows - Help Net Security" — https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/
- "claude-code-ultimate-guide/agent-teams.md" — https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md
- "Claude AI Workflows | How I AI — Step-by-Step Guides" — https://www.chatprd.ai/how-i-ai/workflows/tool/claude

**Key Findings:**
- Skills stored globally: ~/.claude/skills/ (available in every project) or project-specific: .claude/skills/ (version-controllable)
- Subagents: each runs in own context with custom system prompt, specific tool access, independent permissions
- Agent Teams (research preview): multiple agents working in parallel on shared codebases
- Claude Managed Agents (launched April 8, 2026): composable APIs for cloud-hosted agents; handles sandboxed execution, checkpointing, credential management, scoped permissions, end-to-end tracing; $0.08/session-hour + token costs

---

## SEARCH BATCH 5: SKILL.md Open Standard

### Query: "SKILL.md standard Anthropic OpenAI agent skills open standard 2026"

**Results:**
- "What Is the Agent Skills Open Standard? (2026 Explainer)" — https://www.agensi.io/learn/agent-skills-open-standard
- "Agent Skills Overview - Agent Skills" — https://agentskills.io/home
- "Agent Skills Marketplace - Claude, Codex & ChatGPT Skills | SkillsMP" — https://skillsmp.com/
- "Agent Skills Open Standard Explained | Anthropic SKILL.md Specification..." — https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
- "Equipping agents for the real world with Agent Skills" — https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- "Agent Skills: Anthropic's Next Bid to Define AI Standards - The New Stack" — https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/
- "Anthropic Launches Skills Open Standard for Claude" — https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude
- "skills/skill-creator/SKILL.md at main · anthropics/skills" — https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md
- "Agent Skills – Codex | OpenAI Developers" — https://developers.openai.com/codex/skills
- "Unveiling Agent Skill: Anthropic's Open Standard..." — https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71

**Key Findings:**
- SKILL.md open standard: released by Anthropic December 18, 2025
- Within 48 hours: Microsoft integrated into VS Code, OpenAI added to ChatGPT and Codex CLI
- Within 90 days: 32 tools from competing companies adopted it (Google Gemini CLI, JetBrains Junie, AWS Kiro, Block's Goose, Cline, Windsurf, OpenCode)
- A skill folder contains: SKILL.md file (YAML frontmatter: name + description + instructions), optional supplementary files, executable scripts
- Cross-agent portability: a skill written for Claude Code works in Codex CLI when copied to the right directory
- Article authors: Barry Zhang, Keith Lazuka, Mahesh Murag (Anthropic)

---

## SEARCH BATCH 6: skills.sh / Vercel

### Query: "skills.sh Vercel agent skills directory leaderboard 2026"

**Results:**
- "Introducing skills, the open agent skills ecosystem - Vercel" — https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
- "The Agent Skills Directory" — https://skills.sh/
- "Agent Skills - Vercel Docs" — https://vercel.com/docs/agent-resources/skills
- "Skills.sh Review (2026): The Open Agent Skills Directory" — https://www.toolworthy.ai/tool/skills-sh
- "Agent Skills Marketplace: Skills.sh Guide (2026)" — https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/
- "GitHub - vercel-labs/skills: The open agent skills tool - npx skills" — https://github.com/vercel-labs/skills
- "skills/find-skills/SKILL.md at main · vercel-labs/skills" — https://github.com/vercel-labs/skills/blob/main/skills/find-skills/SKILL.md
- "find-skills by vercel-labs/skills" — https://skills.sh/vercel-labs/skills/find-skills
- "find-skills • skills • vercel-labs • Skills • Registry • Tessl" — https://tessl.io/registry/skills/github/vercel-labs/skills/find-skills
- "Vercel Introduces Skills.sh, an Open Ecosystem for Agent Commands - InfoQ" — https://www.infoq.com/news/2026/02/vercel-agent-skills/

**Key Findings:**
- Launched January 20, 2026
- 90,000+ skills tracked; 19 AI agents supported
- CLI: `npx skills add <owner>/<repo>`
- Top skills: find-skills (579,000+ installs), vercel-react-best-practices (216,000+ installs)
- Leaderboard: real-time install telemetry; all-time and 24-hour trending views
- Open standard: skills follow Anthropic's SKILL.md spec; cross-tool portable

---

## SEARCH BATCH 7: Claude Managed Agents

### Query: "Claude Managed Agents API announcement April 2026"

**Results:**
- "Claude Managed Agents overview - Claude API Docs" — https://platform.claude.com/docs/en/managed-agents/overview
- "Claude Managed Agents: What It Actually Offers..." — https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14
- "Claude Managed Agents: get to production 10x faster | Claude" — https://claude.com/blog/claude-managed-agents
- "What Is Claude Managed Agents? A Developer Guide" — https://www.verdent.ai/guides/what-is-claude-managed-agents
- "Claude Platform - Release Notes" — https://platform.claude.com/docs/en/release-notes/overview
- "Anthropic rolls out Claude Managed Agents | InfoWorld" — https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html
- "Claude Managed Agents Pricing: Costs and Limits (2026)" — https://www.verdent.ai/guides/claude-managed-agents-pricing
- "Claude Managed Agents: What Just Launched | Claude AI Dev" — https://claudeai.dev/blog/claude-managed-agents-what-just-launched/
- "Claude Managed Agents Review (2026): Pricing & Setup Guide" — https://www.toolworthy.ai/tool/claude-managed-agents
- "Claude Managed Agents Explained: $0.08/Hr AI Agents at Scale" — https://findskill.ai/blog/claude-managed-agents-explained/

**Key Findings:**
- Launch date: April 8, 2026
- Beta status, requires `managed-agents-2026-04-01` beta header
- Features: sandboxed code execution, checkpointing, credential management, scoped permissions, end-to-end tracing; built-in prompt caching and compaction
- Pricing: $0.08/session-hour + standard token costs; no flat fee, no per-agent license
- Multi-agent coordination and self-evaluation: still in "research preview"

---

## SEARCH BATCH 8: MCP Dev Summit, Community Discussion

### Query: "agent skills open standard MCP dev summit April 2026 community discussion"

**Results:**
- "MCP Dev Summit North America | LF Events" — https://events.linuxfoundation.org/mcp-dev-summit-north-america/
- "MCP Dev Summit 2026: AAIF Sets A Clear Direction..." — https://futurumgroup.com/insights/mcp-dev-summit-2026-aaif-sets-a-clear-direction-with-disciplined-guardrails/
- "Agentic AI Foundation Unveils MCP Dev Summit Schedule" — https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/
- "Skills Aren't the MCP Killer: Notes from the Best Talk at MCP Dev Summit" — https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/
- "AAIF's MCP Dev Summit: Gateways, gRPC, and Observability Signal Protocol Hardening - InfoQ" — https://www.infoq.com/news/2026/04/aaif-mcp-summit/
- "Agentic AI Foundation Unveils MCP Dev Summit North America 2026 Schedule" — https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule
- "Skills Over MCP Interest Group - April 14th 2026 Office Hours Notes" — https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585
- "MCP Dev Summit: Standardizing AI Agents, Starting with MCP - SD Times" — https://sdtimes.com/ai/mcp-dev-summit-standardizing-ai-agents-starting-with-mcp/
- "Agentic AI Foundation Unveils MCP Dev Summit North America 2026 Schedule" — https://finance.yahoo.com/news/agentic-ai-foundation-unveils-mcp-140000965.html
- "Model Context Protocol - Wikipedia" — https://en.wikipedia.org/wiki/Model_Context_Protocol

**Key Findings:**
- MCP Dev Summit North America: April 2-3, 2026, NYC; 1,200 attendees; 17 keynotes; 95+ sessions
- AAIF (Agentic AI Foundation) goal: define open standards for agentic AI systems
- Pedro Rodrigues (Supabase) session "Skills Are Not the MCP Killer": skills and MCP are complementary, not competing
- MCP = integration problem (N agents × M services); Skills = context saturation problem
- Pedro's live demo: MCP-only agent accidentally bypassed PostgreSQL Row-Level Security; adding a skill fixed the issue by directing agent to read security docs first
- Quote: "MCP is the pilot, skills are the co-pilot"
- April 14, 2026 GitHub Discussion #2585: "Skills Over MCP Interest Group Office Hours"
- Architectural decisions: skill discovery via index.json on startup; multi-file skills ship as archives; progressive disclosure without mandating filesystem
- Mintlify shipped custom skill file hosting via .well-known URI, exposes skills as MCP resources

---

## SEARCH BATCH 9: Lazy Loading, Context Management

### Query: "MCP tool search lazy loading context window agent skills 2026"

**Results:**
- "Efficient MCP Tool Loading" — https://ampcode.com/news/lazy-load-mcp-with-skills
- "Lazy Load: AI Agent Context Token Reduction for MCP Tools" — https://mcpmarket.com/server/lazy-load
- "Skills Over MCP Interest Group - April 14th 2026 Office Hours Notes" — https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585
- "Add mcp search tool, lazy mcp load, reduce mcp tool occupying a lot of context · Issue #9266 · openai/codex" — https://github.com/openai/codex/issues/9266
- "GitHub - voicetreelab/lazy-mcp: MCP proxy server with lazy loading support" — https://github.com/voicetreelab/lazy-mcp
- "Skills Aren't the MCP Killer: Notes from the Best Talk at MCP Dev Summit" — https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/
- "Claude Code MCP Tool Search: Save 95% Context" — https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search
- "What is MCP Tool Search? The Claude Code feature that fixes context pollution" — https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide
- "MCP, Skills, and Agents / Cra.mr" — https://cra.mr/mcp-skills-and-agents/
- "GitHub - PeterCha90/mcp-lazy-load: MCP tools eating your context window?" — https://github.com/PeterCha90/mcp-lazy-load

**Key Findings:**
- MCP Tool Search announced January 14, 2026 by Anthropic
- Mechanism: detects if MCP tool descriptions exceed 10K tokens; defers tools with defer_loading: true; injects a Tool Search tool instead of all definitions; loads 3-5 relevant tools (~3K tokens) per query on-demand
- Result: 85% token overhead reduction (Anthropic's figure); up to 95% in practice
- Now enabled by default; no opt-in required
- Open-source community lazy-loading tools: voicetreelab/lazy-mcp, PeterCha90/mcp-lazy-load
- OpenAI Codex tracking similar feature (GitHub Issue #9266)
- Skills also load lazily: agent reads description first, pulls full instructions only if relevant

---

## SEARCH BATCH 10: Desktop Extensions (DXT/MCPB)

### Query: "claude code desktop extensions DXT format one-click install 2026"

**Results:**
- "Claude Desktop Extensions (DXT)" — https://www.desktopextensions.com/
- "GitHub - milisp/awesome-claude-dxt: Awesome Claude Desktop Extensions" — https://github.com/milisp/awesome-claude-dxt
- "anthropics/dxt: Desktop Extensions: One-click local MCP..." — https://github.com/anthropics/dxt
- "One-click MCP server installation for Claude Desktop" — https://www.anthropic.com/engineering/desktop-extensions
- "GitHub - samihalawa/awesome-claude-dxt: 500+ extensions..." — https://github.com/samihalawa/awesome-claude-dxt
- "Desktop Extensions (DXT)" — https://mcp.so/dxt
- "GitHub - vinod-eng/ClaudeDesktopExtension: Desktop Extensions: One-click local MCP server installation" — https://github.com/vinod-eng/ClaudeDesktopExtension
- "Introducing Socket MCP for Claude Desktop - Socket" — https://socket.dev/blog/introducing-socket-mcp-for-claude-desktop
- "How to Deploy MCP Servers in Claude Desktop Using .dxt Extensions | Glama" — https://glama.ai/blog/2025-07-11-getting-started-with-mcp-desktop-extensions-dxt-in-claude-desktop
- "GitHub - modelcontextprotocol/mcpb: Desktop Extensions: One-click local MCP server installation" — https://github.com/modelcontextprotocol/mcpb

**Key Findings:**
- .dxt format: packaged local MCP servers for one-click install (similar to .crx or .vsix)
- Download .dxt, double-click or drag into Settings → Extensions
- Format evolution: .mcpb (MCP Bundle) is now the recommended format for new extensions; .dxt legacy supported
- 500+ extensions in awesome-claude-dxt community collection
- Zero-configuration deployment; handles all dependencies automatically
- Socket launched Socket MCP for Claude Desktop for security scanning

---

## SEARCH BATCH 11: Kestra MCP

### Query: "Kestra MCP plugin catalog AI agents April 2026"

**Results:**
- "Kestra MCP: A Live Plugin and Blueprint Catalog for AI Coding Agents" — https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints
- Additional Kestra pages: https://kestra.io/plugins/plugin-ai/tool, https://github.com/kestra-io/plugin-ai, https://kestra.io/1-0, https://kestra.io/docs/ai-tools/ai-agents, https://github.com/kestra-io/mcp-server-python

**Key Findings:**
- Remote HTTP MCP at https://api.kestra.io/v1/mcp
- 13 read-only tools: list_plugins, plugin_tasks, versions, plugin_versions, list_task_runners, list_triggers, list_storages, list_secret_managers, list_log_exporters, task_schema, blueprints, get_blueprint_flow, search
- Zero authentication; public endpoint; always current (mirrors live registry)
- Claude Code integration: `claude mcp add --transport http kestra https://api.kestra.io/v1/mcp`
- Published April 30, 2026; framework-agnostic (works with Codex CLI, Gemini CLI, OpenCode)

---

## SEARCH BATCH 12: HN and Community Discussion

### Query: Hacker News MCP servers Claude Code agent tools discussion 2026

**Results:**
- "What Hacker News Gets Right About AI Coding Agents in 2026" — https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- "CVE MCP Server Turns Claude Into a Fully Capable Security Analyst" — https://cybersecuritynews.com/cve-mcp-server-and-claude/
- "Code Mode: give agents an entire API in 1,000 tokens" (Cloudflare) — https://blog.cloudflare.com/code-mode-mcp/
- "The Claude Code Survival Guide for 2026: Skills, Agents & MCP Servers" — https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we
- "Best MCP Servers for Web Developers in 2026" — https://www.deployhq.com/blog/best-mcp-servers-for-web-developers
- "January 2026: AI Agents Take Over, Claude Code Workflows..." — https://codewithandrea.com/newsletter/january-2026/
- "5 MCP servers every Claude Code user should know in 2026" — https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1
- "Show HN: LangAlpha – what if Claude Code was built for Wall Street?" — https://news.ycombinator.com/item?id=47766370

**Key Findings:**
- HN discussion themes: workflows over demos, verification as bottleneck, skills over prompts, orchestration > raw autonomy
- Cloudflare "Code Mode": give agents an entire API in 1,000 tokens via MCP
- CVE MCP Server: 27 tools across 21 APIs, turns Claude into security analyst
- "January 2026: AI Agents Take Over" newsletter covers MCP servers, skills, sub-agents, hooks, multi-agent orchestration, and OpenCode
- LangAlpha HN thread: Claude Code adapted for Wall Street workflows

---

## WEBFETCH: Anthropic Engineering Blog — Agent Skills

**Source:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- Release: October 16, 2025 (article); open standard update December 18, 2025
- Skills = "organized folders of instructions, scripts, and resources that agents can discover and load dynamically"
- Progressive disclosure: SKILL.md YAML frontmatter → supplementary files → executable scripts
- Mirrors "an onboarding guide for a new hire"
- Supported: Claude.ai, Claude Code, Claude Agent SDK, Claude Developer Platform
- Authors: Barry Zhang, Keith Lazuka, Mahesh Murag

---

## WEBFETCH: Kestra MCP Blog (April 30, 2026)

**Source:** https://kestra.io/blogs/2026-04-30-kestra-mcp-plugins-blueprints
- Endpoint: https://api.kestra.io/v1/mcp (HTTP MCP, no auth)
- 13 tools (see Batch 11 above)
- Quote: "Connect it to your AI coding agent once; from that point, the agent can discover plugins, inspect task schemas, and fetch Blueprint YAML without ever leaving the conversation."
- Published April 30, 2026; works with all MCP-compatible clients

---

## WEBFETCH: Obot.ai — "Skills Aren't the MCP Killer"

**Source:** https://obot.ai/blog/skills-arent-the-mcp-killer-mcp-dev-summit/
- Speaker: Pedro Rodrigues (Supabase), MCP Dev Summit April 2-3, 2026
- Thesis: Skills and MCP solve different problems; the "killer" framing is wrong
- MCP = integration problem (N agents × M services); Skills = context saturation
- Analogy: "MCP is the pilot, skills are the co-pilot"
- Live demo: MCP-only agent bypassed PostgreSQL Row-Level Security, exposing all teams' data; skill directing agent to read security docs first fixed the issue
- Quote: "Agents are very lazy to go beyond their training data, and they need a push to search the web or find the right information."
- Key: Context (proper instructions), not capability, is the limiting factor

---

## WEBFETCH: Vercel skills.sh Launch

**Source:** https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
- Launch: January 20, 2026
- CLI: `npx skills add <owner>/<repo>`
- Directory: skills.sh with popularity leaderboard, real-time install telemetry
- 17+ agent platforms supported
- "a CLI for installing and managing skill packages for agents"

---

## WEBFETCH: GitHub Discussion #2585 — Skills Over MCP Office Hours (April 14, 2026)

**Source:** https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2585
- Host discovery: `index.json` on startup → skill metadata injected into context
- Tool bloat problem: servers with 40-50 tools need skills to narrow agent focus
- Quote (Pedro Rodrigues, Supabase): "Agents are very lazy into requesting more information about what they don't know."
- Script execution: multi-file skills ship as archives, not individual fetches
- Mintlify: quietly shipped .well-known URI skill hosting, exposes skills as MCP resources
- Metadata duplication (index.json ↔ frontmatter): automated via GitHub Action

---

## YOUTUBE VIDEOS FOUND

1. "The Ultimate Claude Code Guide | MCP, Skills & More" — https://www.youtube.com/watch?v=uogzSxOw4LU (3 weeks ago ≈ early April 2026)
2. "Claude Plugins & Skills Tutorial (All Updates Combined) | Ansh Mehra" — https://www.youtube.com/watch?v=6EFOT6hjvAU (February 2026)
3. "Meta Ads CLI + MCP: Complete Setup Guide (Run Facebook Ads from Claude)" — https://www.youtube.com/watch?v=mcT9f3JjYho (April 29, 2026)

---

## ADDITIONAL WEB SOURCES

- "Best Claude Code Skills and Plugins (2026 Guide) – RAXXO Studios" — https://raxxo.shop/blogs/lab/best-claude-code-skills-plugins-2026-guide
- "Cloudflare Code Mode: give agents an entire API in 1,000 tokens" — https://blog.cloudflare.com/code-mode-mcp/
- "MCP, Skills, and Agents / Cra.mr" — https://cra.mr/mcp-skills-and-agents/
- "Claude Code Skills & Agents: Build Custom Slash Commands" — https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865
- "Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks" — https://alexop.dev/posts/understanding-claude-code-full-stack/
- "The Best AI Agent Skills Marketplaces in 2026" — https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- "Claude Code Plugins vs Skills" — https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained
- "MCP Servers List 2026: Complete Directory" — https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory
- "Claude Managed Agents Explained" — https://findskill.ai/blog/claude-managed-agents-explained/
- "Futurum: MCP Dev Summit 2026 AAIF Report" — https://futurumgroup.com/insights/mcp-dev-summit-2026-aaif-sets-a-clear-direction-with-disciplined-guardrails/
- "InfoQ: AAIF MCP Summit Coverage" — https://www.infoq.com/news/2026/04/aaif-mcp-summit/
- "SD Times: MCP Dev Summit" — https://sdtimes.com/ai/mcp-dev-summit-standardizing-ai-agents-starting-with-mcp/
- "The New Stack: Agent Skills - Anthropic's Next Bid to Define AI Standards" — https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/
- "AI Business: Anthropic Launches Skills Open Standard" — https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude
- "InfoWorld: Anthropic Rolls Out Claude Managed Agents" — https://www.infoworld.com/article/4156852/anthropic-rolls-out-claude-managed-agents.html
- "Help Net Security: Claude Managed Agents" — https://www.helpnetsecurity.com/2026/04/09/claude-managed-agents-bring-execution-and-control-to-ai-agent-workflows/
- "DevOps.com: Claude Introduces Agent Skills" — https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/
- "Code With Andrea Newsletter: January 2026 AI Agents" — https://codewithandrea.com/newsletter/january-2026/
- "Microsoft .NET Blog: Extend coding agent with .NET Skills" — https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/
- "Paperclipped: Agent Skills Open Standard Interoperability Guide" — https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
- "Socket: Introducing Socket MCP for Claude Desktop" — https://socket.dev/blog/introducing-socket-mcp-for-claude-desktop
- "Glama: Getting Started with MCP Desktop Extensions (.dxt)" — https://glama.ai/blog/2025-07-11-getting-started-with-mcp-desktop-extensions-dxt-in-claude-desktop
- "Medium (lmpo): Unveiling Agent Skill: Anthropic's Open Standard" — https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71
- "Medium (unicodeveloper): Claude Managed Agents — Honest Pros and Cons" — https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14
- "Cyber Security News: CVE MCP Server" — https://cybersecuritynews.com/cve-mcp-server-and-claude/
- "Developers Digest: What HN Gets Right About AI Coding Agents" — https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- "Wikipedia: Model Context Protocol" — https://en.wikipedia.org/wiki/Model_Context_Protocol
- "Model Context Protocol Docs: Connect to local MCP servers" — https://modelcontextprotocol.io/docs/develop/connect-local-servers
- "Udemy: Claude Code 2026 Bootcamp" — https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/
- "Tessl Registry: find-skills by vercel-labs" — https://tessl.io/registry/skills/github/vercel-labs/skills/find-skills
- "Composio: YouTube MCP Integration" — https://composio.dev/toolkits/youtube/framework/claude-code
- "GitHub JCodesMore: youtube-mcp plugin" — https://github.com/JCodesMore/youtube-mcp
- "ampcode.com: Efficient MCP Tool Loading" — https://ampcode.com/news/lazy-load-mcp-with-skills
- "MCPMarket: Lazy Load Server" — https://mcpmarket.com/server/lazy-load
- "GitHub openai/codex Issue #9266: Add mcp search tool, lazy mcp load" — https://github.com/openai/codex/issues/9266
- "GitHub voicetreelab/lazy-mcp" — https://github.com/voicetreelab/lazy-mcp
- "GitHub PeterCha90/mcp-lazy-load" — https://github.com/PeterCha90/mcp-lazy-load
- "atcyrus.com: MCP Tool Search — context pollution guide" — https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide
- "claudefa.st: MCP Tool Search — Save 95% Context" — https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search
- "Anthropic Engineering: Desktop Extensions" — https://www.anthropic.com/engineering/desktop-extensions
- "mcp.so: Desktop Extensions (DXT)" — https://mcp.so/dxt
- "desktopextensions.com" — https://www.desktopextensions.com/
- "GitHub anthropics/dxt" — https://github.com/anthropics/dxt
- "GitHub milisp/awesome-claude-dxt" — https://github.com/milisp/awesome-claude-dxt
- "GitHub samihalawa/awesome-claude-dxt" — https://github.com/samihalawa/awesome-claude-dxt
- "GitHub modelcontextprotocol/mcpb" — https://github.com/modelcontextprotocol/mcpb
- "GitHub anthropics/skills: skill-creator/SKILL.md" — https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md
- "GitHub wshobson/agents: multi-agent orchestration" — https://github.com/wshobson/agents
- "GitHub FlorianBruniaux/claude-code-ultimate-guide: agent-teams.md" — https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md
- "GitHub quemsah/awesome-claude-plugins" — https://github.com/quemsah/awesome-claude-plugins
- "GitHub kestra-io/plugin-ai" — https://github.com/kestra-io/plugin-ai
- "GitHub kestra-io/mcp-server-python" — https://github.com/kestra-io/mcp-server-python
- "Kestra: AI Agent documentation" — https://kestra.io/docs/ai-tools/ai-agents
- "Kestra: 1.0 launch" — https://kestra.io/1-0
- "Kestra: AI Tools overview" — https://kestra.io/docs/ai-tools
- "SkillsMP.com" — https://skillsmp.com/
- "AgentSkillExchange.com" — https://agentskillexchange.com/
- "AgentSkills.io" — https://agentskills.io/home
- "ClaudeMarketplaces.com" — https://claudemarketplaces.com/
- "Agensi.io: Learn Best Marketplaces" — https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- "KDnuggets: Top 5 Agent Skill Marketplaces" — https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
- "Brightcoding: Claude Skills Marketplace Essential Plugin Hub" — https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers
- "LobeHub Skills" — https://lobehub.com/skills
- "VirtualUncle: Skills.sh Guide" — https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/
- "DevToolPicks: Claude Skills vs MCP vs Plugins" — https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026
- "Morphllm: Claude Code Skills vs MCP vs Plugins" — https://www.morphllm.com/claude-code-skills-mcp-plugins
- "Geeky Gadgets: Claude Code MCP vs Skills vs Hooks" — https://www.geeky-gadgets.com/claude-code-mcp-plugins-explained/
- "Mejba.me: Top 10 Claude Code Skills Plugins CLIs 2026" — https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026
- "Redwerk: 7 Best Claude Code Plugins 2026" — https://redwerk.com/blog/best-claude-code-plugins/
- "TurboDocx: Best Claude Code Plugins Skills MCP Servers" — https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers
- "Alexop.dev: Understanding Claude Code's Full Stack" — https://alexop.dev/posts/understanding-claude-code-full-stack/
- "DEV Community: Best Claude Code Skills Plugins 2026" — https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4
- "DEV Community: Claude Code Skills Agents Custom Slash Commands" — https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865
- "DEV Community: Claude Code Skills vs MCP Servers 2026" — https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k
- "Smart Webtech: Claude Code Workflows and Best Practices" — https://smart-webtech.com/blog/claude-code-workflows-and-best-practices/
- "Verdent: Claude Managed Agents Guide" — https://www.verdent.ai/guides/what-is-claude-managed-agents
- "Verdent: Claude Managed Agents Pricing" — https://www.verdent.ai/guides/claude-managed-agents-pricing
- "ClaudeAI.dev: Managed Agents Launch Post" — https://claudeai.dev/blog/claude-managed-agents-what-just-launched/
- "ToolWorthy: Claude Managed Agents Review" — https://www.toolworthy.ai/tool/claude-managed-agents
- "Anthropic Blog: Claude Managed Agents" — https://claude.com/blog/claude-managed-agents
- "Claude Platform API Docs: Managed Agents Overview" — https://platform.claude.com/docs/en/managed-agents/overview
- "Claude API Docs: Agent Skills Overview" — https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- "Claude Code Docs: Sub-agents" — https://code.claude.com/docs/en/sub-agents
- "Claude Code Docs: MCP" — https://code.claude.com/docs/en/mcp
- "Claude Support: Getting Started with Local MCP Servers" — https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop
- "Claude Release Notes" — https://platform.claude.com/docs/en/release-notes/overview
- "ModelContextProtocol.io: Connect to local MCP servers" — https://modelcontextprotocol.io/docs/develop/connect-local-servers
- "OpenAI Developers: Agent Skills – Codex" — https://developers.openai.com/codex/skills
- "Linux Foundation: MCP Dev Summit North America" — https://events.linuxfoundation.org/mcp-dev-summit-north-america/
- "Linux Foundation Press Release" — https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule
- "Yahoo Finance: MCP Dev Summit news" — https://finance.yahoo.com/news/agentic-ai-foundation-unveils-mcp-140000965.html
- "Futurum: MCP Dev Summit AAIF" — https://futurumgroup.com/insights/mcp-dev-summit-2026-aaif-sets-a-clear-direction-with-disciplined-guardrails/
- "InfoQ: AAIF MCP Summit" — https://www.infoq.com/news/2026/04/aaif-mcp-summit/
- "InfoQ: Vercel Agent Skills" — https://www.infoq.com/news/2026/02/vercel-agent-skills/
- "SDTimes: MCP Dev Summit" — https://sdtimes.com/ai/mcp-dev-summit-standardizing-ai-agents-starting-with-mcp/
- "ChatPRD: Claude AI Workflows" — https://www.chatprd.ai/how-i-ai/workflows/tool/claude
- "Toolworthy: skills.sh Review" — https://www.toolworthy.ai/tool/skills-sh
- "systemPrompt.io: Claude Code MCP Servers Extensions Guide" — https://systemprompt.io/guides/claude-code-mcp-servers-extensions
- "MCPPlayground: How to Set Up MCP in Claude Desktop" — https://mcpplaygroundonline.com/blog/how-to-setup-mcp-claude-desktop
- "ToolRadar: MCP Servers in Claude Desktop" — https://toolradar.com/blog/claude-desktop-mcp-server-setup
- "TokenMix: MCP Servers List 2026" — https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory
- "DeployHQ: Best MCP Servers for Web Developers" — https://www.deployhq.com/blog/best-mcp-servers-for-web-developers
- "Gist: 5 MCP servers every Claude Code user should know" — https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1
- "Hacker News: LangAlpha Show HN" — https://news.ycombinator.com/item?id=47766370
- "Deepwiki: microsoft/agent-skills Plugins" — https://deepwiki.com/microsoft/agent-skills/4-plugins
- "MCP Servers ClaudeFA.st Setup" — https://claudefa.st/blog/tools/mcp-extensions/best-addons
- "ClaudeFA.st Cursor MCP Setup" — https://claudefa.st/blog/tools/mcp-extensions/cursor-mcp-setup
- "Chris Ayers: Agent Skills Plugins and Marketplace" — https://chris-ayers.com/posts/agent-skills-plugins-marketplace/
- "Paperclipped: Agent Skills Open Standard" — https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
- "AiBusiness: Anthropic Launches Skills Open Standard" — https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude
- "Raxxo Shop Blog: Best Claude Code Skills Plugins 2026" — https://raxxo.shop/blogs/lab/best-claude-code-skills-plugins-2026-guide
- "LinkedIn: Claude Code Survival Guide 2026" — https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we
- "Codewithandrea Newsletter: January 2026" — https://codewithandrea.com/newsletter/january-2026/
- "Findskill.ai: Claude Managed Agents Explained" — https://findskill.ai/blog/claude-managed-agents-explained/
- "Verdent: What Is Claude Managed Agents" — https://www.verdent.ai/guides/what-is-claude-managed-agents
- "Medium @lmpo: Agent Skill Anthropic Open Standard" — https://medium.com/@lmpo/unveiling-agent-skill-anthropics-open-standard-for-enhancing-ai-agents-1b47bd067d71
- "Medium @unicodeveloper: Claude Managed Agents" — https://medium.com/@unicodeveloper/claude-managed-agents-what-it-actually-offers-the-honest-pros-and-cons-and-how-to-run-agents-52369e5cff14
- "Anthropic Engineering: Desktop Extensions" — https://www.anthropic.com/engineering/desktop-extensions
