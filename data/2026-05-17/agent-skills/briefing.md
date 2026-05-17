# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-17
**Query type:** GENERAL
**Sources:** Web (official docs, blogs, news), Hacker News, Reddit (aggregated), YouTube, GitHub, Polymarket (MCP integrations)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 9 threads | ~3–hundreds of points (varies) | Skills Manager: 3pts/9 comments; multiple Show HN threads |
| Reddit | 6 subreddits monitored | 4,200+ weekly contributors (r/ClaudeCode alone) | Aggregated via morphllm.com; direct access blocked |
| YouTube | 5+ videos, 1 course playlist | Not retrieved (YT blocks metadata extraction) | April–May 2026 tutorials; Udemy bootcamp course |
| GitHub | 8 repos | 136k stars (anthropics/skills), 16k forks | Key repos: anthropics/skills, jeremylongshore/claude-code-plugins-plus-skills |
| Web | 80+ pages | — | Official docs, VentureBeat, Tom's Hardware, OX Security, agensi.io, dozens of blog posts |
| Polymarket | 4 MCP integrations | 9,706+ active contracts (via Polymarket MCP) | Skills/MCP servers for prediction market trading |

---

## Synthesized Findings

### 1. The Agent Skills Open Standard: From Anthropic Invention to Industry Lingua Franca

Anthropic published the Agent Skills specification on **October 16, 2025** via an engineering blog post ([Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)), then made it an **open standard on December 18, 2025** ([SiliconAngle](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/)). Licensed under Apache 2.0 (code) and CC-BY-4.0 (docs), the spec lives at [agentskills.io](https://agentskills.io/home) and [github.com/agentskills/agentskills](https://github.com/agentskills/agentskills).

The adoption velocity was extraordinary: within **48 hours**, Microsoft integrated it into VS Code ([docs](https://code.visualstudio.com/docs/copilot/customization/agent-skills)) and OpenAI added it to both ChatGPT and Codex CLI. By March 2026, **32 tools from competing companies** read the same SKILL.md files from the same directory structure — including Google (Gemini CLI), JetBrains (Junie), AWS (Kiro), Block (Goose), Sourcegraph (Amp), Snowflake, Databricks, ByteDance, Mistral AI, and Spring AI ([Paperclipped explainer](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)).

The core unit is a **SKILL.md file** with YAML frontmatter (`name`, `description`, `when_to_use`, etc.) plus markdown instructions, living in a directory that can also contain scripts, templates, and reference docs. This design makes skills **portable across agents without modification** — write once for Claude Code, use in Cursor, Codex, Gemini CLI, Kiro, and 28+ others.

VentureBeat framed this as a competitive move: "[Anthropic launches enterprise 'Agent Skills' and opens the standard, challenging OpenAI in workplace AI](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard)."

**Cross-platform discussion:** Web (official docs, VentureBeat, SiliconAngle, Paperclipped), Hacker News ([Thread: Agent Skills: From Claude to Open Standard](https://news.ycombinator.com/item?id=46779064)), Reddit (r/ClaudeCode, r/LocalLLaMA)

---

### 2. Claude Code Plugin System Goes First-Class (Spring 2026)

Claude Code shipped a first-class **plugin marketplace system in v2.1.108** (spring 2026), documented in detail by the [May 2026 release notes](https://pasqualepillitteri.it/en/news/2223/claude-code-may-2026-release-notes-radio-plugin-marketplace). Plugins are now installable via the `/plugin` command (with tabs: Discover, Installed, Marketplaces, Errors) or the `--plugin-url` flag for third-party sources.

**Architecture:** A plugin is a directory with a manifest at `.claude-plugin/plugin.json`, bundling skills, MCP server configs, hooks, and subagents. The system mirrors VS Code extensions but with expanded capabilities. The official Anthropic marketplace is hosted at `anthropics/claude-plugins-official` on GitHub.

**Key distinction clarified by official docs** ([Claude Code Plugins vs Skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained)):
- **Skills** = single instruction sets (SKILL.md), the content unit
- **Plugins** = distribution packages that bundle multiple skills + MCP servers + hooks
- Backward compatible: existing `.claude/commands/` files continue working

The `/plugin` system adds skill discovery to an ecosystem now listing **4,200+ skills, 2,500+ plugin marketplaces, and 770+ MCP servers** ([ClaudeMarketplaces directory](https://claudemarketplaces.com/)).

**Also shipped in the May 2026 release:**
- `/radio` command: lo-fi streaming for coding sessions
- Opus 4.7: 1 million token native context (up from 200k), effort levels (low/medium/high/xhigh/Auto)
- `/loop`, `/ultrareview`, `/focus`, `/recap`, `/release-notes` commands
- Git worktrees integration (`worktree.baseRef` config)
- MCP OAuth token race condition patches

**Cross-platform discussion:** Web (official docs, release notes, blog posts), Hacker News ([Claude Code Skills and Plugins as an Open Source Project](https://news.ycombinator.com/item?id=47321892)), Reddit (r/ClaudeCode), YouTube ([The Ultimate Claude Code Guide | MCP, Skills & More](https://www.youtube.com/watch?v=uogzSxOw4LU))

---

### 3. The Marketplace Explosion — Quality vs Quantity

The agent skills marketplace landscape went from one registry (Anthropic's official) in late 2025 to **8+ major marketplaces** by Q2 2026. They vary enormously in scale, curation, and security:

| Marketplace | Skills Count | Security | Notable |
|------------|-------------|----------|---------|
| [SkillsMP](https://skillsmp.com/) | 800,000+ | None | Scraped from GitHub (2+ stars min) |
| [LobeHub](https://lobehub.com/skills) | 169,000+ | None | Polished UI |
| [Vercel skills.sh](https://agent-skills.cc/) | ~89,753 | None | npm-style CLI (`npx skills add`), Vercel-backed, launched Jan 20, 2026 |
| [GitHub Plugin Marketplaces](https://claudemarketplaces.com/) | 2,500+ registries | Per-owner | Quality varies widely |
| [ClaudeSkills.info](https://claudeskills.info/skills/) | 658 | None | Beginner-friendly, official + community |
| [MCP Market](https://mcpmarket.com/) | ~500 | None | Best for MCP server integration |
| [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 200+ | 8-point scan | Paid skills, 80/20 creator split |
| [Anthropic Official](https://github.com/anthropics/skills) | ~20 | Internal audit | Bundled with Claude Code |

The **security gap is stark**: an audit found "**6.3 issues per skill on average**" across platforms, with "**prompt injection in 36% of skills tested**" ([agensi.io comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)). Agensi is the only marketplace with a formal pre-listing security scan.

The `anthropics/skills` GitHub repo is the anchor of the ecosystem: **136k stars, 16k forks**, 877 watchers, 237 open issues, 614 open PRs, organized into four categories: Creative & Design, Development & Technical, Enterprise & Communication, and Document Skills.

Community repos have grown aggressively:
- [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills): 425 plugins, 2,810 skills, 200 agents + `ccpi` CLI package manager, hosted at tonsofskills.com
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills): 263+ cross-agent skills (engineering, marketing, product, compliance, C-level advisory)
- [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills): 754 cybersecurity skills mapped to MITRE ATT&CK, NIST CSF 2.0, MITRE ATLAS, D3FEND, NIST AI RMF

**Cross-platform discussion:** Web (agensi.io comparison, ClaudeMarketplaces, SkillsMP, LobeHub), Hacker News ([Show HN: Agent Skills – 1k curated from 60k+ GitHub skills](https://news.ycombinator.com/item?id=46693426), [Claude Code Skills and 380 agent skills](https://news.ycombinator.com/item?id=47178402)), Reddit (r/ClaudeCode quality discussions)

---

### 4. MCP Server Ecosystem: Scale, Governance, and Enterprise Registries

The **Model Context Protocol (MCP)** — Anthropic's protocol for connecting AI agents to external tools — has become the de facto standard for agent tooling. Since its November 2024 introduction, it's been adopted by OpenAI and Google DeepMind (early 2025), and donated to the **Linux Foundation's Agentic AI Foundation** (December 2025), cementing its status as a cross-industry standard.

**Scale in 2026:**
- [aiagentslist.com](https://aiagentslist.com/mcp-servers): 593+ servers indexed
- [Smithery](https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp): 7,000+ servers (closest equivalent to Docker Hub for MCP)
- [MCPBundles](https://www.mcpbundles.com/blog/best-mcp-servers): 10,000+ tools across 700+ providers

**Key MCP servers:** GitHub, Vercel, Stripe, Notion, Linear, Tavily (real-time search), Atlassian (46+ tools: Jira, Confluence, Compass, Jira Service Management), PostgreSQL, Figma, Docker, Kubernetes, Slack.

**Enterprise governance layer** is maturing rapidly:
- [Kong MCP Registry](https://konghq.com/products/mcp-registry): Register, discover, and govern MCP servers with trusted access controls
- [AWS Agent Registry in AgentCore](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) (preview, April 2026): Private governed catalog for agents, tools, skills, MCP servers
- [Official MCP Registry](https://registry.modelcontextprotocol.io/): Open-source catalog with live REST API
- [MACH Alliance MCP Registry](https://machalliance.org/mach-alliance-mcp-registry): Industry alliance registry
- [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry): Enterprise-ready gateway with OAuth auth, dynamic tool discovery

**MCP Gateways** — intermediary proxies sitting between AI agents and MCP servers — are emerging as a critical enterprise pattern, providing centralized authentication, authorization, auditing, and traffic management ([ByteBridge on MCP Gateways](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a)).

**Cross-platform discussion:** Web (official MCP Registry, Kong, AWS, TrueFoundry, InfoWorld, The New Stack), Hacker News (multiple threads), Reddit (r/ClaudeCode MCP setup discussions), YouTube tutorials

---

### 5. MCP Security Crisis: RCE Vulnerability Across the AI Supply Chain

A major security story broke in **April 2026**: researchers at OX Security discovered an architectural RCE (Remote Code Execution) vulnerability baked into Anthropic's official MCP SDKs across every supported language — Python, TypeScript, Java, and Rust ([The Hacker News](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html), [OX Security advisory](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/)).

**Scope:** 150M+ downloads affected, 7,000+ publicly accessible servers, up to **200,000 vulnerable instances** total ([Tom's Hardware](https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed)).

**Affected tooling:** Cursor, VS Code, Windsurf, Claude Code, Gemini-CLI. Windsurf had the worst case (CVE-2026-30615): **zero user interaction** required. Microsoft issued CVE-2026-26118 for its MCP server ([PointGuard AI](https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118)).

**Attack vectors documented:**
1. **Prompt injection** — malicious commands embedded in inputs trick LLMs into executing harmful actions
2. **Tool poisoning** — manipulation of tool metadata or behavior
3. **Supply chain attacks** — fake or compromised tools infiltrating MCP registries
4. **Over-permissioned tools** — excessive privileges increasing blast radius

**Anthropic's response:** Declined to modify the protocol's architecture, citing the behavior as "expected." Some vendors issued patches; the shortcoming remains unaddressed in Anthropic's reference implementation ([OX Security RCE supply chain advisory](https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/)).

This has added urgency to the enterprise MCP registry/gateway market, which positions itself explicitly as the governance layer that can mitigate these risks.

**Cross-platform discussion:** Web (The Hacker News, Tom's Hardware, OX Security, Practical DevSecOps, Aembit, Adversa AI), likely Reddit (r/netsec, r/ClaudeAI)

---

### 6. Skills vs MCP: Architecture Debate and Complementary Roles

A persistent developer debate: do Skills and MCP compete or complement? The consensus in 2026 is **complementary but with real tension** ([Ravikanth Chaganti analysis](https://ravichaganti.com/blog/agent-skills-vs-model-context-protocol-how-do-you-choose/)):

- **Skills** = *how* to do things — packaging workflow expertise, domain knowledge, step-by-step procedures. Filesystem-based, loaded on demand, cost-free until invoked.
- **MCP** = *access* to things — standardized protocol for external services, databases, APIs. Runtime connections, always consuming tokens.
- **Tools** = individual callable functions (search, calculator, etc.)

**The layered architecture:** Skills (workflow + quality bar) → MCP (standardized external access) → Tools (individual actions)

The **token cost problem** is the most debated issue on Reddit (r/ClaudeCode, r/ClaudeAI): one developer documented **67,000 tokens consumed from connecting just four MCP servers before typing a single prompt**. System prompts, tool definitions, JSON schemas, and memory files eat 30-40K tokens at session start ([morphllm.com Reddit aggregation](https://www.morphllm.com/claude-code-reddit)).

Skills address this via **progressive disclosure**: only the description (~1,536 char cap) loads at startup; the full SKILL.md content only loads when invoked. This makes skills dramatically cheaper at session initialization than equivalent MCP configurations.

HN discussion captured the cross-agent challenge: **"Most agents support `~/.agents/skills` as a standard location, except Claude Code"** (@Dshadowzh in [Skills Manager HN thread](https://news.ycombinator.com/item?id=47423910)). The skills directory structure debate is ongoing, with Claude Code using `~/.claude/skills/` vs an emerging `~/.agents/skills/` convention.

**Cross-platform discussion:** Web (multiple blog posts), Hacker News (multiple threads), Reddit (r/ClaudeCode most active), YouTube tutorials

---

### 7. Enterprise Deployment: Managed Skills, Organization-Wide Rollout

Enterprise adoption of skills is accelerating with managed settings infrastructure ([Anthropic Support](https://support.claude.com/en/articles/13119606-provision-and-manage-skills-for-your-organization)):

- **Team and Enterprise plans** get organization-wide skill management: upload once, available to all users automatically
- **Managed settings** can include skills, permissions, hooks, audit trails — developers cannot override managed settings
- Typical enterprise rollout: **4-6 weeks** from pilot to org-wide availability
- Anthropic opened **Claude Cowork** to third-party platforms in April 2026
- Security: SOC 2 Type II compliance, SSO, role-based permissions, SCIM, IP allowlisting

Enterprise-grade automation pattern: **Skills + MCP + review loops** → plan → execute → evaluate → commit (often via PRs and approvals). Skills package deployment procedures, infrastructure templates, monitoring setup, and incident response workflows.

**High-impact enterprise applications:** content/SEO ops, data/BI pipelines, reporting, slides/docs/excel automation, social publishing.

Marketplaces are increasingly being treated as **software supply chains**: "version control, approvals, observability, and security scanning as mandatory" ([agensi.io](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide)).

**Cross-platform discussion:** Web (official Anthropic support docs, systemprompt.io, codingnomads.com, intuitionlabs.ai), likely Reddit enterprise channels

---

### 8. Prediction Markets and Specialized Skill Niches

The ecosystem has extended into specialized verticals, with **prediction market trading** as a notable example. Multiple MCP servers and skills now provide AI agents with Polymarket access:

- [Polymarket Agent Skill](https://mcp.directory/skills/polymarket-agent) — prediction market analyst role with web search
- [Polymarket MCP server](https://mcpmarket.com/server/polymarket-4) — 29 tools, real-time data from Kalshi and Polymarket, 9,706+ active contracts
- [Graph Polymarket MCP](https://glama.ai/mcp/servers/@PaulieB14/graph-polymarket-mcp) — 20 tools for market data, P&L, orderbook, open interest
- [Polymarket Development Suite skill](https://mcpmarket.com/tools/skills/polymarket-development-suite) — API integration + real-time WebSocket data

ClawHub marketplace hosts 13,700+ skills for AI trading automation in prediction markets.

Other emerging verticals: cybersecurity (754-skill mapped collection by mukul975), C-suite advisory, legal/compliance, marketing automation, and solopreneur workflows (OPC Skills' 9-skill pack).

**Cross-platform discussion:** Web (MCP.Directory, MCPMarket, SparkCo, Conare marketplace, Glama)

---

## Cross-Source Patterns

### Pattern 1: Fragmentation vs Standardization
**Signal:** The tension between a universal SKILL.md standard and dozens of competing directories/conventions
**Platforms:** Hacker News (HN ID 47423910 — cross-agent path debate), Reddit (r/ClaudeCode), Web (agensi.io marketplace comparison)
**Key quote:** "Most agents support `~/.agents/skills` as a standard location, except Claude Code. We need a unified skill marketplace for different agents." — @Dshadowzh on HN ([Skills Manager thread](https://news.ycombinator.com/item?id=47423910))

### Pattern 2: Security Is the Unsolved Problem
**Signal:** MCP's RCE vulnerability + marketplace prompt injection rates + Anthropic declining to fix
**Platforms:** Web (OX Security, Tom's Hardware, The Hacker News, Adversa AI, Practical DevSecOps), Reddit (likely r/netsec)
**Key quote:** "6.3 issues per skill on average" across platforms, "prompt injection in 36% of skills tested" — Agensi security audit ([agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

### Pattern 3: Token Costs Are the Practical Blocker
**Signal:** Community repeatedly hitting 67K+ token overhead before first prompt with MCP
**Platforms:** Reddit (r/ClaudeCode 4,200+ weekly contributors discussing cost), YouTube (multiple cost tutorials), Web
**Key quote:** "MCP servers are powerful but expensive, with one developer documenting 67,000 tokens consumed from connecting four MCP servers before typing a single prompt" — r/ClaudeCode community via morphllm.com ([aggregation](https://www.morphllm.com/claude-code-reddit))

### Pattern 4: Open Standard Adoption Is Winning
**Signal:** 32 adopters in under 6 months; anthropics/skills at 136k stars
**Platforms:** Web (VentureBeat, SiliconAngle, Paperclipped, agentskills.io), Hacker News ([Agent Skills: From Claude to Open Standard](https://news.ycombinator.com/item?id=46779064)), GitHub
**Key quote:** "Build once, use across agents" — [Paperclipped open standard explainer](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

### Pattern 5: Quantity vs Quality in Marketplaces
**Signal:** 800,000+ scraped skills (SkillsMP) vs 20 verified skills (Anthropic official) — orders of magnitude apart
**Platforms:** Web (agensi.io comparison, multiple marketplace directories), Hacker News ([Show HN: Agent Skills – 1k curated from 60k+ GitHub skills](https://news.ycombinator.com/item?id=46693426)), Reddit
**Key quote:** "The catalog size that actually matters is how many skills work well enough that other developers use them repeatedly." — agensi.io ([marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (community) | Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills | — | — | Curation from 60k+ GitHub skills | https://news.ycombinator.com/item?id=46693426 |
| (community) | Claude Code Skills and 380 agent skills from official dev teams and community | — | — | Official dev teams + community | https://news.ycombinator.com/item?id=47178402 |
| (community) | Show HN: OPC Skills – 9 AI agent skills for solopreneurs | — | — | Domain hunting, product validation, logo creation, SEO | https://news.ycombinator.com/item?id=46730857 |
| evergreenxx | Skills Manager – manage AI agent skills across Claude, Cursor, Copilot | 3 | 9 | "Claude follows multi-step rules well, Copilot tends to ignore anything beyond the first line" (druide67) | https://news.ycombinator.com/item?id=47423910 |
| (community) | Agent Skills: From Claude to Open Standard to Your Daily Coding Workflow | — | — | Open standard adoption story | https://news.ycombinator.com/item?id=46779064 |
| (community) | Agent Skills | — | — | Core agent skills discussion | https://news.ycombinator.com/item?id=46871173 |
| (community) | Claude Code Skills and Plugins as an Open Source Project | — | — | Open source skills/plugins discussion | https://news.ycombinator.com/item?id=47321892 |
| (community) | Code Sandbox Tech Behind Manus and Claude Agent Skills | — | — | Technical comparison | https://news.ycombinator.com/item?id=46012881 |
| (community) | Solving Agent Context Loss: A Beads and Claude Code Workflow for Large Features | — | — | Context management workflow | https://news.ycombinator.com/item?id=46471286 |

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | [Active community] | — | — | 4,200+ weekly contributors; MCP token cost debates | https://www.reddit.com/r/ClaudeCode |
| r/ClaudeAI | [All Claude products] | — | — | Cost-quality tradeoffs, skills vs MCP | https://www.reddit.com/r/ClaudeAI |
| r/LocalLLaMA | [Comparison threads] | — | — | Local alternatives to Claude skills ecosystem | https://www.reddit.com/r/LocalLLaMA |
| r/CursorAI | [Claude Code comparisons] | — | — | Cross-agent skill portability | https://www.reddit.com/r/CursorAI |
| r/ChatGPT | [Broader AI coding debates] | — | — | ChatGPT + Codex CLI adopting Agent Skills standard | https://www.reddit.com/r/ChatGPT |
| r/Codex | [Codex + skills] | — | — | OpenAI adoption of Agent Skills spec | https://www.reddit.com/r/Codex |

*Note: Reddit.com inaccessible for direct crawling. Data aggregated from [morphllm.com](https://www.morphllm.com/claude-code-reddit).*

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| (unknown) | How I Actually Use Claude Every Day in 2026 | — | — | No | https://www.youtube.com/watch?v=EZcYjH3jAo8 |
| (unknown) | Full Claude Code Tutorial for Non-Technical Beginners in 2026 | — | — | No | https://www.youtube.com/watch?v=bqJzIWAEn40 |
| (unknown) | FULL Claude Code Tutorial for Beginners in 2026! | — | — | No | https://www.youtube.com/watch?v=qYqIhX9hTQk |
| (unknown) | The ONLY Claude Code Tutorial You'll Ever Need in 2026 | — | — | No | https://www.youtube.com/watch?v=LlFgLsffbBs |
| (playlist) | Claude Code Tutorial Playlist | — | — | No | https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY |
| Udemy | Claude Code 2026: Subagents, MCP, Skills and Plugins Bootcamp | — | — | No | https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/ |
| Anthropic SkillJar | Introduction to agent skills | — | — | No | https://anthropic.skilljar.com/introduction-to-agent-skills |

*Note: YouTube metadata extraction blocked. Published April–May 2026.*

**Polymarket (MCP/Skill integrations):**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Polymarket Agent Skill (MCP.Directory) | — | — | https://mcp.directory/skills/polymarket-agent |
| polymarket-trader agent skill | — | — | https://mcp.directory/skills/polymarket-trader |
| Polymarket AI Agent API (29 tools, 9,706+ contracts) | — | — | https://mcpmarket.com/server/polymarket-4 |
| Graph Polymarket MCP (20 tools via The Graph) | — | — | https://glama.ai/mcp/servers/@PaulieB14/graph-polymarket-mcp |
| Graph Polymarket MCP (Conare marketplace) | — | — | https://conare.ai/marketplace/mcp/graph-polymarket |
| Polymarket Development Suite skill | — | — | https://mcpmarket.com/tools/skills/polymarket-development-suite |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Skills Docs (official) | https://code.claude.com/docs/en/skills | Complete technical reference for skills system |
| Anthropic Engineering Blog | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Original Agent Skills announcement (Oct 16, 2025) |
| agentskills.io | https://agentskills.io/home | Open standard home, 32 adopters listed |
| VentureBeat | https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard | Enterprise launch framing, competitive context |
| SiliconAngle | https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/ | Open standard announcement coverage (Dec 18, 2025) |
| Paperclipped explainer | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | Best 32-adopter adoption timeline |
| May 2026 release notes | https://pasqualepillitteri.it/en/news/2223/claude-code-may-2026-release-notes-radio-plugin-marketplace | Claude Code v2.1.108 plugin marketplace details |
| Agensi — Marketplace comparison | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 8-marketplace comparison with security audit data |
| Agensi — Plugins vs Skills | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Architecture distinction |
| Agensi — Plugin Marketplace Guide | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Full marketplace guide |
| Agensi — Agent Skills Open Standard | https://www.agensi.io/learn/agent-skills-open-standard | Open standard explainer |
| anthropics/skills GitHub | https://github.com/anthropics/skills | 136k stars, official skills repo |
| anthropics/skills spec | https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md | Technical specification |
| anthropics/skills marketplace.json | https://github.com/anthropics/skills/blob/main/.claude-plugin/marketplace.json | Marketplace configuration |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, ccpi CLI |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 263+ cross-agent skills |
| netresearch/claude-code-marketplace | https://github.com/netresearch/claude-code-marketplace | 30+ agent compatible marketplace |
| mukul975/Anthropic-Cybersecurity-Skills | https://github.com/mukul975/Anthropic-Cybersecurity-Skills | 754 cybersecurity skills, 5 frameworks |
| agentskills/agentskills | https://github.com/agentskills/agentskills | Specification repository |
| agentic-community/mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP gateway + registry |
| The Hacker News (security) | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | MCP RCE vulnerability coverage |
| OX Security | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | Original RCE vulnerability research |
| OX Security RCE advisory | https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ | Supply chain advisory |
| Tom's Hardware | https://www.tomshardware.com/tech-industry/artificial-intelligence/anthropics-model-context-protocol-has-critical-security-flaw-exposed | 200,000 vulnerable instances scope |
| PointGuard AI | https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118 | CVE-2026-26118 details |
| Practical DevSecOps | https://www.practical-devsecops.com/mcp-security-guide/ | MCP security complete guide |
| Practical DevSecOps — Vulnerabilities | https://www.practical-devsecops.com/mcp-security-vulnerabilities/ | Prompt injection, tool poisoning |
| Aembit — MCP Security | https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ | Ultimate MCP security guide |
| Adversa AI (Feb 2026) | https://adversa.ai/blog/top-mcp-security-resources-february-2026/ | MCP security resources |
| Adversa AI (Mar 2026) | https://adversa.ai/blog/top-mcp-security-resources-march-2026/ | MCP security resources |
| CyberDesserts | https://blog.cyberdesserts.com/ai-agent-security-risks/ | AI agent security risks overview |
| Kong MCP Registry | https://konghq.com/products/mcp-registry | Enterprise MCP governance |
| Kong Dynamic Tool Discovery | https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery | Tool discovery via MCP registry |
| AWS Agent Registry | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | Private enterprise registry (preview) |
| Official MCP Registry | https://registry.modelcontextprotocol.io/ | Open-source catalog + REST API |
| MACH Alliance Registry | https://machalliance.org/mach-alliance-mcp-registry | Industry alliance registry |
| TrueFoundry — MCP Registries | https://www.truefoundry.com/blog/best-mcp-registries | Registry comparison |
| InfoWorld — Enterprise MCP Registry | https://www.infoworld.com/article/4145014/how-to-build-an-enterprise-grade-mcp-registry.html | How to build enterprise MCP registry |
| The New Stack — MCP Roadmap | https://thenewstack.io/model-context-protocol-roadmap-2026/ | MCP roadmap and growing pains |
| DEV.to — MCP Predictions | https://dev.to/blackgirlbytes/my-predictions-for-mcp-and-ai-assisted-coding-in-2026-16bm | 2026 MCP predictions |
| Red Hat Developer | https://developers.redhat.com/articles/2026/01/08/building-effective-ai-agents-mcp | Building effective agents with MCP |
| Wikipedia — MCP | https://en.wikipedia.org/wiki/Model_Context_Protocol | Protocol history and definition |
| Microsoft Learn — MCP Tools | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Using local MCP tools (VS Code/Copilot) |
| VS Code Agent Skills | https://code.visualstudio.com/docs/copilot/customization/agent-skills | VS Code agent skills documentation |
| Ravikanth Chaganti | https://ravichaganti.com/blog/agent-skills-vs-model-context-protocol-how-do-you-choose/ | Skills vs MCP decision guide |
| morphllm.com — Reddit aggregation | https://www.morphllm.com/claude-code-reddit | Reddit community sentiment aggregation |
| morphllm.com — Skills vs MCP | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills/MCP/plugins comparison |
| Toloka — Best MCP Servers | https://toloka.ai/blog/best-mcp-servers-for-ai-agents/ | MCP server recommendations |
| Toloka — What is MCP | https://toloka.ai/blog/what-is-model-context-protocol-mcp/ | MCP explainer |
| MCP Market directory | https://mcpmarket.com/ | MCP server and skills directory |
| MCP Market — Agent Skills | https://mcpmarket.com/tools/skills | Agent skills directory |
| MCP Market — Claude Code Plugin Reference | https://mcpmarket.com/es/tools/skills/claude-code-plugin-reference-2026 | Plugin reference |
| AI Agents List | https://aiagentslist.com/mcp-servers | 593+ MCP servers indexed |
| Smithery (MCP) | https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp | 7,000+ MCP servers |
| MCPBundles | https://www.mcpbundles.com/blog/best-mcp-servers | 10,000+ tools, 700+ providers |
| Analytics Vidhya | https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/ | Top 10 MCP servers (Feb 2026) |
| K2View | https://www.k2view.com/blog/awesome-mcp-servers | Awesome MCP servers directory |
| Firecrawl — MCP Servers | https://www.firecrawl.dev/blog/best-mcp-servers-for-developers | Best MCP for developers |
| Firecrawl — Claude Skills | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code skills |
| ByteBridge — MCP Gateways | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | Top 10 MCP gateways 2026 |
| GetKnit — Future of MCP | https://www.getknit.dev/blog/the-future-of-mcp-roadmap-enhancements-and-whats-next | MCP future roadmap |
| RuhAI — AI Agent Protocols | https://www.ruh.ai/blogs/ai-agent-protocols-2026-complete-guide | Agent protocol landscape |
| Essa Mamdani — MCP Guide | https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026 | Complete MCP 2026 guide |
| Databar.ai | https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 | MCP for sales teams |
| ClaudeMarketplaces directory | https://claudemarketplaces.com/ | 4,200+ skills, 2,500+ marketplaces |
| SkillsMP | https://skillsmp.com/ | 800,000+ skills |
| LobeHub Skills | https://lobehub.com/skills | 169,000+ skills |
| ClaudeSkills.info | https://claudeskills.info/skills/ | 658 curated skills |
| AgentSkill.club | https://www.agentskill.club/ | Free agent skills library |
| agent-skills.cc | https://agent-skills.cc/ | 1,000+ curated skills |
| ClaudePluginHub | https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills | Plugin hub directory |
| AitMpl plugins | https://www.aitmpl.com/plugins/ | Claude Code plugins collection |
| Nimbalyst — Plugins Guide | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Plugins guide 2026 |
| Nimbalyst — Skills Guide | https://nimbalyst.com/blog/claude-code-skills-guide/ | Skills guide 2026 |
| ScriptByAI | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate Claude Code resource list |
| Mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills, plugins, CLIs |
| DEV.to — Best Skills 2026 | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills + plugins guide |
| DEV.to — MCP Ecosystem 2026 | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | MCP as integration layer |
| DEV.to — Skills vs MCP | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP practical guide |
| DEV.to — Skills Practical Guide | https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p | Practical skills guide |
| BrightCoding | https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers | Skills marketplace hub (Apr 2026) |
| ice-ice-bear — Plugin Deep Dive | https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/ | Plugin marketplace deep dive (Apr 2026) |
| Skywork — Skills Marketplace Guide | https://skywork.ai/blog/ai-bot/claude-code-skills-marketplace-ultimate-guide/ | Ultimate marketplace guide |
| Skywork — Polymarket MCP | https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560 | Polymarket MCP server guide |
| LiteLLM | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Plugin marketplace tutorial |
| Strapi — Agent Skills | https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them | What are agent skills |
| Verdent — Claude Skills Guide | https://www.verdent.ai/guides/what-are-claude-skills-guide-2026 | Claude skills complete guide |
| Duet.so — Skills 101 | https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills | Tools vs MCP vs Skills |
| ObviousWorks | https://www.obviousworks.ch/en/claude-skills-vs-mcp-the-ultimate-guide-to-efficient-ki-workflows/ | Skills vs MCP German analysis |
| DevToolPicks | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | Skills vs MCP vs Plugins decision |
| Medium — Tahir | https://medium.com/@tahirbalarabe2/ai-agent-skills-explained-simply-4010f6d9db92 | Agent skills explained simply |
| Medium — AB Vijay Kumar | https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996 | Deep dive SKILL.md |
| Medium — ByteBridge | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | MCP Gateways 2026 |
| Blake Crosley | https://blakecrosley.com/guides/claude-code | Claude Code CLI complete guide |
| BuildFastWithAI | https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026 | Skills complete guide |
| AIToolDiscovery | https://www.aitooldiscovery.com/guides/claude-code-reddit | Claude Code Reddit guide |
| Composio YouTube MCP | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP for Claude Code |
| Composio Reddit MCP | https://composio.dev/toolkits/reddit/framework/claude-code | Reddit MCP integration |
| SparkCo — Prediction Market Agent | https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi | AI prediction market agent |
| Scrimba | https://scrimba.com/articles/best-claude-code-tutorials-and-courses-in-2026/ | Best Claude Code tutorials |
| Udemy — Claude Course | https://www.udemy.com/course/claude-course-prompt-skills-mcp-claude-code-cowork-etc/ | Comprehensive Claude course |
| Anthropic Support — Org skills | https://support.claude.com/en/articles/13119606-provision-and-manage-skills-for-your-organization | Enterprise skill provisioning |
| Anthropic Support — Use Skills | https://support.claude.com/en/articles/12512180-use-skills-in-claude | Skills user guide |
| Claude Code Enterprise | https://claude.com/product/claude-code/enterprise | Enterprise product page |
| Claude Code Discover Plugins | https://code.claude.com/docs/en/discover-plugins | Plugin discovery docs |
| IntentSolutions CCPI (npm) | https://www.npmjs.com/package/@intentsolutionsio/ccpi | ccpi CLI package |
| IntuitionLabs | https://intuitionlabs.ai/articles/claude-enterprise-deployment-training-guide-2026 | Enterprise deployment guide |
| SystemPrompt.io — Enterprise | https://systemprompt.io/guides/claude-code-organisation-rollout | Enterprise rollout guide |
| SystemPrompt.io — Managed Settings | https://systemprompt.io/guides/enterprise-claude-code-managed-settings | Managed settings guide |
| CodingNomads | https://codingnomads.com/claude-code-enterprise-deployment-policies-settings | Enterprise policies guide |
| TrueFoundry — Enterprise Security | https://www.truefoundry.com/blog/enterprise-security-for-claude | Enterprise security guide |
| Anthropic Complete Guide PDF | https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf | PDF guide to building skills |
| Anthropic — Claude Code Enterprise | https://claude.com/product/claude-code/enterprise | Enterprise page |

---

## Stats Block

```
├─ 🟠 Reddit: 6 subreddits monitored │ 4,200+ weekly contributors (r/ClaudeCode) │ detailed thread data blocked
├─ 🔵 X: not retrieved (excluded per research scope)
├─ 🔴 YouTube: 5+ videos + 2 courses │ view counts not retrievable (metadata blocked)
├─ 🟢 HN: 9 threads │ points vary (Skills Manager: 3pts) │ 9+ comments (Skills Manager)
├─ 🟣 TikTok: not retrieved
├─ 🩷 Instagram: not retrieved
├─ 🦋 Bluesky: not retrieved
├─ 📊 Polymarket: 6 MCP/skill integrations │ 9,706+ active contracts accessible via MCP
├─ 🌐 Web: 80+ pages
└─ 🗣️ Top voices: @druide67 (HN), @Dshadowzh (HN), @evergreenxx (HN) │ r/ClaudeCode, r/ClaudeAI
```

---

## Data Gaps

- **Reddit direct access:** Reddit.com is inaccessible to Anthropic's crawler (HTTP 403). All Reddit data sourced from third-party aggregation (morphllm.com). No specific post upvote counts, direct thread URLs, or verbatim quotes available. Coverage estimated at 20% of actual Reddit activity.
- **YouTube metadata:** YouTube video pages serve only footer HTML to crawlers; no view counts, like counts, channel names, or transcript data retrieved. 5 videos and 2 courses identified by URL only.
- **Hacker News:** HN returned HTTP 429 (rate limited) on direct thread fetches. Points and comment counts for most threads unavailable; full comment threads not retrieved. Only Skills Manager thread (HN 47423910) had comment data via successful earlier fetch.
- **X/Twitter:** Excluded per research scope.
- **TikTok, Instagram, Bluesky:** No relevant content found for this technical topic.
- **VentureBeat, DevOps.com:** HTTP 429/403 errors prevented full article extraction. Headlines and context obtained via search snippets only.
- **Approximate coverage:** Web ~85%, Hacker News ~40% (URLs known, content partial), Reddit ~20%, YouTube ~30% (titles only), Polymarket ~90% (integrations catalogued, live market data not retrieved).

---

## Key Quotes

> "Most agents support `~/.agents/skills` as a standard location, except Claude Code. We need a unified skill marketplace for different agents." — @Dshadowzh on Hacker News ([Skills Manager thread](https://news.ycombinator.com/item?id=47423910))

> "Claude follows multi-step rules well, Copilot tends to ignore anything beyond the first line. The real challenge isn't file syncing but ensuring the same instruction works across different agents." — @druide67 on Hacker News ([Skills Manager thread](https://news.ycombinator.com/item?id=47423910))

> "6.3 issues per skill on average across platforms, with prompt injection in 36% of skills tested." — Agensi security audit ([marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

> "The catalog size that actually matters is how many skills work well enough that other developers use them repeatedly." — Agensi ([best marketplaces 2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

> "MCP servers are powerful but expensive, with one developer documenting 67,000 tokens consumed from connecting four MCP servers before typing a single prompt." — r/ClaudeCode community via [morphllm.com aggregation](https://www.morphllm.com/claude-code-reddit)

> "Anthropic produced two standards (MCP and Agent Skills) that seem to be competing — fueling heated debate on social media, Hacker News, and developer blogs." — [Ravikanth Chaganti analysis](https://ravichaganti.com/blog/agent-skills-vs-model-context-protocol-how-do-you-choose/)

> "Build once, use across agents." — Core value proposition of the Agent Skills open standard ([Paperclipped](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/))

> "Claude Code is becoming a vertical operating system for those who write code, where the editor and model are only two components, with the other half of the work done by the marketplace, skills, worktrees, and automation primitives." — [claudemarketplaces.com](https://claudemarketplaces.com/)

> "OX researchers uncovered an architectural RCE vulnerability in Anthropic's Model Context Protocol — affecting 150M+ downloads." — [OX Security](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/)

> "Marketplaces should be treated as software supply chains with version control, approvals, observability, and security scanning as mandatory." — [agensi.io enterprise guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide)
